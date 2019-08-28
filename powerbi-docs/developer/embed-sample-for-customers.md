---
title: Análise integrada para inserir conteúdo do Power BI em seu aplicativo para seus clientes
description: Aprenda a integrar ou inserir um painel, um bloco ou um relatório em um aplicativo usando as APIs do Power BI para análise integrada para seus clientes. Saiba como integrar o Power BI ao seu aplicativo usando o software de análise integrada, ferramentas de análise integrada ou ferramentas de business intelligence integrada.
author: rkarlin
ms.author: rkarlin
manager: kfile
ms.reviewer: nishalit
ms.topic: tutorial
ms.service: powerbi
ms.subservice: powerbi-developer
ms.custom: seodec18
ms.date: 04/02/2019
ms.openlocfilehash: e945e19505d7342cf3ba2236b4811e87a69730ab
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "65710967"
---
# <a name="tutorial-embed-power-bi-content-into-an-application-for-your-customers"></a>Tutorial: Inserir conteúdo do Power BI em um aplicativo para seus clientes

Com o **Power BI Embedded no Azure**, você pode inserir relatórios, painéis ou blocos em um aplicativo usando app owns data. **App owns data** representa um aplicativo que usa o Power BI como sua plataforma de análise incorporada. Como **desenvolvedor ISV**, é possível criar conteúdo do Power BI que exibe relatórios, painéis ou blocos em um aplicativo totalmente integrado e interativo, sem precisar que os usuários tenham uma licença do Power BI. Este tutorial demonstra como integrar um relatório em um aplicativo usando o SDK do .NET do Power BI com a API JavaScript do Power BI usando o **Power BI Embedded no Azure** para clientes.

![Relatório de Inserção do Power BI](media/embed-sample-for-customers/embed-sample-for-customers-035.png)

Neste tutorial, você aprenderá a:
> [!div class="checklist"]
> * Registrar um aplicativo no Azure.
> * Insira um relatório do Power BI em um aplicativo.

## <a name="prerequisites"></a>Pré-requisitos

Para começar, você precisa ter:

* Uma [conta Power BI Pro](../service-self-service-signup-for-power-bi.md) (uma conta mestra que é um nome de usuário e senha para entrar em sua conta do Power BI Pro) ou uma [entidade de serviço (token somente de aplicativo)](embed-service-principal.md).
* Uma assinatura da [Microsoft Azure](https://azure.microsoft.com/).
* Você precisa ter seu próprio [locatário do Azure Active Directory](create-an-azure-active-directory-tenant.md) configurado.

Se não estiver inscrito no **Power BI Pro**, [inscreva-se para uma avaliação gratuita](https://powerbi.microsoft.com/pricing/) antes de começar.

Caso você não tenha uma assinatura do Azure, crie uma [conta gratuita](https://azure.microsoft.com/free/?WT.mc_id=A261C142F) antes de começar.

## <a name="set-up-your-embedded-analytics-development-environment"></a>Configurar seu ambiente de desenvolvimento de análise integrada

Antes de começar a inserir relatórios, dashboard ou blocos no seu aplicativo, você precisará verificar se o ambiente permite inserção com o Power BI.

Você pode examinar a [Ferramenta de configuração de integração](https://aka.ms/embedsetup/AppOwnsData) para que possa iniciar rapidamente e baixar um aplicativo de exemplo que ajuda a criar um ambiente e a inserir um relatório.

No entanto, se você optar por configurar o ambiente manualmente, você poderá continuar abaixo.

### <a name="register-an-application-in-azure-active-directory-azure-ad"></a>Registrar um aplicativo no Azure AD (Azure Active Directory)

[Registre seu aplicativo](register-app.md) no Azure Active Directory para permitir que ele tenha acesso às [APIs REST do Power BI](https://docs.microsoft.com/rest/api/power-bi/). Registrando o aplicativo, você pode estabelecer uma identidade para ele e especificar permissões para recursos REST do Power BI. Dependendo de se você deseja usar uma conta mestra ou [entidade de serviço](embed-service-principal.md), determine como começar a registrar um aplicativo.

O método você adota afeta o tipo de aplicativo que você registra no Azure.

Se você continuar usando uma conta mestra, continue com o registro de um aplicativo **nativo**. Você usa um aplicativo Nativo porque você está trabalhando com um logon não interativo.

No entanto, se você continuar usando a entidade de serviço, precisará continuar com o registro de um **aplicativo Web do lado do servidor**. Registre um aplicativo Web do lado do servidor para criar um segredo do aplicativo.

## <a name="set-up-your-power-bi-environment"></a>Configurar seu ambiente do Power BI

### <a name="create-an-app-workspace"></a>Criar um workspace de aplicativo

Se você estiver inserindo relatórios, painéis ou blocos para seus clientes, precisará colocar o conteúdo dentro de um workspace do aplicativo. Há diferentes tipos de workspaces que você pode configurar: o [workspaces tradicionais](../service-create-workspaces.md) ou o [novos workspaces](../service-create-the-new-workspaces.md). Se você está usando uma conta *mestra*, não importa qual tipo de workspaces você usa. No entanto, se você usa *[entidade de serviço](embed-service-principal.md)* para entrar em seu aplicativo, é necessário usar os novos workspaces. Em qualquer cenário, tanto a conta *mestra* quanto a *entidade de serviço* devem ser administradoras dos workspaces do aplicativo envolvido com o seu aplicativo.

### <a name="create-and-publish-your-reports"></a>Crie e publique seus relatórios

É possível criar seus relatórios e conjuntos de dados usando o Power BI Desktop e, em seguida, publicar esses relatórios em um workspace do aplicativo. Há duas maneiras de realizar essa tarefa: Como um usuário final, você pode publicar relatórios para um workspace de aplicativo tradicional com uma conta mestra (licença do Power BI Pro). Se você estiver usando a entidade de serviço, poderá publicar relatórios nos novos workspaces usando as [APIs de REST do Power BI](https://docs.microsoft.com/rest/api/power-bi/imports/postimportingroup).

As etapas a seguir explicam como publicar seu relatório PBIX em seu workspace do Power BI.

1. Baixe o exemplo [Blog Demo](https://github.com/Microsoft/powerbi-desktop-samples) do GitHub.

    ![relatório de exemplo](media/embed-sample-for-customers/embed-sample-for-customers-026-1.png)

2. Abra o relatório de exemplo do PBIX no **Power BI Desktop**.

   ![Relatório de área de trabalho do PBI](media/embed-sample-for-customers/embed-sample-for-customers-027.png)

3. Publique em **workspaces do aplicativo**. Esse processo é diferente dependendo de se você está usando uma conta mestra (licença do Power Pro) ou entidade de serviço. Se você estiver usando uma conta mestra, poderá publicar seu relatório por meio do Power BI Desktop.  Agora, se você estiver usando a entidade de serviço, deverá usar as APIs REST do Power BI.

## <a name="embed-content-using-the-sample-application"></a>Insira conteúdo usando o aplicativo de exemplo

Este exemplo é deliberadamente mantido simples para fins de demonstração. Fica a seu encargo ou de seus desenvolvedores proteger o segredo do aplicativo ou as credenciais da conta mestra.

Siga as etapas abaixo para começar a inserir seu conteúdo usando o aplicativo de exemplo.

1. Baixe o [Visual Studio](https://www.visualstudio.com/) (versão 2013 ou posterior). Baixe a versão mais recente do [pacote do NuGet](https://www.nuget.org/profiles/powerbi).

2. Baixe o [exemplo App Owns Data](https://github.com/Microsoft/PowerBI-Developer-Samples) do GitHub para começar.

    ![Exemplo de aplicativo App Owns Data](media/embed-sample-for-customers/embed-sample-for-customers-026.png)

3. Abra o arquivo **Web.config** no aplicativo de exemplo. Há campos que você precisa preencher para executar o aplicativo. Você pode escolher **MasterUser** ou **ServicePrincipal** para **AuthenticationType**. Dependendo de qual tipo de método de autenticação é escolhido, há campos diferentes para preencher.

    > [!Note]
    > O padrão **AuthenticationType** neste exemplo é MasterUser.

    <center>

    | **MasterUser** <br> (licença do Power BI Pro) | **ServicePrincipal** <br> (token somente de aplicativo)|
    |---------------|-------------------|
    | [applicationId](#application-id) | [applicationId](#application-id) |
    | [workspaceId](#workspace-id) | [workspaceId](#workspace-id) |
    | [reportId](#report-id) | [reportId](#report-id) |
    | [pbiUsername](#power-bi-username-and-password) |  |
    | [pbiPassword](#power-bi-username-and-password) |  |
    |  | [applicationsecret](#application-secret) |
    |  | [tenant](#tenant) |

   </center>

    ![Arquivo de configuração da Web](media/embed-sample-for-customers/embed-sample-for-customers-030.png)

### <a name="application-id"></a>ID do aplicativo

Esse atributo é necessário para ambos os AuthenticationTypes (conta mestra e [entidade de serviço](embed-service-principal.md)).

Preencha as informações de **applicationId** com a **ID do Aplicativo** do **Azure**. A **applicationId** é usada pelo aplicativo para identificar-se aos usuários para os quais você está solicitando permissões.

Para obter a **applicationId**, siga estas etapas:

1. Entre no [Portal do Azure](https://portal.azure.com).

2. No painel de navegação esquerdo, escolha **Todos os serviços** e selecione **Registros de aplicativo**.

    ![Pesquisa de registro de aplicativo](media/embed-sample-for-customers/embed-sample-for-customers-003.png)

3. Selecione o aplicativo que precisa usar a **applicationId**.

    ![Escolhendo o aplicativo](media/embed-sample-for-customers/embed-sample-for-customers-006.png)

4. Há uma **ID do Aplicativo** listada como GUID. Use essa **ID do aplicativo** como a **applicationId** do aplicativo.

    ![applicationId](media/embed-sample-for-customers/embed-sample-for-customers-007.png)

### <a name="workspace-id"></a>ID do workspace

Esse atributo é necessário para ambos os AuthenticationTypes (conta mestra e [entidade de serviço](embed-service-principal.md)).

Preencha as informações de **workspaceId** com o GUID do workspace (grupo) do aplicativo do Power BI. Você pode obter essas informações da URL quando conectado ao serviço do Power BI ou usando o Powershell.

URL <br>

![workspaceId](media/embed-sample-for-customers/embed-sample-for-customers-031.png)

PowerShell <br>

```powershell
Get-PowerBIworkspace -name "App Owns Embed Test"
```

   ![workspaceId do powershell](media/embed-sample-for-customers/embed-sample-for-customers-031-ps.png)

### <a name="report-id"></a>ID do Relatório

Esse atributo é necessário para ambos os AuthenticationTypes (conta mestra e [entidade de serviço](embed-service-principal.md)).

Preencha as informações de **reportId** com o GUID de relatório do Power BI. Você pode obter essas informações da URL quando conectado ao serviço do Power BI ou usando o Powershell.

URL<br>

![reportId](media/embed-sample-for-customers/embed-sample-for-customers-032.png)

PowerShell <br>

```powershell
Get-PowerBIworkspace -name "App Owns Embed Test" | Get-PowerBIReport
```

![reportId do powershell](media/embed-sample-for-customers/embed-sample-for-customers-032-ps.png)

### <a name="power-bi-username-and-password"></a>Nome de usuário e senha do Power BI

Esses atributos são necessárias somente para a conta mestra AuthenticationType.

Se você estiver usando [entidade de serviço](embed-service-principal.md) para autenticar, não precisa cumprir os atributos de nome de usuário ou senha.

* Preencha o **pbiUsername** com a conta mestra do Power BI.
* Preencha o **pbiPassword** com a senha da conta mestra do Power BI.

### <a name="application-secret"></a>Segredo do aplicativo

Esse atributo é necessário somente para a [entidade de serviço](embed-service-principal.md) AuthenticationType.

Preencha as informações de **ApplicationSecret** da seção **Chaves** na seção **Registros de aplicativo** no **Azure**.  Esse atributo funciona ao usar a [entidade de serviço](embed-service-principal.md).

Para obter o **ApplicationSecret**, siga estas etapas:

1. Entre no [portal do Azure](https://portal.azure.com).

2. No painel de navegação esquerdo, selecione **Todos os serviços** e **Registros de aplicativo**.

    ![Pesquisa de registro de aplicativo](media/embed-sample-for-customers/embed-sample-for-customers-003.png)

3. Selecione o aplicativo que precisa usar o **ApplicationSecret**.

    ![Escolha um aplicativo](media/embed-sample-for-customers/embed-sample-for-customers-0038.png)

4. Selecione **certificados e segredos** sob **gerenciar**.

5. Selecione **novos segredos de cliente**.

6. Insira um nome na caixa **Descrição** e selecione uma duração. Em seguida, selecione **Salvar** para obter o **Valor** para seu aplicativo. Quando você fecha o painel **Chaves** depois de salvar o valor da chave, o campo de valor é mostrado como oculto. Neste ponto, você não pode recuperar o valor da chave. Se você perder o valor da chave, crie uma nova no portal do Azure.

    ![Valor da chave](media/embed-sample-for-customers/embed-sample-for-customers-042.png)

### <a name="tenant"></a>Locatário

Esse atributo é necessário somente para a [entidade de serviço](embed-service-principal.md) AuthenticationType.

Preencha as informações do **locatário** com sua ID de locatário do Azure. Essas informações podem ser obtidas no [centro de administração do Azure AD](/onedrive/find-your-office-365-tenant-id) quando você estiver conectado ao serviço do Power BI ou usando o Powershell.

### <a name="run-the-application"></a>Execute o aplicativo

1. Selecione **Executar** no **Visual Studio**.

    ![Execute o aplicativo](media/embed-sample-for-customers/embed-sample-for-customers-033.png)

2. Selecione **Inserir Relatório**. Dependendo do conteúdo que você optar por testar – relatórios, painéis ou blocos –, selecione essa opção no aplicativo.

    ![Selecione um conteúdo](media/embed-sample-for-customers/embed-sample-for-customers-034.png)

3. Agora, você pode exibir o relatório no aplicativo de exemplo.

    ![Exibir o aplicativo](media/embed-sample-for-customers/embed-sample-for-customers-035.png)

## <a name="embed-content-within-your-application"></a>Inserir conteúdo em seu aplicativo

Embora as etapas para inserir seu conteúdo possam ser feitas com as [APIs REST do Power BI](https://docs.microsoft.com/rest/api/power-bi/), os códigos de exemplo descritos neste artigo são feitos com o **SDK do .NET**.

A inserção para seus clientes dentro de seu aplicativo exige que você obtenha um **token de acesso** para sua conta mestra ou [entidade de serviço](embed-service-principal.md) do **Azure AD**. É necessário obter um [token de acesso do Azure AD](get-azuread-access-token.md#access-token-for-non-power-bi-users-app-owns-data) para o seu aplicativo do Power BI antes de fazer chamadas a [APIs REST do Power BI](https://docs.microsoft.com/rest/api/power-bi/).

Para criar o cliente do Power BI com o **token de acesso**, crie o objeto de cliente do Power BI que permitirá interagir com as [APIs REST do Power BI](https://docs.microsoft.com/rest/api/power-bi/). Crie o objeto do cliente do Power BI encapsulando o **AccessToken** com um objeto ***Microsoft.Rest.TokenCredentials***.

```csharp
using Microsoft.IdentityModel.Clients.ActiveDirectory;
using Microsoft.Rest;
using Microsoft.PowerBI.Api.V2;

var tokenCredentials = new TokenCredentials(authenticationResult.AccessToken, "Bearer");

// Create a Power BI Client object. it's used to call Power BI APIs.
using (var client = new PowerBIClient(new Uri(ApiUrl), tokenCredentials))
{
    // Your code to embed items.
}
```

### <a name="get-the-content-item-you-want-to-embed"></a>Obter o item de conteúdo que você deseja inserir

É possível usar o objeto do cliente do Power BI para recuperar uma referência ao item que deseja inserir.

Veja um exemplo de código de como recuperar o primeiro relatório de um workspace específico.

*Um exemplo de obtenção de um item de conteúdo, seja um bloco, um relatório ou um dashboard que você deseja inserir, está disponível no arquivo Services\EmbedService.cs no [aplicativo de exemplo](https://github.com/Microsoft/PowerBI-Developer-Samples).*

```csharp
using Microsoft.PowerBI.Api.V2;
using Microsoft.PowerBI.Api.V2.Models;

// You need to provide the workspaceId where the dashboard resides.
ODataResponseListReport reports = await client.Reports.GetReportsInGroupAsync(workspaceId);

// Get the first report in the group.
Report report = reports.Value.FirstOrDefault();
```

### <a name="create-the-embed-token"></a>Criar o token de inserção

Gerou um token de inserção, que pode ser usado a partir da API do JavaScript. O token de inserção é específico ao item que está sendo inserido. Sempre que você inserir uma parte do conteúdo do Power BI, precisará criar um novo token de inserção para ele. Para obter mais informações, incluindo qual **accessLevel** usar, consulte [API GenerateToken](https://msdn.microsoft.com/library/mt784614.aspx).

*Um exemplo de criação de um token de inserção para um relatório, dashboard ou bloco está disponível dentro do arquivo Services\EmbedService.cs no [aplicativo de exemplo](https://github.com/Microsoft/PowerBI-Developer-Samples).*

```csharp
using Microsoft.PowerBI.Api.V2;
using Microsoft.PowerBI.Api.V2.Models;

// Generate Embed Token.
var generateTokenRequestParameters = new GenerateTokenRequest(accessLevel: "view");
EmbedToken tokenResponse = client.Reports.GenerateTokenInGroup(workspaceId, report.Id, generateTokenRequestParameters);

// Generate Embed Configuration.
var embedConfig = new EmbedConfig()
{
    EmbedToken = tokenResponse,
    EmbedUrl = report.EmbedUrl,
    Id = report.Id
};
```

Uma classe é criada para **EmbedConfig** e **TileEmbedConfig**. Uma amostra está disponível nos arquivos **Modelos\EmbedConfig.cs** e **Modelos\TileEmbedConfig.cs**.

### <a name="load-an-item-using-javascript"></a>Carregar um item usando o JavaScript

Use o JavaScript para carregar um relatório em um elemento div na página da Web.

Para obter um exemplo completo de como usar a API JavaScript, use a [ferramenta de Playground](https://microsoft.github.io/PowerBI-JavaScript/demo). A ferramenta de Playground é uma maneira rápida de experimentar diferentes tipos de exemplos do Power BI Embedded. Também é possível obter mais informações sobre a API de JavaScript, acessando a página da [wiki PowerBI-JavaScript](https://github.com/Microsoft/powerbi-javascript/wiki).

Aqui está uma amostra que usa um modelo de **EmbedConfig** e de **TileEmbedConfig**, juntamente com as exibições de um relatório.

*Um exemplo de adição de uma exibição de um bloco, relatório ou painel está disponível nos arquivos Views\Home\EmbedReport.cshtml, Views\Home\EmbedDashboard.cshtml ou Views\Home\Embedtile.cshtml no [aplicativo de exemplo](#embed-content-using-the-sample-application).*

```javascript
<script src="~/scripts/powerbi.js"></script>
<div id="reportContainer"></div>
<script>
    // Read embed application token from Model
    var accessToken = "@Model.EmbedToken.Token";

    // Read embed URL from Model
    var embedUrl = "@Html.Raw(Model.EmbedUrl)";

    // Read report Id from Model
    var embedReportId = "@Model.Id";

    // Get models. models contains enums that can be used.
    var models = window['powerbi-client'].models;

    // Embed configuration used to describe what and how to embed.
    // This object is used when calling powerbi.embed.
    // This also includes settings and options such as filters.
    // You can find more information at https://github.com/Microsoft/PowerBI-JavaScript/wiki/Embed-Configuration-Details.
    var config = {
        type: 'report',
        tokenType: models.TokenType.Embed,
        accessToken: accessToken,
        embedUrl: embedUrl,
        id: embedReportId,
        permissions: models.Permissions.All,
        settings: {
            filterPaneEnabled: true,
            navContentPaneEnabled: true
        }
    };

    // Get a reference to the embedded report HTML element
    var reportContainer = $('#reportContainer')[0];

    // Embed the report and display it within the div container.
    var report = powerbi.embed(reportContainer, config);
</script>
```

## <a name="move-to-production"></a>Mover para a produção

Agora que você terminou o desenvolvimento do seu aplicativo, é hora de conferir uma capacidade dedicada para o workspace do seu aplicativo. 

> [!Important]
> É necessário ter capacidade dedicada para passar para a produção.

### <a name="create-a-dedicated-capacity"></a>Criar uma capacidade dedicada

Ao criar uma capacidade dedicada, é possível tirar proveito de um recurso dedicado para o seu cliente. Você pode comprar uma capacidade dedicada no [portal do Microsoft Azure](https://portal.azure.com). Para obter detalhes sobre como criar uma capacidade do Power BI Embedded, veja [Criar capacidade do Power BI Embedded no portal do Azure](azure-pbie-create-capacity.md).

Use a tabela a seguir para determinar qual capacidade do Power BI Embedded melhor atende as suas necessidades.

| Nó de capacidade | Total de núcleos<br/>*(Back-end + front-end)* | Núcleos de back-end | Núcleos de front-end | Limites de conexão dinâmica/DirectQuery|
| --- | --- | --- | --- | --- | --- |
| A1 |1 núcleo virtual |0,5 núcleo, 3 GB de RAM |0,5 núcleo |0 5 por segundo |
| A2 |2 núcleos virtuais |1 núcleo, 5 GB de RAM |1 núcleo | 10 por segundo |
| A3 |4 núcleos virtuais |2 núcleos, 10 GB de RAM |2 núcleos | 15 por segundo |
| A4 |8 núcleos virtuais |4 núcleos, 25 GB de RAM |4 núcleos |30 por segundo |
| A5 |16 núcleos virtuais |8 núcleos, 50 GB de RAM |8 núcleos |60 por segundo |
| A6 |32 núcleos virtuais |16 núcleos, 100 GB de RAM |16 núcleos |120 por segundo |

**_Com os SKUs A, não é possível acessar o conteúdo do Power BI com uma licença do Power BI GRATUITA._**

Usar tokens inseridos com licenças PRO destina-se a teste de desenvolvimento, portanto, o número de tokens inseridos que uma conta mestra ou entidade de serviço do Power BI pode gerar é limitado. Uma capacidade dedicada requer inserção em um ambiente de produção. Não há limite para a quantidade de tokens inseridos que você pode gerar com uma capacidade dedicada. Acesse [Recursos Disponíveis](https://docs.microsoft.com/rest/api/power-bi/availablefeatures/getavailablefeatures) para verificar o valor de uso que indica o uso inserido atual, em percentual. A quantidade de uso é por conta mestre.

Para obter mais informações, consulte [Artigo sobre planejamento de capacidade de análise integrada](https://aka.ms/pbiewhitepaper).

### <a name="assign-an-app-workspace-to-a-dedicated-capacity"></a>Atribua um workspace de aplicativo a uma capacidade dedicada

Depois de criar uma capacidade dedicada, você pode atribuir o workspace do aplicativo a uma capacidade dedicada.

Para atribuir uma capacidade dedicada a um workspace usando [entidade de serviço](embed-service-principal.md), use a [API REST do Power BI](https://docs.microsoft.com/rest/api/power-bi/capacities/groups_assigntocapacity). Quando você estiver usando as APIs REST do Power BI, use a [ID de objeto de entidade de serviço](embed-service-principal.md#how-to-get-the-service-principal-object-id).

Siga as etapas abaixo para atribuir uma capacidade dedicada a um workspace usando uma **conta mestre**.

1. No **serviço do Power BI**, expanda os workspaces e selecione as reticências do workspace que você está usando para inserir seu conteúdo. Depois, selecione **Editar workspaces**.

    ![Editar Workspace](media/embed-sample-for-customers/embed-sample-for-customers-036.png)

2. Expanda **Avançado**, habilite **Capacidade dedicada** e selecione a capacidade dedicada criada por você. Depois, selecione **Salvar**.

    ![Atribuir capacidade dedicada](media/embed-sample-for-customers/embed-sample-for-customers-024.png)

3. Depois que você selecionar **Salvar**, será exibido um **losango** próximo ao nome do workspace do aplicativo.

    ![workspace do aplicativo vinculado a uma capacidade](media/embed-sample-for-customers/embed-sample-for-customers-037.png)

## <a name="next-steps"></a>Próximas etapas

Neste tutorial, você aprendeu como inserir o conteúdo do Power BI em um aplicativo para seus clientes. Você também pode tentar inserir o conteúdo do Power BI para sua organização.

> [!div class="nextstepaction"]
>[Inserir para a organização](embed-sample-for-your-organization.md)

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)
