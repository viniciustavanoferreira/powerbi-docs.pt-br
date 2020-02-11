---
title: Pré-requisitos de fonte de dados do Power BI
description: Pré-requisitos de fonte de dados do Power BI
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/29/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: c3ccbe6ad87a813185943845431fa1a859b09a76
ms.sourcegitcommit: 8b300151b5c59bc66bfef1ca2ad08593d4d05d6a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2020
ms.locfileid: "76888421"
---
# <a name="power-bi-data-source-prerequisites"></a>Pré-requisitos de fonte de dados do Power BI
Para cada provedor de dados, o Power BI dá suporte a uma versão específica do provedor em objetos. Para obter mais informações sobre as fontes de dados disponíveis para o Power BI, confira [Fontes de dados](desktop-data-sources.md). A tabela a seguir descreve esses requisitos.

| Fonte de dados | Provedor | Versão mínima do provedor | Versão mínima da fonte de dados | Objetos de fonte dados com suporte | Link de download |
| --- | --- | --- | --- | --- | --- |
| SQL Server |ADO.net (interno no .Net Framework) |.NET Framework 3.5 (somente) |SQL Server 2005+ |Tabelas/modos de exibição, Funções escalares, Funções de tabela |Incluído no .NET Framework 3.5 ou superior |
| Acessar |Mecanismo de Banco de Dados do Microsoft Access (ACE) |ACE 2010 SP1 |Nenhuma restrição |Tabelas/modos de exibição |[Link de download](https://go.microsoft.com/fwlink/?linkid=285987&clcid=0x409) |
| Excel (somente arquivos .xls) (veja a observação 1) |Mecanismo de Banco de Dados do Microsoft Access (ACE) |ACE 2010 SP1 |Nenhuma restrição |Tabelas, planilhas |[Link de download](https://go.microsoft.com/fwlink/?linkid=285987&clcid=0x409) |
| Oracle (consulte a observação 2) |ODP.NET |ODAC 11.2 versão 5 (11.2.0.3.20) |9.x+ |Tabelas/modos de exibição |[Link de download](https://go.microsoft.com/fwlink/?linkid=272376&clcid=0x409) |
| | System.Data.OracleClient (criado no .NET Framework) |.NET Framework 3.5 |9.x+ |Tabelas/modos de exibição |Incluído no .NET Framework 3.5 ou superior |
| IBM DB2 |Cliente ADO.Net da IBM (parte do pacote de driver do servidor de dados da IBM) |10.1 |9.1+ |Tabelas/modos de exibição |[Link de download](https://go.microsoft.com/fwlink/?linkid=274911&clcid=0x409) |
| MySQL |Conector/rede |6.6.5 |5.1 |Tabelas/modos de exibição, Funções escalares |[Link de download](https://go.microsoft.com/fwlink/?linkid=278885&clcid=0x409) |
| PostgreSQL |Provedor ADO.NET NPGSQL |2.0.12 |9.4 |Tabelas/modos de exibição |[Link de download](https://go.microsoft.com/fwlink/?linkid=282716&clcid=0x409) |
| Teradata |Provedor de dados .Net para Teradata |14+ |12+ |Tabelas/modos de exibição |[Link de download](https://go.microsoft.com/fwlink/?linkid=278886&clcid=0x409) |
| SAP Sybase SQL Anywhere |iAnywhere.Data.SQLAnywhere para .NET 3.5 |16+ |16+ |Tabelas/modos de exibição |[Link de download](https://go.microsoft.com/fwlink/?linkid=324846) |

>[!NOTE]
>Arquivos do Excel com extensão .xlsx não exigem instalação separada do provedor.

>[!NOTE]
>Os provedores da Oracle também exigem software cliente da Oracle (versão 8.1.7+).
> 
> 

