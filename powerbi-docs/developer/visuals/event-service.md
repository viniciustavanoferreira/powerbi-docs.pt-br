---
title: Renderizar eventos em visuais do Power BI
description: Os visuais do Power BI podem notificar o Power BI que estão prontos para exportar para o PowerPoint ou para PDF.
author: Yarovinsky
ms.author: alexyar
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: b481ce94e5025045466a05d71e30a00f02be7ead
ms.sourcegitcommit: b602cdffa80653bc24123726d1d7f1afbd93d77c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70237154"
---
# <a name="render-events-in-power-bi-visuals"></a>Renderizar eventos em visuais do Power BI

A nova API consiste em três métodos (`started`, `finished` ou `failed`) que devem ser chamados durante a renderização.

Quando a renderização é iniciada, o código do visual do Power BI chama o método `renderingStarted` para indicar que o processo de renderização foi iniciado.

Se a renderização for concluída com êxito, o código do visual do Power BI chamará imediatamente o método `renderingFinished`, notificando os ouvintes (principalmente *Exportar para PDF* e *Exportar para o PowerPoint*) de que a imagem do visual está pronta para a exportação.

Se ocorrer um problema durante o processo, o visual do Power BI não poderá ser renderizado com êxito. Para notificar os ouvintes de que o processo de renderização não foi concluído, o código do visual do Power BI visual deve chamar o método `renderingFailed`. Esse método também fornece uma cadeia de caracteres opcional para informar um motivo para a falha.

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
     * Should be called just before the actual rendering starts, 
     * usually at the start of the update method
     *
     * @param options - the visual update options received as an update parameter
     */
    renderingStarted(options: VisualUpdateOptions): void;

    /**
     * Should be called immediately after rendering finishes successfully
     * 
     * @param options - the visual update options received as an update parameter
     */
    renderingFinished(options: VisualUpdateOptions): void;

    /**
     * Called when rendering fails, with an optional reason string
     * 
     * @param options - the visual update options received as an update parameter
     * @param reason - the optional failure reason string
     */
    renderingFailed(options: VisualUpdateOptions, reason?: string): void;
}
```

### <a name="sample-the-visual-displays-no-animations"></a>Exemplo: O visual não exibe animações

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

### <a name="sample-the-visual-displays-animations"></a>Exemplo: O visual exibe animações

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
            // Learn more at https://github.com/d3/d3-transition/blob/master/README.md#transition_end
            d3.select(this.element).transition().duration(100).style("opacity","0").end().then(() => {
                // renderingFinished called after transition end
                this.events.renderingFinished(options);
            });
        }
```

## <a name="rendering-events-for-visual-certification"></a>Renderizar eventos para a certificação de visuais

Um requisito da certificação de visuais é o suporte para renderizar eventos pelo visual. Para obter mais informações, confira [requisitos de certificação](https://docs.microsoft.com/power-bi/power-bi-custom-visuals-certified?#certification-requirements).
