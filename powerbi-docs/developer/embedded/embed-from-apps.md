---
title: Inserir relatórios ou dashboards de aplicativos
description: Aprenda como integrar, ou inserir, um relatório ou dashboard de um aplicativo do Power BI e não de um workspace.
author: KesemSharabi
ms.author: kesharab
ms.topic: conceptual
ms.service: powerbi
ms.subservice: powerbi-developer
ms.custom: mvc
ms.date: 11/27/2018
ms.openlocfilehash: 2298350051db947c037c5e2e73f5dc963aa049bc
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/05/2020
ms.locfileid: "80114602"
---
# <a name="embed-reports-or-dashboards-from-apps"></a>Inserir relatórios ou dashboards de aplicativos

No Power BI, você pode criar aplicativos para reunir relatórios e dashboards relacionados, tudo em um só lugar. Em seguida, você os publica para grandes grupos de pessoas em sua organização. O uso desses aplicativos é relevante quando todos os usuários são usuários do Power BI. Portanto, você pode compartilhar conteúdo com eles por meio de aplicativos do Power BI. Este artigo apresenta algumas etapas rápidas para inserir conteúdo de um aplicativo do Power BI publicado em um aplicativo de terceiros.

## <a name="grab-a-report-embedurl-for-embedding"></a>Pegar uma embedURL do relatório para inserção

1. Criar uma instância do aplicativo em um workspace do usuário, **Meu Workspace**. Compartilhe consigo mesmo ou conduza outro usuário a passar por esse fluxo.

2. Abra o relatório desejado no serviço do Power BI.

3. Vá para **Arquivo** > **Inserir no SharePoint Online** e capture a embedURL do relatório. Veja um exemplo de embedURL no instantâneo abaixo. Como alternativa, você pode chamar a API REST GetReports/GetReport e extrair o campo da embedURL do relatório correspondente da resposta. A chamada REST não deve ter um identificador de workspace como parte da URL, uma vez que o aplicativo foi instanciado no workspace do usuário.

    ![Inserir de aplicativos](media/embed-from-apps/embed-from-app.png)

4. Use o embedURL recuperado na etapa 3 com o SDK do JavaScript.

## <a name="grab-a-dashboard-embedurl-for-embedding"></a>Pegar uma embedURL de dashboard para inserção

1. Criar uma instância do aplicativo em um workspace do usuário, **Meu Workspace**. Compartilhe consigo mesmo ou conduza outro usuário a passar por esse fluxo.

2. Chame a API REST de GetDashboards e extraia o campo embedURL do dashboard correspondente da resposta. A chamada REST não deve ter um identificador de workspace como parte da URL, uma vez que o aplicativo foi instanciado no workspace do usuário.

3. Use o embedURL recuperado na etapa 2 com o SDK do JavaScript.

## <a name="next-steps"></a>Próximas etapas

Examine como inserir de workspaces para clientes de terceiros e para a organização:

> [!div class="nextstepaction"]
>[Inserir para clientes de terceiros](embed-sample-for-customers.md)

> [!div class="nextstepaction"]
>[Inserir para a organização](embed-sample-for-your-organization.md)
