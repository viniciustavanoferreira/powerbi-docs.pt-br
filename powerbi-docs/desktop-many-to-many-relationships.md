---
title: Relações muitos para muitos no Power BI Desktop
description: Usar relações com uma cardinalidade muitos para muitos no Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 12/19/2019
ms.author: davidi
LocalizationGroup: Transform and shape data
ms.openlocfilehash: 7452879e47cd4b058fcdb3e08f0ded35a85da1aa
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/05/2020
ms.locfileid: "75761055"
---
# <a name="apply-many-many-relationships-in-power-bi-desktop"></a>Aplicar relações muitos para muitos no Power BI Desktop

Com as *relações com uma cardinalidade muitos para muitos* no Power BI Desktop, você pode unir tabelas que usam uma cardinalidade igual a *muitos para muitos*. Você pode criar modelos de dados mais fáceis e intuitivos que contêm duas ou mais fontes de dados. As *relações com uma cardinalidade muitos para muitos* faz parte das funcionalidades mais amplas de *modelos compostos* do Power BI Desktop.

![Uma relação muitos para muitos no painel "Editar relação", Power BI Desktop](media/desktop-many-to-many-relationships/many-to-many-relationships_01.png)

Uma *relação com uma cardinalidade muitos para muitos* no Power BI Desktop é composta por um de três recursos relacionados:

* **Modelos compostos**: Um *modelo composto* permite que um relatório tenha duas ou mais conexões de dados, incluindo conexões do DirectQuery ou importação, em qualquer combinação. Para obter mais informações, confira [Usar modelos compostos no Power BI Desktop](desktop-composite-models.md).

* **Relações com uma cardinalidade muitos para muitos**: Com os modelos compostos, você pode estabelecer *relações com uma cardinalidade muitos para muitos* entre tabelas. Esta abordagem remove os requisitos de valores exclusivos nas tabelas. Ela também remove as soluções alternativas anteriores, como introduzir novas tabelas somente para estabelecer relações. O recurso é descrito em detalhes neste artigo.

* **Modo de armazenamento**: agora você pode especificar quais visuais exigem uma consulta para fontes de dados de back-end. Visuais que não exigem uma consulta serão importados, mesmo se forem baseados no DirectQuery. Esse recurso ajuda a melhorar o desempenho e reduzir a carga de back-end. Anteriormente, mesmo visuais simples, como segmentações, iniciavam consultas que eram enviadas para as fontes de back-end. Para mais informações, veja o [modo de Armazenamento no Power BI Desktop](desktop-storage-mode.md).

## <a name="what-a-relationship-with-a-many-many-cardinality-solves"></a>Problemas resolvidos por uma relação com uma cardinalidade muitos para muitos

Antes de as *relações com uma cardinalidade muitos para muitos* serem disponibilizadas, a relação entre duas tabelas era definida no Power BI. Pelo menos uma das colunas da tabela envolvidas na relação precisava conter valores exclusivos. Muitas vezes, no entanto, não há colunas contendo valores exclusivos.

Por exemplo, duas tabelas podem ter uma coluna rotulada Country. No entanto, os valores de Country não eram exclusivos em nenhuma das tabelas. Para unir essas tabelas, você precisava criar uma solução alternativa. Uma solução alternativa pode ser introduzir tabelas extras com os valores exclusivos necessários. Com as *relações com uma cardinalidade muitos para muitos*, você poderá unir essas tabelas diretamente se usar uma relação com uma cardinalidade igual a *muitos para muitos*.

## <a name="use-relationships-with-a-many-many-cardinality"></a>Usar relações com uma cardinalidade muitos para muitos

Ao definir uma relação entre duas tabelas no Power BI, é preciso definir a cardinalidade da relação. Por exemplo, a relação entre ProductSales e Product,&mdash;usando as colunas ProductSales[ProductCode] e Product[ProductCode],&mdash;será definida como *Muitos para um*. Definimos a relação dessa forma, porque cada produto tem muitas vendas e a coluna na tabela Product (ProductCode) é exclusiva. Ao definir uma cardinalidade da relação como *Muitos para um*, *Um para muitos* ou *Um para um*, o Power BI a valida, de modo que a cardinalidade selecionada corresponda aos dados reais.

Por exemplo, confira o modelo simples nesta imagem:

![Tabelas ProductSales e Product, exibição de Relação, Power BI Desktop](media/desktop-many-to-many-relationships/many-to-many-relationships_02.png)

Agora, imagine que a tabela **Produto** exibe apenas duas linhas, conforme mostrado:

![Visual da tabela Produto com duas linhas, Power BI Desktop](media/desktop-many-to-many-relationships/many-to-many-relationships_03.png)

Imagine também que a tabela Sales só tem quatro linhas, incluindo a linha para um produto C. Devido a um erro de integridade referencial, a linha do produto C não existe na tabela **Product**.

![Visual de tabela Sales com quatro linhas, Power BI Desktop](media/desktop-many-to-many-relationships/many-to-many-relationships_04.png)

O **ProductName** e o **Price** (da tabela **Product**), juntamente com a **Qtd** total de cada produto (da tabela ProductSales), serão exibidos conforme mostrado:

![Visual exibindo o nome, o preço e a quantidade do produto, Power BI Desktop](media/desktop-many-to-many-relationships/many-to-many-relationships_05.png)

Como você pode ver na imagem anterior, há uma linha **ProductName** em branco que está associada às vendas do produto C. Essa linha em branco indica o seguinte:

* Qualquer linha na tabela **ProductSales** sem nenhuma linha correspondente na tabela **Produto**. Há um problema de integridade referencial, como vemos no produto C deste exemplo.

* Qualquer linha na tabela **ProductSales** para a qual a coluna de chave estrangeira é nula.

Por esses motivos, em ambos os casos, a linha em branco refere-se a vendas em que **ProductName** e **Price** são desconhecidos.

Às vezes, as tabelas são unidas por duas colunas, mas nenhuma delas é exclusiva. Por exemplo, considere estas duas tabelas:

* A tabela **Vendas** exibe dados de vendas por **Estado**, com cada linha contendo o valor das vendas para o tipo de venda nesse estado. Os estados são CA, WA e TX.

    ![Tabela Sales exibindo as vendas por estado, Power BI Desktop](media/desktop-many-to-many-relationships/many-to-many-relationships_06.png)

* A tabela **CityData** exibe os dados nas cidades, incluindo a população e o estado (como CA, WA e Nova York).

    ![Tabela Sales exibindo a cidade, o estado e a população, Power BI Desktop](media/desktop-many-to-many-relationships/many-to-many-relationships_07.png)

Agora, há uma coluna para **Estado** em ambas as tabelas. É razoável querer relatar o total de vendas por estado e a população total de cada estado. No entanto, há um problema: a coluna **State** não é exclusiva em nenhuma das tabelas.

## <a name="the-previous-workaround"></a>A solução alternativa anterior

Antes da versão de julho de 2018 do Power BI Desktop, não era possível criar uma relação direta entre essas tabelas. Uma solução alternativa comum era:

* Criar uma terceira tabela que continha apenas as IDs de State exclusivas. A tabela pode ser qualquer uma destas ou todas estas:
  * Uma tabela calculada (definida usando o [DAX] Data Analysis Expressions).
  * Uma tabela baseada em uma consulta que é definida no Editor de Consultas, que pode exibir as IDs exclusivas extraídas de uma das tabelas.
  * O conjunto completo combinado.

* Em seguida, relacione as duas tabelas originais à nova tabela usando relações comuns *Muitos para um*.

Você pode deixar a tabela de solução alternativa visível. Ou pode ocultar a tabela de solução alternativa, de modo que ela não seja exibida na lista **Campos**. Se você ocultar a tabela, as relações *Muitos para um* normalmente serão definidas para filtro em ambas as direções e você poderá usar o campo Estado de uma das tabelas. A filtragem cruzada posterior será propagada para a outra tabela. Essa abordagem é mostrada na imagem a seguir:

![Tabela Estado oculta, exibição de Relação, Power BI Desktop](media/desktop-many-to-many-relationships/many-to-many-relationships_08.png)

Um visual que exibe o **Estado** (da tabela **CityData**), juntamente com a **População** total e o total de **Vendas** apareceria desta forma:

![Tabelas State, Population e Sales, Power BI Desktop](media/desktop-many-to-many-relationships/many-to-many-relationships_09.png)

> [!NOTE]
> Como o estado da tabela **CityData** é usado nesta solução alternativa, somente os estados dessa tabela são listados e, portanto, o TX é excluído. Além disso, ao contrário das relações *Muitos para um*, embora a linha do total inclua todas as **Vendas** (incluindo as do TX), os detalhes não incluem uma linha em branco que abrange essas linhas não correspondentes. Da mesma forma, nenhuma linha em branco abrange **Sales**, para a qual há um valor nulo em **State**.

Suponha que você também adicione City a esse visual. Embora a população por City seja conhecida, as **Sales** mostradas para a City simplesmente repetirão as **Sales** do **State** correspondente. Esse cenário normalmente ocorre quando o agrupamento de colunas não está relacionado a uma medida agregada, conforme mostrado aqui:

![População de estado e cidade e vendas, Power BI Desktop](media/desktop-many-to-many-relationships/many-to-many-relationships_10.png)

Digamos que você defina a nova tabela Sales como a combinação de todos os States aqui e a tornemos visível na lista **Fields**. O mesmo visual exibirá **State** (na nova tabela), a **Population** total e o total de **Sales**:

![Visual de estado, população e vendas, Power BI Desktop](media/desktop-many-to-many-relationships/many-to-many-relationships_11.png)

Como você pode ver, o TX,&mdash;com os dados de **Sales**, mas com os dados de *Population* desconhecidos,&mdash;e Nova York,&mdash;com os dados de **Population** conhecidos, mas sem dados de **Sales**,&mdash;serão incluídos. Essa solução alternativa não é ideal, e tem vários problemas. Para relações com uma cardinalidade muitos para muitos, os problemas resultantes são resolvidos conforme descrito na próxima seção.

## <a name="use-a-relationship-with-a-many-many-cardinality-instead-of-the-workaround"></a>Usar uma relação com uma cardinalidade muitos para muitos em vez da solução alternativa

Com a versão de julho de 2018 do Power BI Desktop, você pode relacionar tabelas diretamente, como aquelas que descrevemos anteriormente, sem precisar recorrer a soluções alternativas semelhantes. Agora é possível definir a cardinalidade da relação como *muitos para muitos*. Essa configuração indica que nenhuma tabela contém valores exclusivos. Para essas relações, você ainda pode controlar qual tabela filtra a outra. Ou você pode aplicar a filtragem bidirecional, em que cada tabela filtra a outra.

No Power BI Desktop, a cardinalidade usa como padrão *muitos para muitos* quando determina que nenhuma das tabelas contém valores exclusivos para as colunas da relação. Nesses casos, uma mensagem de aviso confirma se você deseja definir uma relação, e a alteração não é o efeito indesejado de um problema de dados.

Por exemplo, quando você cria uma relação diretamente entre CityData e Sales,&mdash;em que os filtros devem fluir de CityData para Sales,&mdash;o Power BI Desktop exibe a caixa de diálogo **Editar relação**:

![Caixa de diálogo Editar relação, Power BI Desktop](media/desktop-many-to-many-relationships/many-to-many-relationships_01.png)

O modo de exibição **Relação** resultante conteria a relação direta, muitos para muitos, entre as duas tabelas. A aparência das tabelas na lista **Campos** e o comportamento posterior delas quando os visuais são criados são semelhantes a quando aplicamos a solução alternativa. Na solução alternativa, a tabela extra que exibe os dados distintos de Estado não se torna visível. Conforme descrito anteriormente, um visual que mostra dados de **State**, **Population** e **Sales** será exibido:

![Tabelas State, Population e Sales, Power BI Desktop](media/desktop-many-to-many-relationships/many-to-many-relationships_12.png)

As principais diferenças entre as *relações com uma cardinalidade muitos para muitos* e as relações *muitos para um* mais comuns são as seguintes:

* Os valores mostrados não incluem uma linha em branco que conta para as linhas incompatíveis na outra tabela. Além disso, os valores não consideram as linhas em que a coluna usada na relação na outra tabela é nula.
* Não é possível usar a função `RELATED()`, pois mais de uma linha pode estar relacionada.
* Usar a função `ALL()` em uma tabela não removerá os filtros aplicados a outras tabelas relacionadas a ela por uma relação muitos para muitos. No exemplo anterior, uma medida definida, conforme mostrado aqui, não removerá os filtros nas colunas da tabela CityData relacionada:

    ![Exemplo de script](media/desktop-many-to-many-relationships/many-to-many-relationships_13.png)

    Um visual que mostra os dados de **State**, **Sales** e **Sales total** resultará neste gráfico:

    ![Visual da tabela](media/desktop-many-to-many-relationships/many-to-many-relationships_14.png)

Com as diferenças anteriores em mente, verifique se os cálculos que usam `ALL(<Table>)`, como *% do total geral*, estão retornando os resultados pretendidos.

## <a name="limitations-and-considerations"></a>Limitações e considerações

Há algumas limitações nesta versão das *relações com uma cardinalidade muitos para muitos* e dos modelos compostos.

As seguintes fontes (multidimensionais) do Live Connect não podem ser usadas com os modelos compostos:

* SAP HANA
* SAP Business Warehouse
* SQL Server Analysis Services
* Conjuntos de dados do Power BI
* Azure Analysis Services

Ao se conectar a essas fontes multidimensionais usando o DirectQuery, não é possível se conectar à outra fonte do DirectQuery nem a combinar com os dados importados.

As limitações existentes do uso do DirectQuery ainda se aplicam quando você usa *relações com uma cardinalidade muitos para muitos*. Muitas limitações agora são por tabela, dependendo do modo de armazenamento da tabela. Por exemplo, uma coluna calculada em uma tabela importada pode se referir a outras tabelas, mas uma coluna calculada em uma tabela do DirectQuery ainda se refere apenas às colunas na mesma tabela. Outras limitações serão aplicáveis ao modelo como um todo se uma das tabelas do modelo forem DirectQuery. Por exemplo, os recursos Insights Rápidos e P e R não estarão disponíveis em um modelo se uma das tabelas dele tiver um modo de armazenamento do DirectQuery.

## <a name="next-steps"></a>Próximas etapas

Para obter mais informações sobre modelos compostos e DirectQuery, confira os seguintes artigos:
* [Usar modelos compostos no Power BI Desktop](desktop-composite-models.md)
* [Modo de armazenamento no Power BI Desktop](desktop-storage-mode.md)
* [Usar DirectQuery no Power BI](desktop-directquery-about.md)
* [Fontes de dados do Power BI](power-bi-data-sources.md)
