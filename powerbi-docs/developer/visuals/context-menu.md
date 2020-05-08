---
title: Funcionalidades e propriedades de visuais do Power BI
description: Este artigo descreve os recursos e as propriedades de visuais do Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: rkarlin
manager: rkarlin
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 7d24ea77fd73ca6a83176d1b8560c88fa98a8d6b
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/05/2020
ms.locfileid: "79380745"
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
