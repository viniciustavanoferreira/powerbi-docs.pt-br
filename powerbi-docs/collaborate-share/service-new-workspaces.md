---
title: Organizar o trabalho em novos workspaces no Power BI
description: Saiba mais sobre novos workspaces, coleções de painéis e relatórios criados para oferecer métricas-chave para sua organização.
author: maggiesMSFT
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/26/2020
ms.author: maggies
ms.custom: contperfq4
LocalizationGroup: Share your work
ms.openlocfilehash: 77de9608978379cee83236b0c362bd2d7d57d5c6
ms.sourcegitcommit: a7b142685738a2f26ae0a5fa08f894f9ff03557b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/28/2020
ms.locfileid: "84120353"
---
# <a name="organize-work-in-the-new-workspaces-in-power-bi"></a>Organizar o trabalho em novos workspaces no Power BI

*Workspaces* são locais para colaborar com colegas e criar coleções de painéis, relatórios, conjuntos de dados e relatórios paginados. A nova experiência com o workspace ajuda você a gerenciar melhor o acesso ao conteúdo. Este artigo descreve os novos espaços de trabalho e como eles diferem dos clássicos.  Como ocorre com espaços de trabalho clássicos, você ainda os usa para criar e distribuir aplicativos. Pronto para criar um workspace? Leia [Criar uma experiência de workspace](service-create-the-new-workspaces.md).

:::image type="content" source="media/service-new-workspaces/power-bi-workspace-opportunity.png" alt-text="Nova experiência de workspace do Power BI":::

Os workspaces novos e atualizados podem coexistir lado a lado com os clássicos. A nova experiência de workspace é o tipo de workspace padrão. Caso precise, você ainda pode criar e usar [workspaces clássicos](service-create-workspaces.md) com base em grupos do Microsoft 365. Pronto para migrar seu workspace clássico? Confira [Atualizar workspaces clássicos para os novos workspaces no Power BI](service-upgrade-workspaces.md) para obter detalhes.

## <a name="new-and-classic-workspace-differences"></a>Diferenças entre workspaces novos e clássicos

Com os novos workspaces, reformulamos alguns recursos. Aqui estão as principais diferenças:

- **A criação dos workspaces não cria grupos do Microsoft 365,** como ocorre com workspaces clássicos. Toda a nova administração do workspace está no Power BI, não no Office 365. Se quiser, você ainda poderá gerenciar o acesso do usuário ao conteúdo por meio de grupos do Microsoft 365. Basta adicionar um grupo do Microsoft 365 à lista de acesso ao workspace.
- **Use funções do workspace mais granulares** para obter um gerenciamento de permissões mais flexível nos novos workspaces.  Nos espaços de trabalho clássicos, é possível adicionar apenas indivíduos às listas de membros e administradores. 
- **Atribuir grupos de usuários a funções do workspace**: nos novos workspaces, é possível adicionar vários grupos de segurança do Active Directory, listas de distribuição ou grupos do Microsoft 365 a essas funções para facilitar o gerenciamento de usuários. 
- **Lista de contatos**: nos novos workspaces, você pode especificar quem recebe a notificação sobre a atividade do workspace.
- **Criar aplicativos de modelo**: você só pode criar *aplicativos de modelo* nos novos workspaces. Aplicativos de modelo são aplicativos que você pode distribuir aos clientes fora da sua organização. Esses clientes podem se conectar aos próprios dados com seu aplicativo de modelo. Saiba mais sobre [aplicativos de modelo](../connect-data/service-template-apps-overview.md).
- **Compartilhar conjuntos de dados**: para compartilhar um conjunto de dados fora de um workspace específico, você precisará salvar o relatório que contém o conjunto de dados em um dos novos workspaces. Não é possível compartilhar conjuntos de dados de workspaces clássicos. Saiba mais sobre [conjuntos de dados compartilhados](../connect-data/service-datasets-across-workspaces.md).
- **Pacotes de conteúdo organizacionais**: você cria e consome pacotes de conteúdo organizacional em workspaces clássicos. Não é possível criá-los ou consumi-los nos novos workspaces. Aplicativos e aplicativos de modelo substituem pacotes de conteúdo organizacional em novos workspaces.

Este artigo explica esses recursos mais detalhadamente.

> [!NOTE]
> O Power BI continua a listar todos os grupos do Microsoft 365 dos quais você é membro. Isso evita a alteração de fluxos de trabalho existentes.

### <a name="features-that-work-differently"></a>Recursos que funcionam de forma diferente

Nos novos workspaces, alguns recursos funcionam de forma diferente. Essas diferenças são intencionais, baseadas nos comentários que recebemos dos clientes. Elas permitem uma abordagem mais flexível para a colaboração em workspaces.

- **Imposição de licenciamento**: a publicação de relatórios em uma nova experiência do workspace impõe as regras de licenciamento existentes. Os usuários que colaboram em novos workspaces ou compartilham conteúdo com outras pessoas no serviço do Power BI precisam de uma licença do Power BI Pro. Os usuários sem licença Pro veem o erro "Somente usuários com licenças Power BI Pro podem publicar neste workspace".
- **Configuração "Membros podem compartilhar novamente"** : a função Colaborador nos novos workspaces substitui a configuração "Membros podem compartilhar novamente" nos workspaces clássicos.
- **Workspaces somente leitura**: a função Visualizador nos novos workspaces substitui a concessão de acesso somente leitura aos usuários de um workspace clássico. A função Visualizador permite acesso somente leitura ao conteúdo nos novos workspace.
- **Usuários sem uma licença Pro** poderão acessar um novo workspace se ele estiver em uma capacidade Power BI Premium, mas somente na função Visualizador.
- **Permitir que os usuários exportem dados**: mesmo usuários com a função Visualizador no novo workspace poderão exportar dados se tiverem a permissão Compilar nos conjuntos de dados do workspace. Leia mais sobre a [Permissão Criar em conjuntos de dados](../connect-data/service-datasets-build-permissions.md).
- Sem botão **Sair do workspace** nos novos workspaces.

### <a name="workspace-contact-list"></a>Lista de contatos do workspace

O novo recurso **Lista de contatos** permite que você especifique quais usuários recebem a notificação sobre problemas que ocorrem em novos workspaces. Por padrão, qualquer usuário ou grupo especificado como um administrador do workspace é notificado. Você pode adicioná-lo à lista. Os usuários ou grupos na lista de contatos também são listados na interface do usuário (IU) dos novos workspaces para que os usuários finais do workspace saibam quem contatar. 

Leia sobre [como criar a lista de contatos do workspace](service-create-the-new-workspaces.md#create-a-contact-list).

### <a name="workspace-onedrive"></a>OneDrive do Workspace

Como dissemos, o Power BI não cria um grupo do Microsoft 365 em segundo plano quando você cria um grupo dos novos workspaces. Ainda assim, pode ser útil ter um OneDrive associado ao novo workspace. Com o recurso OneDrive do Workspace nos novos workspaces, você pode configurar um grupo do Microsoft 365 cujo armazenamento de arquivos da Biblioteca de Documentos do SharePoint esteja disponível para usuários do workspace. É possível criar o grupo fora do Power BI.
 
O Power BI não faz a sincronização entre associações e permissões do grupo do Microsoft 365 para usuários ou grupos com acesso ao novo workspace. Você pode sincronizá-las: gerencie o acesso ao workspace por meio do mesmo grupo do Microsoft 365 cujo armazenamento de arquivos você define nessa configuração. 

Confira [como definir o OneDrive do workspace](service-create-the-new-workspaces.md#set-a-workspace-onedrive).  

## <a name="roles-in-the-new-workspaces"></a>Funções nos novos workspaces

As funções permitem gerenciar quem pode fazer o que nos novos workspaces, para que as equipes possam colaborar. Os novos workspaces permitem que você atribua funções a indivíduos e a grupos de usuários: grupos de segurança, grupos do Microsoft 365 e listas de distribuição. 

Para conceder acesso a um novo workspace, atribua esses grupos de usuários ou indivíduos a uma das funções do workspace: Administrador, Membro, Colaborador ou Visualizador. Todos em um grupo de usuários recebem a função que você atribuiu. Se alguém estiver em vários grupos de usuários, receberá o nível mais alto de permissão fornecido pelas funções que foram atribuídas. Se você aninhar grupos de usuários, todos os usuários contidos terão permissão. Todos esses recursos, exceto exibição e interação, exigem uma licença Power BI Pro. Leia mais sobre [licenciamento](#licenses) neste artigo.

[!INCLUDE [power-bi-workspace-roles-table](../includes/power-bi-workspace-roles-table.md)]

> [!NOTE]
> - Você pode atribuir usuários a funções, seja sozinho ou em um grupo, mesmo que eles não possam usar a função. Em outras palavras, você pode atribuir usuários que não têm licenças do Power BI Pro a uma função que requer uma licença. Confira [Licenças](#licenses) neste artigo para obter detalhes.
> - Para impor a [RLS (Segurança em Nível de Linha)](../admin/service-admin-rls.md) para usuários que procuram conteúdo em um workspace, use a função Visualizador. Você também pode impor a RLS sem conceder acesso ao novo workspace. [Publique um aplicativo](service-create-distribute-apps.md) e distribua para os usuários ou use o [compartilhamento para distribuir conteúdo](service-share-dashboards.md).

## <a name="licensing-and-administering"></a>Licenciamento e administração

### <a name="licenses"></a>Licenças
Se um dos novos workspaces estiver em uma capacidade compartilhada, todos que você adicionar a ele precisarão de uma licença do Power BI Pro. Esses usuários podem colaborar nos dashboards e relatórios no novo workspace. Para distribuir conteúdo a outras pessoas da sua organização, atribua licenças do Power BI Pro a esses usuários ou coloque o workspace em uma capacidade do Power BI Premium.

Quando o novo workspace está em uma capacidade do Power BI Premium, os usuários com a função de visualizador podem acessar o workspace, mesmo que não tenham uma licença do Power BI Pro. No entanto, se você atribuir a esses usuários uma função mais elevada, como Administrador, Membro ou Colaborador, será solicitado que eles iniciem uma avaliação do Pro quando tentarem acessar o workspace. Se você quiser que os usuários sem licenças Pro usem a função de Visualizador, verifique se eles também não têm outras funções do workspace, seja como indivíduos ou como parte de um grupo de usuários.

> [!NOTE]
> A publicação de relatórios em uma nova experiência de workspace tem a imposição mais rigorosa das regras de licenciamento existentes. Se o usuário tentar publicar a partir do Power BI Desktop ou de outras ferramentas de cliente sem uma licença Pro, verá o erro: "Somente usuários com licenças do Power BI Pro podem publicar neste workspace."

### <a name="guest-users"></a>Usuários convidados

Por padrão, [os usuários Convidados do Azure AD B2B](../admin/service-admin-azure-ad-b2b.md) não podem acessar espaços de trabalho. Os administradores do Power BI podem [permitir que usuários convidados externos editem e gerenciem conteúdo da organização](../admin/service-admin-azure-ad-b2b.md#guest-users-who-can-edit-and-manage-content). Os usuários Convidados habilitados podem acessar os workspaces para os quais têm permissão.

### <a name="administering-new-workspace-experience-workspaces"></a>Administrar as novas experiências de workspaces

A administração de novas experiências de workspace está no Portal de administração do Power BI. Os administradores do Power BI decidem quem em uma organização pode criar workspaces e distribuir aplicativos. Os administradores podem ver o estado de todos os workspaces em sua organização. Eles também podem gerenciar e recuperar workspaces. Leia mais sobre como [administrar os novos workspaces](../admin/service-admin-portal.md#create-the-new-workspaces) no artigo do Portal de administração.

### <a name="auditing"></a>Auditoria

O Power BI faz a auditoria das seguintes atividades para novas experiências de workspaces.

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

**Os links para conteúdos existentes são afetados pela nova experiência de workspace?**

Não. Os links para itens existentes em espaços de trabalho clássicos não são afetados pela nova experiência de espaço de trabalho. A disponibilidade geral (GA) da nova experiência de workspace altera o workspace padrão que você cria, mas não altera workspaces existentes. 

**Os workspaces existentes foram atualizados para a nova experiência de workspace com GA?**

Não. A nova experiência de workspace com GA altera apenas o tipo de workspace padrão para a nova experiência de workspace. Os workspaces clássicos existentes com base em grupos do Microsoft 365 permanecem inalterados.

**Os workspaces ainda são criados automaticamente para grupos do Microsoft 365?**

Sim. Como damos suporte a ambos os tipos de workspaces lado a lado, continuamos a listar todos os grupos do Microsoft 365 aos quais você tem acesso na lista de workspaces.

## <a name="next-steps"></a>Próximas etapas

* [Criar novos workspaces no Power BI](service-create-the-new-workspaces.md)
* [Criar espaços de trabalho clássicos](service-create-workspaces.md)
* [Instalar e usar aplicativos no Power BI](service-create-distribute-apps.md)
* Dúvidas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)

