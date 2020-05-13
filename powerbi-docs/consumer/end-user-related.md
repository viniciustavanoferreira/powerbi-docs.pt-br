---
title: Exibir conteúdo relacionado de painéis, relatórios e conjuntos de dados
description: Navegação simplificada, exibição de conteúdo relacionado nos dashboards, relatórios e conjuntos de dados
author: mihart
ms.reviewer: ''
featuredvideoid: B2vd4MQrz4M
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 03/11/2020
ms.author: mihart
LocalizationGroup: Get started
ms.openlocfilehash: 3dcd968d00d98106a8b717e635b8a7fdf958dc70
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83347322"
---
# <a name="view-related-content-in-the-power-bi-service"></a>Exibir conteúdo relacionado no serviço do Power BI

[!INCLUDE[consumer-appliesto-ynny](../includes/consumer-appliesto-ynny.md)]

[!INCLUDE [power-bi-service-new-look-include](../includes/power-bi-service-new-look-include.md)]

O painel **Conteúdo relacionado** mostra como o conteúdo do serviço do Power BI (dashboards, relatórios e conjuntos de dados) está interconectado. O painel **Conteúdo relacionado** também é uma plataforma de lançamento para executar ações. Aqui, é possível abrir um painel, abrir um relatório, gerar insights, analisar os dados no Excel e muito mais.  

No Power BI, os relatórios são gerados a partir de conjuntos de dados, visualizações de relatórios são fixadas em painéis e os elementos visuais dos painéis nos redirecionam aos relatórios. Mas como saber quais painéis hospedam elementos visuais do seu relatório de Marketing? E como localizar esses painéis? O seu painel Compras utiliza elementos visuais de mais de um conjunto de dados? Nesse caso, que nomes receberam e como é possível abri-los e editá-los? Seu conjunto de dados de RH está sendo usado em algum relatório ou painel? Ou, pode ser movido sem desfazer links? Perguntas como essas podem ser todas respondidas no painel **Conteúdo relacionado**.  O painel exibe o conteúdo relacionado, permite que você tenha controle sobre o conteúdo e navegue facilmente pelo conteúdo relacionado.

![conteúdo relacionado](./media/end-user-related/power-bi-list.png)

> [!NOTE]
> O recurso de conteúdo relacionado não funciona em conjuntos de dados de streaming.
> 
> 

## <a name="view-related-content-for-a-dashboard-or-report"></a>Exibir o conteúdo relacionado de um painel ou relatório
Assista Exibirá o conteúdo relacionado de um dashboard. Em seguida, siga as instruções passo a passo abaixo do vídeo para experimentar sozinho com o conjunto de dados exemplo de Análise de compras.

<iframe width="560" height="315" src="https://www.youtube.com/embed/B2vd4MQrz4M#t=3m05s" frameborder="0" allowfullscreen></iframe>

Com um dashboard ou relatório aberto, selecione **Mais opções** (...) na barra de menus e escolha **Exibição relacionada** na lista suspensa.

![Menu suspenso de reticências](./media/end-user-related/power-bi-dropdown.png)

O painel **Conteúdo relacionado** é aberto. Para um painel, ele mostra todos os relatórios com visualizações fixadas no painel e seus conjuntos de dados associados. Para esse painel, há visualizações fixadas de apenas um relatório, e esse relatório tem base em apenas um conjunto de dados. 

![Painel Conteúdo relacionado](./media/end-user-related/power-bi-view-related-dashboard.png)

Neste ponto, você pode controlar diretamente o conteúdo relacionado.  Por exemplo, selecione um nome de relatório ou de painel para abri-lo.  Para um relatório listado, selecione um ícone para [analisar no Excel](../collaborate-share/service-analyze-in-excel.md) ou [obter insights](end-user-insights.md). Para um conjunto de dados, você pode ver a data e hora da última atualização, [analisar no Excel](../collaborate-share/service-analyze-in-excel.md) e [obter insights](end-user-insights.md).  



## <a name="view-related-content-for-a-dataset"></a>Exibir o conteúdo relacionado de um conjunto de dados
É preciso ter no mínimo permissões de *exibição* em um conjunto de dados para abrir o painel **Conteúdo relacionado**. Neste exemplo, estamos usando o [Exemplo de Análise de Compras](../create-reports/sample-procurement.md).

No painel de navegação, localize o cabeçalho **Workspaces** e selecione um workspace na lista. Se houver algum conteúdo em um workspace, ele será exibido na tela à direita. 

![workspaces no painel de navegação](./media/end-user-related/power-bi-workspace.png)


Em um workspace, selecione a guia **Conjuntos de dados** e, em seguida, localize o ícone **Exibição relacionada**![ícone Exibição relacionada](./media/end-user-related/power-bi-view-related-icon-new.png).

![Guia Conjuntos de dados](./media/end-user-related/power-bi-related-dataset.png)

Selecione o ícone para abrir o painel **Conteúdo relacionado**.

![O painel de conteúdo relacionado abre na parte superior da exibição de conteúdo do Power BI](media/end-user-related/power-bi-dataset.png)

Neste ponto, você pode controlar diretamente o conteúdo relacionado. Por exemplo, selecione um nome de dashboard ou de relatório para abri-lo.  Em qualquer painel da lista, selecione um ícone para [compartilhar o painel com outras pessoas](../collaborate-share/service-share-dashboards.md) ou abrir a janela **Configurações** do painel. Para relatórios, selecione um ícone para [analisar no Excel](../collaborate-share/service-analyze-in-excel.md), [renomear](../create-reports/service-rename.md) ou [obter insights](end-user-insights.md).  

## <a name="limitations-and-troubleshooting"></a>Limitações e solução de problemas
* Se você não vir "Exibição relacionada", procure pelo ícone ![ícone Exibição relacionada](./media/end-user-related/power-bi-view-related-icon-new.png). Selecione o ícone para abrir o painel **Conteúdo relacionado**.
* Para abrir o Conteúdo relacionado de um relatório, é preciso estar na [exibição de Leitura](end-user-reading-view.md).
* O recurso Conteúdo relacionado não funciona em conjuntos de dados de streaming.

## <a name="next-steps"></a>Próximas etapas
* [Introdução ao serviço do Power BI](../fundamentals/service-get-started.md)
* Mais perguntas? [Experimente a Comunidade do Power BI](https://community.powerbi.com/)
