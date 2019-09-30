---
title: Configurar SSO – Kerberos
description: Configure seu gateway com o Kerberos para habilitar o SSO do Power BI para fontes de dados locais
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 07/15/2019
LocalizationGroup: Gateways
ms.openlocfilehash: 9958059fcf0d86323fc95f44f6fcfcb08fe7b52b
ms.sourcegitcommit: 7a0ce2eec5bc7ac8ef94fa94434ee12a9a07705b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/18/2019
ms.locfileid: "71100500"
---
# <a name="configure-kerberos-based-sso-from-power-bi-service-to-on-premises-data-sources"></a>Configurar o SSO baseado em Kerberos do serviço do Power BI para fontes de dados locais

Use a [delegação restrita de Kerberos](/windows-server/security/kerberos/kerberos-constrained-delegation-overview) para habilitar a conectividade ininterrupta de SSO. Habilitar SSO torna mais fácil para relatórios e dashboards do Power BI atualizar os dados de fontes locais.

Vários itens devem ser configurados para que a delegação restrita de Kerberos funcione corretamente, incluindo os _SPNs_ (nomes das entidades de serviço) e as configurações de delegação nas contas de serviço.

### <a name="prerequisite-1-install-and-configure-the-microsoft-on-premises-data-gateway"></a>Pré-requisito 1: Instalar e configurar o gateway de dados local da Microsoft

O gateway de dados local é compatível com atualização in-loco e com o _controle das configurações_ de gateway existentes.

### <a name="prerequisite-2-run-the-gateway-windows-service-as-a-domain-account"></a>Pré-requisito 2: executar o serviço Windows do gateway como uma conta de domínio

Em uma instalação padrão, o gateway é executado como uma conta de serviço do computador local (especificamente, _NT Service\PBIEgwService_), conforme mostrado na imagem a seguir:

![Captura de tela da conta de serviço](media/service-gateway-sso-kerberos/service-account.png)

Para habilitar a delegação restrita de Kerberos, o gateway precisa ser executado como uma conta de domínio, a menos que a instância do Azure AD (Azure Active Directory) já esteja sincronizada com a instância do Active Directory local (usando o Azure AD DirSync/Connect). Para alternar para uma conta de domínio, confira [Mudar a conta de serviço de gateway](/data-integration/gateway/service-gateway-service-account).

> [!NOTE]
> Se o Microsoft Azure Active Directory Connect está configurado e as contas de usuário estão sincronizadas, o serviço do gateway não precisa executar pesquisas no Microsoft Azure Active Directory local no tempo de execução. Ao invés disso, basta usar o SID do serviço local para que o serviço de gateway conclua toda a configuração necessária no Microsoft Azure Active Directory. As etapas de configuração da delegação restrita de Kerberos descritas neste artigo são as mesmas que as etapas de configuração exigidas no contexto do Microsoft Azure Active Directory. Elas são simplesmente aplicadas ao objeto de computador do gateway (conforme identificado pelo SID do serviço local) no Microsoft Azure AD em vez da conta de domínio.

### <a name="prerequisite-3-have-domain-admin-rights-to-configure-spns-setspn-and-kerberos-constrained-delegation-settings"></a>Pré-requisito 3: ter direitos de administrador de domínio para configurar definições de SPNs (SetSPN) e da delegação restrita de Kerberos

Não é recomendado que um administrador de domínio conceda temporária ou permanentemente direitos para outra pessoa configurar os SPNs e a delegação de Kerberos sem exigir que a pessoa tenha direitos de administrador de domínio. Na seção a seguir, abordaremos as etapas de configuração recomendadas mais detalhadamente.

## <a name="configure-kerberos-constrained-delegation-for-the-gateway-and-data-source"></a>Configurar a delegação restrita de Kerberos para o gateway e a fonte de dados

Como administrador de domínio, configure um SPN para a conta de domínio do serviço do gateway (se exigido) e defina as configurações de delegação na conta de domínio do serviço do gateway.

### <a name="configure-an-spn-for-the-gateway-service-account"></a>Configurar um SPN para a conta de serviço do gateway

Primeiro, determine se um SPN já foi criado para a conta de domínio usada como a conta de serviço do gateway:

1. Como administrador de domínio, inicialize **Usuários e Computadores do Active Directory**.

2. Clique com o botão direito do mouse no domínio, selecione **Localizar** e insira o nome da conta de serviço do gateway.

3. No resultado da pesquisa, clique com o botão direito do mouse na conta de serviço do gateway e selecione **Propriedades**.

4. Se a guia **Delegação** está visível na caixa de diálogo **Propriedades**, isso indica que já foi criado um SPN e é possível pular para [Decidir entre a delegação restrita de Kerberos padrão ou baseada em recursos](#decide-on-resource-based-or-standard-kerberos-constrained-delegation).

    Se não há uma guia **Delegação** na caixa de diálogo **Propriedades**, crie manualmente um SPN na conta para habilitá-la. Use a [ferramenta setspn](https://technet.microsoft.com/library/cc731241.aspx) fornecida com o Windows (é necessário ter direitos de administrador de domínio para criar o SPN).

    Por exemplo, imagine que a conta de serviço do gateway seja **Contoso\GatewaySvc** e o nome do computador com o serviço do gateway em execução seja **MyGatewayMachine**. Para definir o SPN para a conta de serviço do gateway, é preciso executar o seguinte comando:

    ![Imagem do comando de definição do SPN](media/service-gateway-sso-kerberos/set-spn.png)

    Você também pode definir o SPN usando o snap-in Usuários e Computadores do Active Directory do MMC (Console de Gerenciamento Microsoft).

### <a name="decide-on-resource-based-or-standard-kerberos-constrained-delegation"></a>Decidir entre a delegação restrita de Kerberos padrão ou baseada em recursos

As definições de delegação podem ser configuradas _tanto_ para delegação restrita de Kerberos baseada em recursos, quanto para a delegação restrita de Kerberos padrão. Use a delegação baseada em recursos se sua fonte de dados pertence a um domínio diferente daquele do gateway, mas observe que essa abordagem exige o Windows Server 2012 ou posterior. Confira a [página de visão geral sobre a delegação restrita de Kerberos](/windows-server/security/kerberos/kerberos-constrained-delegation-overview) para saber mais sobre as diferenças entre as duas abordagens à delegação.

 Depois de decidir qual abordagem você deseja usar, vá para a _seção_ [Configurar a conta de serviço do gateway para a delegação restrita de Kerberos padrão](#configure-the-gateway-service-account-for-standard-kerberos-constrained-delegation) _ou_ [Configurar a conta de serviço do gateway para a delegação restrita de Kerberos baseada em recursos ](#configure-the-gateway-service-account-for-resource-based-kerberos-constrained-delegation). Não preencha as duas subseções.

## <a name="configure-the-gateway-service-account-for-standard-kerberos-constrained-delegation"></a>Configurar a conta de serviço do gateway para delegação restrita de Kerberos padrão

> [!NOTE]
> Conclua as etapas nesta seção se quiser habilitar a delegação restrita de Kerberos padrão. Se quiser habilitar a delegação restrita de Kerberos baseada em recursos, execute as etapas na subseção [Configurar a conta de serviço do gateway para a delegação restrita de Kerberos baseada em recursos](#configure-the-gateway-service-account-for-resource-based-kerberos-constrained-delegation).

Agora defina as configurações de delegação para a conta de serviço do gateway. Há diversas ferramentas que podem ser usadas para realizar essas etapas. Aqui, usaremos Usuários e Computadores do Active Directory, que é um snap-in do MMC (Console de Gerenciamento Microsoft) para administrar e publicar informações no diretório. Ele está disponível nos controladores de domínio padrão, mas também pode ser habilitado pela configuração do Recurso do Windows em outros computadores.

Precisamos configurar a delegação restrita de Kerberos com o trânsito de protocolos. Com a delegação restrita, é preciso ser explícito sobre para quais serviços você deseja permitir que o gateway apresente credenciais delegadas. Por exemplo, somente o SQL Server ou o servidor SAP HANA aceita chamadas de delegação da conta de serviço do gateway.

Esta seção pressupõe que você já tenha configurado SPNs para as fontes de dados subjacentes (como SQL Server, SAP HANA, SAP BW, Teradata ou Spark). Para saber como configurar os SPNs do servidor de fonte de dados, confira a documentação técnica do respectivo servidor de banco de dados. Você também pode ver o título *Que SPN seu aplicativo exige?* na postagem no blog [Minha Lista de Verificação do Kerberos](https://techcommunity.microsoft.com/t5/SQL-Server-Support/My-Kerberos-Checklist-8230/ba-p/316160).

Nas etapas a seguir, vamos supor que haja um ambiente local com dois computadores: um gateway e um servidor de banco de dados que executa o SQL Server que já estava configurado para o SSO baseado em Kerberos. As etapas podem ser adotadas para uma das demais fontes de dados compatíveis, desde que a fonte de dados já tenha sido configurada para logon único baseado em Kerberos. Para este exemplo, vamos também supor as configurações e os nomes a seguir:

* Domínio do Active Directory (Netbios): Contoso
* Nome do computador do gateway: **MyGatewayMachine**
* Conta de serviço do gateway: **Contoso\GatewaySvc**
* Nome do computador da fonte de dados do SQL Server: **TestSQLServer**
* Conta de serviço da fonte de dados do SQL Server: **Contoso\SQLService**

Defina as configurações de delegação da seguinte maneira:

1. Com direitos de administrador de domínio, abra **Usuários e Computadores do Active Directory**.

2. Clique com o botão direito do mouse na conta de serviço do gateway (**Contoso\GatewaySvc**) e escolha **Propriedades**.

3. Selecione a guia **Delegação**.

4. Selecione **Confiar neste computador para delegação apenas a serviços especificados** > **Usar qualquer protocolo de autenticação**.

5. Em **Serviços aos quais esta conta pode apresentar credenciais delegadas**, selecione **Adicionar**.

6. Na nova caixa de diálogo, selecione **Usuários ou Computadores**.

7. Insira a conta de serviço para a fonte de dados, por exemplo, uma fonte de dados SQL Server pode ter uma conta de serviço como **Contoso\SQLService**. Depois que a conta tiver sido adicionada, selecione **OK**.

8. Selecione o SPN que você criou para o servidor de banco de dados. Em nosso exemplo, o SPN começa com **MSSQLSvc**. Se você tiver adicionado o SPN NetBIOS e o FQDN para o serviço de banco de dados, selecione ambos. Talvez você veja apenas um.

9. Selecione **OK**. Agora você verá o SPN na lista.

    ![Captura de tela da caixa de diálogo Propriedades do Conector de Gateway](media/service-gateway-sso-kerberos/gateway-connector-properties.png)

Agora, pule para [Conceder direitos de política local da conta de serviço do gateway no computador do gateway](#grant-the-gateway-service-account-local-policy-rights-on-the-gateway-machine) para continuar o processo de instalação.

## <a name="configure-the-gateway-service-account-for-resource-based-kerberos-constrained-delegation"></a>Configurar a conta de serviço do gateway para delegação restrita de Kerberos baseada em recursos

> [!NOTE]
> Conclua as etapas nesta seção se quiser habilitar a delegação restrita de Kerberos baseada em recursos. Se quiser habilitar a delegação restrita de Kerberos padrão, execute as etapas na subseção [Configurar a conta de serviço do gateway para a delegação restrita de Kerberos padrão](#configure-the-gateway-service-account-for-standard-kerberos-constrained-delegation).

Use a [delegação restrita de Kerberos baseada em recursos](/windows-server/security/kerberos/kerberos-constrained-delegation-overview) para habilitar a conectividade de logon único no Windows Server 2012 e versões posteriores, permitindo que os serviços de front-end e back-end estejam em domínios diferentes. Para que isso funcione, o domínio de serviço de back-end precisa confiar no domínio do serviço de front-end.

Nas etapas a seguir, suponhamos que haja um ambiente local com dois computadores em diferentes domínios: um gateway e um servidor de banco de dados que executa o SQL Server que já estava configurado para logon único baseado em Kerberos. As etapas podem ser adotadas para uma das demais fontes de dados compatíveis, desde que a fonte de dados já tenha sido configurada para logon único baseado em Kerberos. Para este exemplo, vamos também supor as configurações e os nomes a seguir:

* Nome do computador do gateway: **MyGatewayMachine**
* Conta de serviço do gateway: **ContosoFrontEnd\GatewaySvc**
* Nome do computador da fonte de dados do SQL Server: **TestSQLServer**
* Conta de serviço da fonte de dados do SQL Server: **ContosoBackEnd\SQLService**

Considerando os nomes e as configurações do exemplo, conclua as seguintes etapas de configuração:

1. No controlador de domínio para o domínio **ContosoFrontEnd**, verifique se não há configurações de delegação aplicadas à conta de serviço do gateway usando o snap-in **Usuários e Computadores do Active Directory** do MMC (Console de Gerenciamento Microsoft).

    ![Propriedades do conector de gateway](media/service-gateway-sso-kerberos-resource/gateway-connector-properties.png)

2. Usando o **Usuários e Computadores do Active Directory** no controlador de domínio para o domínio **ContosoBackEnd**, verifique se não há configurações de delegação aplicadas à conta de serviço do back-end. Além disso, verifique se o atributo **msDS-AllowedToActOnBehalfOfOtherIdentity** dessa conta também não está definido. Você pode encontrar esse atributo no **Editor de Atributos**, conforme mostrado na imagem a seguir:

    ![Propriedades do serviço do SQL](media/service-gateway-sso-kerberos-resource/sql-service-properties.png)

3. Crie um grupo em **Usuários e Computadores do Active Directory** no controlador de domínio para o domínio **ContosoBackEnd**. Adicione a conta de serviço do gateway a esse grupo, como mostrado na imagem a seguir. A imagem mostra um novo grupo chamado _ResourceDelGroup_ e a conta de serviço do gateway, **GatewaySvc**, adicionados a esse grupo.

    ![Propriedades do grupo](media/service-gateway-sso-kerberos-resource/group-properties.png)

4. Abra um prompt de comando e execute os seguintes comandos no controlador de domínio para o domínio **ContosoBackEnd** com a finalidade de atualizar o atributo **msDS-AllowedToActOnBehalfOfOtherIdentity** da conta de serviço do back-end:

    ```powershell
    $c = Get-ADGroup ResourceDelGroup
    Set-ADUser SQLService -PrincipalsAllowedToDelegateToAccount $c
    ```

5. Você pode verificar que a atualização será refletida na guia "Editor de atributo", nas propriedades da conta de serviço de back-end em **Usuários e computadores do Active Directory.**

## <a name="grant-the-gateway-service-account-local-policy-rights-on-the-gateway-machine"></a>Conceder direitos de política local da conta de serviço do gateway no computador do gateway

Por fim, no computador que executa o serviço do gateway (**MyGatewayMachine** em nosso exemplo), é necessário conceder à conta de serviço do gateway a política local **Representar um cliente após autenticação** e **Atuar como parte do sistema operacional (SeTcbPrivilege)** . Execute e verifique essa configuração com o Editor de Política de Grupo Local (**gpedit**).

1. No computador do gateway, execute: *gpedit.msc*.

2. Acesse **Política do Computador Local** > **Configuração do Computador** > **Configurações do Windows** > **Configurações de Segurança** > **Políticas Locais** > **Atribuição de Direitos do Usuário**.

    ![Captura de tela da estrutura de pastas da Política do Computador Local](media/service-gateway-sso-kerberos/user-rights-assignment.png)

3. Em **Atribuição de Direitos de Usuário**, na lista de políticas, selecione **Representar um cliente após a autenticação**.

    ![Captura de tela de Representar uma política de cliente](media/service-gateway-sso-kerberos/impersonate-client.png)

    Clique com o botão direito do mouse e abra **Propriedades**. Verifique a lista de contas. A lista deve incluir a conta de serviço do gateway (**Contoso\GatewaySvc**).

4. Em **Atribuição de Direitos de Usuário**, na lista de políticas, selecione **Atuar como parte do sistema operacional (SeTcbPrivilege)** . Verifique se a conta de serviço do gateway também está incluída na lista de contas.

5. Reinicie o processo do serviço do **gateway de dados local**.

### <a name="set-user-mapping-configuration-parameters-on-the-gateway-machine-if-required"></a>Definir parâmetros de configuração do mapeamento de usuário no computador do gateway, se necessário

Se você não tem o Microsoft Azure Active Directory Connect configurado, siga estas etapas para mapear um usuário do serviço do Power BI para um usuário local do Active Directory. Cada usuário do Active Directory mapeado dessa maneira precisa ter permissões de logon único para sua fonte de dados. Para saber mais, confira este [vídeo do Guy in a Cube](https://www.youtube.com/watch?v=NG05PG9aiRw).

1. Abra o arquivo de configuração do gateway principal, `Microsoft.PowerBI.DataMovement.Pipeline.GatewayCore.dll`. Por padrão, esse arquivo é armazenado em C:\Arquivos de Programas\On-premises data gateway.

1. Defina **ADUserNameLookupProperty** como um atributo do Active Directory não utilizado. Suponhamos que `msDS-cloudExtensionAttribute1` seja usado nas etapas a seguir, embora esse atributo esteja disponível apenas no Windows Server 2012 e posterior. Defina **ADUserNameReplacementProperty** como `SAMAccountName`. Salve o arquivo de configuração.

1. Na guia **Serviços** do Gerenciador de Tarefas, clique com o botão direito do mouse no serviço do gateway e selecione **Reiniciar**.

    ![Captura de tela da guia Serviços do Gerenciador de Tarefas](media/service-gateway-sso-kerberos/restart-gateway.png)

1. Para cada usuário do serviço do Power BI para o qual você deseja habilitar o SSO do Kerberos, defina a propriedade `msDS-cloudExtensionAttribute1` de um usuário local do Active Directory (com permissão de SSO para sua fonte de dados) como o nome de usuário completo do usuário do serviço do Power BI. Por exemplo, se você efetua login no serviço do Power BI como `test@contoso.com` e deseja mapear esse usuário para um usuário local do Active Directory com permissões de SSO, como `test@LOCALDOMAIN.COM`, defina o atributo `msDS-cloudExtensionAttribute1` de `test@LOCALDOMAIN.COM` como `test@contoso.com`.

É possível definir a propriedade `msDS-cloudExtensionAttribute1` usando o snap-in Usuários e Computadores do Active Directory do MMC (Console de Gerenciamento Microsoft).

1. Como administrador de domínio, inicie Usuários e Computadores do Active Directory, um snap-in do MMC.

1. Clique com o botão direito do mouse no domínio, selecione Localizar e digite o nome da conta do usuário local do Active Directory para o qual você deseja mapear.

1. Selecione a guia **Editor de Atributo**.

    Localize a propriedade `msDS-cloudExtensionAttribute1` e clique duas vezes nela. Defina o valor como o nome de usuário completo usado para fazer login no serviço do Power BI.

1. Selecione **OK**.

    ![Captura de tela da caixa de diálogo Editor de Atributos de Cadeia de Caracteres](media/service-gateway-sso-kerberos/edit-attribute.png)

1. Selecione **Aplicar**. Verifique se o valor correto foi definido na coluna **Valor**.

## <a name="complete-data-source-specific-configuration-steps"></a>Concluir as etapas de configuração específicas da fonte de dados

O SAP HANA e o SAP BW têm requisitos e pré-requisitos de configuração adicionais específicos para cada fonte de dados, e estes precisam ser atendidos antes de ser possível estabelecer uma conexão de logon único através do gateway com essas fontes de dados. Confira a [página de configurações do SAP HANA](service-gateway-sso-kerberos-sap-hana.md) e a [página de configurações do SAP BW – CommonCryptoLib (sapcrypto.dll)](service-gateway-sso-kerberos-sap-bw-commoncryptolib.md) para saber mais. Também é possível [configurar o SAP BW para uso com a biblioteca SNC gx64krb5](service-gateway-sso-kerberos-sap-bw-gx64krb.md). Porém, essa biblioteca não é recomendada pela Microsoft já que não é mais compatível com SAP. Você deve usar CommonCryptoLib _ou_ gx64krb5 como sua biblioteca SNC. Não realize estas etapas de configuração para as duas bibliotecas.

> [!NOTE]
> Outras bibliotecas SNC também podem funcionar no SSO do BW, mas não têm suporte oficial da Microsoft.

## <a name="run-a-power-bi-report"></a>Executar um relatório do Power BI

Depois de concluir todas as etapas de configuração, use a página **Gerenciar Gateway** no Power BI para configurar a fonte de dados que será usada para SSO. Se há vários gateways, escolha o gateway configurado para o SSO do Kerberos. Em seguida, em **Configurações Avançadas** da fonte de dados, verifique se a opção "Usar SSO via Kerberos para consultas de DirectQuery" está marcada.

![Captura de tela da opção Configurações avançadas](media/service-gateway-sso-kerberos/advanced-settings.png)

 Publique um relatório **baseado em DirectQuery** no Power BI Desktop. Esse relatório deve usar dados acessíveis para o usuário que é mapeado para o usuário do Azure Active Directory que entra no serviço do Power BI. Você deve usar o DirectQuery em vez de importar, devido a como a atualização funciona. Ao atualizar relatórios baseados em importação, o gateway usa as credenciais inseridas nos campos **Nome de usuário** e **Senha** de quando você criou a fonte de dados. Em outras palavras, o SSO do Kerberos **não** é usado. Além disso, ao publicar, não se esqueça de escolher o gateway configurado para SSO caso haja vários gateways. No serviço do Power BI, agora você deve ser capaz de atualizar o relatório ou criar um novo com base no conjunto de dados publicado.

Essa configuração funciona na maioria dos casos. No entanto, dependendo do ambiente, pode haver configurações diferentes com o Kerberos. Se o relatório ainda não for carregado, contate o administrador de domínio para investigar o caso. Se sua fonte de dados é SAP BW, também é possível consultar as seções de solução de problemas das páginas de configuração específicas da fonte de dados para [CommonCryptoLib](service-gateway-sso-kerberos-sap-bw-commoncryptolib.md#troubleshooting) e [gx64krb5 / gsskrb5](service-gateway-sso-kerberos-sap-bw-gx64krb.md#troubleshooting).

## <a name="next-steps"></a>Próximas etapas

Para obter mais informações sobre o **gateway de dados local** e o **DirectQuery**, confira os seguintes recursos:

* [O que é um gateway de dados local?](/data-integration/gateway/service-gateway-getting-started)
* [DirectQuery no Power BI](desktop-directquery-about.md)
* [Fontes de dados com suporte do DirectQuery](desktop-directquery-data-sources.md)
* [DirectQuery e SAP BW](desktop-directquery-sap-bw.md)
* [DirectQuery e SAP HANA](desktop-directquery-sap-hana.md)
