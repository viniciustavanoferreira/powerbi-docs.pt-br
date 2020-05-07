---
title: Dimensionar a capacidade do Power BI Embedded | Microsoft Docs
description: Este artigo explica como dimensionar uma capacidade do Power BI Embedded no Microsoft Azure.
services: power-bi-embedded
author: KesemSharabi
ms.author: kesharab
editor: ''
tags: ''
ms.service: power-bi-embedded
ms.topic: conceptual
ms.date: 01/31/2019
ms.openlocfilehash: 365f24ec80d58297a852fa3d040c04c8c763eeda
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/05/2020
ms.locfileid: "80114694"
---
# <a name="scale-your-power-bi-embedded-capacity-in-the-azure-portal"></a>Dimensionar a capacidade do Power BI Embedded no portal do Azure

Este artigo explica como dimensionar uma capacidade do Power BI Embedded no Microsoft Azure. O dimensionamento permite aumentar ou diminuir o tamanho de sua capacidade.

Para fazer isso, é necessário já ter criado uma capacidade do Power BI Embedded. Se você ainda não criou, confira [Criar uma capacidade do Power BI Embedded no portal do Azure](azure-pbie-create-capacity.md) para começar.

> [!NOTE]
> Uma operação de dimensionamento pode levar cerca de um minuto. Durante esse tempo, a capacidade não estará disponível. O carregamento do conteúdo inserido pode falhar.

## <a name="scale-a-capacity"></a>Dimensionar uma capacidade

1. Entre no [Portal do Azure](https://portal.azure.com/).

2. Selecione **Todos os serviços** > **Power BI Embedded** para ver suas capacidades.

    ![Todos os serviços no portal do Azure](media/azure-pbie-scale-capacity/azure-portal-more-services.png)

3. Selecione a capacidade que você deseja dimensionar.

    ![Lista de capacidades do Power BI Embedded no portal do Azure](media/azure-pbie-scale-capacity/azure-portal-capacity-list.png)

4. Selecione **Tipo de preço** em **Dimensionar** dentro de sua capacidade.

    ![Opção de tipo de preço em escala](media/azure-pbie-scale-capacity/azure-portal-scale-pricing-tier.png)

    O tipo de preço atual está contornado em azul.

    ![Tipo de preço atual contornado em azul](media/azure-pbie-scale-capacity/azure-portal-current-tier.png)

5. Para escalar ou reduzir verticalmente, selecione o novo tipo para o qual deseja mudar. A seleção de um novo tipo coloca um contorno tracejado azul ao redor da seleção. Clique em **Selecionar** para dimensionar para o novo tipo.

    ![Selecionar o novo tipo](media/azure-pbie-scale-capacity/azure-portal-select-new-tier.png)

    O dimensionamento da capacidade pode levar um ou dois minutos para ser concluído.

6. Confirme o tipo exibindo a guia de visão geral. O tipo de preço atual está listado.

    ![Confirmar tipo atual](media/azure-pbie-scale-capacity/azure-portal-confirm-tier.png)

## <a name="next-steps"></a>Próximas etapas

Para pausar ou iniciar sua capacidade, confira [Pausar e iniciar a capacidade do Power BI Embedded no portal do Azure](azure-pbie-pause-start.md).

Para começar a inserir conteúdo do Power BI em seu aplicativo, confira [Como inserir dashboards, relatórios e blocos do Power BI](https://powerbi.microsoft.com/documentation/powerbi-developer-embedding-content/).

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
