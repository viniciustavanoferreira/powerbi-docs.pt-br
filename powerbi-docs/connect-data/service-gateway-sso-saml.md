---
title: Use SAML (Security Assertion Markup Language) para SSO do Power BI em fontes de dados locais
description: Configure seu gateway com SAML (Security Assertion Markup Language) para habilitar SSO do Power BI em fontes de dados locais.
author: arthiriyer
ms.author: arthii
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 10/10/2019
LocalizationGroup: Gateways
ms.openlocfilehash: 87684ee408663d3d3e68534fa89fd227327b6ac7
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83328440"
---
# <a name="use-security-assertion-markup-language-saml-for-sso-from-power-bi-to-on-premises-data-sources"></a>Use SAML (Security Assertion Markup Language) para SSO do Power BI em fontes de dados locais

A habilitação do SSO facilita a atualização de dados de fontes locais em relatórios e dashboards do Power BI, respeitando as permissões no nível de usuário configuradas nessas fontes. Use [SAML (Security Assertion Markup Language)](https://www.onelogin.com/pages/saml) para habilitar a conectividade ininterrupta de logon único. 

## <a name="supported-data-sources"></a>Fontes de dados com suporte

Atualmente, há suporte para SAP HANA com SAML. Para saber mais sobre como configurar e definir o logon único para o SAP HANA usando o SAML, confira [SSO do SAML para a Plataforma BI para HANA](https://wiki.scn.sap.com/wiki/display/SAPHANA/SAML+SSO+for+BI+Platform+to+HANA).

Temos compatibilidade com outras fontes de dados para o [Kerberos](service-gateway-sso-kerberos.md), incluindo o SAP HANA.

Para o SAP HANA, é recomendável habilitar a criptografia antes de estabelecer uma conexão de SSO do SAML. Para habilitar a criptografia, configure o servidor do HANA para aceitar conexões criptografadas. Também configure o gateway para usar a criptografia para se comunicar com o servidor do HANA. Como o driver ODBC do HANA não criptografa declarações SAML por padrão, a declaração SAML assinada será enviada do gateway para o servidor do HANA *às claras* e estará vulnerável à interceptação e reutilização por terceiros. Para ver instruções sobre como habilitar a criptografia para o HANA com a biblioteca OpenSSL, confira [Habilitar criptografia para o SAP HANA](/power-bi/desktop-sap-hana-encryption).

## <a name="configuring-the-gateway-and-data-source"></a>Como configurar a fonte de dados e o gateway

Para usar o SAML, é necessário estabelecer uma relação de confiança entre os servidores do HANA em que você quer habilitar o SSO e o gateway. Nesse cenário, o gateway será o IdP (provedor de identidade) do SAML. Há várias maneiras para estabelecer essa relação, como importar o certificado X509 do IdP do gateway para o repositório de confiança dos servidores HANA ou fazer com que o certificado X509 do gateway seja assinado por uma AC (autoridade de certificação) raiz considerada confiável pelos servidores do HANA. Embora descrevamos a segunda abordagem neste guia, é possível usar outra se for mais conveniente.

Embora este guia use o OpenSSL como provedor de criptografia do servidor do HANA, a SAP recomenda usar a Biblioteca Criptográfica do SAP (também conhecida como CommonCryptoLib ou sapcrypto) em vez do OpenSSL para concluir as etapas de configuração para estabelecer a relação de confiança. Para saber mais, confira a documentação oficial da SAP.

As etapas a seguir descrevem como estabelecer uma relação de confiança entre um servidor do HANA e o IdP do gateway assinando o certificado X509 do IdP do gateway com uma AC raiz considerada confiável pelo servidor do HANA. Você criará essa AC raiz:

1. Crie a chave privada e o certificado X509 da AC raiz. Por exemplo, para criar o certificado X509 da AC raiz e a chave privada no formato .pem, insira este comando:

   ```
   openssl req -new -x509 -newkey rsa:2048 -days 3650 -sha256 -keyout CA_Key.pem -out CA_Cert.pem -extensions v3_ca
   ```

    Verifique se a chave privada da AC raiz está protegida adequadamente. Se ela for obtida por terceiros, poderá ser usada para acesso não autorizado ao servidor do HANA. 

 1. Adicione o certificado (por exemplo, CA_Cert.pem) ao repositório de confiança do servidor do HANA para que este confie em todos os certificados assinados pela AC raiz que você criou. 

    O local do repositório de confiança do servidor do HANA pode ser encontrado examinando a definição de configuração **ssltruststore**. Se você tiver seguido as instruções na documentação do SAP que aborda como configurar o OpenSSL, o servidor do HANA talvez já confie em uma AC raiz que você pode reutilizar. Para saber mais, confira [Como configurar o Open SSL do SAP HANA Studio para o Servidor do SAP HANA](https://archive.sap.com/documents/docs/DOC-39571). Se você tiver vários servidores do HANA em que deseja habilitar o SSO do SAML, verifique se cada um dos servidores confia nessa AC raiz.

1. Crie o certificado X509 do IdP do gateway. 

   Por exemplo, para criar uma solicitação de assinatura de certificado (IdP_Req.pem) e uma chave privada (IdP_Key.pem) válidas por um ano, execute o seguinte comando:

   ```
   openssl req -newkey rsa:2048 -days 365 -sha256 -keyout IdP_Key.pem -out IdP_Req.pem -nodes
   ```

 1. Assine a solicitação de assinatura de certificado usando a AC raiz que você configurou como confiável pelos servidores do HANA. 

    Por exemplo, para assinar IdP_Req.pem usando CA_Cert.pem e CA_Key.pem (o certificado e a chave da AC raiz), execute o seguinte comando:

    ```
    openssl x509 -req -days 365 -in IdP_Req.pem -sha256 -extensions usr_cert -CA CA_Cert.pem -CAkey CA_Key.pem -CAcreateserial -out IdP_Cert.pem
    ```

     O certificado de IdP resultante será válido por um ano (consulte a opção -days). 

Importe o certificado do IdP no HANA Studio para criar um novo provedor de identidade SAML:

1. No SAP HANA Studio, clique com o botão direito do mouse no nome do servidor do SAP HANA e, em seguida, navegue até **Segurança** &gt; **Abrir Console de Segurança** &gt; **Provedor de Identidade SAML** &gt; **Biblioteca Criptográfica do OpenSSL**.

    ![Provedores de identidade](media/service-gateway-sso-saml/identity-providers.png)

1. Selecione **Importar**, navegue até IdP_Cert.pem e importe-o.

1. No SAP HANA Studio, selecione a pasta **Segurança**.

    ![Pasta de segurança](media/service-gateway-sso-saml/security-folder.png)

1. Expanda **Usuários** e, em seguida, selecione o usuário em que você deseja mapear o usuário do Power BI.

1. Selecione **SAML**e **Configurar**.

    ![Configurar SAML](media/service-gateway-sso-saml/configure-saml.png)

1. Selecione o provedor de identidade que você criou na etapa 2. Em **Identidade Externa**, insira o UPN do usuário do Power BI (normalmente, o endereço de email com o qual o usuário faz logon no Power BI) e, em seguida, selecione **Adicionar**. Se você tiver configurado o gateway para usar a opção de configuração *ADUserNameReplacementProperty*, insira o valor que substituirá o UPN original do usuário do Power BI. 

   Por exemplo, se definir *ADUserNameReplacementProperty* como **SAMAccountName**, você deverá inserir o **SAMAccountName** do usuário.

    ![Selecionar o provedor de identidade](media/service-gateway-sso-saml/select-identity-provider.png)

Agora que você tem o certificado e a identidade do gateway configurados, converta o certificado em um formato pfx e configure o gateway para usá-lo:

1. Converta o certificado para o formato pfx executando o comando a seguir. Esse comando nomeia o arquivo .pfx resultante samlcert.pfx e define *root* como a senha:

    ```
    openssl pkcs12 -export -out samltest.pfx -in IdP_Cert.pem -inkey IdP_Key.pem -passin pass:root -passout pass:root
    ```

1. Copie o arquivo pfx para o computador do gateway:

    1. Clique duas vezes em samltest.pfx e, em seguida, selecione **Computador Local** &gt; **Avançar**.

    1. Insira a senha e, em seguida, selecione **Próximo**.

    1. Selecione **Colocar todos os certificados no repositório a seguir** e, em seguida, **Procurar** &gt; **Pessoal** &gt; **OK**.

    1. Selecione **Avançar** e, em seguida, **Concluir**.

       ![Importar certificado](media/service-gateway-sso-saml/import-certificate.png)

1. Conceda à conta de serviço de gateway acesso à chave privada do certificado:

    1. No computador do gateway, execute o MMC (Console de Gerenciamento Microsoft).

        ![Executar MMC](media/service-gateway-sso-saml/run-mmc.png)

    1. Em **Arquivo**, selecione **Adicionar/Remover Snap-in**.

        ![Adicionar snap-in](media/service-gateway-sso-saml/add-snap-in.png)

    1. Selecione **Certificados** &gt; **Adicionar** e, em seguida, selecione **Conta de computador** &gt; **Avançar**.

    1. Selecione **Computador Local** &gt; **Concluir** &gt; **OK**.

    1. Expanda **Certificados** &gt; **Pessoal** &gt; **Certificados** e encontre o certificado.

    1. Clique com o botão direito do mouse no certificado e navegue até **Todas as Tarefas** &gt; **Gerenciar Chaves Privadas**.

        ![Gerenciar chaves privadas](media/service-gateway-sso-saml/manage-private-keys.png)

    1. Adicione a conta de serviço de gateway à lista. Por padrão, a conta é **NT SERVICE\PBIEgwService.** Você pode descobrir qual conta está executando o serviço de gateway executando **services.msc** e localizando **Serviço de gateway de dados local**.

        ![Serviço do gateway](media/service-gateway-sso-saml/gateway-service.png)

Por fim, siga estas etapas para adicionar a impressão digital do certificado à configuração do gateway:

1. Execute o seguinte comando do PowerShell para listar os certificados em seu computador:

    ```powershell
    Get-ChildItem -path cert:\LocalMachine\My
    ```

1. Copie a impressão digital do certificado criado.

1. Navegue até o diretório do gateway, que, por padrão, é C:\Arquivos de Programas\Gateway de dados local.

1. Abra PowerBI.DataMovement.Pipeline.GatewayCore.dll.config e localize a seção *SapHanaSAMLCertThumbprint*. Cole a impressão digital copiada.

1. Reinicie o serviço de gateway.

## <a name="running-a-power-bi-report"></a>Executando um relatório do Power BI

Agora você pode usar a página **Gerenciar Gateway** no Power BI para configurar a fonte de dados do SAP HANA. Em **Configurações Avançadas**, habilite o SSO por meio do SAML. Em seguida, você poderá publicar relatórios e conjuntos de dados associados àquela fonte de dados.

   ![Configurações avançadas](media/service-gateway-sso-saml/advanced-settings.png)

## <a name="troubleshooting"></a>Solução de problemas

Depois de configurar o SSO baseado em SAML, talvez você veja o seguinte erro no portal do Power BI: *As credenciais fornecidas não podem ser usadas para a fonte SAP HANA.* Esse erro indica que a credencial do SAML foi rejeitada pelo SAP HANA.

Os rastreamentos de autenticação do lado do servidor fornecem informações detalhadas para solução de problemas com credenciais no SAP HANA. Siga estas etapas para configurar o rastreamento no servidor SAP HANA:

1. No servidor SAP HANA, ative o rastreamento de autenticação executando a consulta a seguir:

    ```
    ALTER SYSTEM ALTER CONFIGURATION ('indexserver.ini', 'SYSTEM') set ('trace', 'authentication') = 'debug' with reconfigure 
    ```

1. Reproduza o problema.

1. No HANA Studio, abra o console de administração e selecione a guia **Arquivos de Diagnóstico**.

1. Abra o rastreamento mais recente do servidor de indexação e procure por *SAMLAuthenticator.cpp*.

    Você encontrará uma mensagem de erro detalhada indicando a causa raiz, por exemplo:

    ```
    [3957]{-1}[-1/-1] 2018-09-11 21:40:23.815797 d Authentication   SAMLAuthenticator.cpp(00091) : Element '{urn:oasis:names:tc:SAML:2.0:assertion}Assertion', attribute 'ID': '123123123123123' is not a valid value of the atomic type 'xs:ID'.
    [3957]{-1}[-1/-1] 2018-09-11 21:40:23.815914 i Authentication   SAMLAuthenticator.cpp(00403) : No valid SAML Assertion or SAML Protocol detected
    ```

1. Depois de solucionar os problemas, desative o rastreamento de autenticação executando a consulta a seguir:

    ```
    ALTER SYSTEM ALTER CONFIGURATION ('indexserver.ini', 'SYSTEM') UNSET ('trace', 'authentication');
    ```

## <a name="next-steps"></a>Próximas etapas

Para saber mais sobre o gateway de dados local e o DirectQuery, confira estes recursos:

* [O que é um gateway de dados local?](/data-integration/gateway/service-gateway-onprem)
* [DirectQuery no Power BI](desktop-directquery-about.md)
* [Fontes de dados com suporte do DirectQuery](power-bi-data-sources.md)
* [DirectQuery e SAP BW](desktop-directquery-sap-bw.md)
* [DirectQuery e SAP HANA](desktop-directquery-sap-hana.md)
