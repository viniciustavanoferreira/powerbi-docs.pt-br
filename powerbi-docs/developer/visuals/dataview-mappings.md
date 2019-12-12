---
title: Entender o mapeamento de exibição de dados em visuais do Power BI
description: Este artigo descreve como o Power BI transforma os dados antes de passá-los para elementos visuais.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: b50ebde94d78ca42437979d792fb6402affe8855
ms.sourcegitcommit: f77b24a8a588605f005c9bb1fdad864955885718
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2019
ms.locfileid: "74696590"
---
# <a name="understand-data-view-mapping-in-power-bi-visuals"></a>Entender o mapeamento de exibição de dados em visuais do Power BI

Este artigo aborda o mapeamento de exibição de dados e descreve como as funções de dados se relacionam entre si e permitem que você especifique requisitos condicionais para elas. O artigo também descreve cada tipo `dataMappings`.

Cada mapeamento válido produz uma exibição de dados, mas atualmente há suporte para executar apenas uma consulta por visual. Normalmente, você obtém apenas uma exibição de dados. No entanto, você pode fornecer vários mapeamentos de dados com diferentes condições, que permitem:

```json
"dataViewMappings": [
    {
        "conditions": [ ... ],
        "categorical": { ... },
        "single": { ... },
        "table": { ... },
        "matrix": { ... }
    }
]
```

O Power BI criará um mapeamento para uma exibição de dados se e somente se o mapeamento válido estiver preenchido em `dataViewMappings`.

Em outras palavras, `categorical` pode ser definido em `dataViewMappings`, mas outros mapeamentos, como `table` ou `single`, podem não ser. Por exemplo:

```json
"dataViewMappings": [
    {
        "categorical": { ... }
    }
]
```

O Power BI produz uma exibição de dados com um único mapeamento `categorical` e `table` e outros mapeamentos são indefinidos:

```javascript
{
    "categorical": {
        "categories": [ ... ],
        "values": [ ... ]
    },
    "metadata": { ... }
}
```

## <a name="conditions"></a>Condições

Esta seção descreve as condições para um mapeamento de dados específico. Você poderá fornecer vários conjuntos de condições e, se os dados corresponderem a um dos conjuntos de condições descritos, o visual aceitará os dados como válidos.

No momento, para cada campo, você pode especificar um valor mínimo e um máximo. O valor representa o número de campos que podem ser associados a essa função de dados. 

> [!NOTE]
> Se uma função de dados for omitida na condição, ela poderá ter qualquer número de campos.

### <a name="example-1"></a>Exemplo 1

Você pode arrastar vários campos para cada função de dados. Neste exemplo, você limita a categoria a um campo de dados e a medida, a dois campos de dados.

```json
"conditions": [
    { "category": { "max": 1 }, "y": { "max": 2 } },
]
```

### <a name="example-2"></a>Exemplo 2

Neste exemplo, é exigida uma das duas condições:
* Exatamente um campo de dados de categoria e exatamente duas medidas
* Exatamente duas categorias e exatamente uma medida.

```json
"conditions": [
    { "category": { "min": 1, "max": 1 }, "measure": { "min": 2, "max": 2 } },
    { "category": { "min": 2, "max": 2 }, "measure": { "min": 1, "max": 1 } }
]
```

## <a name="single-data-mapping"></a>Mapeamento de dados único

O mapeamento de dados único é a forma mais simples de mapeamento de dados. Ele aceita um único campo measure e fornece o total. Se o campo for numérico, ele fornecerá a soma. Caso contrário, ele fornecerá uma contagem de valores exclusivos.

Para usar o mapeamento de dados único, você precisa definir o nome da função de dados que deseja mapear. Esse mapeamento funciona apenas com um único campo de medida. Se um segundo campo for atribuído, nenhuma exibição de dados será gerada, portanto, também é uma boa prática incluir uma condição que limite os dados a um único campo.

> [!NOTE]
> Esse mapeamento de dados não pode ser usado junto com nenhum outro mapeamento de dados. Ele se destina a reduzir os dados a um valor numérico single.

### <a name="example-3"></a>Exemplo 3

```json
{
    "dataRoles": [
        {
            "displayName": "Y",
            "name": "Y",
            "kind": "Measure"
        }
    ],
    "dataViewMappings": [
        {
            "conditions": [
                {
                    "Y": {
                        "max": 1
                    }
                }
            ],
            "single": {
                "role": "Y"
            }
        }
    ]
}
```

A exibição de dados resultante ainda contém os outros tipos (tabela, categórico etc.), mas cada mapeamento contém apenas o valor único. A prática recomendada é acessar o valor somente no formato único.

```JSON
{
    "dataView": [
        {
            "metadata": null,
            "categorical": null,
            "matrix": null,
            "table": null,
            "tree": null,
            "single": {
                "value": 94163140.3560001
            }
        }
    ]
}
```

Exemplo de código para processar o mapeamento de exibição de dados simples

```typescript
"use strict";
import powerbi from "powerbi-visuals-api";
import DataView = powerbi.DataView;
import DataViewSingle = powerbi.DataViewSingle;
// standart imports
// ...

export class Visual implements IVisual {
    private target: HTMLElement;
    private host: IVisualHost;
    private valueText: HTMLParagraphElement;

    constructor(options: VisualConstructorOptions) {
        // constructor body
        this.target = options.element;
        this.host = options.host;
        this.valueText = document.createElement("p");
        this.target.appendChild(this.valueText);
        // ...
    }

    public update(options: VisualUpdateOptions) {
        const dataView: DataView = options.dataViews[0];
        const singleDataView: DataViewSingle = dataView.single;

        if (!singleDataView ||
            !singleDataView.value ) {
            return
        }

        this.valueText.innerText = singleDataView.value.toString();
    }
}
```

Como resultado, o visual exibe um único valor do Power BI:

![Exemplo de visual de mapeamento de exibição de dados única](./media/visual-simple-dataview-mapping.png)

## <a name="categorical-data-mapping"></a>Mapeamento de dados categóricos

O mapeamento de dados categóricos é usado para obter um ou dois agrupamentos independentes de dados.

### <a name="example-4"></a>Exemplo 4

Aqui está a definição do exemplo anterior para funções de dados:

```json
"dataRole":[
    {
        "displayName": "Category",
        "name": "category",
        "kind": "Grouping"
    },
    {
        "displayName": "Y Axis",
        "name": "measure",
        "kind": "Measure"
    }
]
```

Aqui está o mapeamento:

```json
"dataViewMappings": {
    "categorical": {
        "categories": {
            "for": { "in": "category" }
        },
        "values": {
            "select": [
                { "bind": { "to": "measure" } }
            ]
        }
    }
}
```

É um exemplo simples. Ele diz: "Mapear minha função de dados `category` para que cada campo que eu arrasto para `category` seja mapeado para `categorical.categories`. Mapear também a minha função de dados `measure` para `categorical.values`."

* **for...in**: para todos os itens nesta função de dados, inclua-os na consulta de dados.
* **bind...to**: produz o mesmo resultado que *for...in*, mas espera que a função de dados tenha uma condição que a restrinja a um campo único.

### <a name="example-5"></a>Exemplo 5

Este exemplo usa as duas primeiras funções de dados do exemplo anterior e, além disso, define `grouping` e `measure2`.

```json
"dataRole":[
    {
        "displayName": "Category",
        "name": "category",
        "kind": "Grouping"
    },
    {
        "displayName": "Y Axis",
        "name": "measure",
        "kind": "Measure"
    },
    {
        "displayName": "Grouping with",
        "name": "grouping",
        "kind": "Grouping"
    },
    {
        "displayName": "X Axis",
        "name": "measure2",
        "kind": "Grouping"
    }
]
```

Aqui está o mapeamento:

```json
"dataViewMappings":{
    "categorical": {
        "categories": {
            "for": { "in": "category" }
        },
        "values": {
            "group": {
                "by": "grouping",
                "select":[
                    { "bind": { "to": "measure" } },
                    { "bind": { "to": "measure2" } }
                ]
            }
        }
    }
}
```

Aqui, a diferença está em como mapeamos valores categóricos. Estamos dizendo que "Mapear minhas funções de dados `measure` e `measure2` a serem agrupadas pela função de dados `grouping`".

### <a name="example-6"></a>Exemplo 6

Aqui estão as funções de dados:

```json
"dataRoles": [
    {
        "displayName": "Categories",
        "name": "category",
        "kind": "Grouping"
    },
    {
        "displayName": "Measures",
        "name": "measure",
        "kind": "Measure"
    },
    {
        "displayName": "Series",
        "name": "series",
        "kind": "Measure"
    }
]
```

Aqui está o mapeamento de exibição de dados:

```json
"dataViewMappings": [
    {
        "categorical": {
            "categories": {
                "for": {
                    "in": "category"
                }
            },
            "values": {
                "group": {
                    "by": "series",
                    "select": [{
                            "for": {
                                "in": "measure"
                            }
                        }
                    ]
                }
            }
        }
    }
]
```

A exibição de dados categóricos poderia ser visualizada desta forma:

| Categórica |  |  | | | |
|-----|-----|------|------|------|------|
| | Ano | 2013 | 2014 | 2015 | 2016 |
| País | | |
| EUA | | x | x | 650 | 350 |
| Canadá | | x | 630 | 490 | x |
| México | | 645 | x | x | x |
| REINO UNIDO | | x | x | 831 | x |

O Power BI a produz como a exibição de dados categóricos. É o conjunto de categorias.

```JSON
{
    "categorical": {
        "categories": [
            {
                "source": {...},
                "values": [
                    "Canada",
                    "USA",
                    "UK",
                    "Mexico"
                ],
                "identity": [...],
                "identityFields": [...],
            }
        ]
    }
}
```

Cada categoria é mapeada também para um conjunto de valores. Cada um desses valores é agrupado por série, que é expressa em anos.

Por exemplo, cada matriz de `values` representa dados de cada ano.
Além disso, cada matriz de `values` tem quatro valores, referentes ao Canadá, aos EUA, ao Reino Unido e ao México, respectivamente:

```JSON
{
    "values": [
        // Values for 2013 year
        {
            "source": {...},
            "values": [
                null, // Value for `Canada` category
                null, // Value for `USA` category
                null, // Value for `UK` category
                645 // Value for `Mexico` category
            ],
            "identity": [...],
        },
        // Values for 2014 year
        {
            "source": {...},
            "values": [
                630, // Value for `Canada` category
                null, // Value for `USA` category
                null, // Value for `UK` category
                null // Value for `Mexico` category
            ],
            "identity": [...],
        },
        // Values for 2015 year
        {
            "source": {...},
            "values": [
                490, // Value for `Canada` category
                650, // Value for `USA` category
                831, // Value for `UK` category
                null // Value for `Mexico` category
            ],
            "identity": [...],
        },
        // Values for 2016 year
        {
            "source": {...},
            "values": [
                null, // Value for `Canada` category
                350, // Value for `USA` category
                null, // Value for `UK` category
                null // Value for `Mexico` category
            ],
            "identity": [...],
        }
    ]
}
```

O exemplo de código para processar o mapeamento de exibição de dados categóricos é descrito abaixo. O exemplo cria a estrutura hierárquica `Country => Year => Value`

```typescript
"use strict";
import powerbi from "powerbi-visuals-api";
import DataView = powerbi.DataView;
import DataViewDataViewCategoricalSingle = powerbi.DataViewCategorical;
import DataViewValueColumnGroup = powerbi.DataViewValueColumnGroup;
import PrimitiveValue = powerbi.PrimitiveValue;
// standart imports
// ...

export class Visual implements IVisual {
    private target: HTMLElement;
    private host: IVisualHost;
    private categories: HTMLElement;

    constructor(options: VisualConstructorOptions) {
        // constructor body
        this.target = options.element;
        this.host = options.host;
        this.categories = document.createElement("pre");
        this.target.appendChild(this.categories);
        // ...
    }

    public update(options: VisualUpdateOptions) {
        const dataView: DataView = options.dataViews[0];
        const categoricalDataView: DataViewCategorical = dataView.categorical;

        if (!categoricalDataView ||
            !categoricalDataView.categories ||
            !categoricalDataView.categories[0] ||
            !categoricalDataView.values) {
            return;
        }

        // Categories have only one column in data buckets
        // If you want to support several columns of categories data bucket, you should iterate categoricalDataView.categories array.
        const categoryFieldIndex = 0;
        // Measure has only one column in data buckets.
        // If you want to support several columns on data bucket, you should iterate years.values array in map function
        const measureFieldIndex = 0;
        let categories: PrimitiveValue[] = categoricalDataView.categories[categoryFieldIndex].values;
        let values: DataViewValueColumnGroup[] = categoricalDataView.values.grouped();

        let data = {};
        // iterate categories/countries
        categories.map((category: PrimitiveValue, categoryIndex: number) => {
            data[category.toString()] = {};
            // iterate series/years
            values.map((years: DataViewValueColumnGroup) => {
                if (!data[category.toString()][years.name] && years.values[measureFieldIndex].values[categoryIndex]) {
                    data[category.toString()][years.name] = []
                }
                if (years.values[0].values[categoryIndex]) {
                    data[category.toString()][years.name].push(years.values[measureFieldIndex].values[categoryIndex]);
                }
            });
        });

        this.categories.innerText = JSON.stringify(data, null, 6);
        console.log(data);
    }
}
```

O resultado do visual:

![O visual com mapeamento categórico de exibição de dados](./media/categorical-data-view-mapping-visual.png)

## <a name="table-data-mapping"></a>Mapeamento de dados de tabela

A exibição de dados de tabela é um mapeamento de dados simples. Essencialmente, é uma lista de pontos de dados em que pontos de dados numéricos podem ser agregados.

### <a name="example-7"></a>Exemplo 7

Com as funcionalidades fornecidas:

```json
"dataRoles": [
    {
        "displayName": "Column",
        "name": "column",
        "kind": "Measure"
    },
    {
        "displayName": "Value",
        "name": "value",
        "kind": "Measure"
    }
]
```

```json
"dataViewMappings": [
    {
        "table": {
            "rows": {
                "select": [
                    {
                        "for": {
                            "in": "column"
                        }
                    },
                    {
                        "for": {
                            "in": "value"
                        }
                    }
                ]
            }
        }
    }
]
```

Você pode visualizar a exibição de dados da tabela como segue:  

Exemplo de dados:

| País| Ano | Vendas |
|-----|-----|------|
| EUA | 2016 | 100 |
| EUA | 2015 | 50 |
| Canadá | 2015 | 200 |
| Canadá | 2015 | 50 |
| México | 2013 | 300 |
| REINO UNIDO | 2014 | 150 |
| EUA | 2015 | 75 |

Associação de dados:

![Associações de dados do mapeamento de exibição de dados de tabela](./media/table-dataview-mapping-data.png)

O Power BI exibe os dados como a exibição de dados da tabela. Você não deve presumir que os dados sejam ordenados.

```JSON
{
    "table" : {
        "columns": [...],
        "rows": [
            [
                "Canada",
                2014,
                630
            ],
            [
                "Canada",
                2015,
                490
            ],
            [
                "Mexico",
                2013,
                645
            ],
            [
                "UK",
                2014,
                831
            ],
            [
                "USA",
                2015,
                650
            ],
            [
                "USA",
                2016,
                350
            ]
        ]
    }
}
```

Você pode agregar os dados selecionando o campo desejado e, em seguida, selecionando soma.  

![Agregação de dados](./media/data-aggregation.png)

Exemplo de código para processar o mapeamento de exibição de dados de tabela.

```typescript
"use strict";
import "./../style/visual.less";
import powerbi from "powerbi-visuals-api";
// ...
import DataViewMetadataColumn = powerbi.DataViewMetadataColumn;
import DataViewTable = powerbi.DataViewTable;
import DataViewTableRow = powerbi.DataViewTableRow;
import PrimitiveValue = powerbi.PrimitiveValue;
// other imports
// ...

export class Visual implements IVisual {
    private target: HTMLElement;
    private host: IVisualHost;
    private table: HTMLParagraphElement;

    constructor(options: VisualConstructorOptions) {
        // constructor body
        this.target = options.element;
        this.host = options.host;
        this.table = document.createElement("table");
        this.target.appendChild(this.table);
        // ...
    }

    public update(options: VisualUpdateOptions) {
        const dataView: DataView = options.dataViews[0];
        const tableDataView: DataViewTable = dataView.table;

        if (!tableDataView) {
            return
        }
        while(this.table.firstChild) {
            this.table.removeChild(this.table.firstChild);
        }

        //draw header
        const tableHeader = document.createElement("th");
        tableDataView.columns.forEach((column: DataViewMetadataColumn) => {
            const tableHeaderColumn = document.createElement("td");
            tableHeaderColumn.innerText = column.displayName
            tableHeader.appendChild(tableHeaderColumn);
        });
        this.table.appendChild(tableHeader);

        //draw rows
        tableDataView.rows.forEach((row: DataViewTableRow) => {
            const tableRow = document.createElement("tr");
            row.forEach((columnValue: PrimitiveValue) => {
                const cell = document.createElement("td");
                cell.innerText = columnValue.toString();
                tableRow.appendChild(cell);
            })
            this.table.appendChild(tableRow);
        });
    }
}
```

O arquivo de estilos visuais `style/visual.less` contém o layout da tabela:

```less
table {
    display: flex;
    flex-direction: column;
}

tr, th {
    display: flex;
    flex: 1;
}

td {
    flex: 1;
    border: 1px solid black;
}
```

![O visual com mapeamento de exibição de dados de tabela](./media/table-dataview-mapping-visual.png)

## <a name="matrix-data-mapping"></a>Mapeamento de dados de matriz

O mapeamento de dados de matriz é semelhante ao mapeamento de dados de tabela, mas as linhas são apresentadas hierarquicamente. Qualquer um dos valores de função de dados pode ser usado como um valor de cabeçalho de coluna.

```json
{
    "dataRoles": [
        {
            "name": "Category",
            "displayName": "Category",
            "displayNameKey": "Visual_Category",
            "kind": "Grouping"
        },
        {
            "name": "Column",
            "displayName": "Column",
            "displayNameKey": "Visual_Column",
            "kind": "Grouping"
        },
        {
            "name": "Measure",
            "displayName": "Measure",
            "displayNameKey": "Visual_Values",
            "kind": "Measure"
        }
    ],
    "dataViewMappings": [
        {
            "matrix": {
                "rows": {
                    "for": {
                        "in": "Category"
                    }
                },
                "columns": {
                    "for": {
                        "in": "Column"
                    }
                },
                "values": {
                    "select": [
                        {
                            "for": {
                                "in": "Measure"
                            }
                        }
                    ]
                }
            }
        }
    ]
}
```

O Power BI cria uma estrutura de dados hierárquica. A raiz da hierarquia de árvore inclui os dados da coluna **Pais** da função de dados `Category`, com filhos da coluna **Filhos** da tabela de função de dados.

Conjunto de dados:

| Pais | Filhos | Netos | Colunas | Valores |
|-----|-----|------|-------|-------|
| Pai1 | Filho1 | Neto1 | Col1 | 5 |
| Pai1 | Filho1 | Neto1 | Col2 | 6 |
| Pai1 | Filho1 | Neto2 | Col1 | 7 |
| Pai1 | Filho1 | Neto2 | Col2 | 8 |
| Pai1 | Filho2 | Neto3 | Col1 | 5 |
| Pai1 | Filho2 | Neto3 | Col2 | 3 |
| Pai1 | Filho2 | Neto4 | Col1 | 4 |
| Pai1 | Filho2 | Neto4 | Col2 | 9 |
| Pai1 | Filho2 | Neto5 | Col1 | 3 |
| Pai1 | Filho2 | Neto5 | Col2 | 5 |
| Pai2 | Filho3 | Neto6 | Col1 | 1 |
| Pai2 | Filho3 | Neto6 | Col2 | 2 |
| Pai2 | Filho3 | Neto7 | Col1 | 7 |
| Pai2 | Filho3 | Neto7 | Col2 | 1 |
| Pai2 | Filho3 | Neto8 | Col1 | 10 |
| Pai2 | Filho3 | Neto8 | Col2 | 13 |

O visual de matriz principal do Power BI renderiza os dados como uma tabela.

![Matrix visual](./media/matrix-visual-smaple.png)

O visual obtém sua estrutura de dados conforme descrito no código a seguir (somente as duas primeiras linhas da tabela são mostradas aqui):

```json
{
    "metadata": {...},
    "matrix": {
        "rows": {
            "levels": [...],
            "root": {
                "childIdentityFields": [...],
                "children": [
                    {
                        "level": 0,
                        "levelValues": [...],
                        "value": "Parent1",
                        "identity": {...},
                        "childIdentityFields": [...],
                        "children": [
                            {
                                "level": 1,
                                "levelValues": [...],
                                "value": "Child1",
                                "identity": {...},
                                "childIdentityFields": [...],
                                "children": [
                                    {
                                        "level": 2,
                                        "levelValues": [...],
                                        "value": "Grand child1",
                                        "identity": {...},
                                        "values": {
                                            "0": {
                                                "value": 5 // value for Col1
                                            },
                                            "1": {
                                                "value": 6 // value for Col2
                                            }
                                        }
                                    },
                                    ...
                                ]
                            },
                            ...
                        ]
                    },
                    ...
                ]
            }
        },
        "columns": {
            "levels": [...],
            "root": {
                "childIdentityFields": [...],
                "children": [
                    {
                        "level": 0,
                        "levelValues": [...],
                        "value": "Col1",
                        "identity": {...}
                    },
                    {
                        "level": 0,
                        "levelValues": [...],
                        "value": "Col2",
                        "identity": {...}
                    },
                    ...
                ]
            }
        },
        "valueSources": [...]
    }
}
```

## <a name="data-reduction-algorithm"></a>Algoritmo de redução de dados

Para controlar a quantidade de dados a serem recebidos na exibição de dados, você pode aplicar um algoritmo de redução de dados.

Por padrão, todos os visuais do Power BI têm o algoritmo de redução de dados principal aplicado com *count* definida como 1000 pontos de dados. Isso é o mesmo que definir as seguintes propriedades no arquivo *capabilities.json*:

```json
"dataReductionAlgorithm": {
    "top": {
        "count": 1000
    }
}
```

Você pode modificar o valor de *count* para qualquer valor inteiro até 30.000. Os visuais do Power BI baseados em R podem dar suporte a até 150000 linhas.

## <a name="data-reduction-algorithm-types"></a>Tipos de algoritmo de redução de dados

Há quatro tipos de configurações de algoritmo de redução de dados:

* `top`: se você quiser limitar os dados a valores extraídos da parte superior do conjunto de dados. Os primeiros valores de *count* serão obtidos do conjunto de dados.
* `bottom`: se você quiser limitar os dados a valores extraídos da parte inferior do conjunto de dados. Os últimos valores de "count" serão obtidos do conjunto de dados.
* `sample`: reduza o conjunto de um algoritmo de amostragem simples limitado a um número de itens de *count*. Isso significa que o primeiro e o último itens estão incluídos e há um número de itens equivalente a *count* entre eles, com intervalos iguais.
Por exemplo, se você tiver um conjunto de dados [0, 1, 2, ... 100] e uma *count* de 9, receberá os valores [0, 10, 20... 100].
* `window`: carrega uma *janela* de pontos de dados de cada vez contendo elementos *count*. Atualmente, `top` e `window` são equivalentes. Estamos trabalhando para dar suporte completo a uma configuração de janelas.

## <a name="data-reduction-algorithm-usage"></a>Uso de algoritmo de redução de dados

O algoritmo de redução de dados pode ser usado em mapeamento categórico, de tabela ou de exibição de dados de matriz.

Você pode definir o algoritmo em `categories` e/ou seção de grupo de `values` para mapeamento de dados categóricos.

### <a name="example-8"></a>Exemplo 8

```json
"dataViewMappings": {
    "categorical": {
        "categories": {
            "for": { "in": "category" },
            "dataReductionAlgorithm": {
                "window": {
                    "count": 300
                }
            }  
        },
        "values": {
            "group": {
                "by": "series",
                "select": [{
                        "for": {
                            "in": "measure"
                        }
                    }
                ],
                "dataReductionAlgorithm": {
                    "top": {
                        "count": 100
                    }
                }  
            }
        }
    }
}
```

Você pode aplicar o algoritmo de redução de dados à seção `rows` da tabela de mapeamento de Exibição de Dados.

### <a name="example-9"></a>Exemplo 9

```json
"dataViewMappings": [
    {
        "table": {
            "rows": {
                "for": {
                    "in": "values"
                },
                "dataReductionAlgorithm": {
                    "top": {
                        "count": 2000
                    }
                }
            }
        }
    }
]
```

Você pode aplicar o algoritmo de redução de dados às seções `rows` e `columns` da matriz de mapeamento de Exibição de Dados.

## <a name="next-steps"></a>Próximas etapas

Leia como [Adicionar suporte a busca detalhada para mapeamentos de exibição de dados em visuais do Power BI](drill-down-support.md).
