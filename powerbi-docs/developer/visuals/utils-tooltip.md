---
title: Introdução ao uso de utilitários de dicas de ferramentas no visual do Power BI
description: Este artigo descreve como usar utilitários de dicas de ferramentas para simplificar a personalização dessas dicas em visuais do Power BI
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 02/14/2020
ms.openlocfilehash: 6f4aa276438d84825c4c7aba6872210b5f3a6564
ms.sourcegitcommit: d55d3089fcb3e78930326975957c9940becf2e76
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/04/2020
ms.locfileid: "78264210"
---
# <a name="tooltip-utils"></a>Utilitários de dicas de ferramentas
Este artigo ajuda a instalar, importar e usar utilitários de dicas de ferramentas. Tratam-se de utilitários convenientes para a personalização de qualquer dica de ferramenta em visuais do Power BI.

## <a name="requirements"></a>Requisitos
Para usar o pacote, é necessário ter o seguinte:
* [node.js](https://nodejs.org) (recomendamos a versão LTS mais recente)
* [npm](https://www.npmjs.com/) (a versão mínima com suporte é a 3.0.0)
* O visual personalizado criado por [PowerBI-visuals-tools](https://www.npmjs.com/package/powerbi-visuals-tools)

## <a name="installation"></a>Instalação

Para instalar o pacote, você deve executar o seguinte comando no diretório com seu visual atual:

```bash
npm install powerbi-visuals-utils-colorutils --save
```
Esse comando instala e adiciona um pacote como uma dependência no ```package.json```

## <a name="usage"></a>Uso

> O Guia de Uso descreve uma API pública do pacote. Você encontrará uma descrição e alguns exemplos de cada interface pública do pacote.

O conteúdo desse pacote fornece uma maneira de criar `TooltipServiceWrapper` e métodos para ajudar a manipular ações de dicas de ferramentas. Ele utiliza as interfaces de dicas de ferramentas – `ITooltipServiceWrapper`, `TooltipEventArgs`, `TooltipEnabledDataPoint`. 

Também tem métodos específicos (manipuladores de eventos de toque) relacionados ao desenvolvimento para dispositivos móveis: `touchEndEventName`, `touchStartEventName`, `usePointerEvents`.

`TooltipServiceWrapper` fornece a maneira mais simples de manipular dicas de ferramentas.

Esse módulo fornece a seguinte função e interface:
* [ITooltipServiceWrapper](#itooltipservicewrapper)
  * [addTooltip](#itooltipservicewrapperaddtooltip)
  * [hide](#itooltipservicewrapperhide)

* [Interfaces](#interfaces)
  * [TooltipEventArgs](#tooltipeventargs)
  * [TooltipEnabledDataPoint](#tooltipenableddatapoint)
  * [TooltipServiceWrapperOptions](#tooltipservicewrapperoptions)
* [Eventos de toque](#touch-events)

### `createTooltipServiceWrapper`
Essa função cria uma instância do ITooltipServiceWrapper.

```typescript
function createTooltipServiceWrapper(tooltipService: ITooltipService, rootElement: Element, handleTouchDelay?: number,  getEventMethod?: () => MouseEvent): ITooltipServiceWrapper;
```

O ```ITooltipService``` está disponível em [IVisualHost](https://github.com/microsoft/PowerBI-visuals-tools/blob/master/templates/visuals/.api/v2.6.0/PowerBI-visuals.d.ts#L1335).

**Exemplo**

```typescript
import { createTooltipServiceWrapper } from "powerbi-visuals-utils-tooltiputils";

export class YourVisual implements IVisual {
    // implementation of IVisual.

    constructor(options: VisualConstructorOptions) {
        createTooltipServiceWrapper(
            options.host.tooltipService,
            options.element);

        // returns: an instance of ITooltipServiceWrapper.
    }
}
```

Você pode dar uma olhada no código de exemplo do visual personalizado [aqui](https://github.com/microsoft/powerbi-visuals-gantt/blob/master/src/gantt.ts#L391).

### `ITooltipServiceWrapper`
Essa interface descreve métodos públicos e propriedades do TooltipService.

```typescript
interface ITooltipServiceWrapper {
    addTooltip<T>(selection: d3.Selection<any, any, any, any>, getTooltipInfoDelegate: (args: TooltipEventArgs<T>) => powerbi.extensibility.VisualTooltipDataItem[], getDataPointIdentity?: (args: TooltipEventArgs<T>) => powerbi.visuals.ISelectionId, reloadTooltipDataOnMouseMove?: boolean): void;
    hide(): void;
}
```

#### `ITooltipServiceWrapper.addTooltip`

Esse método adiciona dicas de ferramentas à seleção atual.

```typescript
addTooltip<T>(selection: d3.Selection<any>, getTooltipInfoDelegate: (args: TooltipEventArgs<T>) => VisualTooltipDataItem[], getDataPointIdentity?: (args: TooltipEventArgs<T>) => ISelectionId, reloadTooltipDataOnMouseMove?: boolean): void;
```

**Exemplo**

```typescript
import { createTooltipServiceWrapper, TooltipEventArgs, ITooltipServiceWrapper, TooltipEnabledDataPoint } from "powerbi-visuals-utils-tooltiputils";

let bodyElement = d3.select("body");

let element = bodyElement
    .append("div")
    .style({
        "background-color": "green",
        "width": "150px",
        "height": "150px"
    })
    .classed("visual", true)
    .data([{
        tooltipInfo: [{
            displayName: "Power BI",
            value: 2016
        }]
    }]);

let tooltipServiceWrapper: ITooltipServiceWrapper = createTooltipServiceWrapper(tooltipService, bodyElement.get(0)); // tooltipService is from the IVisualHost.

tooltipServiceWrapper.addTooltip<TooltipEnabledDataPoint>(element, (eventArgs: TooltipEventArgs<TooltipEnabledDataPoint>) => {
    return eventArgs.data.tooltipInfo;
});

// You will see a tooltip if you mouseover the element.
```

Você pode dar uma olhada no código de exemplo do visual personalizado [aqui](https://github.com/microsoft/powerbi-visuals-gantt/blob/master/src/gantt.ts#L2931).

Além disso, preste atenção no seguinte exemplo de personalização de dica de ferramenta no visual personalizado de Gantt [aqui](https://github.com/microsoft/powerbi-visuals-gantt/blob/master/src/gantt.ts#L573-L648)

### `ITooltipServiceWrapper.hide`

Esse método oculta a dica de ferramenta.

```typescript
hide(): void;
```

**Exemplo**

```typescript
import {createTooltipServiceWrapper} from "powerbi-visuals-utils-tooltiputils";

let tooltipServiceWrapper = createTooltipServiceWrapper(options.host.tooltipService, options.element); // options are from the VisualConstructorOptions.

tooltipServiceWrapper.hide();
```
### `Interfaces`
Essas interfaces são usadas durante a criação e o uso do TooltipServiceWrapper. Também são mencionadas nos exemplos do tópico anterior [aqui](#itooltipservicewrapperaddtooltip).

#### `TooltipEventArgs`
```typescript
interface TooltipEventArgs<TData> {
    data: TData;
    coordinates: number[];
    elementCoordinates: number[];
    context: HTMLElement;
    isTouchEvent: boolean;
}
```

#### `TooltipEnabledDataPoint`
```typescript
interface TooltipEnabledDataPoint {
    tooltipInfo?: powerbi.extensibility.VisualTooltipDataItem[];
}
```

#### `TooltipServiceWrapperOptions`
```typescript
interface TooltipServiceWrapperOptions {
    tooltipService: ITooltipService;
    rootElement: Element;
    handleTouchDelay: number;
    getEventMethod?: () => MouseEvent;
```

### `Touch events`

Agora os utilitários de dicas de ferramentas têm a capacidade de manipular vários eventos de toque convenientes ao desenvolvimento para dispositivos móveis.

#### `touchStartEventName`
```typescript
function touchStartEventName(): string
```
Esse método retorna o nome do evento de início de toque.

#### `touchEndEventName`
```typescript
function touchEndEventName(): string
```
Esse método retorna o nome do evento de início de toque.

#### `usePointerEvents`
```typescript
function usePointerEvents(): boolean
```
Esse método retorna se o evento touchStart atual está relacionado ou não ao ponteiro.
