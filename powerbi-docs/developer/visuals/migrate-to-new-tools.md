---
title: Migrar para powerbi-visuals-tools 3.x
description: Introdução à nova versão de powerbi-visuals-tools
author: zBritva
ms.author: v-ilgali
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 245475feeb43ee544117aaa54969f2de1e207cd5
ms.sourcegitcommit: f77b24a8a588605f005c9bb1fdad864955885718
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2019
ms.locfileid: "74696272"
---
# <a name="migrate-to-the-new-powerbi-visuals-tools-3xx"></a>Migrar para o novo powerbi-visuals-tools 3.x.x

A partir da versão 3, as Ferramentas Visuais do Power BI usam o Webpack para criar visuais personalizados.
A nova versão traz muitas oportunidades novas para os desenvolvedores criarem visuais:

* TypeScript v3.x.x por padrão. A partir do TypeScript 1.5, a nomenclatura foi alterada. [Leia mais sobre os módulos TypeScript](https://www.typescriptlang.org/docs/handbook/modules.html).

* Suporte para os módulos ES6. Você não precisa mais usar [externalJS](migrate-to-new-tools.md#fix-loading-external-libraries). Em vez disso, use as importações do ES6.

* Suporte para novas versões do [D3v5](https://d3js.org/) e outras bibliotecas baseadas no módulo ES6.

* Tamanho de pacote reduzido. O Webpack usa [Tree Shaking](https://webpack.js.org/guides/tree-shaking/) para remover código não utilizado. Ele reduz o código do JS e, como resultado, você obtém um melhor desempenho no carregamento visual.

* Melhor desempenho de API.

* A biblioteca Globalize.js [está integrada](migrate-to-new-tools.md#remove-globalizejs-library) em formatting-utils.

* As ferramentas usam [webpack-bundle-analyzer](https://github.com/webpack-contrib/webpack-bundle-analyzer) para exibir a base do código do visual.

Todas as etapas de migração para a nova versão das Ferramentas Visuais do Power BI são descritas abaixo.

## <a name="backward-compatibility"></a>Compatibilidade com versões anteriores

As novas ferramentas têm compatibilidade com versões anteriores para a base de código visual anterior, mas podem exigir algumas alterações adicionais para carregar bibliotecas externas.

As bibliotecas, que dão suporte aos sistemas de módulo, serão importadas como módulos do Webpack. Todos os outros códigos-fonte visuais e bibliotecas serão encapsulados em um módulo.

Agora, variáveis globais como JQuery e Lodash, que foram usadas nas ferramentas de pbiviz anteriores, estão obsoletas. Ou seja, nesse caso, se o código visual antigo repassar variáveis globais, o visual poderá ficar corrompido.

A versão anterior das Ferramentas Visuais do Power BI exigia a definição de uma classe visual no módulo `powerbi.extensibility.visual`.

## <a name="how-to-install-powerbi-visuals-tools"></a>Como instalar powerbi-visuals-tools

O novo conjunto de ferramentas pode ser instalado por meio da execução do comando

```cmd
npm install -g powerbi-visuals-tools
```

Exemplo do visual sampleBarChart e as [alterações](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/sample-next/package.json#L16) correspondentes no `package.json`:

```json
{
    "name": "visual",
    "version": "1.2.3",
    "scripts": {
        "pbiviz": "pbiviz",
        "start": "pbiviz start",
        "lint": "tslint -r \"node_modules/tslint-microsoft-contrib\"  \"+(src|test)/**/*.ts\"",
        "test": "pbiviz package --resources --no-minify --no-pbiviz"
    },
    "devDependencies": {
      "@types/d3": "5.0.0",
      "d3": "5.5.0",
      "powerbi-visuals-tools": "^3.1.0",
      "tslint": "^4.4.2",
      "tslint-microsoft-contrib": "^4.0.0"
    }
}
```

## <a name="how-to-install-power-bi-custom-visuals-api"></a>Como instalar a API de Visuais Personalizados do Power BI

A nova versão de powerbi-visual-tools não inclui todas as versões da API. Em vez disso, o desenvolvedor deve instalar uma versão específica do pacote [`powerbi-visuals-api`](https://www.npmjs.com/package/powerbi-visuals-api). A versão do pacote corresponde à versão da API dos Visuais Personalizados do Power BI e fornece todas as definições de tipo para a API dos Visuais Personalizados do Power BI.

Adicione `powerbi-visuals-api` às dependências do projeto executando o comando `npm install --save-dev powerbi-visuals-api`.
E você deve remover o link das definições antigas de tipo de API. Porque os tipos de `powerbi-visuals-api` são incluídos automaticamente pelo Webpack. As alterações correspondentes estão [nesta](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/sample-next/package.json#L14) linha de `package.json`.

## <a name="update-tsconfigjson"></a>Atualizar `tsconfig.json`

Para usar módulos externos, você deve alternar a opção `out` para `outDir`.
`"outDir": "./.tmp/build/",` em vez de `"out": "./.tmp/build/visual.js",`.

É necessário porque os arquivos TypeScript serão compilados em arquivos JavaScript de forma independente. É por isso que você não precisa mais especificar o arquivo visual.js como uma saída.

E você também poderá alterar a opção `target` para `ES6` se quiser usar JavaScript moderno como uma saída. [É opcional](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/sample-next/tsconfig.json#L6).

## <a name="update-custom-visuals-utils"></a>Atualizar utilitários de Visuais personalizados

Se você usar um dos powerbi-visuals-utils](https://www.npmjs.com/search?q=powerbi-visuals-utils), também deverá atualizá-los para a versão mais recente.

Execute o comando `npm install powerbi-visuals-utils-<UTILNAME> --save`. (Ex.: `npm install powerbi-visuals-utils-dataviewutils --save` ) para obter a nova versão com módulos externos do TypeScript.

Você pode encontrar um exemplo no [repositório](https://github.com/Microsoft/powerbi-visuals-mekkochart) MekkoChart.
Esse visual usa todos os utilitários.

## <a name="remove-globalizejs-library"></a>Remover biblioteca Globalize.js

A nova versão do [powerbi-visuals-utils-formattingutils@4.3](https://www.npmjs.com/package/powerbi-visuals-utils-formattingutils) inclui o globalize.js pronto para uso.
Você não precisa incluir essa biblioteca manualmente no projeto.
Todas as localizações necessárias serão adicionadas ao pacote final automaticamente.

## <a name="fix-loading-external-libraries"></a>Corrigir o carregamento de bibliotecas externas

Em vez disso, inclua o novo arquivo JS após as bibliotecas na matriz `externalJS` de `pbiviz.json`. Exemplo:

```JSON
"externalJS": [
    ...
    "node_modules/lodash/lodash.min.js",
    "externalJS/init.lodash.js",
    ...
]
```

Importe as bibliotecas na fonte. Exemplo para `lodash-es`:

```JS
import * as _ from "lodash-es";
```

em que `_` é uma variável global da biblioteca `lodash`.

## <a name="changes-in-the-visuals-sources"></a>Alterações nas fontes de visuais

A principal alteração é converter módulos internos em módulos externos porque não é possível usar módulos externos dentro de módulos internos.

Essas alterações descrevem as modificações que foram aplicadas ao Gráfico de barras de exemplo

Veja a seguir as descrições detalhadas das alterações:

1. Remover todas as definições de módulos de cada arquivo do [código-fonte](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/sample-next/src/barChart.ts#L153)

    ```typescript
    module powerbi.extensibility.visual {
        ...
    }
    ```

2. [Importar as definições de API de visual personalizado do Power BI](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/sample-next/src/barChart.ts#L2).

    ```typescript
    import powerbi from "powerbi-visuals-api";
    ```

3. [Importe](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/sample-next/src/barChart.ts#L12-L23) as interfaces ou classes necessárias do módulo interno `powerbi`.

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

4. [Importar](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/sample-next/src/barChart.ts#L1) a biblioteca D3.js

    ```typescript
    import * as d3 from "d3";
    ```

    Ou importar somente os módulos de bibliotecas D3 necessários

    ```typescript
    import { max, min } from "d3-array";
    ```

5. [Importar](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/sample-next/src/barChart.ts#L4-L10) utilitários, classes, interfaces definidas no projeto de visual para o arquivo de origem principal

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

A nova versão das ferramentas permite que os desenvolvedores importem o estilo de CSS e LESS diretamente no código do TypeScript.

Portanto, a [seção de estilos](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/sample-next/pbiviz.json#L22) usada anteriormente será ignorada pelo compilador.

Para usar sua folha de estilos, abra o arquivo ts principal e adicione a seguinte linha:  

```typescript
import "./../style/visual.less";
```  

Seus estilos de CSS e LESS serão compilados automaticamente.  

### <a name="externaljs-section-in-pbivizjson"></a>Seção externalJS no pbiviz.json

As ferramentas [não exigem](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/sample-next/pbiviz.json#L20) o carregamento de uma lista de `externalJS` no pacote do visual. Isso porque o Webpack inclui todas as bibliotecas importadas.

**A seção externalJS no pbivi.json deve estar vazia.**

Chame os comandos típicos `npm run package` para criar o pacote visual ou `npm run start` para iniciar o servidor de desenvolvimento.

## <a name="updating-d3js-library-to-version-5"></a>Atualizar a biblioteca D3.js para a versão 5

Com as novas ferramentas, é possível começar a usar a nova versão da biblioteca D3.js.

Chamar comandos para atualizar a D3 no seu projeto visual

`npm install --save d3@5` para instalar a nova D3.js.

`npm install --save-dev @types/d3@5` para instalar as novas definições de tipo para D3.js.

Há várias alterações significativas, e você deve modificar seu código para usar a nova D3.js.

1. A interface `d3.Selection<T>` [foi alterada](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/af2ff9fb0fc70bd94ea0c604d75a362411d5abeb#diff-433142f7814fee940a0ffc98dc75bfcbR157) para `Selection<GElement extends BaseType, Datum, PElement extends BaseType, PDatum>`

2. Não é possível aplicar vários atributos com uma única chamada do método `attr`. Você [deve passar](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/af2ff9fb0fc70bd94ea0c604d75a362411d5abeb#diff-433142f7814fee940a0ffc98dc75bfcbR278) cada atributo em uma chamada diferente do método `attr`. Isso também é [semelhante](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/af2ff9fb0fc70bd94ea0c604d75a362411d5abeb#diff-433142f7814fee940a0ffc98dc75bfcbR247) para o método `style`.

3. O novo método de mesclagem é introduzido na D3.js v4. Normalmente, esse método é usado para mesclar as seleções de inserção e atualização após uma junção de dados. [Chame o método de mesclagem](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/83fe8d52d362dccd0034dd8e32c94080d9376b29#diff-433142f7814fee940a0ffc98dc75bfcbR272) para usar D3 corretamente.

[Leia mais](https://github.com/d3/d3/blob/master/CHANGES.md) sobre as alterações na biblioteca D3.js.

## <a name="babel"></a>Babel

A partir da versão 3.1, as ferramentas usam o Babel para compilar o novo código JS moderno no ES5 antigo para ser compatível com uma ampla variedade de navegadores.

Essa opção é habilitada por padrão, mas você precisa importar manualmente o pacote [`@babel/polyfill`](https://babeljs.io/docs/en/babel-polyfill).

Execute o comando para instalar o pacote

`npm install --save @babel/polyfill`

e importe o pacote no ponto inicial do código do visual (normalmente, é o arquivo "src/visual.ts"):

`import "@babel/polyfill";`

Leia mais sobre o Babel [nos documentos](https://babeljs.io/docs/en/).

Por fim, execute [webpack-visualizer](https://github.com/chrisbateman/webpack-visualizer) para exibir a base de código do visual.  

![Estatísticas de código do visual](./media/webpack-stats.png)
