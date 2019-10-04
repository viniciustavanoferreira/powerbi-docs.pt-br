---
title: Gráficos de dispersão, bolhas e de pontos no Power BI
description: Gráfico de dispersão, gráficos de pontos e gráficos de bolhas no Power BI
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: PVcfPoVE3Ys
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/24/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: d776425d4c19070c00658cbd588c5421d22a0057
ms.sourcegitcommit: e2de2e8b8e78240c306fe6cca820e5f6ff188944
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71192836"
---
# <a name="scatter-charts-bubble-charts-and-dot-plot-charts-in-power-bi"></a>Gráficos de dispersão, gráficos de bolhas e gráficos de pontos no Power BI

[!INCLUDE [power-bi-visuals-desktop-banner](../includes/power-bi-visuals-desktop-banner.md)]

Um gráfico de dispersão sempre tem dois eixos de valor para mostrar um conjunto de dados numéricos em um eixo horizontal e outro conjunto de valores numéricos em um eixo vertical. O gráfico exibe pontos na interseção de um valor numérico de x e y, combinando esses valores em pontos de dados individuais. O Power BI pode distribuir esses pontos de dados de maneira uniforme ou não pelo eixo horizontal. Ele depende dos dados que o gráfico representa.

Assista a este vídeo para ver Will criar um gráfico de dispersão e, em seguida, siga as etapas abaixo para criar uma.
   > [!NOTE]
   > Este vídeo usa uma versão mais antiga do Power BI Desktop.
   > 
   > 
<iframe width="560" height="315" src="https://www.youtube.com/embed/PVcfPoVE3Ys?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP" frameborder="0" allowfullscreen></iframe>

Você pode definir o número de pontos de dados até um máximo de 10 mil.  

## <a name="when-to-use-a-scatter-chart-bubble-chart-or-a-dot-plot-chart"></a>Quando usar um gráfico de dispersão ou de bolhas, um gráfico de pontos

### <a name="scatter-and-bubble-charts"></a>Gráficos de dispersão e bolhas

Um gráfico de dispersão mostra a relação entre dois valores numéricos. Um gráfico de bolhas substitui os pontos de dados por bolhas, com o *tamanho* de bolha representando uma terceira dimensão de dados adicional.

![Captura de tela de um exemplo de gráfico de bolhas.](media/power-bi-visualization-scatter/power-bi-bubble-chart.png)

Os gráficos de dispersão são uma ótima opção:

* Para mostrar as relações entre dois valores numéricos.

* Para plotar dois grupos de números como uma série de coordenadas X e Y.

* Para usar em vez de um gráfico de linhas quando desejar alterar a escala do eixo horizontal.

* Para transformar o eixo horizontal em uma escala logarítmica.

* Para exibir os dados da planilha que incluem pares ou conjuntos de valores agrupados.

    > [!TIP]
    > Em um gráfico de dispersão, é possível ajustar as escalas independentes dos eixos para exibir mais informações sobre os valores agrupados.

* Para mostrar padrões em grandes conjuntos de dados, por exemplo, mostrando exceções, clusters e tendências lineares ou não lineares.

* Para comparar grandes números de pontos de dados sem preocupação com o tempo.  Quanto mais dados você incluir em um gráfico de dispersão, melhores serão as comparações que você poderá fazer.

Além do que os gráficos de dispersão podem fazer por você, os gráficos de bolhas são uma ótima opção:

* Se os dados tiverem três séries de dados que contêm um conjunto de valores cada um.

* Para apresentar dados financeiros.  Os diferentes tamanhos de bolha são úteis para destacar visualmente os valores específicos.

* Para usar com quadrantes.

### <a name="dot-plot-charts"></a>Gráficos de pontos

Um gráfico de pontos é semelhante a um gráfico de bolhas e um gráfico de dispersão, mas é usado para plotar dados categóricos ao longo do eixo X.

![Captura de tela de um gráfico de pontos.](media/power-bi-visualization-scatter/power-bi-dot-plot.png)

Eles são uma ótima opção se você quiser incluir dados categóricos ao longo do eixo X.

## <a name="prerequisites"></a>Pré-requisitos

Este tutorial usa o [arquivo PBIX de exemplo de Análise de Varejo](http://download.microsoft.com/download/9/6/D/96DDC2FF-2568-491D-AAFA-AFDD6F763AE3/Retail%20Analysis%20Sample%20PBIX.pbix).

1. Na seção superior esquerda da barra de menus, selecione **Arquivo** > **Abrir**
   
2. Encontre sua cópia do **arquivo PBIX de exemplo de Análise de Varejo**

1. Abra o **arquivo PBIX de exemplo de Análise de Varejo** na exibição de relatório ![Captura de tela do ícone de exibição de relatório](media/power-bi-visualization-kpi/power-bi-report-view.png).

1. Selecionar ![Captura de tela da guia amarela.](media/power-bi-visualization-kpi/power-bi-yellow-tab.png) para adicionar uma nova página.


## <a name="create-a-scatter-chart"></a>Criar um gráfico de dispersão

1. Inicie em uma página de relatório em branco e, no painel **Campos**, selecione estes campos:

    * **Vendas** > **Vendas por pé quadrado**

    * **Vendas** > **Percentual de variância total de vendas**

    * **Distrito** > **Distrito**

    ![Captura de tela do gráfico de colunas de cluster, do painel Visualizações e do painel Campos com os campos selecionados marcados.](media/power-bi-visualization-scatter/power-bi-bar-chart.png)

1. No painel **Visualização**, selecione a ![Captura de tela do ícone do gráfico de dispersão.](media/power-bi-visualization-scatter/power-bi-scatter-chart-icon.png) para converter o gráfico de colunas de cluster em um gráfico de dispersão.

   ![Captura de tela do gráfico de colunas de cluster sendo transformando em um gráfico de dispersão.](media/power-bi-visualization-scatter/power-bi-scatter-new.png)

1. Arraste **Distrito** de **Detalhes** para **Legenda**.

    O Power BI exibe um gráfico de dispersão que plota a **% da Variação do Total de Vendas** no eixo Y e as **Vendas por Pé Quadrado** no eixo X. As cores do ponto de dados representam distritos:

    ![Captura de tela do gráfico de dispersão.](media/power-bi-visualization-scatter/power-bi-scatter2.png)

Agora vamos adicionar uma terceira dimensão.

## <a name="create-a-bubble-chart"></a>Criar um gráfico de bolhas

1. No painel **Campos**, arraste **Vendas** > **Vendas Deste Ano** > **Valor** para a caixa **Tamanho**. Os pontos de dados são expandidos para volumes proporcionais com o valor de vendas.

   ![Captura de tela do gráfico de dispersão sendo transformado em um gráfico de bolhas, adicionando o Valor de Vendas à caixa Tamanho.](media/power-bi-visualization-scatter/power-bi-scatter-chart-size.png)

1. Focalize uma bolha. O tamanho da bolha reflete o valor das **Vendas Deste Ano**.

    ![exibição de dicas de ferramenta](media/power-bi-visualization-scatter/pbi-scatter-chart-hover.png)

1. Para definir o número de pontos de dados a serem mostrados em seu gráfico de bolhas, na seção **Formato** do painel **Visualizações**, expanda o cartão **Geral** e ajuste o **Volume de Dados**.

    ![Captura de tela do painel Visualizações com o ícone de Formato, lista suspensa Geral e opção de Volume de dados destacados.](media/power-bi-visualization-scatter/pbi-scatter-data-volume.png)

    É possível definir o volume máximo de dados para qualquer número até 10.000. Para garantir um bom desempenho ao definir os números mais altos, faça um teste antes.

    > [!NOTE]
    > Mais pontos de dados podem significar um tempo de carregamento mais longo. Se você optar por publicar relatórios com limites na extremidade mais elevada da escala, teste seus relatórios em toda a Web e dispositivos móveis também. Você deseja confirmar se o desempenho do gráfico corresponde às expectativas dos usuários.

1. É possível [formatar as cores de visualização, os rótulos, os títulos, a tela de fundo e muito mais](service-getting-started-with-color-formatting-and-axis-properties.md).

    Para [melhorar a acessibilidade](../desktop-accessibility.md), considere adicionar formas de marcador a cada linha. Para selecionar a forma do marcador, expanda **Formas**, selecione **Forma do marcador** e, em seguida, selecione uma forma.

    ![Captura de tela da lista suspensa de Formas com as opções de Forma do marcador destacadas.](media/power-bi-visualization-scatter/pbi-scatter-marker.png)

    Você pode alterar a forma do marcador para losango, triângulo ou quadrado. Usar uma forma de marcador diferente para cada linha torna mais fácil para os consumidores do relatório diferenciar as linhas (ou áreas) umas das outras.

## <a name="create-a-dot-plot-chart"></a>Criar um gráfico de pontos

Para criar um gráfico de pontos, substitua o campo numérico do **eixo X** por um campo categórico.

No painel **eixo X**, remova **Vendas por pé quadrado** e substitua por **Distrito** > **Gerente de distrito**.

![Captura de tela de um novo gráfico de pontos.](media/power-bi-visualization-scatter/power-bi-dot-plot-squares.png)

## <a name="considerations-and-troubleshooting"></a>Considerações e solução de problemas

### <a name="your-scatter-chart-has-only-one-data-point"></a>O gráfico de dispersão tem apenas um ponto de dados

O gráfico de dispersão contém apenas um ponto de dados que agrega todos os valores nos eixos X e Y?  Ou talvez ele agrega todos os valores em uma linha horizontal ou vertical?

![Captura de tela de um gráfico de dispersão com um ponto de dados.](media/power-bi-visualization-scatter/pbi-scatter-tshoot1.png)

Adicione um campo à caixa **Detalhes** para informar o Power BI como agrupar os valores. O campo deve ser exclusivo para cada ponto que você deseja plotar. Um simples número de linha ou campo de ID serve.

![Captura de tela de um gráfico de dispersão com RowNum adicionado à caixa Detalhes.](media/power-bi-visualization-scatter/pbi-scatter-tshoot.png)

Se você não tiver isso em seus dados, crie um campo que concatena os valores X e Y juntos em algo exclusivo por ponto:

![Captura de tela de um gráfico de dispersão com TempTime adicionado à caixa Detalhes.](media/power-bi-visualization-scatter/pbi-scatter-tshoot2.png)

Para criar um novo campo, [use o Editor de Consultas do Power BI Desktop para adicionar uma Coluna de Índice](../desktop-add-custom-column.md) ao conjunto de dados. Em seguida, adicione essa coluna à caixa de visualização **Detalhes**.

## <a name="next-steps"></a>Próximas etapas

* [Amostragem de alta densidade em gráficos de dispersão do Power BI](desktop-high-density-scatter-charts.md)

* [Tipos de visualização no Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)

Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)
