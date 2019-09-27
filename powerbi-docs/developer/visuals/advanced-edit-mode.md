---
title: Modo de edição avançada em visuais do Power BI
description: Este artigo discute como definir controles de interface do usuário avançados em visuais do Power BI.
author: KesemSharabi
ms.author: kesharab
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: da72cf603027bc97060e7a00ed4a4e959a3a92e2
ms.sourcegitcommit: e2de2e8b8e78240c306fe6cca820e5f6ff188944
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71194478"
---
# <a name="advanced-edit-mode-in-power-bi-visuals"></a>Modo de edição avançada em visuais do Power BI

Se você precisar de controles avançados de interface do usuário em seu visual do Power BI, aproveite o modo de edição avançado. Quando você estiver no modo de edição de relatório, selecione o botão **Editar** para definir o modo de edição como **Avançado**. O visual pode usar o sinalizador `EditMode` para determinar se ele deve exibir esse controle de interface do usuário.

Por padrão, o visual não é compatível com o modo de edição avançada. Se um comportamento diferente for necessário, você poderá declarar explicitamente isso no arquivo *capabilities.json* configurando a propriedade `advancedEditModeSupport`.

Os valores possíveis são:

- `0` – NotSupported

- `1` – SupportedNoAction

- `2` – SupportedInFocus

## <a name="enter-advanced-edit-mode"></a>Entrar no modo de edição avançada

Um botão **Editar** será exibido se:

* A propriedade `advancedEditModeSupport` estiver definida no arquivo *capabilities.json* para `SupportedNoAction` ou `SupportedInFocus`.

* O visual é exibido no modo de edição de relatório.

Se a propriedade `advancedEditModeSupport` estiver ausente no arquivo *capabilities.json* ou definida como `NotSupported`, o botão **Editar** não será exibido.

![Entrar no modo de edição](./media/edit-mode.png)

Quando você seleciona **Editar**, o visual obtém uma chamada update() com EditMode definido como `Advanced`. Dependendo do valor definido no arquivo *capabilities.json*, as seguintes ações ocorrerão:

* `SupportedNoAction`: Mais nenhuma ação adicional é exigida pelo host.
* `SupportedInFocus`: O host abre o visual no modo de foco.

## <a name="exit-advanced-edit-mode"></a>Sair do modo de edição avançada

O botão **Voltar para o relatório** será exibido se:

* A propriedade `advancedEditModeSupport` estiver definida no arquivo *capabilities.json* como `SupportedInFocus`.
