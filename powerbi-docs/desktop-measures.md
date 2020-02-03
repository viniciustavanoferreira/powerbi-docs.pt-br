---
title: Medidas no Power BI Desktop
description: Criar e usar medidas no Power BI Desktop, incluindo medidas rápidas e a sintaxe DAX
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/29/2020
ms.author: davidi
LocalizationGroup: Model your data
ms.openlocfilehash: 9c181deb4e36624fa714242583e3fe209abdfb47
ms.sourcegitcommit: 8b300151b5c59bc66bfef1ca2ad08593d4d05d6a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2020
ms.locfileid: "76889318"
---
# <a name="create-measures-for-data-analysis-in-power-bi-desktop"></a>Criar medidas para análise de dados no Power BI Desktop

O Power BI Desktop ajuda você a criar informações sobre seus dados com apenas alguns cliques. Mas, às vezes, esses dados simplesmente não incluem tudo o que você precisa para responder algumas de suas perguntas mais importantes. As medidas podem ajudá-lo a alcançar essa meta.

As medidas são usadas em algumas das análises de dados mais comuns. Resumos simples, como somas, médias, mínimo, máximo e contagens, podem ser definidos por meio da lista **Campos**. Os resultados calculados das medidas estão sempre mudando em resposta à sua interação com seus relatórios, permitindo uma exploração de dados ad hoc, rápida e dinâmica. Vamos ver isso mais de perto. Para obter mais informações, confira [Criar medidas calculadas](/learn/modules/model-data-power-bi/4b-create-calculated-measures).

## <a name="understanding-measures"></a>Noções básicas sobre medidas

No Power BI Desktop, as medidas são criadas e exibidas na *Exibição de Relatório* ou na *Exibição de Dados*. As medidas que você cria são exibidas na lista **Campos** com um ícone de calculadora. Você pode nomear as medidas como desejar e adicioná-las a uma visualização nova ou existente, assim como com qualquer outro campo.

![Medir campos em Campos](media/desktop-measures/measuresinpbid_measinfieldlist.png)

> [!NOTE]
> Talvez sejam também de seu interesse *medidas rápidas*, que são medidas prontas que podem ser selecionadas nas caixas de diálogo. Elas são uma boa maneira de criar medidas rapidamente e também de aprender a usar a sintaxe DAX (Data Analysis Expressions), pois as fórmulas DAX criadas automaticamente estão disponíveis para análise. Para obter mais informações, confira [Medidas rápidas](desktop-quick-measures.md).
> 
> 

## <a name="data-analysis-expressions"></a>Data Analysis Expressions (expressões de análise de dados)

As medidas calculam um resultado por meio de uma fórmula de expressão. Quando criar suas próprias medidas, você usará a linguagem de fórmula DAX [(Data Analysis Expressions)](/dax/). O DAX inclui uma biblioteca de mais de 200 funções, operadores e constructos. Sua biblioteca fornece uma enorme flexibilidade na criação de medidas para calcular os resultados de praticamente qualquer análise de dados exigida.

As fórmulas DAX são muito semelhantes às fórmulas do Excel. O DAX tem, até mesmo, muitas das mesmas funções do Excel, como `DATE`, `SUM` e `LEFT`. Porém, as funções DAX, destinam-se a funcionar com os dados relacionais, como ocorre no Power BI Desktop.

## <a name="lets-look-at-an-example"></a>Vejamos um exemplo

Sara é gerente de vendas da Contoso. Foi requisitado que ela fornecesse projeções de vendas de revendedores para o próximo ano fiscal. Sara decide basear as estimativas nos valores de vendas do ano passado, com um aumento anual de 6% resultante de várias promoções agendadas para os próximos seis meses.

Para relatar as estimativas, Sara importa os dados de vendas do ano passado para o Power BI Desktop. Ela localiza o campo **SalesAmount** na tabela **Reseller Sales**. Como os dados importados contêm somente valores de vendas do ano passado, Sara renomeia o campo **SalesAmount** como *Last Years Sales*. Em seguida, Sara arrasta **Last Years Sales** para a tela do relatório. Eles aparecem em uma visualização de gráfico como um valor único, que é a soma de todas as vendas dos revendedores do ano anterior.

Sara observa que um cálculo foi fornecido automaticamente, embora ela não tenha especificado nenhum. O Power BI Desktop criou a própria medida somando todos os valores de **Last Years Sales**.

No entanto, Jan precisa de uma medida para calcular as projeções de vendas para o próximo ano, que serão baseadas nas vendas do ano passado multiplicadas por 1,06 para considerar o aumento de 6% esperado nos negócios. Para esse cálculo, ela criará uma medida. Usando o recurso *Nova Medida*, Sara cria uma medida e, em seguida, insere a seguinte fórmula DAX:

```sql
    Projected Sales = SUM('Sales'[Last Years Sales])*1.06
```

Em seguida, ela arrasta a nova medida Projected Sales para o gráfico.

![Novo visual de Projected Sales](media/desktop-measures/measuresinpbid_lastyearsales.png)

Rapidamente e com pouquíssimo trabalho, agora Sara tem uma medida para calcular as vendas projetadas. Sara poderá analisar melhor as projeções filtrando-as por revendedores específicos ou adicionando outros campos ao relatório.

## <a name="data-categories-for-measures"></a>Categorias de dados para medidas

Também é possível escolher as categorias de dados para medidas.

Entre outras coisas, as categorias de dados permitem que você use medidas para criar URLs dinamicamente e marque a categoria de dados como uma URL da Web.

É possível criar tabelas que exibem as medidas como URLs da Web e clicar na URL criada com base em sua seleção. Essa abordagem é especialmente útil quando você deseja criar um vínculo com outros relatórios do Power BI com [parâmetros de filtro de URL](service-url-filters.md).

## <a name="organizing-your-measures"></a>Organizar suas medidas

As medidas têm uma tabela *Início* que define onde elas são encontradas na lista de campos. Você pode alterar a localização escolhendo um local nas tabelas do seu modelo.

![Selecionar uma tabela para sua medida](media/desktop-measures/measures-03.png)

Você também pode organizar os campos de uma tabela em *Pastas de Exibição*. Selecione **Modelo** na borda esquerda do Power BI Desktop. No painel **Propriedades**, selecione o campo que deseja mover da lista de campos disponíveis. Insira um nome para uma nova pasta em **Pasta de exibição** para criar uma pasta. A criação de uma pasta move o campo selecionado para essa pasta.

![Criar um campo para medidas](media/desktop-measures/measures-04.gif)

É possível criar subpastas usando um caractere de barra invertida. Por exemplo, *Finanças\Moedas* cria uma pasta *Finanças* e, dentro dela, uma pasta *Moedas*.

Você pode fazer com que um campo apareça em várias pastas usando um ponto e vírgula para separar os nomes das pastas. Por exemplo, *Produtos\Nomes;Departamentos* faz com que o campo apareça em uma pasta *Departamentos*, bem como em uma pasta *Nomes* dentro da pasta *Produtos*.

Você pode criar uma tabela especial que contenha apenas medidas. Essa tabela sempre é exibida na parte superior dos **Campos**. Para fazer isso, crie uma tabela com apenas uma coluna. Você pode usar **Inserir Dados** para criar essa tabela. Em seguida, mova suas medidas para essa tabela. Por fim, oculte a coluna, mas não a tabela, criada. Selecione a seta na parte superior dos **Campos** para fechar e reabrir a lista de campos e ver as alterações.

![Organizar medidas e mantê-las na parte superior da Lista de Campos](media/desktop-measures/measures-05.png)

## <a name="learn-more"></a>Saiba mais

Fornecemos a você aqui apenas uma rápida introdução às medidas. Há muito mais para ajudar você a aprender a criar suas próprias medidas. Para saber mais, confira [Tutorial: Criar suas próprias medidas no Power BI Desktop](desktop-tutorial-create-measures.md). Baixe um arquivo de exemplo e obtenha lições passo a passo sobre como criar mais medidas.  

Para se aprofundar um pouco mais no DAX, confira [Noções básicas do DAX no Power BI Desktop](desktop-quickstart-learn-dax-basics.md). A [Referência de Data Analysis Expressions](/dax/) fornece artigos detalhados sobre cada uma das funções, sintaxe, operadores e convenções de nomenclatura. O DAX já existe há vários anos no Power Pivot no Excel e no SQL Server Analysis Services. Há muitos outros excelentes recursos disponíveis também. Não deixe de conferir o [Wiki do Centro de Recursos do DAX](https://social.technet.microsoft.com/wiki/contents/articles/1088.dax-resource-center.aspx), no qual membros influentes da comunidade de BI compartilham seus conhecimentos sobre o DAX.
