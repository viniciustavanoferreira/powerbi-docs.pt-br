---
title: Comparando o Servidor de Relatórios do Power BI e o serviço do Power BI
description: Este artigo compara os recursos do Servidor de Relatórios do Power BI e o serviço do Power BI.
keywords: ''
author: maggiesMSFT
ms.author: maggies
ms.topic: overview
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.custom: mvc
ms.date: 03/04/2020
ms.openlocfilehash: 7762ace1da913713567b79a9650b3f07aa71146d
ms.sourcegitcommit: 6bbc3d0073ca605c50911c162dc9f58926db7b66
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79381044"
---
# <a name="comparing-power-bi-report-server-and-the-power-bi-service"></a>Comparando o Servidor de Relatórios do Power BI e o serviço do Power BI

O Servidor de Relatórios do Power BI e o serviço do Power BI têm muitas semelhanças e algumas diferenças importantes. Esta tabela explica qual é qual.

## <a name="features-of-power-bi-report-server-and-the-power-bi-service"></a>Recursos do Servidor de Relatórios do Power BI e do serviço do Power BI

| Recursos | Servidor de Relatórios do Power BI | Serviço do Power BI | Observações |
|---------|---------|---------|---------|
| Implantação | Local ou nuvem hospedada | Nuvem | O Servidor de Relatórios do Power BI pode ser implantado em VMs do Azure (nuvem hospedada) se licenciado por meio do Power BI Premium ou SQL do Server Enterprise com Software Assurance|
| Dados de origem | Nuvem e/ou local | Nuvem e/ou local |  |
| Licença | Power BI Premium ou EE do SQL Server com SA (Software Assurance) | Power BI Pro e/ou Power BI Premium | |  
| Ciclo de vida | Política de ciclo de vida moderna | Serviço totalmente gerenciado |  |
| Ciclo de lançamento | Três vezes ao ano (janeiro, maio, setembro) | Uma vez por mês | Correções e recursos mais recentes são fornecidos para o serviço do Power BI primeiro. Um pacote cumulativo de atualizações de recursos das versões de serviço do Power BI Desktop é disponibilizado com cada versão do Servidor de Relatórios do Power BI. A maioria dos outros recursos é disponibilizada somente para o serviço do Power BI. |
| Criar relatórios do Power BI no Power BI Desktop | Sim | Sim |  |
| Criar relatórios do Power BI no navegador | Não | Sim |  |
| Hospedagem e conexão a conjuntos de dados compartilhados do Power BI | Não | Sim | [Introdução aos conjuntos de dados entre espaços de trabalho](../service-datasets-across-workspaces.md) |
| Gateway necessário | Não | Sim para fontes de dados locais |  |
| Streaming em tempo real | Não | Sim | [Streaming em tempo real no Power BI](../service-real-time-streaming.md) |
| Dashboards | Não | Sim | [Dashboards no serviço do Power BI](../consumer/end-user-dashboards.md) |
| Distribuir grupo de relatórios usando aplicativos | Não | Sim | [Criar e publicar aplicativos com dashboards e relatórios](../service-create-distribute-apps.md) |
| Pacotes de Conteúdo | Não | Sim | [Pacotes de conteúdo organizacional: introdução](../service-organizational-content-pack-introduction.md) |
| Conectar-se a serviços como o Salesforce | Sim | Sim | [Conectar-se aos serviços que você usa](../service-connect-to-services.md) com os pacotes de conteúdos no serviço do Power BI. No Servidor de Relatórios do Microsoft Power BI, use conectores certificados para se conectar aos serviços. Consulte [Fontes de dados de relatórios do Power BI no Servidor de Relatórios do Power BI](data-sources.md) para obter mais informações. |
| P e R | Não | Sim | [P e R no serviço do Power BI e Power BI Desktop](../power-bi-tutorial-q-and-a.md) 
| Insights rápidos | Não | Sim | [Gerar automaticamente as informações sobre os dados com o Power BI](../consumer/end-user-insights.md) |
| Analisar no Excel | Não | Sim | [Analisar no Excel](../service-analyze-in-excel.md) 
| Relatórios paginados | Sim | Sim | [Os relatórios paginados estão disponíveis no serviço do Power BI](../paginated-reports/paginated-reports-report-builder-power-bi.md) em versão prévia na capacidade Premium |
| Aplicativos móveis do Power BI | Sim | Sim | [Visão geral de aplicativos móveis no Power BI](../consumer/mobile/mobile-apps-for-mobile-devices.md) |
| Mapas do ARC GIS | Não | Sim | [Mapas do ArcGIS no serviço do Power BI e no Power BI Desktop pelo ESRI](../visuals/power-bi-visualization-arcgis.md) |
| Assinaturas de email para relatórios do Power BI | Não | Sim | [Assine para você ou terceiros](../service-report-subscribe.md) um relatório ou um dashboard no serviço do Power BI |
| Assinaturas de email para relatórios paginados | Sim | Sim | [Obtenha uma assinatura para você e para outras pessoas de relatórios paginados no Serviço do Power BI](../consumer/paginated-reports-subscriptions.md)<br><br>[Entrega de email no Reporting Services](https://docs.microsoft.com/sql/reporting-services/working-with-subscriptions-web-portal)  |
| Alertas de dados | Não | Sim | [Alertas de dados](../service-set-data-alerts.md) no serviço do Power BI
| RLS (Segurança em nível de linha) | Sim | Sim | Disponível nos modos de DirectQuery (fonte de dados) e de Importação <br><br>Segurança em nível de linha do [serviço do Power BI](../service-admin-rls.md) <br><br>RLS (Segurança em Nível de Linha) no [Servidor de Relatórios do Power BI](row-level-security-report-server.md) |
| Sair do modo de tela inteira | Não | Sim | [Modo de tela inteira](../consumer/end-user-focus.md) no serviço do Power BI |
| Colaboração avançada com o Office 365 | Não | Sim | [Colaborar em um workspace](../service-collaborate-power-bi-workspace.md) com o Office 365 |
| Visuais do R | Não | Sim | [Criar visuais R](../desktop-r-visuals.md) no Power BI Desktop e publicá-los no serviço do Power BI. Você não pode salvar relatórios do Power BI com visuais R no Servidor de Relatórios do Power BI.  |
| Versões prévias dos recursos | Não | Sim | [Aceitar recursos de visualização do serviço](../consumer/end-user-preview-features.md) do Power BI |
| Visuais do Power BI | Sim | Sim | [Visuais do Power BI](../developer/visuals/power-bi-custom-visuals.md) |
| Modelos compostos | Não | Sim |
| Power BI Desktop | Versão otimizada para o Servidor de Relatório, disponível para download com o Servidor de Relatório | Versão otimizado para o serviço do Power BI, disponível na Windows Store | [Power BI Desktop para o servidor de relatório](https://powerbi.microsoft.com/report-server/) <br><br> [Power BI Desktop para o serviço do Power BI](https://aka.ms/pbidesktopstore) |

## <a name="next-steps"></a>Próximas etapas

[Instalar o Servidor de Relatório do Power BI](install-report-server.md)
