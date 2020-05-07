---
title: 'Exemplo de Análise de Varejo do Power BI: Faça um tour'
description: 'Exemplo de Análise de Varejo do Power BI: Faça um tour'
author: maggiesMSFT
ms.reviewer: amac
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 07/02/2019
ms.author: maggies
LocalizationGroup: Samples
ms.openlocfilehash: eac1c22ba23f7a1a67b2cc120fe38d4c396d864a
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/05/2020
ms.locfileid: "80404725"
---
# <a name="retail-analysis-sample-for-power-bi-take-a-tour"></a>Exemplo de Análise de Varejo do Power BI: Faça um tour

O pacote de conteúdo de exemplo de Análise de Varejo contém um painel, um relatório e um conjunto de dados que analisa os dados de vendas no varejo de itens vendidos em várias lojas e distritos. As métricas comparam o desempenho deste ano ao do ano passado em vendas, unidades, margem bruta e variação, além de análises de novas lojas. 

![Painel para o exemplo de Análise de Varejo](media/sample-retail-analysis/retail1.png)

Este exemplo faz parte de uma série que mostra como o Power BI pode ser usado com dados, relatórios e painéis orientados aos negócios. Ele foi criado pela [obviEnce](http://www.obvience.com/) usando dados reais, que foram mantidos anônimos. Os dados estão disponíveis em vários formatos: pacote de conteúdo, arquivo .pbix do Power BI Desktop ou pasta de trabalho do Excel. Confira [Exemplos para o Power BI](sample-datasets.md). 

Este tutorial explora o pacote de conteúdo de exemplo de Análise de Varejo no serviço do Power BI. Como as experiências de relatório são muito semelhantes no Power BI Desktop e no serviço, você também pode acompanhar usando o arquivo de exemplo .pbix no Power BI Desktop. 

Você não precisa de uma licença do Power BI para explorar os exemplos no Power BI Desktop. Se você não tiver uma licença do Power BI Pro, poderá salvar a amostra em Meu Espaço de Trabalho no serviço do Power BI. 

## <a name="get-the-sample"></a>Obter o exemplo

 Antes de usar o exemplo, primeiro você deve baixá-lo como um [pacote de conteúdo](#get-the-content-pack-for-this-sample), [arquivo .pbix](#get-the-pbix-file-for-this-sample) ou [pasta de trabalho do Excel](#get-the-excel-workbook-for-this-sample).

### <a name="get-the-content-pack-for-this-sample"></a>Obter o pacote de conteúdo para este exemplo

1. Abra o serviço do Power BI (app.powerbi.com), entre e abra o workspace em que você deseja salvar o exemplo. 

    Se você não tiver uma licença do Power BI Pro, poderá salvar a amostra em Meu Espaço de Trabalho.

2. No canto inferior esquerdo, selecione **Obter Dados**.

    ![Selecionar Obter Dados](media/sample-datasets/power-bi-get-data.png)
3. Na página **Obter Dados** que aparece, selecione **Exemplos**.
   
4. Selecione **Exemplo de Análise de Varejo** e escolha **Conectar**.  
  
   ![Conectar-se ao exemplo](media/sample-retail-analysis/retail16.png)
   
5. O Power BI importa o pacote de conteúdo e adiciona um novo painel, um relatório e um conjunto de dados ao seu workspace atual.
   
   ![Entrada Exemplo de Análise de Varejo](media/sample-retail-analysis/retail-entry.png)
  
### <a name="get-the-pbix-file-for-this-sample"></a>Obter o arquivo. pbix para este exemplo

Como alternativa, você pode baixar o exemplo de Análise de Varejo como um [arquivo .pbix](https://download.microsoft.com/download/9/6/D/96DDC2FF-2568-491D-AAFA-AFDD6F763AE3/Retail%20Analysis%20Sample%20PBIX.pbix), que foi projetado para uso com o Power BI Desktop. 

### <a name="get-the-excel-workbook-for-this-sample"></a>Obter a pasta de trabalho do Excel para este exemplo

Se quiser exibir a fonte de dados deste exemplo, ela também está disponível como uma [Pasta de trabalho do Excel](https://go.microsoft.com/fwlink/?LinkId=529778). A pasta de trabalho contém planilhas do Power View que você pode exibir e modificar. Para ver os dados brutos, habilite os suplementos de Análise de Dados e, em seguida, selecione **Power Pivot > Gerenciar**. Para habilitar os suplementos do Power View e do Power Pivot, confira [Explorar os exemplos do Excel no Excel](sample-datasets.md#explore-excel-samples-inside-excel) para saber mais.

## <a name="start-on-the-dashboard-and-open-the-report"></a>Iniciar no painel e abrir o relatório

1. No espaço de trabalho onde você salvou o exemplo, abra a guia **Painéis**, localize o painel **Exemplo de Análise de Varejo** e selecione-o. 
2. No painel, selecione o bloco **Total de Lojas, Lojas Novas & Existentes**, que é aberto na página **Visão Geral de Vendas da Loja** no relatório Amostra de Análise de Varejo. 

   ![Bloco Total de lojas](media/sample-retail-analysis/retail-analysis-7.png)  

   Nesta página de relatório, você vê que temos um total de 104 lojas, 10 das quais são novas. Temos duas redes, Fashions Direct e Lindseys. Em média, as lojas Fashions Direct são maiores.
3. No gráfico de pizza **Vendas deste Ano por Cadeia**, selecione **Fashions Direct**.

   ![Gráfico Vendas deste Ano por Cadeia](media/sample-retail-analysis/retail3.png)  

   Observe o resultado no gráfico de bolhas **Percentual de Variação Total de Vendas**:

   ![Gráfico Percentual de Variação Total de Vendas](media/sample-retail-analysis/pbi_sample_retanlbubbles.png)  

   O distrito **FD-01** tem a maior média de **Vendas por Pé Quadrado** e o FD-02 tem a menor **Variação Total de Vendas** em relação ao ano passado. O FD-03 e o FD-04 são os de pior desempenho geral.
4. Selecione algumas das bolhas individuais ou outros gráficos para ver o realce cruzado revelando o impacto de suas seleções.
5. Para retornar ao dashboard, selecione **Exemplo de Análise de Varejo** no painel de navegação superior.

   ![Barra de navegação](media/sample-retail-analysis/power-bi-breadcrumbs.png)
6. No painel, selecione o bloco **Vendas deste Ano nas Lojas Novas & Existentes**, o que equivale a digitar *This year sales* na caixa de perguntas e respostas.

   ![Bloco Vendas deste Ano](media/sample-retail-analysis/pbi_sample_retanlthisyrsales.png)

   Os resultados da sessão de perguntas e respostas aparecem:

   ![Vendas deste ano nas Perguntas e Respostas](media/sample-retail-analysis/retail7.png)

## <a name="review-a-tile-created-with-power-bi-qa"></a>Examinar um bloco criado com P e R do Power BI
Vamos analisar mais detalhadamente.

1. Altere a pergunta para _vendas deste ano **por distrito**_ . Observe o resultado: Perguntas e Respostas coloca automaticamente a resposta em um gráfico de barras e sugere outras frases:

   ![As vendas deste ano por distrito nas Perguntas e Respostas](media/sample-retail-analysis/retail8.png)
2. Agora altere a pergunta para _vendas deste ano **por cep e cadeia**_ .

   Observe como o Power BI responde à pergunta enquanto você digita e exibe o gráfico apropriado.
3. Experimente mais perguntas e confira que tipo de resultados você recebe.
4. Quando estiver pronto, retorne ao painel.

## <a name="dive-deeper-into-the-data"></a>Aprofundar-se nos dados
Agora vamos explorar em um nível mais detalhado, observando os desempenhos dos distritos.

1. No painel, selecione o bloco **Vendas deste ano, Vendas do ano passado**, que abre a página **Vendas mensais do distrito** do relatório.

   ![Bloco Vendas deste ano, Vendas do ano passado](media/sample-retail-analysis/pbi_sample_retanlareacht.png)

   No gráfico **Percentual de Variação de Vendas total por Mês Fiscal**, observe a grande variabilidade no percentual da variância em relação ao ano passado, com janeiro, abril e julho sendo meses particularmente ruins.

   ![Gráfico Percentual de Variação de Vendas total por Mês Fiscal](media/sample-retail-analysis/pbi_sample_retanlsalesvarcol.png)

   Vamos ver se podemos chegar até onde os problemas podem estar.
2. No gráfico de bolhas, selecione a bolha **020-Mens**.

   ![Selecionar 020-Mens](media/sample-retail-analysis/retail11.png)  

   Observe que, embora a categoria masculina não tenha sido tão severamente afetada em abril como o negócio geral, janeiro e julho ainda foram meses problemáticos.
1. Selecione a bolha**010-Womens**.

   ![Selecionar 010-Womens](media/sample-retail-analysis/retail12.png)

   Observe que a categoria feminina teve um desempenho muito pior que o dos negócios gerais em todos os meses e em quase todos os meses em comparação com o ano anterior.
1. Selecione a bolha novamente para limpar o filtro.

## <a name="try-out-the-slicer"></a>Experimentar a segmentação
Vejamos o desempenho de distritos específicos.

1. Selecione **Allan Guinot** na segmentação do **Gerente do Distrito** no canto superior esquerdo.

   ![Selecionar Allan Guinot](media/sample-retail-analysis/retail13.png)

   Observe que o distrito de Allan teve um desempenho superior em março e junho, em comparação ao ano passado.
2. Com o item **Allan Guinot** ainda selecionado, selecione a bolha **Womens-10** no gráfico de bolhas.

   ![Itens Allan Guinot e Womens-10 selecionados](media/sample-retail-analysis/power-bi-allan.png)

   Observe que, em relação à categoria Womens-10, o distrito de Allan não alcançou o volume do ano passado.
3. Explore os outros gerentes e categorias de distrito – quais outras informações você pode encontrar?
4. Quando estiver pronto, retorne ao painel.

## <a name="what-the-data-says-about-sales-growth-this-year"></a>O que os dados dizem sobre o crescimento de vendas este ano
A última área que queremos explorar é o nosso crescimento, examinando as novas lojas abertas este ano.

1. Selecione o bloco **Lojas abertas este ano por mês aberto, cadeia**, que abre a página **Análise de novas lojas** do relatório.

   ![Página Análise de Novas Lojas](media/sample-retail-analysis/retail15.png)

   Como fica evidente na telha, mais lojas da Fashions Direct do que as lojas da Lindseys abriram este ano.
2. Observe o gráfico **Vendas por pés quadrados por nome**:

   ![Gráfico Vendas por Pé Quadrado por Nome](media/sample-retail-analysis/retail14.png)

    Observe a diferença na média de vendas/pé quadrado nas novas lojas.
3. Selecione o item de legenda **Fashions Direct** no gráfico **Abrir Contagem de Lojas por Mês Aberto e Cadeia** no canto superior direito. Observe, que mesmo para a mesma rede, a melhor loja (Winchester Fashions Direct), em desempenho, significativamente supera a pior loja (Cincinnati 2 Fashions Direct) por US$ 21,22 vs. US$ 12,86, respectivamente.

   ![Opção Fashions Direct selecionada](media/sample-retail-analysis/power-bi-lindseys.png)
4. Selecione **Winchester Fashions Direct** na segmentação **Nome** e observe o gráfico de linhas. Os primeiros números de vendas foram relatados em fevereiro.
5. Selecione **Cincinnati 2 Fashions Direct** na segmentação e você observe no gráfico de linhas que ela foi aberta em junho e parece ser a loja com o pior desempenho.
6. Explore selecionando outras barras, linhas e bolhas nos gráficos e veja quais insights você pode descobrir.

## <a name="next-steps-connect-to-your-data"></a>Próximas etapas: Conecte-se aos seus dados
Esse ambiente é seguro para teste, pois você pode optar por não salvar as alterações. Mas se você salvá-las, sempre é possível selecionar **Obter Dados** para ter uma nova cópia deste exemplo.

Esperamos que este tour tenha mostrado como os painéis, P e R e relatórios do Power BI podem fornecer informações sobre os dados de exemplo. Agora é sua vez – conecte-se aos seus próprios dados. Com o Power BI, é possível se conectar a uma grande variedade de fontes de dados. Para saber mais, confira [Introdução ao serviço do Power BI](service-get-started.md).
