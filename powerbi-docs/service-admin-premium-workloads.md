---
title: Como configurar cargas de trabalho no Power BI Premium
description: Saiba como configurar cargas de trabalho em uma capacidade Premium do Power BI.
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/08/2020
LocalizationGroup: Premium
ms.openlocfilehash: a252c10b247ad5fc06565139bc69fc43a9add467
ms.sourcegitcommit: 81407c9ccadfa84837e07861876dff65d21667c7
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81267470"
---
# <a name="configure-workloads-in-a-premium-capacity"></a>Configurar cargas de trabalho em uma capacidade Premium

Este artigo descreve como habilitar e configurar cargas de trabalho para as capacidades Premium do Power BI. Por padrão, as capacidades dão suporte apenas à carga de trabalho associada à execução de consultas do Power BI. Habilite e configure também as cargas de trabalho adicionais para **[IA (Serviços Cognitivos)](service-cognitive-services.md)** , **[Fluxos de dados](service-dataflows-overview.md#dataflow-capabilities-on-power-bi-premium)** e **[Relatórios paginados](paginated-reports/paginated-reports-save-to-power-bi-service.md)** .

## <a name="default-memory-settings"></a>Configurações de memória padrão

As cargas de trabalho de consulta são otimizadas para os recursos determinados pelo SKU da capacidade Premium e limitadas por esses recursos. As capacidades Premium também dão suporte a cargas de trabalho adicionais que podem usar seus recursos de capacidade. Os valores de memória padrão para essas cargas de trabalho se baseiam nos nós de capacidade disponíveis para o SKU. As configurações de memória máxima não são cumulativas. A memória até o valor máximo especificado é alocada dinamicamente para IA e fluxos de dados, mas é alocada estaticamente para relatórios paginados.

|                   | EM1/A1                  | EM2/A2                  | EM3/A3                  | P1/A4                  | P2/A5                  | P3/A6                   |
|-------------------|---------------------------|---------------------------|---------------------------|--------------------------|--------------------------|---------------------------|
| IA                | Sem suporte               | Padrão de 40%; mínimo de 40%  | 20% padrão; 20% mínimo  | Padrão de 20%; mínimo de 8%  | Padrão de 20%; mínimo de 4%  | Padrão de 20%; mínimo de 2%   |
| Conjuntos de dados          | 100% padrão; 67% mínimo | 100% padrão; 40% mínimo | 100% padrão; 20% mínimo | 100% padrão; 8% mínimo | 100% padrão; 4% mínimo | 100% padrão; 2% mínimo  |
| Fluxos de dados         | Padrão de 40%; mínimo de 40%  | Padrão de 24%; mínimo de 24%  | Padrão de 20%; mínimo de 12%  | Padrão de 20%; mínimo de 5%  | Padrão de 20%; mínimo de 3%  | Padrão de 20%; mínimo de 2%   |
| Relatórios paginados | Sem suporte               | Sem suporte               | Sem suporte               | Padrão de 20%; mínimo de 10% | Padrão de 20%; mínimo de 5%  | Padrão de 20%; mínimo de 2,5% |
|                   |                           |                           |                           |                          |                          |                           |

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
| **Tamanho máximo do conjunto de dados offline (GB)** | O tamanho máximo do conjunto de dados offline na memória. Esse é o tamanho compactado em disco. O valor padrão é 0, que é o limite mais alto definido pelo SKU. O intervalo permitido está entre 0 e o limite de tamanho da capacidade. |
| **Contagem máxima do conjunto de linhas de resultado** | O número máximo de linhas retornadas em uma consulta DAX. O valor padrão é -1 (nenhum limite) e o intervalo permitido é de 100.000 a 214.7483.647. |
| **Limite de memória de consulta (%)** | A porcentagem máxima de memória disponível na carga de trabalho que pode ser usada para executar uma consulta MDX ou DAX. O valor padrão é 0, o que resulta na aplicação do limite de memória de consulta automática específico do SKU. |
| **Tempo limite da consulta (segundos)** | A quantidade máxima de tempo antes que uma consulta expire. O padrão é de 3.600 segundos (1 hora). Um valor de 0 especifica que as consultas não atingirão o tempo limite. |
| **Atualização automática de página (visualização)** | Botão de alternância para permitir que workspaces premium tenham relatórios com atualização automática de página. |
| **Intervalo mínimo de atualização** | Se a atualização automática de página estiver ativada, esse será o intervalo mínimo permitido para o intervalo de atualização de página. O valor padrão é cinco minutos, e o mínimo permitido é um segundo. |
|  |  |  |

#### <a name="max-intermediate-row-set-count"></a>Contagem Máxima de Conjuntos de Linhas Intermediárias

Use essa configuração para controlar o impacto de relatórios com uso intensivo de recursos ou mal designados. Quando uma consulta a um conjunto de dados do DirectQuery apresenta um resultado muito grande do banco de dados de origem, isso pode causar um pico no uso da memória e uma sobrecarga de processamento. Essa situação pode levar à insuficiência de recursos para outros usuários e relatórios. Essa configuração permite que o administrador de capacidade ajuste quantas linhas uma consulta individual pode buscar da fonte de dados.

Como alternativa, se a capacidade puder dar suporte a mais de um milhão de linhas por padrão e você tiver um conjunto de dados grande, aumente essa configuração para buscar mais linhas.

Observe que essa configuração afeta apenas as consultas do DirectQuery, enquanto a [Contagem Máxima de Conjuntos de Linhas de Resultado](#max-result-row-set-count) afeta as consultas DAX.

#### <a name="max-offline-dataset-size"></a>Tamanho Máximo do Conjunto de Dados Offline

Use essa configuração para impedir que os criadores de relatório publiquem um grande conjunto de dados que possa afetar negativamente a capacidade. Observe que o Power BI não pode determinar o tamanho real em memória até que o conjunto de dados seja carregado na memória. É possível que um conjunto de dados com um tamanho offline menor possa ter um volume de memória maior do que um conjunto de dados com um tamanho offline maior.

Se você tiver um conjunto de dados que seja maior que o tamanho especificado para essa configuração, o conjunto de dados falhará ao ser carregado quando um usuário tentar acessá-lo. O conjunto de dados também poderá falhar ao ser carregado se for maior do que a memória máxima configurada para a carga de trabalho dos conjuntos de dados.

Para proteger o desempenho do sistema, um limite rígido adicional específico do SKU para o tamanho máximo do conjunto de dados offline é aplicado, seja qual for o valor configurado. Esse limite rígido não se aplica aos conjuntos de dados do Power BI que são otimizados para tamanhos de dados grandes. Para obter mais informações, confira [Modelos grandes no Power BI Premium](service-premium-large-models.md).

|                                           | EM1/A1 | EM2/A2 | EM3/A3 | P1/A4 | P2/A5 | P3/A6 |   
|-------------------------------------------|----------|----------|----------|---------|---------|---------|
| Limite rígido de tamanho máximo do conjunto de dados offline | 3 GB     | 5 GB     | 6 GB     | 10 GB   | 10 GB   | 10 GB   |
|                                           |          |          |          |         |         |         |

#### <a name="max-result-row-set-count"></a>Contagem Máxima de Conjuntos de Linhas de Resultado

Use essa configuração para controlar o impacto de relatórios com uso intensivo de recursos ou mal designados. Se esse limite for atingido em uma consulta DAX, um usuário do relatório verá o erro a seguir. Ele deverá copiar os detalhes do erro e contatar um administrador.

![Não foi possível carregar os dados deste visual](media/service-admin-premium-workloads/could-not-load-data.png)

Observe que essa configuração afeta apenas as consultas DAX, enquanto a configuração [Contagem Máxima de Conjuntos de Linhas Intermediárias](#max-intermediate-row-set-count) afeta as consultas do DirectQuery.

#### <a name="query-memory-limit"></a>Limite de Memória de Consulta

Use essa configuração para controlar o impacto de relatórios com uso intensivo de recursos ou mal designados. Algumas consultas e alguns cálculos podem apresentar resultados intermediários que usam muita memória na capacidade. Essa situação pode fazer com que outras consultas sejam executadas muito lentamente, causar a remoção de outros conjuntos de dados da capacidade e levar erros de memória insuficiente para outros usuários da capacidade.

Essa configuração se aplica a todas as consultas DAX e MDX executadas por relatórios do Power BI, relatórios Analisar no Excel, bem como outras ferramentas que podem se conectar ao ponto de extremidade XMLA.

Observe que as operações de atualização de dados também podem executar consultas DAX como parte da atualização dos caches visuais e dos blocos do dashboard após a atualização dos dados no conjunto de dados. Essas consultas também podem falhar devido a essa configuração, o que pode causar a exibição da operação de atualização de dados em um estado de falha, mesmo que a atualização dos dados no conjunto de dados tenha ocorrido com êxito.

A configuração padrão é 0, o que resulta na aplicação do limite de memória de consulta automática específico do SKU a seguir.

|                              | EM1/A1 | EM2/A2 | EM3/A3 | P1/A4 | P2/A5 | P3/A6 |   
|------------------------------|----------|----------|----------|---------|---------|---------|
| Limite de memória de consulta automática | 1 GB     | 2 GB     | 2 GB     | 6 GB    | 6 GB    | 10 GB   |
|                              |          |          |          |         |         |         |

Para proteger o desempenho do sistema, um limite rígido de 10 GB é imposto a todas as consultas executadas por relatórios do Power BI, seja qual for o limite de memória de consulta configurado pelo usuário. Esse limite rígido não se aplica às consultas emitidas por ferramentas que usam o protocolo do Analysis Services (também conhecido como XMLA). Os usuários devem considerar a possibilidade de simplificar a consulta ou os cálculos, caso a consulta faça uso intensivo de memória.

#### <a name="query-timeout"></a>Tempo Limite da Consulta

Use essa configuração para manter um melhor controle das consultas de execução longa, o que pode fazer com que os relatórios sejam carregados lentamente para os usuários.

Essa configuração se aplica a todas as consultas DAX e MDX executadas por relatórios do Power BI, relatórios Analisar no Excel, bem como outras ferramentas que podem se conectar ao ponto de extremidade XMLA.

Observe que as operações de atualização de dados também podem executar consultas DAX como parte da atualização dos caches visuais e dos blocos do dashboard após a atualização dos dados no conjunto de dados. Essas consultas também podem falhar devido a essa configuração, o que pode causar a exibição da operação de atualização de dados em um estado de falha, mesmo que a atualização dos dados no conjunto de dados tenha ocorrido com êxito.

Essa configuração se aplica a uma única consulta e não ao tempo necessário para executar todas as consultas associadas à atualização de um conjunto de dados ou um relatório. Considere o seguinte exemplo:

- A configuração **Tempo Limite da Consulta** é 1.200 (20 minutos).
- Há cinco consultas a serem executadas, e cada uma delas é executada por 15 minutos.

O tempo combinado de todas as consultas é de 75 minutos, mas o limite de configuração não é atingido porque todas as consultas individuais são executadas em menos de 20 minutos.

Observe que os relatórios do Power BI substituem esse padrão com um tempo limite muito menor para cada consulta na capacidade. O tempo limite para cada consulta geralmente é de cerca de três minutos.

#### <a name="automatic-page-refresh-preview"></a>Atualização automática de página (visualização)

Quando habilitada, a atualização automática de página permite que os usuários da capacidade Premium atualizem páginas de relatórios em um intervalo definido nas fontes do DirectQuery. Como administrador de capacidade, você pode fazer o seguinte:

- Ativar e desativar a atualização automática de página
- Definir um intervalo mínimo de atualização

A imagem a seguir mostra o local da configuração do intervalo de atualização automática:

![configuração de administrador para intervalo de atualização automática](media/service-admin-premium-workloads/automatic-refresh-interval.png)

As consultas criadas pela atualização automática de página vão diretamente para a fonte de dados; portanto, é importante considerar a confiabilidade e carga dessas fontes ao permitir a atualização automática de página em sua organização. 

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

Ao atualizar um fluxo de dados, a carga de trabalho do fluxo de dados gera um contêiner para cada entidade no fluxo de dados. Cada contêiner pode consumir memória até o volume especificado na configuração Tamanho do Contêiner. O padrão para todas as SKUs é de 700 MB. Será conveniente alterar essa configuração se:

- Os fluxos de dados demorarem muito para atualizar ou a atualização do fluxo de dados falhar por atingir o tempo limite.
- As entidades de fluxo de dados incluírem etapas de computação, por exemplo, uma junção.  

É recomendável usar o aplicativo [Métricas de capacidade do Power BI Premium](service-admin-premium-monitor-capacity.md) para analisar o desempenho da carga de trabalho Fluxo de dados.

Em alguns casos, aumentar o tamanho do contêiner talvez não melhore o desempenho. Por exemplo, se o fluxo de dados estiver obtendo dados apenas de uma fonte sem fazer cálculos significativos, a alteração do tamanho do contêiner provavelmente não será útil. Aumentar o tamanho do contêiner poderá ajudar se permitir que a carga de trabalho Fluxo de Dados aloque mais memória para operações de atualização de entidade. Com mais memória alocada, pode haver redução no tempo necessário para atualizar entidades intensamente computadas.

O valor do Tamanho do Contêiner não pode exceder a memória máxima da carga de trabalho de Fluxos de Dados. Por exemplo, uma capacidade P1 tem 25 GB de memória. Se a Memória Máx. (%) da carga de trabalho Fluxo de Dados estiver definida como 20%, o Tamanho do Contêiner (MB) não poderá exceder 5000. Em todos os casos, o Tamanho do Contêiner não poderá exceder a Memória Máx., mesmo se você definir um valor mais alto.

### <a name="paginated-reports"></a>Relatórios paginados

A carga de trabalho de relatórios paginados permite executar relatórios paginados com base no formato do SQL Server Reporting Services padrão no serviço do Power BI. Use a configuração a seguir para controlar o comportamento da carga de trabalho.

| Nome da Configuração | Descrição |
|---------------------------------|----------------------------------------|
| **Memória Máxima (%)** | O percentual máximo de memória disponível que os relatórios paginados podem usar em uma capacidade. |
|  |  |

Os relatórios paginados oferecem os mesmos recursos que o SSRS (SQL Server Reporting Services) oferece hoje, incluindo a capacidade de autores de relatórios adicionarem código personalizado.  Isso permite que os autores alterem os relatórios dinamicamente, por exemplo, alterando as cores do texto com base em expressões de código.  Para garantir o isolamento adequado, os relatórios paginados são executados em uma área restrita protegida por capacidade. A execução de relatórios na mesma capacidade pode causar efeitos colaterais entre eles. Da mesma forma que você restringe os autores que podem publicar o conteúdo em uma instância do SSRS, recomendamos seguir uma prática semelhante com os relatórios paginados. Verifique se os autores que publicam conteúdo em uma capacidade são confiáveis para a organização. Você pode proteger ainda mais seu ambiente provisionando várias capacidades e atribuindo autores diferentes a cada uma delas. 

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

> [!IMPORTANT]
> Se a capacidade do Power BI Premium estiver enfrentando um alto uso de recursos, resultando em problemas de desempenho ou confiabilidade, você poderá receber emails de notificação para identificar e resolver o problema. Confira [Notificações de capacidade e confiabilidade](service-interruption-notifications.md#capacity-and-reliability-notifications) para obter mais informações.

## <a name="next-steps"></a>Próximas etapas

[Otimizar as capacidades do Power BI Premium](service-premium-capacity-optimize.md)     
[Preparação de dados de autoatendimento no Power BI com Fluxos de dados](service-dataflows-overview.md)   
[O que são relatórios paginados no Power BI Premium?](paginated-reports/paginated-reports-report-builder-power-bi.md)   
[Atualização automática de página no Power BI Desktop (visualização)](desktop-automatic-page-refresh.md)

Mais perguntas? [Perguntar à Comunidade do Power BI](https://community.powerbi.com/)
