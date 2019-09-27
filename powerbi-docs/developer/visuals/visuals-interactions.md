---
title: Interações visuais em visuais do Power BI
description: Este artigo discute como verificar se os visuais do Power BI devem permitir interações visuais.
author: KesemSharabi
ms.author: kesharab
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 0155f0fce1bc0fec5c96aef1c7e1dc9cf64b122f
ms.sourcegitcommit: e2de2e8b8e78240c306fe6cca820e5f6ff188944
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71193898"
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
