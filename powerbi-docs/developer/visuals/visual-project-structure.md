---
title: Estrutura do projeto do visual do Power BI
description: Este artigo descreve a estrutura de arquivos e pastas de um projeto do Power BI Visual
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.topic: conceptual
ms.subservice: powerbi-custom-visuals
ms.date: 01/12/2020
ms.openlocfilehash: 16e7a317102602ffb4faf04da0ed2cae588a2a4d
ms.sourcegitcommit: 052df769e6ace7b9848493cde9f618d6a2ae7df9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/14/2020
ms.locfileid: "75925528"
---
# <a name="power-bi-visual-project-structure"></a>Estrutura do projeto do visual do Power BI

A melhor maneira de começar a criar um novo visual no Power BI é usando a ferramenta [pbiviz](https://www.npmjs.com/package/powerbi-visuals-tools) para visuais do Power BI.

Para criar um novo visual, navegue até o diretório no qual você deseja que o visual do Power BI resida e execute o comando:

`pbiviz new <visual project name>`

A execução desse comando cria a pasta do visual do Power BI, que contém os seguintes arquivos:

```markdown
project
├───.vscode
│   ├───launch.json
│   └───settings.json
├───assets
│   └───icon.png
├───node_modules
├───src
│   ├───settings.ts
│   └───visual.ts
├───style
│   └───visual.less
├───capabilities.json
├───package-lock.json
├───package.json
├───pbiviz.json
├───tsconfig.json
└───tslint.json
```

## <a name="folder-and-file-description"></a>Descrição da pasta e do arquivo

Esta seção fornece informações de cada pasta e arquivo do diretório criado pela ferramenta **pbiciz** dos visuais do Power BI.  

### <a name="vscode"></a>.vscode

Esta pasta contém as configurações do projeto do VS Code.

Para configurar seu novo workspace, edite o arquivo `.vscode/settings.json`.

Saiba mais em [Configurações do Workspace e do Usuário](https://code.visualstudio.com/docs/getstarted/settings)

### <a name="assets"></a>ativos

Esta pasta contém o arquivo `icon.png`.

A ferramenta de visuais do Power BI usa esse arquivo como o novo ícone do visual do Power BI no painel de visualização Power BI.

<!--- ![Visualization pane](./media/visualization-pane-analytics-tab.png) --->

### <a name="src"></a>src

Esta pasta contém o código-fonte do visual.

Nessa pasta, a ferramenta de visuais do Power BI cria os seguintes arquivos:
* `visual.ts`, o código-fonte principal do visual.
* `settings.ts`, o código de configurações do visual. As classes no arquivo fornecem uma interface para definir as [propriedades do visual](./objects-properties.md#properties).

### <a name="style"></a>estilo

Essa pasta contém o arquivo `visual.less`, que contém os estilos do visual.

### <a name="capabilitiesjson"></a>capabilities.json

Esse arquivo contém as principais propriedades e configurações (ou [funcionalidades](./capabilities.md)) do visual. Ele permite que o visual declare recursos, objetos, propriedades e [mapeamentos de exibição de dados](./dataview-mappings.md) com suporte.

### <a name="package-lockjson"></a>package-lock.json

Esse arquivo é gerado automaticamente para qualquer operação em que o *npm* modifique a árvore `node_modules` ou o arquivo `package.json`.

Saiba mais sobre esse arquivo na documentação oficial do [npm-package-lock.json](https://docs.npmjs.com/files/package-lock.json).

### <a name="packagejson"></a>package.json

Este arquivo descreve o pacote do projeto. Normalmente contém informações sobre o projeto, como os autores, a descrição e as dependências do projeto.

Saiba mais sobre esse arquivo na documentação oficial do [npm-package.json](https://docs.npmjs.com/files/package.json.html).

### <a name="pbivizjson"></a>pbiviz.json

Este arquivo contém os metadados do visual.

Para exibir o arquivo `pbiviz.json` de exemplo com comentários que descrevem as entradas de metadados, confira a seção [entradas de metadados](#metadata-entries).

### <a name="tsconfigjson"></a>tsconfig.json

Um arquivo de configuração para [TypeScript](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html).

O arquivo deve conter o caminho para o arquivo **\*.ts** em que a classe principal do visual está localizada na propriedade `visualClassName` do arquivo `pbiviz.json`.

### <a name="tslintjson"></a>tslint.json

O arquivo contém a [configuração de TSLint](https://palantir.github.io/tslint/usage/configuration/).

## <a name="metadata-entries"></a>Entradas de metadados

Os comentários na seguinte legenda de código do arquivo `pbiviz.json` descrevem as entradas de metadados.

> [!NOTE]
> * Não há suporte para `externalJS` a partir da versão 3.x.x da ferramenta **pbiciz**.
> * Para receber suporte para localização, [adicione a localidade do Power BI ao seu visual](./localization.md).

```json
{
  "visual": {
     // The visual's internal name.
    "name": "<visual project name>",

    // The visual's display name.
    "displayName": "<visual project name>",

    // The visual's unique ID.
    "guid": "<visual project name>23D8B823CF134D3AA7CC0A5D63B20B7F",

    // The name of the visual's main class. Power BI creates the instance of this class to start using the visual in a Power BI report.
    "visualClassName": "Visual",

    // The visual's version number.
    "version": "1.0.0",
    
    // The visual's description (optional)
    "description": "",

    // A URL linking to the visual's support page (optional).
    "supportUrl": "",

    // A link to the source code available from GitHub (optional).
    "gitHubUrl": ""
  },
  // The version of the Power BI API the visual is using.
  "apiVersion": "2.6.0",

  // The name of the visual's author and email.
  "author": { "name": "", "email": "" },

  // 'icon' holds the path to the icon file in the assets folder; the visual's display icon.
  "assets": { "icon": "assets/icon.png" },

  // Contains the paths for JS libraries used in the visual.
  // Note: externalJS' isn't used in the Power BI visuals tool version 3.x.x or higher.
  "externalJS": null,

  // The path to the 'visual.less' style file.
  "style": "style/visual.less",

  // The path to the `capabilities.json` file.
  "capabilities": "capabilities.json",

  // The path to the `dependencies.json` file which contains information about R packages used in R based visuals.
  "dependencies": null,

  // An array of paths to files with localizations.
  "stringResources": []
}
```

## <a name="next-steps"></a>Próximas etapas

* Para entender as interações entre um visual, um usuário e o Power BI, confira [Conceito visual do Power BI](./power-bi-visuals-concept.md).

* Comece a desenvolver seus próprios visuais do Power BI desde o início com o [guia passo a passo](./custom-visual-develop-tutorial.md).