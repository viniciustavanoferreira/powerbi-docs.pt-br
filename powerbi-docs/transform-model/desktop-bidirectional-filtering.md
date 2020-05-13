---
title: Filtragem cruzada bidirecional no Power BI Desktop
description: Habilitar a filtragem cruzada usando o DirectQuery no Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/15/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 141dabdce7816d21c49d8c7f98d1438c2fc20e8d
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83339089"
---
# <a name="enable-bidirectional-cross-filtering-for-directquery-in-power-bi-desktop"></a>Habilitar a filtragem cruzada bidirecional para o DirectQuery no Power BI Desktop

Ao filtrar tabelas para criar a exibição apropriada dos dados, os criadores de relatórios e os modeladores de dados enfrentam desafios que determinam como aplicar filtros a um relatório. Antes, o contexto de filtro da tabela era mantido em um lado do relacionamento, mas não no outro. Essa disposição geralmente exigia uma fórmula DAX complexa para obter os resultados desejados.

Com a filtragem cruzada bidirecional, os criadores de relatório e os modeladores de dados agora têm mais controle sobre como aplicar filtros ao trabalhar com tabelas relacionadas. A filtragem cruzada bidirecional permite aplicar filtros em *ambos* os lados de uma relação de tabela. Você pode aplicar os filtros propagando o contexto de filtro para uma segunda tabela relacionada no outro lado de um relacionamento de tabela.

## <a name="enable-bidirectional-cross-filtering-for-directquery"></a>Habilitar filtragem cruzada bidirecional para o DirectQuery

Você pode habilitar a filtragem cruzada na caixa de diálogo **Editar relacionamento**. Para habilitar a filtragem cruzada para um relacionamento, configure as seguintes opções:

* Defina **Direção do filtro cruzado** como **Ambas**.
* Selecione **Aplicar filtro de segurança em ambas as direções**.

  ![Configure a filtragem cruzada bidirecional no Power BI Desktop.](media/desktop-bidirectional-filtering/bidirectional-filtering_2.png)

> [!NOTE]
> Ao criar fórmulas DAX de filtragem cruzada no Power BI Desktop, use *UserPrincipalName*. Esse campo geralmente é igual ao logon de um usuário, por exemplo <em>joe@contoso.com</em>, em vez de *UserName*. Assim, talvez seja necessário criar uma tabela relacionada que mapeie *UserName* ou *EmployeeID* para *UserPrincipalName*.

Para obter mais informações e exemplos de como funciona a filtragem cruzada bidirecional, confira o [white paper sobre Filtragem cruzada bidirecional para Power BI Desktop](https://download.microsoft.com/download/2/7/8/2782DF95-3E0D-40CD-BFC8-749A2882E109/Bidirectional%20cross-filtering%20in%20Analysis%20Services%202016%20and%20Power%20BI.docx).

