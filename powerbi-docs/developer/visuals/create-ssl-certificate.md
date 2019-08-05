---
title: Criação de um certificado SSL
description: Instruções de solução alternativa para criar certificados manualmente para o servidor do desenvolvedor
author: zBritva
ms.author: v-ilgali
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: tutorial
ms.date: 06/18/2019
ms.openlocfilehash: 3287e8a7eb1c36c3f0d8a1fc24faa0442de2dddf
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68425426"
---
# <a name="creating-ssl-certificate"></a>Criação de um certificado SSL

Execute o comando a seguir para gerar o certificado usando o cmdlet New-SelfSignedCertificate do PowerShell no Windows 8 ou posterior.

A ferramenta requer a instalação do OpenSSL para o **Windows** **7**. O utilitário `openssll` precisa estar disponível na linha de comando.

Para instalar o OpenSSL, visite [https://www.openssl.org](https://www.openssl.org) ou [https://wiki.openssl.org/index.php/Binaries](https://wiki.openssl.org/index.php/Binaries)

```cmd
pbiviz --create-cert
```

## <a name="create-certificate-mac-os-x"></a>Criar certificado (Mac OS X)

Geralmente, o utilitário OpenSSL está disponível em sistemas operacionais Linux ou Mac OS X.

Caso contrário, você pode instalar do

gerenciador de pacotes *Brew*

```cmd
brew install openssl
brew link openssl --force
```

ou usando o *MacPorts*

```cmd
sudo port install openssl
```

Após a instalação OpenSSL para gerar uma nova chamada de certificado:

```cmd
pbiviz --create-cert
```

## <a name="create-certificate-linux"></a>Criar certificado (Linux)

Os utilitários OpenSSL não estão disponíveis no seu sistema operacional Linux, você pode instalá-los usando os comandos a seguir.

Para o gerenciador de pacotes *APT*:

```cmd
sudo apt-get install openssl
```

Para o *Yellowdog Updater*:

```cmd
yum install openssl
```

Para o *Redhat Package Manager*:

```cmd
rpm install openssl
```

Se o OpenSSL já estiver disponível em sua chamada do sistema operacional

```cmd
pbiviz --create-cert
```

para gerar um novo certificado.

Ou obtenha-o de [https://www.openssl.org](https://www.openssl.org) ou [https://wiki.openssl.org/index.php/Binaries](https://wiki.openssl.org/index.php/Binaries)

## <a name="generate-certificate-manually"></a>Gerar certificado manualmente

Você pode especificar os certificados gerados por quaisquer ferramentas.

Se tiver o OpenSSL instalado em seu sistema, você poderá executar o comando a seguir para gerar um novo certificado

```cmd
openssl req -x509 -newkey rsa:4096 -keyout PowerBICustomVisualTest_private.key -out PowerBICustomVisualTest_public.crt -days 365
```

Normalmente, os certificados do servidor Web PowerBI-visuals-tools estão localizados em

```cmd
%appdata%\npm\node_modules\PowerBI-visuals-tools\certs
```

para a instância global das ferramentas

ou

```cmd
<custom visual project root>\node_modules\PowerBI-visuals-tools\certs
```

para a instância local das ferramentas.

Você deverá salvar o arquivo de certificado como `PowerBICustomVisualTest_public.cer` e a chave privada como `PowerBICustomVisualTest_public.key` se você usa o formato PEM.
Salve o arquivo de certificado como `PowerBICustomVisualTest_public.pfx` se você usa o formato PFX.

Se o arquivo de certificado PFX exigir uma senha, você deverá especificá-la em

```cmd
\PowerBI-visuals-tools\config.json
```

na seção do servidor:

```cmd
"server":{
    "root":"webRoot",
    "assetsRoute":"/assets",
    "privateKey":"certs/PowerBICustomVisualTest_private.key",
    "certificate":"certs/PowerBICustomVisualTest_public.crt",
    "pfx":"certs/PowerBICustomVisualTest_public.pfx",
    "port":"8080",
    "passphrase":"YOUR PASSPHRASE"
}
```
