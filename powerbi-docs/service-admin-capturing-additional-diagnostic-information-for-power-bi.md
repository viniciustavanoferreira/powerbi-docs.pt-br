---
title: Capturar informações adicionais de diagnóstico
description: Estas instruções fornecem duas opções possíveis para coletar manualmente as informações adicionais de diagnóstico do cliente Web Power BI.
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 09/17/2019
ms.author: kfollis
ms.custom: seodec18
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 670373afb5cb890c87a24a129cd43fde7bd5d892
ms.sourcegitcommit: 6272c4a0f267708ca7d38a45774f3bedd680f2d6
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/06/2020
ms.locfileid: "74698890"
---
# <a name="capture-additional-diagnostic-information-for-power-bi"></a>Capturar informações adicionais de diagnóstico para o Power BI

Este artigo fornece instruções para coletar manualmente informações adicionais de diagnóstico do cliente Web do Power BI.

1. Navegue até o [Power BI](https://app.powerbi.com) com o Microsoft Edge ou o Internet Explorer.

1. Pressione **F12** para abrir as Ferramentas de Desenvolvedor do Microsoft Edge.

   ![Captura de tela da guia Elementos das Ferramentas de Desenvolvedor do Microsoft Edge.](media/service-admin-capturing-additional-diagnostic-information-for-power-bi/edge-developer-tools.png)

1. Selecione a guia **Rede**. Ele listará o tráfego que já foi capturado.

   ![Captura de tela da guia Rede das Ferramentas de Desenvolvedor do Microsoft Edge.](media/service-admin-capturing-additional-diagnostic-information-for-power-bi/edge-network-tab.png)

    Você pode:

    * Navegue na janela e reproduza qualquer problema que possa estar ocorrendo.

    * Oculte e exiba a janela Ferramentas de Desenvolvedor a qualquer momento durante a sessão pressionando F12.

1. Para interromper sessão de criação de perfil, clique no quadrado vermelho na guia **Rede** da área de ferramentas do desenvolvedor.

   ![Captura de tela da guia Rede das Ferramentas do Desenvolvedor do Microsoft Edge com um texto explicativo no botão Parar.](media/service-admin-capturing-additional-diagnostic-information-for-power-bi/edge-network-tab-stop.png)

1. Escolha o ícone de disquete para exportar os dados como um arquivo HTTP Archive (HAR).

   ![Captura de tela da guia Rede das Ferramentas do Desenvolvedor do Microsoft Edge com um texto explicativo no ícone de disquete.](media/service-admin-capturing-additional-diagnostic-information-for-power-bi/edge-network-tab-save.png)

1. Forneça um nome de arquivo e salve o arquivo HAR.

    O arquivo HAR contém todas as informações sobre solicitações de rede entre a janela do navegador e o Power BI, incluindo:

    * As IDs de atividade de cada solicitação.

    * O carimbo de data/hora preciso de cada solicitação.

    * Quaisquer informações de erro retornadas para o cliente.

    Este rastreamento também conterá os dados usados para preencher os elementos visuais mostrados na tela.

1. Você pode fornecer o arquivo HAR para dar suporte à análise.

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
