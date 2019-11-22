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
ms.openlocfilehash: 206f1aec7c76b00b6f725d8469eb3e483a01c653
ms.sourcegitcommit: f7b28ecbad3e51f410eff7ee4051de3652e360e8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/13/2019
ms.locfileid: "74061766"
---
# <a name="add-context-menu-to-power-bi-visual"></a>Adicionar menu de contexto ao Visual do Power BI

Você pode usar `selectionManager.showContextMenu()` com parâmetros `selectionId` e uma posição (como um objeto `{x:, y:}`) para que o Power BI exiba um menu de contexto para seu visual.

> [!IMPORTANT]
> O `selectionManager.showContextMenu()` foi introduzido na API de visuais 2.2.0.

Normalmente, ele é adicionado como um evento de clique com o botão direito do mouse (ou um pressionamento longo para dispositivos de toque). Context-Menu foi adicionado ao BarChart de exemplo para referência:

```typescript
    public update(options: VisualUpdateOptions) {
        //...
        //handle context menu
        this.svg.on('contextmenu', () => {
            const mouseEvent: MouseEvent = d3.event as MouseEvent;
            const eventTarget: EventTarget = mouseEvent.target;
            let dataPoint = d3.select(eventTarget).datum();
            this.selectionManager.showContextMenu(dataPoint? dataPoint.selectionId : {}, {
                x: mouseEvent.clientX,
                y: mouseEvent.clientY
            });
            mouseEvent.preventDefault();
        });
```
