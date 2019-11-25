---
title: Configurar credenciais de forma programática para o Power BI
description: Como configurar as credenciais de modo programático para o Power BI para a automação
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 02/25/2019
ms.openlocfilehash: 73ef45b5dbed8535b13aa557cb52929d4eea0e46
ms.sourcegitcommit: c395fe83d63641e0fbd7c98e51bbab224805bbcc
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74265604"
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

3. Criptografe a cadeia de caracteres de credenciais com a chave pública do Gateway usando o algoritmo de criptografia RSA.

    Use a seguinte classe auxiliar para criptografia:

    ```csharp
        public static class AsymmetricKeyEncryptionHelper
        {
            private const int SegmentLength = 85;
            private const int EncryptedLength = 128;

            /// <summary>

            /// Encrypts credentials using the RSA algorithm

            /// </summary>

            public static string EncodeCredentials(string credentialData, string publicKeyExponent, string publicKeyModulus)
            {
                using (RSACryptoServiceProvider rsa = new RSACryptoServiceProvider(EncryptedLength * 8))
                {
                    var parameters = rsa.ExportParameters(false);

                    parameters.Exponent = Convert.FromBase64String(publicKeyExponent);

                    parameters.Modulus = Convert.FromBase64String(publicKeyModulus);

                    rsa.ImportParameters(parameters);

                    return Encrypt(credentialData, rsa);
                }
            }

             private static string Encrypt(string plainText, RSACryptoServiceProvider rsa)
            {

                byte[] plainTextArray = Encoding.UTF8.GetBytes(plainText);

                // Split the message into different segments, each segment's length is 85. So, the result may be 85,85,85,20. 

                bool hasIncompleteSegment = plainTextArray.Length % SegmentLength != 0; 

                int segmentNumber = (!hasIncompleteSegment) ? (plainTextArray.Length / SegmentLength) : ((plainTextArray.Length SegmentLength) + 1);

                byte[] encryptedData = new byte[segmentNumber * EncryptedLength];

                int encryptedDataPosition = 0;

                for (var i = 0; i < segmentNumber; i++)
                {
                    int lengthToCopy;

                    if (i == segmentNumber - 1 && hasIncompleteSegment)

                        lengthToCopy = plainTextArray.Length % SegmentLength;

                    else

                        lengthToCopy = SegmentLength;

                    var segment = new byte[lengthToCopy];

                    Array.Copy(plainTextArray, i * SegmentLength, segment, 0, lengthToCopy);

                    var segmentEncryptedResult = rsa.Encrypt(segment, true);

                    Array.Copy(segmentEncryptedResult, 0, encryptedData, encryptedDataPosition, segmentEncryptedResult.Length);

                    encryptedDataPosition += segmentEncryptedResult.Length;

                }

                return Convert.ToBase64String(encryptedData);

            }

        }

        var encryptedCredentials = AsymmetricKeyEncryptionHelper.EncodeCredentials(credentials);
    ```

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
