---
title: Comprar e atribuir licenças do Power BI Pro
description: Saiba como comprar e atribuir licenças do Power BI Pro para que os usuários possam acessar todo o conteúdo e todos os recursos no serviço do Power BI.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: quickstart
ms.date: 10/21/2018
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: 4778fd8beb1faa30562bcf3dcca6d78bfac5dac4
ms.sourcegitcommit: 4a3afe761d2f4a5bd897fafb36b53961739e8466
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/20/2019
ms.locfileid: "69654809"
---
# <a name="purchase-and-assign-power-bi-pro-licenses"></a>Comprar e atribuir licenças do Power BI Pro

O Power BI Pro é uma licença individual que permite acesso a todo o conteúdo e a todas as funcionalidades no serviço do Power BI, incluindo a capacidade de compartilhar conteúdo e colaborar com outros usuários do Pro. Somente usuários Pro podem publicar conteúdo em workspaces do aplicativo, compartilhar dashboards e assinar dashboards e relatórios. Para obter mais informações, consulte [Recursos do Power BI por tipo de licença](service-features-license-type.md).

Este artigo explica como comprar licenças do Power BI Pro no Office 365. O artigo explica as duas opções disponíveis para atribuir essas licenças a usuários individuais: Office 365 e Azure (escolha uma delas).

## <a name="prerequisites"></a>Pré-requisitos

Você deve ser um membro da função [**Administrador global** ou **Administrador de cobrança**](https://support.office.com/article/about-office-365-admin-roles-da585eea-f576-4f55-a1e0-87090b6aaa9d) no Office 365.

Para atribuir licenças no Azure, você precisa ser um proprietário da assinatura do Azure que o Power BI usa para realizar pesquisas no Active Directory.

## <a name="purchase-licenses-in-office-365"></a>Comprar licenças no Office 365

Siga estas etapas para comprar licenças do Power BI Pro:

1. Abra o [Centro de administração do Microsoft 365](https://portal.office.com/adminportal/home#/homepage).

2. No painel de navegação esquerdo, selecione **Cobrança** > **Assinaturas**.

    ![Painel de navegação](media/service-admin-purchasing-power-bi-pro/service-purchasing-power-bi-pro-01.png)

3. No canto superior direito da página **Assinaturas**, selecione **Adicionar assinaturas**.

    ![Assinatura](media/service-admin-purchasing-power-bi-pro/service-purchasing-power-bi-pro-02.png)

4. Localize a oferta de assinatura desejada:

    Em **Enterprise Suite**, selecione **Office 365 Enterprise E5**.

    ![Assinatura do Office E5](media/service-admin-purchasing-power-bi-pro/service-purchasing-power-bi-pro-03.png)

    Em **Outros Planos**, selecione **Power BI Pro**.

    ![Assinatura do Power BI](media/service-admin-purchasing-power-bi-pro/service-purchasing-power-bi-pro-04.png)

5. Passe o mouse sobre as reticências ( **. . .** ) para a assinatura desejada e selecione **Comprar agora**.

    ![Comprar agora](media/service-admin-purchasing-power-bi-pro/service-purchasing-power-bi-pro-05.png)

6. Escolha **Pagar mensalmente** ou **Pagar por um ano inteiro**, de acordo com sua preferência de cobrança.

7. Em **Quantos usuários você deseja?** , insira a quantidade de licenças desejada e, em seguida, selecione **Fazer check-out agora** para concluir a transação.

8. Verifique se a assinatura adquirida agora está listada na página **Assinaturas**.

   ![Assinatura adquirida](media/service-admin-purchasing-power-bi-pro/service-purchasing-power-bi-pro-06.png)

9. Para adicionar mais licenças após a compra inicial, selecione **Power BI Pro** na página **Assinaturas** e, em seguida, selecione **Adicionar/Remover licenças**.

## <a name="assign-licenses-in-office-365"></a>Atribuir licenças no Office 365

Siga estas etapas para atribuir licenças do Power BI Pro a contas de usuário individuais:

1. Abra o [Centro de administração do Microsoft 365](https://portal.office.com/adminportal/home#/homepage).

2. No painel de navegação à esquerda, expanda **Usuários** e, em seguida, selecione **Usuários ativos**.

    ![Usuários ativos](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-05.png)

3. Selecione um usuário. Em seguida, em **Licenças de produto**, selecione **Editar**.

    ![Editar licenças de produto](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-06.png)

4. No **Power BI Pro**, mude a configuração para **Ativa** e, em seguida, selecione **Salvar**.

    ![Licenças de produto ativadas](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-07.png)

5. Em **Status** para a conta selecionada, verifique se a licença do Power BI Pro foi atribuída com êxito.

    ![Verificar o status da licença](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-08.png)

## <a name="assign-licenses-in-azure"></a>Atribuir licenças no Azure

Siga estas etapas para atribuir licenças do Power BI Pro a contas de usuário individuais:

1. Abra o [portal do Azure](https://ms.portal.azure.com/#@microsoft.onmicrosoft.com/dashboard/private/39bc3cf7-31a4-43f6-954c-f2d69ca2f0).

2. Na barra de navegação esquerda, selecione **Azure Active Directory**.

    ![Azure Active Directory](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-01.png)

3. Em **Azure Active Directory**, selecione **Licenças**.

    ![Licenças](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-02.png)

4. Em **Licenças**, selecione **Todos os produtos** e selecione **Power BI Pro** para ver a lista de usuários licenciados.

    ![Licenças – Todos os produtos](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-03.png)

5. Selecione **Atribuir** para adicionar uma licença do Power BI Pro a uma conta de usuário adicional.

    ![Atribuir licença](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-04.png)

## <a name="next-steps"></a>Próximas etapas

Agora que você atribuiu licenças, saiba mais sobre o Power BI Pro.

[Licenciamento do Power BI na sua organização](service-admin-licensing-organization.md)

[Encontrar usuários do Power BI que entraram](service-admin-access-usage.md)

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
