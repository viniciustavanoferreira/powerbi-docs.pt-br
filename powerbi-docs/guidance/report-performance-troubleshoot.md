---
title: Solucionar problemas de desempenho de relatório no Power BI
description: Guia de solução de problemas para diagnosticar desempenho lento de relatório no Power BI.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/15/2020
ms.author: v-pemyer
ms.openlocfilehash: a5230a39706ce5d6941c00386160fe10114442e1
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/05/2020
ms.locfileid: "81527981"
---
# <a name="troubleshoot-report-performance-in-power-bi"></a>Solucionar problemas de desempenho de relatório no Power BI

Este artigo fornece diretrizes que permitem a desenvolvedores e administradores solucionar problemas de desempenho lento de relatório. Ele se aplica a relatórios do Power BI e também a relatórios paginados do Power BI.

Relatórios lentos podem ser identificados por usuários de relatório que, ao trabalhar com relatórios, experienciam carregamento lento ou atualização lenta ao interagir com segmentações ou outros recursos. Quando os relatórios são hospedados em uma capacidade Premium, também é possível identificar os relatórios lentos monitorando o [Aplicativo de Métricas do Power BI Premium](../service-admin-premium-monitor-capacity.md). Esse aplicativo ajuda você a monitorar a integridade e a capacidade de sua assinatura do Power BI Premium.

## <a name="follow-flowchart-steps"></a>Siga as etapas do fluxograma

Use o fluxograma a seguir para ajudar você a entender a causa do desempenho lento e para determinar a ação a ser tomada.

:::image type="content" source="media/report-performance-troubleshoot/flowchart.png" alt-text="A imagem mostra o fluxograma, cuja descrição completa está no texto do artigo." border="true":::

Há seis terminadores de fluxograma, cada um descrevendo uma ação a ser tomada:

|Terminador|Ações|
|---------|---------|
|![Terminador de fluxograma 1.](media/common/icon-01-red-30x30.png)|Gerenciar a capacidade<br />Dimensionar a capacidade |
|![Terminador de fluxograma 2.](media/common/icon-02-red-30x30.png)|Investigar a atividade da capacidade durante o uso típico do relatório|
|![Terminador de fluxograma 3.](media/common/icon-03-red-30x30.png)|Alteração de arquitetura<br />Considere usar o Azure Analysis Services<br />Verificar o gateway local|
|![Terminador de fluxograma 4.](media/common/icon-04-red-30x30.png)|Considere usar o Azure Analysis Services<br />Considere usar o Power BI Premium|
|![Terminador de fluxograma 5.](media/common/icon-05-red-30x30.png)|Usar o Power BI Desktop Performance Analyzer<br />Otimizar relatório, modelo ou DAX|
|![Terminador de fluxograma 6.](media/common/icon-06-red-30x30.png)|Gerar tíquete de suporte|

## <a name="take-action"></a>Executar ação

A primeira é compreender se o relatório lento está hospedado em uma capacidade Premium.

### <a name="premium-capacity"></a>Capacidade Premium

Quando o relatório estiver hospedado em uma capacidade Premium, use o **aplicativo de Métricas do Power BI Premium** para determinar se a capacidade de hospedagem de relatório excede os recursos da capacidade com frequência. Esse é o caso para a CPU quando ela excede 80% com frequência. Para a memória, é quando a [métrica de memória ativa](../service-premium-metrics-app.md#the-active-memory-metric) excede 50. Quando há pressão sobre os recursos, pode ser hora de [gerenciar ou dimensionar a capacidade](../service-admin-premium-manage.md) (terminador de fluxograma 1). Quando há recursos adequados, investigue a atividade da capacidade durante o uso típico do relatório (terminador de fluxograma 2).

### <a name="shared-capacity"></a>Capacidade compartilhada

Quando o relatório é hospedado na capacidade compartilhada, não é possível monitorar a integridade da capacidade. Você precisará adotar uma abordagem investigativa diferente.

Primeiro, determine se o desempenho lento ocorre em horários específicos do dia ou do mês. Se esse for o caso e muitos usuários estiverem abrindo o relatório nesses horários, considere duas opções:

- Aumente a taxa de transferência da consulta migrando o conjunto de dados para o [Azure Analysis Services](/azure/analysis-services/analysis-services-overview) ou uma capacidade Premium (terminador de fluxograma 4).
- Use o [Performance Analyzer](../desktop-performance-analyzer.md) do Power BI Desktop para descobrir como está o desempenho de cada um de seus elementos de relatório, como visuais e fórmulas DAX. Isso é especialmente útil para determinar se é a consulta ou a renderização visual que está contribuindo para os problemas de desempenho (terminador de fluxograma 5).

Se você determinar que não há nenhum padrão de tempo, considere então se o desempenho lento está isolado em uma geografia ou região específica. Se está, é provável que a fonte de dados seja remota e haja uma comunicação de rede lenta. Nesse caso, considere:

- Alterar a arquitetura usando o [Azure Analysis Services](/azure/analysis-services/analysis-services-overview) (terminador de fluxograma 3).
- Otimizar o [desempenho do gateway de dados local](/data-integration/gateway/service-gateway-performance) (terminador de fluxograma 3).

Por fim, se você determinar que não há um padrão de tempo _e_ que o desempenho lento ocorre em todas as regiões, investigue se o desempenho lento ocorre em dispositivos, clientes ou navegadores da Web específicos. Se não ocorrer, use o [Performance Analyzer](../desktop-performance-analyzer.md) do Power BI Desktop, conforme descrito anteriormente, para otimizar o relatório ou o modelo (terminador de fluxograma 5).

Quando você determina que dispositivos, clientes ou navegadores da Web específicos contribuem para um desempenho lento, é recomendável criar um tíquete de suporte por meio da [página de suporte do Power BI](https://powerbi.microsoft.com/support/) (terminador de fluxograma 6).

## <a name="next-steps"></a>Próximas etapas

Para obter mais informações sobre este artigo, confira os seguintes recursos:

- [Diretrizes do Power BI](index.yml)
- [Monitorar o desempenho de relatórios](monitor-report-performance.md)
- [Performance Analyzer](../desktop-performance-analyzer.md)
- White paper: [Planejando uma implantação do Power BI Enterprise](https://go.microsoft.com/fwlink/?linkid=2057861)
- Dúvidas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
- Sugestões? [Contribuir com ideias para aprimorar o Power BI](https://ideas.powerbi.com/)
