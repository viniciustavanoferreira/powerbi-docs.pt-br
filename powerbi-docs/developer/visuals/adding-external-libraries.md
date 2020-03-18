---
title: Como adicionar bibliotecas externas aos visuais do Power BI
description: Este artigo descreve como usar bibliotecas externas em visuais do Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 02/24/2020
ms.openlocfilehash: 13d5f2ed62ddefb8ac99fe2c91c72fc599a15936
ms.sourcegitcommit: ced8c9d6c365cab6f63fbe8367fb33e6d827cb97
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/07/2020
ms.locfileid: "78922495"
---
# <a name="adding-external-libraries"></a>Adicionar bibliotecas externas

Este artigo descreve como usar bibliotecas externas em visuais do Power BI. Ele inclui informações sobre como instalar, importar e chamar bibliotecas externas, no código do visual do Power BI.

## <a name="javascript-libraries"></a>Bibliotecas JavaScript

1. Instale uma biblioteca JavaScript externa usando um gerenciador de pacotes, como *npm* ou *yarn*.
2. Importe os módulos necessários para os arquivos de origem usando a biblioteca externa.

>[!NOTE]
>Instale o pacote apropriado para adicionar digitações à biblioteca JavaScript, e obter IntelliSense e segurança para tempo de compilação.

### <a name="installing-the-d3-library"></a>Como instalar a biblioteca d3

Veja um exemplo de como instalar a [biblioteca d3](https://www.npmjs.com/package/d3) e o pacote [@types/d3](https://www.npmjs.com/package/@types/d3), usando [npm](https://www.npmjs.com/).

Para obter um exemplo completo, veja o código de [Visualizações do Power BI](https://github.com/microsoft/powerbi-visuals-gantt/blob/master/src/gantt.ts#L29).

1. Instale o pacote do *d3* e o pacote de *tipos do d3*.

    ```powershell
    npm install d3@5 --save
    npm install @types/d3@5 --save
    ```

2. Importe a biblioteca do *d3* nos arquivos que a usam, como `visual.ts`.

    ```typescript
    import * as d3 from "d3";
    ```

## <a name="css-framework"></a>Estrutura de CSS

1. Instale uma estrutura de CSS externa usando um gerenciador de pacotes, como *npm* ou *yarn*.
2. No arquivo `.less` do visual, inclua a instrução `import`.

### <a name="installing-bootstrap"></a>Como instalar o Bootstrap

Veja um exemplo de como instalar o [Bootstrap](https://www.npmjs.com/package/bootstrap) usando o [npm](https://www.npmjs.com/).

Para obter um exemplo completo, veja o código de [Visualizações do Power BI](https://github.com/Microsoft/powerbi-visuals-sankey/blob/c8200da56913cd8b253be949a35fad0f4472b6de/style/visual.less#L32).

1. Instale o pacote do *Bootstrap*.

    ```powershell
    npm install bootstrap --save
    ```

2. Inclua a instrução `import` no `visual.less`.

    ```less
    @import (less) "node_modules/bootstrap/dist/css/bootstrap.css";
    ```
