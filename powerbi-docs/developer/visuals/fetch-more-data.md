---
title: Buscar mais dados
description: Habilitar a busca segmentada de conjuntos de dados grandes para visuais do Power BI
author: AviSander
ms.author: asander
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: bc8ff673927fd66bf44164e4e9950c279b98c6c1
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68425058"
---
# <a name="fetch-more-data-from-power-bi"></a>Buscar mais dados do Power BI

Carregue mais dados para que a API exceda o limite rígido de 30 mil pontos de dados. Isso faz com que os dados sejam trazidos em partes. O tamanho da parte é configurável para melhorar o desempenho de acordo com o caso de uso.  

## <a name="enable-segmented-fetch-of-large-datasets"></a>Habilitar a busca segmentada de conjuntos de dados grandes

Para o modo de segmento `dataview`, defina uma "janela" dataReductionAlgorithm no `capabilities.json` do visual para o dataViewMapping necessário.
O `count` determinará o tamanho da janela, o que limita o número de novas linhas de dados anexadas ao `dataview` em cada atualização.

A ser adicionado em capabilities.json

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

## <a name="usage-in-the-custom-visual"></a>Uso no visual personalizado

Os dados de indicação existem ou não podem ser determinados verificando a existência de `dataView.metadata.segment`:

```typescript
    public update(options: VisualUpdateOptions) {
        const dataView = options.dataViews[0];
        console.log(dataView.metadata.segment);
        // output: __proto__: Object
    }
```

Verificando `options.operationKind`, também é possível confirmar se esta é a primeira atualização ou a subsequente.

`VisualDataChangeOperationKind.Create` significa o primeiro segmento e `VisualDataChangeOperationKind.Append` significa segmentos subsequentes.

Confira o snippet de código abaixo para obter uma amostra de implementação:

```typescript
// CV update implementation
public update(options: VisualUpdateOptions) {
    // indicates this is the first segment of new data.
    if (options.operationKind == VisualDataChangeOperationKind.Create) {

    }

    // on second or subesquent segments:
    if (options.operationKind == VisualDataChangeOperationKind.Append) {

    }

    // complete update implementation
}
```

O método `fetchMoreData` também pode ser invocado de um manipulador de eventos de interface do usuário

```typescript
btn_click(){
{
    // check if more data is expected for the current dataview
    if (dataView.metadata.segment) {
        //request for more data if available, as resopnce Power BI will call update method
        let request_accepted: bool = this.host.fetchMoreData();
        // handle rejection
        if (!request_accepted) {
            // for example when the 100 MB limit has been reached
        }
    }
}
```

O Power BI chamará `update` o método do visual com o novo segmento de dados como resposta à chamada ao método `this.host.fetchMoreData`.

> [!NOTE]
> O Power BI, no momento, limitará o total de dados buscados a **100 MB** para evitar restrições de memória do cliente. Você pode detectar que esse limite seja atingido quando fetchMoreData() retornar 'false'.*
