---
title: Exemplos de visuais do Power BI
description: Este artigo apresenta exemplos de visuais do Power BI, incluindo segmentações, mais de 20 tipos de gráficos, WebGL e visuais e scripts R.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 03/17/2019
ms.openlocfilehash: 5e2ad0fa43a186be76a58f1ab3bb4bf054a677a5
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83132076"
---
# <a name="samples-of-power-bi-visuals"></a>Exemplos de visuais do Power BI

Você pode baixar, usar e modificar esses visuais do Power BI pelo GitHub. Esses exemplos ilustram como lidar com situações comuns ao desenvolver com Power BI.

## <a name="slicers"></a>Segmentações

Uma segmentação restringe a parte dos dados que é mostrada nas outras visualizações de um relatório. As segmentações são uma das várias maneiras de filtrar dados no Power BI.

| <img src="media/samples/chiclet-slicer.png" width="200">  | <img src="media/samples/timeline-slicer.png" width="200"> | <img src="media/samples/sample-slicer.png" width="200">|
| ------------- | ------------- | -------------|
| [Chiclet Slicer](https://github.com/Microsoft/powerbi-visuals-chicletslicer/)  </br>Exibir botões de imagem ou de texto que agem como um filtro na tela nos outros visuais | [Segmentação da linha do tempo](https://github.com/Microsoft/powerbi-visuals-timeline/) </br>Seletor de intervalo de data gráfico que filtra por data | [Exemplo de segmentação](https://github.com/Microsoft/powerbi-visuals-sampleslicer/) </br>Demonstra o uso da API de Filtragem Avançada

## <a name="charts"></a>Gráficos

Inspire-se com nossa galeria, que inclui gráficos de barras, gráficos de pizza, Nuvem de Palavras e outros.

| <img src="media/samples/aster-plot.png" width="200">  | <img src="media/samples/bullet-chart.png" width="200"> | <img src="media/samples/Chord.png" width="200">|
| ------------- | ------------- | -------------|
| [Aster Plot](https://github.com/Microsoft/powerbi-visuals-asterplot/)  </br>Uma curva em um gráfico de rosca padrão que usa um segundo valor para orientar o ângulo de flecha | [Bullet chart ](https://github.com/Microsoft/powerbi-visuals-bulletchart/) </br>Um gráfico de barras com elementos visuais adicionais que fornecem contexto útil para metas de controle | [Chord](https://github.com/Microsoft/powerbi-visuals-chord/) </br>Um método gráfico que exibe as relações entre os dados em uma matriz
| <img src="media/samples/dot-plot.png" width="200"> | <img src="media/samples/dual-kpi.png" width="200">| <img src="media/samples/enhanced-scatter.png" width="200"> 
| [Dot plot](https://github.com/Microsoft/powerbi-visuals-dotplot/) </br>Mostra a distribuição de frequências com uma apresentação excelente | [Dual KPI](https://github.com/Microsoft/powerbi-visuals-dualkpi/) </br>Visualiza com eficiência duas medidas ao longo do tempo, mostrando suas tendências em uma linha do tempo conjunta | [Enhanced Scatter](https://github.com/Microsoft/powerbi-visuals-enhancedscatter/) </br>Aprimoramentos no gráfico de dispersão existente
| <img src="media/samples/forcegraph.png" width="200">| <img src="media/samples/gantt.png" width="200">| <img src="media/samples/table-heatmap.png" width="200">
| [Force Graph](https://github.com/Microsoft/powerbi-visuals-forcegraph/) </br>Diagrama de layout de forças com caminho curvado, o que é útil para mostrar conexões entre entidades | [Gantt](https://github.com/Microsoft/powerbi-visuals-gantt/) </br>Um gráfico de barras que ilustra uma linha do tempo ou um agendamento de projeto com recursos | [Table Heatmap](https://github.com/Microsoft/powerbi-visuals-heatmap/) </br>Compare dados de modo fácil e intuitivo usando cores em uma tabela
| <img src="media/samples/histogram-chart.png" width="200"> | <img src="media/samples/linedot-chart.png" width="200"> | <img src="media/samples/mekko-chart.png" width="200"> 
| [Histogram chart](https://github.com/Microsoft/powerbi-visuals-histogram/) </br>Visualiza a distribuição de dados em um intervalo contínuo ou em um período determinado | [Gráfico LineDot](https://github.com/Microsoft/powerbi-visuals-linedotchart/) </br>Um gráfico de linhas animado com pontos animados que estimulam o envolvimento de um público com os dados | [Gráfico do Mekko](https://github.com/Microsoft/powerbi-visuals-mekkochart/) </br>Uma mistura de gráfico de colunas 100% empilhado e gráfico de barras 100% empilhado combinados em uma exibição
| <img src="media/samples/multikpi.png" width="200"> | <img src="media/samples/powerkpi.png" width="200"> | <img src="media/samples/powerkpi-matrix.png" width="200"> 
| [Vários KPIs](https://github.com/microsoft/PowerBI-visuals-MultiKPI/) </br> Uma visualização de vários KPIs avançada com um KPI principal junto a vários minigráficos de dados de suporte | [Power KPI](https://github.com/microsoft/PowerBI-visuals-PowerKPI/) </br>Um eficiente Indicador de KPI com gráfico de várias linhas e rótulos para a data atual, o valor e as variações | [Power KPI Matrix](https://github.com/microsoft/PowerBI-visuals-PowerKPIMatrix/) </br>Monitore scorecards balanceados e um número ilimitado de métricas e KPIs em uma lista compacta e fácil de ler
| <img src="media/samples/pulse-chart.png" width="200">| <img src="media/samples/radar-chart.png" width="200"> | <img src="media/samples/sankey-chart.png" width="200"> 
| [Gráfico de pulso](https://github.com/Microsoft/powerbi-visuals-pulsechart/) </br>Esse gráfico de linhas anotado com eventos principais é perfeito para contar uma história usando dados| [Gráfico de radar](https://github.com/Microsoft/powerbi-visuals-radarchart/) </br>Apresente várias medidas plotadas ao longo de um eixo de categorias, o que é útil para comparar atributos | [Gráfico de Sankey](https://github.com/Microsoft/powerbi-visuals-sankey/) </br>Diagrama de fluxo no qual a largura da série é proporcional à quantidade do fluxo
| <img src="media/samples/stream-graph.png" width="200"> | <img src="media/samples/sunburst.png" width="200">| <img src="media/samples/tornado.png" width="200">
| [Gráfico de fluxo](https://github.com/Microsoft/powerbi-visuals-streamgraph/) </br>Um gráfico de área empilhado com interpolação suave, geralmente usado para mostrar valores ao longo do tempo | [Sunburst chart](https://github.com/Microsoft/powerbi-visuals-sunburst/) </br>Gráfico de rosca de vários níveis para visualizar dados hierárquicos| [Tornado chart](https://github.com/Microsoft/powerbi-visuals-tornado/) </br>Compare a importância relativa de variáveis entre dois grupos
 | <img src="media/samples/word-cloud.png" width="200">
 | [Word Cloud](https://github.com/Microsoft/powerbi-visuals-wordcloud/) </br>Crie um visual divertido com o texto frequente em seus dados

## <a name="webgl"></a>WebGL

O WebGL permite que o conteúdo da Web use uma API baseada no OpenGL ES 2.0 para fazer renderização 2D e 3D em uma tela HTML.

| <img src="media/samples/globe-map.png" width="250">|
| ------------- |
| [Globe Map](https://github.com/Microsoft/powerbi-visuals-globemap/) </br>Plotar locais em um mapa 3D interativo

## <a name="r-visuals"></a>Visuais do R

Estes exemplos demonstram como aproveitar a capacidade analítica e visual de scripts e visuais R.

| <img src="media/samples/association-rules.png" width="200">| <img src="media/samples/clustering.png" width="200">| <img src="media/samples/clustering-with-outliers.png" width="200">|
|------------- |------------- |------------- |------------- |
| [Association rules](https://github.com/Microsoft/powerbi-visuals-assorules/) </br>Descobrir relações entre dados aparentemente não relacionados usando instruções if-then | [Clustering](https://github.com/Microsoft/powerbi-visuals-clustering-kmeans/) </br>Localize grupos de similaridade em seus dados usando o algoritmo k-means | [Clustering with outliers](https://github.com/microsoft/PowerBI-visuals-dbscan/) </br>Encontre grupos de semelhanças e exceções em seus dados
| <img src="media/samples/correlation-plot.png" width="200"> | <img src="media/samples/decision-tree-chart.png" width="200"> | <img src="media/samples/forecasting-tbats.png" width="200"> 
| [Correlation plot](https://github.com/Microsoft/powerbi-visuals-corrplot/) </br>Realce as variáveis mais correlacionadas em uma tabela de dados | [Decision tree chart](https://github.com/Microsoft/powerbi-visuals-decision-tree/) </br>Diagrama esquemático em forma de árvore para determinar a probabilidade estatística usando particionamento recursivo | [Forecasting TBATS](https://github.com/Microsoft/powerbi-visuals-forcasting-tbats/) </br>Previsão de série temporal para séries que têm várias sazonalidades usando o modelo TBATS
| <img src="media/samples/forecasting-with-ARIMA.png" width="200"> | <img src="media/samples/funnel-plot.png" width="200"> | <img src="media/samples/outliers-detection.png" width="200"> 
| [Forecasting with ARIMA](https://github.com/Microsoft/powerbi-visuals-forcastingarima/) </br>Preveja valores futuros com base em dados históricos usando a ARIMA (média de movimentação integrada de regressão automática) | [Funnel plot](https://github.com/Microsoft/powerbi-visuals-funnel/) </br>Localize exceções em seus dados usando um gráfico de funil | [Outliers detection](https://github.com/Microsoft/powerbi-visuals-outliers-det/) </br>Encontre exceções em seus dados usando o método e a plotagem mais apropriados
| <img src="media/samples/spline-chart.png" width="200"> | <img src="media/samples/time-series-decomposition-chart.png" width="200"> | <img src="media/samples/time-series-forecasting-chart.png" width="200">
| [Spline chart](https://github.com/Microsoft/powerbi-visuals-spline/) </br>Visualize e compreenda dados confusos | [Time series decomposition chart](https://github.com/Microsoft/powerbi-visuals-timeseriesdecomposition/) </br>Entenda os componentes da série temporal usando "Decomposição de tendência e sazonal usando perdas" | [Time series forecasting chart](https://github.com/Microsoft/powerbi-visuals-forcasting-exp/) </br>Usando um modelo de suavização exponencial para prever valores futuros com base em valores observados anteriormente

## <a name="next-steps"></a>Próximas etapas

Para experimentar a criação de visuais do Power BI, confira [Tutorial: Como desenvolver um visual no Power BI](custom-visual-develop-tutorial.md).
