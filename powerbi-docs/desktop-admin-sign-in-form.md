---
title: Como os administradores podem gerenciar o formulário de entrada do Power BI Desktop
description: Saiba como é possível gerenciar o formulário de entrada inicial ao abrir o Power BI Desktop.
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/15/2019
ms.author: davidi
ms.openlocfilehash: 934827311e089e34e56fbcffe4d4c58a056df4ad
ms.sourcegitcommit: 97597ff7d9ac2c08c364ecf0c729eab5d59850ce
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75761693"
---
# <a name="administrators-manage-the-power-bi-desktop-sign-in-form"></a>Administradores: Gerenciar o formulário de entrada do Power BI Desktop
Na primeira vez em que o Power BI Desktop é iniciado, é exibido um formulário de entrada. As informações podem ser preenchidas ou entre no Power BI para continuar. Os administradores gerenciam este formulário usando uma chave do Registro. 

![Formulário de entrada inicial para o Power BI Desktop](media/desktop-admin-sign-in-form/sign-in-form.png)

Os administradores usam a seguinte chave do Registro para desabilitar o formulário de entrada. Isso também pode ser enviado por push para toda a organização usando políticas globais.

```
Key: HKEY_CURRENT_USER\SOFTWARE\Policies\Microsoft\Microsoft Power BI Desktop
valueName: ShowLeadGenDialog
```
Você pode também experimentar a chave a seguir, que tem sido muito útil para alguns clientes com base nas configurações deles:

```
Key: HKEY_CURRENT_USER\SOFTWARE\Microsoft\Microsoft Power BI Desktop
valueName: ShowLeadGenDialog
```

Um valor de 0 desabilitará a caixa de diálogo.




Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)

