---
title: Criar certificados SSL para elementos visuais do Power BI
description: Saiba como gerar certificados SSL usando Power BI Visual Tools no Windows, Mac, Linux ou manualmente.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 05/08/2020
ms.openlocfilehash: 37bd8f15dcf17cd0f967e819338a719edf2a3054
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83276365"
---
# <a name="create-an-ssl-certificate"></a>Criar um certificado SSL

Este artigo descreve como gerar e instalar certificados SSL (Secure Sockets Layer) para visuais do Power BI.

Para os procedimentos do Windows, macOS X e Linux, você deve ter o pacote **pbiviz** do Power BI Visual Tools instalado. Para saber mais, confira [Configurar o ambiente do desenvolvedor](https://docs.microsoft.com/power-bi/developer/visuals/custom-visual-develop-tutorial#setting-up-the-developer-environment). 

## <a name="create-a-certificate-on-windows"></a>Criar um certificado no Windows

Para gerar um certificado usando o cmdlet `New-SelfSignedCertificate` do PowerShell no Windows 8 ou posterior, execute o seguinte comando:

```powershell
pbiviz --install-cert
```

Para o Windows 7, a ferramenta `pbiviz` requer que o utilitário OpenSSL esteja disponível na linha de comando. Para instalar o OpenSSL, acesse [OpenSSL](https://www.openssl.org) ou [Binários OpenSSL](https://wiki.openssl.org/index.php/Binaries).

Para saber mais e obter instruções para instalar um certificado, confira [Criar e instalar um certificado para Windows](https://docs.microsoft.com/power-bi/developer/visuals/custom-visual-develop-tutorial#windows).

## <a name="create-a-certificate-on-macos-x"></a>Criar um certificado no macOS X

O utilitário OpenSSL geralmente está disponível no sistema operacional macOS X.

Você também pode instalar o utilitário OpenSSL executando um dos seguintes comandos:

- Do gerenciador de pacotes do *Brew*:
  
  ```cmd
  brew install openssl
  brew link openssl --force
  ```

- Usando *MacPorts*:
  
  ```cmd
  sudo port install openssl
  ```

Depois de instalar o utilitário OpenSSL, execute o seguinte comando para gerar um novo certificado:

```cmd
pbiviz --install-cert
```

Para saber mais e obter instruções, confira [Criar e instalar um certificado para OS X](https://docs.microsoft.com/power-bi/developer/visuals/custom-visual-develop-tutorial#osx).

## <a name="create-a-certificate-on-linux"></a>Criar um certificado no Linux

O utilitário OpenSSL geralmente está disponível no sistema operacional Linux.

Antes de começar, execute os seguintes comandos para garantir que `openssl` e `certutil` estejam instalados:

```sh
which openssl
which certutil
```

Se `openssl` e `certutil` não estiverem instalados, instale os utilitários `openssl` e `libnss3`.

### <a name="create-the-ssl-configuration-file"></a>Criar o arquivo de configuração de SSL

Crie um arquivo chamado */tmp/openssl.cnf* que contenha o seguinte texto:

```
authorityKeyIdentifier=keyid,issuer
basicConstraints=CA:FALSE
keyUsage = digitalSignature, nonRepudiation, keyEncipherment, dataEncipherment
subjectAltName = @alt_names

[ alt_names ]
DNS.1=localhost
```

### <a name="generate-root-certificate-authority"></a>Gerar autoridade de certificado raiz

Para gerar a autoridade de certificado raiz (AC) para assinar certificados locais, execute os seguintes comandos:

```sh
touch $HOME/.rnd
openssl req -x509 -nodes -new -sha256 -days 1024 -newkey rsa:2048 -keyout /tmp/local-root-ca.key -out /tmp/local-root-ca.pem -subj "/C=US/CN=Local Root CA/O=Local Root CA"
openssl x509 -outform pem -in /tmp/local-root-ca.pem -out /tmp/local-root-ca.crt
```

### <a name="generate-a-certificate-for-localhost"></a>Gerar um certificado para o localhost 

Para gerar um certificado para `localhost` usando a AC gerada e *openssl.cnf*, execute os seguintes comandos:

```sh
PBIVIZ=`which pbiviz`
PBIVIZ=`dirname $PBIVIZ`
PBIVIZ="$PBIVIZ/../lib/node_modules/powerbi-visuals-tools/certs"
# Make sure that $PBIVIZ contains the correct certificate directory path. ls $PBIVIZ should list 'blank' file.
openssl req -new -nodes -newkey rsa:2048 -keyout $PBIVIZ/PowerBIVisualTest_private.key -out $PBIVIZ/PowerBIVisualTest.csr -subj "/C=US/O=PowerBI Visuals/CN=localhost"
openssl x509 -req -sha256 -days 1024 -in $PBIVIZ/PowerBIVisualTest.csr -CA /tmp/local-root-ca.pem -CAkey /tmp/local-root-ca.key -CAcreateserial -extfile /tmp/openssl.cnf -out $PBIVIZ/PowerBIVisualTest_public.crt
```

### <a name="add-root-certificates"></a>Adicionar certificados de raiz

Para adicionar um certificado raiz ao banco de dados do navegador Chrome, execute:

```sh
certutil -A -n "Local Root CA" -t "CT,C,C" -i /tmp/local-root-ca.pem -d sql:$HOME/.pki/nssdb
```

Para adicionar um certificado raiz ao banco de dados do navegador Mozilla Firefox, execute:

```sh
for certDB in $(find $HOME/.mozilla* -name "cert*.db")
do
certDir=$(dirname ${certDB});
certutil -A -n "Local Root CA" -t "CT,C,C" -i /tmp/local-root-ca.pem -d sql:${certDir}
done
```

Para adicionar um certificado raiz de todo o sistema, execute:

```sh
sudo cp /tmp/local-root-ca.pem /usr/local/share/ca-certificates/
sudo update-ca-certificates
```

### <a name="remove-root-certificates"></a>Remover certificados raiz

Para remover um certificado raiz, execute:

```sh
sudo rm /usr/local/share/ca-certificates/local-root-ca.pem
sudo update-ca-certificates --fresh
```

## <a name="generate-a-certificate-manually"></a>Gerar um certificado manualmente

Você também pode gerar um certificado SSL manualmente usando o OpenSSL. Você pode especificar quaisquer ferramentas para gerar seus certificados.

Se o utilitário OpenSSL já estiver instalado, gere um novo certificado executando:

```cmd
openssl req -x509 -newkey rsa:4096 -keyout PowerBIVisualTest_private.key -out PowerBIVisualTest_public.crt -days 365
```

Normalmente, você pode encontrar os certificados do servidor Web do `PowerBI-visuals-tools` executando um dos seguintes comandos:

- Para a instância global das ferramentas:
  
  ```cmd
  %appdata%\npm\node_modules\PowerBI-visuals-tools\certs
  ```

- Para a instância local das ferramentas:
  
  ```cmd
  <Power BI visual project root>\node_modules\PowerBI-visuals-tools\certs
  ```

### <a name="pem-format"></a>Formato PEM

Se você usar o formato de certificado Privacy Enhanced Mail (PEM), salve o arquivo de certificado como *PowerBIVisualTest_public.crt* e salve a chave privada como *PowerBIVisualTest_private.key*.

### <a name="pfx-format"></a>Formato PFX

Se você usar o formato de certificado Personal Information Exchange (PFX), salve o arquivo de certificado como *PowerBIVisualTest_public.pfx*.

Se o arquivo de certificado PFX exigir uma senha:

1. No arquivo de configuração, especifique:
   
   ```cmd
   \PowerBI-visuals-tools\config.json
   ```
   
1. Na seção `server`, especifique a senha substituindo o espaço reservado \<SUA FRASE SECRETA>:

    ```cmd
    "server":{
        "root":"webRoot",
        "assetsRoute":"/assets",
        "privateKey":"certs/PowerBIVisualTest_private.key",
        "certificate":"certs/PowerBIVisualTest_public.crt",
        "pfx":"certs/PowerBIVisualTest_public.pfx",
        "port":"8080",
        "passphrase":"<YOUR PASSPHRASE>"
    }
    ```

## <a name="next-steps"></a>Próximas etapas
- [Desenvolver um visual do Power BI](custom-visual-develop-tutorial.md)
- [Exemplos de visuais do Power BI](samples.md)
- [Publicar um visual do Power BI no AppSource](office-store.md)
