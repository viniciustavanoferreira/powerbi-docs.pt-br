---
title: O recurso supportsKeyboardFocus
description: Este artigo descreve como usar o recurso supportsKeyboardFocus em visuais do Power BI e seus requisitos.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 04/30/2020
ms.openlocfilehash: c8cf0f4e896b8a44764d1c363c597182f55d30b3
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83276503"
---
# <a name="use-the-supportskeyboardfocus-feature"></a>Usar o recurso supportsKeyboardFocus

Este artigo descreve como usar o recurso `supportsKeyboardFocus` em visuais do Power BI.
O recurso `supportsKeyboardFocus` permite navegar pelos pontos de dados do visual usando apenas o teclado.

Para saber mais sobre a navegação de visuais pelo teclado, confira [Navegação pelo teclado](../../create-reports/desktop-accessibility-consuming-tools.md#keyboard-navigation).

## <a name="example"></a>Exemplo

Abra um visual que use o recurso `supportsKeyboardFocus`. Selecione qualquer ponto de dados dentro do visual e pressione a tecla Tab. O foco é movido para o próximo ponto de dados cada vez que você pressiona a tecla Tab. Pressione Enter para selecionar o ponto de dados realçado.

![Dá suporte ao exemplo de foco do teclado](./media/supportskeyboardfocus-feature/supports-keyboard-focus-example.png)

## <a name="requirements"></a>Requisitos

Esse recurso requer a API v 2.1.0 ou superior.

Esse recurso pode ser aplicado a todos os visuais, exceto visuais de imagem.

## <a name="usage"></a>Uso

Para usar o recurso `supportsKeyboardFocus`, adicione o código a seguir ao arquivo *capabilities.json* do seu visual.
Essa funcionalidade permite que o visual receba foco por meio da navegação por teclado.

```json
    {   
            ...
        "supportsKeyboardFocus": true
            ...
    }

```

## <a name="next-steps"></a>Próximas etapas

Para saber mais sobre os recursos de acessibilidade, confira [Criar relatórios do Power BI para acessibilidade](../../create-reports/desktop-accessibility-creating-reports.md).

Para experimentar o desenvolvimento do Power BI, confira [Desenvolver um visual do Power BI](custom-visual-develop-tutorial.md).
