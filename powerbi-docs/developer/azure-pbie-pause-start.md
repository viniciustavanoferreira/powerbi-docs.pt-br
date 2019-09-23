---
title: Pausar e iniciar a capacidade do Power BI Embedded no portal do Azure | Microsoft Docs
description: Este artigo explica como pausar e iniciar uma capacidade do Power BI Embedded no Microsoft Azure.
services: power-bi-embedded
author: rkarlin
ms.author: rkarlin
manager: kfile
editor: ''
tags: ''
ms.service: power-bi-embedded
ms.topic: conceptual
ms.date: 09/28/2017
ms.openlocfilehash: 8a02654f264fb83f501679e4e205e08017f083f6
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "61386953"
---
# <a name="pause-and-start-your-power-bi-embedded-capacity-in-the-azure-portal"></a>Pausar e iniciar a capacidade do Power BI Embedded no portal do Azure

Este artigo explica como pausar e iniciar uma capacidade do Power BI Embedded no Microsoft Azure. Para fazer isso, é necessário já ter criado uma capacidade do Power BI Embedded. Se você ainda não criou, confira [Criar uma capacidade do Power BI Embedded no portal do Azure](azure-pbie-create-capacity.md) para começar.

Se você não tiver uma assinatura do Azure, crie uma [conta gratuita](https://azure.microsoft.com/free/) antes de começar.

## <a name="pause-your-capacity"></a>Pausar sua capacidade

A pausa da sua capacidade evita que você seja cobrado. A pausa da sua capacidade é ideal quando você não precisa usar a capacidade durante um período de tempo. Use as etapas a seguir para pausar a capacidade.

> [!NOTE]
> A pausa de um capacidade pode impedir que o conteúdo fique disponível no Power BI. Cancele a atribuição dos workspaces da sua capacidade antes de pausar para evitar interrupção.

1. Entre no [Portal do Azure](https://portal.azure.com/).

2. Selecione **Todos os serviços** > **Power BI Embedded** para ver suas capacidades.

    ![Todos os serviços no portal do Azure](media/azure-pbie-pause-start/azure-portal-more-services.png)

3. Selecione a capacidade que deseja pausar.

    ![Lista de capacidades do Power BI Embedded no portal do Azure](media/azure-pbie-pause-start/azure-portal-capacity-list.png)

4. Selecione **Pausar** nos detalhes da capacidade.

    ![Pausar sua capacidade](media/azure-pbie-pause-start/azure-portal-pause-capacity.png)

5. Selecione **Sim** para confirmar que você deseja pausar a capacidade.

    ![Confirmar pausa](media/azure-pbie-pause-start/azure-portal-confirm-pause.png)

## <a name="start-your-capacity"></a>Iniciar sua capacidade

Retome o uso iniciando sua capacidade. O início da capacidade também retoma a cobrança.

1. Entre no [Portal do Azure](https://portal.azure.com/).

2. Selecione **Todos os serviços** > **Power BI Embedded** para ver suas capacidades.

    ![Todos os serviços no portal do Azure](media/azure-pbie-pause-start/azure-portal-more-services.png)

3. Selecione a capacidade que você deseja iniciar.

    ![Lista de capacidades do Power BI Embedded no portal do Azure](media/azure-pbie-pause-start/azure-portal-capacity-list.png)

4. Selecione **Iniciar** nos detalhes da capacidade.

    ![Iniciar sua capacidade](media/azure-pbie-pause-start/azure-portal-start-capacity.png)

5. Selecione **Sim** para confirmar que você deseja iniciar a capacidade.

    ![Confirmar início](media/azure-pbie-pause-start/azure-portal-confirm-start.png)

Se algum conteúdo estiver atribuído a essa capacidade, ele ficará disponível após o início.

## <a name="next-steps"></a>Próximas etapas

Se você quiser escalar ou reduzir verticalmente a capacidade, confira [Dimensionar a capacidade do Power BI Embedded](azure-pbie-scale-capacity.md).

Para começar a inserir conteúdo do Power BI em seu aplicativo, confira [Como inserir dashboards, relatórios e blocos do Power BI](https://powerbi.microsoft.com/documentation/powerbi-developer-embedding-content/).

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)