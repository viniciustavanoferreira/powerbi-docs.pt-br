---
title: Usar e gerenciar agregações no Power BI Desktop
description: Use agregações para realizar análises interativas em Big Data no Power BI Desktop.
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 02/14/2020
ms.author: davidi
LocalizationGroup: Transform and shape data
ms.openlocfilehash: b7ff14b4932ba77b47fdb603124d29858c622fc7
ms.sourcegitcommit: d6a48e6f6e3449820b5ca03638b11c55f4e9319c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/18/2020
ms.locfileid: "77427636"
---
# <a name="use-aggregations-in-power-bi-desktop"></a>Usar agregações no Power BI Desktop

As *agregações* do Power BI permitem reduzir os tamanhos das tabelas, de modo que você possa se concentrar nos dados importantes e aprimorar o desempenho da consulta. As agregações permitem uma análise interativa em Big Data de maneiras que não são possíveis de outra forma e podem reduzir drasticamente o custo da descoberta de conjuntos de dados grandes para a tomada de decisões.

Algumas vantagens do uso de agregações incluem:

- **Melhor desempenho de consulta em Big Data**. Cada interação com os visuais do Power BI envia consultas DAX para o conjunto de dados. Os dados agregados armazenados em cache usam uma fração dos recursos necessários para os dados detalhados, de modo que você possa descobrir Big Data que, de outra forma, seriam inacessíveis.
- **Atualização de dados otimizados**. Tamanhos de cache menores reduzem os tempos de atualização, de modo que os dados cheguem aos usuários mais rapidamente.
- **Arquiteturas balanceadas**. O cache na memória do Power BI pode tratar consultas agregadas, limitando as consultas enviadas no modo DirectQuery e ajudando você a atender aos limites de simultaneidade. As consultas no nível de detalhes restantes tendem a ser consultas filtradas no nível da transação, as quais os data warehouses e sistemas de Big Data normalmente tratam de maneira satisfatória.

![Agregações no Microsoft Power BI Desktop](media/desktop-aggregations/aggregations_07.jpg)

Fontes de dados dimensionais, como data warehouses e data marts, podem usar [agregações baseadas em relação](#aggregation-based-on-relationships). As fontes de Big Data baseadas em Hadoop geralmente [baseiam as agregações em colunas GroupBy](#aggregation-based-on-groupby-columns). Este artigo descreve as diferenças típicas de modelagem do Power BI para cada tipo de fonte de dados.

## <a name="create-an-aggregated-table"></a>Criar uma tabela agregada

Para criar uma tabela agregada:
1. Configure uma nova tabela com os campos desejados, dependendo da fonte de dados e do modelo. 
1. Defina as agregações usando a caixa de diálogo **Gerenciar agregações**.
1. Se aplicável, altere o [modo de armazenamento](#storage-modes) da tabela agregada. 

### <a name="manage-aggregations"></a>Gerenciar agregações

Depois de criar a tabela que contém os campos desejados, no painel **Campos** de qualquer exibição do Power BI Desktop, clique com o botão direito do mouse na tabela e selecione **Gerenciar agregações**.

![Selecionar Gerenciar agregações](media/desktop-aggregations/aggregations-06.png)

A caixa de diálogo **Gerenciar agregações** mostra uma linha para cada coluna na tabela, na qual você pode especificar o comportamento de agregação. No exemplo a seguir, as consultas à tabela de detalhes **Sales** são redirecionadas internamente para a tabela de agregação **Sales Agg**. 

O menu suspenso **Resumo** na caixa de diálogo **Gerenciar agregações** oferece os seguintes valores:
- Contagem
- GroupBy
- Max
- Mín
- Soma
- Contar linhas da tabela

![Gerenciar caixa de diálogo de agregações](media/desktop-aggregations/aggregations_07.jpg)

Nesse exemplo de agregação baseada em relação, as entradas GroupBy são opcionais. Com exceção de DISTINCTCOUNT, elas não afetam o comportamento de agregação e servem principalmente para facilitar a leitura. Sem as entradas GroupBy, as agregações ainda são atingidas com base nas relações. Isso é diferente do [exemplo de Big Data](#aggregation-based-on-groupby-columns) mais adiante neste artigo, no qual as entradas GroupBy são necessárias.

Depois de definir as agregações desejadas, selecione **Aplicar Tudo**. 

### <a name="validations"></a>Validações

A caixa de diálogo **Gerenciar agregações** impõe as seguintes validações importantes:

- A **Coluna de Detalhes** precisa ter o mesmo tipo de dados da **Coluna de Agregação**, exceto pelas funções **Resumo** Contar e Contar linhas da tabela. Contar e Contar linhas da tabela só estão disponíveis para colunas de agregação de inteiros e não exigem um tipo de dados correspondente.
- Não são permitidas agregações encadeadas que abranjam três ou mais tabelas. Por exemplo, as agregações na **Tabela A** não podem se referir a uma **Tabela B** que tenha agregações referentes a uma **Tabela C**.
- Não são permitidas agregações duplicadas, em que duas entradas usam a mesma função **Resumo** e referem-se à mesma **Tabela de Detalhes** e **Coluna de Detalhes**.
- A **Tabela de Detalhes** precisa usar o modo de armazenamento DirectQuery, não Importação.
- Não há suporte ao agrupamento por uma coluna de chave estrangeira usada por uma relação inativa e à dependência da função USERELATIONSHIP para ocorrências de agregação.

A maioria dessas validações é imposta pela desabilitação dos valores suspensos e pela exibição do texto explicativo na dica de ferramenta, conforme mostrado na imagem a seguir.

![Validações mostradas pela dica de ferramenta](media/desktop-aggregations/aggregations_08.jpg)

### <a name="aggregation-tables-are-hidden"></a>As tabelas de agregação são ocultadas

Usuários com acesso somente leitura ao conjunto de dados não podem consultar tabelas de agregação. Isso evita preocupações de segurança quando elas são usadas com a *RLS (Segurança em Nível de Linha)* . Os consumidores e as consultas referem-se à tabela de detalhes, não à tabela de agregação; eles não precisam saber nada sobre a tabela de agregação.

Por esse motivo, as tabelas de agregação ficam ocultas na exibição de **Relatório**. Se a tabela ainda não estiver oculta, a caixa de diálogo **Gerenciar agregações** a definirá como oculta quando você selecionar **Aplicar tudo**.

### <a name="storage-modes"></a>Modos de armazenamento
O recurso de agregação interage com os modos de armazenamento no nível da tabela. As tabelas do Power BI podem usar os modos de armazenamento *DirectQuery*, *Importação* ou *Duplo*. O DirectQuery consulta o back-end diretamente, enquanto a Importação armazena os dados em cache na memória e envia consultas para os dados armazenados em cache. Todas as fontes de dados de Importação e do DirectQuery não multidimensionais do Power BI podem funcionar com agregações. 

Para definir o modo de armazenamento de uma tabela agregada como Importação para acelerar as consultas, selecione a tabela agregada na exibição de **Modelo** do Power BI Desktop. No painel **Propriedades**, expanda **Avançado**, clique na lista suspensa em **Modo de armazenamento**e selecione **Importação**. Observe que essa ação é irreversível. 

![Definir o modo de armazenamento](media/desktop-aggregations/aggregations-04.png)

Para obter mais informações sobre os modos de armazenamento de tabelas, confira [Gerenciar o modo de armazenamento no Power BI Desktop](desktop-storage-mode.md).

### <a name="rls-for-aggregations"></a>RLS para agregações

Para que funcionem corretamente em agregações, as expressões RLS devem filtrar a tabela de agregação e a tabela de detalhes. 

No exemplo a seguir, a expressão RLS na tabela **Geography** funciona para agregações, porque Geography está no lado da filtragem das relações com a tabela **Sales** e a tabela **Sales Agg**. As consultas que atingem a tabela de agregação e aquelas que não atingem terão a RLS aplicada com êxito.

![RLS bem-sucedida para agregações](media/desktop-aggregations/manage-roles.png)

Uma expressão RLS na tabela **Product** filtra apenas a tabela de detalhes **Sales**, não a tabela agregada **Sales Agg**. Como a tabela de agregação é outra representação dos mesmos dados na tabela de detalhes, não é seguro responder a consultas na tabela de agregação, porque o filtro RLS não pode ser aplicado. Não é recomendável filtrar somente a tabela de detalhes, pois as consultas de usuário dessa função não se beneficiarão das ocorrências de agregação. 

Não é permitido o uso de uma expressão RLS que filtre somente a tabela de agregação **Sales Agg** e não a tabela de detalhes **Sales**.

![A RLS somente na tabela de agregação não é permitida](media/desktop-aggregations/filter-agg-error.jpg)

Para [agregações baseadas em colunas GroupBy](#aggregation-based-on-groupby-columns), uma expressão RLS aplicada à tabela de detalhes pode ser usada para filtrar a tabela de agregação, pois todas as colunas GroupBy na tabela de agregação são abrangidas pela tabela de detalhes. Por outro lado, um filtro RLS na tabela de agregação não pode ser aplicado à tabela de detalhes e, portanto, não é permitido.

## <a name="aggregation-based-on-relationships"></a>Agregações baseadas em relações

Os modelos dimensionais normalmente usam *agregações baseadas em relações*. Os conjuntos de dados do Power BI provenientes de data warehouses e data marts se parecem com esquemas floco de neve/estrela, com relações entre tabelas de dimensões e tabelas de fatos.

No modelo a seguir de uma só fonte de dados, as tabelas usam o modo de armazenamento DirectQuery. A tabela de fatos **Vendas** contém bilhões de linhas. A definição do modo de armazenamento de **Sales** como Importação para armazenamento em cache consumirá uma sobrecarga considerável de memória e gerenciamento.

![Tabelas de detalhes em um modelo](media/desktop-aggregations/aggregations_02.jpg)

Em vez disso, crie a tabela de agregação **Sales Agg**. Na tabela **Sales Agg**, o número de linhas é igual à soma de **SalesAmount** agrupado por **CustomerKey**, **DateKey** e **ProductSubcategoryKey**. A tabela **Sales Agg** está em uma granularidade maior do que **Sales** e, portanto, em vez de bilhões, ela pode conter milhões de linhas, que são muito mais fáceis de serem gerenciadas.

Se as tabelas de dimensões a seguir forem as mais comumente usadas para as consultas com alto valor empresarial, elas poderão filtrar **Sales Agg** usando relações *um-para-muitos* ou *muitos para um*.

- Geografia
- Cliente
- Data
- Subcategoria de Produto
- Categoria de produto

A imagem a seguir mostra este modelo.

![Tabela de agregação em um modelo](media/desktop-aggregations/aggregations_03.jpg)

A tabela a seguir mostra as agregações para a tabela **Agregação de vendas**.

![Agregações para a tabela Sales Agg](media/desktop-aggregations/aggregations-table_01.jpg)

> [!NOTE]
> A tabela **Sales Agg**, como qualquer tabela, tem a flexibilidade de ser carregada de diversas maneiras. A agregação pode ser executada no banco de dados de origem usando processos ETL/ELT ou pela [expressão M](/powerquery-m/power-query-m-function-reference) para a tabela. A tabela agregada pode usar o modo de armazenamento Importação com ou sem a [atualização incremental no Power BI Premium](service-premium-incremental-refresh.md) ou usar o DirectQuery e ser otimizada para consultas rápidas usando [índices columnstore](/sql/relational-databases/indexes/columnstore-indexes-overview). Essa flexibilidade permite arquiteturas equilibradas que podem distribuir a carga de consulta para evitar gargalos.

A alteração do modo de armazenamento da tabela agregada **Sales Agg** para **Importação** abre uma caixa de diálogo informando que as tabelas de dimensões relacionadas podem ser definidas com o modo de armazenamento *Duplo*. 

![Caixa de diálogo Modo de armazenamento](media/desktop-aggregations/aggregations_05.jpg)

A definição das tabelas de dimensões relacionadas como Duplo permite que elas funcionem como Importação ou DirectQuery, dependendo da subconsulta. No exemplo:

- As consultas que agregam métricas da tabela **Sales Agg** no modo Importação e fazem o agrupamento por atributos das tabelas relacionadas no modo Duplo podem ser retornadas por meio do cache na memória.
- As consultas que agregam métricas da tabela **Sales** do DirectQuery e fazem o agrupamento por atributos por das tabelas relacionadas no modo Duplo podem ser retornadas no modo DirectQuery. A lógica de consulta, incluindo a operação GroupBy, é transmitida para o banco de dados de origem.

Para obter mais informações sobre o modo de armazenamento Duplo, confira [Gerenciar o modo de armazenamento no Power BI Desktop](desktop-storage-mode.md).

### <a name="strong-vs-weak-relationships"></a>Relações fortes versus fracas

As ocorrências de agregações baseadas em relações exigem relações fortes.

As relações fortes incluem as seguintes combinações de modo de armazenamento, em que ambas as tabelas são provenientes de uma só fonte:

| Tabela do lado *muitos* | Tabela do lado *um* |
| ------------- |----------------------| 
| Dupla          | Dupla                 | 
| Importar        | Importar ou Dupla       | 
| DirectQuery   | DirectQuery ou Dupla  | 

O único caso no qual uma relação de *origem cruzada* é considerada forte é se ambas as tabelas são definidas como Importação. Relações muitos para muitos são sempre consideradas fracas.

Para ocorrências de agregação de *origem cruzada* que não dependem de relações, confira [Agregações baseadas em colunas GroupBy](#aggregation-based-on-groupby-columns). 

### <a name="relationship-based-aggregation-query-examples"></a>Exemplos de consulta de agregação baseada em relação

A seguinte consulta atinge a agregação, porque as colunas na tabela **Data** estão na granularidade que pode atingir a agregação. A coluna **SalesAmount** usa a agregação **Sum**.

![Consulta de agregação baseada em uma relação bem-sucedida](media/desktop-aggregations/aggregations-code_02.jpg)

A consulta a seguir não atinge a agregação. Apesar de solicitar a soma de **SalesAmount**, a consulta executa uma operação GroupBy em uma coluna na tabela **Product**, que não está na granularidade que pode atingir a agregação. Se você observar as relações no modelo, uma subcategoria de produto poderá ter várias linhas de **Product**. A consulta não pode determinar com qual produto deve ser feita a agregação. Nesse caso, a consulta é revertida para DirectQuery e envia uma consulta SQL à fonte de dados.

![Consulta que não pode usar a agregação](media/desktop-aggregations/aggregations-code_03.jpg)

As agregações não são apenas para cálculos simples que executam uma soma simples. Cálculos completos também podem se beneficiar. Conceitualmente, um cálculo complexo é dividido em subconsultas para cada SUM, MIN, MAX e COUNT e cada subconsulta é avaliada para determinar se ela pode atingir a agregação. Esta lógica não se aplica a todos os casos devido à otimização do plano de consulta, mas em geral ela deve ser aplicada. O exemplo a seguir atinge a agregação:

![Consulta de agregação complexa](media/desktop-aggregations/aggregations-code_04.jpg)

A função COUNTROWS pode se beneficiar das agregações. A consulta a seguir atinge a agregação porque há uma agregação **Contar linhas da tabela** definida para a tabela **Sales**.

![Consulta de agregação COUNTROWS](media/desktop-aggregations/aggregations-code_05.jpg)

A função AVERAGE pode se beneficiar das agregações. A consulta a seguir atinge a agregação, porque AVERAGE torna-se internamente um SUM dividido por um COUNT. Como a coluna **UnitPrice** tem agregações definidas para SUM e COUNT, a agregação é atingida.

![Consulta de agregação AVERAGE](media/desktop-aggregations/aggregations-code_06.jpg)

Em alguns casos, a função DISTINCTCOUNT pode se beneficiar de agregações. A consulta a seguir atinge a agregação, porque há uma entrada GroupBy para **CustomerKey**, que mantém a distinção de **CustomerKey** na tabela de agregação. Essa técnica ainda pode atingir o limite de desempenho, em que mais de dois a cinco milhões de valores distintos podem afetar o desempenho da consulta. No entanto, ela pode ser útil em cenários em que há bilhões de linhas na tabela de detalhes, mas de dois a cinco milhões de valores distintos na coluna. Nesse caso, a DISTINCTCOUNT poderá ser executada mais rapidamente do que o exame da tabela com bilhões de linhas, mesmo se ela tiver sido armazenada em cache na memória.

![Consulta de agregação DISTINCTCOUNT](media/desktop-aggregations/aggregations-code_07.jpg)

As funções de inteligência de dados temporais do DAX têm reconhecimento de agregação. A consulta a seguir atinge a agregação porque a função DATESYTD gera uma tabela de valores **CalendarDay** e a tabela de agregação tem em uma granularidade que é coberta por colunas de agrupamento na tabela **Data**. Este é um exemplo de filtro com valor de tabela para a função CALCULATE, que pode funcionar com agregações.

![Consulta de agregação SUMMARIZECOLUMNS](media/desktop-aggregations/aggregations-code-07b.jpg)

## <a name="aggregation-based-on-groupby-columns"></a>Agregação baseada em colunas GroupBy 

Os modelos de Big Data baseados em Hadoop têm características diferentes do que modelos dimensionais. Para evitar junções entre tabelas grandes, os modelos de Big Data geralmente não usam relações, mas desnormalizam atributos de dimensão em tabelas de fatos. Você pode descobrir esses modelos de Big Data para uma análise interativa usando *agregações baseadas em colunas GroupBy*.

A tabela a seguir contém a coluna numérica **Movimento** a ser agregada. Todas as outras colunas são atributos pelos quais é feito o agrupamento. A tabela contém dados de IoT e um grande número de linhas. O modo de armazenamento é DirectQuery. As consultas na fonte de dados agregadas em todo o conjunto de dados são lentas devido ao grande volume. 

![Uma tabela de IoT](media/desktop-aggregations/aggregations_09.jpg)

Para habilitar a análise interativa nesse conjunto de dados, adicione uma tabela de agregação que faz o agrupamento pela maioria dos atributos, mas exclui os atributos de alta cardinalidade como longitude e latitude. Isso reduz drasticamente o número de linhas, e é pequeno o suficiente para se ajustar confortavelmente em um cache na memória. 

![Tabela Agregação de atividade do driver](media/desktop-aggregations/aggregations_10.jpg)

Defina os mapeamentos de agregação da tabela **Driver Activity Agg** na caixa de diálogo **Gerenciar agregações**. 

![Caixa de diálogo Gerenciar agregações para a tabela Agregação de atividade do driver](media/desktop-aggregations/aggregations_11.jpg)

Em agregações baseadas em colunas GroupBy, as entradas **GroupBy** não são opcionais. Sem elas, as agregações não serão atingidas. Isso é diferente de usar agregações baseadas em relações, em que as entradas GroupBy são opcionais.

A tabela a seguir mostra as agregações para a tabela **Agregação de atividade do driver**.

![Tabela de agregações Agregação de atividade do driver](media/desktop-aggregations/aggregations-table_02.jpg)

Defina o modo de armazenamento da tabela agregada **Driver Activity Agg** como Importação.

### <a name="groupby-aggregation-query-example"></a>Exemplo de consulta de agregação GroupBy

A consulta a seguir atinge a agregação porque a coluna **Activity Date** é abrangida pela tabela de agregação. A função COUNTROWS usa a agregação **Contar linhas da tabela**.

![Consulta de agregação GroupBy bem-sucedida](media/desktop-aggregations/aggregations-code_08.jpg)

Especialmente para os modelos que contêm atributos de filtro em tabelas de fatos, é uma boa ideia usar agregações **Contar linhas da tabela**. O Power BI pode enviar consultas ao conjunto de dados usando COUNTROWS nos casos não explicitamente solicitados pelo usuário. Por exemplo, a caixa de diálogo de filtro mostra a contagem de linhas para cada valor.

![Caixa de diálogo de filtro](media/desktop-aggregations/aggregations-12.png)

## <a name="combined-aggregation-techniques"></a>Técnicas de agregação combinadas

Você pode combinar as relações e as técnicas de colunas GroupBy para agregações. As agregações baseadas em relações podem exigir que as tabelas de dimensões desnormalizadas sejam divididas em várias tabelas. Se isso for caro ou impraticável para determinadas tabelas de dimensões, replique os atributos necessários na tabela de agregação para essas dimensões e use relações para outras.

Por exemplo, o modelo a seguir replica **Month**, **Quarter**, **Semester** e **Year** na tabela **Sales Agg**. Não há nenhuma relação entre **Sales Agg** e a tabela **Date**, mas há relações com **Customer** e **Product Subcategory**. O modo de armazenamento de **Agregação de vendas** é Importação.

![Técnicas de agregação combinadas](media/desktop-aggregations/aggregations_15.jpg)

A tabela a seguir mostra as entradas definidas na caixa de diálogo **Gerenciar agregações** da tabela **Agregação de vendas**. As entradas GroupBy em que **Date** é a tabela de detalhes são obrigatórias para atingir agregações de consultas agrupadas pelos atributos de **Date**. Como no exemplo anterior, as entradas **GroupBy** para **CustomerKey** e **ProductSubcategoryKey** não afetam as ocorrências de agregação, com exceção de DISTINCTCOUNT, devido à presença de relações.

![Entradas para a tabela de agregações Sales Agg](media/desktop-aggregations/aggregations-table_04.jpg)

### <a name="combined-aggregation-query-examples"></a>Exemplos de consulta de agregação combinada

A consulta a seguir atinge a agregação porque a tabela de agregação abrange **CalendarMonth**, e **CategoryName** é acessível por meio de relações um-para-muitos. **SalesAmount** usa a agregação **SUM**.

![Exemplo de consulta que atinge a agregação](media/desktop-aggregations/aggregations-code_09.jpg)

A consulta a seguir não atinge a agregação porque a tabela de agregação não abrange **CalendarDay**.

![Exemplo de consulta que não atinge a agregação](media/desktop-aggregations/aggregations-code_10.jpg)

A consulta de inteligência de dados temporais não atinge a agregação porque a função DATESYTD gera uma tabela de valores **CalendarDay** e a tabela de agregação não abrange **CalendarDay**.

![Exemplo de consulta que não atinge a agregação](media/desktop-aggregations/aggregations-code_11.jpg)

## <a name="aggregation-precedence"></a>Precedência de agregação

A precedência de agregação permite que várias tabelas de agregação sejam consideradas por uma única subconsulta.

O seguinte exemplo é um [modelo composto](desktop-composite-models.md) que contém várias fontes:

- A tabela **Driver Activity** do DirectQuery contém mais de um trilhão de linhas de dados de IoT originados de um sistema de Big Data. Ela atende a consultas de detalhamento para exibir leituras de IoT individuais em contextos de filtro controlados.
- A tabela **Agregação de atividade do driver** é uma tabela de agregação intermediária em modo DirectQuery. Ela contém mais de um bilhão de linhas no SQL Data Warehouse do Azure e é otimizada na origem usando índices columnstore.
- A tabela de Importação **Driver Activity Agg2** está em uma alta granularidade, porque os atributos GroupBy por são poucos e de baixa cardinalidade. O número de linhas poderia ser tão baixo quanto milhares; portanto, ele pode se ajustar facilmente em um cache na memória. Esses atributos são usados por um importante dashboard executivo, portanto, as consultas referentes a eles devem ser rápidas.

> [!NOTE]
> Só há suporte para as tabelas de agregação do DirectQuery que usam outra fonte de dados da tabela de detalhes se a tabela de agregação for de uma fonte do SQL Server, do SQL do Azure ou do SQL Data Warehouse do Azure.

O volume de memória deste modelo é relativamente pequeno, mas usa um grande conjunto de dados. Ele representa uma arquitetura equilibrada, porque distribui a carga de consulta entre os componentes da arquitetura, utilizando-os de acordo com os pontos fortes.

![Tabelas para um modelo de volume de memória pequeno que descobre um conjunto de dados grande](media/desktop-aggregations/aggregations_13.jpg)

A caixa de diálogo **Gerenciar agregações** de **Driver Activity Agg2** define o campo **Precedência** como *10*, que é maior do que para **Driver Activity Agg**. A configuração de precedência mais alta significa que as consultas que usam agregações considerarão **Driver Activity Agg2** primeiro. As subconsultas que não estão na granularidade e que podem ser respondidas por **Driver Activity Agg2** considerarão **Driver Activity Agg**. Consultas de detalhes que não podem ser respondidas por nenhuma tabela de agregação serão direcionadas à **Atividade do driver**.

A tabela especificada na coluna **Detail Table** é **Driver Activity**, não **Driver Activity Agg**, porque as agregações encadeadas não são permitidas.

![Gerenciar caixa de diálogo de agregações](media/desktop-aggregations/aggregations_14.jpg)

A tabela a seguir mostra as agregações para a tabela **Agregação de atividade do driver 2**.

![Tabela de agregações Agregação de atividade do driver 2](media/desktop-aggregations/aggregations-table_03.jpg)

## <a name="detect-whether-queries-hit-or-miss-aggregations"></a>Detectar se as consultas atingem ou ignoram agregações

O SQL Profiler pode detectar se as consultas são retornadas do mecanismo de armazenamento de cache na memória ou enviadas por push para a fonte de dados pelo DirectQuery. Você pode usar o mesmo processo para detectar se as agregações estão sendo atingidas. Para obter mais informações, confira [Consultas que atingem ou ignoram o cache](desktop-storage-mode.md#queries-that-hit-or-miss-the-cache). 

O SQL Profiler também fornece o evento estendido `Query Processing\Aggregate Table Rewrite Query`.

O snippet de código JSON a seguir mostra um exemplo da saída do evento quando uma agregação é usada.

- **matchingResult** mostra que a subconsulta usou uma agregação.
- **dataRequest** mostra as colunas GroupBy e as colunas agregadas usadas pela subconsulta.
- **mapping** mostra as colunas na tabela de agregação para as quais foram mapeadas.

![Saída de um evento quando a agregação é usada](media/desktop-aggregations/aggregations-code_01.jpg)

## <a name="keep-caches-in-sync"></a>Manter os caches sincronizados

As agregações que combinam o modo de armazenamento DirectQuery, Importação e/ou Duplo poderão retornar dados diferentes se o cache na memória não for mantido em sincronia com os dados de origem. Por exemplo, a execução de consulta não tentará mascarar os problemas de dados filtrando os resultados do DirectQuery para que correspondam aos valores armazenados em cache. Há técnicas estabelecidas para lidar com esses problemas na origem, se necessário. As otimizações de desempenho devem ser usadas apenas de maneiras que não comprometam sua capacidade de atender aos requisitos empresariais. É sua responsabilidade conhecer seus fluxos de dados e o design de acordo. 

## <a name="next-steps"></a>Próximas etapas

Para obter mais informações sobre modelos compostos, confira:

- [Usar modelos compostos no Power BI Desktop](desktop-composite-models.md)
- [Aplicar relações muitos para muitos no Power BI Desktop](desktop-many-to-many-relationships.md)
- [Gerenciar o modo de armazenamento no Power BI Desktop](desktop-storage-mode.md)

Para obter mais informações sobre o DirectQuery, confira:

- [Sobre o uso do DirectQuery no Power BI](desktop-directquery-about.md)
- [Fontes de dados do Power BI](desktop-directquery-data-sources.md)
