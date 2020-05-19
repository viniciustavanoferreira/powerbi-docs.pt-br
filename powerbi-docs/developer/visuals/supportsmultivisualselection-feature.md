---
title: O recurso supportsMultiVisualSelection
description: Este artigo descreve como usar o recurso supportsMultiVisualSelection em visuais do Power BI e seus requisitos.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 04/30/2020
ms.openlocfilehash: 6ad986308fb82f8191829d29654bb96b55d0fbd0
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83272685"
---
# <a name="use-the-supportsmultivisualselection-feature"></a>Usar o recurso supportsMultiVisualSelection

O recurso `supportsMultiVisualSelection` permite que você use a seleção em vários visuais em um relatório.

## <a name="example"></a>Exemplo

Em um relatório com mais de um visual, selecione dois valores para que eles se apliquem a outros visuais. Por exemplo, no [exemplo de Análise de Varejo](../../create-reports/sample-retail-analysis.md), selecione **Direção de Moda** em um visual. Pressione CTRL e selecione **Jan** em outro visual. No relatório, suas seleções se aplicam aos outros visuais que dão suporte ao uso desse recurso. Outros visuais agora incluem **Fashions Direct** e **Jan**.

## <a name="requirements"></a>Requisitos

Esse recurso requer a API v3.2.0 ou superior.

Não é possível aplicar esse recurso a visuais de imagem. Você não pode aplicá-lo a alguns visuais avançados, como fator principal, árvore hierárquica, visuais de P e R, caixas de texto e gráficos de medidor.

## <a name="usage"></a>Uso

Para usar o recurso `supportsMultiVisualSelection`, adicione o código a seguir ao arquivo `capabilities.json` do seu visual.

```json
    {   
            ...
        "supportsMultiVisualSelection": true
            ...
    }
```

## <a name="next-steps"></a>Próximas etapas

Para saber mais sobre os conceitos do Power BI, confira [Visuais no Power BI](power-bi-visuals-concept.md).

Para experimentar o desenvolvimento do Power BI, confira [Desenvolver um visual do Power BI](custom-visual-develop-tutorial.md).
