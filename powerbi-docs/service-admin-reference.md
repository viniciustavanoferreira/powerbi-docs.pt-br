---
title: Cmdlets do PowerShell, APIs REST e SDK do .NET para administradores
description: Saiba mais sobre as maneiras de administrar o Power BI por meio de scripts e APIs de programação.
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 09/09/2019
ms.author: kfollis
LocalizationGroup: Administration
ms.openlocfilehash: b4f4227a53a87cd831962bc5c944a569531b8232
ms.sourcegitcommit: f77b24a8a588605f005c9bb1fdad864955885718
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2019
ms.locfileid: "74699856"
---
# <a name="powershell-cmdlets-rest-apis-and-net-sdk-for-power-bi-administration"></a>Cmdlets do PowerShell, APIs REST e SDK do .NET para a administração do Power BI
O Power BI permite aos administradores fazer scripts de tarefas comuns com os cmdlets do PowerShell. Ele também expõe as APIs REST e fornece um SDK do .NET para desenvolver soluções administrativas. Este tópico mostra uma lista de cmdlets e o método do SDK correspondente, bem como o ponto de extremidade da API REST. Para obter mais informações, veja:

- [Download](https://www.powershellgallery.com/packages/MicrosoftPowerBIMgmt/) e [documentação](https://docs.microsoft.com/powershell/power-bi/overview?view=powerbi-ps) do PowerShell
- [Documentação](https://docs.microsoft.com/rest/api/power-bi/admin) da API REST
- [Download](https://www.nuget.org/packages/Microsoft.PowerBI.Api/) do SDK do .NET

> Os cmdlets abaixo devem ser chamados com `-Scope Organization` para operar no locatário para administração.

| **Nome do cmdlet** | **Aliases** | **Método do SDK** | **Ponto de extremidade da API REST** | **Descrição** |
| --- | --- | --- | --- | --- |
| `Get-PowerBIDatasource` | N/D | `Datasets_GetDataSourcesAsAdmin` | /v1.0/myorg/admin/datasets/{datasetkey}/datasources | Obtém as fontes de dados para um determinado conjunto de dados. |
| `Get-PowerBIDataset` | N/D | `Datasets_GetDatasetsAsAdmin` | /v1.0/myorg/admin/datasets | Obtém a lista completa de conjuntos de dados em um locatário do Power BI. |
| `Get-PowerBIWorkspace` | `Get-PowerBIGroup` | `Groups_GetGroupsAsAdmin` | /v1.0/myorg/admin/groups | Obtém a lista completa de workspaces em um locatário do Power BI. |
| `Add-PowerBIWorkspaceUser` | `Add-PowerBIGroupUser` | `Groups_AddUserAsAdmin` | /v1.0/myorg/admin/groups/{groupId}/users | Adiciona um usuário como um membro a um determinado workspace. |
| `Remove-PowerBIWorkspaceUser` | `Remove-PowerBIGroupUser` | `Groups_DeleteUserAsAdmin` | /v1.0/myorg/admin/groups/{groupId}/users/{user} | Remove um usuário da lista de membros de um determinado workspace. |
| `Restore-PowerBIWorkspace` |`Restore-PowerBIGroup` | `Groups_RestoreDeletedGroupAsAdmin` | /v1.0/myorg/admin/groups/{groupId}/restore | Restaura um workspace excluído. |
| `Set-PowerBIWorkspace` |`Set-PowerBIGroup` | `Groups_UpdateGroupAsAdmin` | /v1.0/myorg/admin/groups/{groupId} | Atualiza as propriedades de um determinado workspace. |
| `Get-PowerBIDataset -WorkspaceId` | N/D | `Groups_GetDatasetsAsAdmin` | /v1.0/myorg/admin/groups/{group\_id}/datasets | Obtém os conjuntos de dados dentro de um determinado workspace. |
| `Get-PowerBIReport` | N/D | `Reports_GetReportsAsAdmin` | /v1.0/myorg/admin/reports | Obtém a lista completa de relatórios em um locatário do Power BI. |
| `Get-PowerBIDashboard` | N/D | `Dashboards_GetDashboardsAsAdmin` | /v1.0/myorg/admin/dashboards | Obtém a lista completa de dashboards em um locatário do Power BI. |
| `Get-PowerBIDashboard -WorkspaceId` | N/D | `Groups_GetDashboardsAsAdmin` | /v1.0/myorg/admin/groups/{group\_id}/dashboards | Obtém os dashboards dentro de um determinado workspace. |
| `Get-PowerBITile` | `Get-PowerBIDashboardTile` | `Dashboards_GetTilesAsAdmin` | /v1.0/myorg/admin/dashboards/{dashboard\_id}/tiles | Obtém os blocos de um determinado dashboard. |
| `Get-PowerBIReport` | N/D | `Groups_GetReportsAsAdmin` | /v1.0/myorg/admin/groups/{group\_id}/reports | Obtém os relatórios dentro de um determinado workspace. |
| `Get-PowerBIImport` | N/D | `Imports_GetImportsAsAdmin` | /v1.0/myorg/admin/imports | Obtém a lista completa de importações em um locatário do Power BI. |
| `Connect-PowerBIServiceAccount` | `Login-PowerBI` &  `Login-PowerBIServiceAccount` | N/D | N/D | Faça logon no Power BI e inicie uma sessão. |
| `Disconnect-PowerBIServiceAccount` | `Logout-PowerBI` & `Logout-PowerBIServiceAccount` | N/D | N/D | Faça logoff do Power BI e feche a sessão existente. |
| `Invoke-PowerBIRestMethod`| N/D | Não aplicável | N/D | Envie chamadas arbitrárias da API REST ao Power BI. |
| `Get-PowerBIAccessToken`| N/D | Não aplicável | N/D | Obtenha o token de acesso do Power BI em uma sessão. |
| `Resolve-PowerBIError`| N/D | Não aplicável | N/D | Obtenha informações detalhadas do erro para chamadas de cmdlet sem êxito. |
