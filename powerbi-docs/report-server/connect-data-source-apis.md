---
title: Alterar cadeias de conexão da fonte de dados com o PowerShell
description: Altere as cadeias de conexão da fonte de dados usando APIs no PowerShell – Servidor de Relatórios do Power BI.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: how-to
ms.date: 01/21/2020
ms.author: maggies
ms.openlocfilehash: bb769937e99cd3e936d7f5f3967e8f17b939242c
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85236057"
---
# <a name="change-data-source-connection-strings-in-power-bi-reports-with-powershell---power-bi-report-server"></a>Altere as cadeias de conexão da fonte de dados no Power BI com o PowerShell – Servidor de Relatórios do Power BI


É possível alterar as cadeias de conexão da fonte de dados nos relatórios do Power BI no Servidor de Relatórios do Power BI usando APIs no PowerShell. 

> [!NOTE]
> No momento, esse recurso funciona apenas para o DirectQuery. Em breve, haverá suporte para atualização de dados e importação.

1. Instale os commandlets do PowerShell do Servidor de Relatórios do Power BI. Veja as instruções de instalação dos commandlets em [https://github.com/Microsoft/ReportingServicesTools](https://github.com/Microsoft/ReportingServicesTools). 

2. Busque as informações da fonte de dados existente para o arquivo do Power BI por meio dos commandlets do PowerShell:

    ```powershell
    Get-RsRestItemDataSource -RsItem '/MyPbixReport'
    ```

    Para exibir informações da primeira fonte de dados contida no relatório do Power BI: 

    ```powershell
    $dataSources[0]
    ```

3. Atualize a conexão e as informações da credencial conforme necessário. Se a atualização da cadeia de conexão e da fonte de dados usar as credenciais armazenadas, você precisará fornecer a senha da conta. 

    Para atualizar a cadeia de conexão da fonte de dados:

    ```powershell
    $dataSources[0].ConnectionString = 'data source=myCatalogServer;initial catalog=ReportServer;persist security info=False' 
    ```

    Para alterar o tipo de credencial da fonte de dados:

    ```powershell
    $dataSources[0].DataModelDataSource.AuthType = 'Integrated'
    ```

    Para alterar o nome de usuário/senha da fonte de dados:

    ```powershell
    $dataSources[0].DataModelDataSource.Username = 'domain\user'
    ```
    ```powershell
    $dataSources[0].DataModelDataSource.Secret = 'password'
    ```

4. Salve as credenciais atualizadas no servidor.

    ```powershell
    Set-RsRestItemDataSource -RsItem '/MyPbixReport' -RsItemType 'PowerBIReport' -DataSources $dataSources
    ```

## <a name="next-steps"></a>Próximas etapas

[Fontes de dados de relatório paginado no Servidor de Relatórios do Power BI](connect-data-sources.md) 

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
