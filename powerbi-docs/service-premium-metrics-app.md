---
title: Aplicativo de métricas do Power BI Premium
description: Saiba como usar o aplicativo de métricas do Power BI Premium para gerenciar e solucionar problemas de capacidade Premium.
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 12/19/2019
LocalizationGroup: Premium
ms.openlocfilehash: ae11ec64a0bffbd3e64c0fd677a7225c2b31f521
ms.sourcegitcommit: a175faed9378a7d040a08ced3e46e54503334c07
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79488673"
---
# <a name="power-bi-premium-metrics-app"></a>Aplicativo de métricas do Power BI Premium

Você pode usar o **aplicativo de métricas do Power BI Premium** para gerenciar a integridade e a capacidade da sua assinatura do Power BI Premium. Com o aplicativo, os administradores usam o **Centro de integridade da capacidade** para ver e interagir com indicadores que monitoram a integridade da capacidade Premium. O aplicativo de métricas consiste na página de aterrissagem, chamada de **Centro de Integridade da Capacidade**, e detalhes sobre três métricas importantes:

* Memória ativa
* Esperas da consulta
* Esperas de atualização

![O aplicativo de métricas do Power BI Premium](media/service-premium-metrics-app/premium-metrics-app-00.png)

As seções a seguir descrevem a página de aterrissagem e as três páginas do relatório de métricas em detalhes. 

## <a name="premium-capacity-health-center"></a>Central de Integridade da Capacidade Premium

Quando você abre o **aplicativo de métricas do Power BI Premium**, vê o **Centro de Integridade da Capacidade**, que fornece uma visão geral da integridade da sua capacidade do Power BI Premium.

![O centro de integridade da capacidade no aplicativo de métricas Premium](media/service-premium-metrics-app/premium-metrics-app-01.png)

Na página de aterrissagem, você pode selecionar a capacidade do Power BI Premium que deseja exibir quando sua organização tem várias assinaturas Premium. Para exibir uma capacidade Premium, selecione a lista suspensa próxima à parte superior da página chamada **Selecionar uma capacidade para ver suas métricas**.

Os três KPIs mostram a integridade atual da capacidade Premium selecionada com base nas configurações aplicadas a cada um deles. 

Para abrir a página de detalhes e exibir informações específicas sobre cada KPI, selecione o botão **Explorar** na parte inferior do visual de cada um. As seções a seguir descrevem cada KPI e os detalhes que sua página fornece.

## <a name="the-active-memory-metric"></a>A métrica de memória ativa

A métrica de **memória ativa** é parte da categoria de *planejamento da capacidade*, que é um bom indicador de integridade para avaliar o consumo de recursos da sua capacidade quando utilizada, para que você possa ajustar a capacidade conforme a necessidade e planejar sua escala. 

![O KPI de memória ativa](media/service-premium-metrics-app/premium-metrics-app-02.png)

A **memória ativa** é a memória usada para processar os conjuntos de dados que estão em uso no momento e, portanto, não serão removidos quando houver necessidade de memória. A métrica de memória ativa indica se a capacidade pode lidar com carga adicional ou se já está próxima do limite ou acima da capacidade com a carga atual. A memória ativa que está sendo consumida no momento significa que há menos memória disponível para dar suporte a atualizações e consultas adicionais. 

O KPI de **memória ativa** mede o número de vezes que a memória ativa da capacidade ultrapassou o limite de 70% 50 vezes (o marcador é definido como 30% dos últimos sete dias), o que indica que a capacidade poderá começar a causar problemas de desempenho para os usuários nas consultas.

O visual de medidor mostrado nesta seção revela que, nos últimos sete dias a partir da hora em que o relatório foi atualizado pela última vez, a capacidade ultrapassou o limite de 70% quatro vezes, dividida em buckets por hora. O valor máximo do medidor, 168, representa os últimos sete dias, em horas.

Para saber os detalhes do KPI de memória ativa, clique no botão **Explorar** para ver uma página de relatório que fornece visualizações específicas das métricas detalhadas, juntamente com um guia de solução de problemas na coluna à direita da página. 

Há dois cenários explicados que você pode ver na página do relatório; selecione **Cenário 1** ou **Cenário 2** na página. 

![A página de detalhes da memória ativa](media/service-premium-metrics-app/premium-metrics-app-03.png)

Os guias de solução de problemas associados a cada cenário fornecem explicações detalhadas sobre o que significam as métricas, para que você possa entender melhor a situação da capacidade e o que pode ser feito para atenuar eventuais problemas. 

Esses dois cenários estão descritos nas seções a seguir.

### <a name="scenario-one---current-load-is-too-high"></a>Cenário um – a carga atual é muito alta 

Para determinar se há memória suficiente para a conclusão das cargas de trabalho, confira o primeiro visual na página: **A: Porcentagens de Memória Consumida**, que exibe a memória consumida pelos conjuntos de dados que estão sendo processados ativamente e que, portanto, não pode ser removida.

O limite de alarme, que é a linha pontilhada vermelha, marca incidentes de 90% de consumo de memória.

O limite de aviso, que é a linha pontilhada amarela, marca incidentes de 70% de consumo de memória. 

A linha pontilhada preta indica a linha de tendência de uso de memória com base no uso da memória da capacidade atual no decorrer da linha do tempo do grafo.

As altas ocorrências de memória ativa acima do limite de alarme (linha vermelha pontilhada) e da linha de tendência de memória (linha preta pontilhada) indicam a pressão sobre a capacidade da memória, o que pode estar impedindo o carregamento de conjuntos de dados adicionais na memória durante esse tempo. 

Ao ver esses casos, você deverá examinar atentamente outros gráficos na página para determinar melhor o que e por que toda essa memória está sendo consumida com frequência e como balancear a carga, otimizar ou, se necessário, escalar a capacidade verticalmente. 

O segundo visual na página, **B: Conjuntos de dados ativos carregados por hora**, exibe as contagens do número máximo de conjuntos de dados que foram carregados na memória, em buckets por hora. 

O terceiro visual, **C: Por que os conjuntos de dados estão na memória**, é uma tabela que lista o conjunto de valores por nome do workspace, o nome do conjunto de valores, o tamanho descompactado de conjuntos de dados na memória e explica o motivo pelo qual ele foi carregado na memória (por exemplo, por atualização, consulta ou ambos).

#### <a name="diagnosing-scenario-one"></a>Diagnosticar o cenário um

A alta utilização de memória ativa de forma consistente pode resultar na remoção de conjuntos de dados que estão sendo usados ativamente ou impedir o carregamento de novos conjuntos de dados. As etapas a seguir podem ajudá-lo a diagnosticar problemas

1. Veja o gráfico *A: Percentuais de memória consumida*

    **a.** Se o Gráfico A mostra que o limite de alarme (90%) é ultrapassado muitas vezes e/ou por horas consecutivas, sua capacidade está ficando com pouca memória muito frequentemente. No gráfico abaixo, podemos ver que o limite de aviso (70%) foi ultrapassado quatro vezes.

    ![Gráfico A, percentuais de memória consumida](media/service-premium-metrics-app/premium-metrics-app-04.png)

    **b.** O gráfico *B: Conjuntos de dados ativos carregados por hora* mostra o número máximo de conjuntos de dados individuais carregados na memória em buckets por hora. A escolha de uma barra no visual filtrará de forma cruzada os motivos pelos quais os conjuntos de dados estão no visual da memória.  

    ![Gráfico B, Memória consumida por hora](media/service-premium-metrics-app/premium-metrics-app-05.png)     

    **c.** Confira a tabela **Por que os conjuntos de tabelas estão na memória** para ver uma lista dos conjuntos de dados que foram carregados na memória. Classifique por *Tamanho do Conjunto de Valores (MB)* a fim de destacar os conjuntos de dados que ocupam mais memória. As operações de capacidade são classificadas como *interativas* ou *em segundo plano*. As operações interativas incluem a renderização de solicitações e a resposta às interações do usuário (filtragem, perguntas e respostas, consultas e outros). O total de consultas e atualizações indicam se existem operações com muita interação (consultas) ou em segundo plano (atualizações) realizadas no conjunto de dados. É importante entender que as operações interativas são sempre priorizadas em vez de operações em segundo plano para garantir a melhor experiência do usuário possível. Se não houver recursos suficientes, as operações em segundo plano serão adicionadas a uma fila e processadas quando os recursos forem liberados. Operações em segundo plano, como atualizações de conjunto de dados e funções de IA, podem ser interrompidas no meio do processo pelo serviço do Power BI e adicionadas a uma fila.
    
    ![tabela c, lista de conjuntos de dados](media/service-premium-metrics-app/premium-metrics-app-06.png)  

#### <a name="remedies-for-scenario-one"></a>Soluções para o cenário um

Você pode seguir as seguintes etapas para corrigir os problemas associados ao cenário um:

1. **Escalar a capacidade verticalmente** – a ação de escalar verticalmente a capacidade para a SKU seguinte disponibilizará duas vezes mais a quantidade de memória da SKU atual, aliviando, assim, eventual pressão de memória que a capacidade possa estar enfrentando no momento.

2. **Mover conjuntos de trabalho para outra capacidade** – se você tiver outra capacidade que tenha mais memória disponível, poderá mover os espaços de trabalho que contêm os conjuntos de grandes maiores para essa capacidade.


### <a name="scenario-two---future-load-will-exceed-limits"></a>Cenário dois – a futura carga excederá os limites

Para determinar se há memória suficiente para a conclusão das cargas de trabalho, confira o visual **A: Porcentagens de Memória Consumida** na parte superior da página, que representa a memória consumida por conjuntos de dados que estão sendo ativamente processados e, portanto, não podem ser removida. A linha pontilhada preta destaca as tendências. Em uma capacidade que sofre pressão na memória, o mesmo visual mostrará claramente a linha de tendência (linha pontilhada preta) de memória ascendente, o que significa que provavelmente está impedindo o carregamento de outros conjuntos de dados na memória naquele momento. A linha de tendência, a linha tracejada preta, mostra a tendência de crescimento com base nos sete dias de dados. 

![A página de detalhes da memória ativa](media/service-premium-metrics-app/premium-metrics-app-07.png)

#### <a name="diagnosing-scenario-two"></a>Diagnosticar o cenário dois

Para diagnosticar o cenário dois, determine se a linha de tendência está mostrando uma tendência ascendente em relação aos limites de aviso ou alarme. 

1. Considere o **Gráfico A:**

    ![Grafo de memória consumida](media/service-premium-metrics-app/premium-metrics-app-08.png)

    **a.** Se o gráfico mostrar uma inclinação para cima, isso indicará que o consumo de memória aumentou nos últimos sete dias.

    **b.** Suponha o crescimento atual e preveja quando a linha de tendência ultrapassará o limite de aviso (a linha pontilhada amarela).

    **c.** Continue verificando a linha de tendência pelo menos a cada dois dias para ver se a tendência continua.

#### <a name="remedies-for-scenario-two"></a>Soluções para o cenário dois

Você pode seguir as seguintes etapas para corrigir os problemas associados ao cenário dois:

1. **Escalar a capacidade verticalmente** – a ação de escalar verticalmente a capacidade para a SKU seguinte disponibilizará duas vezes mais a quantidade de memória da SKU atual, aliviando, assim, eventual pressão de memória que a capacidade possa estar enfrentando no momento.

2. **Mover conjuntos de trabalho para outra capacidade** – se você tiver outra capacidade que tenha mais memória disponível, poderá mover os espaços de trabalho que contêm os conjuntos de grandes maiores para essa capacidade.


## <a name="the-query-waits-metric"></a>A métrica de esperas da consulta

A categoria **Consulta** indica se os usuários podem experimentar visuais de relatório que estão demorando para responder ou que podem não responder. **Esperas da consulta** é o tempo que a consulta leva para iniciar a execução a partir do momento em que foi disparada. Esse KPI mede se 25% ou mais das consultas da capacidade selecionada estão aguardando 100 milissegundos ou mais para serem executadas. As esperas da consulta ocorrem quando não há CPU disponível suficiente para executar todas as consultas pendentes. 

![O medidor de esperas da consulta](media/service-premium-metrics-app/premium-metrics-app-09.png)

O medidor no visual em questão mostra que nos últimos sete dias a partir da hora em que o relatório foi atualizado pela última vez, 17,32% das consultas aguardaram mais de 100 milissegundos. 

Para obter detalhes sobre o KPI de esperas da consulta, clique no botão **Explorar** para exibir uma página de relatório com a visualização de métricas relevantes e um guia de solução de problemas na coluna à direita da página. O guia de solução de problemas tem dois cenários, cada um fornecendo explicações detalhadas sobre a métrica, a situação da capacidade e o que você pode fazer para atenuar o problema.

Discutiremos cada cenário de esperas da consulta, um de cada vez, nas seções a seguir.

### <a name="scenario-one---long-running-queries-consume-cpu"></a>Cenário um – consultas de execução prolongada consomem CPU

No cenário um, as consultas de execução prolongada estão ocupando muita CPU. 

Você pode investigar se o desempenho insatisfatório do relatório é causado por uma sobrecarga de capacidade ou devido a um relatório ou conjunto de relatórios mal projetado. Há várias razões pelas quais uma consulta pode ser executada por um período prolongado, que é definido como demorando mais de 10 segundos para sua execução. O tamanho e a complexidade do conjunto de dados, bem como a complexidade da consulta, são apenas alguns exemplos do que pode causar uma consulta de execução prolongada. 

Na página do relatório, os seguintes elementos visuais são exibidos: 

* A tabela superior chamada **A: Tempos de espera altos** lista os conjuntos de dados com consultas que estão em espera. 
* A tabela **B: Distribuições de tempo de espera alto por hora** mostra a distribuição de tempos de espera altos. 
* O gráfico **C: Contagens de consultas prolongadas por hora** exibe a contagem de consultas de execução prolongada que foram executadas divididas em buckets por hora.
* O último visual, a tabela **D: Consultas de execução prolongada**, lista as consultas de execução prolongada e suas estatísticas.

![A página de detalhes de esperas da consulta](media/service-premium-metrics-app/premium-metrics-app-10.png)

Há etapas que você pode seguir para diagnosticar e corrigir problemas com tempos de espera de consulta, descritos a seguir.

#### <a name="diagnosing-scenario-one"></a>Diagnosticar o cenário um

Primeiro, você pode determinar se as consultas de execução prolongada estão ocorrendo quando suas consultas estão em espera. 

![Tabela de tempos de espera altos](media/service-premium-metrics-app/premium-metrics-app-11.png)

Examine o **Gráfico B**, que mostra a contagem de consultas que estão aguardando por mais de 100 ms. Selecione uma das colunas que mostra um número alto de esperas.

![Distribuição do tempo de espera alta](media/service-premium-metrics-app/premium-metrics-app-12.png)

Quando você clica em uma coluna com tempos de espera altos, o **Gráfico C** é filtrado para mostrar a contagem de consultas de execução prolongada em andamento durante esse tempo, mostradas nesta imagem:

![Contagens de consultas longas por hora](media/service-premium-metrics-app/premium-metrics-app-13.png)

Além disso, o **Gráfico D** também é filtrado para mostrar as consultas de execução prolongada em execução durante esse período de tempo selecionado.

![Consultas de execução prolongada](media/service-premium-metrics-app/premium-metrics-app-14.png)

#### <a name="remedies-for-scenario-one"></a>Soluções para o cenário um

Aqui estão as etapas que você pode seguir para corrigir problemas do cenário um:

1. **Execute o PerfAnalyzer para otimizar relatórios e conjuntos de dados** – o analisador de desempenho para relatórios mostrará o efeito de cada interação em uma página, incluindo quanto tempo cada visual leva para ser atualizado e onde o tempo é gasto.

2. **Escalar a capacidade verticalmente** – a ação de escalar verticalmente a capacidade para a SKU seguinte disponibilizará duas vezes mais a quantidade de CPU, aliviando, assim, eventual pressão de CPU que esteja atrasando as consultas.

3. **Mover conjuntos de dados para outra capacidade** – se você tiver outra capacidade que tenha mais CPU disponível, poderá mover os espaços de trabalho que contêm os conjuntos de dados que contêm as consultas em espera para outra capacidade.

### <a name="scenario-two---too-many-queries"></a>Cenário dois – consultas em excesso

No cenário dois, muitas consultas estão em execução.

Quando o número de consultas a serem executadas exceder a capacidade, as consultas serão colocadas em uma fila até que os recursos estejam disponíveis para executá-las. Se o tamanho da fila ficar muito grande, as consultas nessa fila poderão acabar aguardando mais de 100 milissegundos.

![Cenário dois](media/service-premium-metrics-app/premium-metrics-app-15.png)


#### <a name="diagnosing-scenario-two"></a>Diagnosticar o cenário dois

Na **Tabela A**, selecione um conjunto de dados que tenha uma alta porcentagem de tempo de espera.

![tabela de tempos de espera altos](media/service-premium-metrics-app/premium-metrics-app-16.png)

Depois que você escolher um conjunto de dados com um tempo de espera alto, o **Gráfico B** será filtrado para mostrar as distribuições de tempo de espera das consultas nesse conjunto de dados nos últimos sete dias. Selecione uma das colunas do **Gráfico B**.

![gráfico de distribuição de tempos de espera altos por hora](media/service-premium-metrics-app/premium-metrics-app-17.png)

O **Gráfico C** é filtrado para mostrar o comprimento da fila na hora selecionada do Gráfico B.

![comprimento da fila de consultas por hora](media/service-premium-metrics-app/premium-metrics-app-18.png)

Se o comprimento da fila tiver ultrapassado o limite de 20, é provável que as consultas no conjunto de dados selecionado fiquem atrasadas, devido ao excesso de consultas sendo executadas simultaneamente.

![Tabela de execução de consultas](media/service-premium-metrics-app/premium-metrics-app-19.png)

#### <a name="remedies-for-scenario-two"></a>Soluções para o cenário dois

Você pode seguir as seguintes etapas para corrigir os problemas associados ao cenário dois:

1. **Escalar a capacidade verticalmente** – a ação de escalar verticalmente a capacidade para a SKU seguinte disponibilizará duas vezes mais a quantidade de memória da SKU atual, aliviando, assim, eventual pressão de memória que a capacidade possa estar enfrentando no momento.

2. **Mover conjuntos de trabalho para outra capacidade** – se você tiver outra capacidade que tenha mais memória disponível, poderá mover os espaços de trabalho que contêm os conjuntos de grandes maiores para essa capacidade.


## <a name="the-refresh-waits-metric"></a>A métrica de esperas de atualização

As métricas de **esperas de atualização** fornece informações sobre quando os usuários podem estar recebendo dados de relatório antigos ou obsoletos. As **esperas de atualização** são o tempo que determinada atualização de dados aguardou para iniciar a execução, desde o momento em que ela foi disparada sob demanda ou agendada para execução. É um KPI que mede se 10% ou mais das solicitações de atualização pendentes estão aguardando 10 minutos ou mais. A espera geralmente ocorre quando não há memória ou CPU suficiente disponível.

![O medidor de esperas de atualização](media/service-premium-metrics-app/premium-metrics-app-20.png)

Esse medidor mostra que nos últimos sete dias desde a última atualização do relatório de atualização, 3,18% das atualizações aguardaram mais de 10 minutos. 

Para saber os detalhes do KPI **Esperas de atualização**, clique no botão **Explorar**, que apresenta uma página com métricas e um guia de solução de problemas na coluna à direita da página do relatório. O guia fornece explicações detalhadas sobre as métricas na página e ajuda você a entender a situação da capacidade e o que você pode fazer para atenuar eventuais problemas.

![Explorar métricas de esperas de atualização](media/service-premium-metrics-app/premium-metrics-app-21.png)

Há dois cenários explicados que você pode ver na página do relatório; selecione Cenário 1 ou Cenário 2 na página. Discutiremos um cenário de cada vez nas seções a seguir.

### <a name="scenario-one---not-enough-memory"></a>Cenário um – não há memória suficiente

No cenário um, não há memória suficiente disponível para carregar o conjunto de dados. Há duas situações que resultam na limitação da atualização em condições de memória insuficiente:

1. Memória insuficiente para carregar o conjunto de dados.
2. A atualização foi cancelada devido a uma operação de prioridade mais alta. 

A prioridade para carregar conjuntos de dados é a seguinte:

1. Consulta interativa
2. Atualização sob demanda
3. Atualização agendada

Se não houver memória suficiente para carregar um conjunto de dados para uma consulta interativa, as atualizações agendadas serão interrompidas e seus conjuntos de dados serão descarregados até que haja memória suficiente disponível. Se isso não liberar memória suficiente, as atualizações sob demanda serão interrompidas e seus conjuntos de dados serão descarregados.

#### <a name="diagnosing-scenario-one"></a>Diagnosticar o cenário um

Para diagnosticar o cenário um, primeiro determine se a limitação ocorre porque não há memória suficiente. Estas são as etapas para executar o procedimento.

1.    Selecione o conjunto de dados da **Tabela A** desejado clicando nele: 

    ![Tabela A](media/service-premium-metrics-app/premium-metrics-app-22.png)

    a. Quando um conjunto de dados é selecionado na **Tabela A**, o **Gráfico B** é filtrado para mostrar quando ocorreu a espera.

    ![Gráfico B](media/service-premium-metrics-app/premium-metrics-app-23.png)

    b. O **Gráfico C** é, então, filtrado para mostrar se há limitações, explicadas na próxima etapa. 

2. Examine os resultados no **Gráfico C** filtrado. Se o gráfico mostrar uma limitação de memória ocorrida na hora em que o conjunto de dados estava em espera, ele estava em espera devido a condições de memória insuficiente.

    ![Gráfico C](media/service-premium-metrics-app/premium-metrics-app-24.png)

3. Por fim, marque o **Gráfico D**, que mostra os tipos de atualizações que estão ocorrendo entre as agendadas e as sob demanda. A limitação pode ser causada por atualizações sob demanda que estejam ocorrendo ao mesmo tempo.

    ![Gráfico D](media/service-premium-metrics-app/premium-metrics-app-25.png)


#### <a name="remedies-for-scenario-one"></a>Soluções para o cenário um

Você pode seguir as seguintes etapas para corrigir os problemas associados ao cenário um:

1. **Escalar a capacidade verticalmente** – a ação de escalar verticalmente a capacidade para a SKU seguinte disponibilizará duas vezes mais a quantidade de memória da SKU atual, aliviando, assim, eventual pressão de memória e CPU que a capacidade esteja enfrentando no momento.

2. **Mover conjuntos de dados para outra capacidade** – se seus tempos de espera estão sendo afetados por pressão na memória e você tiver outra capacidade com mais memória disponível, poderá mover os espaços de trabalho que contêm os conjuntos de dados em espera para a outra capacidade.

3. **Distanciar as atualizações agendadas** – o distanciamento das atualizações ajuda a evitar o excesso de atualizações que tentam ser executadas simultaneamente.



### <a name="scenario-two---not-enough-cpu-for-refresh"></a>Cenário dois – não há CPU suficiente para atualização

No cenário dois, não há CPU suficiente disponível para executar a atualização. 

No caso de capacidades dedicadas, o Power BI limita o número de atualizações que podem ocorrer simultaneamente. Esse número é igual ao número de núcleos de back-end x 1,5. Por exemplo, uma capacidade de P1 dedicada, que tem quatro núcleos de back-end, pode executar seis atualizações simultaneamente. Depois que o número máximo de atualizações simultâneas é atingido, outras atualizações precisam aguardar até que uma atualização em execução seja concluída.

![Cenário dois de atualização](media/service-premium-metrics-app/premium-metrics-app-26.png)

#### <a name="diagnosing-scenario-two"></a>Diagnosticar o cenário dois

Para diagnosticar o cenário dois, primeiro determine se a limitação ocorre devido ao máximo de execuções de atualização simultâneas. Estas são as etapas para executar o procedimento.

1.    Selecione o conjunto de dados da **Tabela A** desejado clicando nele: 

    ![Tabela A](media/service-premium-metrics-app/premium-metrics-app-22.png)

    a. Quando um conjunto de dados é selecionado na **Tabela A**, o **Gráfico B** é filtrado para mostrar quando ocorreu a espera.

    ![Gráfico B](media/service-premium-metrics-app/premium-metrics-app-23.png)

    b. O **Gráfico C** é, então, filtrado para mostrar se há limitações, explicadas na próxima etapa. 

2. Examine os resultados no **Gráfico C** filtrado. Se o gráfico mostrar que o *máximo de simultaneidade* ocorreu no momento em que o conjunto de dados estava em espera, ele estava em espera devido à falta de CPU disponível.

    ![Gráfico C](media/service-premium-metrics-app/premium-metrics-app-24.png)

3. Por fim, marque o **Gráfico D**, que mostra os tipos de atualizações que estão ocorrendo entre as agendadas e as sob demanda. A limitação pode ser causada por atualizações sob demanda que estejam ocorrendo ao mesmo tempo.

    ![Gráfico D](media/service-premium-metrics-app/premium-metrics-app-25.png)


#### <a name="remedies-for-scenario-two"></a>Soluções para o cenário dois

1. **Escalar a capacidade verticalmente** – a ação de escalar verticalmente a capacidade para a SKU seguinte disponibilizará duas vezes mais a quantidade de memória da SKU atual e duas vezes mais o número de atualizações simultâneas que a SKU atual, aliviando, assim, eventual pressão de memória e CPU que a capacidade esteja enfrentando no momento.

2. **Mover conjuntos de dados para outra capacidade** – se seus tempos de espera estão sendo causados pelo limite máximo de simultaneidade e tiver outra capacidade com mais memória disponível, poderá mover os espaços de trabalho que contêm os conjuntos de dados em espera para a outra capacidade.

3. **Distanciar as atualizações agendadas** – o distanciamento das atualizações ajuda a evitar o excesso de atualizações que tentam ser executadas simultaneamente.



## <a name="next-steps"></a>Próximas etapas

* [O que é o Power BI Premium?](service-premium-what-is.md)
* [Notas de versão do Power BI Premium](service-premium-release-notes.md)
* [White paper do Microsoft Power BI Premium](https://aka.ms/pbipremiumwhitepaper)
* [Planejando um white paper de implantação do Power BI Enterprise](https://aka.ms/pbienterprisedeploy)
* [Ativação da Avaliação Pro Estendida](service-extended-pro-trial.md)
* [Perguntas frequentes do Power BI Embedded](developer/embedded/embedded-faq.md)

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)