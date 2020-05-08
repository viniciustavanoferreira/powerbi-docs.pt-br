---
title: Suporte ao modo de alto contraste em visuais do Power BI
description: Este artigo descreve como adicionar suporte ao modo de alto contraste para visuais do Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 9372187ae1fdfac27f6b3e7267a1c0622c063464
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/05/2020
ms.locfileid: "80114326"
---
# <a name="high-contrast-mode-support-in-power-bi-visuals"></a>Suporte ao modo de alto contraste em visuais do Power BI

A configuração de *alto contraste* do Windows torna o texto e os aplicativos mais fáceis de ver exibindo cores mais distintas. Este artigo discute como adicionar suporte ao modo de alto contraste para visuais do Power BI. Para obter mais informações, confira [suporte de alto contraste no Power BI](https://powerbi.microsoft.com/blog/power-bi-desktop-june-2018-feature-summary/#highContrast).

Para exibir uma implementação do suporte de alto contraste, vá para o [repositório do visual PowerBI-visuals-sampleBarChart](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/61011c82b66ca0d3321868f1d089c65101ca42e6).

## <a name="on-initialization"></a>Na inicialização

O membro colorPalette de `options.host` tem várias propriedades para o modo de alto contraste. Use essas propriedades para determinar se o modo de alto contraste está ativo e, em caso afirmativo, que cores usar.

### <a name="detect-that-power-bi-is-in-high-contrast-mode"></a>Detectar que o Power BI está em modo de alto contraste

Se `host.colorPalette.isHighContrast` for `true`, o modo de alto contraste estará ativo e o visual deverá se desenhar adequadamente.

### <a name="get-high-contrast-colors"></a>Obter cores de alto contraste

No modo de alto contraste, seu visual deve se limitar às seguintes configurações:

* A cor do **primeiro plano** é usada para desenhar linhas, ícones, textos e contornos ou preenchimentos de formas.
* A cor do **segundo plano** é usada para o segundo plano e como a cor de preenchimento das formas contornadas.
* A cor do **Primeiro plano – selecionada** é usada para indicar um elemento selecionado ou ativo.
* A cor do **Hiperlink** é usada somente para texto de hiperlink.

> [!NOTE]
> Se for necessária uma cor secundária, a cor de primeiro plano poderá ser usada com alguma opacidade (visuais nativos do Power BI usam opacidade de 40%). Use com moderação para manter os detalhes visuais fáceis de ver.

Durante a inicialização, você pode armazenar os seguintes valores:

```typescript
private isHighContrast: boolean;

private foregroundColor: string;
private backgroundColor: string;
private foregroundSelectedColor: string;
private hyperlinkColor: string;
//...

constructor(options: VisualConstructorOptions) {
    this.host = options.host;
    let colorPalette: ISandboxExtendedColorPalette = host.colorPalette;
    //...
    this.isHighContrast = colorPalette.isHighContrast;
    if (this.isHighContrast) {
        this.foregroundColor = colorPalette.foreground.value;
        this.backgroundColor = colorPalette.background.value;
        this.foregroundSelectedColor = colorPalette.foregroundSelected.value;
        this.hyperlinkColor = colorPalette.hyperlink.value;
    }
```

Outra opção é armazenar o objeto `host` durante a inicialização e acessar as propriedades `colorPalette` relevantes durante a atualização.

## <a name="on-update"></a>Ao atualizar

As implementações específicas de suporte de alto contraste variam de visual para visual e dependem dos detalhes do design gráfico. Para manter os detalhes importantes fáceis de distinguir com as cores limitadas, o modo de alto contraste costuma exigir um design um pouco diferente do modo padrão.

Os visuais nativos do Power BI seguem estas diretrizes:

* Todos os pontos de dados usam a mesma cor (primeiro plano).
* Todos os textos, eixos, setas, linhas e assim por diante usam a cor de primeiro plano.
* As formas espessas são desenhadas como contornos, com traços espessos (pelo menos dois pixels) e preenchimento de cor da tela de fundo.
* Quando os pontos de dados são relevantes, eles são diferenciados por diferentes formas de marcador e as linhas de dados são diferenciadas por traços diferentes.
* Quando um elemento de dados é realçado, todos os outros elementos alteram sua opacidade para 40%.
* Para segmentações, os elementos de filtro ativo usam a cor selecionada em primeiro plano.

No gráfico de barras de exemplo a seguir, todas as barras são desenhadas com dois pixels de contorno em primeiro plano e preenchimento de segundo plano. Compare o modo com as cores padrão e com alguns temas de alto contraste:

![Gráfico de Barras de exemplo usando cores padrão](media/high-contrast-support/hc-samplebarchart-standard.png)
![Gráfico de barras de exemplo usando *Dark #2*](media/high-contrast-support/hc-samplebarchart-dark2.png)
![Gráfico de barras de exemplo usando tema de cor *White*](media/high-contrast-support/hc-samplebarchart-white.png)

A próxima seção mostra um local na função `visualTransform` que foi alterada para dar suporte a alto contraste. Ele é chamado como parte da renderização durante a atualização.

### <a name="before"></a>Antes

```typescript
for (let i = 0, len = Math.max(category.values.length, dataValue.values.length); i < len; i++) {
    let defaultColor: Fill = {
        solid: {
            color: colorPalette.getColor(category.values[i] + '').value
        }
    };

    barChartDataPoints.push({
        category: category.values[i] + '',
        value: dataValue.values[i],
        color: getCategoricalObjectValue<Fill>(category, i, 'colorSelector', 'fill', defaultColor).solid.color,
        selectionId: host.createSelectionIdBuilder()
            .withCategory(category, i)
            .createSelectionId()
    });
}
```

### <a name="after"></a>Depois

```typescript
for (let i = 0, len = Math.max(category.values.length, dataValue.values.length); i < len; i++) {
    const color: string = getColumnColorByIndex(category, i, colorPalette);

    const selectionId: ISelectionId = host.createSelectionIdBuilder()
        .withCategory(category, i)
        .createSelectionId();

    barChartDataPoints.push({
        color,
        strokeColor,
        strokeWidth,
        selectionId,
        value: dataValue.values[i],
        category: `${category.values[i]}`,
    });
}

//...

function getColumnColorByIndex(
    category: DataViewCategoryColumn,
    index: number,
    colorPalette: ISandboxExtendedColorPalette,
): string {
    if (colorPalette.isHighContrast) {
        return colorPalette.background.value;
    }

    const defaultColor: Fill = {
        solid: {
            color: colorPalette.getColor(`${category.values[index]}`).value,
        }
    };

    return getCategoricalObjectValue<Fill>(category, index, 'colorSelector', 'fill', defaultColor).solid.color;
}
```
