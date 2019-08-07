---
title: Usar medidas no Power BI Desktop
description: Medidas no Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 07/29/2019
ms.author: davidi
LocalizationGroup: Model your data
ms.openlocfilehash: 431c1738a5d2e975fd96a8209ca8245cd4414d40
ms.sourcegitcommit: 73228d0a9038b8369369c059ad06168d2c5ff062
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/02/2019
ms.locfileid: "68730170"
---
# <a name="measures-in-power-bi-desktop"></a>Medidas no Power BI Desktop

O **Power BI Desktop** ajuda a criar informações sobre seus dados com apenas alguns cliques. Mas, às vezes, esses dados simplesmente não incluem tudo o que você precisa para responder algumas de suas perguntas mais importantes. As medidas podem ajudá-lo a alcançar essa meta.

As medidas são usadas em algumas das análises de dados mais comuns. Resumos simples, como somas, médias, mínimo, máximo e contagens, podem ser definidos na lista Campos, como discutido no vídeo de [Resumo e categoria](https://docs.microsoft.com/power-bi/guided-learning/visualizations?tutorial-step=16). Você pode criar cálculos mais avançados usando uma fórmula DAX. Os resultados calculados das medidas estão sempre mudando em resposta à sua interação com seus relatórios, permitindo uma exploração de dados ad hoc, rápida e dinâmica. Vamos ver isso mais de perto.

## <a name="understanding-measures"></a>Noções básicas sobre medidas

No **Power BI Desktop**, as medidas são criadas e exibidas na **Exibição de Relatório** ou na **Exibição de Dados**. As medidas que você cria são exibidas na lista Campos com um ícone de calculadora. Você pode nomear as medidas como desejar e adicioná-las a uma visualização nova ou existente, assim como com qualquer outro campo.

![](media/desktop-measures/measuresinpbid_measinfieldlist.png)

> [!NOTE]
> Talvez sejam também de seu interesse **medidas rápidas**, que são medidas prontas que podem ser selecionadas nas caixas de diálogo. Elas são uma boa maneira de criar medidas rapidamente e também de aprender a sintaxe DAX, uma vez que suas fórmulas DAX criadas automaticamente estão disponíveis para examinar. Confira o artigo: [medidas rápidas](desktop-quick-measures.md).
> 
> 

## <a name="data-analysis-expressions"></a>Data Analysis Expressions (expressões de análise de dados)

As medidas calculam um resultado por meio de uma fórmula de expressão. Quando criar suas próprias medidas, você usará a linguagem de fórmula DAX [(Data Analysis Expressions)](https://msdn.microsoft.com/library/gg413422.aspx). O DAX inclui uma biblioteca de mais de 200 funções, operadores e constructos. Sua biblioteca fornece uma enorme flexibilidade na criação de medidas para calcular os resultados de praticamente qualquer análise de dados exigida.

As fórmulas DAX são muito semelhantes às fórmulas do Excel. O DAX tem muitas das mesmas funções que o Excel, como DATE, SUM e LEFT. As funções do DAX, no entanto, devem funcionar com dados relacionais, como os que temos no Power BI Desktop.

## <a name="lets-look-at-an-example"></a>Vejamos um exemplo
Sara é gerente de vendas da Contoso. Foi requisitado que ela fornecesse projeções de vendas de revendedores para o próximo ano fiscal. Sara decide basear suas estimativas nos valores de vendas do ano anterior, com um aumento anual de 6% resultante de várias promoções agendadas para os próximos seis meses.

Para relatar as estimativas, Sara importa os dados de vendas do ano anterior para o Power BI Desktop. Ela localiza o campo SalesAmount na tabela Reseller Sales. Como os dados importados contêm somente valores de vendas do ano anterior, Sara renomeia o campo SalesAmount como Last Years Sales. Em seguida, Sara arrasta Last Years Sales para a tela do relatório. Eles aparecem em uma visualização de gráfico como um valor único, que é a soma de todas as vendas dos revendedores do ano anterior.

Sara observa que um cálculo foi fornecido automaticamente, embora ela não tenha especificado nenhum. O Power BI Desktop criou sua própria medida somando todos os valores em Last Years Sales.

No entanto, Sara precisa de uma medida para calcular as projeções de vendas para o próximo ano, que serão baseadas nas vendas do ano anterior multiplicadas por 1,06 - para considerar o aumento de 6% esperado nos negócios. Para esse cálculo, ela criará sua própria medida. Usando o recurso Nova Medida, ela cria uma nova medida e, em seguida, insere a seguinte fórmula DAX:

    Projected Sales = SUM('Sales'[Last Years Sales])*1.06

Em seguida, Sara arrasta sua nova medida Projected Sales até o gráfico.

![](media/desktop-measures/measuresinpbid_lastyearsales.png)

Rapidamente e com pouquíssimo trabalho, agora Sara tem uma medida para calcular as vendas projetadas. Sara poderá analisar melhor suas projeções filtrando por revendedores específicos ou adicionando outros campos ao relatório.

## <a name="data-categories-for-measures"></a>Categorias de dados para medidas

Também é possível escolher as categorias de dados para medidas. 

Entre outras coisas, isso permite que você use medidas para criar URLs dinamicamente e marcar a categoria de dados como uma URL da Web. 

É possível criar tabelas que exibem as medidas como URLs da Web e clicar na URL criada com base em sua seleção. Isso será especialmente útil quando você desejar vincular a outros relatórios do Power BI com [parâmetros de filtro de URL](service-url-filters.md).


## <a name="organizing-your-measures"></a>Organizar suas medidas

As medidas têm uma tabela *Início* que define onde elas são encontradas na lista de campos. Você pode alterar a localização escolhendo um local nas tabelas do seu modelo.

![Selecionar uma tabela para sua medida](media/desktop-measures/measures-03.png)

Você também pode organizar os campos de uma tabela em *Pastas de Exibição*. Selecione **Exibição de Modelo** no lado esquerdo da janela de Power BI Desktop, em seguida, selecione o campo que você deseja mover da lista de campos disponíveis exibidos na tela. No painel de propriedades, uma caixa de texto aparece para a **Pasta de exibição**. Digite um nome no campo **Pasta de exibição**, crie a pasta e mova o campo selecionado para essa pasta.

![Criar um campo para medidas](media/desktop-measures/measures-04.gif)

É possível criar subpastas usando um caractere de barra invertida. Por exemplo, *Finanças\Moedas* cria uma pasta *Finança* e, dentro dela, uma pasta *Moedas*.

Você pode fazer com que um campo apareça em várias pastas usando um ponto e vírgula para separar os nomes das pastas. Por exemplo, *Produtos\Nomes;Departamentos* faz com que o campo apareça em uma pasta *Departamentos*, bem como em uma pasta *Nomes* dentro da pasta *Produtos*.

Por fim, você pode criar uma tabela especial que contenha apenas medidas que sempre aparecem na parte superior da **Lista de Campos**. Para fazer isso, crie uma tabela com apenas uma coluna. Você pode usar **Inserir Dados** para criar essa tabela. Em seguida, mova suas medidas para essa tabela. Por fim, oculte a coluna (não a tabela) criada. Você precisará fechar e reabrir a **Lista de Campos** para que o Power BI Desktop a exiba corretamente, clicando na divisa na parte superior da **Lista de Campos**.

![Organizar medidas e mantê-las na parte superior da Lista de Campos](media/desktop-measures/measures-05.png)

## <a name="learn-more"></a>Saiba mais
Fornecemos aqui apenas uma rápida introdução às medidas, mas há muito mais conteúdo para lhe ajudar a criá-las por conta própria. Não deixe de conferir o [Tutorial: Criar suas próprias medidas no Power BI Desktop](desktop-tutorial-create-measures.md), em que você pode baixar um arquivo de exemplo e obter lições passo a passo sobre como criar mais medidas.  

Para se aprofundar mais no DAX, não deixe de conferir [DAX basics in Power BI Desktop](desktop-quickstart-learn-dax-basics.md) (Noções básicas do DAX no Power BI Desktop). A [Referência de Data Analysis Expressions](https://msdn.microsoft.com/library/gg413422.aspx) fornece artigos detalhados sobre cada uma das funções, sintaxe, operadores e convenções de nomenclatura. O DAX já existe há muitos anos no Power Pivot no Excel e no SQL Server Analysis Services; portanto, há muitos outros recursos excelentes disponíveis também. Não deixe de conferir o [Wiki do Centro de Recursos do DAX](http://social.technet.microsoft.com/wiki/contents/articles/1088.dax-resource-center.aspx), no qual membros influentes da comunidade de BI compartilham seus conhecimentos sobre o DAX.



