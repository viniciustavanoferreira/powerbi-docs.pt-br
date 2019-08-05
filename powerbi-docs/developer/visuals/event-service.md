---
title: Renderização de eventos
description: Os visuais do Power BI podem notificar o Power BI que estão prontos para exportar para o Power Point/PDF
author: Yarovinsky
ms.author: alexyar
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 46166b3503a770e033b98474fcf9240235296cc2
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68425081"
---
# <a name="event-service"></a>Serviço de eventos

A nova API consiste em três métodos (iniciado, concluído ou com falha) que devem ser chamados durante a renderização.

Quando a renderização é iniciada, o código do visual personalizado chama o método renderingStarted para indicar que o processo de renderização foi iniciado.

Se a renderização for concluída com êxito, o código do Visual personalizado chamará imediatamente o método `renderingFinished`, notificando os ouvintes (**principalmente 'Exportar para PDF' e 'Exportar para o PowerPoint'** ) que a imagem do visual está pronta.

Caso tenha ocorrido um problema durante o processo de renderização, impedindo que o Visual personalizado seja concluído com êxito, o código Visual personalizado deve chamar o método `renderingFailed`, notificando o ouvinte de que o processo de renderização não foi concluído. Esse método também fornece uma cadeia de caracteres opcional para a causa da falha.

## <a name="usage"></a>Uso

```typescript
export interface IVisualHost extends extensibility.IVisualHost {
    eventService: IVisualEventService ;
}

/**
 * An interface for reporting rendering events
 */
export interface IVisualEventService {
    /**
     * Should be called just before the actual rendering was started. 
     * Usually at the very start of the update method.
     *
     * @param options - the visual update options received as update parameter
     */
    renderingStarted(options: VisualUpdateOptions): void;

    /**
     * Shoudl be called immediately after finishing successfull rendering.
     * 
     * @param options - the visual update options received as update parameter
     */
    renderingFinished(options: VisualUpdateOptions): void;

    /**
     * Called when rendering failed with optional reason string
     * 
     * @param options - the visual update options received as update parameter
     * @param reason - the option failure reason string
     */
    renderingFailed(options: VisualUpdateOptions, reason?: string): void;
}
```

### <a name="simple-sample-the-visual-hasnt-any-animations-on-rendering"></a>Exemplo simples. O Visual não tem nenhuma animação na renderização

```typescript
    export class Visual implements IVisual {
        ...
        private events: IVisualEventService;
        ...

        constructor(options: VisualConstructorOptions) {
            ...
            this.events = options.host.eventService;
            ...
        }

        public update(options: VisualUpdateOptions) {
            this.events.renderingStarted(options);
            ...
            this.events.renderingFinished(options);
        }
```

### <a name="sample-the-visual-with-animation"></a>Exemplo. O visual com animação

Se o visual tiver animações ou funções assíncronas para renderização, o método `renderingFinished` deverá ser chamado após a animação ou dentro da função assíncrona.

```typescript
    export class Visual implements IVisual {
        ...
        private events: IVisualEventService;
        private element: HTMLElement;
        ...

        constructor(options: VisualConstructorOptions) {
            ...
            this.events = options.host.eventService;
            this.element = options.element;
            ...
        }

        public update(options: VisualUpdateOptions) {
            this.events.renderingStarted(options);
            ...
            // read more https://github.com/d3/d3-transition/blob/master/README.md#transition_end
            d3.select(this.element).transition().duration(100).style("opacity","0").end().then(() => {
                // renderingFinished called after transition end
                this.events.renderingFinished(options);
            });
        }
```

## <a name="rendering-events-for-visual-certification"></a>Renderizar eventos para a certificação de visuais

O suporte à renderização de eventos pelo visual é um dos requisitos da certificação de visuais. Leia mais sobre os [requisitos de certificação](https://docs.microsoft.com/power-bi/power-bi-custom-visuals-certified?#certification-requirements)
