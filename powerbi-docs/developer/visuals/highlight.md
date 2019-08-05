---
title: Realce
description: Seleções de pontos de dados realçando em elementos visuais Power BI
author: sranins
ms.author: rasala
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 1ee45781ddc29eee9eeab23a5d748fb7752fe907
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68424805"
---
# <a name="highlight-data-points-in-power-bi-visuals"></a>Realçar pontos de dados em visuais do Power BI

Por padrão, sempre que um elemento é selecionado, a matriz `values` no objeto `dataView` será filtrada apenas para os valores selecionados. Isso fará com que todos os outros elementos visuais na página exibam apenas os dados selecionados.

![realçar comportamento padrão de 'dataview'](./media/highlight-dataview.png)

Se você definir a propriedade `supportsHighlight` em `capabilities.json` como `true`, receberá a matriz `values` completa sem filtro junto com uma matriz `highlights`. A matriz `highlights` terá o mesmo comprimento que a matriz de valores e quaisquer valores não selecionados serão definidos como `null`. Com essa propriedade habilitada, é responsabilidade do visual realçar os dados apropriados comparando a matriz `values` com a matriz `highlights`.

![realçar 'dataview' supportshighlight](./media/highlight-dataview-supports.png)

No exemplo, você observará a barra 1 selecionada. E é o único valor na matriz de realces. Também é importante observar que pode haver várias seleções e realce parcial. Há o valor numérico correspondente nos valores e as matrizes de realces estarão presentes, mas serão diferentes.
