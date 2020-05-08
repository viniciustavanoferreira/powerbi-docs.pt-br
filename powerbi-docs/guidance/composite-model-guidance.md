---
title: Diretrizes de modelos compostos no Power BI Desktop
description: Diretrizes para desenvolver modelos compostos.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 12/24/2019
ms.author: v-pemyer
ms.openlocfilehash: fa9ecd66d30839e169252065f7f736189b71b6ce
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/05/2020
ms.locfileid: "76889470"
---
# <a name="composite-model-guidance-in-power-bi-desktop"></a>Diretrizes de modelos compostos no Power BI Desktop

Este artigo se destina a modeladores de dados que estão desenvolvendo modelos compostos no Power BI. Ele descreve os casos de uso de modelo composto e fornece diretrizes de design. Especificamente, as diretrizes servem para ajudar você a determinar se um modelo composto é apropriado para sua solução. Se esse for o caso, então este artigo também o ajudará a criar um modelo ideal.

> [!NOTE]
> Este artigo não aborda a introdução aos modelos compostos. Se você não estiver totalmente familiarizado com os modelos compostos, recomendamos que leia primeiro o artigo [Usar modelos compostos no Power BI Desktop](../desktop-composite-models.md).
>
> Como os modelos compostos consistem em pelo menos uma fonte DirectQuery, também é importante que você tenha um entendimento completo das [relações de modelos](../desktop-relationships-understand.md), dos [modelos DirectQuery](../desktop-directquery-about.md) e das [diretrizes de design de modelo DirectQuery](directquery-model-guidance.md).

## <a name="composite-model-use-cases"></a>Casos de uso de modelo composto

Sempre que possível, é melhor desenvolver um modelo no Modo de importação. Esse modo fornece a maior flexibilidade de design e o melhor desempenho.

No entanto, os desafios relacionados a grandes volumes de dados ou relatórios de dados quase em tempo real não podem ser resolvidos pelos Modelos de importação. Em qualquer um desses casos, você pode considerar o uso de um modelo DirectQuery, desde que seus dados sejam armazenados em uma única fonte de dados [compatível com o modo DirectQuery](../power-bi-data-sources.md).

Além disso, você pode considerar o desenvolvimento de um modelo composto nas situações a seguir.

- Seu modelo pode ser um modelo DirectQuery, mas você quer melhorar o desempenho. Em um modelo composto, o desempenho pode ser melhorado configurando o armazenamento apropriado para cada tabela. Você também pode adicionar [agregações](../desktop-aggregations.md). Ambas as otimizações serão discutidas mais adiante neste artigo.
- Você deseja combinar um modelo DirectQuery com dados adicionais, que devem ser importados para o modelo. Os dados importados podem ser carregados de uma fonte de dados diferente ou de tabelas calculadas.
- Você deseja combinar duas ou mais fontes de dados DirectQuery em um único modelo.

> [!NOTE]
> Os modelos compostos não podem combinar fontes de Conexão dinâmica ou fontes de banco de dados analíticas do DirectQuery. As fontes de Conexão dinâmica incluem [modelos hospedados externos](../service-datasets-understand.md#external-hosted-models) e conjuntos de dados do Power BI. As fontes de banco de dados analíticas do DirectQuery incluem SAP Business Warehouse e SAP HANA.

## <a name="optimize-model-design"></a>Otimizar o design de modelos

Um modelo composto pode ser otimizado configurando os [modos de armazenamento](../desktop-storage-mode.md) de tabelas e adicionando [agregações](../desktop-aggregations.md).

### <a name="table-storage-mode"></a>Modo de armazenamento de tabela

Em um modelo composto, você pode configurar o modo de armazenamento para cada tabela (exceto tabelas calculadas):

- **DirectQuery**: Recomendamos que você defina esse modo para tabelas que representam grandes volumes de dados ou que precisam fornecer resultados quase em tempo real. Os dados nunca serão importados para essas tabelas. Normalmente, essas tabelas serão de tipo de fato, ou seja, tabelas usadas para resumos.
- **Importação**: recomendamos que você defina esse modo para tabelas de tipo de dimensão – tabelas usadas para filtragem e agrupamento. Na verdade, é a única opção para tabelas baseadas em fontes sem suporte pelo modo DirectQuery. As tabelas calculadas sempre são tabelas de importação.
- **Dupla**: recomendamos que você defina esse modo para tabelas de tipo de dimensão, quando houver uma possibilidade de serem consultadas junto com tabelas de tipo de fato DirectQuery da mesma fonte.

Há vários cenários possíveis em que o Power BI consulta um modelo composto:

- **Consultas somente de tabelas de importação ou duplas**: todos os dados são recuperados do cache de modelo. Isso fornecerá o desempenho mais rápido possível. Esse cenário é comum para tabelas de tipo de dimensão consultadas por filtros ou visuais de segmentação.
- **Consulta de tabelas duplas ou tabelas DirectQuery da mesma fonte**: todos os dados são recuperados enviando uma ou mais consultas nativas para a fonte DirectQuery. Isso fornecerá o desempenho mais rápido possível, especialmente quando existirem índices apropriados nas tabelas de origem. Esse cenário é comum para consultas que relacionam tabelas de tipo de dimensão duplas e tabelas de tipo de fato DirectQuery. Essas consultas são _intrailha_ e, portanto, todas as relações um para um ou um para muitos são avaliadas como [relações fortes](../desktop-relationships-understand.md#strong-relationships).
- **Todas as outras consultas**: essas consultas envolvem relações entre ilhas. Isso ocorre porque uma tabela de importação está relacionada a uma tabela DirectQuery, ou uma tabela dupla está relacionada a uma tabela DirectQuery de uma fonte diferente; nesse caso, ela se comporta como uma tabela de importação. Todas as relações são avaliadas como [relações fracas](../desktop-relationships-understand.md#weak-relationships). Isso também significa que os agrupamentos aplicados a tabelas que não são DirectQuery devem ser enviados para a fonte DirectQuery como uma tabela virtual. Nesse caso, a consulta nativa pode ser ineficiente, especialmente para grandes conjuntos de agrupamentos. Além disso, ela tem o potencial de expor dados confidenciais na consulta nativa.

Em resumo, recomendamos que você:

- Examine com atenção se o modelo composto é a solução certa – embora ele permita a integração no nível de modelo de diferentes fontes de dados, também apresenta complexidades de design com possíveis consequências
- Defina o modo de armazenamento para **DirectQuery** quando a tabela for de um tipo de fato que armazena grandes volumes de dados ou precisar fornecer resultados quase em tempo real
- Defina o modo de armazenamento para **Duplo** quando uma tabela for de tipo de dimensão e consultada junto com tabelas de tipo de fato **DirectQuery** baseadas na mesma fonte
- Configure as frequências de atualização apropriadas para manter o cache de modelo de tabelas duplas (e quaisquer tabelas calculadas dependentes) sincronizado com os bancos de dados da fonte
- Busque garantir a integridade dos dados entre as fontes de dados (incluindo o cache de modelo) – as relações fracas eliminarão as linhas quando os valores das colunas relacionadas não corresponderem
- Otimize as fontes de dados DirectQuery com índices apropriados para ter junções, filtragem e agrupamentos eficientes
- Não carregue dados confidenciais em tabelas duplas ou de importação se houver o risco de uma consulta nativa ser interceptada. Para obter mais informações, confira [Usar modelos compostos no Power BI Desktop (implicações de segurança)](../desktop-composite-models.md#security-implications)

### <a name="aggregations"></a>Agregações

Você pode adicionar agregações às tabelas DirectQuery em seu modelo composto. As agregações são armazenadas em cache no modelo e, portanto, comportam-se como tabelas de importação (embora não possam ser usadas como uma tabela de modelo). Sua finalidade é melhorar o desempenho de consultas de "granulação mais alta". Para obter mais informações, confira [Agregações no Power BI Desktop](../desktop-aggregations.md).

Recomendamos que a tabela de agregação siga uma regra básica: sua contagem de linhas deve ser pelo menos 10 vezes menor que a tabela subjacente. Por exemplo, se a tabela subjacente armazenar 1 bilhão de linhas, a tabela de agregação não deverá exceder 100 milhões linhas. Essa regra garante um ganho de desempenho adequado em relação ao custo de criação e manutenção da tabela de agregação.

## <a name="next-steps"></a>Próximas etapas

Para obter mais informações relacionadas a este artigo, confira os seguintes recursos:

- [Usar modelos compostos no Power BI Desktop](../desktop-composite-models.md)
- [Modelar relações no Power BI Desktop](../desktop-relationships-understand.md)
- [Modelos de DirectQuery no Power BI Desktop](../desktop-directquery-about.md)
- [Usar o DirectQuery no Power BI Desktop](../desktop-use-directquery.md)
- [Solução de problemas do modelo de DirectQuery no Power BI Desktop](../desktop-directquery-troubleshoot.md)
- [Fontes de dados do Power BI](../power-bi-data-sources.md)
- [Modo de armazenamento no Power BI Desktop](../desktop-storage-mode.md)
- [Agregações no Power BI Desktop](../desktop-aggregations.md)
- Dúvidas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
- Sugestões? [Contribuir com ideias para aprimorar o Power BI](https://ideas.powerbi.com)
