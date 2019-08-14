---
title: Análise integrada para inserir conteúdo do Power BI em seu aplicativo para sua organização
description: Saiba como integrar um relatório (Power BI ou Paginado), um dashboard ou um bloco a um aplicativo ou inseri-lo em um aplicativo usando as APIs do Power BI para análise integrada em sua organização. Saiba como integrar o Power BI ao seu aplicativo usando o software de análise integrada, ferramentas de análise integrada ou ferramentas de business intelligence integrada.
author: rkarlin
ms.author: rkarlin
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: tutorial
ms.custom: seodec18
ms.date: 07/29/2019
ms.openlocfilehash: ce13b161f0a9bf5291f2c0d127106b0db2c6fa29
ms.sourcegitcommit: 6c2c7a090b0826e3cfc3a897566e802857bbacc8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/06/2019
ms.locfileid: "68808235"
---
# <a name="tutorial-embed-power-bi-content-into-an-application-for-your-organization"></a>Tutorial: Inserir conteúdo do Power BI em um aplicativo para sua organização

No **Power BI**, você pode inserir relatórios (Power BI ou Paginados), dashboard ou blocos em um aplicativo usando usuário proprietário dos dados. O **user owns data** permite que o aplicativo estenda o serviço do Power BI para que ele possa usar análise integrada. Este tutorial demonstra como integrar um relatório (Power BI ou Paginado) a um aplicativo. Você pode usar o SDK do .NET do Power BI juntamente com a API do JavaScript do Power BI para inserir o Power BI em um aplicativo para sua organização.

![Relatório de Inserção do Power BI](media/embed-sample-for-your-organization/embed-sample-for-your-organization-035.png)

Neste tutorial, você aprenderá as seguintes tarefas:
> [!div class="checklist"]
> * Registrar um aplicativo no Azure.
> * Insira um relatório paginado ou do Power BI em um aplicativo usando o locatário do Power BI.

## <a name="prerequisites"></a>Pré-requisitos

Para começar, você precisa ter:

* Uma [conta do Power BI Pro](../service-self-service-signup-for-power-bi.md).
* Uma assinatura da [Microsoft Azure](https://azure.microsoft.com/).
* Você precisa ter seu próprio [locatário do Azure Active Directory](create-an-azure-active-directory-tenant.md) configurado.
* Para inserir relatórios paginados, você precisa pelo menos de uma capacidade A4/P1, confira [Qual o tamanho da capacidade Premium necessária para relatórios paginados?](../paginated-reports-faq.md#what-size-premium-capacity-do-i-need-for-paginated-reports).

Se não estiver inscrito no **Power BI Pro**, [inscreva-se para uma avaliação gratuita](https://powerbi.microsoft.com/pricing/) antes de começar.

Caso você não tenha uma assinatura do Azure, crie uma [conta gratuita](https://azure.microsoft.com/free/?WT.mc_id=A261C142F) antes de começar.

## <a name="set-up-your-embedded-analytics-development-environment"></a>Configurar seu ambiente de desenvolvimento de análise integrada

Antes de começar a inserir relatórios, dashboard ou blocos no seu aplicativo, você precisará verificar se o ambiente permite inserção com o Power BI.

Você pode examinar a [Ferramenta de configuração de integração](https://aka.ms/embedsetup/UserOwnsData) para que possa iniciar rapidamente e baixar um aplicativo de exemplo que ajuda a criar um ambiente e a inserir um relatório. No caso de inserir um relatório paginado, é necessário atribuir pelo menos a capacidade A4/P1 ao workspace do aplicativo criado.

Se você optar por configurar o ambiente manualmente, poderá continuar abaixo.

### <a name="register-an-application-in-azure-active-directory"></a>Registrar um aplicativo no Azure Active Directory

[Registre seu aplicativo](register-app.md) no Azure Active Directory para permitir que ele tenha acesso às [APIs REST do Power BI](https://docs.microsoft.com/rest/api/power-bi/). Registrando o aplicativo, você pode estabelecer uma identidade para ele e especificar permissões para recursos REST do Power BI.

Você precisa para continuar com o registro de um **aplicativo Web do lado do servidor**. Registre um aplicativo Web do lado do servidor para criar um segredo do aplicativo.

## <a name="set-up-your-power-bi-environment"></a>Configurar seu ambiente do Power BI

### <a name="create-an-app-workspace"></a>Criar um workspace de aplicativo

Se você estiver inserindo relatórios, painéis ou blocos para seus clientes, precisará colocar o conteúdo dentro de um espaço de trabalho do aplicativo. Há diferentes tipos de workspaces que você pode configurar: o [workspaces tradicionais](../service-create-workspaces.md) ou o [novos workspaces](../service-create-the-new-workspaces.md).

### <a name="create-and-publish-your-power-bi-reports"></a>Criar e publicar os relatórios do Power BI

Você pode criar seus relatórios e conjuntos de dados usando o Power BI Desktop. Em seguida, você pode publicar esses relatórios em um workspace do aplicativo. O usuário final que publicar os relatórios precisa ter uma licença do Power BI Pro para publicar em um workspace do aplicativo.

1. Baixe a [demonstração](https://github.com/Microsoft/powerbi-desktop-samples) de exemplo do GitHub.

    ![Baixar a demo](media/embed-sample-for-your-organization/embed-sample-for-your-organization-026-1.png)

2. Abra o relatório de exemplo .pbix no Power BI Desktop.

   ![Relatório de exemplo do Power BI Desktop](media/embed-sample-for-your-organization/embed-sample-for-your-organization-027.png)

3. Publique no workspace do aplicativo.

   ![Publicar um relatório do Power BI Desktop](media/embed-sample-for-your-organization/embed-sample-for-your-organization-028.png)

    Agora, você pode exibir o relatório no serviço do Power BI online.

   ![Exibir um relatório do Power BI Desktop](media/embed-sample-for-your-organization/embed-sample-for-your-organization-029.png)
   
### <a name="create-and-publish-your-paginated-reports"></a>Criar e publicar relatórios paginados

É possível criar relatórios paginados usando o [Construtor de Relatórios do Power BI](../paginated-reports-report-builder-power-bi.md#create-reports-in-power-bi-report-builder). Será possível [carregar o relatório](../paginated-reports-quickstart-aw.md#upload-the-report-to-the-service) para um workspace do aplicativo atribuído a uma capacidade pelo menos A4/P1. O usuário final que carrega o relatório precisa ter uma licença do Power BI Pro para publicar em um workspace do aplicativo.
   
## <a name="embed-your-content-by-using-the-sample-application"></a>Insira o conteúdo usando o aplicativo de exemplo

Este exemplo é deliberadamente mantido simples para fins de demonstração.

Siga as etapas abaixo para começar a inserir seu conteúdo usando o aplicativo de exemplo.

1. Baixe o [Visual Studio](https://www.visualstudio.com/) (versão 2013 ou posterior). Baixe a versão mais recente do [pacote do NuGet](https://www.nuget.org/profiles/powerbi).

2. Baixe o [exemplo User Owns Data](https://github.com/Microsoft/PowerBI-Developer-Samples) do GitHub para começar.

    ![Amostra do aplicativo User Owns Data](media/embed-sample-for-your-organization/embed-sample-for-your-organization-026.png)

3. Abra o arquivo **Cloud.config** no aplicativo de exemplo.

    Há campos que você precisa preencher para executar o aplicativo.

    | Campo |
    |--------------------|
    | **[ID do Aplicativo](#application-id)** |
    | **[Segredo do aplicativo](#application-secret)** |
    | **[ID do workspace](#workspace-id)** |
    | **[ID do Relatório](#report-id)** |
    | **[AADAuthorityUrl](#aadauthorityurl)** |

    ![Cloud.config file](media/embed-sample-for-your-organization/embed-sample-for-your-organization-030.png)

### <a name="application-id"></a>ID do aplicativo

Preencha as informações de **applicationId** com a **ID do Aplicativo** do **Azure**. A **applicationId** é usada pelo aplicativo para identificar-se aos usuários para os quais você está solicitando permissões.

Para obter a **applicationId**, siga estas etapas:

1. Entre no [Portal do Azure](https://portal.azure.com).

2. No painel de navegação esquerdo, escolha **Todos os serviços** e selecione **Registros de aplicativo**.

3. Selecione o aplicativo que precisa usar a **applicationId**.

    ![Escolhendo o aplicativo](media/embed-sample-for-your-organization/embed-sample-for-your-organization-042.png)

4. Há uma **ID do Aplicativo** listada como GUID. Use essa **ID do aplicativo** como a **applicationId** do aplicativo.

    ![applicationId](media/embed-sample-for-your-organization/embed-sample-for-your-organization-043.png)

### <a name="workspace-id"></a>ID do workspace

Preencha as informações de **workspaceId** com o GUID do workspace (grupo) do aplicativo do Power BI. Você pode obter essas informações da URL quando conectado ao serviço do Power BI ou usando o Powershell.

URL <br>

![workspaceId](media/embed-sample-for-your-organization/embed-sample-for-your-organization-040.png)

PowerShell <br>

```powershell
Get-PowerBIworkspace -name "User Owns Embed Test"
```

   ![workspaceId do powershell](media/embed-sample-for-your-organization/embed-sample-for-your-organization-040-ps.png)

### <a name="report-id"></a>ID do Relatório

Preencha as informações de **reportId** com o GUID de relatório do Power BI. Você pode obter essas informações da URL quando conectado ao serviço do Power BI ou usando o Powershell.

URL do relatório do Power BI <br>

![reportId do PBI](media/embed-sample-for-your-organization/embed-sample-for-your-organization-041.png)

URL do relatório paginado <br>



URL do relatório paginado<br>

![reportId paginado](media/embed-sample-for-your-organization/paginated-reports-url.png)

PowerShell <br>

```powershell
Get-PowerBIworkspace -name "User Owns Embed Test" | Get-PowerBIReport
```

![reportId do powershell](media/embed-sample-for-your-organization/embed-sample-for-your-organization-041-ps.png)

### <a name="aadauthorityurl"></a>AADAuthorityUrl

Preencha a informação **AADAuthorityUrl** com a URL que permite a você inserir no locatário organizacional ou inserir com um usuário convidado.

Para inserir com seu locatário organizacional, use a URL: *https://login.microsoftonline.com/common/oauth2/authorize* .

Para inserir com um convidado, use a URL *https://login.microsoftonline.com/report-owner-tenant-id* , em que você adiciona a ID de locatário do proprietário do relatório substituindo *relatório-proprietário-locatário-id*.

### <a name="run-the-application"></a>Execute o aplicativo

1. Selecione **Executar** no **Visual Studio**.

    ![Execute o aplicativo](media/embed-sample-for-your-organization/embed-sample-for-your-organization-033.png)

2. Selecione **Inserir Relatório**. Dependendo do conteúdo que você optar por testar – relatórios, painéis ou blocos –, selecione essa opção no aplicativo.

    ![Selecionar conteúdo](media/embed-sample-for-your-organization/embed-sample-for-your-organization-034.png)

3. Agora, você pode exibir o relatório no aplicativo de exemplo.

    ![Exibir o relatório no aplicativo](media/embed-sample-for-your-organization/embed-sample-for-your-organization-035.png)

## <a name="embed-your-content-within-your-application"></a>Insira o conteúdo dentro de seu aplicativo

Embora as etapas para inserir seu conteúdo possam ser feitas com as [APIs REST do Power BI](https://docs.microsoft.com/rest/api/power-bi/), os códigos de exemplo descritos neste artigo são feitos com o SDK do .NET.

Para integrar um relatório a um aplicativo Web, você pode usar a API REST do Power BI ou o SDK do C# do Power BI. Você também pode usar um token de acesso de autorização do Azure Active Directory para obter um relatório. Em seguida, carregue o relatório usando o mesmo token de acesso. A API REST do Power BI fornece acesso programático a recursos específicos do Power BI. Para obter mais informações, confira [Visão geral das APIs REST do Power BI](https://docs.microsoft.com/rest/api/power-bi/) e a [API JavaScript do Power BI](https://github.com/Microsoft/PowerBI-JavaScript).

### <a name="get-an-access-token-from-azure-ad"></a>Obter um token de acesso do Azure AD

No aplicativo, primeiro você deve obter um token de acesso do Azure AD para que seja possível fazer chamadas à API REST do Power BI. Para obter mais informações, consulte [Autenticar usuários e obter um token de acesso do Azure AD para o aplicativo do Power BI](get-azuread-access-token.md).

### <a name="get-a-report"></a>Obter um relatório

Para obter um relatório paginado ou do Power BI, use a operação [Obter Relatórios](https://docs.microsoft.com/rest/api/power-bi/reports/getreports) que obtém uma lista de relatórios paginados e do Power BI. Na lista de relatórios, obtenha uma ID de relatório.

### <a name="get-reports-by-using-an-access-token"></a>Obter relatórios usando um token de acesso

A operação [Obter Relatórios](https://docs.microsoft.com/rest/api/power-bi/reports/getreports) retorna uma lista de relatórios. É possível obter um relatório individual na lista de relatórios.

Para fazer a chamada à API REST, você deve incluir um cabeçalho *Autorização* no formato *Portador {token de acesso}* .

#### <a name="get-reports-with-the-rest-api"></a>Obter relatórios com a API REST

O exemplo de código a seguir mostra como recuperar relatórios com a API REST:

> [!Note]
> Há um exemplo de como obter um item de conteúdo que você deseja inserir disponível no arquivo Default.aspx.cs no [aplicativo de exemplo](https://github.com/Microsoft/PowerBI-Developer-Samples). Exemplos são relatório, dashboard ou bloco.

```csharp
using Newtonsoft.Json;

//Get a Report. In this sample, you get the first Report.
protected void GetReport(int index)
{
    //Configure Reports request
    System.Net.WebRequest request = System.Net.WebRequest.Create(
        String.Format("{0}/Reports",
        baseUri)) as System.Net.HttpWebRequest;

    request.Method = "GET";
    request.ContentLength = 0;
    request.Headers.Add("Authorization", String.Format("Bearer {0}", accessToken.Value));

    //Get Reports response from request.GetResponse()
    using (var response = request.GetResponse() as System.Net.HttpWebResponse)
    {
        //Get reader from response stream
        using (var reader = new System.IO.StreamReader(response.GetResponseStream()))
        {
            //Deserialize JSON string
            PBIReports Reports = JsonConvert.DeserializeObject<PBIReports>(reader.ReadToEnd());

            //Sample assumes at least one Report.
            //You could write an app that lists all Reports
            if (Reports.value.Length > 0)
            {
                var report = Reports.value[index];

                txtEmbedUrl.Text = report.embedUrl;
                txtReportId.Text = report.id;
                txtReportName.Text = report.name;
            }
        }
    }
}

//Power BI Reports used to deserialize the Get Reports response.
public class PBIReports
{
    public PBIReport[] value { get; set; }
}
public class PBIReport
{
    public string id { get; set; }
    public string reportType { get; set }
    public string name { get; set; }
    public string webUrl { get; set; }
    public string embedUrl { get; set; }
}
```

#### <a name="get-reports-by-using-the-net-sdk"></a>Obter relatórios usando o SDK do .NET

Use o SDK do .NET para recuperar uma lista de relatórios, em vez de chamar a API REST diretamente. O exemplo de código a seguir mostra como listar os relatórios:

```csharp
using Microsoft.IdentityModel.Clients.ActiveDirectory;
using Microsoft.PowerBI.Api.V2;
using Microsoft.PowerBI.Api.V2.Models;

var tokenCredentials = new TokenCredentials(<ACCESS TOKEN>, "Bearer");

// Create a Power BI Client object. It is used to call Power BI APIs.
using (var client = new PowerBIClient(new Uri(ApiUrl), tokenCredentials))
{
    // Get the first report all reports in that workspace
    ODataResponseListReport reports = client.Reports.GetReports();

    Report report = reports.Value.FirstOrDefault();

    var embedUrl = report.EmbedUrl;
}
```

### <a name="load-a-report-by-using-javascript"></a>Carregar um relatório usando JavaScript

Use o JavaScript para carregar um relatório em um elemento div na página da Web. O exemplo de código a seguir mostra como recuperar um relatório de um determinado workspace:

> [!NOTE]  
> Um exemplo de carregamento de um item de conteúdo que você deseja inserir está disponível no arquivo **default.aspx** no [aplicativo de exemplo](https://github.com/Microsoft/PowerBI-Developer-Samples).

```javascript
<!-- Embed Report-->
<div> 
    <asp:Panel ID="PanelEmbed" runat="server" Visible="true">
        <div>
            <div><b class="step">Step 3</b>: Embed a report</div>

            <div>Enter an embed url for a report from Step 2 (starts with https://):</div>
            <input type="text" id="tb_EmbedURL" style="width: 1024px;" />
            <br />
            <input type="button" id="bEmbedReportAction" value="Embed Report" />
        </div>

        <div id="reportContainer"></div>
    </asp:Panel>
</div>
```

#### <a name="sitemaster"></a>Site.master

```javascript
window.onload = function () {
    // client side click to embed a selected report.
    var el = document.getElementById("bEmbedReportAction");
    if (el.addEventListener) {
        el.addEventListener("click", updateEmbedReport, false);
    } else {
        el.attachEvent('onclick', updateEmbedReport);
    }

    // handle server side post backs, optimize for reload scenarios
    // show embedded report if all fields were filled in.
    var accessTokenElement = document.getElementById('MainContent_accessTokenTextbox');
    if (accessTokenElement !== null) {
        var accessToken = accessTokenElement.value;
        if (accessToken !== "")
            updateEmbedReport();
    }
};

// update embed report
function updateEmbedReport() {

    // check if the embed url was selected
    var embedUrl = document.getElementById('tb_EmbedURL').value;
    if (embedUrl === "")
        return;

    // get the access token.
    accessToken = document.getElementById('MainContent_accessTokenTextbox').value;

    // Embed configuration used to describe the what and how to embed.
    // This object is used when calling powerbi.embed.
    // You can find more information at https://github.com/Microsoft/PowerBI-JavaScript/wiki/Embed-Configuration-Details.
    var config = {
        type: 'report',
        accessToken: accessToken,
        embedUrl: embedUrl
    };

    // Grab the reference to the div HTML element that will host the report.
    var reportContainer = document.getElementById('reportContainer');

    // Embed the report and display it within the div container.
    var report = powerbi.embed(reportContainer, config);

    // report.on will add an event handler which prints to Log window.
    report.on("error", function (event) {
        var logView = document.getElementById('logView');
        logView.innerHTML = logView.innerHTML + "Error<br/>";
        logView.innerHTML = logView.innerHTML + JSON.stringify(event.detail, null, "  ") + "<br/>";
        logView.innerHTML = logView.innerHTML + "---------<br/>";
    }
  );
}
```

## <a name="using-a-power-bi-premium-dedicated-capacity"></a>Usando uma capacidade dedicada do Power BI Premium

Agora que você terminou o desenvolvimento do seu aplicativo, é hora de conferir uma capacidade dedicada para o workspace do seu aplicativo.

### <a name="create-a-dedicated-capacity"></a>Criar uma capacidade dedicada

Ao criar uma capacidade dedicada, você pode usufruir de um recurso dedicado ao conteúdo no workspace do aplicativo. Para relatórios paginados, você deve fazer backup do workspace de aplicativo com a capacidade de pelo menos A4/P1. É possível criar uma capacidade dedicada usando o [Power BI Premium.](../service-premium-what-is.md)

A tabela a seguir lista os SKUs do Power BI Premium disponíveis no [Microsoft Office 365](../service-admin-premium-purchase.md):

| Nó de capacidade | Total de vCores<br/>(back-end + front-end) | vCores de back-end | vCores de front-end | Limites de conexão dinâmica/DirectQuery |
| --- | --- | --- | --- | --- | --- |
| EM1 |1 vCore |0,5 vCore, 10 GB de RAM |0,5 vCore |3,75 por segundo |
| EM2 |2 vCores |1 vCore, 10 GB de RAM |1 vCores |7,5 por segundo |
| EM3 |4 vCores |2 vCores, 10 GB de RAM |2 vCores |15 por segundo |
| P1 |8 vCores |4 vCores, 25 GB de RAM |4 vCores |30 por segundo |
| P2 |16 vCores |8 vCores, 50 GB de RAM |8 vCores |60 por segundo |
| P3 |32 vCores |16 vCores, 100 GB de RAM |16 vCores |120 por segundo |
| P4 |64 vCores |32 vCores, 200 GB de RAM |32 vCores |240 por segundo |
| P5 |128 vCores |64 vCores, 400 GB de RAM |64 vCores |480 por segundo |

> [!NOTE]
> - Quando você está tentando inserir com aplicativos do Microsoft Office, pode usar SKUs de EM para acessar o conteúdo com uma licença gratuita do Power BI. Mas você não pode acessar o conteúdo com uma licença gratuita do Power BI quando você estiver usando o Powerbi.com ou o Power BI Mobile.
> - Quando você está tentando inserir com aplicativos do Microsoft Office usando o Powerbi.com ou o Power BI Mobile, pode acessar o conteúdo com uma licença gratuita do Power BI.

### <a name="assign-an-app-workspace-to-a-dedicated-capacity"></a>Atribua um workspace de aplicativo a uma capacidade dedicada

Depois de criar uma capacidade dedicada, você pode atribuir o workspace do aplicativo a uma capacidade dedicada. Para concluir este processo, siga estas etapas:

1. No serviço do Power BI, expanda os workspaces e selecione as reticências do workspace que você está usando para inserir seu conteúdo. Depois, selecione **Editar workspaces**.

    ![Editar um workspace](media/embed-sample-for-your-organization/embed-sample-for-your-organization-036.png)

2. Expanda **Avançado** e habilite **Capacidade dedicada**. Selecione a capacidade dedicada que você criou. Depois, selecione **Salvar**.

    ![Atribuir uma capacidade dedicada](media/embed-sample-for-your-organization/embed-sample-for-your-organization-024.png)

3. Depois de selecionar **Salvar**, você verá um losango ao lado do nome do workspace do aplicativo.

    ![Workspace do aplicativo vinculado a uma capacidade](media/embed-sample-for-your-organization/embed-sample-for-your-organization-037.png)

## <a name="admin-settings"></a>Configurações de administração

Administradores globais ou administradores do serviço do Power BI podem ativar ou desativar a capacidade de usar as APIs REST para um locatário. Administradores do Power BI podem definir essa configuração para toda a organização ou para grupos de segurança individuais. Isso é habilitado para toda a organização por padrão. Você pode fazer estas alterações no [portal de administração do Power BI](../service-admin-portal.md).

## <a name="next-steps"></a>Próximas etapas

Neste tutorial, você aprendeu a inserir conteúdo do Power BI em um aplicativo usando a conta da organização do Power BI. Agora, você pode tentar inserir o conteúdo do Power BI em um aplicativo usando aplicativos. Também é possível tentar inserir conteúdo do Power BI para seus clientes (não compatível ainda para inserir relatórios paginados):

> [!div class="nextstepaction"]
> [Inserir de aplicativos](embed-from-apps.md)

> [!div class="nextstepaction"]
>[Inserir para seus clientes](embed-sample-for-customers.md)

Se você tiver outras dúvidas, [experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/).
