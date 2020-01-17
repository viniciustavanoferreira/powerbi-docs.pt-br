---
title: Criptografar credenciais
description: Passo a passo – criptografar as credenciais para fontes de dados do Gateway Local
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 01/08/2020
ms.openlocfilehash: b1fc4a505aa993c606743eefb6e8fb8c0379317d
ms.sourcegitcommit: 4b926ab5f09592680627dca1f0ba016b07a86ec0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75836619"
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

Criptografe o valor das credenciais usando a chave pública do gateway. Diferentes versões do gateway podem ter diferentes tamanhos de chave pública.

Veja o exemplo no código do SDK, disponível no repositório PowerBI-CSharp no GitHub, [PowerBI-CSharp/sdk/PowerBI.Api/Extensions/V2/](https://github.com/microsoft/PowerBI-CSharp/tree/master/sdk/PowerBI.Api/Extensions/V2).

- [AsymmetricKeyEncryptor.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/V2/AsymmetricKeyEncryptor.cs)
- [Asymmetric1024KeyEncryptionHelper.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/V2/Asymmetric1024KeyEncryptionHelper.cs)
- [AsymmetricHigherKeyEncryptionHelper.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/V2/AsymmetricHigherKeyEncryptionHelper.cs)
- [AuthenticatedEncryption.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/V2/AuthenticatedEncryption.cs)