---
title: Modelar relações no Power BI Desktop
description: Apresentar a teoria sobre relacionamentos de modelo no Power BI Desktop
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 10/15/2019
ms.author: v-pemyer
ms.openlocfilehash: 8562d0fd5acee2f18576f0a6b6f2e3d613354f92
ms.sourcegitcommit: 0d7ad791a2d2bef45d5d60e38e0af4c9fc22187b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/13/2019
ms.locfileid: "74009629"
---
# <a name="model-relationships-in-power-bi-desktop"></a>Modelar relações no Power BI Desktop

Este artigo destina-se a modeladores de dados de importação que trabalham com Power BI Desktop. É um tópico importante de design de modelo essencial para fornecer modelos intuitivos, precisos e ideais.

Para obter uma discussão mais aprofundada sobre o design de modelo ideal, incluindo relacionamentos e funções de tabela, confira o artigo [Entender o esquema em estrela e a importância para o Power BI](guidance/star-schema.md).

## <a name="relationship-purpose"></a>Finalidade do relacionamento

Em síntese, os relacionamentos do Power BI propagam filtros aplicados nas colunas de tabelas de modelo a outras tabelas de modelo. Os filtros serão propagados desde que haja um caminho de relacionamento a seguir, o que pode envolver a propagação em várias tabelas.

Os caminhos de relacionamento são determinísticos, o que significa que os filtros sempre são propagados da mesma maneira e sem variação aleatória. No entanto, os relacionamentos podem ser desabilitados ou ter o contexto de filtro modificado por cálculos de modelo que usam funções DAX específicas. Para obter mais informações, confira o tópico [Funções DAX relevantes](#relevant-dax-functions) mais adiante neste artigo.

> [!IMPORTANT]
> É importante entender que os relacionamentos de modelo não impõem a integridade dos dados. Para obter mais informações, confira o tópico [Avaliação de relacionamento](#relationship-evaluation) mais adiante neste artigo. Esse tópico explica como os relacionamentos de modelo se comportam quando há problemas de integridade de dados com seus dados.

Vamos ver como os relacionamentos propagam filtros com um exemplo animado.

![Exemplo animado de propagação do filtro de relação](media/desktop-relationships-understand/animation-filter-propagation.gif)

Neste exemplo, o modelo consiste em quatro tabelas: **Categoria**, **Produto**, **Ano** e **Vendas**. A tabela **Categoria** está relacionada à tabela **Produto** e a tabela **Produto** está relacionada à tabela **Vendas**. A tabela **Ano** também está relacionada à tabela **Vendas**. Todas as relações são de um para muitos (cujos detalhes são descritos posteriormente neste artigo).

Uma consulta (talvez gerada por um Visual de cartão de Power BI) solicita a quantidade total de vendas para pedidos de vendas feitos para uma única categoria, **Cat-A** e por um único ano, **CY2018**. É por isso que você pode ver filtros aplicados nas tabelas **Categoria** e **Ano**. O filtro na tabela **Categoria** é propagada para a tabela **Produto** para isolar dois produtos atribuídos à categoria **Cat-A**. Em seguida, os filtros de tabela **Produto** propagam-se para a tabela **Vendas** para isolar apenas duas linhas de vendas para esses produtos. Essas duas linhas de vendas representam as vendas de produtos atribuídos à categoria **Cat-A**. Sua quantidade combinada é de 14 unidades. Ao mesmo tempo, o filtro da tabela **Ano** propaga para filtrar ainda mais a tabela **Vendas**, resultando em apenas uma linha de vendas para produtos atribuídos à categoria **Cat-A** e que foi pedido no ano **CY2018**. O valor de quantidade retornado pela consulta é de 11 unidades. Observe que, quando vários filtros são aplicados a uma tabela (como a tabela **Vendas**, neste exemplo), é sempre uma operação AND, exigindo que todas as condições sejam verdadeiras.

### <a name="disconnected-tables"></a>Tabelas desconectadas

É incomum que uma tabela de modelo não esteja relacionada a outra tabela de modelo. Essa tabela em um design de modelo válido pode ser descrita como uma _tabela desconectada_. Uma tabela desconectada não se destina a propagar filtros para outras tabelas de modelo. Em vez disso, ela é usada para aceitar "entrada do usuário" (talvez com um visual de segmentação), permitindo que os cálculos de modelo usem o valor de entrada de uma maneira útil. Por exemplo, considere uma tabela desconectada carregada com um intervalo de valores de taxa de câmbio monetário. Fornecer um filtro é aplicado para filtrar por um único valor de taxa. O valor pode ser usado por uma expressão de medida para converter valores de vendas.

O parâmetro what-if do Power BI Desktop é um recurso que cria uma tabela desconectada. Para obter mais informações, confira o artigo [Criar e usar um parâmetro What If para visualizar variáveis no Power BI Desktop](desktop-what-if.md).

## <a name="relationship-properties"></a>Propriedades do relacionamento

Um relacionamento de modelo relaciona uma coluna em uma tabela a uma coluna em uma tabela diferente. (Há um caso especializado em que esse requisito não é verdadeiro, e isso se aplica somente a relações de várias colunas em modelos DirectQuery. Para obter mais informações, confira o artigo da função DAX [COMBINEVALUES](/dax/combinevalues-function-dax).)

> [!NOTE]
> Não é possível relacionar uma coluna a uma coluna diferente _na mesma tabela_. Às vezes, isso é confundido com a capacidade de definir uma restrição de chave estrangeira de banco de dados relacional que faz autorreferência de tabela. Esse conceito de banco de dados relacional pode ser usado para armazenar relações pai-filho (por exemplo, cada registro de funcionário está relacionado a um funcionário "subordinado a"). A geração de uma hierarquia de modelo baseada nesse tipo de relacionamento não pode ser resolvida pela criação de relacionamentos de modelo. Para conseguir isso, confira o artigo [Funções pai e filho](/dax/parent-and-child-functions-dax).

### <a name="cardinality"></a>Cardinalidade

Cada relacionamentos de modelo deve ser definido com um tipo de cardinalidade. Há quatro opções de tipo de cardinalidade, representando as características de dados das colunas relacionadas "de" e "para". O lado "um" significa que a coluna contém valores exclusivos; o lado "dois" significa que a coluna pode conter valores duplicados.

> [!NOTE]
> Se uma operação de atualização de dados tentar carregar valores duplicados em uma coluna do lado "um", toda a atualização de dados falhará.

As quatro opções, juntamente com suas notações abreviadas, são descritas na seguinte lista com marcadores:

- Um para muitos (1:\*)
- Muitos para um (\*:1)
- Um para um (1:1)
- Muitos para muitos (\*:\*)

Quando você cria um relacionamento no Power BI Desktop, o designer detecta e define automaticamente o tipo de cardinalidade. O designer pode fazer isso porque consulta o modelo para saber quais colunas contêm valores exclusivos. Para modelos de Import, ele usa estatísticas de armazenamento interno; para modelos DirectQuery, ele envia consultas de criação de perfil para a fonte de dados. Porém, às vezes ele pode errar. Isso acontece porque as tabelas ainda devem ser carregadas com os dados ou porque as colunas que você espera que contenham valores duplicados atualmente contêm valores exclusivos. Em ambos os casos, você pode atualizar o tipo de cardinalidade fornecendo qualquer uma das colunas do lado "um" contendo valores exclusivos (ou a tabela ainda deve ser carregada com linhas de dados).

As opções de cardinalidade de **um para muitos** e de **muitos para um** são essencialmente iguais e também são os tipos de cardinalidade mais comuns.

Ao configurar um relacionamento de um para muitos ou de muitos para um, você escolherá aquele que corresponde à ordem em que as colunas estão relacionadas. Considere como você configuraria o relacionamento da tabela **Produto** com a tabela **Vendas** usando a coluna **ProductID** encontrada em cada tabela. O tipo de cardinalidade seria _Um para muitos_, pois a coluna **ProductID** na tabela **Produto** contém valores exclusivos. Se você tivesse relacionado as tabelas na direção inversa, **Vendas** para **Produto**, a cardinalidade seria _Muitos para um_.

Um relacionamento de **um para um** significa que ambas as colunas contêm valores exclusivos. Esse tipo de cardinalidade não é comum e provavelmente representa um design de modelo de qualidade inferior devido ao armazenamento de dados redundantes.<!-- For guidance on using this cardinality type, see the [One-to-one relationship guidance](guidance/relationships-one-to-one) article.-->

Um relacionamento de **Muitos para muitos** significa que ambas as colunas podem conter valores duplicados. Esse tipo de cardinalidade é usado raramente. Normalmente, é útil ao criar requisitos de modelo complexos.<!-- For guidance on using this cardinality type, see the [Many-to-many relationship guidance](guidance/relationships-many-to-many) article.-->

> [!NOTE]
> O tipo de cardinalidade de muitos para muitos não tem suporte atualmente para modelos desenvolvidos para o Servidor de Relatórios do Power BI.

> [!TIP]
> No modo de exibição de modelo do Power BI Desktop, você pode interpretar o tipo de cardinalidade de um relacionamento examinando os indicadores (1 ou \*) em qualquer um dos lados da linha de relacionamento. Para determinar quais colunas estão relacionadas, você precisará selecionar (ou focalizar) a linha de relacionamento para realçar as colunas.

### <a name="cross-filter-direction"></a>Direção do filtro cruzado

Cada relacionamento de modelo deve ser definido com uma direção de filtro cruzado. Sua seleção determina as direções em que os filtros serão propagados. As opções de filtro cruzado possíveis dependem do tipo de cardinalidade.

| Tipo de cardinalidade | Opções de filtro cruzado |
| --- | --- |
| Um para muitos (ou muitos para um) | Único<br>Ambos |
| Um para um | Ambos |
| Muitos para muitos | Única (Tabela1 a Tabela2)<br>Única (Tabela2 a Tabela1)<br>Ambos |

A direção de filtro cruzado _único_ significa "direção única" e _Ambas_ significa "ambas as direções". Um relacionamento que filtra em ambas as direções é geralmente descrito como _bidirecional_.

Para relacionamentos de um para muitos, a direção do filtro cruzado é sempre do lado "um" e, opcionalmente, do lado "muitos" (bidirecional). Para relacionamentos de um para um, a direção do filtro cruzado é sempre de ambas as tabelas. Por fim, para os relacionamentos de muitos para muitos, a direção do filtro cruzado pode ser de uma das tabelas ou de ambas as tabelas. Observe que, quando o tipo de cardinalidade inclui um lado "um", os filtros sempre se propagam desse lado.

Quando a direção do filtro cruzado é definida como **Ambas**, uma propriedade adicional está disponível para aplicar a filtragem bidirecional quando as regras da RLS (segurança em nível de linha) são impostas. Para obter mais informações sobre a RLS, confira o artigo [RLS (segurança em nível de linha) com o Power BI Desktop](desktop-rls.md).

A modificação da direção do filtro cruzado do relacionamento, incluindo a desabilitação da propagação do filtro, também pode ser feita pelo cálculo de modelo. Isso é feito usando a função DAX [CROSSFILTER](/dax/crossfilter-function).

Os relacionamentos bidirecionais podem afetar negativamente o desempenho. Além disso, a tentativa de configurar um relacionamento bidirecional pode resultar em caminhos de propagação de filtro ambíguos. Nesse caso, o Power BI Desktop pode falhar ao confirmar a alteração do relacionamento e alertará você com uma mensagem de erro. Às vezes, no entanto, o Power BI Desktop pode permitir que você defina caminhos de relacionamento ambíguos entre tabelas. As regras de precedência que afetam a detecção de ambiguidade e a resolução de caminho são descritas posteriormente neste artigo no tópico [Regras de precedência](#precedence-rules).

É recomendável usar a filtragem bidirecional somente conforme necessário.<!-- For guidance on bi-directional filtering, see the [Cross filter relationship guidance](guidance/relationships-bidirectional-filtering) article.-->

> [!TIP]
> No modo de exibição de modelo do Power BI Desktop, você pode interpretar a direção de filtro cruzado de um relacionamento observando as pontas de seta ao longo da linha de relacionamento. Uma única ponta de seta representa um filtro de direção única na direção da ponta de seta; uma ponta de seta dupla representa um relacionamento bidirecional.

### <a name="make-this-relationship-active"></a>Ativar esta relação

Só pode haver um caminho de propagação de filtro ativo entre duas tabelas de modelo. No entanto, é possível introduzir caminhos de relacionamento adicionais, embora esses relacionamentos devam ser configurados como _inativos_. Os relacionamento inativos só podem se tornar ativos durante a avaliação de um cálculo de modelo. Isso é feito usando a função DAX [USERELATIONSHIP](/dax/userelationship-function-dax).

<!--For guidance on defining inactive relationships, see the [Active vs inactive relationship guidance](guidance/relationships-active-inactive) article.-->

> [!TIP]
> No modo de exibição de modelo do Power BI Desktop, você pode interpretar o status ativo vs. inativo do relacionamento. Um relacionamento ativo é representado por uma linha sólida; um relacionamento inativo é representado como uma linha tracejada.

### <a name="assume-referential-integrity"></a>Pressupor integridade referencial

A propriedade _Supor integridade referencial_ está disponível apenas para relacionamentos de um para muitos e de um para um entre duas tabelas do modo de armazenamento DirectQuery baseadas na mesma fonte de dados. Quando habilitadas, as consultas nativas enviadas à fonte de dados unirão as duas tabelas usando uma junção interna, em vez de uma junção externa. Em geral, habilitar essa propriedade melhora o desempenho da consulta, embora dependa dos detalhes da fonte de dados.

Essa propriedade sempre deve ser habilitada quando existir uma restrição de chave estrangeira de banco de dados entre as duas tabelas. Quando uma restrição FOREIGN KEY não existir, você ainda poderá habilitar a propriedade, desde que tenha certeza de que há integridade de dados.

> [!IMPORTANT]
> Caso a integridade dos dados seja comprometida, a junção interna eliminará linhas sem correspondência entre as tabelas. Por exemplo, considere uma tabela **Vendas** de modelo com um valor de coluna **ProductID** que não existia na tabela **Produto** relacionada. Filtrar a propagação da tabela **Produto** para a tabela **Vendas** eliminará as linhas de vendas de produtos desconhecidos. Isso resultaria em um subestado dos resultados das vendas.
>
> Para obter mais informações, confira o artigo [Pressupor configurações de integridade referencial no Power BI Desktop](desktop-assume-referential-integrity.md).

## <a name="relevant-dax-functions"></a>Funções DAX relevantes

Há várias funções DAX relevantes para relacionamentos de modelo. Cada função é descrita brevemente na seguinte lista com marcadores:

- [RELATED](/dax/related-function-dax): recupera o valor do lado "um".
- [RELATEDTABLE](/dax/relatedtable-function-dax): recupera uma tabela de linhas do lado "muitos".
- [USERELATIONSHIP](/dax/userelationship-function-dax): força o uso de um relacionamento de modelo inativo específico.
- [CROSSFILTER](/dax/crossfilter-function): modifica a direção do filtro cruzado do relacionamento (para uma ou ambas) ou desabilita a propagação do filtro (nenhuma).
- [COMBINEVALUES](/dax/combinevalues-function-dax): une duas cadeias de cadeia de caracteres de texto em uma. A finalidade dessa função é oferecer suporte a relacionamentos de várias colunas em modelos DirectQuery.
- [TREATAS](/dax/treatas-function): aplica o resultado de uma expressão de tabela como filtros a colunas de uma tabela não relacionada.
- [Funções pai e filho](/dax/parent-and-child-functions-dax): uma família de funções relacionadas que podem ser usadas para gerar colunas calculadas para a naturalização de uma hierarquia pai-filho. Essas colunas podem então ser usadas para criar uma hierarquia de nível fixo.

## <a name="relationship-evaluation"></a>Avaliação de relacionamento

Os relacionamentos de modelo, de uma perspectiva de avaliação, são classificados como _fortes_ ou _fracos_. Não é uma propriedade de relacionamento configurável. Na verdade, é inferida do tipo de cardinalidade e da fonte de dados das duas tabelas relacionadas. É importante entender o tipo de avaliação porque pode haver implicações ou consequências de desempenho caso a integridade dos dados seja comprometida. Essas implicações e consequências de integridade são descritas neste tópico.

Primeiro, alguma teoria de modelagem é necessária para entender totalmente as avaliações de relacionamento.

Um modelo Import ou DirectQuery adquire todos os seus dados do cache Vertipaq ou do banco de dados de origem. Em ambas as instâncias, o Power BI é capaz de determinar que existe um lado de "um" de um relacionamento.

Um modelo composto, no entanto, pode incluir tabelas que usam modos de armazenamento diferentes (Import, DirectQuery ou Dual) ou várias fontes DirectQuery. Cada fonte, incluindo o cache Vertipaq de dados de Import, é considerada uma _ilha de dados_. Os relacionamentos de modelo podem ser classificados como _intrailha_ ou _entre ilhas_. Um relacionamento intrailha relaciona duas tabelas em uma ilha de dados, enquanto um relacionamentos entre ilhas relaciona as tabelas de ilhas de dados diferentes. Observe que os relacionamentos nos modelos de importação ou DirectQuery são sempre intrailha.

Vejamos um exemplo de um modelo Composto.

![Exemplo de um modelo Composto que consiste em duas ilhas](media/desktop-relationships-understand/data-island-example.png)

Neste exemplo, o modelo composto consiste em duas ilhas: uma ilha de dados Vertipaq e uma ilha de dados de origem DirectQuery. A ilha de dados Vertipaq contém três tabelas e a ilha de dados de origem DirectQuery contém duas tabelas. Existe um relacionamento entre ilhas para relacionar uma tabela na ilha de dados Vertipaq a uma tabela na ilha de dados de origem DirectQuery.

### <a name="strong-relationships"></a>Relacionamentos fortes

Um relacionamento de modelo é _forte_ quando o mecanismo de consulta pode determinar o lado "um" do relacionamento. Ele tem uma confirmação de que a coluna do lado "um" contém valores exclusivos. Todos os relacionamentos intrailha de um para muitos são fortes.

No exemplo a seguir, há dois relacionamentos fortes, ambos marcados como **S**. Os relacionamentos incluem o relacionamento de um para muitos contido na ilha Vertipaq e o relacionamento de um para muitos contido na origem do DirectQuery.

![Exemplo de um modelo composto que consiste em duas ilhas com relacionamentos fortes marcados](media/desktop-relationships-understand/data-island-example-strong.png)

Para modelos de importação, em que todos os dados são armazenados no cache Vertipaq, uma estrutura de dados é criada para cada relacionamento forte no momento da atualização de dados. As estruturas de dados consistem em mapeamentos indexados de todos os valores de coluna para coluna e sua finalidade é acelerar a junção de tabelas no momento da consulta.

No momento da consulta, os relacionamentos fortes permitem que ocorra a _expansão da tabela_. A expansão da tabela resulta na criação de uma tabela virtual, incluindo as colunas nativas da tabela base e, em seguida, se expandindo para tabelas relacionadas. Para tabelas de importação, isso é feito no mecanismo de consulta; para tabelas DirectQuery, é feito na consulta nativa enviada ao banco de dados de origem (desde que a propriedade "Supor referencial de integridade" não esteja habilitada). O mecanismo de consulta age na tabela expandida, aplicando filtros e agrupando pelos valores nas colunas da tabela expandida.

> [!NOTE]
> Os relacionamentos inativos também são expandidos, mesmo quando o relacionamento não é usado por um cálculo. Relacionamentos bidirecionais não têm impacto na expansão da tabela.

Para relacionamentos de um para muitos, a expansão de tabela ocorre dos lados de "muitos" para os lados de "um" usando semântica LEFT OUTER JOIN. Quando um valor correspondente do lado de "muitos" para o lado de "um" não existir, uma linha virtual em branco será adicionada à tabela do lado de "um".

A expansão de tabela também ocorre para relacionamentos intrailha de um para um, mas usando semântica FULL OUTER JOIN. Isso garante que as linhas virtuais em branco sejam adicionadas em ambos os lados, quando necessário.

As linhas virtuais em branco são efetivamente _Membros Desconhecidos_. Membros desconhecidos representam violações de integridade referencial em que o valor do lado de "muitos" não tem um valor do lado de "um" correspondente. O ideal é que esses espaços em branco não existam e possam ser eliminados pela limpeza ou pelo reparo dos dados de origem.

Vamos ver como a expansão de tabela funciona com um exemplo animado.

![Exemplo animado de expansão de tabela](media/desktop-relationships-understand/animation-expanded-table.gif)

Neste exemplo, o modelo consiste em três tabelas: **Categoria**, **Produto** e **Vendas**. A tabela **Categoria** está relacionada à tabela **Produto** com uma relação de um para muitos; a tabela **Produtos** está relacionada à tabela **Vendas** com uma relação de um para muitos. A tabela **Categoria** contém duas linhas; a tabela **Produto** contém três linhas; e a tabela **Vendas** contêm cinco linhas. Há valores correspondentes em ambos os lados de todos os relacionamentos, o que significa que não há nenhuma violação de integridade referencial. Uma tabela expandida de tempo de consulta é revelada. A tabela consiste nas colunas de todas as três tabelas. É efetivamente uma perspectiva desnormalizada dos dados contidos nas três tabelas. Uma nova linha é adicionada à tabela **Vendas** e tem um valor de identificador de produção (9) que não tem valor correspondente na tabela **Produto**. É uma violação de integridade referencial. Na tabela expandida, a nova linha tem valores (em branco) para as colunas das tabelas **Categoria** e **Produto**.

### <a name="weak-relationships"></a>Relacionamentos fracos

Um relacionamento de modelo é _fraco_ quando não há um lado de "um" garantido. Pode ser o caso por dois motivos:

- O relacionamento usa um tipo de cardinalidade de muitos para muitos (mesmo que uma ou ambas as colunas contenham valores exclusivos)
- O relacionamento é entre ilhas (que pode ser caso apenas para modelos compostos)

No exemplo a seguir, há dois relacionamentos fracos, ambos marcados como **W**. Os dois relacionamentos incluem o relacionamento de muitos para muitos contido na ilha Vertipaq e o relacionamento entre ilhas de um para muitos.

![Exemplo de um modelo composto que consiste em duas ilhas com relacionamentos fracos marcados](media/desktop-relationships-understand/data-island-example-weak.png)

Para modelos de importação, as estruturas de dados nunca são criadas para relacionamentos fracos. Isso significa que as junções de tabela devem ser resolvidas no momento da consulta.

A expansão de tabela nunca ocorre para relacionamentos fracos. As junções de tabela são obtidas usando semântica de junção interna e, por esse motivo, não são adicionadas linhas virtuais em branco para compensar as violações de integridade referencial.

Há restrições adicionais relativas a relacionamentos fracos:

- A função DAX RELACIONADA não pode ser usada para recuperar os valores de coluna do lado "um"
- Impor RLS tem restrições de topologia

> [!NOTE]
> No modo de exibição de modelo Power BI Desktop, nem sempre é possível determinar se um relacionamento de modelo é forte ou fraco. Um relacionamento de muitos para muitos sempre será fraco, pois é um relacionamento de um para muitos quando é um relacionamento entre ilhas. Para determinar se é um relacionamento entre ilhas, você precisará inspecionar os modos de armazenamento de tabela e as fontes de dados para chegar à determinação correta.

### <a name="precedence-rules"></a>Regras de precedência

Os relacionamentos bidirecionais podem introduzir vários (e, portanto, ambíguos) caminhos de propagação de filtro entre tabelas de modelo. A lista a seguir apresenta as regras de precedência que o Power BI usa para detecção de ambiguidade e resolução de caminho:

1. Relacionamentos de muitos para um e de um para um, incluindo relacionamentos fracos
2. Relacionamentos de muitos para muitos
3. Relacionamentos bidirecionais, na direção inversa (ou seja, do lado "Muitos")

### <a name="performance-preference"></a>Preferência de desempenho

A lista a seguir classifica o desempenho de propagação do filtro, do desempenho mais rápido ao mais lento:

1. Relacionamentos intrailhas de um para muitos
2. Relacionamentos de cardinalidade de muitos para muitos
3. Relacionamentos de modelo muitos para muitos obtidos com uma tabela intermediária e que envolvem pelo menos um relacionamento bidirecional
4. Relacionamentos entre ilhas

<!--For further information and guidance on many-to-many relationships, see the [Cross filter relationship guidance](guidance/relationships-bidirectional-filtering) article.-->

## <a name="next-steps"></a>Próximas etapas

- [Entender o esquema em estrela e a importância para o Power BI](guidance/star-schema.md)
- Dúvidas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
