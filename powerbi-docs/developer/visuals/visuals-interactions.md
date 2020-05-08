---
title: Interações visuais em visuais do Power BI
description: Este artigo discute como verificar se os visuais do Power BI devem permitir interações visuais.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: b8b1a1a59ee9fae5a1c248548a14c5f91438edc9
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/05/2020
ms.locfileid: "79378928"
---
# <a name="visual-interactions-in-power-bi-visuals"></a>Interações visuais em visuais do Power BI

Os visuais podem consultar o valor do sinalizador `allowInteractions`, que indica se o visual deve permitir interações visuais. Por exemplo, visuais são interativos durante a exibição ou edição de relatório, mas não são interativos quando exibidos em um dashboard. Essas interações são *clique*, *panorâmica*, *zoom*, *seleção* e outras. 

> [!NOTE]
> Você deve habilitar dicas de ferramenta em todos os cenários, não importa o sinalizador indicado.

O sinalizador `allowInteractions` é passado como um booliano durante a inicialização do visual, como membro da interface IVisualHost.

Em qualquer cenário do Power BI que exija que os visuais não sejam interativos (por exemplo, blocos de dashboard), o sinalizador `allowInteractions` é definido como `false`. Caso contrário (por exemplo, Relatório), `allowInteractions` será definido como `true`.

Para obter mais informações, confira o [repositório visual SampleBarChart](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/59a47935d8f5272ce145fe804193599ddb7e2001).

```typescript
   ...
   let allowInteractions = options.host.allowInteractions;
   bars.on('click', function(d) {
       if (allowInteractions) {
           selectionManager.select(d.selectionId);
           ...
       }
   });
```
