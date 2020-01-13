---
title: Introdução ao uso de utilitários de gráfico no visual do Power BI
description: Este artigo descreve como usar os utilitários de gráfico para desenhar eixos e legendas no visual do Power BI
author: vtkalek
ms.author: asander
manager: asander
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: e67b37f73b3cea097a296f313fbfc8922b7dd945
ms.sourcegitcommit: 4359baa43ca01b179d28ec59f4e61ba8c07ee288
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/20/2019
ms.locfileid: "75308561"
---
# <a name="chart-utils"></a>Utilitários de gráfico

ChartUtils é um conjunto de interfaces e métodos para criar eixos, rótulos de dados e legendas em visuais do Power BI.

## <a name="installation"></a>Instalação

Para instalar o pacote, você deve executar o seguinte comando no diretório com seu visual atual:

```bash
npm install powerbi-visuals-utils-chartutils --save
```

## <a name="axis-helper"></a>Assistente de eixo

O assistente de eixo (objeto `axis` em utilitários) fornece funções para simplificar as manipulações com o eixo.

O módulo fornece as seguintes funções:

### <a name="getrecommendednumberofticksforxaxis"></a>getRecommendedNumberOfTicksForXAxis

Essa função retorna o número recomendado de tiques de acordo com a largura do gráfico.

```typescript
function getRecommendedNumberOfTicksForXAxis(availableWidth: number): number;
```

Exemplo:

```typescript
import { axis } from "powerbi-visuals-utils-chartutils";
// ...
axis.getRecommendedNumberOfTicksForXAxis(1024);

// returns: 8
```

### <a name="getrecommendednumberofticksforyaxis"></a>getRecommendedNumberOfTicksForYAxis

Essa função retorna o número recomendado de tiques de acordo com a altura do gráfico.

```typescript
function getRecommendedNumberOfTicksForYAxis(availableWidth: number);
```

Exemplo:

```typescript
import { axis } from "powerbi-visuals-utils-chartutils";
// ...
axis.getRecommendedNumberOfTicksForYAxis(100);

// returns: 3
```

### <a name="getbestnumberofticks"></a>getBestNumberOfTicks

Obtém o número ideal de tiques com base no valor mínimo, no valor máximo e nos metadados da medida e na contagem máxima de tiques;

```typescript
function getBestNumberOfTicks(
  min: number,
  max: number,
  valuesMetadata: DataViewMetadataColumn[],
  maxTickCount: number,
  isDateTime?: boolean
): number;
```

Exemplo:

```typescript
import { axis } from "powerbi-visuals-utils-chartutils";
// ...
var dataViewMetadataColumnWithIntegersOnly: powerbi.DataViewMetadataColumn[] = [
  {
    displayName: "col1",
    isMeasure: true,
    type: ValueType.fromDescriptor({ integer: true })
  },
  {
    displayName: "col2",
    isMeasure: true,
    type: ValueType.fromDescriptor({ integer: true })
  }
];
var actual = axis.getBestNumberOfTicks(
  0,
  3,
  dataViewMetadataColumnWithIntegersOnly,
  6
);

// returns: 4
```

### <a name="getticklabelmargins"></a>getTickLabelMargins

Essa função retorna as margens para rótulos de tique.

```typescript
function getTickLabelMargins(
  viewport: IViewport,
  yMarginLimit: number,
  textWidthMeasurer: ITextAsSVGMeasurer,
  textHeightMeasurer: ITextAsSVGMeasurer,
  axes: CartesianAxisProperties,
  bottomMarginLimit: number,
  properties: TextProperties,
  scrollbarVisible?: boolean,
  showOnRight?: boolean,
  renderXAxis?: boolean,
  renderY1Axis?: boolean,
  renderY2Axis?: boolean
): TickLabelMargins;
```

Exemplo:

```typescript
import { axis } from "powerbi-visuals-utils-chartutils";
// ...

axis.getTickLabelMargins(
  plotArea,
  marginLimits.left,
  TextMeasurementService.measureSvgTextWidth,
  TextMeasurementService.estimateSvgTextHeight,
  axes,
  marginLimits.bottom,
  textProperties,
  /*scrolling*/ false,
  showY1OnRight,
  renderXAxis,
  renderY1Axis,
  renderY2Axis
);

// returns:  xMax, yLeft, yRight, stackHeigh;
```

### <a name="isordinal"></a>isOrdinal

Verifica se uma cadeia de caracteres é nula ou indefinida ou vazia.

```typescript
function isOrdinal(type: ValueTypeDescriptor): boolean;
```

Exemplo:

```typescript
import { axis } from "powerbi-visuals-utils-chartutils";
// ...
let type = ValueType.fromDescriptor({ misc: { barcode: true } });
axis.isOrdinal(type);

// returns: true
```

### <a name="isdatetime"></a>isDateTime

Verifica se o valor é do tipo DateTime.

```typescript
function isDateTime(type: ValueTypeDescriptor): boolean;
```

Exemplo:

```typescript
import { axis } from "powerbi-visuals-utils-chartutils";
// ...

axis.isDateTime(ValueType.fromDescriptor({ dateTime: true }));

// returns: true
```

### <a name="getcategorythickness"></a>getCategoryThickness

Usa a escala D3 para obter a espessura real da categoria.

```typescript
function getCategoryThickness(scale: any): number;
```

Exemplo:

```typescript
import { axis } from "powerbi-visuals-utils-chartutils";
// ...

let range = [0, 100];
let domain = [0, 10];
let scale = d3.scale
  .linear()
  .domain(domain)
  .range(range);
let actualThickness = axis.getCategoryThickness(scale);
```

### <a name="invertordinalscale"></a>invertOrdinalScale

Essa função inverte a escala ordinal. Se x < scale.range()[0], então scale.domain()[0] é retornado.
Caso contrário, ele retorna o item mais alto em scale.domain(), que é <=x.

```typescript
function invertOrdinalScale(scale: d3.scale.Ordinal<any, any>, x: number);
```

Exemplo:

```typescript
import { axis } from "powerbi-visuals-utils-chartutils";
// ...

let domain: number[] = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9],
  pixelSpan: number = 100,
  ordinalScale: d3.scale.ordinal = axis.createOrdinalScale(
    pixelSpan,
    domain,
    0.4
  );

axis.invertOrdinalScale(ordinalScale, 49);

// returns: 4
```

### <a name="findclosestxaxisindex"></a>findClosestXAxisIndex

Essa função localiza e retorna o índice do eixo x mais próximo.

```typescript
function findClosestXAxisIndex(
  categoryValue: number,
  categoryAxisValues: AxisHelperCategoryDataPoint[]
): number;
```

Exemplo:

```typescript
import { axis } from "powerbi-visuals-utils-chartutils";
// ...

/**
 * Finds the index of the category of the given x coordinate given.
 * pointX is in non-scaled screen-space, and offsetX is in render-space.
 * offsetX does not need any scaling adjustment.
 * @param {number} pointX The mouse coordinate in screen-space, without scaling applied
 * @param {number} offsetX Any left offset in d3.scale render-space
 * @return {number}
 */
private findIndex(pointX: number, offsetX?: number): number {
    // we are using mouse coordinates that do not know about any potential CSS transform scale
    let xScale = this.scaleDetector.getScale().x;
    if (!Double.equalWithPrecision(xScale, 1.0, 0.00001)) {
        pointX = pointX / xScale;
    }
    if (offsetX) {
        pointX += offsetX;
    }

    let index = axis.invertScale(this.xAxisProperties.scale, pointX);
    if (this.data.isScalar) {
        // When we have scalar data the inverted scale produces a category value, so we need to search for the closest index.
        index = axis.findClosestXAxisIndex(index, this.data.categoryData);
    }

    return index;
}
```

### <a name="diffscaled"></a>diffScaled

Essa função computa e retorna uma comparação de valores na escala.

```typescript
function diffScaled(
  scale: d3.scale.Linear<any, any>,
  value1: any,
  value2: any
): number;
```

Exemplo:

```typescript
import { axis } from "powerbi-visuals-utils-chartutils";
// ...

var scale: d3.scale.Linear<number, number>,
    range = [0, 999],
    domain = [0, 1, 2, 3, 4, 5, 6, 7, 8, 999];

scale = d3.scale.linear()
    .range(range)
    .domain(domain);

return axis.diffScaled(scale, 0, 0));

// returns: 0
```

### <a name="createdomain"></a>createDomain

Essa função cria um domínio de valores para o eixo.

```typescript
function createDomain(
  data: any[],
  axisType: ValueTypeDescriptor,
  isScalar: boolean,
  forcedScalarDomain: any[],
  ensureDomain?: NumberRange
): number[];
```

Exemplo:

```typescript
import { axis } from "powerbi-visuals-utils-chartutils";
// ...

var cartesianSeries = [
  {
    data: [
      { categoryValue: 7, value: 11, categoryIndex: 0, seriesIndex: 0 },
      {
        categoryValue: 9,
        value: 9,
        categoryIndex: 1,
        seriesIndex: 0
      },
      {
        categoryValue: 15,
        value: 6,
        categoryIndex: 2,
        seriesIndex: 0
      },
      { categoryValue: 22, value: 7, categoryIndex: 3, seriesIndex: 0 }
    ]
  }
];

var domain = axis.createDomain(
  cartesianSeries,
  ValueType.fromDescriptor({ text: true }),
  false,
  []
);

// returns: [0, 1, 2, 3]
```

### <a name="getcategoryvaluetype"></a>getCategoryValueType

Essa função obtém a `ValueType` de uma coluna de categoria. O padrão será `Text` se o tipo não estiver presente.

```typescript
function getCategoryValueType(
  data: any[],
  axisType: ValueTypeDescriptor,
  isScalar: boolean,
  forcedScalarDomain: any[],
  ensureDomain?: NumberRange
): number[];
```

Exemplo:

```typescript
import { axis } from "powerbi-visuals-utils-chartutils";
// ...

var cartesianSeries = [
  {
    data: [
      { categoryValue: 7, value: 11, categoryIndex: 0, seriesIndex: 0 },
      {
        categoryValue: 9,
        value: 9,
        categoryIndex: 1,
        seriesIndex: 0
      },
      {
        categoryValue: 15,
        value: 6,
        categoryIndex: 2,
        seriesIndex: 0
      },
      { categoryValue: 22, value: 7, categoryIndex: 3, seriesIndex: 0 }
    ]
  }
];

axis.getCategoryValueType(
  cartesianSeries,
  ValueType.fromDescriptor({ text: true }),
  false,
  []
);

// returns: [0, 1, 2, 3]
```

### <a name="createaxis"></a>createAxis

Essa função cria um eixo D3, incluindo escala. Ele pode ser vertical ou horizontal e ser do tipo data/hora, numérico ou texto.

```typescript
function createAxis(options: CreateAxisOptions): IAxisProperties;
```

Exemplo:

```typescript
import { axis } from "powerbi-visuals-utils-chartutils";
import { valueFormatter } from "powerbi-visuals-utils-formattingutils";
// ...

var dataPercent = [0.0, 0.33, 0.49];

var formatStringProp: powerbi.DataViewObjectPropertyIdentifier = {
  objectName: "general",
  propertyName: "formatString"
};
let metaDataColumnPercent: powerbi.DataViewMetadataColumn = {
  displayName: "Column",
  type: ValueType.fromDescriptor({ numeric: true }),
  objects: {
    general: {
      formatString: "0 %"
    }
  }
};

var os = axis.createAxis({
  pixelSpan: 100,
  dataDomain: [dataPercent[0], dataPercent[2]],
  metaDataColumn: metaDataColumnPercent,
  formatString: valueFormatter.getFormatString(
    metaDataColumnPercent,
    formatStringProp
  ),
  outerPadding: 0.5,
  isScalar: true,
  isVertical: true
});
```

### <a name="applycustomizeddomain"></a>applyCustomizedDomain

Essa função define o domínio personalizado, mas não é alterada quando nada é definido.

```typescript
function applyCustomizedDomain(customizedDomain, forcedDomain: any[]): any[];
```

Exemplo:

```typescript
import { axis } from "powerbi-visuals-utils-chartutils";
// ...

let customizedDomain = [undefined, 20],
  existingDomain = [0, 10];

axis.applyCustomizedDomain(customizedDomain, existingDomain);

// returns: {0:0, 1:20}
```

### <a name="combinedomain"></a>combineDomain

Essa função combina o domínio forçado com o domínio real se um dos valores foi definido.
O forcedDomain está na primeira prioridade. Estenderá o domínio se qualquer ponto de referência exigir isso.

```typescript
function combineDomain(
  forcedDomain: any[],
  domain: any[],
  ensureDomain?: NumberRange
): any[];
```

Exemplo:

```typescript
import { axis } from "powerbi-visuals-utils-chartutils";
// ...

let forcedYDomain = this.valueAxisProperties
  ? [this.valueAxisProperties["secStart"], this.valueAxisProperties["secEnd"]]
  : null;

let xDomain = [minX, maxX];

axis.combineDomain(forcedYDomain, xDomain, ensureXDomain);
```

### <a name="poweroften"></a>powerOfTen

Essa função indica se o número é uma potência de 10.

```typescript
function powerOfTen(d: any): boolean;
```

Exemplo:

```typescript
import { axis } from "powerbi-visuals-utils-chartutils";
// ...

axis.powerOfTen(10);

// returns: true
```

## <a name="datalabelmanager"></a>DataLabelManager

O `DataLabelManager` ajuda a criar e manter rótulos. Ele organiza os elementos de rótulo usando o ponto de ancoragem ou o retângulo. As colisões podem ser detectadas automaticamente para reposicionar ou ocultar elementos.

A classe `DataLabelManager` fornece os seguintes métodos:

## <a name="hidecollidedlabels"></a>hideCollidedLabels

Esse método organiza a posição dos rótulos e a visibilidade na tela de acordo com os tamanhos e a sobreposição dos rótulos.

```typescript
function hideCollidedLabels(
  viewport: IViewport,
  data: any[],
  layout: any,
  addTransform: boolean = false
): LabelEnabledDataPoint[];
```

Exemplo:

```typescript
let dataLabelManager = new DataLabelManager();
let filteredData = dataLabelManager.hideCollidedLabels(
  this.viewport,
  values,
  labelLayout,
  true
);
```

## <a name="isvalid"></a>IsValid

Esse método estático verifica se o retângulo fornecido é válido (tem largura e altura positivas).

```typescript
function isValid(rect: IRect): boolean;
```

Exemplo:

```typescript
let rectangle = {
  left: 150,
  top: 130,
  width: 120,
  height: 110
};

DataLabelManager.isValid(rectangle);

// returns: true
```

## <a name="datalabelutils"></a>DataLabelUtils

O `DataLabelUtils` fornece utilitários para manipular rótulos de dados.

O módulo fornece as seguintes funções, interfaces e classes:

### <a name="getlabelprecision"></a>getLabelPrecision

Essa função calcula a precisão do formato fornecido.

```typescript
function getLabelPrecision(precision: number, format: string): number;
```

### <a name="getlabelformattedtext"></a>getLabelFormattedText

Essa função retorna a precisão de formato do formato fornecido.

```typescript
function getLabelFormattedText(options: LabelFormattedTextOptions): string;
```

Exemplo:

```typescript
import { dataLabelUtils } from "powerbi-visuals-utils-chartutils";
// ...

let options: LabelFormattedTextOptions = {
  text: "some text",
  fontFamily: "sans",
  fontSize: "15",
  fontWeight: "normal"
};

dataLabelUtils.getLabelFormattedText(options);
```

### <a name="enumeratedatalabels"></a>enumerateDataLabels

Essa função retorna VisualObjectInstance para rótulos de dados.

```typescript
function enumerateDataLabels(
  options: VisualDataLabelsSettingsOptions
): VisualObjectInstance;
```

### <a name="enumeratecategorylabels"></a>enumerateCategoryLabels

Essa função adiciona VisualObjectInstance para rótulos de dados de categoria ao objeto de enumeração.

```typescript
function enumerateCategoryLabels(
  enumeration: VisualObjectInstanceEnumerationObject,
  dataLabelsSettings: VisualDataLabelsSettings,
  withFill: boolean,
  isShowCategory: boolean = false,
  fontSize?: number
): void;
```

### <a name="createcolumnformattercachemanager"></a>createColumnFormatterCacheManager

Essa função retorna o gerenciador de cache que fornece acesso rápido a rótulos formatados

```typescript
function createColumnFormatterCacheManager(): IColumnFormatterCacheManager;
```

Exemplo:

```typescript
import { dataLabelUtils } from "powerbi-visuals-utils-chartutils";
// ...

let value: number = 200000;

labelSettings.displayUnits = 1000000;
labelSettings.precision = 1;

let formattersCache = DataLabelUtils.createColumnFormatterCacheManager();
let formatter = formattersCache.getOrCreate(null, labelSettings);
let formattedValue = formatter.format(value);

// formattedValue == "0.2M"
```

## <a name="legend-service"></a>Serviço de legenda

O serviço de `Legend` fornece interfaces auxiliares para criação e gerenciamento de legendas PBI para visuais personalizados

O módulo fornece as seguintes funções e interfaces:

### <a name="createlegend"></a>createLegend

Essa função auxiliar simplifica a criação de legendas de visuais personalizados do Power BI.

```typescript
function createLegend(
  legendParentElement: HTMLElement, // top visual element, container in which legend will be created
  interactive: boolean, // indicates that legend should be interactive
  interactivityService: IInteractivityService, // reference to IInteractivityService interface which need to create legend click events
  isScrollable: boolean = false, // indicates that legend could be scrollable or not
  legendPosition: LegendPosition = LegendPosition.Top // Position of the legend inside of legendParentElement container
): ILegend;
```

Exemplo:

```typescript
public constructor(options: VisualConstructorOptions) {
    this.visualInitOptions = options;
    this.layers = [];

    var element = this.element = options.element;
    var viewport = this.currentViewport = options.viewport;
    var hostServices = options.host;

    //... some other init calls

    if (this.behavior) {
        this.interactivityService = createInteractivityService(hostServices);
    }
    this.legend = createLegend(
        element,
        options.interactivity && options.interactivity.isInteractiveLegend,
        this.interactivityService,
        true);
}
```

### <a name="ilegend"></a>ILegend

Essa interface implementa todos os métodos necessários para a criação de legenda

```typescript
export interface ILegend {
  getMargins(): IViewport;
  isVisible(): boolean;
  changeOrientation(orientation: LegendPosition): void; // processing legend orientation
  getOrientation(): LegendPosition; // get information about current legend orientation
  drawLegend(data: LegendData, viewport: IViewport); // all legend rendering code is placing here
  /**
   * Reset the legend by clearing it
   */
  reset(): void;
}
```

### <a name="drawlegend"></a>drawLegend

Essa função mede a altura do texto com as propriedades de texto SVG determinadas.

```typescript
function drawLegend(data: LegendData, viewport: IViewport): void;
```

Exemplo:

```typescript
private renderLegend(): void {
    if (!this.isInteractive) {
        let legendObjectProperties = this.data.legendObjectProperties;
        if (legendObjectProperties) {
            let legendData = this.data.legendData;
            LegendData.update(legendData, legendObjectProperties);
            let position = <string>legendObjectProperties[legendProps.position];
            if (position)
                this.legend.changeOrientation(LegendPosition[position]);

            this.legend.drawLegend(legendData, this.parentViewport);
        } else {
            this.legend.changeOrientation(LegendPosition.Top);
            this.legend.drawLegend({ dataPoints: [] }, this.parentViewport);
        }
    }
}
```

## <a name="next-steps"></a>Próximas etapas

- [Leia como usar InteractivityUtils para adicionar seleções nos visuais do Power BI](utils-interactivity-selections.md)
