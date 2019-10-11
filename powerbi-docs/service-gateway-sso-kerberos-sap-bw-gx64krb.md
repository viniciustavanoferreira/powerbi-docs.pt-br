---
title: Usar o Kerberos para logon único (SSO) no SAP BW com gx64krb5
description: Configurar o servidor do SAP BW para habilitar o SSO do serviço do Power BI usando gx64krb5
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 08/01/2019
LocalizationGroup: Gateways
ms.openlocfilehash: 4932f00fa7585c6b4f9186c29b65700d7a14fbea
ms.sourcegitcommit: 9bf3cdcf5d8b8dd12aa1339b8910fcbc40f4cbe4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/05/2019
ms.locfileid: "71968699"
---
# <a name="use-kerberos-for-single-sign-on-sso-to-sap-bw-using-gx64krb5"></a>Usar o Kerberos para logon único (SSO) no SAP BW com gx64krb5

Este artigo descreve como configurar a fonte de dados do SAP BW para habilitar o SSO no serviço do Power BI usando o gx64krb5.

> [!NOTE]
> Conclua as etapas deste artigo, além das etapas em [Configurar o SSO de Kerberos](service-gateway-sso-kerberos.md) para habilitar a atualização baseada em SSO de relatórios com base no Servidor de Aplicativos do SAP BW no serviço do Power BI. No entanto, a Microsoft recomenda o uso da CommonCryptoLib, não do gx64krb5, como a biblioteca SNC. O SAP não oferece mais suporte para gx64krb5, e as etapas necessárias para configurá-lo para uso com o gateway são significativamente mais complexas em comparação a CommonCryptoLib. Confira [Configurar SAP BW para SSO usando CommonCryptoLib](service-gateway-sso-kerberos-sap-bw-commoncryptolib.md) para saber como configurar o SSO usando CommonCryptoLib. Você deve concluir a configuração para CommonCryptoLib _ou_ gx64krb5. Não conclua as etapas de configuração para as duas bibliotecas.

### <a name="set-up-gx64krb5-on-gateway-machine-and-the-sap-bw-server"></a>Configurar o gx64krb5 no computador do gateway e no servidor do SAP BW
Este guia tenta ser o mais abrangente possível. Se você já concluiu algumas destas etapas, ignore-as. Por exemplo, talvez você já tenha configurado o servidor do SAP BW para SSO usando o gx64krb5.

### <a name="set-up-gx64krb5-on-the-gateway-machine-and-the-sap-bw-server"></a>Configurar o gx64krb5 no computador do gateway e no servidor do SAP BW

> [!NOTE]
> Não há mais suporte ativo para o `gx64krb5` pela SAP. Para saber mais, veja [Nota SAP 352295](https://launchpad.support.sap.com/#/notes/352295). Observe também que `gx64krb5` não permite conexões de SSO do gateway de dados com Servidores de Mensagens do SAP BW. Apenas as conexões com Servidores de Aplicativos do SAP BW são possíveis. Essa restrição somente do Servidor de Aplicativos não existe se você usar [CommonCryptoLib](service-gateway-sso-kerberos-sap-bw-commoncryptolib.md) como sua biblioteca do SNC. Outras bibliotecas SNC também podem funcionar no SSO do BW, mas não têm suporte oficial da Microsoft.

`gx64krb5` precisa estar em uso pelo cliente e pelo servidor para concluir uma conexão SSO por meio do gateway, ou seja, o cliente e o servidor precisam usar a mesma biblioteca SNC.

1. Baixe `gx64krb5` da [Nota da SAP 2115486](https://launchpad.support.sap.com/) (é necessário ser um usuário do SAP). Verifique se você tem pelo menos a versão 1.0.11.x. Baixe também `gsskrb5` (a versão de 32 bits da biblioteca) se quiser testar a conexão SSO no GUI do SAP antes de tentar a conexão SSO por meio do gateway (recomendado). A versão de 32 bits é necessária para testar com o GUI do SAP, porque este só está disponível em 32 bits.

1. Coloque `gx64krb5` em uma localização no computador do gateway que possa ser acessada pelo usuário do serviço do gateway. Caso você deseje testar a conexão SSO usando a GUI do SAP, coloque também uma cópia de `gsskrb5` no computador e defina a variável de ambiente **SNC_LIB** para que aponte para ela. O usuário do serviço do gateway e os usuários do AD (Active Directory) que o usuário do serviço representará precisam de permissões de leitura e execução na cópia de `gx64krb5`. Recomendamos conceder permissões nos arquivos .dll ao grupo de usuários autenticados. Para fins de teste, você também pode conceder explicitamente essas permissões para o usuário do serviço do gateway e o usuário do Active Directory usado para teste.

1. Se o servidor do BW ainda não estiver configurado para SSO usando o gx64krb5, coloque outra cópia da .dll no computador do servidor do SAP BW em uma localização acessível ao servidor do SAP BW. Consulte a [documentação do SAP](https://launchpad.support.sap.com/#/notes/2115486) (usuário s necessário) para obter mais informações sobre como configurar o gx64krb5 para uso com um servidor do SAP BW.

1. Nos computadores cliente e servidor, defina as variáveis de ambiente `SNC_LIB` e/ou `SNC_LIB_64`. Se usar gsskrb5, defina a variável `SNC_LIB` como o caminho absoluto de gsskrb5.dll. Se usar gx64krb5, defina a variável `SNC_LIB_64` como o caminho absoluto de gx64krb5.dll.

### <a name="configure-an-sap-bw-service-user-and-enable-snc-communication-on-the-bw-server"></a>Configurar um usuário do serviço do SAP BW e habilitar a comunicação SNC no servidor do BW

Conclua esta seção caso ainda não tenha configurado o servidor do SAP BW para comunicação SNC (por exemplo, SSO) usando o gx64krb5.

> [!NOTE]
> Esta seção pressupõe que você já criou um usuário de serviço para BW e associou a ele um SPN adequado (por exemplo, algo que começa com `SAP/`).

1. Permita acesso ao usuário de serviço ao Servidor de Aplicativos do SAP BW:

    1. No computador do servidor do SAP BW, adicione o usuário de serviço ao grupo Administrador Local. Abra o programa Gerenciamento de Computador e identifique o grupo Administrador Local do servidor. Por ex.:

        ![Captura de tela do programa Gerenciamento de Computador](media/service-gateway-sso-kerberos/computer-management.png)

    1. Clique duas vezes no grupo Administrador Local e selecione **Adicionar** para adicionar o usuário de serviço ao grupo. Selecione **Verificar Nomes** para garantir que você inseriu o nome corretamente. Selecione **OK**.

1. Defina o usuário de serviço do servidor do SAP BW como o usuário que inicia o serviço do servidor do SAP BW no computador do servidor SAP BW.

    1. Abra **Executar** e insira **Services.msc**. Procure o serviço correspondente à instância do Servidor de Aplicativos do SAP BW. Clique com o botão direito do mouse nele e selecione **Propriedades**.

        ![Captura de tela de Serviços, com as Propriedades realçadas](media/service-gateway-sso-kerberos/server-properties.png)

    1. Alterne para a guia **Fazer logon** e altere o usuário para o usuário de serviço do SAP BW. Insira a senha do usuário e selecione **OK**.

1. Entre no servidor no Logon do SAP e defina os seguintes parâmetros de perfil usando a transação RZ10:

    1. Defina o parâmetro de perfil **snc/identity/as** como *p:&lt;o usuário do serviço do SAP BW criado&gt;* , como *p:BWServiceUser\@MYDOMAIN.COM*. Observe o p: que precede o UPN do usuário de serviço. Ele não é p:CN= como quando a Biblioteca de Criptografia Comum é usada como a biblioteca SNC.

    1. Defina o parâmetro de perfil **snc/gssapi\_lib** como *&lt;caminho para gx64krb5.dll no computador do servidor do BW&gt;* . Lembre-se de colocar a biblioteca em uma localização que o Servidor de Aplicativos do SAP BW possa acessar.

    1. Também defina os seguintes parâmetros de perfil adicionais, alterando os valores conforme necessário para atender às suas necessidades. Observe que as últimas cinco opções permitem que os clientes se conectem ao servidor SAP BW usando o Logon do SAP, sem a necessidade de ter o SNC configurado.

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

1. Após definir esses parâmetros de perfil, abra o Console de Gerenciamento do SAP no computador do servidor e reinicie a instância do SAP BW. Se o servidor não for iniciado, confirme se você definiu os parâmetros de perfil corretamente. Para obter mais informações sobre configurações de perfil de parâmetro, confira a [documentação da SAP](https://help.sap.com/saphelp_nw70ehp1/helpdata/en/e6/56f466e99a11d1a5b00000e835363f/frameset.htm). Consulte também as informações sobre solução de problemas mais adiante nesta seção caso tenha problemas.

### <a name="map-a-sap-bw-user-to-an-active-directory-user"></a>Mapear um usuário do SAP BW para um usuário do Active Directory

Caso ainda não tenha feito isso, mapeie um usuário do Active Directory para um usuário do Servidor de Aplicativos do SAP BW e teste a conexão de SSO no Logon do SAP.

1. Entre no servidor SAP BW usando o Logon do SAP. Execute a transação SU01.

1. Em **Usuário**, insira o usuário do SAP BW para o qual deseja habilitar conexões SSO (na captura de tela abaixo, estamos preparando a definição de permissões para BIUSER). Selecione o ícone **Editar** (imagem de uma caneta) próximo ao canto superior esquerdo da janela Logon do SAP.

    ![Captura de tela da tela Manutenção de usuário do SAP BW](media/service-gateway-sso-kerberos/user-maintenance.png)

1. Selecione a guia **SNC**. Na caixa de entrada do nome SNC, insira *p:&lt;seu usuário do Active Directory&gt;@&lt;seu domínio&gt;* . Observe o p: obrigatório que deve preceder o UPN do usuário do Active Directory. O usuário do Active Directory especificado deve pertencer à pessoa ou à organização para a qual você deseja habilitar o acesso SSO ao Servidor de Aplicativos do SAP BW. Por exemplo, caso deseje habilitar o acesso SSO para o usuário *testuser\@TESTDOMAIN.COM*, insira *p:testuser\@TESTDOMAIN.COM*.

    ![Captura de tela da tela Manter usuários do SAP BW](media/service-gateway-sso-kerberos/maintain-users.png)

1. Selecione o ícone **Salvar** (a imagem de um disquete) próximo ao canto superior esquerdo da tela.

### <a name="test-sign-in-via-sso"></a>Testar a entrada por meio do SSO

Verifique se você pode entrar no servidor usando o Logon da SAP por SSO como o usuário do Active Directory para o qual você acaba de habilitar acesso por SSO.

1. Como o usuário do Active Directory para o qual você acabou de habilitar o acesso SSO, entre em um computador no domínio no qual o Logon da SAP esteja instalado. Inicie o Logon do SAP e crie uma conexão.

1. Copie a .dll do `gsskrb5` baixada anteriormente para uma localização no computador ao qual você acabou de se conectar. Defina a variável de ambiente `SNC_LIB` como o caminho absoluto dessa localização.

1. Inicie o Logon do SAP e crie uma conexão.

1. Na tela **Criar Entrada do Sistema**, selecione **Sistema Especificado pelo Usuário** e, em seguida, **Avançar**.

    ![Captura de tela da tela Criar Entrada do Sistema](media/service-gateway-sso-kerberos/new-system-entry.png)

1. Preencha os detalhes apropriados na próxima tela, incluindo o servidor de aplicativos, o número da instância e a ID do sistema. Em seguida, selecione **Concluir**.

1. Clique com o botão direito do mouse na nova conexão e selecione **Propriedades**. Selecione a guia **Rede**. Na caixa de texto **Nome SNC**, insira *p:&lt;o UPN do usuário do serviço do SAP BW&gt;* , como *p:BWServiceUser\@MYDOMAIN.COM*. Selecione **OK**.

    ![Captura de tela da tela Propriedades da Entrada do Sistema](media/service-gateway-sso-kerberos/system-entry-properties.png)

1. Clique duas vezes na conexão recém-criada para tentar uma conexão de SSO com o servidor SAP BW. Se essa conexão for bem-sucedida, vá para a próxima etapa. Caso contrário, examine as etapas anteriores neste documento para garantir que foram concluídas corretamente, ou examine a seção de solução de problemas abaixo. Observe que, se não conseguir se conectar ao servidor SAP BW por meio do SSO neste contexto, você não poderá se conectar ao servidor SAP BW usando o SSO no contexto do gateway.

### <a name="add-registry-entries-to-the-gateway-machine"></a>Adicionar entradas de registro ao computador do gateway

Adicione as entradas de Registro necessárias ao Registro do computador em que o gateway está instalado, bem como a computadores destinados à conexão do Power BI Desktop. Estes são os comandos para execução:

1. ```REG ADD HKLM\SOFTWARE\Wow6432Node\SAP\gsskrb5 /v ForceIniCredOK /t REG_DWORD /d 1 /f```

1. ```REG ADD HKLM\SOFTWARE\SAP\gsskrb5 /v ForceIniCredOK /t REG_DWORD /d 1 /f```

### <a name="add-a-new-sap-bw-application-server-data-source-to-the-power-bi-service-or-edit-an-existing-one"></a>Adicionar uma nova fonte de dados do Servidor de Aplicativos do SAP BW ao serviço do Power BI ou edite uma existente

1. Na janela de configuração da fonte de dados, insira o **Nome do host**, o **Número do Sistema** e a **ID do cliente** do Servidor de Aplicativos, como faria para entrar no servidor SAP BW por meio do Power BI Desktop.

1. No campo **Nome do Parceiro SNC**, insira *p:&lt;o SPN mapeado para o usuário do serviço do SAP BW&gt;* . Por exemplo, se o SPN for **SAP/BWServiceUser\@MYDOMAIN.COM**, você deverá inserir *p:SAP/BWServiceUser\@MYDOMAIN.COM* no campo **Nome do Parceiro SNC**.

1. Para a biblioteca SNC, selecione **SNC\_LIB** ou **SNC\_LIB\_64**. Verifique se **SNC\_LIB\_64** no computador do gateway aponta para gx64krb5.dll. Como alternativa, selecione a opção "Personalizado" e forneça o caminho absoluto de gx64krb5.dll (no computador do gateway).

1. Marque a caixa **Usar SSO via Kerberos para consultas do DirectQuery** e selecione **Aplicar**. Se a conexão de teste não for bem-sucedida, verifique se as etapas de instalação e de configuração anteriores foram concluídas corretamente.

1. [Executar um relatório do Power BI](service-gateway-sso-kerberos.md#run-a-power-bi-report)

## <a name="troubleshooting"></a>Solução de problemas

### <a name="troubleshoot-gx64krb5-configuration"></a>Solução de problemas de configuração do gx64krb5

Em caso de problemas, siga estas etapas para solucionar problemas de instalação do gx64krb5 e de conexões SSO.

* A exibição dos logs do servidor (…work\dev\_w0 no computador do servidor) pode ser útil para solucionar os erros encontrados na conclusão das etapas de instalação do gx64krb5. Isso se aplica especialmente se o servidor SAP BW não é iniciado após a alteração dos parâmetros de perfil.

* Se você não puder iniciar o serviço SAP BW devido a uma falha de logon, talvez você tenha fornecido a senha incorreta ao definir o usuário "iniciar como" do SAP BW. Verifique a senha fazendo logon em um computador no ambiente do Active Directory como o usuário de serviço do SAP BW.

* Caso você receba erros que indiquem que as credenciais da fonte de dados subjacente (por exemplo, SQL Server) estão impedindo a inicialização do servidor, verifique se você permitiu acesso ao usuário do serviço ao banco de dados do SAP BW.

* Talvez você receba a seguinte mensagem: *(GSS-API) O destino especificado é desconhecido ou inacessível.* Isso geralmente significa que o nome SNC incorreto foi especificado. Use apenas "p", não "p:CN =" nem qualquer outro valor no aplicativo cliente que não seja o UPN do usuário de serviço.

* Talvez você receba a seguinte mensagem: *(GSS-API) Um nome inválido foi fornecido.* Garanta que "p:" esteja no valor do parâmetro de perfil da identidade SNC do servidor.

* Talvez você receba a seguinte mensagem: *(Erro de SNC) O módulo especificado não pôde ser encontrado.* Isso geralmente é causado pela colocação de `gx64krb5.dll` em um lugar que exige privilégios elevados (direitos de administrador) para o acesso.

### <a name="troubleshoot-gateway-connectivity-issues"></a>Solucionar problemas de conectividade do gateway

1. Verifique os logs de gateway. Abra o aplicativo de configuração do gateway, selecione **Diagnóstico** e, em seguida, **Exportar logs**. Os erros mais recentes são mostrados na parte inferior de qualquer arquivo de log examinado.

    ![Captura de tela do aplicativo de gateway de dados local, com o Diagnóstico realçado](media/service-gateway-sso-kerberos/gateway-diagnostics.png)

1. Ative o rastreamento do SAP BW e examine os arquivos de log gerados. Há vários tipos diferentes de rastreamento do SAP BW disponíveis (por exemplo, rastreamento CPIC). Veja a documentação da SAP para obter mais informações.

## <a name="next-steps"></a>Próximas etapas

Para obter mais informações sobre o **gateway de dados local** e o **DirectQuery**, confira os seguintes recursos:

* [O que é um gateway de dados local?](/data-integration/gateway/service-gateway-onprem)
* [DirectQuery no Power BI](desktop-directquery-about.md)
* [Fontes de dados com suporte do DirectQuery](desktop-directquery-data-sources.md)
* [DirectQuery e SAP BW](desktop-directquery-sap-bw.md)
* [DirectQuery e SAP HANA](desktop-directquery-sap-hana.md)
