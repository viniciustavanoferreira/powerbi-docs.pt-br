---
ms.openlocfilehash: f22c12ec0ad5bd413f3658704132143c878df1aa
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/05/2020
ms.locfileid: "73799637"
---
O uso de **variáveis** é uma parte extremamente avançada de uma função DAX.

![](media/7-4-dax-expressions/dax-variables_1.png)

Você pode definir uma variável em qualquer lugar de uma expressão DAX, usando a seguinte sintaxe:

    VARNAME = RETURNEDVALUE

As variáveis podem ser qualquer tipo de dados, incluindo tabelas inteiras.

Tenha em mente que sempre que você fizer referência a uma variável na expressão DAX, o Power BI terá de recalcular o valor de acordo com sua definição. Por esse motivo, é uma boa prática evitar a repetição de variáveis na função.

> Conteúdo do vídeo gentilmente cedido por [Alberto Ferrari, SQLBI](https://www.sqlbi.com/learning-dax)
> 
> 

