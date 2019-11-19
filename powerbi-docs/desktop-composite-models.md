---
title: Usar modelos compostos no Power BI Desktop
description: Criar modelos de dados com várias conexões de dados e relações muitos para muitos no Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 08/19/2019
ms.author: davidi
LocalizationGroup: Transform and shape data
ms.openlocfilehash: c79994f2144dfe019c3ac10a51230d17b75b542e
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/09/2019
ms.locfileid: "73876568"
---
# <a name="use-composite-models-in-power-bi-desktop"></a>Usar modelos compostos no Power BI Desktop

Anteriormente no Power BI Desktop, quando você usava um DirectQuery em um relatório, nenhuma outra conexão de dados, seja DirectQuery ou Importação, era permitida para esse relatório. Com modelos compostos, essa restrição é removida. Um relatório pode incluir perfeitamente as conexões de dados de mais de um DirectQuery ou conexão de Importar dados, em qualquer combinação que você escolher.

![Modelos compostos no Power BI Desktop](media/desktop-composite-models/composite-models_01.png)

O recurso de modelos compostos no Power BI Desktop consiste em três recursos relacionados:

* **Modelos compostos**: permite que um relatório tenha várias conexões de dados, incluindo conexões DirectQuery ou Importação, em qualquer combinação. Este artigo descreve os modelos compostos em detalhes.

* **Relações muitos-para-muitos**: com *modelos compostos*, você pode estabelecer *relações muitos-para-muitos* entre as tabelas. Esta abordagem remove os requisitos de valores exclusivos nas tabelas. Ela também remove as soluções alternativas anteriores, como introduzir novas tabelas somente para estabelecer relações. Para mais informações, confira [Relações muitos para muitos no Power BI Desktop (versão prévia)](desktop-many-to-many-relationships.md).

* **Modo de armazenamento**: agora você pode especificar quais visuais exigem uma consulta para fontes de dados de back-end. Visuais que não exigem uma consulta serão importados, mesmo se forem baseados no DirectQuery. Esse recurso ajuda a melhorar o desempenho e reduzir a carga de back-end. Antes, mesmo visuais simples como as segmentações iniciavam consultas enviadas para fontes de back-end. Para mais informações, confira [Modo de armazenamento no Power BI Desktop (versão prévia)](desktop-storage-mode.md).


## <a name="use-composite-models"></a>Usar modelos compostos

Com modelos compostos, você pode se conectar a uma variedade de fontes de dados ao usar o Power BI Desktop ou o serviço do Power BI. Você pode fazer essas conexões de dados de algumas maneiras:

* Importar dados para o Power BI, que é a maneira mais comum de obter dados.
* Conectar-se diretamente aos dados no repositório fonte original usando o DirectQuery. Para saber mais sobre o DirectQuery, confira [Usar o DirectQuery no Power BI](desktop-directquery-about.md).

Quando você usa o DirectQuery, os *modelos compostos* tornam possível criar um modelo do Power BI (como um único arquivo *.pbix* do Power BI Desktop) que execute um destes procedimentos ou ambos:

* Combina dados de uma ou mais fontes de DirectQuery.
* Combina dados de fontes de DirectQuery e importação de dados.

Por exemplo, usando modelos compostos, você pode criar um modelo que combina os seguintes tipos de dados:

* Dados de vendas de um data warehouse corporativo.
* Dados de meta de vendas de um banco de dados departamental do SQL Server.
* Dados importados de uma planilha. 

Um modelo que combina dados de mais de uma origem de DirectQuery ou que combina o DirectQuery com a importação de dados é chamado de *modelo composto*.


É possível criar relações entre tabelas, como sempre, mesmo as tabelas provenientes de outras origens. Todas as relações de origem cruzada são criadas com uma cardinalidade de *muitos para muitos*, independentemente da cardinalidade atual. É possível alterá-las para "um para muitos", "muitos para um" ou "um para um". Independentemente da cardinalidade definida, as relações de origem cruzada têm comportamentos diferentes em que não é possível usar as funções DAX para recuperar valores no lado "um" do lado "muitos". Também é possível ver o impacto de desempenho em comparação com as relações "muitos para muitos" na mesma origem.

> [!NOTE]
> No contexto de modelos compostos, todas as tabelas importadas efetivamente são uma única fonte, independentemente da fonte de dados subjacente real da qual são importadas.   

## <a name="example-of-a-composite-model"></a>Exemplo de um modelo composto

Para obter um exemplo de um *modelo composto*, considere a possibilidade de um relatório que se conectou a um depósito de dados corporativos no SQL Server usando o DirectQuery. Nesse caso, o data warehouse contém dados de *Vendas por País*, *Trimestre* e *Bicicleta (produto)* , conforme mostrado na seguinte imagem:

![Exibição de relações para modelos compostos](media/desktop-composite-models/composite-models_04.png)

Neste ponto, você pode criar visuais simples usando os campos dessa fonte. Por exemplo, a imagem a seguir mostra o total de vendas por *ProductName*, para um trimestre selecionado. 

![Visual com base nos dados](media/desktop-composite-models/composite-models_05.png)

Porém, e se você tiver dados em uma planilha do Excel do Office sobre o gerente atribuído a cada produto, juntamente com a prioridade de marketing? Se você quiser exibir o *Valor de Vendas* por *Gerente de Produto*, talvez não seja possível adicionar esses dados locais ao data warehouse corporativo. Ou então, pode levar meses, na melhor das hipóteses. 

Talvez seja possível importar os dados de vendas do data warehouse, em vez de usar o DirectQuery. E os dados de vendas poderiam ser combinados aos dados que você importou da planilha. No entanto, essa abordagem não é razoável, pelos motivos que levam ao uso do DirectQuery antes de mais nada. As razões podem incluir:

* Alguma combinação das regras de segurança impostas na fonte subjacente.
* A necessidade de ser capaz de exibir os dados mais recentes.
* A enorme escala dos dados. 

É aí que entram os modelos compostos. Os modelos compostos permitem que você se conecte ao data warehouse usando o DirectQuery e use GetData para fontes adicionais. Neste exemplo, primeiro vamos estabelecer a conexão do DirectQuery para o data warehouse corporativo. Usamos GetData, escolhemos o Excel e navegamos até a planilha que contém os dados locais. Por fim, podemos importar a planilha que contém os *Nomes de Produtos*, o *Gerente de Vendas* atribuído e a *Prioridade*.  

![Janela do Navegador](media/desktop-composite-models/composite-models_06.png)

Na lista **Campos**, você pode ver duas tabelas: a tabela original *Bicicleta* do SQL Server e uma nova tabela **ProductManagers**. A nova tabela contém os dados importados do Excel. 

![Exibição de campos de tabelas](media/desktop-composite-models/composite-models_07.png)

Da mesma forma, na exibição **Relacionamento** no Power BI Desktop, agora podemos ver uma tabela adicional chamada **ProductManagers**. 

![Exibição de relações de tabelas](media/desktop-composite-models/composite-models_08.png)

Agora, precisamos relacionar essas tabelas às outras tabelas no modelo. Como sempre, criamos um relacionamento entre a tabela **Bicicleta** do SQL Server e a tabela importada **ProductManagers**. Ou seja, o relacionamento entre *Bike[ProductName]* e *ProductManagers[ProductName]* . Conforme discutido anteriormente, todas as relações que passam pela origem têm a cardinalidade padrão *muitos para muitos*. 

![A janela "Criar relacionamento"](media/desktop-composite-models/composite-models_09.png)

Agora que estabelecemos esse relacionamento, ele é mostrado na exibição **Relacionamento** no Power BI Desktop, como se poderia esperar.

![Exibição de novo relacionamento](media/desktop-composite-models/composite-models_10.png)

Agora podemos criar elementos visuais usando qualquer um dos campos na lista **Campos**. Essa abordagem combina perfeitamente os dados de várias fontes. Por exemplo, o total de *SalesAmount* de cada *Gerente de Produto* é exibido na seguinte imagem: 

![O painel Campos](media/desktop-composite-models/composite-models_11.png)

O exemplo a seguir exibe um caso comum de uma tabela *dimensão*, como *Produto* ou *Cliente*, que é estendida com alguns dados extras importados de outro lugar. Também é possível fazer com que as tabelas usem o DirectQuery para se conectar a várias fontes. Para continuar o exemplo, imagine que *SalesTargets* por *País* e *Período* sejam armazenados em um banco de dados de departamento separado. Como de costume, você pode usar *GetData* para se conectar aos dados, conforme mostrado na seguinte imagem: 

![A janela Navegador](media/desktop-composite-models/composite-models_12.png)

Como fizemos anteriormente, podemos criar relacionamentos entre a nova tabela e outras tabelas no modelo e criar elementos visuais que combinam os dados da tabela. Vamos examinar novamente a exibição **Relacionamentos**, em que estabelecemos novos relacionamentos:

![Exibição de relacionamentos com muitas tabelas](media/desktop-composite-models/composite-models_13.png)

A imagem a seguir baseia-se em novos dados e relacionamentos que criamos. O visual na parte inferior esquerda mostra o total de *Valor de Vendas* versus *Destino*, e o cálculo de variância mostra a diferença. Os dados de *Valor de Vendas* e o *Destino* são provenientes de dois bancos de dados do SQL Server diferentes. 

![Imagem mostrando mais dados](media/desktop-composite-models/composite-models_14.png)

## <a name="set-the-storage-mode"></a>Definir o modo de armazenamento

Cada tabela em um modelo composto tem um modo de armazenamento que indica se a tabela é baseada no DirectQuery ou em importação. O modo de armazenamento pode ser exibido e modificado no painel **Propriedade**. Para exibir o modo de armazenamento, clique com o botão direito do mouse em uma tabela na lista **Campos** e selecione **Propriedades**. A imagem a seguir mostra o modo de armazenamento da tabela **SalesTargets**.

![Configuração do modo de armazenamento](media/desktop-composite-models/composite-models_15.png)

O modo de armazenamento também pode ser visto na dica de ferramenta de cada tabela.

![Dica de ferramenta que exibe o modo de armazenamento](media/desktop-composite-models/composite-models_16.png)

Para qualquer arquivo do Power BI Desktop (um arquivo *.pbix*) que contém algumas tabelas de DirectQuery e algumas tabelas de importação, a barra de status mostra um modo de armazenamento chamado **Misto**. Você pode clicar no termo na barra de status e alternar facilmente todas as tabelas para Importação.

Para saber mais sobre o modo de armazenamento, confira [Modo de armazenamento no Power BI Desktop (versão prévia)](desktop-storage-mode.md).  

> [!NOTE]
> Você pode usar o modo de armazenamento *Misto* no Power BI Desktop e no serviço do Power BI.

## <a name="calculated-tables"></a>Tabelas calculadas

Você pode adicionar tabelas calculadas a um modelo que usa o DirectQuery. As DAX (Expressões de Análise de Dados) que definem a tabela calculada podem fazer referência a tabelas importadas, a tabelas do DirectQuery ou a uma combinação das duas. 

As tabelas calculadas sempre são importadas, e seus dados são atualizados quando você atualiza as tabelas. Se uma tabela calculada se refere a uma tabela do DirectQuery, visuais que fazem referência à tabela DirectQuery sempre mostram os valores mais recentes na fonte subjacente. Como alternativa, os visuais que fazem referência à tabela calculada mostram os valores no momento em que a tabela calculada foi atualizada pela última vez.

## <a name="security-implications"></a>Implicações de segurança 

Os modelos compostos têm algumas implicações de segurança. Uma consulta enviada a uma fonte de dados pode incluir valores de dados que foram recuperados de outra origem. No exemplo anterior, o visual que mostra *Valor de Vendas* por *Gerente de Produto* envia uma consulta SQL ao banco de dados relacional **Vendas**. Essa consulta SQL pode conter os nomes dos *Gerentes de Produto* e seus respectivos *Produtos*. 

![Script mostrando implicações de segurança](media/desktop-composite-models/composite-models_17.png)

Consequentemente, as informações armazenadas na planilha agora estão incluídas em uma consulta que é enviada ao banco de dados relacional. Se essas informações são confidenciais, você deve considerar as implicações de segurança. Em particular, considere os seguintes pontos:

* Qualquer administrador de banco de dados que pode exibir rastreamentos ou logs de auditoria pode exibir essas informações, mesmo sem permissões para os dados em sua fonte original. Neste exemplo, o administrador precisaria de permissões para o arquivo do Excel.

* As configurações de criptografia para cada fonte devem ser consideradas. Convém evitar a recuperação de informações de uma fonte por meio de uma conexão criptografada e sua inclusão acidental em uma consulta que é enviada a outra fonte por meio de uma conexão não criptografada. 

Para confirmar que você considerou todas as implicações de segurança, o Power BI Desktop exibe uma mensagem de aviso quando você cria um modelo composto.  

Por motivos semelhantes, tenha cuidado ao abrir um arquivo do Power BI Desktop enviado de uma fonte não confiável. Se o arquivo contém modelos compostos, as informações que alguém recupera de uma fonte usando as credenciais do usuário que abre o arquivo são enviadas para outra fonte de dados como parte da consulta. As informações podem ser exibidas pelo autor mal-intencionado do arquivo do Power BI Desktop. Portanto, quando você abre inicialmente um arquivo do Power BI Desktop que contém várias fontes, o Power BI Desktop exibe um aviso. O aviso é semelhante ao que é exibido quando você abre um arquivo que contém consultas SQL nativas.  

## <a name="performance-implications"></a>Implicações de desempenho  

Ao usar o DirectQuery, você deve sempre considerar desempenho, principalmente para garantir que a fonte de back-end tenha recursos suficientes para fornecer uma boa experiência aos usuários. Uma boa experiência significa que os visuais são atualizados em cinco segundos ou menos. Você também deve seguir o conselho de desempenho do artigo [Usar o DirectQuery no Power BI](desktop-directquery-about.md). 

O uso de modelos compostos gera considerações de desempenho adicionais. Um único visual pode resultar no envio de consultas a várias fontes, o que geralmente passa os resultados de uma consulta para uma segunda fonte. Essa situação pode resultar nas seguintes formas de execução:

* **Uma consulta SQL que inclui um grande número de valores literais**: por exemplo, um visual que solicita o total de *Valor de Vendas* para um conjunto de *Gerentes de Produto* selecionados, primeiro precisará saber quais *Produtos* eram gerenciados pelos gerentes de produto. Essa sequência deve ocorrer antes que o visual envie uma consulta SQL que inclui todas as IDs de produto em uma cláusula *WHERE*.

* **Uma consulta SQL que consulta em um nível mais baixo de granularidade, com os dados agregados localmente**: à medida que o número de *Produtos* que atende aos critérios de filtro de *Gerente de produto* aumenta, pode se tornar ineficiente ou inviável incluir todos os produtos em uma cláusula *WHERE*. Em vez disso, você pode consultar a origem relacional em um nível inferior de *Produto* e agregar os resultados localmente. Se a cardinalidade de *Produtos* exceder um limite de um milhão, a consulta falhará.

* **Várias consultas SQL, uma por grupo por valor**: quando a agregação usa **DistinctCount** e é agrupada por alguma coluna de outra fonte, e se a fonte externa não oferece suporte à passagem eficiente de vários valores literais que definem o agrupamento, é necessário enviar uma consulta SQL por grupo por valor. 

   Por exemplo, um visual que solicita uma contagem distinta de *CustomerAccountNumber* (de tabela do SQL Server) por *Gerente de Produto* (importada de uma planilha) precisa passar os detalhes da tabela *Gerentes de Produto* na consulta enviada ao SQL Server. Em outras fontes (por exemplo, Redshift), essa ação é impraticável. Em vez disso, deve haver uma consulta SQL enviada por *Gerente de Vendas* até um limite prático e, nesse ponto, a consulta falha. 

Cada um desses casos tem suas próprias implicações sobre o desempenho, e os detalhes exatos variam para cada fonte de dados. Embora a cardinalidade das colunas usadas na relação que une as duas fontes permaneça baixa (alguns milhares), o desempenho não deve ser afetado. À medida que a cardinalidade cresce, você deve prestar mais atenção ao impacto sobre o desempenho resultante. Aplique essas diretrizes como uma prática recomendada. 

Além disso, o uso de relações *muitos para muitos* significa que consultas separadas devem ser enviadas à fonte subjacente para cada total ou subtotal nível, em vez de agregar os valores detalhados localmente. Um visual de tabela simples com totais enviaria as duas consultas SQL, em vez de uma. 

## <a name="limitations-and-considerations"></a>Limitações e considerações

Esta versão dos modelos compostos apresenta algumas limitações:

No momento, há suporte para [atualização incremental](service-premium-incremental-refresh.md) somente para modelos compostos conectando-se a fontes de dados SQL, Oracle e Teradata.

As seguintes fontes (multidimensionais) do Live Connect não podem ser usadas com os modelos compostos:

* SAP HANA
* SAP Business Warehouse
* SQL Server Analysis Services
* Conjuntos de dados do Power BI
* Azure Analysis Services

Ao se conectar a essas fontes multidimensionais usando o DirectQuery, não é possível se conectar também à outra fonte do DirectQuery, nem combiná-la com Importar dados.

As limitações existentes do DirectQuery ainda se aplicam ao usar modelos compostos. Muitas dessas limitações agora são por tabela, dependendo do modo de armazenamento dela. Por exemplo, uma coluna calculada em Importar tabela pode se referir a outras tabelas, mas uma coluna calculada em uma tabela do DirectQuery ainda se refere apenas às colunas na mesma tabela. Outras limitações se aplicam ao modelo como um todo se quaisquer das tabelas no modelo forem DirectQuery. Por exemplo, os recursos QuickInsights e P e R não estarão disponíveis em um modelo se qualquer uma das tabelas nele tiver um modo de armazenamento do DirectQuery. 

## <a name="next-steps"></a>Próximas etapas

Para obter mais informações sobre modelos compostos e DirectQuery, confira os seguintes artigos:
* [Relações muitos para muitos no Power BI Desktop](desktop-many-to-many-relationships.md)
* [Modo de armazenamento no Power BI Desktop](desktop-storage-mode.md)
* [Usar DirectQuery no Power BI](desktop-directquery-about.md)
* [Fontes de dados com suporte do DirectQuery no Power BI](desktop-directquery-data-sources.md)

