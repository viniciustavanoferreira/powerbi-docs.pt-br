---
title: Compartilhar um conjunto de dados (versão prévia)
description: Como um proprietário de conjunto de dados, você pode criar e compartilhar seus conjuntos de dados para que outras pessoas possam usá-los. Saiba como você pode manter o controle de quem tem acesso aos dados usando a permissão Criar.
author: maggiesMSFT
manager: kfile
ms.reviewer: chbraun
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 08/14/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 17c3322ed5f24d106412bafb9c4235ee15a626aa
ms.sourcegitcommit: 4d5166944fcc6fe4666cab055ae75e7a0a77866d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/16/2019
ms.locfileid: "69530524"
---
# <a name="share-a-dataset-preview"></a>Compartilhar um conjunto de dados (versão prévia)

Como um criador de *modelos de dados* no Power BI Desktop, você pode compartilhá-los como *conjuntos de dados* no serviço do Power BI. Em seguida, os criadores de relatórios poderão descobrir e reutilizar os conjuntos de dados que você compartilhou com facilidade. Saiba como compartilhá-los e como você controla quem tem acesso aos dados usando a permissão Criar.

## <a name="steps-to-sharing-your-dataset"></a>Etapas para compartilhar seu conjunto de dados

1. Comece criando um arquivo .pbix com um modelo de dados no Power BI Desktop. Se pretende oferecer esse conjunto de dados para outras pessoas criarem relatórios, talvez você nem mesmo projete um relatório no arquivo .pbix.

    Uma melhor prática é salvar o arquivo .pbix em um grupo do Office 365.

1. Publique o arquivo .pbix em um [workspace da nova experiência](service-create-the-new-workspaces.md) no serviço do Power BI.
    
    Os outros membros desse workspace já podem criar relatórios em outros workspaces com base nesse conjunto de dados.

1. Você também pode [publicar um aplicativo](service-create-distribute-apps.md) usando esse workspace. Quando fizer isso, na página **Permissões**, especifique quem tem permissões e o que eles podem fazer.

    > [!NOTE]
    > Se você selecionar **Organização inteira**, ninguém da organização terá permissões Criar. Esse problema já é conhecido. Em vez disso, especifique endereços de email em **Indivíduos ou grupos específicos**.  Caso você deseje que toda a sua organização tenha permissões Criar, especifique um alias de email para toda a organização.

    ![Definir as permissões do aplicativo](media/service-datasets-build-permissions/power-bi-dataset-app-permissions.png)

1. Selecione **Publicar aplicativo** ou **Atualizar aplicativo** se ele já tiver sido publicado.

## <a name="build-permissions-for-shared-datasets"></a>Permissões Criar para conjuntos de dados compartilhados

O tipo de permissão Criar só é relevante para conjuntos de dados. Com ele, os usuários podem criar um conteúdo em um conjunto de dados, como relatórios, dashboards, blocos fixados de P e R e Descoberta de Insights. Elas também podem criar um conteúdo no conjunto de dados fora do Power BI, como planilhas do Excel por meio do recurso Analisar no Excel, XMLA e Exportar.

Os usuários obtêm a permissão Criar de maneiras diferentes:

- Se for um membro de um workspace com, pelo menos, função de Colaborador, você terá automaticamente permissão de Build para um conjunto de dados e permissão para copiar um relatório.
 
- Um membro do workspace no qual reside o conjunto de dados pode atribuir a permissão a usuários ou grupos de segurança específicos na Central de permissões. Selecione as reticências (...) ao lado de um conjunto de dados > **Gerenciar Permissões**.

    ![Selecionar as reticências](media/service-datasets-build-permissions/power-bi-dataset-manage-permissions.png)

    Isso abrirá a Central de permissões desse conjunto de dados, na qual você pode definir e alterar permissões.

    ![Central de permissões](media/service-datasets-build-permissions/power-bi-dataset-permissions.png)

- Um administrador ou um membro do workspace no qual reside o conjunto de dados pode decidir, durante a publicação do aplicativo, que os usuários com a permissão no aplicativo também devem obter a permissão Criar nos conjuntos de dados subjacentes. Confira [Etapas para compartilhar seu conjunto de dados](#steps-to-sharing-your-dataset) neste artigo para obter detalhes.

- Digamos que você tenha permissões Compartilhar novamente e Criar em um conjunto de dados. Ao compartilhar um relatório ou um dashboard baseado nesse conjunto de dados, você pode especificar que os destinatários também obtenham a permissão Criar no conjunto de dados subjacente.

    ![Permissões Criar](media/service-datasets-build-permissions/power-bi-share-report-allow-users.png)

Você pode remover as permissões Criar de uma pessoa para um conjunto de dados. Se você fizer isso, elas ainda poderão ver o relatório criado no conjunto de dados compartilhado, mas não poderão mais editá-lo.

## <a name="more-granular-permissions"></a>Permissões mais granulares

O Power BI introduziu a permissão Criar em junho de 2019 como um complemento às permissões existentes, Ler e Compartilhar novamente. Todos os usuários que já tinham a permissão Ler em conjuntos de dados por meio de permissões do aplicativo, compartilhamento ou acesso ao workspace naquela época também tinham permissões Criar nesses mesmos conjuntos de dados. Eles obtinham a permissão Criar automaticamente, porque a permissão Ler já concedia a eles o direito de criar um conteúdo com base no conjunto de dados, por meio do recurso Analisar no Excel ou Exportar.

Com essa permissão Criar mais granular, você pode escolher quem pode apenas exibir o conteúdo no relatório ou no dashboard existente e quem pode criar um conteúdo conectado aos conjuntos de dados subjacentes.

Se o conjunto de dados estiver sendo usado por um relatório fora do workspace do conjunto de dados, você não poderá excluir esse conjunto de dados. Em vez disso, você verá uma mensagem de erro.

Você poderá remover as permissões Criar. Se você fizer isso, as pessoas cujas permissões foram revogadas por você ainda poderão ver o relatório, mas não poderão mais editá-lo.

## <a name="track-your-dataset-usage"></a>Acompanhar o uso do conjunto de dados

Quando você tiver um conjunto de dados compartilhado em seu workspace, talvez você precise saber quais relatórios em outros workspaces são baseados nele.

1. Na exibição de lista Conjuntos de dados, selecione **Exibir relacionados**.

    ![Ícone Exibir relacionados](media/service-datasets-build-permissions/power-bi-dataset-view-related-to-dataset.png)

1. A caixa de diálogo **Conteúdo relacionado** mostra todos os itens relacionados. Nessa lista, você verá os itens relacionados nesse workspace e em **Outros workspaces**.
 
    ![Caixa de diálogo Conteúdo relacionado](media/service-datasets-build-permissions/power-bi-dataset-related-workspaces.png)

## <a name="next-steps"></a>Próximas etapas

- [Usar conjuntos de dados em workspaces (versão prévia)](service-datasets-across-workspaces.md)
- Dúvidas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)
