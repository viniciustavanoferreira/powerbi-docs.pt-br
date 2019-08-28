---
title: Gráficos de cascata no Power BI
description: Gráficos de cascata no Power BI
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: maTzOJSRB3g
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/24/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: c9ad87d851f52db6cd2720c9e3bd5d4bb7b189a7
ms.sourcegitcommit: 58c649ec5fd2447a0f9ca4c4d45a0e9fff2f1b6a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/27/2019
ms.locfileid: "67408877"
---
# <a name="waterfall-charts-in-power-bi"></a>Gráficos de cascata no Power BI

Os gráficos de cascata mostram o total em execução à medida que o Power BI adiciona ou subtrai valores. São úteis para entender como um valor inicial (como a receita líquida) é afetado por uma série de alterações positivas e negativas.

As colunas são codificadas por cores para que você possa notar rapidamente aumentos e diminuições. Com frequência, as colunas de valor inicial e final [iniciam-se no eixo horizontal](https://support.office.com/article/Create-a-waterfall-chart-in-Office-2016-for-Windows-8de1ece4-ff21-4d37-acd7-546f5527f185#BKMK_Float "iniciam-se no eixo horizontal"), enquanto os valores intermediários são colunas flutuantes. Devido a esse estilo, os gráficos de cascata também são chamados de gráficos de ponte.

<iframe width="560" height="315" src="https://www.youtube.com/embed/qKRZPBnaUXM" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>

## <a name="when-to-use-a-waterfall-chart"></a>Ao usar um gráfico de cascata

Os gráficos de cascata são uma ótima opção:

* Quando houver alterações para a medida ao longo do tempo, uma série ou categorias diferentes.

* Para auditar as principais alterações que contribuem para o valor total.

* Para traçar o lucro anual da empresa, mostrando várias fontes de receita e chegar ao lucro total (ou perda).

* Para ilustrar o início e final do número de funcionários de sua empresa em um ano.

* Para visualizar o quanto você ganha e gasta mensalmente, e o saldo parcial da sua conta.

## <a name="prerequisites"></a>Pré-requisitos

* O serviço do Power BI ou o Power BI Desktop

* Relatório Exemplo de Análise de Varejo

## <a name="get-the-retail-analysis-sample-report"></a>Obter o relatório de exemplo de Análise de Varejo

Essas instruções usam o exemplo de análise de varejo. Criar uma visualização requer permissões de edição para o conjunto de dados e o relatório. Felizmente, os exemplos do Power BI são todos editáveis. Se alguém compartilhar um relatório com você, é possível criar visualizações em relatórios. Para acompanhar, obtenha o [Relatório de exemplo de Análise de Varejo](../sample-datasets.md).

Após obter o conjunto de dados do **Exemplo de Análise de Varejo**, você pode começar a usar.

## <a name="create-a-waterfall-chart"></a>Criar um gráfico de cascata

Crie um gráfico de cascata que exibe a variação de vendas (vendas estimadas versus vendas reais) por mês.

1. No **Meu Workspace**, selecione **Conjuntos de dados** > **Criar um relatório**.

    ![Captura de tela de conjuntos de dados > Criar um relatório.](media/power-bi-visualization-waterfall-charts/power-bi-create-a-report.png)

1. No painel **Campos**, selecione **Vendas** > **Variação do Total de Vendas**.

   ![Captura de tela de vendas > Variação do Total de Vendas selecionada e o visual resultante.](media/power-bi-visualization-waterfall-charts/power-bi-first-value.png)

1. Selecione o ícone de cascata ![Captura de tela do ícone de cascata](media/power-bi-visualization-waterfall-charts/power-bi-waterfall-icon.png) para converter o gráfico em um mapa de árvore.

    Se a **Variação Total de Vendas** não estiver na área do **eixo Y**, arraste-a para lá.

    ![Modelos de visualização](media/power-bi-visualization-waterfall-charts/convertwaterfall.png)

1. Selecione **Hora** > **FiscalMonth** para adicioná-la à caixa **Categoria**.

    ![cascata](media/power-bi-visualization-waterfall-charts/power-bi-waterfall.png)

1. Verifique se o Power BI classificou o gráfico de cascata em ordem cronológica. No canto superior direito do gráfico, selecione as reticências (...).

    Verifique se há um indicador amarelo ao lado esquerdo das opções **Classificar em ordem crescente** e **FiscalMonth**

    ![Selecione classificar por > FiscalMonth](media/power-bi-visualization-waterfall-charts/power-bi-sort-by.png)

    Você também pode examinar os valores do eixo X e ver se estão na ordem de **Jan** à **Ago**.

    Aprofunde-se um pouco mais para ver o que está contribuindo mais para as alterações a cada mês.

1. Arraste **Repositório** > **Região** para o bucket **Divisão**.

    ![Mostra Repositório no bucket de Divisão](media/power-bi-visualization-waterfall-charts/power-bi-waterfall-breakdown.png)

    Por padrão, o Power BI adiciona os cinco principais colaboradores a aumentos ou diminuições por mês.

    ![Mostra Repositório no bucket de Divisão](media/power-bi-visualization-waterfall-charts/power-bi-waterfall-breakdown-initial.png)

    Você está interessado apenas nos dois colaboradores principais.

1. No painel **Formato**, selecione **Divisão** e defina **Divisões máximas** para **2**.

    ![Formato > Divisão](media/power-bi-visualization-waterfall-charts/power-bi-waterfall-breakdown-maximum.png)

    Uma rápida análise revela que as regiões de Ohio e Pensilvânia são os maiores colaboradores para a movimentação, negativa e positiva, em nosso gráfico de cascata.

    ![gráfico de cascata](media/power-bi-visualization-waterfall-charts/power-bi-waterfall-axis.png)

    É uma descoberta interessante. Ohio e Pensilvânia têm um impacto significativo devido às vendas nessas duas regiões serem muito maiores do que nas outras? Você pode verificar isso.

1. Crie um mapa que examina o valor de vendas deste ano e as vendas do último ano por território.

    ![close-up do mapa em PA e Ohio](media/power-bi-visualization-waterfall-charts/power-bi-map.png)

    O mapa corrobora a teoria. Ele mostra que essas duas regiões tiveram o valor mais alto de vendas no ano passado (tamanho da bolha) e neste ano (sombreamento da bolha).

## <a name="highlighting-and-cross-filtering"></a>Realce e filtragem cruzada

Para obter informações sobre como usar o painel **Filtros**, veja [Adicionar um filtro a um relatório no modo de exibição de Edição](../power-bi-report-add-filter.md).

Realçar uma coluna em um gráfico de cascata faz a filtragem cruzada dos filtros com outras visualizações na página do relatório e vice-versa. No entanto, a coluna **Total** não dispara o realce ou responde à filtragem cruzada.

## <a name="next-steps"></a>Próximas etapas

* [Alterar como os visuais interagem em um relatório do Power BI](../service-reports-visual-interactions.md)

* [Tipos de visualização no Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)
