---
title: API de filtros visuais
description: Como visuais do Power BI podem filtrar outros visuais
author: sranins
ms.author: rasala
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 50e9601faf497675ebc3f24609a856a600e3bcb1
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68425035"
---
# <a name="power-bi-visual-filters-api"></a>API de filtros visuais do Power BI

A filtragem de visuais permite a filtragem de dados. A principal diferença das seleções é que outros visuais serão filtrados de qualquer modo, apesar do suporte a destaque por outro visual.

Para habilitar a filtragem para o visual, o visual em questão deve conter o objeto `filter` na seção `general` do conteúdo de capabilities.json.

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

As interfaces de API de filtro estão disponíveis no pacote [`powerbi-models`](https://www.npmjs.com/package/powerbi-models). O pacote também contém classes para criar instâncias de filtro.

```cmd
npm install powerbi-models --save
```

Se usar as ferramentas de versão antigas (versão inferior a 3.x.x), você deverá incluir `powerbi-models` no pacote de visuais. [Guia resumido de como incluir o pacote](https://github.com/Microsoft/powerbi-visuals-sampleslicer/blob/master/doc/AddingAdvancedFilterAPI.md)

Todos os filtros estendem a interface `IFilter`.

```typescript
export interface IFilter {
    $schema: string;
    target: IFilterTarget;
}
```

`target` – é uma coluna de tabela na fonte de dados.

## <a name="basic-filter-api"></a>API de filtro básico

A interface de filtro básico é

```typescript
export interface IBasicFilter extends IFilter {
    operator: BasicFilterOperators;
    values: (string | number | boolean)[];
}
```

`operator` – é enumeração com os valores "In", "NotIn", "All"

`values` – são valores para condição

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

O filtro significa "informe todas as linhas em que `col1` é igual a um dos valores 1, 2 ou 3".

O equivalente SQL é

```sql
SELECT * FROM table WHERE col1 IN ( 1 , 2 , 3 )
```

Para criar um filtro, você pode usar a classe BasicFilter em `powerbi-models`.

Se você usar a versão antiga das ferramentas, deverá obter uma instância de modelos no objeto window por `window['powerbi-models']`:

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

## <a name="advanced-filter-api"></a>API de filtro avançado

A [API de Filtro Avançado](https://github.com/Microsoft/powerbi-models) permite consultas complexas de filtragem/seleção de pontos de dados entre visuais com base em vários critérios (como "LessThan", "Contains", "Is", "IsBlank" e assim por diante).

O filtro foi introduzido na API de visuais 1.7.0.

A API de Filtro Avançado também requer `target` com `table` e o nome `column`. Mas os operadores de API de Filtro Avançado são `"And" | "Or"`. 

Além disso, o filtro usa condições em vez de valores com interface:

```typescript
interface IAdvancedFilterCondition {
    value: (string | number | boolean);
    operator: AdvancedFilterConditionOperators;
}
```

Os operadores de condição para o parâmetro `operator` são `"None" | "LessThan" | "LessThanOrEqual" | "GreaterThan" | "GreaterThanOrEqual" | "Contains" | "DoesNotContain" | "StartsWith" | "DoesNotStartWith" | "Is" | "IsNot" | "IsBlank" | "IsNotBlank"`

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

O equivalente SQL é

```sql
SELECT * FROM table WHERE col1 < 0;
```

O código de exemplo completo de uso da API de Filtro Avançado pode ser encontrado no [repositório `Sampleslicer visual`](https://github.com/Microsoft/powerbi-visuals-sampleslicer).

## <a name="tuple-filter-api-multi-column-filter"></a>API de filtro de tupla (filtro de várias colunas)

A API de filtro de tupla foi introduzida na API de visuais 2.3.0.

A API de filtro de tupla é semelhante à de filtro básico, mas permite definir condições para várias colunas e tabelas.

E um filtro tem a interface: 

```typescript
interface ITupleFilter extends IFilter {
    $schema: string;
    filterType: FilterType;
    operator: TupleFilterOperators;
    target: ITupleFilterTarget;
    values: TupleValueType[];
}
```

`target` é uma matriz de colunas com nomes de tabela:

```typescript
declare type ITupleFilterTarget = IFilterTarget[];
```

  O filtro pode endereçar colunas de tabelas diferentes.

`$schema` é "http://powerbi.com/product/schema#tuple"

`filterType` é `FilterType.Tuple`

`operator` permite somente o uso do operador `"In"`

`values` é uma matriz de tuplas de valor, em que cada tupla representa uma combinação permitida dos valores da coluna de destino 

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
        // the 1st column combination value (aka column tuple/vector value) that the filter will pass through
        {
            value: "Team1" // the value for `Team` column of `DataTable` table
        },
        {
            value: 5 // the value for `Value` column of `DataTable` table
        }
    ],
    [
        // the 2nd column combination value (aka column tuple/vector value) that the filter will pass through
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

**A ordem dos nomes de coluna e os valores de condição são confidenciais.**

O equivalente SQL é

```sql
SELECT * FROM DataTable WHERE ( Team = "Team1" AND Value = 5 ) OR ( Team = "Team2" AND Value = 6 );
```  

## <a name="restoring-json-filter-from-dataview"></a>Como restaurar o filtro JSON do DataView

Começando na API 2.2, os **filtros JSON** podem ser restaurados de **VisualUpdateOptions**

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

O Power BI chama o método `update` do visual quando usa indicadores de alternância e o visual obtém o objeto `filter` correspondente.
[Leia mais sobre o suporte a indicadores](bookmarks-support.md)

### <a name="sample-json-filter"></a>Filtro JSON de exemplo

![Filtro JSON de captura de tela](./media/json-filter.png)

### <a name="clear-json-filter"></a>Limpar filtro JSON

A API de filtro aceita o valor de filtro `null` como redefinido ou limpo.

```typescript
// invoke the filter
visualHost.applyJsonFilter(null, "general", "filter", FilterAction.merge);
```
