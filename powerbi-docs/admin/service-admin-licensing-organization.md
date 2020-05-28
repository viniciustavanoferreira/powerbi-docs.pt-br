---
title: Licenciamento do Power BI na sua organização
description: Visão geral dos diferentes tipos de licença disponíveis no Power BI e de como os administradores compram e gerenciam o licenciamento para suas próprias organizações.
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 05/14/2020
ms.author: kfollis
LocalizationGroup: Administration
ms.openlocfilehash: a0ce3eab2992c59c5b887db1f0838f88db7ad2da
ms.sourcegitcommit: a72567f26c1653c25f7730fab6210cd011343707
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83563478"
---
# <a name="power-bi-licensing-in-your-organization"></a>Licenciamento do Power BI na sua organização

O que um usuário pode fazer no serviço do Power BI depende do tipo de licença por usuário que eles têm. O nível de acesso fornecido pela sua licença depende se o workspace que está sendo acessado está atribuído à capacidade do Power BI Premium. Todos os usuários do serviço do Power BI precisam ter uma licença.

Há duas maneiras para os usuários obterem uma licença. Ao usarem recursos de inscrição por autoatendimento e as respectivas contas corporativas ou de estudante, os usuários podem obter sua própria licença gratuita ou Pro. Ou então, os administradores podem obter uma assinatura do Power BI e atribuir licenças a usuários.

Este artigo se concentra na compra de serviços e no licenciamento por usuário de uma perspectiva do administrador. Para obter mais informações sobre como os usuários podem obter suas próprias licenças, confira [Inscrever-se no Power BI como indivíduo](../fundamentals/service-self-service-signup-for-power-bi.md).

## <a name="who-can-purchase-and-assign-licenses"></a>Quem pode comprar e atribuir licenças?

É preciso que uma função de administrador lhe seja atribuída para que você possa comprar ou atribuir licenças para sua organização. As funções de administrador são atribuídas usando o centro de administração do Azure Active Directory ou o centro de administração do Microsoft 365. A tabela a seguir mostra qual função é necessária para realizar tarefas relacionadas à compra e ao licenciamento. Para obter mais informações sobre como atribuir funções de administrador a um usuário no Azure Active Directory, confira [Exibir e atribuir funções de administrador no Azure Active Directory](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-manage-roles-portal). Para saber mais sobre as funções de administrador no Microsoft 365, incluindo as práticas recomendadas, confira [Sobre funções de administrador](https://docs.microsoft.com/microsoft-365/admin/add-users/about-admin-roles?view=o365-worldwide).

| Quem pode comprar serviços e licenças? | Quem pode gerenciar licenças de usuário? |
| --------------- | --------------- |
| Administrador de cobrança | Administrador de licenças |
| Administrador global | Administrador de usuários |
|  | Administrador global |

Essas funções gerenciam a organização. Para obter informações sobre a função de administrador de serviços do Power BI, confira [Noções básicas sobre as funções de administrador de serviços do Power BI](service-admin-role.md).

## <a name="get-power-bi-for-your-organization"></a>Obter o Power BI para sua organização

Um administrador global ou um administrador de cobrança pode se inscrever para o serviço do Power BI e comprar as licenças para os usuários em sua própria organização. Se você não estiver pronto para comprar, selecione a avaliação do Power BI Pro. Você receberá 25 licenças para usar por um mês. Para obter instruções passo a passo sobre como se inscrever, confira [Obter uma assinatura do Power BI para sua organização](service-admin-org-subscription.md).

## <a name="about-self-service-sign-up"></a>Sobre a inscrição por autoatendimento

Os usuários individuais podem obter suas próprias licenças do Power BI inscrevendo-se com as respectivas contas corporativas ou de estudante. Com uma licença gratuita, os usuários podem explorar o Power BI para visualização e análise de dados pessoais usando o Meu Workspace, mas não podem compartilhar com outros usuários. Para compartilhar conteúdo, uma licença do Power BI Pro é necessária. Os usuários podem atualizar o tipo das próprias licenças para Pro ou inscrever-se para a Pro diretamente, caso a organização esteja usando a nuvem comercial. A compra direta ou a atualização para o Pro não está disponível para organizações educacionais ou organizações implantadas em nuvens do Azure Government, Azure Alemanha ou Azure China 21Vianet.

Se você não quiser que os usuários em sua organização usem a inscrição por autoatendimento, confira [Habilitar ou desabilitar a inscrição por autoatendimento](service-admin-disable-self-service.md) para saber como desativá-la.

Se você quiser saber como ver quais usuários em sua organização podem já ter uma licença, confira [Exibir e gerenciar licenças de usuário](service-admin-manage-licenses.md).

## <a name="license-types-and-capabilities"></a>Tipos e funcionalidades de licenças

Há dois tipos de licenças de Power BI por usuário: gratuita e Pro. O tipo de licença que um usuário precisa é determinado pelo local em que o conteúdo é armazenado e pelo modo como ele interage com esse conteúdo. O local em que o conteúdo pode ser armazenado é determinado pelo [tipo de assinatura](#subscription-types) da sua organização.

Um tipo de assinatura, o [Power BI Premium](service-admin-premium-purchase.md), permite que os usuários com uma licença gratuita atuem no conteúdo em workspaces atribuídos à capacidade Premium. Fora da capacidade Premium, um usuário com uma licença gratuita só pode usar o serviço do Power BI para se conectar a dados e criar relatórios e dashboards no **Meu Workspace**. Eles não podem compartilhar conteúdo com outras pessoas nem publicar conteúdo em outros workspaces. Para saber mais sobre os tipos de workspace, confira [Tipos de workspaces](../consumer/end-user-workspaces.md#types-of-workspaces).

Uma assinatura Standard do Power BI usa a capacidade compartilhada. Se o conteúdo é armazenado na capacidade compartilhada, os usuários que recebem uma licença de Power BI Pro podem colaborar apenas com outros usuários do Power BI Pro. Eles podem consumir conteúdo compartilhado por outros usuários, publicar conteúdo em workspaces de aplicativo, compartilhar dashboards e assinar dashboards e relatórios.  Quando os workspaces estão na capacidade Premium, os usuários do Pro podem distribuir conteúdo a usuários que não têm uma licença do Power BI Pro.

A tabela a seguir resume as funcionalidades básicas de cada tipo de licença. Para obter um detalhamento da disponibilidade de recursos por tipo de licença, confira [Recursos por tipo de licença](../fundamentals/service-features-license-type.md).

| Tipo de licença | Funcionalidades quando o workspace está na capacidade compartilhada | Funcionalidades adicionais quando o workspace está na capacidade Premium |
| --------- | ----------- | ----------- |
| Power BI (Gratuito) | Acesso ao conteúdo no Meu Workspace | Consumir conteúdo compartilhado com eles |
| Power BI Pro | Publicar conteúdo em outros workspaces, compartilhar dashboards, assinar dashboards e relatórios, compartilhar com usuários que têm uma licença Pro | Distribuir conteúdo a usuários que têm licenças gratuitas |

## <a name="subscription-types"></a>Tipos de assinatura

Todas as assinaturas de licença comercial baseadas em usuário da Microsoft são baseadas em identidades do Azure Active Directory. Para usar o serviço Power BI, você precisa entrar com uma identidade compatível com o Azure Active Directory no escopo de licenças comerciais. Você pode adicionar o Power BI a qualquer assinatura da Microsoft que use o Azure Active Directory para serviços de identidade. Algumas assinaturas, como o Office 365 E5, incluem uma licença do Power BI Pro, portanto, não é necessária uma inscrição separada para o Power BI.

Há dois tipos de assinaturas do Power BI para organizações: Standard e Premium.

Com uma assinatura padrão por autoatendimento do Power BI Pro, os administradores atribuem licenças por usuário. Há um valor mensal por usuário para licenças do Power BI Pro. Esse tipo de licença permite a colaboração, publicação, compartilhamento e análise ad hoc. O conteúdo é salvo na capacidade de armazenamento compartilhado, que é totalmente gerenciada pela Microsoft.

Uma assinatura do Power BI Premium aloca capacidade dedicada a uma organização. Adequado para Enterprise BI, Big Data Analytics e relatórios locais e na nuvem, o Premium fornece controles avançados de administração e implantação. Os recursos de computação e armazenamento dedicados são gerenciados pelos administradores de capacidade em sua organização. Há um custo mensal para esse ambiente dedicado. Além de outras vantagens do Premium, o conteúdo armazenado nessa capacidade pode tanto ser acessado por usuários que não têm licenças de Power BI Pro quanto distribuído para eles. Pelo menos um usuário precisa ter uma licença de Power BI Pro atribuída a si para usar o Premium, e os criadores de conteúdo e desenvolvedores ainda precisam de uma licença do Power BI Pro.

Os dois tipos de assinaturas não são mutuamente exclusivos. Você pode ter tanto o Power BI Premium quanto o Power BI Pro. Nessa configuração, o conteúdo armazenado na capacidade Premium pode ser compartilhado com todos os usuários e a capacidade compartilhada também está disponível. Para obter informações sobre os limites de capacidade, confira [Gerenciar o armazenamento de dados em workspaces do Power BI](service-admin-manage-your-data-storage-in-power-bi.md).

Para comparar os recursos e os preços de produto, confira [Preços do Power BI](https://powerbi.microsoft.com/pricing).

## <a name="guest-user-access"></a>Acesso dos usuários convidados

Talvez você queira distribuir conteúdo a usuários que estão fora da sua organização. É possível compartilhar conteúdo com usuários externos, convidando-os para verem o conteúdo como convidados. O Azure AD B2B (Azure Active Directory Business-to-business) permite o compartilhamento de conteúdo com usuários convidados externos. Os seguintes pré-requisitos precisam ser atendidos para possibilitar o compartilhamento com usuários externos:

- A capacidade de compartilhar conteúdo com usuários externos precisa estar habilitada

- O usuário convidado precisa ter a licença correta em vigor para ver o conteúdo compartilhado

Para obter mais informações sobre acesso de usuários convidados, confira [Distribuição do conteúdo do Power BI para usuários convidados externos com o Azure AD B2B](service-admin-azure-ad-b2b.md).

## <a name="purchase-power-bi-pro-licenses"></a>Comprar licenças do Power BI Pro

Como administrador, você adquire licenças do Power BI Pro por meio do Microsoft 365 ou de um parceiro da Microsoft. Depois de comprar as licenças, você pode atribuí-las a cada usuário. Para obter mais informações, consulte [Comprar e atribuir licenças do Power BI Pro](service-admin-purchasing-power-bi-pro.md).

### <a name="power-bi-pro-license-expiration"></a>Expiração de licença do Power BI Pro

Há um período de carência após a expiração de uma licença do Power BI Pro. Para licenças que fazem parte de uma compra de licença de volume, o período de carência é de 90 dias. Se você adquiriu a licença diretamente, o período de carência é de 30 dias.

O Power BI Pro tem o mesmo ciclo de vida de assinatura que o Microsoft 365. Para saber mais, confira [O que acontece com meus dados e o acesso quando termina minha assinatura do Microsoft 365 para empresas?](/microsoft-365/commerce/subscriptions/what-if-my-subscription-expires).


## <a name="next-steps"></a>Próximas etapas

- [Comprar e atribuir licenças do Power BI Pro](service-admin-purchasing-power-bi-pro.md)
- [Documentação de assinaturas e de cobrança empresariais](/microsoft-365/commerce/?view=o365-worldwide)
- [Encontrar usuários do Power BI que entraram](service-admin-access-usage.md)
- Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
