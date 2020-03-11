---
title: Como depurar visuais do Power BI
description: Este artigo descreve como depurar visuais do Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 02/14/2020
ms.openlocfilehash: 4ce61fcd4f322abc0362956453d76ced9b78d887
ms.sourcegitcommit: d55d3089fcb3e78930326975957c9940becf2e76
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/04/2020
ms.locfileid: "78264233"
---
# <a name="how-to-debug-power-bi-visuals"></a>Como depurar visuais do Power BI

Esta página mostra algumas dicas de depuração ao criar o visual. Ele inclui etapas básicas e mostra as diferenças entre a depuração de visuais de aplicativos de front-end padrão e do Power BI.
Depois de ler o artigo, você poderá depurar visuais personalizados usando pontos de interrupção, além de registrar exceções em log e capturar exceções no Chrome e no Edge.

## <a name="using-breakpoints"></a>Usar pontos de interrupção

Como o JavaScript do visual é totalmente recarregado toda vez que o visual é atualizado, todos os pontos de interrupção que você adicionar serão perdidos quando o visual depurado for atualizado. Como alternativa, use as instruções do `debugger` em seu código. É recomendável desativar o recarregamento automático ao usar `debugger` em seu código.

```typescript
public update(options: VisualUpdateOptions) {
    console.log('Visual update', options);
    debugger;
    this.target.innerHTML = `<p>Update count: <em>${(this.updateCount</em></p>`;
}
```


## <a name="showing-exceptions"></a>Mostrar exceções

Ao trabalhar em seu visual, você observará que todos os erros são "consumidos" pelo serviço do Power BI. Esse é um recurso intencional de Power BI para impedir que visuais com comportamento inadequado façam o aplicativo inteiro se tornar instável.

Como alternativa, adicione o código para capturar suas exceções e registrá-las em log ou defina seu depurador para interromper as exceções detectadas.


## <a name="log-exceptions"></a>Registrar exceções em log

Para registrar em log as exceções no seu visual do Power BI, adicione o código a seguir ao seu visual para definir um decorador de registro de exceção em log.

```typescript
export function logExceptions(): MethodDecorator {
     return function (target: Object, propertyKey: string, descriptor: TypedPropertyDescriptor<Function>)
    : TypedPropertyDescriptor<Function> {
            
        return {
            value: function () {
                try {
                    return descriptor.value.apply(this, arguments);
                } catch (e) {
                    console.error(e);
                    throw e;
                }
            }
        }
    }
}
```
Em seguida, você pode usar esse decorador em qualquer função para ver o registro de erros em log.

```typescript
@logExceptions()
public update(options: VisualUpdateOptions) {
```

## <a name="break-on-exceptions"></a>Interromper em exceções

Você também pode definir o navegador para interromper nas exceções detectadas. Ele interrompe a execução de código caso ocorra um erro e permite que você depure a partir desse ponto.

### <a name="edge"></a>Microsoft Edge

1. Abra as ferramentas para desenvolvedores (F12).
2. Acesse a guia **Depurador**.
3. Clique no ícone **interromper em exceções** (hexágono com um símbolo de pausa).
4. Selecione **Interromper em todas as exceções**.

![Campos de função de dados](./media/how-to-debug-edge.png)

## <a name="chrome"></a>Chrome

1. Abra as ferramentas para desenvolvedores (F12).
2. Acesse a guia **Fontes**.
3. Clique no ícone **interromper em exceções** (sinal de parada com um símbolo de pausa).
4. Marque a caixa de seleção **Pausar em Exceções Capturadas**.

![Campos de função de dados](./media/how-to-debug-chrome.png)

## <a name="next-steps"></a>Próximas etapas
* [Solucionar problemas de visuais do Power BI](../power-bi-custom-visuals-troubleshoot.md)
* Saiba mais e solucione suas dúvidas nas [Perguntas frequentes sobre os visuais do Power BI](../power-bi-custom-visuals-faq.md#organizational-power-bi-visuals)
