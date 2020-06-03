---
title: Introdução a conjuntos de dados entre workspaces
description: Saiba como você pode compartilhar um conjunto de dados com usuários em toda a organização. Em seguida, eles podem criar relatórios com base no conjunto de dados em seus próprios workspaces.
author: maggiesMSFT
ms.reviewer: kayu
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/30/2020
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 0458498b5677f20bac3a2e50f884d820ef1c3648
ms.sourcegitcommit: 5e5a7e15cdd55f71b0806016ff91256a398704c1
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83793621"
---
# <a name="intro-to-datasets-across-workspaces"></a>Introdução a conjuntos de dados entre workspaces

Business intelligence é uma atividade colaborativa. É importante estabelecer conjuntos de dados padronizados que possam ser a 'única fonte de verdade'. Em seguida, descobrir e reutilizar esses conjuntos de dados padronizados é fundamental. Quando os modeladores de dados especialistas em sua organização criam e compartilham conjuntos de dados otimizados, os criadores de relatórios podem começar com esses conjuntos de dados para criar relatórios precisos. Em seguida, sua organização terá dados consistentes para tomar decisões e uma cultura de dados íntegra.

![Selecionar um conjunto de dados compartilhado](media/service-datasets-across-workspaces/power-bi-select-shared-dataset.png)

No Power BI, os criadores de conjuntos de dados podem manter controle de quem tem acesso a seus dados usando a [Permissão Compilar](service-datasets-build-permissions.md). Os criadores de conjuntos de dados também podem *certificar* ou *promover* conjuntos de dados para que outras pessoas possam descobri-los. Dessa forma, os autores do relatório sabem quais conjuntos de dados são de alta qualidade e oficiais, e eles podem usar esses conjuntos de dados sempre que criarem no Power BI. Os administradores de locatários têm uma nova configuração de locatário para [controlar o uso de conjuntos de dados em workspaces](service-datasets-admin-across-workspaces.md).

## <a name="dataset-sharing-and-the-new-workspace-experience"></a>Compartilhamento de conjuntos de dados e a nova experiência de workspace

A criação de relatórios com base em conjuntos de dados em diferentes workspaces e a cópia de relatórios para diferentes workspaces estão estreitamente ligados à [nova experiência de workspace](../collaborate-share/service-create-the-new-workspaces.md):

- No serviço, quando você abre o catálogo do conjunto de dados em uma nova experiência de workspace, o catálogo do conjunto de dados mostra os conjuntos de dados que estão em Meu workspace e outros workspaces da nova experiência de workspace. 
- Quando você abre o catálogo do conjunto de dados em um workspace clássico, você vê apenas os conjuntos de dados desse workspace, não aqueles de outros workspaces.
- No Power BI Desktop, você pode publicar relatórios do Live Connect em diferentes workspaces, desde que os conjuntos de dados estejam em workspaces da nova experiência.
- Ao copiar relatórios em workspaces, o workspace de destino precisa ser um workspace da nova experiência.

## <a name="discover-datasets"></a>Descobrir conjuntos de dados

Ao criar um relatório com base em um conjunto de dados existente, a primeira etapa é se conectar ao conjunto de dados, no serviço do Power BI ou no Power BI Desktop. Leia mais sobre [como descobrir conjuntos de dados em diferentes workspaces](service-datasets-discover-across-workspaces.md)

## <a name="copy-a-report"></a>Copiar um relatório

Quando você encontrar um relatório de seu interesse, em um workspace ou um aplicativo, você poderá fazer uma cópia dele e, em seguida, modificá-lo de acordo com suas necessidades. Você não precisa se preocupar com a criação do modelo de dados. Ele já é criado para você. Além disso, é muito mais fácil modificar um relatório existente do que começar do zero. Leia mais sobre como [copiar relatórios](service-datasets-copy-reports.md).

## <a name="build-permission-for-datasets"></a>Permissão Criar em conjuntos de dados

Com o tipo de permissão Criar, se você for um criador de conjuntos de dados, poderá determinar quem em sua organização pode criar novo conteúdo em seus conjuntos de dados. Pessoas com a permissão Criar também podem criar um conteúdo no conjunto de dados fora do Power BI, como planilhas do Excel, por meio do recurso Analisar no Excel, XMLA e Exportar. Leia mais sobre a [Permissão Criar](service-datasets-build-permissions.md).

## <a name="promotion-and-certification"></a>Promoção e certificação

Se você cria conjuntos de dados, quando criar um com o qual outras pessoas possam se beneficiar, poderá facilitar sua descoberta [promovendo seu conjunto de dados](service-datasets-promote.md). Solicite também aos especialistas de sua organização a [certificação do conjunto de dados](service-datasets-certify.md).

## <a name="licensing"></a>Licenças

Os recursos específicos e as experiências criadas com base nas funcionalidades do conjunto de dados compartilhado são licenciados de acordo com os cenários existentes. Por exemplo:

- Em geral, a descoberta e a conexão a conjuntos de dados compartilhados estão disponíveis para qualquer pessoa, não é um recurso restrito ao Premium.
- Os usuários sem uma licença Pro só poderão usar conjuntos de dados entre workspaces para a criação de relatórios se esses conjuntos de dados residirem no Meu Workspace desses usuários ou em um workspace com suporte Premium. A mesma restrição de licenciamento se aplicará se eles criarem relatórios no Power BI Desktop ou no serviço do Power BI.
- Copiar relatórios entre workspaces requer uma licença Pro.
- A cópia de relatórios por meio de um aplicativo exige uma licença Pro, como era necessário para pacotes de conteúdo organizacional.
- A promoção e a certificação de conjuntos de dados exigem uma licença Pro.

## <a name="considerations-and-limitations"></a>Considerações e limitações

- Como editor de aplicativos, você precisa ter a certeza de que seu público-alvo tem acesso aos conjuntos de dados fora do workspace. Caso contrário, os usuários terão problemas ao interagir com seu aplicativo: os relatórios não serão abertos sem acesso ao conjunto de dados e os blocos do painel serão mostrados como bloqueados. Além disso, os usuários não poderão abrir o aplicativo se o primeiro item em sua navegação for um relatório sem acesso ao conjunto de dados.
- A criação de um relatório com base em um conjunto de dados em outro workspace exige a nova experiência de workspace em ambas as extremidades: O relatório e o conjunto de dados precisam estar em uma nova experiência de workspace. Você só pode copiar relatórios de uma nova experiência de workspace para outra, não para workspaces clássicos nem para o Meu Workspace. 
- Em um workspace clássico, a experiência de descoberta de conjunto de dados mostra apenas os conjuntos de dados desse workspace.
- Por design, o recurso "Publicar na Web" não funciona em relatórios baseados em conjuntos de dados compartilhados.
- Se duas pessoas forem membros de um workspace que acessa um conjunto de dados compartilhado, talvez apenas uma delas veja o conjunto de dados relacionado no workspace. Somente as pessoas com, pelo menos, acesso de leitura ao conjunto de dados podem ver o conjunto de dados compartilhado. 

## <a name="next-steps"></a>Próximas etapas

- [Promover conjuntos de dados](service-datasets-promote.md)
- [Certificar conjuntos de dados](service-datasets-certify.md)
- [Controlar o uso de conjuntos de dados em workspaces](service-datasets-admin-across-workspaces.md)
- Dúvidas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
