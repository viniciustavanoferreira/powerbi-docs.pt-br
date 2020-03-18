---
title: Adicionar suporte a indicador para visuais do Power BI
description: Os visuais do Power BI podem manipular a alternância de indicadores
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 06/18/2019
ms.openlocfilehash: 5bf1c79aa411788fdb3275b938e7eaad7d6014a1
ms.sourcegitcommit: 6bbc3d0073ca605c50911c162dc9f58926db7b66
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79380515"
---
# <a name="add-bookmark-support-for-power-bi-visuals"></a>Adicionar suporte a indicador para visuais do Power BI

Com os indicadores de relatório do Power BI, você pode capturar uma exibição configurada de uma página de relatório, o estado de seleção e o estado de filtragem do visual. Mas isso requer ação adicional do lado dos visuais do Power BI para dar suporte ao indicador e reagir corretamente às alterações.

Para obter mais informações sobre indicadores, confira [Usar indicadores para compartilhar informações e criar histórias no Power BI](https://docs.microsoft.com/power-bi/desktop-bookmarks).

## <a name="report-bookmarks-support-in-your-visual"></a>Suporte a indicadores de relatório no visual

Se o visual interagir com outros visuais, selecionar pontos de dados ou filtrar outros visuais, você precisará restaurar o estado das propriedades.

## <a name="add-report-bookmarks-support"></a>Adicionar suporte a indicadores de relatório

1. Instale (ou atualize) o utilitário necessário, [powerbi-visuals-utils-interactivityutils](https://github.com/Microsoft/PowerBI-visuals-utils-interactivityutils/) versão 3.0.0 ou posterior. Ele contém classes adicionais para manipular com a seleção de estado ou o filtro. Ele é necessário para filtrar visuais e qualquer visual que usa `InteractivityService`.

2. Atualize a API do visual para a versão 1.11.0 para usar `registerOnSelectCallback` em uma instância do `SelectionManager`. É necessário para visuais sem filtro que usam o `SelectionManager` simples, em vez do `InteractivityService`.

### <a name="how-power-bi-visuals-interact-with-power-bi-in-report-bookmarks"></a>Como os visuais do Power BI interagem com o Power BI em indicadores de relatório

Vamos considerar o seguinte cenário: você deseja criar vários indicadores na página do relatório, com um estado de seleção diferente em cada indicador.

Primeiro, você seleciona um ponto de dados em seu visual. O visual interage com o Power BI e outros visuais, passando seleções para o host. Em seguida, seleciona **Adicionar** no painel **Indicador** e o Power BI salva as seleções atuais para o novo indicador.

Isso acontece repetidamente à medida que você altera a seleção e adiciona novos indicadores. Depois de criar os indicadores, você pode alternar entre eles.

Quando você seleciona um indicador, o Power BI restaura o estado de seleção ou o filtro salvo e passa para os visuais. Outros visuais são realçados ou filtrados de acordo com o estado armazenado no indicador. O host do Power BI é responsável pelas ações. O visual é responsável por refletir corretamente o novo estado de seleção (por exemplo, para alterar as cores dos pontos de dados renderizados).

O novo estado de seleção é comunicado ao visual por meio do método `update`. O argumento `options` contém uma propriedade especial, `options.jsonFilters`. Sua propriedade JSONFilter pode conter `Advanced Filter` e `Tuple Filter`.

O visual deve restaurar valores de filtro para exibir o estado correspondente do visual para o indicador selecionado. Ou, se o visual usar somente seleções, você poderá usar a chamada de função retorno de chamada especial registrada como o método `registerOnSelectCallback` de ISelectionManager.

### <a name="visuals-with-selection"></a>Visuais com Seleção

Se o visual interage com outros visuais usando a [Seleção](https://github.com/Microsoft/PowerBI-visuals/blob/master/Tutorial/Selection.md), você pode adicionar indicadores de uma das duas maneiras:

* Se o visual ainda não tiver usado [InteractivityService](https://github.com/Microsoft/powerbi-visuals-utils-interactivityutils/blob/master/docs/api/interactivityService.md), você poderá usar o método `FilterManager.restoreSelectionIds`.

* Se o visual já usar [InteractivityService](https://github.com/Microsoft/powerbi-visuals-utils-interactivityutils/blob/master/docs/api/interactivityService.md) para gerenciar seleções, você deverá usar o método `applySelectionFromFilter` na instância do `InteractivityService`.

#### <a name="use-iselectionmanagerregisteronselectcallback"></a>Usar ISelectionManager.registerOnSelectCallback

Quando você seleciona um indicador, o Power BI chama o método `callback` do visual com as seleções correspondentes. 

```typescript
this.selectionManager.registerOnSelectCallback(
    (ids: ISelectionId[]) => {
        //called when a selection was set by Power BI
    });
);
```

Vamos supor que você tenha um ponto de dados em seu visual criado no método [visualTransform](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/master/src/barChart.ts#L74).

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

Agora você tem `visualDataPoints` como seus pontos de dados e a matriz `ids` passados para a função `callback`.

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

### <a name="use-interactivityservice-for-control-selections-in-the-visual"></a>Usar InteractivityService para controlar seleções no Visual

Se o visual usar `InteractivityService`, ele dará suporte a indicadores sem exigir que você realize nenhuma ação adicional.

Quando você seleciona indicadores, o utilitário manipula o estado de seleção do Visual.

### <a name="visuals-with-a-filter"></a>Visuais com um filtro

Vamos supor que o visual crie um filtro de dados por intervalo de datas. Você tem `startDate` e `endDate` como as datas de início e de término do intervalo.

O visual cria um filtro avançado e chama o método de host `applyJsonFilter` para filtrar dados pelas condições relevantes.

O destino é a tabela usada para filtragem.

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

Cada vez que você seleciona um indicador, o visual personalizado recebe uma chamada `update`.

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

Depois disso, o visual deve alterar seu estado interno para refletir as condições atuais. O estado interno inclui os pontos de dados e os objetos de visualização (linhas, retângulos e assim por diante).

> [!IMPORTANT]
> No cenário de indicadores de relatório, o visual não deve chamar `applyJsonFilter` para filtrar os outros elementos visuais. Eles já serão filtrados pelo Power BI.

O visual da Segmentação da Linha do Tempo altera o seletor de intervalo para os intervalos de dados correspondentes.

Para obter mais informações, confira [Repositório de segmentação da linha do tempo](https://github.com/Microsoft/powerbi-visuals-timeline/commit/606f1152f59f82b5b5a367ff3b117372d129e597?diff=unified#diff-b6ef9a9ac3a3225f8bd0de84bee0a0df).

### <a name="filter-the-state-to-save-visual-properties-in-bookmarks"></a>Filtre o estado para salvar as propriedades visuais em indicadores

A propriedade `filterState` cria uma propriedade de uma parte da filtragem. O visual pode armazenar uma variedade de valores em indicadores.

Para salvar o valor da propriedade como um estado de filtro, marque a propriedade de objeto como `"filterState": true` no arquivo *capabilities.json*.

Por exemplo, a Segmentação de Linha do Tempo armazena os valores de propriedade `Granularity` em um filtro. Ela permite que a granularidade atual mude conforme você altera os indicadores.

Para obter mais informações, confira [Repositório de segmentação da linha do tempo](https://github.com/microsoft/powerbi-visuals-timeline/commit/8b7d82dd23cd2bd71817f1bc5d1e1732347a185e#diff-290828b604cfa62f1cb310f2e90c52fdR334).
