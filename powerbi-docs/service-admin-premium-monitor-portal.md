---
title: Monitorar as capacidades do Power BI Premium por meio do portal de administração
description: Use o portal de administração do Power BI para monitorar suas capacidades Premium.
author: mgblythe
ms.author: mblythe
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/10/2019
LocalizationGroup: Premium
ms.openlocfilehash: 0d1e0da498a7a2c78e86b643b8a86cb87d6d095a
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/09/2019
ms.locfileid: "73856862"
---
# <a name="monitor-capacities-in-the-admin-portal"></a>Monitorar capacidades no portal de administração

A guia **Integridade** na área **Configurações de capacidade** no Portal do administrador oferece um resumo de métricas sobre sua capacidade e suas cargas de trabalho habilitadas.  

![Guia Integridade da capacidade no portal](media/service-admin-premium-monitor-portal/admin-portal-health.png)

Se precisar de métricas mais abrangentes, use o aplicativo [Métricas de Capacidade do Power BI Premium](service-admin-premium-monitor-capacity.md). O aplicativo fornece busca detalhada e filtragem e métricas mais detalhadas para quase todo aspecto que afeta o desempenho da capacidade. Para saber mais, confira [Monitorar capacidades Premium com o aplicativo](service-admin-premium-monitor-capacity.md).

## <a name="system-metrics"></a>Métricas do sistema

Na guia **Integridade**, no nível mais alto, a utilização da CPU e o uso de memória fornecem uma visão rápida das métricas mais importantes da capacidade. Essas métricas são cumulativas, incluindo todas as cargas de trabalho habilitadas para a capacidade.

| **Métrica** | **Descrição** |
| --- | --- |
| USO DA CPU | Utilização média da CPU, como um percentual do total disponível da CPU. |
| USO DE MEMÓRIA | Uso médio de memória em gigabytes (GB).|

## <a name="workload-metrics"></a>Métricas de carga de trabalho

Para cada carga de trabalho habilitada para a capacidade. A utilização da CPU e o uso de memória são mostrados.

| **Métrica** | **Descrição** |
| --- | --- |
| USO DA CPU | Utilização média da CPU, como um percentual do total disponível da CPU. |
| USO DE MEMÓRIA | Uso médio de memória em gigabytes (GB).|

### <a name="detailed-workload-metrics"></a>Métricas detalhadas da carga de trabalho

Cada carga de trabalho tem métricas adicionais. O tipo de métrica mostrado depende da carga de trabalho. Para ver as métricas detalhadas de uma carga de trabalho, clique na seta (para baixo) expandir.

![Expansão da integridade da carga de trabalho](media/service-admin-premium-monitor-portal/admin-portal-health-expand.png)

#### <a name="dataflows"></a>Fluxos de dados

##### <a name="dataflow-operations"></a>Operações do fluxo de dados

| **Métrica** | **Descrição** |
| --- | --- |
| Contagem total | o total é atualizado para cada fluxo de dados. |
| Contagem de Êxito | Total de atualizações bem-sucedidas para cada fluxo de dados.|
| Duração Média (min) | a duração média da atualização para o fluxo de dados, em minutos |
| Duração Máxima (min) | a duração da atualização de execução mais longa para o fluxo de dados, em minutos. |
| Tempo Médio de Espera (min) | a latência média entre o horário agendado e o início de uma atualização para o fluxo de dados, em minutos. |
| Tempo Máximo de Espera (min) | o tempo de espera máximo para o fluxo de dados, em minutos.  |

#### <a name="datasets"></a>Conjuntos de dados

##### <a name="refresh"></a>Atualizar

| **Métrica** | **Descrição** |
| --- | --- |
| Contagem total | o total é atualizado para cada conjunto de dados. |
| Contagem de Êxito | Total de atualizações bem-sucedidas para cada conjunto de dados. |
| Contagem de Falha | Total de atualizações com falha para cada conjunto de dados. |
| Taxa de êxito  | Número de atualizações bem-sucedidas dividido pelo total de atualizações a serem medidas. confiabilidade. |
| Duração Média (min) | a duração média da atualização para o conjunto de dados, em minutos.  |
| Duração Máxima (min) | a duração da atualização de execução mais longa para o conjunto de dados, em minutos. |
| Tempo Médio de Espera (min) | a latência média entre o horário agendado e o início de uma atualização para o conjunto de dados, em minutos. |
| Tempo Máximo de Espera (min) | o tempo de espera máximo para o conjunto de dados, em minutos. |

##### <a name="query"></a>Consultar

| **Métrica** | **Descrição** |
| --- | --- |
| Contagem total | o número total de consultas executadas para o conjunto de dados. |
| Duração Média (ms) |a duração média de consulta do conjunto de dados, em milissegundos|
| Duração máxima (ms) |a duração da consulta de execução mais longa no conjunto de dados, em milissegundos. |
| Tempo de Espera Médio (ms) |o tempo médio de espera da consulta para o conjunto de dados, em milissegundos. |
| Tempo Máximo de Espera (ms) |a duração da consulta de espera mais longa no conjunto de dados, em milissegundos. |

##### <a name="eviction"></a>Remoção

| **Métrica** | **Descrição** |
| --- | --- |
| Contagem de Modelos | O número total de remoções de conjunto de dados para essa capacidade. Quando uma capacidade enfrenta a pressão de memória, o nó remove um ou mais conjuntos de dados da memória. Conjuntos de dados que estão inativos (sem nenhuma operação de atualização/consulta em execução no momento) são removidos primeiro. Em seguida, a ordem de remoção se baseia em uma medida de LRU (“menos utilizado recentemente”). |

#### <a name="paginated-reports"></a>Relatórios paginados

##### <a name="report-execution"></a>Execução de Relatório

| **Métrica** | **Descrição** |
| --- | --- |
| Contagem de Execuções  | O número de vezes que o relatório foi executado e exibido pelos usuários.|

##### <a name="report-usage"></a>Uso do Relatório

| **Métrica** | **Descrição** |
| --- | --- |
| Contagem de Êxito | O número de vezes que o relatório foi exibido por um usuário. |
| Contagem de Falha |O número de vezes que o relatório foi exibido por um usuário.|
| Contagem de linhas |o número de linhas de dados no relatório. |
| Duração da Recuperação de Dados (ms) |a quantidade média de tempo que leva para recuperar dados para o relatório, em milissegundos. Durações longas podem indicar consultas lentas ou outros problemas de fonte de dados.  |
| Duração do Processamento (ms) |a quantidade média de tempo que leva para processar os dados para um relatório, em milissegundos. |
| Duração da Renderização (ms) |a quantidade média de tempo necessária para renderizar um relatório no navegador, em milissegundos. |

> [!NOTE]
> As métricas detalhadas para a carga de trabalho de **IA** ainda não estão disponíveis.

## <a name="next-steps"></a>Próximas etapas

Agora que você entende como monitorar as capacidades do Power BI Premium, saiba mais sobre como otimizar as capacidades.

> [!div class="nextstepaction"]
> [Como otimizar as capacidades Premium do Power BI](service-premium-capacity-optimize.md)
