---
title: Exemplos de expressões no Construtor de Relatórios do Power BI
description: As expressões costumam ser usadas em relatórios paginados do Power BI Report Builder para controlar o conteúdo e a aparência do relatório.
ms.date: 10/21/2019
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.assetid: 87ddb651-a1d0-4a42-8ea9-04dea3f6afa4
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 48e81c91a4555b4c8ea847ddffb1413058bbb152
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/05/2020
ms.locfileid: "78921138"
---
# <a name="expression-examples-in-power-bi-report-builder"></a>Exemplos de expressões no Construtor de Relatórios do Power BI
As expressões costumam ser usadas em relatórios paginados do Power BI Report Builder para controlar o conteúdo e a aparência do relatório. As expressões são escritas no Microsoft Visual Basic e podem usar funções internas, código personalizado, variáveis de grupo e relatório e variáveis definidas pelo usuário. As expressões começam com um sinal de igual (=).   

Este tópico fornece exemplos de expressões que podem ser usadas para tarefas comuns em um relatório.  
  
-   [Funções do Visual Basic](#VisualBasicFunctions) Exemplos de funções de data, cadeia de caracteres, conversão e condicionais do Visual Basic.  
  
-   [Funções de relatório](#ReportFunctions) Exemplos de agregações e outras funções de relatório internas.  
  
-   [Aparência dos dados de relatório](#AppearanceofReportData) Exemplos de alteração da aparência de um relatório.  
  
-   [Propriedades](#Properties) Exemplos de definição das propriedades de item de relatório para controlar o formato ou a visibilidade.  
  
-   [Parâmetros](#Parameters) Exemplos de uso de parâmetros em uma expressão.  
  
-   [Código personalizado](#CustomCode) Exemplos de código personalizado inserido.  
  
Para obter mais informações sobre expressões simples e complexas, nas quais você pode usar expressões, e os tipos de referências que podem ser incluídas em uma expressão, confira os tópicos em [Expressões no Construtor de Relatórios do Power BI](report-builder-expressions.md). 
  
## <a name="functions"></a>Funções  
 Muitas expressões em um relatório contêm funções. Formate dados, aplique lógica e acesse os metadados de relatório usando essas funções. Escreva expressões que usam funções da biblioteca em tempo de execução do Microsoft Visual Basic e dos namespaces `xref:System.Convert` e `xref:System.Math`. Você pode adicionar referências a funções no código personalizado. Use também classes do Microsoft .NET Framework, incluindo `xref:System.Text.RegularExpressions`.  
  
##  <a name="visual-basic-functions"></a><a name="VisualBasicFunctions"></a> Funções do Visual Basic  
 Use funções do Visual Basic para manipular os dados exibidos em caixas de texto ou usados para parâmetros, propriedades ou outras áreas do relatório. Esta seção fornece exemplos que demonstram algumas dessas funções. Para obter mais informações, confira [Membros da Biblioteca de Runtime do Visual Basic](https://go.microsoft.com/fwlink/?LinkId=198941) no MSDN.  
  
 O .NET Framework fornece muitas opções de formato personalizado, por exemplo, para formatos de data específicos. Para saber mais, confira [Tipos de formatação](/dotnet/standard/base-types/formatting-types).  
  
### <a name="math-functions"></a>Funções matemáticas  
  
-   A função **Round** é útil para arredondar números para o inteiro mais próximo. A seguinte expressão arredonda 1,3 para 1:  
  
    ```  
    = Round(1.3)  
    ```  
  
     Escreva também uma expressão para arredondar um valor para um múltiplo especificado, semelhante à função **MRound** no Excel. Multiplique o valor por um fator que cria um inteiro, arredonde o número e, em seguida, divida-o pelo mesmo fator. Por exemplo, para arredondar 1,3 para o múltiplo mais próximo de 0,2 (1,4), use a seguinte expressão:  
  
    ```  
    = Round(1.3*5)/5  
    ```  
  
###  <a name="date-functions"></a><a name="DateFunctions"></a> Funções de data  
  
-   A função **Today** fornece a data atual. Esta expressão pode ser usada em uma caixa de texto para exibir a data no relatório ou em um parâmetro para filtrar os dados com base na data atual.  
  
    ```  
    =Today()  
    ```  
  
-   Use a função **DateInterval** para remover uma parte específica de uma data. Estes são alguns parâmetros **DateInterval** válidos:

    -   DateInterval.Second
    -   DateInterval.Minute
    -   DateInterval.Hour
    -   DateInterval.Weekday
    -   DateInterval.Day
    -   DateInterval.DayOfYear
    -   DateInterval.WeekOfYear
    -   DateInterval.Month
    -   DateInterval.Quarter
    -   DateInterval.Year

    Por exemplo, esta expressão mostrará o número da semana no ano atual da data de hoje:
  
    ```  
    =DatePart(DateInterval.WeekOfYear, today()) 
    ```  
  
-   A função **DateAdd** é útil para fornecer um intervalo de datas com base em um único parâmetro. A expressão a seguir fornece uma data seis meses posterior à data de um parâmetro chamado *StartDate*.  
  
    ```  
    =DateAdd(DateInterval.Month, 6, Parameters!StartDate.Value)  
    ```  
  
-   A função **Year** exibe o ano de uma data específica. Use isso para agrupar datas ou exibir o ano como um rótulo para um conjunto de datas. Esta expressão fornece o ano para determinado grupo de datas de ordem de vendas. A função **Month** e outras funções também podem ser usadas para manipular datas. Para obter mais informações, confira a documentação do Visual Basic.  
  
    ```  
    =Year(Fields!OrderDate.Value)  
    ```  
  
-   Você pode combinar funções em uma expressão para personalizar o formato. A expressão a seguir altera o formato de uma data no formato mês-dia-ano para mês-semana-número da semana. Por exemplo, 12/23/2009 para dezembro, semana 3:  
  
    ```  
    =Format(Fields!MyDate.Value, "MMMM") & " Week " &   
    (Int(DateDiff("d", DateSerial(Year(Fields!MyDate.Value),   
    Month(Fields!MyDate.Value),1), Fields!FullDateAlternateKey.Value)/7)+1).ToString  
    ```  
  
     Quando usada como um campo calculado em um conjunto de dados, esta expressão pode ser usada em um gráfico para agregar valores por semana em cada mês.  
  
-   A expressão a seguir formata o valor SellStartDate como MMM-YY. O campo SellStartDate é um tipo de dados de datetime.  
  
    ```  
    =FORMAT(Fields!SellStartDate.Value, "MMM-yy")  
    ```  
  
-   A expressão a seguir formata o valor SellStartDate como dd/MM/yyyy. O campo SellStartDate é um tipo de dados de datetime.  
  
    ```  
    =FORMAT(Fields!SellStartDate.Value, "dd/MM/yyyy")  
    ```  
  
-   A função **CDate** converte o valor em uma data. A função **Now** retorna um valor de data contendo a data e a hora atuais de acordo com o sistema. **DateDiff** retorna um valor Long especificando o número de intervalos de tempo entre dois valores Date.  
  
     O exemplo a seguir exibe a data de início do ano atual  
  
    ```  
    =DateAdd(DateInterval.Year,DateDiff(DateInterval.Year,CDate("01/01/1900"),Now()),CDate("01/01/1900"))  
    ```  
  
-   O exemplo a seguir exibe a data de início do mês anterior com base no mês atual.  
  
    ```  
    =DateAdd(DateInterval.Month,DateDiff(DateInterval.Month,CDate("01/01/1900"),Now())-1,CDate("01/01/1900"))  
    ```  
  
-   A expressão a seguir gera os anos de intervalo entre SellStartDate e LastReceiptDate. Esses campos estão em dois conjuntos de dados diferentes, DataSet1 e DataSet2.  
  
    ```  
    =DATEDIFF("yyyy", First(Fields!SellStartDate.Value, "DataSet1"), First(Fields!LastReceiptDate.Value, "DataSet2"))  
    ```  
  
-   A função **DatePart** retorna um valor Integer que contém o componente especificado de determinado valor Date. A expressão a seguir retorna o ano para o primeiro valor de SellStartDate em DataSet1. O escopo do conjunto de dados é especificado porque há vários conjuntos de dados no relatório.  
  
    ```  
    =Datepart("yyyy", First(Fields!SellStartDate.Value, "DataSet1"))  
  
    ```  
  
-   A função **DateSerial** retorna um valor Date representando um ano, um mês e um dia especificados, com as informações de hora definidas como meia-noite. O exemplo a seguir exibe a data de término do mês anterior, com base no mês atual.  
  
    ```  
    =DateSerial(Year(Now()), Month(Now()), "1").AddDays(-1)  
    ```  
  
-   As expressões a seguir exibem várias datas com base em um valor de parâmetro de data selecionado pelo usuário.  
  
|Descrição de exemplo|Exemplo|  
|-------------------------|-------------|  
|Ontem|`=DateSerial(Year(Parameters!TodaysDate.Value),Month(Parameters!TodaysDate.Value),Day(Parameters!TodaysDate.Value)-1)`|  
|Dois dias atrás|`=DateSerial(Year(Parameters!TodaysDate.Value),Month(Parameters!TodaysDate.Value),Day(Parameters!TodaysDate.Value)-2)`|  
|Um mês atrás|`=DateSerial(Year(Parameters!TodaysDate.Value),Month(Parameters!TodaysDate.Value)-1,Day(Parameters!TodaysDate.Value))`|  
|Dois meses atrás|`=DateSerial(Year(Parameters!TodaysDate.Value),Month(Parameters!TodaysDate.Value)-2,Day(Parameters!TodaysDate.Value))`|  
|Um ano atrás|`=DateSerial(Year(Parameters!TodaysDate.Value)-1,Month(Parameters!TodaysDate.Value),Day(Parameters!TodaysDate.Value))`|  
|Dois anos atrás|`=DateSerial(Year(Parameters!TodaysDate.Value)-2,Month(Parameters!TodaysDate.Value),Day(Parameters!TodaysDate.Value))`|  
  
###  <a name="string-functions"></a><a name="StringFunctions"></a> Funções de cadeia de caracteres  
  
-   Combine mais de um campo usando operadores de concatenação e constantes do Visual Basic. A seguinte expressão retorna dois campos, cada um em uma linha separada na mesma caixa de texto:  
  
    ```  
    =Fields!FirstName.Value & vbCrLf & Fields!LastName.Value   
    ```  
  
-   Formate datas e números em uma cadeia de caracteres com a função **Format**. A seguinte expressão exibe valores dos parâmetros *StartDate* e *EndDate* no formato de data completa:  
  
    ```  
    =Format(Parameters!StartDate.Value, "D") & " through " &  Format(Parameters!EndDate.Value, "D")    
    ```  
  
     Se a caixa de texto contiver apenas uma data ou um número, você deverá usar a propriedade Format da caixa de texto para aplicar a formatação em vez da função **Format** dentro da caixa de texto.  
  
-   As funções **Right**, **Len** e **InStr** são úteis para retornar uma substring, por exemplo, cortar *DOMÍNIO*\\*nome de usuário* para apenas o nome de usuário. A seguinte expressão retorna a parte da cadeia de caracteres à direita de um caractere de barra invertida (\\) de um parâmetro chamado *User*:  
  
    ```  
    =Right(Parameters!User.Value, Len(Parameters!User.Value) - InStr(Parameters!User.Value, "\"))  
    ```  
  
     A seguinte expressão resulta no mesmo valor que o anterior, usando membros da classe `xref:System.String` do .NET Framework em vez de funções do Visual Basic:  
  
    ```  
    =Parameters!User.Value.Substring(Parameters!User.Value.IndexOf("\")+1, Parameters!User.Value.Length-Parameters!User.Value.IndexOf("\")-1)  
    ```  
  
-   Exiba os valores selecionados de um parâmetro de vários valores. O seguinte exemplo usa a função **Join** para concatenar os valores selecionados do parâmetro *MySelection* em uma única cadeia de caracteres que pode ser definida como uma expressão para o valor de uma caixa de texto em um item de relatório:  
  
    ```  
    = Join(Parameters!MySelection.Value)  
    ```  
  
     O exemplo a seguir faz o mesmo que o exemplo acima, além de exibir uma cadeia de texto antes da lista de valores selecionados.  
  
    ```  
    ="Report for " & JOIN(Parameters!MySelection.Value, " & ")  
  
    ```  
  
-   As funções **Regex** do .NET Framework `xref:System.Text.RegularExpressions` são úteis para alterar o formato de cadeias de caracteres existentes, por exemplo, formatação de um número de telefone. A seguinte expressão usa a função **Replace** para alterar o formato de um número de telefone de dez dígitos em um campo de "*nnn*-*nnn*-*nnnn*" para "(*nnn*) *nnn*-*nnnn*":  
  
    ```  
    =System.Text.RegularExpressions.Regex.Replace(Fields!Phone.Value, "(\d{3})[ -.]*(\d{3})[ -.]*(\d{4})", "($1) $2-$3")  
    ```  
  
    > [!NOTE]  
    >  Verifique se o valor para Fields!Phone.Value não tem espaços extras e é do tipo `xref:System.String`.  
  
### <a name="lookup"></a>Lookup  
  
-   Especificando um campo de chave, você pode usar a função **Lookup** para recuperar um valor de um conjunto de dados para uma relação um-para-um, por exemplo, um par chave-valor. A seguinte expressão exibe o nome do produto de um conjunto de dados ("Product"), considerando o identificador de produto para correspondência:  
  
    ```  
    =Lookup(Fields!PID.Value, Fields!ProductID.Value, Fields.ProductName.Value, "Product")  
    ```  
  
### <a name="lookupset"></a>LookupSet  
  
-   Especificando um campo de chave, você pode usar a função **LookupSet** para recuperar um conjunto de valores de um conjunto de dados para uma relação um-para-muitos. Por exemplo, uma pessoa pode ter vários números de telefone. No exemplo a seguir, suponha que o conjunto de dados PhoneList contenha um identificador de pessoa e um número de telefone em cada linha. **LookupSet** retorna uma matriz de valores. A seguinte expressão combina os valores retornados em uma única cadeia de caracteres e exibe a lista de números de telefone da pessoa especificada por ContactID:  
  
    ```  
    =Join(LookupSet(Fields!ContactID.Value, Fields!PersonID.Value, Fields!PhoneNumber.Value, "PhoneList"),",")  
    ```  
  
###  <a name="conversion-functions"></a><a name="ConversionFunctions"></a> Funções de conversão  
 Use funções do Visual Basic para converter um campo de um tipo de dados em outro tipo de dados. As funções de conversão podem ser usadas para converter o tipo de dados padrão de um campo no tipo de dados necessário para cálculos ou para combinar texto.  
  
-   A expressão a seguir converte a constante 500 no tipo Decimal a fim de compará-la com um tipo de dados de dinheiro do Transact-SQL no campo Value em uma expressão de filtro.  
  
    ```  
    =CDec(500)  
    ```  
  
-   A expressão a seguir exibe o número de valores selecionados para o parâmetro de vários valores *MySelection*.  
  
    ```  
    =CStr(Parameters!MySelection.Count)  
    ```  
  
###  <a name="decision-functions"></a><a name="DecisionFunctions"></a> Funções de decisão  
  
-   A função **Iif** retorna um dos dois valores, dependendo se a expressão é verdadeira ou não. A expressão a seguir usa a função **Iif** para retornar um valor booliano igual a **True** se o valor de `LineTotal` excede 100. Caso contrário, ela retorna **False**:  
  
    ```  
    =IIF(Fields!LineTotal.Value > 100, True, False)  
    ```  
  
-   Use várias funções **IIF** (também conhecidas como "IIFs aninhadas") para retornar um dos três valores, dependendo do valor de `PctComplete`. A expressão a seguir pode ser colocada na cor de preenchimento de uma caixa de texto para alterar a cor da tela de fundo, dependendo do valor na caixa de texto.  
  
    ```  
    =IIF(Fields!PctComplete.Value >= 10, "Green", IIF(Fields!PctComplete.Value >= 1, "Blue", "Red"))  
    ```  
  
     Os valores superiores ou iguais a 10 são exibidos com uma tela de fundo verde, entre 1 e 9 são exibidos com uma tela de fundo azul e inferiores a 1 são exibidos com uma tela de fundo vermelha.  
  
-   Uma maneira diferente de obter a mesma funcionalidade usa a função **Switch**. A função **Switch** é útil quando você tem três ou mais condições a serem testadas. A função **Switch** retorna o valor associado à primeira expressão em uma série que é avaliada como verdadeira:  
  
    ```  
    =Switch(Fields!PctComplete.Value >= 10, "Green", Fields!PctComplete.Value >= 1, "Blue", Fields!PctComplete.Value = 1, "Yellow", Fields!PctComplete.Value <= 0, "Red")  
    ```  
  
     Os valores superiores ou iguais a 10 são exibidos com uma tela de fundo verde, entre 1 e 9 são exibidos com uma tela de fundo azul, iguais a 1 são exibidos com uma tela de fundo amarela e iguais ou inferiores a 0 são exibidos com uma tela de fundo vermelha.  
  
-   Teste o valor do campo `ImportantDate` e retorne "Vermelho", se ele for mais antigo que uma semana e "Azul", caso contrário. Esta expressão pode ser usada para controlar a propriedade Color de uma caixa de texto em um item de relatório:  
  
    ```  
    =IIF(DateDiff("d",Fields!ImportantDate.Value, Now())>7,"Red","Blue")  
    ```  
  
-   Teste o valor do campo `PhoneNumber` e retorne "Sem valor" se ele for **null** (**nothing** no Visual Basic); caso contrário, retorne o valor do número de telefone. Esta expressão pode ser usada para controlar o valor de uma caixa de texto em um item de relatório.  
  
    ```  
    =IIF(Fields!PhoneNumber.Value Is Nothing,"No Value",Fields!PhoneNumber.Value)  
    ```  
  
-   Teste o valor do campo `Department` e retorne o nome de um sub-relatório ou **null** (**Nothing** no Visual Basic). Esta expressão pode ser usada para sub-relatórios detalhados condicionais.  
  
    ```  
    =IIF(Fields!Department.Value = "Development", "EmployeeReport", Nothing)  
    ```  
  
-   Teste se um valor de campo é nulo. Esta expressão pode ser usada para controlar a propriedade **Hidden** de um item de relatório de imagem. No exemplo a seguir, a imagem especificada pelo campo [LargePhoto] é exibida somente se o valor do campo não é nulo.  
  
    ```  
    =IIF(IsNothing(Fields!LargePhoto.Value),True,False)  
    ```  
  
-   A função **MonthName** retorna um valor de cadeia de caracteres que contém o nome do mês especificado. O exemplo a seguir exibe NA no campo Month quando o campo contém o valor 0.  
  
    ```  
    IIF(Fields!Month.Value=0,"NA",MonthName(IIF(Fields!Month.Value=0,1,Fields!Month.Value)))  
  
    ```  
  
##  <a name="report-functions"></a><a name="ReportFunctions"></a> Funções de relatório  
 Em uma expressão, você pode adicionar uma referência a funções de relatório adicionais que manipulam dados em um relatório. Esta seção fornece exemplos para duas dessas funções. 
  
###  <a name="sum"></a><a name="Sum"></a> Sum  
  
-   A função **Sum** pode somar os valores em um grupo ou uma região de dados. Essa função pode ser útil no cabeçalho ou no rodapé de um grupo. A seguinte expressão exibe a soma dos dados no grupo Order ou na região de dados:  
  
    ```  
    =Sum(Fields!LineTotal.Value, "Order")  
    ```  
  
-   Use também a função **Sum** para cálculos de agregação condicionais. Por exemplo, se um conjunto de dados tem um campo chamado State com os possíveis valores Not Started, Started e Finished, a seguinte expressão, quando colocada em um cabeçalho de grupo, calcula a soma de agregação apenas para o valor Finished:  
  
    ```  
    =Sum(IIF(Fields!State.Value = "Finished", 1, 0))  
    ```  
  
###  <a name="rownumber"></a><a name="RowNumber"></a> RowNumber  
  
-   A função **RowNumber**, quando usada em uma caixa de texto dentro de uma região de dados, exibe o número de linha de cada instância da caixa de texto na qual a expressão aparece. Essa função pode ser útil para numerar linhas em uma tabela. Ela também pode ser útil para tarefas mais complexas, como fornecer quebras de página com base no número de linhas. Para obter mais informações, confira [Quebras de página](#PageBreaks) neste tópico.  
  
     O escopo especificado para **RowNumber** controla quando a renumeração é iniciada. A palavra-chave **Nothing** indica que a função iniciará a contagem na primeira linha na região de dados mais externa. Para iniciar a contagem em regiões de dados aninhadas, use o nome da região de dados. Para iniciar a contagem em um grupo, use o nome do grupo.  
  
    ```  
    =RowNumber(Nothing)  
    ```  
  
##  <a name="appearance-of-report-data"></a><a name="AppearanceofReportData"></a> Aparência dos dados de relatório  
 Use expressões para manipular como os dados são exibidos em um relatório. Por exemplo, você pode exibir os valores de dois campos em uma única caixa de texto, exibir informações sobre o relatório ou avaliar o impacto de como as quebras de página são inseridas no relatório.  
  
###  <a name="page-headers-and-footers"></a><a name="PageHeadersandFooters"></a> Cabeçalhos e rodapés de página  
 Ao criar um relatório, talvez você deseje exibir o nome do relatório e o número da página no rodapé do relatório. Para fazer isso, use as seguintes expressões:  
  
-   A expressão a seguir fornece o nome do relatório e a hora em que ele foi executado. Ela pode ser colocada em uma caixa de texto no rodapé ou no corpo do relatório. A hora é formatada com a cadeia de caracteres de formatação de data abreviada do .NET Framework:  
  
    ```  
    =Globals.ReportName & ", dated " & Format(Globals.ExecutionTime, "d")  
    ```  
  
-   A seguinte expressão, colocada em uma caixa de texto no rodapé de um relatório, fornece o número da página e o total de páginas no relatório:  
  
    ```  
    =Globals.PageNumber & " of " & Globals.TotalPages  
    ```  
  
 Os exemplos a seguir descrevem como exibir o primeiro e o último valor de uma página no cabeçalho de página, semelhante ao que você pode encontrar em uma listagem de diretório. O exemplo pressupõe uma região de dados que contenha uma caixa de texto chamada `LastName`.  
  
-   A seguinte expressão, colocada em uma caixa de texto no lado esquerdo do cabeçalho de página, fornece o primeiro valor da caixa de texto `LastName` na página:  
  
    ```  
    =First(ReportItems("LastName").Value)  
    ```  
  
-   A seguinte expressão, colocada em uma caixa de texto no lado direito do cabeçalho de página, fornece o último valor da caixa de texto `LastName` na página:  
  
    ```  
    =Last(ReportItems("LastName").Value)  
    ```  
  
 O exemplo a seguir descreve como exibir um total de páginas. O exemplo pressupõe uma região de dados que contenha uma caixa de texto chamada `Cost`.  
  
-   A seguinte expressão, colocada no cabeçalho ou no rodapé de página, fornece a soma dos valores na caixa de texto `Cost` da página:  
  
    ```  
    =Sum(ReportItems("Cost").Value)  
    ```  
  
> [!NOTE]  
>  Só é possível referenciar um item de relatório por expressão em um cabeçalho ou um rodapé de página. Além disso, você pode referenciar o nome da caixa de texto, mas não a expressão de dados real na caixa de texto, nas expressões de cabeçalho e rodapé de página.  
  
###  <a name="page-breaks"></a><a name="PageBreaks"></a> Quebras de página  
 Em alguns relatórios, o ideal é colocar uma quebra de página no final de um número especificado de linhas, em vez de em grupos ou itens de relatório ou além deles. Para fazer isso, crie um grupo que contém os grupos ou os registros detalhados desejados, adicione uma quebra de página ao grupo e, em seguida, adicione uma expressão de grupo ao grupo por um número especificado de linhas.  
  
-   A expressão a seguir, quando colocada na expressão de grupo, atribui um número a cada conjunto de 25 linhas. Quando uma quebra de página é definida para o grupo, esta expressão resulta em uma quebra de página a cada 25 linhas.  
  
    ```  
    =Ceiling(RowNumber(Nothing)/25)  
    ```  
  
     Para permitir que o usuário defina um valor para o número de linhas por página, crie um parâmetro chamado `RowsPerPage` e baseie a expressão de grupo no parâmetro, conforme mostrado na seguinte expressão:  
  
    ```  
    =Ceiling(RowNumber(Nothing)/Parameters!RowsPerPage.Value)  
    ```  
  
##  <a name="properties"></a><a name="Properties"></a> Propriedades  
 As expressões não são usadas apenas para exibir dados em caixas de texto. Elas também podem ser usadas para alterar como as propriedades são aplicadas aos itens de relatório. Você pode alterar as informações de estilo de um item de relatório ou alterar sua visibilidade.  
  
###  <a name="formatting"></a><a name="Formatting"></a> Formatação  
  
-   A seguinte expressão, quando usada na propriedade Color de uma caixa de texto, altera a cor do texto dependendo do valor do campo `Profit`:  
  
    ```  
    =Iif(Fields!Profit.Value < 0, "Red", "Black")  
    ```  
  
     Use também a variável de objeto `Me` do Visual Basic. Essa variável é outra maneira de se referir ao valor de uma caixa de texto.  
  
     `=Iif(Me.Value < 0, "Red", "Black")`  
  
-   A seguinte expressão, quando usada na propriedade BackgroundColor de um item de relatório em uma região de dados, alterna a cor da tela de fundo de cada linha entre verde-pálido e branco:  
  
    ```  
    =Iif(RowNumber(Nothing) Mod 2, "PaleGreen", "White")  
    ```  
  
     Se você estiver usando uma expressão para um escopo especificado, talvez você precise indicar o conjunto de dados para a função de agregação:  
  
    ```  
    =Iif(RowNumber("Employees") Mod 2, "PaleGreen", "White")  
    ```  
  
> [!NOTE]  
>  As cores disponíveis foram obtidas da enumeração KnownColor do .NET Framework.  
  
### <a name="chart-colors"></a>Cores do gráfico  
 Para especificar cores para um gráfico de formas, você pode usar um código personalizado para controlar a ordem em que as cores são mapeadas para valores de ponto de dados. Isso ajuda você a usar cores consistentes para vários gráficos que tenham os mesmos grupos de categorias. 
  
###  <a name="visibility"></a><a name="Visibility"></a> Visibilidade  
 Você pode mostrar e ocultar itens em um relatório usando as propriedades de visibilidade para o item de relatório. Em uma região de dados como uma tabela, você pode ocultar inicialmente as linhas de detalhes com base no valor em uma expressão.  
  
-   A seguinte expressão, quando usada para visibilidade inicial das linhas de detalhes em um grupo, mostra as linhas de detalhes de todas as vendas que excedem 90% no campo `PctQuota`:  
  
    ```  
    =Iif(Fields!PctQuota.Value>.9, False, True)  
    ```  
  
-   A seguinte expressão, quando definida na propriedade Hidden de uma tabela, mostra a tabela apenas se ela tem mais de 12 linhas:  
  
    ```  
    =IIF(CountRows()>12,false,true)  
    ```  
  
-   A seguinte expressão, quando definida na propriedade **Hidden** de uma coluna, mostra a coluna apenas se o campo existe no conjunto de dados do relatório depois que os dados são recuperados da fonte de dados:  
  
    ```  
    =IIF(Fields!Column_1.IsMissing, true, false)  
    ```  
  
###  <a name="urls"></a><a name="Hyperlinks"></a> URLs  
 Você pode personalizar URLs usando dados de relatório e também controlar condicionalmente se as URLs são adicionadas como uma ação para uma caixa de texto.  
  
-   A expressão a seguir, quando usada como uma ação em uma caixa de texto, gera uma URL personalizada que especifica o campo de conjunto de dados `EmployeeID` como um parâmetro de URL.  
  
    ```  
    ="https://adventure-works/MyInfo?ID=" & Fields!EmployeeID.Value  
    ```  
  
-   A expressão a seguir controla condicionalmente se uma URL deve ser adicionada a uma caixa de texto. Esta expressão depende de um parâmetro chamado `IncludeURLs`, que permite a um usuário decidir se deseja incluir URLs ativas em um relatório. Esta expressão é definida como uma ação em uma caixa de texto. Definindo o parâmetro como False e, em seguida, exibindo o relatório, você pode exportar o relatório para o Microsoft Excel sem hiperlinks.  
  
    ```  
    =IIF(Parameters!IncludeURLs.Value,"https://adventure-works.com/productcatalog",Nothing)  
    ```  
  
##  <a name="report-data"></a><a name="ReportData"></a> Dados de relatório  
 As expressões podem ser usadas para manipular os dados que são usados no relatório. Veja os parâmetros e outras informações de relatório. Você pode, até mesmo, alterar a consulta que é usada para recuperar dados do relatório.  
  
###  <a name="parameters"></a><a name="Parameters"></a> Parâmetros  
 Você pode usar expressões em um parâmetro para variar o valor padrão do parâmetro. Por exemplo, você pode usar um parâmetro para filtrar os dados para um usuário específico com base na ID de usuário que é usada para executar o relatório.  
  
-   A seguinte expressão, quando usada como o valor padrão de um parâmetro, coleta a ID de usuário da pessoa que executa o relatório:  
  
    ```  
    =User!UserID  
    ```  
  
-   Para referenciar um parâmetro em um parâmetro de consulta, uma expressão de filtro, uma caixa de texto ou outra área do relatório, use a coleção global **Parâmetros**. Este exemplo pressupõe que o parâmetro seja chamado *Department*:  
  
    ```  
    =Parameters!Department.Value  
    ```  
  
-   Os parâmetros podem ser criados em um relatório, mas definidos como ocultos. Quando o relatório é executado no servidor de relatório, o parâmetro não é exibido na barra de ferramentas e o leitor do relatório não pode alterar o valor padrão. Use um parâmetro oculto definido como um valor padrão como uma constante personalizada. Use esse valor em qualquer expressão, incluindo uma expressão de campo. A seguinte expressão identifica o campo especificado pelo valor de parâmetro padrão para o parâmetro chamado *ParameterField*:  
  
    ```  
    =Fields(Parameters!ParameterField.Value).Value  
    ```  
  
##  <a name="custom-code"></a><a name="CustomCode"></a> Código personalizado  
 Use um código personalizado inserido em um relatório. 
  
### <a name="using-group-variables-for-custom-aggregation"></a>Como usar variáveis de grupo para agregação personalizada  
 Inicialize o valor para uma variável de grupo que seja local a um escopo de grupo específico e, em seguida, inclua uma referência a essa variável em expressões. Uma das maneiras de usar uma variável de grupo com um código personalizado é implementar uma agregação personalizada. 
  
## <a name="suppressing-null-or-zero-values-at-run-time"></a>Como suprimir valores nulos ou zero em tempo de execução  
 Alguns valores em uma expressão podem ser avaliados como nulos ou indefinidos no momento do processamento de relatório. Isso pode criar erros em tempo de execução que resultam na exibição de **#Error** na caixa de texto em vez da expressão avaliada. A função **IIF** é particularmente sensível a esse comportamento porque, ao contrário de uma instrução If-Then-Else, cada parte da instrução **IIF** é avaliada (incluindo chamadas de função) antes de ser passada para a rotina que testa quanto a **true** ou **false**. A instrução `=IIF(Fields!Sales.Value is NOTHING, 0, Fields!Sales.Value)` gera **#Error** no relatório renderizado se `Fields!Sales.Value` é NOTHING.  
  
 Para evitar essa condição, use uma das seguintes estratégias:  
  
-   Defina o numerador como 0 e o denominador como 1 se o valor do campo B for 0 ou indefinido; caso contrário, defina o numerador com o valor do campo A e o denominador com o valor do campo B.  
  
    ```  
    =IIF(Field!B.Value=0, 0, Field!A.Value / IIF(Field!B.Value =0, 1, Field!B.Value))  
    ```  
  
-   Use uma função de código personalizado para retornar o valor da expressão. O exemplo a seguir retorna a diferença percentual entre um valor atual e um valor anterior. Isso pode ser usado para calcular a diferença entre quaisquer dois valores sucessivos e trata o caso atípico da primeira comparação (quando não há nenhum valor anterior) e os casos em que o valor anterior ou o valor atual é **null** (**Nothing** no Visual Basic).  
  
    ```  
    Public Function GetDeltaPercentage(ByVal PreviousValue, ByVal CurrentValue) As Object  
        If IsNothing(PreviousValue) OR IsNothing(CurrentValue) Then  
            Return Nothing  
        Else if PreviousValue = 0 OR CurrentValue = 0 Then  
            Return Nothing  
        Else   
            Return (CurrentValue - PreviousValue) / CurrentValue  
        End If  
    End Function  
    ```  
  
     A expressão a seguir mostra como chamar esse código personalizado de uma caixa de texto para o contêiner "ColumnGroupByYear" (grupo ou região de dados).  
  
    ```  
    =Code.GetDeltaPercentage(Previous(Sum(Fields!Sales.Value),"ColumnGroupByYear"), Sum(Fields!Sales.Value))  
    ```  
  
     Isso ajuda a evitar exceções em tempo de execução. Agora você pode usar uma expressão como `=IIF(Me.Value < 0, "red", "black")` na propriedade **Color** da caixa de texto para exibir condicionalmente o texto com base em se os valores são superiores ou inferiores a 0.  
  
## <a name="next-steps"></a>Próximas etapas

- [O que são os relatórios paginados no Power BI Premium?](paginated-reports-report-builder-power-bi.md)
  
