---
title: Administrando o Power BI – perguntas frequentes
description: Confira as respostas a perguntas frequentes sobre a inscrição no Power BI, o gerenciamento de locatários e outras tarefas administrativas.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 11/16/2018
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: c32f4b0a03ba751d5b8cbd6e98633275ece9222b
ms.sourcegitcommit: 6a44cb5b0328b60ebe7710378287f1e20bc55a25
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70877818"
---
# <a name="administering-power-bi---frequently-asked-questions-faq"></a>Administrando o Power BI – perguntas frequentes

Este artigo aborda perguntas frequentes sobre a administração do Power BI. Para obter uma visão geral da administração do Power BI, confira [O que é administração do Power BI?](service-admin-administering-power-bi-in-your-organization.md).

## <a name="whats-in-this-article"></a>O que você encontrará neste artigo

### <a name="sign-up-for-power-bi-section"></a>Inscrever-se no serviço do Power BI

* [Usar o PowerShell](#using-powershell)
* [Como os usuários podem se inscrever no Power BI?](#how-do-users-sign-up-for-power-bi)
* [Como usuários individuais em minha organização podem se inscrever?](#how-do-individual-users-in-my-organization-sign-up)
* [Como impedir que os usuários ingressem em meu locatário existente do Office 365?](#how-can-i-prevent-users-from-joining-my-existing-office-365-tenant)
* [Como permitir que usuários ingressem em meu locatário existente do Office 365?](#how-can-i-allow-users-to-join-my-existing-office-365-tenant)
* [Como verificar se tenho o bloqueio ativado no locatário?](#how-do-i-check-if-i-have-the-block-on-in-the-tenant)
* [Como impedir que meus usuários existentes comecem a usar o Power BI?](#how-can-i-prevent-my-existing-users-from-starting-to-use-power-bi)
* [Como posso permitir que meus usuários existentes se inscrevam no Power BI?](#how-can-i-allow-my-existing-users-to-sign-up-for-power-bi)

### <a name="administration-of-power-bi-section"></a>Seção Administração do Power BI

* [Como isso mudará minha maneira de gerenciar identidades dos usuários em minha organização hoje?](#how-will-this-change-the-way-i-manage-identities-for-users-in-my-organization-today)
* [Como podemos gerenciar o Power BI?](#how-do-we-manage-power-bi)
* [Se eu tiver vários domínios, poderei controlar o locatário do Office 365 ao qual os usuários serão adicionados?](#if-i-have-multiple-domains-can-i-control-the-office-365-tenant-that-users-get-added-to)
* [Como remover o Power BI para usuários que já se inscreveram?](#how-do-i-remove-power-bi-for-users-that-already-signed-up)
* [Como posso saber se novos usuários ingressaram em meu locatário?](#how-do-i-know-when-new-users-have-joined-my-tenant)
* [Devo estar preparado para outras questões?](#are-there-any-additional-things-i-should-prepare-for)
* [Onde está localizado meu locatário do Power BI?](#where-is-my-power-bi-tenant-located)
* [O que é o SLA (Contrato de Nível de Serviço) do Power BI?](#what-is-the-power-bi-sla)
* [Como o Power BI lida com alta disponibilidade e failover?](#how-does-power-bi-handle-high-availability-and-failover)

### <a name="security-in-power-bi-section"></a>Seção Segurança no Power BI

* [O Power BI atende aos requisitos de conformidade regional, nacional e específicos do setor?](#does-power-bi-meet-national-regional-and-industry-specific-compliance-requirements)
* [Como funciona a segurança no Power BI?](#how-does-security-work-in-power-bi)

## <a name="sign-up-for-power-bi"></a>Inscrever-se no Power BI

### <a name="using-powershell"></a>Usar o PowerShell

Alguns dos procedimentos nesta seção exigem scripts do Windows PowerShell. Se você não estiver familiarizado com o PowerShell, recomendamos o [guia de Introdução ao PowerShell](http://go.microsoft.com/fwlink/p/?LinkID=286814). Para executar os scripts, primeiro instale a versão mais recente de 64 bits do [Azure Active Directory PowerShell para Graph](/powershell/azure/active-directory/).

### <a name="how-do-users-sign-up-for-power-bi"></a>Como os usuários podem se inscrever para obter o Power BI?

Como administrador, você pode se inscrever no Power BI no [site do Power BI](https://powerbi.microsoft.com) ou na página [Comprar serviços](https://admin.microsoft.com/AdminPortal/Home#/catalog) do Centro de administração do Microsoft 365. Quando um administrador se inscreve no Power BI, ele pode atribuir licenças aos usuários que devem ter acesso.

Além disso, usuários individuais em sua organização poderão se inscrever no Power BI por meio do [site do Power BI](https://powerbi.microsoft.com). Quando um usuário da organização se inscreve no Power BI, ele recebe automaticamente uma licença do Power BI. Para saber mais, confira [Inscrever-se no Power BI como indivíduo](service-self-service-signup-for-power-bi.md) e [Licenciamento do Power BI na sua organização](service-admin-licensing-organization.md).

### <a name="how-do-individual-users-in-my-organization-sign-up"></a>Como usuários individuais em minha organização podem se inscrever?

Há três cenários que podem se aplicar aos usuários em sua organização:

* **Cenário 1**: sua organização já tem um ambiente existente do Office 365 e o usuário que está se inscrevendo no Power BI já tem uma conta do Office 365.
    Neste cenário, se um usuário já tiver uma conta corporativa ou de estudante no locatário (por exemplo, contoso.com), mas ainda não tiver o Power BI, a Microsoft simplesmente ativará o plano para essa conta. O usuário receberá uma notificação automática sobre como usar o serviço do Power BI.

* **Cenário 2**: sua organização tem um ambiente existente do Office 365, mas o usuário que está se inscrevendo no Power BI não tem uma conta do Office 365.
    Nesse cenário, o usuário tem um endereço de email no domínio da organização (por exemplo, contoso.com), mas ainda não tem uma conta do Office 365. Nesse caso, o usuário pode se inscrever no Power BI e receber automaticamente uma conta. Isso permite o acesso do usuário ao serviço do Power BI. Por exemplo, se uma funcionária chamada Nancy usar seu email de trabalho (por exemplo, nancy@contoso.com) para se inscrever, a Microsoft a adicionará automaticamente como usuária no ambiente do Office 365 da Contoso e ativará o Power BI para essa conta.

* **Cenário 3**: sua organização não tem um ambiente do Office 365 conectado ao seu domínio de email.
    Sua organização não precisa tomar ações administrativas para tirar proveito do Power BI. O serviço adiciona usuários a um novo diretório de usuários, somente para nuvem. Também é possível escolher tomar o controle como administrador de locatários e gerenciá-los.

> [!IMPORTANT]
> Se sua organização tiver vários domínios de email e você preferir que todas as extensões de endereço de email estejam no mesmo locatário, adicione todos os domínios de endereço de email a um locatário do Azure Active Directory antes de todos os usuários se inscreverem. Após a criação dos usuários, não há nenhum mecanismo automatizado para movê-los entre locatários. Para saber mais sobre esse processo, confira [Se eu tiver vários domínios, poderei controlar o locatário do Office 365 ao qual os usuários são adicionados?](#if-i-have-multiple-domains-can-i-control-the-office-365-tenant-that-users-get-added-to) posteriormente neste artigo e [Adicionar um domínio ao Office 365](/office365/admin/setup/add-domain/).

### <a name="how-can-i-prevent-users-from-joining-my-existing-office-365-tenant"></a>Como impedir que os usuários ingressem em meu locatário existente do Office 365?

Há etapas que você pode tomar, como administrador, para impedir que os usuários ingressem em seu locatário existente do Office 365. Se você bloquear o acesso, as tentativas de inscrição dos usuários falharão e eles verão uma mensagem orientando a entrar em contato com o administrador da organização. Não será preciso repetir esse processo se você já tiver desabilitado a distribuição automática de licenças (por exemplo, pelo Office 365 Education para estudantes, docentes e funcionários).

Use o seguinte script do PowerShell para impedir que novos usuários ingressem em um locatário gerenciado. ([Saiba mais sobre o PowerShell][1].)

```powershell
$msolcred = get-credential
connect-msolservice -credential $msolcred

Set-MsolCompanySettings -AllowEmailVerifiedUsers $false
```

> [!NOTE]
> O bloqueio de acesso impede que novos usuários em sua organização se inscrevam no Power BI. Os usuários que se inscreverem no Power BI antes da desabilitação de novas inscrições para sua organização ainda manterão suas licenças. Para remover um usuário, confira [Como faço para remover o Power BI para usuários que já se inscreveram?](#how-do-i-remove-power-bi-for-users-that-already-signed-up) mais adiante neste artigo.

### <a name="how-can-i-allow-users-to-join-my-existing-office-365-tenant"></a>Como permitir que usuários ingressem em meu locatário existente do Office 365?

Use o script do PowerShell a seguir para permitir que novos usuários ingressem em um locatário gerenciado. ([Saiba mais sobre o PowerShell][1].)

```powershell
$msolcred = get-credential
connect-msolservice -credential $msolcred

Set-MsolCompanySettings -AllowEmailVerifiedUsers $true
```

### <a name="how-do-i-check-if-i-have-the-block-on-in-the-tenant"></a>Como verificar se tenho o bloqueio ativado no locatário?

Use o seguinte script do PowerShell para verificar as configurações. *AllowEmailVerifiedUsers* deve ser false. ([Saiba mais sobre o PowerShell][1].)

```powershell
$msolcred = get-credential
connect-msolservice -credential $msolcred

Get-MsolCompanyInformation | fl allow*
```

### <a name="how-can-i-prevent-my-existing-users-from-starting-to-use-power-bi"></a>Como impedir que meus usuários existentes comecem a usar o Power BI?

A configuração do Azure AD que controla isso é **AllowAdHocSubscriptions**. A maioria dos locatários tem essa configuração definida como *true*, o que significa que ela está habilitada. Se você adquiriu o Power BI por meio de um parceiro, ela pode estar definida como *false*, o que significa que ela está desabilitada.

Use o script do PowerShell a seguir para desabilitar assinaturas ad hoc. ([Saiba mais sobre o PowerShell][1].)

1. Entre no Azure Active Directory usando suas credenciais do Office 365. A primeira linha do script do PowerShell a seguir solicita suas credenciais. Na segunda linha, você será conectado ao Azure Active Directory.

    ```powershell
     $msolcred = get-credential
     connect-msolservice -credential $msolcred
    ```

   ![Captura da tela de entrada do Azure Active Directory por meio do PowerShell](media/service-admin-licensing-organization/azure-ad-sign-in.png)

1. Depois de entrar, execute o comando a seguir para ver para como seu locatário está configurado atualmente.

    ```powershell
     Get-MsolCompanyInformation | fl AllowAdHocSubscriptions
    ```

1. Execute o comando a seguir para habilitar (`$true`) ou desabilitar (`$false`) **AllowAdHocSubscriptions**.

    ```powershell
     Set-MsolCompanySettings -AllowAdHocSubscriptions $false
    ```

> [!NOTE]
> Use o sinalizador **AllowAdHocSubscriptions** para controlar vários recursos de usuários em sua organização, inclusive a capacidade de inscrição dos usuários no Serviço do Azure Rights Management. Alterar esse sinalizador afetará todos esses recursos. Com uma configuração de *false*, os usuários ainda podem se inscrever para uma avaliação do Pro.

### <a name="how-can-i-allow-my-existing-users-to-sign-up-for-power-bi"></a>Como posso permitir que meus usuários existentes se inscrevem no Power BI?

Para permitir que os usuários existentes se inscrevam no Power BI, execute o comando listado para a pergunta anterior, mas em vez de `$false`, passe `$true` na última etapa.

## <a name="administration-of-power-bi"></a>Administração do Power BI

### <a name="how-will-this-change-the-way-i-manage-identities-for-users-in-my-organization-today"></a>Como isso mudará minha maneira de gerenciar identidades dos usuários em minha organização hoje?

Há três cenários que podem se aplicar aos usuários em sua organização:

* **Cenário 1**: se a organização já tiver um ambiente existente do Office 365 e todos os usuários na organização tiverem contas do Office 365, o gerenciamento de identidades não mudará.

* **Cenário 2**: se a organização já tiver um ambiente existente do Office 365, mas nem todos os usuários na organização tiverem contas do Office 365, criaremos um usuário no locatário e atribuiremos licenças com base no endereço corporativo ou de estudante do usuário.

    Como resultado, o número de usuários que você está gerenciando em qualquer momento específico crescerá conforme os usuários em sua organização se inscreverem no serviço.

* **Cenário 3**: se a organização não tiver um ambiente do Office 365 conectado ao domínio de email, não haverá alteração na forma de gerenciar identidades.

    O serviço adiciona usuários a um novo diretório de usuários, somente para nuvem. Além disso, é possível escolher tomar o controle como administrador de locatários e gerenciá-los.

### <a name="how-do-we-manage-power-bi"></a>Como podemos gerenciar o Power BI?

O Power BI fornece um portal de administração que permite exibir estatísticas de uso, fornece um link para o Centro de administração do Microsoft 365 para gerenciar usuários e grupos e fornece a capacidade de controlar configurações de locatário.

Para usar o portal de administração do Power BI, sua conta deve ser marcada como **Administrador Global** no Office 365 ou no Azure Active Directory ou ter recebido a função de administrador do serviço do Power BI na sua conta de usuário. Para saber mais, confira [Noções básicas sobre a função de administrador do Power BI](service-admin-role.md) e [Portal de administração do Power BI](service-admin-portal.md).

### <a name="if-i-have-multiple-domains-can-i-control-the-office-365-tenant-that-users-get-added-to"></a>Se eu tiver vários domínios, poderei controlar o locatário do Office 365 ao qual os usuários serão adicionados?

Se você não fizer nada, o serviço criará um locatário para cada domínio e subdomínio de email de usuários. Se você quiser que todos os usuários estejam no mesmo locatário independentemente de suas extensões de endereço de email: Crie um locatário de destino antecipadamente ou use um locatário existente. Em seguida, adicione todos os domínios e subdomínios existentes que deseja consolidar neste locatário. Todos os usuários com endereços de email que terminam com esses domínios e subdomínios ingressam automaticamente no locatário de destino ao se inscreverem.

> [!IMPORTANT]
> Após a criação dos usuários, não há nenhum mecanismo automatizado compatível para movê-los entre locatários. Para saber mais sobre a adição de domínios a um único locatário do Office 365, consulte [Adicionar usuários e domínio ao Office 365](/office365/admin/setup/add-domain/).

### <a name="how-do-i-remove-power-bi-for-users-that-already-signed-up"></a>Como remover o Power BI para usuários que já se inscreveram?

Se um usuário se inscrever no Power BI, mas você não quiser mais que ele tenha acesso ao Power BI, remova a licença do Power BI desse usuário.

1. Acesse o [centro de administração do Microsoft 365](https://admin.microsoft.com/AdminPortal/Home#/homepage).

1. Na barra de navegação à esquerda, selecione **Usuários** > **Usuários ativos**.

1. Localize o usuário cuja licença você quer remover e selecione o nome dele.

    Você também pode executar o gerenciamento de licenças em massa a usuários. Para fazer isso, selecione vários usuários e selecione **Editar licenças de produto**.

1. Na página de detalhes do usuário, ao lado de **Licenças de produto**, selecione **Editar**.

1. De acordo com a licença aplicada à conta, defina **Power BI (free)** ou **Power BI Pro** como **Desativado**.

1. Selecione **Salvar**.

### <a name="how-do-i-know-when-new-users-have-joined-my-tenant"></a>Como posso saber se novos usuários ingressaram em meu locatário?

Os usuários que ingressarem no seu locatário como parte desse programa receberão uma licença exclusiva, que você poderá filtrar dentro no painel do usuário ativo, no dashboard do administrador. Para criar essa nova exibição, execute estas etapas.

1. Navegue até o [Centro de administração do Microsoft 365](https://admin.microsoft.com/AdminPortal/Home#/homepage).

1. Na barra de navegação à esquerda, selecione **Usuários** > **Usuários ativos**.

1. No menu **Modos de exibição**, selecione **Adicionar modo de exibição personalizado**.

1. Nomeie o novo modo de exibição e, em **Licença de produto atribuída**, selecione **Power BI (Gratuito)** ou **Power BI Pro**.

    Você só pode ter uma licença por exibição. Se você tiver as licenças **Power BI (Gratuito)** e **Power BI Pro** em sua organização, poderá criar dois modos de exibição.

1. Insira quaisquer outras condições desejadas e selecione **Adicionar**.

1. Após a criação do novo modo de exibição, ele estará disponível no menu **Modos de exibição**.

### <a name="are-there-any-additional-things-i-should-prepare-for"></a>Devo estar preparado para outras questões?

Você pode perceber um aumento nas solicitações de redefinição de senha. Para saber mais sobre esse processo, confira [Redefinir a senha do usuário](/office365/admin/add-users/reset-passwords).

Você pode remover um usuário do seu locatário pelo processo padrão no centro de administração do Microsoft 365. No entanto, se o usuário ainda tiver um endereço de email ativo de sua organização, ele poderá reingressar, a menos que você bloqueie o ingresso de todos os usuários.

### <a name="where-is-my-power-bi-tenant-located"></a>Onde está localizado meu locatário do Power BI?

Para saber em qual região de dados seu locatário do Power BI está, confira [Onde está localizado meu locatário do Power BI?](service-admin-where-is-my-tenant-located.md).

### <a name="what-is-the-power-bi-sla"></a>O que é o SLA do Power BI?

Para saber mais sobre o SLA (Contrato de Nível de Serviço) do Power BI, confira o artigo [Termos de licenciamento e documentação](http://www.microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&DocumentTypeId=37) na seção **Licenciamento** do site de Licenciamento da Microsoft.

### <a name="how-does-power-bi-handle-high-availability-and-failover"></a>Como o Power BI lida com alta disponibilidade e failover?

Para saber mais sobre a alta disponibilidade e o failover, veja [Perguntas frequentes de recuperação de desastre, failover e alta disponibilidade do Power BI](service-admin-failover.md).

## <a name="security-in-power-bi"></a>Segurança no Power BI

### <a name="does-power-bi-meet-national-regional-and-industry-specific-compliance-requirements"></a>O Power BI atende aos requisitos de conformidade regional, nacional e específicos do setor?

Para saber mais sobre a conformidade do Power BI, consulte o [Microsoft Trust Center](https://www.microsoft.com/TrustCenter/CloudServices/business-application-platform/default.aspx).

### <a name="how-does-security-work-in-power-bi"></a>Como funciona a segurança no Power BI?

A Microsoft criou o Power BI de acordo com o Office 365, que por sua vez baseia-se nos serviços do Azure, como o Azure Active Directory. Para obter uma visão geral da arquitetura do Power BI, consulte [Segurança do Power BI](service-admin-power-bi-security.md).

## <a name="next-steps"></a>Próximas etapas

[Portal de administração do Power BI](service-admin-portal.md)  
[Noções básicas sobre a função de administrador do Power BI](service-admin-role.md)  
[Inscrição de autoatendimento no Power BI](service-self-service-signup-for-power-bi.md)  
[Compra do Power BI Pro](service-admin-purchasing-power-bi-pro.md)  
[O que é o Power BI Premium?](service-premium-what-is.md)  
[Como comprar o Power BI Premium](service-admin-premium-purchase.md)  
[White paper do Power BI Premium](https://aka.ms/pbipremiumwhitepaper)  
[Gerenciar seu grupo no Power BI e no Office 365](service-manage-app-workspace-in-power-bi-and-office-365.md)  
[Gerenciamento de contas de usuário do Office 365](/office365/servicedescriptions/office-365-platform-service-description/user-account-management/)  
[Gerenciamento de grupo do Office 365](/office365/admin/email/create-edit-or-delete-a-security-group/)  

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)

[1]: https://docs.microsoft.com/powershell/scripting/overview