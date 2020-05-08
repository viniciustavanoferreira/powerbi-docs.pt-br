---
title: Adicionar uma página de aterrissagem aos visuais do Power BI
description: Este artigo descreve como adicionar a página de aterrissagem a visuais do Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 06/18/2019
ms.openlocfilehash: 6f1590d5635ed6e55833350027c52379e5d7cf51
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/05/2020
ms.locfileid: "79379940"
---
# <a name="add-a-landing-page-to-your-power-bi-visuals"></a>Adicionar uma página de aterrissagem aos visuais do Power BI

Com a API 2.3.0, você pode adicionar uma página de aterrissagem aos visuais do Power BI. Para fazer isso, adicione `supportsLandingPage` às funcionalidades e defina-o como true. Essa ação inicializa e atualiza seu visual antes de você adicionar dados a ele. Uma vez que o visual não mostra mais uma marca-d'água, você pode criar sua própria página de aterrissagem para ser exibida no visual, desde que não contenha dados.

```typescript
export class BarChart implements IVisual {
    //...
    private element: HTMLElement;
    private isLandingPageOn: boolean;
    private LandingPageRemoved: boolean;
    private LandingPage: d3.Selection<any>;

    constructor(options: VisualConstructorOptions) {
            //...
            this.element = options.element;
            //...
    }

    public update(options: VisualUpdateOptions) {
    //...
        this.HandleLandingPage(options);
    }

    private HandleLandingPage(options: VisualUpdateOptions) {
        if(!options.dataViews || !options.dataViews.length) {
            if(!this.isLandingPageOn) {
                this.isLandingPageOn = true;
                const SampleLandingPage: Element = this.createSampleLandingPage(); //create a landing page
                this.element.appendChild(SampleLandingPage);
                this.LandingPage = d3.select(SampleLandingPage);
            }

        } else {
                if(this.isLandingPageOn && !this.LandingPageRemoved){
                    this.LandingPageRemoved = true;
                    this.LandingPage.remove();
                }
        }
    }
```

Uma página de aterrissagem de exemplo é mostrada na imagem a seguir:

![captura de tela da página de aterrissagem](media/landing-page/app-landing-page.png)
