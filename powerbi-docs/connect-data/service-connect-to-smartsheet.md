---
title: Conectar-se ao Smartsheet com o Power BI
description: Smartsheet para o Power BI
author: paulinbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: how-to
ms.date: 05/04/2020
ms.author: painbar
LocalizationGroup: Connect to services
ms.openlocfilehash: a1cf9c96b976acbfd9a5cefe4d413b4aa0fac9bf
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85236278"
---
# <a name="connect-to-smartsheet-with-power-bi"></a>Conectar-se ao Smartsheet com o Power BI
Este artigo explica como extrair seus dados da sua conta do Smarsheet com um aplicativo de modelo do Power BI. O Smartsheet oferece uma plataforma fácil para colaboração e compartilhamento de arquivos. O aplicativo de modelo Smartsheet para Power BI fornece um painel, relatórios e o conjunto de dados que mostra uma visão geral da sua conta de Smartsheet. Também é possível usar o [Power BI Desktop](desktop-connect-to-data.md) para se conectar diretamente às planilhas individuais em sua conta. 

Depois de instalar o aplicativo de modelo, você pode alterar o dashboard e o relatório. Em seguida, pode distribuí-lo como um aplicativo para os colegas de sua organização.

Conectar-se ao [aplicativo de modelo Smartsheet](https://app.powerbi.com/groups/me/getapps/services/pbi-contentpacks.pbiapps-smartsheet) para Power BI.

>[!NOTE]
>É preferível uma conta de administrador Smartsheet para conectar e carregar o aplicativo de modelo do Power BI, pois o acesso é adicional.

## <a name="how-to-connect"></a>Como se conectar

[!INCLUDE [powerbi-service-apps-get-more-apps](../includes/powerbi-service-apps-get-more-apps.md)]

3. Selecione **Smartsheet** \> **Obter Agora**.
4. Em **Instalar este aplicativo do Power BI?** selecione **Instalar**.
4. No painel **Aplicativos**, selecione o bloco **Smartsheet**.

    ![Bloco do aplicativo SmartSheet do Power BI](media/service-connect-to-smartsheet/power-bi-smartsheet-tile.png)

6. Em **Introdução a seu novo aplicativo**, selecione **Conectar**.

    ![Introdução ao novo aplicativo](media/service-connect-to-zendesk/power-bi-new-app-connect-get-started.png)

4. Para o Método de Autenticação, selecione **oAuth2 \> Entrar**.
   
   Quando solicitado, insira suas credenciais do Smartsheet e siga o processo de autenticação.
   
   ![Credenciais do SmartSheet](media/service-connect-to-smartsheet/creds.png)
   
   ![Credenciais do SmartSheet](media/service-connect-to-smartsheet/creds2.png)

5. Depois que o Power BI importa os dados, o painel do Smartsheet é aberto.
   
   ![Painel do SmartSheet](media/service-connect-to-smartsheet/power-bi-smartsheet-dashboard.png)

## <a name="modify-and-distribute-your-app"></a>Modificar e distribuir seu aplicativo

Você instalou o aplicativo de modelo do Smartsheet. Isso significa que você também criou o workspace do Smartsheet. No workspace, você pode alterar o relatório e o dashboard e, em seguida, distribuí-lo como um *aplicativo* para os colegas em sua organização. 

1. Para exibir todo o conteúdo do seu novo workspace do Smartsheet, no painel de navegação, selecione **Workspaces** > **Smartsheet**. 

    ![Worspace do Smartsheet no painel de navegação](media/service-connect-to-smartsheet/power-bi-smartsheet-workspace.png)

    Esta exibição é a lista de conteúdo do workspace. No canto superior direito, você verá **Atualizar aplicativo**. Quando você estiver pronto para distribuir seu aplicativo para seus colegas, é aí que você começará. 

    ![Lista de conteúdo do Smartsheet](media/service-connect-to-smartsheet/power-bi-smartsheet-workspace-content.png)

2. Selecione **Relatórios** e **Conjunto de dados** para ver os outros elementos no workspace.

    Leia sobre [como distribuir aplicativos](../collaborate-share/service-create-distribute-apps.md) para seus colegas.

## <a name="whats-included"></a>O que está incluído
O aplicativo de modelo do Smartsheet para o Power BI inclui uma visão geral de sua conta do Smartsheet, tais como o número de workspaces, os relatórios e as planilhas existentes, informações sobre a data em que são modificados etc. Os usuários administradores também veem algumas informações sobre os usuários em seu sistema, como os principais criadores de planilhas.  

Para se conectar diretamente a planilhas individuais em sua conta, é possível usar o conector do Smartsheet no [Power BI Desktop](desktop-connect-to-data.md).  

## <a name="next-steps"></a>Próximas etapas

* [Criar novos workspaces no Power BI](../collaborate-share/service-create-the-new-workspaces.md)
* [Instalar e usar aplicativos no Power BI](../consumer/end-user-apps.md)
* [Conectar-se a aplicativos do Power BI para serviços externos](service-connect-to-services.md)
* Dúvidas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)