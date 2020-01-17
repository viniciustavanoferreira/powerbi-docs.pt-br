---
title: Configurar credenciais de forma programática para o Power BI
description: Como configurar as credenciais de modo programático para o Power BI para a automação
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 01/08/2020
ms.openlocfilehash: 222edd901409fa71d98308f27407838d54564834
ms.sourcegitcommit: 4b926ab5f09592680627dca1f0ba016b07a86ec0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75836586"
---
# <a name="configure-credentials-programmatically-for-power-bi"></a>Configurar credenciais de forma programática para o Power BI

Siga estas etapas para configurar as credenciais programaticamente para o Power BI.

## <a name="configure-a-credential-flow-for-data-sources"></a>Configurar um fluxo de credenciais para fontes de dados

1. Chame [Obter Fontes de Dados](https://docs.microsoft.com/rest/api/power-bi/datasets/getdatasourcesingroup) para descobrir as fontes de dados do conjunto de dados. No corpo da resposta para cada fonte de dados, há o tipo, os detalhes de conexão, gateway e ID de fonte de dados.

    ```csharp
    var datasources = pbiClient.Datasets.GetDatasources(datasetId).Value;
    var datasource = datasources.First(); // select a datasource
    ```

2. Compile cadeia de caracteres de credenciais de acordo com os [Exemplos de Fonte de Dados de Atualização](https://docs.microsoft.com/rest/api/power-bi/gateways/updatedatasource) dependendo do tipo de credenciais.

    ```csharp
    var credentials = "{\"credentialData\":[{\"name\":\"username\", \"value\":\"john\"},{\"name\":\"password\", \"value\":\"*****\"}]}";
    ```

3. Compile os detalhes de credencial.

    ```csharp
    var credentialDetails = new CredentialDetails(
                    credentials,
                    CredentialTypeEnum.Basic,
                    EncryptedConnectionEnum.Encrypted,
                    EncryptionAlgorithmEnum.None,
                    PrivacyLevelEnum.Private);
    ```

4. Chame [Atualizar Fonte de Dados](https://docs.microsoft.com/rest/api/power-bi/gateways/updatedatasource) para definir credenciais, usando a ID da fonte de dados e o gateway da etapa 1 e usando os detalhes de credencial da etapa 4.

    ```csharp
    pbiClient.Gateways.UpdateDatasource(gatewayId, datasourceId, credentialDetails);
    ```

### <a name="expired-on-premises-data-source-credentials-flow"></a>Fluxo de credenciais da fonte de dados local expirada

1. [Siga as etapas 1 e 2 do cenário anterior](#configure-a-credential-flow-for-data-sources).

2. Chame [Obter Gateway](https://docs.microsoft.com/rest/api/power-bi/gateways/getgateways) para recuperar a chave pública do gateway.

    ```csharp
    var gateway = pbiClient.Gateways.GetGatewayById(datasource.GatewayId);
    ```

3. Criptografe a cadeia de caracteres de credenciais com a chave pública do gateway. Diferentes versões do gateway podem ter diferentes tamanhos de chave pública.
    
    Veja o exemplo no código do SDK, disponível no repositório PowerBI-CSharp no GitHub, [PowerBI-CSharp/sdk/PowerBI.Api/Extensions/V2/](https://github.com/microsoft/PowerBI-CSharp/tree/master/sdk/PowerBI.Api/Extensions/V2).
    * [AsymmetricKeyEncryptor.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/V2/AsymmetricKeyEncryptor.cs)
    * [Asymmetric1024KeyEncryptionHelper.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/V2/Asymmetric1024KeyEncryptionHelper.cs)
    * [AsymmetricHigherKeyEncryptionHelper.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/V2/AsymmetricHigherKeyEncryptionHelper.cs)
    * [AuthenticatedEncryption.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/V2/AuthenticatedEncryption.cs)

4. Compile detalhes de credenciais com credenciais criptografadas.

    ```csharp
    var credentialDetails = new CredentialDetails(
                    encryptedCredentials,
                    CredentialTypeEnum.Basic,
                    EncryptedConnectionEnum.Encrypted,
                    EncryptionAlgorithmEnum.RSA-OAEP,
                    PrivacyLevelEnum.Private);
    ```

5. Chame [Atualizar Fonte de Dados](https://docs.microsoft.com/rest/api/power-bi/gateways/updatedatasource) para definir credenciais.

    ```csharp
    pbiClient.Gateways.UpdateDatasource(gatewayId, datasourceId, credentialDetails);
    ```

## <a name="configure-a-new-data-source-for-a-data-gateway"></a>Configurar uma nova fonte de dados para um gateway de dados

1. Instale o [Gateway de dados local](https://powerbi.microsoft.com/gateway/) no seu computador.

2. Chame [Obter Gateways](https://docs.microsoft.com/rest/api/power-bi/gateways/getgateways) para recuperar a ID de gateway e a chave pública.

    ```csharp
    var gateways = pbiClient.Gateways.GetGateways().Value;
    var gateway = gateways.First(); // select a gateway
    ```

3. Compile detalhes de credencial como no cenário anterior usando a chave pública do gateway recuperada na etapa de [fluxo de credenciais de fonte de dados local expiradas](#expired-on-premises-data source-credentials-flow-on-premises-data-gateway).

4. criar o corpo da solicitação

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

## <a name="troubleshooting"></a>Solução de problemas

### <a name="no-gateway-and-data-source-id-found-when-calling-get-data-sources"></a>Nenhuma ID da fonte de dados e gateway encontrado ao chamar obter fontes de dados

Esse problema significa que o conjunto de dados não está associado a um gateway. Ao criar um novo conjunto de dados, para cada conexão de nuvem, uma fonte de dados sem credenciais é criada automaticamente no gateway de nuvem do usuário. Este gateway é usado para armazenar as credenciais para conexões de nuvem.

Depois de criar o conjunto de dados, uma associação automática é feita entre o conjunto de dados e um gateway adequado, que contém as fontes de dados correspondente para todas as conexões. Se não houver nenhum gateway assim ou vários gateways adequados, a associação automática falhará.

Crie fontes de dados locais ausentes, se houver, e associe o conjunto de dados para um gateway manualmente usando [Associar ao Gateway](https://docs.microsoft.com/rest/api/power-bi/datasets/bindtogateway).

Para descobrir os gateways que podem ser associados, use [Descobrir Gateways](https://docs.microsoft.com/rest/api/power-bi/datasets/discovergateways).