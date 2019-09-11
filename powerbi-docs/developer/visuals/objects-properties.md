---
title: Objetos e propriedades de visuais do Power BI
description: Este artigo descreve as propriedades personalizáveis de visuais do Power BI.
author: MrMeison
ms.author: rasala
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: e15d80af35ff7c56879dab4380d4ae0c9fdd0e8a
ms.sourcegitcommit: b602cdffa80653bc24123726d1d7f1afbd93d77c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70236625"
---
# <a name="objects-and-properties-of-power-bi-visuals"></a>Objetos e propriedades de visuais do Power BI

Objetos descrevem propriedades personalizáveis associadas um visual. Um objeto pode ter várias propriedades, sendo que cada propriedade tem um tipo associado que descreve qual será a propriedade. Este artigo fornece informações sobre objetos e tipos de propriedade.

`myCustomObject` é o nome interno usado para fazer referência ao objeto dentro de `dataView` e `enumerateObjectInstances`.

```json
"objects": {
    "myCustomObject": {
        "displayName": "My Object Name",
        "properties": { ... }
    }
}
```

## <a name="display-name"></a>Nome para exibição

`displayName` é o nome que será mostrado no painel de propriedades.

## <a name="properties"></a>Propriedades

`properties` é um mapa das propriedades definidas pelo desenvolvedor.

```json
"properties": {
    "myFirstProperty": {
        "displayName": "firstPropertyName",
        "type": ValueTypeDescriptor | StructuralTypeDescriptor
    }
}
```

> [!NOTE]
> `show` é uma propriedade especial que habilita uma alternância para alternar o objeto.

Exemplo:

```json
"properties": {
    "show": {
        "displayName": "My Property Switch",
        "type": {"bool": true}
    }
}
```

### <a name="property-types"></a>Tipos de propriedade

Há dois tipos de propriedade: `ValueTypeDescriptor` e `StructuralTypeDescriptor`.

#### <a name="value-type-descriptor"></a>Descritor de tipo de valor

Os tipos `ValueTypeDescriptor` são principalmente primitivos e costumam ser usados como um objeto estático.

Aqui estão alguns dos elementos `ValueTypeDescriptor` comuns:

```typescript
export interface ValueTypeDescriptor {
    text?: boolean;
    numeric?: boolean;
    integer?: boolean;
    bool?: boolean;
}
```

#### <a name="structural-type-descriptor"></a>Descritor de tipo estrutural

Tipos `StructuralTypeDescriptor` são usados principalmente para objetos associados a dados.
O tipo `StructuralTypeDescriptor` mais comum é *fill*.

```typescript
export interface StructuralTypeDescriptor {
    fill?: FillTypeDescriptor;
}
```

## <a name="gradient-property"></a>Propriedade de gradiente

A propriedade de gradiente não pode ser definida como uma propriedade padrão. Em vez disso, você precisa definir uma regra para substituição da propriedade do seletor de cor (tipo *fill*).

Um exemplo é mostrado no código a seguir:

```json
"properties": {
    "showAllDataPoints": {
        "displayName": "Show all",
        "displayNameKey": "Visual_DataPoint_Show_All",
        "type": {
            "bool": true
        }
    },
    "fill": {
        "displayName": "Fill",
        "displayNameKey": "Visual_Fill",
        "type": {
            "fill": {
                "solid": {
                    "color": true
                }
            }
        }
    },
    "fillRule": {
        "displayName": "Color saturation",
        "displayNameKey": "Visual_ColorSaturation",
        "type": {
            "fillRule": {}
        },
        "rule": {
            "inputRole": "Gradient",
            "output": {
                "property": "fill",
                    "selector": [
                        "Category"
                    ]
            }
        }
    }
}
```

preste atenção às propriedades *fill* e *fillRule*. A primeira é o seletor de cor, a segunda é a regra de substituição para gradiente que substituirá a *propriedade fill*, `visually`, quando as condições da regra forem atendidas.

Esse vínculo entre a propriedade *fill* e a regra de substituição é definido na seção `"rule"`>`"output"` da propriedade *fillRule*.

A propriedade `"Rule"`>`"InputRole"` define qual função de dados dispara a regra (condição). Neste exemplo, se a função de dados `"Gradient"` contiver dados, a regra será aplicada à propriedade `"fill"`.

Um exemplo da função de dados que dispara a regra de preenchimento (`the last item`) é mostrado no código a seguir:

```json
{
    "dataRoles": [
            {
                "name": "Category",
                "kind": "Grouping",
                "displayName": "Details",
                "displayNameKey": "Role_DisplayName_Details"
            },
            {
                "name": "Series",
                "kind": "Grouping",
                "displayName": "Legend",
                "displayNameKey": "Role_DisplayName_Legend"
            },
            {
                "name": "Gradient",
                "kind": "Measure",
                "displayName": "Color saturation",
                "displayNameKey": "Role_DisplayName_Gradient"
            }
    ]
}
```

## <a name="the-enumerateobjectinstances-method"></a>O método enumerateObjectInstances

Para usar objetos com eficiência, você precisa de uma função em seu visual personalizado chamada `enumerateObjectInstances`. Essa função preenche o painel de propriedades com objetos e também determina em que lugar os objetos devem estar associados no dataView.  

Veja como é a aparência de uma configuração típica:

```typescript
public enumerateObjectInstances(options: EnumerateVisualObjectInstancesOptions): VisualObjectInstanceEnumeration {
    let objectName: string = options.objectName;
    let objectEnumeration: VisualObjectInstance[] = [];

    switch( objectName ) {
        case 'myCustomObject':
            objectEnumeration.push({
                objectName: objectName,
                properties: { ... },
                selector: { ... }
            });
            break;
    };

    return objectEnumeration;
}
```

### <a name="properties"></a>Propriedades

As propriedades no `enumerateObjectInstances` refletem as propriedades que você definiu em suas funcionalidades. Veja um exemplo no final deste artigo.

### <a name="objects-selector"></a>Seletor de objetos

O seletor no `enumerateObjectInstances` determina o lugar em que cada objeto é associado no dataView. Há quatro opções distintas.

#### <a name="static"></a>estático

Este objeto está associado a metadados `dataviews[index].metadata.objects`, como mostrado aqui.

```typescript
selector: null
```

#### <a name="columns"></a>colunas

Esse objeto é vinculado a colunas com o `QueryName` correspondente.

```typescript
selector: {
    metadata: 'QueryName'
}
```

#### <a name="selector"></a>seletor

Esse objeto é associado ao elemento para o qual você criou um `selectionID`. Neste exemplo, vamos pressupor que criamos `selectionID`s para alguns pontos de dados e estamos fazendo um loop neles.

```typescript
for (let dataPoint in dataPoints) {
    ...
    selector: dataPoint.selectionID.getSelector()
}
```

#### <a name="scope-identity"></a>Identidade do escopo

Esse objeto é vinculado a valores específicos na interseção de grupos. Por exemplo, se você tiver categorias `["Jan", "Feb", "March", ...]` e séries `["Small", "Medium", "Large"]`, talvez queira ter um objeto na interseção de valores que correspondam a `Feb` e `Large`. Para fazer isso, você poderia obter `DataViewScopeIdentity` das duas colunas, enviá-las por push para a variável `identities` e usar essa sintaxe com o seletor.

```typescript
selector: {
    data: <DataViewScopeIdentity[]>identities
}
```

##### <a name="example"></a>Exemplo

O exemplo a seguir mostra como seria a aparência de um objectEnumeration para um objeto customColor com uma propriedade *fill*. Queremos que esse objeto seja vinculado estaticamente a `dataViews[index].metadata.objects`, como mostrado:

```typescript
objectEnumeration.push({
    objectName: "customColor",
    displayName: "Custom Color",
    properties: {
        fill: {
            solid: {
                color: dataPoint.color
            }
        }
    },
    selector: null
});
```
