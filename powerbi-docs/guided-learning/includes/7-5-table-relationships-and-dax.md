---
ms.openlocfilehash: cd6ea6fd52f929e2cd254214cf0e8c96e858f6c2
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "61273160"
---
O Power BI permite criar relações entre várias tabelas, incluindo tabelas provenientes de fontes de dados completamente diferentes. Você pode ver esses relacionamentos de qualquer modelo de dados na exibição **Relações** do Power BI Desktop.

![](media/7-5-table-relationships-and-dax/dax-relationships_1.png)

## <a name="dax-relational-functions"></a>Funções relacionais do DAX
O DAX tem **funções relacionais** que permitem interagir com tabelas que têm relações estabelecidas.

Você pode retornar o valor de uma coluna ou retornar todas as linhas em uma relação usando as funções DAX.

Por exemplo, a função **RELATED** segue as relações e retorna o valor de uma coluna, enquanto **RELATEDTABLE** segue as relações e retorna uma tabela inteira que é filtrada para incluir somente as linhas relacionadas.

![](media/7-5-table-relationships-and-dax/dax-relationships_2.png)

A função **RELATED** funciona em relações *muitos para um*, enquanto **RELATEDTABLE** é usada para relações *um para muitos*.

É possível usar funções relacionais para criar expressões que incluem valores em várias tabelas. O DAX retornará um resultado com essas funções, independentemente do tamanho da cadeia da relação.

> Conteúdo do vídeo gentilmente cedido por [Alberto Ferrari, SQLBI](http://www.sqlbi.com/learning-dax)
> 
> 

