---
title: Expressões no Construtor de Relatórios do Power BI
description: As expressões são amplamente usadas nos relatórios paginados do Power BI Report Builder para recuperar, calcular, exibir, agrupar, classificar, filtrar, parametrizar e formatar dados.
ms.date: 06/06/2019
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.assetid: 76d3ac86-650c-46fe-8086-8b3edcea3882
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 96c62fec55f87a31970b624a79314656ced0c159
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/05/2020
ms.locfileid: "78921115"
---
# <a name="expressions-in-power-bi-report-builder"></a>Expressões no Construtor de Relatórios do Power BI
  As expressões são amplamente usadas nos relatórios paginados do Power BI Report Builder para recuperar, calcular, exibir, agrupar, classificar, filtrar, parametrizar e formatar dados. 
  
  Muitas propriedades de item de relatório podem ser definidas como uma expressão. Expressões ajudam a controlar o conteúdo, o design e a interatividade do relatório. As expressões são escritas no Microsoft Visual Basic, salvas na definição de relatório e avaliadas pelo processador de relatório quando você executa o relatório.  
  
 Ao contrário de aplicativos como o Microsoft Office Excel, em que você trabalha com os dados diretamente em uma planilha, em um relatório você trabalha com expressões que são espaços reservados para os dados. Para ver os dados reais das expressões avaliadas, é necessário visualizar o relatório. Quando você executa o relatório, o processador de relatório avalia cada expressão conforme combina os dados e os elementos de layout do relatório, como tabelas e gráficos.  
  
 Quando você cria um relatório, várias expressões de itens de relatório são definidas para você. Por exemplo, quando você arrasta um campo do painel de dados para uma célula de tabela na área de design do relatório, o valor da caixa de texto é definido como uma expressão simples para o campo. Na figura a seguir, o painel de dados do relatório exibe os campos do conjunto de dados ID, Name, SalesTerritory, Code e Sales. Três campos foram adicionados à tabela: [Name], [Code] e [Sales]. A notação [Name] na área de design representa a expressão subjacente `=Fields!Name.Value`.  
  
![Modo de exibição de Design do Construtor de Relatórios](media/report-builder-expressions/report-builder-data-design-preview.png)
  
 Quando você visualiza o relatório, o processador de relatório combina a região de dados de tabela com os dados reais da conexão de dados e exibe uma linha na tabela para cada linha no conjunto de resultados.  
  
 Para inserir expressões manualmente, selecione um item na área de design e use os menus de atalho e caixas de diálogo para definir as propriedades do item. Quando vir o botão ***(fx)*** ou o valor `<Expression>` em uma lista suspensa, você saberá que você pode definir a propriedade como uma expressão. 
  
##  <a name="understanding-simple-and-complex-expressions"></a><a name="Types"></a> Reconhecimento expressões simples e complexas  
 As expressões começam com um sinal de igual (=) e são escritas no Microsoft Visual Basic. Expressões podem incluir uma combinação de constantes, operadores e referências a valores internos (campos, coleções e funções) e a código externo ou personalizado.  
  
 Você pode usar expressões para especificar o valor das muitas propriedades de item de relatório. As propriedades mais comuns são valores para caixas de texto e texto de espaço reservado. Normalmente, se uma caixa de texto contém apenas uma expressão, a expressão é o valor da propriedade da caixa de texto. Se uma caixa de texto contém várias expressões, cada expressão é o valor do texto de espaço reservado na caixa de texto.  
  
 Por padrão, as expressões aparecem na área de design do relatório como *expressões simples* ou *complexas*.  
  
-   **Simples** Uma expressão simples contém uma referência a um único item em uma coleção interna, por exemplo, um campo de conjunto de dados, um parâmetro ou um campo interno. Na área de design, uma expressão simples aparece entre colchetes. Por exemplo, `[FieldName]` corresponde à expressão subjacente `=Fields!FieldName.Value`. Expressões simples são criadas automaticamente quando você cria o layout do relatório e arrasta itens do painel de dados de relatório para a área de design. Para obter mais informações sobre os símbolos que representam diferentes coleções internas, confira [Reconhecimento de símbolos de prefixo para expressões simples](#DisplayText).  
  
-   **Complexas** Uma expressão complexa contém referências a vários operadores, chamadas de função e referências internas. Uma expressão complexa aparece como <\<Expr>> quando o valor da expressão inclui mais de uma referência simples. Para exibir a expressão, passe o mouse sobre ela e use a dica de ferramenta. Para editar a expressão, abra-a na caixa de diálogo **Expressão**.  
  
 A figura a seguir mostra expressões simples e complexas típicas para texto de espaço reservado e caixas de texto.  
  
![Formato padrão de expressão do Construtor de Relatórios](media/report-builder-expressions/report-builder-expression-default-format.png) 
  
 Para exibir valores de exemplo em vez de texto para expressões, aplique a formatação ao texto de espaço reservado ou à caixa de texto. A figura a seguir mostra a área de design de relatório configurada para mostrar valores de exemplo:  
  
![Formato de exemplo de expressão do Construtor de Relatórios](media/report-builder-expressions/report-builder-expression-sample-values-format.png)  


## <a name="understanding-prefix-symbols-in-simple-expressions"></a><a name="DisplayText"></a> Reconhecimento de símbolos de prefixo em expressões simples  

Expressões simples usam símbolos para indicar se a referência é a um campo, um parâmetro, uma coleção interna ou a coleção ReportItems. A tabela a seguir mostra exemplos de texto de exibição e de expressão:  
  
|Item|Exemplo de texto de exibição|Exemplo de texto de expressão|  
|----------|--------------------------|-----------------------------|  
|Campos de conjunto de dados|`[Sales]`<br /><br /> `[SUM(Sales)]`<br /><br /> `[FIRST(Store)]`|`=Fields!Sales.Value`<br /><br /> `=Sum(Fields!Sales.Value)`<br /><br /> `=First(Fields!Store.Value)`|  
|Parâmetros de relatório|`[@Param]`<br /><br /> `[@Param.Label]`|`=Parameters!Param.Value`<br /><br /> `=Parameters!Param.Label`|  
|Campos internos|`[&ReportName]`|`=Globals!ReportName.Value`|  
|Caracteres literais usados para o texto de exibição|`\[Sales\]`|`[Sales]`|  
  
##  <a name="writing-complex-expressions"></a><a name="References"></a> Escrevendo expressões complexas  
 Expressões podem incluir referências a funções, operadores, constantes, campos, parâmetros, itens de coleções internas e código personalizado ou assemblies personalizados incorporados.  
  
 A tabela a seguir lista os tipos de referências que podem ser incluídas em uma expressão:  
  
|Referências|Descrição|Exemplo|  
|----------------|-----------------|-------------|  
|Constants|Descreve as constantes que podem ser acessadas interativamente para propriedades que exigem valores constantes, como cores de fonte.|`="Blue"`|  
|Operators|Descreve os operadores que podem ser usados para combinar referências em uma expressão. Por exemplo, o operador **&** é usado para concatenar cadeias de caracteres.|`="The report ran at: " & Globals!ExecutionTime & "."`|  
|Coleções internas|Descreve as coleções internas que podem ser incluídas em uma expressão, como `Fields`, `Parameters` e `Variables`.|`=Fields!Sales.Value`<br /><br /> `=Parameters!Store.Value`<br /><br /> `=Variables!MyCalculation.Value`|  
|Relatório interno e funções de agregação|Descreve as funções internas, como `Sum` ou `Previous`, que podem ser acessadas de uma expressão.|`=Previous(Sum(Fields!Sales.Value))`|  
|Referências a assembly e código personalizado em expressões no Construtor de Relatórios |Descreve como você pode acessar as classes de CLR internas `xref:System.Math` e `xref:System.Convert`, outras classes de CLR, funções de biblioteca em tempo de execução do Visual Basic ou métodos de um assembly externo.<br /><br /> Descreve como você pode acessar o código personalizado inserido em seu relatório ou que é compilado e instalado como um assembly personalizado no cliente de relatório e no servidor de relatório.|`=Sum(Fields!Sales.Value)`<br /><br /> `=CDate(Fields!SalesDate.Value)`<br /><br /> `=DateAdd("d",3,Fields!BirthDate.Value)`<br /><br /> `=Code.ToUSD(Fields!StandardCost.Value)`|  
   
##  <a name="validating-expressions"></a><a name="Valid"></a> Validando expressões  
 Quando você cria uma expressão para uma propriedade de item de relatório específica, as referências que podem ser incluídas em uma expressão dependem dos valores que a propriedade de item de relatório pode aceitar e do escopo em que a propriedade é avaliada. Por exemplo:  
  
-   Por padrão, a expressão [Sum] calcula a soma dos dados que estão no escopo no momento em que a expressão é avaliada. Para uma célula de tabela, o escopo depende de associações a grupos de linhas e colunas. 
  
-   Para o valor de uma propriedade de Fonte, o valor deve ser avaliado como o nome de uma fonte.  
  
-   A sintaxe da expressão é validada no tempo de design. A validação do escopo da expressão ocorre quando você publica o relatório. No caso de validações que dependem de dados reais, só é possível detectar erros em tempo de execução. Algumas dessas expressões geram #Error como uma mensagem de erro no relatório renderizado. 

## <a name="next-steps"></a>Próximas etapas

- [O que são os relatórios paginados no Power BI Premium?](paginated-reports-report-builder-power-bi.md)
