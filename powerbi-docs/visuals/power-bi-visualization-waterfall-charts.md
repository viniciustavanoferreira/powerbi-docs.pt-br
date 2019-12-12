---
title: Gráficos de cascata no Power BI
description: Gráficos de cascata no Power BI
author: mihart
ms.reviewer: ''
featuredvideoid: maTzOJSRB3g
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 12/5/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 6abca661a1553bfabc3da35fe714ff9bced5555a
ms.sourcegitcommit: 212fb4a46af3e434a230331f18456c6a49a408fd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/07/2019
ms.locfileid: "74907582"
---
# <a name="waterfall-charts-in-power-bi"></a>Gráficos de cascata no Power BI

[!INCLUDE [power-bi-visuals-desktop-banner](../includes/power-bi-visuals-desktop-banner.md)]

Os gráficos de cascata mostram o total em execução à medida que o Power BI adiciona ou subtrai valores. São úteis para entender como um valor inicial (como a receita líquida) é afetado por uma série de alterações positivas e negativas.

As colunas são codificadas por cores para que você possa notar rapidamente aumentos e diminuições. As colunas dos valores inicial e final às vezes [começam no eixo horizontal](https://support.office.com/article/Create-a-waterfall-chart-in-Office-2016-for-Windows-8de1ece4-ff21-4d37-acd7-546f5527f185#BKMK_Float "iniciar no eixo horizontal"), enquanto os valores intermediários são colunas flutuantes. Devido a esse estilo, os gráficos de cascata também são chamados de gráficos de ponte.

   > [!NOTE]
   > Este vídeo usa uma versão mais antiga do Power BI Desktop.
   > 
   > 

<iframe width="560" height="315" src="https://www.youtube.com/embed/qKRZPBnaUXM" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>

## <a name="when-to-use-a-waterfall-chart"></a>Ao usar um gráfico de cascata

Os gráficos de cascata são uma ótima opção:

* Quando houver alterações para a medida ao longo do tempo, uma série ou categorias diferentes.

* Para auditar as principais alterações que contribuem para o valor total.

* Para traçar o lucro anual da empresa, mostrando várias fontes de receita e chegar ao lucro total (ou perda).

* Para ilustrar o início e final do número de funcionários de sua empresa em um ano.

* Para visualizar o quanto você ganha e gasta mensalmente, e o saldo parcial da sua conta.

## <a name="prerequisite"></a>Pré-requisito

Este tutorial usa o [arquivo PBIX de exemplo de Análise de Varejo](https://download.microsoft.com/download/9/6/D/96DDC2FF-2568-491D-AAFA-AFDD6F763AE3/Retail%20Analysis%20Sample%20PBIX.pbix).

1. Na seção superior esquerda da barra de menus, selecione **Arquivo** > **Abrir**
   
2. Encontre sua cópia do **arquivo PBIX de exemplo de Análise de Varejo**

1. Abra o **arquivo PBIX de exemplo de Análise de Varejo** na exibição de relatório ![Captura de tela do ícone de exibição de relatório](media/power-bi-visualization-kpi/power-bi-report-view.png).

1. Selecionar ![Captura de tela da guia amarela.](media/power-bi-visualization-kpi/power-bi-yellow-tab.png) para adicionar uma nova página.


## <a name="create-a-waterfall-chart"></a>Criar um gráfico de cascata

Crie um gráfico de cascata que exibe a variação de vendas (vendas estimadas versus vendas reais) por mês.

### <a name="build-the-waterfall-chart"></a>Criar o gráfico de cascata

1. No painel **Campos**, selecione **Vendas** > **Variação do Total de Vendas**.

   ![Captura de tela de vendas > Variação do Total de Vendas selecionada e o visual resultante.](media/power-bi-visualization-waterfall-charts/power-bi-bar.png)

1. Selecione o ícone de cascata ![Captura de tela do ícone de cascata](media/power-bi-visualization-waterfall-charts/power-bi-waterfall-icon.png)

    ![Modelos de visualização](media/power-bi-visualization-waterfall-charts/convert-waterfall.png)

1. Selecione **Hora** > **FiscalMonth** para adicioná-la à caixa **Categoria**.

    ![cascata](media/power-bi-visualization-waterfall-charts/power-bi-waterfall-month.png)

### <a name="sort-the-waterfall-chart"></a>Classificar o gráfico de cascata

1. Certifique-se de que o Power BI classifique o gráfico de cascata em ordem cronológica por mês. No canto superior direito do gráfico, selecione **Mais opções** (...).

    Para este exemplo, selecione **Classificar por** e escolha **FiscalMonth**. Um indicador amarelo ao lado de sua seleção indica quando a opção de seleção está sendo aplicada.

    ![Selecione classificar por > FiscalMonth](media/power-bi-visualization-waterfall-charts/power-bi-sort-by-fiscalmonth.png)
    
    Para exibir os meses em ordem cronológica, selecione **Classificação crescente**. Assim como na etapa anterior, verifique se há um indicador amarelo ao lado esquerdo de **Classificação crescente**. Isso indica que a opção selecionada está sendo aplicada.

    ![Selecione Classificar por > Ordem crescente](media/power-bi-visualization-waterfall-charts/power-bi-waterfall-ascending.png)

    

    Observe que seu gráfico está classificado de janeiro a agosto com relação ao FiscalMonth.  

### <a name="explore-the-waterfall-chart"></a>Explorar o gráfico de cascata

Aprofunde-se um pouco mais para ver o que está contribuindo mais para as alterações a cada mês.

1.  Selecione **Repositório** > **Território**, que adicionará **Território** ao bucket **Divisão**.

    ![Mostra Repositório no bucket de Divisão](media/power-bi-visualization-waterfall-charts/power-bi-waterfall-breakdown.png)

    O Power BI usa o valor em **Divisão** para adicionar mais dados à visualização. Ele adiciona os cinco principais colaboradores dos aumentos ou diminuições para cada mês fiscal. Isso significa que fevereiro, por exemplo, agora tem seis pontos de dados, em vez de apenas um.  

    ![Mostra Repositório no bucket de Divisão](media/power-bi-visualization-waterfall-charts/power-bi-waterfall-breakdown-default.png)

    Digamos que você esteja interessado apenas nos dois colaboradores principais.

1. No painel **Formato**, selecione **Divisão** e defina **Divisões máximas** para **2**.

    ![Formato > Divisão](media/power-bi-visualization-waterfall-charts/power-bi-waterfall-breakdown-two.png)

    Uma rápida análise revela que as regiões de Ohio e Pensilvânia são os maiores colaboradores para a movimentação, negativa e positiva, em nosso gráfico de cascata.

    ![gráfico de cascata](media/power-bi-visualization-waterfall-charts/power-bi-axis-waterfall.png)

## <a name="next-steps"></a>Próximas etapas

* [Alterar como os visuais interagem em um relatório do Power BI](../service-reports-visual-interactions.md)

* [Tipos de visualização no Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)
