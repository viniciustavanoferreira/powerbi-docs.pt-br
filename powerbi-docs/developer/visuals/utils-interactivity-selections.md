---
title: Utilitários de interatividade de visuais do Power BI
description: O artigo descreve como adicionar seleções aos visuais do Power BI usando utilitários de interatividade
author: zBritva
ms.author: v-ilgali
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 8a9218085b0da655d1ce4b3ece0b2666c4826c86
ms.sourcegitcommit: f7b28ecbad3e51f410eff7ee4051de3652e360e8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/13/2019
ms.locfileid: "74061858"
---
# <a name="microsoft-power-bi-visuals-interactivity-utils"></a>Utilitários de interatividade de visuais do Microsoft Power BI

InteractivityUtils é um conjunto de funções e classes para simplificar a implementação da seleção cruzada e da filtragem cruzada para visuais personalizados do Power BI.

## <a name="installation"></a>Instalação

> [!NOTE]
> Se você continuar usando a versão antiga do powerbi-visuals-tools (número de versão menor que 3.x.x), instale a nova versão das ferramentas (3.x.x).

> [!IMPORTANT]
> As novas atualizações dos utilitários de interatividade oferecem suporte apenas à versão mais recente das ferramentas. [Leia mais, como atualizar seu código de visuais para usar com as ferramentas mais recentes](migrate-to-new-tools.md)

Para instalar o pacote, você deve executar o seguinte comando no diretório com seu visual personalizado atual:

```bash
npm install powerbi-visuals-utils-interactivityutils --save
```

A partir da versão 3.0 ou posterior, você também precisa instalar o ```powerbi-models``` para resolver dependências.

```bash
npm install powerbi-models --save
```

Para utilitários de interatividade do usuário, você precisa importar o componente necessário no código-fonte do visual.

```typescript
import { interactivitySelectionService } from "powerbi-visuals-utils-interactivityutils";
```

### <a name="including-css-artifacts-to-the-custom-visual"></a>Incluir artefatos CSS para o visual personalizado

Para usar o pacote com seus visuais personalizados, você deve importar o seguinte arquivo CSS para o arquivo `your.less`:

`node_modules/powerbi-visuals-utils-interactivityutils/lib/index.css`

Como resultado, você terá a seguinte estrutura de arquivo:

```less
@import (less) "node_modules/powerbi-visuals-utils-interactivityutils/lib/index.css";
```

> [!NOTE]
> Você deve importar o arquivo .css como arquivo .less porque as Ferramentas de Visuais do Power BI agrupam as regras CSS externas.

## <a name="usage"></a>Uso

### <a name="define-interface-for-data-points"></a>Definir uma interface para pontos de dados

Geralmente, os pontos de dados contêm seleções e valores. A interface estende a interface `SelectableDataPoint`. `SelectableDataPoint` já contém propriedades:

```typescript
  /** Flag for identifying that data point was selected */
  selected: boolean;
  /** Identity for identifying the selectable data point for selection purposes */
  identity: powerbi.extensibility.ISelectionId;
  /**
   * A specific identity for when data points exist at a finer granularity than
   * selection is performed.  For example, if your data points should select based
   * only on series even if they exist as category/series intersections.
   */
  specificIdentity?: powerbi.extensibility.ISelectionId;
```

A primeira etapa do uso de utilitários de interatividade é criar uma instância dos utilitários de interatividade e salvar o objeto como propriedade do visual

```typescript
export class Visual implements IVisual {
  // ...
  private interactivity: interactivityBaseService.IInteractivityService<VisualDataPoint>;
  // ...
  constructor(options: VisualConstructorOptions) {
      // ...
      this.interactivity = interactivitySelectionService.createInteractivitySelectionService(this.host);
      // ...
  }
}
```

```typescript
import { interactivitySelectionService } from "powerbi-visuals-utils-interactivityutils";

export interface VisualDataPoint extends interactivitySelectionService.SelectableDataPoint {
    value: powerbi.PrimitiveValue;
}
```

A segunda etapa é estender a classe de comportamento base:

> [!NOTE]
> BaseBehavior introduzido na [versão 5.6. x dos utilitários de interatividade](https://www.npmjs.com/package/powerbi-visuals-utils-interactivityutils/v/5.6.0). Se você usar a versão antiga, crie uma classe de comportamento a partir da amostra abaixo (a classe `BaseBehavior` é a mesma):

Defina a interface para as opções da classe de comportamento:

```typescript
import { SelectableDataPoint } from "./interactivitySelectionService";

import {
    IBehaviorOptions,
    BaseDataPoint
} from "./interactivityBaseService";

export interface BaseBehaviorOptions<SelectableDataPointType extends BaseDataPoint> extends IBehaviorOptions<SelectableDataPointType> {
    /** D3 selection object of main elements on the chart */
    elementsSelection: Selection<any, SelectableDataPoint, any, any>;
    /** D3 selection object of some element on backgroup to hadle click of reset selection */
    clearCatcherSelection: d3.Selection<any, any, any, any>;
}
```

Defina a classe para `visual behaviour`. A classe responsável por manipular os eventos de mouse `click` e `contextmenu`.
Ao usar cliques para elementos de dados, o visual chama o manipulador de seleção para selecionar pontos de dados. Ou desmarque a seleção se o usuário clicar no elemento em segundo plano do visual. E a classe tem os métodos correspondentes: `bindClick`, `bindClearCatcher`, `bindContextMenu`.

```typescript
export class Behavior<SelectableDataPointType extends BaseDataPoint> implements IInteractiveBehavior {
    /** D3 selection object of main elements on the chart */
    protected options: BaseBehaviorOptions<SelectableDataPointType>;
    protected selectionHandler: ISelectionHandler;

    protected bindClick() {
      // ...
    }

    protected bindClearCatcher() {
      // ...
    }

    protected bindContextMenu() {
      // ...
    }

    public bindEvents(
        options: BaseBehaviorOptions<SelectableDataPointType>,
        selectionHandler: ISelectionHandler): void {
      // ...
    }

    public renderSelection(hasSelection: boolean): void {
      // ...
    }
}
```

ou você pode estender a classe `BaseBehavior`:

```typescript
import powerbi from "powerbi-visuals-api";
import { interactivitySelectionService, baseBehavior } from "powerbi-visuals-utils-interactivityutils";

export interface VisualDataPoint extends interactivitySelectionService.SelectableDataPoint {
    value: powerbi.PrimitiveValue;
}

export class Behavior extends baseBehavior.BaseBehavior<VisualDataPoint> {
  // ...
}
```

Para manipular o clique nos elementos, chame o método `on` do objeto de seleção D3 (para elementsSelection e clearCatcherSelection também):

```typescript
protected bindClick() {
  const {
      elementsSelection
  } = this.options;

  elementsSelection.on("click", (datum) => {
      const mouseEvent: MouseEvent = getEvent() as MouseEvent || window.event as MouseEvent;
      mouseEvent && this.selectionHandler.handleSelection(
          datum,
          mouseEvent.ctrlKey);
  });
}
```

Adicione um manipulador semelhante para o evento `contextmenu` chamar o método `showContextMenu` do gerenciador de seleção:

```typescript
protected bindContextMenu() {
    const {
        elementsSelection
    } = this.options;

    elementsSelection.on("contextmenu", (datum) => {
        const event: MouseEvent = (getEvent() as MouseEvent) || window.event as MouseEvent;
        if (event) {
            this.selectionHandler.handleContextMenu(
                datum,
                {
                    x: event.clientX,
                    y: event.clientY
                });
            event.preventDefault();
        }
    });
}
```

Os utilitários de interatividade chamam métodos `bindEvents` para atribuir funções a manipuladores e adicionam chamadas de `bindClick`, `bindClearCatcher` e `bindContextMenu` ao método `bindEvents`:

```typescript
  public bindEvents(
      options: BaseBehaviorOptions<SelectableDataPointType>,
      selectionHandler: ISelectionHandler): void {

      this.options = options;
      this.selectionHandler = selectionHandler;

      this.bindClick();
      this.bindClearCatcher();
      this.bindContextMenu();
  }
```

O método `renderSelection` responsável pela atualização do estado dos visuais no gráfico.

A amostra do método de implementação `renderSelection`:

```typescript
public renderSelection(hasSelection: boolean): void {
    this.options.elementsSelection.style("opacity", (category: any) => {
        if (category.selected) {
            return 0.5;
        } else {
            return 1;
        }
    });
}
```

A última etapa é criar a instância de `visual behavior` e chamada do método `bind` da instância dos utilitários de interatividade:

```typescript
this.interactivity.bind(<BaseBehaviorOptions<VisualDataPoint>>{
    behavior: this.behavior,
    dataPoints: this.categories,
    clearCatcherSelection: select(this.target),
    elementsSelection: selectionMerge
});
```

* `selectionMerge` é o objeto de seleção D3, o qual representa todos os elementos selecionáveis no visual.

* `select(this.target)` é o objeto de seleção D3, que representa os principais elementos DOm do visual.

* Pontos de dados `this.categories` com elementos, em que a interface é `VisualDataPoint` (ou `categories: VisualDataPoint[];`)

* `this.behavior` é uma nova instância de `visual behavior`

  criada no construtor do visual:

  ```typescript
  export class Visual implements IVisual {
    // ...
    constructor(options: VisualConstructorOptions) {
        // ...
        this.behavior = new Behavior();
    }
    // ...
  }
  ```

Agora, seu visual está pronto para a seleção de manipulador.

## <a name="next-steps"></a>Próximas etapas

* [Leia como lidar com seleções na alternância de indicadores](bookmarks-support.md#visuals-with-selection)

* [Leia como adicionar o menu de contexto para pontos de dados de visuais](context-menu.md)

* [Leia como usar o gerenciador de seleção para adicionar seleções nos visuais do Power BI](selection-api.md)
