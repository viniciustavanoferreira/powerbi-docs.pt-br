---
title: Organizar o trabalho em novos workspaces no Power BI
description: Saiba mais sobre novos workspaces, coleções de painéis e relatórios criados para oferecer métricas-chave para sua organização.
author: maggiesMSFT
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/07/2020
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 701f478ce4dd59d77c1722b1386cd79ad3fbf2a0
ms.sourcegitcommit: 250242fd6346b60b0eda7a314944363c0bacaca8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83693786"
---
# <a name="organize-work-in-the-new-workspaces-in-power-bi"></a>Organizar o trabalho em novos workspaces no Power BI

*Workspaces* são locais para colaborar com colegas e criar coleções de painéis, relatórios, conjuntos de dados e relatórios paginados. A nova experiência com o workspace ajuda você a gerenciar melhor o acesso ao conteúdo. Este artigo descreve os novos espaços de trabalho e como eles diferem dos clássicos.  Como ocorre com espaços de trabalho clássicos, você ainda os usa para criar e distribuir aplicativos. Pronto para criar um workspace? Leia [Criar uma experiência de workspace](service-create-the-new-workspaces.md).

Os workspaces novos e atualizados podem coexistir lado a lado com os clássicos. A nova experiência de workspace é o tipo de workspace padrão. Caso precise, você ainda pode criar e usar [workspaces clássicos](service-create-workspaces.md) com base em Grupos do Microsoft 365. Pronto para migrar seu workspace clássico? Confira [Atualizar workspaces clássicos para os novos workspaces no Power BI](service-upgrade-workspaces.md) para obter detalhes.

Com os novos workspaces, é possível:

- Atribuir funções de workspace a grupos de usuários: grupos de segurança, listas de distribuição, grupos do Microsoft 365 e indivíduos.
- Criar um workspace no Power BI sem criar um grupo do Microsoft 365 associado e subjacente. Toda a administração do workspace está no Power BI, não no Microsoft 365.
- Continuar a gerenciar o acesso de usuários ao conteúdo por meio dos Grupos do Microsoft 365, se desejar. Basta adicionar um grupo do Microsoft 365 à lista de acesso ao workspace.
- Usar funções de workspace mais granulares para obter um gerenciamento de permissões mais flexível em um workspace.

O Power BI continua a listar todos os Grupos do Microsoft 365 dos quais você é membro. Isso evita a alteração de fluxos de trabalho existentes.

## <a name="new-and-classic-workspace-differences"></a>Diferenças entre workspaces novos e clássicos

Com os novos workspaces, reformulamos alguns recursos. Aqui estão as principais diferenças:

- Criar esses workspaces não cria grupos do Microsoft 365, como ocorre com os workspaces clássicos. No entanto, agora você pode usar um grupo do Microsoft 365 para dar aos usuários acesso ao workspace, atribuindo a ele uma função.
- Nos espaços de trabalho clássicos, é possível adicionar apenas indivíduos às listas de membros e administradores. Nos workspaces novos, é possível adicionar a essas listas vários grupos de segurança do Active Directory, listas de distribuição ou grupos do Microsoft 365, para facilitar o gerenciamento de usuários.
- É possível criar um pacote de conteúdo organizacional de um espaço de trabalho clássico. Não é possível criar um dos novos workspaces.
- É possível consumir um pacote de conteúdo organizacional de um espaço de trabalho clássico. Não é possível consumir um dos novos workspaces.

### <a name="workspace-features-that-work-differently"></a>Recursos do workspace de aplicativo que funcionam de forma diferente

Alguns recursos funcionam de forma diferente dos workspaces atuais nos novos workspaces. Essas diferenças são intencionais, baseadas nos comentários que recebemos dos clientes. Elas permitem uma abordagem mais flexível para a colaboração com workspaces.

- **Imposição de licenciamento**: a publicação de relatórios em uma nova experiência de workspace impõe as regras de licenciamento existentes. Os usuários que colaboram em workspaces ou compartilham conteúdo com outras pessoas no serviço do Power BI precisam de uma licença Power BI Pro. Os usuários sem licença Pro veem o erro "Somente usuários com licenças Power BI Pro podem publicar neste workspace".
- **Os membros podem ou não compartilhar novamente**: a função de Colaborador substitui esta configuração.
- **Workspaces somente leitura**: em vez de conceder aos usuários acesso somente leitura a um workspace, atribua a eles a função de Visualizador. Ela permite acesso ao conteúdo de um workspace semelhante ao acesso somente leitura.
- **Usuários sem uma licença Pro** poderão acessar o workspace se este estiver em uma capacidade Power BI Premium, mas somente se eles tiverem a função de Visualizador.
- **Permitir que os usuários exportem dados**: os usuários com a função de Visualizador poderão exportar dados se tiverem a permissão Compilar nos conjuntos de dados do workspace. Leia mais sobre a [Permissão Criar em conjuntos de dados](../connect-data/service-datasets-build-permissions.md).
- Nenhum botão **Sair do workspace**.

### <a name="workspace-contact-list"></a>Lista de contatos do workspace

O novo recurso **Lista de contatos** permite que você especifique quais usuários recebem a notificação sobre problemas que ocorrem no workspace. Por padrão, qualquer usuário ou grupo especificado como um administrador do workspace é notificado, mas você pode personalizar a lista. Os usuários ou grupos listados na lista de contatos serão mostrados na interface do usuário (IU) para ajudar os usuários a obter ajuda relacionada ao workspace. 

Saiba mais sobre a [configuração da lista de contatos do workspace](service-create-the-new-workspaces.md#workspace-contact-list).

### <a name="workspace-onedrive"></a>OneDrive do Workspace

O recurso OneDrive do Workspace permite que você configure um grupo do Microsoft 365 cujo armazenamento de arquivos da Biblioteca de Documentos do SharePoint esteja disponível para usuários do workspace. É possível criar o grupo fora do Power BI.

O Power BI não sincroniza as permissões de usuários ou grupos que estão configurados para ter acesso ao workspace com a associação ao grupo do Microsoft 365. A prática recomendada é gerenciar o acesso ao workspace por meio do mesmo grupo do Microsoft 365 cujo armazenamento de arquivos você define nessa configuração.

Confira como [definir e acessar o OneDrive do Workspace](service-create-the-new-workspaces.md#workspace-onedrive).  

## <a name="roles-in-the-new-workspaces"></a>Funções nos novos workspaces

Para permitir acesso a um novo workspace, adicione grupos de usuários ou indivíduos a uma das funções do workspace: administradores, membros, colaboradores ou visualizadores. Todos em um grupo de usuários obtêm a função que você definiu. Se um indivíduo estiver em vários grupos de usuários, ele receberá o nível mais alto de permissão fornecido pelas funções que foram atribuídas a ele.

As funções permitem que você gerencie quem pode fazer o que em um workspace para que as equipes possam colaborar. Os novos workspaces permitem que você atribua funções a indivíduos e a grupos de usuários: grupos de segurança, grupos do Microsoft 365 e listas de distribuição.

Ao atribuir funções a um grupo de usuários, os indivíduos no grupo têm acesso ao conteúdo. Se você aninhar grupos de usuários, todos os usuários contidos terão permissão.

[!INCLUDE [power-bi-workspace-roles-table](../includes/power-bi-workspace-roles-table.md)]

> [!NOTE]
> Para impor a Segurança em Nível de Linha (RLS) para usuários que procuram conteúdo em um workspace, use a função Visualizador. Para impor a RLS sem fornecer acesso ao workspace, publique um aplicativo do Power BI para esses usuários ou use o compartilhamento para distribuir conteúdo.

## <a name="licensing"></a>Licenças
Todas as pessoas que você adiciona a um workspace na capacidade compartilhada precisam de uma licença do Power BI Pro. No workspace, esses usuários podem colaborar nos dashboards e relatórios que você planeja publicar para um público-alvo maior ou até mesmo para toda a organização. 

Para distribuir conteúdo a outras pessoas da sua organização, atribua licenças do Power BI Pro a esses usuários ou coloque o workspace em uma capacidade do Power BI Premium.

Quando o workspace está em uma capacidade do Power BI Premium, os usuários com a função de visualizador podem acessar o workspace, mesmo se não tiverem uma licença do Power BI Pro. No entanto, se você atribuir a esses usuários uma função mais elevada, como Administrador, Membro ou Colaborador, será solicitado que eles iniciem uma Avaliação do Pro quando tentarem acessar o workspace. Para usar a função de Visualizador para usuários sem licenças Pro, verifique se eles não têm outras funções de workspace também, seja individualmente ou por meio de um grupo de usuários.

> [!NOTE]
> A publicação de relatórios em uma nova experiência de workspace tem a imposição mais rigorosa das regras de licenciamento existentes. Se o usuário tentar publicar a partir do Power BI Desktop ou de outras ferramentas de cliente sem uma licença Pro, verá o erro: "Somente usuários com licenças do Power BI Pro podem publicar neste workspace."

## <a name="administering-new-workspace-experience-workspaces"></a>Administrar as novas experiências de workspaces

A administração de novas experiências de workspace agora está no portal de administração do Power BI. Os administradores do Power BI decidem quem em uma organização pode criar workspaces e distribuir aplicativos. Os administradores podem ver o estado de todos os workspaces em sua organização. Eles também podem gerenciar e recuperar workspaces. Leia mais sobre como [Criar workspaces](../admin/service-admin-portal.md#create-the-new-workspaces) no artigo do Portal de administração.

## <a name="guest-users"></a>Usuários convidados

Por padrão, [os usuários Convidados do Azure AD B2B](../admin/service-admin-azure-ad-b2b.md) não podem acessar espaços de trabalho. Os administradores do Power BI podem [permitir que usuários convidados externos editem e gerenciem conteúdo da organização](../admin/service-admin-azure-ad-b2b.md#guest-users-who-can-edit-and-manage-content). Os usuários Convidados habilitados podem acessar os workspaces para os quais têm permissão.

## <a name="auditing"></a>Auditoria

As seguintes atividades são auditadas pelo Power BI para novas experiências de workspaces.

| Nome amigável | Nome da operação |
|---|---|
| Pasta do Power BI criada | CreateFolder |
| Pasta do Power BI excluída | DeleteFolder |
| Pasta do Power BI atualizada | UpdateFolder |
| Acesso à pasta do Power BI atualizado| UpdateFolderAccess |

Leia mais sobre [Auditoria do Power BI](../admin/service-admin-auditing.md).

## <a name="limitations-and-considerations"></a>Limitações e considerações

Limitações a serem consideradas:

- Os workspaces podem conter um máximo de mil conjuntos de dados ou mil relatórios por conjunto de dados. 
- Uma pessoa com uma licença do Power BI Pro pode ser membro de um máximo de 1.000 workspaces.
- O Power BI Publisher para Excel não é compatível.

## <a name="frequently-asked-questions"></a>Perguntas frequentes

**Os links para conteúdos existentes são afetados pela nova experiência de workspace**

Não. Os links para itens existentes em espaços de trabalho clássicos não são afetados pela nova experiência de espaço de trabalho. A disponibilidade geral (GA) da nova experiência de workspace altera o workspace padrão que você cria, mas não altera workspaces existentes. 

**Os workspaces existentes foram atualizados para a nova experiência de workspace com GA?**

Não. A nova experiência de workspace com GA altera apenas o tipo de workspace padrão para a nova experiência de workspace. Os workspaces clássicos existentes com base em grupos do Microsoft 365 permanecem inalterados.

**Os workspaces ainda são criados automaticamente para grupos do Microsoft 365?**

Sim. Como damos suporte a ambos os tipos de workspaces lado a lado, continuamos a listar todos os Grupos do Microsoft 365 aos quais você tem acesso na lista de workspaces.

## <a name="next-steps"></a>Próximas etapas

* [Criar novos workspaces no Power BI](service-create-the-new-workspaces.md)
* [Criar espaços de trabalho clássicos](service-create-workspaces.md)
* [Instalar e usar aplicativos no Power BI](service-create-distribute-apps.md)
* Dúvidas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)

