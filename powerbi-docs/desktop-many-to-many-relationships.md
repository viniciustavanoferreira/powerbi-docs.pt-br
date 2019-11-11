---
title: Relações muitos para muitos no Power BI Desktop
description: Usar relações com uma cardinalidade muitos para muitos no Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 02/13/2019
ms.author: davidi
LocalizationGroup: Transform and shape data
ms.openlocfilehash: 578d5f77753884575111b3247f5aa4d3ae79e179
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/09/2019
ms.locfileid: "73866812"
---
# <a name="relationships-with-a-many-many-cardinality-in-power-bi-desktop"></a>Relações com uma cardinalidade muitos para muitos no Power BI Desktop

Com o recurso *relações com uma cardinalidade muitos para muitos* no Power BI Desktop, você pode unir tabelas que usam uma cardinalidade igual a *muitos para muitos*. Você pode criar modelos de dados mais fáceis e intuitivos que contêm duas ou mais fontes de dados. O recurso *relações com uma cardinalidade muitos para muitos* faz parte das funcionalidades mais amplas de *modelos compostos* do Power BI Desktop.

![Uma relação muitos para muitos no painel “Editar relação”](media/desktop-many-to-many-relationships/many-to-many-relationships_01.png)

A funcionalidade *relações com uma cardinalidade muitos para muitos* do Power BI Desktop é um de três recursos relacionados:

* **Modelos compostos**: permite que um relatório tenha duas ou mais conexões de dados, incluindo conexões DirectQuery ou Importação, em qualquer combinação. Para ver mais informações, confira [Modelos compostos no Power BI Desktop](desktop-composite-models.md).

* **Relações com uma cardinalidade muitos para muitos**: Com os *modelos compostos*, você pode estabelecer *relações com uma cardinalidade muitos para muitos* entre tabelas. Esta abordagem remove os requisitos de valores exclusivos nas tabelas. Ela também remove as soluções alternativas anteriores, como introduzir novas tabelas somente para estabelecer relações. O recurso é descrito em detalhes neste artigo.

* **Modo de armazenamento**: agora você pode especificar quais visuais exigem uma consulta para fontes de dados de back-end. Visuais que não exigem uma consulta serão importados, mesmo se forem baseados no DirectQuery. Esse recurso ajuda a melhorar o desempenho e reduzir a carga de back-end. Antes, mesmo visuais simples como as segmentações iniciavam consultas enviadas para fontes de back-end. Para mais informações, confira [Modo de armazenamento no Power BI Desktop (versão prévia)](desktop-storage-mode.md).

## <a name="what-relationships-with-a-many-many-cardinality-solves"></a>O que as *relações com uma cardinalidade muitos para muitos* resolvem

Antes de o recurso *relações com uma cardinalidade muitos para muitos* ficar disponível, a relação entre duas tabelas era definida no Power BI. Pelo menos uma das colunas da tabela envolvidas na relação precisava conter valores exclusivos. Muitas vezes, no entanto, não há colunas contendo valores exclusivos. 

Por exemplo, duas tabelas podem ter uma coluna com o rótulo *País*, mas os valores de *País* não eram exclusivos em nenhuma das tabelas. Para unir essas tabelas, era necessário criar uma solução alternativa. Essa solução poderia ser introduzir tabelas adicional no modelo com os valores exclusivos necessários. Com o recurso *relações com uma cardinalidade muitos para muitos*, você pode unir essas tabelas diretamente usando uma relação com uma cardinalidade igual a **muitos para muitos**.  

## <a name="use-relationships-with-a-many-many-cardinality"></a>Usar *relações com uma cardinalidade muitos para muitos*

Ao definir uma relação entre duas tabelas no Power BI, é preciso definir a cardinalidade da relação. Por exemplo, a relação entre *ProductSales* e *Produto*&mdash;usando as colunas *ProductSales[ProductCode]* e *Product[ProductCode]* &mdash;seria definida como *Muitos para um*. Definimos a relação dessa forma porque há muitas vendas para cada produto e a coluna na tabela *Produto* *(ProductCode)* é exclusiva. Ao definir uma cardinalidade da relação como *Muitos para um*, *Um para muitos* ou *Um para um*, o Power BI a valida para ajudar a garantir que a cardinalidade selecionada corresponda aos dados reais.

Por exemplo, confira o modelo simples na imagem a seguir:

![Modo de Exibição de Relação](media/desktop-many-to-many-relationships/many-to-many-relationships_02.png)

Agora, imagine que a tabela *Produto* exibe apenas duas linhas, conforme mostrado:

![Visual da tabela de Produto visual com duas linhas](media/desktop-many-to-many-relationships/many-to-many-relationships_03.png)

Imagine também que a tabela *Vendas* tem apenas quatro linhas, incluindo a linha para um produto C. Devido a um erro de integridade referencial, a linha de produto C não existe na tabela *Produto*.

![Visual da tabela Vendas com quatro linhas](media/desktop-many-to-many-relationships/many-to-many-relationships_04.png)

O *ProductName* e o *Preço* (da tabela *Produto*), juntamente com a *Qtd* total para cada produto (da tabela *ProductSales*) seria exibido como mostrado a seguir: 

![Visual exibindo o nome, preço e quantidade do produto](media/desktop-many-to-many-relationships/many-to-many-relationships_05.png)

Como podemos ver na imagem anterior, há uma linha *ProductName* em branco que está associada às vendas do produto C. Essa linha em branco é contabilizada da seguinte forma:

* Qualquer linha na tabela *ProductSales* sem nenhuma linha correspondente na tabela *Produto*. Há um problema de integridade referencial, como visto para o produto *C* neste exemplo.

* Qualquer linha na tabela *ProductSales* para a qual a coluna de chave estrangeira é nula. 

Por esses motivos, em ambos os casos, a linha em branco refere-se a vendas em que *ProductName* e *Price* são desconhecidos.

No entanto, pode ocorrer que as tabelas sejam unidas por duas colunas, mas nenhuma coluna seja exclusiva. Por exemplo, considere as duas seguintes tabelas:

* A tabela *Vendas* exibe dados de vendas por *Estado*, com cada linha contendo o valor das vendas para o tipo de venda nesse estado. Os estados são CA, WA e TX. 

    ![Tabela de vendas exibindo as vendas por estado](media/desktop-many-to-many-relationships/many-to-many-relationships_06.png)

* A tabela *CityData* exibe dados nas cidades, incluindo a população e o estado (incluindo CA, WA e Nova York).

    ![Tabela de vendas exibindo a cidade, estado e população](media/desktop-many-to-many-relationships/many-to-many-relationships_07.png)

Embora não haja uma coluna para *Estado* em ambas as tabelas e seja razoável querer relatar o total de vendas por estado e a população total de cada estado, há um problema: a coluna *Estado* não é exclusiva em nenhuma das tabelas. 

## <a name="the-previous-workaround"></a>A solução alternativa anterior

Em versões do Power BI Desktop anteriores à versão de julho de 2018, não era possível para os usuários criar uma relação direta entre essas tabelas. Uma solução alternativa comum para esse problema era fazer o seguinte:

* Crie uma terceira tabela que continha apenas as IDs de *Estado* exclusivas. A tabela poderia ser qualquer uma ou todas das seguintes:
  * Uma tabela calculada (definida usando o [DAX] Data Analysis Expressions).
  * Uma tabela baseada em uma consulta que é definida no Editor de Consultas, que pode exibir as IDs exclusivas extraídas de uma das tabelas.
  * O conjunto completo combinado.

* Relacione as duas tabelas originais à nova tabela, usando relações *Muitos para um* comuns.

Você pode deixar a tabela da solução alternativa visível ou ocultá-la para que ela não apareça na lista **Campos**. Se você omitir a tabela, as relações *Muitos para 1* normalmente serão definidas para filtrar em ambos os sentidos e você poderá usar o campo *Estado* de qualquer uma das tabelas. As filtragens cruzadas subsequentes seriam propagadas para a outra tabela. Essa abordagem é mostrada na imagem a seguir:

![Modo de Exibição de Relação](media/desktop-many-to-many-relationships/many-to-many-relationships_08.png)

Um visual que exibe o *Estado* (da tabela *CityData*), juntamente com a *População* total e o total de *Vendas* apareceria desta forma:

![Visual da tabela](media/desktop-many-to-many-relationships/many-to-many-relationships_09.png)

> [!NOTE]
> Como o estado da tabela *CityData* é usado nesta solução alternativa, somente os estados nessa tabela são listados e, portanto, TX é excluído. Além disso, diferentemente de relações *muitos para um*, embora a linha do total inclua todas as *Vendas* (incluindo as de TX), os detalhes não incluem uma linha em branco que abrange essas linhas não correspondentes. Da mesma forma, não haveria linhas em branco abrangendo *Vendas* para as quais houvesse um valor nulo para o *Estado*.

Se você também adicionar *Cidade* ao visual, embora a população por *Cidade* seja conhecida, as *Vendas* mostradas para a *Cidade* simplesmente repetirão as *Vendas* para o *Estado* correspondente. Esse é normalmente o caso quando o agrupamento em uma coluna não está relacionado a nenhuma medida de agregação, conforme mostrado na imagem a seguir:

![Visual da tabela](media/desktop-many-to-many-relationships/many-to-many-relationships_10.png)

Se definirmos a nova tabela *Vendas* como a combinação de todos os *Estados* nesta solução alternativa e torná-la visível na lista **Campos**, o mesmo visual exibirá tanto o *Estado* (na nova tabela) quanto a *População* total e o total *Vendas*, conforme mostrado na imagem a seguir:

![Visual da tabela](media/desktop-many-to-many-relationships/many-to-many-relationships_11.png)

Como podemos ver, os dados de *TX*&mdash;com *Vendas*, mas com os dados de *População* desconhecidos &mdash;e *Nova York*&mdash;com os dados de *População* conhecidos, mas não dados *Vendas*&mdash;seriam incluídos. Essa solução alternativa não é ideal, e tem vários problemas. Com a criação das relações com uma cardinalidade muitos para muitos, os problemas resultantes são resolvidos conforme descrito na próxima seção.

## <a name="use-relationships-with-a-many-many-cardinality-instead-of-the-workaround"></a>Usar *relações com uma cardinalidade muitos para muitos* em vez da solução alternativa

A partir da versão de julho de 2018 do Power BI Desktop, é possível relacionar tabelas diretamente, como aquelas que descrevemos anteriormente, sem precisar recorrer a soluções alternativas semelhantes. Agora é possível definir a cardinalidade da relação para *Muitos para muitos*. Essa configuração indica que nenhuma tabela contém valores exclusivos. Para essas relações, você ainda pode controlar qual tabela filtra a outra tabela, ou aplicar filtragem bidirecional, em que ambas as tabelas se filtram entre si.  

No Power BI Desktop, a cardinalidade usa como padrão *Muitos para muitos* quando é determinado que nenhuma destas tabelas contém valores exclusivos para as colunas na relação. Nesses casos, um aviso é exibido, para confirmar se essa configuração de relação é o comportamento desejado, e não um efeito não intencional de um problema de dados. 

Por exemplo, ao criar uma relação diretamente entre *CityData* e *Vendas*&mdash;, em que os filtros fluem de *CityData* para *Vendas*&mdash;, o Power BI Desktop exibe a janela **Editar relação** como mostrado na imagem a seguir:

![A janela “Editar relação”](media/desktop-many-to-many-relationships/many-to-many-relationships_01.png)

O modo de exibição **Relação** resultante conteria a relação direta, muitos para muitos, entre as duas tabelas. A aparência das tabelas na lista **Campos**, e seu comportamento subsequente quando os visuais são criados, é semelhante a quando aplicamos a solução alternativa. Na solução alternativa, a tabela extra que exibe os dados de *Estado* distintos não estão visível. Por exemplo, conforme descrito na seção anterior, um visual mostrando os dados de *Estado*, *População* e *Vendas* seriam exibidos da seguinte maneira:

![Visual da tabela](media/desktop-many-to-many-relationships/many-to-many-relationships_12.png)

As principais diferenças entre as *relações com uma cardinalidade muitos para muitos* e as relações *muitos para um* mais comuns são as seguintes:

* Os valores mostrados não incluem uma linha em branco que conta para as linhas incompatíveis na outra tabela. Nem esses valores consideram as linhas em que a coluna usada na relação na outra tabela é nula.
* Não é possível usar a função `RELATED()`, pois mais de uma linha pode estar relacionada.
* Usar a função `ALL()` em uma tabela não removerá os filtros aplicados a outras tabelas relacionadas a ela por uma relação muitos para muitos. No exemplo anterior, uma medida definida conforme mostrado no script a seguir não removeria os filtros nas colunas na tabela *CityData* relacionada:

    ![Exemplo de script](media/desktop-many-to-many-relationships/many-to-many-relationships_13.png)

    Um visual que mostra os dados de *Estado*, *Vendas* e *Total de vendas* resultaria no seguinte:

    ![Visual da tabela](media/desktop-many-to-many-relationships/many-to-many-relationships_14.png)

Com as diferenças anteriores em mente, verifique se os cálculos que usam `ALL(\<Table>)`, como *% do total geral*, estão retornando os resultados pretendidos. 


## <a name="limitations-and-considerations"></a>Limitações e considerações

Há algumas limitações nesta versão das *relações com uma cardinalidade muitos para muitos* e dos modelos compostos.

As seguintes fontes (multidimensionais) do Live Connect não podem ser usadas com os modelos compostos:

* SAP HANA
* SAP Business Warehouse
* SQL Server Analysis Services
* Conjuntos de dados do Power BI
* Azure Analysis Services

Ao se conectar a essas fontes multidimensionais usando o DirectQuery, não é possível se conectar também à outra fonte do DirectQuery, nem combiná-la com os dados importados.

As limitações existentes do uso do DirectQuery ainda se aplicam quando você usa *relações com uma cardinalidade muitos para muitos*. Muitas dessas limitações agora são por tabela, dependendo do modo de armazenamento dela. Por exemplo, uma coluna calculada em uma tabela importada pode se referir a outras tabelas, mas uma coluna calculada em uma tabela do DirectQuery ainda se refere apenas às colunas na mesma tabela. Outras limitações serão aplicáveis ao modelo como um todo se quaisquer das tabelas no modelo forem DirectQuery. Por exemplo, os recursos QuickInsights e P e R não estarão disponíveis em um modelo se qualquer uma das tabelas nele tiver um modo de armazenamento do DirectQuery. 

## <a name="next-steps"></a>Próximas etapas

Para obter mais informações sobre modelos compostos e DirectQuery, confira os seguintes artigos:
* [Modelos compostos no Power BI Desktop](desktop-composite-models.md)
* [Modo de armazenamento no Power BI Desktop (versão prévia)](desktop-storage-mode.md)
* [Usar o DirectQuery no Power BI Desktop](desktop-directquery-about.md)
* [Fontes de dados compatíveis com o DirectQuery no Power BI Desktop](desktop-directquery-data-sources.md)
