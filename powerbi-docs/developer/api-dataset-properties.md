---
title: Propriedades do conjunto de dados do Power BI
description: Saiba mais sobre as propriedades das APIs do conjunto de dados do Power BI
author: rkarlin
ms.author: rkarlin
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 06/08/2018
ms.openlocfilehash: 508f304e2f5033c301db683e3b7557856fb3731b
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "61386283"
---
# <a name="dataset-properties"></a>Propriedades do conjunto de dados

O v1 atual da API de conjuntos de dados permite apenas um conjunto de dados a ser criado com um nome e uma coleção de tabelas. Cada tabela pode ter um nome e uma coleção de colunas. Cada coluna tem um nome e tipo de dados. Estamos expandindo bastante essas propriedades, principalmente com suporte para medidas e relações entre tabelas. A lista completa de propriedades com suporte para esta versão é a seguinte:

> [!IMPORTANT]
> Ela pode ser acessada na página [Grupos de operação de conjuntos de dados](https://docs.microsoft.com/rest/api/power-bi/datasets).

## <a name="dataset"></a>Conjunto de dados

Nome  |Type  |Descrição  |Somente leitura  |Necessário
---------|---------|---------|---------|---------
ID     |  GUID       | Identificador exclusivo do sistema todo para o conjunto de dados.        | True        | False        
Nome     | Cadeia de caracteres        | Nome do conjunto de dados definido pelo usuário.        | False        | True        
tabelas     | Tabela[]        | Coleção de tabelas.        |  False       | False        
relacionamentos     | Relação[]        | Coleção de relações entre tabelas.        | False        |  False  
defaultMode     | Cadeia de caracteres        | Determina se o conjunto de dados é enviado, transmitido ou as duas opções, com valores de "Push" e "Streaming".         | Falso        |  False

## <a name="table"></a>Table

Nome  |Type  |Descrição  |Somente leitura  |Necessário
---------|---------|---------|---------|---------
Nome     | Cadeia de caracteres        |  Nome da tabela definido pelo usuário. Ele também é usado como o identificador da tabela.       | False        |  True       
colunas     |  coluna[]       |  Coleção de colunas.       | False        |  True       
medidas     | medida[]        |  Coleção de medidas.       | False        |  False       
isHidden     | Boolean        | Se for true, a tabela ficará oculta das ferramentas de cliente.        | False        | False        

## <a name="column"></a>Coluna

Nome  |Type  |Descrição  |Somente leitura  |Necessário
---------|---------|---------|---------|---------
Nome     |  Cadeia de caracteres        | Nome da coluna definido pelo usuário.        |  False       | True       
tipo de dados     |  Cadeia de caracteres       |  Suporte para [tipos de dados EDM](https://msdn.microsoft.com/library/ee382832.aspx) e restrições. Consulte [Restrições de tipo de dados](#DataTypeRestrictions).      |  False       | True        
formatString     | Cadeia de caracteres        | Uma cadeia de caracteres que descreve como o valor deve ser formatado quando ele for exibido. Para saber mais sobre a formatação da cadeia de caracteres, consulte [conteúdo de FORMAT_STRING](https://msdn.microsoft.com/library/ms146084.aspx).      | False        | False        
sortByColumn    | Cadeia de caracteres        |   Nome da cadeia de caracteres de uma coluna na mesma tabela para ser usada para classificar a coluna atual.     | False        | False       
dataCategory     | Cadeia de caracteres        |  Valor da cadeia de caracteres a ser usada para a categoria de dados que descreve os dados dentro desta coluna. Alguns valores comuns incluem: endereço, cidade, continente, país, imagem, ImageUrl, latitude, longitude, organização, local, código postal, estado ou província, WebUrl       |  Falso       | False        
isHidden    |  Boolean       |  Propriedade que indica se a coluna está oculta da exibição. O padrão é false.       | False        | False        
summarizeBy     | Cadeia de caracteres        |  Método de agregação padrão para a coluna. Os valores incluem: padrão, nenhum, soma, mín, máx, contagem, média, contagem distinta     |  False       | False

## <a name="measure"></a>Medida

Nome  |Type  |Descrição  |Somente leitura  |Necessário
---------|---------|---------|---------|---------
Nome     | Cadeia de caracteres        |  Nome da medida definido pelo usuário.       |  False       | True        
expressão     | Cadeia de caracteres        | Uma expressão DAX válida.        | False        |  True       
formatString     | Cadeia de caracteres        |  Uma cadeia de caracteres que descreve como o valor deve ser formatado quando ele for exibido. Para saber mais sobre a formatação da cadeia de caracteres, consulte [conteúdo de FORMAT_STRING](https://msdn.microsoft.com/library/ms146084.aspx).       | False        | False        
isHidden     | Cadeia de caracteres        |  Se for true, a tabela ficará oculta das ferramentas de cliente.       |  False       | False       

## <a name="relationship"></a>Relação

Nome  |Type  |Descrição  |Somente leitura  |Necessário 
---------|---------|---------|---------|---------
Nome     | Cadeia de caracteres        | Nome da relação definido pelo usuário. Ele também é usado como o identificador da relação.        | False       | True        
crossFilteringBehavior     | Cadeia de caracteres        |    A direção do filtro da relação: OneDirection (padrão), BothDirections, Automatic       | Falso        | False        
fromTable     | Cadeia de caracteres        | Nome da tabela de chave estrangeira.        | False        | True         
fromColumn    | Cadeia de caracteres        | Nome da coluna de chave estrangeira.        | False        | True         
toTable    | Cadeia de caracteres        | Nome da tabela de chave primária.        | False        | True         
toColumn     | Cadeia de caracteres        | Nome da coluna de chave primária.        | False        | True        

<a name="DataTypeRestrictions"/>

## <a name="data-type-restrictions-applies-to-datatype-property"></a>Restrições de tipo de dados (aplica-se à propriedade de tipo de dados)

Tipo de dados  |Restrições  
---------|---------
Int64     |   Int64.MaxValue e Int64.MinValue não permitidos.      
Double     |  Valores de Double.MaxValue e Double.MinValue não permitidos. Não há suporte para NaN. Não há suporte para +Infinity e -Infinity em algumas funções (por exemplo, Min e Max).       
Boolean     |   True ou false.
Datetime    |   Durante o carregamento de dados, podemos quantizar valores com frações de dias para múltiplos inteiros de 1/300 de segundo (3,33 ms).      
Cadeia de caracteres     |  Atualmente permite até 4.000 caracteres por valor de cadeia de caracteres.
Decimal|precision=28, scale=4

## <a name="example"></a>Exemplo
O exemplo de código a seguir inclui um número dessas propriedades:

```json
{

  "name": "PushAdvanced",

  "tables": [

    {

      "name": "Date",

      "columns": [

        {

          "name": "Date",

          "dataType": "dateTime",

          "formatString": "dddd\\, mmmm d\\, yyyy",

          "summarizeBy": "none"

        }

      ]

    },

    {

      "name": "sales",

      "columns": [

        {

          "name": "Date",

          "dataType": "dateTime",

          "formatString": "dddd\\, mmmm d\\, yyyy",

          "summarizeBy": "none"

        },

        {

          "name": "Sales",

          "dataType": "int64",

          "formatString": "0",

          "summarizeBy": "sum"

        }

      ],

      "measures": [

        {

          "name": "percent to forecast",

          "expression": "SUM(sales[Sales])/SUM(forecast[forecast])",

          "formatString": "0.00 %;-0.00 %;0.00 %"

        }

      ]

    },

    {

      "name": "forecast",

      "columns": [

        {

          "name": "date",

          "dataType": "dateTime",

          "formatString": "m/d/yyyy",

          "summarizeBy": "none"

        },

        {

          "name": "forecast",

          "dataType": "int64",

          "formatString": "0",

          "summarizeBy": "sum"

        }

      ]

    }

  ],

  "relationships": [

    {

      "name": "2ea345ce-b147-436e-8ac2-9d3c4d82af8d",

      "fromTable": "sales",

      "fromColumn": "Date",

      "toTable": "Date",

      "toColumn": "Date",

      "crossFilteringBehavior": "bothDirections"

    },

    {

      "name": "5d95f419-e589-4345-9581-6e70670b1bba",

      "fromTable": "forecast",

      "fromColumn": "date",

      "toTable": "Date",

      "toColumn": "Date",

      "crossFilteringBehavior": "bothDirections"

    }

  ]

}
```