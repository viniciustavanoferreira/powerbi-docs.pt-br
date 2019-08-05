---
title: Objetos e propriedades
description: Propriedades personalizáveis do visual do Power BI
author: MrMeison
ms.author: rasala
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: c22a1cfb281c9902d490e2320b85c2f6bbb63468
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68424598"
---
# <a name="object-and-properties"></a>Objetos e propriedades

Objetos descrevem propriedades personalizáveis associadas ao visual.
Cada objeto pode ter várias propriedades e cada propriedade tem um tipo associado a ela.
Os tipos referem-se ao que será essa propriedade. Veja abaixo mais informações sobre tipos.

`myCustomObject` é o nome interno usado para fazer referência ao objeto dentro de `dataView` e `enumerateObjectInstances`

```json
"objects": {
    "myCustomObject": {
        "displayName": "My Object Name",
        "properties": { ... }
    }
}
```

## <a name="display-name"></a>Nome de Exibição

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

#### <a name="value-type-descriptor"></a>Descritor de Tipo de Valor

`ValueTypeDescriptor` são basicamente tipos primitivos e normalmente são usados como um objeto estático.
Aqui estão alguns dos `ValueTypeDescriptor` comuns

```typescript
export interface ValueTypeDescriptor {
    text?: boolean;
    numeric?: boolean;
    integer?: boolean;
    bool?: boolean;
}
```

#### <a name="structural-type-descriptor"></a>Descritor de tipo estrutural

`StructuralTypeDescriptor` são usados principalmente para objetos associados a dados.
Preenchimento é o `StructuralTypeDescriptor` mais comum

```typescript
export interface StructuralTypeDescriptor {
    fill?: FillTypeDescriptor;
}
```

## <a name="gradient-property"></a>Propriedade de gradiente

A propriedade de gradiente não pode ser definida como uma propriedade padrão. Em vez disso, você precisa definir uma regra para substituição da propriedade do seletor de cor (tipo de preenchimento).
Veja o exemplo abaixo:

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

Preste atenção às propriedades `"fill"` e `"fillRule"`. A primeira é o seletor de cor, a segunda é a regra de substituição para gradiente que substituirá a propriedade de `visually` "preenchimento" quando as condições da regra forem atendidas.

Esse vínculo entre a propriedade Preenchimento e a regra de substituição é definido na seção `"rule"`->`"output"` da propriedade `"fillRule"`.

`"Rule"`->`"InputRole"` define qual função de dados dispara a regra (condição). Neste exemplo, se a função de dados `"Gradient"` contiver dados, a regra será aplicada à propriedade `"fill"`.

Abaixo, você pode ver um exemplo da função de dados que dispara a regra de preenchimento (`the last item`).

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

## <a name="enumerateobjectinstances-method"></a>Método `enumerateObjectInstances`

Para usar objetos com eficiência, você precisará de uma função em seu visual personalizado chamada `enumerateObjectInstances`. Essa função preencherá o painel de propriedades com objetos e também determinará em que lugar os objetos devem estar associados no dataView.  

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

As propriedades no `enumerateObjectInstances` refletirão as propriedades que você definiu em seus recursos. Veja o exemplo na parte inferior da página.

### <a name="objects-selector"></a>Seletor de objetos

O seletor no `enumerateObjectInstances` determina o lugar em que cada objeto será associado no dataView. Há quatro opções distintas.

#### <a name="static"></a>estático

Esse objeto será associado a metadados `dataviews[index].metadata.objects`

```typescript
selector: null
```

#### <a name="columns"></a>colunas

Esse objeto será vinculado a colunas com o `QueryName` correspondente.

```typescript
selector: {
    metadata: 'QueryName'
}
```

#### <a name="selector"></a>seletor

Esse objeto será associado ao elemento para o qual criamos um `selectionID`. Neste exemplo, vamos pressupor que criamos `selectionID` para alguns pontos de dados e estamos fazendo um loop neles.

```typescript
for (let dataPoint in dataPoints) {
    ...
    selector: dataPoint.selectionID.getSelector()
}
```

#### <a name="scope-identity"></a>Identidade do escopo

Esse objeto será vinculado a valores específicos na interseção de grupos. Por exemplo, se eu tiver categorias `["Jan", "Feb", "March", ...]` e séries `["Small", "Medium", "Large"]`, talvez queira ter um objeto na interseção de valores que correspondem a `Feb` e `Large`. Para fazer isso, eu poderia obter `DataViewScopeIdentity` das duas colunas, enviá-las por push para a variável `identities` e usar essa sintaxe com o seletor.

```typescript
selector: {
    data: <DataViewScopeIdentity[]>identities
}
```

##### <a name="example"></a>Exemplo

Neste exemplo, mostramos a aparência de um objectEnumeration para um objeto customColor com uma propriedade `fill`. Queremos que esse objeto seja vinculado estaticamente a `dataViews[index].metadata.objects`

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
