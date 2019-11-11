---
title: inserir um relatório do Servidor de Relatórios do Power BI usando um iFrame no SharePoint Server
description: Este artigo mostra como inserir um relatório do Servidor de Relatórios do Power BI em um iFrame no SharePoint Server
author: maggiesMSFT
ms.author: maggies
ms.date: 08/12/2019
ms.topic: conceptual
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.custom: mvc
ms.openlocfilehash: 195be0766e135dcccc2124a998fb5a32e8703d5b
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/09/2019
ms.locfileid: "73875008"
---
# <a name="embed-a-power-bi-report-server-report-using-an-iframe-in-sharepoint-server"></a>inserir um relatório do Servidor de Relatórios do Power BI usando um iFrame no SharePoint Server

Neste artigo, você aprenderá a inserir um relatório do Servidor de Relatórios do Power BI usando um iFrame em uma página do SharePoint. Se estiver trabalhando com o SharePoint Online, o Servidor de Relatórios do Power BI deverá estar acessível publicamente. No SharePoint Online, o Web part do Power BI que funciona com o serviço do Power BI não funcionará com o Servidor de Relatórios do Power BI.  

![Exemplo do iFrame](media/quickstart-embed/quickstart_embed_01.png)

## <a name="prerequisites"></a>Pré-requisitos
* [Servidor de Relatórios do Power BI](https://powerbi.microsoft.com/report-server/) instalado e configurado.
* [Power BI Desktop otimizado para o Servidor de Relatórios do Power BI](install-powerbi-desktop.md) instalado.
* Um ambiente do [SharePoint](https://docs.microsoft.com/sharepoint/install/install) instalado e configurado.

## <a name="create-the-power-bi-report-url"></a>Criar a URL do relatório do Power BI

1. Baixe o exemplo do GitHub: [Demonstração do Blog](https://github.com/Microsoft/powerbi-desktop-samples). Selecione **Clonar ou baixar** e, em seguida, selecione **Baixar ZIP**.

    ![Baixar o arquivo PBIX de exemplo](media/quickstart-embed/quickstart_embed_14.png)

2. Descompacte o arquivo e abra o arquivo .pbix de exemplo no Power BI Desktop otimizado para o Servidor de Relatórios do Power BI.

    ![Ferramenta do PBI RS Desktop](media/quickstart-embed/quickstart_embed_02.png)

3. Salve o relatório no **Servidor de Relatórios do Power BI**. 

    ![Salvar no PBI RS](media/quickstart-embed/quickstart_embed_03.png)

4. Exiba o relatório no portal da Web do Servidor de Relatórios do Power BI.

    ![Portal da Web](media/quickstart-embed/quickstart_embed_04.png)

### <a name="capture-the-url-parameter"></a>Capturar o parâmetro da URL

Depois que você tiver sua URL, poderá criar um iFrame em uma página do SharePoint para hospedar o relatório. Para qualquer URL de relatório do Servidor de Relatórios do Power BI, adicione o seguinte parâmetro da cadeia de caracteres de consulta para inserir seu relatório em um iFrame do SharePoint: `?rs:embed=true`.

   Por exemplo:
    ``` 
    https://myserver/reports/powerbi/Sales?rs:embed=true
    ```
## <a name="embed-the-report-in-a-sharepoint-iframe"></a>Inserir o relatório em um iFrame do SharePoint

1. Navegue até a página **Conteúdo do Site** no SharePoint.

    ![Página de Conteúdo do site](media/quickstart-embed/quickstart_embed_05.png)

2. Escolha a página em que deseja adicionar seu relatório.

    ![Aplicativo da página de Conteúdo do site](media/quickstart-embed/quickstart_embed_06.png)

3. Selecione o ícone de engrenagem na parte superior direita e, em seguida, selecione **Editar página**.

    ![Opção Editar página](media/quickstart-embed/quickstart_embed_07.png)

4. Selecione **Adicionar um Web Part**.

5. Em **Categorias**, selecione **Mídia e Conteúdo**. Em **Partes**, selecione **Editor de Conteúdo** e, em seguida, **Adicionar**.

    ![Selecionar Web Part do Editor de Conteúdo](media/quickstart-embed/quickstart_embed_09.png)

6. Selecione **Clique aqui para adicionar novo conteúdo**.

7. No menu superior, selecione **Formatar Texto** e selecione **Editar Fonte**.

     ![Editar Fonte](media/quickstart-embed/quickstart_embed_11.png)

8. Na janela **Editar Fonte**, cole o código do iFrame na **Código-fonte HTML** e selecione **OK**.

    ![Código do iFrame](media/quickstart-embed/quickstart_embed_12.png)

     Por exemplo:
     ```html
     <iframe width="800" height="600" src="https://myserver/reports/powerbi/Sales?rs:embed=true" frameborder="0" allowFullScreen="true"></iframe>
     ```

9. No menu superior, selecione **Página** e, em seguida, selecione **Interromper Edição**.

    ![Parar a Edição](media/quickstart-embed/quickstart_embed_13.png)

    O relatório é exibido na página.

    ![Exemplo do iFrame](media/quickstart-embed/quickstart_embed_01.png)

## <a name="next-steps"></a>Próximas etapas

- [Criar um relatório do Power BI para o Servidor de Relatórios do Power BI](quickstart-create-powerbi-report.md).  
- [Criar um relatório paginado para o Servidor de Relatórios do Power BI](quickstart-create-paginated-report.md).  

Mais perguntas? [Experimente a Comunidade do Power BI](https://community.powerbi.com/). 