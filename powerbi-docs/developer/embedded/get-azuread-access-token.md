---
title: Autenticar usuários e obter um token de acesso do Azure AD para o aplicativo
description: Saiba como registrar um aplicativo no Azure Active Directory para uso com a inserção de conteúdo do Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 06/04/2019
ms.openlocfilehash: cac59a4689eecd75c53ca1c62d7b097438b2ae53
ms.sourcegitcommit: 2c798b97fdb02b4bf4e74cf05442a4b01dc5cbab
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80114510"
---
# <a name="get-an-azure-ad-access-token-for-your-power-bi-application"></a>Obter um token de acesso do Azure AD para seu aplicativo do Power BI

Esse artigo mostra como você pode autenticar usuários no aplicativo do Power BI e recuperar um token de acesso para usar com a [API REST do Power BI](https://docs.microsoft.com/rest/api/power-bi/).

Antes do seu aplicativo chamar a API REST, você precisará obter um **token de acesso de autenticação** do Azure AD (Azure Active Directory). Seu aplicativo usa um token para obter acesso aos dashboards, aos blocos e ao relatório do Power BI. Para obter mais informações, confira [Autorizar acesso a aplicativos Web do Azure Active Directory usando o código de fluxo de concessão do OAuth 2.0](https://docs.microsoft.com/azure/active-directory/develop/v1-protocols-oauth-code).

Dependendo de como você insere o conteúdo, o token de acesso é recuperado de maneira diferente. Este artigo mostra duas abordagens diferentes.

## <a name="access-token-for-power-bi-users-user-owns-data"></a>Token de acesso para usuários do Power BI (o usuário possui dados)

Este exemplo refere-se a quando os usuários se conectam manualmente no Azure AD com a conexão da organização. Essa tarefa é usada ao inserir conteúdo para usuários que têm acesso ao serviço do Power BI.

### <a name="get-an-azure-ad-authorization-code"></a>Obter um código de autorização do Azure AD

A primeira etapa para obter um **token de acesso** é obter um código de autorização do **Azure AD**. Crie uma cadeia de caracteres de consulta com as propriedades a seguir e a redireciona para o **Azure AD**.

#### <a name="authorization-code-query-string"></a>Cadeia de caracteres de consulta do código de autorização

```csharp
var @params = new NameValueCollection
{
    //Azure AD will return an authorization code. 
    //See the Redirect class to see how "code" is used to AcquireTokenByAuthorizationCode
    {"response_type", "code"},

    //Client ID is used by the application to identify themselves to the users that they are requesting permissions from.
    //You get the client id when you register your Azure app.
    {"client_id", Properties.Settings.Default.ClientID},

    //Resource uri to the Power BI resource to be authorized
    // https://analysis.windows.net/powerbi/api
    {"resource", Properties.Settings.Default.PowerBiAPI},

    //After user authenticates, Azure AD will redirect back to the web app
    {"redirect_uri", "https://localhost:13526/Redirect"}
};
```

Depois de construir uma cadeia de caracteres de consulta, você a redireciona para o **Azure AD** para obter um **código de autorização**.  Veja abaixo um método em C# completo para construir uma cadeia de caracteres de consulta do **código de autorização** e redirecioná-la para o **Azure AD**. Então, você usa o **código de autorização** para obter um **token de acesso**.

Em redirect.aspx.cs, [AuthenticationContext.AcquireTokenByAuthorizationCode](https://docs.microsoft.com/dotnet/api/microsoft.identitymodel.clients.activedirectory.authenticationcontext.acquiretokenbyauthorizationcodeasync?view=azure-dotnet#Microsoft_IdentityModel_Clients_ActiveDirectory_AuthenticationContext_AcquireTokenByAuthorizationCodeAsync_System_String_System_Uri_Microsoft_IdentityModel_Clients_ActiveDirectory_ClientCredential_System_String_) requer a geração do token.

#### <a name="get-authorization-code"></a>Obter o código de autorização

```csharp
protected void signInButton_Click(object sender, EventArgs e)
{
    //Create a query string
    //Create a sign-in NameValueCollection for query string
    var @params = new NameValueCollection
    {
        //Azure AD will return an authorization code. 
        //See the Redirect class to see how "code" is used to AcquireTokenByAuthorizationCode
        {"response_type", "code"},

        //Client ID is used by the application to identify themselves to the users that they are requesting permissions from. 
        //You get the client id when you register your Azure app.
        {"client_id", Properties.Settings.Default.ClientID},

        //Resource uri to the Power BI resource to be authorized
        // https://analysis.windows.net/powerbi/api
        {"resource", Properties.Settings.Default.PowerBiAPI},

        //After user authenticates, Azure AD will redirect back to the web app
        {"redirect_uri", "https://localhost:13526/Redirect"}
    };

    //Create sign-in query string
    var queryString = HttpUtility.ParseQueryString(string.Empty);
    queryString.Add(@params);

    //Redirect authority
    //Authority Uri is an Azure resource that takes a client id to get an Access token
    // AADAuthorityUri = https://login.microsoftonline.com/common/
    string authorityUri = Properties.Settings.Default.AADAuthorityUri;
    var authUri = String.Format("{0}?{1}", authorityUri, queryString);
    Response.Redirect(authUri);
}
```

### <a name="get-an-access-token-from-authorization-code"></a>Obter um token de acesso do código de autorização

Depois que o **Azure AD** redirecionar de volta para seu aplicativo Web com um **código de autorização**, você poderá usá-lo para obter um token de acesso. Veja abaixo um exemplo do C# que pode ser usada na página de redirecionamento e no evento `Page_Load` do default.aspx.

Você pode recuperar o namespace **Microsoft.IdentityModel.Clients.ActiveDirectory** no pacote NuGet da [Biblioteca de Autenticação do Active Directory](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/).

```powershell
Install-Package Microsoft.IdentityModel.Clients.ActiveDirectory
```

#### <a name="redirectaspxcs"></a>Redirect.aspx.cs

```csharp
using Microsoft.IdentityModel.Clients.ActiveDirectory;

protected void Page_Load(object sender, EventArgs e)
{
    //Redirect uri must match the redirect_uri used when requesting Authorization code.
    string redirectUri = String.Format("{0}Redirect", Properties.Settings.Default.RedirectUrl);
    string authorityUri = Properties.Settings.Default.AADAuthorityUri;

    // Get the auth code
    string code = Request.Params.GetValues(0)[0];

    // Get auth token from auth code
    TokenCache TC = new TokenCache();

    AuthenticationContext AC = new AuthenticationContext(authorityUri, TC);
    ClientCredential cc = new ClientCredential
        (Properties.Settings.Default.ClientID,
        Properties.Settings.Default.ClientSecret);

    AuthenticationResult AR = AC.AcquireTokenByAuthorizationCode(code, new Uri(redirectUri), cc);

    //Set Session "authResult" index string to the AuthenticationResult
    Session[_Default.authResultString] = AR;

    //Redirect back to Default.aspx
    Response.Redirect("/Default.aspx");
}
```

#### <a name="defaultaspx"></a>Default.aspx

```csharp
using Microsoft.IdentityModel.Clients.ActiveDirectory;

protected void Page_Load(object sender, EventArgs e)
{

    //Test for AuthenticationResult
    if (Session[authResultString] != null)
    {
        //Get the authentication result from the session
        authResult = (AuthenticationResult)Session[authResultString];

        //Show Power BI Panel
        signInStatus.Visible = true;
        signInButton.Visible = false;

        //Set user and token from authentication result
        userLabel.Text = authResult.UserInfo.DisplayableId;
        accessTokenTextbox.Text = authResult.AccessToken;
    }
}
```

## <a name="access-token-for-non-power-bi-users-app-owns-data"></a>Token de acesso para usuários que não têm o Power BI (o aplicativo possui dados)

Normalmente, essa abordagem é usada para aplicativos do tipo ISV (fornecedor de software independente) em que o aplicativo tem acesso aos dados. Os usuários não necessariamente são usuários do Power BI e o aplicativo controla a autenticação e o acesso dos usuários.

### <a name="access-token-with-a-master-account"></a>Token de acesso com uma conta mestra

Para essa abordagem, você usa uma única conta *mestra*, que é um usuário do Power BI Pro. As credenciais da conta são armazenadas com o aplicativo. O aplicativo autentica-se no Azure AD com essas credenciais armazenadas. O código de exemplo mostrado abaixo foi obtido da [amostra O aplicativo possui dados](https://github.com/guyinacube/PowerBI-Developer-Samples)

### <a name="access-token-with-service-principal"></a>Token de acesso com a entidade de serviço

Para essa abordagem, você deve usar uma [entidade de serviço](embed-service-principal.md), que é um token **somente de aplicativo**. O aplicativo autentica-se com relação ao Azure AD com a entidade de serviço. O código de exemplo mostrado abaixo foi obtido da [amostra O aplicativo possui dados](https://github.com/guyinacube/PowerBI-Developer-Samples)

#### <a name="embedservicecs"></a>EmbedService.cs

```csharp
var authenticationContext = new AuthenticationContext(AuthorityUrl);
       AuthenticationResult authenticationResult = null;
       if (AuthenticationType.Equals("MasterUser"))
       {
              // Authentication using master user credentials
              var credential = new UserPasswordCredential(Username, Password);
              authenticationResult = authenticationContext.AcquireTokenAsync(ResourceUrl, ApplicationId, credential).Result;
       }
       else
       {
             // Authentication using app credentials
             var credential = new ClientCredential(ApplicationId, ApplicationSecret);
             authenticationResult = await authenticationContext.AcquireTokenAsync(ResourceUrl, credential);
       }


m_tokenCredentials = new TokenCredentials(authenticationResult.AccessToken, "Bearer");
```

## <a name="troubleshoot"></a>Solucionar problemas

Mensagem de erro "'AuthenticationContext' não contém uma definição para 'AcquireToken' e nenhum 'AcquireToken' acessível aceitando um primeiro argumento do tipo 'AuthenticationContext' pôde ser encontrado (está faltando uma referência de assembly ou uma diretiva de uso?)".

   Tente baixar [Microsoft.IdentityModel.Clients.ActiveDirectory](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/2.22.302111727) se você vir esse erro.

## <a name="next-steps"></a>Próximas etapas

Agora que você tem o token de acesso, chame a API REST do Power BI para inserir o conteúdo. Para obter informações, confira [Como inserir conteúdo do Power BI](embed-sample-for-customers.md#embed-content-within-your-application).

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
