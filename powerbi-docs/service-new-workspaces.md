---
title: Organizar o trabalho em novos workspaces no Power BI
description: Saiba mais sobre novos workspaces, coleções de painéis e relatórios criados para oferecer métricas-chave para sua organização.
author: maggiesMSFT
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 03/16/2020
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 40bbec8a6a28def6cde9128b51c8919fd4f493de
ms.sourcegitcommit: 9ec2c608b90bf651df613f0714addd251a885039
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/24/2020
ms.locfileid: "82120332"
---
# <a name="organize-work-in-the-new-workspaces-in-power-bi"></a>Organizar o trabalho em novos workspaces no Power BI

 *Workspaces* são locais para colaborar com colegas e criar coleções de painéis e relatórios (paginados ou não). A nova experiência com o workspace ajuda você a gerenciar melhor o acesso ao conteúdo. Este artigo descreve os novos espaços de trabalho e como eles diferem dos clássicos.  Como ocorre com espaços de trabalho clássicos, você ainda os usa para criar e distribuir aplicativos. Leia sobre como [criar uma nova experiência de workspace](service-create-the-new-workspaces.md).

A nova experiência de workspace atingiu a disponibilidade geral (GA) e agora é o workspace padrão. Você ainda poderá continuar a criar e usar [espaços de trabalho clássicos](service-create-workspaces.md) com base em Grupos do Office 365. 

> [!NOTE]
> Para impor a Segurança em Nível de Linha (RLS) para usuários que procuram conteúdo em um workspace, use a função Visualizador. Para impor a RLS sem fornecer acesso ao workspace, publique um aplicativo do Power BI para esses usuários ou use o compartilhamento para distribuir conteúdo.

Com os novos workspaces, é possível:

- Atribuir funções de workspace a grupos de usuários: grupos de segurança, listas de distribuição, grupos do Office 365 e indivíduos.
- Criar um workspace no Power BI sem criar um grupo do Office 365.
- Usar funções de workspace mais granulares para obter um gerenciamento de permissões mais flexível em um workspace.
- O administrador do Power BI pode controlar quem pode criar workspaces no Power BI.

Quando você cria um dos novos workspaces, você não está criando um grupo do Office 365 associado e subjacente. Toda a administração do workspace está no Power BI, não no Office 365. Com a nova experiência de workspace, agora você pode adicionar um grupo do Office 365 à lista de acesso do workspace para continuar gerenciando o acesso do usuário ao conteúdo por meio de grupos do Office 365.

## <a name="administering-new-workspace-experience-workspaces"></a>Administrar as novas experiências de workspaces
A administração das novas experiências de workspaces está disponível agora no Power BI, ou seja, os administradores do Power BI decidem quem pode criar workspaces em uma organização. Eles também podem gerenciar e recuperar workspaces usando o portal de administração do Power BI ou cmdlets do PowerShell. Para espaços de trabalho clássicos com base em grupos do Office 365, a administração continuará a ser feita no portal de administração do Office 365 e no Azure Active Directory.

Em **Configurações de workspaces**, no portal de administração, os administradores podem usar a configuração Criar workspaces (nova experiência de workspaces) para permitir que todas as pessoas ou ninguém em uma organização crie uma nova experiência de workspaces. Eles também podem limitar a criação de membros de grupos de segurança específicos.

> [!NOTE]
> Por padrão, a configuração Criar workspaces (nova experiência de workspaces) permite que somente usuários autorizados a criar grupos do Office 365 possam criar novos workspaces no Power BI. Certifique-se de definir um valor no portal de administração do Power BI para garantir que os usuários adequados possam criar novas experiências de workspaces.

![Configurações de workspace no portal de administração](media/service-new-workspaces/power-bi-workspace-admin-settings.png)

A [lista de workspaces está disponível](service-admin-portal.md#workspaces) no portal de administração do Power BI. 

![Lista de workspaces](media/service-admin-portal/workspaces-list.png)

## <a name="new-workspaces-side-by-side-with-classic-workspaces"></a>Novos espaços de trabalho lado a lado com espaços de trabalho clássicos

Os espaços de trabalho novos, atualizados e espaços de trabalho clássicos coexistem lado a lado e você pode criar ambos. A nova experiência de workspace é o tipo de workspace padrão. O Power BI continua a listar todos os grupos do Office 365 do qual o usuário é membro no Power BI para evitar a alteração de fluxos de trabalho existentes. Para saber como criar um novo workspace, confira [Criar novos workspaces](service-create-the-new-workspaces.md). Para saber como criar um espaço de trabalho clássico, confira [Criar espaços de trabalho clássicos](service-create-workspaces.md).

## <a name="roles-in-the-new-workspaces"></a>Funções nos novos workspaces

Para permitir acesso a um novo workspace, adicione grupos de usuários ou indivíduos a uma das funções do workspace: administradores, membros, colaboradores ou visualizadores. Todos em um grupo de usuários obtêm a função que você definiu. Se um indivíduo estiver em vários grupos de usuários, ele terá o nível mais alto de permissão fornecido pela função que lhe foi atribuída.

As funções permitem que você gerencie quem pode fazer o que em um workspace para que as equipes possam colaborar. Os novos workspaces permitem que você atribua funções a indivíduos e a grupos de usuários: grupos de segurança, grupos do Office 365 e listas de distribuição. 

Ao atribuir funções a um grupo de usuários, os indivíduos no grupo têm acesso ao conteúdo. Se você aninhar grupos de usuários, todos os usuários contidos terão permissão.

[!INCLUDE [power-bi-workspace-roles-table](includes/power-bi-workspace-roles-table.md)]

## <a name="licensing"></a>Licenças
Todas as pessoas que você adiciona a um workspace na capacidade compartilhada precisam de uma licença do Power BI Pro. No workspace, esses usuários podem colaborar nos dashboards e relatórios que você planeja publicar para um público-alvo maior ou até mesmo para toda a organização. 

Para distribuir conteúdo a outras pessoas da sua organização, atribua licenças do Power BI Pro a esses usuários ou coloque o workspace em uma capacidade do Power BI Premium.

Quando o workspace está em uma capacidade do Power BI Premium, os usuários com a função de visualizador podem acessar o workspace, mesmo se não tiverem uma licença do Power BI Pro. No entanto, se você atribuir a esses usuários uma função superior, como Administrador, Membro ou Colaborador, será solicitado que eles iniciem uma Avaliação do Pro quando tentarem acessar o workspace. Para aproveitar a capacidade de Visualizador para usuários sem licenças do Pro, verifique se os usuários com a função Visualizador não estão em outras funções do workspace, individualmente ou por meio de um grupo de usuários. 

> [!NOTE]
> A publicação de relatórios em uma nova experiência de workspace tem a imposição mais rigorosa das regras de licenciamento existentes. Usuários que tentarem publicar do Power BI Desktop ou de outras ferramentas de cliente sem uma licença do Pro verão o erro "Somente usuários com licenças do Power BI Pro podem publicar neste workspace."

## <a name="how-the-new-workspaces-are-different"></a>O que é diferente nos novos workspaces

Com os novos workspaces, reformulamos alguns recursos. Aqui estão as alterações que você pode esperar como permanentes. 

* Criar esses workspaces não cria grupos do Office 365, como ocorre com os workspaces clássicos. No entanto, agora você pode usar um grupo do Office 365 para dar aos usuários acesso ao workspace, atribuindo a ele uma função. 
* Nos espaços de trabalho clássicos, é possível adicionar apenas indivíduos às listas de membros e administradores. Nos novos workspaces, é possível adicionar vários grupos de segurança do AD, listas de distribuição ou grupos do Office 365 a essas listas para facilitar o gerenciamento de usuários. 
- É possível criar um pacote de conteúdo organizacional de um espaço de trabalho clássico. Não é possível criar um dos novos workspaces.
- É possível consumir um pacote de conteúdo organizacional de um espaço de trabalho clássico. Não é possível consumir um dos novos workspaces.

## <a name="workspace-contact-list"></a>Lista de contatos do workspace
O novo recurso **Lista de contatos** permite que você especifique quais usuários recebem a notificação sobre problemas que ocorrem no workspace. Por padrão, qualquer usuário ou grupo especificado como um administrador do workspace é notificado, mas você pode personalizar a lista. Os usuários ou grupos listados na lista de contatos serão mostrados na interface do usuário (IU) para ajudar os usuários a obter ajuda relacionada ao workspace. 

Saiba mais sobre a [configuração da lista de contatos do workspace](service-create-the-new-workspaces.md#workspace-contact-list).

## <a name="workspace-onedrive"></a>OneDrive do Workspace
O recurso OneDrive do Workspace permite que você configure um grupo do Office 365 cujo armazenamento de arquivos da Biblioteca de Documentos do SharePoint esteja disponível para usuários do espaço de trabalho. O grupo precisa ser criado fora do Power BI. 

O Power BI não sincroniza as permissões de usuários ou grupos que estão configurados para ter acesso ao workspace com a associação ao grupo do Office 365. A prática recomendada é gerenciar o acesso ao workspace por meio do mesmo grupo do Office 365 cujo armazenamento de arquivos você define nessa configuração. 

Confira como [definir e acessar o OneDrive do Workspace](service-create-the-new-workspaces.md#workspace-onedrive).  

## <a name="auditing"></a>Auditoria

As seguintes atividades são auditadas pelo Power BI para novas experiências de workspaces.

| Nome amigável | Nome da operação |
|---|---|
| Pasta do Power BI criada | CreateFolder |
| Pasta do Power BI excluída | DeleteFolder |
| Pasta do Power BI atualizada | UpdateFolder |
| Acesso à pasta do Power BI atualizado| UpdateFolderAccess |

Leia mais sobre [Auditoria do Power BI](service-admin-auditing.md).

## <a name="guest-users"></a>Usuários convidados

Por padrão, [os usuários Convidados do Azure AD B2B](service-admin-azure-ad-b2b.md) não podem acessar espaços de trabalho. Os administradores do Power BI podem [permitir que usuários convidados externos editem e gerenciem conteúdo da organização](service-admin-azure-ad-b2b.md#guest-users-who-can-edit-and-manage-content). Os usuários Convidados habilitados podem acessar espaços de trabalho para os quais tiverem permissão.

## <a name="limitations-and-considerations"></a>Limitações e considerações

Limitações a serem consideradas:

- Os workspaces podem conter um máximo de mil conjuntos de dados ou mil relatórios por conjunto de dados. 
- Uma pessoa com uma licença do Power BI Pro pode ser membro de um máximo de 1.000 workspaces.
- O Power BI Publisher para Excel não é compatível.

## <a name="workspace-features-that-work-differently"></a>Recursos do workspace de aplicativo que funcionam de forma diferente

Alguns recursos funcionam de forma diferente dos workspaces atuais nos novos workspaces. Essas diferenças são intencionais, com base nos comentários recebidos dos clientes, e permitem uma abordagem mais flexível para colaboração com workspaces:

- Imposição de licenciamento: A publicação de relatórios em uma nova experiência de workspace impõe regras de licenciamento existentes que exigem uma licença do Power BI Pro para usuários que colaboram em workspaces ou compartilham conteúdo com outros no serviço do Power BI. Os usuários sem licença Pro veem o erro "Somente usuários com licenças Power BI Pro podem publicar neste workspace".
- Os membros podem ou não compartilhar novamente: substituídos pela função Colaborador
- Workspaces somente leitura: Em vez de conceder aos usuários o acesso somente leitura a um workspace, atribua aos usuários uma função de Visualizador que permite acesso somente leitura semelhante ao conteúdo de um workspace.
- Os usuários sem uma licença do Pro poderão acessar o workspace se ele estiver em uma capacidade Power BI Premium, mesmo se os usuários tiverem somente a função de Visualizador.
- Para permitir que os usuários com a função de Visualizador exportem dados, verifique se eles têm a permissão Criar nos conjuntos de dados no workspace. Leia mais sobre a [Permissão Criar em conjuntos de dados](service-datasets-build-permissions.md).
- Nenhum botão **Sair do workspace**.

## <a name="frequently-asked-questions"></a>Perguntas frequentes

**São links para conteúdos existentes afetados pela nova experiência de disponibilidade geral (GA) de workspaces**

Não. Os links para itens existentes em espaços de trabalho clássicos não são afetados pela nova experiência de espaço de trabalho. A disponibilidade geral (GA) da nova experiência de workspace altera o workspace padrão que você cria, mas não altera workspaces existentes. 

**Os workspaces existentes foram atualizados para a nova experiência de workspace com GA?**

Não. A nova experiência de workspace com GA altera apenas o tipo de workspace padrão para a nova experiência de workspace. Os espaços de trabalho clássicos existentes com base em grupos do Office 365 permanecem inalterados.

**Os workspaces ainda são criados automaticamente para grupos do Office 365?**

Sim. Como damos suporte a ambos os tipos de workspaces lado a lado, continuamos a listar todos os grupos do Office 365 aos quais o usuário tem acesso na lista de workspaces.

## <a name="next-steps"></a>Próximas etapas
* [Criar novos workspaces no Power BI](service-create-the-new-workspaces.md)
* [Criar espaços de trabalho clássicos](service-create-workspaces.md)
* [Instalar e usar aplicativos no Power BI](service-create-distribute-apps.md)
* Dúvidas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
