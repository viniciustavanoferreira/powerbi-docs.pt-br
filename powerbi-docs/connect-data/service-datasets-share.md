---
title: Compartilhar um conjunto de dados
description: Como um proprietário de conjunto de dados, você pode criar e compartilhar seus conjuntos de dados para que outras pessoas possam usá-los. Saiba como compartilhá-los.
author: maggiesMSFT
ms.reviewer: kayu
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/30/2020
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: b6e45113662117d5c6c793211644c4895f666a40
ms.sourcegitcommit: 49daa8964c6e30347e29e7bfc015762e2cf494b3
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84273335"
---
# <a name="share-a-dataset"></a>Compartilhar um conjunto de dados

Como um criador de *modelos de dados* no Power BI Desktop, você cria *conjuntos de dados* que podem ser distribuídos no serviço do Power BI. Em seguida, outros criadores de relatório podem usar seus conjuntos de valores como base para seus próprios relatórios. Neste artigo, você aprenderá a compartilhar seus conjuntos de dados. Para saber como conceder e remover o acesso aos seus conjuntos de dados compartilhados, leia sobre a [permissão Criar](service-datasets-build-permissions.md).

## <a name="steps-to-sharing-your-dataset"></a>Etapas para compartilhar seu conjunto de dados

1. Comece criando um arquivo .pbix com um modelo de dados no Power BI Desktop. Se pretende oferecer esse conjunto de dados para outras pessoas criarem relatórios, talvez você nem mesmo projete um relatório no arquivo .pbix.

    Uma melhor prática é salvar o arquivo .pbix em um grupo do Microsoft 365.

1. Publique o arquivo .pbix em uma [nova experiência do workspace](../collaborate-share/service-create-the-new-workspaces.md) no serviço do Power BI.
    
    Os outros membros desse workspace já podem criar relatórios em outros workspaces com base nesse conjunto de dados. Use a opção Gerenciar Permissões no conjunto de dados na lista de conteúdo do workspace para permitir acesso de usuários adicionais ao conjunto de dados. 

1. Você também pode [publicar um aplicativo](../collaborate-share/service-create-distribute-apps.md) usando esse workspace. Quando fizer isso, na página **Permissões**, especifique quem tem permissões e o que eles podem fazer.

    > [!NOTE]
    > Se você selecionar **Organização inteira**, ninguém da organização terá a permissão Criar. Esse problema já é conhecido. Em vez disso, especifique endereços de email em **Indivíduos ou grupos específicos**.  Caso você deseje que toda a sua organização tenha a permissão Criar, especifique um alias de email para toda a organização.

    ![Definir as permissões do aplicativo](media/service-datasets-build-permissions/power-bi-dataset-app-permission-new-look.png)

1. Selecione **Publicar aplicativo** ou **Atualizar aplicativo** se ele já tiver sido publicado.

## <a name="track-your-dataset-usage"></a>Acompanhar o uso do conjunto de dados

Quando você tiver um conjunto de dados compartilhado em seu workspace, talvez você precise saber quais relatórios em outros workspaces são baseados nele.

1. Na exibição de lista Conjuntos de dados, selecione **Exibir relacionados**.

    ![Ícone Exibir relacionados](media/service-datasets-build-permissions/power-bi-dataset-view-related-to-dataset.png)

1. A caixa de diálogo **Conteúdo relacionado** mostra todos os itens relacionados. Nessa lista, você verá os itens relacionados nesse workspace e em **Outros workspaces**.
 
    ![Caixa de diálogo Conteúdo relacionado](media/service-datasets-build-permissions/power-bi-dataset-related-workspaces.png)

## <a name="limitations-and-considerations"></a>Limitações e considerações
O que lembrar a respeito do compartilhamento de conjuntos de dados:

* Quando você compartilha um conjunto de dados gerenciando permissões, compartilhando relatórios ou dashboards, ou publicando um aplicativo, você está permitindo o acesso a todo o conjunto de dados, a menos que a [RLS (segurança em nível de linha)](../admin/service-admin-rls.md) limite o acesso. Os autores de relatório podem usar funcionalidades que personalizam experiências do usuário ao exibir ou interagir com relatórios, por exemplo, ocultar colunas, limitar as ações em visuais e outras. Essa experiência de usuário personalizada não restringe quais dados os usuários podem acessar no conjunto de dados. Use a [RLS (segurança em nível de linha)](../admin/service-admin-rls.md) no conjunto de dados para que as credenciais de cada pessoa determinem quais dados elas podem acessar.

## <a name="next-steps"></a>Próximas etapas

- [Usar conjuntos de dados em workspaces](service-datasets-across-workspaces.md)
- Dúvidas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
