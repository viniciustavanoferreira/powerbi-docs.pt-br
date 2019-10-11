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
ms.openlocfilehash: a05924fc093c1514f51c3fabac3162433e2188f7
ms.sourcegitcommit: 9bf3cdcf5d8b8dd12aa1339b8910fcbc40f4cbe4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/05/2019
ms.locfileid: "71968883"
---
# <a name="configure-workloads-in-a-premium-capacity"></a>Configurar cargas de trabalho em uma capacidade Premium

Este artigo descreve como habilitar e configurar cargas de trabalho para as capacidades Premium do Power BI. Por padrão, as capacidades dão suporte apenas à carga de trabalho associada à execução de consultas do Power BI. Habilite e configure também as cargas de trabalho adicionais para **[IA (Serviços Cognitivos)](service-cognitive-services.md)** , **[Fluxos de dados](service-dataflows-overview.md#dataflow-capabilities-on-power-bi-premium)** e **[Relatórios paginados](paginated-reports-save-to-power-bi-service.md)** .

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

A carga de trabalho de IA permite que você use serviços cognitivos e Machine Learning Automatizado no Power BI. Use as configurações a seguir para controlar o comportamento da carga de trabalho.

| Nome da Configuração | Descrição |
|---------------------------------|----------------------------------------|
| **Memória Máxima (%)** | O percentual máximo de memória disponível que os processos de IA podem usar em uma capacidade. |
| **Permitir o uso do Power BI Desktop** | Essa configuração é reservada para uso futuro e não é exibida em todos os locatários. |
| **Permitir a criação de modelos de machine learning** | Especifica se os analistas de negócios podem treinar, validar e invocar modelos de aprendizado de machine learning diretamente no Power BI. Confira mais informações em [Machine Learning Automatizado no Power BI (versão prévia)](service-machine-learning-automated.md). |
| **Habilitar paralelismo para solicitações de IA** | Especifica se as solicitações de IA podem ser executadas em paralelo. |
|  |  |

### <a name="datasets"></a>Conjuntos de dados

A carga de trabalho de conjuntos de dados está habilitada por padrão e não pode ser desabilitada. Use as configurações a seguir para controlar o comportamento da carga de trabalho. Há informações de uso adicionais abaixo da tabela para algumas das configurações.

| Nome da Configuração | Descrição |
|---------------------------------|----------------------------------------|
| **Memória Máxima (%)** | O percentual máximo de memória disponível que os conjuntos de dados podem usar em uma capacidade. |
| **Ponto de Extremidade XMLA** | Especifica que as conexões de aplicativos cliente respeitam o conjunto de associação do grupo de segurança nos níveis do workspace e do aplicativo. Para obter mais informações, confira [Conectar-se a conjuntos de dados com ferramentas e aplicativos cliente](service-premium-connect-tools.md). |
| **Contagem máxima de conjuntos de linhas intermediárias** | O número máximo de linhas intermediárias retornado por DirectQuery. O valor padrão é de 1.000.000 e o intervalo permitido é de 100.000 a 2.147.483.647. |
| **Tamanho máximo do conjunto de dados offline (GB)** | O tamanho máximo do conjunto de dados offline na memória. Esse é o tamanho compactado em disco. O valor padrão é definido pelo SKU e o intervalo permitido é de 0,1 a 10 GB. |
| **Contagem máxima do conjunto de linhas de resultado** | O número máximo de linhas retornadas em uma consulta DAX. O valor padrão é -1 (nenhum limite) e o intervalo permitido é de 100.000 a 214.7483.647. |
| **Limite de memória de consulta (%)** | O percentual máximo de memória disponível que pode ser usada para resultados temporários em uma consulta ou em uma medida DAX. |
| **Tempo limite da consulta (segundos)** | A quantidade máxima de tempo antes que uma consulta expire. O padrão é de 3.600 segundos (1 hora). Um valor de 0 especifica que as consultas não atingirão o tempo limite. |
|  |  |  |

#### <a name="max-intermediate-row-set-count"></a>Contagem Máxima de Conjuntos de Linhas Intermediárias

Use essa configuração para controlar o impacto de relatórios com uso intensivo de recursos ou mal designados. Quando uma consulta a um conjunto de dados do DirectQuery apresenta um resultado muito grande do banco de dados de origem, isso pode causar um pico no uso da memória e uma sobrecarga de processamento. Essa situação pode levar à insuficiência de recursos para outros usuários e relatórios. Essa configuração permite que o administrador de capacidade ajuste quantas linhas uma consulta individual pode buscar da fonte de dados.

Como alternativa, se a capacidade puder dar suporte a mais de um milhão de linhas por padrão e você tiver um conjunto de dados grande, aumente essa configuração para buscar mais linhas.

Observe que essa configuração afeta apenas as consultas do DirectQuery, enquanto a [Contagem Máxima de Conjuntos de Linhas de Resultado](#max-result-row-set-count) afeta as consultas DAX.

#### <a name="max-offline-dataset-size"></a>Tamanho Máximo do Conjunto de Dados Offline

Use essa configuração para impedir que os criadores de relatório publiquem um grande conjunto de dados que possa afetar negativamente a capacidade. Observe que o Power BI não pode determinar o tamanho real em memória até que o conjunto de dados seja carregado na memória. É possível que um conjunto de dados com um tamanho offline menor possa ter um volume de memória maior do que um conjunto de dados com um tamanho offline maior.

Se você tiver um conjunto de dados que seja maior que o tamanho especificado para essa configuração, o conjunto de dados falhará ao ser carregado quando um usuário tentar acessá-lo.

#### <a name="max-result-row-set-count"></a>Contagem Máxima de Conjuntos de Linhas de Resultado

Use essa configuração para controlar o impacto de relatórios com uso intensivo de recursos ou mal designados. Se esse limite for atingido em uma consulta DAX, um usuário do relatório verá o erro a seguir. Ele deverá copiar os detalhes do erro e contatar um administrador.

![Não foi possível carregar os dados deste visual](media/service-admin-premium-workloads/could-not-load-data.png)

Observe que essa configuração afeta apenas as consultas DAX, enquanto a configuração [Contagem Máxima de Conjuntos de Linhas Intermediárias](#max-intermediate-row-set-count) afeta as consultas do DirectQuery.

#### <a name="query-memory-limit"></a>Limite de Memória de Consulta

Use essa configuração para controlar o impacto de relatórios com uso intensivo de recursos ou mal designados. Algumas consultas e alguns cálculos podem apresentar resultados intermediários que usam muita memória na capacidade. Essa situação pode fazer com que outras consultas sejam executadas muito lentamente, causar a remoção de outros conjuntos de dados da capacidade e levar erros de memória insuficiente para outros usuários da capacidade.

Essa configuração se aplica à atualização de dados e à renderização de relatório. A atualização de dados executa a atualização de dados da fonte de dados e a atualização de consulta, a menos que a atualização de consulta esteja desabilitada. Se a atualização de consulta não estiver desabilitada, esse limite de memória também se aplicará a essas consultas. As consultas com falha fazem com que o estado de atualização agendada seja relatado como uma falha, mesmo que a atualização de dados tenha sido bem-sucedida.

#### <a name="query-timeout"></a>Tempo Limite da Consulta

Use essa configuração para manter um melhor controle das consultas de execução longa, o que pode fazer com que os relatórios sejam carregados lentamente para os usuários. Essa configuração se aplica à atualização de dados e à renderização de relatório. A atualização de dados executa a atualização de dados da fonte de dados e a atualização de consulta, a menos que a atualização de consulta esteja desabilitada. Se a atualização de consulta não estiver desabilitada, essa limitação de tempo limite também se aplicará a essas consultas.

Essa configuração se aplica a uma única consulta e não ao tempo necessário para executar todas as consultas associadas à atualização de um conjunto de dados ou um relatório. Considere o seguinte exemplo:

- A configuração **Tempo Limite da Consulta** é 1.200 (20 minutos).
- Há cinco consultas a serem executadas, e cada uma delas é executada por 15 minutos.

O tempo combinado de todas as consultas é de 75 minutos, mas o limite de configuração não é atingido porque todas as consultas individuais são executadas em menos de 20 minutos.

Observe que os relatórios do Power BI substituem esse padrão com um tempo limite muito menor para cada consulta na capacidade. O tempo limite para cada consulta geralmente é de cerca de três minutos.

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