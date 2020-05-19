---
title: Conectar-se ao Zendesk com o Power BI
description: Zendesk para o Power BI
author: paulinbar
ms.reviewer: sarinas
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 05/04/2020
ms.author: painbar
LocalizationGroup: Connect to services
ms.openlocfilehash: 17d65296246100180f722dfccacb31ee9ebeade7
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83327152"
---
# <a name="connect-to-zendesk-with-power-bi"></a>Conectar-se ao Zendesk com o Power BI

Este artigo explica como extrair seus dados da sua conta do Zendesk com um aplicativo de modelo do Power BI. O aplicativo Zendesk oferece um dashboard e um conjunto de relatórios do Power BI que fornecem informações sobre os volumes de tíquetes e o desempenho do agente. Os dados são atualizados automaticamente uma vez por dia. 

Depois de instalar o aplicativo de modelo, você pode personalizar o dashboard e o relatório para realçar as informações mais importantes para você. Em seguida, pode distribuí-lo como um aplicativo para os colegas de sua organização.

Conecte-se ao [aplicativo de modelo do Zendesk](https://app.powerbi.com/getdata/services/zendesk) ou leia mais sobre a [integração do Zendesk](https://powerbi.microsoft.com/integrations/zendesk) com o Power BI.

Depois de instalar o aplicativo de modelo, você pode alterar o dashboard e o relatório. Em seguida, pode distribuí-lo como um aplicativo para os colegas de sua organização.

>[!NOTE]
>Você precisa de uma conta de administrador do Zendesk para se conectar. Mais detalhes sobre os [requisitos](#system-requirements) abaixo.

## <a name="how-to-connect"></a>Como se conectar

[!INCLUDE [powerbi-service-apps-get-more-apps](../includes/powerbi-service-apps-get-more-apps.md)]

3. Selecione **Zendesk** \> **Obter agora**.
4. Em **Instalar este aplicativo do Power BI?** selecione **Instalar**.
4. No painel **Aplicativos**, selecione o bloco **Zendesk**.

    ![Bloco do aplicativo Zendesk do Power BI](media/service-connect-to-zendesk/power-bi-zendesk-tile.png)

6. Em **Introdução a seu novo aplicativo**, selecione **Conectar**.

    ![Introdução ao novo aplicativo](media/service-connect-to-zendesk/power-bi-new-app-connect-get-started.png)

4. Forneça a URL associada à sua conta. A URL tem o formato **https://company.zendesk.com** . Veja detalhes sobre [como encontrar esses parâmetros](#finding-parameters) abaixo.
   
   ![Conectar-se ao Zendesk](media/service-connect-to-zendesk/pbi_zendeskconnect.png)

5. Quando solicitado, insira suas credenciais do Zendesk.  Selecione **oAuth 2** como o Mecanismo de Autenticação e clique em **Entrar**. Siga o fluxo de autenticação do Zendesk. (Caso você já tenha entrado no Zendesk em seu navegador, talvez suas credenciais não sejam solicitadas.)
   
   > [!NOTE]
   > Esse aplicativo de modelo requer que você se conecte com uma conta de administrador do Zendesk. 
   > 
   
   ![Entrar com oAuth2](media/service-connect-to-zendesk/pbi_zendesksignin.png)
6. Clique em **Permitir** para permitir que o Power BI acesse seus dados do Zendesk.
   
   ![Clique em Permitir](media/service-connect-to-zendesk/zendesk2.jpg)
7. Clique em **Conectar** para iniciar o processo de importação. 
8. Após o Power BI importar os dados, você verá a lista de conteúdo do seu aplicativo Zendesk: um novo dashboard, relatório e conjunto de dados.
9. Selecione o dashboard do Zendesk para iniciar o processo de exploração.

    ![Dashboard do Zendesk](media/service-connect-to-zendesk/power-bi-zendesk-dashboard.png)
   
## <a name="modify-and-distribute-your-app"></a>Modificar e distribuir seu aplicativo

Você instalou o aplicativo de modelo do Zendesk. Isso significa que você também criou o workspace do Zendesk. No workspace, você pode alterar o relatório e o dashboard e, em seguida, distribuí-lo como um *aplicativo* para os colegas em sua organização. 

1. Para exibir todo o conteúdo do seu novo workspace do Zendesk, no painel de navegação, selecione **Workspaces** > **Zendesk**. 

    ![Workspace do Zendesk no painel de navegação](media/service-connect-to-zendesk/power-bi-zendesk-workspace-left-nav.png)

    Esta exibição é a lista de conteúdo do workspace. No canto superior direito, você verá **Atualizar aplicativo**. Quando você estiver pronto para distribuir seu aplicativo para seus colegas, é aí que você começará. 

    ![Lista de conteúdo do Zendesk](media/service-connect-to-zendesk/power-bi-zendesk-content-list.png)

2. Selecione **Relatórios** e **Conjunto de dados** para ver os outros elementos no workspace.

    Leia sobre [como distribuir aplicativos](../collaborate-share/service-create-distribute-apps.md) para seus colegas.

## <a name="system-requirements"></a>Requisitos do sistema
Uma conta de administrador do Zendesk é necessária para acessar o aplicativo de modelo do Zendesk. Se você for um agente ou um usuário final e estiver interessado em ver seus dados no Zendesk, adicione uma sugestão e examine o conector do Zendesk no [Power BI Desktop](desktop-connect-to-data.md).

## <a name="finding-parameters"></a>Localizando parâmetros
A URL do Zendesk será igual à URL que você usa para se conectar em sua conta do Zendesk. Se você não lembrar da URL do Zendesk, use a [ajuda de logon](https://www.zendesk.com/login/) do Zendesk.

## <a name="troubleshooting"></a>Solução de problemas
Se você estiver com problemas para se conectar, verifique a URL do Zendesk e confirme que está usando uma conta de administrador do Zendesk.

## <a name="next-steps"></a>Próximas etapas

* [Criar novos workspaces no Power BI](../collaborate-share/service-create-the-new-workspaces.md)
* [Instalar e usar aplicativos no Power BI](../consumer/end-user-apps.md)
* [Conectar-se a aplicativos do Power BI para serviços externos](service-connect-to-services.md)
* Dúvidas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
