---
title: Diretrizes de relação muitos para muitos
description: Diretrizes para o desenvolvimento de relações de modelo muitos-para-muitos.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/25/2019
ms.author: v-pemyer
ms.openlocfilehash: 6ce82516413fe43cfbc1336e2f6f51003277fb4a
ms.sourcegitcommit: 3d6b27e3936e451339d8c11e9af1a72c725a5668
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2020
ms.locfileid: "76161284"
---
# <a name="many-to-many-relationship-guidance"></a>Diretrizes de relação muitos para muitos

Este artigo destina-se aos modeladores de dados que trabalham com o Power BI Desktop. Ele descreve três diferentes cenários de modelagem de muitos-para-muitos. Ele também fornece diretrizes sobre como projetar com êxito para esses cenários em seus modelos.

> [!NOTE]
> Este artigo não inclui nenhuma introdução às relações de modelo. Se você não estiver totalmente familiarizado com essas relações, as respectivas propriedades e como configurá-las, recomendamos que leia primeiro o artigo [Relações de modelo no Power BI Desktop](../desktop-relationships-understand.md).
>
> Também é importante que você compreenda o design em esquema em estrela. Para obter mais informações, confira [Entender o esquema em estrela e a importância dele para o Power BI](star-schema.md).

Na verdade, há três cenários de muitos-para-muitos. Eles podem ocorrer quando for necessário:

- [Relacionar duas tabelas de tipo de dimensão](#relate-many-to-many-dimensions)
- [Relacionar duas tabelas de tipo de fato](#relate-many-to-many-facts)
- [Relacionar tabelas de tipo de fato de granulação mais alta](#relate-higher-grain-facts)quando a tabela de tipo de fato armazena linhas com uma granulação mais alta do que as linhas da tabela de tipo de dimensão

## <a name="relate-many-to-many-dimensions"></a>Relacionar dimensões muitos-para-muitos

Vamos considerar o primeiro tipo de cenário muitos-para-muitos com um exemplo. O cenário clássico relaciona duas entidades: clientes de banco e contas bancárias. Considere que os clientes podem ter várias contas e que as contas podem ter vários clientes. Quando uma conta tem vários clientes, eles costumam ser chamados de _titulares de conta conjunta_.

A modelagem dessas entidades é bastante direta. Uma tabela de tipo de dimensão armazena contas e outra tabela de tipo de dimensão armazena os clientes. Como é característico das tabelas de tipo de dimensão, há uma coluna de ID em cada tabela. Para modelar a relação entre as duas tabelas, uma terceira é necessária. Essa tabela é conhecida como _tabela de ponte_. Neste exemplo, a finalidade é armazenar uma linha para cada associação de conta de cliente. Curiosamente, quando essa tabela contém apenas colunas de ID, ela é chamada de [_tabela de fato sem fatos_](star-schema.md#factless-fact-tables).

Aqui está um diagrama de modelo simplista das três tabelas.

![Um diagrama de modelo contém três tabelas. O design é descrito no parágrafo a seguir.](media/relationships-many-to-many/bank-account-customer-model-example.png)

A primeira tabela é denominada **Conta** e contém duas colunas: **AccountID** e **Conta**. A primeira tabela é denominada **AccountCustomer** e contém duas colunas: **AccountID** e **CustomerID**. A terceira tabela é denominada **Cliente** e contém duas colunas: **CustomerID** e **Cliente**. Não há relações entre nenhuma das tabelas.

Duas relações de um-para-muitos são adicionadas para relacionar as tabelas. Aqui está um diagrama de modelo atualizado das tabelas relacionadas. Uma tabela de tipo de fato chamada **Transação** foi adicionada. Ela registra transações de conta. A tabela de ponte e todas as colunas de ID foram ocultas.

![O diagrama de modelo agora contém quatro tabelas. Relações um-para-muitos foram adicionadas para relacionar todas as tabelas.](media/relationships-many-to-many/bank-account-customer-model-related-tables-1.png)

Para ajudar a descrever como funciona a propagação do filtro de relações, o diagrama de modelo foi modificado para revelar as linhas de tabela.

> [!NOTE]
> Não é possível exibir linhas de tabela no diagrama de modelo do Power BI Desktop. Isso é feito neste artigo a fim de contribuir com a discussão, fornecendo exemplos claros.

![O diagrama de modelo agora revela as linhas de tabela. Os detalhes de linha são descritos no parágrafo a seguir.](media/relationships-many-to-many/bank-account-customer-model-related-tables-2.png)

Os detalhes de linha para as quatro tabelas são descritos na seguinte lista com marcadores:

- A tabela **Conta** tem duas linhas:
  - **AccountID** 1 é para Conta-01
  - **AccountID** 2 é para Conta-02
- A tabela **Cliente** tem duas linhas:
  - **CustomerID** 91 é para o Cliente-91
  - **CustomerID** 92 é para o Cliente-92
- A tabela **AccountCustomer** tem três linhas:
  - **AccountID** 1 está associada à **CustomerID** 91
  - **AccountID** 1 está associada à **CustomerID** 92
  - **AccountID** 3 está associada à **CustomerID** 92
- A tabela **Transação** tem três linhas:
  - **Data** 1º de janeiro de 2019, **AccountID** 1, **Valor** 100
  - **Data** 2 de fevereiro de 2019, **AccountID** 2, **Valor** 200
  - **Data** 3 de março de 2019, **AccountID** 1, **Valor** -25

Vejamos o que acontece quando o modelo é consultado.

Abaixo estão dois elementos visuais que resumem a coluna **Valor** da tabela **Transação**. O primeiro visual é agrupado por conta e, portanto, a soma das colunas de **Valor** representa o _saldo da conta_. O segundo visual é agrupado por cliente e, portanto, a soma das colunas de **Valor** representa o _saldo do cliente_.

![Dois visuais de relatório ficam lado a lado. Os visuais são descritos no parágrafo a seguir.](media/relationships-many-to-many/bank-account-customer-model-queried-1.png)

O primeiro visual é intitulado **Saldo da Conta** e tem duas colunas: **Conta** e **Valor**. Ele exibe o seguinte resultado:

- O valor do saldo da Conta-01 é 75
- O valor do saldo da Conta-02 é 200
- O total é 275

O segundo visual é intitulado **Saldo do Cliente** e tem duas colunas: **Cliente** e **Valor**. Ele exibe o seguinte resultado:

- O valor do saldo do Cliente-91 é 275
- O valor do saldo do Cliente-92 é 275
- O total é 275

Uma observação rápida das linhas da tabela e do visual **Saldo da Conta** revela que os resultados para cada conta e para o valor total estão corretos. Isso ocorre porque cada agrupamento de conta resulta em uma propagação de filtro para a tabela **Transação** para essa conta.

No entanto, há algo que não parece estar correto com o visual **Saldo do Cliente**. Cada cliente no visual **Saldo do Cliente** tem o mesmo saldo que o saldo total. Esse resultado só poderia estar correto se todos os clientes fossem titulares de uma conta conjunta, para todas as contas. Esse não é o caso neste exemplo. O problema está relacionado à propagação do filtro. Ele não está fluindo até a tabela **Transação**.

Siga as instruções de filtro de relação da tabela **Cliente** para a tabela **Transação**. Deve ficar evidente que a relação entre a **Conta** e a tabela **AccountCustomer** está se propagando na direção errada. A direção do filtro para essa relação deve ser definida para **Ambas**.

![O diagrama de modelo foi atualizado. Uma única alteração foi feita na relação entre as tabelas Conta e AccountCustomer. Agora, essa relação filtra em ambas as direções.](media/relationships-many-to-many/bank-account-customer-model-related-tables-3.png)

![Os mesmos dois visuais de relatório ficam lado a lado. O primeiro visual não foi alterado. O segundo visual revela um resultado diferente e é descrito nos parágrafos a seguir.](media/relationships-many-to-many/bank-account-customer-model-queried-2.png)

Como esperado, não houve alteração no visual **Saldo da Conta**.

Os visuais de **Saldo do Cliente**, no entanto, agora exibem o seguinte resultado:

- O valor do saldo do Cliente-91 é 75
- O valor do saldo do Cliente-92 é 275
- O total é 275

O visual **Saldo do Cliente** agora exibe um resultado correto. Siga as instruções de filtro por conta própria e veja como os saldos do cliente foram calculados. Além disso, entenda que o visual total significa _todos os clientes_.

Alguém que não esteja familiarizado com as relações de modelo pode concluir que o resultado está incorreto. Essa pessoa poderia perguntar: _Por que o saldo total para **Cliente-91** e **Cliente-92** não é igual a 350 (75 + 275)?_

A resposta a essa pergunta está na compreensão da relação muitos-para-muitos. Cada saldo do cliente pode representar a adição de vários saldos de conta e, portanto, os saldos do cliente são _não aditivos_.

### <a name="relate-many-to-many-dimensions-guidance"></a>Diretrizes para relacionar dimensões muitos-para-muitos

Quando você tem uma relação muitos-para-muitos entre tabelas de tipo de dimensão, fornecemos as seguintes diretrizes:

- Adicione cada entidade muitos-para-muitos relacionada como uma tabela de modelo, assegurando que ela tenha uma coluna de ID (identificação) exclusiva
- Adicione uma tabela de ponte para armazenar entidades associadas
- Crie relações um-para-muitos entre as três tabelas
- Configure **uma** relação bidirecional para permitir que a propagação do filtro continue para as tabelas de tipo de fato
- Quando não for apropriado ter valores de ID ausentes, defina a propriedade **Is Nullable** das colunas de ID como FALSE. A atualização de dados falhará ao se obter os valores ausentes
- Oculte a tabela de ponte (a menos que ela contenha colunas ou medidas adicionais necessárias para relatórios)
- Oculte as colunas de ID que não forem adequadas para relatórios (por exemplo, quando as IDs forem chaves substitutas)
- Se fizer sentido deixar uma coluna de ID visível, verifique se ela está no lado "um" da relação. Sempre oculte a coluna do lado "muitos". Isso resulta no melhor desempenho possível do filtro.
- Para evitar confusão ou má interpretação, comunique explicações para seus usuários de relatório. Você pode adicionar descrições com caixas de texto ou [dicas de ferramenta de cabeçalho de visual](report-page-tooltips.md)

Não recomendamos que você relacione diretamente tabelas de tipo de dimensão muitos-para-muitos. Essa abordagem de design requer a configuração de uma relação com uma cardinalidade muitos-para-muitos. Conceitualmente, isso pode ser alcançado, mas implica que as colunas relacionadas conterão valores duplicados. No entanto, a presença de uma coluna de ID em tabelas de tipo de dimensão é uma prática de design bem aceita. As tabelas de tipo de dimensão sempre devem usar a coluna de ID como o lado "um" de uma relação.

## <a name="relate-many-to-many-facts"></a>Relacionar fatos muitos-para-muitos

O segundo tipo de cenário de muitos-para-muitos envolve relacionar duas tabelas de tipo de fato. Duas tabelas de tipo de fato podem ser relacionadas diretamente. Essa técnica de design pode ser útil para exploração de dados rápida e simples. No entanto, esclarecemos que essa abordagem de design geralmente não é recomendável. Explicaremos o porquê mais adiante nesta seção.

Vamos considerar um exemplo que envolve duas tabelas de tipo de fato: **Ordem** e **Cumprimento**. A tabela **Ordem** contém uma linha por linha de ordem, enquanto a tabela **Cumprimento** pode conter zero ou mais linhas por linha de ordem. As linhas na tabela **Ordem** representam ordens de venda. As linhas na tabela **Cumprimento** representam os itens de ordem que foram enviados. Uma relação muitos-para-muitos relaciona as duas colunas de **OrderID**, com a propagação de filtro somente da tabela **Ordem** (a **Ordem** filtra o **Cumprimento**).

![Um diagrama de modelo contém duas tabelas: Ordem e Cumprimento. Uma relação muitos-para-muitos relaciona as duas colunas OrderID, filtrando de Ordem para Cumprimento.](media/relationships-many-to-many/order-fulfillment-model-example.png)

A cardinalidade da relação é definida como muitos-para-muitos para dar suporte ao armazenamento de valores de **OrderID** duplicados nas duas tabelas. Na tabela **Ordem**, os valores de **OrderID** duplicados podem existir porque uma ordem pode ter várias linhas. Na tabela **Cumprimento**, os valores **OrderID** duplicados podem existir porque as ordens podem ter várias linhas, e as linhas de ordem podem ser cumpridas por muitas remessas.

Agora, vamos dar uma olhada nas linhas da tabela. Na tabela **Cumprimento**, observe que as linhas de ordem podem ser cumpridas por várias remessas. (A ausência de uma linha de ordem significa que a ordem ainda deve ser cumprida.)

![O diagrama de modelo agora revela as linhas de tabela. Os detalhes de linha são descritos no parágrafo a seguir.](media/relationships-many-to-many/order-fulfillment-model-related-tables.png)

Os detalhes de linha para as duas tabelas são descritos na seguinte lista com marcadores:

- A tabela **Ordem** tem cinco linhas:
  - **OrderDate** 1º de janeiro de 2019, **OrderID** 1, **OrderLine** 1, **ProductID** Prod-A, **OrderQuantity** 5, **Vendas** 50
  - **OrderDate** 1º de janeiro de 2019, **OrderID** 1, **OrderLine** 2, **ProductID** Prod-B, **OrderQuantity** 10, **Vendas** 80
  - **OrderDate** 2 de fevereiro de 2019, **OrderID** 2, **OrderLine** 1, **ProductID** Prod-B, **OrderQuantity** 5, **Vendas** 40
  - **OrderDate** 2 de fevereiro de 2019, **OrderID** 2, **OrderLine** 2, **ProductID** Prod-C, **OrderQuantity** 1, **Vendas** 20
  - **OrderDate** 3 de março de 2019, **OrderID** 3, **OrderLine** 1, **ProductID** Prod-C, **OrderQuantity** 5, **Vendas** 100
- A tabela **Cumprimento** tem quatro linhas:
  - **FulfillmentDate** 1º de janeiro de 2019, **FulfillmentID** 50, **OrderID** 1, **OrderLine** 1, **FulfillmentQuantity** 2
  - **FulfillmentDate** 2 de fevereiro de 2019, **FulfillmentID** 51, **OrderID** 2, **OrderLine** 1, **FulfillmentQuantity** 5
  - **FulfillmentDate** 2 de fevereiro de 2019, **FulfillmentID** 52, **OrderID** 1, **OrderLine** 1, **FulfillmentQuantity** 3
  - **FulfillmentDate** 1º de janeiro de 2019, **FulfillmentID** 53, **OrderID** 1, **OrderLine** 2, **FulfillmentQuantity** 10

Vejamos o que acontece quando o modelo é consultado. Aqui está um visual de tabela que compara as quantidades de ordem e de cumprimento pela coluna **OrderID** da tabela **Ordem**.

![Um visual de tabela tem três colunas: OrderID, OrderQuantity e FulfillmentQuantity. Há três linhas, uma para cada ordem. OrderID 2 e 3 não foram completamente cumpridas.](media/relationships-many-to-many/order-fulfillment-model-queried.png)

O visual fornece um resultado preciso. No entanto, a utilidade do modelo é limitada. Você só pode filtrar ou agrupar pela coluna **OrderID** da tabela **Order**.

### <a name="relate-many-to-many-facts-guidance"></a>Diretrizes para relacionar fatos muitos-para-muitos

Em geral, não recomendamos relacionar duas tabelas de tipo de fato diretamente usando a cardinalidade muitos-para-muitos. O principal motivo é que o modelo não fornecerá flexibilidade para as maneiras em que seus visuais de relatório filtrarão ou agruparão. No exemplo, só é possível que os visuais filtrem ou agrupem pela coluna **OrderID** da tabela **Ordem**. Um motivo adicional está relacionado à qualidade de seus dados. Se seus dados tiverem problemas de integridade, algumas linhas poderão ser omitidas durante a consulta devido à natureza da _relação fraca_. Para obter mais informações, confira [Avaliação da relação](../desktop-relationships-understand.md#relationship-evaluation).

Em vez de relacionar as tabelas de tipo de fato diretamente, recomendamos que você adote princípios de design de [esquema em estrela](star-schema.md). Você faz isso adicionando tabelas de tipo de dimensão. As tabelas de tipo de dimensão se relacionam então às tabelas de tipo de fato usando relações um-para-muitos. Essa abordagem de design é robusta, pois fornece opções de relatório flexíveis. Ele permite filtrar ou agrupar usando qualquer uma das colunas de tipo de dimensão e resumir qualquer tabela de tipo de fato relacionada.

Vamos considerar uma solução melhor.

![Um diagrama de modelo inclui seis tabelas: OrderLine, OrderDate, Ordem, Cumprimento, Produto e FulfillmentDate. Todas as tabelas estão relacionadas. O design é descrito no parágrafo a seguir.](media/relationships-many-to-many/order-fulfillment-model-improved.png)

Observe as seguintes alterações de design:

- O modelo agora tem quatro tabelas adicionais: **OrderLine**, **OrderDate**, **Produto** e **FulfillmentDate**
- Todas as quatro tabelas adicionais são tabelas de tipo de dimensão. Relações um-para-muitos relacionam essas tabelas às tabelas de tipo de fato
- A tabela **OrderLine** contém uma coluna **OrderLineID**, que representa o valor **OrderID** multiplicado por 100, além do valor de **OrderLine**, que é um identificador exclusivo para cada linha da ordem
- As tabelas **Ordem** e **Cumprimento** agora contêm uma coluna **OrderLineID** e não contêm mais as colunas **OrderID** e **OrderLine**
- A tabela **Cumprimento** agora contém as colunas **OrderDate** e **ProductID**
- A tabela **FulfillmentDate** se relaciona somente à tabela **Cumprimento**
- Todas as colunas de identificador exclusivo estão ocultas

Dedicar o tempo necessário para aplicação de princípios de design de esquema em estrela oferece os seguintes benefícios:

- Seus visuais de relatório podem _filtrar ou agrupar_ por qualquer coluna visível das tabelas de tipo de dimensão
- Seus visuais de relatório podem _resumir_ qualquer coluna visível das tabelas de tipo de fato
- Filtros aplicados às tabelas **OrderLine**, **OrderDate** ou **Produto** serão propagados para ambas as tabelas de tipo de fato
- Todas as relações são um-para-muitos e cada relação é uma _relação forte_. Eventuais problemas de integridade de dados não serão mascarados. Para obter mais informações, confira [Avaliação da relação](../desktop-relationships-understand.md#relationship-evaluation).

## <a name="relate-higher-grain-facts"></a>Relacionar fatos com granulação mais alta

Esse cenário muitos-para-muitos é muito diferente dos outros dois já descritos neste artigo.

Vamos considerar um exemplo envolvendo quatro tabelas: **Data**, **Vendas**, **Produto** e **Destino**. **Data** e **Produto** são tabelas de tipo de dimensão, e relações um-para-muitos relacionam cada uma delas à tabela de tipo de fato **Vendas**. Até agora, isso representa um bom design de esquema em estrela. No entanto, a tabela **Destino** ainda precisa ser relacionada às outras tabelas.

![Um diagrama de modelo inclui quatro tabelas: Data, Vendas, Produto e Destino. A tabela Destino não está relacionada a nenhuma outra tabela. O design é descrito no parágrafo a seguir.](media/relationships-many-to-many/sales-targets-model-example.png)

A tabela **Destino** contém três colunas: **Category**, **TargetQuantity** e **TargetYear**. As linhas da tabela revelam uma granularidade de ano e categoria do produto. Em outras palavras, os destinos, que são usados para medir o desempenho das vendas, são definidos a cada ano para cada categoria de produto.

![A tabela Destino tem três colunas: TargetYear, Category e TargetQuantity. Seis linhas registram destinos para 2019 e 2020, cada um para três categorias.](media/relationships-many-to-many/sales-targets-model-target-rows.png)

Já que a tabela **Destino** armazena dados em um nível mais alto do que as tabelas de tipo de dimensão, uma relação um-para-muitos não pode ser criada. Bem, isso é verdade para apenas uma das relações. Vamos explorar como a tabela **Destino** pode estar relacionada às tabelas de tipo de dimensão.

### <a name="relate-higher-grain-time-periods"></a>Relacionar períodos com granulação mais alta

Uma relação entre as tabelas **Data** e **Destino** devem ser uma relação um-para-muitos. Isso se deve ao fato de os valores da coluna **TargetYear** serem datas. Neste exemplo, cada valor da coluna **TargetYear** é a primeira data do ano de destino.

> [!TIP]
> Ao armazenar os fatos em uma granularidade de tempo maior que um dia, defina o tipo de dados da coluna como **Data** (ou **Número inteiro** caso você esteja usando chaves de data). Na coluna, armazene um valor que representa o primeiro dia do período. Por exemplo, um período de ano é registrado como 1º de janeiro do ano em questão, enquanto um período de mês é registrado como o primeiro dia do mês em questão.

É preciso ter cuidado para garantir que os filtros de nível de mês ou de data produzam um resultado significativo. Sem nenhuma lógica especial de cálculo, os visuais de relatório podem relatar que as datas de destino são literalmente o primeiro dia de cada ano. Todos os outros dias, bem como todos os meses, exceto janeiro, resumirão a quantidade de destino como BLANK.

O visual de matriz a seguir mostra o que acontece quando o usuário do relatório faz um detalhamento de um ano para os respectivos meses. O visual está resumindo a coluna **TargetQuantity**. (A opção [Mostrar itens sem dados](../desktop-show-items-no-data.md) foi habilitada para as linhas de matriz.)

![Um visual de matriz revela a quantidade de destino do ano de 2020 como 270. Quando expandido para revelar os meses de 2020, janeiro equivale a 270 e todas as outras quantidades de destino no nível do mês equivalem a BLANK.](media/relationships-many-to-many/sales-targets-model-matrix-blank-months-bad.png)

Para evitar esse comportamento, recomendamos que você controle o resumo de seus dados de fatos usando medidas. Uma maneira de controlar o modo como o resumo é realizado é retornar BLANK quando períodos de nível inferior são consultados. Outra maneira, definida com um DAX sofisticado, é distribuir valores entre períodos de nível inferior.

Considere a definição de medida a seguir, que usa a função DAX [ISFILTERED](/dax/isfiltered-function-dax). Ela retorna apenas um valor quando as colunas **Date** ou **Month** não são filtradas.

```dax
Target Quantity =
IF(
    NOT ISFILTERED('Date'[Date])
        && NOT ISFILTERED('Date'[Month]),
    SUM(Target[TargetQuantity])
)
```

O visual de matriz a seguir agora usa a medida **Quantidade de Destino**. Ele mostra que todas as quantidades de destino mensais equivalem a BLANK.

![Um visual de matriz revela a quantidade de destino do ano de 2020 como 270. Quando expandido para revelar os meses de 2020, todas as quantidades de destino no nível do mês equivalem a BLANK.](media/relationships-many-to-many/sales-targets-model-matrix-blank-months-good.png)

### <a name="relate-higher-grain-non-date"></a>Relacionar granulação mais alta (não data)

Uma abordagem de design diferente é necessária ao relacionar uma coluna não data de uma tabela de tipo de dimensão a uma tabela de tipo de fato (quando essa última está em uma granulação mais alta do que a tabela de tipo de dimensão).

As colunas **Categoria** (referentes a ambas as tabelas **Produtos** e **Destino**) contêm valores duplicados. Portanto, não há "um" para uma relação um-para-muitos. Nesse caso, você precisará criar uma relação muitos-para-muitos. A relação deve propagar filtros em uma única direção, da tabela de tipo de dimensão para a tabela de tipo de fato.

![Um fragmento do diagrama de modelo mostra as tabelas Destino e Produto. Uma relação muitos-para-muitos relaciona as duas tabelas. A direção do filtro é de Produto para Destino.](media/relationships-many-to-many/sales-targets-model-relate-non-date.png)

Agora, vamos dar uma olhada nas linhas da tabela.

![Um diagrama de modelo contém duas tabelas: Destino e Produto. Uma relação muitos-para-muitos relaciona as duas colunas Category. Os detalhes de linha são descritos no parágrafo a seguir.](media/relationships-many-to-many/sales-targets-model-relate-non-date-tables.png)

Na tabela **Destino**, há quatro linhas: duas linhas para cada ano de destino (2019 e 2020) e duas categorias (Roupas e Acessórios). Na tabela **Produtos**, há três produtos. Dois pertencem à categoria de roupas e um pertence à categoria de acessórios. Uma das cores de roupas é verde e as duas restantes são azuis.

Um agrupamento visual de tabela pela coluna **Category** da tabela **Produto** produz o resultado a seguir.

![Um visual de tabela tem duas colunas: Category e TargetQuantity. Os acessórios custam 60, roupas custam 40 e o total é 100.](media/relationships-many-to-many/sales-targets-model-visual-category-targets.png)

Esse visual produz o resultado correto. Agora, vamos considerar o que acontece quando a coluna **Cor** da tabela **Produto** é usada para agrupar a quantidade de destino.

![Um visual de tabela tem duas colunas: Cor e TargetQuantity. Azul é 100, Verde é 40 e o total é 100.](media/relationships-many-to-many/sales-targets-model-visual-color-targets-bad.png)

O visual produz uma representação incorreta dos dados. O que está acontecendo?

Um filtro na coluna **Cor** da tabela **Produto** resulta em duas linhas. Uma das linhas é para a categoria Roupas e a outra é para a categoria Acessórios. Esses dois valores de categoria são propagados como filtros para a tabela **Destino**. Em outras palavras, como a cor azul é usada por produtos de duas categorias, _essas categorias_ são usadas para filtrar os destinos.

Para evitar esse comportamento, conforme descrito anteriormente, recomendamos que você controle o resumo de seus dados de fatos usando medidas.

Considere a definição de medida a seguir. Observe que todas as colunas da tabela **Produto** que estão abaixo do nível de categoria são testadas quanto a filtros.

```dax
Target Quantity =
IF(
    NOT ISFILTERED('Product'[ProductID])
        && NOT ISFILTERED('Product'[Product])
        && NOT ISFILTERED('Product'[Color]),
    SUM(Target[TargetQuantity])
)
```

O visual de tabela a seguir agora usa a medida **Quantidade de Destino**. Ele mostra que todas as quantidades de destino de cor equivalem a BLANK.

![Um visual de tabela tem duas colunas: Cor e TargetQuantity. Azul equivale a BLANK, verde equivale a BLANK e o total é 100.](media/relationships-many-to-many/sales-targets-model-visual-color-targets-good.png)

O design final do modelo é semelhante ao mostrado a seguir.

![O diagrama de modelo mostra que as tabelas Data e Destino estão relacionadas com uma relação um-para-muitos. As tabelas Produto e Destino estão relacionadas com uma relação muitos-para-muitos, filtrando de Produto para Destino.](media/relationships-many-to-many/sales-targets-model-example-final.png)

### <a name="relate-higher-grain-facts-guidance"></a>Diretrizes para relacionar fatos com granulação mais alta

Quando você precisa relacionar uma tabela de tipo de dimensão a uma tabela de tipo de fato e a tabela de tipo de fato armazena linhas com uma granulação mais alta do que aquela das linhas da tabela de tipo de dimensão, fornecemos as seguintes diretrizes:

- Para datas de fatos com granulação mais alta:
  - Na tabela de tipo de fato, armazene a primeira data do período
  - Crie uma relação um-para-muitos entre a tabela de data e a tabela de tipo de fato
- Para outros fatos com granulação mais alta:
  - Crie uma relação muitos-para-muitos entre a tabela de tipo de dimensão e a tabela de tipo de fato
- Para ambos os tipos:
  - Resumo de controle com lógica de medida: retornar BLANK quando colunas de tipo de dimensão de nível inferior forem usadas para filtrar ou agrupar
  - Ocultar colunas de tabela de tipo de fato resumíveis: dessa maneira, somente as medidas podem ser usadas para resumir a tabela de tipo de fato

## <a name="next-steps"></a>Próximas etapas

Para obter mais informações relacionadas a este artigo, confira os seguintes recursos:

- [Modelar relações no Power BI Desktop](../desktop-relationships-understand.md)
- [Entender o esquema em estrela e a importância para o Power BI](star-schema.md)
- Dúvidas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
