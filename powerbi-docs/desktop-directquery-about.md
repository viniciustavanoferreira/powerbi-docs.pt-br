---
title: Usando o DirectQuery no Power BI
description: Entenda como usar o DirectQuery com o Power BI e conheça as melhores práticas para saber como e quando usar o DirectQuery ou outras opções
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 04/09/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 0f2d6bae607383eb8934b3f395add540c6754690
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/05/2020
ms.locfileid: "81006700"
---
# <a name="about-using-directquery-in-power-bi"></a>Sobre o uso do DirectQuery no Power BI

Você pode se conectar a todos os tipos de fontes de dados diferentes ao usar o *Power BI Desktop* ou o *serviço do Power BI* e fazer essas conexões de dados de maneiras diferentes. Você pode *importar* dados para o Power BI, que é a maneira mais comum de obter dados, ou conectar-se diretamente aos dados no repositório de origem original, que é conhecido como *DirectQuery*. Este artigo descreve as funcionalidades do DirectQuery:

* Diferentes opções de conectividade para o DirectQuery
* Orientação para quando você deve considerar o uso do DirectQuery em vez da importação
* Desvantagens do uso do DirectQuery
* Melhores práticas para o uso do DirectQuery

Siga as melhores práticas para usar a importação versus o DirectQuery:

* Você deve importar dados para o Power BI sempre que possível. A importação aproveita o mecanismo de consulta de alto desempenho do Power BI e proporciona uma experiência altamente interativa e completa.
* Caso as suas metas não possam ser atendidas com a importação de dados, considere o uso do DirectQuery. Por exemplo, se os dados estão frequentemente em alteração e os relatórios devem refletir os dados mais recentes, o DirectQuery pode ser a melhor opção. No entanto, o uso do DirectQuery só é possível quando a fonte de dados subjacente pode fornecer consultas interativas, menos de 5 segundos para a consulta de agregação típica, e pode processar a carga de consulta que será gerada. Além disso, a lista de limitações do uso do DirectQuery deve ser considerada cuidadosamente.

O conjunto de funcionalidades oferecido pelo Power BI para a importação e o DirectQuery evoluirá ao longo do tempo. As alterações incluirão o fornecimento de mais flexibilidade ao usar dados importados, de modo que a importação possa ser usada em mais casos, bem como a eliminação de algumas das desvantagens do uso do DirectQuery. Independentemente das melhorias, ao usar o DirectQuery, o desempenho da fonte de dados subjacente sempre é uma consideração importante. Se essa fonte de dados subjacente estiver lenta, o uso do DirectQuery nessa fonte ficará impraticável.

Este artigo aborda o DirectQuery com o Power BI, não o *SQL Server Analysis Services*. O DirectQuery também é um recurso do SQL Server Analysis Services. Muitos dos detalhes descritos neste artigo se aplicam a esse recurso. Há também diferenças importantes. Para obter informações sobre como usar o DirectQuery com o SQL Server Analysis Services, confira [DirectQuery no SQL Server 2016 Analysis Services](https://download.microsoft.com/download/F/6/F/F6FBC1FC-F956-49A1-80CD-2941C3B6E417/DirectQuery%20in%20Analysis%20Services%20-%20Whitepaper.pdf).

Este artigo concentra-se no fluxo de trabalho recomendado para o DirectQuery, em que o relatório é criado no Power BI Desktop, mas também aborda a conexão diretamente no serviço do Power BI.

## <a name="power-bi-connectivity-modes"></a>Modos de conectividade do Power BI

O Power BI se conecta a um grande número de fontes de dados variadas, que abrangem:

* Serviços online (Salesforce, Dynamics 365 e outros)
* Bancos de dados (SQL Server, Access, Amazon Redshift e outros)
* Arquivos simples (Excel, JSON e outros)
* Outras fontes de dados (Spark, sites, Microsoft Exchange e outros)

Para essas fontes, é possível importar os dados no Power BI. Para algumas delas, também é possível se conectar usando o DirectQuery. Para obter um resumo das fontes que dão suporte ao DirectQuery, confira [Fontes de dados compatíveis com o DirectQuery](desktop-directquery-data-sources.md). Mais fontes serão habilitadas para o DirectQuery no futuro, concentrando-se principalmente em fontes que possam proporcionar um bom desempenho de consulta interativa.

O SQL Server Analysis Services é um caso especial. Ao se conectar ao SQL Server Analysis Services, você pode optar por importar os dados ou usar uma *conexão dinâmica*. O uso de uma conexão dinâmica é semelhante ao DirectQuery. Nenhum dado é importado e a fonte de dados subjacente sempre é consultada para atualizar um visual. Uma conexão dinâmica é diferente em muitos outros aspectos e, portanto, um termo diferente, *conexão dinâmica* versus *DirectQuery*, é usado.

Estas três opções para se conectar aos dados: *importação*, *DirectQuery* e *conexão dinâmica*.

### <a name="import-connections"></a>Conexões de importação

Para a importação, ao usar **Obter Dados** no Power BI Desktop para se conectar a uma fonte de dados como o SQL Server, o comportamento dessa conexão será o seguinte:

* Durante a experiência de Obter Dados, o conjunto de tabelas selecionado define cada uma das consultas que retornará um conjunto de dados. Essas consultas podem ser editadas antes do carregamento dos dados, por exemplo, para aplicar filtros, agregar os dados ou unir tabelas diferentes.
* Após o carregamento, todos os dados definidos por essas consultas serão importados para o cache do Power BI.
* Com a criação de um visual no Power BI Desktop, os dados importados serão consultados. O repositório do Power BI garante que a consulta será rápida. Todas as alterações no visual são refletidas imediatamente.
* As alterações nos dados subjacentes não são refletidas em nenhum visual. É necessário *atualizar* para reimportar os dados.
* Após a publicação do relatório como um arquivo *.pbix* no serviço do Power BI, um conjunto de dados é criado e carregado no serviço do Power BI. Os dados importados são incluídos no conjunto de dados. Em seguida, é possível agendar a atualização desses dados, por exemplo, para reimportar os dados todos os dias. Dependendo da localização da fonte de dados original, poderá ser necessário configurar um gateway de dados local.
* Ao abrir um relatório existente no serviço do Power BI ou criar um relatório, os dados importados são consultados novamente, garantindo a interatividade.
* Páginas inteiras de relatório ou visuais podem ser fixadas como blocos de dashboard. Os blocos são atualizados automaticamente sempre que o conjunto de dados subjacente é atualizado.

### <a name="directquery-connections"></a>Conexões do DirectQuery

Para o DirectQuery, ao usar **Obter Dados** no Power BI Desktop para se conectar a uma fonte de dados, o comportamento dessa conexão será o seguinte:

* Durante a experiência inicial de Obter Dados, a fonte é selecionada. Para fontes relacionais, um conjunto de tabelas é selecionado e cada uma ainda define uma consulta que retorna logicamente um conjunto de dados. Para fontes multidimensionais como SAP BW, somente a fonte é selecionada.
* No entanto, após o carregamento, nenhum dado é importado para o repositório do Power BI. Em vez disso, após a criação de um visual no Power BI Desktop, as consultas são enviadas à fonte de dados subjacente para recuperar os dados necessários. O tempo necessário para atualizar o visual depende do desempenho da fonte de dados subjacente.
* As alterações nos dados subjacentes não são imediatamente refletidas em nenhum visual existente. Ainda é necessário fazer a atualização. As consultas necessárias são reenviadas para cada visual e o visual é atualizado conforme necessário.
* Após a publicação do relatório no serviço do Power BI, isso resultará novamente em um conjunto de dados no serviço do Power BI, o mesmo usado para a importação. No entanto, *nenhum dado* será incluído nesse conjunto de dados.
* Ao abrir um relatório existente no serviço do Power BI ou criar um relatório, a fonte de dados subjacente é novamente consultada para recuperar os dados necessários. Dependendo da localização da fonte de dados original, poderá ser necessário configurar um gateway de dados local, assim como será necessário para o modo de importação se os dados forem atualizados.
* Páginas inteiras de relatório ou visuais podem ser fixadas como blocos de Dashboard. Para garantir que a abertura de um dashboard seja rápida, os blocos são atualizados automaticamente de acordo com um agendamento, por exemplo, a cada hora. A frequência dessa atualização pode ser controlada, para refletir a frequência com que os dados são alterados e o nível de importância de ver os dados mais recentes. Ao abrir um dashboard, os blocos refletem os dados na hora da última atualização, não necessariamente as últimas alterações feitas na fonte subjacente. Você pode atualizar um dashboard aberto para garantir que ele seja atual.

### <a name="live-connections"></a>Conexões dinâmicas

Ao se conectar ao SQL Server Analysis Services, há uma opção para importar dados do modelo de dados selecionado ou conectar-se dinamicamente a ele. Se você usar a importação, defina uma consulta nessa fonte externa do SQL Server Analysis Services e os dados serão importados normalmente. Se você usar a conexão dinâmica, não haverá nenhuma consulta definida e todo o modelo externo será mostrado na lista de campos.

A situação descrita no parágrafo anterior se aplica à conexão com as seguintes fontes também, com exceção de que não há nenhuma opção para importar os dados:

* Conjuntos de dados do Power BI, por exemplo, ao se conectar a um conjunto de dados do Power BI que foi anteriormente criado e publicado no serviço, com a finalidade de criar um relatório com base nele.
* Common Data Services.

O comportamento de relatórios no SQL Server Analysis Services, após a publicação no serviço do Power BI, é semelhante ao comportamento dos relatórios do DirectQuery das seguintes maneiras:

* Ao abrir um relatório existente no serviço do Power BI ou criar um relatório, a fonte subjacente do SQL Server Analysis Services é consultada, possivelmente, exigindo um gateway de dados local.
* Os blocos de dashboard são atualizados automaticamente de acordo com um agendamento, por exemplo, a cada hora.

Há também diferenças importantes. Por exemplo, nas conexões dinâmicas, a identidade do usuário que abre o relatório sempre é transmitida para a fonte subjacente do SQL Server Analysis Services.

Deixando essas comparações de lado, vamos nos concentrar apenas no DirectQuery no restante deste artigo.

## <a name="when-is-directquery-useful"></a>Quando o DirectQuery é útil?

A tabela a seguir descreve cenários nos quais a conexão com o DirectQuery pode ser especialmente útil. Ela inclui casos em que manter os dados na fonte original é considerado benéfico. A descrição inclui uma discussão sobre a disponibilidade do cenário especificado no Power BI.

| Limitação | Descrição |
| --- | --- |
| Dados com alterações frequentes e a necessidade de relatórios quase em tempo real |Os modelos com os dados importados podem ser atualizados no máximo uma vez por hora (com uma frequência maior com as assinaturas do Power BI Pro ou do Power BI Premium). Se os dados estiverem continuamente em alteração e for necessário que os relatórios mostrem os dados mais recentes, o uso da importação com a atualização agendada poderá não atender a essas necessidades. Você pode transmitir os dados diretamente para o Power BI, embora haja limites para os volumes de dados compatíveis com esse caso. <br/> <br/> O uso do DirectQuery, por outro lado, significa que abrir ou atualizar um relatório ou um dashboard sempre mostra os dados mais recentes na fonte. Além disso, os blocos de dashboard podem ser atualizados com mais frequência, por exemplo, a cada 15 minutos. |
| Os dados são muito grandes |Se os dados forem muito grandes, não será possível importá-los todos eles. O DirectQuery, por outro lado, não exige uma grande transferência de dados, pois ele é consultado in-loco. <br/> <br/> No entanto, dados grandes também podem indicar que o desempenho das consultas nessa fonte subjacente é muito lento, conforme abordado em [Implicações do uso do DirectQuery](#implications-of-using-directquery). Você nem sempre precisa importar os dados detalhados completos. Em vez disso, os dados podem ser pré-agregados durante a importação. O *Editor de Consultas* facilita a pré-agregação durante a importação. Em última análise, é possível importar exatamente os dados de agregação necessários para cada visual. Embora o DirectQuery seja a abordagem mais simples para dados grandes, a importação de dados agregados poderá oferecer uma solução caso a fonte subjacente seja muito lenta. |
| Regras de segurança são definidas na fonte subjacente |Quando os dados são importados, o Power BI se conecta à fonte de dados usando as credenciais do usuário atual no Power BI Desktop ou as credenciais definidas como parte da configuração da atualização agendada no serviço do Power BI. Na publicação e no compartilhamento de um relatório desse tipo, tenha cuidado para só compartilhá-lo com usuários que tenham a permissão de ver os mesmos dados ou para definir a Segurança em Nível de Linha como parte do conjunto de dados. <br/> <br/> Como o DirectQuery sempre consulta a fonte subjacente, o ideal é que essa configuração permita que qualquer segurança nessa fonte subjacente seja aplicada. No entanto, atualmente, o Power BI sempre se conecta à fonte subjacente usando as mesmas credenciais que são usadas para a importação. <br/> <br/> Até que o Power BI permita que a identidade do consumidor do relatório seja transmitida para a fonte subjacente, o DirectQuery não oferece nenhuma vantagem em relação à segurança da fonte de dados. |
| Houver aplicação de restrições de soberania de dados |Algumas organizações têm políticas em relação à soberania de dados, resultando na impossibilidade de os dados deixarem as instalações da organização. Uma solução baseada na importação claramente apresentaria problemas. Por outro lado, com o DirectQuery os dados permanecem na fonte subjacente. <br/> <br/> No entanto, mesmo com o DirectQuery, alguns caches de dados no nível do visual são mantidos no serviço do Power BI, devido à atualização agendada dos blocos. |
| A fonte de dados subjacente é uma fonte OLAP contendo medidas |Se a fonte de dados subjacente contiver *medidas*, como o SAP HANA ou o SAP Business Warehouse, a importação dos dados ocasionará outros problemas. Isso significa que os dados importados estão em um determinado nível de agregação, conforme definido pela consulta. Por exemplo, as medidas **TotalSales** por **Class**, **Year** e **City**. Nesse caso, se um visual for criado com a solicitação de dados em um nível mais alto de agregação, como **TotalSales** por **Year**, haverá uma agregação adicional do valor agregado. Essa agregação é adequada para medidas aditivas, como **Sum** e **Min**, mas é um problema para medidas não aditivas, como **Average** e **DistinctCount**. <br/> <br/> Para facilitar a obtenção dos dados de agregação corretos, conforme necessário para um visual específico, diretamente da fonte, é necessário enviar consultas por visual, como no DirectQuery. <br/> <br/> Ao conectar-se com o SAP BW (Business Warehouse), a escolha do DirectQuery permite esse tratamento das medidas. Para obter informações sobre o SAP BW, confira [DirectQuery e SAP BW](desktop-directquery-sap-bw.md). <br/> <br/> No entanto, atualmente, o DirectQuery no SAP HANA a trata como uma fonte relacional e fornece um comportamento semelhante à importação. Essa abordagem é detalhada em [DirectQuery e SAP HANA](desktop-directquery-sap-hana.md). |

Em resumo, considerando as funcionalidades atuais do DirectQuery no Power BI, ele oferece os benefícios nos seguintes cenários:

* Dados com alterações frequentes e a necessidade de relatórios quase em tempo real.
* Manipulação de dados muito grandes, sem a necessidade de pré-agregação.
* Aplicação de restrições de soberania de dados.
* A fonte é uma fonte multidimensional que contém medidas, como o SAP BW.

Os detalhes da lista anterior relacionam-se ao uso do Power BI isoladamente. Em vez disso, você pode usar um modelo externo do SQL Server Analysis Services ou do Azure Analysis Services para importar dados. Em seguida, use o Power BI para se conectar a esse modelo. Embora essa abordagem exija configuração adicional, ela oferece maior flexibilidade. Volumes de dados muito maiores podem ser importados. Não há restrição para a frequência com que os dados podem ser atualizados.

## <a name="implications-of-using-directquery"></a>Implicações do uso do DirectQuery

O uso do DirectQuery tem implicações potencialmente negativas, conforme detalhado nesta seção. Algumas dessas limitações são ligeiramente diferentes de acordo com a fonte exata que está sendo usada. Abordamos as limitações sempre que aplicável e artigos separados abordam essas fontes que são significativamente diferentes.

### <a name="performance-and-load-on-the-underlying-source"></a>Desempenho e carregamento na fonte subjacente

Ao usar o DirectQuery, a experiência geral depende muito do desempenho da fonte de dados subjacente. Se a atualização de cada visual, por exemplo, após a alteração de um valor de segmentação, levar alguns segundos, geralmente, menos de 5 segundos, a experiência será razoável. A experiência pode parecer lenta em comparação com a resposta imediata ao importar os dados para o Power BI. Se a lentidão da origem fizer com que visuais individuais levem mais de dezenas de segundos, a experiência se tornará extremamente ruim. As consultas podem, até mesmo, atingir o tempo limite.

Junto com o desempenho da fonte subjacente, preste atenção à carga colocada na origem. A carga afeta o desempenho. Cada usuário que abre um relatório compartilhado e cada bloco de dashboard que é atualizado enviam, pelo menos, uma consulta por visual à fonte subjacente. Esse fato exige que a fonte possa processar uma carga de consulta como essa, mantendo um desempenho razoável.

### <a name="security-implications-when-combining-data-sources"></a>Implicações de segurança ao combinar fontes de dados

É possível usar várias fontes de dados em um modelo do DirectQuery, assim como ao importar dados, usando o recurso [Modelos compostos](desktop-composite-models.md). Ao usar várias fontes de dados, é importante entender como os dados são movidos entre as fontes de dados subjacentes e as [implicações de segurança](desktop-composite-models.md#security-implications) que isso gera.

### <a name="limited-data-transformations"></a>Transformações de dados limitadas

Da mesma forma, há limitações nas transformações de dados que podem ser aplicadas no Editor de Consultas. Com os dados importados, um conjunto sofisticado de transformações pode ser aplicado com facilidade para limpar e remodelar os dados antes de usá-los para criar visuais, como analisar documentos JSON ou dinamizar dados de uma coluna para um formato de linha. Essas transformações são mais limitadas no DirectQuery.

Primeiro, ao se conectar a uma fonte OLAP como o SAP Business Warehouse, nenhuma transformação poderá ser definida e todo o modelo externo será obtido da fonte. Para fontes relacionais como o SQL Server, ainda é possível definir um conjunto de transformações por consulta, mas essas transformações são limitadas por questões de desempenho.

Qualquer uma dessas transformações precisará ser aplicada em cada consulta à fonte subjacente, ao invés de uma vez a cada atualização de dados, de modo que elas fiquem limitadas às transformações que possam ser convertidas razoavelmente em uma só consulta nativa. Se você usar uma transformação que seja muito complexa, receberá um erro que indicará que ela precisará ser excluída ou o modelo precisará ser alternado para importação.

Além disso, a consulta resultante da caixa de diálogo **Obter Dados** ou do Editor de Consultas será usada em uma subseleção dentro das consultas geradas e enviada para recuperar os dados necessários para um visual. A consulta definida no Editor de Consultas precisará ser válida nesse contexto. Em particular, não é possível usar uma consulta com expressões de tabela comuns nem uma que invoque procedimentos armazenados.

### <a name="modeling-limitations"></a>Limitações de modelagem

O termo *modelagem*, nesse contexto, significa o ato de refinar e enriquecer os dados brutos, como parte da criação de um relatório que os utiliza. Os exemplos incluem:

* Definir relações entre tabelas
* Adicionar novos cálculos (colunas calculadas e medidas)
* Renomear e ocultar colunas e medidas
* Definir hierarquias
* Definir a formatação, a ordem de classificação e o resumo padrão de uma coluna
* Agrupar ou realizar clustering de valores

Ao usar o DirectQuery, muitos desses enriquecimentos de modelo ainda poderão ser feitos e, certamente, ainda haverá o princípio de que os dados brutos estarão sendo enriquecidos para aprimorar o consumo posterior. No entanto, há algumas funcionalidades de modelagem que não estão disponíveis ou que são limitadas ao usar o DirectQuery. Geralmente, as limitações são aplicadas para evitar problemas de desempenho. O conjunto de limitações que são comuns a todas as fontes do DirectQuery é listado aqui. Limitações adicionais podem se aplicar a fontes individuais, conforme descrito em [Próximas etapas](#next-steps).

* **Nenhuma hierarquia de datas interna:** Ao importar dados, cada coluna de data/datetime também terá uma hierarquia de data interna disponível por padrão. Por exemplo, se uma tabela de ordens de vendas estiver sendo importada, incluindo uma coluna **OrderDate** e, em seguida, após o uso de **OrderDate** em um visual, será possível escolher o nível apropriado (ano, mês, dia) a ser usado. Essa hierarquia de data interna não está disponível ao usar o DirectQuery. Se houver uma tabela **Date** disponível na fonte subjacente, como é comum em muitos data warehouses, as funções de inteligência de dados temporais do DAX poderão ser usadas normalmente.
* **Suporte para data/hora com precisar apenas até os segundos:** ao usar colunas de hora em seu conjunto de dados, o Power BI emite apenas consultas para a origem subjacente até o nível de detalhe dos segundos. As consultas não são enviadas à fonte do DirectQuery durante milissegundos. Remova essa parte das horas das colunas de origem.
* **Limitações em colunas calculadas:** as colunas calculadas são limitadas a serem intra-linha e, sendo assim, só podem fazer referência a valores de outras colunas da mesma tabela, sem o uso de quaisquer funções de agregação. Além disso, as funções escalares DAX, como `LEFT()`, que são permitidas, são limitadas às funções que podem ser enviadas por push para a fonte subjacente. As funções variam de acordo com as funcionalidades exatas da origem. As funções para as quais não há suporte não são listadas no preenchimento automático durante a criação do DAX em uma coluna calculada e resultam em um erro caso sejam usadas.
* **Não há suporte para as funções DAX pai-filho:** No modo DirectQuery, não é possível usar a família de funções `DAX PATH()` que geralmente processam estruturas pai-filho, como plano de contas ou hierarquias de funcionários.
* **Não há suporte para tabelas calculadas:** não há suporte para a capacidade de definir uma tabela calculada usando uma expressão DAX no modo DirectQuery.
* **Filtragem de relacionamentos:** Para obter informações sobre a filtragem bidirecional, confira [Filtragem cruzada bidirecional](https://download.microsoft.com/download/2/7/8/2782DF95-3E0D-40CD-BFC8-749A2882E109/Bidirectional%20cross-filtering%20in%20Analysis%20Services%202016%20and%20Power%20BI.docx). Este white paper apresenta exemplos no contexto do SQL Server Analysis Services. Os pontos fundamentais aplicam-se igualmente ao Power BI.
* **Sem Clustering:** ao usar o DirectQuery, não é possível usar a funcionalidade Clustering para localizar grupos automaticamente.

### <a name="reporting-limitations"></a>Limitações de relatórios

Quase todos os recursos de relatórios têm suporte para modelos do DirectQuery. Sendo assim, desde que a fonte subjacente ofereça um nível adequado de desempenho, o mesmo conjunto de visualizações poderá ser usado. Há algumas limitações importantes em algumas das outras funcionalidades oferecidas no serviço do Power BI depois que um relatório é publicado:

* **Não há suporte para Insights Rápidos:** Os Insights Rápidos do Power BI pesquisam diferentes subconjuntos do conjunto de dados durante a aplicação de um conjunto de algoritmos sofisticados para descobrir insights que possam ser interessantes. Considerando a necessidade de consultas de desempenho muito alto, essa funcionalidade não está disponível em conjuntos de dados que usam o DirectQuery.
* **Não há suporte para P e R:** as P e R do Power BI permitem explorar dados usando recursos intuitivos em idioma natural e receber as respostas na forma de quadros e gráficos. No entanto, atualmente, não há suporte para ela em conjuntos de dados que usam o DirectQuery.
* **O uso de Explorar no Excel provavelmente resultará em desempenho insatisfatório:** explore os dados usando a funcionalidade Explorar no Excel em um conjunto de dados. Essa abordagem permite a criação de Tabelas Dinâmicas e Gráficos Dinâmicos no Excel. Embora haja suporte para essa funcionalidade em conjuntos de dados que usam o DirectQuery, o desempenho será geralmente mais lento do que na criação de visuais no Power BI e, portanto, se o uso do Excel for importante para os cenários, esse fato deverá ser considerado em sua decisão de usar o DirectQuery.

### <a name="security"></a>Segurança

Conforme discutido anteriormente neste artigo, um relatório no DirectQuery sempre usa as mesmas credenciais fixas para se conectar à fonte de dados subjacente depois que ele é publicado no serviço do Power BI. Esse comportamento se aplica ao DirectQuery, não às conexões dinâmicas com o SQL Server Analysis Services, que são diferentes nesse sentido. Imediatamente após a publicação de um relatório do DirectQuery, é necessário configurar as credenciais do usuário que serão usadas. Até que você configure as credenciais, a abertura do relatório no serviço do Power BI resultará em um erro.

Depois que as credenciais do usuário forem fornecidas, elas serão usadas, *seja qual for o usuário que abrirá o relatório*. Dessa forma, isso é exatamente como os dados importados. Cada usuário vê os mesmos dados, a menos que a Segurança em Nível de Linha tenha sido definida como parte do relatório. É necessário dar a mesma atenção ao compartilhamento do relatório, caso haja regras de segurança definidas na fonte subjacente.

### <a name="behavior-in-the-power-bi-service"></a>Comportamento no serviço do Power BI

Esta seção descreve o comportamento de um relatório do DirectQuery no serviço do Power BI, para explicar o grau de carregamento que será colocado na fonte de dados de back-end, dado o número de usuários com os quais o relatório e o dashboard serão compartilhados, a complexidade do relatório e se a Segurança em Nível de Linha foi definida no relatório.

#### <a name="reports--opening-interacting-with-editing"></a>Relatórios – abrir, interagir, editar

Quando um relatório é aberto, todos os visuais da página atualmente visível são atualizados. Cada visual geralmente exige, pelo menos, uma consulta à fonte de dados subjacente. Alguns visuais podem exigir mais de uma consulta. Por exemplo, um visual pode mostrar valores de agregação de duas tabelas de fatos diferentes, conter uma medida mais complexa ou conter os totais de uma medida não aditiva, como Contagem Distinta. O acesso de uma nova página atualiza esses visuais. A atualização envia um novo conjunto de consultas para a fonte subjacente.

Cada interação do usuário no relatório pode resultar na atualização de visuais. Por exemplo, a seleção de outro valor em uma segmentação exige o envio de um novo conjunto de consultas para atualizar todos os visuais afetados. O mesmo é verdadeiro ao clicar em um visual para realizar destaques cruzados de outros visuais ou alterar um filtro.

Da mesma forma, a edição de um novo relatório exige o envio de consultas para cada etapa no caminho para produzir o visual final.

Ocorre o cache dos resultados. A atualização de um visual é instantânea se exatamente os mesmos resultados foram obtidos recentemente. Se a Segurança em Nível de Linha não estiver definida, esses caches não serão compartilhados entre os usuários.

#### <a name="dashboard-refresh"></a>Atualização do dashboard

Visuais individuais ou páginas inteiras podem ser fixados como blocos no dashboard. Os blocos baseados nos conjuntos de dados do DirectQuery são atualizados automaticamente de acordo com um agendamento. Os blocos enviam consultas para a fonte de dados de back-end. Por padrão, os conjuntos de dados são atualizados a cada hora, mas podem ser definidos como parte das configurações do conjunto de dados para ocorrerem entre intervalos semanais e de 15 minutos.

Se nenhuma Segurança em Nível de Linha estiver definida no modelo, cada bloco será atualizado uma vez e os resultados compartilhados entre todos os usuários. Caso contrário, poderá haver um grande efeito multiplicador. Cada bloco exige que as consultas separadas por usuário sejam enviadas para a fonte subjacente.

Um dashboard com 10 blocos, compartilhado com 100 usuários, criado em um conjunto de dados usando o DirectQuery com a Segurança em Nível de Linha e configurado para ser atualizado a cada 15 minutos, fará com que, pelo menos, 1.000 consultas sejam enviadas a cada 15 minutos à fonte de back-end.

Preste atenção especial ao uso da Segurança em Nível de Linha e da configuração do agendamento de atualização.

#### <a name="time-outs"></a>Tempos limite

Um tempo limite de quatro minutos é aplicado a consultas individuais no serviço do Power BI. As consultas que levam mais tempo do que isso falharão. Conforme enfatizado anteriormente, recomendamos que você use o DirectQuery para fontes que fornecem desempenho de consulta quase interativo. Esse limite tem como finalidade evitar problemas de tempos de execução excessivamente longos.

### <a name="other-implications"></a>Outras implicações

Algumas outras implicações gerais do uso do DirectQuery são as seguintes:

* **Se os dados forem alterados, será necessário fazer a atualização para garantir que os dados mais recentes sejam mostrados:** Considerando o uso dos caches, não há nenhuma garantia de que o visual sempre mostre os dados mais recentes. Por exemplo, um visual pode mostrar as transações do dia anterior. Devido à alteração de uma segmentação, ela pode ser atualizada para mostrar as transações dos últimos dois dias. As transações podem incluir transações recentes, recém-recebidas. Se a segmentação for retornada ao valor original, isso fará com que ela mostre novamente o valor armazenado em cache obtido anteriormente.

  A seleção de **Atualizar** limpa todos os caches e atualiza todos os visuais na página para mostrar os dados mais recentes.

* **Se os dados forem alterados, não haverá nenhuma garantia de consistência entre os visuais:** visuais diferentes, na mesma página ou em páginas diferentes, podem ser atualizados em diferentes momentos. Se os dados da fonte subjacente forem alterados, não haverá nenhuma garantia de que cada visual mostrará os dados exatamente no mesmo ponto de tempo. Na verdade, considerando que, às vezes, mais de uma consulta é necessária para um só visual, por exemplo, para obter os detalhes e os totais, não há nenhuma garantia de consistência, mesmo em um só visual. Garantir essa consistência exige a sobrecarga da atualização de todos os visuais sempre que qualquer visual é atualizado, em conjunto com o uso de recursos caros como o isolamento do instantâneo na fonte de dados subjacente.

  Esse problema pode ser atenuado em grande parte selecionando **Atualizar** novamente para atualizar todos os visuais da página. Mesmo com o uso do modo de importação, há um problema semelhante para garantir a consistência com a importação de dados de mais de uma tabela.

* **A atualização no Power BI Desktop é necessária para refletir as mudanças nos metadados:** Depois que um relatório for publicado, a opção **Atualizar** atualizará os visuais do relatório. Se o esquema da fonte subjacente for alterado, essas alterações não serão aplicadas automaticamente para alterar os campos disponíveis na lista de campos. Se tabelas ou colunas forem removidas da fonte subjacente, isso poderá resultar em uma falha de consulta após a atualização. A abertura do relatório no Power BI Desktop e a escolha de **Atualizar** atualizará os campos no modelo para refletir as alterações.

* **Limite de 1 milhão de linhas retornadas em qualquer consulta:** há um limite fixo de 1 milhão de linhas colocadas no número de linhas que podem ser retornadas em qualquer consulta individual para a fonte subjacente. Esse limite geralmente não tem nenhuma implicação prática e os próprios visuais não exibirão essa quantidade de pontos. No entanto, o limite pode ocorrer nos casos em que o Power BI não otimiza por completo as consultas enviadas e há um resultado intermediário sendo solicitado que excede o limite. Isso pode ocorrer durante a criação de um visual, no caminho para um estado final mais razoável. Por exemplo, a inclusão de **Customer** e **TotalSalesQuantity** alcançará esse limite se houver mais de 1 milhão de clientes, até que algum filtro seja aplicado.

  O erro retornado será: "O conjunto de resultados de uma consulta a uma fonte de dados externa excedeu o tamanho máximo permitido de '1.000.000' linhas."

* **Não é possível alterar do modo de importação para o modo DirectQuery:** Embora seja possível alternar um modelo do modo DirectQuery para usar o modo de importação, todos os dados necessários precisam ser importados. Também não é possível alternar de volta, principalmente, devido ao conjunto de recursos sem suporte no modo DirectQuery. Os modelos do DirectQuery em fontes multidimensionais, como o SAP BW, também não podem ser alternados do DirectQuery para importação, devido ao tratamento diferente das medidas externas.

## <a name="directquery-in-the-power-bi-service"></a>DirectQuery no serviço do Power BI

Há suporte para todas as fontes no Power BI Desktop. Algumas fontes também estão disponíveis diretamente no serviço do Power BI. Por exemplo, é possível que um usuário empresarial use o Power BI para se conectar aos respectivos dados no Salesforce e obtenha um dashboard imediatamente, sem usar o Power BI Desktop.

Apenas duas das fontes habilitadas do DirectQuery estão disponíveis diretamente no serviço:

* Spark
* SQL Data Warehouse do Azure

No entanto, recomendamos que qualquer uso do DirectQuery nessas duas fontes seja iniciado no Power BI Desktop. O motivo é que, quando a conexão é feita inicialmente no serviço do Power BI, muitas limitações básicas serão aplicadas. Embora o ponto de partida tenha sido fácil, no serviço do Power BI, há limitações no aprimoramento posterior do relatório resultante. Por exemplo, não é possível criar cálculos nem usar muitos recursos analíticos ou, até mesmo, atualizar os metadados para refletir as alterações no esquema subjacente.

## <a name="guidance-for-using-directquery-successfully"></a>Diretrizes para usar o DirectQuery com êxito

Se você pretende usar o DirectQuery, esta seção fornece algumas diretrizes de alto nível de como garantir o sucesso. As diretrizes desta seção são derivadas das implicações do uso do DirectQuery descritas neste artigo.

### <a name="back-end-data-source-performance"></a>Desempenho da fonte de dados de back-end

Confirme se os visuais simples são atualizados em um tempo razoável. Um tempo de atualização deverá ocorrer dentro de 5 segundos para que a experiência interativa seja razoável. Se os visuais estiverem levando mais de 30 segundos, é muito provável que outros problemas ocorrerão após a publicação do relatório. Esses problemas podem tornar a solução impraticável.

Se as consultas estiverem lentas, examine as consultas que estão sendo enviadas à fonte subjacente e o motivo do desempenho da consulta. Este artigo não aborda a grande variedade de melhores práticas de otimização de banco de dados em todo o conjunto de possíveis fontes subjacentes. No entanto, ele aborda as práticas padrão de banco de dados aplicáveis à maioria das situações:

* As relações baseadas em colunas de inteiros geralmente têm melhor desempenho do que junções em colunas de outros tipos de dados.
* Os índices apropriados devem ser criados. A criação de índice geralmente significa o uso de índices de repositório de coluna nas fontes que dão suporte a eles, por exemplo, o SQL Server.
* Todas as estatísticas necessárias na fonte devem ser atualizadas.

### <a name="model-design-guidance"></a>Diretrizes de design de modelo

Ao definir o modelo, considere o uso destas diretrizes:

* **Evite consultas complexas no Editor de Consultas.** O Editor de Consultas converte uma consulta complexa em uma só consulta SQL. A consulta individual é exibida na subseleção de cada consulta enviada a essa tabela. Se essa consulta for complexa, poderá resultar em problemas de desempenho em todas as consultas enviadas. A consulta SQL real de um conjunto de etapas pode ser obtida através da seleção da última etapa no Editor de Consultas e a escolha de **Exibir Consulta Nativa** no menu de contexto.
* **Mantenha as medidas simples.** Pelo menos, inicialmente, recomendamos limitar as medidas a agregações simples. Em seguida, se as medidas tiverem um desempenho satisfatório, medidas mais complexas poderão ser definidas, atentando-se, porém, ao desempenho de cada uma delas.
* **Evite relações em colunas calculadas.** Essas diretrizes são relevantes para bancos de dados em que você precisa fazer junções de várias colunas. Atualmente, o Power BI não permite que uma relação seja baseada em várias colunas como a FK/PK. A solução alternativa comum é concatenar as colunas usando uma coluna calculada e basear a junção nessa coluna. Embora essa solução alternativa seja razoável para dados importados, para o DirectQuery, ela resulta em uma junção em uma expressão. Esse resultado geralmente impede o uso de qualquer índice e gera um baixo desempenho. A única solução alternativa é realmente materializar as várias colunas em uma única coluna no banco de dados subjacente.
* **Evite relações em colunas uniqueidentifier.** O Power BI não dá suporte nativo ao tipo de dados `uniqueidentifier`. A definição de uma relação entre colunas do tipo `uniqueidentifier` resulta em uma consulta com uma junção envolvendo uma conversão. Novamente, essa abordagem geralmente resulta em um baixo desempenho. Até que esse caso seja especificamente otimizado, a única solução alternativa seria materializar colunas de um tipo alternativo no banco de dados subjacente.
* **Ocultar a coluna to em relações.** A coluna *to* em relações é normalmente a chave primária na tabela *to*. Essa coluna deve estar oculta. Se estiver oculta, ela não será exibida na lista de campos e não poderá ser usada em visuais. Geralmente, as colunas em que as relações se baseiam são, na verdade, *colunas do sistema*, por exemplo, chaves alternativas em um data warehouse. É sempre uma boa prática ocultar essas colunas. Caso a coluna tenha significado, introduza uma coluna calculada que seja visível e que tenha uma expressão simples de ser igual à chave primária, como seguinte exemplo:

  ```sql  
      ProductKey_PK   (Destination of a relationship, hidden)
      ProductKey (= [ProductKey_PK],   visible)
      ProductName
      ...
  ```

* **Examine todos os usos de colunas calculadas e alterações de tipo de dados.** O uso dessas funcionalidades não é necessariamente prejudicial. Elas resultam nas consultas enviadas à fonte subjacente contendo expressões em vez de referências simples a colunas. Isso novamente pode resultar em uma não utilização de índices.
* **Evite usar filtragem cruzada bidirecional em relacionamentos.** O uso de filtragem cruzada bidirecional pode levar a instruções de consulta que não têm um bom desempenho.
* **Experimente com a configuração *Pressupor integridade referencial*.** A configuração Pressupor Integridade Referencial em relações permite que as consultas usem instruções `INNER JOIN` em vez de `OUTER JOIN`. Essas diretrizes geralmente aprimoram o desempenho de consulta, embora elas dependam das especificações da fonte de dados.
* **Não use a filtragem de dados relativos no Editor de Consultas.** É possível definir a filtragem de data relativa no Editor de Consultas. Por exemplo, para filtrar as linhas em que a data esteja nos últimos 14 dias.
  
  ![Filtrar as linhas dos últimos 14 dias](media/desktop-directquery-about/directquery-about_02.png)
  
  No entanto, esse filtro é convertido em um filtro com base na data fixada, como no momento em que a consulta foi criada. Esse resultado pode ser observado na exibição da consulta nativa.
  
  ![Filtrar as linhas na consulta SQL nativa](media/desktop-directquery-about/directquery-about_03.png)
  
  Provavelmente, esse resultado não é o que você desejava. Para garantir que o filtro seja aplicado com base na data, no momento em que o relatório é executado, aplique o filtro no relatório como um Filtro de Relatório. Atualmente, essa abordagem é feita com a criação de uma coluna calculada, o cálculo do número de dias atrás, o uso da função `DAX DATE()` e, em seguida, o uso dessa coluna calculada em um filtro.

### <a name="report-design-guidance"></a>Diretrizes de design de relatório

Ao criar um relatório usando uma conexão do DirectQuery, siga estas diretrizes:

* **Considere o uso das opções de Redução de consulta:** o Power BI fornece opções no relatório para enviar menos consultas e desabilitar algumas interações que resultam em uma experiência insatisfatória, caso as consultas resultantes levem muito tempo para serem executadas. Para acessar essas opções no Power BI Desktop, acesse **Arquivo** > **Opções e configurações** > **Opções** e selecione **Redução de consulta**.

   ![Opções de redução de consulta](media/desktop-directquery-about/directquery-about_03b.png)

    Marcar seleções da caixa em **Redução de consulta** permite desativar o realce cruzado em todo o relatório. Exiba também um botão **Aplicar** para seleções de filtro ou segmentações. Essa abordagem permite que você faça muitas seleções de filtro e segmentação antes de aplicá-las. Nenhuma consulta é enviada até que você selecione o botão **Aplicar** na segmentação. As seleções em seguida podem ser usadas para filtrar os dados.

    Essas opções se aplicam ao relatório durante a sua interação com ele no Power BI Desktop. Essas opções também se aplicam quando os usuários consomem o relatório no serviço do Power BI.

* **Aplique filtros primeiro:** aplique todos os filtros adequados sempre no início da criação de um visual. Por exemplo, em vez de arrastar em **TotalSalesAmount** e **ProductName** e, em seguida, filtrar para determinado ano, aplique o filtro em **Year** logo no início. Cada etapa da criação de um visual envia uma consulta. Embora seja possível fazer outra alteração antes que a primeira consulta seja concluída, essa abordagem ainda mantém uma carga desnecessária na fonte subjacente. Ao aplicar os filtros no início, as consultas intermediárias serão geralmente menos dispendiosas. Além disso, a não aplicação dos filtros no início pode resultar no limite de 1 milhão de linhas.
* **Limite o número de visuais em uma página:** ao abrir uma página ou alterar uma segmentação ou um filtro no nível da página, todos os visuais de uma página são atualizados. Também há um limite no número de consultas enviadas em paralelo. Conforme o número de visuais aumenta, alguns dos visuais serão atualizados em série, aumentando o tempo necessário para atualizar a página inteira. Por esse motivo, recomendamos que você limite o número de visuais em uma página individual e, em vez disso, tenha um número maior de páginas mais simples.
* **Considere desativar a interação entre visuais:** Por padrão, as visualizações em uma página de relatório podem ser usadas para filtro cruzado e realce cruzado de outras visualizações na página. Por exemplo, ao selecionar **1999** no gráfico de pizza, é feito o realce cruzado do gráfico de colunas para mostrar as vendas por categoria para **1999**.
  
  ![Vários visuais com filtragem cruzada e realce cruzado](media/desktop-directquery-about/directquery-about_04.png)
  
  A filtragem cruzada e o realce cruzado no DirectQuery exigem que as consultas sejam enviadas para a fonte subjacente. A interação deverá ser desativada se o tempo necessário para responder às seleções dos usuários for excessivamente longo. Você pode desativar essa interação. Desative a interação para todo o relatório, conforme descrito anteriormente nas opções de redução de consulta, ou caso a caso. Para obter mais informações, confira [Como os visuais realizam filtragem cruzada entre si em um relatório do Power BI](consumer/end-user-interactions.md).

Além das sugestões anteriores, cada uma das seguintes funcionalidades de relatório pode causar problemas de desempenho:

* **Filtros de medida:** os visuais que contêm medidas ou agregações de colunas podem conter filtros nessas medidas. Por exemplo, o gráfico a seguir mostra **SalesAmount** por **Categoria**, mas só incluindo as categorias com mais de **20 milhões** em vendas.
  
  ![Visual mostrando medidas que contêm filtros](media/desktop-directquery-about/directquery-about_05.png)
  
  Esta abordagem faz com que duas consultas sejam enviadas à fonte subjacente:
  
  * A primeira consulta recupera as categorias que atendem à condição **SalesAmount** superior a 20 milhões.
  * Em seguida, a segunda consulta recupera os dados necessários para o visual, incluindo as categorias que atendem à condição na cláusula `WHERE`.
  
  Essa abordagem geralmente funciona bem se houver centenas ou milhares de categorias, como neste exemplo. O desempenho poderá diminuir se o número de categorias for muito maior. A consulta falha para mais de um milhão de categorias que atendem à condição. O limite de 1 milhão de linhas foi abordado anteriormente.

* **Filtros TopN:** filtros avançados podem ser definidos para realizar a filtragem somente dos valores N superiores ou inferiores classificados de acordo com uma medida. Por exemplo, os filtros podem incluir as 10 principais categorias do visual anterior. Novamente, essa abordagem fará com que duas consultas sejam enviadas à fonte subjacente. No entanto, a primeira consulta retornará todas as categorias da fonte subjacente e, em seguida, os TopN serão determinados com base nos resultados retornados. Dependendo da cardinalidade da coluna envolvida, essa abordagem poderá causar problemas de desempenho ou falhas de consulta, devido ao limite de 1 milhão de linhas.

* **Valor mediano:** Geralmente, qualquer agregação, como `Sum` ou `Count Distinct`, é enviada por push à fonte subjacente. No entanto, isso não é verdadeiro para a mediana, pois, geralmente, não há suporte para essa agregação na fonte de subjacente. Nesses casos, os dados de detalhes são recuperados da fonte subjacente e a mediana é calculada com base nos resultados retornados. Essa abordagem é razoável quando a mediana deve ser calculada em relação a um número relativamente pequeno de resultados. Ocorrerão problemas de desempenho ou falhas de consulta devido ao limite de 1 milhão de linhas se a cardinalidade for grande. Por exemplo, a **Mediana da População do País** pode ser razoável, ao contrário da **Mediana do Preço de Vendas**.

* **Filtros de texto avançados (_contém_ e similares):** ao filtrar uma coluna de texto, a filtragem avançada permite o uso de filtros como *contém* e *começa com*, por exemplo. Esses filtros certamente poderão causar degradação no desempenho para algumas fontes de dados. Especificamente, o filtro padrão *contains* não deverá ser usado se houver necessidade de uma correspondência exata. Embora os resultados possam ser os mesmos, dependendo dos dados reais, o desempenho poderá ser drasticamente diferente devido ao uso de índices.

* **Segmentações de dados de seleção múltipla:** por padrão, as segmentações de dados permitem que seja realizada apenas uma única seleção. Permitir seleções múltiplas em filtros pode causar alguns problemas de desempenho, pois o usuário seleciona um conjunto de itens na segmentação. Por exemplo, se o usuário selecionar os 10 produtos de interesse, cada nova seleção resultará no envio de consultas para a origem. Embora o usuário possa selecionar o próximo item antes da conclusão da consulta, essa abordagem resulta em uma carga extra na fonte subjacente.

* **Considere desativar os totais nos visuais:** por padrão, tabelas e matrizes exibem totais e subtotais. Em muitos casos, as consultas separadas devem ser enviadas para a fonte de dados subjacente para obter os valores para esses totais. Esse fato se aplica sempre ao usar a agregação *DistinctCount* ou em todos os casos ao usar o DirectQuery no SAP BW ou no SAP HANA. Esses totais devem ser desativados usando o painel **Formato**.

### <a name="maximum-number-of-connections-option-for-directquery"></a>Opção de número máximo de conexões do DirectQuery

Você pode definir o número máximo de conexões abertas pelo DirectQuery para cada fonte de dados subjacente, que controla o número de consultas enviadas simultaneamente para cada fonte de dados.

O DirectQuery abre um número máximo padrão de 10 conexões simultâneas. Você pode alterar o número máximo do arquivo atual no Power BI Desktop. Acesse **Arquivo** > **Opções e Configurações** > **Opções**. Na seção **Arquivo Atual** no painel esquerdo, selecione **DirectQuery**.

![Como definir o número máximo de conexões do DirectQuery](media/desktop-directquery-about/directquery-about_05b.png)

A configuração só é habilitada quando há, pelo menos, uma fonte do DirectQuery no relatório atual. O valor se aplica a todas as fontes do DirectQuery e às novas fontes do DirectQuery adicionadas ao mesmo relatório.

O aumento de **Máximo de conexões por fonte de dados** garante que mais consultas, até o número máximo especificado, possam ser enviadas para a fonte de dados subjacente. Essa abordagem é útil quando muitos visuais estão em uma só página ou muitos usuários acessam um relatório ao mesmo tempo. Depois que o número máximo de conexões é atingido, as consultas seguintes são colocadas na fila até que uma conexão fique disponível. O aumento desse limite resulta em mais carga na fonte subjacente e, portanto, a configuração não garante a melhoria do desempenho geral.

Depois que um relatório é publicado, o número máximo de consultas simultâneas enviadas para a fonte de dados subjacente também depende dos limites fixados. Os limites dependem do ambiente de destino no qual o relatório é publicado. Diferentes ambientes, como o Power BI, o Power BI Premium ou o Servidor de Relatórios do Power BI, podem impor limites distintos.

### <a name="diagnosing-performance-issues"></a>Diagnosticar problemas de desempenho

Esta seção descreve como diagnosticar problemas de desempenho ou obter informações mais detalhadas para permitir que os relatórios sejam otimizados.

Recomendamos que você inicie o diagnóstico de problemas de desempenho no Power BI Desktop, em vez de no serviço do Power BI. Problemas de desempenho geralmente se baseiam no desempenho da fonte subjacente. Você pode identificar e diagnosticar problemas com mais facilidade no ambiente mais isolado do Power BI Desktop. Essa abordagem inicialmente elimina alguns componentes, como o gateway do Power BI. Se os problemas de desempenho estiverem ausentes do Power BI Desktop, investigue as especificidades do relatório no serviço do Power BI. O [Performance Analyzer](desktop-performance-analyzer.md) é uma ferramenta útil para identificar problemas ao longo desse processo.

Da mesma forma, recomendamos primeiro tentar isolar os problemas em um visual individual, em vez de muitos visuais em uma página.

Digamos que as etapas nos parágrafos anteriores desta seção tenham sido removidas. Agora temos um só visual em uma página do Power BI Desktop que ainda está lento. Use o [Performance Analyzer](desktop-performance-analyzer.md) para determinar as consultas enviadas para a fonte subjacente pelo Power BI Desktop. Também é possível ver as informações de rastreamento e diagnóstico que podem ser emitidas pela fonte de dados subjacente. Os rastreamentos também podem conter detalhes úteis de como a consulta foi executada e como ela pode ser aprimorada.

Além disso, mesmo na ausência desses rastreamentos na fonte, é possível ver as consultas enviadas pelo Power BI, juntamente com os respectivos tempos de execução, conforme descrito na seção a seguir.

#### <a name="determining-the-queries-sent-by-power-bi-desktop"></a>Determinando as consultas enviadas pelo Power BI Desktop

Por padrão, o Power BI Desktop registra eventos durante uma determinada sessão em um arquivo de rastreamento chamado *FlightRecorderCurrent.trc*.

Para algumas fontes do DirectQuery, esse log inclui todas as consultas enviadas para a fonte de dados subjacente. As fontes restantes do DirectQuery serão incluídas no futuro. As seguintes fontes enviam consultas ao log:

* SQL Server
* Banco de Dados SQL do Azure
* SQL Data Warehouse do Azure
* Oracle
* Teradata
* SAP HANA

O arquivo de rastreamento pode ser encontrado na pasta *AppData* do usuário atual:

*\<User>\AppData\Local\Microsoft\Power BI Desktop\AnalysisServicesWorkspaces*

Para acessar essa pasta, no Power BI Desktop, selecione **Arquivo** > **Opções e configurações** > **Opções** e, em seguida, selecione **Diagnóstico**. A seguinte caixa de diálogo é exibida:

![Um link para abrir a pasta de rastreamentos](media/desktop-directquery-about/directquery-about_06.png)

Ao selecionar **Abrir a pasta de rastreamentos/despejo de memória** em **Opções de Diagnóstico**, a seguinte pasta é aberta: *\<User>\AppData\Local\Microsoft\Power BI Desktop\Traces*.

Ao navegar até a pasta pai dessa pasta, a pasta que contém *AnalysisServicesWorkspaces* é exibida, que conterá uma pasta do workspace para cada instância aberta do Power BI Desktop. Essas pastas são nomeadas com um sufixo de inteiro, como *AnalysisServicesWorkspace2058279583*.

Dentro dessa pasta, há uma pasta *\\Data*. Ela contém o arquivo de rastreamento *FlightRecorderCurrent.trc* da sessão atual do Power BI. A pasta de workspace correspondente é excluída quando a sessão associada do Power BI Desktop é encerrada.

Os arquivos de rastreamento podem ser lidos com a ferramenta *SQL Server Profiler*. Obtenha-o como parte do download gratuito do [SQL Server Management Studio](https://msdn.microsoft.com/library/mt238290.aspx).

Depois de baixar e instalar o SQL Server Management Studio, execute o SQL Server Profiler.

![SQL Server Profiler](media/desktop-directquery-about/directquery-about_07.png)

Para abrir o arquivo de rastreamento, execute as seguintes etapas:

1. No SQL Server Profiler, selecione **Arquivo** > **Abrir** > **Arquivo de rastreamento**.

1. Insira o caminho até o arquivo de rastreamento da sessão atualmente aberta do Power BI, como abaixo: *C:\Users\<user>\AppData\Local\Microsoft\Power BI Desktop\AnalysisServicesWorkspaces\AnalysisServicesWorkspace2058279583\Data*.

1. Abra *FlightRecorderCurrent.trc*.

Todos os eventos da sessão atual são exibidos. Um exemplo anotado é mostrado aqui, destacando os grupos de eventos. Cada grupo tem os seguintes eventos:

* Um evento `Query Begin` e `Query End`, que representam o início e o término de uma consulta DAX gerada pela interface do usuário, por exemplo, de um visual ou do preenchimento de uma lista de valores na interface do usuário do filtro.
* Um ou mais pares de eventos `DirectQuery Begin` e `DirectQuery End`, que representam uma consulta enviada à fonte de dados subjacente, como parte da avaliação da consulta DAX.

Várias consultas DAX podem ser executadas em paralelo, de modo que os eventos de diferentes grupos posam ser intercalados. O valor da `ActivityID` pode ser usado para determinar quais eventos pertencem ao mesmo grupo.

![SQL Server Profiler com os eventos Query Begin e Query End](media/desktop-directquery-about/directquery-about_08.png)

Outras colunas de interesse são as seguintes:

* **TextData:** os detalhes textuais do evento. Para eventos `Query Begin/End`, o detalhe é a consulta DAX. Para eventos `DirectQuery Begin/End`, o detalhe é a consulta SQL enviada à fonte subjacente. O **TextData** do evento atualmente selecionado também é exibido na região, na parte inferior.
* **EndTime:** a hora em que o evento foi concluído.
* **Duration:** o tempo, em milissegundos, necessário para executar a consulta DAX ou SQL.
* **Error:** indica se ocorreu um erro e, nesse caso, o evento também será exibido em vermelho.

Na imagem acima, algumas das colunas menos interessantes foram reduzidas, a fim de permitir que outras colunas sejam vistas com mais facilidade.

Recomendamos a seguinte abordagem para capturar um rastreamento e ajudar a diagnosticar um possível problema de desempenho:

* Abra uma sessão individual do Power BI Desktop, para evitar a confusão de ter várias pastas de workspace.
* Execute o conjunto de ações desejadas no Power BI Desktop. Inclua algumas ações adicionais, para garantir que os eventos desejados sejam liberados no arquivo de rastreamento.
* Abra o SQL Server Profiler e examine o rastreamento, conforme descrito anteriormente. Lembre-se de que o fechamento do Power BI Desktop exclui o arquivo de rastreamento. Além disso, as ações adicionais no Power BI Desktop não são exibidas imediatamente. O arquivo de rastreamento deve ser fechado e reaberto para ver os novos eventos.
* Mantenha as sessões individuais razoavelmente pequenas, talvez 10 segundos de ações, não centenas. Essa abordagem facilita a interpretação do arquivo de rastreamento. Também há um limite no tamanho do arquivo de rastreamento. Em sessões longas, há a possibilidade de remoção dos eventos iniciais.

#### <a name="understanding-the-form-of-query-sent-by-power-bi-desktop"></a>Noções básicas sobre a forma da consulta enviada pelo Power BI Desktop

O formato geral das consultas criadas e enviadas pelo Power BI Desktop usa subseleções de cada uma das tabelas referenciadas. A consulta do Editor de Consultas define a subseleção. Por exemplo, suponha as seguintes tabelas TPC-DS no SQL Server:

![Tabelas do TPC-DS no SQL Server](media/desktop-directquery-about/directquery-about_09.png)

Considere a consulta a seguir:

![Uma consulta de exemplo](media/desktop-directquery-about/directquery-about_10.png)

Essa consulta tem como resultado o seguinte visual:

![Resultado visual de uma consulta](media/desktop-directquery-about/directquery-about_11.png)

A atualização desse visual resultará na consulta SQL mostrada aqui. Como você pode ver, há três subseleções para `Web Sales`, `Item` e `Date_dim`, e cada uma retorna todas as colunas na respectiva tabela, embora, na realidade, apenas quatro colunas sejam referenciadas pelo visual. Essas consultas nas subseleções que estão sombreadas são exatamente o resultado das consultas definidas no Editor de Consultas. O uso de subseleções dessa maneira não afetou o desempenho das fontes de dados compatíveis com o DirectQuery até o momento. Fontes de dados como o SQL Server simplesmente otimizam as referências para as outras colunas.

O Power BI emprega esse padrão porque a consulta SQL usada pode ser fornecida diretamente pelo analista. Ela é usada "conforme fornecida", sem que haja uma tentativa de reescrevê-la.

![Consulta SQL usada conforme fornecido](media/desktop-directquery-about/directquery-about_12.png)

## <a name="next-steps"></a>Próximas etapas

Este artigo descreve aspectos do DirectQuery que são comuns entre todas as fontes de dados. Há determinados detalhes que são específicos a fontes individuais. Confira os seguintes artigos que abordam fontes específicas:

* [DirectQuery e SAP HANA](desktop-directquery-sap-hana.md)
* [DirectQuery e SAP BW](desktop-directquery-sap-bw.md)

Para obter mais informações sobre o DirectQuery, confira o seguinte recurso:

* [Fontes de dados com suporte do DirectQuery](desktop-directquery-data-sources.md)
