---
title: Painel de análise
description: Como criar linhas de referência dinâmica em visuais do Power BI
author: Guy-Moses
ms.author: guymos
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: b3b50f8dbcf40a3923e86422e24f8ed020894445
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68425518"
---
# <a name="analytics-pane-in-power-bi-visuals"></a>Painel Análise em visuais do Power BI

O **painel Análise** foi [introduzido para visuais nativos](https://docs.microsoft.com/power-bi/desktop-analytics-pane) em novembro de 2018.
Os visuais personalizados com API v2.5.0 podem apresentar e gerenciar suas propriedades no **painel Análise**.

![Painel Análise](./media/visualization-pane-analytics-tab.png)

Ele é tratado de modo semelhante ao [gerenciamento de propriedades no painel Formatar](https://docs.microsoft.com/power-bi/developer/custom-visual-develop-tutorial-format-options), definindo-se um objeto no arquivo capabilities.json do visual. 

As diferenças são as seguintes:

1. Na definição do `object`, adicione um campo `objectCategory` com um valor de 2.

    > [!NOTE]
    > O campo `objectCategory` é um campo opcional introduzido na API 2.5.0. Ele define o aspecto do visual que o objeto controla (1 = Formatação, 2 = Análise). A "Formatação" é usada para aparência, cores, eixos, rótulos etc. A "análise" é usada para previsões, linhas de tendência, linhas de referência, formas e assim por diante.
    >
    > `objectCategory`, se omitido, assume "Formatação" como padrão.

2. O objeto precisa ter as duas propriedades a seguir:
    1. `show` do tipo bool, com o valor padrão de false.
    2. `displayName` do tipo text. O valor padrão que você escolherá se tornará o nome de exibição inicial da instância.

```json
{
  "objects": {
    "YourAnalyticsPropertiesCard": {
      "displayName": "Your analytics properties card's name",
      "objectCategory": 2,
      "properties": {
        "show": {
          "type": {
            "bool": true
          }
        },
        "displayName": {
          "type": {
            "text": true
          }
        },
      ... //any other properties for your Analytics card
      }
    }
  ...
  }
}
```

Qualquer outra propriedade pode ser definida da mesma maneira usada para objetos de Formatar. A enumeração de objetos é feita exatamente do mesmo modo que no **painel Formatar**.

***Limitações e problemas conhecidos***

  1. Ainda não há suporte para várias instâncias. Os objetos não podem ter um [seletor](https://microsoft.github.io/PowerBI-visuals/docs/concepts/objects-and-properties/#selector) que não seja estático (ou seja, "selector": null) e visuais personalizados não podem ter várias instâncias de um cartão definidas pelo usuário.
  2. Propriedades do tipo `integer` não são exibidas corretamente. Como alternativa, use o tipo `numeric` em vez delas.

> [!NOTE]
> Use o painel Análise somente para objetos que adicionam novas informações ou fazem novos esclarecimentos sobre as informações apresentadas. Por exemplo, linhas de referência dinâmica que ilustram tendências importantes.
> Todas as opções que controlam a aparência do visual, ou seja, a formatação, devem ser mantidas no painel de Formatação.
