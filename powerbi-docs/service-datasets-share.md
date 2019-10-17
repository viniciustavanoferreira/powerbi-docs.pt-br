---
title: Compartilhar um conjunto de dados (versão prévia)
description: Como um proprietário de conjunto de dados, você pode criar e compartilhar seus conjuntos de dados para que outras pessoas possam usá-los. Saiba como compartilhá-los.
author: maggiesMSFT
manager: kfile
ms.reviewer: chbraun
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 10/01/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: c490228a1dfa1e6c842db3c41ab077a99f35f975
ms.sourcegitcommit: 5e277dae93832d10033defb2a9e85ecaa8ffb8ec
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72021104"
---
# <a name="share-a-dataset-preview"></a>Compartilhar um conjunto de dados (versão prévia)

Como um criador de *modelos de dados* no Power BI Desktop, você cria *conjuntos de dados* que podem ser distribuídos no serviço do Power BI. Em seguida, outros criadores de relatório podem usar seus conjuntos de valores como base para seus próprios relatórios. Neste artigo, você aprenderá a compartilhar seus conjuntos de dados. Para saber como conceder e remover o acesso aos seus conjuntos de dados compartilhados, leia sobre a [permissão Criar](service-datasets-build-permissions.md).

## <a name="steps-to-sharing-your-dataset"></a>Etapas para compartilhar seu conjunto de dados

1. Comece criando um arquivo .pbix com um modelo de dados no Power BI Desktop. Se pretende oferecer esse conjunto de dados para outras pessoas criarem relatórios, talvez você nem mesmo projete um relatório no arquivo .pbix.

    Uma melhor prática é salvar o arquivo .pbix em um grupo do Office 365.

1. Publique o arquivo .pbix em um [workspace da nova experiência](service-create-the-new-workspaces.md) no serviço do Power BI.
    
    Os outros membros desse workspace já podem criar relatórios em outros workspaces com base nesse conjunto de dados.

1. Você também pode [publicar um aplicativo](service-create-distribute-apps.md) usando esse workspace. Quando fizer isso, na página **Permissões**, especifique quem tem permissões e o que eles podem fazer.

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

## <a name="next-steps"></a>Próximas etapas

- [Usar conjuntos de dados em workspaces (versão prévia)](service-datasets-across-workspaces.md)
- Dúvidas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)
