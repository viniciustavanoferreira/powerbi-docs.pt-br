---
title: API de Armazenamento Local em Visuais do Power BI
description: Este artigo descreve como usar a API de Visuais do Power BI para ter acesso ao armazenamento local do navegador
author: KesemSharabi
ms.author: kesharab
ms.reviewer: rkarlin
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 01/21/2019
ms.openlocfilehash: e2cb11ea9be85916e6b5557e7933f6a6b5a7159a
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/05/2020
ms.locfileid: "79380584"
---
# <a name="local-storage-api"></a>API de Armazenamento Local

A API de Armazenamento Local é uma API que um visual personalizado pode usar para solicitar que o host salve ou carregue dados do armazenamento do dispositivo. Ela é isolada no sentido de que há uma separação do acesso ao armazenamento entre diferentes tipos de visual.

## <a name="sample"></a>Exemplo

Se o visual personalizado precisar aumentar algum contador sempre que o método de atualização for chamado, mas o valor do contador também precisar ser preservado e não redefinido a cada início do visual:

```typescript
export class Visual implements IVisual {
        // ...
        private updateCountName: string = 'updateCount';
        private updateCount: number;
        private storage: ILocalVisualStorageService;
        // ...

        constructor(options: VisualConstructorOptions) {
            // ...
            this.storage = options.host.storageService;
            // ...

            this.storage.get(this.updateCountName).then(count =>
            {
                this.updateCount = +count;
            })
            .catch(() =>
            {
                this.updateCount = 0;
                this.storage.set(this.updateCountName, this.updateCount.toString());
            });
            // ...
        }

        public update(options: VisualUpdateOptions) {
            // ...
            this.updateCount++;
            this.storage.set(this.updateCountName, this.updateCount.toString());
            // ...
        }
}
```

## <a name="known-limitations-and-issues"></a>Limitações e problemas conhecidos

A API de Armazenamento Local não é ativada para os visuais do Power BI por padrão. Se desejar ativá-la para seu visual do Power BI, envie uma solicitação para Suporte a visuais do Power BI `pbicvsupport@microsoft.com`.  
**Observe que o visual deve estar disponível em [AppSource](https://appsource.microsoft.com/en-us/marketplace/apps?product=power-bi-visuals) e ser [certificado](https://powerbi.microsoft.com/en-us/documentation/powerbi-custom-visuals-certified/).**
