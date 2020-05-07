---
title: Instalação automática de aplicativos do Power BI durante a inserção na sua organização
description: Saiba como instalar automaticamente aplicativos do Power BI durante a inserção na sua organização.
ms.subservice: powerbi-developer
author: KesemSharabi
ms.author: kesharab
ms.topic: conceptual
ms.service: powerbi
ms.custom: ''
ms.date: 04/16/2019
ms.openlocfilehash: 0adfb72c408f96749afc8a3d7a6884e10e52fadb
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/05/2020
ms.locfileid: "80114671"
---
# <a name="auto-install-power-bi-apps-when-embedding-for-your-organization"></a>Instale automaticamente aplicativos do Power BI durante a inserção na sua organização

Para inserir o conteúdo de um aplicativo, o usuário que está inserindo deve ter [acesso ao aplicativo](../../service-create-distribute-apps.md). Se o aplicativo for instalado para o usuário, a inserção funcionará sem problemas. Para obter mais informações, confira [Inserir relatórios ou painéis do aplicativo](embed-from-apps.md). É possível definir no PowerBI.com que todos os aplicativos podem ser [instalados automaticamente](https://powerbi.microsoft.com/blog/automatically-install-apps/). No entanto, essa ação é feita no nível de locatário e se aplica a todos os aplicativos.

## <a name="auto-install-app-on-embedding"></a>Aplicativo de instalação automática na inserção

Se um usuário tiver acesso a um aplicativo, mas o aplicativo não estiver instalado, então a inserção falhará. Para evitar essas falhas durante a inserção de um aplicativo, você pode permitir a instalação automática do aplicativo após a inserção. Essa ação significa que, se o aplicativo que o usuário tentar inserir não estiver instalado, ele será instalado automaticamente para você. Portanto, o conteúdo que você deseja é inserido imediatamente, resultando em uma experiência positiva para o usuário.

## <a name="embed-for-power-bi-users-user-owns-data"></a>Inserir para os usuários do Power BI (o usuário tem dados)

Para permitir a instalação automática de aplicativos para seus usuários, você precisa dar ao seu aplicativo a permissão “Criar conteúdo” ao [registrar seu aplicativo](register-app.md#register-with-the-power-bi-application-registration-tool), ou adicioná-lo caso já esteja registrado.

![Registrar o aplicativo cria conteúdo](media/embed-auto-install-app/register-app-create-content.png)

Em seguida, você precisa fornecer a ID do aplicativo na URL de inserção. Para fornecer a ID do aplicativo, o criador do aplicativo primeiro precisa instalar o aplicativo e depois usar uma das chamadas à [API Rest do Power BI](https://docs.microsoft.com/rest/api/power-bi/) compatíveis: [Obter Relatórios](https://docs.microsoft.com/rest/api/power-bi/reports/getreports) ou [Obter Dashboards](https://docs.microsoft.com/rest/api/power-bi/dashboards/getdashboards). Então, o criador do aplicativo precisa levar a URL de inserção da resposta da API REST. A ID do aplicativo aparecerá na URL se o conteúdo for proveniente de um aplicativo.  Depois de ter a URL de inserção, você poderá usá-la para inserir regularmente.

## <a name="secure-embed"></a>Proteger inserção

Para usar a instalação automática de aplicativos, o criador do aplicativo precisa primeiro instalar o aplicativo e depois ir até o aplicativo no PowerBI.com, navegar até o relatório e obter o link de maneira usual. Todos os outros usuários com acesso ao aplicativo autorizados a usar o link podem inserir o relatório.

## <a name="considerations-and-limitations"></a>Considerações e limitações

* Você só pode inserir relatórios e dashboards neste cenário.

* No momento, esse recurso não é compatível com os dados de propriedade de aplicativos e cenários de inserção do SharePoint.