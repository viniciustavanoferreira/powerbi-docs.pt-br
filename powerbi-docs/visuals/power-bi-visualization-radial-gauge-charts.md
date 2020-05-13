---
title: Gráficos de medidor radial no Power BI
description: Gráficos de medidor radial no Power BI
author: mihart
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/05/2020
ms.author: rien
LocalizationGroup: Visualizations
ms.openlocfilehash: 4274136df063258b6879057636f11ec437873ae6
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83276342"
---
# <a name="radial-gauge-charts-in-power-bi"></a>Gráficos de medidor radial no Power BI

[!INCLUDE[consumer-appliesto-nyyn](../includes/consumer-appliesto-nyyn.md)]

[!INCLUDE [power-bi-visuals-desktop-banner](../includes/power-bi-visuals-desktop-banner.md)]

Um gráfico de medidor radial tem um arco circular e mostra um único valor que acompanha o progresso em relação a um objetivo/KPI (indicador chave de desempenho). A linha (ou *agulha*) representa o valor de meta ou destino. O sombreamento representa o progresso em relação a esse objetivo. O valor dentro do arco representa o valor do progresso. O Power BI distribui uniformemente todos os valores possíveis ao longo do arco, do mínimo (valor mais à esquerda) para o máximo (valor mais à direita).

![Captura de tela de medidor radial.](media/power-bi-visualization-radial-gauge-charts/gauge-m.png)

Neste exemplo, você é um revendedor de carros, controlando a média de vendas da equipe por mês. A agulha representa uma meta de vendas de 140 carros. A média mínima possível de vendas é 0 e o máximo é 200.  O sombreamento azul mostra que a equipe tem uma média de aproximadamente 120 vendas neste mês. Felizmente, há ainda outra semana para atingir a meta.

> [!NOTE]
> Compartilhar seu relatório com um colega do Power BI exige que você tenha licenças de Power BI Pro individuais ou que o relatório seja salvo na capacidade Premium.

## <a name="when-to-use-a-radial-gauge"></a>Quando usar um medidor radial

Os medidores radiais são uma ótima opção para:

* Mostrar o progresso para atingir uma meta.

* Representar uma medida percentual, como um KPI.

* Mostrar a integridade de uma única medida.

* Exibir informações que você pode verificar e compreender rapidamente.

## <a name="prerequisites"></a>Pré-requisitos

Este tutorial usa o [arquivo do Excel de Exemplo Financeiro](https://download.microsoft.com/download/9/6/D/96DDC2FF-2568-491D-AAFA-AFDD6F763AE3/Retail%20Analysis%20Sample%20PBIX.pbix).

1. Na seção superior esquerda da barra de menus, selecione **Obter Dados** > **Excel**
   
2. Encontre sua cópia do **arquivo do Excel de Exemplo Financeiro**

1. Abra o **arquivo do Excel de Exemplo Financeiro** na exibição de relatório ![Captura de tela do ícone de exibição de relatório](media/power-bi-visualization-kpi/power-bi-report-view.png).

1. Selecione **finanças** e **Sheet1**

1. Clique em **Carregar**

1. Selecionar ![Captura de tela da guia amarela.](media/power-bi-visualization-kpi/power-bi-yellow-tab.png) para adicionar uma nova página.



## <a name="create-a-basic-radial-gauge"></a>Criar um medidor radial básico

### <a name="step-1-create-a-gauge-to-track-gross-sales"></a>Etapa 1: criar um medidor para acompanhar as Vendas Brutas

1. Comece em uma página de relatório em branco

1. No painel **Campos**, selecione **Vendas Brutas**.

   ![](media/power-bi-visualization-radial-gauge-charts/grosssalesvalue-new.png)

1. Altere a agregação para **Média**.

   ![Captura de tela do painel Campos com Vendas Brutas e a Agregação de Média destacada.](media/power-bi-visualization-radial-gauge-charts/changetoaverage-new.png)

1. Selecionar o ícone de medidor ![Captura de tela do ícone de medidor.](media/power-bi-visualization-radial-gauge-charts/gaugeicon-new.png) para converter o gráfico de colunas em um gráfico de medidor.

    ![Captura de tela do gráfico de medidor.](media/power-bi-visualization-radial-gauge-charts/gauge-no-target.png)

    Dependendo de quando você baixa o arquivo de **Exemplo Financeiro**, você poderá ver os números que não correspondem a esses números.

    > [!TIP]
    > Por padrão, o Power BI cria um gráfico de medidor no qual o valor atual (nesse caso, **Média das Vendas Brutas**) deve estar no ponto na metade do medidor. Como o valor **Média das Vendas Brutas** é de US$ 182.760, o valor inicial (Mínimo) é definido como 0 e o valor final (Máximo) é definido como o dobro do valor atual.

### <a name="step-3-set-a-target-value"></a>Etapa 3: definir um valor de destino

1. Arraste **COGS** do painel **Campos** para o contêiner **Valor de destino**.

1. Altere a agregação para **Média**.

   O Power BI adiciona uma agulha para representar o valor de destino de **US$ 145.480**.

   ![Captura de tela do gráfico de medidor com a média de COGS adicionada.](media/power-bi-visualization-radial-gauge-charts/gaugeinprogress-new.png)

    Observe que ultrapassamos o nosso alvo.

   > [!NOTE]
   > Você pode inserir manualmente um valor de destino. Consulte a seção [Use as opções de formatação manual para definir os valores Mínimo, Máximo e Destino](#use-manual-format-options-to-set-minimum-maximum-and-target-values).

### <a name="step-4-set-a-maximum-value"></a>Etapa 4: definir um valor máximo

Na Etapa 2, o Power BI usou o campo **Valor** para definir automaticamente o valor mínimo e o máximo. E se você quiser definir seu próprio valor máximo? Digamos que, em vez de usar o dobro do valor atual como o valor máximo possível, você deseja defini-lo como o maior número de vendas brutas no conjunto de dados.

1. Arraste **Vendas Brutas** do painel **Campos** para o **Valor Máximo** também.

1. Altere a agregação para **Máximo**.

   ![Captura de tela do painel Campos com Vendas Brutas e a Agregação máxima destacada.](media/power-bi-visualization-radial-gauge-charts/setmaximum-new.png)

   O medidor é redesenhado com um novo valor de término, 1,21 milhão em vendas brutas.

   ![Captura de tela do gráfico de medidor concluído.](media/power-bi-visualization-radial-gauge-charts/power-bi-final-gauge.png)

### <a name="step-5-save-your-report"></a>Etapa 5: Salvar seu relatório

1. [Salve o relatório](../create-reports/service-report-save.md).

## <a name="use-manual-format-options-to-set-minimum-maximum-and-target-values"></a>Use as opções de formatação manual para definir os valores Mínimo, Máximo e Destino

1. Remova **Vendas Brutas Máx.** do **Valor máximo** também.

1. Selecione o ícone de rolo de pintura para abrir o painel **Formatar**.

   ![Captura de tela do gráfico de medidor e do painel Formatar com o ícone de rolo de tinta destacado.](media/power-bi-visualization-radial-gauge-charts/power-bi-roller.png)

1. Expanda o **Eixo de medidor** e insira valores para **Mín.** e **Máx**.

    ![Captura de tela das opções de eixo de medidor.](media/power-bi-visualization-radial-gauge-charts/power-bi-gauge-axis.png)

1. Desmarque a opção **COGS** no painel **Campos** para remover o valor de destino.

    ![Captura de tela da opção COGS desmarcada.](media/power-bi-visualization-radial-gauge-charts/pbi-remove-target.png)

1. Quando o campo **Destino** aparecer no **Eixo do medidor**, insira um valor.

     ![Captura de tela das opções de eixo do medidor com Destino destacado.](media/power-bi-visualization-radial-gauge-charts/power-bi-gauge-target.png)

1. Como opção, continue com a formatação do gráfico de medidor.

Depois que você tiver concluído essas etapas, terá um gráfico de medidor que pode ter esta aparência:

![Captura de tela do gráfico de medidor final.](media/power-bi-visualization-radial-gauge-charts/power-bi-final.png)

## <a name="next-step"></a>Próxima etapa

* [Visuais de KPI (Indicador Chave de Desempenho)](power-bi-visualization-kpi.md)

* [Tipos de visualização no Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)

Mais perguntas? [Experimente a Comunidade do Power BI](https://community.powerbi.com/)

