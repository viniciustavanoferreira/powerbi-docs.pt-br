---
title: Configurar credenciais de forma programática para o Power BI
description: Como configurar as credenciais de modo programático durante a automação do Power BI
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 02/23/2020
ms.openlocfilehash: bd7758be32d18fd3be06a7847edc7795c2b5f9e1
ms.sourcegitcommit: 2c798b97fdb02b4bf4e74cf05442a4b01dc5cbab
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80114763"
---
# <a name="configure-credentials-programmatically-for-power-bi"></a>Configurar credenciais de forma programática para o Power BI

Siga estas etapas para configurar as credenciais programaticamente para o Power BI.

## <a name="update-credentials-flow-for-data-sources"></a>Atualizar fluxo de credenciais para fontes de dados

1. Chame [Obter Fontes de Dados](https://docs.microsoft.com/rest/api/power-bi/datasets/getdatasourcesingroup) para descobrir as fontes de dados do conjunto de dados. No corpo da resposta para cada fonte de dados, há o tipo, os detalhes de conexão, gateway e ID da fonte de dados.

    ```csharp
    // Select a datasource
    var datasources = pbiClient.Datasets.GetDatasources(datasetId).Value;
    var datasource = datasources.First();
    ```

2. Compile cadeia de caracteres de credenciais de acordo com os [Exemplos de Fonte de Dados de Atualização](https://docs.microsoft.com/rest/api/power-bi/gateways/updatedatasource) dependendo do tipo de credenciais.

    # <a name="net-sdk-v3"></a>[SDK v3 do .NET](#tab/sdk3)

    ```csharp
    var credentials =  new BasicCredentials(username: "username", password :"*****");
    ```

    # <a name="net-sdk-v2"></a>[SDK do .NET v2](#tab/sdk2)

     ```csharp
    var credentials = "{\"credentialData\":[{\"name\":\"username\", \"value\":\"john\"},{\"name\":\"password\", \"value\":\"*****\"}]}";
    ```

    ---

2. Chame [Obter Gateway](https://docs.microsoft.com/rest/api/power-bi/gateways/getgateways) para recuperar a chave pública do gateway.

    ```csharp
    var gateway = pbiClient.Gateways.GetGatewayById(datasource.GatewayId);
    ```

3. Criptografe as credenciais.

    # <a name="net-sdk-v3"></a>[SDK v3 do .NET](#tab/sdk3)

    ```csharp
    var credentialsEncryptor = new AsymmetricKeyEncryptor(gateway.publicKey);
    ```

    # <a name="net-sdk-v2"></a>[SDK do .NET v2](#tab/sdk2)

    Criptografe a cadeia de caracteres de credenciais com a chave pública do gateway da etapa 2. Diferentes versões do gateway podem ter diferentes tamanhos de chave pública. Confira os seguintes exemplos no código do SDK, disponíveis no [repositório do GitHub PowerBI-CSharp](https://github.com/microsoft/PowerBI-CSharp/tree/master/sdk/PowerBI.Api/Extensions):
    * [AsymmetricKeyEncryptor.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/AsymmetricKeyEncryptor.cs)
    * [Asymmetric1024KeyEncryptionHelper.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/Asymmetric1024KeyEncryptionHelper.cs)
    * [AsymmetricHigherKeyEncryptionHelper.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/AsymmetricHigherKeyEncryptionHelper.cs)
    * [AuthenticatedEncryption.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/AuthenticatedEncryption.cs) 

    ---  

4. Compile detalhes de credenciais com credenciais criptografadas.

    # <a name="net-sdk-v3"></a>[SDK v3 do .NET](#tab/sdk3)

    Use a classe AssymetricKeyEncriptor com a chave pública recuperada na **Etapa 3**.

    ```csharp
    var credentialDetails = new CredentialDetails(
            credentials,
            PrivacyLevel.Private,
            EncryptedConnection.Encrypted,
            credentialsEncryptor);
    ```


    # <a name="net-sdk-v2"></a>[SDK do .NET v2](#tab/sdk2)

    ```csharp
    var credentialDetails = new CredentialDetails(
            credentials,
            CredentialTypeEnum.Basic,
            EncryptedConnectionEnum.Encrypted,
            EncryptionAlgorithmEnum.None,
            PrivacyLevelEnum.Private);
    ```

    ---

5. Chame [Atualizar Fonte de Dados](https://docs.microsoft.com/rest/api/power-bi/gateways/updatedatasource) para definir credenciais.

    ```csharp
    pbiClient.Gateways.UpdateDatasource(gatewayId, datasourceId, credentialDetails);
    ```

## <a name="configure-a-new-data-source-for-a-data-gateway"></a>Configurar uma nova fonte de dados para um gateway de dados

1. Instale o [Gateway de dados local](https://powerbi.microsoft.com/gateway/) no seu computador.

2. Chame [Obter Gateways](https://docs.microsoft.com/rest/api/power-bi/gateways/getgateways) para recuperar a ID de gateway e a chave pública.

    ```csharp
    // Select a gateway
    var gateways = pbiClient.Gateways.GetGateways().Value;
    var gateway = gateways.First();
    ```

3. Compile detalhes de credenciais do modo como foi descrito na [Atualizar fluxo de credenciais para fontes de dados](#update-credentials-flow-for-data-sources), usando a chave pública de gateway recuperada na **Etapa 2**.

4. Crie o corpo da solicitação.

    ```csharp
    var request = new PublishDatasourceToGatewayRequest(
            dataSourceType: "SQL",
            connectionDetails: "{\"server\":\"myServer\",\"database\":\"myDatabase\"}",
            credentialDetails: credentialDetails,
            dataSourceName: "my sql datasource");
    ```

5. Chame a API [Criar Fonte de Dados](https://docs.microsoft.com/rest/api/power-bi/gateways/createdatasource).

    ```csharp
    pbiClient.Gateways.CreateDatasource(gateway.Id, request);
    ```

## <a name="credential-types"></a>Tipos de credenciais

Quando você chama [Criar Fonte de Dados](https://docs.microsoft.com/rest/api/power-bi/gateways/createdatasource) ou [Atualizar Fonte de Dados](https://docs.microsoft.com/rest/api/power-bi/gateways/updatedatasource) em um **gateway local corporativo** usando a [API Rest do Power BI](https://docs.microsoft.com/rest/api/power-bi/), o valor de credenciais deve ser criptografado usando a chave pública do gateway.

>[!NOTE]
>.NET SDK v3 também pode veicular os exemplos de .NET SDK v2 listados abaixo.

### <a name="windows-and-basic-credentials"></a>Windows e credenciais básicas

# <a name="net-sdk-v3"></a>[SDK v3 do .NET](#tab/sdk3)

```csharp
// Windows credentials
var credentials = new WindowsCredentials(username: "john", password: "*****");

// Or

// Basic credentials
var credentials = new BasicCredentials(username: "john", password: "*****");

var credentialsEncryptor = new AsymmetricKeyEncryptor(publicKey);
var credentialDetails = new CredentialDetails(credentials, PrivacyLevel.Private, EncryptedConnection.Encrypted, credentialsEncryptor);
```

# <a name="net-sdk-v2"></a>[SDK do .NET v2](#tab/sdk2)

```csharp
var credentials = "{\"credentialData\":[{\"name\":\"username\", \"value\":\"john\"},{\"name\":\"password\", \"value\":\"*****\"}]}";
```

---

### <a name="key-credentials"></a>Credenciais de chave

# <a name="net-sdk-v3"></a>[SDK v3 do .NET](#tab/sdk3)

```csharp
var credentials = new KeyCredentials("TestKey");
var credentialsEncryptor = new AsymmetricKeyEncryptor(publicKey);
var credentialDetails = new CredentialDetails(credentials, PrivacyLevel.Private, EncryptedConnection.Encrypted, credentialsEncryptor);
```

# <a name="net-sdk-v2"></a>[SDK do .NET v2](#tab/sdk2)

```csharp
var credentials = "{\"credentialData\":[{\"name\":\"key\", \"value\":\"ec....LA=\"}]}";
```

---

**Credenciais do OAuth2**

# <a name="net-sdk-v3"></a>[SDK v3 do .NET](#tab/sdk3)

```csharp
var credentials = new OAuth2Credentials("TestToken");
var credentialsEncryptor = new AsymmetricKeyEncryptor(publicKey);
var credentialDetails = new CredentialDetails(credentials, PrivacyLevel.Private, EncryptedConnection.Encrypted, credentialsEncryptor);
```

# <a name="net-sdk-v2"></a>[SDK do .NET v2](#tab/sdk2)

```csharp
var credentials = "{\"credentialData\":[{\"name\":\"accessToken\", \"value\":\"eyJ0....fwtQ\"}]}";
```

---

**Credenciais anônimas**

# <a name="net-sdk-v3"></a>[SDK v3 do .NET](#tab/sdk3)

```csharp
var credentials = new AnonymousCredentials();
var credentialDetails = new CredentialDetails(credentials, PrivacyLevel.Private, EncryptedConnection.NotEncrypted);
```

# <a name="net-sdk-v2"></a>[SDK do .NET v2](#tab/sdk2)

```csharp
var credentials = "{\"credentialData\":\"\"}";
```

---

## <a name="troubleshooting"></a>Solução de problemas

### <a name="no-gateway-and-data-source-id-found-when-calling-get-data-sources"></a>Nenhuma ID da fonte de dados e gateway encontrado ao chamar obter fontes de dados

Esse problema significa que o conjunto de dados não está associado a um gateway. Ao criar um novo conjunto de dados, para cada conexão de nuvem, uma fonte de dados sem credenciais é criada automaticamente no gateway de nuvem do usuário. Este gateway é usado para armazenar as credenciais para conexões de nuvem.

Depois de criar o conjunto de dados, uma associação automática é criada entre o conjunto de dados e um gateway adequado, que contém as fontes de dados correspondente para todas as conexões. Se não houver nenhum gateway assim ou vários gateways adequados, a associação automática falhará.

Se você estiver usando conjuntos de dados no local, crie as fontes de dados locais ausentes e associe o conjunto de dados a um gateway manualmente usando [Associar ao Gateway](https://docs.microsoft.com/rest/api/power-bi/datasets/bindtogateway).

Para descobrir os gateways que podem ser associados, use [Descobrir Gateways](https://docs.microsoft.com/rest/api/power-bi/datasets/discovergateways).