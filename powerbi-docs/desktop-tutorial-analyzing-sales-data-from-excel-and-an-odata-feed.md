---
title: 'Tutorial: combinar dados do Excel e de um feed OData no Power BI Desktop'
description: 'Tutorial: combinar dados do Excel e de um feed OData'
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: tutorial
ms.date: 01/17/2020
ms.author: davidi
LocalizationGroup: Learn more
ms.openlocfilehash: 0e3f742e0ad9d3b9bf81c9dd95e9193413a70d6a
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/05/2020
ms.locfileid: "76539913"
---
# <a name="tutorial-analyze-sales-data-from-excel-and-an-odata-feed"></a>Tutorial: Analisar dados de vendas do Excel e de um feed OData

É comum ter dados em várias fontes de dados. Por exemplo, você poderia ter dois bancos de dados, um para informações sobre o produto e outro para informações de vendas. Com o *Power BI Desktop*, é possível combinar dados de diferentes origens para criar visualizações e análises de dados interessantes e atrativas.

Neste tutorial, você combinará dados de duas fontes de dados:

* Uma pasta de trabalho do Excel com informações sobre o produto
* Um feed OData contendo dados de pedidos

Você vai importar cada conjunto de dados e realizar operações de transformação e agregação. Em seguida, você usará os dados das duas fontes para produzir um relatório de análise de vendas com visualizações interativas. Depois, você pode aplicar essas técnicas a consultas de SQL Server, arquivos CSV e outras fontes de dados no Power BI Desktop.

>[!NOTE]
>No Power BI Desktop, normalmente há algumas maneiras de realizar uma mesma tarefa. Por exemplo, você pode clicar com o botão direito do mouse ou usar um menu **Mais opções** em uma coluna ou célula para ver mais seleções da faixa de opções. Vários métodos alternativos são descritos nas etapas abaixo.

## <a name="import-excel-product-data"></a>Importar dados de produto do Excel

Primeiro, importe os dados de produto da pasta de trabalho *Products.xlsx* do Excel para o Power BI Desktop.

1. [Baixe a pasta de trabalho Products.xlsx do Excel](https://download.microsoft.com/download/1/4/E/14EDED28-6C58-4055-A65C-23B4DA81C4DE/Products.xlsx) e salve-a como *Products.xlsx*.

1. Selecione a seta ao lado de **Obter Dados** na guia **Página Inicial** da faixa de opções do Power BI Desktop e, em seguida, selecione **Excel** no menu **Mais Comum**.

   ![Obter dados](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_1.png)

   >[!NOTE]
   >Também é possível selecionar o próprio item **Obter Dados** ou, ainda, selecionar **Obter Dados** na caixa de diálogo **Começar** do Power BI e, em seguida, selecionar **Excel** ou **Arquivo** > **Excel** na caixa de diálogo **Obter Dados** e, então, selecionar **Conectar**.

1. Na caixa de diálogo **Abrir**, navegue até o arquivo **Products.xlsx** e selecione-o e, em seguida, selecione **Abrir**.

1. No **Navegador**, selecione a tabela **Products** e, em seguida, **Transformar Dados**.

   ![Painel Navegador do Excel](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_2.png)

Uma visualização de tabela é aberta no Editor do Power Query, no qual é possível aplicar transformações para limpar os dados.

![Editor do Power Query](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_3.png)

>[!NOTE]
>Você também pode abrir o Editor do Power Query selecionando **Editar Consultas** > **Editar Consultas** da faixa de opções **Página Inicial** no Power BI Desktop ou clicando com o botão direito do mouse ou escolhendo **Mais opções** ao lado de qualquer consulta na exibição **Relatório** e selecionando **Editar Consulta**.

## <a name="clean-up-the-products-columns"></a>Limpar as colunas de produtos

Seu relatório combinado usará as colunas **ProductID**, **ProductName**, **QuantityPerUnit** e **UnitsInStock** da pasta de trabalho do Excel. Você pode remover as outras colunas.

1. No Editor do Power Query, selecione as colunas **ProductID**, **ProductName**, **QuantityPerUnit** e **UnitsInStock**. Você pode usar Ctrl para selecionar mais de uma coluna ou Shift para selecionar colunas próximas umas das outras.

1. Clique com o botão direito do mouse em qualquer um dos cabeçalhos selecionados. Selecione **Remover Outras Colunas** no menu suspenso.
   Também é possível selecionar **Remover Colunas** > **Remover Outras Colunas** do grupo **Gerenciar Colunas** na guia de faixa de opções **Início**.

   ![Remover outras colunas](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/analyzingsalesdata_removeothercolumns.png)

## <a name="import-the-odata-feeds-order-data"></a>Importar os dados de pedidos do feed OData

Em seguida, importe os dados de pedido do feed OData de exemplo do sistema de vendas da Northwind.

1. No Editor do Power Query, selecione **Nova Fonte** e, em seguida, no menu **Mais Comum**, selecione **Feed OData**.

   ![Obter OData](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/get_odata.png)

1. Na caixa de diálogo **Feed OData**, cole a URL do feed OData da Northwind, `https://services.odata.org/V3/Northwind/Northwind.svc/`. Selecione **OK**.

   ![Caixa de diálogo do feed OData](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/get_odata2.png)

1. No **Navegador**, selecione a tabela **Orders** e, em seguida, selecione **OK** para carregar os dados no Editor do Power Query.

   ![Navegador para OData](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/analyzingsalesdata_odatafeed.png)

   >[!NOTE]
   >No **Navegador**, você pode selecionar qualquer nome de tabela sem marcar a caixa de seleção para ver uma visualização.

## <a name="expand-the-order-data"></a>Expandir os dados de pedido

Você pode usar referências de tabela para criar consultas ao se conectar a fontes de dados com várias tabelas, como bancos de dados relacionais ou o feed OData da Northwind. A tabela **Orders** contém referências a várias tabelas relacionadas. Você pode usar a operação de expansão para adicionar as colunas **ProductID**, **UnitPrice** e **Quantity** da tabela relacionada **Order_Details** à tabela (**Orders**) em questão.

1. Role para a direita na tabela **Orders** até ver a coluna **Order_Details**. Ela contém referências a outra tabela e não dados.

   ![Coluna Order_Details](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/order-details-column.png)

1. Selecione o ícone **Expandir** (![ícone Expandir](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/expand.png)) no cabeçalho da coluna **Order_Details**.

1. No menu suspenso:

   1. Selecione **(Selecionar Todas as Colunas)** para limpar todas as colunas.

   1. Selecione **ProductID**, **UnitPrice** e **Quantity** e, então, selecione **OK**.

      ![Expandir o menu suspenso](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/expand-drop-down-menu.png)

Depois de expandir a tabela **Order_Details**, três novas colunas de tabela aninhada substituirão a coluna **Order_Details**. Há novas linhas na tabela de dados para cada dado de pedido adicionado.

![Colunas expandidas](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/expanded-columns.png)

## <a name="create-a-custom-calculated-column"></a>Criar uma coluna calculada personalizada

O Power Query Editor permite criar cálculos e campos personalizados para enriquecer seus dados. Você criará uma coluna personalizada que multiplicará o preço unitário pela quantidade de itens a fim de calcular o preço total de cada item de linha do pedido.

1. Na guia de faixa de opções **Adicionar Coluna** do Power Query Editor, selecione **Coluna Personalizada**.

   ![Como adicionar uma coluna personalizada](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/adding-a-custom-column.png)

1. Na caixa de diálogo **Coluna Personalizada**, digite **LineTotal** no campo **Nome da nova coluna**.

1. No campo **Fórmula de coluna personalizada** após o **=** , insira **[Order_Details.UnitPrice]** \* **[Order_Details.Quantity]** . Você também pode selecionar os nomes dos campos na caixa de rolagem **Colunas disponíveis** e selecionar **<< Inserir** em vez de digitá-los.

1. Selecione **OK**.

   ![Caixa de diálogo Coluna Personalizada](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/custom-column-dialog-box.png)

   O novo campo **LineTotal** aparece como a última coluna na tabela **Orders**.

## <a name="set-the-new-fields-data-type"></a>Definir o tipo de dados do novo campo

Quando o Power Query Editor se conecta a dados, ele faz uma suposição sobre o tipo de dados de cada campo para fins de exibição. Um ícone de cabeçalho indica o tipo de dados atribuído a cada campo. Você também pode verificar em **Tipo de Dados** no grupo **Transformar** da guia de faixa de opções **Página Inicial**.

Sua nova coluna **LineTotal** tem o tipo de dados **Qualquer**, mas tem valores de moeda. Para atribuir um tipo de dados, clique com o botão direito do mouse no cabeçalho da coluna **LineTotal**, selecione **Alterar Tipo** no menu suspenso e, em seguida, selecione **Número decimal fixo**.

![Alterar tipo de dados para decimal fixo](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/change-data-type-to-fixed-decimal.png)

>[!NOTE]
>Também é possível selecionar a coluna **LineTotal** e, em seguida, selecionar a seta ao lado de **Tipo de Dados** na área **Transformar** da guia de faixa de opções da **Página Inicial** e, por fim, selecionar **Número decimal fixo**.

## <a name="clean-up-the-orders-columns"></a>Limpar as colunas de pedidos

Para facilitar o trabalho com seu modelo nos relatórios, você pode excluir, renomear e reordenar algumas colunas.

O relatório usará as seguintes colunas:

* **OrderDate**
* **ShipCity**
* **ShipCountry**
* **Order_Details.ProductID**
* **Order_Details.UnitPrice**
* **Order_Details.Quantity**
* **LineTotal**

Selecione essas colunas e use **Remover Outras Colunas**, como você fez com os dados do Excel. Ou, selecione as colunas não listadas, clique com o botão direito do mouse em uma delas e selecione **Remover Colunas**.

Você pode renomear as colunas prefixadas com "**Order_Details.** " para torná-las mais fáceis de ler:

1. Clique duas vezes ou toque e segure o cabeçalho de cada coluna ou, ainda, clique com o botão direito do mouse no cabeçalho da coluna e selecione **Renomear** no menu suspenso.

1. Exclua o prefixo **Order_Details.** prefixo de cada nome.

Por fim, para tornar a coluna **LineTotal** mais fácil de acessar, arraste e solte-a à esquerda, logo à direita da coluna **ShipCountry**.

![Tabela limpa](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/cleaned-up-table.png)

## <a name="review-the-query-steps"></a>Examinar as etapas de consulta

Suas ações no Power Query Editor para formatar e transformar dados serão registradas. Cada ação é exibida à direita no painel **Configurações de Consulta** em **Etapas Aplicadas**. Você pode retornar em **Etapas Aplicadas** para examinar as etapas e editar, excluir ou reorganizá-las se necessário. No entanto, alterar as etapas anteriores é arriscado, pois poderá prejudicar as etapas posteriores.

Selecione cada uma de suas consultas na lista **Consultas** no lado esquerdo do Power Query Editor e examine as **Etapas Aplicadas** em **Config. Consulta**. Após a aplicação das transformações de dados anteriores, as **Etapas Aplicadas** de suas duas consultas deverão ser semelhantes a isso:

![Etapas Aplicadas de consulta de produtos](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/products-query-applied-steps.png) &nbsp;&nbsp; ![Etapas Aplicadas de consulta de pedidos](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/orders-query-applied-steps.png)

>[!TIP]
>As Etapas Aplicadas são formadas por fórmulas escritas na *Linguagem do Power Query*, também conhecida como [linguagem M](https://docs.microsoft.com/powerquery-m/power-query-m-reference). Para ver e editar as fórmulas, selecione **Editor Avançado** no grupo **Consulta** da guia **Página Inicial** da faixa de opções.

## <a name="import-the-transformed-queries"></a>Importar as consultas transformadas

Quando estiver satisfeito com os dados transformados e pronto para importá-los para a Exibição de **Relatório** do Power BI Desktop, selecione **Fechar e Aplicar** > **Fechar e Aplicar** no grupo **Fechar** da guia de faixa de opções **Página Inicial**.

![Fechar e Aplicar](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_4.png)

Após os dados serem carregados, as consultas aparecerão na lista **Campos** na exibição de **Relatório** do Power BI Desktop.

![Consultas na lista Campos](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/queries-in-fields-list.png)

## <a name="manage-the-relationship-between-the-datasets"></a>Gerenciar a relação entre conjuntos de dados

O Power BI Desktop não requer que você combine consultas para relatar informações sobre elas. No entanto, você pode usar as relações entre conjuntos de dados, com base em campos comuns, para estender e enriquecer seus relatórios. O Power BI Desktop pode detectar relações automaticamente ou você pode criá-las na caixa de diálogo **Gerenciar Relações** do Power BI Desktop. Para obter mais informações, veja [Criar e gerenciar relações no Power BI Desktop](desktop-create-and-manage-relationships.md).

O campo `ProductID` compartilhado cria uma relação entre os `Orders` deste tutorial e os conjuntos de dados `Products`.

1. Na exibição de **Relatório** do Power BI Desktop, selecione **Gerenciar Relações** na área **Relações** da guia de faixa de opções **Página Inicial**.

   ![Faixa de opções Gerenciar Relações](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_5.png)

1. Na caixa de diálogo **Gerenciar relações**, veja que o Power BI Desktop já detectou e listou uma relação ativa entre as tabelas **Products** e **Orders**. Para exibir a relação, selecione **Editar**.

   ![Caixa de diálogo Gerenciar Relações](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_6.png)

   A caixa de diálogo **Editar Relação** é aberta, mostrando detalhes da relação.  

   ![Caixa de diálogo Editar Relação](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_7.png)

1. O Power BI Desktop detectou automaticamente a relação corretamente, de modo que você pode selecionar **Cancelar** e **Fechar**.

No Power BI Desktop, no lado esquerdo, selecione **Modelo** para exibir e gerenciar relações de consulta. Clique duas vezes na seta na linha que conecta as duas consultas para abrir a caixa de diálogo **Editar Relação** e exibir ou alterar a relação.

![Exibição de Relação](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_8.png)

Para voltar à exibição de **Relatório** da exibição de **Modelo**, selecione o ícone **Relatório**.

![Ícone de Exibição de Relatório](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_9.png)

## <a name="create-visualizations-using-your-data"></a>Criar visualizações usando seus dados

Você pode criar diferentes visualizações na Exibição de Revisão do Power BI Desktop para obter insights sobre os dados. Os relatórios podem ter várias páginas e cada página pode ter vários visuais. Você e outras pessoas podem interagir com suas visualizações para ajudar a analisar e compreender os dados. Para obter mais informações, confira [Interagir com um relatório no modo de exibição de Edição no serviço do Power BI](service-interact-with-a-report-in-editing-view.md).

Você pode usar seus dois conjuntos de dados, bem como a relação entre eles, para ajudar a visualizar e analisar seus dados de vendas.

Primeiro, crie um gráfico de colunas empilhadas que usa campos das duas consultas para mostrar a quantidade de cada produto pedido.

1. Selecione o campo **Quantity** de **Orders** no painel **Campos** painel à direita ou arraste-o para um espaço em branco na tela. Um gráfico de colunas empilhadas é criado, mostrando a quantidade total de todos os produtos pedidos.

1. Para mostrar a quantidade de cada produto pedido, selecione **ProductName** de **Produtos** no painel **Campos** ou arraste-o para o gráfico.

1. Para classificar os produtos dos mais para os menos pedidos, selecione as reticências ( **...** ) em **Mais opções** no canto superior direito da visualização e, em seguida, selecione **Classificar por Quantidade**.

1. Use as alças nos cantos do gráfico para aumentá-lo para que mais nomes de produtos fiquem visíveis.

   ![Gráfico de barras Quantity por ProductName](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/quantity-by-productname-bar-chart.png)

Em seguida, crie um gráfico mostrando os valores em dinheiro dos pedidos (**LineTotal**) ao longo do tempo (**OrderDate**).

1. Sem nada selecionado na tela, selecione **LineTotal** de **Orders** no painel **Campos** ou arraste-o para um espaço em branco na tela. O gráfico de colunas empilhadas mostra o valor em dinheiro total de todos os pedidos.

1. Selecione o gráfico empilhado, depois selecione **OrderDate** em **Orders** ou arraste-o para o gráfico. Agora, o gráfico mostra os totais de linha para cada data de pedido.

1. Arraste os cantos para redimensionar a visualização e ver mais dados.

   ![Gráfico de linhas LineTotals por OrderDate](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/linetotals-by-orderdate-line-chart.png)

   >[!TIP]
   >Se você vir apenas **Anos** no gráfico e apenas três pontos de dados, selecione a seta ao lado de **OrderDate** no campo **Eixo** do painel **Visualizações** e selecione **OrderDate**, em vez de **Hierarquia de Datas**.

Por fim, crie uma visualização de mapa mostrando as quantidades de pedidos de cada país.

1. Sem nada selecionado na tela, selecione **ShipCountry** de **Orders** no painel **Campos** ou arraste-o para um espaço em branco na tela. O Power BI Desktop detecta que os dados são nomes de países. Em seguida, ele cria automaticamente uma visualização de mapa, com um ponto de dados para cada país com pedidos.

1. Para fazer com que os tamanhos dos pontos de dados correspondam às quantidades de pedidos de cada país, arraste o campo **LineTotal** para o mapa. Você também pode arrastá-lo para **Arrastar os campos de dados aqui** em **Tamanho**, no painel **Visualizações**. Agora, os tamanhos dos círculos no mapa refletem os valores em dinheiro dos pedidos de cada país.

   ![Visualização de mapa LineTotals por ShipCountry](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/linetotals-by-shipcountry-map-visualization.png)

## <a name="interact-with-your-report-visuals-to-analyze-further"></a>Interagir com os elementos visuais de seu relatório para analisar com mais profundidade

No Power BI Desktop você pode interagir com elementos visuais que realizam ações cruzadas de realce e filtragem entre si para revelar outras tendências. Para obter mais detalhes, confira [Filtros e realce em relatórios do Power BI](power-bi-reports-filters-and-highlighting.md).

Devido à relação entre as consultas, as interações com uma visualização afetam todas as outras visualizações na página.

Na visualização de mapa, selecione o círculo centralizado no **Canadá**. As outras duas visualizações são filtradas de forma a realçar os totais de linha e as quantidades de pedidos canadenses.

![Dados de vendas filtrados para o Canadá](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/sales-data-filtered-for-canada.png)

Selecione um produto do gráfico **Quantidade por ProductName** para ver o mapa e o filtro de gráfico de data para exibir os dados desse produto. Selecione uma data do gráfico **LineTotal por OrderDate** para ver o mapa e o filtro do gráfico de produto para mostrar os dados dessa data.

>[!TIP]
>Para cancelar uma seleção, selecione-a novamente ou selecione uma das outras visualizações.

## <a name="complete-the-sales-analysis-report"></a>Concluir o relatório de análise de vendas

Seu relatório concluído combina dados do arquivo do Excel *Products.xlsx* e do feed OData da Northwind em elementos visuais que ajudam a analisar informações de pedidos, períodos e produtos de diferentes países. Quando seu relatório estiver pronto, você poderá [fazer upload dele no serviço do Power BI](desktop-upload-desktop-files.md) ou compartilhá-lo com outros usuários do Power BI.

## <a name="next-steps"></a>Próximas etapas

* [Leia outros tutoriais do Power BI Desktop](/power-bi/guided-learning/)
* [Assista a vídeos do Power BI Desktop](/power-bi/desktop-videos)
* [Visite o Fórum do Power BI](https://go.microsoft.com/fwlink/?LinkID=519326)
* [Leia o Blog do Power BI](https://go.microsoft.com/fwlink/?LinkID=519327)
