---
title: Buscar mais dados do Power BI
description: Este artigo discute como habilitar uma busca segmentada de grandes conjuntos de altos para visuais do Power BI.
author: KesemSharabi
ms.author: kesharab
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: b67977abd93b3aa605430dd2d7fb516ca33bd51c
ms.sourcegitcommit: e2de2e8b8e78240c306fe6cca820e5f6ff188944
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71194060"
---
# <a name="fetch-more-data-from-power-bi"></a>Buscar mais dados do Power BI

Este artigo discute como carregar mais dados para ignorar o limite rígido de um ponto de dados de 30 KB. Essa abordagem fornece dados em partes. Para melhorar o desempenho, você pode configurar o tamanho da parte para acomodar seu caso de uso.  

## <a name="enable-a-segmented-fetch-of-large-datasets"></a>Habilitar uma busca segmentada de conjuntos de dados grandes

Para o modo de segmento `dataview`, você define um tamanho de janela para dataReductionAlgorithm no arquivo *capabilities.json* do visual para o dataViewMapping necessário. O `count` determina o tamanho da janela, o que limita o número de novas linhas de dados que podem ser anexadas ao `dataview` em cada atualização.

Adicione o seguinte código ao arquivo *capabilities.json*:

```typescript
"dataViewMappings": [
    {
        "table": {
            "rows": {
                "for": {
                    "in": "values"
                },
                "dataReductionAlgorithm": {
                    "window": {
                        "count": 100
                    }
                }
            }
    }
]
```

Novos segmentos são acrescentados ao `dataview` existente e fornecidos ao visual como uma chamada `update`.

## <a name="usage-in-the-power-bi-visual"></a>Uso no visual do Power BI

Você pode determinar se os dados existem verificando a existência de `dataView.metadata.segment`:

```typescript
    public update(options: VisualUpdateOptions) {
        const dataView = options.dataViews[0];
        console.log(dataView.metadata.segment);
        // output: __proto__: Object
    }
```

Você também pode verificar se é a primeira atualização ou uma atualização subsequente verificando `options.operationKind`. No código a seguir, `VisualDataChangeOperationKind.Create` refere-se ao primeiro segmento e `VisualDataChangeOperationKind.Append` refere-se aos segmentos subsequentes.

Para obter uma implementação de exemplo, confira o seguinte snippet de código:

```typescript
// CV update implementation
public update(options: VisualUpdateOptions) {
    // indicates this is the first segment of new data.
    if (options.operationKind == VisualDataChangeOperationKind.Create) {

    }

    // on second or subsequent segments:
    if (options.operationKind == VisualDataChangeOperationKind.Append) {

    }

    // complete update implementation
}
```

Você também pode invocar `fetchMoreData` o método de um manipulador de eventos de interface do usuário, como mostrado aqui:

```typescript
btn_click(){
{
    // check if more data is expected for the current data view
    if (dataView.metadata.segment) {
        //request for more data if available; as a response, Power BI will call update method
        let request_accepted: bool = this.host.fetchMoreData();
        // handle rejection
        if (!request_accepted) {
            // for example, when the 100 MB limit has been reached
        }
    }
}
```

Como uma resposta a chamar o método `this.host.fetchMoreData`, o Power BI chama o método `update` do visual com um novo segmento de dados.

> [!NOTE]
> Para evitar restrições de memória do cliente, o Power BI atualmente limita o total de dados buscados a 100 MB. Você pode ver que o limite foi atingido quando fetchMoreData() retorna `false`.
