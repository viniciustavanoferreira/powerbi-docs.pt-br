---
title: Usar agregações no Power BI Desktop
description: Execute análises interativas em Big Data no Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/07/2019
ms.author: davidi
LocalizationGroup: Transform and shape data
ms.openlocfilehash: 37cbea42d530f05df1d9f1003554680b80c5b5c3
ms.sourcegitcommit: 212fb4a46af3e434a230331f18456c6a49a408fd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/07/2019
ms.locfileid: "74907927"
---
# <a name="aggregations-in-power-bi-desktop"></a>Agregações no Power BI Desktop

O uso de **agregações** no Power BI permite a análise interativa em Big Data de maneiras que anteriormente não eram possíveis. As **agregações** podem reduzir drasticamente o custo de usar grandes conjuntos de dados para a tomada de decisão.

![agregações no Microsoft Power BI Desktop](media/desktop-aggregations/aggregations_07.jpg)

A lista a seguir oferece as vantagens de usar **agregações**:

* **Desempenho de consulta em Big Data** – conforme os usuários interagem com elementos visuais nos relatórios do Power BI, as consultas DAX são enviadas ao conjunto de dados. Impulsione velocidades de consulta armazenando os dados em cache no nível agregado, usando uma fração dos recursos necessários no nível de detalhe. Use Big Data de uma forma que não seria possível de outra maneira.
* **Otimização da atualização de dados** – reduza os tamanhos de cache e tempos de atualização armazenando os dados em cache no nível agregado. Acelere o tempo para disponibilizar dados para os usuários.
* **Obter arquiteturas equilibradas** – permita que o cache na memória do Power BI lide com consultas agregadas, o que ele faz com eficiência. Limite as consultas enviadas à fonte de dados no modo DirectQuery, ajudando a ficar dentro dos limites de simultaneidade. As consultas que passam tendem a ser filtradas, consultas de nível da transação, com as quais os data warehouses e sistemas de Big Data normalmente lidam bem.

### <a name="table-level-storage"></a>Armazenamento em nível de tabela
Normalmente, o armazenamento em nível de tabela é usado com o recurso de agregações. Para obter mais informações, confira o artigo [modo de armazenamento no Power BI Desktop](desktop-storage-mode.md).

### <a name="data-source-types"></a>Tipos de fontes de dados
As agregações são usadas com fontes de dados que representam modelos dimensionais, como data warehouses, data marts e fontes de Big Data baseadas no Hadoop. Este artigo descreve as diferenças de modelagem típicas no Power BI para cada tipo de fonte de dados.

Todas as fontes DirectQuery e de Importação do Power BI (não multidimensionais) trabalham com agregações.

## <a name="aggregations-based-on-relationships"></a>Agregações com base em relações

As **agregações** com base em relações são usadas normalmente com modelos dimensionais. Os conjuntos de dados do Power BI oriundos de data warehouses e data marts se parecem com esquemas floco de neve/estrela com relações entre tabelas de dimensões e tabelas de fatos.

Considere o seguinte modelo, proveniente de uma única fonte de dados. Digamos que todas as tabelas estão usando o DirectQuery para começar. A tabela de fatos **Vendas** contém bilhões de linhas. Definir o modo de armazenamento de **Vendas** como **Importação** para armazenamento em cache consumiria uma sobrecarga considerável de memória e de gerenciamento.

![tabelas em um modelo](media/desktop-aggregations/aggregations_02.jpg)

Em vez disso, criamos a tabela **Agregação de vendas** como uma tabela de agregação. Ela tem uma granularidade maior do que a de **Vendas** e, portanto, contém bem menos linhas. O número de linhas deve ser igual à soma de **SalesAmount** agrupada por **CustomerKey**, **DateKey** e **ProductSubcategoryKey**. Em vez de bilhões, poderiam ser milhões de linhas, o que é muito mais fácil de gerenciar.

Vamos supor que as seguintes tabelas de dimensões são mais comumente usadas para as consultas com alto valor de negócios. Elas são as tabelas que podem filtrar **Agregação de vendas** usando relações *um-para-muitos* (ou *muitos-para-um*).

* Geografia
* Cliente
* Data
* Subcategoria de Produto
* Categoria de produto

A imagem a seguir mostra este modelo.

![tabela de agregação em um modelo](media/desktop-aggregations/aggregations_03.jpg)

> [!NOTE]
> A tabela **Agregação de vendas** é apenas outra tabela; portanto, ela tem a flexibilidade de ser carregada de diversas formas. Por exemplo, a agregação pode ser executada no banco de dados de origem usando processos ETL/ELT ou pela [Expressão M](/powerquery-m/power-query-m-function-reference) para a tabela. Ela pode usar o Modo de armazenamento de importação com ou sem a [atualização incremental no Power BI Premium](service-premium-incremental-refresh.md) ou pode ser o DirectQuery e otimizada para consultas rápidas usando [índices columnstore](https://docs.microsoft.com/sql/relational-databases/indexes/columnstore-indexes-overview). Essa flexibilidade permite arquiteturas equilibradas que distribuem a carga de consulta para evitar gargalos.

### <a name="storage-mode"></a>Modo de armazenamento 
Vamos continuar com o exemplo que estamos usando. Podemos definir o modo de armazenamento de **Agregação de vendas** como **Importação** para agilizar as consultas.

![configurando o modo de armazenamento](media/desktop-aggregations/aggregations_04.jpg)

Quando fazemos isso, a seguinte caixa de diálogo é exibida, informando que as tabelas de dimensões relacionadas podem ser definidas como modo de armazenamento **Duplo**. 

![caixa de diálogo do modo de armazenamento](media/desktop-aggregations/aggregations_05.jpg)

Defini-las como **Dual** permite que as tabelas de dimensões relacionadas atuem como Importação ou DirectQuery dependendo da subconsulta.

* As consultas que agregam métricas na tabela **Agregação de vendas**, que é Importação, e agrupam atributos nas tabelas Dual relacionadas podem ser retornadas do cache na memória.
* As consultas que agregam métricas na tabela **Vendas**, que é DirectQuery, e agrupam por atributos nas tabelas Dual relacionadas podem ser retornadas no modo DirectQuery. A lógica de consulta, incluindo o grupo por operação, será transmitida para o banco de dados de origem.

Para obter mais informações sobre o modo de armazenamento **Dual**, consulte o artigo [modo de armazenamento](desktop-storage-mode.md).

### <a name="strong-vs-weak-relationships"></a>Relações fortes versus fracas
As ocorrências de agregações baseadas em relações exigem relações fortes.

As relações fortes incluem as seguintes combinações, em que as duas tabelas são provenientes de uma *única fonte*.

| Tabela do lado *muitos | Tabela do lado *um* |
| ------------- |----------------------| 
| Dupla          | Dupla                 | 
| Importar        | Importar ou Dupla       | 
| DirectQuery   | DirectQuery ou Dupla  | 

O único caso no qual uma relação de *origem cruzada* é considerada forte é quando as duas tabelas são de Importação. Relações muitos para muitos são sempre consideradas fracas.

Para ocorrências de agregação de *origem cruzada* que não dependem de relações, confira a seção abaixo sobre agregações com base em colunas "Agrupar por".

### <a name="aggregation-tables-arent-addressable"></a>Tabelas de agregação não são endereçáveis
Usuários com acesso somente leitura ao conjunto de dados não podem consultar tabelas de agregação. Isso previne preocupações de segurança no uso com RLS. Os consumidores e as consultas referem-se à tabela de detalhes, não à tabela de agregação; eles nem mesmo precisam saber que a tabela de agregação existe.

Por esse motivo, a tabela **Sales Agg** deve estar oculta. Se não estiver, a caixa de diálogo Gerenciar agregações a definirá como oculta quando o usuário clicar no botão Aplicar tudo.

### <a name="manage-aggregations-dialog"></a>Gerenciar caixa de diálogo de agregações
Em seguida, definiremos as agregações. Selecione o menu de contexto **Gerenciar agregações** para a tabela **Agregação de vendas** clicando com o botão direito do mouse na tabela.

![Seleção do menu Gerenciar agregações](media/desktop-aggregations/aggregations_06.jpg)

A caixa de diálogo **Gerenciar agregações** é exibida. Ela mostra uma linha para cada coluna na tabela **Agregação de vendas**, em que podemos especificar o comportamento da agregação. As consultas enviadas ao conjunto de dados do Power BI que se referem à tabela **Vendas** são redirecionadas internamente para a tabela **Agregação de vendas**. Os consumidores do conjunto de dados não precisam saber que a tabela **Agregação de vendas** existe.

![Gerenciar caixa de diálogo de agregações](media/desktop-aggregations/aggregations_07.jpg)

A tabela a seguir mostra as agregações para a tabela **Agregação de vendas**.

![tabela de agregações](media/desktop-aggregations/aggregations-table_01.jpg)

#### <a name="summarization-function"></a>Função de resumo

O menu suspenso Resumo oferece os seguintes valores para seleção.
* Contagem
* GroupBy
* Máx
* Mín
* Soma
* Contar linhas da tabela

#### <a name="validations"></a>Validações

As seguintes validações notáveis são impostas pela caixa de diálogo:

* A coluna de detalhes selecionada deve ter o mesmo tipo de dados que a coluna de agregação, exceto pelas funções de resumo Contar e Contar linhas da tabela. Contar e Contar linhas da tabela são oferecidas apenas para colunas de agregação de inteiros e não exigem um tipo de dados correspondente.
* Não são permitidas agregações encadeadas que abranjam três ou mais tabelas. Por exemplo, não é possível configurar agregações na **Tabela A** que se referem à **Tabela B** que tem agregações que se referem à **Tabela C**.
* Não são permitidas agregações duplicadas em que duas entradas usam a mesma função de resumo e referem-se à mesma coluna/tabela de detalhes.
* A tabela de detalhes deve ser DirectQuery, não Importação.

A maioria dessas validações são impostas desabilitando os valores suspensos e mostrando o texto explicativo na dica de ferramenta, conforme mostrado na imagem a seguir.

![validações mostradas pela dica de ferramenta](media/desktop-aggregations/aggregations_08.jpg)

### <a name="group-by-columns"></a>Agrupar por colunas

Neste exemplo, as três entradas GroupBy são opcionais, elas não afetam o comportamento de agregação (exceto a consulta de exemplo DISTINCTCOUNT, mostrada na próxima imagem). Elas são incluídas principalmente para fins de legibilidade. Sem essas entradas GroupBy, as agregações ainda seriam atingidas com base nas relações. Esse é um comportamento diferente de usar agregações sem relações, que é abrangido pelo exemplo de Big Data fornecido posteriormente neste artigo.

### <a name="inactive-relationships"></a>Relações inativas
Não há suporte para agrupar por uma coluna de chave estrangeira usada por um relacionamento inativo e contando com a função USERELATIONSHIP para ocorrências de agregação.

### <a name="detecting-whether-aggregations-are-hit-or-missed-by-queries"></a>Detectando se as agregações foram atingidas ou não pelas consultas

Para obter mais informações sobre como detectar se as consultas são retornadas do cache na memória (mecanismo de armazenamento) ou do DirectQuery (enviadas por push à fonte de dados) usando o SQL Profiler, consulte o artigo [modo de armazenamento](desktop-storage-mode.md). Esse processo também pode ser usado para detectar se as agregações estão sendo atingidas.

Além disso, o seguinte evento estendido é fornecido no SQL Profiler.

    Query Processing\Aggregate Table Rewrite Query

O snippet de código JSON a seguir mostra um exemplo da saída do evento quando uma agregação é usada.

* **matchingResult** mostra que uma agregação foi usada para a subconsulta.
* **dataRequest** mostra as colunas agrupar por e as colunas agregadas usadas pela subconsulta.
* **mapping** mostra as colunas na tabela de agregação para as quais foram mapeadas.

![saída de um evento quando a agregação é usada](media/desktop-aggregations/aggregations-code_01.jpg)

### <a name="query-examples"></a>Exemplos de consulta
A seguinte consulta atinge a agregação, porque as colunas na tabela *Data* estão na granularidade que pode atingir a agregação. Será usada a agregação **Sum** para **SalesAmount**.

![exemplo de consulta](media/desktop-aggregations/aggregations-code_02.jpg)

A consulta a seguir não atinge a agregação. Apesar de solicitar a soma de **SalesAmount**, ela está executando uma operação "Agrupar por" em uma coluna na tabela **Produto**, que não está na granularidade que pode atingir a agregação. Se você observar as relações no modelo, uma subcategoria de produto poderá ter várias linhas **Produto**. A consulta não poderia determinar a qual produto agregar. Nesse caso, a consulta é revertida para DirectQuery e envia uma consulta SQL à fonte de dados.

![exemplo de consulta](media/desktop-aggregations/aggregations-code_03.jpg)

As agregações não são apenas para cálculos simples que executam uma soma simples. Cálculos completos também podem se beneficiar. Conceitualmente, um cálculo complexo é dividido em subconsultas para cada SUM, MIN, MAX e COUNT, e cada subconsulta é avaliada para determinar se a agregação pode ser atingida. Esta lógica não se aplica a todos os casos devido à otimização do plano de consulta, mas em geral ela deve ser aplicada. O exemplo a seguir atinge a agregação:

![exemplo de consulta](media/desktop-aggregations/aggregations-code_04.jpg)

A função COUNTROWS pode se beneficiar das agregações. A seguinte consulta atinge a agregação, porque há uma agregação **Contar** linhas da tabela definida para a tabela **Vendas**.

![exemplo de consulta](media/desktop-aggregations/aggregations-code_05.jpg)

A função AVERAGE pode se beneficiar das agregações. A consulta a seguir atinge a agregação, porque AVERAGE torna-se internamente um SUM dividido por um COUNT. Como a coluna **UnitPrice** tem agregações definidas para SUM e COUNT, a agregação é atingida.

![exemplo de consulta](media/desktop-aggregations/aggregations-code_06.jpg)

Em alguns casos, a função DISTINCTCOUNT pode se beneficiar de agregações. A consulta a seguir atinge a agregação, porque há uma entrada GroupBy para **CustomerKey**, que mantém a distinção de **CustomerKey** na tabela de agregação. Esta técnica ainda está sujeita ao limite de desempenho em que mais de aproximadamente de dois a cinco milhões de valores diferentes podem afetar o desempenho da consulta. No entanto, ela pode ser útil em cenários em que há bilhões de linhas da tabela de detalhes e de dois a cinco milhões de valores distintos na coluna. Nesse caso, a contagem distinta poderá ser executada mais rapidamente do que examinar a tabela com bilhões de linhas, mesmo se ela tiver sido armazenada na memória.

![exemplo de consulta](media/desktop-aggregations/aggregations-code_07.jpg)

### <a name="rls"></a>RLS
As expressões RLS (segurança em nível de linha) devem filtrar a tabela de agregação e a tabela de detalhes para que funcionem corretamente. Após o exemplo, uma expressão RLS na tabela **Geografia** funcionará porque a Geografia está no lado da filtragem de relacionamentos tanto com a tabela **Vendas** quanto com a tabela **Agregação de Vendas**. Consultas que chegam à tabela de agregação e aquelas que não chegam têm RLS aplicado com êxito.

![agregações gerenciam funções](media/desktop-aggregations/manage-roles.png)

Uma expressão RLS na tabela **Produto** filtraria apenas a tabela **Vendas**, não a tabela **Agregação de Vendas**. Isso não é recomendado. As consultas enviadas por usuários que acessam o conjunto de dado usando essa função não se beneficiarão de ocorrências de agregação. Como a tabela de agregação é outra representação dos mesmos dados na tabela de detalhes, não seria seguro responder a consultas da tabela de agregação porque o filtro RLS não pode ser aplicado.

Uma expressão RLS na própria tabela **Sales Agg** filtraria apenas a tabela de agregação, e não a tabela de detalhes. Isso não é permitido.

![agregações gerenciam funções](media/desktop-aggregations/filter-agg-error.jpg)

## <a name="aggregations-based-on-group-by-columns"></a>Agregações baseadas em colunas agrupar por 

Os modelos de Big Data baseados em Hadoop têm características diferentes do que modelos dimensionais. Para evitar junções entre tabelas grandes, elas geralmente não contam com relações. Em vez disso, os atributos de dimensão geralmente são desnormalizados para tabelas de fatos. Esses modelos de Big Data podem ser usados para se fazer uma análise interativa usando **agregações** com base em colunas agrupar por.

A tabela a seguir contém a coluna numérica **Movimento** a ser agregada. Todas as outras colunas são atributos pelos quais agrupar. Ela contém dados de IoT e um grande número de linhas. O modo de armazenamento é DirectQuery. As consultas na fonte de dados agregadas em todo o conjunto de dados são lentas devido ao grande volume.

![Uma tabela de IoT](media/desktop-aggregations/aggregations_09.jpg)

Para habilitar a análise interativa neste conjunto de dados, adicionamos uma tabela de agregação que agrupa pela maioria dos atributos, mas exclui atributos de alta cardinalidade como longitude e latitude. Isso reduz drasticamente o número de linhas, e é pequeno o suficiente para se ajustar confortavelmente em um cache na memória. O modo de armazenamento da **Agregação de atividade do driver** é Importação.

![Tabela Agregação de atividade do driver](media/desktop-aggregations/aggregations_10.jpg)

Em seguida, definimos os mapeamentos de agregação na caixa de diálogo **Gerenciar agregações**. Ela exibe uma linha para cada coluna na tabela **Agregação de atividade do driver**, em que podemos especificar o comportamento da agregação.

![Caixa de diálogo Gerenciar agregações para a tabela Agregação de atividade do driver](media/desktop-aggregations/aggregations_11.jpg)

A tabela a seguir mostra as agregações para a tabela **Agregação de atividade do driver**.

![Tabela de agregações Agregação de atividade do driver](media/desktop-aggregations/aggregations-table_02.jpg)

### <a name="group-by-columns"></a>Agrupar por colunas

Neste exemplo, as entradas **GroupBy** **não são opcionais**. Sem elas, as agregações não seriam atingidas. Esse é um comportamento diferente para usar agregações com base em relações, que é abrangido pelo exemplo de modelo dimensional fornecido anteriormente neste artigo.

### <a name="query-examples"></a>Exemplos de consulta

A consulta a seguir atinge a agregação, porque a coluna **Data da atividade** é abrangida pela tabela de agregação. A agregação Contar linhas da tabela é usada pela função COUNTROWS.

![exemplo de consulta](media/desktop-aggregations/aggregations-code_08.jpg)

Principalmente para modelos que contêm atributos de filtro em tabelas de fatos, é uma boa ideia usar agregações Contar linhas da tabela. O Power BI pode enviar consultas ao conjunto de dados usando COUNTROWS nos casos não explicitamente solicitados pelo usuário. Por exemplo, a caixa de diálogo de filtro mostra a contagem de linhas para cada valor.

![caixa de diálogo de filtros](media/desktop-aggregations/aggregations_12.jpg)

### <a name="rls"></a>RLS

As mesmas regras de RLS detalhadas acima para agregações com base em relações, quanto a se uma expressão RLS pode filtrar a tabela de agregação, a tabela de detalhes ou ambas, também se aplicam a agregações com base nas colunas Agrupar por. No exemplo, uma expressão RLS aplicada à tabela **Atividade do Driver** pode ser usada para filtrar a tabela **Agregação de Atividade do Drive**, pois todas as colunas Agrupar por na tabela de agregação são cobertas pela tabela de detalhes. Um filtro RLS na tabela **Agregação de Atividade do Driver**, por outro lado, não pode ser aplicado à tabela **Atividade do Driver**, portanto, ele não é permitido.

## <a name="aggregation-precedence"></a>Precedência de agregação

A precedência de agregação permite que várias tabelas de agregação sejam consideradas por uma única subconsulta.

Considere o exemplo a seguir. É um [modelo de composição](desktop-composite-models.md) que contém várias fontes DirectQuery.

* A tabela de importação **Agregação de atividade do driver2** está em uma alta granularidade, porque os atributos agrupar por são poucos e de baixa cardinalidade. O número de linhas poderia ser tão baixo quanto milhares; portanto, ele pode se ajustar facilmente em um cache na memória. Esses atributos são usados por um importante dashboard executivo, portanto, as consultas referentes a eles devem ser rápidas.
* A tabela **Agregação de atividade do driver** é uma tabela de agregação intermediária em modo DirectQuery. Contém mais de um bilhão de linhas no SQL DW do Azure e é otimizada na origem usando índices columnstore.
* A tabela **Atividade do driver** é DirectQuery e contém mais de um trilhão de linhas de dados de IoT originados de um sistema de Big Data. Ela atende a consultas de detalhamento para exibir leituras de IoT individuais em contextos de filtro controlados.

> [!NOTE]
> As tabelas de agregação DirectQuery que usam uma fonte de dados diferente para a tabela de detalhes só terão suporte se a tabela de agregação for de um SQL Server, do Azure SQL ou da origem do SQL DW do Azure.

O volume de memória deste modelo é relativamente pequeno, mas usa um grande conjunto de dados. Ele representa uma arquitetura equilibrada, porque distribui a carga de consulta entre os componentes da arquitetura que os utiliza com base em seus pontos fortes.

![tabelas para um modelo de volume de memória pequeno que usa um grande conjunto de dados](media/desktop-aggregations/aggregations_13.jpg)

A caixa de diálogo **Gerenciar agregações** para **Agregação de Atividade do Driver2** mostra que o campo *Precedência* é 10, maior do que **Agregação de Atividade do Driver**, o que significa que ele será considerado primeiro por consultas que usam agregações. As subconsultas que não estão na granularidade e que podem ser respondidas por **Agregação de Atividade do Driver2** considerarão **Agregação de Atividade do Driver**. Consultas de detalhes que não podem ser respondidas por nenhuma tabela de agregação serão direcionadas à **Atividade do driver**.

A tabela especificada na coluna **Tabela de detalhes** é **Atividade do driver**, e não **Agregação de atividade do driver**, porque as agregações encadeadas não são permitidas (consulte [validações](#validations) anteriormente neste artigo).

![Gerenciar caixa de diálogo de agregações](media/desktop-aggregations/aggregations_14.jpg)

A tabela a seguir mostra as agregações para a tabela **Agregação de atividade do driver 2**.

![Tabela de agregações Agregação de atividade do driver 2](media/desktop-aggregations/aggregations-table_03.jpg)

## <a name="aggregations-based-on-group-by-columns-combined-with-relationships"></a>Agregações baseadas nas colunas agrupar por combinadas com relações

Inclusive, é possível combinar as duas técnicas de agregações descritas anteriormente neste artigo. **Agregações** com base em relações podem exigir que as tabelas de dimensões desnormalizadas sejam divididas em várias tabelas. Se isso for dispendioso ou inviável para determinadas tabelas de dimensão, os atributos necessários poderão ser replicados na tabela de agregação para determinadas dimensões e relações usadas para outras pessoas.

O modelo a seguir replica *Mês*, *Trimestre*, *Semestre* e *Ano* na tabela **Agregação de vendas**. Não há nenhuma relação entre **Agregação de vendas** e a tabela **Data**. Há relações para **Cliente** e **Subcategoria de produto**. O modo de armazenamento de **Agregação de vendas** é Importação.

![combinando técnicas de agregação](media/desktop-aggregations/aggregations_15.jpg)

A tabela a seguir mostra as entradas definidas na caixa de diálogo **Gerenciar agregações** da tabela **Agregação de vendas**. As entradas GroupBy em que **Data** é a tabela de detalhes são obrigatórias para atingir agregações para consultas agrupadas pelos atributos de data. Como no exemplo anterior, as entradas GroupBy para CustomerKey e ProductSubcategoryKey não afetam as ocorrências de agregação devido à presença de relações (novamente com a exceção de DISTINCTCOUNT).

![Tabela de agregações Agregação de vendas](media/desktop-aggregations/aggregations-table_04.jpg)

### <a name="query-examples"></a>Exemplos de consulta

A consulta a seguir atinge a agregação, porque CalendarMonth é abrangido pela tabela de agregação, e CategoryName está acessível por meio de relações um para muitos. A agregação Sum é usada para **SalesAmount**.

![exemplo de consulta](media/desktop-aggregations/aggregations-code_09.jpg)

A consulta a seguir não atinge a agregação, porque CalendarDay não é abrangido pela tabela de agregação.

![exemplo de consulta](media/desktop-aggregations/aggregations-code_10.jpg)

A seguinte consulta de inteligência de tempo não atingirá a agregação porque a função DATESYTD gera uma tabela de valores CalendarDay, não abrangida pela tabela de agregação.

![exemplo de consulta](media/desktop-aggregations/aggregations-code_11.jpg)

## <a name="caches-should-be-kept-in-sync"></a>Os caches devem ser mantidos em sincronia

**Agregações** que combinam o modo de armazenamento DirectQuery e Importação e/ou Dual poderão retornar dados diferentes se o cache na memória não for mantido sincronizado com os dados de origem. A execução da consulta não tenta ocultar os problemas de dados, filtrando, por exemplo, os resultados de DirectQuery para coincidir com os valores armazenados em cache. Esses recursos são otimizações de desempenho e devem ser usados apenas de maneiras que não comprometam sua capacidade de atender aos requisitos de negócios. É sua responsabilidade conhecer seus fluxos de dados; portanto, projete de acordo com eles. Há técnicas estabelecidas para lidar com esses problemas na origem, se necessário.

## <a name="next-steps"></a>Próximas etapas

Os artigos a seguir tratam mais sobre os modelos compostos e também descrevem o DirectQuery em detalhes.

* [Modelos compostos no Power BI Desktop](desktop-composite-models.md)
* [Relações muitos para muitos no Power BI Desktop](desktop-many-to-many-relationships.md)
* [Modo de armazenamento no Power BI Desktop](desktop-storage-mode.md)

Artigos do DirectQuery:

* [Usar o DirectQuery no Power BI](desktop-directquery-about.md)
* [Fontes de dados com suporte do DirectQuery no Power BI](desktop-directquery-data-sources.md)
