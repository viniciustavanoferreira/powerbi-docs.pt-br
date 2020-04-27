---
title: Habilitar ou desabilitar a inscrição e a compra por autoatendimento
description: Informações sobre como os administradores podem desativar a capacidade dos usuários de se inscreverem para o Power BI e comprarem uma licença.
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/08/2020
ms.author: kfollis
LocalizationGroup: Administration
ms.openlocfilehash: 561d8b6cd0e17e885ced984315a04376400a2a58
ms.sourcegitcommit: b2cb0b02bdc451bf11a92a68f2c4d560a811f563
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81447500"
---
# <a name="enable-or-disable-self-service-sign-up-and-purchasing"></a>Habilitar ou desabilitar a inscrição e a compra por autoatendimento

Na maioria das organizações, a inscrição por autoatendimento está habilitada por padrão. Os usuários individuais em sua organização podem se inscrever para o Power BI usando suas próprias contas corporativas ou de estudante. Também pode ser oferecida aos usuários a opção de comprar uma licença de Power BI Pro diretamente, caso eles tentem usar um recurso que exija o Pro. Como administrador, você determina se deseja habilitar ou desabilitar a inscrição por autoatendimento. Você também pode controlar se os usuários em sua organização podem ou não fazer compras por autoatendimento para obter suas próprias licenças.

> [!NOTE]
>Se você tiver adquirido Power BI por meio de um CSP (provedor de soluções de nuvem) da Microsoft, a configuração poderá ser desabilitada para impedir que os usuários se inscrevam individualmente. Seu CSP também pode estar agindo como administrador global da sua organização, exigindo que você entre em contato com ele para ajudar na alteração dessa configuração.
>
>

Você usa os comandos do PowerShell para alterar as configurações que controlam a inscrição e a compra por autoatendimento. Há duas configurações que controlam se os usuários em sua organização podem ou não fazer inscrição por autoatendimento ou fazer compras por autoatendimento.

- Se você quiser desabilitar todas as inscrições por autoatendimento, altere uma configuração do Azure Active Directory chamada **AllowAdHocSubscriptions**, usando os comandos do PowerShell do Azure AD. Siga as etapas neste artigo para [habilitar ou desabilitar a inscrição por autoatendimento](#enable-or-disable-self-service-signup). Essa opção desativa a inscrição por autoatendimento para *todos* os aplicativos e serviços baseados em nuvem da Microsoft.

- Se você quiser impedir que os usuários adquiram suas próprias licenças do Pro, altere a configuração **AllowSelfServicePurchase** usando os comandos do MSCommerce PowerShell. Essa configuração permite que você desative a compra por autoatendimento para produtos específicos. Siga as etapas neste artigo para [habilitar ou desabilitar a compra por autoatendimento de licenças do Power BI Pro](#enable-or-disable-self-service-purchase).

## <a name="enable-or-disable-self-service-signup"></a>Habilitar ou desabilitar a inscrição por autoatendimento

Se a inscrição por autoatendimento estiver habilitada, o valor de **AllowAdHocSubscriptions** será *true*. Vamos dar uma olhada no que acontece quando você altera essa configuração para *false*:

- Se você alterar a configuração de true para false, novos usuários na sua organização serão impedidos de se inscreverem individualmente. Usuários que se inscreveram para o Power BI antes de você alterar a configuração manterão suas licenças.

- Se você alterar a configuração para false, os usuários que já tiverem uma licença do Power BI (gratuito) ainda poderão se inscrever para uma avaliação individual do Power BI Pro.

- Um administrador precisa atribuir todas as licenças do Power BI a novos usuários que precisam de uma.

### <a name="before-you-begin"></a>Antes de começar

Essas etapas usam comandos do PowerShell do Azure Active Directory para alterar o valor da configuração **AllowAdHocSubscriptions**. Você precisa ter o módulo do PowerShell do Azure AD instalado para que esses comandos estejam disponíveis. Para obter mais informações sobre o uso do PowerShell, confira [Introdução ao Windows PowerShell](https://docs.microsoft.com/powershell/scripting/getting-started/getting-started-with-windows-powershell?view=powershell-7).

Para instalar o módulo do Azure AD, inicie o Windows PowerShell como administrador. Verifique se sua política de execução local permite que você execute scripts. Se você tiver problemas, confira as [políticas de execução do PowerShell](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_execution_policies?view=powershell-7#powershell-execution-policies) para saber como alterar sua política local.

Execute o seguinte comando para instalar o módulo do Azure AD:

```powershell
Install-Module MSOnline
```

### <a name="change-the-self-service-signup-policy"></a>Alterar a política de inscrição por autoatendimento

No PowerShell, execute o seguinte comando para se conectar ao Azure AD:

```powershell
Connect-MsolService
```

Insira suas credenciais de administrador na caixa de diálogo de entrada, concluindo qualquer autenticação de dois fatores que possa ser necessária. Após a verificação, você será retornado para a janela do PowerShell.

Para exibir a configuração atual, execute o comando a seguir. Usando a opção "fl", a saída é canalizada para uma lista formatada.

```powershell
Get-MsolCompanyInformation | fl AllowAdHocSubscriptions
```

Para alterar a configuração atual, execute este comando:

```powershell
Set-MsolCompanySettings -AllowAdHocSubscriptions $false
```

Depois de executar esse comando, a inscrição por autoatendimento fica desabilitada para todos os usuários. Para ativá-la novamente, execute esse comando novamente e defina o valor como $true.

## <a name="enable-or-disable-self-service-purchase"></a>Habilitar ou desabilitar a compra por autoatendimento

Se a compra por autoatendimento estiver habilitada, o valor de **AllowSelfServicePurchase** será *true*. Vamos dar uma olhada no que acontece quando você altera essa configuração para *false*:

- Se você alterar a configuração de true para false, os usuários na sua organização serão impedidos de comprarem suas próprias licenças do Power BI Pro. Usuários tiverem comprado uma licença antes de você alterar a configuração manterão suas licenças.

- Se você alterar a configuração para false, os usuários que tiverem uma licença do Power BI (Gratuito) não poderão obter uma licença individual do Power BI Pro. 

- Um administrador precisa atribuir uma licença Pro a todos os usuários que precisam de uma.

### <a name="before-you-begin"></a>Antes de começar

Essas etapas usam comandos do MSCommerce PowerShell para alterar o valor da configuração **AllowSelfServicePurchase**. Você precisa ter o módulo do MSCommerce PowerShell instalado para que esses comandos estejam disponíveis. Para obter mais informações sobre o uso do PowerShell, confira [Introdução ao Windows PowerShell](https://docs.microsoft.com/powershell/scripting/getting-started/getting-started-with-windows-powershell?view=powershell-7).

Para instalar o módulo do MSCommerce, inicie o Windows PowerShell como administrador. Verifique se sua política de execução local permite que você execute scripts. Se você tiver problemas, confira as [políticas de execução do PowerShell](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_execution_policies?view=powershell-7#powershell-execution-policies) para saber como alterar sua política local.

Execute o seguinte comando para instalar o módulo do MSCommerce:

```powershell
Install-Module -name MSCommerce
```

### <a name="change-the-self-service-signup-policy"></a>Alterar a política de inscrição por autoatendimento

No PowerShell, execute o seguinte comando para se conectar:

```powershell
Connect-MSCommerce
```

Insira suas credenciais de administrador na caixa de diálogo de entrada, concluindo qualquer autenticação de dois fatores que possa ser necessária. Após a verificação, a janela do PowerShell mostra uma conexão bem-sucedida.

Para exibir a configuração atual, execute o comando a seguir. Para evitar que o texto seja truncado, a opção "fl" é usada, canalizando a saída para uma lista formatada.

```powershell
Get-MSCommercePolicy -PolicyId AllowSelfServicePurchase | fl
```

Você pode desabilitar a configuração que permite a compra por autoatendimento para um produto individual fornecendo a respectiva **ProductId**. Para alterar a configuração atual do serviço do Power BI, execute este comando:

```powershell
Update-MSCommerceProductPolicy -PolicyId AllowSelfServicePurchase -ProductId CFQ7TTC0L3PB -Enabled $False
```

Depois de executar esse comando, a compra por autoatendimento do Power BI fica desabilitada para todos os usuários. Para ativá-la novamente, execute esse comando novamente e defina o valor como $true.

## <a name="next-steps"></a>Próximas etapas

Para obter mais informações sobre a compra por autoatendimento do Power BI e o restante do Power Platform, veja estes artigos:

- [Perguntas frequentes sobre compra por autoatendimento](https://docs.microsoft.com/microsoft-365/commerce/subscriptions/self-service-purchase-faq?view=o365-worldwide#admin-capabilities)
- [Usar o AllowSelfServicePurchase para o módulo MSCommerce PowerShell](https://docs.microsoft.com/microsoft-365/commerce/subscriptions/allowselfservicepurchase-powershell?view=o365-worldwide)
