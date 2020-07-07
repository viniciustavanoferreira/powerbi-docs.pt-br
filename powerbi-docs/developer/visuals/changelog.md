---
title: Log de mudanças de API de visuais do Power BI
description: Este artigo descreve as principais alterações em diferentes versões da API de visuais do Power BI
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 03/13/2019
ms.openlocfilehash: 3cf415cbd14da28d523a042fdf4099fe464a4a8b
ms.sourcegitcommit: a07fa723bb459494c60cf6d749b4554af723482a
ms.contentlocale: pt-BR
ms.lasthandoff: 06/12/2020
ms.locfileid: "84739174"
---
# <a name="power-bi-visuals-api-changelog"></a>Log de mudanças de API de visuais do Power BI
Esta página contém um rápido resumo das versões da API. As versões listadas aqui são consideradas estáveis e não serão alteradas.

## <a name="api-v320"></a>API v3.2.0
  * Compatível com **[supportsMultiVisualSelection](./supportsmultivisualselection-feature.md)**

## <a name="api-v260"></a>API v2.6.0
  * Adiciona **isInFocus** para atualizar a opção e o método **switchFocusModeState** para o host do visual
  * Dá suporte à personalização **subtotais**

## <a name="api-v250"></a>API v2.5.0
  * Dá suporte ao **[painel Análise](./analytics-pane.md)**
  * Dá suporte aos métodos `SelectionIdBuilder` **withMatrixNode** e **withTable**
  * Não dá mais suporte à interface `DataRepetitionSelector`, substituída pela interface `data.CustomVisualOpaqueIdentity`

## <a name="api-v230"></a>API v2.3.0
  * **[API da página de aterrissagem](./landing-page.md)**
  * **[API de armazenamento local](./local-storage.md)**
  * **[API de filtro de tupla (filtro com várias colunas)](./filter-api.md#the-tuple-filter-api-multi-column-filter)**
  * **[API de renderização de eventos](./event-service.md#render-events-in-power-bi-visuals)**

## <a name="api-v220"></a>API v2.2.0
  * Dá suporte à **[restauração do filtro JSON do DataView](./filter-api.md#restore-the-json-filter-from-the-data-view)**
  * **[API de ContextMenu](./context-menu.md)**

## <a name="api-v210"></a>API v2.1.0
  * Aprimoramentos de desempenho:
    * Tempos de carregamento mais rápidos
    * Menor volume de memória
    * Transações de dados e eventos otimizadas  

**Notas de versão**
* As APIs de filtragem refatorada estarão disponíveis na API 2.2 e não têm suporte na API 2.1.
* Os visuais receberão apenas o tipo dataView, declarado em seus recursos. Os visuais que usaram vários tipos dataView serão interrompidos em consequência dessa atualização.
* Não dá mais suporte à interface `DataViewScopeIdentity`, substituída pela interface `data.DataRepetitionSelector`. Se você usou a propriedade de chave da interface `DataViewScopeIdentity`, pode substituí-la por `JSON.stringify(identity)`
* `undefined` é substituído por `null` dentro do dataView. Na iteração em uma matriz usando `var item in myArray`, ela ignora `undefined`, mas não ignora `null`. Os visuais que usam esse padrão podem ser interrompidos por essa atualização. Certifique-se de verificar `null` nas matrizes:
   ```typescript
   for (var item in myArray) {
     if (!item) {
       continue;
     }
     console.log(item);
   }
   ```
* A propriedade `proto` não armazena mais metadados\dados ocultos dentro do dataView. Os visuais que acessam as propriedades via `proto` podem ser interrompidos por essa atualização.

## <a name="api-v1130"></a>API v1.13.0
* Dá suporte ao recurso **[Sincronizar segmentações de dados](./enable-sync-slicers.md)** . Observe que isso só funciona para segmentações de dados de campo único devido ao estado de código atual do PBI; [leia mais](/power-bi/desktop-slicers).
* Acessibilidade: [Suporte de alto contraste](./high-contrast-support.md) 
* Acessibilidade: Permitir sinalizador de Foco do teclado

## <a name="api-v1120"></a>API v1.12.0
* Dá suporte a Temas
* Dá suporte a **[fetchMoreData](./fetch-more-data.md)** . Observe que a **API de Buscar mais dados** supera o limite rígido de 30 mil pontos de dados
* **[API de dicas de ferramenta de tela](./add-tooltips.md#add-report-page-tooltips)**

## <a name="api-v1110"></a>API v1.11.0
* **[API do FilterManager](./filter-api.md)**
* Dá suporte a **[Indicadores](./bookmarks-support.md)** 

## <a name="api-v1100"></a>API v1.10.0
* Adiciona `ILocalizationManager`
* **API de autenticação**

## <a name="api-v190"></a>API v1.9.0
* **[API de launchUrl](./launch-url.md)**

## <a name="api-v180"></a>API v1.8.0
* Dá suporte ao novo tipo **fillRule** (gradiente) no esquema de funcionalidades
* Dá suporte à propriedade **regra** no esquema de funcionalidades para propriedades de objeto

## <a name="api-v170"></a>API v1.7.0
* Dá suporte a **[RESJSON](./localization.md#resource-file)**

## <a name="api-v162"></a>API v1.6.2
* Dá suporte ao **[Modo de edição](./advanced-edit-mode.md)** para que o visual entre no modo de edição no visual
* Dá suporte aos **[Visuais interativos do Power BI em R (HTML)](https://microsoft.github.io/PowerBI-visuals/tutorials/building-r-powered-custom-visual/creating-r-visuals.md)** , baseados em HTML

## <a name="api-v150"></a>API v1.5.0
* Dá suporte a **[Permitir interações](./visuals-interactions.md)** para interatividade do visual

## <a name="api-v140"></a>API v1.4.0
* Dá suporte a **[Localização](./localization.md)**

## <a name="api-v130"></a>API v1.3.0
* Dá suporte a **[Dicas de ferramentas](./add-tooltips.md)**

## <a name="api-v120"></a>API v1.2.0
* Adiciona **colorPalette** para gerenciar as cores usadas no visual.
* Dá suporte a **Seleção múltipla** – selectionManager pode aceitar uma matriz de `SelectionId`.
* Dá suporte a **[Visuais do R](https://microsoft.github.io/PowerBI-visuals/tutorials/building-r-powered-custom-visual/creating-r-visuals.md)** usando scripts do R

## <a name="api-v110"></a>API v1.1.0
* Dá suporte ao visual de depuração em iFrame
* Adiciona uma área restrita de peso leve com inicialização mais rápida do iFrame
* Corrige o problema [Capabilities.objects não dá suporte ao tipo "texto"](https://github.com/Microsoft/PowerBI-visuals-tools/issues/12)
* Dá suporte a `pbiviz update` para atualizar definições e esquema de tipo de API de visuais
* Dá suporte ao sinalizador `--api-version` em `pbiviz new` para criar visuais com uma versão de API específica
* Dá suporte à versão alfa da API v 1.2.0

**Host do visual**
* Adiciona **createSelectionIdBuilder** para criar identificadores exclusivos usados para a seleção de dados
* Adiciona **createSelectionManager** para gerenciar o estado de seleção do Visual e comunica as alterações ao host do visual
* Adiciona uma matriz de **cores** padrão para usar nos visuais

## <a name="api-v100"></a>API v1.0.0
* Versão da API inicial
