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
ms.date: 08/21/2019
LocalizationGroup: Premium
ms.openlocfilehash: 2d2eb51c5aad44572f1b427248fd85ef19a6306f
ms.sourcegitcommit: e62889690073626d92cc73ff5ae26c71011e012e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/23/2019
ms.locfileid: "69985689"
---
# <a name="configure-workloads-in-a-premium-capacity"></a>Configurar cargas de trabalho em uma capacidade Premium

Este artigo descreve como habilitar e configurar cargas de trabalho para as capacidades Premium do Power BI. Por padrão, as capacidades dão suporte apenas à carga de trabalho associada à execução de consultas do Power BI. Habilite e configure também as cargas de trabalho adicionais para **[IA (Serviços Cognitivos)](service-cognitive-services.md)** , **[Fluxos de dados](service-dataflows-overview.md#dataflow-capabilities-on-power-bi-premium)** e **[Relatórios paginados](paginated-reports-save-to-power-bi-service.md)** .

## <a name="default-memory-settings"></a>Configurações de memória padrão

As cargas de trabalho de consulta são otimizadas para os recursos determinados pelo SKU da capacidade Premium e limitadas por esses recursos. As capacidades Premium também dão suporte a cargas de trabalho adicionais que podem usar seus recursos de capacidade. Os valores de memória padrão para essas cargas de trabalho se baseiam nos nós de capacidade disponíveis para o SKU. As configurações de memória máxima não são cumulativas. A memória até o valor máximo especificado é alocada dinamicamente para IA e fluxos de dados, mas é alocada estaticamente para relatórios paginados.

### <a name="microsoft-office-skus-for-software-as-a-service-saas-scenarios"></a>SKUs do Microsoft Office para cenários SaaS (Software como Serviço)

|                     | EM2                      | EM3                       | P1                      | P2                       | P3                       |
|---------------------|--------------------------|--------------------------|-------------------------|--------------------------|--------------------------|
| IA | Não aplicável | Não aplicável | 20% padrão; 20% mínimo | Padrão de 20%; mínimo de 10% | Padrão de 20%; mínimo de 5% |
| Fluxos de dados | Não aplicável |Padrão de 20%; mínimo de 12%  | Padrão de 20%; mínimo de 5%  | Padrão de 20%; mínimo de 3% | Padrão de 20%; mínimo de 2%  |
| Relatórios paginados | Não aplicável |Não aplicável | Padrão de 20%; mínimo de 10% | Padrão de 20%; mínimo de 5% | Padrão de 20%; mínimo de 2,5% |
| | | | | | |

### <a name="microsoft-azure-skus-for-platform-as-a-service-paas-scenarios"></a>SKUs do Microsoft Azure para cenários PaaS (Plataforma como Serviço)

|                  | A1                       | A2                       | A3                      | A4                       | A5                      | A6                        |
|-------------------|--------------------------|--------------------------|-------------------------|--------------------------|-------------------------|---------------------------|
| IA | Não aplicável                      | 20% padrão; 100% mínimo                     | 20% padrão; 50% mínimo                     | 20% padrão; 20% mínimo | Padrão de 20%; mínimo de 10% | Padrão de 20%; mínimo de 5% |
| Fluxos de dados         | Padrão de 40%; mínimo de 40% | Padrão de 24%; mínimo de 24% | Padrão de 20%; mínimo de 12% | Padrão de 20%; mínimo de 5%  | Padrão de 20%; mínimo de 3% | Padrão de 20%; mínimo de 2%   |
| Relatórios paginados | Não aplicável                      | Não aplicável                      | Não aplicável                     | Padrão de 20%; mínimo de 10% | Padrão de 20%; mínimo de 5% | Padrão de 20%; mínimo de 2,5% |
| | | | | | |

## <a name="workload-settings"></a>Configurações de carga de trabalho

### <a name="ai-preview"></a>IA (versão prévia)

A carga de trabalho de IA permite que você use serviços cognitivos e Machine Learning Automatizado no Power BI. Use as configurações a seguir para controlar o comportamento da carga de trabalho.

| Nome da Configuração | Descrição |
|---------------------------------|----------------------------------------|
| **Memória Máxima (%)** | O percentual máximo de memória disponível que os processos de IA podem usar em uma capacidade. |
| **Permitir o uso do Power BI Desktop** | Essa configuração é reservada para uso futuro e não é exibida em todos os locatários. |
| **Permitir a criação de modelos de machine learning** | Especifica se os analistas de negócios podem treinar, validar e invocar modelos de aprendizado de machine learning diretamente no Power BI. Confira mais informações em [Machine Learning Automatizado no Power BI (versão prévia)](service-machine-learning-automated.md). |
| **Habilitar paralelismo para solicitações de IA** | Especifica se as solicitações de IA podem ser executadas em paralelo. |
|  |  |

### <a name="datasets"></a>Conjuntos de dados

A carga de trabalho de conjuntos de dados está habilitada por padrão e não pode ser desabilitada. Use as configurações a seguir para controlar o comportamento da carga de trabalho.

| Nome da Configuração | Descrição |
|---------------------------------|----------------------------------------|
| **Memória Máxima (%)** | O percentual máximo de memória disponível que os conjuntos de dados podem usar em uma capacidade. |
| **Ponto de Extremidade XMLA** | Especifica que as conexões de aplicativos cliente respeitam o conjunto de associação do grupo de segurança nos níveis do workspace e do aplicativo. Para obter mais informações, confira [Conectar-se a conjuntos de dados com ferramentas e aplicativos cliente](service-premium-connect-tools.md). |
| **Contagem máxima de conjuntos de linhas intermediárias** | O número máximo de linhas intermediárias retornado por DirectQuery. O valor padrão é de 1.000.000 e o intervalo permitido é de 100.000 a 2.147.483.647. Use essa configuração para controlar o impacto de relatórios com uso intensivo de recursos ou mal designados. |
| **Tamanho máximo do conjunto de dados offline (GB)** | O tamanho máximo do conjunto de dados offline na memória. Esse é o tamanho compactado em disco. O valor padrão é definido pelo SKU e o intervalo permitido é de 0,1 a 10 GB. Use essa configuração para impedir que os criadores de relatório publiquem um grande conjunto de dados que possa afetar negativamente a capacidade. |
| **Contagem máxima do conjunto de linhas de resultado** | O número máximo de linhas retornadas em uma consulta DAX. O valor padrão é -1 (nenhum limite) e o intervalo permitido é de 100.000 a 214.7483.647. Use essa configuração para controlar o impacto de relatórios com uso intensivo de recursos ou mal designados. |
| **Limite de memória de consulta (%)** | O percentual máximo de memória disponível que pode ser usada para resultados temporários em uma consulta ou em uma medida DAX. Use essa configuração para controlar o impacto de relatórios com uso intensivo de recursos ou mal designados. |
| **Tempo limite da consulta (segundos)** | A quantidade máxima de tempo antes que uma consulta expire. O padrão é de 3.600 segundos (1 hora). Um valor de 0 especifica que as consultas não atingirão o tempo limite. Use essa configuração para manter um melhor controle de consultas de longa execução. |
|  |  |  |

### <a name="dataflows"></a>Fluxos de dados

A carga de trabalho de fluxos de dados permite que você use a preparação de dados de autoatendimento de fluxos de dados para ingerir, transformar, integrar e enriquecer dados. Use as configurações a seguir para controlar o comportamento da carga de trabalho.

| Nome da Configuração | Descrição |
|---------------------------------|----------------------------------------|
| **Memória Máxima (%)** | O percentual máximo de memória disponível que os fluxos de dados podem usar em uma capacidade. |
| **Mecanismo de computação de fluxos de dados aprimorado (versão prévia)** | Habilite esta opção para um cálculo até 20 vezes mais rápido de entidades computadas ao trabalhar com volumes de dados de grande escala. **Você deve reiniciar a capacidade para ativar o novo mecanismo.** Para obter mais informações, confira [Mecanismo de computação de fluxos de dados aprimorado](#enhanced-dataflows-compute-engine). |
| **Tamanho do Contêiner** | O tamanho máximo do contêiner que os fluxos de datas usam para cada entidade no fluxo de dados. O valor padrão é de 700 MB. Confira mais informações em [Tamanho do contêiner](#container-size). |
|  |  |

#### <a name="enhanced-dataflows-compute-engine"></a>Mecanismo de computação de fluxo de dados aprimorado

Para beneficiar-se do novo mecanismo de computação, divida a ingestão de dados em fluxos de dados separados e coloque a lógica de transformação em entidades computadas em diferentes fluxos de dados. Essa abordagem é recomendada porque o mecanismo de computação funciona em fluxos de dados que fazem referência a um fluxo de dados existente. Ela não funciona em fluxos de dados de ingestão. Seguir essas diretrizes garante que o novo mecanismo de computação processe as etapas de transformação, como junções e mesclagens, para um desempenho ideal.

#### <a name="container-size"></a>Tamanho do contêiner

Ao atualizar um fluxo de dados, a carga de trabalho do fluxo de dados gera um contêiner para cada entidade no fluxo de dados. Cada contêiner pode consumir memória até o volume especificado na configuração **Tamanho do Contêiner. O padrão para todas as SKUs é de 700 MB. Será conveniente alterar essa configuração se:

- Os fluxos de dados demorarem muito para atualizar ou a atualização do fluxo de dados falhar por atingir o tempo limite.
- As entidades de fluxo de dados incluírem etapas de computação, por exemplo, uma junção.  

É recomendável usar o aplicativo [Métricas de capacidade do Power BI Premium](service-admin-premium-monitor-capacity.md) para analisar o desempenho da carga de trabalho Fluxo de dados.

Em alguns casos, aumentar o tamanho do contêiner talvez não melhore o desempenho. Por exemplo, se o fluxo de dados estiver obtendo apenas dado de uma fonte sem executar cálculos significativos, alterar o tamanho do contêiner provavelmente não ajudará. Aumentar o tamanho do contêiner poderá ajudar se permitir que a carga de trabalho Fluxo de Dados aloque mais memória para operações de atualização de entidade. Com mais memória alocada, pode haver redução no tempo necessário para atualizar entidades intensamente computadas.

O valor Tamanho do Contêiner não pode exceder a memória máxima da carga de trabalho Fluxos de Dados. Por exemplo, uma capacidade P1 tem 25 GB de memória. Se a Memória Máx. (%) da carga de trabalho Fluxo de Dados estiver definida como 20%, o Tamanho do Contêiner (MB) não poderá exceder 5000. Em todos os casos, o Tamanho do Contêiner não poderá exceder a Memória Máx., mesmo se você definir um valor mais alto.

### <a name="paginated-reports"></a>Relatórios paginados

A carga de trabalho de relatórios paginados permite executar relatórios paginados com base no formato do SQL Server Reporting Services padrão no serviço do Power BI. Use a configuração a seguir para controlar o comportamento da carga de trabalho.

| Nome da Configuração | Descrição |
|---------------------------------|----------------------------------------|
| **Memória Máxima (%)** | O percentual máximo de memória disponível que os relatórios paginados podem usar em uma capacidade. |
|  |  |

Relatórios paginados permitem que o código personalizado seja executado ao renderizar um relatório. Por exemplo, alterar dinamicamente a cor do texto com base no conteúdo, que pode usar memória adicional. O Power BI Premium executa relatórios paginados em um espaço contido dentro da capacidade. A Memória Máx. especificada será usada *se* a carga de trabalho estiver ou não ativa. Se você alterar a configuração Memória Máx. de padrão, verifique se você a definiu como baixa o suficiente para não afetar negativamente outras cargas de trabalho.

Em alguns casos, a carga de trabalho de relatórios paginados pode ficar indisponível. Nesse caso, a carga de trabalho mostra um estado de erro no Portal de administração, e os usuários veem tempos limite para renderização de relatório. Para atenuar esse problema, desabilite a carga de trabalho e habilite-a novamente.

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