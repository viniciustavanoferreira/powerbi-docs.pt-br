---
title: Criar um certificado SSL
description: Instruções de solução alternativa para criar certificados manualmente para o servidor do desenvolvedor
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 06/18/2019
ms.openlocfilehash: fab40863d7beae4892a56975aa5e92c4fe5486ac
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/05/2020
ms.locfileid: "79380262"
---
# <a name="create-an-ssl-certificate"></a>Criar um certificado SSL

Este artigo descreve como criar um certificado SSL.

Para gerar o certificado usando o cmdlet `New-SelfSignedCertificate` do PowerShell no Windows 8 ou posterior, execute o seguinte comando:

```cmd
pbiviz --install-cert
```

A ferramenta requer a instalação do OpenSSL para o Windows 7. O utilitário OpenSSL deve estar disponível na linha de comando.

Para instalar o OpenSSL, acesse o site [OpenSSL](https://www.openssl.org) ou [Binários do OpenSSL](https://wiki.openssl.org/index.php/Binaries).

## <a name="create-a-certificate-mac-os-x"></a>Criar um certificado (Mac OS X)

Normalmente, o utilitário OpenSSL está disponível no sistema operacional Linux ou Mac OS X.

Você também pode instalar o utilitário executando um dos seguintes comandos:

* Do gerenciador de pacotes do *Brew*:

    ```cmd
    brew install openssl
    brew link openssl --force
    ```

* Usando *MacPorts*:

    ```cmd
    sudo port install openssl
    ```

Depois de instalar o utilitário OpenSSL para gerar um novo certificado, execute o seguinte comando:

```cmd
pbiviz --install-cert
```

## <a name="create-a-certificate-linux"></a>Criar um certificado (Linux)

Se o utilitário OpenSSL não estiver disponível no seu sistema operacional Linux, você poderá instalá-lo usando um dos seguintes comandos:

* Para o gerenciador de pacotes *APT*:

    ```cmd
    sudo apt-get install openssl
    ```

* Para o *Yellowdog Updater*:

    ```cmd
    yum install openssl
    ```

* Para o *Redhat Package Manager*:

    ```cmd
    rpm install openssl
    ```

Se o utilitário OpenSSL já estiver disponível em seu sistema operacional, gere um novo certificado executando o seguinte comando:

```cmd
pbiviz --install-cert
```

Ou você pode obter o utilitário OpenSSL acessando o site [OpenSSL](https://www.openssl.org) ou [Binários do OpenSSL](https://wiki.openssl.org/index.php/Binaries).

## <a name="generate-the-certificate-manually"></a>Gerar o certificado manualmente

Você pode especificar os certificados gerados por quaisquer ferramentas.

Se o utilitário OpenSSL já estiver instalado em seu sistema operacional, gere um novo certificado executando os seguintes comandos:

```cmd
openssl req -x509 -newkey rsa:4096 -keyout PowerBICustomVisualTest_private.key -out PowerBICustomVisualTest_public.crt -days 365
```

Normalmente, você pode encontrar os certificados do servidor Web do PowerBI-visuals-tools executando um dos seguintes:

* Para a instância global das ferramentas:

    ```cmd
    %appdata%\npm\node_modules\PowerBI-visuals-tools\certs
    ```

* Para a instância local das ferramentas:

    ```cmd
    <custom visual project root>\node_modules\PowerBI-visuals-tools\certs
    ```

Se você usar o formato PEM, salve o arquivo de certificado como *PowerBICustomVisualTest_public.crt* e salve privateKey como *PowerBICustomVisualTest_public.key*.

Se você usar o formato PFX, salve o arquivo de certificado como *PowerBICustomVisualTest_public.pfx*.

Se o arquivo de certificado PFX exigir uma senha, faça o seguinte:
1. No arquivo de configuração, especifique:

    ```cmd
    \PowerBI-visuals-tools\config.json
    ```

1. Na seção `server`, especifique a senha substituindo o espaço reservado "*SUA FRASE SECRETA*":

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