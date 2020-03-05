---
title: Introdução a testes de unidade para projetos de visual do Power BI
description: Este artigo descreve como escrever testes de unidade para projetos de visual do Power BI
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: tutorial
ms.date: 06/18/2019
ms.openlocfilehash: 590f11f23a04a698459cc4db99efe5308ccc0ce3
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/09/2019
ms.locfileid: "73879947"
---
# <a name="tutorial-add-unit-tests-for-power-bi-visual-projects"></a>Tutorial: Adicionar testes de unidade a projetos de visual do Power BI

Este artigo descreve as noções básicas de como escrever testes de unidade para seus visuais do Power BI, incluindo como:

* Configurar a estrutura de teste do executor de teste do Karma JavaScript, Jasmine.
* Usar o pacote powerbi-visuals-utils-testutils.
* Usar simulações e elementos fictícios para ajudar a simplificar o teste de unidade de visuais do Power BI.

## <a name="prerequisites"></a>Pré-requisitos

* Um projeto de visuais do Power BI instalado
* Um ambiente do Node.js configurado

## <a name="install-and-configure-the-karma-javascript-test-runner-and-jasmine"></a>Instalar e configurar o executor de teste do Karma JavaScript e o Jasmine

Adicione as bibliotecas necessárias ao arquivo *package.json* na seção `devDependencies`:

```json
"@babel/polyfill": "^7.2.5",
"@types/d3": "5.5.0",
"@types/jasmine": "2.5.37",
"@types/jasmine-jquery": "1.5.28",
"@types/jquery": "2.0.41",
"@types/karma": "3.0.0",
"@types/lodash-es": "4.17.1",
"coveralls": "3.0.2",
"istanbul-instrumenter-loader": "^3.0.1",
"jasmine": "2.5.2",
"jasmine-core": "2.5.2",
"jasmine-jquery": "2.1.1",
"jquery": "3.1.1",
"karma": "3.1.1",
"karma-chrome-launcher": "2.2.0",
"karma-coverage": "1.1.2",
"karma-coverage-istanbul-reporter": "^2.0.4",
"karma-jasmine": "2.0.1",
"karma-junit-reporter": "^1.2.0",
"karma-sourcemap-loader": "^0.3.7",
"karma-typescript": "^3.0.13",
"karma-typescript-preprocessor": "0.4.0",
"karma-webpack": "3.0.5",
"puppeteer": "1.17.0",
"style-loader": "0.23.1",
"ts-loader": "5.3.0",
"ts-node": "7.0.1",
"tslint": "^5.12.0",
"webpack": "4.26.0"
```

Para saber mais sobre *package.json*, consulte a descrição em [npm-package.json](https://docs.npmjs.com/files/package.json).

Salve o arquivo *package.json* e, na localização `package.json`, execute o seguinte comando:

```cmd
npm install
```

O gerenciador de pacotes instala todos os novos pacotes que são adicionados ao *package.json*.

Para executar testes de unidade, configure o executor e a configuração `webpack`.

O código a seguir é um exemplo do arquivo *test.webpack.config.js*:

```typescript
const path = require('path');
const webpack = require("webpack");

module.exports = {
    devtool: 'source-map',
    mode: 'development',
    optimization : {
        concatenateModules: false,
        minimize: false
    },
    module: {
        rules: [
            {
                test: /\.tsx?$/,
                use: 'ts-loader',
                exclude: /node_modules/
            },
            {
                test: /\.json$/,
                loader: 'json-loader'
            },
            {
                test: /\.tsx?$/i,
                enforce: 'post',
                include: /(src)/,
                exclude: /(node_modules|resources\/js\/vendor)/,
                loader: 'istanbul-instrumenter-loader',
                options: { esModules: true }
            },
            {
                test: /\.less$/,
                use: [
                    {
                        loader: 'style-loader'
                    },
                    {
                        loader: 'css-loader'
                    },
                    {
                        loader: 'less-loader',
                        options: {
                            paths: [path.resolve(__dirname, 'node_modules')]
                        }
                    }
                ]
            }
        ]
    },
    externals: {
        "powerbi-visuals-api": '{}'
    },
    resolve: {
        extensions: ['.tsx', '.ts', '.js', '.css']
    },
    output: {
        path: path.resolve(__dirname, ".tmp/test")
    },
    plugins: [
        new webpack.ProvidePlugin({
            'powerbi-visuals-api': null
        })
    ]
};
```

O código a seguir é um exemplo do arquivo *karma.conf.ts*:

```typescript
"use strict";

const webpackConfig = require("./test.webpack.config.js");
const tsconfig = require("./test.tsconfig.json");
const path = require("path");

const testRecursivePath = "test/visualTest.ts";
const srcOriginalRecursivePath = "src/**/*.ts";
const coverageFolder = "coverage";

process.env.CHROME_BIN = require("puppeteer").executablePath();

import { Config, ConfigOptions } from "karma";

module.exports = (config: Config) => {
    config.set(<ConfigOptions>{
        mode: "development",
        browserNoActivityTimeout: 100000,
        browsers: ["ChromeHeadless"], // or Chrome to use locally installed Chrome browser
        colors: true,
        frameworks: ["jasmine"],
        reporters: [
            "progress",
            "junit",
            "coverage-istanbul"
        ],
        junitReporter: {
            outputDir: path.join(__dirname, coverageFolder),
            outputFile: "TESTS-report.xml",
            useBrowserName: false
        },
        singleRun: true,
        plugins: [
            "karma-coverage",
            "karma-typescript",
            "karma-webpack",
            "karma-jasmine",
            "karma-sourcemap-loader",
            "karma-chrome-launcher",
            "karma-junit-reporter",
            "karma-coverage-istanbul-reporter"
        ],
        files: [
            "node_modules/jquery/dist/jquery.min.js",
            "node_modules/jasmine-jquery/lib/jasmine-jquery.js",
            {
                pattern: './capabilities.json',
                watched: false,
                served: true,
                included: false
            },
            testRecursivePath,
            {
                pattern: srcOriginalRecursivePath,
                included: false,
                served: true
            }
        ],
        preprocessors: {
            [testRecursivePath]: ["webpack", "coverage"]
        },
        typescriptPreprocessor: {
            options: tsconfig.compilerOptions
        },
        coverageIstanbulReporter: {
            reports: ["html", "lcovonly", "text-summary", "cobertura"],
            dir: path.join(__dirname, coverageFolder),
            'report-config': {
                html: {
                    subdir: 'html-report'
                }
            },
            combineBrowserReports: true,
            fixWebpackSourcePaths: true,
            verbose: false
        },
        coverageReporter: {
            dir: path.join(__dirname, coverageFolder),
            reporters: [
                // reporters not supporting the `file` property
                { type: 'html', subdir: 'html-report' },
                { type: 'lcov', subdir: 'lcov' },
                // reporters supporting the `file` property, use `subdir` to directly
                // output them in the `dir` directory
                { type: 'cobertura', subdir: '.', file: 'cobertura-coverage.xml' },
                { type: 'lcovonly', subdir: '.', file: 'report-lcovonly.txt' },
                { type: 'text-summary', subdir: '.', file: 'text-summary.txt' },
            ]
        },
        mime: {
            "text/x-typescript": ["ts", "tsx"]
        },
        webpack: webpackConfig,
        webpackMiddleware: {
            stats: "errors-only"
        }
    });
};
```

Se necessário, você pode modificar essa configuração.

O código em *karma.conf.js* contém a seguinte variável:

* `recursivePathToTests`: Localiza o código de teste

* `srcRecursivePath`: Localiza o código JavaScript de saída após a compilação

* `srcCssRecursivePath`: Localiza o CSS de saída depois de compilar menos arquivo com estilos

* `srcOriginalRecursivePath`: Localiza o código-fonte do seu visual

* `coverageFolder`: Determina o local em que o relatório de cobertura deve ser criado

O arquivo de configuração inclui as seguintes propriedades:

* `singleRun: true`: Os testes são executados em um sistema de CI (integração contínua) ou podem ser executados uma vez. Você pode alterar a configuração para *false* para depurar seus testes. O Karma mantém o navegador em execução para que você possa usar o console para depuração.

* `files: [...]`: Nessa matriz, você pode especificar os arquivos a serem carregados no navegador. Normalmente, há arquivos de origem, casos de teste, bibliotecas (Jasmine, utilitários de teste). Você pode adicionar outros arquivos à lista, conforme necessário.

* `preprocessors`: Nesta seção, você configurará ações executadas antes da execução dos testes de unidade. Eles preparam o typescript para JavaScript, preparam os arquivos de source map e geram o relatório de cobertura de código. Você pode desabilitar `coverage` ao depurar seus testes. A cobertura gera código adicional para verificar o código para a cobertura de teste, o que complica a depuração dos testes.

Para obter descrições de todas as configurações do karma, vá para a página [Arquivo de Configuração do Karma](https://karma-runner.github.io/1.0/config/configuration-file.html).

Para sua conveniência, você pode adicionar um comando de teste em `scripts`:

```json
{
    "scripts": {
        "pbiviz": "pbiviz",
        "start": "pbiviz start",
        "typings":"node node_modules/typings/dist/bin.js i",
        "lint": "tslint -r \"node_modules/tslint-microsoft-contrib\"  \"+(src|test)/**/*.ts\"",
        "pretest": "pbiviz package --resources --no-minify --no-pbiviz --no-plugin",
        "test": "karma start"
    }
    ...
}
```

Agora você está pronto para começar a escrever seus testes de unidade.

## <a name="check-the-dom-element-of-the-visual"></a>Verificar o elemento DOM do visual

Para testar o Visual, primeiro crie uma instância do visual.

### <a name="create-a-visual-instance-builder"></a>Criar um construtor de instância do visual

Adicione um arquivo *visualBuilder.ts* à pasta de *test* usando o seguinte código:

```typescript
import {
    VisualBuilderBase
} from "powerbi-visuals-utils-testutils";

import {
    BarChart as VisualClass
} from "../src/visual";

import  powerbi from "powerbi-visuals-api";
import VisualConstructorOptions = powerbi.extensibility.visual.VisualConstructorOptions;

export class BarChartBuilder extends VisualBuilderBase<VisualClass> {
    constructor(width: number, height: number) {
        super(width, height);
    }

    protected build(options: VisualConstructorOptions) {
        return new VisualClass(options);
    }

    public get mainElement() {
        return this.element.children("svg.barChart");
    }
}
```

Há um método `build` para criar uma instância do seu visual. `mainElement` é um método Get, que retorna uma instância do elemento DOM (Modelo de Objeto do Documento) de "raiz" em seu visual. O getter é opcional, mas facilita a gravação do teste de unidade.

Agora você tem um build de uma instância do seu visual. Vamos escrever o caso de teste. O caso de teste verifica os elementos SVG criados quando o visual é exibido.

### <a name="create-a-typescript-file-to-write-test-cases"></a>Criar um arquivo typescript para escrever casos de teste

Adicione um arquivo *visualTest.ts* para os casos de teste usando o seguinte código:

```typescript
import powerbi from "powerbi-visuals-api";

import { BarChartBuilder } from "./VisualBuilder";

import {
    BarChart as VisualClass
} from "../src/visual";

import VisualBuilder = powerbi.extensibility.visual.test.BarChartBuilder;

describe("BarChart", () => {
    let visualBuilder: VisualBuilder;
    let dataView: DataView;

    beforeEach(() => {
        visualBuilder = new VisualBuilder(500, 500);
    });

    it("root DOM element is created", () => {
        expect(visualBuilder.mainElement).toBeInDOM();
    });
});
```

Vários métodos são chamados:

* [`describe`](https://jasmine.github.io/api/2.6/global.html#describe): Descreve um caso de teste. No contexto da estrutura do Jasmine, geralmente descreve um conjunto ou grupo de especificações.

* `beforeEach`: É chamado antes de cada chamada do método `it`, que é definida no método [`describe`](https://jasmine.github.io/api/2.6/global.html#beforeEach).

* [`it`](https://jasmine.github.io/api/2.6/global.html#it): Define uma única especificação. O método `it` deve conter um ou mais `expectations`.

* [`expect`](https://jasmine.github.io/api/2.6/global.html#expect): Cria uma expectativa para uma especificação. Uma especificação tem êxito se todas as expectativas são aprovadas sem falhas.

* `toBeInDOM`: Um dos métodos de *correspondências*. Para obter mais informações sobre correspondências, confira [Namespace do Jasmine: correspondências](https://jasmine.github.io/api/2.6/matchers.html).

Para obter mais informações sobre o Jasmine, confira a página [Documentação da estrutura do Jasmine](https://jasmine.github.io/).

### <a name="launch-unit-tests"></a>Iniciar testes de unidade

Esse teste verifica se o elemento SVG raiz dos visuais é criado. Para executar o teste de unidade, digite o seguinte comando na ferramenta de linha de comando:

```cmd
npm run test
```

`karma.js` executa o caso de teste no navegador Chrome.

![Karma JavaScript aberto no Chrome](./media/karmajs-chrome.png)

> [!NOTE]
> Você deve instalar o Google Chrome localmente.

Na janela de linha de comando, você obterá a seguinte saída:

```cmd
> karma start

23 05 2017 12:24:26.842:WARN [watcher]: Pattern "E:/WORKSPACE/PowerBI/PowerBI-visuals-sampleBarChart/data/*.csv" does not match any file.
23 05 2017 12:24:30.836:WARN [karma]: No captured browser, open https://localhost:9876/
23 05 2017 12:24:30.849:INFO [karma]: Karma v1.3.0 server started at https://localhost:9876/
23 05 2017 12:24:30.850:INFO [launcher]: Launching browser Chrome with unlimited concurrency
23 05 2017 12:24:31.059:INFO [launcher]: Starting browser Chrome
23 05 2017 12:24:33.160:INFO [Chrome 58.0.3029 (Windows 10 0.0.0)]: Connected on socket /#2meR6hjXFmsE_fjiAAAA with id 5875251
Chrome 58.0.3029 (Windows 10 0.0.0): Executed 1 of 1 SUCCESS (0.194 secs / 0.011 secs)

=============================== Coverage summary ===============================
Statements   : 27.43% ( 65/237 )
Branches     : 19.84% ( 25/126 )
Functions    : 43.86% ( 25/57 )
Lines        : 20.85% ( 44/211 )
================================================================================
```

### <a name="how-to-add-static-data-for-unit-tests"></a>Como adicionar dados estáticos para testes de unidade

Crie o arquivo *visualData.ts* na pasta *test* usando o seguinte código:

```typescript
import powerbi from "powerbi-visuals-api";
import DataView = powerbi.DataView;

import {
    testDataViewBuilder,
    getRandomNumbers
} from "powerbi-visuals-utils-testutils";

export class SampleBarChartDataBuilder extends TestDataViewBuilder {
    public static CategoryColumn: string = "category";
    public static MeasureColumn: string = "measure";

    public constructor() {
        super();
        ...
    }

    public getDataView(columnNames?: string[]): DataView {
        let dateView: any = this.createCategoricalDataViewBuilder([
            ...
        ],
        [
            ...
        ], columnNames).build();

        // there's client side computed maxValue
        let maxLocal = 0;
        this.valuesMeasure.forEach((item) => {
                if (item > maxLocal) {
                    maxLocal = item;
                }
        });
        (<any>dataView).categorical.values[0].maxLocal = maxLocal;
    }
}
```

A classe `SampleBarChartDataBuilder` estende `TestDataViewBuilder` e implementa o método abstrato `getDataView`.

Quando você coloca dados em buckets de campos de dados, o Power BI produz um objeto categórico `dataview` baseado em seus dados.

![Buckets de campo de dados](./media/fields-buckets.png)

Em testes de unidade, você não tem funções principais do Power BI para reproduzir os dados. Mas você precisa mapear seus dados estáticos para `dataview` categóricos. A `TestDataViewBuilder` classe pode ajudá-lo a mapeá-la.

Para obter mais informações sobre mapeamento de Exibição de Dados, confira [DataViewMappings](https://github.com/Microsoft/PowerBI-visuals/blob/master/Capabilities/DataViewMappings.md).

No método `getDataView`, você chama o método `createCategoricalDataViewBuilder` com seus dados.

No arquivo [capabilities.json](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/master/capabilities.json#L2) do visual `sampleBarChart`, temos objetos dataRoles e dataViewMapping:

```json
"dataRoles": [
    {
        "displayName": "Category Data",
        "name": "category",
        "kind": "Grouping"
    },
    {
        "displayName": "Measure Data",
        "name": "measure",
        "kind": "Measure"
    }
],
"dataViewMappings": [
    {
        "conditions": [
            {
                "category": {
                    "max": 1
                },
                "measure": {
                    "max": 1
                }
            }
        ],
        "categorical": {
            "categories": {
                "for": {
                    "in": "category"
                }
            },
            "values": {
                "select": [
                    {
                        "bind": {
                            "to": "measure"
                        }
                    }
                ]
            }
        }
    }
],
```

Para gerar o mesmo mapeamento, você deve definir os seguintes parâmetros para o método `createCategoricalDataViewBuilder`:

```typescript
([
    {
        source: {
            displayName: "Category",
            queryName: SampleBarChartData.ColumnCategory,
            type: ValueType.fromDescriptor({ text: true }),
            roles: {
                Category: true
            },
        },
        values: this.valuesCategory
    }
],
[
    {
        source: {
            displayName: "Measure",
            isMeasure: true,
            queryName: SampleBarChartData.MeasureColumn,
            type: ValueType.fromDescriptor({ numeric: true }),
            roles: {
                Measure: true
            },
        },
        values: this.valuesMeasure
    },
], columnNames)
```

Em que `this.valuesCategory` é uma matriz de categorias:

```ts
public valuesCategory: string[] = ["Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday", "Sunday"];
```

E `this.valuesMeasure` é uma matriz de medidas para cada categoria:

```ts
public valuesMeasure: number[] = [742731.43, 162066.43, 283085.78, 300263.49, 376074.57, 814724.34, 570921.34];
```

agora você pode usar a classe `SampleBarChartDataBuilder` em seu teste de unidade.

A `ValueType` classe é definida no pacote powerbi-visuals-utils-testutils. E o método `createCategoricalDataViewBuilder` requer a biblioteca `lodash`.

Adicione esses pacotes às dependências.

Em `package.json` na seção `devDependencies`

```json
"lodash-es": "4.17.1",
"powerbi-visuals-utils-testutils": "2.2.0"
```

Chame

```cmd
npm install
```

para instalar a biblioteca `lodash-es`.

Agora, você pode executar o teste de unidade novamente. Você deve obter a seguinte saída:

```cmd
> karma start

23 05 2017 16:19:54.318:WARN [watcher]: Pattern "E:/WORKSPACE/PowerBI/PowerBI-visuals-sampleBarChart/data/*.csv" does not match any file.
23 05 2017 16:19:58.333:WARN [karma]: No captured browser, open https://localhost:9876/
23 05 2017 16:19:58.346:INFO [karma]: Karma v1.3.0 server started at https://localhost:9876/
23 05 2017 16:19:58.346:INFO [launcher]: Launching browser Chrome with unlimited concurrency
23 05 2017 16:19:58.394:INFO [launcher]: Starting browser Chrome
23 05 2017 16:19:59.873:INFO [Chrome 58.0.3029 (Windows 10 0.0.0)]: Connected on socket /#NcNTAGH9hWfGMCuEAAAA with id 3551106
Chrome 58.0.3029 (Windows 10 0.0.0): Executed 1 of 1 SUCCESS (1.266 secs / 1.052 secs)

=============================== Coverage summary ===============================
Statements   : 56.72% ( 135/238 )
Branches     : 32.54% ( 41/126 )
Functions    : 66.67% ( 38/57 )
Lines        : 52.83% ( 112/212 )
================================================================================
```

Seu visual é aberto no navegador Chrome, conforme mostrado:

![O UT inicia no Chrome](./media/karmajs-chrome-ut-runned.png)

O resumo mostra que a cobertura aumentou. Para saber mais sobre a cobertura de código atual, abra `coverage\index.html`.

![Índice de cobertura do UT](./media/code-coverage-index.png)

Ou examine o escopo da pasta `src`:

![Cobertura da pasta src](./media/code-coverage-src-folder.png)

No escopo do arquivo, você pode exibir o código-fonte. Os utilitários `Coverage` realçarão a linha em vermelho se determinado código não for executado durante os testes de unidade.

![Cobertura de código do arquivo visual.ts](./media/code-coverage-visual-src.png)

> [!IMPORTANT]
> A cobertura de código não significa que você tenha boa cobertura de funcionalidade do visual. Um teste de unidade simples fornece uma cobertura de mais de 96% em `src\visual.ts`.

## <a name="next-steps"></a>Próximas etapas

Quando seu visual está pronto, você pode enviá-lo para publicação. Para saber mais, confira [Publicar visuais do Power BI no AppSource](../office-store.md).
