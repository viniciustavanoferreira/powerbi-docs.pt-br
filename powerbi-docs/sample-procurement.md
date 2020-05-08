---
title: 'Exemplo de Análise de compras: faça um tour'
description: 'Exemplo de Análise de Varejo para o Power BI: faça um tour'
author: maggiesMSFT
ms.reviewer: amac
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 07/02/2019
ms.author: maggies
LocalizationGroup: Samples
ms.openlocfilehash: 8ee77485da03cb8e507d30d511c08aa869c3e4ba
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/05/2020
ms.locfileid: "80404680"
---
# <a name="procurement-analysis-sample-for-power-bi-take-a-tour"></a>Exemplo de Análise de Varejo para o Power BI: faça um tour

O pacote de conteúdo de amostra da Análise de Compras contém um painel, um relatório e um conjunto de dados que analisa os gastos de uma empresa de fabricação em fornecedores por categoria e local. No exemplo, exploraremos essas áreas:

* Quem são os principais fornecedores
* Em quais categorias ocorrem a maioria das despesas
* Quais fornecedores fornecem o desconto mais alto e quando

![Painel para o exemplo de Análise de Compras](media/sample-procurement/procurement1.png)

Este exemplo faz parte de uma série que mostra como o Power BI pode ser usado com dados, relatórios e painéis orientados aos negócios. Ele foi criado pela [obviEnce](http://www.obvience.com/) usando dados reais, que foram mantidos anônimos. Os dados estão disponíveis em vários formatos: pacote de conteúdo, arquivo .pbix do Power BI Desktop ou pasta de trabalho do Excel. Confira [Exemplos para o Power BI](sample-datasets.md). 

Este tutorial explora o pacote de conteúdo de exemplo de Análise de Compras no serviço do Power BI. Como as experiências de relatório são muito semelhantes no Power BI Desktop e no serviço, você também pode acompanhar usando o arquivo de exemplo .pbix no Power BI Desktop. 

Você não precisa de uma licença do Power BI para explorar os exemplos no Power BI Desktop. Se você não tiver uma licença do Power BI Pro, poderá salvar a amostra em Meu Espaço de Trabalho no serviço do Power BI. 

## <a name="get-the-sample"></a>Obter o exemplo

Antes de usar o exemplo, primeiro você deve baixá-lo como um [pacote de conteúdo](#get-the-content-pack-for-this-sample), [arquivo .pbix](#get-the-pbix-file-for-this-sample) ou [pasta de trabalho do Excel](#get-the-excel-workbook-for-this-sample).

### <a name="get-the-content-pack-for-this-sample"></a>Obter o pacote de conteúdo para este exemplo

1. Abra o serviço do Power BI (app.powerbi.com), entre e abra o workspace em que você deseja salvar o exemplo. 

    Se você não tiver uma licença do Power BI Pro, poderá salvar a amostra em Meu Espaço de Trabalho.

2. No canto inferior esquerdo, selecione **Obter Dados**.

    ![Selecionar Obter Dados](media/sample-datasets/power-bi-get-data.png)
3. Na página **Obter Dados** que aparece, selecione **Exemplos**.

4. Selecione **Exemplo de Análise de Compras** e, em seguida, escolha **Conectar**.  
  
   ![Conectar-se ao exemplo](media/sample-procurement/procurement1a.png)
   
5. O Power BI importa o pacote de conteúdo e adiciona um novo painel, um relatório e um conjunto de dados ao seu espaço de trabalho atual.
   
   ![Entrada Exemplo de Análise de Compras](media/sample-procurement/procurement-entry.png)
  
### <a name="get-the-pbix-file-for-this-sample"></a>Obter o arquivo. pbix para este exemplo

Como alternativa, você pode baixar o exemplo de Análise de Compras como um [arquivo .pbix](https://download.microsoft.com/download/D/5/3/D5390069-F723-413B-8D27-5888500516EB/Procurement%20Analysis%20Sample%20PBIX.pbix), que foi projetado para uso com o Power BI Desktop. 

### <a name="get-the-excel-workbook-for-this-sample"></a>Obter a pasta de trabalho do Excel para este exemplo

Se quiser exibir a fonte de dados deste exemplo, ela também está disponível como uma [Pasta de trabalho do Excel](https://go.microsoft.com/fwlink/?LinkId=529784). A pasta de trabalho contém planilhas do Power View que você pode exibir e modificar. Para ver os dados brutos, habilite os suplementos de Análise de Dados e, em seguida, selecione **Power Pivot > Gerenciar**. Para habilitar os suplementos do Power View e do Power Pivot, confira [Explorar os exemplos no Excel](sample-datasets.md#explore-excel-samples-inside-excel) para obter detalhes.


## <a name="spending-trends"></a>Tendências de gastos
Primeiro vamos analisar as tendências em gastos por categoria e local.  

1. No espaço de trabalho onde você salvou o exemplo, abra a guia **Painéis**, localize o painel **Exemplo de Análise de Compras** e selecione-o. 
2. Selecione o bloco do painel, **Total da fatura por país/região**, que abre a página **Visão geral de gastos** do relatório **Exemplo de Análise de Compras**.

    ![Página Visão geral de gastos](media/sample-procurement/procurement2.png)

Observe o seguintes detalhes:

* No gráfico de linhas **Total da fatura por mês e categoria**: a categoria **Direto** apresenta gastos consistentes, **Logística** apresenta um pico em dezembro e **Outros** demonstra um pico em fevereiro.
* No mapa **Total da Fatura por País/Região**: a maioria de nossos gastos está concentrada nos EUA.
* No gráfico de colunas **Total da Fatura por Subcategoria**, **Hardware** e **Serviços e produtos indiretos** são as categorias que apresentam os maiores gastos.
* No gráfico de barras **Total da Fatura por Camada**, a maioria de nossos negócios é feita com nossos fornecedores da Camada 1 (os 10 primeiros). Isso nos permite gerenciar melhor relacionamentos com fornecedores.

## <a name="spending-in-mexico"></a>Gastos no México
Vamos explorar as áreas de gastos no México.

1. No mapa **Total de Faturas por País/Região**, selecione a bolha **México**. Observe que, no gráfico de colunas **Fatura Total por Subcategoria**, a maioria dos gastos está na subcategoria de **Produtos e serviços indiretos**.

   ![Selecione México na página Visão geral de gastos](media/sample-procurement/pbi_procsample_spendmexico.png)
2. Faça uma busca detalhada na coluna **Serviços e produtos indiretos**:

   * No gráfico **Fatura Total por Subcategoria**, selecione a seta de busca ![Seta de busca detalhada](media/sample-procurement/pbi_drilldown_icon.png) no canto superior direito do gráfico.
   * Selecione a coluna **Serviços e produtos indiretos**.

      Como você pode ver, os gastos mais altos, de longe, são para a subcategoria **Vendas e Marketing**.
   * Selecione **México** no mapa novamente.

      Para o México, os maiores gastos estão na subcategoria **Manutenção e Reparo**.

      ![Busca detalhada de Bens Indiretos e Serviços para o México](media/sample-procurement/pbi_procsample_drill_mexico.png)
3. Selecione a seta para cima no canto superior esquerdo do gráfico para fazer drill up.
4. Selecione a seta novamente para desativar os detalhes.  
5. No painel de navegação superior, selecione **Exemplo de Análise de Compras** para retornar ao dashboard.

## <a name="evaluate-different-cities"></a>Avaliar cidades diferentes
Podemos usar o realce para avaliar cidades diferentes.

1. Selecione o bloco do painel, **Percentual do total da fatura e desconto por mês**, que abre a página **Visão geral de desconto** do relatório **Exemplo de Análise de Compras**.
2. No mapa de árvore **Total de faturas por cidade**, selecione cada cidade para ver como elas se comparam. Observe que quase todas as faturas de Miami são de fornecedores de nível 1.

   ![Cidade vs % de desconto por nível](media/sample-procurement/pbi_procsample_miamitreemap2.png)

## <a name="vendor-discounts"></a>Descontos de fornecedor
Também vamos explorar os descontos disponíveis de fornecedores e os períodos de tempo quando chegarmos à maioria dos descontos:
* Os descontos são diferentes a cada mês ou permanecem os mesmos?
* Algumas cidades obtêm mais descontos do que outras?

![Página Análise de desconto](media/sample-procurement/procurement4.png)

### <a name="discount-by-month"></a>Desconto por mês
Se você observar o gráfico de combinação **Total da fatura e % de desconto por mês**, podemos ver que Fevereiro é o mês mais movimentado e que Setembro, o menos movimentado. 

Observe a porcentagem de desconto durante esses meses: quando o volume aumenta, o desconto diminui e quando o volume está baixo, o desconto aumenta. Quanto mais precisarmos de desconto, a negociação é pior.

![Gráfico Percentual do total da fatura e desconto por mês](media/sample-procurement/procurement5.png)

### <a name="discount-by-city"></a>Desconto por cidade
Outra área a explorar é o desconto por cidade. Selecione cada cidade, por sua vez, no mapa da árvore e veja como os outros gráficos mudam:

* St. Louis teve um grande aumento no total de faturas em fevereiro e uma grande queda nas economias de desconto em abril.
* A cidade do México tem a porcentagem de desconto mais alta (11,05%) e Atlanta a menor (0,08%).

![Gráficos de desconto para a cidade do México](media/sample-procurement/procurement6.png)

### <a name="edit-the-report"></a>Editar o relatório
Selecione **Editar relatório** no canto superior esquerdo e explore no Modo de Exibição de Edição:

* Veja como as páginas são feitas.
* Adicione páginas e gráficos com base nos mesmos dados.
* Altere o tipo de visualização para um gráfico; por exemplo, mude o mapa da árvore para um gráfico de rosca.
* Fixe gráficos no seu painel.

## <a name="next-steps-connect-to-your-data"></a>Próximas etapas: conectar-se aos seus dados
Esse ambiente é seguro para teste, pois você pode optar por não salvar as alterações. Mas se você salvá-las, sempre é possível selecionar **Obter Dados** para ter uma nova cópia deste exemplo.

Esperamos que este tour tenha mostrado como os painéis, P e R e relatórios do Power BI podem fornecer informações sobre os dados de exemplo. Agora é sua vez – conecte-se aos seus próprios dados. Com o Power BI, é possível se conectar a uma grande variedade de fontes de dados. Para saber mais, confira [Introdução ao serviço do Power BI](service-get-started.md).

