---
title: Conectar-se ao MailChimp com o Power BI
description: MailChimp para o Power BI
author: maggiesMSFT
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 04/26/2019
ms.author: maggies
LocalizationGroup: Connect to services
ms.openlocfilehash: 8599c22246183d28d13eb80f05250baa8dc27f5d
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "64579031"
---
# <a name="connect-to-mailchimp-with-power-bi"></a>Conectar-se ao MailChimp com o Power BI
Este artigo explica a efetuar pull de seus dados de sua conta do MailChimp com um aplicativo de modelo do Power BI. O aplicativo de modelo gera um espaço de trabalho com um dashboard, um conjunto de relatórios e um conjunto de dados para permitir que você explore seus dados do MailChimp. Use a análise dos [painéis do MailChimp](https://powerbi.microsoft.com/integrations/mailchimp) para identificar rapidamente as tendências existentes em suas campanhas, seus relatórios e seus assinantes individuais. Os dados são atualizados diariamente, garantindo que os dados que você está monitorando seja atualizados.

Depois de instalar o aplicativo de modelo, você pode alterar o painel e relatório. Em seguida, você pode distribuí-lo como um aplicativo para seus colegas em sua organização.

Conectar-se para o [MailChimp modelo aplicativo](https://app.powerbi.com/getdata/services/mailchimp) para o Power BI.

## <a name="how-to-connect"></a>Como se conectar

[!INCLUDE [powerbi-service-apps-get-more-apps](./includes/powerbi-service-apps-get-more-apps.md)]

3. Selecione **MailChimp** \> **obtê-lo agora**.
4. Na **instalar este aplicativo do Power BI?** selecionar **instalar**.
4. No **aplicativos** painel, selecione o **MailChimp** lado a lado.

    ![Bloco de aplicativo do Power BI MailChimp](media/service-connect-to-mailchimp/power-bi-connect-mailchimp.png)

6. Na **começar com seu novo aplicativo**, selecione **Conecte dados**.

    ![Introdução ao novo aplicativo](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-connect-data.png)

1. Para o Método de Autenticação, selecione **oAuth2** \> **Entrar**.
   
    Quando solicitado, insira suas credenciais do MailChimp e siga o processo de autenticação.
   
    Na primeira vez que você se conectar, o Power BI solicitará a você o acesso somente leitura à sua conta. Selecione **Permitir** para iniciar o processo de importação. Ele pode levar alguns minutos, dependendo do volume de dados em sua conta.
   
    ![Conector do Power BI para MailChimp](media/service-connect-to-mailchimp/allow.png)

5. Depois que o Power BI importar os dados, abre o painel do MailChimp.
   
    ![Painel do Power BI MailChimp](media/service-connect-to-mailchimp/power-bi-mailchimp-dashboard.png)

## <a name="modify-and-distribute-your-app"></a>Modificar e distribuir seu aplicativo

Você instalou o aplicativo de modelo do MailChimp. Isso significa que você também criou o espaço de trabalho de aplicativo do MailChimp. No espaço de trabalho, você pode alterar o relatório e painel de controle e, em seguida, distribuí-lo como um *aplicativo* para seus colegas em sua organização. 

1. Para exibir todo o conteúdo do seu novo espaço de trabalho de MailChimp, na barra de navegação à esquerda, selecione **espaços de trabalho** > **MailChimp**. 

    ![Espaço de trabalho do MailChimp no painel de navegação à esquerda](media/service-connect-to-mailchimp/power-bi-mailchimp-left-nav.png)

    Essa exibição é a lista de conteúdo para o espaço de trabalho. No canto superior direito, você verá **atualizar aplicativo**. Quando você estiver pronto para distribuir seu aplicativo para seus colegas, que é onde você começará.

    ![Lista de conteúdo do MailChimp](media/service-connect-to-mailchimp/power-bi-mailchimp-content-list.png)

2. Selecione **relatórios** e **conjuntos de dados** para ver os outros elementos no espaço de trabalho. 

    Leia sobre [distribuindo aplicativos](service-create-distribute-apps.md) para seus colegas.

## <a name="next-steps"></a>Próximas etapas

* [Criar novos workspaces no Power BI](service-create-the-new-workspaces.md)
* [Instalar e usar aplicativos no Power BI](consumer/end-user-apps.md)
* [Aplicativos do Power BI para serviços externos](service-connect-to-services.md)
* Dúvidas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)

