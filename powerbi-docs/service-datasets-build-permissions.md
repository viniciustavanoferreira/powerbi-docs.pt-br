---
title: Permissão Criar para conjuntos de dados compartilhados (versão prévia)
description: Saiba como você manter o controle de quem tem acesso aos dados usando a permissão Criar.
author: maggiesMSFT
manager: kfile
ms.reviewer: chbraun
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 10/01/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 069ec5e0c767bcfcb0a4a41c2180ae78146800f2
ms.sourcegitcommit: 5e277dae93832d10033defb2a9e85ecaa8ffb8ec
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72020955"
---
# <a name="build-permission-for-shared-datasets-preview"></a>Permissão Criar para conjuntos de dados compartilhados (versão prévia)

Como um criador de *modelos de dados* no Power BI Desktop, você pode compartilhá-los como *conjuntos de dados* no serviço do Power BI. Em seguida, os criadores de relatórios poderão descobrir e reutilizar os conjuntos de dados que você compartilhou com facilidade. Saiba como controlar quem tem acesso aos dados usando a permissão Criar.

A permissão Criar só é relevante para conjuntos de dados. Ao dar aos usuários a permissão Criar, eles podem criar um conteúdo em um conjunto de dados, como relatórios, dashboards, blocos fixados de P e R e Descoberta de Insights. Elas também podem criar um conteúdo no conjunto de dados fora do Power BI, como planilhas do Excel por meio do recurso Analisar no Excel, XMLA e exportar os dados subjacentes.

## <a name="ways-to-give-build-permission"></a>Maneiras de conceder a permissão Criar

Você pode conceder a permissão Criar para um conjunto de dados de diferentes formas:

- Membros de um workspace com, pelo menos, uma função de Colaborador têm automaticamente a permissão Criar para um conjunto de dados nesse workspace e permissão para copiar um relatório.
 
- Os membros do workspace no qual reside o conjunto de dados podem atribuir a permissão a usuários ou grupos de segurança específicos na Central de permissões. Se você é membro do workspace, selecione as reticências (...) ao lado de um conjunto de dados > **Gerenciar Permissões**.

    ![Selecionar as reticências](media/service-datasets-build-permissions/power-bi-dataset-permissions-new-look.png)

    Isso abrirá a Central de permissões desse conjunto de dados, na qual você pode definir e alterar permissões.

    ![Central de permissões](media/service-datasets-build-permissions/power-bi-dataset-remove-permissions-no-callouts.png)

- Um administrador ou um membro do workspace no qual reside o conjunto de dados pode decidir, durante a publicação do aplicativo, que os usuários com a permissão no aplicativo também devem obter a permissão Criar nos conjuntos de dados subjacentes. Confira [Compartilhar um conjunto de dados](service-datasets-share.md) para obter mais detalhes.

- Digamos que você tenha as permissões Compartilhar novamente e Criar em um conjunto de dados. Ao compartilhar um relatório ou um dashboard nesse conjunto de dados, você pode especificar que os destinatários também obtenham a permissão Criar no conjunto de dados subjacente.

    ![Permissão Criar](media/service-datasets-build-permissions/power-bi-share-report-allow-users.png)

Você pode remover a permissão Criar de uma pessoa em um conjunto de dados. Se você fizer isso, elas ainda poderão ver o relatório criado no conjunto de dados compartilhado, mas não poderão mais editá-lo. Confira a próxima seção para saber mais detalhes.

## <a name="remove-build-permission-for-a-dataset"></a>Remover permissão Criar em um conjunto de dados

Em algum momento, talvez seja necessário remover a permissão Criar de alguns usuários de um conjunto de dados compartilhado. 

1. Em um workspace, acesse a página da lista **Conjuntos de dados**. 
1. Selecione as reticências (...) ao lado do conjunto de dados > **Gerenciar permissão**.

    ![Gerenciar permissões](media/service-datasets-build-permissions/power-bi-dataset-permissions-new-look.png)

1. Selecione as reticências (...) ao lado de um nome > **Remover permissão Criar**.

    ![Remover permissão Criar](media/service-datasets-build-permissions/power-bi-dataset-remove-build-permissions.png)

    As pessoas ainda poderão ver o relatório criado no conjunto de dados compartilhado, mas não poderão mais editá-lo.

### <a name="remove-build-permission-for-a-dataset-in-an-app"></a>Remover permissão Criar para um conjunto de dados em um aplicativo

Digamos que você tenha distribuído um aplicativo de um workspace para um grupo de pessoas. Posteriormente, você decide remover o acesso ao aplicativo de algumas pessoas. Remover o acesso ao aplicativo não remove automaticamente as permissões Criar e Compartilhar novamente. Essa é um etapa adicional. 

1. Em uma página de lista do workspace, selecione **Atualizar o aplicativo**. 

    ![Atualizar aplicativo](media/service-datasets-build-permissions/power-bi-app-update.png)

1. Na guia **Permissões**, selecione o **X** para excluir a pessoa ou o grupo. 

    ![Selecione o X](media/service-datasets-build-permissions/power-bi-app-delete-user.png)
1. Selecione **Atualizar aplicativo**.

    Você verá uma mensagem explicando que precisa acessar **Gerenciar permissões** para remover a permissão Criar para usuários com acesso existente. 

    ![Mensagem de gerenciar permissões](media/service-datasets-build-permissions/power-bi-dataset-app-remove-message.png)

1. Selecione **Atualizar**.

1. No workspace, acesse a página da lista **Conjuntos de dados**. 
1. Selecione as reticências (...) ao lado do conjunto de dados > **Gerenciar permissão**.

    ![Gerenciar permissões](media/service-datasets-build-permissions/power-bi-dataset-permissions-new-look.png)

1. Selecione as reticências (...) ao lado do nome > **Remover permissão Criar**.

    ![Remover permissão Criar](media/service-datasets-build-permissions/power-bi-dataset-remove-build-permissions.png)

    As pessoas ainda poderão ver o relatório criado no conjunto de dados compartilhado, mas não poderão mais editá-lo.

## <a name="more-granular-permissions"></a>Permissões mais granulares

O Power BI introduziu a permissão Criar em junho de 2019 como um complemento às permissões existentes, Ler e Compartilhar novamente. Todos os usuários que já tinham a permissão Ler em conjuntos de dados por meio de permissões do aplicativo, compartilhamento ou acesso ao workspace naquela época também tinha a permissão Criar nesses mesmos conjuntos de dados. Eles obtinham a permissão Criar automaticamente, porque a permissão Ler já concedia a eles o direito de criar um conteúdo com base no conjunto de dados, por meio do recurso Analisar no Excel ou Exportar.

Com essa permissão Criar mais granular, você pode escolher quem pode apenas exibir o conteúdo no relatório ou no dashboard existente e quem pode criar um conteúdo conectado aos conjuntos de dados subjacentes.

Se o conjunto de dados estiver sendo usado por um relatório fora do workspace do conjunto de dados, você não poderá excluir esse conjunto de dados. Em vez disso, você verá uma mensagem de erro.

Você pode remover a permissão Criar. Se você fizer isso, as pessoas cujas permissões foram revogadas por você ainda poderão ver o relatório, mas não poderão mais editá-lo nem exportar dados subjacentes. Os usuários apenas com permissão de leitura ainda podem exportar dados resumidos. 

## <a name="next-steps"></a>Próximas etapas

- [Usar conjuntos de dados em workspaces (versão prévia)](service-datasets-across-workspaces.md)
- Dúvidas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)
