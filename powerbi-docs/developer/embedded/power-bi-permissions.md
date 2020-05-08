---
title: Permissões do Power BI
description: Permissões do Power BI
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 10/01/2018
ms.openlocfilehash: 51c43a19613381d39e0397864e55baed2022663c
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/05/2020
ms.locfileid: "79491354"
---
# <a name="power-bi-permissions"></a>Permissões do Power BI

## <a name="permission-scopes"></a>Escopos de permissão

As permissões do Power BI fornecem a um aplicativo a capacidade de executar determinadas ações em nome de um usuário. Todas as permissões devem ser aprovadas por um usuário para serem válidas.

| Nome de Exibição | Descrição | Valor do escopo |
| --- | --- | --- |
| Exibir todos os conjuntos de dados |O aplicativo pode exibir todos os conjuntos de dados para o usuário conectado e conjuntos de dados aos quais o usuário tem acesso. |Dataset.Read.All |
| Ler e gravar todos os conjuntos de dados |O aplicativo pode exibir e gravar em todos os conjuntos de dados para o usuário conectado e conjuntos de dados aos quais o usuário tem acesso. |Dataset.ReadWrite.All |
| Adicionar dados ao conjunto de dados de um usuário |Dá acesso a um aplicativo para adicionar ou excluir linhas de conjunto de dados de um usuário. Essa permissão não concede ao aplicativo acesso aos dados do usuário. |Data.Alter_Any |
| Criar conteúdo |O aplicativo pode criar automaticamente conteúdo e conjuntos de dados para um usuário. |Content.Create |
| Exibir grupos de usuários |O aplicativo pode exibir todos os grupos aos quais o usuário conectado pertence. |Group.Read |
| Exibir todos os grupos |O aplicativo pode exibir todos os grupos aos quais o usuário conectado pertence. |Group.Read.All |
| Ler e gravar todos os Grupos |O aplicativo pode exibir e gravar em todos os grupos para o usuário conectado e em todos os grupos aos quais o usuário tenha acesso. |Group.ReadWrite.All |
| Exibir todos os Dashboards |O aplicativo pode exibir todos os painéis para o usuário conectado e os painéis aos quais o usuário tem acesso. |Dashboard.Read.All |
| Exibir todos os Relatórios |O aplicativo pode exibir todos os relatórios para o usuário conectado e os relatórios aos quais o usuário tem acesso. O aplicativo também pode ver os dados nos relatórios, bem como sua estrutura. |Report.Read.All |
| Ler e gravar todos os relatórios |O aplicativo pode exibir e gravar em todos os relatórios para o usuário conectado e em todos relatórios a que o usuário tem acesso. Isso não fornece direitos para criar um novo relatório. |Report.ReadWrite.All |
| Ler e gravar todas as Capacidades |O aplicativo pode exibir e gravar em todas as capacidades para o usuário conectado e em qualquer capacidade à qual o usuário tenha acesso. Isso não fornece direitos para criar uma nova capacidade. |Capacities.ReadWrite.All |
| Ler todas as Capacidades |O aplicativo pode exibir e gravar em todas as capacidades para o usuário conectado e em quaisquer capacidades às quais o usuário tenha acesso. Isso não fornece direitos para criar uma nova capacidade. |Capacities.Read.All |
| Ler e gravar todo o conteúdo no locatário |O aplicativo pode exibir e gravar em todos os artefatos, como grupos, relatórios, dashboards e conjuntos de dados no Power BI. Desde que o usuário conectado seja um administrador de serviços do Power BI. |Tenant.ReadWrite.All |
| Exibir todo o conteúdo no locatário |O aplicativo pode exibir todos os artefatos, como grupos, relatórios, dashboards e conjuntos de dados no Power BI. Desde que o usuário conectado seja um administrador de serviços do Power BI. |Tenant.Read.All |

Um aplicativo pode solicitar permissões ao tentar entrar na página do usuário pela primeira vez ao passar as permissões solicitadas no parâmetro de escopo da chamada. Se as permissões forem concedidas, um token de acesso será retornado ao aplicativo, e poderá ser usado em chamadas à API futuras. O acesso pode ser usado somente por um aplicativo específico.

> [!NOTE]
> As APIs do Power BI ainda se referem aos workspaces como grupos. As referências a grupos significam que você está trabalhando com workspaces.

## <a name="requesting-permissions"></a>Solicitando permissões

Embora você possa chamar a API para autenticar com um nome de usuário e senha, para executar ações em nome de outro usuário, será necessário solicitar permissões que o usuário aprovará e enviará o token de acesso resultante em todas as chamadas futuras. Para este processo, seguiremos o protocolo [OAuth 2.0](https://oauth.net/2/) padrão. Embora a implementação real possa variar, o fluxo do OAuth para o Power BI tem os seguintes elementos:

* **Interface do Usuário de Logon** - Trata-se de uma interface do usuário que o desenvolvedor pode evocar para solicitar permissões. Exigirá que o usuário entre, caso ainda não tenha entrado. O usuário também precisa aprovar as permissões que o aplicativo está solicitando. A janela de logon lançará um código de acesso ou uma mensagem de erro para uma URL de redirecionamento que é fornecida.
  * Uma URL de redirecionamento padrão deve ser fornecida pelo Power BI para ser usada por aplicativos nativos.
* **Código de Autorização** - Os Códigos de Autorização são retornados aos aplicativos Web após o logon por meio do parâmetros de URL na URL de redirecionamento. Como eles estão nos parâmetros, há alguns riscos de segurança. Os aplicativos Web terão de trocar o código de autorização por um Token de Autorização
* **Token de Autorização** - São usados para autenticar chamadas de API em nome de outro usuário. Eles terão escopo para um aplicativo específico. Os tokens têm um tempo de vida definido e quando expiram precisam ser atualizados.
* **Atualizar Token** - Quando os tokens expiram, há um processo para atualizá-los.

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)