---
title: Noções básicas do DAX no Power BI Desktop
description: Noções básicas do DAX no Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 10/21/2019
ms.author: davidi
LocalizationGroup: Model your data
ms.openlocfilehash: fcff0bf1d6c68b9bdb000855f4984b3664b882c1
ms.sourcegitcommit: 6272c4a0f267708ca7d38a45774f3bedd680f2d6
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/06/2020
ms.locfileid: "73877901"
---
# <a name="dax-basics-in-power-bi-desktop"></a>Noções básicas do DAX no Power BI Desktop
Este artigo é destinado aos novos usuários do Power BI Desktop. Ele fornece uma introdução rápida e fácil sobre como você pode usar expressões DAX (Data Analysis Expressions) para resolver vários problemas de cálculo básico e análise de dados. Examinaremos algumas informações conceituais, uma série de tarefas que você pode concluir e uma verificação de conhecimentos para testar o que aprendeu. Depois de ler este artigo, você deve ter uma boa compreensão dos conceitos fundamentais mais importantes no DAX.

## <a name="what-is-dax"></a>O que é DAX?
O DAX é uma coleção de funções, operadores e constantes que podem ser usados em uma fórmula, ou expressão, para calcular e retornar um ou mais valores. Resumindo, o DAX ajuda você a criar novas informações de dados já presentes em seu modelo.

## <a name="why-is-dax-so-important"></a>Por que DAX é tão importante?
É fácil criar um arquivo do Power BI Desktop e importar alguns dados para ele. Você pode até mesmo criar relatórios que mostrem informações valiosas sem usar nenhuma fórmula DAX. Mas e se você precisar analisar o percentual de crescimento em diferentes categorias de produto e para intervalos de datas diferentes? Ou você precisa calcular o crescimento ano a ano comparado às tendências do mercado? As fórmulas DAX oferecem essa e outras funcionalidades importantes também. Aprender a criar fórmulas DAX eficientes ajudará você a tirar o máximo proveito de seus dados. Quando obtém as informações de que precisa, você pode começar a resolver problemas comerciais reais, que afetam o seu resultado final. Esse é o poder do Power BI, e o DAX ajudará você a aproveitá-lo.

## <a name="prerequisites"></a>Pré-requisitos
Você pode já estar familiarizado com a criação de fórmulas no Microsoft Excel. Esse conhecimento será útil na compreensão do DAX, mas mesmo se você não tiver experiência com fórmulas do Excel, os conceitos descritos aqui ajudarão você a começar a criar fórmulas DAX e resolver problemas do BI do mundo real, imediatamente.

Nós nos concentraremos em entender as fórmulas DAX usadas em cálculos, mais especificamente, em medidas e colunas calculadas. Você já deve estar familiarizado com o uso do Power BI Desktop para importar dados e adicionar campos a um relatório, além dos conceitos fundamentais de [medidas](desktop-measures.md) e [colunas calculadas](desktop-calculated-columns.md).

### <a name="example-workbook"></a>Pasta de trabalho de exemplo

A melhor maneira de aprender a usar o DAX é criar algumas fórmulas básicas, usá-las com alguns dados reais e ver você mesmo os resultados. As tarefas e os exemplos aqui descritos usam o [arquivo Amostra de Vendas da Contoso para o Power BI Desktop](https://download.microsoft.com/download/4/6/A/46AB5E74-50F6-4761-8EDB-5AE077FD603C/Contoso%20Sales%20for%20Power%20BI%20Designer.zip). Esse é o mesmo arquivo de exemplo usado no artigo [Tutorial: criar suas próprias medidas no Power BI Desktop](desktop-tutorial-create-measures.md). 

## <a name="lets-begin"></a>Vamos começar!
Estruturaremos nosso entendimento sobre o DAX em relação a três conceitos fundamentais: *sintaxe*, *funções* e *contexto*. Há outros conceitos importantes no DAX, mas o entendimento desses três conceitos fornecerá a melhor base na qual você poderá desenvolver suas habilidades com o DAX.

### <a name="syntax"></a>Sintaxe
Antes de criar suas próprias fórmulas, vamos dar uma olhada na sintaxe das fórmulas DAX. A sintaxe inclui os vários elementos que compõem uma fórmula, ou mais resumidamente, o modo como a fórmula é escrita. Por exemplo, esta é uma fórmula DAX simples para uma medida:

![Sintaxe da fórmula DAX](media/desktop-quickstart-learn-dax-basics/qsdax_1_syntax.png)

Esta fórmula inclui os seguintes elementos de sintaxe:

**A.** O nome da medida, **Total Sales**.

**B.** O operador de sinal de igual ( **=** ), que indica o início da fórmula. Quando calculada, ela retornará um resultado.

**C.** A função DAX **SUM**, que soma todos os números da coluna **Sales[SalesAmount]** . Você aprenderá mais sobre as funções mais tarde.

**D.** Os parênteses **()** , que envolvem uma expressão que contém um ou mais argumentos. Todas as funções exigem pelo menos um argumento. Um argumento transmite um valor para uma função.

**E.** A tabela referenciada, **Sales**.

**F.** A coluna referenciada, **[SalesAmount]** , na tabela Sales. Com este argumento, a função SUM sabe em que coluna deve agregar uma SUM.

Ao tentar entender uma fórmula DAX, geralmente, é útil decompor cada um dos elementos em uma linguagem que você usa e fala todos os dias. Por exemplo, você pode ler esta fórmula como:

> *Para a medida chamada Total Sales, calcule (=) a SUM dos valores na coluna [SalesAmount], na tabela Sales.*
> 
> 

Quando adicionada a um relatório, essa medida calcula e retorna valores somando as quantidades de vendas para cada um dos outros campos que são incluídos, por exemplo, “Cell Phones in the USA”.

Você deve estar pensando: "Por acaso essa medida não é equivalente a uma adição manual do campo SalesAmount ao meu relatório?" Bem, sim. Mas há um bom motivo para criar nossa própria medida que soma os valores do campo SalesAmount: podemos usar isso como um argumento em outras fórmulas. Isso pode parecer um pouco confuso agora, mas conforme você desenvolver suas habilidades com a fórmula DAX, conhecer essa medida tornará suas fórmulas e seu modelo mais eficientes. Na verdade, você verá mais tarde a medida Total Sales aparecendo como um argumento em outras fórmulas.

Vamos dar uma olhada em mais alguns pontos sobre essa fórmula. Em especial, vale lembrar que introduzimos uma função, [SUM](https://msdn.microsoft.com/library/ee634387.aspx). Funções são fórmulas gravadas previamente, que tornam mais fácil fazer cálculos complexos e manipulações com números, datas, hora, texto e muito mais. Você aprenderá mais sobre as funções posteriormente.

Veja também que o nome da coluna [SalesAmount] era precedido pela tabela Sales, à qual a coluna pertence. Esse nome é conhecido como um nome de coluna totalmente qualificado, pois inclui o nome da coluna precedido pelo nome da tabela. As colunas referenciadas na mesma tabela não exigem que o nome da tabela seja incluído na fórmula, o que pode criar fórmulas longas que referenciam muitas colunas mais curtas e fáceis de serem lidas. No entanto, é uma boa prática incluir o nome da tabela nas fórmulas de medida, mesmo quando estão na mesma tabela.

> [!NOTE]
> Se um nome de tabela contiver espaços, palavras-chave reservadas ou caracteres não permitidos, você precisará colocar o nome da tabela entre aspas simples. Além disso, você precisará colocar os nomes de tabela entre aspas se o nome contiver quaisquer caracteres fora do conjunto de caracteres alfanuméricos ANSI, independentemente de sua localidade dar ou não suporte ao conjunto de caracteres.
> 
> 

É importante que suas fórmulas tenham a sintaxe correta. Na maioria dos casos, se a sintaxe não estiver correta, um erro de sintaxe será retornado. Em outros casos, a sintaxe pode estar correta, mas os valores retornados podem não ser o que você esperava. O editor do DAX no Power BI Desktop inclui um recurso de sugestões, usado para criar fórmulas sintaticamente corretas, ajudando você a selecionar os elementos corretos.

Vamos criar uma fórmula simples. Essa tarefa ajudará você a entender melhor a sintaxe da fórmula e como o recurso de sugestões na barra de fórmulas pode ajudá-lo.

### <a name="task-create-a-measure-formula"></a>Tarefa: criar uma fórmula de medida

1. [Baixe](https://download.microsoft.com/download/4/6/A/46AB5E74-50F6-4761-8EDB-5AE077FD603C/Contoso%20Sales%20for%20Power%20BI%20Designer.zip) e abra o arquivo Amostra de Vendas da Contoso para o Power BI Desktop. 
    
2. Na exibição Relatório, na lista de campos, clique com o botão direito do mouse na tabela **Sales** e, em seguida, selecione **Nova Medida**.
    
3. Na barra de fórmulas, substitua **Measure** inserindo um novo nome de medida, *Previous Quarter Sales*.
    
4. Após o sinal de igual, digite as primeiras letras *CAL* e, em seguida, clique duas vezes na função que você deseja usar. Nesta fórmula, você deseja usar a função **CALCULATE**.

   Você usará a função CALCULATE para filtrar os valores que desejamos somar por um argumento que transmitimos à função CALCULATE. Isso é o que chamamos de aninhar funções. A função CALCULATE tem pelo menos dois argumentos. O primeiro é a expressão a ser avaliada e o segundo é um filtro.
   
5. Após o parêntese de abertura *(* para a função **CALCULATE**, digite *SUM* seguido por outro parêntese de abertura *(* . 

   A seguir, passaremos um argumento para a função SUM.

6. Comece a digitar *Sal* e selecione **Sales [SalesAmount]** , seguido por um parêntese de fechamento *)* . 

   Esse é o primeiro argumento de expressão para a função CALCULATE.
    
7. Digite uma vírgula ( *,* ) seguida por um espaço para especificar o primeiro filtro e, em seguida, digite *PREVIOUSQUARTER*. 
    
   Você usará a função de time intelligence PREVIOUSQUARTER para filtrar os resultados SUM pelo trimestre anterior.
    
8. Depois da abertura de parênteses *(* , para a função PREVIOUSQUARTER, digite *Calendar[DateKey]* .
    
   A função PREVIOUSQUARTER tem um argumento, uma coluna contendo um intervalo contíguo de datas. Em nosso caso, essa é a coluna DateKey na tabela de Calendário.
    
9. Feche os dois argumentos passados para as funções PREVIOUSQUARTER e CALCULATE digitando dois parênteses de fechamento *))* .
    
   Sua fórmula agora deve ter essa aparência:
    
   **Previous Quarter Sales = CALCULATE(SUM(Sales[SalesAmount]), PREVIOUSQUARTER(Calendar[DateKey]))**
    
10. Selecione a marca de seleção ![Ícone de marca de seleção](media/desktop-quickstart-learn-dax-basics/qsdax_syntax_taskcheckmark.png) na barra de fórmulas ou pressione Enter para validar a fórmula e adicioná-la ao modelo.

Você conseguiu! Você acabou de criar uma medida complexa usando o DAX, e não estamos falando de uma medida fácil. O que essa fórmula fará é calcular o total de vendas do trimestre anterior, dependendo dos filtros aplicados em um relatório. Por exemplo, se colocamos SalesAmount e nossa nova medida Previous Quarter Sales em um gráfico e, em seguida, adicionamos Year e QuarterOfYear como Segmentação de Dados, obtemos algo semelhante a isto:

![Gráfico de Previous Quarter Sales e SalesAmount](media/desktop-quickstart-learn-dax-basics/qsdax_3_chart.png)

Você acabou de conhecer vários aspectos importantes das fórmulas DAX: 

- Essa fórmula incluiu duas funções. [PREVIOUSQUARTER](https://msdn.microsoft.com/library/ee634385.aspx), uma função de inteligência de dados temporais, está aninhada como um argumento passado para [CALCULATE](https://msdn.microsoft.com/library/ee634825.aspx), uma função de filtro. 

   Fórmulas DAX podem conter até 64 funções aninhadas. É improvável que uma fórmula chegue a conter tantas funções aninhadas. Na verdade, uma fórmula como essa é difícil de ser criada e depurada; além disso, provavelmente, ela não será muito rápida.

- Nesta fórmula, você também usou filtros. Filtros restringem o que será calculado. Nesse caso, você selecionou um filtro como um argumento, que é, na verdade, o resultado de outra função. Você aprenderá mais sobre filtros posteriormente.

- Você usou a função CALCULATE. Essa é uma das funções mais avançadas no DAX. Conforme você criar modelos e fórmulas mais complexas, provavelmente, usará essa função muitas vezes. Embora uma abordagem detalhada da função CALCULATE não esteja no escopo deste artigo, fique atento a ela conforme seu conhecimento sobre o DAX aumentar.

### <a name="syntax-quickquiz"></a>Teste rápido sobre sintaxe
1. Qual é a função desse botão na barra de fórmulas?
   
   > ![Seleção de botão](media/desktop-quickstart-learn-dax-basics/qsdax_2_syntaxquiz.png)
   > 
   > 
2. O que sempre está em torno de um nome de coluna em uma fórmula DAX?

As respostas são fornecidas no final deste artigo.

### <a name="functions"></a>Funções
Funções são fórmulas predefinidas que realizam cálculos usando valores específicos, chamados argumentos, em uma determinada ordem ou estrutura. Argumentos podem ser outras funções, outra fórmula, expressão, referências de coluna, números, texto, valores lógicos como TRUE ou FALSE, ou constantes.

O DAX inclui as seguintes categorias de funções: [Date and Time](https://msdn.microsoft.com/library/ee634786.aspx), [Time Intelligence](https://msdn.microsoft.com/library/ee634763.aspx), [Information](https://msdn.microsoft.com/library/ee634552.aspx), [Logical](https://msdn.microsoft.com/library/ee634365.aspx), [Mathematical](https://msdn.microsoft.com/library/ee634241.aspx), [Statistical](https://msdn.microsoft.com/library/ee634822.aspx), [Text](https://msdn.microsoft.com/library/ee634938.aspx), [Parent/Child](https://msdn.microsoft.com/library/mt150102.aspx) e [Other](https://msdn.microsoft.com/library/mt150101.aspx). Se já estiver familiarizado com as funções em fórmulas do Excel, muitas das funções no DAX podem parecer semelhantes para você. No entanto, as funções DAX são exclusivas nos seguintes aspectos:

* Uma função DAX sempre referencia uma coluna ou uma tabela completa. Se desejar usar apenas valores específicos de uma tabela ou coluna, é possível adicionar filtros à fórmula.
* Se precisar personalizar cálculos linha por linha, o DAX fornece funções que permitem usar o valor da linha atual ou um valor relacionado como um tipo de argumento, para realizar cálculos que variam de acordo com o contexto. Você aprenderá mais sobre o contexto posteriormente.
* O DAX inclui várias funções que retornam uma tabela em vez de um valor. A tabela não é exibida, mas é usada para fornecer entrada para outras funções. Por exemplo, é possível recuperar uma tabela e, em seguida, contar os valores distintos contidos nela, ou calcular somas dinâmicas em diferentes colunas ou tabelas filtradas.
* O DAX inclui uma variedade de funções de inteligência de dados temporais. Estas funções permitem definir ou selecionar intervalos de datas e executar cálculos dinâmicos, baseados nesses intervalos. Por exemplo, é possível comparar somas em períodos paralelos.
* O Excel tem uma função popular, VLOOKUP. As funções DAX não usam uma célula ou intervalo de células como referência, como a VLOOKUP faz no Excel. As funções DAX usam uma coluna ou tabela como referência. Lembre-se de que, no Power BI Desktop, você está trabalhando com um modelo de dados relacionais. Procurar valores em outra tabela é fácil e, na maioria dos casos, você não precisa criar nenhuma fórmula.
  
  Como você pode ver, as funções no DAX podem ajudar você a criar fórmulas avançadas. Nós abordamos apenas as noções básicas das funções. Conforme desenvolver suas habilidades com o DAX, você criará fórmulas usando muitas funções diferentes. Um dos melhores lugares para obter detalhes sobre cada uma das funções DAX é a [Referência de funções DAX](https://msdn.microsoft.com/query-bi/dax/data-analysis-expressions-dax-reference).

### <a name="functions-quickquiz"></a>Teste rápido sobre funções
1. Uma função sempre faz referência a que?
2. Uma fórmula pode conter mais de uma função?
3. Que categoria de funções você usaria para concatenar duas cadeias de caracteres de texto em uma cadeia de caracteres?

As respostas são fornecidas no final deste artigo.

### <a name="context"></a>Contexto
Contexto é um dos conceitos do DAX mais importantes para se compreender. Há dois tipos de contexto no DAX: o contexto de linha e o contexto de filtro. Primeiro, vamos dar uma olhada no contexto de linha.

**Contexto de linha**

É mais fácil pensar no contexto de linha como a linha atual. Ele se aplica sempre que uma fórmula tem uma função que utiliza filtros para identificar uma única linha em uma tabela. A função aplicará inerentemente um contexto de linha a cada linha da tabela que essa função está filtrando. Esse tipo de contexto de linha geralmente se aplica a medidas.

**Contexto de filtro**

O contexto do filtro é um pouco mais difícil de entender do que o contexto de linha. Você pode pensar com facilidade no contexto de filtro como: um ou mais filtros aplicados em um cálculo para determinar um resultado ou valor.

O contexto de filtro não existe no lugar do contexto de linha; em vez disso, eles são aplicados em conjunto. Por exemplo, para restringir ainda mais os valores a serem incluídos em um cálculo, você pode aplicar um contexto de filtro que especifica o contexto de linha e determinado valor (filtro) nesse contexto de linha.

O contexto de filtro é visto facilmente em seus relatórios. Por exemplo, ao adicionar TotalCost a uma visualização e, em seguida, Year e Region, você está definindo um contexto de filtro que seleciona um subconjunto de dados com base em um determinado ano e região.

Por que o contexto de filtro é tão importante no DAX? Visto que, embora o contexto de filtro possa ser aplicado mais facilmente pela adição de campos a uma visualização, ele também pode ser aplicado em uma fórmula DAX pela definição de um filtro com funções como ALL, RELATED, FILTER, CALCULATE, por relações e por outras medidas e colunas. Por exemplo, vamos dar uma olhada na seguinte fórmula em uma medida chamada Store Sales:

![Medida Store Sales](media/desktop-quickstart-learn-dax-basics/qsdax_4_context.png)

Para entender melhor essa fórmula podemos decompô-la, de modo muito similar ao que ocorre em outras fórmulas.

Esta fórmula inclui os seguintes elementos de sintaxe:

**A.** O nome da medida, **Store Sales**.

**B.** O operador de sinal de igual ( **=** ), que indica o início da fórmula.

**C.** A função **CALCULATE**, que avalia uma expressão, como um argumento, em um contexto que é modificado pelos filtros especificados.

**D.** Os parênteses **()** , que envolvem uma expressão que contém um ou mais argumentos.

**E.** Uma medida **[Total Sales]** na mesma tabela como uma expressão. A medida Total Sales tem a fórmula: =SUM(Sales[SalesAmount]).

**F.** Uma vírgula ( **,** ), que separa o primeiro argumento da expressão do argumento do filtro.

**G.** A coluna referenciada totalmente qualificada, **Channel[ChannelName]** . Esse é o nosso contexto de linha. Cada linha dessa coluna especifica um canal, como Store ou Online.

**H.** O valor específico, **Store**, como um filtro. Esse é o nosso contexto de filtro.

Esta fórmula garante que somente os valores de vendas definidos pela medida Total Sales sejam calculados, apenas para as linhas da coluna Channel[ChannelName], com o valor *Store* usado como um filtro.

Como você pode imaginar, a capacidade de definir o contexto de filtro em uma fórmula apresenta funcionalidades incríveis e poderosas. A capacidade de referenciar apenas um valor específico em uma tabela relacionada é apenas um exemplo disso. Não se preocupe se você não entender totalmente o contexto, logo de imediato. Ao criar suas próprias fórmulas, você entenderá melhor o contexto e a razão pela qual ele é tão importante no DAX.

### <a name="context-quickquiz"></a>Teste rápido de contexto
1. Quais são os dois tipos de contexto?
2. O que é o contexto de filtro?
3. O que é o contexto de linha?

As respostas são fornecidas no final deste artigo.

## <a name="summary"></a>Resumo
Agora que você tem uma noção básica dos conceitos mais importantes do DAX, você pode começar a criar fórmulas DAX para medidas por conta própria. DAX pode ser realmente um pouco difícil de aprender, mas há muitas fontes de aprendizado disponíveis para você. Depois de ler este artigo e experimentar algumas das suas próprias fórmulas, você pode aprender mais sobre outros conceitos e fórmulas de DAX que podem ajudá-lo a resolver seus próprios problemas empresariais. Há muitos recursos do DAX disponíveis para você: o mais importante é a [Referência ao DAX (Expressões de Análise de Dados)](https://msdn.microsoft.com/library/gg413422.aspx).

Como o DAX já existe há vários anos em outras ferramentas de BI da Microsoft, como modelos de tabela do Analysis Services e do Power Pivot, há muitas informações úteis disponíveis. Você encontrará mais informações em white papers, livros e blogs tanto da Microsoft quanto de profissionais de BI de vanguarda. O [Wiki do Centro de Recursos do DAX no TechNet](https://social.technet.microsoft.com/wiki/contents/articles/dax-resource-center.aspx) também é um ótimo lugar para começar.

### <a name="quickquiz-answers"></a>Respostas do Teste Rápido
Sintaxe:

1. Valida e insere a medida no modelo.
2. Colchetes [].

Funções:

1. Uma tabela e uma coluna.
2. Sim. Uma fórmula pode conter até 64 funções aninhadas.
3. [Funções de texto](https://msdn.microsoft.com/library/ee634938.aspx).

Contexto:

1. Contexto de linha e contexto de filtro.
2. Um ou mais filtros em um cálculo que determina um único valor.
3. A linha atual.

