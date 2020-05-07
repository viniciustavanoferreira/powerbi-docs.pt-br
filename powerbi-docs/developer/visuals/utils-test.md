---
title: Introdução ao uso de utilitários de teste em visuais do Power BI
description: Este artigo descreve como usar os utilitários de teste simplificam o uso de simulações e métodos específicos em testes de unidade dos visuais do Power BI
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 02/14/2020
ms.openlocfilehash: c50ad894b2e1f5eb838abdd4442f473f8bcbbb10
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82196596"
---
# <a name="power-bi-visuals-test-utils"></a>Utilitários de teste dos visuais do Power BI

Este artigo ajudará você a instalar, importar e usar os utilitários de teste dos visuais do Power BI. Esses utilitários de teste podem ser usados para testes de unidade e incluem simulações e métodos para elementos como exibições de dados, seleções e esquemas de cores.

## <a name="requirements"></a>Requisitos

Para usar este pacote, você precisará instalar o seguinte:

* [Node.js](https://nodejs.org), versão LTS (recomendada)
* [npm](https://www.npmjs.com/), versão 3.0.0 ou superior
* O pacote [PowerBI-visuals-tools](https://github.com/Microsoft/PowerBI-visuals-tools)

## <a name="installation"></a>Instalação

Para instalar os utilitários de teste e adicionar as respectivas dependências ao *package.json*, execute o seguinte comando no diretório de visuais do Power BI:

```bash
npm install powerbi-visuals-utils-testutils --save
```

O exemplo a seguir fornece descrições e exemplos na API pública de utilitários de teste.

## <a name="visualbuilderbase"></a>VisualBuilderBase

Usado por **VisualBuilder** em testes de unidade com os métodos usados com mais frequência `build`, `update` e `updateRenderTimeout`. 

O método `build` retorna uma instância criada do visual.

Os métodos `enumerateObjectInstances` e `updateEnumerateObjectInstancesRenderTimeout` são necessários para verificar as alterações nas opções de bucket e de formatação.

```typescript
abstract class VisualBuilderBase<T extends IVisual> {
    element: JQuery;
    viewport: IViewport;
    visualHost: IVisualHost;
    protected visual: T;
    constructor(width?: number, height?: number, guid?: string, element?: JQuery);
    protected abstract build(options: VisualConstructorOptions): T;
     nit(): void;
    destroy(): void;
    update(dataView: DataView[] | DataView): void;
    updateRenderTimeout(dataViews: DataView[] | DataView, fn: Function, timeout?: number): number;
    updateEnumerateObjectInstancesRenderTimeout(dataViews: DataView[] | DataView, options: EnumerateVisualObjectInstancesOptions, fn: (enumeration: VisualObjectInstance[]) => void, timeout?: number): number;
    updateFlushAllD3Transitions(dataViews: DataView[] | DataView): void;
    updateflushAllD3TransitionsRenderTimeout(dataViews: DataView[] | DataView, fn: Function, timeout?: number): number;
    enumerateObjectInstances(options: EnumerateVisualObjectInstancesOptions): VisualObjectInstance[];
}
```

> [!NOTE]
> Para obter mais exemplos, confira [Como escrever testes de unidade para VisualBuilderBase](./unit-tests-introduction.md#create-a-visual-instance-builder) e um [cenário de uso real de VisualBuilderBase](https://github.com/microsoft/powerbi-visuals-gantt/blob/master/test/visualBuilder.ts).

## <a name="dataviewbuilder"></a>DataViewBuilder

Usado por **TestDataViewBuilder**, esse módulo fornece uma classe **CategoricalDataViewBuilder** usada no método `createCategoricalDataViewBuilder`. Também especifica as interfaces e os métodos necessários para trabalhar com uma **DataView** fictícia em testes de unidade.

* `withValues` adiciona colunas de série estática e `withGroupedValues` adiciona colunas de série dinâmica

  Não aplique a série dinâmica e a série estática a **DataViewCategorical** de um visual. Você só pode usá-las na consulta **DataViewCategorical**, em que **DataViewTransform** deverá dividi-las em objetos **DataViewCategorical** separados do visual.

* `build` retorna a DataView com metadados e DataViewCategorical

  `build` retorna **Undefined** se a combinação de parâmetros é inválida, como a inclusão de séries dinâmicas e estáticas ao criar a **DataView** do visual.

```typescript
class CategoricalDataViewBuilder implements IDataViewBuilderCategorical {
    withCategory(options: DataViewBuilderCategoryColumnOptions): IDataViewBuilderCategorical;
    withCategories(categories: DataViewCategoryColumn[]): IDataViewBuilderCategorical;
    withValues(options: DataViewBuilderValuesOptions): IDataViewBuilderCategorical;
    withGroupedValues(options: DataViewBuilderGroupedValuesOptions): IDataViewBuilderCategorical;
    build(): DataView;
}

function createCategoricalDataViewBuilder(): IDataViewBuilderCategorical;
```

## <a name="testdataviewbuilder"></a>TestDataViewBuilder

Usado para a criação de **VisualData** em testes de unidade. Quando os dados são colocados em buckets de campo de dados, o Power BI Produz um objeto **DataView** categórico com base nos dados. O **TestDataViewBuilder** ajuda a simular a criação de uma **DataView** categórica.

```typescript
abstract class TestDataViewBuilder {
    static DataViewName: string;
    private aggregateFunction;
    static setDefaultQueryName(source: DataViewMetadataColumn): DataViewMetadataColumn;
    static getDataViewBuilderColumnIdentitySources(options: TestDataViewBuilderColumnOptions[] | TestDataViewBuilderColumnOptions): DataViewBuilderColumnIdentitySource[];
    static getValuesTable(categories?: DataViewCategoryColumn[], values?: DataViewValueColumn[]): any[][];
    static createDataViewBuilderColumnOptions(categoriesColumns: (TestDataViewBuilderCategoryColumnOptions | TestDataViewBuilderCategoryColumnOptions[])[], valuesColumns: (DataViewBuilderValuesColumnOptions | DataViewBuilderValuesColumnOptions[])[], filter?: (options: TestDataViewBuilderColumnOptions) => boolean, customizeColumns?: CustomizeColumnFn): DataViewBuilderAllColumnOptions;
    static setUpDataViewBuilderColumnOptions(options: DataViewBuilderAllColumnOptions, aggregateFunction: (array: number[]) => number): DataViewBuilderAllColumnOptions;
    static setUpDataView(dataView: DataView, options: DataViewBuilderAllColumnOptions): DataView;
    protected createCategoricalDataViewBuilder(categoriesColumns: (TestDataViewBuilderCategoryColumnOptions | TestDataViewBuilderCategoryColumnOptions[])[], valuesColumns: (DataViewBuilderValuesColumnOptions | DataViewBuilderValuesColumnOptions[])[], columnNames: string[], customizeColumns?: CustomizeColumnFn): IDataViewBuilderCategorical;
    abstract getDataView(columnNames?: string[]): DataView;
}
```

  A seguinte lista apresenta as interfaces usadas com mais frequência ao criar uma `testDataView`:

  ```typescript
  interface TestDataViewBuilderColumnOptions extends DataViewBuilderColumnOptions {
      values: any[];
  }

  interface TestDataViewBuilderCategoryColumnOptions extends TestDataViewBuilderColumnOptions {
      objects?: DataViewObjects[];
      isGroup?: boolean;
  }

  interface DataViewBuilderColumnOptions {
      source: DataViewMetadataColumn;
  }

  interface DataViewBuilderSeriesData {
      values: PrimitiveValue[];
      highlights?: PrimitiveValue[];
      /** Client-computed maximum value for a column. */
      maxLocal?: any;
      /** Client-computed maximum value for a column. */
      minLocal?: any;
  }

  interface DataViewBuilderColumnIdentitySource {
      fields: any[];
      identities?: CustomVisualOpaqueIdentity[];
  }
  ```
   
> [!NOTE]
> Para obter mais exemplos, confira [Como escrever testes de unidade para TestDataViewBuilder](./unit-tests-introduction.md#how-to-add-static-data-for-unit-tests) e um [cenário de uso real de TestDataViewBuilder](https://github.com/microsoft/powerbi-visuals-gantt/blob/master/test/visualData.ts).

## <a name="mocks"></a>Simulações

### <a name="mockivisualhost"></a>MockIVisualHost

Implementa **IVisualHost** para testar os visuais do Power BI sem dependências externas, como a estrutura do Power BI.

Os métodos úteis incluem `createSelectionIdBuilder`, `createSelectionManager`, `createLocalizationManager` e as propriedades getter.

```typescript
import powerbi from "powerbi-visuals-api";

import VisualObjectInstancesToPersist = powerbi.VisualObjectInstancesToPersist;
import ISelectionIdBuilder = powerbi.visuals.ISelectionIdBuilder;
import ISelectionManager = powerbi.extensibility.ISelectionManager;
import IColorPalette = powerbi.extensibility.IColorPalette;
import IVisualEventService = powerbi.extensibility.IVisualEventService;
import ITooltipService = powerbi.extensibility.ITooltipService;
import IVisualHost = powerbi.extensibility.visual.IVisualHost;

class MockIVisualHost implements IVisualHost {
      constructor(
          colorPalette?: IColorPalette,
          selectionManager?: ISelectionManager,
          tooltipServiceInstance?: ITooltipService,
          localeInstance?: MockILocale,
          allowInteractionsInstance?: MockIAllowInteractions,
          localizationManager?: powerbi.extensibility.ILocalizationManager,
          telemetryService?: powerbi.extensibility.ITelemetryService,
          authService?: powerbi.extensibility.IAuthenticationService,
          storageService?: ILocalVisualStorageService,
          eventService?: IVisualEventService);
      createSelectionIdBuilder(): ISelectionIdBuilder;
      createSelectionManager(): ISelectionManager;
      createLocalizationManager(): ILocalizationManager;
      colorPalette: IColorPalette;
      locale: string;
      telemetry: ITelemetryService;
      tooltipService: ITooltipService;
      allowInteractios: boolean;
      storageService: ILocalVisualStorageService;
      eventService: IVisualEventService;
      persistProperties(changes: VisualObjectInstancesToPersist): void;
}
```
   
- `createVisualHost` cria e retorna uma instância de **IVisualHost**, na verdade, **MockIVisualHost**
  ```typescript
  function createVisualHost(locale?: Object, allowInteractions?: boolean, colors?: IColorInfo[], isEnabled?: boolean, displayNames?: any, token?: string): IVisualHost;
  ```

    Exemplo
    ```typescript
    import { createVisualHost } from "powerbi-visuals-utils-testutils"

    let host: IVisualHost = createVisualHost();
    ```

> [!IMPORTANT]
> **MockIVisualHost** é uma implementação fictícia de **IVisualHost** e só deve ser usada com testes de unidade.

### <a name="mockicolorpalette"></a>MockIColorPalette

Implementa **IColorPalette** para testar os visuais do Power BI sem dependências externas, como a estrutura do Power BI.

**MockIColorPalette** fornece propriedades úteis para verificar o esquema de cores ou o modo de alto contraste em testes de unidade.

  ```typescript
  import powerbi from "powerbi-visuals-api";
  import IColorPalette = powerbi.extensibility.ISandboxExtendedColorPalette;
  import IColorInfo = powerbi.IColorInfo;

  class MockIColorPalette implements IColorPalette {
      constructor(colors?: IColorInfo[]);
      getColor(key: string): IColorInfo;
      reset(): IColorPalette;
      isHighContrastMode: boolean;
      foreground: {value: string};
      foregroundLight: {value: string};
      ...
      background: {value: string};
      backgroundLight: {value: string};
      ...
      shapeStroke: {value: string};
  }
  ```
  - `createColorPalette` cria e retorna uma instância de **IColorPalette**, na verdade, **MockIColorPalette**
    ```typescript
    function createColorPalette(colors?: IColorInfo[]): IColorPalette;
    ```

    Exemplo
    ```typescript
    import { createColorPalette } from "powerbi-visuals-utils-testutils"

    let colorPalette: IColorPalette = createColorPalette();
    ```
    
> [!IMPORTANT]
> **MockIColorPalette** é uma implementação fictícia de **IColorPalette** e só deve ser usada com testes de unidade.

### <a name="mockiselectionid"></a>MockISelectionId

Implementa **ISelectionId** para testar os visuais do Power BI sem dependências externas, como a estrutura do Power BI.

  ```typescript
  import powerbi from "powerbi-visuals-api";
  import Selector = powerbi.data.Selector;
  import ISelectionId = powerbi.visuals.ISelectionId;

  class MockISelectionId implements ISelectionId {
      constructor(key: string);
      equals(other: ISelectionId): boolean;
      includes(other: ISelectionId, ignoreHighlight?: boolean): boolean;
      getKey(): string;
      getSelector(): Selector;
      getSelectorsByColumn(): Selector;
      hasIdentity(): boolean;
  }
  ```

  - `createSelectionId` cria e retorna uma instância de **ISelectionId**, na verdade, **MockISelectionId**
    ```typescript
    function createSelectionId(key?: string): ISelectionId;
    ```

    Exemplo
    ```typescript
    import { createColorPalette } from "powerbi-visuals-utils-testutils"

    let selectionId: ISelectionId = createSelectionId();
    ```
    
> [!NOTE]
> **MockISelectionId** é uma implementação fictícia de **ISelectionId** e só deve ser usada com testes de unidade.

### <a name="mockiselectionidbuilder"></a>MockISelectionIdBuilder

Implementa **ISelectionIdBuilder** para testar os visuais do Power BI sem dependências externas, como a estrutura do Power BI. 

  ```typescript
  import DataViewCategoryColumn = powerbi.DataViewCategoryColumn;
  import DataViewValueColumn = powerbi.DataViewValueColumn;
  import DataViewValueColumnGroup = powerbi.DataViewValueColumnGroup;
  import DataViewValueColumns = powerbi.DataViewValueColumns;
  import ISelectionIdBuilder = powerbi.visuals.ISelectionIdBuilder;
  import ISelectionId = powerbi.visuals.ISelectionId;

  class MockISelectionIdBuilder implements ISelectionIdBuilder {
      withCategory(categoryColumn: DataViewCategoryColumn, index: number): this;
      withSeries(seriesColumn: DataViewValueColumns, valueColumn: DataViewValueColumn | DataViewValueColumnGroup): this;
      withMeasure(measureId: string): this;
      createSelectionId(): ISelectionId;
      withMatrixNode(matrixNode: DataViewMatrixNode, levels: DataViewHierarchyLevel[]): this;
      withTable(table: DataViewTable, rowIndex: number): this;
  }
  ```

  - `createSelectionIdBuilder` cria e retorna uma instância de **ISelectionIdBuilder**, na verdade, **MockISelectionIdBuilder**
    ```typescript
    function createSelectionIdBuilder(): ISelectionIdBuilder;
    ```

    Exemplo
    ```typescript
    import { selectionIdBuilder } from "powerbi-visuals-utils-testutils";

    let selectionIdBuilder = createSelectionIdBuilder();
    ```

> [!NOTE]
> **MockISelectionIdBuilder** é uma implementação fictícia de **ISelectionIdBuilder** e só deve ser usada com testes de unidade.

### <a name="mockiselectionmanager"></a>MockISelectionManager

Implementa **ISelectionManager** para testar os visuais do Power BI sem dependências externas, como a estrutura do Power BI. 

  ```typescript
  import powerbi from "powerbi-visuals-api";
  import IPromise = powerbi.IPromise;
  import ISelectionId = powerbi.visuals.ISelectionId;
  import ISelectionManager = powerbi.extensibility.ISelectionManager;

  class MockISelectionManager implements ISelectionManager {
      select(selectionId: ISelectionId | ISelectionId[], multiSelect?: boolean): IPromise<ISelectionId[]>;
      hasSelection(): boolean;
      clear(): IPromise<{}>;
      getSelectionIds(): ISelectionId[];
      containsSelection(id: ISelectionId): boolean;
      showContextMenu(selectionId: ISelectionId, position: IPoint): IPromise<{}>;
      registerOnSelectCallback(callback: (ids: ISelectionId[]) => void): void;
      simutateSelection(selections: ISelectionId[]): void;
  }
  ```

  - `createSelectionManager` cria e retorna uma instância de **ISelectionManager**, na verdade, **MockISelectionManager**
    ```typescript
    function createSelectionManager(): ISelectionManager
    ```

    Exemplo
    ```typescript
    import { createSelectionManager } from "powerbi-visuals-utils-testutils";

    let selectionManager: ISelectionManager = createSelectionManager();
    ```

> [!NOTE]
> **MockISelectionManager** é uma implementação fictícia de **ISelectionManager** e só deve ser usada com testes de unidade.

### <a name="mockilocale"></a>MockILocale

  Define a localidade e a altera de acordo com as suas necessidades durante o processo de teste de unidade.
  ```typescript
  class MockILocale {
      constructor(locales?: Object): void; // Default locales are en-US and ru-RU 
      locale(key: string): void;// setter property
      locale(): string; // getter property
  }
  ```
  - `createLocale` cria e retorna uma instância de **MockILocale**
    ```typescript
    funciton createLocale(locales?: Object): MockILocale;
    ```

### <a name="mockitooltipservice"></a><a id="mockitooltipservice"></a> MockITooltipService
Simula `TooltipService` e o chama de acordo com as suas necessidades durante o processo de teste de unidade.
  ```typescript
  class MockITooltipService implements ITooltipService {
      constructor(isEnabled: boolean = true);
      enabled(): boolean;
      show(options: TooltipShowOptions): void;
      move(options: TooltipMoveOptions): void;
      hide(options: TooltipHideOptions): void;
  }
  ```
  - `createTooltipService` cria e retorna uma instância de **MockITooltipService**
    ```typescript
    function createTooltipService(isEnabled?: boolean): ITooltipService;
    ```

### <a name="mockiallowinteractions"></a>MockIAllowInteractions

```typescript
export class MockIAllowInteractions {
    constructor(public isEnabled?: boolean); // false by default
}
```
  - `createAllowInteractions` cria e retorna uma instância de **MockIAllowInteractions**
    ```typescript
    function createAllowInteractions(isEnabled?: boolean): MockIAllowInteractions;
    ```

### <a name="mockilocalizationmanager"></a><a id="mockilocalizationmanager"></a> MockILocalizationManager
Fornece habilidades básicas de **LocalizationManager**, que são necessárias para o teste de unidade.
```typescript
class MockILocalizationManager implements ILocalizationManager {
    constructor(displayNames: {[key: string]: string});
    getDisplayName(key: string): string; // returns default or setted displayNames for localized elements
}
```
  - `createLocalizationManager` cria e retorna uma instância de **ILocalizationManager**, na verdade, **MockILocalizationManager**
    ```typescript
    function createLocalizationManager(displayNames?: any): ILocalizationManager;
    ```

    Exemplo
    ```typescript
    import { createLocalizationManager } from "powerbi-visuals-utils-testutils";
    let localizationManagerMock: ILocalizationManager = createLocalizationManager();
    ```

### <a name="mockitelemetryservice"></a>MockITelemetryService
Simula o uso de **TelemetryService**.
```typescript
class MockITelemetryService implements ITelemetryService {
    instanceId: string;
    trace(veType: powerbi.VisualEventType, payload?: string) {
    }
}
```
  Criação de `MockITelemetryService`
    ```typescript
    function createTelemetryService(): ITelemetryService;
    ```
### <a name="mockiauthenticationservice"></a>MockIAuthenticationService
Simula o trabalho de **AuthenticationService** fornecendo um token fictício do AAD.
```typescript
class MockIAuthenticationService implements IAuthenticationService  {
    constructor(token: string);
    getAADToken(visualId?: string): powerbi.IPromise<string>
}
```
  - `createAuthenticationService` cria e retorna uma instância de **IAuthenticationService**, na verdade, **MockIAuthenticationService**
    ```typescript
    function createAuthenticationService(token?: string): IAuthenticationService;
    ```

### <a name="mockistorageservice"></a>MockIStorageService
Permite o uso de **ILocalVisualStorageService** com o mesmo comportamento de **LocalStorage**.
```typescript
class MockIStorageService implements ILocalVisualStorageService {
  get(key: string): IPromise<string>;
  set(key: string, data: string): IPromise<number>;
  remove(key: string): void;
}
```
  - `createStorageService` cria e retorna uma instância de **ILocalVisualStorageService**, na verdade, **MockIStorageService**
    ```typescript
    function createStorageService(): ILocalVisualStorageService;
    ```

### <a name="mockieventservice"></a>MockIEventService
```typescript
import powerbi from "powerbi-visuals-api";
import IVisualEventService = powerbi.extensibility.IVisualEventService;
import VisualUpdateOptions = powerbi.extensibility.VisualUpdateOptions;

class MockIEventService implements IVisualEventService {
      renderingStarted(options: VisualUpdateOptions): void;
      renderingFinished(options: VisualUpdateOptions): void;
      renderingFailed(options: VisualUpdateOptions, reason?: string): void;
}
```
  - `createEventService` cria e retorna uma instância de **IVisualEventService**, na verdade, **MockIEventService**
    ```typescript
    function createEventService(): IVisualEventService;
    ```

## <a name="utils"></a>Utilitários

Os utilitários incluem métodos auxiliares para testes de unidade dos visuais do Power BI, incluindo auxiliares relacionados a cores, números e eventos.

- `renderTimeout` retorna o tempo limite
  ```typescript
  function renderTimeout(fn: Function, timeout: number = DefaultWaitForRender): number
  ```

- `testDom` ajuda a definir um acessório em testes de unidade
  ```typescript
  function testDom(height: number | string, width: number | string): JQuery
  ```
  Exemplo
  ```typescript
  import { testDom }  from "powerbi-visuals-utils-testutils";
  describe("testDom", () => {
      it("should return an element", () => {
          let element: JQuery = testDom(500, 500);
          expect(element.get(0)).toBeDefined();
      });
  });
  ```

### <a name="color-related-helper-methods"></a>Métodos auxiliares relacionados a cores

- `getSolidColorStructuralObject`
  ```typescript
  function getSolidColorStructuralObject(color: string): any
  ```
  Retorna a seguinte estrutura:

  ```json
  { solid: { color: color } }
  ```

- `assertColorsMatch` compara objetos **RgbColor** analisados com base em cadeias de caracteres de entrada
  ```typescript
  function assertColorsMatch(actual: string, expected: string, invert: boolean = false): boolean
  ```

- `parseColorString` analisa a cor com base na cadeia de caracteres de entrada e a retorna na **RgbColor** da interface especificada
  ```typescript
  function parseColorString(color: string): RgbColor
  ```

### <a name="number-related-helper-methods"></a>Métodos auxiliares relacionados a números

- `getRandomNumbers` gera um número aleatório usando os valores mínimo e máximo. Você pode especificar `exceptionList` e fornecer uma função para a alteração do resultado.
  ```typescript
  function getRandomNumber(
      min: number,
      max: number,
      exceptionList?: number[],
      changeResult: (value: any) => number = x => x): number
  ```

- `getRandomNumbers` fornece uma matriz de números aleatórios gerados pelo método `getRandomNumber` com os valores mínimo e máximo especificados
  ```typescript
  function getRandomNumbers(count: number, min: number = 0, max: number = 1): number[]
  ```

### <a name="event-related-helper-methods"></a>Métodos auxiliares relacionados a eventos
Os métodos a seguir são escritos para a simulação de eventos de página da Web em testes de unidade.

- `clickElement` simula um clique no elemento especificado
  ```typescript
  function clickElement(element: JQuery, ctrlKey: boolean = false): void
  ```

- `createTouch` retorna um objeto **Touch** para ajudar a simular um evento de toque
  ```typescript
  function createTouch(x: number, y: number, element: JQuery, id: number = 0): Touch
  ```

- `createTouchesList` retorna uma lista de eventos de **Touch** simulados
  ```typescript
  function createTouchesList(touches: Touch[]): TouchList
  ```

- `createContextMenuEvent` retorna **MouseEvent**
  ```typescript
  function createContextMenuEvent(x: number, y: number): MouseEvent
  ```

- `createMouseEvent` cria e retorna **MouseEvent**
  ```typescript
  function createMouseEvent(
      mouseEventType: MouseEventType,
      eventType: ClickEventType,
      x: number,
      y: number,
      button: number = 0): MouseEvent
  ```

- `createTouchEndEvent`
  ```typescript
  function createTouchEndEvent(touchList?: TouchList): UIEvent
  ```

- `createTouchMoveEvent`
  ```typescript
  function createTouchMoveEvent(touchList?: TouchList): UIEvent
  ```

- `createTouchStartEvent`
  ```typescript
  function createTouchStartEvent(touchList?: TouchList): UIEvent
  ```

### <a name="d3-event-related-helper-methods"></a>Métodos auxiliares relacionados a eventos D3

Os métodos a seguir são usados para simular eventos D3 em testes de unidade.

- `flushAllD3Transitions` força a conclusão de todas as transições D3

  ```typescript
  function flushAllD3Transitions()
  ```
  
  > [!NOTE]
  > Normalmente, as transições de atraso zero são executadas após um atraso instantâneo (<10 ms), mas isso poderá causar uma pequena cintilação se o navegador renderizar a página duas vezes. Uma vez no final do primeiro loop do evento e novamente logo após o primeiro retorno de chamada do temporizador.
  >
  > Essas cintilações são mais perceptíveis no IE e com um grande número de modos de exibição da Web e não são recomendadas para o iOS.
  > 
  > Ao liberar a fila do temporizador no final do primeiro loop do evento, você pode executar qualquer transição de atraso zero imediatamente e evitar a cintilação.

Os seguintes métodos também estão incluídos:
```typescript
function d3Click(element: JQuery, x: number, y: number, eventType?: ClickEventType, button?: number): void
function d3MouseUp(element: JQuery, x: number, y: number, eventType?: ClickEventType, button?: number): void
function d3MouseDown(element: JQuery, x: number, y: number, eventType?: ClickEventType, button?: number): void
function d3MouseOver(element: JQuery, x: number, y: number, eventType?: ClickEventType, button?: number): void
function d3MouseMove(element: JQuery, x: number, y: number, eventType?: ClickEventType, button?: number): void
function d3MouseOut(element: JQuery, x: number, y: number, eventType?: ClickEventType, button?: number): void
function d3KeyEvent(element: JQuery, typeArg: string, keyArg: string, keyCode: number): void
function d3TouchStart(element: JQuery, touchList?: TouchList): void
function d3TouchMove(element: JQuery, touchList?: TouchList): void
function d3TouchEnd(element: JQuery, touchList?: TouchList): void
function d3ContextMenu(element: JQuery, x: number, y: number): void
```

### <a name="helper-interfaces"></a>Interfaces auxiliares
A interface e as enumerações a seguir são usadas na função auxiliar.

```typescript
interface RgbColor {
    R: number;
    G: number;
    B: number;
    A?: number; 
}

enum ClickEventType {
    Default = 0,
    CtrlKey = 1,
    AltKey = 2,
    ShiftKey = 4,
    MetaKey = 8,
}

enum MouseEventType {
    click,
    mousedown,
    mouseup,
    mouseover,
    mousemove,
    mouseout,
}
```

## <a name="next-steps"></a>Próximas etapas

Para escrever testes de unidade para os visuais do Power BI baseados no webpack e teste de unidade com `karma` e `jasmine`, confira, por exemplo, o [Tutorial: Adicionar testes de unidade a projetos de visuais do Power BI](./unit-tests-introduction.md).
