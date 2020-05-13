---
title: Gráficos de linhas no Power BI
description: Gráficos de linhas no Power BI
author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/05/2020
ms.author: rien
LocalizationGroup: Visualizations
ms.openlocfilehash: 9f7cd6c277a02ce4e44db40930184cce955e5948
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83274180"
---
# <a name="line-charts-in-power-bi"></a>Gráficos de linhas no Power BI

[!INCLUDE[consumer-appliesto-nyyn](../includes/consumer-appliesto-nyyn.md)]

Um gráfico de linhas é uma série de pontos de dados representada por pontos e conectada por linhas retas. Um gráfico de linhas pode ter uma ou muitas linhas. Os gráficos de linhas têm um eixo X e um eixo Y. 

![gráfico de linhas simples](media/power-bi-line-charts/power-bi-line.png)



## <a name="create-a-line-chart"></a>Criar um gráfico de linhas
Essas instruções usam o aplicativo Exemplo de Vendas e Marketing para criar um gráfico de linhas que exibe as vendas deste ano por categoria. Para acompanhar, obtenha o aplicativo de exemplo em appsource.com.

> [!NOTE]
> Compartilhar seu relatório com um colega do Power BI exige que você tenha licenças de Power BI Pro individuais ou que o relatório seja salvo na capacidade Premium.

1. Comece em uma página de relatório em branco. Caso esteja usando o serviço do Power BI, abra o relatório no [Modo de Exibição de Edição](../create-reports/service-interact-with-a-report-in-editing-view.md).

2. No painel Campos, selecione **SalesFact** \> **Total de unidades**e selecione **Data** > **Mês**.  O Power BI cria um gráfico de colunas na tela do relatório.

    ![Selecione no painel Campos](media/power-bi-line-charts/power-bi-step1.png)

4. Converta em um gráfico de linhas selecionando o modelo de gráfico de linhas no painel Visualizações. 

    ![converter em um gráfico de linhas](media/power-bi-line-charts/power-bi-convert-to-line.png)
   

4. Filtre o gráfico de linhas para mostrar os dados nos anos 2012-2014. Se o painel Filtros estiver recolhido, expanda-o agora. No painel Campos, selecione **Data** \> **Ano** e arraste para o painel Filtros. Solte-o sob o título **Filtros neste visual**. 
     
    ![linha ao lado do painel Campos](media/power-bi-line-charts/power-bi-year-filter.png)

    Altere os **Filtros avançados** para **Filtros básicos** e selecione **2012**, **2013** e **2014**.

    ![Filtrar por ano](media/power-bi-line-charts/power-bi-filter-year.png)

6. Opcionalmente, [ajuste o tamanho e a cor do texto do gráfico](power-bi-visualization-customize-title-background-and-legend.md). 

    ![Aumentar o tamanho da fonte e alterar a fonte do eixo Y](media/power-bi-line-charts/power-bi-line-3years.png)

## <a name="add-additional-lines-to-the-chart"></a>Adicionar linhas adicionais ao gráfico
Os gráficos de linhas podem ter muitas linhas diferentes. E, em alguns casos, os valores nas linhas podem ser tão divergentes que não são exibidos bem juntos. Vamos dar uma olhada na adição de linhas adicionais a nosso gráfico atual e, em seguida, saiba como formatar o gráfico quando os valores representados pelas linhas são muito diferentes. 

### <a name="add-additional-lines"></a>Adicionar linhas adicionais
Em vez de examinar o total de unidades para todas as regiões como uma única linha no gráfico, vamos dividir o total de unidades por região. Adicione mais linhas arrastando **Área geográfica** > **Região** para a caixa Legenda.

   ![Uma linha para cada região](media/power-bi-line-charts/power-bi-line-regions.png)


### <a name="use-two-y-axes"></a>Usar dois eixos Y
E se você quiser examinar o total de vendas e o total de unidades no mesmo gráfico? Os números de vendas são muito maiores do que os números de unidade, tornando o gráfico de linhas inutilizável. Na verdade, a linha vermelha para total de unidades parece ser zero.

   ![valores altamente divergentes](media/power-bi-line-charts/power-bi-diverging.png)

Para exibir valores altamente divergentes em um gráfico, use um gráfico de combinação. Você pode saber tudo sobre gráficos de combinação lendo [Gráficos de combinação no Power BI](power-bi-visualization-combo-chart.md). Em nosso exemplo abaixo, exibimos as vendas e o total de unidades juntos em um gráfico, adicionando um segundo eixo Y. 

   ![valores altamente divergentes](media/power-bi-line-charts/power-bi-dual-axes.png)

## <a name="highlighting-and-cross-filtering"></a>Realce e filtragem cruzada
Para obter informações sobre como usar o painel Filtros, veja [Adicionar um filtro a um relatório](../create-reports/power-bi-report-add-filter.md).

Selecionar um ponto de dados em um gráfico de linhas realiza o realce cruzado e a filtragem cruzada das outras visualizações na página do relatório e vice-versa. Para acompanhar, abra a guia **Participação no mercado**.  

Em um gráfico de linhas, um único ponto de dados é a interseção de um ponto no eixo X e Y. Quando você seleciona um ponto de dados, o Power BI adiciona marcadores indicando qual ponto (para uma única linha) ou pontos (se houver duas ou mais linhas) são a origem para o realce cruzado e filtragem cruzada de outros visuais na página do relatório. Se o visual for muito denso, o Power BI selecionará o ponto mais próximo de onde você clica no visual.

Neste exemplo, selecionamos um ponto de dados que abrange: Julho de 2014, percentual de unidades de Participação no mercado R12 de 33,16 e percentual de unidades de Participação de no mercado de 34,74.

![selecione um único ponto de dados em um gráfico de linhas](media/power-bi-line-charts/power-bi-single-select.png)

Observe como o gráfico de colunas é realçado de forma cruzada, e o medidor é filtrado de forma cruzada.

Para gerenciar como os gráficos são filtrados e realçados de forma cruzada entre si, veja [Interações de visualização em um relatório do Power BI](../create-reports/service-reports-visual-interactions.md)

## <a name="considerations-and-troubleshooting"></a>Considerações e solução de problemas
* Um gráfico de linhas não pode ter dois eixos Y.  Você precisará usar um gráfico de combinação em vez disso.
* Nos exemplos acima, os gráficos foram formatados para aumentar o tamanho da fonte, alterar a cor da fonte, adicionar títulos de eixo, centralizar o título do gráfico e legenda, iniciar ambos os eixos em zero e muito mais. O painel Formatação (ícone de rolo de tinta) tem um conjunto aparentemente interminável de opções para fazer com que seus gráficos tenham a aparência desejada. A melhor maneira de saber mais sobre isso é explorando o painel Formatação.

## <a name="next-steps"></a>Próximas etapas

[Tipos de visualização no Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)





