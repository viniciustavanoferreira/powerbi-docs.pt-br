---
title: Conectar-se ao Zendesk com o Power BI
description: Zendesk para o Power BI
author: maggiesMSFT
manager: kfile
ms.reviewer: sarinas
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 04/26/2019
ms.author: maggies
LocalizationGroup: Connect to services
ms.openlocfilehash: 1edc4179b000191dfeff87387417009bc28e0ee5
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "64578796"
---
# <a name="connect-to-zendesk-with-power-bi"></a>Conectar-se ao Zendesk com o Power BI

Este artigo explica a efetuar pull de seus dados de sua conta do Zendesk com um aplicativo de modelo do Power BI. O aplicativo do Zendesk oferece um painel do Power BI e um conjunto de relatórios do Power BI que fornecem informações sobre os volumes de tíquete e o desempenho do agente. Os dados são atualizados automaticamente uma vez por dia. 

Depois de instalar o aplicativo de modelo, você pode personalizar o painel e relatório para destacar as informações que lhe interessam. Em seguida, você pode distribuí-lo como um aplicativo para seus colegas em sua organização.

Conecte-se ao [pacote de conteúdo do Zendesk](https://app.powerbi.com/getdata/services/zendesk) ou leia mais sobre a [Integração do Zendesk](https://powerbi.microsoft.com/integrations/zendesk) com o Power BI.

Depois de instalar o aplicativo de modelo, você pode alterar o painel e relatório. Em seguida, você pode distribuí-lo como um aplicativo para seus colegas em sua organização.

>[!NOTE]
>Você precisa de uma conta de administrador do Zendesk para se conectar. Mais detalhes sobre os [requisitos](#system-requirements) abaixo.

## <a name="how-to-connect"></a>Como se conectar

[!INCLUDE [powerbi-service-apps-get-more-apps](./includes/powerbi-service-apps-get-more-apps.md)]

3. Selecione **Zendesk** \> **obtê-lo agora**.
4. Na **instalar este aplicativo do Power BI?** selecionar **instalar**.
4. No **aplicativos** painel, selecione o **Zendesk** lado a lado.

    ![Bloco de aplicativo do Power BI Zendesk](media/service-connect-to-zendesk/power-bi-zendesk-tile.png)

6. Na **começar com seu novo aplicativo**, selecione **Conecte dados**.

    ![Introdução ao novo aplicativo](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-connect-data.png)

4. Forneça a URL associada à sua conta. A URL tem o formato **https://company.zendesk.com** . Veja detalhes sobre [como encontrar esses parâmetros](#finding-parameters) abaixo.
   
   ![Conectar-se ao Zendesk](media/service-connect-to-zendesk/pbi_zendeskconnect.png)

5. Quando solicitado, insira suas credenciais do Zendesk.  Selecione **oAuth 2** como o Mecanismo de Autenticação e clique em **Entrar**. Siga o fluxo de autenticação do Zendesk. (Se você já tiver entrado Zendesk em seu navegador, você pode não ser solicitado para credenciais.)
   
   > [!NOTE]
   > Este pacote de conteúdo exige que você se conectar com uma conta de administrador do Zendesk. 
   > 
   
   ![Entrar com o oAuth2](media/service-connect-to-zendesk/pbi_zendesksignin.png)
6. Clique em **Permitir** para permitir que o Power BI acesse seus dados do Zendesk.
   
   ![Clique em permitir](media/service-connect-to-zendesk/zendesk2.jpg)
7. Clique em **Conectar** para iniciar o processo de importação. 
8. Depois que o Power BI importar os dados, consulte a lista de conteúdo para seu aplicativo Zendesk: um novo painel, relatório e conjunto de dados.
9. Selecione o painel para iniciar o processo de exploração.

    ![Painel do Zendesk](media/service-connect-to-zendesk/power-bi-zendesk-dashboard.png)
   
## <a name="modify-and-distribute-your-app"></a>Modificar e distribuir seu aplicativo

Você instalou o aplicativo de modelo do Zendesk. Isso significa que você também criou o espaço de trabalho de aplicativo do Zendesk. No espaço de trabalho, você pode alterar o relatório e painel de controle e, em seguida, distribuí-lo como um *aplicativo* para seus colegas em sua organização. 

1. Para exibir todo o conteúdo do seu novo espaço de trabalho de Zendesk, na barra de navegação à esquerda, selecione **espaços de trabalho** > **Zendesk**. 

    ![Espaço de trabalho do Zendesk no painel de navegação à esquerda](media/service-connect-to-zendesk/power-bi-zendesk-workspace-left-nav.png)

    Essa exibição é a lista de conteúdo para o espaço de trabalho. No canto superior direito, você verá **atualizar aplicativo**. Quando você estiver pronto para distribuir seu aplicativo para seus colegas, que é onde você começará. 

    ![Lista de conteúdo do Zendesk](media/service-connect-to-zendesk/power-bi-zendesk-content-list.png)

2. Selecione **relatórios** e **conjuntos de dados** para ver os outros elementos no espaço de trabalho.

    Leia sobre [distribuindo aplicativos](service-create-distribute-apps.md) para seus colegas.

## <a name="system-requirements"></a>Requisitos de sistema
Uma conta de administrador do Zendesk é necessária para acessar o pacote de conteúdo do Zendesk. Se você for um agente ou um usuário final e estiver interessado em ver seus dados do Zendesk, adicione uma sugestão e examine o conector do Zendesk na [Power BI Desktop](desktop-connect-to-data.md).

## <a name="finding-parameters"></a>Localizando parâmetros
A URL do Zendesk será igual à URL que você usa para se conectar em sua conta do Zendesk. Se você não lembrar da URL do Zendesk, use a [ajuda de logon](https://www.zendesk.com/login/) do Zendesk.

## <a name="troubleshooting"></a>Solução de problemas
Se você estiver tendo problemas para se conectar, verifique a URL do Zendesk e confirme se que você estiver usando uma conta de administrador do Zendesk.

## <a name="next-steps"></a>Próximas etapas

* [Criar novos workspaces no Power BI](service-create-the-new-workspaces.md)
* [Instalar e usar aplicativos no Power BI](consumer/end-user-apps.md)
* [Conectar-se aos aplicativos do Power BI para serviços externos](service-connect-to-services.md)
* Dúvidas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)

