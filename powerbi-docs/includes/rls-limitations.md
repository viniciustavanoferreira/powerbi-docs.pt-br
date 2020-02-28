---
author: davidiseminger
ms.service: powerbi
ms.topic: include
ms.date: 01/31/2020
ms.author: davidi
ms.openlocfilehash: b67025de5e2a70876a31fd42e22c9572403288fa
ms.sourcegitcommit: cde65bb8b1bed1ee8cf512651afeb829ddc155de
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77464315"
---
## <a name="limitations"></a>Limitações

As limitações atuais da segurança no nível de linha nos modelos de nuvem são as seguintes:

* Se você definiu funções e regras anteriormente no serviço do Power BI, deverá criá-las novamente no Power BI Desktop.

* Você pode definir a RLS somente nos conjuntos de dados criados com o Power BI Desktop. Se desejar habilitar a RLS para conjuntos de dados criados com o Excel, deverá primeiro converter os arquivos em arquivos PBIX (Power BI Desktop). [Saiba mais](../desktop-import-excel-workbooks.md).

* Há suporte apenas para conexões de Importação e DirectQuery. Conexões dinâmicas do Analysis Services são tratadas no modelo local.

## <a name="known-issues"></a>Problemas conhecidos

Há um problema conhecido em que você recebe uma mensagem de erro quando tenta publicar um relatório publicado anteriormente no Power BI Desktop. O cenário é descrito a seguir:

1. Sara tem um conjunto de dados que foi publicado no serviço do Power BI e ela configurou a RLS.

1. Sara atualiza o relatório no Power BI Desktop e o publica novamente.

1. Sara recebe um erro.

**Solução alternativa:** Publique novamente o arquivo do Power BI Desktop por meio do serviço do Power BI até que esse problema seja resolvido. Você pode fazer isso selecionando **Obter Dados** > **Arquivos**.
