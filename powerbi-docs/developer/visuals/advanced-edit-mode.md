---
title: Modo de edição avançada
description: Visuais do Power BI com controles de interface do usuário avançados
author: shaym83
ms.author: shaym
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 625105aed773bce5cf70932f092faf60ea001c2c
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68425541"
---
# <a name="advanced-edit-mode"></a>Modo de edição avançada

Os visuais que exigem controles de interface do usuário avançados podem declarar suporte ao modo de edição avançada.
Se esse modo for compatível, quando se estiver no modo de edição de relatório, um botão `Edit` será exibido no menu do visual.
Quando o `Edit` botão é clicado, EditMode é definido para `Advanced`.
O visual pode usar o sinalizador EditMode para determinar que esses controles de interface do usuário devem ser exibidos.

Por padrão, o visual não é compatível com o modo de edição avançada.
Se um comportamento diferente for necessário, ele deverá ser declarado explicitamente no arquivo `capabilities.json` do visual, definindo-se a propriedade `advancedEditModeSupport`.

Os valores possíveis são:

- 0 – NotSupported

- 1 – SupportedNoAction

- 2 – SupportedInFocus

## <a name="entering-advanced-edit-mode"></a>Entrar no modo de edição avançada

O botão `Edit` ficará visível se:

 1 – a propriedade `advancedEditModeSupport` for definida em capabilities.json para `SupportedNoAction` ou `SupportedInFocus`;

 2 – o visual for exibido no modo de edição de relatório.

Se a propriedade `advancedEditModeSupport` estiver ausente em capabilities.json ou definida para `NotSupported`, o botão 'Editar' desaparecerá.

![Entrar no modo de edição](./media/edit-mode.png)

Quando o usuário clica em `Edit`, o visual recebe uma chamada update() com EditMode definido para `Advanced`.
De acordo com o valor definido nas funcionalidades, as seguintes ações ocorrerão:

* `SupportedNoAction` – nenhuma ação adicional pelo host;
* `SupportedInFocus` – o host abre o visual no modo de foco.

## <a name="exiting-advanced-edit-mode"></a>Sair do modo de edição avançada

O botão `Back to report` ficará visível se:

1 – a propriedade `advancedEditModeSupport` for definida em capabilities.json para `SupportedInFocus`.
