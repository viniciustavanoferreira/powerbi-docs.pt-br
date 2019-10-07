---
title: Fontes de dados com suporte do DirectQuery no Power BI
description: Obtenha uma lista de quais fontes de dados podem usar o DirectQuery.
author: davidiseminger
ms.author: davidi
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 09/04/2019
LocalizationGroup: Connect to data
ms.openlocfilehash: 75b7a606e588ca7f6d1393c5b6e0dd9041f6d63e
ms.sourcegitcommit: b7a9862b6da940ddebe61bc945a353f91cd0e4bd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/04/2019
ms.locfileid: "71945197"
---
# <a name="data-sources-supported-by-directquery-in-power-bi"></a>Fontes de dados com suporte do DirectQuery no Power BI

O **Power BI Desktop** e o **serviço do Power BI** têm várias fontes de dados às quais você pode se conectar para obter acesso aos dados. Este artigo descreve quais fontes de dados do Power BI dão suporte ao método de conexão conhecido como **DirectQuery**. Para obter mais informações sobre o DirectQuery, consulte [**DirectQuery no Power BI**](desktop-directquery-about.md).

As seguintes fontes de dados dão suporte ao DirectQuery no Power BI:

* Amazon Redshift
* AtScale (Beta)
* Azure Data Explorer
* Azure HDInsight Spark
* [Banco de dados SQL do Azure](service-azure-sql-database-with-direct-connect.md)
* [SQL Data Warehouse do Azure](service-azure-sql-data-warehouse-with-direct-connect.md)
* Denodo
* Google BigQuery
* Consulta Interativa do HDInsight
* IBM DB2 (Provedor Microsoft))
* IBM Netezza
* Impala (versão 2.x)
* MarkLogic
* Banco de Dados Oracle (versão 12 e posterior)
* Oracle Essbase
* PostgreSQL
* Servidor de Aplicativos SAP Business Warehouse
* Servidor de Mensagens SAP Business Warehouse
* SAP HANA
* Snowflake
* Spark (versão 0.9 e posterior)
* SQL Server
* Teradata
* Vertica

As fontes de dados que têm **(Beta)** ou **(Versão prévia)** depois do nome estão sujeitas a alterações e não há suporte para que elas sejam usadas em produção. É possível que também não haja suporte para elas após a publicação de um relatório no **serviço do Power BI**, o que significa que abrir um relatório publicado ou explorar o conjunto de dados pode resultar em um erro.

A única diferença entre fontes de dados **(Beta)** e em **(Versão prévia)** é que as fontes em **(Versão prévia)** precisam ser habilitadas como um recurso de versão prévia antes que fiquem disponíveis para uso. Para habilitar um conector de dados em **(Versão prévia)** , no **Power BI Desktop**, acesse **Arquivo > Opções e Configurações > Opções** e, em seguida, **Recursos de versão prévia**.

> [!NOTE]
> Consultas DirectQuery para SQL Server requerem autenticação usando as credenciais de autenticação atuais do Windows ou credenciais de banco de dados para estabelecer o acesso. Credenciais alternativas não são compatíveis.
>

## <a name="on-premises-gateway-requirements"></a>Requisitos de gateway local
A tabela a seguir especifica se um **Gateway de dados local** é necessário para se conectar à fonte de dados especificada após publicar um relatório no **serviço do Power BI**.

| Fonte | Gateway necessário? |
| --- | --- |
| Amazon Redshift |Não |
| Azure HDInsight Spark (Beta) |Não |
| Banco de Dados SQL do Azure |Não |
| SQL Data Warehouse do Azure |Não |
| Google BigQuery |Não |
| IBM Netezza |Sim |
| IBM DB2 (Provedor IBM) |Sim |
| IBM DB2 (Provedor Microsoft) |Não |
| Banco de Dados do IBM Informix |Não |
| Impala (versão 2.x) |Sim |
| MySQL |Sim |
| ODBC |Sim |
| Banco de dados Oracle |Sim |
| PostgreSQL |Sim |
| Servidor de Aplicativos SAP Business Warehouse |Sim |
| Servidor de Mensagens SAP Business Warehouse |Ainda não tem suporte no **serviço do Power BI** |
| SAP HANA |Sim |
| Snowflake |Sim |
| Spark (beta), versão 0.9 e posterior |Sim |
| SQL Server |Sim |
| Sybase |Sim |
| Teradata |Sim |
| Vertica |Sim |


## <a name="single-sign-on-sso-for-directquery-sources"></a>SSO (logon único) para fontes do DirectQuery

Quando a opção de SSO está habilitada e os usuários acessam os relatórios baseados na fonte de dados, o Power BI envia suas credenciais autenticadas do Azure AD nas consultas à fonte de dados subjacente. Isso permite que o Power BI respeite as configurações de segurança que são configuradas no nível da fonte de dados.

A opção de SSO entra em vigor em todos os conjuntos de dados que usam essa fonte de dados. Isso não afeta o método de autenticação usado para cenários de importação. As seguintes fontes de dados dão suporte ao SSO para conexões por meio do DirectQuery:

- Banco de Dados SQL do Azure
- SQL Data Warehouse do Azure
- Impala
- SAP HANA
- SAP BW
- Spark
- SQL Server
- Teradata

> [!Note]
> Não há suporte para Autenticação Multifator do Microsoft Azure (MFA). Os usuários que desejam usar o SSO com o DirectQuery precisam ser isentos de MFA.

## <a name="next-steps"></a>Próximas etapas
Para obter mais informações sobre o DirectQuery, confira os seguintes recursos:

* [DirectQuery no Power BI](desktop-directquery-about.md)
* [DirectQuery e SAP HANA](desktop-directquery-sap-hana.md)
* [DirectQuery e SAP BW](desktop-directquery-sap-bw.md)
* [Gateway de dados local](service-gateway-onprem.md)

