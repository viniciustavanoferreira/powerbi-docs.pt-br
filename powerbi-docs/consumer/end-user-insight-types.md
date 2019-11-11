---
title: Tipos de Insights com suporte para o Power BI
description: Quick Insights e View Insights com o Power BI.
author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 10/31/2019
ms.author: mihart
LocalizationGroup: Dashboards
ms.openlocfilehash: 75462c2414854d0848254a36b89bcdd1de365ec5
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/09/2019
ms.locfileid: "73863474"
---
# <a name="types-of-insights-supported-by-power-bi"></a>Tipos de Insights com suporte para o Power BI

O serviço do Power BI pode procurar insights automaticamente em seus dashboards ou seus relatórios.

## <a name="how-does-insights-work"></a>Como o Insights funciona?
O Power BI pesquisa rapidamente diferentes subconjuntos do conjunto de dados. À medida que ele pesquisa, o Power BI aplica um conjunto de algoritmos sofisticados para descobrir insights potencialmente interessantes. Ele examina ao máximo possível um conjunto de dados no período de tempo designado.

Você pode executar insights em um conjunto de dados ou bloco de painel.   

## <a name="what-types-of-insights-can-we-find"></a>Que tipos de informações é possível encontrar?
Estes são alguns dos algoritmos que usamos:

## <a name="category-outliers-topbottom"></a>Exceções de categoria (superior/inferior)
Realça os casos em que, para uma medida no modelo, um ou dois membros de uma dimensão têm valores muito mais altos do que outros membros da dimensão.  

![Exemplo de exceções de categoria](./media/end-user-insight-types/pbi-auto-insight-types-category-outliers.png)

## <a name="change-points-in-a-time-series"></a>Alterar os pontos em uma série temporal
Realça os casos em que há alterações significativas nas tendências em uma série temporal de dados.

![Exemplo de alterar pontos em uma série temporal](./media/end-user-insight-types/pbi-auto-insight-types-changepoint.png)

## <a name="correlation"></a>Correlação
Detecta os casos em que várias medidas mostram uma correlação entre si quando plotadas em uma dimensão no conjunto de dados.

![Exemplo de correlação](./media/end-user-insight-types/pbi-auto-insight-types-correlation.png)

## <a name="low-variance"></a>Baixa variância
Detecta os casos em que os pontos de dados não estão distantes da média.

![Exemplo de baixa variância](./media/end-user-insight-types/power-bi-low-variance.png)

## <a name="majority-major-factors"></a>Maioria (Principais fatores)
Encontra casos em que a maioria de um valor total pode ser atribuída a um único fator quando dividida por outra dimensão.  

![Exemplo de fatores principais](./media/end-user-insight-types/pbi-auto-insight-types-majority.png)

## <a name="overall-trends-in-time-series"></a>Tendências gerais na série temporal
Detecta as tendências ascendentes ou descendentes em dados de série temporal.

![Exemplo de tendências gerais na série temporal](./media/end-user-insight-types/pbi-auto-insight-types-trend.png)

## <a name="seasonality-in-time-series"></a>Periodicidade na série temporal
Encontra padrões periódicos nos dados de série temporal, como periodicidade semanal, mensal ou anual.

![Exemplo de sazonalidade](./media/end-user-insight-types/pbi-auto-insight-types-seasonality-new.png)

## <a name="steady-share"></a>Compartilhamento constante
Realça os casos em que há uma correlação de pai-filho entre o compartilhamento de um valor do filho em relação ao valor geral do pai em uma variável contínua.

![Exemplo de compartilhamento constante](./media/end-user-insight-types/pbi-auto-insight-types-steadyshare.png)

## <a name="time-series-outliers"></a>Exceções da série temporal
Para dados em uma série temporal, detecta quando há datas ou horas específicas com valores significativamente diferentes dos outros valores de data/hora.

![Exemplo de exceções da série temporal](./media/end-user-insight-types/pbi-auto-insight-types-time-series-outliers.png)

## <a name="next-steps"></a>Próximas etapas
[Insights do Power BI](end-user-insights.md)

Mais perguntas? [Experimente a Comunidade do Power BI](https://community.powerbi.com/)

