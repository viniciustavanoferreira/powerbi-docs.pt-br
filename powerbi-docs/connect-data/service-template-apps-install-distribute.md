---
title: Instalar e distribuir aplicativos de modelo em sua organização – Power BI
description: Saiba mais sobre como instalar, personalizar e distribuir aplicativos de modelo em sua organização no Power BI.
author: paulinbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: how-to
ms.date: 05/19/2020
ms.author: painbar
ms.openlocfilehash: e66d1b8b57af9ee04239e7222db742b64cc25883
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.contentlocale: pt-BR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85235706"
---
# <a name="install-and-distribute-template-apps-in-your-organization"></a>Instalar e distribuir aplicativos de modelo em sua organização

Você é um analista do Power BI? Caso seja, este artigo explica como instalar [aplicativos de modelo](service-template-apps-overview.md) para se conectar a muitos dos serviços que você usa para administrar sua empresa, como Salesforce, Microsoft Dynamics e Google Analytics. Em seguida, você pode modificar o dashboard e os relatórios pré-criados do aplicativo de modelo para atender às necessidades da sua organização e distribuí-los para seus colegas como [aplicativos](../consumer/end-user-apps.md). 

![Aplicativos do Power BI instalados](media/service-template-apps-install-distribute/power-bi-get-apps.png)

Se você estiver interessado em criar aplicativos de modelo por conta própria para distribuição fora da sua organização, confira [Criar um aplicativo de modelo no Power BI](service-template-apps-create.md). Com pouca ou nenhuma codificação, parceiros do Power BI podem criar aplicativos do Power BI e disponibilizá-los a clientes do Power BI. 

## <a name="prerequisites"></a>Pré-requisitos  

Para instalar, personalizar e distribuir um aplicativo de modelo, você precisa: 

* Uma [licença do Power BI Pro](../fundamentals/service-self-service-signup-for-power-bi.md).
* Permissões para instalar aplicativos de modelo no seu locatário.
* Um link para instalação válido para o aplicativo, que você obtém de AppSource ou do criador de aplicativos.
* Uma boa familiaridade com os [conceitos básicos do Power BI](../fundamentals/service-basic-concepts.md).

## <a name="install-a-template-app"></a>Instalar um aplicativo de modelo

1. No painel de navegação do serviço do Power BI, selecione **Aplicativos** > **Obter aplicativos**.

    ![Obter aplicativos](media/service-template-apps-install-distribute/power-bi-get-apps-arrow.png)

1. No Marketplace de aplicativos do Power BI que aparece, selecione **Aplicativos de modelo**. Todos os aplicativos de modelo disponíveis no AppSource serão exibidos. Navegue para localizar o aplicativo de modelo que você está procurando ou obtenha uma seleção filtrada usando a caixa de pesquisa. Digitar parte do nome de um aplicativo de modelo ou de uma categoria, como finanças, análise, marketing etc., facilitará a localização do item que você está procurando.

    ![Pesquisar no AppSource](media/service-template-apps-install-distribute/power-bi-appsource.png)

1. Ao encontrar o aplicativo de modelo que você está procurando, clique nele. A oferta do aplicativo de modelo será exibida. Clique em **OBTER AGORA**.

   ![Oferta do aplicativo de modelo](media/service-template-apps-install-distribute/power-bi-template-app-offer.png)

1. Na caixa de diálogo que aparece, selecione **Instalar**.

    ![Instalar aplicativo](media/service-template-apps-install-distribute/power-install-dialog.png)
    
    O aplicativo é instalado, junto ao workspace com o mesmo nome que tem todos os artefatos necessários para maior [personalização](#customize-and-share-the-app).

    > [!NOTE]
    > Se você usar um link de instalação para um aplicativo que não esteja listado no AppSource, uma caixa de diálogo de validação solicitará que você confirme sua escolha.
    >
    >Para poder instalar um aplicativo de modelo que não esteja listado na AppSource, você precisa solicitar as permissões relevantes ao administrador. Confira [Configurações do aplicativo de modelo](../admin/service-admin-portal.md#template-apps-settings) no portal do administrador do Power BI para detalhes.

    Quando a instalação for concluída com êxito, uma notificação indicará que seu novo aplicativo está pronto.

    ![Ir para o aplicativo](media/service-template-apps-install-distribute/power-bi-go-to-app.png)

## <a name="connect-to-data"></a>Conectar aos dados

1. Selecione **Ir para o aplicativo**.

1. Na janela **Introdução ao novo aplicativo**, selecione **Explorar**.

   ![Tela inicial do aplicativo de modelo](media/service-template-apps-install-distribute/power-bi-template-app-get-started.png)

   O aplicativo é aberto, mostrando os dados de exemplo.

1. Selecione o link **Conectar seus dados** na barra de notificação na parte superior da página.

   ![Aplicativo GitHub conectar o link de dados](media/service-template-apps-install-distribute/power-bi-template-app-connect-data.png)


    
    Isso abre uma caixa de diálogo ou uma série de caixas de diálogo em que você altera a fonte de dados dos dados de exemplo para sua própria fonte de dados. Isso geralmente significa a redefinição de parâmetros de conjunto de dados e credenciais de fonte de dados. Confira [Limitações conhecidas](service-template-apps-overview.md#known-limitations).
    
    No exemplo a seguir, a conexão com os dados envolve duas caixas de diálogo.

   ![Caixas de diálogo Conectar-se a dados](media/service-template-apps-install-distribute/power-bi-template-app-connect-to-data-dialogs.png)

    Depois que você terminar de preencher as caixas de diálogo de conexão, o processo de conexão será iniciado. Uma faixa informa que os dados estão sendo atualizados e, enquanto isso, você está exibindo dados de exemplo.

    ![Como exibir dados de exemplo](media/service-template-apps-install-distribute/power-bi-template-app-viewing-sample-data.png)

   Os dados de relatório serão atualizados automaticamente uma vez por dia, a menos que você tenha desabilitado isso durante o processo de entrada. Você também poderá [configurar sua agenda de atualização](./refresh-scheduled-refresh.md) para manter os dados do relatório atualizados, se assim desejar.

## <a name="customize-and-share-the-app"></a>Personalizar e compartilhar o aplicativo

Depois que você tiver se conectado aos seus dados e a atualização de dados estiver concluída, você poderá personalizar qualquer um dos relatórios e dashboards incluídos pelos aplicativos, bem como compartilhar o aplicativo com seus colegas. No entanto, todas as alterações feitas serão substituídas quando você atualizar o aplicativo com uma nova versão, a menos que você salve os itens alterados com nomes diferentes. [Veja detalhes sobre a substituição](#overwrite-behavior).

Para personalizar e compartilhar seu aplicativo, selecione o ícone de lápis no canto superior direito da página.

![Editar o aplicativo](media/service-template-apps-install-distribute/power-bi-template-app-edit-app.png)


Para obter informações sobre como editar artefatos no workspace, confira
* [Visão geral do editor de relatório no Power BI](../create-reports/service-the-report-editor-take-a-tour.md)
* [Conceitos básicos para designers no serviço do Power BI](../fundamentals/service-basic-concepts.md)

Quando terminar de fazer as alterações desejadas nos artefatos no workspace, você estará pronto para publicar e compartilhar o aplicativo. Confira [Publicar seu aplicativo](../collaborate-share/service-create-distribute-apps.md#publish-your-app) para saber como fazer isso.

## <a name="update-a-template-app"></a>Atualizar um aplicativo de modelo

De tempos em tempos, os criadores de aplicativo de modelo lançam novas versões aprimoradas de seus aplicativos de modelo por meio de AppSource, link direto ou ambos.

Se você originalmente baixou o aplicativo do AppSource, quando uma nova versão do aplicativo de modelo for disponibilizada, você será notificado de duas maneiras:
* Uma faixa de atualização é exibida no serviço do Power BI informando que uma nova versão do aplicativo está disponível.
  ![Notificação de atualização do aplicativo de modelo](media/service-template-apps-install-distribute/power-bi-new-app-version-notification-banner.png)
* Você recebe uma notificação no painel de notificação do Power BI.


  ![Notificação de atualização do aplicativo de modelo](media/service-template-apps-install-distribute/power-bi-new-app-version-notification-pane.png)

>[!NOTE]
>Se você obteve originalmente o aplicativo por meio de link direto, em vez de pela AppSource, a única maneira de saber quando uma nova versão está disponível é entrar em contato com o criador do aplicativo de modelo.

  Para instalar a atualização, clique em **Obter** na faixa de notificação ou no centro de notificações, ou localize o aplicativo novamente no AppSource e escolha **Obter agora**. Se você tem um link direto para a atualização do criador do aplicativo de modelo, basta clicar no link.
  
  Você será consultado sobre se deseja substituir a versão atual ou instalar a nova versão em um novo workspace. Por padrão, "substituir" está selecionado.

  ![Atualizar aplicativo de modelo](media/service-template-apps-install-distribute/power-bi-update-app-overwrite.png)

- **Substituir uma versão existente:** substitui o workspace existente pela versão atualizada do aplicativo de modelo. [Veja detalhes sobre a substituição](#overwrite-behavior).

- **Instalar em um novo workspace:** Instala uma nova versão do workspace e do aplicativo que você precisa reconfigurar (ou seja, conectar-se a dados, definir a navegação e permissões).

### <a name="overwrite-behavior"></a>Comportamento de substituição

* A substituição atualiza os relatórios, os dashboards e o conjunto de dados dentro do workspace, não do aplicativo. A substituição não altera a navegação, a configuração e a permissões do aplicativo.
* Depois de atualizar o workspace, você precisa **atualizar o aplicativo** para aplicar as alterações do workspace ao aplicativo.
* A substituição mantém os parâmetros e a autenticação configurados. Após a atualização, é iniciada uma atualização automática do conjunto de dados. **Durante essa atualização, o aplicativo, os relatórios e os dashboards apresentam dados de exemplo**.

  ![Dados de exemplo](media/service-template-apps-install-distribute/power-bi-sample-data.png)

* A substituição sempre apresenta dados de exemplo até que a atualização seja concluída. Se o autor do aplicativo de modelo tiver feito alterações ao conjunto de dados ou aos parâmetros, os usuários do workspace e do aplicativo não verão a nova data até que a atualização seja concluída. Em vez disso, eles continuarão vendo os dados de exemplo durante esse tempo.
* A substituição nunca exclui os novos relatórios ou dashboards que você adicionou ao workspace. Ela substitui apenas os relatórios e os dashboards originais por alterações do autor original.

>[!IMPORTANT]
>Lembre-se de [atualizar o aplicativo](#customize-and-share-the-app) após a substituição para aplicar as alterações aos relatórios e ao dashboard para os usuários do aplicativo organizacional.

## <a name="next-steps"></a>Próximas etapas

[Criar workspaces com seus colegas no Power BI](../collaborate-share/service-create-the-new-workspaces.md)
