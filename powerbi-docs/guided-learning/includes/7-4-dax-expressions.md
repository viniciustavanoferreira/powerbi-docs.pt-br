---
ms.openlocfilehash: 5c2b254f20bd1eba97840a464a1b554cc4fe1238
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "61273157"
---
O uso de **variáveis** é uma parte extremamente avançada de uma função DAX.

![](media/7-4-dax-expressions/dax-variables_1.png)

Você pode definir uma variável em qualquer lugar de uma expressão DAX, usando a seguinte sintaxe:

    VARNAME = RETURNEDVALUE

As variáveis podem ser qualquer tipo de dados, incluindo tabelas inteiras.

Tenha em mente que sempre que você fizer referência a uma variável na expressão DAX, o Power BI terá de recalcular o valor de acordo com sua definição. Por esse motivo, é uma boa prática evitar a repetição de variáveis na função.

> Conteúdo do vídeo gentilmente cedido por [Alberto Ferrari, SQLBI](http://www.sqlbi.com/learning-dax)
> 
> 

