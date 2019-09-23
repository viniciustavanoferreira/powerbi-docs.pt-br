---
title: Visão geral do manual do desenvolvedor, Servidor de Relatório do Power BI
description: Bem-vindo ao manual do desenvolvedor para o Servidor de Relatório do Power BI, um local para armazenar e gerenciar seus relatórios do Power BI, móveis e paginados.
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 11/01/2017
ms.openlocfilehash: f0186b362a9e3cc956835b94089228dc606eca35
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "64769942"
---
# <a name="developer-handbook-overview-power-bi-report-server"></a>Visão geral do manual do desenvolvedor, Servidor de Relatório do Power BI

Bem-vindo ao manual do desenvolvedor para o Servidor de Relatório do Power BI, um local para armazenar e gerenciar seus relatórios do Power BI, móveis e paginados.

![Manual do Administrador](media/developer-handbook-overview/admin-handbook.png)

Este manual realçará as opções que você, como desenvolvedor, tem disponíveis para trabalhar com o Servidor de Relatórios do Power BI.

## <a name="embedding"></a>Inserção

Para qualquer relatório no Servidor de Relatório do Power BI, é possível inserir em um iFrame adicionando o parâmetro querystring `?rs:Embed=true` à URL. Essa técnica funciona com relatórios do Power BI, bem como outros tipos de relatório.

### <a name="report-viewer-control"></a>Controle do Visualizador de Relatórios

Para relatórios paginados, é possível aproveitar o Controle do Visualizador de Relatórios. Com ele, você pode colocar o controle em um aplicativo Web ou janela do .NET. Para obter mais informações, consulte [Get started with the Report Viewer Control (Introdução ao Controle do Visualizador de Relatórios)](https://docs.microsoft.com/sql/reporting-services/application-integration/integrating-reporting-services-using-reportviewer-controls-get-started).

## <a name="apis"></a>APIs

Há várias opções de API para interagir com o Servidor de Relatório do Power BI. Essa técnica inclui o seguinte.

* [APIs REST](rest-api.md)
* [Acesso à URL](https://docs.microsoft.com/sql/reporting-services/url-access-ssrs)
* [Provedor WMI](https://docs.microsoft.com/sql/reporting-services/wmi-provider-library-reference/reporting-services-wmi-provider-library-reference-ssrs)

Também é possível usar os [Utilitários do PowerShell](https://github.com/Microsoft/ReportingServicesTools) de software livre para gerenciar o servidor de relatório.

> [!NOTE]
> No momento, os utilitários do PowerShell não dão suporte a arquivos do Power BI Desktop (.pbix).

## <a name="custom-extensions"></a>Extensões personalizadas

A Biblioteca de Extensões é um conjunto de classes, interfaces e tipos de valor incluídos no Servidor de Relatório do Power BI. Esta biblioteca fornece acesso à funcionalidade do sistema e foi criada para ser a base sobre a qual os aplicativos Microsoft .NET Framework podem ser usados para estender os componentes do Servidor de Relatório do Power BI.

Há vários tipos de extensões que podem ser criadas.

* Extensões de processamento de dados
* Extensões de entrega
* Extensões de renderização para relatórios paginados
* Extensões de segurança

Para saber mais, consulte [Extension library (Biblioteca de extensões)](https://docs.microsoft.com/sql/reporting-services/extensions/reporting-services-extension-library).

## <a name="next-steps"></a>Próximas etapas

[Introdução ao Controle do Visualizador de Relatórios](https://docs.microsoft.com/sql/reporting-services/application-integration/integrating-reporting-services-using-reportviewer-controls-get-started)  
[Criando aplicativos que usam o serviço Web e o .NET Framework](https://docs.microsoft.com/sql/reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework)  
[Acesso à URL](https://docs.microsoft.com/sql/reporting-services/url-access-ssrs)  
[Biblioteca de extensões](https://docs.microsoft.com/sql/reporting-services/extensions/reporting-services-extension-library)  
[Provedor WMI](https://docs.microsoft.com/sql/reporting-services/wmi-provider-library-reference/reporting-services-wmi-provider-library-reference-ssrs)

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)