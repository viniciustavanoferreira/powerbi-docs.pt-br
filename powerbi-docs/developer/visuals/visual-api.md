---
title: API de visual
description: Este artigo descreve como usar API IVIsual para visuais do Power BI
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 03/19/2020
ms.openlocfilehash: 6ec30fdd4812427ae855ff9a167d946d2a415c28
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83302956"
---
# <a name="visual-api"></a>API de visual
Todos os visuais começam com uma classe que implementa a interface `IVisual`. Você pode dar qualquer nome à classe, desde que haja uma classe que implemente com exatidão a interface `IVisual`.

> [!NOTE]
> O nome da classe do visual deve corresponder ao que está definido no arquivo *pbiviz.json*.

Confira a classe do visual de exemplo com os seguintes métodos que devem ser implementados:

* `constructor`, um construtor padrão para inicializar o estado do visual
* `update`, para atualizar os dados do visual
* `enumerateObjectInstances`, para retornar objetos para preencher o painel de propriedades (opções de formatação), onde você pode modificá-los conforme necessário
* `destroy`, um destruidor padrão para limpeza

```typescript
class MyVisual implements IVisual {
    
    constructor(options: VisualConstructorOptions) {
        //one time setup code goes here (called once)
    }
    
    public update(options: VisualUpdateOptions): void {
        //code to update your visual goes here (called on all view or data changes)
    }

    public enumerateObjectInstances(options: EnumerateVisualObjectInstancesOptions): VisualObjectInstanceEnumeration {
        //returns objects to populate the property pane (called for each object defined in capabilities)
    }
    
    public destroy(): void {
        //one time cleanup code goes here (called once)
    }
}
```

## <a name="constructor"></a>construtor

O construtor da classe do visual é chamado quando é criada uma instância para o visual. Ele pode ser usado para qualquer operação de configuração necessária para o visual.

```typescript
constructor(options: VisualConstructorOptions)
```

**VisualConstructorOptions**

* `element: HTMLElement`, uma referência ao elemento DOM que conterá o visual
* `host: IVisualHost`, uma coleção de propriedades e serviços que podem ser usados para interagir com o host do visual (Power BI)

   `IVisualHost` contém os seguintes serviços:

   ```typescript
   export interface IVisualHost extends extensibility.IVisualHost {
       createSelectionIdBuilder: () => visuals.ISelectionIdBuilder;
       : () => ISelectionManager;
       colorPalette: ISandboxExtendedColorPalette;
       persistProperties: (changes: VisualObjectInstancesToPersist) => void;
       applyJsonFilter: (filter: IFilter[] | IFilter, objectName: string, propertyName: string, action: FilterAction) => void;
       tooltipService: ITooltipService;
       telemetry: ITelemetryService;
       authenticationService: IAuthenticationService;
       locale: string;
       allowInteractions: boolean;
       launchUrl: (url: string) => void;
       fetchMoreData: () => boolean;
       instanceId: string;
       refreshHostData: () => void;
       createLocalizationManager: () => ILocalizationManager;
       storageService: ILocalVisualStorageService;
       eventService: IVisualEventService;
       switchFocusModeState: (on: boolean) => void;
   }
   ```
   * `createSelectionIdBuilder`, gera e armazena metadados para itens selecionáveis em seu visual
   * `createSelectionManager`, cria a ponte de comunicação usada para notificar o host do visual sobre as alterações no estado de seleção; confira [API de seleção](./selection-api.md).
   * `createLocalizationManager`, gera um gerente para ajudar com a [Localização](./localization.md)
   * `allowInteractions: boolean`, um sinalizador booliano que sugere se o visual deve ser interativo ou não
   * `applyJsonFilter`, aplica tipos de filtro específicos; confira [API de filtro](./filter-api.md)
   * `persistProperties`, permite que os usuários mantenham propriedades e as salvem junto com a definição do visual, para que fiquem disponíveis na próxima recarga
   * `eventService`, retorna um [serviço de evento](./event-service.md) para dar suporte a eventos de **Renderização**
   * `storageService`, retorna um serviço para ajudar a usar o [armazenamento local](./local-storage.md) no visual
   * `authenticationService`, gera um serviço para ajudar com a autenticação do usuário
   * `tooltipService`, retorna um [serviço de dica de ferramenta](./add-tooltips.md) para ajudar a usar dicas de ferramentas no visual
   * `launchUrl`, ajuda a [iniciar a URL](./launch-url.md) na próxima guia
   * `locale`, retorna uma cadeia de caracteres de localidade; confira [Localização](./localization.md)
   * `instanceId`, retorna uma cadeia de caracteres para identificar a atual instância do visual
   * `colorPalette`, retorna a colorPalette necessária para aplicar cores aos seus dados
   * `fetchMoreData`, dá suporte ao uso de mais dados do que o limite padrão (mil linhas)
   * `switchFocusModeState`, ajuda a alterar o estado do modo de foco

## <a name="update"></a>atualizar

Todos os visuais devem implementar um método de atualização pública, chamado sempre que há uma alteração no ambiente de dados ou de host.

```typescript
public update(options: VisualUpdateOptions): void
```

**VisualUpdateOptions**

* `viewport: IViewport`, dimensões do visor em que o visual deve ser renderizado
* `dataViews: DataView[]`, o objeto DataView que contém todos os dados necessários para renderizar seu visual (o visual normalmente usará a propriedade categórica em DataView)
* `type: VisualUpdateType`, sinalizadores para indicar os tipos da atualização (**Data** | **Resize** | **ViewMode** | **Style** | **ResizeEnd**)
* `viewMode: ViewMode`, sinalizadores para indicar o modo de exibição do visual (**View** | **Edit** | **InFocusEdit**)
* `editMode: EditMode`, sinalizador para indicar o modo de edição do visual (**Default** | **Advanced**) (se o visual der suporte a **AdvancedEditMode**, ele deverá renderizar seus controles de interface do usuário avançados somente quando **editMode** for definido como **Advanced**; confira [AdvancedEditMode](./advanced-edit-mode.md))
* `operationKind?: VisualDataChangeOperationKind`, sinalizador para indicar o tipo de alteração de dados (**Create** | **Append**)
* `jsonFilters?: IFilter[]`, coleção de filtros JSON aplicados
* `isInFocus?: boolean`, sinalizador para indicar se o visual está no modo de foco ou não
    
## <a name="enumerateobjectinstances-optional"></a>enumerateObjectInstances `optional`

Esse método é chamado para cada objeto listado nos recursos. Usando as opções (atualmente, apenas o nome), você retorna uma `VisualObjectInstanceEnumeration` com informações sobre como exibir essa propriedade.

```typescript
enumerateObjectInstances(options:EnumerateVisualObjectInstancesOptions):VisualObjectInstanceEnumeration
```

**EnumerateVisualObjectInstancesOptions**

* `objectName: string`, nome do objeto

## <a name="destroy-optional"></a>destroy `optional`

A função destroy é chamada quando o visual é descarregado e pode ser usada para limpar tarefas, como remover ouvintes de evento.

``` typescript
public destroy(): void
```

> [!Note]
> Geralmente, o Power BI não chama `destroy`, pois é mais rápido remover o IFrame inteiro que contém o visual.
