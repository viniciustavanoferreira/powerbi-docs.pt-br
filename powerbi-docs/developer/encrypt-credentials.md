---
title: Criptografar credenciais
description: Passo a passo – criptografar as credenciais para fontes de dados do Gateway Local
author: mahirdiab
ms.author: madia
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 02/04/2019
ms.openlocfilehash: 4747d548f8b02806c1e7b1359d140b09039e09d8
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/09/2019
ms.locfileid: "73863859"
---
# <a name="encrypt-credentials"></a>Criptografar credenciais

Quando você chama [Criar Fonte de Dados](https://docs.microsoft.com/rest/api/power-bi/gateways/createdatasource) ou [Atualizar Fonte de Dados](https://docs.microsoft.com/rest/api/power-bi/gateways/updatedatasource) em um **gateway local corporativo** usando a [API Rest do Power BI](https://docs.microsoft.com/rest/api/power-bi/), o valor de credenciais deve ser criptografado usando a chave pública do gateway.

Veja o exemplo de código abaixo de como criptografar as credenciais no .NET.

As credenciais fornecidas para o método de EncodeCredentials abaixo devem estar em um dos formatos a seguir, dependendo do tipo de credenciais:

**Credenciais básicas/do Windows**

```csharp
var credentials = "{\"credentialData\":[{\"name\":\"username\", \"value\":\"john\"},{\"name\":\"password\", \"value\":\"*****\"}]}";
```

**Credenciais de chave**

```csharp
var credentials = "{\"credentialData\":[{\"name\":\"key\", \"value\":\"ec....LA=\"}]}";
```

**Credenciais do OAuth2**

```csharp
var credentials = "{\"credentialData\":[{\"name\":\"accessToken\", \"value\":\"eyJ0....fwtQ\"}]}";
```

**Credenciais anônimas**

```csharp
var credentials = "{\"credentialData\":\"\"}";
```

**Criptografar credenciais**

```csharp
public static class AsymmetricKeyEncryptionHelper
{

    private const int SegmentLength = 85;
    private const int EncryptedLength = 128;

    public static string EncodeCredentials(string credentials, string publicKeyExponent, string publicKeyModulus)
    {
        using (RSACryptoServiceProvider rsa = new RSACryptoServiceProvider(EncryptedLength * 8))
        {
            var parameters = rsa.ExportParameters(false);
            parameters.Exponent = Convert.FromBase64String(publicKeyExponent);
            parameters.Modulus = Convert.FromBase64String(publicKeyModulus);
            rsa.ImportParameters(parameters);
            return Encrypt(credentials, rsa);
        }
    }

    private static string Encrypt(string plainText, RSACryptoServiceProvider rsa)
    {
        byte[] plainTextArray = Encoding.UTF8.GetBytes(plainText);

        // Split the message into different segments, each segment's length is 85. So the result may be 85,85,85,20.
        bool hasIncompleteSegment = plainTextArray.Length % SegmentLength != 0;

        int segmentNumber = (!hasIncompleteSegment) ? (plainTextArray.Length / SegmentLength) : ((plainTextArray.Length / SegmentLength) + 1);

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
```