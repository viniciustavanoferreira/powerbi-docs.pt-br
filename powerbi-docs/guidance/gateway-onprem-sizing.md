---
title: Dimensionamento de gateway de dados local
description: Orientação para trabalhar com o dimensionamento do gateway de dados local.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 12/30/2019
ms.author: v-pemyer
ms.openlocfilehash: 4f289bf319bf29de8f8765d55bf3400048420af5
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/05/2020
ms.locfileid: "76829042"
---
# <a name="on-premises-data-gateway-sizing"></a>Dimensionamento de gateway de dados local

Este artigo se destina aos administradores do Power BI que precisam instalar e gerenciar o [gateway de dados local](../service-gateway-onprem.md).

O gateway é necessário sempre que o Power BI precisa acessar dados que não estão acessíveis diretamente pela Internet. Ele pode ser instalado em um servidor local ou em uma IaaS (infraestrutura como serviço) hospedada pela VM.

## <a name="gateway-workloads"></a>Cargas de trabalho do gateway

O gateway de dados local dá suporte a duas cargas de trabalho. É importante que você entenda primeiro essas cargas de trabalho antes de discutirmos o dimensionamento e as recomendações do gateway.

### <a name="cached-data-workload"></a>Carga de trabalho de dados armazenados em cache

A carga de trabalho de _dados armazenados em cache_ recupera e transforma os dados de origem para carregá-los em conjuntos de dados do Power BI. Ela faz isso em três etapas:

1. **Conexão**: o gateway se conecta aos dados de origem
1. **Recuperação de dados e transformação**: os dados são recuperados e, quando necessário, são transformados. Sempre que possível, o mecanismo de mashup do Power Query envia as etapas de transformação para a fonte de dados – isso é conhecido como _[dobragem de consultas](power-query-folding.md)_ . Quando isso não é possível, as transformações devem ser feitas pelo gateway. Nesse caso, o gateway consumirá mais recursos de CPU e memória.
1. **Transferência**: os dados são transferidos para o serviço do Power BI – uma conexão de Internet confiável e rápida é importante, especialmente para grandes volumes de dados

![O diagrama exibe o gateway de dados local conectando-se a fontes locais: banco de dados relacional, pasta de trabalho do Excel e arquivos CSV. O gateway recupera e transforma os dados.](media/gateway-onprem-sizing/gateway-onprem-workload-cached-data.png)

### <a name="live-connection-and-directquery-workloads"></a>Cargas de trabalho de Conexão Dinâmica e DirectQuery

As cargas de trabalho de _Conexão Dinâmica e DirectQuery_ funcionam principalmente no modo de passagem. O serviço do Power BI envia consultas, e o gateway responde com os resultados da consulta. Em geral, os resultados da consulta têm um tamanho pequeno.

- Para obter mais informações sobre a Conexão Dinâmica, confira [Conjuntos de dados no serviço do Power BI (modelos hospedados externamente)](../service-datasets-understand.md#external-hosted-models).
- Para obter mais informações sobre o DirectQuery, confira [Modos de conjunto de dados no serviço do Power BI (modo DirectQuery)](../service-dataset-modes-understand.md#directquery-mode).

Essa carga de trabalho requer recursos de CPU para roteamento e resultados de consultas. Geralmente, há uma demanda muito menor por CPU do que a exigida pela carga de trabalho de dados de cache, especialmente quando é necessário transformar dados para armazenamento em cache.

Uma conectividade confiável, rápida e consistente é importante para garantir que os usuários de relatórios tenham experiências dinâmicas.

![O diagrama exibe o gateway de dados local conectando-se a fontes locais: Banco de dados tabular e relacional do Analysis Services. O gateway funciona principalmente no modo de passagem.](media/gateway-onprem-sizing/gateway-onprem-workload-liveconnection-directquery.png)

## <a name="sizing-considerations"></a>Considerações de dimensionamento

Determinar o dimensionamento correto para o computador de gateway pode depender das seguintes variáveis:

- Para cargas de trabalho de dados de cache:
  - O número de atualizações de conjunto de dados simultâneos
  - Os tipos de fontes de dados (banco de dados relacional, banco de dados analítico, feeds de dados ou arquivos)
  - O volume de dados a ser recuperado das fontes de dados
  - As transformações necessárias a serem feitas pelo mecanismo de mashup do Power Query
  - O volume de dados a ser transferido para o serviço do Power BI
- Para cargas de trabalho de Conexão Dinâmica e DirectQuery:
  - O número de usuários de relatórios simultâneos
  - O número de visuais nas páginas de relatório (cada visual envia pelo menos uma consulta)
  - A frequência de atualizações do cache de consulta do dashboard do Power BI
  - O número de relatórios em tempo real que usam o recurso de [Atualização automática de página](../desktop-automatic-page-refresh.md)
  - Se os conjuntos de dados impõem a [RLS (segurança em nível de linha)](../desktop-rls.md)

Geralmente, as cargas de trabalho de Conexão Dinâmica e DirectQuery exigem recursos suficientes de CPU, enquanto as cargas de trabalho de dados de cache exigem mais recursos de CPU e memória. Ambas as cargas de trabalho dependem de uma boa conectividade com o serviço do Power BI e com as fontes de dados.

> [!NOTE]
> As capacidades do Power BI impõem limites quanto ao paralelismo de atualização do modelo e à taxa de transferência de Conexão Dinâmica e DirectQuery. Não faz sentido dimensionar seus gateways para oferecer mais do que o serviço do Power BI suporta. Os limites diferem na SKU Premium (e na SKU A de tamanho equivalente). Para obter mais informações, confira [O que é Power BI Premium? (Nós de Capacidade)](../service-premium-what-is.md#capacity-nodes).

## <a name="recommendations"></a>Recomendações

As recomendações de dimensionamento de gateway dependem de muitas variáveis. Nesta seção, fornecemos recomendações gerais que você pode levar em consideração.

### <a name="initial-sizing"></a>Dimensionamento inicial

Pode ser difícil estimar com precisão o tamanho correto. Recomendamos que você inicie com um computador com pelo menos 8 núcleos de CPU, 8 GB de RAM e vários adaptadores de rede Gigabit. Em seguida, você pode medir uma carga de trabalho de gateway típica registrando contadores de sistema de CPU e memória. Para obter mais informações, confira [Monitorar e otimizar o desempenho do gateway de dados local](/data-integration/gateway/service-gateway-performance).

### <a name="connectivity"></a>Conectividade

Planeje a melhor conectividade possível entre o serviço do Power BI e o gateway e entre o gateway e as fontes de dados.

- Busque por confiabilidade, velocidades rápidas e latências baixas e consistentes
- Elimine ou reduza saltos de máquina entre o gateway e suas fontes de dados
- Remova qualquer limitação imposta pela camada de proxy do firewall. Para obter mais informações sobre pontos de extremidade do Power BI, confira [URLs do Power BI para a lista de permissões](../power-bi-whitelist-urls.md).
- Configure o [Azure ExpressRoute](/azure/expressroute/expressroute-introduction) para estabelecer uma conexão privada e gerenciada no Power BI
- Para fontes de dados em VMs do Azure, verifique se as VMs estão [colocadas com o serviço do Power BI](../service-admin-where-is-my-tenant-located.md)
- Para cargas de trabalho de Conexão Dinâmica para SSAS (SQL Server Analysis Services) envolvendo a RLS dinâmica, garanta uma boa conectividade entre o computador do gateway e o Active Directory local

### <a name="clustering"></a>Clustering

Para implantações em larga escala, você pode criar um gateway de instalações de clusters. Os clusters evitam pontos únicos de falha e podem balancear a carga do tráfego entre gateways. Você pode:

- Instalar um ou mais gateways em um cluster
- Isolar cargas de trabalho para gateways autônomos ou clusters de servidores de gateway

Para obter mais informações, confira [Gerenciar clusters de alta disponibilidade e balanceamento de carga do gateway de dados local](/data-integration/gateway/service-gateway-high-availability-clusters).

### <a name="dataset-design-and-settings"></a>Design e configurações do conjunto de dados

O design do conjunto de dados e suas configurações podem impactar as cargas de trabalho do gateway. Para reduzir a carga de trabalho do gateway, você pode considerar as seguintes ações.

Para Conjuntos de dados de importação:

- Configure a atualização de dados menos frequente
- Configure a [atualização incremental](../service-premium-incremental-refresh.md) para minimizar a quantidade de dados a serem transferidos
- Sempre que possível, verifique se ocorre a [dobragem de consultas](power-query-folding.md)
- Especialmente para grandes volumes de dados ou para a necessidade de resultados de baixa latência, converta o design em um modelo DirectQuery ou [composto](../service-dataset-modes-understand.md#composite-mode)

Para conjunto de dados DirectQuery:

- Otimize o design de fontes de dados, modelos e relatórios – para obter mais informações, confira [Diretrizes sobre modelos de DirectQuery no Power BI Desktop](directquery-model-guidance.md)
- Crie [agregações](../desktop-aggregations.md) para armazenar em cache resultados de nível superior reduzindo o número de solicitações DirectQuery
- Restrinja os intervalos de [Atualização automática de página](../desktop-automatic-page-refresh.md), em designs de relatórios e configurações de capacidade
- Em especial, quando a RLS dinâmica for imposta, restrinja a frequência de atualização do cache do dashboard
- Especialmente para volumes de dados menores ou para dados não voláteis, converta o design para um modelo [composto](../service-dataset-modes-understand.md#composite-mode) ou de importação

Para conjunto de dados de Conexão Dinâmica:

- Em especial, quando a RLS dinâmica for imposta, restrinja a frequência de atualização do cache do dashboard

## <a name="next-steps"></a>Próximas etapas

Para obter mais informações relacionadas a este artigo, confira os seguintes recursos:

- [Diretrizes para implantar um gateway de dados para o Power BI](../service-gateway-deployment-guidance.md)
- [Definir as configurações de proxy do gateway de dados local](/data-integration/gateway/service-gateway-proxy)
- [Monitorar e otimizar o desempenho do gateway de dados local](/data-integration/gateway/service-gateway-performance)
- [Solucionar problemas de gateways – Power BI](../service-gateway-onprem-tshoot.md)
- [Solucionar problemas do gateway de dados local](/data-integration/gateway/service-gateway-tshoot)
- [A importância da dobragem de consultas](power-query-folding.md)
- Dúvidas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
- Sugestões? [Contribuir com ideias para aprimorar o Power BI](https://ideas.powerbi.com)
