---
title: Tipos de Insights com suporte para o Power BI
description: Quick Insights e View Insights com o Power BI.
author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 02/24/2020
ms.author: mihart
LocalizationGroup: Dashboards
ms.openlocfilehash: a89cb77b99356f9f282b522c2041e96210a026e9
ms.sourcegitcommit: 4d98274aa0b9aa09db99add2dda91a3ba8fed40b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/25/2020
ms.locfileid: "77576772"
---
# <a name="types-of-insights-supported-by-power-bi"></a>Tipos de Insights com suporte para o Power BI

Você pode pedir ao Power BI que examine seus dados e encontre tendências e padrões interessantes. Essas tendências e esses padrões são apresentados na forma de visuais chamados *Insights*. 

Para saber como usar os Insights, confira [Insights do Power BI](end-user-insights.md)

![um conjunto de Insights](media/end-user-insight-types/power-bi-insight.png)

## <a name="how-does-insights-work"></a>Como o Insights funciona?
O Power BI pesquisa rapidamente diferentes subconjuntos do conjunto de dados. À medida que ele pesquisa, o Power BI aplica um conjunto de algoritmos sofisticados para descobrir insights potencialmente interessantes. Os *consumidores* do Power BI podem executar os Insights em blocos de dashboard.

## <a name="some-terminology"></a>Um pouco de terminologia
O Power BI usa algoritmos estatísticos para descobrir Insights. Os algoritmos são listados e descritos na próxima seção deste artigo. Antes de chegarmos aos algoritmos, vejamos as definições de alguns termos que talvez não sejam conhecidos. 

* **Medida**: uma medida é um campo quantitativo (numérico) que pode ser usado para fazer cálculos. Os cálculos comuns são soma, média e mínimo. Por exemplo, se nossa empresa fabrica e vende skates, nossas medidas podem ser o número de skates vendidos e o lucro médio por ano.  
* **Dimensão**: as dimensões são dados categóricos (texto). Uma dimensão descreve uma pessoa, um objeto, um item, produtos, um lugar e um período. Em um conjunto de dados, as dimensões são uma maneira de agrupar *medidas* em categorias úteis. Para nossa empresa de skates, algumas dimensões podem incluir a análise de vendas (uma medida) por modelo, cor, país ou campanha de marketing.   
* **Correlação**: uma correlação nos informa como o comportamento dos itens está relacionado.  Se os padrões de aumento e diminuição são semelhantes, eles estão correlacionados positivamente. E se os padrões são opostos, eles estão correlacionados negativamente. Por exemplo, se as vendas de nossos skates vermelhos aumentam toda vez que fazemos uma campanha de marketing na TV, as vendas dos skates vermelhos e a campanha de TV estão correlacionadas positivamente.
* **Série temporal**: uma série temporal é uma maneira de exibir o tempo como pontos de dados sucessivos. Esses pontos de dados podem ser incrementos, como segundos, horas, meses ou anos.  
* **Variável contínua**: uma variável contínua pode ser qualquer valor entre os limites mínimo e máximo; caso contrário, é uma variável discreta. Entre os exemplos estão temperatura, peso, idade e tempo. As variáveis contínuas podem incluir frações ou partes do valor. O número total de skates azuis vendidos é uma variável discreta, já que não podemos vender metade de um skate.  

## <a name="what-types-of-insights-can-you-find"></a>Quais tipos de insights é possível encontrar?
Esses são os algoritmos usados pelo Power BI. 

### <a name="category-outliers-topbottom"></a>Exceções de categoria (superior/inferior)
Realça os casos em que uma ou duas categorias têm valores muito maiores do que outras categorias.  

![Exemplo de exceções de categoria](./media/end-user-insight-types/pbi-auto-insight-types-category-outliers.png)

### <a name="change-points-in-a-time-series"></a>Alterar os pontos em uma série temporal
Realça os casos em que há alterações significativas nas tendências em uma série temporal de dados.

![Exemplo de alterar pontos em uma série temporal](./media/end-user-insight-types/pbi-auto-insight-types-changepoint.png)

### <a name="correlation"></a>Correlação
Detecta casos em que várias medidas mostram um padrão ou uma tendência semelhante quando plotadas em uma categoria ou um valor no conjunto de dados.

![Exemplo de correlação](./media/end-user-insight-types/pbi-auto-insight-types-correlation.png)

### <a name="low-variance"></a>Baixa variância
Detecta casos em que os pontos de dados de uma dimensão não estão longe da média, assim, a "variação" é baixa. Digamos que você tenha a medida "vendas" e uma dimensão "região". E ao analisar a região, você percebe que há uma diferença muito pequena entre os pontos de dados e a média (dos pontos de dados). Esse insight é disparado quando a variação das vendas em todas as regiões está abaixo de um limite. Em outras palavras, quando as vendas são muito semelhantes em todas as regiões.

![Exemplo de baixa variância](./media/end-user-insight-types/power-bi-low-variance.png)

### <a name="majority-major-factors"></a>Maioria (Principais fatores)
Encontra casos em que a maioria de um valor total pode ser atribuída a um único fator quando dividida por outra dimensão.  

![Exemplo de fatores principais](./media/end-user-insight-types/pbi-auto-insight-types-majority.png)

### <a name="overall-trends-in-time-series"></a>Tendências gerais na série temporal
Detecta as tendências ascendentes ou descendentes em dados de série temporal.

![Exemplo de tendências gerais na série temporal](./media/end-user-insight-types/pbi-auto-insight-types-trend.png)

### <a name="seasonality-in-time-series"></a>Periodicidade na série temporal
Encontra padrões periódicos nos dados de série temporal, como periodicidade semanal, mensal ou anual.

![Exemplo de sazonalidade](./media/end-user-insight-types/pbi-auto-insight-types-seasonality-new.png)

### <a name="steady-share"></a>Compartilhamento constante
Realça os casos em que há uma correlação de pai-filho entre o compartilhamento de um valor do filho em relação ao valor geral do pai em uma variável contínua. Um insight de compartilhamento constante é aplicado ao contexto de uma medida, dimensão e de outra dimensão de data/hora. Esse insight é disparado quando determinado valor de dimensão, por exemplo, "a região nordeste", tem uma porcentagem constante de vendas gerais nessa dimensão de data/hora.

O insight de compartilhamento constante é semelhante ao insight de variação baixa, pois ambos estão relacionados à falta de variação de um valor ao longo do tempo. No entanto, o insight de compartilhamento constante mede a falta de variação do **percentual geral** ao longo do tempo, enquanto o insight de variação baixa mede a falta de variação dos valores de medidas absolutas em uma dimensão.

![Exemplo de compartilhamento constante](./media/end-user-insight-types/pbi-auto-insight-types-steadyshare.png)

### <a name="time-series-outliers"></a>Exceções da série temporal
Para dados em uma série temporal, detecta quando há datas ou horas específicas com valores significativamente diferentes dos outros valores de data/hora.

![Exemplo de exceções da série temporal](./media/end-user-insight-types/pbi-auto-insight-types-time-series-outliers.png)

## <a name="next-steps"></a>Próximas etapas
[Insights do Power BI](end-user-insights.md)

Mais perguntas? [Experimente a Comunidade do Power BI](https://community.powerbi.com/)

