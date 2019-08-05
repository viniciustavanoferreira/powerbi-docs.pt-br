---
title: Interações visuais
description: Como verificar se o Visual do Power BI deve permitir interações visuais
author: shaym83
ms.author: shaym
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 739e59c6da3c1e464e0462a928bc4f33ea0d01f8
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68424483"
---
# <a name="visuals-interactions"></a>Interações visuais

Os visuais podem consultar o valor do sinalizador 'allowInteractions', que indica se o Visual deve permitir interações visuais.
Por exemplo, visuais são interativos durante a exibição ou edição de relatório, mas não são interativos quando exibidos em um dashboard.
Essas interações são clique, panorâmica, zoom, seleção e outras.
Observe que as dicas de ferramenta devem ser habilitadas em todos os cenários, seja qual for esse sinalizador.

O sinalizador 'allowInteractions' é passado como um booliano durante a inicialização do Visual, como membro da interface IVisualHost.

Em qualquer cenário de Power BI que exija que os visuais não sejam interativos (por exemplo, blocos de dashboard), o sinalizador 'allowInteractions' será definido como false.
Caso contrário (por exemplo, relatório), 'allowInteractions' será definido como true.

Para obter mais informações, confira o [repositório visual SampleBarChart](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/59a47935d8f5272ce145fe804193599ddb7e2001)

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
