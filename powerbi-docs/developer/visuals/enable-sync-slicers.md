---
title: Habilitar o recurso Sincronizar Segmentação de Dados em visuais do Power BI
description: Este artigo descreve como adicionar o recurso Sincronizar Segmentação de Dados a visuais do Power BI.
author: KesemSharabi
ms.author: kesharab
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 47f0148528d1ccfd451aa8e8ed87b4bec99d087e
ms.sourcegitcommit: e2de2e8b8e78240c306fe6cca820e5f6ff188944
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71194387"
---
# <a name="sync-slicers-in-power-bi-visuals"></a>Sincronizar segmentação de dados em visuais do Power BI

Para dar suporte ao recurso [Sincronizar Segmentação de Dados](https://docs.microsoft.com/power-bi/desktop-slicers), o visual de segmentação personalizada deve usar a API versão 1.13 ou posterior.

Além disso, você precisa habilitar a opção no arquivo *capabilities.json* conforme mostra o código a seguir:

```json
{
    ...
    "supportsHighlight": true,
    "suppressDefaultTitle": true,
    "supportsSynchronizingFilterState": true,
    "sorting": {
        "default": {}
    }
}
```

Depois de atualizar o arquivo *capabilities.json*, você poderá exibir o painel de opções **Sincronizar segmentação de dados** quando selecionar visual de segmentação personalizada.

> [!NOTE]
> O recurso Sincronizar Segmentação de Dados não é compatível com mais de um campo. Se a segmentação tiver mais de um campo (**Categoria** ou **Medida**), o recurso será desabilitado.

![O painel "Segmentações de dados de sincronização"](./media/sync-slicers-panel.png)

No painel **Segmentação de dados de sincronização**, você pode ver que a sua visibilidade de segmentação e sua filtragem podem ser aplicadas a várias páginas de relatório.
