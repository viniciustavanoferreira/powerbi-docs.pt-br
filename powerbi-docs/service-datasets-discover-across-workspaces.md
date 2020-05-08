---
title: Criar relatórios com base em conjuntos de dados de diferentes workspaces (versão prévia) – Power BI
description: Saiba como você pode compartilhar um conjunto de dados com usuários em toda a organização. Em seguida, eles podem criar relatórios com base no conjunto de dados em seus próprios workspaces.
author: maggiesMSFT
ms.reviewer: chbraun
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 07/03/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 371507eb86e1b68225e9d66ee3a1363b0e163d4f
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/05/2020
ms.locfileid: "73877164"
---
# <a name="create-reports-based-on-datasets-from-different-workspaces-preview"></a>Criar relatórios com base em conjuntos de dados de diferentes workspaces (versão prévia)

Saiba como você pode criar relatórios em seus próprios workspaces com base em conjuntos de dados de outros workspaces. Para criar um relatório baseado em um conjunto de dados existente, você pode começar no Power BI Desktop ou no serviço do Power BI, em Meu Workspace ou em uma [nova experiência de workspace](service-create-the-new-workspaces.md).

- No serviço do Power BI: **Obter dados** > **Conjuntos de dados publicados**.
- No Power BI Desktop: **Obter dados** > **Conjuntos de dados do Power BI**.

    ![Conectar-se a um conjunto de dados existente](media/service-datasets-across-workspaces/power-bi-connect-dataset-pk.png)
   
Em ambos os casos, a experiência de descoberta de conjunto de dados começa na caixa de diálogo **Selecionar um conjunto de dados para criar um relatório**. Você verá todos os conjuntos de dados aos quais tem acesso, independentemente do local em que estejam:

![Selecionar um conjunto de dados](media/service-datasets-across-workspaces/power-bi-select-dataset.png)

Observe que o primeiro deles é rotulado **Promovido**. Falaremos mais sobre isso em [Encontrar um conjunto de dados endossado](#find-an-endorsed-dataset), mais adiante neste artigo.

Os conjuntos de dados exibidos nesta lista atendem a, pelo menos, uma das seguintes condições:

- O conjunto de dados está em um dos workspaces da nova experiência de workspace e você é membro desse workspace. Confira [Considerações e limitações](service-datasets-across-workspaces.md#considerations-and-limitations).
- Você tem a permissão Criar no conjunto de dados, que está em um workspace da nova experiência de workspace.
- O conjunto de dados está em Meu Workspace.

> [!NOTE]
> Se você for um usuário gratuito, verá apenas os conjuntos de dados em Meu Workspace ou os conjuntos de dados nos quais você tem a permissão Criar e que estão em workspaces da capacidade Premium.

Ao clicar em **Criar**, você criará uma conexão dinâmica com o conjunto de dados e a experiência de criação de relatório será aberta com o conjunto de dados completo disponível. Você não fez uma cópia do conjunto de dados. O conjunto de dados ainda reside em sua localização original. Você pode usar todas as tabelas e as medidas no conjunto de dados para criar seus próprios relatórios. As restrições de RLS (Segurança em Nível de Linha) no conjunto de dados estão em vigor, de modo que você veja apenas os dados que têm permissões de ver de acordo com sua função RLS.

Você pode salvar o relatório no workspace atual no serviço do Power BI ou publicar o relatório em um workspace por meio do Power BI Desktop. O Power BI cria automaticamente uma entrada na lista de conjuntos de dados se o relatório é baseado em um conjunto de dados fora do workspace. O ícone para esse conjunto de dados é diferente do ícone para conjuntos de dados no workspace: ![Ícone do conjunto de dados compartilhado](media/service-datasets-discover-across-workspaces/power-bi-shared-dataset-icon.png)

Dessa forma, os membros do workspace podem saber quais relatórios e dashboards usam conjuntos de dados que estão fora do workspace. A entrada mostra informações sobre o conjunto de dados e algumas ações selecionadas.

![Ações do conjunto de dados](media/service-datasets-across-workspaces/power-bi-dataset-actions.png)

## <a name="find-an-endorsed-dataset"></a>Encontrar um conjunto de dados endossado

Há dois tipos diferentes de conjuntos de dados endossados. Os proprietários de conjuntos de dados podem *promover* um conjunto de dados que eles recomendam para você. Além disso, o administrador de locatários do Power BI pode designar especialistas em sua organização que podem *certificar* conjuntos de dados para uso de todos. Os conjuntos de dados promovidos e certificados exibem *selos* que você vê ao procurar um conjunto de dados e na lista de conjuntos de dados em um workspace. O nome da pessoa que certificou um conjunto de dados é exibido em uma dica de ferramenta durante a experiência de descoberta do conjunto de dados; passe o mouse sobre o rótulo **Certificado** e você o verá.

- No serviço do Power BI: **Obter dados** > **Conjuntos de dados publicados**.
- No Power BI Desktop: **Obter dados** > **Conjuntos de dados do Power BI**.

    Na caixa de diálogo **Selecionar um conjunto de dados**, os conjuntos de dados endossados aparecem no início da lista por padrão. 

    ![Conjunto de dados promovido](media/service-datasets-certify-promote/power-bi-dataset-promoted.png)

## <a name="next-steps"></a>Próximas etapas

- [Usar conjuntos de dados em workspaces (versão prévia)](service-datasets-across-workspaces.md)
- Dúvidas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
