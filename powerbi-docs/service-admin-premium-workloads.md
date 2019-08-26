---
title: Como configurar cargas de trabalho no Power BI Premium
description: Saiba como configurar cargas de trabalho em uma capacidade Premium do Power BI.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/15/2019
LocalizationGroup: Premium
ms.openlocfilehash: 49a1f02e5aa327c2704b6c2d789934a43b760ad0
ms.sourcegitcommit: 0e50ebfa8762e19286566432870ef16d242ac78f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68962026"
---
# <a name="configure-workloads-in-a-premium-capacity"></a>Configurar cargas de trabalho em uma capacidade Premium

Este artigo descreve como habilitar e configurar cargas de trabalho para as capacidades Premium do Power BI. Por padrão, as capacidades dão suporte apenas à carga de trabalho associada à execução de consultas do Power BI. Habilite e configure também as cargas de trabalho adicionais para **[IA (Serviços Cognitivos)](service-cognitive-services.md)**, **[Fluxos de dados](service-dataflows-overview.md#dataflow-capabilities-on-power-bi-premium)** e **[Relatórios paginados](paginated-reports-save-to-power-bi-service.md)**.

## <a name="default-memory-settings"></a>Configurações de memória padrão

As cargas de trabalho de consulta são otimizadas para os recursos determinados pelo SKU da capacidade Premium e limitadas por esses recursos. As capacidades Premium também dão suporte a cargas de trabalho adicionais que podem usar seus recursos de capacidade. Os valores de memória padrão para essas cargas de trabalho se baseiam nos nós de capacidade disponíveis para o SKU. As configurações de memória máxima não são cumulativas. A memória até o valor máximo especificado é alocada dinamicamente para IA e fluxos de dados, mas é alocada estaticamente para relatórios paginados.

### <a name="microsoft-office-skus-for-software-as-a-service-saas-scenarios"></a>SKUs do Microsoft Office para cenários SaaS (Software como Serviço)

|                     | EM2                      | EM3                       | P1                      | P2                       | P3                       |
|---------------------|--------------------------|--------------------------|-------------------------|--------------------------|--------------------------|
| IA | N/D | N/D | 20% padrão; 20% mínimo | Padrão de 20%; mínimo de 10% | Padrão de 20%; mínimo de 5% |
| Fluxos de dados | N/D |Padrão de 20%; mínimo de 12%  | Padrão de 20%; mínimo de 5%  | Padrão de 20%; mínimo de 3% | Padrão de 20%; mínimo de 2%  |
| Relatórios paginados | N/D |N/D | Padrão de 20%; mínimo de 10% | Padrão de 20%; mínimo de 5% | Padrão de 20%; mínimo de 2,5% |
| | | | | | |

### <a name="microsoft-azure-skus-for-platform-as-a-service-paas-scenarios"></a>SKUs do Microsoft Azure para cenários PaaS (Plataforma como Serviço)

|                  | A1                       | A2                       | A3                      | A4                       | A5                      | A6                        |
|-------------------|--------------------------|--------------------------|-------------------------|--------------------------|-------------------------|---------------------------|
| IA | N/D                      | 20% padrão; 100% mínimo                     | 20% padrão; 50% mínimo                     | 20% padrão; 20% mínimo | Padrão de 20%; mínimo de 10% | Padrão de 20%; mínimo de 5% |
| Fluxos de dados         | Padrão de 40%; mínimo de 40% | Padrão de 24%; mínimo de 24% | Padrão de 20%; mínimo de 12% | Padrão de 20%; mínimo de 5%  | Padrão de 20%; mínimo de 3% | Padrão de 20%; mínimo de 2%   |
| Relatórios paginados | N/D                      | Não aplicável                      | N/D                     | Padrão de 20%; mínimo de 10% | Padrão de 20%; mínimo de 5% | Padrão de 20%; mínimo de 2,5% |
| | | | | | |

## <a name="workload-settings"></a>Configurações de carga de trabalho

### <a name="ai-preview"></a>IA (versão prévia)

Além da configuração **Memória Máx.**, a carga de trabalho IA tem uma configuração adicional, **Permitir o uso de Power BI Desktop**. O padrão é **Desativado**. Essa configuração é reservada para uso futuro e talvez não seja exibida em todos os locatários.

### <a name="datasets-preview"></a>Conjuntos de dados (versão prévia)

Por padrão, a carga de trabalho Conjuntos de Dados é habilitada e não pode ser desabilitada. Essa carga de trabalho contém uma configuração adicional para o _ponto de extremidade XMLA_ e um conjunto de configurações relacionadas ao desempenho. Essa configuração de **Ponto de Extremidade XMLA** especifica que as conexões de aplicativos cliente respeitam o conjunto de associação do grupo de segurança nos níveis do workspace e do aplicativo. Para saber mais, confira [Conectar-se a conjuntos de dados com ferramentas e aplicativos cliente](service-premium-connect-tools.md).

As configurações relacionadas ao desempenho são descritas na tabela a seguir.

| Nome da Configuração | Descrição | Uso |
|---------------------------------|----------------------------------------|----------------------------------------|
| **Contagem máxima de conjuntos de linhas intermediárias** | O número máximo de linhas intermediárias retornado por DirectQuery. O valor padrão é definido como 1000000 e o intervalo permitido é entre 100000 e 2147483647 | Controle o impacto de relatórios com uso intensivo de recursos ou mal designados. |
| **Tamanho máximo do conjunto de dados offline (GB)** | Tamanho máximo do conjunto de dados offline na memória. Esse é o tamanho compactado em disco. O valor padrão é definido pelo SKU e o intervalo permitido é de 0,1 a 10 GB | Impeça que os criadores de relatório publiquem um grande conjunto de dados que possa afetar negativamente a capacidade. |
| **Contagem máxima do conjunto de linhas de resultado** | Define o número máximo de linhas retornadas em uma consulta DAX. O valor padrão é definido como -1 (nenhum limite) e o intervalo permitido é entre 100000 e 2147483647 | Controle o impacto de relatórios com uso intensivo de recursos ou mal designados. |
| **Limite de memória de consulta (%)** | Aplica-se somente a medidas e consultas DAX. Especificado em % e limita quanto de memória pode ser usado por resultados temporários durante uma consulta. | Controle o impacto de relatórios com uso intensivo de recursos ou mal designados. |
| **Tempo limite da consulta (segundos)** | Um inteiro que define o tempo limite, em segundos, para consultas. O padrão é 3.600 segundos (ou 60 minutos). 0 (zero) especifica que nenhuma consulta atingirá o tempo limite. | Mantenha melhor controle de consultas de longa execução. |
|  |  |  |

### <a name="dataflows"></a>Fluxos de dados

Além da configuração **Memória Máx.**, a carga de trabalho Fluxos de Dados tem uma configuração adicional, **Tamanho do contêiner**. Com essa configuração, você otimiza o desempenho da carga de trabalho de fluxo de dados para processar fluxos de dados mais complexos e com computação intensa.

Ao atualizar um fluxo de dados, a carga de trabalho do fluxo de dados gera um contêiner para cada entidade no fluxo de dados. Cada contêiner pode usar a memória até o volume especificado na configuração Tamanho do contêiner. O padrão para todos os SKUs é **700 MB**. Será conveniente alterar essa configuração se:

- Os fluxos de dados demorarem muito para atualizar ou a atualização do fluxo de dados falhar por atingir o tempo limite.
- As entidades de fluxo de dados incluírem etapas de computação, por exemplo, uma junção.  

É recomendável usar o aplicativo [Métricas de capacidade do Power BI Premium](service-admin-premium-monitor-capacity.md) para analisar o desempenho da carga de trabalho Fluxo de dados. 

Em alguns casos, aumentar o tamanho do contêiner talvez não melhore o desempenho. Por exemplo, se o fluxo de dados estiver obtendo apenas dado de uma fonte sem executar cálculos significativos, alterar o tamanho do contêiner provavelmente não ajudará. Aumentar o tamanho do contêiner poderá ajudar se permitir que a carga de trabalho Fluxo de Dados aloque mais memória para operações de atualização de entidade. Com mais memória alocada, pode haver redução no tempo necessário para atualizar entidades intensamente computadas.

O valor Tamanho do Contêiner não pode exceder a memória máxima da carga de trabalho Fluxos de Dados. Por exemplo, uma capacidade P1 tem 25 GB de memória. Se a Memória Máx. (%) da carga de trabalho Fluxo de Dados estiver definida como 20%, o Tamanho do Contêiner (MB) não poderá exceder 5000. Em todos os casos, o Tamanho do Contêiner não poderá exceder a Memória Máx., mesmo se você definir um valor mais alto.

### <a name="paginated-reports-preview"></a>Relatórios paginados (versão prévia)

Relatórios paginados permitem que o código personalizado seja executado ao renderizar um relatório. Por exemplo, alterar dinamicamente a cor do texto com base no conteúdo, que pode usar memória adicional. O Power BI Premium executa relatórios paginados em um espaço contido dentro da capacidade. A Memória Máx. especificada será usada *se* a carga de trabalho estiver ou não ativa. Se você alterar a configuração Memória Máx. de padrão, verifique se você a definiu como baixa o suficiente para não afetar negativamente outras cargas de trabalho.

Em alguns casos, a carga de trabalho Relatórios Paginados pode se tornar indisponível. Nesse caso, a carga de trabalho mostra um estado de erro no Portal de administração, e os usuários veem tempos limite para renderização de relatório. Para atenuar esse problema, desabilite a carga de trabalho e habilite-a novamente.

## <a name="configure-workloads"></a>Configurar cargas de trabalho

Maximize os recursos disponíveis da sua capacidade, habilitando as cargas de trabalho somente se elas forem usadas. Altere as configurações de memória e outras configurações apenas quando tiver determinado que as configurações padrão não estão atendendo aos requisitos de recursos de capacidade.

### <a name="to-configure-workloads-in-the-power-bi-admin-portal"></a>Para configurar cargas de trabalho no portal de administração do Power BI

1. Em **Configurações de capacidade** > **CAPACIDADES PREMIUM**, selecione uma capacidade.

1. Em **MAIS OPÇÕES**, expanda **Cargas de trabalho**.

1. Habilite uma ou mais cargas de trabalho e defina um valor para **Memória Máxima** e outras configurações.

1. Selecione **Aplicar**.

### <a name="rest-api"></a>API REST

As cargas de trabalho podem ser habilitadas e atribuídas a uma capacidade usando as APIs REST de [Capacidades](https://docs.microsoft.com/rest/api/power-bi/capacities).

## <a name="monitoring-workloads"></a>Monitoramento de cargas de trabalho

O [aplicativo de Métricas de capacidade do Power BI Premium](service-admin-premium-monitor-capacity.md) fornece o conjunto de dados, os fluxos de dados e as métricas de relatórios paginados para monitorar as cargas de trabalho habilitadas para suas capacidades. 

## <a name="next-steps"></a>Próximas etapas

[Otimizar as capacidades do Power BI Premium](service-premium-capacity-optimize.md)     
[Preparação de dados de autoatendimento no Power BI com Fluxos de dados](service-dataflows-overview.md)   
[O que são os relatórios paginados no Power BI Premium?](paginated-reports-report-builder-power-bi.md)   

Mais perguntas? [Perguntar à Comunidade do Power BI](http://community.powerbi.com/)