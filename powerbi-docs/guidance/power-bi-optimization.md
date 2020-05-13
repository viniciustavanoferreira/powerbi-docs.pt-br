---
title: Guia de otimização para o Power BI
description: Guia de otimização para o Power BI.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 02/16/2020
ms.author: v-pemyer
ms.openlocfilehash: f189ea2944f86a3caabfbc51ae5b2887bc7c89bb
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83278597"
---
# <a name="optimization-guide-for-power-bi"></a>Guia de otimização para o Power BI

Este artigo fornece diretrizes que permitem a desenvolvedores e administradores produzir e manter soluções otimizadas do Power BI. Você pode otimizar sua solução em diferentes camadas de arquitetura. As camadas incluem:

- As fontes de dados
- O modelo de dados
- Visualizações, incluindo dashboards, relatórios do Power BI e relatórios paginados do Power BI
- O ambiente, incluindo capacidades, gateways de dados e a rede

## <a name="optimizing-the-data-model"></a>Otimizar modelos de dados

O modelo de dados dá suporte à experiência inteira de visualização. Os modelos de dados são hospedados externa ou internamente e, no Power BI, são chamados de _conjuntos de dados_. É importante entender suas opções e escolher o tipo apropriado de conjunto de dados para sua solução. Os três modos de conjunto de dados são: Importação, DirectQuery e composto. Confira mais informações em [Conjuntos de dados no serviço do Power BI](../connect-data/service-datasets-understand.md) e em [Modos de conjuntos de dados no serviço do Power BI](../connect-data/service-dataset-modes-understand.md).

Para obter diretrizes específicas do modo de conjunto de dados, confira:

- [Técnicas de redução de dados para modelagem de importação](import-modeling-data-reduction.md)
- [Diretrizes sobre modelos de DirectQuery no Power BI Desktop](directquery-model-guidance.md)
- [Diretrizes sobre modelos compostos no Power BI Desktop](composite-model-guidance.md)

## <a name="optimizing-visualizations"></a>Otimizar visualizações

As visualizações do Power BI, incluindo dashboards, relatórios do Power BI e relatórios paginados do Power BI. Cada uma tem diferentes arquiteturas e, portanto, suas próprias diretrizes. 

### <a name="dashboards"></a>Dashboards

É importante entender que o Power BI mantém um cache para os blocos de dashboard, exceto para blocos de relatório em tempo real e blocos de streaming. Confira mais informações em [Atualização de dados no Power BI (Atualização de bloco)](../connect-data/refresh-data.md#tile-refresh). Caso seu conjunto de armazenamento imponha a [RLS (Segurança em Nível de Linha)](../admin/service-admin-rls.md) dinâmica, entenda as implicações de desempenho, pois os blocos serão armazenados em cache por usuário.

Quando você fixa blocos de relatório em tempo real em um painel, eles não são alimentados a partir do cache de consulta. Em vez disso, eles se comportam como relatórios e consultam os núcleos de back-end em tempo real.

Como o nome sugere, a recuperação de dados do cache proporciona um desempenho melhor e mais consistente do que confiar na fonte de dados. Uma maneira de aproveitar essa funcionalidade é ter painéis como a primeira página de aterrissagem para seus usuários. Fixe os visuais usados com frequência e altamente solicitados aos dashboards. Dessa forma, os dashboards se tornam uma valiosa "primeira linha de defesa", que oferece um desempenho consistente sem sobrecarregar a capacidade. Os usuários ainda podem clicar no relatório para analisar os detalhes.

Para conjuntos de dados de conexão dinâmica e do DirectQuery, o cache é atualizado periodicamente ao consultar a fonte de dados. Por padrão, a atualização ocorre a cada hora, embora você possa configurar uma frequência diferente nas configurações do conjunto de dados. Cada atualização de cache envia as consultas à fonte de dados subjacente para atualizar o cache. O número de consultas geradas depende do número de visuais fixados nos dashboards que dependem dessa fonte de dados. Observe que se a segurança em nível de linha estiver habilitada, as consultas serão geradas para cada contexto de segurança diferente. Por exemplo, considere que haja duas funções diferentes que categorizem os usuários, com duas exibições diferentes dos dados. Durante a atualização do cache de consulta, o Power BI gera dois conjuntos de consultas.

### <a name="power-bi-reports"></a>Relatórios do Power BI

Existem várias recomendações para otimizar os designs de relatórios do Power BI.

> [!NOTE]
> Quando os relatórios são baseados em um conjunto de dados do DirectQuery, confira otimizações adicionais para o design de relatório em [Diretrizes sobre modelos do DirectQuery no Power BI Desktop (Otimizar designs de relatórios)](directquery-model-guidance.md#optimize-report-designs).

#### <a name="apply-the-most-restrictive-filters"></a>Aplicar os filtros mais restritivos

Quanto mais dados um visual precisar exibir, mais lentamente esse visual será carregado. Embora esse princípio pareça óbvio, é fácil esquecer. Por exemplo: suponha que você tenha um grande conjunto de dados. Sobre esse conjunto de dados, você cria um relatório com uma tabela. Os usuários finais usam segmentações na página para obter as linhas que desejam e, normalmente, só estão interessados em algumas dezenas de linhas.

Um erro comum é deixar o modo de exibição padrão da tabela sem filtro, ou seja, exibindo todas as mais de 100 milhões de linhas. Os dados dessas linhas são carregados na memória e descompactados a cada atualização. Esse processamento cria grandes demandas para a memória. A solução é usar o filtro "Os N principais" para reduzir o número máximo de itens que a tabela exibe. É possível definir o item máximo como maior do que o que usuários precisam, por exemplo, 10 mil. O resultado é que a experiência do usuário final não muda, mas o uso da memória cai muito. E o mais importante é que o desempenho melhora.

Uma abordagem de design semelhante à acima é recomendável para todos os visuais em seus relatórios. Pergunte-se: todos os dados neste visual são necessários? Existem maneiras de filtrar a quantidade de dados mostrados no visual com impacto mínimo na experiência do usuário final? Lembre-se de que as tabelas podem ser particularmente caras.

#### <a name="limit-visuals-on-report-pages"></a>Limitar visuais em páginas do relatório

O princípio acima aplica-se igualmente ao número de elementos visuais adicionados a uma página de relatório. Recomendamos limitar o número de elementos visuais de determinada página de relatório apenas ao que é necessário. [Detalhamento de páginas](report-drillthrough.md) e [Dicas de ferramentas de página de relatório](report-page-tooltips.md) são ótimas maneiras de fornecer detalhes adicionais sem aglomerar mais visuais na página.

#### <a name="evaluate-custom-visual-performance"></a>Avaliar o desempenho do visual personalizado

Coloque cada visual personalizado em execução para garantir alto desempenho. Visuais do Power BI otimizados de maneira precária podem afetar negativamente o desempenho de todo o relatório.

### <a name="power-bi-paginated-reports"></a>Relatórios paginados no Power BI

É possível otimizar os designs de relatórios paginados do Power BI ao aplicar no design a prática recomendada para a recuperação de dados do relatório. Para obter mais informações, confira [Diretrizes de recuperação de dados para relatórios paginados](report-paginated-data-retrieval.md).

Além disso, garanta que sua capacidade tenha memória suficiente alocada para a [carga de trabalho dos relatórios paginados](../admin/service-admin-premium-workloads.md#paginated-reports).

## <a name="optimizing-the-environment"></a>Otimizar o ambiente

É possível otimizar o ambiente do Power BI definindo as configurações de capacidade, dimensionando gateways de dados e reduzindo a latência da rede.

### <a name="capacity-settings"></a>Configurações de capacidade

Ao usar capacidades dedicadas, disponíveis com o Power BI Premium (P SKUs) ou com o Power BI Embedded (A SKUs, A4-A6), você pode gerenciar configurações de capacidade. Para obter mais informações, confira [Gerenciar capacidades Premium](../admin/service-premium-capacity-manage.md). Confira as diretrizes sobre como otimizar a capacidade em [Otimização de capacidades Premium](../admin/service-premium-capacity-optimize.md).

### <a name="gateway-sizing"></a>Dimensionamento de gateway

O gateway é necessário sempre que o Power BI precisa acessar dados que não estejam diretamente acessíveis pela Internet. Você pode instalar um [gateway de dados local](../connect-data/service-gateway-onprem.md) em um servidor local ou em uma IaaS (infraestrutura como serviço) hospedada em uma VM.

Para entender as recomendações de dimensionamento e cargas de trabalho de gateways, confira [Dimensionamento de gateway de dados local](gateway-onprem-sizing.md).

### <a name="network-latency"></a>Latência da rede

A latência de rede pode afetar o desempenho do relatório, aumentando o tempo necessário para que as solicitações acessem o serviço do Power BI e para que as respostas sejam entregues. Locatários no Power BI são atribuídos a uma região específica.

> [!TIP]
> Para determinar onde seu locatário está localizado, confira o artigo [Onde meu locatário do Power BI está localizado?](../admin/service-admin-where-is-my-tenant-located.md)

Quando os usuários de um locatário acessam o serviço do Power BI, suas solicitações sempre são roteadas para essa região. Quando as solicitações acessam o serviço do Power BI, o serviço pode enviar solicitações adicionais, por exemplo, para a fonte de dados subjacente ou o gateway de dados, que também estão sujeitos à latência de rede.

Ferramentas como o [Teste de Velocidade do Azure](https://azurespeedtest.azurewebsites.net/) fornecem uma indicação da latência de rede entre o cliente e a região do Azure. Em geral, para minimizar o impacto da latência de rede, empenhe-se para manter fontes de dados, gateways e o cluster do Power BI o mais próximo possível. Elas devem residir, de preferência, na mesma região. Se a latência de rede for um problema, tente localizar os gateways e as fontes de dados mais próximos do seu cluster do Power BI, colocando-os em máquinas virtuais hospedadas na nuvem.

## <a name="monitoring-performance"></a>Monitoramento de desempenho

Você pode monitorar o desempenho do servidor para identificar gargalos. Consultas ou visuais de relatório lentos devem ser um ponto focal de otimização contínua. O monitoramento pode ser feito no tempo de design no Power BI Desktop ou em cargas de trabalho de produção em capacidades do Power BI Premium. Confira mais informações em [Monitorar o desempenho de relatórios no Power BI](monitor-report-performance.md).

## <a name="next-steps"></a>Próximas etapas

Para obter mais informações sobre este artigo, confira os seguintes recursos:

- [Diretrizes do Power BI](index.yml)
- [Monitorar o desempenho de relatórios](monitor-report-performance.md)
- White paper: [Planejando uma implantação do Power BI Enterprise](https://go.microsoft.com/fwlink/?linkid=2057861)
- Dúvidas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
- Sugestões? [Contribuir com ideias para aprimorar o Power BI](https://ideas.powerbi.com/)




