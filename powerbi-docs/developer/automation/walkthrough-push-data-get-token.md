---
title: Obter um token de acesso de autenticação
description: Passo a passo para enviar dados por push – Obter um token de acesso de autenticação
author: KesemSharabi
ms.author: kesharab
ms.reviewer: madia
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: tutorial
ms.date: 05/29/2019
ms.openlocfilehash: 7e74b01a6b12302393a3e4bc40b2e9cccfc13d63
ms.sourcegitcommit: a175faed9378a7d040a08ced3e46e54503334c07
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79488259"
---
# <a name="step-2-get-an-authentication-access-token"></a>Etapa 2: Obter um token de acesso de autenticação

Este artigo é a segunda etapa da série [Enviar dados por push a um conjunto de dados do Power BI](walkthrough-push-data.md).

Na etapa 1, você [registrou um aplicativo cliente no Azure AD](../embedded/register-app.md). Nesta etapa, você obtém um token de acesso de autenticação. Os aplicativos do Power BI são integrados ao Azure Active Directory para fornecer ao seu aplicativo conexão e autorização seguras. Seu aplicativo usa um token para se autenticar no Azure AD e obter acesso a recursos do Power BI.

## <a name="get-an-authentication-access-token"></a>Obter um token de acesso de autenticação

Antes de começar, conclua a [etapa anterior](../embedded/register-app.md) da série [Enviar dados por push a um conjunto de dados do Power BI](walkthrough-push-data.md). 

Este procedimento exige o Visual Studio 2015 ou posterior.

1. No Visual Studio, crie um novo projeto do **Aplicativo de Console** em C#.

2. Instale a [Biblioteca de Autenticação do Azure AD para o pacote NuGet do .NET](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/2.22.302111727). O aplicativo .NET precisa deste pacote para obter um token de segurança de autenticação. 

     a. Selecione **Ferramentas** > **Gerenciador de Pacotes NuGet** > **Console do Gerenciador de Pacotes**.

     b. Insira **Install-Package Microsoft.IdentityModel.Clients.ActiveDirectory -Version 2.21.301221612**

     c. Em Program.cs, adicione `using Microsoft.IdentityModel.Clients.ActiveDirectory;`.

3. Adicione o código de exemplo listado após estas etapas em Program.cs.

4. Substitua "{ClientID}", pela **ID do cliente** você obteve no [artigo anterior da série](../embedded/register-app.md) ao registrar seu aplicativo.

5. Execute o aplicativo de console e entre em sua conta do Power BI. 

   Uma cadeia de caracteres de token deverá aparecer na janela do console.

**Exemplo de código para obter um token de segurança de autenticação**

Adicione este código a Program {...}.

* Uma variável de token para chamar operações: 
  
  ```csharp
  private static string token = string.Empty;
  
  static void Main(string[] args)
  {
  }
  ```
* Em static void Main(string[] args):
  
  ```csharp
  static void Main(string[] args)
  {
    //Get an authentication access token
    token = GetToken();
  }
  ```
* Adicione um método GetToken():

```csharp
       #region Get an authentication access token
       private static string GetToken()
       {
           // TODO: Install-Package Microsoft.IdentityModel.Clients.ActiveDirectory -Version 2.21.301221612
           // and add using Microsoft.IdentityModel.Clients.ActiveDirectory

           //The client id that Azure AD created when you registered your client app.
           string clientID = "{Client_ID}";

           //RedirectUri you used when you register your app.
           //For a client app, a redirect uri gives Azure AD more details on the application that it will authenticate.
           // You can use this redirect uri for your client app
           string redirectUri = "https://login.live.com/oauth20_desktop.srf";

           //Resource Uri for Power BI API
           string resourceUri = "https://analysis.windows.net/powerbi/api";

           //OAuth2 authority Uri
           string authorityUri = "https://login.microsoftonline.net/common/";

           //Get access token:
           // To call a Power BI REST operation, create an instance of AuthenticationContext and call AcquireToken
           // AuthenticationContext is part of the Active Directory Authentication Library NuGet package
           // To install the Active Directory Authentication Library NuGet package in Visual Studio,
           //  run "Install-Package Microsoft.IdentityModel.Clients.ActiveDirectory" from the nuget Package Manager Console.

           // AcquireToken will acquire an Azure access token
           // Call AcquireToken to get an Azure token from Azure Active Directory token issuance endpoint
           AuthenticationContext authContext = new AuthenticationContext(authorityUri);
           string token = authContext.AcquireToken(resourceUri, clientID, new Uri(redirectUri)).AccessToken;

           Console.WriteLine(token);
           Console.ReadLine();

           return token;
       }

       #endregion
```

Depois de obter um token de autenticação, você pode chamar qualquer operação do Power BI.

O próximo artigo desta série mostra como [Criar um conjunto de dados no Power BI](walkthrough-push-data-create-dataset.md).


## <a name="complete-code-listing"></a>Listagem de código completo

```csharp
using System;
using Microsoft.IdentityModel.Clients.ActiveDirectory;

namespace walkthrough_push_data
{
    class Program
    {
        private static string token = string.Empty;

        static void Main(string[] args)
        {

            //Get an authentication access token
            token = GetToken();

        }

        #region Get an authentication access token
        private static string GetToken()
        {
            // TODO: Install-Package Microsoft.IdentityModel.Clients.ActiveDirectory -Version 2.21.301221612
            // and add using Microsoft.IdentityModel.Clients.ActiveDirectory

            //The client id that Azure AD created when you registered your client app.
            string clientID = "{Client_ID}";

            //RedirectUri you used when you register your app.
            //For a client app, a redirect uri gives Azure AD more details on the application that it will authenticate.
            // You can use this redirect uri for your client app
            string redirectUri = "https://login.live.com/oauth20_desktop.srf";

            //Resource Uri for Power BI API
            string resourceUri = "https://analysis.windows.net/powerbi/api";

            //OAuth2 authority Uri
            string authorityUri = "https://login.microsoftonline.com/common/";

            //Get access token:
            // To call a Power BI REST operation, create an instance of AuthenticationContext and call AcquireToken
            // AuthenticationContext is part of the Active Directory Authentication Library NuGet package
            // To install the Active Directory Authentication Library NuGet package in Visual Studio,
            //  run "Install-Package Microsoft.IdentityModel.Clients.ActiveDirectory" from the nuget Package Manager Console.

            // AcquireToken will acquire an Azure access token
            // Call AcquireToken to get an Azure token from Azure Active Directory token issuance endpoint
            AuthenticationContext authContext = new AuthenticationContext(authorityUri);
            string token = authContext.AcquireToken(resourceUri, clientID, new Uri(redirectUri)).AccessToken;

            Console.WriteLine(token);
            Console.ReadLine();

            return token;
        }

        #endregion

    }
}
```



## <a name="next-steps"></a>Próximas etapas

* O próximo artigo desta série será [Criar um conjunto de dados no Power BI](walkthrough-push-data-create-dataset.md)
* [Visão geral da API REST do Power BI](overview-of-power-bi-rest-api.md)  
* [APIs REST do Power BI](https://docs.microsoft.com/rest/api/power-bi/)  

Mais perguntas? [Experimente a Comunidade do Power BI](https://community.powerbi.com/)