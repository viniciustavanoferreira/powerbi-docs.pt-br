---
title: Usar parâmetros em cascata nos relatórios paginados
description: Orientações para a criação de relatórios paginados usando parâmetros em cascata.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 01/14/2020
ms.author: v-pemyer
ms.openlocfilehash: 2a8dca43077fe12e4903585e3926cc67fe864136
ms.sourcegitcommit: 3d6b27e3936e451339d8c11e9af1a72c725a5668
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2020
ms.locfileid: "76162401"
---
# <a name="use-cascading-parameters-in-paginated-reports"></a>Usar parâmetros em cascata nos relatórios paginados

Este artigo se destina aos autores de relatórios que elaboram [relatórios paginados](../paginated-reports-report-builder-power-bi.md) do Power BI. Ele apresenta cenários de criação de parâmetros em cascata. Os parâmetros em cascata são parâmetros de relatórios com dependências. Quando um usuário de relatório seleciona um valor (ou valores) de parâmetro, ele é usado para definir os valores disponíveis para outro parâmetro.

> [!NOTE]
> Este artigo não aborda uma introdução aos parâmetros em cascata nem como configurá-los. Se você não estiver totalmente familiarizado com parâmetros em cascata, recomendamos que leia primeiro [Adicionar parâmetros em cascata a um relatório (Report Builder e SSRS)](/sql/reporting-services/report-design/add-cascading-parameters-to-a-report-report-builder-and-ssrs).

## <a name="design-scenarios"></a>Cenários de criação

Existem dois cenários de criação para o uso de parâmetros em cascata. Eles podem ser usados com eficiência para:

- Filtrar _grandes conjuntos_ de itens
- Apresentar itens _relevantes_

### <a name="example-database"></a>Banco de dados de exemplo

Os exemplos apresentados neste artigo se baseiam em um Banco de Dados SQL do Azure. O banco de dados registra as operações de vendas e contém várias tabelas que armazenam revendedores, produtos e pedidos de vendas.

Uma tabela chamada **Revendedor** armazena um registro para cada revendedor e contém milhares de registros. A tabela **Revendedor** tem as seguintes colunas:

- CódigoDoRevendedor (inteiro)
- ResellerName
- País-Região
- Estado-Província
- Cidade
- PostalCode

Também há uma tabela chamada **Vendas**, que armazena registros de pedidos de vendas e tem uma relação de chave estrangeira com a tabela **Revendedor**, na coluna **ResellerCode**.

### <a name="example-requirement"></a>Requisito de exemplo

Há um requisito para desenvolver um relatório de Perfil do Revendedor. O relatório deve ser criado para exibir informações de um único revendedor. Não é indicado fazer com que o usuário do relatório insira um código de revendedor, pois ele raramente os memoriza.

## <a name="filter-large-sets-of-items"></a>Filtrar grandes conjuntos de itens

Vamos dar uma olhada em três exemplos para ajudar a limitar grandes conjuntos de itens disponíveis, como revendedores. Eles são:

- [Filtrar por colunas relacionadas](#filter-by-related-columns)
- [Filtrar por uma coluna de agrupamento](#filter-by-a-grouping-column)
- [Filtrar por padrão de pesquisa](#filter-by-search-pattern)

### <a name="filter-by-related-columns"></a>Filtrar por colunas relacionadas

Neste exemplo, o usuário do relatório interage com cinco parâmetros de relatório. Ele deve selecionar o país-região, estado-província, cidade e CEP. Um parâmetro final lista os revendedores que residem nesse local geográfico.

![A imagem mostra cinco parâmetros de relatório: País-região, Estado-província, Cidade, CEP e Revendedor. Os quatro primeiros têm valores definidos, e a lista de Revendedores está filtrada com apenas quatro itens.](media/paginated-report-cascading-parameter/filter-by-related-columns-example.png)

Veja como desenvolver os parâmetros em cascata:

1. Crie os cinco parâmetros de relatório, ordenados na sequência correta.
2. Crie o conjunto **PaísRegião**, que recupera valores distintos de país-região, usando a seguinte instrução de consulta:

    ```sql
    SELECT DISTINCT
      [Country-Region]
    FROM
      [Reseller]
    ORDER BY
      [Country-Region]
    ```

3. Crie o conjunto **EstadoProvíncia**, que recupera valores distintos de estado-província para o país-região selecionado, usando a seguinte instrução de consulta:

    ```sql
    SELECT DISTINCT
      [State-Province]
    FROM
      [Reseller]
    WHERE
      [Country-Region] = @CountryRegion
    ORDER BY
      [State-Province]
    ```

4. Crie o conjunto **Cidade**, que recupera valores distintos de cidade para o país-região e o estado-província selecionados, usando a seguinte instrução de consulta:

    ```sql
    SELECT DISTINCT
      [City]
    FROM
      [Reseller]
    WHERE
      [Country-Region] = @CountryRegion
      AND [State-Province] = @StateProvince
    ORDER BY
      [City]
    ```

5. Siga o padrão para criar o conjunto **CEP**.
6. Crie o conjunto **Revendedor** para recuperar todos os revendedores dos valores geográficos selecionados, usando a seguinte instrução de consulta:

    ```sql
    SELECT
      [ResellerCode],
      [ResellerName]
    FROM
      [Reseller]
    WHERE
      [Country-Region] = @CountryRegion
      AND [State-Province] = @StateProvince
      AND [City] = @City
      AND [PostalCode] = @PostalCode
    ORDER BY
      [ResellerName]
    ```

7. Relacione os parâmetros de consulta com os parâmetros de relatório correspondentes para todos os conjuntos de dados, exceto o primeiro.

> [!NOTE]
> Todos os parâmetros de consulta (prefixados com o símbolo @) mostrados nesses exemplos podem ser inseridos em instruções SELECT ou passados para procedimentos armazenados.
>
> Em geral, os procedimentos armazenados são uma abordagem de design melhor. Isso se deve ao fato de seus planos de consulta serem armazenados em cache para uma execução mais rápida e permitirem o desenvolvimento de uma lógica mais sofisticada, quando necessário. No entanto, no momento eles não têm suporte para fontes de dados relacionais de gateway, ou seja, SQL Server, Oracle e Teradata.
>
> Por fim, você deve sempre garantir que existam índices adequados para dar suporte à recuperação de dados eficientes. Caso contrário, os parâmetros do relatório podem ter um preenchimento lento, e o banco de dados pode ficar sobrecarregado. Confira mais informações sobre a indexação de SQL Server em [Guia de design e arquitetura de indexação do SQL Server](/sql/relational-databases/sql-server-index-design-guide?view=sql-server-2017).

### <a name="filter-by-a-grouping-column"></a>Filtrar por uma coluna de agrupamento

Neste exemplo, o usuário de relatório interage com um parâmetro de relatório para selecionar a primeira letra do revendedor. Um segundo parâmetro lista os revendedores cujo nome começa com a letra selecionada.

![A imagem mostra dois parâmetros de relatório: Grupo e Revendedor. O primeiro valor de parâmetro está definido como a letra A, e a lista de Revendedores está filtrada para muitos itens que iniciam com essa letra.](media/paginated-report-cascading-parameter/filter-by-grouping-column-example.png)

Veja como desenvolver os parâmetros em cascata:

1. Crie os parâmetros de relatório **GrupoDeRelatórios** e **Revendedor**, ordenados na sequência correta.
2. Crie o conjunto de dados **GrupoDeRelatórios** para recuperar as primeiras letras usadas por todos os revendedores, utilizando a seguinte instrução de consulta:

    ```sql
    SELECT DISTINCT
      LEFT([ResellerName], 1) AS [ReportGroup]
    FROM
      [Reseller]
    ORDER BY
      [ReportGroup]
    ```

3. Crie o conjunto de dados **Revendedor** para recuperar todos os revendedores que começam com a letra selecionada, usando a seguinte instrução de consulta:

    ```sql
    SELECT
      [ResellerCode],
      [ResellerName]
    FROM
      [Reseller]
    WHERE
      LEFT([ResellerName], 1) = @ReportGroup
    ORDER BY
      [ResellerName]
    ```

4. Relacione o parâmetro de consulta do conjunto de dados **Revendedor** com o parâmetro de relatório correspondente.

É mais eficiente adicionar a coluna de agrupamento à tabela **Revendedor**. Quando persistida e indexada, ela oferece o melhor resultado. Confira mais informações em [Specify Computed Columns in a Table](/sql/relational-databases/tables/specify-computed-columns-in-a-table).

```sql
ALTER TABLE [Reseller]
ADD [ReportGroup] AS LEFT([ResellerName], 1) PERSISTED
```

Essa técnica pode oferecer um potencial ainda maior. Considere o script a seguir que adiciona uma nova coluna de agrupamento para filtrar revendedores por _faixas predefinidas de letras_. Ele também cria um índice para recuperar com eficiência os dados exigidos pelos parâmetros do relatório.

```sql
ALTER TABLE [Reseller]
ADD [ReportGroup2] AS CASE
  WHEN [ResellerName] LIKE '[A-C]%' THEN 'A-C'
  WHEN [ResellerName] LIKE '[D-H]%' THEN 'D-H'
  WHEN [ResellerName] LIKE '[I-M]%' THEN 'I-M'
  WHEN [ResellerName] LIKE '[N-S]%' THEN 'N-S'
  WHEN [ResellerName] LIKE '[T-Z]%' THEN 'T-Z'
  ELSE '[Other]'
END PERSISTED
GO

CREATE NONCLUSTERED INDEX [Reseller_ReportGroup2]
ON [Reseller] ([ReportGroup2]) INCLUDE ([ResellerCode], [ResellerName])
GO
```

### <a name="filter-by-search-pattern"></a>Filtrar por padrão de pesquisa

Neste exemplo, o usuário de relatório interage com um parâmetro de relatório para inserir um padrão de pesquisa. Um segundo parâmetro lista os revendedores cujo nome contém o padrão.

![A imagem mostra dois parâmetros de relatório: Pesquisa e Revendedor. O primeiro valor do parâmetro está definido como o texto "red", e a lista de Revendedores está filtrada para vários itens que contêm esse texto.](media/paginated-report-cascading-parameter/filter-by-search-pattern-example.png)

Veja como desenvolver os parâmetros em cascata:

1. Crie os parâmetros de relatório **Pesquisa** e **Revendedor**, ordenados na sequência correta.
2. Crie o conjunto de dados **Revendedor** para recuperar todos os revendedores que contêm o texto da pesquisa, usando a seguinte instrução de consulta:

    ```sql
    SELECT
      [ResellerCode],
      [ResellerName]
    FROM
      [Reseller]
    WHERE
      [ResellerName] LIKE '%' + @Search + '%'
    ORDER BY
      [ResellerName]
    ```

3. Relacione o parâmetro de consulta do conjunto de dados **Revendedor** com o parâmetro de relatório correspondente.

> [!TIP]
> Esse design pode ser aprimorado para oferecer mais controle aos usuários de relatório, permitindo que eles definam o próprio valor de correspondência de padrão. Por exemplo, o valor de pesquisa "red%" filtrará os revendedores com nomes que _começam_ com os caracteres "red".
>
> Confira mais informações em [LIKE (Transact-SQL)](/sql/t-sql/language-elements/like-transact-sql?view=sql-server-ver15#using-the--wildcard-character).

Veja como permitir que os usuários de relatório definam o próprio padrão.

```sql
WHERE
  [ResellerName] LIKE @Search
```

Contudo, muitos profissionais que não são de banco de dados desconhecem o caractere curinga da porcentagem (%). Em vez disso, eles estão familiarizados com o caractere asterisco (*). Com a modificação da cláusula WHERE, eles podem usar esse caractere.

```sql
WHERE
  [ResellerName] LIKE SUBSTITUTE(@Search, '%', '*')
```

## <a name="present-relevant-items"></a>Apresentar itens relevantes

Nesta situação, é possível usar dados de fato para limitar os valores disponíveis. Os usuários de relatório verão os itens em que a atividade foi registrada.

Neste exemplo, o usuário de relatório interage com três parâmetros de relatório. Os dois primeiros definem um intervalo com as datas dos pedidos de vendas. O terceiro parâmetro lista os revendedores cujos pedidos foram criados durante esse período.

![A imagem mostra três parâmetros de relatório: Data Inicial do Pedido, Data Final do Pedido e Revendedor. Os dois parâmetros de data estão definidos para o mês de janeiro de 2020, e a lista de Revendedores está filtrada para muitos itens que representam os revendedores que fizeram pedidos durante este mês.](media/paginated-report-cascading-parameter/filter-relevant-items-example.png)

Veja como desenvolver os parâmetros em cascata:

1. Crie os parâmetros de relatório **DataInicialDoPedido**, **DataFinalDoPedido** e **Revendedor**, ordenados na sequência correta.
2. Crie o conjunto de dados **Revendedor** para recuperar todos os revendedores que fizeram pedidos no intervalo de datas, usando a seguinte instrução de consulta:

    ```sql
    SELECT DISTINCT
      [r].[ResellerCode],
      [r].[ResellerName]
    FROM
      [Reseller] AS [r]
    INNER JOIN [Sales] AS [s]
      ON [s].[ResellerCode] = [r].[ResellerCode]
    WHERE
      [s].[OrderDate] >= @OrderDateStart
      AND [s].[OrderDate] < DATEADD(DAY, 1, @OrderDateEnd)
    ORDER BY
      [r].[ResellerName]
    ```

## <a name="recommendations"></a>Recomendações

Recomendamos que projete seus relatórios com parâmetros em cascata sempre que possível. O motivo é que eles:

- Oferecem experiências úteis e intuitivas para seus usuários de relatório
- São eficientes, pois recuperam conjuntos menores de valores disponíveis

Otimize suas fontes de dados:

- Com o uso de procedimentos armazenados sempre que possível
- Com a adição de índices apropriados para a recuperação de dados eficiente
- Com a materialização de valores de coluna, e até mesmo linhas, para evitar avaliações caras de tempo de consulta

## <a name="next-steps"></a>Próximas etapas

Para obter mais informações relacionadas a este artigo, confira os seguintes recursos:

- [Parâmetros de relatório no Power BI Report Builder](../report-builder-parameters.md)
- [Adicionar parâmetros em cascata a um relatório (Report Builder e SSRS)](/sql/reporting-services/report-design/add-cascading-parameters-to-a-report-report-builder-and-ssrs)
- Dúvidas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
- Sugestões? [Contribuir com ideias para aprimorar o Power BI](https://ideas.powerbi.com)
