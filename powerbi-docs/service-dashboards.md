---
title: Introdução a dashboards para designers do Power BI
description: Os dashboards são um recurso chave do serviço do Power BI. Eles são uma única página, geralmente chamada de tela, que conta uma história por meio de visualizações.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 09/19/2019
ms.author: maggies
LocalizationGroup: Dashboards
ms.openlocfilehash: eb2c513e8ee8ad1c8ad93866f688e40f6c5af56d
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/05/2020
ms.locfileid: "76160778"
---
# <a name="introduction-to-dashboards-for-power-bi-designers"></a>Introdução a dashboards para designers do Power BI

Um *dashboard* do Power BI é uma página única, geralmente chamada de tela, que conta uma história por meio de visualizações. Por ser limitado a uma única página, um dashboard bem projetado contém apenas os elementos mais importantes da história. Os leitores podem exibir relatórios relacionados para obter detalhes.

![Painel](media/service-dashboards/power-bi-dashboard2.png)

Dashboards são um recurso do serviço do Power BI apenas. Eles não estão disponíveis no Power BI Desktop. Embora não seja possível criar dashboards em dispositivos móveis, você pode [exibir e compartilhar](mobile-apps-view-dashboard.md) os dashboards lá.

## <a name="dashboard-basics"></a>Noções básicas de dashboard 

As visualizações que você vê no dashboard são chamadas de *blocos*. Você *fixa* blocos em um painel de relatórios. Se for novo no Power BI, você poderá ter uma boa base lendo [Conceitos básicos para designers no serviço do Power BI](service-basic-concepts.md).

As visualizações em um dashboard são originadas de relatórios e cada um deles é baseado em um conjunto de dados. Uma maneira de pensar em um dashboard é como uma porta de entrada para os relatórios e os conjuntos de dados subjacentes. Selecionar uma visualização leva você para o relatório (e o conjunto de dados) em que ela é baseada.

![Diagrama mostrando a relação entre dashboards, relatórios, conjuntos de dados](media/service-dashboards/power-bi-diagram.png)

## <a name="advantages-of-dashboards"></a>Vantagens dos dashboards
Os dashboards são uma ótima maneira de monitorar seus negócios e ver todas as suas métricas mais importantes rapidamente. As visualizações em um dashboard podem vir de um conjunto de dados subjacente ou de muitos e de um relatório subjacente ou de muitos. Um dashboard combina dados locais e na nuvem, proporcionando uma exibição consolidada independentemente do local em que os dados residem.

Dashboards não são apenas uma bela imagem. É altamente interativo e os blocos são atualizados conforme os dados subjacentes mudam.

## <a name="who-can-create-a-dashboard"></a>Quem pode criar um painel?
A capacidade de criar um dashboard é considerada um recurso do *criador* e requer permissões de edição para o relatório. As permissões de edição estão disponíveis para os criadores do relatório e os colegas aos quais o criador concede acesso. Por exemplo, se David criar um relatório no espaço de trabalho ABC e adicionar você como membro desse espaço de trabalho, você e David terão permissão de edição. Por outro lado, se um relatório tiver sido compartilhado com você diretamente ou como parte de um [aplicativo do Power BI](service-create-distribute-apps.md), você está *consumindo* o relatório. Não é possível fixar blocos ao painel. 

> [!IMPORTANT]
> Você precisa de uma licença do [Power BI Pro](service-free-vs-pro.md) para criar painéis em workspaces. Você pode criar painéis em seu próprio Meu Workspace sem uma licença do Power BI Pro.


## <a name="dashboards-versus-reports"></a>Dashboards versus relatórios
[Relatórios](service-reports.md) e painéis parecem semelhantes, pois são ambos são telas preenchidas com visualizações. Mas há grandes diferenças, como você pode ver na tabela a seguir.

| **Funcionalidade** | **Painéis** | **Relatórios** |
| --- | --- | --- |
| Páginas |Uma página |Uma ou mais páginas |
| Fontes de dados |Um ou mais relatórios e um ou mais conjuntos de dados por dashboard |Um único conjunto de dados por relatório |
| Disponível no Power BI Desktop |Não | Sim. Pode criar e exibir relatórios no Power BI Desktop |
| Assinatura |Sim. Pode assinar um dashboard |Sim. Pode assinar uma página de relatório |
| Filtragem |Não. Não é possível filtrar ou fatiar |Sim. Diferentes maneiras de filtrar, realçar e fatiar |
| Em destaque |Sim. Pode definir um dashboard como o dashboard *em destaque* |Não |
| Favorito | Sim. Pode definir vários dashboards como *favoritos* | Sim. Pode definir vários relatórios como *favoritos*
| Definir alertas |Sim. Disponível para blocos de dashboard em determinadas circunstâncias |Não |
| Consultas de linguagem natural (P e R) |Sim | Sim, desde que você tenha permissões de edição para o relatório e o conjunto de dados subjacente |
| Pode ver campos e tabelas do conjunto de dados subjacentes |Não. Pode exportar dados, mas não consegue ver tabelas e campos no dashboard de controle em si |Sim |


## <a name="next-steps"></a>Próximas etapas
* Fique à vontade com os dashboards fazendo um tour em um dos nossos [dashboards de exemplo](sample-tutorial-connect-to-the-samples.md).
* Aprenda sobre [blocos de dashboard](service-dashboard-tiles.md).
* Deseja acompanhar um bloco de dashboard individual e receber um email quando ele alcançar um certo limite? [Criar um alerta em um bloco](service-set-data-alerts.md).
* Aprenda como usar o [Power BI Q&A](power-bi-tutorial-q-and-a.md) para fazer perguntas sobre os dados e receba uma resposta na forma de uma visualização.
