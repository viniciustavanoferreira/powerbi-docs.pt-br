---
title: Gráficos de medidor radial no Power BI
description: Gráficos de medidor radial no Power BI
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: xmja6Epqa
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/24/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 8b0db9aebe72d54aa464ec012e614ae0ec5bc723
ms.sourcegitcommit: 1c96b65a03ec0a0612e851dd58c363f4d56bca38
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/25/2019
ms.locfileid: "67390394"
---
# <a name="radial-gauge-charts-in-power-bi"></a>Gráficos de medidor radial no Power BI

Um gráfico de medidor radial tem um arco circular e mostra um único valor que acompanha o progresso em relação a um objetivo/KPI (indicador chave de desempenho). A linha (ou *agulha*) representa o valor de meta ou destino. O sombreamento representa o progresso em relação a esse objetivo. O valor dentro do arco representa o valor do progresso. O Power BI distribui uniformemente todos os valores possíveis ao longo do arco, do mínimo (valor mais à esquerda) para o máximo (valor mais à direita).

![Captura de tela de medidor radial.](media/power-bi-visualization-radial-gauge-charts/gauge_m.png)

Neste exemplo, você é um revendedor de carros, controlando a média de vendas da equipe por mês. A agulha representa uma meta de vendas de 140 carros. A média mínima possível de vendas é 0 e o máximo é 200.  O sombreamento azul mostra que a equipe tem uma média de aproximadamente 120 vendas neste mês. Felizmente, há ainda outra semana para atingir a meta.

Veja Will mostrando como criar elementos visuais de métrica únicos: medidores, cartões e KPIs.

<iframe width="560" height="315" src="https://www.youtube.com/embed/xmja6EpqaO0?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP" frameborder="0" allowfullscreen></iframe>

## <a name="when-to-use-a-radial-gauge"></a>Quando usar um medidor radial

Os medidores radiais são uma ótima opção para:

* Mostrar o progresso para atingir uma meta.

* Representar uma medida percentual, como um KPI.

* Mostrar a integridade de uma única medida.

* Exibir informações que você pode verificar e compreender rapidamente.

## <a name="prerequisites"></a>Pré-requisitos

* O serviço do Power BI ou o Power BI Desktop

* Pasta de trabalho do Excel de exemplo financeiro: [baixe o exemplo diretamente](http://go.microsoft.com/fwlink/?LinkID=521962).

## <a name="create-a-basic-radial-gauge"></a>Criar um medidor radial básico

Estas instruções usam o serviço do Power BI. Para acompanhar, entre no Power BI e abra o arquivo Exemplo Financeiro do Excel.

### <a name="step-1-open-the-financial-sample-excel-file"></a>Etapa 1: abrir o arquivo do Excel de Exemplo Financeiro

1. Se ainda não fez isso, baixe o [arquivo do Excel de Exemplo Financeiro](../sample-financial-download.md). Lembre-se do local em que você o salvou.

1. No serviço do Power BI, selecione **Obter dados** > **Arquivos**.

1. Selecione **Arquivo local** e navegue até o local do arquivo de exemplo.

1. Selecione **Importar**. O Power BI adiciona o Exemplo Financeiro a seu workspace como um conjunto de dados.

1. Na lista de conteúdo **Conjuntos de dados**, selecione o ícone **Criar relatório** para o **Exemplo Financeiro**.

    ![Captura de tela da lista de conjuntos de dados com uma seta apontando para o ícone Criar relatório para o Exemplo Financeiro.](media/power-bi-visualization-radial-gauge-charts/power-bi-dataset.png)

### <a name="step-2-create-a-gauge-to-track-gross-sales"></a>Etapa 2: criar um medidor para acompanhar as Vendas Brutas

Na última seção, quando você tiver selecionado o ícone **Criar relatório**, o Power BI criou um relatório em branco na exibição de edição.

1. No painel **Campos**, selecione **Vendas Brutas**.

   ![](media/power-bi-visualization-radial-gauge-charts/grosssalesvalue_new.png)

1. Altere a agregação para **Médio**.

   ![Captura de tela do painel Campos com Vendas Brutas e a Agregação de Média destacada.](media/power-bi-visualization-radial-gauge-charts/changetoaverage_new.png)

1. Selecionar o ícone de medidor ![Captura de tela do ícone de medidor.](media/power-bi-visualization-radial-gauge-charts/gaugeicon_new.png) para converter o gráfico de colunas em um gráfico de medidor.

    ![Captura de tela do gráfico de medidor.](media/power-bi-visualization-radial-gauge-charts/gauge_no_target.png)

    Dependendo de quando você baixa o arquivo de **Exemplo Financeiro**, você poderá ver os números que não correspondem a esses números.

    > [!TIP]
    > Por padrão, o Power BI cria um gráfico de medidor no qual o valor atual (nesse caso, **Média das Vendas Brutas**) deve estar no ponto na metade do medidor. Como o valor **Média das Vendas Brutas** é de US$ 182.760, o valor inicial (Mínimo) é definido como 0 e o valor final (Máximo) é definido como o dobro do valor atual.

### <a name="step-3-set-a-target-value"></a>Etapa 3: definir um valor de destino

1. Arraste **COGS** do painel **Campos** para o contêiner **Valor de destino**.

1. Altere a agregação para **Médio**.

   O Power BI adiciona uma agulha para representar o valor de destino de **US$ 145.480**.

   ![Captura de tela do gráfico de medidor com a média de COGS adicionada.](media/power-bi-visualization-radial-gauge-charts/gaugeinprogress_new.png)

    Observe que ultrapassamos o nosso alvo.

   > [!NOTE]
   > Você pode inserir manualmente um valor de destino. Consulte a seção [Use as opções de formatação manual para definir os valores Mínimo, Máximo e Destino](#use-manual-format-options-to-set-minimum-maximum-and-target-values).

### <a name="step-4-set-a-maximum-value"></a>Etapa 4: definir um valor máximo

Na Etapa 2, o Power BI usou o campo **Valor** para definir automaticamente o valor mínimo e o máximo. E se você quiser definir seu próprio valor máximo? Digamos que, em vez de usar o dobro do valor atual como o valor máximo possível, você deseja defini-lo como o maior número de vendas brutas no conjunto de dados.

1. Arraste **Vendas Brutas** do painel **Campos** para o **Valor Máximo** também.

1. Altere a agregação para **Máximo**.

   ![Captura de tela do painel Campos com Vendas Brutas e a Agregação máxima destacada.](media/power-bi-visualization-radial-gauge-charts/setmaximum_new.png)

   O medidor é redesenhado com um novo valor de término, 1,21 milhão em vendas brutas.

   ![Captura de tela do gráfico de medidor concluído.](media/power-bi-visualization-radial-gauge-charts/power-bi-final-gauge.png)

### <a name="step-5-save-your-report"></a>Etapa 5: Salvar seu relatório

1. [Salve o relatório](../service-report-save.md).

1. [Adicione o gráfico de medidor como um bloco do dashboard](../service-dashboard-pin-tile-from-report.md). 

## <a name="use-manual-format-options-to-set-minimum-maximum-and-target-values"></a>Use as opções de formatação manual para definir os valores Mínimo, Máximo e Destino

1. Remova **Vendas Brutas Máx.** do **Valor máximo** também.

1. Selecione o ícone de rolo de pintura para abrir o painel **Formatar**.

   ![Captura de tela do gráfico de medidor e do painel Formatar com o ícone de rolo de tinta destacado.](media/power-bi-visualization-radial-gauge-charts/power-bi-roller.png)

1. Expanda o **Eixo de medidor** e insira valores para **Mín.** e **Máx**.

    ![Captura de tela das opções de eixo de medidor.](media/power-bi-visualization-radial-gauge-charts/power-bi-gauge-axis.png)

1. Desmarque a opção **COGS** no painel **Campos** para remover o valor de destino.

    ![Captura de tela da opção COGS desmarcada.](media/power-bi-visualization-radial-gauge-charts/pbi_remove_target.png)

1. Quando o campo **Destino** aparecer no **Eixo do medidor**, insira um valor.

     ![Captura de tela das opções de eixo do medidor com Destino destacado.](media/power-bi-visualization-radial-gauge-charts/power-bi-gauge-target.png)

1. Como opção, continue com a formatação do gráfico de medidor.

Depois que você tiver concluído essas etapas, terá um gráfico de medidor que pode ter esta aparência:

![Captura de tela do gráfico de medidor final.](media/power-bi-visualization-radial-gauge-charts/power-bi-final.png)

## <a name="next-step"></a>Próxima etapa

* [Visuais de KPI (Indicador Chave de Desempenho)](power-bi-visualization-kpi.md)

* [Tipos de visualização no Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)

Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)