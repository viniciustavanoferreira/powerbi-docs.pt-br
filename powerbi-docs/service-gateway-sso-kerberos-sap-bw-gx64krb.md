---
title: Usar o Kerberos para logon único (SSO) no SAP BW com gx64krb5
description: Configurar o servidor do SAP BW para habilitar o SSO do serviço do Power BI usando gx64krb5
author: arthiriyer
ms.author: arthii
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 10/10/2019
LocalizationGroup: Gateways
ms.openlocfilehash: 9588f13a857dc105dce3b3577df7c3b06df027ed
ms.sourcegitcommit: f77b24a8a588605f005c9bb1fdad864955885718
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2019
ms.locfileid: "74699235"
---
# <a name="use-kerberos-for-single-sign-on-sso-to-sap-bw-using-gx64krb5"></a>Usar o Kerberos para logon único (SSO) no SAP BW com gx64krb5

Este artigo descreve como configurar a fonte de dados do SAP BW para habilitar o SSO no serviço do Power BI usando o gx64krb5.

> [!NOTE]
> Conclua as etapas deste artigo, além das etapas em [Configurar o SSO de Kerberos](service-gateway-sso-kerberos.md) para habilitar a atualização baseada em SSO de relatórios com base no Servidor de Aplicativos do SAP BW no serviço do Power BI. No entanto, a Microsoft recomenda o uso da CommonCryptoLib, não do gx64krb5, como a biblioteca SNC. O SAP não é mais compatível com o gx64krb5 e as etapas necessárias para configurá-lo para uso com o gateway são significativamente mais complexas em comparação a CommonCryptoLib. Para saber mais sobre como configurar o SSO usando o CommonCryptoLib, confira [Configurar o SAP BW para SSO usando o CommonCryptoLib](service-gateway-sso-kerberos-sap-bw-commoncryptolib.md). Você deve usar CommonCryptoLib _ou_ gx64krb5 como sua biblioteca SNC. Não conclua as etapas de configuração para as duas bibliotecas.

Este guia é abrangente. Se você já tiver concluído parte das etapas descritas, poderá pulá-lo. Por exemplo, talvez você já tenha configurado o servidor do SAP BW para SSO usando o gx64krb5.

## <a name="set-up-gx64krb5-on-the-gateway-machine-and-the-sap-bw-server"></a>Configurar o gx64krb5 no computador do gateway e no servidor do SAP BW

> [!NOTE]
> A biblioteca do gx64krb5 não é mais compatível com o SAP. Para saber mais, veja [Nota SAP 352295](https://launchpad.support.sap.com/#/notes/352295). O gx64krb5 não permite conexões de SSO do gateway de dados para os Servidores de Mensagens do SAP BW. Somente conexões com os Servidores de Aplicativos do SAP BW são possíveis. Essa restrição não existirá se você usar [CommonCryptoLib](service-gateway-sso-kerberos-sap-bw-commoncryptolib.md) como biblioteca do SNC. Embora outras bibliotecas SNC também possam funcionar no SSO do BW, mas não têm mais suporte oficial da Microsoft.

A biblioteca do gx64krb5 precisa ser usada pelo cliente e pelo servidor para concluir uma conexão de SSO por meio do gateway. Dessa maneira, o cliente e o servidor precisam usar a mesma biblioteca SNC.

1. Baixe o gx64krb5.dll da [Nota da SAP 2115486](https://launchpad.support.sap.com/) (usuário s da SAP necessário). Verifique se você tem pelo menos a versão 1.0.11.x. Baixe também o gsskrb5.dll (a versão de 32 bits da biblioteca) se quiser testar a conexão SSO no GUI do SAP antes de tentar a conexão SSO por meio do gateway (recomendado). A versão de 32 bits é necessária para testar com o GUI do SAP, porque este só está disponível em 32 bits.

1. Coloque o gx64krb5.dll em um local no computador do gateway que possa ser acessado pelo usuário do serviço do gateway. Caso você deseje testar a conexão SSO usando a GUI do SAP, coloque também uma cópia de gsskrb5.dll no computador e defina a variável de ambiente **SNC_LIB** para que aponte para ela. O usuário do serviço do gateway e os usuários do AD (Active Directory) que o usuário do serviço representará precisam de permissões de leitura e execução na cópia de gx64krb5.dll. Recomendamos conceder permissões nos arquivos .dll ao grupo de usuários autenticados. Para fins de teste, você também pode conceder explicitamente essas permissões para o usuário do serviço do gateway e o usuário do Active Directory usado para teste.

1. Se o servidor do BW ainda não estiver configurado para SSO com o gx64krb5.dll, coloque outra cópia da .dll no computador do servidor do SAP BW em um local acessível ao servidor do SAP BW. 

    Para saber mais sobre como configurar o gx64krb5.dll para uso com um servidor do SAP BW, confira a [Documentação do SAP](https://launchpad.support.sap.com/#/notes/2115486) (usuário s do SAP necessário).

1. Nos computadores cliente e servidor, defina as variáveis de ambiente **SNC_LIB** e **SNC_LIB_64**: 
    - Se você usar gsskrb5.dll, defina a variável **SNC_LIB** como o caminho absoluto. 
    - Se você usar gx64krb5.dll, defina a variável **SNC_LIB_64** como o caminho absoluto.

## <a name="configure-an-sap-bw-service-user-and-enable-snc-communication-on-the-bw-server"></a>Configurar um usuário do serviço do SAP BW e habilitar a comunicação SNC no servidor do BW

Conclua esta seção caso ainda não tenha configurado o servidor do SAP BW para comunicação SNC (por exemplo, SSO) usando o gx64krb5.

> [!NOTE]
> Esta seção pressupõe que você já criou um usuário de serviço para BW e associou a ele um SPN adequado (por exemplo, um nome que começa com *SAP/* ).

1. Permita acesso ao usuário de serviço ao Servidor de Aplicativos do SAP BW:

    1. No computador do servidor do SAP BW, adicione o usuário de serviço ao grupo Administrador Local. Abra o programa **Gerenciamento de Computador** e identifique o grupo Administrador Local do servidor. 

        ![Programa Gerenciamento do Computador](media/service-gateway-sso-kerberos/computer-management.png)

    1. Clique duas vezes no grupo Administrador Local e selecione **Adicionar** para adicionar o usuário de serviço ao grupo. 

    1. Selecione **Verificar Nomes** para garantir que você inseriu o nome corretamente e clique em **OK**.

1. Defina o usuário de serviço do servidor do SAP BW como o usuário que o inicia no computador do servidor SAP BW:

    1. Abra **Executar** e insira **Services.msc**. 

    1. Localize o serviço correspondente à instância do Servidor de Aplicativos do SAP BW, clique nele com o botão direito do mouse e selecione **Propriedades**.

        ![Captura de tela de Serviços, com as Propriedades realçadas](media/service-gateway-sso-kerberos/server-properties.png)

    1. Alterne para a guia **Fazer logon** e altere o usuário para o usuário de serviço do SAP BW. 

    1. Insira a senha do usuário e selecione **OK**.

1. Entre no servidor no Logon do SAP e defina os seguintes parâmetros de perfil usando a transação RZ10:

    1. Defina o parâmetro de perfil **snc/identity/as** como *p:&lt;o usuário de serviço do SAP BW que você criou&gt;* . Por exemplo, *p:BWServiceUser\@MYDOMAIN.COM*. *p:* antecede o UPN do usuário do serviço, ao contrário de *p:CN=* , que precede o UPN quando você usa CommonCryptoLib como biblioteca SNC.

    1. Defina o parâmetro de perfil **snc/gssapi\_lib** como o *&lt;caminho para gx64krb5.dll no servidor do BW&gt;* . Coloque a biblioteca em um local que o Servidor de Aplicativos do SAP BW possa acessar.

    1. Defina os seguintes parâmetros de perfil adicionais, alterando os valores conforme necessário para atender às suas necessidades. As últimas cinco opções permitem que os clientes se conectem ao servidor do SAP BW usando o Logon do SAP, sem a necessidade de ter o SNC configurado.

        | **Configuração** | **Valor** |
        | --- | --- |
        | snc/data\_protection/max | 3 |
        | snc/data\_protection/min | 1 |
        | snc/data\_protection/use | 9 |
        | snc/accept\_insecure\_cpic | 1 |
        | snc/accept\_insecure\_gui | 1 |
        | snc/accept\_insecure\_r3int\_rfc | 1 |
        | snc/accept\_insecure\_rfc | 1 |
        | snc/permit\_insecure\_start | 1 |

    1. Defina a propriedade **snc/enable** como 1.

1. Após definir esses parâmetros de perfil, abra o Console de Gerenciamento do SAP no computador do servidor e reinicie a instância do SAP BW. 

   Se o servidor não for iniciado, confirme se você definiu os parâmetros de perfil corretamente. Para saber mais sobre as configurações de parâmetro de perfil, confira a [Documentação do SAP](https://help.sap.com/saphelp_nw70ehp1/helpdata/en/e6/56f466e99a11d1a5b00000e835363f/frameset.htm). Também é possível consultar a seção [Solução de problemas](#troubleshooting) neste artigo.

## <a name="map-an-sap-bw-user-to-an-active-directory-user"></a>Mapear um usuário do SAP BW para um usuário do Active Directory

Caso ainda não tenha feito isso, mapeie um usuário do Active Directory para um usuário do Servidor de Aplicativos do SAP BW e teste a conexão de SSO no Logon do SAP.

1. Entre no servidor SAP BW usando o Logon do SAP. Execute a transação SU01.

1. Em **Usuário**, insira o usuário do SAP BW em que você quer habilitar a conexão de SSO. Selecione o ícone **Editar** (ícone de caneta) perto do canto superior esquerdo da janela Logon do SAP.

    ![Tela Manutenção de usuário do SAP BW](media/service-gateway-sso-kerberos/user-maintenance.png)

1. Selecione a guia **SNC**. Na caixa de entrada do nome SNC, insira *p:&lt;seu usuário do Active Directory&gt;@&lt;seu domínio&gt;* . Para o nome SNC, *p:* deve preceder o UPN do usuário do Active Directory. Observe que o UPN diferencia maiúsculas de minúsculas.

   O usuário do Active Directory especificado deve pertencer à pessoa ou à organização para a qual você deseja habilitar o acesso SSO ao Servidor de Aplicativos do SAP BW. Por exemplo, se você quiser habilitar o acesso de SSO para o usuário testuser\@TESTDOMAIN.COM, insira *p:testuser\@TESTDOMAIN.COM*.

    ![Tela Manter usuários do SAP BW](media/service-gateway-sso-kerberos/maintain-users.png)

1. Clique no ícone **Salvar** (imagem de disquete) próximo ao canto superior esquerdo da tela.

## <a name="test-sign-in-via-sso"></a>Testar a entrada por meio do SSO

Verifique se você pode entrar no servidor usando o Logon do SAP por SSO como o usuário do Active Directory para o qual você habilitou acesso por SSO:

1. Como o usuário do Active Directory para o qual você acabou de habilitar o acesso SSO, entre em um computador no domínio no qual o Logon do SAP esteja instalado. Inicie o Logon do SAP e crie uma conexão.

1. Copie o arquivo gsskrb5.dll baixado anteriormente para o local do computador em que você fez logon. Defina a variável de ambiente **SNC_LIB** para o caminho absoluto desse local.

1. Inicie o Logon do SAP e crie uma conexão.

1. Na tela **Criar Nova Entrada do Sistema**, selecione **Sistema Especificado pelo Usuário** e, em seguida, **Avançar**.

    ![Tela Criar Nova Entrada do Sistema](media/service-gateway-sso-kerberos/new-system-entry.png)

1. Preencha os detalhes apropriados na próxima tela, incluindo o servidor de aplicativos, o número da instância e a ID do sistema. Em seguida, selecione **Concluir**.

1. Clique com o botão direito do mouse na nova conexão, selecione **Propriedades** e a guia **Rede**. 

1. Na caixa **Nome SNC**, insira *p:&lt;o UPN do usuário de serviço do SAP BW&gt;* . Por exemplo, *p:BWServiceUser\@MYDOMAIN.COM*. Selecione **OK**.

    ![Tela Propriedades de Entrada do Sistema](media/service-gateway-sso-kerberos/system-entry-properties.png)

1. Clique duas vezes na conexão recém-criada para tentar uma conexão de SSO com o servidor SAP BW. 

   Se essa conexão for bem-sucedida, vá para a próxima seção. Caso contrário, examine as etapas anteriores neste documento para garantir que foram concluídas corretamente ou examine a seção [Solução de problemas](#troubleshooting). Se não for possível se conectar ao servidor SAP BW por meio do SSO neste contexto, você não poderá se conectar ao servidor SAP BW usando o SSO no contexto do gateway.

## <a name="add-registry-entries-to-the-gateway-machine"></a>Adicionar entradas de registro ao computador do gateway

Adicione as entradas de Registro necessárias ao Registro do computador em que o gateway está instalado, bem como a computadores destinados à conexão do Power BI Desktop. Para adicionar essas entradas de Registro, execute os seguintes comandos:

- ```REG ADD HKLM\SOFTWARE\Wow6432Node\SAP\gsskrb5 /v ForceIniCredOK /t REG_DWORD /d 1 /f```

- ```REG ADD HKLM\SOFTWARE\SAP\gsskrb5 /v ForceIniCredOK /t REG_DWORD /d 1 /f```

## <a name="add-a-new-sap-bw-application-server-data-source-to-the-power-bi-service-or-edit-an-existing-one"></a>Adicionar uma nova fonte de dados do Servidor de Aplicativos do SAP BW ao serviço do Power BI ou edite uma existente

1. Na janela de configuração da fonte de dados, insira o **Nome do host**, o **Número do Sistema** e a **ID do cliente** do Servidor de Aplicativos do SAP BW, como faria para entrar no servidor SAP BW por meio do Power BI Desktop.

1. No campo **Nome do Parceiro SNC**, insira *p:&lt;o SPN mapeado para o usuário do serviço do SAP BW&gt;* . Por exemplo, se o SPN for SAP/BWServiceUser\@MYDOMAIN.COM, insira *p:SAP/BWServiceUser\@MYDOMAIN.COM* no campo **Nome do Parceiro SNC**.

1. Para a biblioteca SNC, selecione **SNC\_LIB** ou **SNC\_LIB\_64**. Verifique se **SNC\_LIB\_64** no computador do gateway aponta para gx64krb5.dll. Como alternativa, selecione a opção **Personalizado** e forneça o caminho absoluto de gx64krb5.dll no computador do gateway.

1. Selecione **Usar SSO via Kerberos para consultas do DirectQuery** e **Aplicar**. Se a conexão de teste não for bem-sucedida, verifique se as etapas de instalação e de configuração anteriores foram concluídas corretamente.

1. [Executar um relatório do Power BI](service-gateway-sso-kerberos.md#run-a-power-bi-report)

## <a name="troubleshooting"></a>Solução de problemas

### <a name="troubleshoot-gx64krb5-configuration"></a>Solução de problemas de configuração do gx64krb5

Caso ocorra algum dos problemas a seguir, siga estas etapas para solucionar problemas de instalação do gx64krb5 e de conexões SSO:

* Você encontra erros ao concluir as etapas de configuração do gx64krb5. Por exemplo, o servidor do SAP BW não será iniciado depois que você alterar os parâmetros do perfil. Exiba os logs do servidor (... work\dev\_W0 na máquina do servidor) para solucionar esses erros. 

* Não é possível iniciar o serviço do SAP BW devido a uma falha de logon. Talvez você tenha digitado a senha incorreta ao configurar o usuário *Iniciar como* do SAP BW. Verifique a senha entrando como o usuário de serviço do SAP BW em um computador no ambiente do Active Directory.

* Caso você receba erros que indiquem que as credenciais da fonte de dados subjacente (por exemplo, SQL Server) estão impedindo a inicialização do servidor, verifique se você permitiu acesso ao usuário do serviço ao banco de dados do SAP BW.

* Talvez receberá a seguinte mensagem: *(GSS-API) O destino especificado é desconhecido ou inacessível*. Isso geralmente significa que o nome SNC incorreto foi especificado. Use apenas *p:* , e não *p:CN =* para anteceder o UPN do usuário de serviço no aplicativo cliente.

* Talvez receberá a seguinte mensagem: *(GSS-API) Um nome inválido foi fornecido*. Garanta que *p:* esteja no valor do parâmetro de perfil da identidade SNC do servidor.

* Talvez receberá a seguinte mensagem: *(Erro de SNC) O módulo especificado não pôde ser encontrado*. Normalmente, esse erro é causado ao colocar o gx64krb5.dll em um local que exige privilégios elevados (direitos de administrador) para acessar.

### <a name="troubleshoot-gateway-connectivity-issues"></a>Solucionar problemas de conectividade do gateway

1. Verifique os logs de gateway. Abra o aplicativo de configuração do gateway, selecione **Diagnóstico** e, em seguida, **Exportar logs**. Os erros mais recentes são mostrados na parte inferior de qualquer arquivo de log examinado.

    ![Aplicativo de gateway de dados local, com o Diagnóstico realçado](media/service-gateway-sso-kerberos/gateway-diagnostics.png)

1. Ative o rastreamento do SAP BW e examine os arquivos de log gerados. Há vários tipos diferentes de rastreamento do SAP BW disponíveis (por exemplo, rastreamento CPIC):

   a. Para habilitar o rastreamento CPIC, defina duas variáveis de ambiente: **CPIC\_TRACE** e **CPIC\_TRACE\_DIR**.

      A primeira variável define o nível de rastreamento e a segunda define o diretório do arquivo de rastreamento. O diretório deve ser um local em que os membros do grupo usuários autenticados possam gravar. 
 
    b. Defina **CPIC\_TRACE** como *3* e **CPIC\_TRACE\_DIR** como qualquer diretório em que você deseja gravar os arquivos de rastreamento. Por exemplo:

      ![Rastreamento CPIC](media/service-gateway-sso-kerberos/cpic-tracing.png)

    c. Reproduza o problema e verifique se **CPIC\_TRACE\_DIR** contém arquivos de rastreamento. 

## <a name="next-steps"></a>Próximas etapas

Para saber mais sobre o gateway de dados local e o DirectQuery, confira estes recursos:

* [O que é um gateway de dados local?](/data-integration/gateway/service-gateway-onprem)
* [DirectQuery no Power BI](desktop-directquery-about.md)
* [Fontes de dados com suporte do DirectQuery](desktop-directquery-data-sources.md)
* [DirectQuery e SAP BW](desktop-directquery-sap-bw.md)
* [DirectQuery e SAP HANA](desktop-directquery-sap-hana.md)
