---
title: Habilitar a sincronização de segmentações
description: Como adicionar o recurso sincronizar segmentações para visuais do Power BI
author: EugeneElkin
ms.author: v-evelk
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 9966475e8bcaccad2090451b47ef09ef0a9af125
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68425012"
---
# <a name="sync-slicers"></a>Sincronizar segmentações

Para dar suporte [Sincronizar segmentações](https://docs.microsoft.com/power-bi/desktop-slicers), o visual de segmentação personalizado deve usar uma API 1.13 ou superior.

O segundo aspecto necessário é habilitar a opção em `capabilities.json` (consulte um exemplo abaixo).

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

Após as alterações em `capabilities.json`, você poderá ver o painel de opções Sincronizar Segmentações quando clicar no visual de segmentação personalizado.

> [!NOTE]
> Se a segmentação tiver mais de um campo (categoria ou medida), o recurso será desabilitado porque o recurso Sincronizar Segmentações não dá suporte a vários campos.

![Painel Sincronizar segmentações](./media/sync-slicers-panel.png)

No painel, você pode ver que sua visibilidade de segmentação e a respectiva filtragem podem ser aplicadas a várias páginas de relatório.
