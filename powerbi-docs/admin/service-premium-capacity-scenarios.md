---
title: Cenários de capacidade do Microsoft Power BI Premium
description: Descreve cenários comuns de capacidade do Power BI Premium.
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/09/2019
ms.custom: seodec18
LocalizationGroup: Premium
ms.openlocfilehash: 9b3e06172d29f218f9234cf1f3d7e1f623495001
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83135316"
---
# <a name="premium-capacity-scenarios"></a>Cenários de capacidade Premium

Este artigo descreve os cenários do mundo real em que capacidades do Power BI Premium foram implementadas. São descritos problemas e desafios comuns e também como identificar problemas e ajudar a resolvê-los:

- [Como manter os conjuntos de dados atualizados](#keeping-datasets-up-to-date)
- [Como identificar conjuntos de dados com resposta lenta](#identifying-slow-responding-datasets)
- [Como identificar as causas de conjuntos de dados que esporadicamente têm resposta lenta](#identifying-causes-for-sporadically-slow-responding-datasets)
- [Como determinar se há memória suficiente](#determining-whether-there-is-enough-memory)
- [Como determinar se há CPU suficiente](#determining-whether-there-is-enough-cpu)

As etapas, juntamente com os exemplos de gráfico e tabela, são do **aplicativo Métricas de Capacidade do Power BI Premium** ao qual um administrador do Power BI tem acesso.

## <a name="keeping-datasets-up-to-date"></a>Como manter os conjuntos de dados atualizados

Nesse cenário, uma investigação foi disparada quando os usuários reclamaram que os dados de relatório às vezes pareciam ser antigos ou "obsoletos".

No aplicativo, o administrador interage com o visual **Atualiza**, classificando conjuntos de dados pelas estatísticas de **Tempo de Espera Máximo** em ordem decrescente. Esse visual os ajuda a revelar conjuntos de dados com os tempos de espera mais longos, agrupados por nome do workspace.

![Atualizações do conjunto de dados classificadas por tempo de espera máximo decrescente, agrupadas por workspace](media/service-premium-capacity-scenarios/dataset-refreshes.png)

No visual **Tempos de Espera de Atualização Médios por Hora**, eles observam que os tempos de espera de atualização consistentemente atingem o pico por volta das 16h todos os dias.

![Esperas de atualização atingem o pico periodicamente às 16h](media/service-premium-capacity-scenarios/peak-refresh-waits.png)

Há várias explicações possíveis para esses resultados:

- Muitas tentativas de atualização podem estar ocorrendo ao mesmo tempo, excedendo os limites definidos pelo nó de capacidade. Nesse caso, seis atualizações simultâneas em um P1 com alocação de memória padrão.

- Os conjuntos de valores a serem atualizados podem ser muito grandes para a memória disponível (exigindo pelo menos 2x a memória necessária para a atualização completa).
- Uma lógica ineficiente do Power Query pode estar resultando em um pico de uso de memória durante a atualização do conjunto de resultados. Em uma capacidade ocupada, esse pico ocasionalmente pode chegar ao limite físico, falhando na atualização e potencialmente afetando outras operações de exibição de relatório na capacidade.
- Os conjuntos de linhas consultados com frequência que precisam permanecer na memória podem afetar a capacidade de atualização de outros conjuntos de valores devido à memória disponível limitada.

Para ajudar a investigar, o administrador do Power BI pode procurar:

- Baixa memória disponível no momento em que os dados são atualizados quando a memória disponível é menor do que o dobro do tamanho do conjunto de dados a ser atualizado.
- Os conjuntos de valores não estão sendo atualizados e não estão na memória antes da atualização, mas foram iniciados para mostrar o tráfego interativo durante os horários de atualização pesada. Para ver quais conjuntos de dados são carregados na memória a qualquer momento, um administrador do Power BI pode examinar a área de conjuntos de dados da guia **Conjuntos de Dados** no aplicativo. O administrador pode fazer uma filtragem cruzada para um determinado momento clicando em uma das barras em **Contagens do Conjuntos de Dados Carregados por Hora**. Um pico local, mostrado na imagem abaixo, indica uma hora em que vários conjuntos de valores foram carregados na memória, o que poderia atrasar o início das atualizações agendadas.
- Ocorrência de mais remoções de conjunto de dados no momento em que as atualizações estão agendadas para começar. As remoções podem indicar que houve uma alta pressão de memória causada pelo fornecimento de muitos relatórios interativos diferentes antes do momento da atualização. O visual **Remoções de Conjunto de Dados por Hora e Consumo de Memória** pode indicar claramente picos de remoções.

A imagem a seguir mostra um pico local nos conjuntos de dados carregados, o que sugere um início atrasado de atualizações da consulta interativa. A seleção de um período no visual **Contagens de Conjunto de Dados Carregados por Hora** fará a filtragem cruzada do visual **Tamanhos do Conjunto de Dados**.

![Um pico local em conjuntos de dados carregados sugere o início atrasado de atualizações da consulta interativas](media/service-premium-capacity-scenarios/hourly-loaded-dataset-counts.png)

O administrador do Power BI pode tentar resolver o problema executando etapas para garantir que memória suficiente esteja disponível para atualizações de dados serem iniciadas das seguintes maneiras:

- Contatando os proprietários do conjunto de dados e pedindo que escalonem e espacem os agendamentos de atualização.
- Reduzindo a carga de consulta do conjunto de dados removendo dashboards desnecessários ou blocos de dashboards, especialmente aqueles que impõem a segurança em nível de linha.
- Acelerando as atualizações de dados otimizando a lógica do Power Query. Melhore a modelagem de colunas calculadas ou tabelas. Reduza os tamanhos dos conjuntos de dados ou configure conjunto de dados maiores para executar a atualização incremental.

## <a name="identifying-slow-responding-datasets"></a>Como identificar conjuntos de dados com resposta lenta

Nesse cenário, uma investigação começou quando os usuários reclamaram que determinados relatórios levaram muito tempo para abrir e, às vezes, travavam.

No aplicativo, o administrador do Power BI pode usar o visual **Durações de Consulta** para determinar os conjuntos de dados de pior desempenho, classificando conjuntos de dados por **Duração Média** decrescente. Esse visual também mostra contagens de consulta do conjunto de dados, assim, você pode ver com que frequência os conjuntos de dados são consultados.

![Conjuntos de dados com pior desempenho](media/service-premium-capacity-scenarios/worst-performing-datasets.png)

O administrador pode consultar o visual **Distribuição da Duração da Consulta**, que mostra uma distribuição geral do desempenho de consulta classificado (<=30 ms, 0 a 100 ms) para o período de tempo filtrado. Geralmente, as consultas que levam um segundo ou menos são consideradas responsivas pela maioria dos usuários; as consultas que demoram mais tendem a criar uma percepção do mau desempenho.

O visual **Distribuição da Duração de Consulta por Hora** permite que o administrador do Power BI identifique períodos de uma hora quando o desempenho da capacidade pode ter sido percebido como insatisfatório. Quanto maiores os segmentos de barras que representam durações de consulta em um segundo, maior será o risco de que os usuários percebam o desempenho como insatisfatório.

O visual é interativo e, quando um segmento da barra é selecionado, o visual da tabela **Durações de Consulta** correspondentes na página do relatório é filtrado de modo cruzado para mostrar os conjuntos de dados que ele representa. Essa filtragem cruzada permite que o administrador do Power BI identifique facilmente quais conjuntos de dados estão respondendo lentamente.

A imagem a seguir mostra um visual filtrado por **Distribuições de Duração de Consulta por Hora**, concentrando-se nos conjuntos de dados de pior desempenho em buckets de uma hora. 

![O visual de Distribuições de Duração de Consulta Filtradas por Hora mostra os conjuntos de dados de pior desempenho](media/service-premium-capacity-scenarios/hourly-query-duration-distributions.png)

Quando o conjunto de dados de baixa desempenho em um período específico de uma hora é identificado, o administrador do Power BI pode investigar se o baixo desempenho é causado por uma capacidade sobrecarregada ou devido a um relatório ou conjunto de dados mal projetado. Eles podem consultar o visual **Tempos de Espera de Consulta** e classificar os conjuntos de dados por tempo médio de espera de consulta. Se um percentual grande de consultas estiver aguardando, uma demanda alta para o conjunto de dados provavelmente será a causa de muitas esperas de consulta. Se o tempo médio de espera da consulta for significativo (>100 ms), poderá valer a pena analisar o conjunto de relatórios e o relatório para ver se podem ser feitas otimizações. Por exemplo, menos visuais em determinadas páginas de relatório ou uma otimização da expressão DAX.

![O visual Tempos de Espera da Consulta ajuda a revelar conjuntos de dados com mau desempenho](media/service-premium-capacity-scenarios/query-wait-times.png)

Há vários motivos possíveis para o acúmulo de tempo de espera de consulta em conjuntos de dados:

- Design de modelo, expressões de medida ou até mesmo design de relatório não ideais são fatores que podem contribuir para consultas de execução prolongada que consomem níveis elevados de CPU. Isso força novas consultas a aguardar até que os threads de CPU fiquem disponíveis e possam criar um efeito de comboio (pense em um congestionamento de trânsito), normalmente observado durante o pico do horário comercial. A página **Esperas de Consulta** será o recurso principal para determinar se os conjuntos de dados têm tempos de espera médios de consulta.
- Um alto número de usuários de capacidade simultâneos (centenas a milhares) consumindo o mesmo relatório ou conjunto de dados. Até mesmo conjuntos de dados bem projetados podem ter um mau desempenho além de um limite de simultaneidade. Isso geralmente é indicado por um único conjunto de dados mostrando um valor drasticamente maior para contagens de consulta do que outros conjuntos de dados (por exemplo, 300 mil consultas para um conjunto de dados em comparação a <30 mil para todos os outros). Em algum momento, as esperas de consulta para esse conjunto de dados começarão a falhar, o que pode ser visto no visual **Durações da Consulta**.
- Muitos conjuntos de dados diferentes consultados ao mesmo tempo, causando ultrapaginação, uma vez que os conjuntos de valores frequentemente alternam entre ficar com e sem memória. Isso faz com que os usuários tenham desempenho lento quando o conjunto de dados é carregado na memória. Para confirmar, o administrador do Power BI pode consultar o visual **Remoções do Conjunto de Dados por Hora e Consumo de Memória**, o que pode indicar que um grande número de conjuntos de dados carregados na memória está sendo removido repetidamente.

## <a name="identifying-causes-for-sporadically-slow-responding-datasets"></a>Como identificar as causas de conjuntos de dados que esporadicamente têm resposta lenta

Nesse cenário, uma investigação começou quando os usuários descreveram que os visuais de relatório às vezes eram lentos para responder ou podiam deixar de responder, mas, em outras ocasiões, eram responsivos de forma aceitável.

Dentro do aplicativo, a seção **Durações da Consulta** foi usada para encontrar o conjunto de dados culpado da seguinte maneira:

- No visual **Durações da Consulta**, o administrador filtrou cada conjunto de dados (começando pelos conjuntos de dados superiores) e examinou as barras com filtro cruzado no visual **Distribuições de Consulta por Hora**.
- Quando uma única barra de uma hora mostrou alterações significativas na proporção entre todos os grupos de duração da consulta versus outras barras de uma hora para esse conjunto de dados (por exemplo, as proporções entre as cores mudam de forma drástica), isso significa que esse conjunto de dados demonstrou uma alteração esporádica no desempenho.
- Barras de uma hora que mostram uma parte irregular das consultas de baixo desempenho indicaram um período em que o conjunto de dados foi afetado por um efeito de vizinho barulhento causado pelas outras atividades de outros conjuntos de dados.

A imagem abaixo mostra uma hora em 30 de Janeiro em que um houve uma queda significativa no desempenho de um conjunto de dados, indicada pelo tamanho do bucket de duração de execução "(3,10 s]". Clicar nessa barra de uma hora revela todos os conjuntos de dados carregados na memória durante esse tempo, identificando possíveis conjuntos de dados que causam o efeito vizinho barulhento.

![Barra mostrando o pior desempenho por uma grande parte](media/service-premium-capacity-scenarios/worst-performing-queries.png)

Depois que um período problemático é identificado (por exemplo, durante 30 de janeiro na imagem acima), o administrador do Power BI pode remover todos os filtros de conjunto de linhas e filtrar somente por esse período para determinar quais conjuntos de dados foram consultados ativamente durante esse tempo. O conjunto de dados culpado pelo efeito de vizinho barulhento geralmente é o conjunto de dados mais consultado ou aquele com a maior duração média de consulta.

Uma solução para esse problema pode ser distribuir os conjuntos de dados culpados em diferentes workspaces em diferentes capacidades Premium ou em capacidade compartilhada, se houver suporte para o tamanho do conjunto de dados, para os requisitos de consumo e para os padrões de atualização.

O inverso também pode ser verdadeiro. O administrador do Power BI pode identificar os horários em que um desempenho de consulta do conjunto de dados melhora drasticamente e então procurar o que desapareceu. Se determinadas informações estiverem ausentes nesse ponto, isso poderá ajudar a indicar a causa do problema.

## <a name="determining-whether-there-is-enough-memory"></a>Como determinar se há memória suficiente

Para determinar se há memória suficiente para a capacidade concluir suas cargas de trabalho, o administrador do Power BI pode consultar o visual **Percentuais de Memória Consumida** na guia **Conjuntos de Dados** do aplicativo. **Toda** (total) a memória representam a memória consumida pelos conjuntos de dados carregados na memória, independentemente de serem consultados ou processados ativamente. A memória **ativa** representa a memória consumida pelos conjuntos de dados que estão sendo processados ativamente.

Em uma capacidade íntegra, o visual terá esta aparência, mostrando uma lacuna entre Toda (total) a memória e a memória Ativa:

![Uma capacidade íntegra mostrará uma lacuna entre Todas (total) a memória e a memória Ativa](media/service-premium-capacity-scenarios/memory-healthy-capacity.png)

Em uma capacidade que está sofrendo pressão de memória, o mesmo visual mostrará claramente a memória ativa e a memória total convergindo, o que significa que é impossível carregar conjuntos de dados adicionais na memória. Nesse caso, o administrador do Power BI pode clicar em **Reinicialização de Capacidade** (em **Opções Avançadas** da área de configurações de capacidade do portal de administração). Reiniciar a capacidade resulta em todos os conjuntos de dados serem liberados da memória, permitindo que sejam recarregados na memória conforme necessário (por consultas ou atualização de dados).

![Memória **Ativa** convergindo com **Toda** a memória](media/service-premium-capacity-scenarios/memory-unhealthy-capacity.png)

## <a name="determining-whether-there-is-enough-cpu"></a>Como determinar se há CPU suficiente

Em geral, a utilização média da CPU da capacidade deve permanecer abaixo de 80%. Exceder esse valor significa que a capacidade está se aproximando da saturação da CPU.

Os efeitos da saturação da CPU são expressos por operações que demoram mais do que deveriam por a capacidade realizar muitas alternâncias de contextos de CPU enquanto tenta processar todas as operações. Em uma capacidade Premium com um alto número de consultas simultâneas, isso é indicado por tempos de espera de consulta longos. Uma consequência de tempos de espera de consulta longos é a capacidade de resposta mais lenta do que o normal. O administrador do Power BI pode identificar facilmente quando a CPU está saturada exibindo o visual **Distribuições de Tempo de Espera de Consulta por Hora**. Contagens de tempo de espera de picos periódicos de consulta indicam uma possível saturação da CPU.

![Contagens de tempo de espera de picos periódicos de consulta indicam uma possível saturação da CPU](media/service-premium-capacity-scenarios/peak-query-wait-times.png)

Um padrão semelhante pode, às vezes, ser detectado em operações em segundo plano se elas contribuírem para a saturação da CPU. Um administrador do Power BI pode procurar um pico periódico em tempos de atualização para um conjunto de dados específico, o que pode indicar a saturação da CPU no momento (provavelmente devido a outras atualizações de conjunto de dados em andamento e/ou consultas interativas). Nessa instância, consultar a exibição **Sistema** no aplicativo pode não revelar necessariamente que a CPU está em 100%. A exibição **Sistema** mostra as médias de hora, mas a CPU pode ficar saturada por vários minutos de operações pesadas, o que aparece como picos em tempos de espera.

Há mais nuances para ver o efeito da saturação da CPU. Embora o número de consultas que esperam seja importante, o tempo de espera da consulta sempre ocorrerá em alguma medida sem causar degradação de desempenho perceptível. Alguns conjuntos de dados (com tempo médio de consulta mais demorado, indicando complexidade ou tamanho) são mais propensos aos efeitos da saturação da CPU do que outros. Para identificar facilmente esses conjuntos de dados, o administrador do Power BI pode procurar alterações na composição de cores das barras no visual **Distribuição de Tempo de Espera por Hora**. Depois de detectar uma barra de exceção, eles podem procurar os conjuntos de dados que tiveram espera de consulta durante esse período e também examinar o tempo médio de espera da consulta em comparação à duração média da consulta. Quando essas duas métricas são da mesma magnitude e a carga de trabalho da consulta para o conjunto de dados não é trivial, é provável que o conjunto de dados seja afetado por CPU insuficiente.

Esse efeito pode ser especialmente aparente quando um conjunto de dados é consumido em pequenos picos de consultas de alta frequência por vários usuários (por exemplo, em uma sessão de treinamento), resultando na saturação da CPU durante cada intermitência. Nesse caso, pode haver tempos de espera de consulta significativos nesse conjunto de dados, afetando outros conjuntos de dados na capacidade (efeito de vizinho barulhento).

Em alguns casos, os administradores do Power BI podem solicitar que os proprietários do conjunto de dados criem uma carga de trabalho de consulta menos volátil criando um dashboard (que consulta periodicamente qualquer atualização de conjunto de dados para blocos armazenados em cache), em vez de um relatório. Isso pode ajudar a evitar picos quando o dashboard é carregado. Essa solução nem sempre é possível para determinados requisitos de negócios, no entanto, pode ser uma maneira eficaz de evitar a saturação da CPU sem alterar o conjunto de dados.

## <a name="acknowledgements"></a>Agradecimentos

Este artigo foi escrito por Peter Myers, MVP de plataforma de dados e especialista independente de BI da [Bitwise Solutions](https://www.bitwisesolutions.com.au/).

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Monitorar as capacidades Premium com o aplicativo](service-admin-premium-monitor-capacity.md)    
> [!div class="nextstepaction"]
> [Monitorar capacidades no portal de administração](service-admin-premium-monitor-portal.md)   

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)

||||||