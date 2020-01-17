---
title: Migrar para powerbi-visuals-tools versão 3.x
description: Introdução à nova versão do powerbi-visuals-tools
author: zBritva
ms.author: v-ilgali
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 1b819aeb0f59df9ee0d48d7c41807abe62efed08
ms.sourcegitcommit: 801d2baa944469a5b79cf591eb8afd18ca4e00b1
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75885143"
---
# <a name="migrate-to-the-new-powerbi-visuals-tools-version-3x"></a>Migrar para o novo powerbi-visuals-tools versão 3.*x*

Começando com a versão 3, as Ferramentas Visuais do Power BI (powerbi-visuals-tools ou `pbiviz`) usam o webpack para criar visuais personalizados.
A nova versão oferece aos desenvolvedores muitos aprimoramentos para a criação de visuais:

- O TypeScript versão 3.*x* é usado por padrão. Começando com o TypeScript 1.5, a nomenclatura foi alterada. [Leia mais sobre os módulos TypeScript](https://www.typescriptlang.org/docs/handbook/modules.html).

- Módulos do ECMAScript 6 (ES6) têm suporte. Use importações do ES6 em vez de [externalJS](migrate-to-new-tools.md#configure-loading-of-external-libraries).

- Novas versões do Data-Driven Documents ([D3v5](https://d3js.org/)) e outras bibliotecas baseadas no módulo ES6 têm suporte.

- Tamanho de pacote reduzido. O webpack usa [Tree shaking](https://webpack.js.org/guides/tree-shaking/) para remover código não utilizado. Isso reduz o código JavaScript e proporcionar um melhor desempenho no carregamento de visuais.

- Melhor desempenho de API.

- A biblioteca Globalize.js [está integrada](migrate-to-new-tools.md#remove-the- globalizejs-library) a FormattingUtils.

- As Ferramentas Visuais do Power BI usam [webpack-bundle-analyzer](https://github.com/webpack-contrib/webpack-bundle-analyzer) para exibir a base do código do visual.

Este artigo descreve todas as etapas de migração para a nova versão das Ferramentas Visuais do Power BI.

## <a name="backward-compatibility"></a>Compatibilidade com versões anteriores

As novas ferramentas têm compatibilidade com versões anteriores para a base de código de visuais anterior, mas podem exigir algumas alterações adicionais para carregar bibliotecas externas.

As bibliotecas que dão suporte aos sistemas do módulo são importadas como módulos do webpack. Todas as outras bibliotecas e o código-fonte do visual são encapsulados em um módulo.

Agora, variáveis globais como JQuery e Lodash, que eram usadas nas Ferramentas Visuais do Power BI anteriores, estão obsoletas. Se o código antigo de seu visual depender de variáveis globais, o visual provavelmente não funcionará com as novas ferramentas.

A versão anterior das Ferramentas Visuais do Power BI exigia a definição de uma classe de visual no módulo `powerbi.extensibility.visual`. Com a nova versão das ferramentas, você precisa definir uma classe de visual no arquivo TypeScript (.ts) principal. Normalmente, esse arquivo é `src/visual.ts`.

## <a name="install-powerbi-visuals-tools"></a>Instalar powerbi-visuals-tools

Execute este comando para instalar as novas ferramentas:

```cmd
npm install -g powerbi-visuals-tools
```

O código a seguir é do arquivo `package.json` no [repositório de visuais do sampleBarChart](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/blob/471f103fcef9af93cff76cbac9c7fc67564acd4b/package.json#L15), após o projeto do visual ter sido atualizado para funcionar com as novas ferramentas:

```json
{
    "name": "visual",
    "version": "3.0.0",
    "scripts": {
        "pbiviz": "pbiviz",
        "start": "pbiviz start",
        "package": "pbiviz package",
        "lint": "tslint -r \"node_modules/tslint-microsoft-contrib\"  \"+(src|test)/**/*.ts\"",
        "test": "pbiviz package --resources --no-minify --no-pbiviz"
    },
    "devDependencies": {
        "@types/d3": "5.7.2",
        "d3": "5.12.0",
        "powerbi-visuals-api": "^2.6.1",
        "powerbi-visuals-tools": "^3.1.7",
        "powerbi-visuals-utils-dataviewutils": "^2.2.1",
        "powerbi-visuals-utils-formattingutils": "^4.4.2",
        "powerbi-visuals-utils-interactivityutils": "^5.6.0",
        "powerbi-visuals-utils-tooltiputils": "^2.3.1",
        "tslint": "^5.20.0",
        "tslint-microsoft-contrib": "^6.2.0"
    }
}
```

## <a name="install-the-power-bi-custom-visuals-api"></a>Instalar a API de Visuais Personalizados do Power BI

A nova versão de powerbi-visual-tools não inclui todas as versões da API. Em vez disso, você precisa instalar uma versão específica do pacote [powerbi-visuals-api](https://www.npmjs.com/package/powerbi-visuals-api). Escolha a versão do pacote que corresponde à versão da API de seus visuais personalizados do Power BI. O pacote fornece todas as definições de tipo para a API de Visuais Personalizados do Power BI.

Adicione `powerbi-visuals-api` às dependências de um projeto executando este comando:

```cmd
npm install --save-dev powerbi-visuals-api
```

Além disso, remova todos os links para definições de tipo de API antigas, pois o webpack inclui automaticamente tipos de `powerbi-visuals-api`. Há alterações correspondentes em [package.json](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/blob/471f103fcef9af93cff76cbac9c7fc67564acd4b/package.json#L14) e [tsconfig.json](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/blob/471f103fcef9af93cff76cbac9c7fc67564acd4b/tsconfig.json#L14).

## <a name="update-tsconfigjson"></a>Atualizar tsconfig.json

Para usar módulos externos, altere a opção `out` para `outDir`. Por exemplo, use `"outDir": "./.tmp/build/",` ao invés de `"out": "./.tmp/build/visual.js",`.

Essa alteração é necessária porque os arquivos TypeScript serão compilados em arquivos JavaScript de forma independente. É por isso que você não precisa mais especificar o arquivo visual.js como uma saída.

Você também poderá alterar a opção `target` para `ES6` se quiser usar JavaScript moderno como uma saída. Essa alteração é [opcional](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/blob/471f103fcef9af93cff76cbac9c7fc67564acd4b/tsconfig.json#L7).

## <a name="update-custom-visuals-utilities"></a>Atualizar utilitários de visuais personalizados

Se você usa um dos pacotes [powerbi-visuals-utils](https://www.npmjs.com/search?q=powerbi-visuals-utils), atualize-os para a versão mais recente. Para fazer isso, execute este comando:

```cmd
npm install powerbi-visuals-utils-<UTILNAME> --save
```

Por exemplo, para obter a nova versão com módulos externos de TypeScript, execute: 

```cmd
npm install powerbi-visuals-utils-dataviewutils --save
```

Para obter um exemplo de um visual que usa todos os pacotes de `powerbi-visuals-utils`, consulte o [Repositório MekkoChart](https://github.com/Microsoft/powerbi-visuals-mekkochart).

## <a name="remove-the-globalizejs-library"></a>Remover a biblioteca Globalize.js

A nova versão de [powerbi-visuals-utils-formattingutils@4.3](https://www.npmjs.com/package/powerbi-visuals-utils-formattingutils) inclui Globalize.js. Sendo assim, você não precisa incluir essa biblioteca manualmente no projeto. Todas as localizações necessárias serão adicionadas ao pacote final automaticamente.

## <a name="configure-loading-of-external-libraries"></a>Configurar o carregamento de bibliotecas externas

Inclua novos arquivos JavaScript após as bibliotecas na matriz `externalJS` de `pbiviz.json`. Por exemplo:

```JSON
"externalJS": [
    ...
    "node_modules/lodash/lodash.min.js",
    "externalJS/init.lodash.js",
    ...
]
```

Importar as bibliotecas em seu código-fonte. Por exemplo, para `lodash-es`, use esta instrução:

```JS
import * as _ from "lodash-es";
```

No exemplo anterior, `_` é a variável global para a biblioteca `lodash`.

## <a name="make-changes-in-the-sources-of-your-visuals"></a>Fazer alterações nas fontes de seus visuais

A principal alteração que você precisa fazer é converter módulos internos em módulos externos. Você não pode usar módulos externos dentro de módulos internos.

Veja uma descrição detalhada das alterações a serem feitas. As modificações são descritas no contexto do exemplo de código de visual personalizado Gráfico de Barras:

1. Remover todas as definições de módulos de cada arquivo de [código-fonte](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/commit/72ec605ce6a311a6cc004453b07973b6ed5e61f9#diff-433142f7814fee940a0ffc98dc75bfcbL1-L3):

    ```typescript
    module powerbi.extensibility.visual {
        ...
    }
    ```

2. [Importar as definições de API de visual personalizado do Power BI](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/commit/72ec605ce6a311a6cc004453b07973b6ed5e61f9#diff-433142f7814fee940a0ffc98dc75bfcbR4):

    ```typescript
    import powerbi from "powerbi-visuals-api";
    ```

3. [Importar as interfaces ou classes necessárias](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/commit/72ec605ce6a311a6cc004453b07973b6ed5e61f9#diff-433142f7814fee940a0ffc98dc75bfcbR12-R35) do módulo interno `powerbi`.

    ```typescript
    import PrimitiveValue = powerbi.PrimitiveValue; 
    import VisualUpdateOptions = powerbi.extensibility.visual.VisualUpdateOptions; 
    import VisualConstructorOptions = powerbi.extensibility.visual.VisualConstructorOptions; 
    import IVisualHost = powerbi.extensibility.visual.IVisualHost; 
    import IColorPalette = powerbi.extensibility.IColorPalette; 
    import IVisual = powerbi.extensibility.visual.IVisual; 
    import VisualObjectInstance = powerbi.VisualObjectInstance; 
    import VisualObjectInstanceEnumeration = powerbi.VisualObjectInstanceEnumeration; 
    import EnumerateVisualObjectInstancesOptions = powerbi.EnumerateVisualObjectInstancesOptions; 
    import Fill = powerbi.Fill; 
    import VisualTooltipDataItem = powerbi.extensibility.VisualTooltipDataItem; 
    import ISelectionManager = powerbi.extensibility.ISelectionManager; 
    ```

4. [Importar a biblioteca D3.js](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/commit/72ec605ce6a311a6cc004453b07973b6ed5e61f9#diff-433142f7814fee940a0ffc98dc75bfcbR2):

    ```typescript
    import * as d3 from "d3";
    ```

    Ou importar somente os módulos da biblioteca D3 necessários:

    ```typescript
    import { max, min } from "d3-array";
    ```

5. [Importar utilitários, classes e interfaces definidas no projeto de visual](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/commit/72ec605ce6a311a6cc004453b07973b6ed5e61f9#diff-433142f7814fee940a0ffc98dc75bfcbR38-R41) para o arquivo de origem principal:

    ```typescript
    import { getLocalizedString } from "./localization/localizationHelper";
    import { getValue, getCategoricalObjectValue } from "./objectEnumerationUtility";
    import {
        ITooltipServiceWrapper,
        TooltipEventArgs,
        createTooltipServiceWrapper
    } from "./tooltipServiceWrapper";
    ```

### <a name="import-css-styles"></a>Importar estilos de CSS

A nova versão das ferramentas permite importar os estilos `CSS` e `Less` diretamente para o código do TypeScript. A [seção de estilos](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/blob/471f103fcef9af93cff76cbac9c7fc67564acd4b/pbiviz.json#L21) que foi usada anteriormente agora é ignorada pelo compilador.

Para usar sua folha de estilos, abra o arquivo TypeScript (.ts) principal e adicione a seguinte linha:  

```typescript
import "./../style/visual.less";
```  

Seus estilos `CSS` e `Less` serão compilados automaticamente.

### <a name="externaljs-section-in-pbivizjson"></a>Seção externalJS no pbiviz.json

As ferramentas [não exigem uma lista de bibliotecas `externalJS`](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/commit/72ec605ce6a311a6cc004453b07973b6ed5e61f9#diff-a1a7bbee7e7d2f9d449f4b534532bcf2R20) para carregamento no pacote do visual, porque o webpack inclui todas as bibliotecas importadas.

> [!NOTE]
> Em `pbiviz.json`, deixe a seção `externalJS` vazia.

Use o comando `npm run package` típico para criar o pacote do visual ou `npm run start` para iniciar o servidor de desenvolvimento.

## <a name="update-the-d3js-library-to-version-5"></a>Atualizar a biblioteca D3.js para a versão 5

Com as novas ferramentas visuais, é possível começar a usar a nova versão da biblioteca D3.js. Execute esses comandos para atualizar a D3 no seu projeto visual:

- `npm install --save d3@5` para instalar a nova D3.js.

- `npm install --save-dev @types/d3@5` para instalar as novas definições de tipo para D3.js.

> [!IMPORTANT]
> A versão 5 da D3 apresenta várias alterações significativas.

Modifique seu código para que funcione com a nova D3.js:

- A interface `d3.Selection<T>` [foi alterada](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/af2ff9fb0fc70bd94ea0c604d75a362411d5abeb#diff-433142f7814fee940a0ffc98dc75bfcbR157) para `Selection<GElement extends BaseType, Datum, PElement extends BaseType, PDatum>`.

- Não é possível aplicar vários atributos usando apenas uma chamada para método `attr`. Em vez disso, você precisa [passar cada atributo em uma chamada separada](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/af2ff9fb0fc70bd94ea0c604d75a362411d5abeb#diff-433142f7814fee940a0ffc98dc75bfcbR278) para `attr`. Faça [chamadas separadas para o método `style`](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/af2ff9fb0fc70bd94ea0c604d75a362411d5abeb#diff-433142f7814fee940a0ffc98dc75bfcbR247) também.

- A versão 4 da D3.js introduziu o novo método `merge`. Normalmente, esse método é usado para mesclar as seleções `enter` e `update` após uma operação de junção de dados. Para usar a D3 corretamente, [chame o método `merge`](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/83fe8d52d362dccd0034dd8e32c94080d9376b29#diff-433142f7814fee940a0ffc98dc75bfcbR272).

[Leia mais](https://github.com/d3/d3/blob/master/CHANGES.md) sobre as alterações na biblioteca D3.js.

## <a name="install-babel-and-core-js"></a>Instalar o Babel e o core-js

Começando na versão 3.1, as ferramentas de visuais usam o Babel para compilar o código JavaScript moderno no ECMAScript 5 (ES5) antigo para dar suporte a uma ampla variedade de navegadores.

A opção do Babel é habilitada por padrão, mas você precisa importar manualmente o pacote [`core-js`](https://www.npmjs.com/package/core-js). Execute este comando para instalar o pacote:

```cmd
npm install --save core-js
```

Em seguida, importe o pacote para o ponto de partida do código do visual. Normalmente, é o arquivo "src/visual.ts".

```JS
import "core-js/stable";
```

Leia mais sobre o Babel [nos documentos](https://babeljs.io/docs/en/).
