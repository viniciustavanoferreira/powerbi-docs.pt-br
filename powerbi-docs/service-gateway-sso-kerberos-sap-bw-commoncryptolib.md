---
title: Usar o logon único Kerberos de SSO para SAP BW usando CommonCryptoLib (sapcrypto.dll)
description: Configurar o servidor de SAP BW para habilitar o SSO do serviço do Power BI usando CommonCryptoLib (sapcrypto.dll)
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 08/01/2019
LocalizationGroup: Gateways
ms.openlocfilehash: 9e676d7a14a2094d2fd7a8e41f8e49dc64f96ec2
ms.sourcegitcommit: 9bf3cdcf5d8b8dd12aa1339b8910fcbc40f4cbe4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/05/2019
ms.locfileid: "71968769"
---
# <a name="use-kerberos-single-sign-on-for-sso-to-sap-bw-using-commoncryptolib-sapcryptodll"></a>Usar o logon único Kerberos de SSO para SAP BW usando CommonCryptoLib (sapcrypto.dll)

Este artigo descreve como configurar a fonte de dados do SAP BW para habilitar o SSO no serviço do Power BI usando a CommonCryptoLib (sapcrypto.dll).

> [!NOTE]
> Conclua as etapas neste artigo, além das etapas em [Configurar o SSO do Kerberos](service-gateway-sso-kerberos.md), antes de tentar atualizar um relatório baseado em SAP BW que usa o SSO do Kerberos. Usar o CommonCryptoLib como sua biblioteca SNC habilita as conexões de SSO com os servidores de aplicativos e de mensagens do SAP BW.

## <a name="configure-sap-bw-to-enable-sso-using-commoncryptolib"></a>Configurar o SAP BW para habilitar o SSO usando a CommonCryptoLib

> [!NOTE]
> O gateway de dados local é um software de 64 bits e, portanto, exige a versão de 64 bits da CommonCryptoLib (sapcrypto.dll) para realizar o SSO do BW. Se você estiver planejando testar a conexão SSO com o servidor do SAP BW na GUI do SAP antes de tentar uma conexão SSO por meio do gateway (recomendado), também precisará da versão de 32 bits da CommonCryptoLib, pois a GUI do SAP é um software de 32 bits.

1. Verifique se o servidor BW está configurado corretamente para o SSO do Kerberos usando CommonCryptoLib. Se estiver, você deverá conseguir usar o SSO para acessar o servidor do BW (seja diretamente ou por meio de um servidor de mensagens do SAP BW) com uma ferramenta do SAP como a GUI do SAP que tenha sido configurada para usar CommonCryptoLib. Para saber mais sobre as etapas de configuração, confira [Logon único do SAP: autenticar com Kerberos/SPNEGO](https://blogs.sap.com/2017/07/27/sap-single-sign-on-authenticate-with-kerberosspnego/). O servidor BW deve usar CommonCryptoLib como biblioteca SNC e ter um nome SNC que comece com "CN=", como "CN=BW1". Para saber mais sobre os requisitos de nome SNC, confira [Parâmetros SNC para configuração do Kerberos](https://help.sap.com/viewer/df185fd53bb645b1bd99284ee4e4a750/3.0/en-US/360534094511490d91b9589d20abb49a.html) (especificamente com o parâmetro snc/identity/as).

1. Se ainda não tiver feito isso, instale a versão x64 do [SAP .NET Connector](https://support.sap.com/en/product/connectors/msnet.html) no computador em que o gateway foi instalado. Verifique se o componente foi instalado tentando se conectar com o servidor do BW no Power BI Desktop por meio do computador do gateway. Se você não conseguir se conectar usando a implementação 2.0, isso indicará que o Conector .NET não está instalado ou não foi instalado no cache de assembly global.

1. Verifique se o SLC (Cliente de Logon Seguro) do SAP não está em execução no computador em que o gateway está instalado. O SLC armazena em cache os tíquetes do Kerberos de um modo que pode interferir na capacidade do gateway de usar o Kerberos para SSO. Se o SLC estiver instalado, desinstale-o ou saia do Cliente de Logon Seguro do SAP: clique com o botão direito do mouse no ícone na bandeja do sistema e selecione "Fazer logoff e sair" antes de tentar uma conexão SSO usando o gateway. O SLC não é compatível para uso em computadores do Windows Server. Para saber mais, confira [Nota SAP 2780475](https://launchpad.support.sap.com/#/notes/2780475) (usuário s necessário).

    ![Cliente de Logon Seguro do SAP](media/service-gateway-sso-kerberos/sap-secure-login-client.png)

    Se você desinstalar o SLC ou selecionar **Fazer logoff** e **Sair**, abra uma janela de comando e insira `klist purge` para limpar quaisquer tíquetes do Kerberos armazenados em cache antes de tentar uma conexão SSO por meio do gateway.

1. Baixe o CommonCryptoLib (sapcrypto.dll) na versão **8.5.25 ou posterior** de 64 bits do SAP Launchpad e copie-o em uma pasta do computador do gateway. No mesmo diretório em que você copiou sapcrypto.dll, crie um arquivo chamado sapcrypto.ini, com o seguinte conteúdo:

    ```
    ccl/snc/enable_kerberos_in_client_role = 1
    ```

    O arquivo .ini contém informações de configuração necessárias do CommonCryptoLib para habilitar o SSO no cenário de gateway.

    > [!NOTE]
    > Esses arquivos devem ser armazenados no mesmo local; em outras palavras, _/path/to/sapcrypto/_ precisa conter sapcrypto.ini e sapcrypto.dll.

    O usuário de serviço do gateway e o usuário do AD (Active Directory) que o usuário do serviço representará precisam de permissões de leitura e execução para ambos os arquivos. É recomendável conceder permissões para os arquivos .ini e .dll ao Grupo de usuários autenticados. Para fins de teste, você também pode conceder explicitamente essas permissões para o usuário do serviço do gateway e o usuário do Active Directory usado para teste. Na captura de tela abaixo, concedemos ao grupo de usuários autenticados permissões de **leitura &amp; e execução** para sapcrypto.dll:

    ![Usuários autenticados](media/service-gateway-sso-kerberos/authenticated-users.png)

1. Caso você ainda não tenha uma fonte de dados do SAP BW associada ao gateway pelo qual deseja que a conexão SSO flua, adicione uma na página **Gerenciar gateways** no serviço do Power BI. Se você já tiver essa fonte de dados, prepare-se para editá-la. Escolha **SAP Business Warehouse** como o **Tipo de Fonte de Dados** caso você queira criar uma conexão SSO para um servidor de aplicativos BW. Escolha o **Servidor de mensagens do SAP Business Warehouse** caso você queira criar uma conexão SSO para um servidor de aplicativos do BW.

    Na **Biblioteca SNC**, selecione a variável de ambiente **SNC\_LIB, SNC\_LIB\_64** ou **Personalizado**. Se você selecionar a opção **SNC\_LIB**, precisará definir o valor da variável de ambiente **SNC\_LIB\_64** no computador do gateway como o caminho absoluto da cópia de 64 bits de sapcrypto.dll no computador do gateway, por exemplo, *C:\Users\Test\Desktop\sapcrypto.dll*. Se você escolher **Personalizado**, cole o caminho absoluto para sapcrypto.dll no campo Caminho da Biblioteca SNC Personalizada exibido na página **Gerenciar gateways**. Como o **Nome do Parceiro SNC**, insira o nome da SNC do servidor BW. Em **Configurações avançadas**, verifique se a opção **Usar SSO via Kerberos para consultas do DirectQuery** está marcada. Os outros campos devem ser preenchidos como seriam se você estivesse estabelecendo uma conexão de autenticação do Windows do PBI desktop.

1. Crie uma variável de ambiente do sistema **CCL\_PROFILE** e aponte-a para sapcrypto.ini:

    ![Variável de ambiente do sistema CCL\_PROFILE](media/service-gateway-sso-kerberos/ccl-profile-variable.png)

    Lembre-se de que os arquivos sapcrypto .dll e .ini devem existir no mesmo local. No exemplo mostrado acima, em que sapcrypto.ini está na área de trabalho, sapcrypto.dll deveria estar na área de trabalho.

1. Reinicie o serviço de gateway:

    ![Reiniciar o serviço de gateway](media/service-gateway-sso-kerberos/restart-gateway-service.png)

1. [Executar um relatório do Power BI](service-gateway-sso-kerberos.md#run-a-power-bi-report)

## <a name="troubleshooting"></a>Solução de problemas

Se não for possível atualizar o relatório no serviço do Power BI, use o rastreamento de gateway, CPIC e CommonCryptoLib para ajudar a diagnosticar o problema. O rastreamento CPIC e CommonCryptoLib são produtos do SAP, então a Microsoft não pode oferecer suporte direto a eles. Para usuários do Active Directory que receberão acesso SSO ao BW, algumas configurações do Active Directory podem exigir que os usuários sejam membros do grupo de administradores no computador em que o gateway está instalado.

1. **Logs do gateway:** Basta reproduzir o problema, abrir o [aplicativo de gateway](https://docs.microsoft.com/data-integration/gateway/service-gateway-app), clicar na guia **Diagnóstico** e selecionar **Exportar logs**:

    ![Exportar logs do gateway](media/service-gateway-sso-kerberos/export-gateway-logs.png)

1. **Rastreamento CPIC:** Para habilitar o rastreamento CPIC, defina duas variáveis de ambiente: **CPIC\_TRACE** e **CPIC\_TRACE\_DIR**. A primeira variável define o nível de rastreamento e a segunda define o diretório do arquivo de rastreamento. O diretório deve ser um local em que os membros do grupo usuários autenticados possam gravar. Defina **CPIC\_TRACE** como 3 e **CPIC\_TRACE\_DIR** como qualquer diretório em que deseja gravar os arquivos de rastreamento. Por ex.:

    ![Rastreamento CPIC](media/service-gateway-sso-kerberos/cpic-tracing.png)

    Reproduza o problema e verifique se CPIC\_TRACE\_DIR contém arquivos de rastreamento.

1. **Rastreamento CommonCryptoLib:** Ative o rastreamento CommonCryptoLib adicionando duas linhas ao arquivo sapcrypto.ini criado anteriormente:

    ```
    ccl/trace/level=5
    ccl/trace/directory=<drive>:\logs\sectrace
    ```

    Altere a opção _ccl/trace/directory_ para um local em que os membros do grupo de usuários autenticados possam gravar. Como alternativa, crie um arquivo .ini para alterar esse comportamento. No mesmo diretório de sapcrypto.ini e sapcrypto.dll, crie um arquivo chamado sectrace.ini, com o conteúdo a seguir. Substitua a opção **DIRECTORY** por uma localização no computador na qual os membros do grupo **Usuários Autenticados** possam fazer a gravação:

    ```
    LEVEL = 5
    DIRECTORY = <drive>:\logs\sectrace
    ```

    Agora, reproduza o problema e verifique se a localização apontada por **DIRECTORY** contém arquivos de rastreamento. Não se esqueça de desativar o rastreamento CPIC e CCL quando terminar.

    Para saber mais sobre o rastreamento CommonCryptoLib, confira [Nota SAP 2491573](https://launchpad.support.sap.com/#/notes/2491573) (usuário s necessário).

## <a name="next-steps"></a>Próximas etapas

Para obter mais informações sobre o **gateway de dados local** e o **DirectQuery**, confira os seguintes recursos:

* [O que é um gateway de dados local?](/data-integration/gateway/service-gateway-onprem)
* [DirectQuery no Power BI](desktop-directquery-about.md)
* [Fontes de dados com suporte do DirectQuery](desktop-directquery-data-sources.md)
* [DirectQuery e SAP BW](desktop-directquery-sap-bw.md)
* [DirectQuery e SAP HANA](desktop-directquery-sap-hana.md)
