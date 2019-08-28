---
title: Personalizar as propriedades dos eixos X e Y
description: Personalizar as propriedades dos eixos X e Y
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: 9DeAKM4SNJM
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/24/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 3bfe84acdf73fcb5ace791c9a84943262d0f73ab
ms.sourcegitcommit: 1c96b65a03ec0a0612e851dd58c363f4d56bca38
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/25/2019
ms.locfileid: "67390110"
---
# <a name="customize-x-axis-and-y-axis-properties"></a>Personalizar as propriedades dos eixos X e Y

Neste tutorial, você aprenderá várias maneiras diferentes de personalizar os eixos X e Y de seus visuais. Nem todos os visuais têm eixos. Gráficos de pizza, por exemplo, não têm eixos. E as opções de personalização variam de visual para visual. Existem muitas opções para abordar em um único artigo, então dê uma olhada em algumas das personalizações de eixos mais usadas e obtenha familiaridade com o painel **Formato** do visual na tela de relatório do Power BI.  

> [!NOTE]
> Esta página aplica-se ao serviço do Power BI e ao Power BI Desktop. Essas personalizações, que ficam disponíveis quando o **Formato** o ícone (de rolo de tinta ![Captura de tela do ícone de rolo de tinta.](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-paintroller.png)) é selecionado, também estão disponíveis no Power BI Desktop.

Assista à Amanda personalizar os eixos X e Y. Ela demonstrará as diferentes maneiras de controlar a concatenação ao fazer drill down e drill up.

<iframe width="560" height="315" src="https://www.youtube.com/embed/9DeAKM4SNJM" frameborder="0" allowfullscreen></iframe>

## <a name="prerequisites"></a>Pré-requisitos

- O serviço do Power BI

- Relatório Exemplo de Análise de Varejo

## <a name="customize-visualization-x--and-y-axes-in-reports"></a>Personalizar os eixos de visualização X e Y em relatórios

Para acompanhar, entre no [serviço do Power BI](https://app.powerbi.com) e abra o relatório [Exemplo de Análise de Varejo](../sample-datasets.md) no modo de exibição [Editar relatório](../service-interact-with-a-report-in-editing-view.md).

### <a name="create-a-stacked-column-chart-visualization"></a>Criar uma visualização de gráfico de colunas empilhadas

Antes de personalizar a visualização, você precisa compilá-la.

1. No serviço do Power BI, expanda **Meu Workspace**.

1. Role a tela para baixo e selecione **Exemplo de Análise de Varejo** na lista de **Conjuntos de dados**.

1. No painel de **Visualizações**, selecione o ícone do gráfico de colunas empilhadas.

    ![Captura de tela do painel de Visualizações e um gráfico de colunas empilhadas vazio](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-stacked-column-chart.png)

1. Para definir os valores do eixo X, no painel **Campos**, selecione **Time** > **FiscalMonth**.

1. Para definir os valores do eixo Y, no painel **Campos**, selecione **Vendas** > **Vendas Deste Ano** e selecione **Vendas** > **Vendas deste Ano** > **Valor**.

    ![Captura de tela do gráfico de colunas empilhadas preenchido.](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-create-chart.png)

### <a name="customize-the-x-axis"></a>Personalizar o eixo X

Agora você pode personalizar o eixo X.

1. No painel **Visualizações**, selecione **Formato** (ícone de rolo de tinta ![Captura de tela do ícone de rolo de tinta.](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-paintroller.png)) para revelar as opções de personalização.

1. Expanda as opções de eixo X.

   ![Captura de tela das opções de eixo X.](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-x-axis.png)

1. Mova a segmentação do **eixo X** para **Ativado**.

    ![Captura de tela na segmentação Ativada.](media/power-bi-visualization-customize-x-axis-and-y-axis/onoffslider.png)

    Um motivo pelo qual você talvez queira desativar o eixo X é para economizar espaço para mais dados.

1. Formatar a fonte, o tamanho e a cor do texto:

    - **Cor**: selecione preto

    - **Tamanho do texto**: insira *14*

    - **Família de fontes**: selecione **Arial Black**

1. Deslize a opção **Título** para **Ativado** para exibir o nome do eixo X. Nesse caso, é o **FiscalMonth**.

1. Formatar a fonte, o tamanho e a cor do texto do título:

    - **Cor do título**: selecione laranja

    - **Título do eixo**: insira *Mês Fiscal*

    - **Tamanho de texto do título**: insira *21*

Depois de concluir as personalizações, o gráfico de colunas empilhadas terá a aparência a seguir:

![Captura de tela do gráfico de colunas empilhadas personalizado.](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-customize-axis.png)

Salve as alterações e vá para a próxima seção.

Se você precisar reverter todas as alterações, selecione **Reverter ao Padrão** na parte inferior do painel de personalização do **eixo X**.

### <a name="customize-the-y-axis"></a>Personalizar o eixo Y

Em seguida, você personalizará o eixo Y.

1. Expanda as opções de eixo Y.

   ![Captura de tela das opções de eixo Y.](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-y-axis.png)

1. Mova a segmentação do **eixo Y** para **Ativado**.  

    ![Captura de tela na segmentação Ativada.](media/power-bi-visualization-customize-x-axis-and-y-axis/onoffslider.png)

    Um motivo pelo qual você talvez queira desativar o eixo Y é para economizar espaço para mais dados.

1. Defina a **Posição** do eixo Y para a **Direita**.

1. Formatar a fonte, o tamanho e a cor do texto:

    - **Cor**: selecione preto

    - **Tamanho do texto**: insira *14*

    - **Família de fontes**: selecione **Arial Black**

1. Defina as **Unidades de exibição** para **Milhões** e **Casas decimais** para *0*.

1. Para essa visualização, o fato de ter um título de eixo Y não melhora o visual; portanto, deixe o **Título** **Desativado**.  

1. Destacaremos as linhas de grade, alterando a cor e aumentando o traço:

    - **Cor**: selecione cinza-escuro

    - **Traço**: insira *2*

Depois de todas essas personalizações, o gráfico de colunas deve ser parecido com isto:

![Captura de tela do gráfico com o eixo Y personalizado.](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-y-axis-complete.png)

## <a name="customizing-visualizations-with-dual-y-axes"></a>Personalizar visualizações de eixo Y duplo

Primeiro, você criará um gráfico de combinação que examina o impacto da contagem da loja nas vendas. É o mesmo gráfico criado no [Tutorial do gráfico de combinação](power-bi-visualization-combo-chart.md). Em seguida, você formatará o eixo Y duplo.

### <a name="create-a-chart-with-two-y-axes"></a>Crie um gráfico com dois eixos Y

1. Crie um novo gráfico de linhas que acompanha a **% de Vendas > Margem Bruta do ano passado** por **Hora > FiscalMonth**.

    ![Captura de tela do novo gráfico de linhas.](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-line-chart.png)

    > [!NOTE]
    > Para obter ajuda sobre a classificação por mês, confira [Classificar o uso de outros critérios](../consumer/end-user-change-sort.md#other).

    A porcentagem da Margem Bruta em janeiro foi de 35%, chegou a 45% em abril, caindo em julho e subindo novamente em agosto. Será que vamos ver um padrão semelhante nas vendas do ano passado e deste ano?

1. Adicione **Vendas deste ano > Valor** e **Vendas do último ano** no gráfico de linhas.

    ![Captura de tela do gráfico de linhas com os novos dados adicionados.](media/power-bi-visualization-customize-x-axis-and-y-axis/flatline_new.png)

    A escala de **% de Margem Bruta do Ano Passado** (a linha azul acompanhando a linha de grade **0M%** ) é muito menor do que a escala de **Vendas**, o que dificulta a comparação. Além disso, os percentuais de rótulo do eixo Y são absurdas.

1. Para tornar o visual mais fácil de ler e interpretar, converta o gráfico de linhas em um gráfico de colunas empilhadas e Linhas.

   ![Captura de tela do painel de Visualizações, com o ícone do gráfico de colunas empilhadas e linhas destacado.](media/power-bi-visualization-customize-x-axis-and-y-axis/converttocombo_new.png)

1. Arraste **% de Margem Bruta no Ano Passado** de **Valores de Coluna** para **Valores de Linha**.

    ![Captura de tela do gráfico de colunas empilhadas e linhas com todos os três valores claramente representados.](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-dual-axes.png)

    Agora você tem o gráfico de colunas empilhadas criado na primeira seção com um gráfico de linhas sobreposto a ele. Opcionalmente, use o que você aprendeu acima para formatar a cor e o tamanho da fonte dos eixos.

   ![Captura de tela do gráfico de colunas empilhadas e linhas personalizado.](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-dual-axes-new.png)

   O Power BI cria dois eixos Y permitindo que os conjuntos de dados sejam dimensionados de forma diferente. O eixo à esquerda calcula os dólares e o eixo à direita calcula o percentual.

### <a name="format-the-secondary-y-axis"></a>Formatar o eixo Y secundário

1. No painel **Visualizações**, selecione o ícone de rolo de tinta para exibir as opções de formato.

1. Expanda as opções de eixo Y.

1. Role a tela para baixo até encontrar a opção **Mostrar secundário**. Verifique se está **Ativada**.

   ![Captura de tela da opção Mostrar secundário.](media/power-bi-visualization-customize-x-axis-and-y-axis/combo3.png)

1. (Opcional) Personalize os dois eixos. Se você mudar a **Posição** para o eixo da coluna ou o eixo de linha, os dois eixos trocarão de lado.

### <a name="add-titles-to-both-axes"></a>Adicionar títulos a ambos os eixos

Com uma visualização complicada, convém adicionar títulos de eixos.  Os títulos ajudam seus colegas a conhecer a história de sua visualização.

1. Alterne **Título** para **Ativado** para o **Eixo Y (Coluna)** e o **Eixo Y (Linha)** .

1. Defina o **Estilo** para **Mostrar somente o título** de ambos.

   ![Captura de tela das opções Título e Estilo.](media/power-bi-visualization-customize-x-axis-and-y-axis/yaxissettings.png)

1. Seu gráfico de combinação agora mostra eixos duplos, ambos com títulos.

   ![Captura de tela do gráfico de eixos Y duplo personalizado.](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-combo-chart.png)

Para obter mais informações, confira [Dicas e truques para formatação com cores no Power BI](service-tips-and-tricks-for-color-formatting.md).

## <a name="considerations-and-troubleshooting"></a>Considerações e solução de problemas

Se o eixo X for categorizado pelo proprietário do relatório como um tipo de data, a opção **Tipo** será exibida e você poderá selecionar entre contínua ou categórica.

## <a name="next-steps"></a>Próximas etapas

- [Visualizações em relatórios do Power BI](power-bi-report-visualizations.md)

- [Personalizar títulos, legendas e telas de fundo de visualizações](power-bi-visualization-customize-title-background-and-legend.md)

- [Introdução com propriedades de eixo e formatação de cor](service-getting-started-with-color-formatting-and-axis-properties.md)

- [Conceitos básicos para consumidores do serviço do Power BI](../consumer/end-user-basic-concepts.md)

Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)
