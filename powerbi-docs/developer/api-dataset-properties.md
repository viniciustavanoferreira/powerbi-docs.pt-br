---
title: Propriedades do conjunto de dados do Power BI
description: Saiba mais sobre as propriedades das APIs do conjunto de dados do Power BI
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 06/08/2018
ms.openlocfilehash: 9d0ab5bcffe3b0267b3e07a684c2c7c9bd0fd316
ms.sourcegitcommit: 6272c4a0f267708ca7d38a45774f3bedd680f2d6
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/06/2020
ms.locfileid: "74265818"
---
# <a name="dataset-properties"></a>Propriedades do conjunto de dados

O v1 atual da API de conjuntos de dados permite apenas um conjunto de dados a ser criado com um nome e uma coleção de tabelas. Cada tabela pode ter um nome e uma coleção de colunas. Cada coluna tem um nome e tipo de dados. Estamos expandindo bastante essas propriedades, principalmente com suporte para medidas e relações entre tabelas. A lista completa de propriedades com suporte para esta versão é a seguinte:

> [!IMPORTANT]
> Ela pode ser acessada na página [Grupos de operação de conjuntos de dados](https://docs.microsoft.com/rest/api/power-bi/datasets).

## <a name="dataset"></a>Conjunto de dados

Nome  |Tipo  |Descrição  |Somente leitura  |Obrigatório
---------|---------|---------|---------|---------
ID     |  GUID       | Identificador exclusivo do sistema todo para o conjunto de dados.        | True        | Falso        
Nome     | Cadeia de caracteres        | Nome do conjunto de dados definido pelo usuário.        | Falso        | True        
tabelas     | Tabela[]        | Coleção de tabelas.        |  Falso       | Falso        
relacionamentos     | Relação[]        | Coleção de relações entre tabelas.        | Falso        |  Falso  
defaultMode     | Cadeia de caracteres        | Determina se o conjunto de dados é enviado, transmitido ou as duas opções, com valores de "Push" e "Streaming".         | Falso        |  Falso

## <a name="table"></a>Tabela

Nome  |Tipo  |Descrição  |Somente leitura  |Obrigatório
---------|---------|---------|---------|---------
Nome     | Cadeia de caracteres        |  Nome da tabela definido pelo usuário. Ele também é usado como o identificador da tabela.       | Falso        |  True       
colunas     |  coluna[]       |  Coleção de colunas.       | Falso        |  True       
medidas     | medida[]        |  Coleção de medidas.       | Falso        |  Falso       
isHidden     | Booliano        | Se for true, a tabela ficará oculta das ferramentas de cliente.        | Falso        | Falso        

## <a name="column"></a>Coluna

Nome  |Tipo  |Descrição  |Somente leitura  |Obrigatório
---------|---------|---------|---------|---------
Nome     |  Cadeia de caracteres        | Nome da coluna definido pelo usuário.        |  Falso       | True       
tipo de dados     |  Cadeia de caracteres       |  Suporte para [tipos de dados EDM](https://msdn.microsoft.com/library/ee382832.aspx) e restrições. Consulte [Restrições de tipo de dados](#DataTypeRestrictions).      |  Falso       | True        
formatString     | Cadeia de caracteres        | Uma cadeia de caracteres que descreve como o valor deve ser formatado quando ele for exibido. Para saber mais sobre a formatação da cadeia de caracteres, consulte [conteúdo de FORMAT_STRING](https://msdn.microsoft.com/library/ms146084.aspx).      | Falso        | Falso        
sortByColumn    | Cadeia de caracteres        |   Nome da cadeia de caracteres de uma coluna na mesma tabela para ser usada para classificar a coluna atual.     | Falso        | Falso       
dataCategory     | Cadeia de caracteres        |  Valor da cadeia de caracteres a ser usada para a categoria de dados que descreve os dados dentro desta coluna. Alguns valores comuns incluem: endereço, cidade, continente, país, imagem, ImageUrl, latitude, longitude, organização, local, código postal, estado ou província, WebUrl       |  Falso       | Falso        
isHidden    |  Booliano       |  Propriedade que indica se a coluna está oculta da exibição. O padrão é false.       | Falso        | Falso        
summarizeBy     | Cadeia de caracteres        |  Método de agregação padrão para a coluna. Os valores incluem: padrão, nenhum, soma, mín, máx, contagem, média, contagem distinta     |  Falso       | Falso

## <a name="measure"></a>Medida

Nome  |Tipo  |Descrição  |Somente leitura  |Obrigatório
---------|---------|---------|---------|---------
Nome     | Cadeia de caracteres        |  Nome da medida definido pelo usuário.       |  Falso       | True        
expressão     | Cadeia de caracteres        | Uma expressão DAX válida.        | Falso        |  True       
formatString     | Cadeia de caracteres        |  Uma cadeia de caracteres que descreve como o valor deve ser formatado quando ele for exibido. Para saber mais sobre a formatação da cadeia de caracteres, consulte [conteúdo de FORMAT_STRING](https://msdn.microsoft.com/library/ms146084.aspx).       | Falso        | Falso        
isHidden     | Cadeia de caracteres        |  Se for true, a tabela ficará oculta das ferramentas de cliente.       |  Falso       | Falso       

## <a name="relationship"></a>Relação

Nome  |Tipo  |Descrição  |Somente leitura  |Obrigatório 
---------|---------|---------|---------|---------
Nome     | Cadeia de caracteres        | Nome da relação definido pelo usuário. Ele também é usado como o identificador da relação.        | Falso       | True        
crossFilteringBehavior     | Cadeia de caracteres        |    A direção do filtro da relação: OneDirection (padrão), BothDirections, Automatic       | Falso        | Falso        
fromTable     | Cadeia de caracteres        | Nome da tabela de chave estrangeira.        | Falso        | True         
fromColumn    | Cadeia de caracteres        | Nome da coluna de chave estrangeira.        | Falso        | True         
toTable    | Cadeia de caracteres        | Nome da tabela de chave primária.        | Falso        | True         
toColumn     | Cadeia de caracteres        | Nome da coluna de chave primária.        | Falso        | True        

<a name="DataTypeRestrictions"/>

## <a name="data-type-restrictions-applies-to-datatype-property"></a>Restrições de tipo de dados (aplica-se à propriedade de tipo de dados)

Tipo de dados  |Restrições  
---------|---------
Int64     |   Int64.MaxValue e Int64.MinValue não permitidos.      
Double     |  Valores de Double.MaxValue e Double.MinValue não permitidos. Não há suporte para NaN. Não há suporte para +Infinity e -Infinity em algumas funções (por exemplo, Min e Max).       
Booliano     |   True ou false.
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