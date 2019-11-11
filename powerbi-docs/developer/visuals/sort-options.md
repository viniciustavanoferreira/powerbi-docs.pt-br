---
title: Opções de classificação para visuais do Power BI
description: Este artigo discute o comportamento de classificação padrão para visuais do Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 546480ae863c63d6517fde7c98e7c9787c022ab6
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/09/2019
ms.locfileid: "73875539"
---
# <a name="sorting-options-for-power-bi-visuals"></a>Opções de classificação para visuais do Power BI

Este artigo descreve como as opções de *classificação* especificam o comportamento de classificação para visuais do Power BI. 

A funcionalidade de classificação requer um dos parâmetros a seguir.

## <a name="default-sorting"></a>Classificação padrão

A opção `default` é a forma mais simples. Ela permite classificar os dados apresentados na seção 'DataMappings'. A opção permite a classificação dos mapeamentos de dados pelo usuário e especifica a direção da classificação.

```json
    "sorting": {
        "default": {   }
    }
```

![Opções de classificação no menu de contexto](./media/sorting.png)

## <a name="implicit-sorting"></a>Classificação implícita

A classificação implícita está classificando com o parâmetro de matriz `clauses`, que descreve a classificação para cada função de dados. `implicit` significa que o usuário do visual não pode alterar a ordem de classificação. O Power BI não exibe opções de classificação no menu do visual. No entanto, o Power BI classifica os dados de acordo com as configurações especificadas.

Os parâmetros `clauses` podem conter vários objetos com dois parâmetros:

- `role`: Determina `DataMapping` para classificação
- `direction`: Determina a direção da classificação (1 = crescente, 2 = decrescente)

```json
    "sorting": {
        "implicit": {
            "clauses": [
                {
                    "role": "category",
                    "direction": 1
                },
                {
                    "role": "measure",
                    "direction": 2
                }
            ]
        }
    }
```

## <a name="custom-sorting"></a>Classificação personalizada

A classificação personalizada significa que a classificação é gerenciada pelo desenvolvedor no código do visual.
