---
title: 'Tutorial: Criar suas próprias medidas no Power BI Desktop'
description: As medidas no Power BI Desktop ajudam você executando cálculos em seus dados conforme você interage com os relatórios.
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: tutorial
ms.date: 11/08/2019
ms.author: davidi
LocalizationGroup: Learn more
ms.openlocfilehash: 0d2b316b53b4107c86a036cc8a436440dd8bd674
ms.sourcegitcommit: 6272c4a0f267708ca7d38a45774f3bedd680f2d6
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/06/2020
ms.locfileid: "74311515"
---
# <a name="tutorial-create-your-own-measures-in-power-bi-desktop"></a>Tutorial: Criar suas próprias medidas no Power BI Desktop
Usando medidas, você pode criar algumas das soluções de análise de dados mais avançadas no Power BI Desktop. As medidas ajudam você a executar cálculos em seus dados conforme você interage com os relatórios. Este tutorial serve como guia para que você compreenda as medidas e crie suas próprias medidas básicas no Power BI Desktop.

## <a name="prerequisites"></a>Pré-requisitos

- Este tutorial destina-se aos usuários do Power BI já familiarizados com o uso do Power BI Desktop para criar modelos mais avançados. Você já deve estar familiarizado com o uso dos recursos Obter Dados e Editor de Consultas para importar dados, trabalhar com várias tabelas relacionadas e adicionar campos à tela de relatório. Se ainda não estiver familiarizado com o Power BI Desktop, não deixe de conferir a [Introdução ao Power BI Desktop](desktop-getting-started.md).
  
- Este tutorial usa o arquivo [Exemplo de Vendas da Contoso para Power BI Desktop](https://download.microsoft.com/download/4/6/A/46AB5E74-50F6-4761-8EDB-5AE077FD603C/Contoso%20Sales%20Sample%20for%20Power%20BI%20Desktop.zip), que inclui dados de vendas online da empresa fictícia, Contoso. Como esses dados são importados de um banco de dados, você não pode se conectar à fonte de dados para exibi-los no Editor de Consulta. Baixe e extraia o arquivo em seu computador.

## <a name="automatic-measures"></a>Medidas automáticas

Quando o Power BI Desktop cria uma medida, ela é criada com mais frequência para você automaticamente. Para ver como o Power BI Desktop cria uma medida, siga estas etapas:

1. No Power BI Desktop, selecione **Arquivo** > **Abrir**, navegue até o arquivo *Contoso Sales Sample for Power BI Desktop.pbix* e selecione **Abrir**.

2. No painel **Campos**, expanda a tabela **Vendas**. Em seguida, selecione a caixa de seleção ao lado do campo **SalesAmount** ou arraste **SalesAmount** para a tela do relatório.

    Uma nova visualização de gráfico de coluna é exibida, mostrando a soma total de todos os valores na coluna **SalesAmount** da tabela **Sales**.

    ![Gráfico de colunas SalesAmount](media/desktop-tutorial-create-measures/meastut_salesamountchart.png)

Qualquer campo (coluna) no painel **Campos** com um ícone de sigma ![Ícone de sigma](media/desktop-tutorial-create-measures/meastut_sigma.png) é numérico e seus valores podem ser agregados. Em vez de exibir uma tabela com muitos valores (dois milhões de linhas para **SalesAmount**), o Power BI Desktop criará e calculará automaticamente uma medida para agregar os dados se detectar um tipo de dados numérico. Soma é a agregação padrão de um tipo de dados numérico, mas você pode aplicar facilmente agregações diferentes, como média ou contagem. Entender o funcionamento das agregações é fundamental para compreender as medidas, pois cada medida executa algum tipo de agregação. 

Para alterar a agregação do gráfico, siga estas etapas:

1. Selecione a visualização **SalesAmount** na tela do relatório.  

1. Na área **Valor** do painel **Visualizações**, selecione a seta para baixo à direita de **SalesAmount**. 

1. No menu exibido, selecione **Média**. 

    A visualização muda para uma média de todos os valores de vendas no campo **SalesAmount**.

    ![Gráfico de média de SalesAmount](media/desktop-tutorial-create-measures/meastut_salesamountaveragechart.png)

Dependendo do resultado desejado, você pode alterar o tipo de agregação. No entanto, nem todos os tipos de agregação se aplicam a cada tipo de dados numérico. Por exemplo, para o campo **SalesAmount**, Sum e Average são úteis, e Mínimo e Máximo também têm seu lugar. No entanto, Count não faz sentido para o campo **SalesAmount**, porque, embora seus valores sejam numéricos, eles não na verdade monetários.

Os valores calculados por meio de medidas mudam de acordo com as interações em seu relatório. Por exemplo, se você arrastar o campo **RegionCountryName** da tabela **Geografia** para seu gráfico **SalesAmount** existente, ele será alterado para mostrar as quantidades de venda média para cada país.

![SaleAmount por País](media/desktop-tutorial-create-measures/meastut_salesamountavchartbyrcn.png)

Quando o resultado de uma medida é alterado devido a uma interação com seu relatório, você afetou o *contexto* da sua medida. Sempre que você interage com as visualizações de seu relatório, você altera o contexto no qual uma medida calcula e exibe seus resultados.

## <a name="create-and-use-your-own-measures"></a>Criar e usar suas próprias medidas

Na maioria dos casos, o Power BI Desktop calcula e retorna valores automaticamente de acordo com os tipos de campos e agregações escolhidos. No entanto, em alguns casos, talvez convenha criar suas próprias medidas para executar cálculos mais complexos e exclusivos. Com o Power BI Desktop, você pode criar suas próprias medidas com a linguagem de fórmula DAX (Data Analysis Expressions). 

Fórmulas DAX usam muitos operadores, funções e sintaxe também utilizados pelas fórmulas do Excel. No entanto, as funções DAX foram projetadas para trabalhar com dados relacionais e realizar cálculos mais dinâmicos durante sua interação com os relatórios. Há mais de 200 funções DAX que fazem tudo, desde agregações simples, como Soma e Média, até funções de estatística e de filtragem mais complexas. Há muitos recursos para ajudar você a saber mais sobre o DAX. Após concluir este tutorial, confira [Conceitos básicos do DAX no Power BI Desktop](desktop-quickstart-learn-dax-basics.md).

Quando você cria sua própria medida, ela é camada de medida *modelo* e adicionada à lista **Campos** da tabela selecionada. Entre as vantagens das medidas de modelo estão a possibilidade de nomeá-las como você quiser, tornando-as mais identificáveis; você pode usá-las como argumentos em outras expressões DAX; e pode fazer com que executem rapidamente cálculos complexos.

### <a name="quick-measures"></a>Medidas rápidas

A partir da versão de fevereiro de 2018 do Power BI Desktop, muitos cálculos comuns foram disponibilizados como *medidas rápidas*, que escrevem as fórmulas DAX para você com base em suas entradas em uma janela. Esses cálculos rápidos e eficientes também são ótimos para aprender DAX ou propagar suas próprias medidas personalizadas. 

Crie uma medida rápida usando um destes métodos: 
 - Em uma tabela no painel **Campos**, clique com o botão direito do mouse em **Mais opções** ( **...** ) ou selecione-o e, em seguida, selecione **Nova medida rápida** na lista.

 - Em **Cálculos**, na guia **Página Inicial** da faixa de opções do Power BI Desktop, selecione **Nova Medida Rápida**.

Para obter mais informações sobre como criar e usar medidas rápidas, confira [Usar medidas rápidas](desktop-quick-measures.md).

### <a name="create-a-measure"></a>Criar uma medida

Vamos supor que você deseja analisar as vendas líquidas subtraindo descontos e devoluções dos valores toais de vendas. Para o contexto existente em sua visualização, você precisa de uma medida que subtraia a soma de DiscountAmount e ReturnAmount da soma de SalesAmount. Não há um campo para Vendas Líquidas na lista **Campos**, mas você tem os blocos de construção para criar sua própria medida para calcular as vendas líquidas. 

Para criar uma nova oferta, siga estas etapas:

1. No painel **Campos**, clique com o botão direito do mouse na tabela **Vendas** ou passe o mouse sobre a tabela e selecione **Mais opções** ( **...** ). 

1. No menu exibido, selecione **Nova medida**. 

    Essa ação salva sua nova medida na tabela **Vendas**, em que será encontrada mais facilmente.
    
    ![Nova medida da lista](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure.png)
    
    Você também pode criar uma medida selecionando **Nova Medida** no grupo **Cálculos** na guia **Página Inicial** da faixa de opções do Power BI Desktop.
    
    ![Nova medida na faixa de opções](media/desktop-tutorial-create-measures/meastut_netsales_newmeasureribbon.png)
    
    >[!TIP]
    >Ao criar uma medida da faixa de opções, você pode criá-la em qualquer uma de suas tabelas, mas será mais fácil localizá-la se você criá-la onde planeja usá-la. Nesse caso, selecione a tabela **Vendas** primeiro para torná-la ativa e selecione **Nova medida**. 
    
    A barra de fórmulas aparece na parte superior da tela do relatório, em que você pode renomear a medida e inserir uma fórmula DAX.
    
    ![Barra de fórmulas](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure_formulabar.png)
    
1. Por padrão, cada nova medida é denominada *Medida*. Se você não a renomear, medidas novas adicionais serão renomeadas *Medida 2*, *Medida 3* e assim por diante. Como desejamos que essa medida se torne mais identificável, realce *Medida* na barra de fórmulas e a altere para *Vendas Líquidas*.
    
1. Comece a inserir sua fórmula. Após o sinal de igual, comece a digitar *Sum*. Conforme você digita, surge uma lista suspensa com sugestões, mostrando todas as funções DAX que começam com as letras que você digitou. Role para baixo, se necessário, para selecionar **SUM** na lista e pressione **Enter**.
    
    ![Escolher SUM na lista](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure_formula_s.png)
    
    Um parêntese de abertura é exibido junto com uma lista suspensa de sugestões das colunas disponíveis que você pode passar para a função SUM.
    
    ![Escolher a coluna](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure_formula_sum.png)
    
1. As expressões sempre aparecem entre parênteses de abertura e de fechamento. Neste exemplo, sua expressão contém um único argumento a ser passado para a função SUM: a coluna **SalesAmount**. Comece digitando *SalesAmount* até que **Sales(SalesAmount)** seja o único valor restante na lista. 

    O nome da coluna precedido pelo nome da tabela é denominado nome totalmente qualificado da coluna. Os nomes de coluna totalmente qualificados tornam suas fórmulas mais legíveis.
    
    ![Selecione SalesAmount](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure_formula_salesam.png)
    
1. Selecione **Sales[SalesAmount]** na lista e insira um parêntese de fechamento.
    
    > [!TIP]
    > Erros de sintaxe são causados frequentemente por um parêntese de fechamento ausente ou mal posicionado.
    
    
    
1. Subtraia as outras duas colunas dentro da fórmula:

    a. Após o parêntese de fechamento da primeira expressão, digite um espaço, um operador de subtração (-) e o outro espaço. 

    b. Insira outra função SUM e comece digitando *DiscountAmount* até que você possa escolher a coluna **Sales[DiscountAmount]** como o argumento. Adicione um parêntese de fechamento. 

    c. Digite um espaço, um operador de subtração, espaço, outra função SUM com **Sales[ReturnAmount]** como o argumento e um parêntese de fechamento.
    
    ![Fórmula completa](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure_formula_discamount.png)
    
1. Pressione **Enter** ou selecione **Confirmar** (ícone de marca de confirmação) na barra de fórmulas para concluir e validar a fórmula. 

    A medida **Vendas Líquidas** validada está pronta para uso na tabela **Vendas** no painel **Campos**.
    
    ![Medida Vendas Líquidas na lista de campos da tabela Vendas](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure_complete.png)
    
1. Se você ficar sem espaço para inserir uma fórmula ou desejar colocá-la em linhas separadas, selecione a seta para baixo do lado direito da barra de fórmulas para abrir mais espaço. 

    A seta para baixo se transforma em uma seta para cima e uma caixa grande é exibida.

    ![Seta para cima da fórmula](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure_formula_chevron.png)

1. Separe partes de sua fórmula pressionando **Alt** + **Enter** para linhas separadas ou pressionando **Tab** para adicionar espaçamento de tabulação.

   ![Fórmula expandida](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure_formula_expanded.png)

### <a name="use-your-measure-in-the-report"></a>Usar sua medida no relatório
Adicione sua nova medida **Vendas Líquidas** à tela do relatório e calcule as vendas líquidas para outros campos que você adicionar ao relatório. 

Para examinar as vendas líquidas por país:

1. Selecione a medida **Net Sales** na tabela **Sales**, ou arraste-a até a tela do relatório.
    
1. Selecione o campo **RegionCountryName** na tabela **Geografia** ou arraste-o até o gráfico **Vendas Líquidas**.
    
    ![Vendas líquidas por país](media/desktop-tutorial-create-measures/meastut_netsales_byrcn.png)
    
1. Para ver a diferença entre o valor total de vendas e o de vendas líquidas, selecione o campo **SalesAmount** ou arraste-o até o gráfico. 

    ![Valor de vendas e Vendas líquidas por país](media/desktop-tutorial-create-measures/meastut_netsales_byrcnandsalesamount.png)

    Agora, o gráfico usa duas medidas: **SalesAmount**, que o Power BI somou automaticamente, e a medida **Vendas Líquidas**, que você criou manualmente. Cada medida foi calculada no contexto de outro campo, **RegionCountryName**.
    
### <a name="use-your-measure-with-a-slicer"></a>Usar sua medida com uma segmentação de dados

Adicione uma segmentação de dados para filtrar ainda mais as vendas líquidas e valores de vendas por ano calendário:
    
1. Selecione uma área em branco ao lado do gráfico. No painel **Visualizações**, selecione a visualização **Tabela**. 

    Essa ação cria uma visualização de tabela em branco na tela do relatório.
    
    ![Nova visualização de tabela em branco](media/desktop-tutorial-create-measures/meastut_netsales_blanktable.png)
    
1. Arraste o campo **Ano** da tabela **Calendário** até a nova visualização de tabela em branco. 
    
    Como **Ano** é um campo numérico, o Power BI Desktop soma seus valores. Essa soma não funciona bem como uma agregação; abordaremos isso na próxima etapa.

    ![Agregação de anos](media/desktop-tutorial-create-measures/meastut_netsales_yearaggtable.png)
    
3. Na caixa **Valores** no painel **Visualizações**, selecione a seta para baixo ao lado de **Ano** e, em seguida, selecione **Não resumir** na lista. Agora, a tabela lista os anos individuais.
    
    ![Selecionar Não resumir](media/desktop-tutorial-create-measures/meastut_netsales_year_donotsummarize.png)
    
4.  Selecione o ícone **Segmentação de Dados** no painel **Visualizações** para converter a tabela em uma segmentação de dados. Se a visualização exibir um controle deslizante em vez de uma lista, selecione **Lista** na seta para baixo no controle deslizante.

    ![Converter tabela em segmentação de dados](media/desktop-tutorial-create-measures/meastut_netsales_year_changetoslicer.png)
    
5.  Selecione qualquer valor na segmentação de dados **Ano** para filtrar o gráfico **Vendas líquidas e valor das vendas por RegionCountryName** adequadamente. As medidas **Vendas Líquidas** e **SalesAmount** são recalculadas e exibem os resultados no contexto do campo **Ano** selecionado. 
    
    ![Gráfico segmentado por ano](media/desktop-tutorial-create-measures/meastut_netsales_chartslicedbyyear.png)

### <a name="use-your-measure-in-another-measure"></a>Usar sua medida em outra medida

Vamos supor que você deseje descobrir quais produtos têm o maior valor de vendas líquidas por unidade vendida. Você precisará de uma medida que divida as vendas líquidas pela quantidade de unidades vendidas. Criar uma medida que divida o resultado de sua medida **Vendas Líquidas** pela soma de **Sales[SalesQuantity]** .

1.  No painel **Campos**, crie uma medida chamada **Vendas Líquidas por Unidade** na tabela **Vendas**.
    
1. Na barra de fórmulas, comece digitando *Net Sales*. A lista de sugestões mostra o que você pode adicionar. Selecione **[Net Sales]** .
    
    ![Fórmula usando Net Sales](media/desktop-tutorial-create-measures/meastut_nspu_formulastep2a.png)
    
1. Você também pode fazer referência a medidas digitando apenas um colchete de abertura ( **[** ). A lista de sugestões mostra apenas as medidas a serem adicionas à sua fórmula.
    
    ![Colchete mostra apenas as medidas](media/desktop-tutorial-create-measures/meastut_nspu_formulastep2b.png)
    
1. Insira um espaço, um operador de divisão (/), outro espaço, uma função SUM e digite *Quantity*. A lista de sugestões mostra todas as colunas com *Quantity* no nome. Selecione **Sales[SalesQuantity]** , digite o parêntese de fechamento e pressione **ENTER** ou selecione **Confirmar** (ícone de marca de confirmação) para validar sua fórmula. 

    A fórmula resultante deve aparecer como:
    
    `Net Sales per Unit = [Net Sales] / SUM(Sales[SalesQuantity])`
    
1. Selecione a medida **Vendas Líquidas por Unidade** na tabela **Vendas** ou arraste-a até uma área em branco na tela do relatório. 

    O gráfico mostra a quantidade de vendas líquida por unidade de todos os produtos vendidos. Este gráfico não é muito informativo; abordaremos isso na próxima etapa.
    
    ![Vendas líquidas gerais por unidade](media/desktop-tutorial-create-measures/meastut_nspu_chart.png)
    
1. Para ver de outro jeito, altere o tipo de visualização de gráfico para **Mapa de árvore**.
    
    ![Alterar para mapa de árvore](media/desktop-tutorial-create-measures/meastut_nspu_changetotreemap.png)
    
1. Selecione o campo **Categoria de Produto** e arraste-o até o mapa de árvore ou até o campo **Grupo** do painel **Visualizações**. Agora você tem informações úteis!
    
    ![Mapa de árvore por categoria de produto](media/desktop-tutorial-create-measures/meastut_nspu_byproductcat.png)
    
7. Tente remover o campo **ProductCategory** e arrastar o campo **ProductName** até o gráfico em vez disso. 
    
    ![Treemap por nome de produto](media/desktop-tutorial-create-measures/meastut_nspu_byproductname.png)
    
   OK, agora estamos apenas experimentando, mas você tem que admitir, isso é muito legal! Experimente outras maneiras de filtrar e formatar a visualização.

## <a name="what-youve-learned"></a>O que você aprendeu
As medidas proporcionam a capacidade para obter as informações que você quer de seus dados. Você aprendeu a criar medidas usando a barra de fórmulas, a nomeá-las de um jeito que faça mais sentido e a localizar e selecionar os elementos certos para as fórmulas usando as listas de sugestão de DAX. Você também foi apresentado ao contexto, no qual o resultado dos cálculos em medidas muda de acordo com outros campos ou outras expressões em sua fórmula.

## <a name="next-steps"></a>Próximas etapas
- Para saber mais sobre medidas rápidas do Power BI Desktop, que fornecem muitos cálculos de medida comum para você, consulte [Usar medidas rápidas para realizar facilmente cálculos avançados e comuns](desktop-quick-measures.md).
  
- Se desejar se aprofundar nas fórmulas DAX e criar algumas medidas mais avançadas, veja [Noções básicas do DAX no Power BI Desktop](desktop-quickstart-learn-dax-basics.md). Este artigo enfoca os conceitos fundamentais no DAX, como sintaxe, funções e uma compreensão mais abrangente sobre o contexto.
  
- Certifique-se de adicionar a [Referência ao DAX (Expressões de Análise de Dados)](https://docs.microsoft.com/dax/index) aos favoritos. É nessa referência em que você encontrará informações detalhadas sobre a sintaxe do DAX, operadores, além de mais de 200 funções DAX.

