---
title: Conectar-se ao Application Insights Conectar-se ao Power BI
description: Application Insights para o Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 08/29/2019
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: 3a41b237ccc4e249d85385b54860f60460efbb31
ms.sourcegitcommit: b53a6f5575f5f8bc443ecdca9c72525ce123518f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2019
ms.locfileid: "70186114"
---
# <a name="connect-to-application-insights-with-power-bi"></a>Conectar-se ao Application Insights com o Power BI
Use o Power BI para criar painéis personalizados eficientes por meio da telemetria do [Application Insights](/azure/application-insights/app-insights-overview/). Preveja a telemetria do seu aplicativo de novas maneiras. Combine métricas de vários aplicativos ou serviços de componente em um único painel. Esta primeira versão do pacote de conteúdo do Power BI para o Application Insights inclui widgets de métricas comuns relacionadas ao uso como usuários ativos, exibição de página, sessões, versão do navegador e do SO e distribuição geográfica de usuários em um mapa.

[!INCLUDE [include-short-name](./includes/service-deprecate-content-packs.md)]

Conecte-se ao [pacote de conteúdo do Application Insights para o Power BI](https://app.powerbi.com/getdata/services/application-insights).

>[!NOTE]
>Esse método de integração foi **preterido**. Para saber mais sobre o método preferencial de conexão do Application Insights com o Power BI use a [funcionalidade de exportação de consulta analítica](https://docs.microsoft.com/azure/application-insights/app-insights-export-power-bi#export-analytics-queries).

## <a name="how-to-connect"></a>Como se conectar
1. Selecione **Obter Dados** na parte inferior do painel de navegação esquerdo.
   
    ![Botão Obter Dados](media/service-connect-to-application-insights/pbi_getdata.png)
2. Na caixa **Serviços** , selecione **Obter**.
   
    ![Botão Obter Serviços](media/service-connect-to-application-insights/pbi_getservices.png)
3. Selecione **Application Insights** > **Obter**.
   
    ![Pacote de conteúdo do Application Insights](media/service-connect-to-application-insights/appinsights.png)
4. Forneça os detalhes do aplicativo ao qual você deseja se conectar, incluindo **Nome de Recurso do Application Insights**, **Grupo de Recursos**e **ID da Assinatura**. Veja [Encontrando os parâmetros do Application Insights](#FindingAppInsightsParams) abaixo para obter mais detalhes.
   
    ![Caixa de diálogo de conexão do Application Insights](media/service-connect-to-application-insights/pbi_contpkappinsitconnectndialog.png)    
5. Selecione **Entrar** e siga as telas para se conectar.
   
    ![Entrada de conexão do Application Insights](media/service-connect-to-application-insights/pbi_contpkappinsitconnectn2.png)
6. O processo de importação é iniciado automaticamente. Quando concluído, uma notificação é mostrada e um novo painel, relatório e conjunto de dados aparecerão no Painel de Navegação, marcados com um asterisco.  Selecione o painel para exibir os dados importados por você.
   
    ![Painel do Application Insights](media/service-connect-to-application-insights/pbi_contpkappinsitdash.png)

**E agora?**

* Tente [fazer uma pergunta na caixa de P e R](consumer/end-user-q-and-a.md) na parte superior do dashboard
* [Altere os blocos](service-dashboard-edit-tile.md) no dashboard.
* [Selecione um bloco](consumer/end-user-tiles.md) para abrir o relatório subjacente.
* Enquanto seu conjunto de dados será agendado para ser atualizado diariamente, você pode alterar o agendamento de atualização ou tentar atualizá-lo sob demanda usando **Atualizar Agora**

## <a name="whats-included"></a>O que está incluído
O pacote de conteúdo do Application Insights inclui as seguintes tabelas e métricas:  

    ´´´
    - ApplicationDetails  
    - UniqueUsersLast7Days   
    - UniqueUsersLast30Days   
    - UniqueUsersDailyLast30Days  
    - UniqueUsersByCountryLast7Days  
    - UniqueUsersByCountryLast30Days   
    - PageViewsDailyLast30Days   
    - SessionsLast7Days   
    - SessionsLast30Days  
    - PageViewsByBrowserVersionDailyLast30Days   
    - UniqueUsersByOperatingSystemLast7Days   
    - UniqueUsersByOperatingSystemLast30Days    
    - SessionsDailyLast30Days   
    - SessionsByCountryLast7Days   
    - SessionsByCountryLast30Days   
    - PageViewsByCountryDailyLast30Days  
    ´´´ 

<a name="FindingAppInsightsParams"></a>

## <a name="finding-parameters"></a>Localizando parâmetros
O Nome de Recurso, Grupo de Recursos e a ID da Assinatura podem ser encontradas no Portal do Azure. A seleção do Nome abrirá uma exibição detalhada, e você poderá usar o menu suspenso Noções Básicas para encontrar todos os valores necessários.

![Parâmetros do Application Insights](media/service-connect-to-application-insights/pbi_contpkappinsitparams.png)

Copie e cole-os nos campos no Power BI:

![Parâmetros do Application Insights](media/service-connect-to-application-insights/pbi_contpkappinsitparam2.png)

## <a name="next-steps"></a>Próximas etapas
[Introdução ao Power BI](service-get-started.md)

[Obter dados no Power BI](service-get-data.md)

