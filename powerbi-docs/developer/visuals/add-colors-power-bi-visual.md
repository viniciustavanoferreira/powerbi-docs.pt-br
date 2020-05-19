---
title: Adicionar cores aos visuais do Power BI
description: Este artigo descreve como adicionar cores aos visuais do Power BI e como manipular pontos de dados para um visual com cores.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 03/27/2020
ms.openlocfilehash: 3f3574545d82ac11c762b7011afdc49cbe855224
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83141158"
---
# <a name="add-colors-to-your-power-bi-visuals"></a>Adicionar cores aos visuais do Power BI

Este artigo descreve como adicionar cores a seus visuais e como manipular pontos de dados para um visual com cores.

`IVisualHost` expõe a cor como um de seus serviços.
O código de exemplo neste artigo modifica o [visual SampleBarChart](https://github.com/microsoft/PowerBI-visuals-sampleBarChart).
Para obter o código-fonte, confira [barChart.ts](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/blob/master/src/barChart.ts).

Para começar a criar visuais, confira [Desenvolver um visual do Power BI](custom-visual-develop-tutorial.md).

## <a name="add-color-to-data-points"></a>Adicionar cor a pontos de dados

Uma cor diferente representa cada ponto de dados.
Adicione a cor à interface do `BarChartDataPoint`, como no seguinte exemplo:

```typescript
/**
 * Interface for BarChart data points.
 *
 * @interface
 * @property {number} value    - Data value for point.
 * @property {string} category - Corresponding category of data value.
 * @property {string} color    - Color corresponding to data point.
 */
interface BarChartDataPoint {
    value: number;
    category: string;
    color: string;
};
```

## <a name="use-the-color-palette-service"></a>Usar o serviço de paleta de cores

O serviço `colorPalette` gerencia as cores usadas em seu visual.
Uma instância do serviço está disponível no `IVisualHost`.

Defina-a no método `update`.

```typescript
constructor(options: VisualConstructorOptions) {
        this.host = options.host; // host: IVisualHost
        ...
    }

public update(options: VisualUpdateOptions) {

    let colorPalette: IColorPalette = host.colorPalette;
    ...
}
```

## <a name="assigning-color-to-data-points"></a>Atribuir cor a pontos de dados

Em seguida, especifique `dataPoints`.
Neste exemplo, cada `dataPoints` inclui valor, categoria e cor.
`dataPoints` também pode incluir outras propriedades.

Em `SampleBarChart`, o método `visualTransform` encapsula o cálculo de `dataPoints`.
Esse método faz parte do ViewModel do gráfico de barras.
Como o método itera o cálculo de `dataPoints` em `visualTransform`, é o lugar ideal para atribuir cores, como no seguinte código:

```typescript

public update(options: VisualUpdateOptions) {
    ....
    let viewModel: BarChartViewModel = visualTransform(options, this.host);
    ....
}

function visualTransform(options: VisualUpdateOptions, host: IVisualHost): BarChartViewModel {
    let colorPalette: IColorPalette = host.colorPalette; // host: IVisualHost
    for (let i = 0, len = Math.max(category.values.length, dataValue.values.length); i < len; i++) {
        barChartDataPoints.push({
            category: category.values[i],
            value: dataValue.values[i],
            color: colorPalette.getColor(category.values[i]).value,
        });
    }
}
```

Em seguida, aplique dados de `dataPoints` no [d3](https://d3js.org/)-selection `barSelection` dentro do método `update`:

```typescript
// This code is actual for d3 v5
// in d3 v5 for this case we should use merge() after enter() and apply changes on barSelectionMerged
this.barSelection = this.barContainer
    .selectAll('.bar')
    .data(this.barDataPoints);

const barSelectionMerged = this.barSelection
    .enter()
    .append('rect')
    .merge(<any>this.barSelection);

barSelectionMerged.classed('bar', true);

barSelectionMerged
.attr("width", xScale.bandwidth())
.attr("height", d => height - yScale(<number>d.value))
.attr("y", d => yScale(<number>d.value))
.attr("x", d => xScale(d.category))
.style("fill", (dataPoint: BarChartDataPoint) => dataPoint.color)
.style("stroke", (dataPoint: BarChartDataPoint) => dataPoint.strokeColor)
.style("stroke-width", (dataPoint: BarChartDataPoint) => `${dataPoint.strokeWidth}px`);

this.barSelection
    .exit()
    .remove();
```

## <a name="next-steps"></a>Próximas etapas

Para saber mais sobre visuais do Power BI, confira [Funcionalidades e propriedades de visuais do Power BI](capabilities.md).

Para saber mais sobre como desenvolver Power BI visuais, confira [Como depurar visuais do Power BI](visuals-how-to-debug.md) e [Solucionar problemas de visuais do Power BI](power-bi-custom-visuals-troubleshoot.md).
