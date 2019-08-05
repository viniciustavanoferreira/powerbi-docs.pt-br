---
title: Indicadores
description: O visual do Power BI pode manipular a alternância de indicadores
author: zBritva
ms.author: v-ilgali
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 90e3fc73cd49a5c84a5c2acc68a8cf5e0e4aa42b
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68425495"
---
# <a name="add-bookmarks-support-for-power-bi-visuals"></a>Adicionar suporte a indicadores para visuais do Power BI

Indicadores de relatório do Power BI permitem capturar a exibição configurada de uma página de relatório, estado de seleção e estado de filtragem do visual. Mas isso requer ação adicional do lado dos visuais personalizados para dar suporte ao indicador e reagir corretamente às alterações.

Leia mais sobre indicadores na [documentação](https://docs.microsoft.com/power-bi/desktop-bookmarks)

## <a name="report-bookmarks-support-in-your-visual"></a>Suporte a indicadores de relatório no visual

Se o visual interagir com outros visuais, selecionar pontos de dados ou filtrar outros visuais, você precisará restaurar o estado das propriedades.

## <a name="how-to-add-report-bookmarks-support"></a>Como adicionar suporte a indicadores de relatório

1. Instale (ou atualize) o utilitário necessário: `powerbi-visuals-utils-interactivityutils`(https://github.com/Microsoft/PowerBI-visuals-utils-interactivityutils/) ) versão 3.0.0 ou superior. Ele contém classes adicionais para manipular com seleção de estado ou filtro. Ele é necessário para filtrar visuais e qualquer visual usando o `InteractivityService`.

2. Atualize a API do visual para a versão 1.11.0 para usar `registerOnSelectCallback` em uma instância de `SelectionManager`. Ela é necessária para visuais sem filtro usando o `SelectionManager` simples em vez de `InteractivityService`.

### <a name="how-custom-visuals-interact-with-power-bi-in-the-report-bookmarks-scenario"></a>Como os visuais personalizados interagem com o Power BI no cenário de indicadores de relatório

Vamos considerar o exemplo a seguir: Um usuário cria vários indicadores na página de relatório, com um estado de seleção diferente em cada indicador.

Primeiro, o usuário seleciona um ponto de dados em seu visual. O visual interage com o Power BI e outros visuais, passando seleções para o host. Em seguida, o usuário seleciona "Adicionar" no `Bookmark panel` e o Power BI salva as seleções atuais para o novo indicador.

Isso acontece repetidamente à medida que o usuário altera a seleção e adiciona novos indicadores.
Depois de criados, o usuário pode alternar entre os indicadores.

Quando os usuários selecionam um indicador, o Power BI restaura o estado de seleção ou o filtro salvo e passa para os visuais. Outros visuais serão realçados ou filtrados de acordo com o estado armazenado no indicador. Host do Power BI responsável por ações. O visual é responsável por refletir corretamente o novo estado de seleção (por exemplo, alterar a cor dos pontos de dados renderizados).

O novo estado de seleção é comunicado ao visual por meio do método `update`. O argumento `options` conterá uma propriedade especial: `options.jsonFilters`. É JSONFilter, a propriedade pode conter `Advanced Filter` e `Tuple Filter`.

O visual deve restaurar valores de filtro para exibir o estado correspondente do visual para o indicador selecionado.

Ou use o método `registerOnSelectCallback` especial registrado na chamada de função de callback de ISelectionManager, se o visual usar somente seleções.

### <a name="visuals-with-selections"></a>Visuais com seleções

Se os visuais interagem com outros visuais usando [seleções](https://github.com/Microsoft/PowerBI-visuals/blob/master/Tutorial/Selection.md). Você tem duas maneiras de adicionar indicadores.

* Você poderá usar o método `FilterManager.restoreSelectionIds` se **não tiver usado [`InteractivityService`](https://github.com/Microsoft/powerbi-visuals-utils-interactivityutils/blob/master/docs/api/interactivityService.md)** antes no visual.

* Se o seu visual já usa **[`InteractivityService`](https://github.com/Microsoft/powerbi-visuals-utils-interactivityutils/blob/master/docs/api/interactivityService.md)** para gerenciar seleções. Você deve usar o método `applySelectionFromFilter` na instância de `InteractivityService`.

#### <a name="using-iselectionmanagerregisteronselectcallback"></a>Usando `ISelectionManager.registerOnSelectCallback`

Quando um usuário clica em indicadores, o Power BI chama o método `callback` do visual com as seleções correspondentes. 

```typescript
this.selectionManager.registerOnSelectCallback(
    (ids: ISelectionId[]) => {
        //called when a selection was set by Power BI
    });
);
```

Vamos supor que você tenha um ponto de dados em seu visual criado no método [`'visualTransform'`](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/master/src/barChart.ts#L74).

E `datapoints` é semelhante a:

```typescript
visualDataPoints.push({
    category: categorical.categories[0].values[i],
    color: getCategoricalObjectValue<Fill>(categorical.categories[0], i, 'colorSelector', 'fill', defaultColor).solid.color,
    selectionId: host.createSelectionIdBuilder()
        .withCategory(categorical.categories[0], i)
        .createSelectionId(),
    selected: false
});
```

Portanto, você tem `visualDataPoints` como os pontos de dados e a matriz `ids` passada para a função `callback`.

Neste ponto, o visual deve comparar a matriz de `ISelectionId[]` com as seleções em sua matriz `visualDataPoints` e marcar os pontos de dados correspondentes conforme selecionados.

```typescript
this.selectionManager.registerOnSelectCallback(
    (ids: ISelectionId[]) => {
        visualDataPoints.forEach(dataPoint => {
            ids.forEach(bookmarkSelection => {
                if (bookmarkSelection.equals(dataPoint.selectionId)) {
                    dataPoint.selected = true;
                }
            });
        });
    });
);
```

Depois de atualizar os pontos de dados, eles refletirão o estado de seleção atual armazenado no objeto `filter`. Em seguida, quando os pontos de dados são renderizados, o estado de seleção do visual personalizado corresponderá ao estado do indicador.

### <a name="using-interactivityservice-for-control-selections-in-the-visual"></a>Usar `InteractivityService` para controlar seleções no visual

Se o visual usar `InteractivityService`, ele dará suporte a indicadores sem exigir que você realize nenhuma ação adicional.

O utilitário manipulará o estado de seleção do visual quando o usuário selecionar indicadores.

### <a name="visuals-with-filter"></a>Visuais com filtro

Vamos supor que o visual crie um filtro de dados por intervalo de datas. Portanto, temos `startDate` e `endDate` como o início e o fim do intervalo.
O visual cria um filtro avançado e chama o método de host `applyJsonFilter` para filtrar dados pelas condições relevantes.
O `target` é a tabela para filtragem.

```typescript
import { AdvancedFilter } from "powerbi-models";

const filter: IAdvancedFilter = new AdvancedFilter(
    target,
    "And",
    {
        operator: "GreaterThanOrEqual",
        value: startDate
            ? startDate.toJSON()
            : null
    },
    {
        operator: "LessThanOrEqual",
        value: endDate
            ? endDate.toJSON()
            : null
    });

this.host.applyJsonFilter(
    filter,
    "general",
    "filter",
    (startDate && endDate)
        ? FilterAction.merge
        : FilterAction.remove
);
```

Cada vez que um usuário clica em um indicador, o visual personalizado recebe uma chamada `update`.

O visual personalizado deve verificar o filtro no objeto:

```typescript
const filter: IAdvancedFilter = FilterManager.restoreFilter(
    && options.jsonFilters
    && options.jsonFilters[0] as any
) as IAdvancedFilter;
```

Se o objeto `filter` não for nulo, o visual deverá restaurar as condições de filtro do objeto:

```typescript
const jsonFilters: AdvancedFilter = this.options.jsonFilters as AdvancedFilter[];

if (jsonFilters
    && jsonFilters[0]
    && jsonFilters[0].conditions
    && jsonFilters[0].conditions[0]
    && jsonFilters[0].conditions[1]
) {
    const startDate: Date = new Date(`${jsonFilters[0].conditions[0].value}`);
    const endDate: Date = new Date(`${jsonFilters[0].conditions[1].value}`);

    // apply restored conditions
} else {
    // apply default settings
}
```

Depois disso, o visual deve alterar seu estado interno – pontos de dados e objetos de visualização (linhas, retângulos e assim por diante) – para refletir as condições atuais.

> [!IMPORTANT]
> No cenário de indicadores de relatório, o visual não deve chamar `applyJsonFilter` para filtrar outros visuais – eles já serão filtrados pelo Power BI.

Seletor de intervalo de alterações visuais da segmentação de linha do tempo para corresponder a intervalos de dados.

Para obter mais informações, confira [Repositório de segmentação da linha do tempo](https://github.com/Microsoft/powerbi-visuals-timeline/commit/606f1152f59f82b5b5a367ff3b117372d129e597?diff=unified#diff-b6ef9a9ac3a3225f8bd0de84bee0a0df).

### <a name="filter-state-to-save-visual-properties-in-bookmarks"></a>Estado do filtro para salvar as propriedades visuais em indicadores

A propriedade `filterState` cria uma propriedade de uma parte da filtragem. O visual pode armazenar valores diferentes em indicadores.

Para salvar o valor da propriedade como estado de filtro, a propriedade do objeto deve ser marcada como `"filterState": true` em `capabilities.json`.

Exemplo: `Timeline Slicer` armazena valores da propriedade `Granularity` no filtro. E isso permite alterar a granularidade atual na alteração de indicadores pelo usuário.

Para obter mais informações, confira [Repositório de segmentação da linha do tempo](https://github.com/microsoft/powerbi-visuals-timeline/commit/8b7d82dd23cd2bd71817f1bc5d1e1732347a185e#diff-290828b604cfa62f1cb310f2e90c52fdR334).
