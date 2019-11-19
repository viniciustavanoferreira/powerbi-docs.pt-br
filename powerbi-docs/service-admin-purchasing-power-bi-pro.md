---
title: Comprar e atribuir licenças do Power BI Pro
description: Saiba como comprar e atribuir licenças de usuário do Power BI Pro para que os usuários possam acessar o conteúdo e colaborar com os próprios colegas no serviço do Power BI.
author: mgblythe
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: quickstart
ms.date: 10/29/2019
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: 72a158e2dca32d2199fcd48e2cc37bf4c90778ea
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/09/2019
ms.locfileid: "73873531"
---
# <a name="purchase-and-assign-power-bi-pro-user-licenses"></a>Comprar e atribuir licenças de usuário do Power BI Pro

O Power BI Pro é uma licença de usuário individual que permite aos usuários ler e interagir com relatórios e dashboards que outros usuários publicaram na serviço do Power BI e compartilhar conteúdo e colaborar com outros usuários do Power BI Pro. Somente os usuários com uma licença de usuário do Power BI Pro podem publicar ou compartilhar conteúdo com outros usuários ou consumir conteúdo criado por outros usuários, a menos que esse conteúdo seja hospedado em uma capacidade do Power BI Premium. Para obter mais informações, consulte [Recursos do Power BI por tipo de licença](service-features-license-type.md).

## <a name="purchase-and-assign-power-bi-pro-user-licenses"></a>Comprar e atribuir licenças de usuário do Power BI Pro

Este artigo explica como comprar licenças de usuário do Power BI Pro no centro de administração do Microsoft 365 e, em seguida, explica duas opções que os administradores têm para atribuir essas licenças a usuários individuais: no centro de administração do Microsoft 365 e no portal do Azure (escolha uma opção).

### <a name="prerequisites"></a>Pré-requisitos

Para comprar e atribuir licenças no centro de administração do Microsoft 365, você deve ser membro da função de **[administrador global ou administrador de cobrança](https://support.office.com/article/about-office-365-admin-roles-da585eea-f576-4f55-a1e0-87090b6aaa9d)** no Microsoft 365.

Para atribuir licenças no portal do Azure, você precisa ser um proprietário da assinatura do Azure que o Power BI usa para realizar pesquisas no Azure Active Directory.

### <a name="purchase-licenses-in-microsoft-365"></a>Comprar licenças no Microsoft 365

Siga estas etapas para comprar licenças do Power BI Pro no centro de administração do Microsoft 365:

1. Abra o [Centro de administração do Microsoft 365](https://portal.office.com/adminportal/home#/homepage).

2. No painel de navegação, selecione **Cobrança** > **Assinaturas**.

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

### <a name="assign-licenses-in-the-microsoft-365-admin-center"></a>Atribuir licenças no centro de administração do Microsoft 365

Siga estas etapas para atribuir licenças do Power BI Pro a contas de usuário individuais:

1. Abra o [Centro de administração do Microsoft 365](https://portal.office.com/adminportal/home#/homepage).

2. No painel de navegação, expanda **Usuários** e, em seguida, selecione **Usuários ativos**.

    ![Usuários ativos](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-05.png)

3. Selecione um usuário. Em seguida, em **Licenças de produto**, selecione **Editar**.

    ![Editar licenças de produto](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-06.png)

4. No **Power BI Pro**, mude a configuração para **Ativa** e, em seguida, selecione **Salvar**.

    ![Licenças de produto ativadas](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-07.png)

5. Em **Status** para a conta selecionada, verifique se a licença do Power BI Pro foi atribuída com êxito.

    ![Verificar o status da licença](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-08.png)

### <a name="assign-licenses-in-the-azure-portal"></a>Atribuir licenças no portal do Azure

Siga estas etapas para atribuir licenças do Power BI Pro a contas de usuário individuais:

1. Abra o [portal do Azure](https://ms.portal.azure.com/#@microsoft.onmicrosoft.com/dashboard/private/39bc3cf7-31a4-43f6-954c-f2d69ca2f0).

2. No painel de navegação, selecione **Azure Active Directory**.

    ![Azure Active Directory](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-01.png)

3. Em **Azure Active Directory**, selecione **Licenças**.

    ![Licenças](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-02.png)

4. Em **Licenças**, selecione **Todos os produtos** e selecione **Power BI Pro** para ver a lista de usuários licenciados.

    ![Licenças – Todos os produtos](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-03.png)

5. Selecione **Atribuir** para adicionar uma licença do Power BI Pro a uma conta de usuário.

    ![Atribuir licença](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-04.png)

## <a name="next-steps"></a>Próximas etapas

Agora que você atribuiu licenças, saiba mais sobre o Power BI Pro.

[Licenciamento do Power BI na sua organização](service-admin-licensing-organization.md)

[Encontrar usuários do Power BI que entraram](service-admin-access-usage.md)

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
