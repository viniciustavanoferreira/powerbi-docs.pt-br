---
title: Fontes de dados de relatório paginado no Servidor de Relatórios do Power BI
description: Saiba mais sobre as fontes de dados as quais os relatórios paginados (.rdl) podem se conectar no Servidor de Relatórios do Power BI.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 05/17/2018
ms.author: maggies
ms.openlocfilehash: 7cb5772e6ccdc1e4036d70f65a3a28210a4f6df1
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/05/2020
ms.locfileid: "78260705"
---
# <a name="paginated-report-data-sources--in-power-bi-report-server"></a>Fontes de dados de relatório paginado no Servidor de Relatórios do Power BI
Os relatórios paginados do Reporting Services no Servidor de Relatórios do Power BI oferecem suporte às mesmas fontes de dados que têm suporte nos SQL Server Reporting Services. Veja a lista de [Fontes de dados com suporte do Reporting Services](https://docs.microsoft.com/sql/reporting-services/report-data/data-sources-supported-by-reporting-services-ssrs).

## <a name="connect-to-oracle-data-sources-with-useinstalleduiculture"></a>Conectar às fontes de dados do Oracle com UseInstalledUICulture

Para conectar às fontes de dados do Oracle, o Servidor de Relatórios do Power BI usa o Provedor de Dados Oracle para .NET (ODP.NET), que é independente de NLS.

Por padrão, o servidor de relatórios usa a cultura de interface do usuário do primeiro cliente para carregar ODP.NET.  Como resultado, todas as conexões ao Oracle subsequentes a partir do servidor de relatórios serão feitas nessa cultura de interface do usuário inicial até que o serviço seja reiniciado.  Essa abordagem pode causar problemas com a renderização de um relatório devido a faltas de correspondência na formatação da cultura de interface do usuário.

Para oferecer uma experiência melhor no Servidor de Relatórios do Power BI, introduzimos uma configuração denominada UseInstalledUICulture. Quando a UseInstalledUICulture está definida como true, o servidor de relatório sempre carrega ODP.NET na cultura de interface do usuário, e não na cultura do primeiro cliente.
Essa configuração está disponível no Servidor de Relatórios do Power BI a partir da versão de fevereiro do serviço

Para habilitar esse recurso, modifique o arquivo rsreportserver.config da entrada de extensão ORACLE, como demonstrado abaixo.
```xml
<Extension Name="ORACLE" Type="Microsoft.ReportingServices.DataExtensions.OracleClientConnectionWrapper,Microsoft.ReportingServices.DataExtensions">
    <Configuration>
        <UseInstalledUICulture>true</UseInstalledUICulture>
    </Configuration>
</Extension>
```

## <a name="next-steps"></a>Próximas etapas
Agora que você se conectou à fonte de dados, [crie um relatório paginado](quickstart-create-paginated-report.md).  


Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
