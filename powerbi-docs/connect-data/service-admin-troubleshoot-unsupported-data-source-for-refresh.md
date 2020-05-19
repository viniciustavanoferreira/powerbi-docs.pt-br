---
title: Solucionando problemas de fonte de dados sem suporte para atualização
description: Solucionando problemas de fonte de dados sem suporte para atualização
author: maggiesMSFT
ms.reviewer: kayu
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: troubleshooting
ms.date: 05/08/2020
ms.author: maggies
ms.custom: seodec18
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 50eb4f0fd50c49a39363093ea600922c61ebfab4
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83324116"
---
# <a name="troubleshooting-unsupported-data-source-for-refresh"></a>Solucionando problemas de fonte de dados sem suporte para atualização
Você verá um erro ao tentar configurar um conjunto de dados para atualização agendada.

        You cannot schedule refresh for this dataset because it gets data from sources that currently don’t support refresh.

Isso acontece quando a fonte de dados usada no Power BI Desktop não dá suporte para atualização. Você precisará encontrar a fonte de dados que está usando e compará-la com a lista de fontes de dados com suporte em [Atualizar dados no Power BI](refresh-data.md). 

## <a name="find-the-data-source"></a>Encontrar a fonte de dados
Se você não tiver certeza de qual fonte de dados foi usada, você pode encontrar usando as seguintes etapas no Power BI Desktop.  

1. No Power BI Desktop, tenha certeza de que está no painel **Relatório** .  
   ![Painel de relatório de área de trabalho](media/service-admin-troubleshoot-unsupported-data-source-for-refresh/tshoot-report-pane.png)
2. Selecione **Editar Consultas** na barra da faixa de opções.  
   ![Editar consultas](media/service-admin-troubleshoot-unsupported-data-source-for-refresh/tshoot-edit-queries.png)
3. Selecione **Editor Avançado**.  
   ![Editor avançado](media/service-admin-troubleshoot-unsupported-data-source-for-refresh/tshoot-advanced-editor.png)
4. Anote o provedor listado para a fonte.  Neste exemplo, o provedor é Active Directory.  
   ![Provedor de fonte de dados](media/service-admin-troubleshoot-unsupported-data-source-for-refresh/tshoot-provider.png)
5. Compare o provedor com a lista de fontes de dados com suporte encontrada em [Fontes de dados do Power BI](power-bi-data-sources.md).

> [!NOTE]
> Para problemas de atualização relacionados a fontes de dados dinâmicas, incluindo fontes de dados que possuem consultas criadas manualmente, confira [Atualização e fontes de dados dinâmicas](refresh-data.md#refresh-and-dynamic-data-sources).


## <a name="next-steps"></a>Próximas etapas
[Atualização de dados](refresh-data.md)  
[Gateway do Power BI – Pessoal](service-gateway-personal-mode.md)  
[On-premises data gateway (Gateway de dados local)](service-gateway-onprem.md)  
[Solução de problemas do gateway de dados local](service-gateway-onprem-tshoot.md)  
[Solução de problemas do Gateway do Power BI – Pessoal](service-admin-troubleshooting-power-bi-personal-gateway.md)  

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
