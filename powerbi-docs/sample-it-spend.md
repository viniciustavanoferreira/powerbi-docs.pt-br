---
title: 'Exemplo de Análise de Gastos de TI para o Power BI: Faça um tour'
description: 'Exemplo de Análise de Gastos de TI para o Power BI: Faça um tour'
author: maggiesMSFT
ms.reviewer: amac
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 07/05/2019
ms.author: maggies
LocalizationGroup: Samples
ms.openlocfilehash: 6f39f8b5c288c1dbff3cd87c7beee27683cfeae2
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/09/2019
ms.locfileid: "73873899"
---
# <a name="it-spend-analysis-sample-for-power-bi-take-a-tour"></a>Exemplo de Análise de Gastos de TI para o Power BI: Faça um tour

O exemplo de pacote de conteúdo da Análise de Gastos de TI contém um painel, um relatório e um conjunto de dados que analisam os custos planejados vs. reais de um departamento de TI. Essa comparação nos ajuda a entender como a empresa se preparou para o ano e investigar áreas com grandes desvios do plano. A empresa neste exemplo passa por um ciclo de planejamento anual e gera trimestralmente uma nova LE (estimativa mais recente) para ajudar a analisar as alterações nos gastos de TI no ano fiscal.

![Painel do exemplo de Análise de Gastos de TI](media/sample-it-spend/it1.png)

Este exemplo faz parte de uma série que mostra como o Power BI pode ser usado com dados, relatórios e painéis orientados aos negócios. Ele foi criado pela [obviEnce](http://www.obvience.com/) usando dados reais, que foram mantidos anônimos. Os dados estão disponíveis em vários formatos: pacote de conteúdo, arquivo .pbix do Power BI Desktop ou pasta de trabalho do Excel. Confira [Exemplos para o Power BI](sample-datasets.md). 

Este tutorial explora o pacote de conteúdo de exemplo de Gastos de TI no serviço do Power BI. Como as experiências de relatório são muito semelhantes no Power BI Desktop e no serviço, você também pode acompanhar usando o arquivo de exemplo .pbix no Power BI Desktop. 

Você não precisa de uma licença do Power BI para explorar os exemplos no Power BI Desktop. Se você não tiver uma licença do Power BI Pro, poderá salvar a amostra em Meu Espaço de Trabalho no serviço do Power BI. 

## <a name="get-the-sample"></a>Obter o exemplo

 Antes de usar o exemplo, primeiro você deve baixá-lo como um [pacote de conteúdo](#get-the-content-pack-for-this-sample), [arquivo .pbix](#get-the-pbix-file-for-this-sample) ou [pasta de trabalho do Excel](#get-the-excel-workbook-for-this-sample).

### <a name="get-the-content-pack-for-this-sample"></a>Obter o pacote de conteúdo para este exemplo

1. Abra o serviço do Power BI (app.powerbi.com), entre e abra o workspace em que você deseja salvar o exemplo.

   Se você não tiver uma licença do Power BI Pro, poderá salvar a amostra em Meu Espaço de Trabalho.

2. No canto inferior esquerdo, selecione **Obter Dados**.
   
   ![Selecionar Obter Dados](media/sample-datasets/power-bi-get-data.png)
3. Na página **Obter Dados** que aparece, selecione **Exemplos**.
   
4. Selecione **Exemplo de Análise de Gastos de TI** e escolha **Conectar**.  
  
   ![Conectar-se ao exemplo](media/sample-it-spend/it-connect.png)
   
5. O Power BI importa o pacote de conteúdo e adiciona um novo dashboard, um relatório e um conjunto de dados ao seu workspace atual.
   
   ![Entrada do exemplo de Análise de Gastos de TI](media/sample-it-spend/it-spend-analysis-sample-entry.png)
  
### <a name="get-the-pbix-file-for-this-sample"></a>Obter o arquivo. pbix para este exemplo

Como alternativa, você pode baixar o exemplo de Análise de Gastos de TI como um [arquivo .pbix](https://download.microsoft.com/download/E/9/8/E98CEB6D-CEBB-41CF-BA2B-1A1D61B27D87/IT%20Spend%20Analysis%20Sample%20PBIX.pbix), que foi projetado para uso com o Power BI Desktop.

### <a name="get-the-excel-workbook-for-this-sample"></a>Obter a pasta de trabalho do Excel para este exemplo

Se quiser exibir a fonte de dados deste exemplo, ela também está disponível como uma [Pasta de trabalho do Excel](https://go.microsoft.com/fwlink/?LinkId=529783). A pasta de trabalho contém planilhas do Power View que você pode exibir e modificar. Para ver os dados brutos, habilite os suplementos de Análise de Dados e, em seguida, selecione **Power Pivot > Gerenciar**. Para habilitar os suplementos Power View e Power Pivot, confira [Dar uma olhada nos exemplos do Excel dentro do próprio Excel](sample-datasets.md#optional-take-a-look-at-the-excel-samples-from-inside-excel-itself) para obter detalhes.

## <a name="it-spend-analysis-sample-dashboard"></a>Painel do exemplo de Análise de Gastos de TI
Os dois blocos de números no lado esquerdo do painel, **% do Plano de Variação** e **% da Estimativa mais Recente da Variação do 3º Trimestre**, nos fornecem uma visão geral de nosso desempenho em relação ao plano e à estimativa mais recente do trimestre (LE3 = estimativa mais recente do 3º trimestre). Em geral, estamos cerca de 6% fora do plano. Vamos explorar a causa dessa variação: quando, onde e qual categoria.

## <a name="ytd-it-spend-trend-analysis-page"></a>Página Análise das Tendências de Gastos de TI Acumulados no Ano
Quando você seleciona bloco do painel **% do Plano de Variação por Região de Vendas**, ele exibe a página **Análise das Tendências de Gastos de TI Acumulados no Ano** do relatório Exemplo de análise de Gastos de TI. De relance, vemos que temos uma variação positiva nos Estados Unidos e na Europa e uma variação negativa no Canadá, na América Latina e na Austrália. Os Estados Unidos têm uma variação +LE de cerca de 6% e a Austrália tem uma variação -LE de cerca de 7%.

![Percentual do plano de variação por região de vendas](media/sample-it-spend/it2.png)

No entanto, apenas examinar esse gráfico e tirar conclusões pode ser enganoso. Precisamos examinar as quantias reais em dólar para ver as coisas de forma objetiva.

1. Selecione **Austrália e Nova Zelândia** no gráfico **% do Plano de Variação por Região de Vendas** e observe o gráfico **Plano de Variação por Área de TI**.

   ![Página Análise das Tendências de Gastos de TI Acumulados no Ano](media/sample-it-spend/it3.png)
2. Agora selecione **EUA**. Observe que a Austrália e a Nova Zelândia são uma parte muito pequena de nossos gastos gerais em comparação com os Estados Unidos.

    Em seguida, vamos explorar qual categoria nos EUA está causando a variação.

## <a name="ask-questions-of-the-data"></a>Fazer perguntas sobre os dados
1. Selecione **Exemplo de Análise de Gastos de TI** no painel de navegação superior para retornar ao dashboard de exemplo.
2. Selecione **Fazer uma pergunta sobre seus dados**.
3. Na lista **Perguntas para começar** no lado esquerdo, selecione **qual é o plano por área de TI**.

   ![gráfico Plano por área de TI](media/sample-it-spend/it-area-chart.png)

4. Na caixa de P e R, limpe a entrada anterior e insira o *mostrar gráfico de barras das áreas de TI, % do plano de variação e % da le3 da variação*.

   ![Gráfico de % do plano de variação e % da LE3 da variação por área de TI](media/sample-it-spend/it4.png)

   Na primeira área de TI, **Infraestrutura**, observe que o percentual mudou drasticamente entre o plano de variação inicial e a estimativa mais recente do plano de variação.

## <a name="ytd-spend-by-cost-elements-page"></a>Página Gastos Acumulados no Ano por Elementos de Custo

1. Retorne ao painel e examine o bloco do painel **% do Plano de Variação, % da Estimativa Mais Recente da variação – 3º Trimestre**.

   ![Bloco % do Plano de Variação, LE3 da Variação](media/sample-it-spend/it5.png)

   Observe que a área Infraestrutura se destaca com uma grande variação positiva para o plano.

1. Selecione esse bloco para abrir o relatório e exibir a página **Gastos Acumulados no Ano por Elementos de Custo**.
2. Selecione a barra **Infraestrutura** no gráfico **% do Plano de Variação e % da LE3 da Variação por Área de TI** na parte inferior direita e observe os valores de variação para o plano no gráfico **% do Plano de Variação por Região de Vendas** na parte inferior esquerda.

    ![Página Gastos Acumulados no Ano por Elementos de Custo](media/sample-it-spend/it6.png)
3. Selecione um nome por vez na segmentação **Grupo de Elementos de Custo** para encontrar o elemento de custo com a maior variação.
4. Com a opção **Outros** selecionada, selecione **Infraestrutura** na segmentação **Área de TI** e selecione subáreas na segmentação **Subárea de TI** para encontrar a subárea com a maior variação.  

   Observe a grande variação para **Rede**. Aparentemente, a empresa decidiu oferecer aos seus funcionários serviços telefônicos como um benefício, embora essa mudança não estivesse planejada.

## <a name="plan-variance-analysis-page"></a>Página Análise de Variação do Plano

1. Selecione a guia **Análise de Variação do Plano** na parte inferior da página.

2. No gráfico **Plano de Variação e % do Plano de Variação por Área de Negócios** à esquerda, selecione a coluna **Infraestrutura** para realçar os valores da área de negócios da infraestrutura no restante da página.

    ![Página Análise de Variação do Plano](media/sample-it-spend/it7.png)

   Observe no gráfico **% do Plano de Variação e Área de Negócios** que a área de negócios da infraestrutura iniciou uma variação positiva em fevereiro. Além disso, observe como o valor de variação para o plano para essa área de negócios varia por país, em comparação com todas as outra áreas de negócios. 

3. Use as segmentações **Área de TI** e **Subárea de TI** à direita para filtrar os valores no restante da página e explorar os dados. 

## <a name="edit-the-report"></a>Editar o relatório
Selecione **Editar Relatório** no canto superior esquerdo e explore na exibição Edição:

* Veja como as páginas são criadas, os campos de cada gráfico e os filtros nas páginas.
* Adicione páginas e gráficos com base nos mesmos dados.
* Altere o tipo de visualização para cada gráfico.
* Fixe gráficos de interesse no seu painel.

## <a name="next-steps-connect-to-your-data"></a>Próximas etapas: Conecte-se aos seus dados
Esse ambiente é seguro para teste, pois você pode optar por não salvar as alterações. Mas se você salvá-las, sempre é possível selecionar **Obter Dados** para ter uma nova cópia deste exemplo.

Esperamos que este tour tenha mostrado como os painéis, P e R e relatórios do Power BI podem fornecer informações sobre os dados de exemplo. Agora é sua vez – conecte-se aos seus próprios dados. Com o Power BI, é possível se conectar a uma grande variedade de fontes de dados. Para saber mais, confira [Introdução ao serviço do Power BI](service-get-started.md).
