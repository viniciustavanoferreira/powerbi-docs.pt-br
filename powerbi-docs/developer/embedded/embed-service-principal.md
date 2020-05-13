---
title: Entidade de serviço com o Power BI
description: Saiba como registrar um aplicativo no Azure Active Directory usando a entidade de serviço e o segredo de um aplicativo para usar com o conteúdo inserido do Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.custom: ''
ms.date: 03/30/2020
ms.openlocfilehash: 40f713c2fd021ea8ecea5789b8ad0bc54cff2294
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83275951"
---
# <a name="embedding-power-bi-content-with-service-principal-and-application-secret"></a>Conteúdo inserido do Power BI com a entidade de serviço e o segredo do aplicativo

[!INCLUDE[service principal overview](../../includes/service-principal-overview.md)]

Este artigo descreve como a autenticação da entidade de serviço usa a *ID do Aplicativo* e o *Segredo do aplicativo*.

## <a name="method"></a>Método

Para usar a entidade de serviço e uma ID de aplicativo com as análises inseridas, siga estas etapas:

1. Crie um [aplicativo Azure AD](https://docs.microsoft.com/azure/active-directory/manage-apps/what-is-application-management).

    1. Crie um segredo do aplicativo do Azure AD.
    
    2. Obtenha a *ID do Aplicativo* e o *Segredo do aplicativo*.

    >[!NOTE]
    >Todas essas etapas são descritas na **etapa 1**. Para obter mais informações, confira o artigo [Criar um aplicativo do Azure AD](https://docs.microsoft.com/azure/active-directory/develop/howto-create-service-principal-portal).

2. Crie um grupo de segurança do Azure AD.

3. Habilite as configurações de administração do serviço do Power BI.

4. Adicione a entidade de serviço ao seu espaço de trabalho.

5. Insira seu conteúdo.

> [!IMPORTANT]
> Depois que você habilita a entidade de serviço para ser usada com o Power BI, as permissões do aplicativo do AD não estão mais em vigor. As permissões do aplicativo então são gerenciadas por meio do portal de administração do Power BI.

## <a name="step-1---create-an-azure-ad-app"></a>Etapa 1 – Criar um aplicativo do Azure AD

Crie um aplicativo do Azure AD usando um destes métodos:
* Crie o aplicativo no [portal do Microsoft Azure](https://portal.azure.com/#allservices)
* Crie um trabalho usando o [PowerShell](https://docs.microsoft.com/powershell/azure/create-azure-service-principal-azureps?view=azps-3.6.1).

### <a name="creating-an-azure-ad-app-in-the-microsoft-azure-portal"></a>Como criar o aplicativo do Azure AD no portal do Microsoft Azure

1. Entre no [Microsoft Azure](https://portal.azure.com/#allservices).

2. Pesquise **Registros de aplicativo** e clique no link **Registros de aplicativo**.

    ![registro de aplicativo do azure](media/embed-service-principal/azure-app-registration.png)

3. Clique em **Novo registro**.

    ![novo registro](media/embed-service-principal/new-registration.png)

4. Preencha as informações obrigatórias:
    * **Nome** – digite um nome para seu aplicativo
    * **Tipos de conta compatíveis**: selecione a conta do Azure AD de que você precisa
    * (Opcional) **URI de redirecionamento** – insira um URI, se necessário

5. Clique em **Registrar**.

6. Após o registro, a *ID do Aplicativo* estará disponível na guia **Visão geral**. Copie e salve a *ID do Aplicativo* para uso posterior.

    ![id do aplicativo](media/embed-service-principal/application-id.png)

7. Clique na guia **Certificados e segredos**.

     ![id do aplicativo](media/embed-service-principal/certificates-and-secrets.png)

8. Clique em **Novo segredo do cliente**

    ![novo segredo do cliente](media/embed-service-principal/new-client-secret.png)

9. Na janela *Adicionar um segredo do cliente*, insira uma descrição, especifique quando deseja que o segredo do cliente expire e clique em **Adicionar**.

10. Copie e salve o valor do *Segredo do cliente*.

    ![valor do segredo do cliente](media/embed-service-principal/client-secret-value.png)

    >[!NOTE]
    >Depois de sair dessa janela, o valor do segredo do cliente ficará oculto e você não poderá exibi-lo ou copiá-lo novamente.

### <a name="creating-an-azure-ad-app-using-powershell"></a>Criar um aplicativo do Azure AD usando o PowerShell

Esta seção inclui um script de exemplo para criar um novo aplicativo do Azure AD usando o [PowerShell](https://docs.microsoft.com/powershell/azure/create-azure-service-principal-azureps?view=azps-1.1.0).

```powershell
# The app ID - $app.appid
# The service principal object ID - $sp.objectId
# The app key - $key.value

# Sign in as a user that's allowed to create an app
Connect-AzureAD

# Create a new Azure AD web application
$app = New-AzureADApplication -DisplayName "testApp1" -Homepage "https://localhost:44322" -ReplyUrls "https://localhost:44322"

# Creates a service principal
$sp = New-AzureADServicePrincipal -AppId $app.AppId

# Get the service principal key
$key = New-AzureADServicePrincipalPasswordCredential -ObjectId $sp.ObjectId
```

## <a name="step-2---create-an-azure-ad-security-group"></a>Etapa 2 – Criar um grupo de segurança do Azure AD

Sua entidade de serviço não tem acesso a nenhum de seus conteúdo e APIs do Power BI. Para dar acesso à entidade de serviço, crie um grupo de segurança no Azure AD e adicione a entidade de serviço que você criou a esse grupo de segurança.

Há duas maneiras de criar um grupo de segurança do Azure AD:
* Manualmente (no Azure)
* Usar o PowerShell

### <a name="create-a-security-group-manually"></a>Criar manualmente um grupo de segurança

Para criar manualmente um grupo de segurança no Azure, siga as instruções no artigo [Criar um grupo básico e adicionar membros usando o Azure Active Directory](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-groups-create-azure-portal). 

### <a name="create-a-security-group-using-powershell"></a>Criar um grupo de segurança usando o PowerShell

Abaixo está um exemplo de script para criar um novo grupo de segurança e adicionar um aplicativo ao grupo de segurança.

>[!NOTE]
>Caso queira habilitar o acesso à entidade de serviço para toda a organização, ignore essa etapa.

```powershell
# Required to sign in as a tenant admin
Connect-AzureAD

# Create an Azure AD security group
$group = New-AzureADGroup -DisplayName <Group display name> -SecurityEnabled $true -MailEnabled $false -MailNickName notSet

# Add the service principal to the group
Add-AzureADGroupMember -ObjectId $($group.ObjectId) -RefObjectId $($sp.ObjectId)
```

## <a name="step-3---enable-the-power-bi-service-admin-settings"></a>Etapa 3 – Habilitar as configurações de administração do serviço do Power BI

Para que um aplicativo do Azure AD possa acessar o conteúdo e as APIs do Power BI, um administrador de Power BI precisa habilitar o acesso à entidade de serviço no portal de administração do Power BI.

Adicione o grupo de segurança que você criou no Azure AD à seção de grupo de segurança específica nas **Configurações do desenvolvedor**.

>[!IMPORTANT]
>As entidades de serviço têm acesso a quaisquer configurações de locatário para as quais estejam habilitadas. Dependendo das configurações de administrador, isso inclui grupos de segurança específicos ou de toda a organização.
>
>Para restringir o acesso da entidade de serviço a configurações de locatário específicas, permita o acesso somente a grupos de segurança específicos. Como alternativa, você pode criar um grupo de segurança dedicado para entidades de serviço e excluí-lo das configurações de locatário desejadas.

![Portal de administração](media/embed-service-principal/admin-portal.png)

## <a name="step-4---add-the-service-principal-as-an-admin-to-your-workspace"></a>Etapa 4 – Adicionar a entidade de serviço como um administrador do novo espaço de trabalho

Para habilitar seus artefatos de acesso do aplicativo do Azure AD, como relatórios, painéis e conjuntos de dados no serviço do Power BI, adicione a entidade de serviço como um membro ou administrador do seu espaço de trabalho.

>[!NOTE]
>Esta seção fornece instruções para a interface do usuário. Você também pode adicionar uma entidade de serviço a um espaço de trabalho usando [Grupos – adicionar API de usuário de grupo](https://docs.microsoft.com/rest/api/power-bi/groups/addgroupuser).

1. Role até o espaço de trabalho para o qual você deseja habilitar o acesso e, no menu **Mais**, selecione **Acesso do espaço de trabalho**.

    ![Configurações do workspace](media/embed-service-principal/workspace-access.png)

2. Adicione a entidade de serviço como **Administrador** ou **Membro** do espaço de trabalho.

    ![Administrador do espaço de trabalho](media/embed-service-principal/add-service-principal-in-the-UI.png)

## <a name="step-5---embed-your-content"></a>Etapa 5 – Inserir seu conteúdo

Você pode inserir o conteúdo em um aplicativo de exemplo ou em seu próprio aplicativo.

* [Insira conteúdo usando o aplicativo de exemplo](embed-sample-for-customers.md#embed-content-using-the-sample-application)
* [Inserir conteúdo em seu aplicativo](embed-sample-for-customers.md#embed-content-within-your-application)

Depois de inserir o conteúdo, você estará pronto para [passar para a produção](embed-sample-for-customers.md#move-to-production).

## <a name="considerations-and-limitations"></a>Considerações e limitações

* A entidade de serviço só funciona com [novos workspaces](../../collaborate-share/service-create-the-new-workspaces.md).
* Não há suporte para **Meu Workspace** ao usar a entidade de serviço.
* É necessária capacidade dedicada ao passar para produção.
* Você não pode entrar no portal do Power BI usando a entidade de serviço.
* Direitos de administrador do Power BI são necessários para habilitar a entidade de serviço nas configurações do desenvolvedor no portal do administrador do Power BI.
* Você não pode instalar nem gerenciar um gateway de dados local usando a entidade de serviço.
* Os aplicativos [inseridos para sua organização](embed-sample-for-your-organization.md) não podem usar a entidade de serviço.
* Não há suporte para gerenciamento de [fluxos de dados](../../transform-model/service-dataflows-overview.md).
* No momento, a entidade de serviço não dá suporte a nenhuma API de administrador.
* Ao usar uma entidade de serviço com uma fonte de dados do [Azure Analysis Services](https://docs.microsoft.com/azure/analysis-services/analysis-services-overview), a própria entidade de serviço precisa ter permissões de uma instância do Azure Analysis Services. O uso de um grupo de segurança que contenha a entidade de serviço para essa finalidade não funciona.

## <a name="next-steps"></a>Próximas etapas

* [Power BI Embedded para seus clientes](embed-sample-for-customers.md)

* [Segurança em nível de linha usando o gateway de dados local com a entidade de serviço](embedded-row-level-security.md#on-premises-data-gateway-with-service-principal)