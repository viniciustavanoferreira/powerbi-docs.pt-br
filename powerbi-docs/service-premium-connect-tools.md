---
title: Conectar-se a conjuntos de dados do Power BI Premium com aplicativos cliente e ferramentas (versão prévia)
description: Descreve como se conectar a conjuntos de dados no Power BI Premium em aplicativos cliente e ferramentas.
author: minewiskan
ms.author: owend
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 07/24/2019
ms.custom: seodec18
LocalizationGroup: Premium
ms.openlocfilehash: 0364fae1648e6155cc5e5a92850861c3bedbabdc
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/09/2019
ms.locfileid: "73871898"
---
# <a name="connect-to-datasets-with-client-applications-and-tools-preview"></a>Conectar-se a conjuntos de dados com aplicativos cliente e ferramentas (versão prévia)

Os workspaces e os conjuntos de dados do Power BI Premium dão suporte a conexões *somente leitura* da Microsoft e a ferramentas e aplicativos cliente de terceiros. Por padrão, as conexões estão habilitadas

> [!NOTE]
> Este artigo pretende apenas apresentar a conectividade somente leitura com workspaces e conjuntos de dados do Power BI Premium. Ele *não* se destina a fornecer informações detalhadas sobre programação, ferramentas e aplicativos específicos, arquitetura e gerenciamento de workspaces e conjuntos de dados. Os assuntos descritos aqui exigem uma compreensão sólida da arquitetura e da administração do modelo de banco de dados de tabela do Analysis Services.

## <a name="protocol"></a>Protocolo

O Power BI Premium usa o protocolo XMLA ([XML for Analysis](https://docs.microsoft.com/bi-reference/xmla/xml-for-analysis-xmla-reference)) para a comunicação entre aplicativos cliente e o mecanismo que gerencia seus workspaces e conjuntos de dados. Essa comunicação é feita por meio do que é normalmente conhecido como pontos de extremidade XMLA. O XMLA é o mesmo protocolo de comunicação usado pelo mecanismo do Microsoft Analysis Services, que, nos bastidores, executa a modelagem semântica, a governança, o ciclo de vida e o gerenciamento de dados do Power BI. 

A grande maioria das ferramentas e dos aplicativos cliente não se comunica explicitamente com o mecanismo usando pontos de extremidade XMLA. Em vez disso, eles usam bibliotecas de clientes, como MSOLAP, ADOMD e AMO, como um intermediário entre o aplicativo cliente e o mecanismo, que se comunica exclusivamente usando XMLA.


## <a name="supported-tools"></a>Ferramentas compatíveis

Essas ferramentas dão suporte ao acesso somente leitura aos workspaces e aos conjuntos de dados do Power BI Premium:

**SSMS (SQL Server Management Studio)** – dá suporte a consultas DAX, MDX, XMLA e TraceEvent. Exige a versão 18.0. Baixe [aqui](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms). 

**SQL Server Profiler** – incluído no SSMS 18.0 (versão prévia), essa ferramenta fornece rastreamento e depuração de eventos do servidor. Você pode capturar e salvar dados sobre cada evento em um arquivo ou uma tabela para análise posterior. Embora oficialmente preterido no SQL Server, o Profiler continua sendo incluído no SSMS e permanece compatível com o Analysis Services e, agora, com o Power BI Premium. Para saber mais, confira [SQL Server Profiler](https://docs.microsoft.com/sql/tools/sql-server-profiler/sql-server-profiler).

**DAX Studio** – ferramenta open-source da comunidade para execução e análise de consultas DAX no Analysis Services. Exige a versão 2.8.2 ou posterior. Para saber mais, confira [daxstudio.org](https://daxstudio.org/).

**Tabelas Dinâmicas do Excel** – a versão Clique para Executar do Office 16.0.11326.10000 ou superior é necessária.

**Terceiros** – inclui aplicativos de visualização de dados do cliente e ferramentas que podem se conectar a conjuntos de dados, consultá-los e consumi-los no Power BI Premium. A maioria das ferramentas exige as últimas versões das bibliotecas de clientes MSOLAP, mas algumas podem usar o ADOMD.

## <a name="client-libraries"></a>Bibliotecas de clientes

As bibliotecas de clientes são necessárias para ferramentas e aplicativos cliente se conectarem aos workspaces do Power BI Premium. As mesmas bibliotecas de clientes usadas para se conectar ao Analysis Services no Power BI Premium também são compatíveis. Os aplicativos cliente da Microsoft, como Excel, SSMS (SQL Server Management Studio) e SSDT (SQL Server Data Tools), instalam as três bibliotecas de clientes e as atualizam junto com as atualizações de aplicativo regulares. Em alguns casos, especialmente com ferramentas e aplicativos de terceiros, talvez você precise instalar versões mais recentes das bibliotecas de clientes. As bibliotecas de clientes são atualizadas mensalmente. Para saber mais, confira [Bibliotecas de clientes para conexão com o Analysis Services](https://docs.microsoft.com/azure/analysis-services/analysis-services-data-providers).

## <a name="connecting-to-a-premium-workspace"></a>Como se conectar a um workspace Premium

Você pode se conectar aos workspaces atribuídos à capacidade dedicada Premium. Os workspaces atribuídos a uma capacidade dedicada têm uma cadeia de conexão no formato de URL. 

Para obter a cadeia de conexão do workspace no Power BI, em **Configurações do Workspace**, na guia **Premium**, em **Conexão do Workspace**, clique em **Copiar**.

![Cadeia de conexão do workspace](media/service-premium-connect-tools/connect-tools-workspace-connection.png)

As conexões de workspace usam o seguinte formato de URL para resolver um workspace como se ele fosse um nome do servidor do Analysis Services:   
`powerbi://api.powerbi.com/v1.0/[tenant name]/[workspace name]` 

Por exemplo, `powerbi://api.powerbi.com/v1.0/contoso.com/Sales Workspace`

### <a name="to-connect-in-ssms"></a>Para se conectar no SSMS

Em **Conectar-se ao Servidor** > **Tipo de Servidor**, selecione **Analysis Services**. Em **Nome do servidor**, insira a URL. Em **Autenticação**, selecione **Active Directory – Universal com Suporte a MFA** e, em seguida, em **Nome de usuário**, insira a ID de usuário organizacional. 

Quando conectado, o workspace é mostrado como um servidor do Analysis Services e os conjuntos de dados no workspace são mostrados como bancos de dados.  

![SSMS](media/service-premium-connect-tools/connect-tools-ssms.png)

### <a name="initial-catalog"></a>Catálogo inicial

Para algumas ferramentas, como o SQL Server Profiler, talvez seja necessário especificar um *Catálogo Inicial*. Especifique um conjunto de dados (banco de dados) no workspace. Em **Conectar-se ao Servidor**, clique em **Opções**. Na caixa de diálogo **Conectar-se ao Servidor**, na guia **Propriedades de Conexão**, em **Conectar-se ao banco de dados**, insira o nome do conjunto de dados.

### <a name="duplicate-workspace-name"></a>Nome do workspace duplicado

Ao se conectar a um workspace com o mesmo nome de outro workspace, você poderá receber o seguinte erro: **Não é possível se conectar a powerbi://api.powerbi.com/v1.0/[nome do locatário]/[nome do workspace].**

Para solucionar esse erro, além do nome do workspace, especifique o ObjectIDGuid, que pode ser copiado da objectID do workspace na URL. Acrescente a objectID à URL de conexão. Por exemplo, `powerbi://api.powerbi.com/v1.0/myorg/Contoso Sales – 9d83d204-82a9-4b36-98f2-a40099093830'

### <a name="duplicate-dataset-name"></a>Nome do conjunto de dados duplicado

Ao se conectar a um conjunto de dados com o mesmo nome de outro conjunto de dados no mesmo workspace, acrescente o GUID do conjunto de dados ao nome do conjunto de dados. Obtenha o nome do conjunto de dados *e* o GUID quando estiver conectado ao workspace no SSMS. 

### <a name="delay-in-datasets-shown"></a>Atraso em conjuntos de dados mostrado

Ao se conectar a um workspace, as alterações em conjuntos de dados novos, excluídos e renomeados podem levar até 5 minutos para serem exibidas. 

### <a name="unsupported-datasets"></a>Conjuntos de dados sem suporte

Os conjuntos de dados a seguir não são acessíveis por meio de pontos de extremidade XMLA. Esses conjuntos de dados *não* serão exibidos no workspace no SSMS nem em outras ferramentas: 

- Conjuntos de dados com uma conexão dinâmica com um modelo do Analysis Services. 
- Conjuntos de dados com os dados de push usando a API REST.
- Conjuntos de dados de uma pasta de trabalho do Excel. 

Os seguintes conjuntos de dados no serviço do Power BI não são compatíveis:   

- Conjuntos de dados com uma conexão dinâmica com um conjunto de dados do Power BI.

### <a name="roles-and-role-memberships"></a>Funções e associações de função

Atualmente, as funções de modelo e as associações de função não podem ser descobertas ou exibidas usando os pontos de extremidade XMLA.

## <a name="disable-connectivity"></a>Desabilitar a conectividade

Por padrão, a conectividade de ponto de extremidade XMLA está habilitada para a carga de trabalho dos conjuntos de dados. Você pode desabilitar a conectividade nas [Configurações de carga de trabalho](service-admin-premium-workloads.md#workload-settings).

## <a name="audit-logs"></a>Logs de auditoria 

Quando as ferramentas e os aplicativos cliente se conectam a um workspace, o acesso por meio de pontos de extremidade XMLA é registrado nos logs de auditoria do Power BI na operação **GetWorkspaces**. Para saber mais, confira [Como auditar o Power BI](service-admin-auditing.md).

## <a name="see-also"></a>Consulte também

[Referências do Analysis Services](https://docs.microsoft.com/bi-reference/#pivot=home&panel=home-all)   
[SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/sql-server-management-studio-ssms)   
[Protocolo Tabular do SQL Server Analysis Services](https://docs.microsoft.com/openspecs/sql_server_protocols/ms-ssas-t/b98ed40e-c27a-4988-ab2d-c9c904fe13cf)   
[DMVs (exibições de gerenciamento dinâmico)](https://docs.microsoft.com/sql/analysis-services/instances/use-dynamic-management-views-dmvs-to-monitor-analysis-services)   


Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
