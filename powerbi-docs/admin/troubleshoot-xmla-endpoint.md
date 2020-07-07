---
title: Solucionar problemas de conectividade de ponto de extremidade XMLA no Power BI Premium (versão prévia)
description: Descreve como solucionar problemas de conectividade por meio do ponto de extremidade XMLA no Power BI Premium.
author: minewiskan
ms.author: owend
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: troubleshooting
ms.date: 06/16/2020
ms.custom: seodec18, css_fy20Q4
LocalizationGroup: Premium
ms.openlocfilehash: be55180f57fec683b8da426e6c73bb95d6365d2f
ms.sourcegitcommit: a453ba52aafa012896f665660df7df7bc117ade5
ms.contentlocale: pt-BR
ms.lasthandoff: 06/27/2020
ms.locfileid: "85485520"
---
# <a name="troubleshoot-xmla-endpoint-connectivity"></a>Solucionar problemas de conectividade de ponto de extremidade XMLA

Os pontos de extremidade XMLA no Power BI Premium usam o protocolo de comunicação do Analysis Services nativo para acessar conjuntos de dados do Power BI. Por isso, a solução de problemas do ponto de extremidade XMLA é muito parecida com a solução de problemas de uma conexão do Analysis Services típica. No entanto, algumas diferenças em relação a dependências específicas do Power BI se aplicam.

## <a name="before-you-begin"></a>Antes de começar

Antes de solucionar problemas de um cenário do ponto de extremidade XMLA, examine os fundamentos abordados em [Conectividade do conjunto de dados com o ponto de extremidade XMLA](service-premium-connect-tools.md). A maioria dos casos de uso de pontos de extremidade XMLA mais comuns é abordada aqui. Outros guias de solução de problemas do Power BI, como [Solucionar problemas de gateways – Power BI](../connect-data/service-gateway-onprem-tshoot.md) e [Solucionar problemas do recurso Analisar no Excel](../collaborate-share/desktop-troubleshooting-analyze-in-excel.md), também podem ser úteis.

## <a name="enabling-the-xmla-endpoint"></a>Habilitar o ponto de extremidade XMLA

O ponto de extremidade XMLA pode ser habilitado nas capacidades do Power BI Premium e Power BI Embedded. Em capacidades menores, como uma A1 com apenas 2,5 GB de memória, você poderá encontrar um erro nas configurações de capacidade ao tentar definir o ponto de extremidade XMLA para **Leitura/Gravação** e selecionar **Aplicar**. O erro indica "Houve um problema com as configurações da carga de trabalho. Tente novamente em alguns minutos.".

Confira algumas opções:

- Limite o consumo de memória de outros serviços na capacidade, como fluxos de dados, a 40% ou menos, ou desabilite completamente um serviço desnecessário.  
- Atualize a capacidade para um SKU maior. Por exemplo, atualizar de uma capacidade A1 para A3 resolve o problema de configuração sem precisar desabilitar os fluxos de dados.

Você também deve habilitar a [configuração Exportar dados](service-premium-connect-tools.md#security) no nível do locatário no portal de administração do Power BI. Essa configuração também é necessária para o recurso Analisar no Excel.

## <a name="establishing-a-client-connection"></a>Estabelecer uma conexão cliente

Após a habilitação do ponto de extremidade XMLA, recomendamos testar a conectividade com um espaço de trabalho na capacidade. Para saber mais, confira [Conectar a um workspace Premium](service-premium-connect-tools.md#connecting-to-a-premium-workspace). Além disso, leia a seção [Requisitos de conexão](service-premium-connect-tools.md#connection-requirements) para obter dicas úteis e informações sobre as limitações de conectividade XMLA atuais.

### <a name="connecting-with-a-service-principal"></a>Conectar com uma entidade de serviço

Se você habilitou configurações de locatário para permitir que entidades de serviço usem APIs do Power BI, conforme descrito em [Habilitar entidades de serviço](service-premium-service-principal.md#enable-service-principals), poderá se conectar a um ponto de extremidade XMLA usando uma entidade de serviço. A entidade de serviço requer o mesmo nível de permissões de acesso no workspace ou no nível de conjunto de dados que usuários comuns.

Para usar uma entidade de serviço, especifique as informações de identidade do aplicativo na cadeia de conexão, como:

- `User ID=<app:appid@tenantid>`
- `Password=<application secret>`

Por exemplo:

`Data Source=powerbi://api.powerbi.com/v1.0/myorg/Contoso;Initial Catalog=PowerBI_Dataset;User ID=app:91ab91bb-6b32-4f6d-8bbc-97a0f9f8906b@19373176-316e-4dc7-834c-328902628ad4;Password=6drX...;`

Se você receber o seguinte erro:

"Não podemos nos conectar ao conjunto de dados devido a informações de conta incompletas. Para entidades de serviço, especifique a ID do locatário junto com a ID do aplicativo usando o formato aplicativo:\<appId>@\<tenantId> e tente novamente."

Especifique a ID do locatário com a ID do aplicativo usando o formato correto.

Também é válido especificar a ID do aplicativo sem a ID do locatário. No entanto, nesse caso, você deve substituir o alias `myorg` na URL da fonte de dados pela ID de locatário real. O Power BI pode localizar a entidade de serviço no locatário correto. Como prática recomendada, use o alias `myorg` e especifique a ID do locatário com a ID do aplicativo no parâmetro ID de usuário.

### <a name="connecting-with-azure-active-directory-b2b"></a>Conectar com o Azure Active Directory B2B

Com o suporte para B2B (business-to-business) do Azure AD (Azure Active Directory ) no Power BI, você pode fornecer aos usuários convidados externos acesso a conjuntos de dados por meio do ponto de extremidade XMLA. Habilite a configuração [Compartilhar conteúdo com usuários externos](service-admin-portal.md#export-and-sharing-settings) no portal de administração do Power BI. Para saber mais, confira [Distribuição do conteúdo do Power BI para usuários convidados externos com o Azure AD B2B](service-admin-azure-ad-b2b.md).

## <a name="deploying-a-dataset"></a>Implantar um conjunto de dados

Você pode implantar um projeto de modelo tabular do Visual Studio (SSDT) em um workspace do Power BI Premium ou no Azure Analysis Services. No entanto, ao implantar em um workspace do Power BI Premium, há algumas considerações adicionais. Examine a seção [Implantar projetos de modelo do Visual Studio (SSDT)](service-premium-connect-tools.md#deploy-model-projects-from-visual-studio-ssdt) no artigo Conectividade do conjunto de dados com o ponto de extremidade XMLA.

### <a name="deploying-a-new-model"></a>Implantar um novo modelo

Na configuração padrão, o Visual Studio tenta processar o modelo como parte da operação de implantação para carregar dados no conjunto a partir das fontes de dados. Conforme descrito em [Implantar projetos de modelo do Visual Studio (SSDT)](service-premium-connect-tools.md#deploy-model-projects-from-visual-studio-ssdt), essa operação pode falhar porque as credenciais da fonte de dados não podem ser especificadas como parte da operação de implantação. Em vez disso, se as credenciais da sua fonte de dados ainda não estiverem definidas para nenhum dos conjuntos de dados existentes, você deverá especificar as credenciais da fonte de dados nas configurações do conjunto usando a interface do usuário do Power BI (**Conjunto de dados** > **Configurações** > **Credenciais da fonte de dados** > **Editar credenciais**). Após a definição das credenciais da fonte de dados, o Power BI poderá aplicar essas credenciais automaticamente a qualquer novo conjunto de dados, depois que a implantação de metadados for bem-sucedida e o conjunto tiver sido criado.

Se o Power BI não puder associar o novo conjunto de dados às credenciais da fonte de dados, você receberá um erro indicando "Não é possível processar o banco de dados. Motivo: Falha ao salvar as modificações no servidor." com o código de erro "DMTS_DatasourceHasNoCredentialError", como mostrado abaixo:

:::image type="content" source="media/troubleshoot-xmla-endpoint/deploy-refresh-error.png" alt-text="Erro da implantação de modelo":::

Para evitar a falha de processamento, defina as **Opções de Implantação** > **Opções de Processamento** para **Não Processar**, como mostrado na imagem a seguir. O Visual Studio implanta apenas os metadados. Você pode configurar as credenciais da fonte de dados e clicar em **Atualizar agora** para o conjunto de dados na interface do usuário do Power BI. Para obter informações sobre como solucionar problemas de processamento, confira a seção [Atualizar um conjunto de dados](#refreshing-a-dataset) mais adiante neste artigo.

:::image type="content" source="media/troubleshoot-xmla-endpoint/do-not-process.png" alt-text="Opção Não Processar":::

### <a name="new-project-from-an-existing-dataset"></a>Novo projeto de um conjunto de dados existente

Não há suporte para a criação de um projeto tabular no Visual Studio por meio da importação dos metadados de um conjunto de dados existente em um workspace do Power BI Premium. No entanto, você pode se conectar ao conjunto de dados usando o SQL Server Management Studio, gerar scripts com os metadados e reutilizá-los em outros projetos tabulares.

## <a name="migrating-a-dataset-to-power-bi"></a>Migrar um conjunto de dados para o Power BI

É recomendável especificar o nível de compatibilidade 1500 (ou superior) para modelos tabulares. Esse nível de compatibilidade oferece suporte à maioria dos recursos e tipos de fonte de dados. Os níveis de compatibilidade posteriores são compatíveis com níveis anteriores.

### <a name="unsupported-data-providers"></a>Provedores de dados sem suporte

No nível de compatibilidade 1500, o Power BI dá suporte aos seguintes tipos de fonte de dados:

- Fontes de dados do provedor (herdadas com uma cadeia de conexão nos metadados de modelo).
- Fontes de dados estruturadas (introduzidas com o nível de compatibilidade 1400).
- Declarações M embutidas de fontes de dados (conforme o Power BI Desktop as declara).

Recomendamos que você use fontes de dados estruturadas, que o Visual Studio criará por padrão ao passar por Importar fluxo de dados. No entanto, se você estiver planejando migrar para o Power BI um modelo existente que usa uma fonte de dados de provedor, verifique se essa fonte depende de um provedor de dados com suporte. Especificamente, o Driver do Microsoft OLE DB para SQL Server e qualquer driver ODBC de terceiros. Para o Driver do OLE DB para SQL Server, você deve alternar a definição da fonte de dados para o Provedor de Dados .NET Framework para SQL Server. Para drivers ODBC de terceiros que podem estar indisponíveis no serviço do Power BI, você deve alternar para uma definição de fonte de dados estruturada.

Também recomendamos substituir o Driver do Microsoft OLE DB para SQL Server (SQLNCLI11) desatualizado em suas definições de fonte de dados do SQL Server pelo Provedor de Dados .NET Framework para SQL Server.

A tabela a seguir fornece um exemplo de cadeia de conexão do Provedor de Dados .NET Framework para SQL Server que substitui uma cadeia de conexão correspondente para o Driver do OLE DB para SQL Server.

|OLE DB Driver for SQL Server  |Provedor de dados do .NET Framework para SQL Server   |
|---------|---------|
|`Provider=SQLNCLI11;Data Source=sqldb.database.windows.net;Initial Catalog=AdventureWorksDW;Trusted_Connection=yes;`    |   `Data Source=sqldb.database.windows.net;Initial Catalog=AdventureWorksDW2016;Integrated Security=SSPI;Encrypt=true;TrustServerCertificate=false`       |

### <a name="cross-referencing-partition-sources"></a>Fontes de partição de referência cruzada

Assim como há vários tipos de fonte de dados, também há vários tipos de fonte de partição que um modelo tabular pode incluir a fim de importar dados para uma tabela. Especificamente, uma partição pode usar uma fonte de partição de consulta ou uma fonte de partição M. Esses tipos de fonte de partição, por sua vez, podem referenciar fontes de dados de provedor ou fontes de dados estruturadas. Enquanto os modelos tabulares no Azure Analysis Services dão suporte à referência cruzada desses vários tipos de partição e fontes de dados, o Power BI aplica uma relação mais estrita. As fontes de partição de consulta devem referenciar fontes de dados de provedor, e as fontes de partição M devem referenciar fontes de dados estruturadas. Outras combinações que não têm suporte no Power BI. Caso você queira migrar um conjunto de dados de referência cruzada, a seguinte tabela descreve as configurações com suporte:  

|Fonte de dados   |Origem da partição   |Comentários   |Com suporte no Power BI Premium com o ponto de extremidade XMLA   |
|---------|---------|---------|---------|
|Fonte de dados do provedor      |   Fonte de partição de consulta      |   O mecanismo AS usa a pilha de conectividade baseada em cartucho para acessar a fonte de dados.       |     Sim     |
|Fonte de dados do provedor      |   Origem da partição M       |   O mecanismo AS converte a fonte de dados do provedor em uma fonte de dados estruturada genérica e usa o Mecanismo de Mashup para importar dados.       |    Não     |
|Fonte de dados estruturada      |     Fonte de partição de consulta     |    O mecanismo AS encapsula a consulta nativa na fonte de partição em uma expressão M e usa o Mecanismo de Mashup para importar os dados.      |    Não     |
|Fonte de dados estruturada      |    Origem da partição M      |     O mecanismo AS usa o Mecanismo de Mashup para importar os dados.     |   Sim      |

## <a name="refreshing-a-dataset"></a>Atualizar um conjunto de dados

Os pontos de extremidade XMLA permitem executar operações de atualização em modelos tabulares, bem como em conjuntos de dados criados no Power BI Desktop. Para dar suporte ao último item, especifique a configuração Formato de armazenamento aprimorado. Essa configuração será necessária se você quiser realizar o processamento ou outras operações de leitura/gravação usando o ponto de extremidade XMLA. Você pode encontrar a configuração no Power BI Desktop em Versão prévia dos recursos. Após a configuração, publique a solução PBIX novamente em seu workspace do Power BI Premium.  

O Power BI retornará o seguinte erro se você realizar uma atualização por meio do ponto de extremidade XMLA em um modelo sem metadados aprimorados: "Há suporte para a operação somente no modelo com a propriedade 'DefaultPowerBIDataSourceVersion' definida como 'PowerBI_V3' no Power BI Premium."

### <a name="data-sources-and-impersonation"></a>Fontes de dados e representação

As configurações de representação que você pode definir para fontes de dados do provedor não são relevantes para o Power BI. O Power BI usa um mecanismo diferente baseado nas configurações do conjunto de dados para gerenciar as credenciais da fonte de dados. Por isso, selecione **Conta de Serviço** se você estiver criando uma Fonte de dados de provedor.

:::image type="content" source="media/troubleshoot-xmla-endpoint/impersonate-services-account.png" alt-text="Representar conta de serviço":::

### <a name="fine-grained-processing"></a>Processamento refinado

Quando é disparada uma atualização agendada ou sob demanda no Power BI, ele normalmente atualiza todo o conjunto de todos. Em muitos casos, é mais eficiente executar atualizações de forma mais seletiva. Você pode realizar tarefas de processamento refinado no SSMS (SQL Server Management Studio), conforme mostrado abaixo ou usando ferramentas ou scripts de terceiros.

:::image type="content" source="media/troubleshoot-xmla-endpoint/process-tables.png" alt-text="Processar tabelas no SSMS":::

## <a name="see-also"></a>Consulte também

[Conectividade do conjunto de dados com o ponto de extremidade XMLA](service-premium-connect-tools.md)   
[Automatizar tarefas do conjunto de dados e do workspace Premium com entidades de serviço](service-premium-service-principal.md)   
[Solucionar problemas do recurso Analisar no Excel](../collaborate-share/desktop-troubleshooting-analyze-in-excel.md)   
[Implantação de solução de modelo tabular](https://docs.microsoft.com/analysis-services/deployment/tabular-model-solution-deployment?view=power-bi-premium-current)
