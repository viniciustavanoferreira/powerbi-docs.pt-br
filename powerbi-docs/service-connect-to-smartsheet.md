---
title: Conectar-se ao Smartsheet com o Power BI
description: Smartsheet para o Power BI
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 04/26/2019
ms.author: maggies
LocalizationGroup: Connect to services
ms.openlocfilehash: 841201aa87139b9630d6fc076d57109fb2b09804
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "64578978"
---
# <a name="connect-to-smartsheet-with-power-bi"></a>Conectar-se ao Smartsheet com o Power BI
Este artigo explica a efetuar pull de seus dados de sua conta de Smartsheet com um aplicativo de modelo do Power BI. O Smartsheet oferece uma plataforma fácil para colaboração e compartilhamento de arquivos. O aplicativo de modelo do Smartsheet para Power BI fornece um painel, relatórios e conjunto de dados que mostram uma visão geral da sua conta de Smartsheet. Você também pode usar [Power BI Desktop](desktop-connect-to-data.md) para se conectar diretamente às planilhas individuais em sua conta. 

Depois de instalar o aplicativo de modelo, você pode alterar o painel e relatório. Em seguida, você pode distribuí-lo como um aplicativo para seus colegas em sua organização.

Conectar-se para o [Smartsheet modelo aplicativo](https://app.powerbi.com/groups/me/getdata/services/smartsheet) para o Power BI.

>[!NOTE]
>Uma conta de administrador Smartsheet é preferida para conectar e carregar o aplicativo de modelo do Power BI, pois tem acesso adicional.

## <a name="how-to-connect"></a>Como se conectar

[!INCLUDE [powerbi-service-apps-get-more-apps](./includes/powerbi-service-apps-get-more-apps.md)]

3. Selecione **Smartsheet** \> **obtê-lo agora**.
4. Na **instalar este aplicativo do Power BI?** selecionar **instalar**.
4. No **aplicativos** painel, selecione o **Smartsheet** lado a lado.

    ![Bloco de aplicativo do Power BI Smartsheet](media/service-connect-to-smartsheet/power-bi-smartsheet-tile.png)

6. Na **começar com seu novo aplicativo**, selecione **Conecte dados**.

    ![Introdução ao novo aplicativo](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-connect-data.png)

4. Para o Método de Autenticação, selecione **oAuth2 \> Entrar**.
   
   Quando solicitado, insira suas credenciais do Smartsheet e siga o processo de autenticação.
   
   ![Credenciais do Smartsheet](media/service-connect-to-smartsheet/creds.png)
   
   ![Entrar do Smartsheet](media/service-connect-to-smartsheet/creds2.png)

5. Depois que o Power BI importar os dados, o painel de Smartsheet é aberto.
   
   ![Painel do Smartsheet](media/service-connect-to-smartsheet/power-bi-smartsheet-dashboard.png)

## <a name="modify-and-distribute-your-app"></a>Modificar e distribuir seu aplicativo

Você instalou o aplicativo de modelo do Smartsheet. Isso significa que você também criou o espaço de trabalho de aplicativo do Smartsheet. No espaço de trabalho, você pode alterar o relatório e painel de controle e, em seguida, distribuí-lo como um *aplicativo* para seus colegas em sua organização. 

1. Para exibir todo o conteúdo do seu novo espaço de trabalho de Smartsheet, na barra de navegação à esquerda, selecione **espaços de trabalho** > **Smartsheet**. 

    ![Espaço de trabalho do Smartsheet no painel de navegação à esquerda](media/service-connect-to-smartsheet/power-bi-smartsheet-workspace.png)

    Essa exibição é a lista de conteúdo para o espaço de trabalho. No canto superior direito, você verá **atualizar aplicativo**. Quando você estiver pronto para distribuir seu aplicativo para seus colegas, que é onde você começará. 

    ![Lista de conteúdo do Smartsheet](media/service-connect-to-smartsheet/power-bi-smartsheet-workspace-content.png)

2. Selecione **relatórios** e **conjuntos de dados** para ver os outros elementos no espaço de trabalho.

    Leia sobre [distribuindo aplicativos](service-create-distribute-apps.md) para seus colegas.

## <a name="whats-included"></a>O que está incluído
O Smartsheet modelo de aplicativo do Power BI inclui uma visão geral de sua conta de Smartsheet, como o número de espaços de trabalho, relatórios e as planilhas têm, quando são modificadas etc. Os usuários administradores também veem algumas informações sobre os usuários em seu sistema, como principais criadores de planilhas.  

Para se conectar diretamente a planilhas individuais em sua conta, é possível usar o conector do Smartsheet no [Power BI Desktop](desktop-connect-to-data.md).  

## <a name="next-steps"></a>Próximas etapas

* [Criar novos workspaces no Power BI](service-create-the-new-workspaces.md)
* [Instalar e usar aplicativos no Power BI](consumer/end-user-apps.md)
* [Conectar-se aos aplicativos do Power BI para serviços externos](service-connect-to-services.md)
* Dúvidas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)