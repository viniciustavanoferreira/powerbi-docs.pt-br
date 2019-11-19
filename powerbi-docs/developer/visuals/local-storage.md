---
title: API de Armazenamento Local em Visuais do Power BI
description: Este artigo descreve como usar a API de Visuais do Power BI para ter acesso ao armazenamento local do navegador
author: uve
ms.author: v-grniki
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 10/31/2019
ms.openlocfilehash: f69a3c8928b8079f79b8a6dd5f5b132235a7089c
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/09/2019
ms.locfileid: "73879896"
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
