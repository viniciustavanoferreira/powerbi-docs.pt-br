---
title: A API de Filtros Visuais em visuais do Power BI
description: Este artigo discute como visuais do Power BI podem filtrar outros visuais.
author: sranins
ms.author: rasala
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: fc0b21116888c8455d4d7b8efc5c476bfc592483
ms.sourcegitcommit: b602cdffa80653bc24123726d1d7f1afbd93d77c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70237116"
---
# <a name="the-visual-filters-api-in-power-bi-visuals"></a>A API de Filtros Visuais em visuais do Power BI

A API de Filtros Visuais permite filtrar dados em visuais do Power BI. A principal diferença de outras seleções é que outros visuais serão filtrados de qualquer modo, apesar do suporte a realce por outro visual.

Para habilitar a filtragem para o visual, o visual em questão deve conter o objeto `filter` na seção `general` do código *capabilities.json*.

```json
"objects": {
        "general": {
            "displayName": "General",
            "displayNameKey": "formattingGeneral",
            "properties": {
                "filter": {
                    "type": {
                        "filter": true
                    }
                }
            }
        }
    }
```

As interfaces da API de Filtros Visuais estão disponíveis no pacote [powerbi-models](https://www.npmjs.com/package/powerbi-models). O pacote também contém classes para criar instâncias de filtro.

```cmd
npm install powerbi-models --save
```

Se você usar uma versão mais antiga (anterior à 3.x.x) das ferramentas, deverá incluir `powerbi-models` no pacote de visuais. Para obter mais informações, confira o guia breve [Adicionar a API de filtro avançado ao visual personalizado](https://github.com/Microsoft/powerbi-visuals-sampleslicer/blob/master/doc/AddingAdvancedFilterAPI.md).

Todos os filtros estendem a interface `IFilter`, conforme mostrado no código a seguir:

```typescript
export interface IFilter {
    $schema: string;
    target: IFilterTarget;
}
```
Em que:
* `target` é a coluna da tabela na fonte de dados.

## <a name="the-basic-filter-api"></a>A API do filtro básico

A interface do filtro básico é mostrada no código a seguir:

```typescript
export interface IBasicFilter extends IFilter {
    operator: BasicFilterOperators;
    values: (string | number | boolean)[];
}
```

Em que:
* `operator` é uma enumeração com os valores *In*, *NotIn* e *All*.
* `values` são valores para a condição.

Exemplo de filtro básico:

```typescript
let basicFilter = {
    target: {
        column: "Col1"
    },
    operator: "In",
    values: [1,2,3]
}
```

O filtro significa "Informe todas as linhas em que `col1` é igual a um dos valores 1, 2 ou 3".

O equivalente SQL é:

```sql
SELECT * FROM table WHERE col1 IN ( 1 , 2 , 3 )
```

Para criar um filtro, você pode usar a classe BasicFilter em `powerbi-models`.

Se você usar uma versão mais antiga da ferramenta, deverá obter uma instância de modelos no objeto de janela usando `window['powerbi-models']`, conforme mostrado no código a seguir:

```javascript
let categories: DataViewCategoricalColumn = this.dataView.categorical.categories[0];

let target: IFilterColumnTarget = {
    table: categories.source.queryName.substr(0, categories.source.queryName.indexOf('.')),
    column: categories.source.displayName
};

let values = [ 1, 2, 3 ];

let filter: IBasicFilter = new window['powerbi-models'].BasicFilter(target, "In", values);
```

O visual invoca o filtro usando o método applyJsonFilter() na interface de host IVisualHost fornecida para o visual no construtor.

```typescript
visualHost.applyJsonFilter(filter, "general", "filter", FilterAction.merge);
```

## <a name="the-advanced-filter-api"></a>A API de Filtro Avançado

A [API de Filtro Avançado](https://github.com/Microsoft/powerbi-models) permite consultas complexas de filtragem e seleção de pontos de dados entre visuais com base em vários critérios (como *LessThan*, *Contains*, *Is*, *IsBlank* e assim por diante).

O filtro foi introduzido na API de visuais 1.7.0.

A API de Filtro Avançado também requer `target` com `table` e o nome `column`. Porém, os operadores de API de Filtro Avançado são *E* e *Ou*. 

Além disso, o filtro usa condições em vez de valores com interface:

```typescript
interface IAdvancedFilterCondition {
    value: (string | number | boolean);
    operator: AdvancedFilterConditionOperators;
}
```

Os operadores de condição para o parâmetro `operator` são *None*, *LessThan*, *LessThanOrEqual*, *GreaterThan*, *GreaterThanOrEqual*, *Contains*, *DoesNotContain*, *StartsWith*, *DoesNotStartWith*, *Is*, *IsNot*, *IsBlank* e "IsNotBlank"`

```javascript
let categories: DataViewCategoricalColumn = this.dataView.categorical.categories[0];

let target: IFilterColumnTarget = {
    table: categories.source.queryName.substr(0, categories.source.queryName.indexOf('.')), // table
    column: categories.source.displayName // col1
};

let conditions: IAdvancedFilterCondition[] = [];

conditions.push({
    operator: "LessThan",
    value: 0
});

let filter: IAdvancedFilter = new window['powerbi-models'].AdvancedFilter(target, "And", conditions);

// invoke the filter
visualHost.applyJsonFilter(filter, "general", "filter", FilterAction.merge);
```

O equivalente SQL é:

```sql
SELECT * FROM table WHERE col1 < 0;
```

Para obter o código de exemplo completo para usar a API de Filtro Avançado, acesse o [repositório do visual Sampleslicer](https://github.com/Microsoft/powerbi-visuals-sampleslicer).

## <a name="the-tuple-filter-api-multi-column-filter"></a>A API de Filtro de Tupla (filtro de várias colunas)

A API de filtro de tupla foi introduzida na API de visuais 2.3.0. É semelhante à API de Filtro Básico, mas permite definir condições para várias colunas e tabelas.

A interface de filtro é mostrada no código a seguir: 

```typescript
interface ITupleFilter extends IFilter {
    $schema: string;
    filterType: FilterType;
    operator: TupleFilterOperators;
    target: ITupleFilterTarget;
    values: TupleValueType[];
}
```

Em que:
* `target` é uma matriz de colunas com nomes de tabela:

    ```typescript
    declare type ITupleFilterTarget = IFilterTarget[];
    ```

  O filtro pode endereçar colunas de várias tabelas.

* `$schema` é http://powerbi.com/product/schema#tuple.

* `filterType` é *FilterType.Tuple*.

* `operator` permite usar somente no operador *In*.

* `values` é uma matriz de tuplas de valor e cada tupla representa uma combinação permitida dos valores da coluna de destino. 

```typescript
declare type TupleValueType = ITupleElementValue[];

interface ITupleElementValue {
    value: PrimitiveValueType
}
```

Exemplo completo:

```typescript
let target: ITupleFilterTarget = [
    {
        table: "DataTable",
        column: "Team"
    },
    {
        table: "DataTable",
        column: "Value"
    }
];

let values = [
    [
        // the first column combination value (or the column tuple/vector value) that the filter will pass through
        {
            value: "Team1" // the value for the `Team` column of the `DataTable` table
        },
        {
            value: 5 // the value for the `Value` column of the `DataTable` table
        }
    ],
    [
        // the second column combination value (or the column tuple/vector value) that the filter will pass through
        {
            value: "Team2" // the value for `Team` column of `DataTable` table
        },
        {
            value: 6 // the value for `Value` column of `DataTable` table
        }
    ]
];

let filter: ITupleFilter = {
    $schema: "http://powerbi.com/product/schema#tuple",
    filterType: FilterType.Tuple,
    operator: "In",
    target: target,
    values: values
}

// invoke the filter
visualHost.applyJsonFilter(filter, "general", "filter", FilterAction.merge);
```

> [!IMPORTANT]
> A ordem dos nomes de coluna e dos valores de condição é sensível.

O equivalente SQL é:

```sql
SELECT * FROM DataTable WHERE ( Team = "Team1" AND Value = 5 ) OR ( Team = "Team2" AND Value = 6 );
```  

## <a name="restore-the-json-filter-from-the-data-view"></a>Restaurar o filtro JSON da exibição de dados

Da API versão 2.2 em diante, você pode restaurar o filtro JSON de *VisualUpdateOptions*, conforme mostrado no código a seguir:

```typescript
export interface VisualUpdateOptions extends extensibility.VisualUpdateOptions {
    viewport: IViewport;
    dataViews: DataView[];
    type: VisualUpdateType;
    viewMode?: ViewMode;
    editMode?: EditMode;
    operationKind?: VisualDataChangeOperationKind;
    jsonFilters?: IFilter[];
}
```

Quando você alterna, indicadores, o Power BI chama o método `update` do visual e o visual obtém um objeto `filter` correspondente. Para obter mais informações, confira [Adicionar suporte a indicador para visuais do Power BI](bookmarks-support.md).

### <a name="sample-json-filter"></a>Exemplo de filtro JSON

Alguns exemplos de código de filtro JSON são mostrados na imagem a seguir:

![Código de filtro JSON](./media/json-filter.png)

### <a name="clear-the-json-filter"></a>Limpar o filtro JSON

A API de filtro aceita o valor `null` do filtro como *redefinir* ou *limpar*.

```typescript
// invoke the filter
visualHost.applyJsonFilter(null, "general", "filter", FilterAction.merge);
```
