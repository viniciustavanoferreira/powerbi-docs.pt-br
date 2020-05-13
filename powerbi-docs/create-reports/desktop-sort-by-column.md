---
title: Classificação por coluna no Power BI Desktop
description: No Power BI, é possível alterar a aparência de um visual classificando-o segundo diferentes campos de dados.
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/30/2020
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: db5bc2566e4711873629522d08a2d0c818071b81
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83334029"
---
# <a name="sort-by-column-in-power-bi-desktop"></a>Classificação por coluna no Power BI Desktop
No Power BI Desktop e no serviço do Power BI, é possível alterar a aparência de um visual classificando-o segundo diferentes campos de dados. Ao alterar a maneira como você classifica um visual, é possível realçar as informações que você deseja transmitir e garantir de que o visual reflita essa tendência (ou ênfase).

Se estiver usando dados numéricos (como valores de vendas) ou dados de texto (como nomes de estado), você pode classificar suas visualizações e fazer com que elas tenham a aparência desejada. O Power BI oferece muita flexibilidade para a classificação e menus rápidos para você usar. Para classificar qualquer visual, selecione seu menu **Mais ações** (...), selecione **Classificar por** e, em seguida, selecione o campo segundo o qual deseja classificar.

![Menu Mais opções](media/desktop-sort-by-column/sortbycolumn_2.png)

## <a name="sorting-example"></a>Exemplo de classificação
Vamos usar um exemplo com mais detalhes e ver como ele funciona no Power BI Desktop.

A visualização a seguir mostra os custos, quantidades e montantes pelo nome do fabricante. Esta é a aparência da visualização antes de fazermos qualquer classificação:

![Visualização inicial](media/desktop-sort-by-column/sortbycolumn_1.png)

O visual está classificado pela coluna **SalesQuantity**. Podemos determinar a coluna de classificação combinando a cor das barras crescentes com a legenda, mas há uma maneira melhor: o menu **Mais opções**, que você acessa selecionando as reticências (...).

![Menu Mais opções](media/desktop-sort-by-column/sortbycolumn_2.png)

As seleções de classificação são as seguintes:

* O campo de classificação atual é **SalesQuantity**, indicado por **SalesQuantity** em negrito precedido por uma barra amarela. 

* A direção de classificação atual é crescente, conforme mostrado por **Classificação crescente** em negrito precedido por uma barra amarela.

Examinaremos o campo e a direção de classificação nas duas próximas seções.

## <a name="select-which-column-to-use-for-sorting"></a>Selecione a coluna a ser usada para classificação
Você observou a barra amarela ao lado de **SalesQuantity** no menu **Mais opções**, indicando que o visual está classificado pela coluna **SalesQuantity**. Classificar por outra coluna é fácil: selecione as reticências (...) para mostrar o menu **Mais opções**, selecione **Classificar por** e, em seguida, selecione uma coluna diferente.

Na imagem a seguir, selecionamos **DiscountAmount** como a coluna segundo a qual queremos classificar. Essa coluna aparece como uma das linhas no visual, e não como uma das barras. 

![Classificar por DiscountAmount](media/desktop-sort-by-column/sortbycolumn_3.png)

Observe como o visual foi alterado. Agora, os valores estão ordenados do valor mais alto de **DiscountAmount**, que é Fabrikam Inc., para o valor mais baixo, que é Northwind Traders. 

Mas e se quisermos classificar em ordem crescente em vez de decrescente? A próxima seção mostra como é fácil faz isso.

## <a name="select-the-sort-order"></a>Selecionar a ordem de classificação
Quando examinamos mais detalhadamente o menu **Mais opções** da imagem anterior, vemos que **Classificação decrescente** está em negrito, precedido por uma barra amarela.

![Classificar do maior para o menor](media/desktop-sort-by-column/sortbycolumn_4.png)

Quando **Classificação decrescente** está selecionado, isso significa que o visual está sendo classificado segundo a coluna selecionada na ordem do maior valor para o menor. Quer mudar? Sem problemas, basta selecionar **Classificação crescente** e a ordem de classificação da coluna selecionada muda do menor para o maior valor.

Aqui está o mesmo visual, depois de alterar a classificação de **DiscountAmount**. Observe que a Northwind Traders agora é o primeiro fabricante listado e que a Fabrikam Inc. é o último, em uma classificação oposta à anterior.

![Classificar do menor para o maior](media/desktop-sort-by-column/sortbycolumn_5.png)

É possível classificar segundo qualquer coluna incluída no visual – nós poderíamos facilmente ter selecionado **SalesQuantity** como a coluna segundo a qual queremos classificar, para mostrar os fabricantes com mais vendas primeiro e ainda manter as outras colunas no visual da forma como se aplicam ao fabricante. Veja o visual com essas configurações:

![Classificar por SalesQuantity](media/desktop-sort-by-column/sortbycolumn_6.png)

## <a name="sort-using-the-sort-by-column-button"></a>Classificar usando o botão Classificar por Coluna
Há outra maneira de classificar os dados, usando o botão **Classificar por Coluna** na faixa de opções **Modelagem**.

![Botão Classificar por Coluna](media/desktop-sort-by-column/sortbycolumn_8.png)

Essa abordagem à classificação exige que primeiro você selecione a coluna (campo) para classificação no painel **Campos** e, em seguida, selecione **Modelagem** > **Classificar por Coluna** para classificar seu visual. Se você não selecionar uma coluna, o botão **Classificar por Coluna** ficará inativo.

Vejamos um exemplo comum. Você tem dados de cada mês do ano e deseja classificá-los com base na ordem cronológica. As etapas a seguir mostram como fazer isso:

1. Observe que quando o visual é selecionado, mas nenhuma coluna é selecionada no painel **Campos**, o botão **Classificar por Coluna** fica inativo (esmaecido).
   
   ![Botão Classificar por Coluna inativo](media/desktop-sort-by-column/sortbycolumn_9.png)

2. Quando selecionamos a coluna pela qual queremos classificar no painel **Campos**, o botão **Classificar por Coluna** se torna ativo.
   
   ![Botão Classificar por Coluna ativo](media/desktop-sort-by-column/sortbycolumn_10.png)
3. Agora, com o visual selecionado, podemos selecionar **MonthOfYear** em vez do padrão **MonthName**, e o visual faz a classificação na ordem que queremos: por mês do ano.
   
   ![Menu Classificar por Coluna](media/desktop-sort-by-column/sortbycolumn_11.png)


<!---
This functionality is no longer active. Jan 2020

## Getting back to default column for sorting
You can sort by any column you'd like, but there may be times when you want the visual to return to its default sorting column. No problem. For a visual that has a sort column selected, open the **More options** menu and select that column again, and the visualization returns to its default sort column.

For example, here's our previous chart:

![Initial visualization](media/desktop-sort-by-column/sortbycolumn_6.png)

When we go back to the menu and select **SalesQuantity** again, the visual defaults to being ordered alphabetically by **Manufacturer**, as shown in the following image.

![Default sort order](media/desktop-sort-by-column/sortbycolumn_7.png)

With so many options for sorting your visuals, creating just the chart or image you want is easy.
--->

## <a name="next-steps"></a>Próximas etapas

Você também pode estar interessado nos seguintes artigos:

* [Usar o detalhamento no Power BI Desktop](desktop-cross-report-drill-through.md)
* [Segmentações no Power BI](../visuals/power-bi-visualization-slicers.md)
