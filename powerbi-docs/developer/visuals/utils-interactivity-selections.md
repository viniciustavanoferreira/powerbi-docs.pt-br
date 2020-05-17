---
title: Utilitários de interatividade de visuais do Power BI
description: O artigo descreve como adicionar seleções aos visuais do Power BI usando utilitários de interatividade
author: KesemSharabi
ms.author: kesharab
ms.reviewer: rkarlin
manager: rkarlin
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 02/24/2020
ms.openlocfilehash: f4d47347c98d19afdfbf07615842bfb4649dc1b9
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/05/2020
ms.locfileid: "79379250"
---
# <a name="power-bi-visuals-interactivity-utils"></a>Utilitários de interatividade de visuais do Power BI

Utilitários de interatividade (`InteractivityUtils`) é um conjunto de funções e classes que podem ser usadas para simplificar a implementação da seleção cruzada e da filtragem cruzada.

> [!NOTE]
> As novas atualizações dos utilitários de interatividade dão suporte apenas à versão mais recente das ferramentas (3.x.x e posterior).

## <a name="installation"></a>Instalação

1. Para instalar o pacote, execute o seguinte comando no diretório com seu projeto de visual atual do Power BI.

    ```bash
    npm install powerbi-visuals-utils-interactivityutils --save
    ```

2. Se você estiver usando a versão 3.0 ou posterior ou a ferramenta, instale `powerbi-models` para resolver as dependências.

    ```bash
    npm install powerbi-models --save
    ```

3. Para usar os utilitários de interatividade, importe o componente necessário no código-fonte do visual do Power BI.

    ```typescript
    import { interactivitySelectionService } from "powerbi-visuals-utils-interactivityutils";
    ```

### <a name="including-the-css-files"></a>Incluir os arquivos CSS

Para usar o pacote com seu visual do Power BI, importe o seguinte arquivo CSS ao seu arquivo `.less`.

`node_modules/powerbi-visuals-utils-interactivityutils/lib/index.css`

Importe o arquivo CSS como um arquivo `.less`, pois a ferramenta de visuais do Power BI encapsula as regras de CSS externas.

```less
@import (less) "node_modules/powerbi-visuals-utils-interactivityutils/lib/index.css";
```

## <a name="selectabledatapoint-properties"></a>Propriedades SelectableDataPoint

Geralmente, os pontos de dados contêm seleções e valores. A interface amplia a interface `SelectableDataPoint`.

`SelectableDataPoint` já contém propriedades, conforme descrito abaixo.

```typescript
  /** Flag for identifying that a data point was selected */
  selected: boolean;

  /** Identity for identifying the selectable data point for selection purposes */
  identity: powerbi.extensibility.ISelectionId;

  /*
   * A specific identity for when data points exist at a finer granularity than
   * selection is performed.  For example, if your data points select based
   * only on series, even if they exist as category/series intersections.
   */

  specificIdentity?: powerbi.extensibility.ISelectionId;
```

## <a name="defining-an-interface-for-data-points"></a>Definir uma interface para pontos de dados

1. Criar uma instância de utilitários de interatividade e salvar o objeto como uma propriedade do visual

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

2. Estenda a classe de comportamento base.

    > [!NOTE]
    > `BaseBehavior` foi introduzido na [versão 5.6.x dos utilitários de interatividade](https://www.npmjs.com/package/powerbi-visuals-utils-interactivityutils/v/5.6.0). Se você usar uma versão antiga, crie uma classe de comportamento da amostra abaixo.

3. Defina a interface para as opções de classe de comportamento.

    ```typescript
    import { SelectableDataPoint } from "./interactivitySelectionService";

    import {
        IBehaviorOptions,
        BaseDataPoint
    } from "./interactivityBaseService";

    export interface BaseBehaviorOptions<SelectableDataPointType extends BaseDataPoint> extends IBehaviorOptions<SelectableDataPointType> {

    /** d3 selection object of the main elements on the chart */
    elementsSelection: Selection<any, SelectableDataPoint, any, any>;

    /** d3 selection object of some elements on backgroup, to hadle click of reset selection */
    clearCatcherSelection: d3.Selection<any, any, any, any>;
    }
    ```

4. Defina uma classe para `visual behavior`. Ou estenda a classe `BaseBehavior`.

    **Definir uma classe para `visual behavior`**

    A classe é responsável por manipular os eventos de mouse `click` e `contextmenu`.

    Quando um usuário clica em elementos de dados, o visual chama o manipulador de seleção para selecionar pontos de dados. Se o usuário clicar no elemento de plano de fundo do visual, ele chamará o manipulador de seleção de limpeza.

    A classe tem os métodos correspondentes a seguir:
    * `bindClick`
    * `bindClearCatcher`
    * `bindContextMenu`.

    ```typescript
    export class Behavior<SelectableDataPointType extends BaseDataPoint> implements IInteractiveBehavior {

        /** d3 selection object of main elements in the chart */
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

    **Estender a classe `BaseBehavior`**

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

5. Para manipular elementos de clique, chame o método `on` do objeto de seleção *d3*. Isso também se aplica a `elementsSelection` e `clearCatcherSelection`.

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

6. Adicione um manipulador semelhante para o evento `contextmenu`, a fim de chamar o método `showContextMenu` do gerenciador de seleção.

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

7. Para atribuir funções aos manipuladores, os utilitários de interatividade chamam o método `bindEvents`. Adicione as seguintes chamadas ao método `bindEvents`:
    * `bindClick`
    * `bindClearCatcher`
    * `bindContextMenu`

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

8. O método `renderSelection` é responsável pela atualização do estado dos visuais no gráfico. Confira uma amostra da implementação de `renderSelection`.

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

9. A última etapa é criar uma instância de `visual behavior` e chamar o método `bind` da instância dos utilitários de interatividade.

    ```typescript
    this.interactivity.bind(<BaseBehaviorOptions<VisualDataPoint>>{
        behavior: this.behavior,
        dataPoints: this.categories,
        clearCatcherSelection: select(this.target),
        elementsSelection: selectionMerge
    });
    ```

    * `selectionMerge` é o objeto de seleção *d3*, que representa todos os elementos selecionáveis no visual.
    * `select(this.target)` é o objeto de seleção *d3*, que representa os elementos DOM principais do visual.
    * `this.categories` são pontos de dados com elementos, em que a interface é `VisualDataPoint` ou `categories: VisualDataPoint[];`.
    * `this.behavior` é uma nova instância de `visual behavior` criada no construtor do visual, conforme mostrado abaixo.

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
## <a name="next-steps"></a>Próximas etapas

* [Leia como lidar com seleções na alternância de indicadores](bookmarks-support.md#visuals-with-selection)

* [Leia como adicionar o menu de contexto para pontos de dados de visuais](context-menu.md)

* [Leia como usar o gerenciador de seleção para adicionar seleções nos visuais do Power BI](selection-api.md)
