---
title: Funcionalidades e propriedades de visuais do Power BI
description: Este artigo descreve os recursos e as propriedades de visuais do Power BI.
author: asander
ms.author: asander
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 5c32a1679f09e05d134da7f27ffa0cee90d75fab
ms.sourcegitcommit: b602cdffa80653bc24123726d1d7f1afbd93d77c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70237298"
---
# <a name="capabilities-and-properties-of-power-bi-visuals"></a>Funcionalidades e propriedades de visuais do Power BI 

Você usa as funcionalidades para fornecer informações ao host sobre seu visual. Todas as propriedades no modelo de funcionalidades são `optional`.

Os objetos raiz das funcionalidades do visual são `dataRoles`, `dataViewMappings` e assim por diante.

```json
{
    "dataRoles": [ ... ],
    "dataViewMappings": [ ... ],
    "objects":  { ... },
    "supportsHighlight": true|false,
    "advancedEditModeSupport": 0|1|2,
    "sorting": { ... }
}

```

## <a name="define-the-data-fields-that-your-visual-expects-dataroles"></a>Defina os campos de dados que seu visual espera: dataRoles

Para definir os campos que podem ser associados aos dados, use `dataRoles`. `dataRoles` usa uma matriz de objetos `DataViewRole`, que define todas as propriedades necessárias.

### <a name="properties"></a>Propriedades

* **name**: o nome interno deste campo de dados (deve ser exclusivo).
* **kind**: o tipo de campo:
    * `Grouping`: valores discretos usados para agrupar campos de medida.
    * `Measure`: valores de dados numéricos.
    * `GroupingOrMeasure`: valores que podem ser usados como um agrupamento ou uma medida.
* **displayName**: o nome exibido para o usuário no painel **Propriedades**.
* **description**: uma breve descrição do campo (opcional).
* **requiredTypes**: o tipo de dados necessário para essa função de dados. Os valores que não correspondem são definidos como null (opcional).
* **preferredTypes**: o tipo de dados preferencial para essa função de dados (opcional).

### <a name="valid-data-types-in-requiredtypes-and-preferredtypes"></a>Tipos de dados válidos em requiredTypes e preferredTypes

* **bool**: um valor booliano
* **integer**: um valor inteiro (número inteiro)
* **numeric**: um valor numérico
* **text**: Um valor de texto
* **geography**: um dado geográfico

### <a name="example"></a>Exemplo

```json
"dataRoles": [
    {
        "displayName": "My Category Data",
        "name": "myCategory",
        "kind": "Grouping",
        "requiredTypes": [
            {
                "text": true
            },
            {
                "numeric": true
            },
            {
                "integer": true
            }
        ],
        "preferredTypes": [
            {
                "text": true
            }
        ]
    },
    {
        "displayName": "My Measure Data",
        "name": "myMeasure",
        "kind": "Measure",
        "requiredTypes": [
            {
                "integer": true
            },
            {
                "numeric": true
            }
        ],
        "preferredTypes": [
            {
                "integer": true
            }
        ]
    },
    {
        "displayNameKey": "Visual_Location",
        "name": "Locations",
        "kind": "Measure",
        "displayName": "Locations",
        "requiredTypes": [
            {
                "geography": {
                    "address": true
                }
            },
            {
                "geography": {
                    "city": true
                }
            },
            {
                "geography": {
                    "continent": true
                }
            },
            {
                "geography": {
                    "country": true
                }
            },
            {
                "geography": {
                    "county": true
                }
            },
            {
                "geography": {
                    "place": true
                }
            },
            {
                "geography": {
                    "postalCode": true
                }
            },
            {
                "geography": {
                    "region": true
                }
            },
            {
                "geography": {
                    "stateOrProvince": true
                }
            }
        ]
    }
]
```

As funções de dados anteriores criariam os campos exibidos na imagem a seguir:

![Campos de função de dados](./media/data-role-display.png)

## <a name="define-how-you-want-the-data-mapped-dataviewmappings"></a>Defina como você deseja mapear os dados: dataViewMappings

Uma propriedade DataViewMappings descreve como as funções de dados se relacionam entre si e permite que você especifique requisitos condicionais para elas.

A maioria dos visuais fornece um mapeamento único, mas você pode fornecer vários DataViewMappings. Cada mapeamento válido produz uma exibição de dados. 

```json
"dataViewMappings": [
    {
        "conditions": [ ... ],
        "categorical": { ... },
        "table": { ... },
        "single": { ... },
        "matrix": { ... }
    }
]
```

Para obter mais informações, confira [Entender o mapeamento de exibição de dados em visuais do Power BI](dataview-mappings.md).

## <a name="define-property-pane-options-objects"></a>Definir opções do painel de propriedade: objetos

Objetos descrevem propriedades personalizáveis associadas ao visual. Cada objeto pode ter várias propriedades e cada propriedade tem um tipo associado a ela. Os tipos referem-se ao que será essa propriedade. 

```json
"objects": {
    "myCustomObject": {
        "displayName": "My Object Name",
        "properties": { ... }
    }
}
```

Para obter mais informações, confira [Objetos e propriedades de visuais do Power BI](objects-properties.md).

## <a name="handle-partial-highlighting-supportshighlight"></a>Manipular realce parcial: supportsHighlight

Por padrão, esse valor é definido como `false`, o que significa que seus valores são automaticamente filtrados quando algo na página é selecionado. Essa filtragem automática, por sua vez, atualiza seu visual para exibir apenas o valor selecionado. Se quiser exibir os dados completos, mas apenas realçar os itens selecionados, precisará definir `supportsHighlight` como `true` em *capabilities.json*.

Para obter mais informações, confira [Realçar pontos de dados em visuais do Power BI](highlight.md).

## <a name="handle-advanced-edit-mode-advancededitmodesupport"></a>Gerenciar o modo de edição avançado: advancedEditModeSupport

Um visual pode declarar seu suporte ao modo de edição avançada. Por padrão, um visual não dá suporte ao modo de edição avançada, a menos que declarado de outra forma no arquivo *capabilities.json*.

Para obter mais informações, confira [Modo de edição avançado em visuais do Power BI](advanced-edit-mode.md).

## <a name="data-sorting-options-for-visual-sorting"></a>Opções de classificação de dados para visual: classificação

Um visual pode definir o próprio comportamento de classificação por meio de suas funcionalidades. Por padrão, um visual não dá suporte à modificação de sua ordem de classificação, a menos que declarado de outra forma no arquivo *capabilities.json*.

Para obter mais informações, confira [Opções de classificação para elementos visuais do Power BI](sort-options.md).
