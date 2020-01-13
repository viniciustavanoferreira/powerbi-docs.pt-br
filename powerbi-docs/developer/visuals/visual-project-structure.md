---
title: Estrutura do projeto do visual do Power BI
description: Este artigo descreve uma estrutura de projetos visuais
author: zBritva
ms.author: v-ilgali
ms.reviewer: ''
ms.service: powerbi
ms.topic: tutorial
ms.subservice: powerbi-custom-visuals
ms.date: 03/15/2019
ms.openlocfilehash: 728aba749f80710fdc0bb1e180b3318e63caa88c
ms.sourcegitcommit: 331ebf6bcb4a5cdbdc82e81a538144a00ec935d4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/28/2019
ms.locfileid: "75542083"
---
# <a name="power-bi-visual-project-structure"></a>Estrutura do projeto do visual do Power BI

Depois de executar o novo `<visual project name>` do pbiviz, a ferramenta cria a estrutura básica de arquivos e pastas na pasta `<visual project name>`.

## <a name="visual-project-structure"></a>Estrutura do projeto visual

![Estrutura do projeto visual](./media/visual-project-structure.png)

* `.vscode` – contém as configurações do projeto para VS Code. Para configurar seu novo workspace, edite o arquivo `.vscode/settings.json`. Leia mais [sobre as configurações de VS Code na documentação](https://code.visualstudio.com/docs/getstarted/settings)

* A pasta `assets` contém somente o arquivo `icon.png`. A ferramenta usa esse arquivo como um ícone do visual no painel Visualização do Power BI.

    ![Painel Visualização](./media/visualization-pane-analytics-tab.png)

* A pasta `node_modules` contém todos os pacotes [instalados pelo gerenciador de pacotes do nó](https://docs.npmjs.com/files/folders.html).

* A pasta `src` contém o código-fonte do visual. Por padrão, a ferramenta cria dois arquivos:

  * `visual.ts` – o código-fonte principal do visual.

  * `settings.ts` -o código de configurações do visual. As classes no arquivo simplificam o [trabalho com as propriedades do visual](./objects-properties.md#properties).

* A pasta `style` contém o arquivo `visual.less` com estilos para o visual.

* O arquivo `capabilities.json` contém as propriedades e as configurações principais do visual. Ele permite que o visual declare recursos, objetos, propriedades e mapeamentos de exibição de dados com suporte.

    Leia mais [sobre as funcionalidades na documentação](./capabilities.md).

* `package-lock.json` é gerado automaticamente para qualquer operação em que o NPM modifica a árvore `node_modules` ou então `package.json`.

    Leia mais [sobre `package-lock.json` na documentação oficial do NPM](https://docs.npmjs.com/files/package-lock.json).

* `package.json` descreve o pacote do projeto. Normalmente, ele contém informações sobre o projeto e os respectivos autores, descrição e dependências.

    Leia mais [sobre `package.json` na documentação oficial do NPM](https://docs.npmjs.com/files/package.json.html).

* `pbiviz.json` contém os metadados do visual. Especifique os metadados do visual neste arquivo.

    Conteúdo típico do arquivo:

  ```json
    {
        "visual": {
            "name": "<visual project name>",
            "displayName": "<visual project name>",
            "guid": "<visual project name>23D8B823CF134D3AA7CC0A5D63B20B7F",
            "visualClassName": "Visual",
            "version": "1.0.0",
            "description": "",
            "supportUrl": "",
            "gitHubUrl": ""
        },
        "apiVersion": "2.6.0",
        "author": { "name": "", "email": "" },
        "assets": { "icon": "assets/icon.png" },
        "externalJS": null,
        "style": "style/visual.less",
        "capabilities": "capabilities.json",
        "dependencies": null,
        "stringResources": []
    }
  ```

    onde

  * `name` – nome interno do visual.

  * `displayName` – o nome do visual na interface de interface do usuário do Power BI.

  * `guid` – ID exclusiva do visual.

  * `visualClassName` – o nome da classe principal para o visual. O Power BI cria a instância dessa classe para começar a usar o visual no relatório do Power BI.

  * `version` – o número de versão do visual.

  * `author` – contém o nome do autor e o email de contato.

  * `icon` em `assets` – o caminho para o arquivo de ícone do visual.

  * `externalJS` contém caminhos para bibliotecas JS usadas no visual.

    > [!IMPORTANT]
    > A versão mais recente da ferramenta 3.x.x ou superior não usa mais `externalJS`.

  * `style` é o caminho para os arquivos de estilo.

  * `capabilities` é o caminho para o arquivo `capabilities.json`.

  * `dependencies` é o caminho para o arquivo `dependencies.json`. `dependencies.json` contém informações sobre pacotes de R usados em visuais baseados em R.

  * `stringResources` é uma matriz de caminhos para arquivos com localizações.

  Leia mais [sobre a localização em visuais na documentação](./localization.md)

* `tsconfig.json` é arquivo de configuração para TypeScript.

    Leia mais [sobre a configuração de TypeScript na documentação oficial](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html)

    O `tsconfig.json` na seção `files` deve conter o caminho para o arquivo *.ts em que a classe principal do visual está localizada na propriedade `visualClassName` do arquivo `pbiviz.json`.

* O arquivo `tslint.json` contém a configuração de TSLint.

    Leia mais [sobre a configuração de TSLint na documentação oficial](https://palantir.github.io/tslint/usage/configuration/)

## <a name="next-steps"></a>Próximas etapas

* Leia mais [sobre o conceito de visual](./power-bi-visuals-concept.md) para entender melhor como o visual, o usuário e o Power BI interagem entre si.

* Comece a desenvolver seus próprios visuais do Power BI do zero [com o guia passo a passo](./custom-visual-develop-tutorial.md).
