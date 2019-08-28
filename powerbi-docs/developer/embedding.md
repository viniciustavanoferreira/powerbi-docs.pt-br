---
title: Análise integrada com o Power BI
description: O Power BI oferece APIs para usar análises integradas para seus dashboards e relatórios nos aplicativos. Saiba mais sobre a integração com o Power BI em ambientes de PaaS e SaaS usando software de análise integrada, ferramentas de análise integrada ou ferramentas de business intelligence inseridas.
author: rkarlin
ms.author: rkarlin
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: overview
helpviewer_keywords:
- embedded analytics
- embedding
- Power BI embedding
- app owns data
- user owns data
- Power BI APIs
ms.custom: seodec18
ms.date: 05/15/2019
ms.openlocfilehash: 8154370a78f418148381c201ba0c2bd50d8ae021
ms.sourcegitcommit: 24781cdab5fbe43fc14248db636169cc54ef6721
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66497906"
---
# <a name="embedded-analytics-with-power-bi"></a>Análise integrada com o Power BI

O serviço do Power BI (SaaS) e o serviço do Power BI Embedded no Azure (PaaS) têm APIs para inserir seus painéis e seus relatórios. Ao inserir um conteúdo, isso fornece acesso aos recursos mais recentes do Power BI, como dashboards, gateways e workspaces do aplicativo.

É possível acessar a [Ferramenta de configuração de inserção](https://aka.ms/embedsetup) para começar rapidamente e baixar um aplicativo de exemplo.

Escolha a solução certa para você:

* A [inserção para a organização](embedding.md#embedding-for-your-organization) permite que você estenda o serviço do Power BI. Para fazer isso, implemente a solução [Inserção para a organização](https://aka.ms/embedsetup/UserOwnsData).
* A [Inserção para os clientes](embedding.md#embedding-for-your-customers) permite que você insira dashboards e relatórios para usuários que não têm uma conta do Power BI. Para fazer isso, implemente a solução [Inserção para os clientes](https://aka.ms/embedsetup/AppOwnsData).

![Exemplo de PBIE](media/what-can-you-do/what-can-you-do-02.png)

## <a name="use-apis"></a>Usar APIs

Há dois cenários principais para a inserção de conteúdo do Power BI:
- Inserção para os usuários de sua organização (que têm licenças do Power BI). 
 
- Inserção para os usuários e os clientes sem a necessidade de licenças do Power BI. 

A [API REST do Power BI](https://docs.microsoft.com/rest/api/power-bi/) permite os dois cenários.

Para clientes e usuários sem licenças do Power BI, você pode inserir painéis e relatórios em seu aplicativo personalizado, usando a mesma API para atender a organização ou os clientes. Os clientes veem os dados gerenciados pelo aplicativo. Além disso, os usuários do Power BI de sua organização têm opções adicionais para exibir *seus próprios dados* diretamente no Power BI ou no contexto do aplicativo inserido. Você pode se beneficiar das APIs REST e do JavaScript para suas necessidades de inserção.

Para entender como funciona a inserção, confira a [amostra de inserção do JavaScript](https://microsoft.github.io/PowerBI-JavaScript/demo/).

## <a name="embedding-for-your-organization"></a>Inserção para a organização

A **inserção para a organização** permite que você estenda o serviço do Power BI. Esse tipo de inserção exige a entrada dos usuários de seu aplicativo no serviço do Power BI para exibir o conteúdo. Depois que alguém na organização se conectar, esse usuário só terá acesso aos dashboards e relatórios dos quais ele é proprietário ou que alguém compartilhou com ele no serviço do Power BI.

Os exemplos de inserção para a organização incluem aplicativos internos, como [SharePoint Online](https://powerbi.microsoft.com/blog/integrate-power-bi-reports-in-sharepoint-online/), [integração do Microsoft Teams](https://powerbi.microsoft.com/blog/power-bi-teams-up-with-microsoft-teams/) (é necessário ter direitos de administrador) e [Microsoft Dynamics](https://docs.microsoft.com/dynamics365/customer-engagement/basics/add-edit-power-bi-visualizations-dashboard).

Para inserção para a sua organização, confira [Tutorial: Inserir o conteúdo do Power BI em um aplicativo para a sua organização](embed-sample-for-your-organization.md).

Recursos de autoatendimento, como editar, salvar e muito mais, estão disponíveis por meio de [API JavaScript](https://github.com/Microsoft/PowerBI-JavaScript) ao inserir para usuários do Power BI.

Examine a [Ferramenta de experiência de inserção](https://aka.ms/embedsetup/UserOwnsData) para começar e baixar um aplicativo de exemplo que explica como integrar um relatório para a sua organização.

## <a name="embedding-for-your-customers"></a>Inserção para os clientes

A **inserção para os clientes** permite que você insira dashboards e relatórios para usuários que não têm uma conta do Power BI. Esse tipo de inserção também é conhecido como *Power BI Embedded*.

O [Power BI Embedded](azure-pbie-what-is-power-bi-embedded.md) é um serviço do **Microsoft Azure** que permite que ISVs (fornecedores independentes de software) e desenvolvedores insiram rapidamente visuais, relatórios e dashboards. Essa inserção é feita por meio de um modelo medido por hora baseado na capacidade.

![Fluxo de inserção ao inserir para os clientes](media/embedding/powerbi-embed-flow.png)

O Power BI Embedded fornece benefícios para um ISV, seus desenvolvedores e clientes. Por exemplo, um ISV pode começar a criar elementos visuais gratuitamente com o Power BI Desktop. Minimizando os esforços de desenvolvimento de análise visual, os ISVs obtêm um tempo de lançamento no mercado mais rápido e se destacam em relação à concorrência com experiências de dados diferenciadas. Os ISVs também podem optar por cobrar uma taxa para o valor adicional criado com a análise integrada.

Com o Power BI Embedded, seus clientes não precisam saber nada sobre o Power BI. Você pode usar dois métodos diferentes para criar um aplicativo inserido:
- Conta do Power BI Pro 
- Entidade de serviço 

A conta do Power BI Pro funciona como uma conta mestra de seu aplicativo (pense nela como uma conta proxy). Essa conta permite que você gere tokens de inserção que fornecem acesso a relatórios e dashboards do Power BI de seu aplicativo.

[Entidade de serviço](embed-service-principal.md) pode inserir o conteúdo do Power BI em um aplicativo usando um token **somente de aplicativo**. Ela também permite que você gere tokens de inserção que fornecem acesso a relatórios e dashboards do Power BI no seu aplicativo.

Os desenvolvedores que usam o Power BI Embedded podem passar o tempo concentrados na criação da funcionalidade principal de seus aplicativos, em vez de gastar tempo desenvolvendo visuais e análise. Eles podem atender rapidamente às demandas de dashboards e relatórios do cliente e inseri-los com facilidade com APIs e SDKs totalmente documentados. Ao habilitar a exploração de dados fácil de navegar em aplicativos, os ISVs permitem que seus clientes tomem decisões rápidas e direcionadas a dados no contexto em qualquer dispositivo.

> [!IMPORTANT]
> Embora a inserção exija o serviço do Power BI, os clientes não precisam ter uma conta do Power BI para exibir o conteúdo inserido de seu aplicativo. 

Quando você estiver pronto para passar para a produção, seu workspace do aplicativo deverá ser atribuído a uma capacidade dedicada. O Power BI Embedded no Microsoft Azure oferece [capacidades dedicadas](azure-pbie-create-capacity.md) a serem usadas com seus aplicativos.

Para obter os detalhes da inserção, confira [Como inserir o conteúdo do Power BI](embed-sample-for-customers.md).

## <a name="next-steps"></a>Próximas etapas

Agora você pode tentar inserir o conteúdo do Power BI em um aplicativo ou tentar inserir o conteúdo do Power BI para seus clientes.

> [!div class="nextstepaction"]
> [Inserir para a organização](embed-sample-for-your-organization.md)

> [!div class="nextstepaction"]
> [O que é o Power BI Embedded?](azure-pbie-what-is-power-bi-embedded.md)

> [!div class="nextstepaction"]
>[Inserir para seus clientes](embed-sample-for-customers.md)

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)
