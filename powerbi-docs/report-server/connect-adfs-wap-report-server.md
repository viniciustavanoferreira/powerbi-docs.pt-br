---
title: Usar o Proxy de Aplicativo Web e os Serviços de Federação do Active Directory – Servidor de Relatórios do Power BI
description: Saiba como usar o WAP (Proxy de Aplicativo Web) e os AD FS (Serviços de Federação do Active Directory) para se conectar ao Servidor de Relatórios do Power BI e ao SSRS (SQL Server Reporting Services) 2016 e posterior.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 01/14/2020
ms.openlocfilehash: 2caa96aceef90ad1d25a521cbf4a3f699a2a64e0
ms.sourcegitcommit: 0ae9328e7b35799d5d9613a6d79d2f86f53d9ab0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/16/2020
ms.locfileid: "76042430"
---
# <a name="use-web-application-proxy-and-active-directory-federated-services---power-bi-report-server"></a>Usar o Proxy de Aplicativo Web e os Serviços de Federação do Active Directory – Servidor de Relatórios do Power BI

Este artigo descreve como usar o WAP (Proxy de Aplicativo Web) e os AD FS (Serviços de Federação do Active Directory) para se conectar ao Servidor de Relatórios do Power BI e ao SSRS (SQL Server Reporting Services) 2016 e posterior. Por meio dessa integração, os usuários que estiverem fora da rede corporativa podem acessar o Servidor de Relatórios do Power BI e os relatórios do Reporting Services em seus navegadores clientes e serão protegidos pela pré-autenticação dos AD FS. Para os aplicativos móveis do Power BI, você também precisa [configurar o OAuth para se conectar ao Servidor de Relatórios do Power BI e ao SSRS](../consumer/mobile/mobile-oauth-ssrs.md).

## <a name="prerequisites"></a>Pré-requisitos

### <a name="domain-name-services-dns-configuration"></a>Configuração DNS (Serviços de nomes de domínio)

- Determine a URL pública à qual o usuário se conectará. Ela será semelhante a este exemplo: `https://reports.contosolab.com`.
- Configure o registro DNS para o nome do host, `reports.contosolab.com`, por exemplo, para apontar para o endereço IP público do servidor WAP (Proxy de Aplicativo Web).
- Configure um registro DNS público para seu servidor AD FS. Por exemplo, talvez você tenha configurado o servidor AD FS com a seguinte URL: `https://adfs.contosolab.com`.
- Configure o registro DNS para apontar para o endereço IP público do servidor WAP (Proxy de Aplicativo Web), como `adfs.contosolab.com`, por exemplo. Ele é publicado como parte do aplicativo WAP.

### <a name="certificates"></a>Certificados

É necessário configurar certificados para o aplicativo WAP e para o servidor AD FS. Esses certificados devem fazer parte de uma autoridade de certificado válida que seus dispositivos reconheçam.

## <a name="1-configure-the-report-server"></a>1. Configurar o servidor de relatório

Precisamos garantir que tenhamos um SPN (Nome da Entidade de Serviço) válido. O SPN válido permite que a autenticação Kerberos adequada ocorra e habilita o servidor de relatório para negociar a autenticação.

### <a name="service-principal-name-spn"></a>SPN (Nome da Entidade de Serviço)

O SPN é um identificador exclusivo para um serviço que usa a autenticação Kerberos. Certifique-se de ter um SPN HTTP apropriado presente para o servidor de relatório.

Para obter informações sobre como configurar o SPN (Nome da Entidade de Serviço) adequado para seu servidor de relatório, consulte [Registrar um SPN (Nome da Entidade de Serviço) para um servidor de relatório](https://docs.microsoft.com/sql/reporting-services/report-server/register-a-service-principal-name-spn-for-a-report-server).

### <a name="enabling-negotiate-authentication"></a>Habilitando a autenticação do tipo negociar

Para habilitar um servidor de relatório para usar a autenticação Kerberos, é necessário configurar o Tipo de Autenticação do servidor de relatório para ser RSWindowsNegotiate. Configure-o no arquivo rsreportserver.config.

```
<AuthenticationTypes>

    <RSWindowsNegotiate />

    <RSWindowsNTLM />

</AuthenticationTypes>
```

Para obter mais informações, consulte [Modify a Reporting Services Configuration File (Modificar um arquivo de configuração de serviços)](https://docs.microsoft.com/sql/reporting-services/report-server/modify-a-reporting-services-configuration-file-rsreportserver-config) e [Configurar a Autenticação do Windows no servidor de relatório](https://docs.microsoft.com/sql/reporting-services/security/configure-windows-authentication-on-the-report-server).

## <a name="2-configure-active-directory-federation-services-ad-fs"></a>2. Configurar o AD FS (Serviços de Federação do Active Directory)

É necessário configurar o AD FS em um servidor do Windows 2016 em seu ambiente. A configuração pode ser feita por meio do Gerenciador do Servidor e selecionando Adicionar Funções e Recursos em Gerenciar. Para obter mais informações, consulte [Serviços de Federação do Active Directory](https://docs.microsoft.com/windows-server/identity/active-directory-federation-services).

Conclua estas etapas no servidor AD FS usando o aplicativo de Gerenciamento do AD FS.

1. Clique com o botão direito do mouse em **Confianças da Terceira Parte Confiável** > **Adicionar Confianças da Terceira Parte Confiável**.

    ![Adicionar Confianças da Terceira Parte Confiável](media/connect-adfs-wap-report-server/report-server-adfs-add-relying-party-trust.png)

2. Siga as etapas do assistente **Adicionar Objeto de Confiança de Terceira Parte Confiável**.

    Escolha a opção **Sem reconhecimento de declaração** para usar a Segurança integrada do Windows como o mecanismo de autenticação.

    ![Bem-vindo ao assistente Adicionar Objeto de Confiança de Terceira Parte Confiável](media/connect-adfs-wap-report-server/report-server-adfs-add-relying-party-trust-welcome.png)

    Informe o nome desejado em **Especificar Nome para Exibição** e selecione **Avançar**.
    Adicione o identificador do objeto de confiança de terceira parte confiável: `<ADFS\_URL>/adfs/services/trust`

    Por exemplo: `https://adfs.contosolab.com/adfs/services/trust`

    ![Servidor de Relatórios](media/connect-adfs-wap-report-server/report-server-adfs-configure-identifiers.png)

    Escolha a **Política de Controle de Acesso** que atende às necessidades da sua organização e selecione **Avançar**.

    ![Escolha o controle de acesso](media/connect-adfs-wap-report-server/report-server-adfs-choose-access-control.png)
    
    Selecione **Avançar** e **Concluir** para terminar o assistente **Adicionar Objeto de Confiança de Terceira Parte Confiável**.

    Ao terminar, as propriedades de Confianças da Terceira Parte Confiável devem ser semelhantes às apresentadas a seguir.

    ![Confianças da Terceira Parte Confiável](media/connect-adfs-wap-report-server/report-server-adfs-relying-party-trusts.png)

## <a name="3-configure-web-application-proxy-wap"></a>3. Configurar o WAP (Proxy do Aplicativo Web)

Habilite a função do Windows Proxy do Aplicativo Web (Função) em um servidor no seu ambiente. Ele deve estar em um servidor Windows 2016. Para obter mais informações, consulte [Proxy de aplicativo Web no Windows Server 2016](https://docs.microsoft.com/windows-server/remote/remote-access/web-application-proxy/web-application-proxy-windows-server) e [Publicar aplicativos usando pré-autenticação do AD FS](https://docs.microsoft.com/windows-server/remote/remote-access/web-application-proxy/Publishing-Applications-using-AD-FS-Preauthentication).

### <a name="configure-constrained-delegation"></a>Configurar a delegação restrita

Para fazer a transição da Autenticação de formulários para a autenticação do Windows, é necessário usar a delegação restrita com transição de protocolos. Essa etapa faz parte da configuração do Kerberos. Já definimos o SPN do servidor de relatório na configuração do servidor de relatório.

É necessário configurar a delegação restrita na conta do computador do servidor WAP dentro do Active Directory. Talvez seja necessário trabalhar com um administrador de domínio se você não tiver direitos no Active Directory.

Para configurar a delegação restrita, siga estas etapas.

1. Em um computador com as ferramentas do Active Directory instaladas, abra **Usuários e Computadores do Active Directory**.
2. Localize a conta do computador do servidor WAP. Por padrão, ela estará no contêiner **Computadores**.
3. Clique com botão direito do mouse no servidor WAP e acesse **Propriedades**.
4. Na guia **Delegação**, selecione **Confiar no computador para delegação apenas a serviços especificados** e **Usar qualquer protocolo de autenticação**.

    ![Confiar neste computador](media/connect-adfs-wap-report-server/report-server-adfs-delegation-use-any.png)

1. Esta opção configura a delegação restrita para essa conta do computador do servidor WAP. Em seguida, é necessário especificar os serviços aos quais este computador tem permissão para delegar.
2. Selecione **Adicionar** na caixa de serviços.

    ![Adicionar objeto de confiança do AD FS](media/connect-adfs-wap-report-server/report-server-adfs-trust-add.png)

1. Selecione **Usuários ou Computadores**.
2. Informe a conta de serviço que você está usando para o servidor de relatórios. Essa conta é a mesma que você usou para adicionar o SPN HTTP na seção anterior [configuração do servidor de relatório](#1-configure-the-report-server). 

3. Selecione o SPN HTTP para o servidor de relatório e selecione **OK**.

    > [!NOTE]
    > Você pode ver apenas o SPN NetBIOS. Na verdade, ele selecionará os SPNs NetBIOS e FQDN se ambos existirem.

1. Ao marcar a caixa de seleção **Expandido**, o resultado deve ter a seguinte aparência.

    ![Propriedades WAP](media/connect-adfs-wap-report-server/report-server-wap-properties.png)

### <a name="add-wap-application"></a>Adicionar aplicativo WAP

1. No servidor Proxy de Aplicativo Web, abra o console **Gerenciamento de Acesso Remoto** e selecione **Proxy de Aplicativo Web** no painel de Navegação. 

2. No painel **Tarefas**, selecione**Publicar**.

2. Na página de Boas-vindas, selecione **Próximo**.

    ![Bem-vindo à publicação](media/connect-adfs-wap-report-server/report-server-welcome-publish-new-app-wizard.png)

3. Na página **Pré-autenticação**, selecione **Serviços de Federação do Active Directory (AD FS)** e **Avançar**.

    ![Pré-autorização](media/connect-adfs-wap-report-server/report-server-preauthentication-new-app-wizard.png)

4. Selecione a pré-autenticação **Web e MSOFBA**, pois vamos configurar apenas o acesso do navegador ao servidor de relatório e não o acesso ao aplicativo móvel.

    ![Clientes com suporte](media/connect-adfs-wap-report-server/report-server-supported-clients-publish-new-app-wizard.png)

5. Adicione a **Terceira Parte Confiável** que criamos no servidor de AD FS, como mostrado abaixo, e depois selecione **Avançar**.

    ![Publicação de Terceira Parte Confiável](media/connect-adfs-wap-report-server/report-server-relying-party-publish-new-app-wizard.png)

6. Na seção **URL Externa**, coloque a URL publicamente acessível configurada no servidor WAP. Adicione a URL configurada com o servidor de relatório (Configuration Manager do servidor de relatório), como mostrado abaixo na seção **URL do Servidor Back-end**. Adicione o SPN do servidor de relatório na seção **SPN do servidor back-end**.

    ![Configurações de publicação](media/connect-adfs-wap-report-server/report-server-publishing-settings-new-app-wizard.png)

7. Selecione **Avançar** e **Publicar**.
8. Execute o comando PowerShell a seguir para validar a configuração WAP.

    ```
    Get-WebApplicationProxyApplication "PBIRSBrowser" | FL
    ```

    ![Comando do PowerShell](media/connect-adfs-wap-report-server/report-server-powershell-get-webapplication.png)

## <a name="connect-to-the-report-server-through-the-browser"></a>Conectar-se ao servidor de relatório por meio do navegador

Em seguida, você pode acessar a URL do WAP público, por exemplo, `https://reports.contosolab.com/ReportServer` para o serviço Web e `https://reports.contosolab.com/Reports` para o portal da Web do navegador. Depois de ser autenticado com êxito, você poderá visualizar os relatórios.

![Entrada do AD FS](media/connect-adfs-wap-report-server/report-server-adfs-sign-in.png)

## <a name="next-steps"></a>Próximas etapas

* [Configurar o OAuth para se conectar ao Servidor de Relatórios do Power BI e ao SSRS](../consumer/mobile/mobile-oauth-ssrs.md)
*[O que é o Servidor de Relatórios do Power BI?](get-started.md)  

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)

