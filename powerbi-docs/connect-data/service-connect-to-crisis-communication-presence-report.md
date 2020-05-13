---
title: Conectar-se ao Relatório de Presença de Comunicação de Crise
description: Como obter e instalar o aplicativo de modelo Relatório de Presença de Comunicação de Crise da COVID-19 e como se conectar aos dados
author: paulinbar
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 04/06/2020
ms.author: painbar
LocalizationGroup: Connect to services
ms.openlocfilehash: fef6bc5c396ccaf89ff4cd0e5a449cb9d01ce75b
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83275491"
---
# <a name="connect-to-the-crisis-communication-presence-report"></a>Conectar-se ao Relatório de Presença de Comunicação de Crise

Este aplicativo do Power BI é o artefato de relatório/dashboard na solução do Microsoft Power Platform para Comunicação de Crise. Ele acompanha a localização do trabalhador para os usuários do aplicativo de Comunicação de Crise. A solução combina funcionalidades do Power Apps, do Power Automate, do Teams, do SharePoint e do Power BI. Ele pode ser usado na Web, em dispositivos móveis ou no Teams.

![Relatório do aplicativo Relatório de Presença de Comunicação de Crise](media/service-connect-to-crisis-communication-presence-report/service-crisis-communication-presence-report.png)

O dashboard mostra aos gestores de emergência os dados agregados no sistema de saúde para ajudá-los a tomar decisões corretas e em tempo hábil.

Este artigo mostra como instalar o aplicativo e como se conectar às fontes de dados. Para obter mais informações sobre o aplicativo Comunicação de Crise, confira [Configurar o modelo de exemplo de Comunicação de Crise e aprender sobre ele no Power Apps](https://docs.microsoft.com/powerapps/maker/canvas-apps/sample-crisis-communication-app)

Depois de instalar o aplicativo de modelo e se conectar às fontes de dados, você poderá personalizar o relatório de acordo com as suas necessidades. Em seguida, poderá distribuí-lo como um aplicativo para os colegas da sua organização.

## <a name="prerequisites"></a>Pré-requisitos

Antes de instalar este aplicativo de modelo, primeiro, você precisará instalar e configurar a [amostra de Comunicação de Crise](https://docs.microsoft.com/powerapps/maker/canvas-apps/sample-crisis-communication-app). A instalação dessa solução cria as referências de fonte de dados necessárias para preencher o aplicativo com os dados.

Ao instalar a amostra de Comunicação de Crise, anote o [caminho da pasta da lista do SharePoint de "CI_Employee Status" e a ID de lista](https://docs.microsoft.com/powerapps/maker/canvas-apps/sample-crisis-communication-app#monitor-office-absences-with-power-bi).

## <a name="install-the-app"></a>Instalar o aplicativo

1. Clique no seguinte link para acessar o aplicativo: [Aplicativo de modelo Relatório de Presença de Comunicação de Crise](https://appsource.microsoft.com/en-us/product/power-bi/pbi-contentpacks.crisiscomms)

1. Na página do aplicativo no AppSource, selecione [**OBTER AGORA**](https://appsource.microsoft.com/en-us/product/power-bi/pbi-contentpacks.crisiscomms).

    [![Aplicativo Relatório de Presença de Comunicação de Crise no AppSource](media/service-connect-to-crisis-communication-presence-report/service-crisis-communication-presence-report-app-appsource-get-it-now.png)](https://appsource.microsoft.com/en-us/product/power-bi/pbi-contentpacks.crisiscomms)

1. Leia as informações em **Mais uma coisa** e selecione **Continuar**.

    ![Aplicativo Relatório de Presença de Comunicação de Crise, Mais uma coisa](media/service-connect-to-crisis-communication-presence-report/service-crisis-communication-presence-report-1-more-thing.png)

1. Selecione **Instalar**. 

    ![Instalar o aplicativo Relatório de Presença de Comunicação de Crise](media/service-connect-to-crisis-communication-presence-report/service-crisis-communication-presence-report-select-install.png)

    Depois que o aplicativo for instalado, você o verá na página Aplicativos.

   ![Aplicativo Relatório de Presença de Comunicação de Crise na página Aplicativos](media/service-connect-to-crisis-communication-presence-report/service-crisis-communication-presence-report-app-apps-page-icon.png)

## <a name="connect-to-data-sources"></a>Conectar-se a fontes de dados

1. Selecione o ícone da página Aplicativos para abrir o aplicativo.

1. Na tela inicial, selecione **Explorar**.

   ![Tela inicial do aplicativo de modelo](media/service-connect-to-crisis-communication-presence-report/service-crisis-communication-presence-report-app-splash-screen.png)

   O aplicativo é aberto, mostrando os dados de exemplo.

1. Selecione o link **Conectar seus dados** na barra de notificação na parte superior da página.

   ![Link Conectar seus dados no aplicativo Relatório de Presença de Comunicação de Crise](media/service-connect-to-crisis-communication-presence-report/service-crisis-communication-presence-report-app-connect-data.png)

1. Na caixa de diálogo:
   1. No campo SharePoint_Folder, insira seu [caminho de lista do SharePoint de "CI_Employee Status"](https://docs.microsoft.com/powerapps/maker/canvas-apps/sample-crisis-communication-app#monitor-office-absences-with-power-bi).
   1. No campo List_ID, insira a ID de lista obtida nas configurações da lista. Quando terminar, clique em **Avançar**.

   ![Caixa de diálogo URL no aplicativo Relatório de Presença de Comunicação de Crise](media/service-connect-to-crisis-communication-presence-report/service-crisis-communication-presence-report-app-url-dialog.png)

1. Na próxima caixa de diálogo exibida, defina o método de autenticação como **OAuth2**. Você não precisará fazer nada na configuração de nível de privacidade.

   Selecione **Entrar**.

   ![Caixa de diálogo de autenticação do aplicativo Relatório de Presença de Comunicação de Crise](media/service-connect-to-crisis-communication-presence-report/service-crisis-communication-presence-report-app-authentication-dialog.png)

1. Na tela de entrada da Microsoft, entre no Power BI.

   ![Tela de entrada da Microsoft](media/service-connect-to-crisis-communication-presence-report/service-crisis-communication-presence-report-app-microsoft-login.png)

   Depois que você se conectar, o relatório se conectará às fontes de dados e será preenchido com os dados atualizados. Durante esse período, o monitor de atividade é ativado.

   ![Atualização em progresso do aplicativo Relatório de Presença de Comunicação de Crise](media/service-connect-to-crisis-communication-presence-report/service-crisis-communication-presence-report-app-refresh-monitor.png)

## <a name="schedule-report-refresh"></a>Agendar atualização do relatório

Quando a atualização de dados for concluída, [configure um agendamento de atualização](../connect-data/refresh-scheduled-refresh.md) para manter os dados do relatório atualizados.

1. Na barra de cabeçalho superior, selecione **Power BI**.

   ![Navegação estrutural do Power BI](media/service-connect-to-crisis-communication-presence-report/service-crisis-communication-presence-report-app-powerbi-breadcrumb.png)

1. No painel de navegação à esquerda, procure o workspace do Dashboard de Suporte a Decisões de Resposta a Emergências Hospitalares em **Workspaces** e siga a instrução descrita no artigo [Configurar a atualização agendada](../connect-data/refresh-scheduled-refresh.md).

## <a name="customize-and-share"></a>Personalizar e compartilhar

Confira [Personalizar e compartilhar o aplicativo](../connect-data/service-template-apps-install-distribute.md#customize-and-share-the-app) para obter detalhes. Examine os [avisos de isenção de responsabilidade do relatório](../create-reports/sample-covid-19-us.md#disclaimers) antes de publicar ou distribuir o aplicativo.

## <a name="next-steps"></a>Próximas etapas
* [Configurar o modelo de exemplo de Comunicação de Crise e aprender sobre ele no Power Apps](https://docs.microsoft.com/powerapps/maker/canvas-apps/sample-crisis-communication-app)
* Dúvidas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
* [O que são os aplicativos de modelo do Power BI?](../connect-data/service-template-apps-overview.md)
* [Instalar e distribuir aplicativos de modelo na sua organização](../connect-data/service-template-apps-install-distribute.md)
