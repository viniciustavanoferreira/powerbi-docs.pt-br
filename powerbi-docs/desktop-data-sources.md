---
title: Fontes de dados no Power BI Desktop
description: Fontes de dados no Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 02/13/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: f13c8f34fbbe927ee6929a0b3e717248aedd63d0
ms.sourcegitcommit: d6a48e6f6e3449820b5ca03638b11c55f4e9319c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/18/2020
ms.locfileid: "77427543"
---
# <a name="data-sources-in-power-bi-desktop"></a>Fontes de dados no Power BI Desktop

O Power BI Desktop permite se conectar a dados de várias fontes diferentes. Para obter uma lista completa de fontes de dados disponíveis, confira [Fontes de dados do Power BI](power-bi-data-sources.md).

Você se conecta aos dados usando a faixa de opções **Página Inicial**. Para mostrar os tipos de dados **Mais Comuns**, selecione o rótulo do botão **Obter Dados** ou a seta para baixo.

![Menu de tipos de dados Mais Comuns, Obter Dados no Power BI Desktop](media/desktop-data-sources/data-sources-01.png)

Para acessar a caixa de diálogo **Obter Dados**, mostre o menu de tipos de dados **Mais Comuns** e selecione **Mais**. Você também pode abrir a caixa de diálogo **Obter Dados** (e ignorar o menu **Mais Comuns**), selecionando diretamente o ícone **Obter Dados**.

![Botão Obter Dados, Power BI Desktop](media/desktop-data-sources/data-sources-02.png)

> [!NOTE]
> A equipe do Power BI está sempre expandindo as fontes de dados disponíveis para o Power BI Desktop e o serviço do Power BI. Assim, você verá com frequência as versões anteriores das fontes de dados de trabalho em andamento marcadas como **Beta** ou **Visualização**. As fontes de dados marcadas como **Beta** ou **Visualização** têm suporte e funcionalidade limitados e não devem ser usadas em ambientes de produção. Além disso, as fontes de dados marcadas como **Beta** ou **Versão prévia** para o Power BI Desktop poderão não estar disponíveis para uso no serviço do Power BI ou em outros serviços da Microsoft enquanto a fonte de dados não estiver em GA (em disponibilidade geral).

> [!NOTE]
> Há muitos conectores de dados para o Power BI Desktop que exigem o Internet Explorer 10 (ou mais recente) para autenticação. 


## <a name="data-sources"></a>Fontes de dados

A caixa de diálogo **Obter Dados** organiza os tipos de dados nas seguintes categorias:

* Todos
* Arquivo
* Banco de dados
* Power Platform
* Azure
* Serviços Online
* Outros

A categoria **Todos** inclui todos os tipos de conexão de dados de todas as categorias.

### <a name="file-data-sources"></a>Fontes de dados do arquivo

A categoria **Arquivo** fornece as seguintes conexões de dados:

* Excel
* Texto/CSV
* XML
* JSON
* Pasta
* PDF
* Pasta do SharePoint

A imagem a seguir mostra a janela **Obter Dados** para **Arquivo**.

![Fonte de dados de arquivo, caixa de diálogo Obter Dados, Power BI Desktop](media/desktop-data-sources/data-sources-03.png)

### <a name="database-data-sources"></a>Fontes de dados do banco de dados

A categoria **Banco de dados** fornece as seguintes conexões de dados:

* Banco de dados do SQL Server
* Banco de dados do Access
* Banco de dados do SQL Server Analysis Services
* Oracle Database
* Banco de dados IBM DB2
* Banco de dados IBM Informix (Beta)
* IBM Netezza
* Banco de dados MySQL
* Banco de dados PostgreSQL
* Banco de dados Sybase
* Banco de dados Teradata
* Banco de dados SAP HANA
* Servidor de Aplicativos SAP Business Warehouse
* Servidor de Mensagens SAP Business Warehouse
* Amazon Redshift
* Impala
* Google BigQuery
* Vertica
* Snowflake
* Essbase
* Cubos do AtScale
* BI Connector Data Virtuality LDW (Beta)
* Denodo
* Dremio
* Exasol
* Indexima (Beta)
* InterSystems IRIS (Beta)
* Jethro (Beta)
* Kyligence
* MarkLogic

> [!NOTE]
> Alguns conectores de banco de dados exigem que você os habilite selecionando **Arquivo > Opções e configurações > Opções**, em seguida, **Recursos de Visualização** e habilitando o conector. Se você não vir alguns dos conectores mencionados acima e quiser usá-los, verifique suas configurações de **Recursos de Visualização**. Observe também que toda fonte de dados marcada como *Beta* ou *Visualização* tem suporte e funcionalidade limitados e não deve ser usada em ambientes de produção.

A imagem a seguir mostra a janela **Obter Dados** para **Banco de dados**.

![Fontes de dados do banco de dados, caixa de diálogo Obter Dados, Power BI Desktop](media/desktop-data-sources/data-sources-04.png)

### <a name="power-platform-data-sources"></a>Fontes de dados do Power Platform

A categoria **Power Platform** fornece as seguintes conexões de dados:

* Conjuntos de dados do Power BI
* Fluxos de dados do Power BI
* Common Data Service
* Fluxo de dados do Power Platform

A imagem a seguir mostra a janela **Obter Dados** do **Power Platform**.

![Fontes de dados do Power Platform, caixa de diálogo Obter Dados, Power BI Desktop](media/desktop-data-sources/data-sources-05.png)

### <a name="azure-data-sources"></a>Fontes de dados do Azure

A categoria **Azure** fornece as seguintes conexões de dados:

* Banco de dados SQL do Azure
* SQL Data Warehouse do Azure
* Banco de Dados do Azure Analysis Services
* Armazenamento de Blobs do Azure
* Armazenamento de Tabelas do Azure
* Azure Cosmos DB
* Azure Data Lake Storage Gen2
* Azure Data Lake Storage Gen1
* Azure HDInsight (HDFS)
* Azure HDInsight Spark
* Consulta Interativa do HDInsight
* Azure Data Explorer (Kusto)
* Gerenciamento de Custos do Azure
* Azure Time Series Insights (Beta)

A imagem a seguir mostra a janela **Obter Dados** para **Azure**.

![Fonte de dados do Azure, caixa de diálogo Obter Dados, Power BI Desktop](media/desktop-data-sources/data-sources-06.png)

### <a name="online-services-data-sources"></a>Fontes de dados dos Serviços Online

A categoria **Serviços Online** fornece as seguintes conexões de dados:

* Lista do SharePoint Online
* Microsoft Exchange Online
* Dynamics 365 (online)
* Dynamics NAV
* Dynamics 365 Business Central
* Central do Microsoft Dynamics 365 Business (local)
* Microsoft Azure Consumption Insights (Beta)
* Azure DevOps (Beta)
* Azure DevOps Server (Beta)
* Objetos do Salesforce
* Relatórios do Salesforce
* Google Analytics
* Adobe Analytics
* appFigures (Beta)
* Data.World – Obter Conjunto de Dados (Beta)
* GitHub (Beta)
* LinkedIn Sales Navigator (Beta)
* MailChimp (Beta)
* Merketo (Beta)
* Mixpanel (Beta)
* Planview Enterprise One – PRM (Beta)
* Planview Projectplace (Beta)
* QuickBooks Online (Beta)
* Smartsheet
* SparkPost (Beta)
* SweetIQ (Beta)
* Planview Enterprise One – CTM (Beta)
* Twilio (Beta)
* tyGraph (Beta)
* Webtrends (Beta)
* ZenDesk (Beta)
* Dynamics 365 Customer Insights (beta)
* Fonte de dados do Emigo
* Entersoft Business Suite (Beta)
* FactSet Analytics (Beta)
* Industrial App Store
* Intune Data Warehouse (Beta)
* Segurança do Microsoft Graph (Beta)
* Product Insights (Beta)
* Quick Base
* TeamDesk (Beta)
* Workplace Analytics (Beta)

A imagem a seguir mostra a janela **Obter Dados** para **Online Services**.

![Fonte de dados dos Serviços Online, caixa de diálogo Obter Dados, Power BI Desktop](media/desktop-data-sources/data-sources-07.png)

### <a name="other-data-sources"></a>Outras fontes de dados

A categoria **Outros** fornece as seguintes conexões de dados:

* Web
* Lista do SharePoint
* Feed OData
* Active Directory
* Microsoft Exchange
* HDFS (Arquivo do Hadoop)
* Spark
* Script R
* Script Python
* ODBC
* OLE DB
* BI360 – Relatórios Financeiros e Orçamento (Beta)
* FHIR
* Grade de Informações (Beta)
* Jamf Pro (Beta)
* MicroStrategy for Power BI
* Paxata
* QubolePresto (Beta)
* Roamler (Beta)
* Siteimprove (Beta)
* SurveyMonkey (Beta)
* Tenforce (Smart)List (Beta)
* Vena (Beta)
* Workforce Dimensions (Beta)
* Zucchetti HR Infinity (Beta)
* Consulta em Branco

A imagem a seguir mostra a janela **Obter Dados** para **Outros**.

![Outras fontes de dados, caixa de diálogo Obter Dados, Power BI Desktop](media/desktop-data-sources/data-sources-08.png)

> [!NOTE]
> Neste momento, não é possível se conectar a fontes de dados personalizadas protegidas usando o Azure Active Directory.

## <a name="connecting-to-a-data-source"></a>Conectando-se a uma fonte de dados

Para se conectar a uma fonte de dados, selecione a fonte de dados na janela **Obter Dados** e selecione **Conectar**. Na imagem a seguir, a opção **Web** é selecionada na categoria de conexão de dados **Outros** .

![Conectar à Web, caixa de diálogo Obter Dados, Power BI Desktop](media/desktop-data-sources/data-sources-08.png)

É exibida uma janela de conexão específica para o tipo de conexão de dados usado. Se as credenciais forem necessárias, será solicitado que você as forneça. A imagem a seguir mostra uma URL sendo inserida para conectar a uma fonte de dados da Web.

![URL de entrada, caixa de diálogo Da Web, Power BI Desktop](media/desktop-data-sources/datasources-fromwebbox.png)

Insira as informações de conexão de recurso ou URL e selecione **OK**. O Power BI Desktop estabelece a conexão com a fonte de dados e apresenta as fontes de dados disponíveis no **Navegador**.

![Caixa de diálogo Navegador, Power BI Desktop](media/desktop-data-sources/datasources-fromnavigatordialog.png)

Para carregar os dados, selecione o botão **Carregar** na parte inferior do painel **Navegador**. Para transformar ou editar a consulta no Editor do Power Query antes de carregar os dados, selecione o botão **Transformar Dados**.

Isso é tudo que é necessário para conectar a fontes de dados no Power BI Desktop. Tente se conectar aos dados da nossa crescente lista de fontes de dados e volte com frequência – continuamos aumentando à lista o tempo todo.

## <a name="using-pbids-files-to-get-data"></a>Usando arquivos PBIDS para obter dados

Os arquivos PBIDS são arquivos do Power BI Desktop que têm uma estrutura específica, e eles têm a extensão .PBIDS para identificá-los como arquivos de fonte de dados do Power BI.

Você pode criar um arquivo PBIDS a fim de simplificar a experiência de **Obter dados** para criadores de relatórios em sua organização. Para facilitar o uso de arquivos PBIDS por um autor de novo relatório, recomendamos que um administrador crie esses arquivos para conexões usadas com frequência.

Quando um autor abre um arquivo PBIDS, o Power BI Desktop é aberto e solicita ao usuário as credenciais para autenticar e conectar-se à fonte de dados especificada no arquivo. A caixa de diálogo **Navegação** é exibida, e o usuário deve selecionar as tabelas da fonte de dados a serem carregadas no modelo. Talvez seja necessário que os usuários selecionem os bancos de dados se nenhum tiver sido especificado no arquivo PBIDS.

Desse ponto em diante, o usuário poderá começar a criar visualizações ou selecionar **Fontes Recentes** para carregar um novo conjunto de tabelas no modelo.

Atualmente, os arquivos PBIDS dão suporte apenas a uma fonte de dados em um arquivo. A especificação de mais de uma fonte de dados resulta em um erro.

Para criar o arquivo PBIDS, um administrador precisará especificar as entradas obrigatórias para uma conexão única. Ele também pode especificar o modo de conexão como DirectQuery ou Importar. Se o**modo** estiver ausente ou for nulo no arquivo, o usuário que abrir o arquivo no Power BI Desktop precisará selecionar **DirectQuery** ou **Importar**.

### <a name="pbids-file-examples"></a>Exemplos de arquivos PBIDS

Esta seção fornece alguns exemplos de fontes de dados usadas com frequência. O tipo de arquivo PBIDS dá suporte apenas a conexões de dados que também têm suporte no Power BI Desktop, com duas exceções: Live Connect e Consulta em Branco.

O arquivo PBIDS *não* inclui informações de autenticação nem de tabela e esquema.  

Os trechos de código a seguir mostram vários exemplos comuns de arquivos PBIDS, mas eles não estão completos nem são abrangentes. Para outras fontes de dados, você pode consultar o [Formato DSR (Fonte de Referência de Dados) para informações de protocolo e endereços](https://docs.microsoft.com/azure/data-catalog/data-catalog-dsr#data-source-reference-specification).

Esses exemplos são apenas para conveniência; não se espera que eles sejam abrangentes nem incluam todos os conectores com suporte no formato DSR. Os administradores ou as organizações podem criar suas próprias fontes de dados usando esses exemplos como guias, por meio dos quais podem criar e dar suporte a seus próprios arquivos de fonte de dados.

#### <a name="azure-as"></a>Azure AS

```json
{ 
    "version": "0.1", 
    "connections": [ 
    { 
        "details": { 
        "protocol": "analysis-services", 
        "address": { 
            "server": "server-here" 
        }, 
        } 
    } 
    ] 
}
```

#### <a name="folder"></a>Pasta

```json
{ 
  "version": "0.1", 
  "connections": [ 
    { 
      "details": { 
        "protocol": "folder", 
        "address": { 
            "path": "folder-path-here" 
        } 
      } 
    } 
  ] 
} 
```

#### <a name="odata"></a>OData

```json
{ 
  "version": "0.1", 
  "connections": [ 
    { 
      "details": { 
        "protocol": "odata", 
        "address": { 
            "url": "URL-here" 
        } 
      } 
    } 
  ] 
} 
```

#### <a name="sap-bw"></a>SAP BW

```json
{ 
  "version": "0.1", 
  "connections": [ 
    { 
      "details": { 
        "protocol": "sap-bw-olap", 
        "address": { 
          "server": "server-name-here", 
          "systemNumber": "system-number-here", 
          "clientId": "client-id-here" 
        }, 
      } 
    } 
  ] 
} 
```

#### <a name="sap-hana"></a>SAP Hana

```json
{ 
  "version": "0.1", 
  "connections": [ 
    { 
      "details": { 
        "protocol": "sap-hana-sql", 
        "address": { 
          "server": "server-name-here:port-here" 
        }, 
      } 
    } 
  ] 
} 
```

#### <a name="sharepoint-list"></a>Lista do SharePoint

A URL deve indicar o site do SharePoint em si, não uma lista dentro do site. Os usuários obtêm um navegador que permite que eles selecionem uma ou mais listas desse site e cada uma delas se torna uma tabela no modelo.

```json
{ 
  "version": "0.1", 
  "connections": [ 
    { 
      "details": { 
        "protocol": "sharepoint-list", 
        "address": { 
          "url": "URL-here" 
        }, 
       } 
    } 
  ] 
} 
```

#### <a name="sql-server"></a>SQL Server

```json
{ 
  "version": "0.1", 
  "connections": [ 
    { 
      "details": { 
        "protocol": "tds", 
        "address": { 
          "server": "server-name-here", 
          "database": "db-name-here (optional) "
        } 
      }, 
      "options": {}, 
      "mode": "DirectQuery" 
    } 
  ] 
} 
```

#### <a name="text-file"></a>Arquivo de texto

```json
{ 
  "version": "0.1", 
  "connections": [ 
    { 
      "details": { 
        "protocol": "file", 
        "address": { 
            "path": "path-here" 
        } 
      } 
    } 
  ] 
} 
```

#### <a name="web"></a>Web

```json
{ 
  "version": "0.1", 
  "connections": [ 
    { 
      "details": { 
        "protocol": "http", 
        "address": { 
            "url": "URL-here" 
        } 
      } 
    } 
  ] 
} 
```

#### <a name="dataflow"></a>Fluxo de dados

```json
{
  "version": "0.1",
  "connections": [
    {
      "details": {
        "protocol": "powerbi-dataflows",
        "address": {
          "workspace":"workspace id (Guid)",
          "dataflow":"optional dataflow id (Guid)",
          "entity":"optional entity name"
        }
       }
    }
  ]
}
```

## <a name="next-steps"></a>Próximas etapas

Você pode fazer de tudo com o Power BI Desktop. Para obter mais informações sobre seus recursos, consulte as seguintes fontes:

* [O que é o Power BI Desktop?](desktop-what-is-desktop.md)
* [Visão geral de consulta com o Power BI Desktop](desktop-query-overview.md)
* [Tipos de dados no Power BI Desktop](desktop-data-types.md)
* [Formatar e combinar dados com o Power BI Desktop](desktop-shape-and-combine-data.md)
* [Tarefas comuns de consulta no Power BI Desktop](desktop-common-query-tasks.md)
