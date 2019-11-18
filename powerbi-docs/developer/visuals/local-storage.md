---
title: API de Armazenamento Local em Visuais do Power BI
description: Este artigo descreve como usar a API de Visuais do Power BI para ter acesso ao armazenamento local do navegador
author: uve
ms.author: v-grniki
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 10/31/2019
ms.openlocfilehash: 3b6746b611a41ddfb471008f5aefa4f7dc391456
ms.sourcegitcommit: 8cc2b7510aae76c0334df6f495752e143a5851c4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73432898"
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

A API de Armazenamento Local não é ativada para os Visuais Personalizados por padrão. Se quiser ativá-la para seu Visual Personalizado, envie uma solicitação para o Suporte a Visuais Personalizados do Power BI `pbicvsupport@microsoft.com`
