---
title: Conectar-se ao Dashboard de Resposta a Emergências Regionais
description: Como obter e instalar o Dashboard de Suporte a Decisões sobre a COVID-19 para o aplicativo de modelo de resposta a emergências regionais e como se conectar aos dados
author: paulinbar
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 04/24/2020
ms.author: painbar
LocalizationGroup: Connect to services
ms.openlocfilehash: 6af8568dc39544ce064643c8dfb80fa2932cf13a
ms.sourcegitcommit: 834cad24901f7fd966c4010e36a7904bc120e57f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/24/2020
ms.locfileid: "82149660"
---
# <a name="connect-to-the-regional-emergency-response-dashboard"></a>Conectar-se ao Dashboard de Resposta a Emergências Regionais
O Dashboard de Resposta a Emergências Regionais é o componente de relatório da [solução de Resposta a Emergências Regionais do Microsoft Power Platform](https://docs.microsoft.com/powerapps/sample-apps/regional-emergency-response/overview). Os administradores da organização regional podem ver o dashboard nos respectivos locatários do Power BI, permitindo a eles que vejam rapidamente dados e métricas importantes que os ajudarão a tomar decisões eficientes.

![Relatório do aplicativo Dashboard de Resposta a Emergências Regionais](media/service-connect-to-regional-emergency-response/service-regional-emergency-response-app-report.png)

Este artigo mostra como instalar o aplicativo de Resposta a Emergências Regionais usando o aplicativo de modelo Dashboard de Resposta a Emergências Regionais e como se conectar às fontes de dados.

Para obter informações detalhadas sobre o que é apresentado no dashboard, confira [Obter insights](https://docs.microsoft.com/powerapps/sample-apps/regional-emergency-response/portals-admin-reporting#get-insights).

Depois de instalar o aplicativo de modelo e se conectar às fontes de dados, você poderá personalizar o relatório de acordo com as suas necessidades. Em seguida, poderá distribuí-lo como um aplicativo para os colegas da sua organização.

## <a name="prerequisites"></a>Pré-requisitos

Antes de instalar esse aplicativo de modelo, primeiro, você precisará instalar e configurar a [solução de Resposta a Emergências Regionais](https://docs.microsoft.com/powerapps/sample-apps/regional-emergency-response/deploy). A instalação dessa solução cria as referências de fonte de dados necessárias para preencher o aplicativo com os dados.

Ao instalar a solução de Resposta a Emergências Regionais, anote a [URL da instância de ambiente do Common Data Service](https://docs.microsoft.com/powerapps/sample-apps/regional-emergency-response/deploy#step-5-configure-and-publish-power-bi-dashboard). Você precisará dela para conectar o aplicativo de modelo aos dados.

## <a name="install-the-app"></a>Instalar o aplicativo

1. Clique no seguinte link para acessar o aplicativo: [Aplicativo de modelo Dashboard de Resposta a Emergências Regionais](https://appsource.microsoft.com/product/power-bi/powerapps_cxo.regional_response)

1. Na página do aplicativo no AppSource, selecione [**OBTER AGORA**](https://appsource.microsoft.com/product/power-bi/powerapps_cxo.regional_response).

    [![Aplicativo Dashboard de Resposta a Emergências Regionais no AppSource](media/service-connect-to-regional-emergency-response/service-regional-emergency-response-app-appsource-get-it-now.png)](https://appsource.microsoft.com/product/power-bi/powerapps_cxo.regional_response)

1. Selecione **Instalar**. 

    ![Instalar o aplicativo Dashboard de Resposta a Emergências Regionais](media/service-connect-to-regional-emergency-response/service-regional-emergency-response-select-install.png)

    Depois que o aplicativo for instalado, você o verá na página Aplicativos.

   ![Aplicativo Dashboard de Resposta a Emergências Regionais na página Aplicativo](media/service-connect-to-regional-emergency-response/service-regional-emergency-response-app-apps-page-icon.png)

## <a name="connect-to-data-sources"></a>Conectar-se a fontes de dados

1. Selecione o ícone da página Aplicativos para abrir o aplicativo.

1. Na tela inicial, selecione **Explorar**.

   ![Tela inicial do aplicativo de modelo](media/service-connect-to-regional-emergency-response/service-regional-emergency-response-app-splash-screen.png)

   O aplicativo é aberto, mostrando os dados de exemplo.

1. Selecione o link **Conectar seus dados** na barra de notificação na parte superior da página.

   ![Link Conectar seus dados no aplicativo Dashboard de Resposta a Emergências Regionais](media/service-connect-to-regional-emergency-response/service-regional-emergency-response-app-connect-data.png)

1. Na caixa de diálogo exibida, digite a [URL da instância de ambiente do Common Data Service](https://docs.microsoft.com/powerapps/sample-apps/emergency-response/deploy-configure#publish-the-power-bi-dashboard). Por exemplo: https://[meuambiente].crm.dynamics.com. Quando terminar, clique em **Avançar**.

   ![Caixa de diálogo da URL do aplicativo Dashboard de Resposta a Emergências Regionais](media/service-connect-to-regional-emergency-response/service-regional-emergency-response-app-url-dialog.png)

1. Na próxima caixa de diálogo exibida, defina o método de autenticação como **OAuth2**. Você não precisará fazer nada na configuração de nível de privacidade.

   Selecione **Entrar**.

   ![Caixa de diálogo de autenticação do aplicativo Dashboard de Resposta a Emergências Regionais](media/service-connect-to-regional-emergency-response/service-regional-emergency-response-app-authentication-dialog.png)

1. Na tela de entrada da Microsoft, entre no Power BI.

   ![Tela de entrada da Microsoft](media/service-connect-to-regional-emergency-response/service-regional-emergency-response-app-microsoft-login.png)

   Depois que você se conectar, o relatório se conectará às fontes de dados e será preenchido com os dados atualizados. Durante esse período, o monitor de atividade é ativado.

   ![Atualização em andamento do aplicativo Dashboard de Resposta a Emergências Regionais](media/service-connect-to-regional-emergency-response/service-regional-emergency-response-app-refresh-monitor.png)

## <a name="schedule-report-refresh"></a>Agendar atualização do relatório

Quando a atualização de dados for concluída, [configure um agendamento de atualização](../refresh-scheduled-refresh.md) para manter os dados do relatório atualizados.

1. Na barra de cabeçalho superior, selecione **Power BI**.

   ![Navegação estrutural do Power BI](media/service-connect-to-regional-emergency-response/service-regional-emergency-response-app-powerbi-breadcrumb.png)

1. No painel de navegação à esquerda, procure o workspace do Dashboard de Resposta a Emergências Regionais em **Workspaces** e siga as instruções descritas no artigo [Configurar a atualização agendada](../refresh-scheduled-refresh.md).

## <a name="customize-and-share"></a>Personalizar e compartilhar

Confira [Personalizar e compartilhar o aplicativo](../service-template-apps-install-distribute.md#customize-and-share-the-app) para obter detalhes. Examine os [avisos de isenção de responsabilidade do relatório](https://docs.microsoft.com/powerapps/sample-apps/regional-emergency-response/overview#disclaimer) antes de publicar ou distribuir o aplicativo.

## <a name="next-steps"></a>Próximas etapas
* [Noções básicas sobre o dashboard de Resposta a Emergências Regionais](https://docs.microsoft.com/powerapps/sample-apps/regional-emergency-response/portals-admin-reporting#get-insights)
* [Configurar o modelo de exemplo de Comunicação de Crise e aprender sobre ele no Power Apps](https://docs.microsoft.com/powerapps/maker/canvas-apps/sample-crisis-communication-app)
* Dúvidas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
* [O que são os aplicativos de modelo do Power BI?](../service-template-apps-overview.md)
* [Instalar e distribuir aplicativos de modelo na sua organização](../service-template-apps-install-distribute.md)
