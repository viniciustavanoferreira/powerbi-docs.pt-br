---
title: Solucionar problemas de gateways – Power BI
description: Este artigo fornece maneiras de solucionar problemas com o gateway de dados local e o Power BI. Apresenta as possíveis soluções alternativas para problemas conhecidos, bem como ferramentas para ajudá-lo.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 07/15/2019
LocalizationGroup: Gateways
ms.openlocfilehash: 6a846a0588aff7dd52e725bfed1435276730e2a3
ms.sourcegitcommit: d74aca333595beaede0d71ba13a88945ef540e44
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/03/2019
ms.locfileid: "68757703"
---
# <a name="troubleshoot-gateways---power-bi"></a>Solucionar problemas de gateways – Power BI

[!INCLUDE [gateway-rewrite](includes/gateway-rewrite.md)]

Este artigo aborda alguns problemas comuns ao usar o gateway de dados local com o Power BI. Se você encontrar um problema que não está listado aqui, poderá usar o site da [Comunidade](http://community.powerbi.com) do Power BI. Ou crie um [tíquete de suporte](http://powerbi.microsoft.com/support).

## <a name="configuration"></a>Configuração

### <a name="error-power-bi-service-reported-local-gateway-as-unreachable-restart-the-gateway-and-try-again"></a>Erro: O serviço do Power BI relatou o gateway local como inacessível. Reinicie o gateway e tente novamente.

No final da configuração, o serviço do Power BI é chamado novamente para validar o gateway. O serviço do Power BI não relata o gateway como dinâmico. Reiniciar o serviço Windows pode permitir que a comunicação seja bem-sucedida. Para obter mais informações, você pode coletar e examinar os logs, conforme descrito em [Coletar logs do aplicativo de gateway de dados local](/data-integration/gateway/service-gateway-tshoot#collect-logs-from-the-on-premises-data-gateway-app).

## <a name="data-sources"></a>Fontes de dados

### <a name="error-unable-to-connect-details-invalid-connection-credentials"></a>Erro: Não é possível estabelecer conexão. Detalhes: "Credenciais de conexão inválidas"

Em **Mostrar detalhes**, a mensagem de erro recebida da fonte de dados é exibida. Para o SQL Server, você verá algo semelhante ao seguinte:

    Login failed for user 'username'.

Verifique se você tem o nome de usuário correto e a senha. Além disso, verifique se essas credenciais podem se conectar à fonte de dados com êxito. Verifique se a conta que está sendo usada corresponde ao método de autenticação.

### <a name="error-unable-to-connect-details-cannot-connect-to-the-database"></a>Erro: Não é possível estabelecer conexão. Detalhes: "Não é possível se conectar ao banco de dados"

Você conseguiu conectar ao servidor, mas não ao banco de dados fornecido. Verifique o nome do banco de dados e se as credenciais do usuário têm a permissão apropriada para acessar esse banco de dados.

Em **Mostrar detalhes**, a mensagem de erro recebida da fonte de dados é exibida. Para o SQL Server, você verá algo semelhante ao seguinte:

    Cannot open database "AdventureWorks" requested by the login. The login failed. Login failed for user 'username'.

### <a name="error-unable-to-connect-details-unknown-error-in-data-gateway"></a>Erro: Não é possível estabelecer conexão. Detalhes: "Erro desconhecido no gateway de dados"

Esse erro pode ocorrer por diferentes motivos. Não se esqueça de validar que você pode se conectar à fonte de dados do computador que hospeda o gateway. Essa situação pode ocorrer devido ao fato de o servidor não estar acessível.

Em **Mostrar detalhes**, é possível ver um código de erro **DM_GWPipeline_UnknownError**.

Você também pode examinar os **Logs de Eventos** > **Logs de Aplicativos e Serviços** > **Serviço do gateway de dados local** para obter mais detalhes.

### <a name="error-we-encountered-an-error-while-trying-to-connect-to-server-details-we-reached-the-data-gateway-but-the-gateway-cant-access-the-on-premises-data-source"></a>Erro: Erro: encontramos um erro ao tentar conectar-se com o \<servidor\>. Detalhes: "Acessamos o gateway de dados, mas o gateway não pode acessar a fonte de dados local."

Você não conseguiu se conectar à fonte de dados especificada. Certifique-se de validar as informações fornecidas para essa fonte de dados.

Em **Mostrar detalhes**, é possível ver um código de erro de **DM_GWPipeline_Gateway_DataSourceAccessError**.

Se a mensagem de erro subjacente for semelhante à seguinte, isso significa que a conta que você está usando para a fonte de dados não é um administrador do servidor para essa instância do Analysis Services. Para obter mais informações, confira [Conceder direitos de administrador de servidor a uma instância de Analysis Services](https://docs.microsoft.com/sql/analysis-services/instances/grant-server-admin-rights-to-an-analysis-services-instance).

    The 'CONTOSO\account' value of the 'EffectiveUserName' XML for Analysis property is not valid.

Caso a mensagem de erro subjacente seja semelhante à seguinte, isso pode indicar que a conta de serviço do Analysis Services pode não ter o atributo de diretório TGGAU ([token-groups-global-and-universal](https://msdn.microsoft.com/library/windows/desktop/ms680300.aspx)).

    The username or password is incorrect.

Os domínios com acesso de compatibilidade anterior ao Windows 2000 têm o atributo TGGAU habilitado. A maioria dos domínios recém-criados não habilita esse atributo por padrão. Para obter mais informações, confira [Alguns aplicativos e APIs exigem acesso às informações de autorização em objetos da conta](https://support.microsoft.com/kb/331951).

Para confirmar se o atributo está habilitado, siga estas etapas.

1. Conecte-se ao computador do Analysis Services no SQL Server Management Studio. Nas propriedades de conexão Avançada, inclua EffectiveUserName para o usuário em questão e veja se essa adição reproduz o erro.
2. Você pode usar a ferramenta dsacls do Active Directory para validar se o atributo está listado. Essa é uma ferramenta encontrada em um controlador de domínio. É necessário saber o que é o nome de domínio diferenciado para a conta e passá-lo para a ferramenta.

        dsacls "CN=John Doe,CN=UserAccounts,DC=contoso,DC=com"

    Você deseja ver algo semelhante ao mostrado a seguir nos resultados:

            Allow BUILTIN\Windows Authorization Access Group
                                          SPECIAL ACCESS for tokenGroupsGlobalAndUniversal
                                          READ PROPERTY

Para corrigir esse problema, é necessário habilitar o TGGAU na conta usada para o serviço Windows do Analysis Services.

#### <a name="another-possibility-for-the-username-or-password-is-incorrect"></a>Outra possibilidade para “O nome de usuário ou senha está incorreto”.

Esse erro também poderá ser causado se o servidor do Analysis Services estiver em um domínio diferente dos usuários e não houver uma relação de confiança bidirecional estabelecida.

Trabalhe com seus administradores de domínio para verificar a relação de confiança entre os domínios.

#### <a name="unable-to-see-the-data-gateway-data-sources-in-the-get-data-experience-for-analysis-services-from-the-power-bi-service"></a>Não é possível ver as fontes de dados do gateway de dados na experiência Obter dados do Analysis Services por meio do serviço do Power BI

Confira se sua conta está listada na guia **Usuários** da fonte de dados na configuração do gateway. Se não tiver acesso ao gateway, verifique com o administrador do gateway e solicite a verificação. Somente as contas na lista **Usuários** podem ver a fonte de dados relacionada na lista do Analysis Services.

### <a name="error-you-dont-have-any-gateway-installed-or-configured-for-the-data-sources-in-this-dataset"></a>Erro: Você não tem nenhum gateway instalado ou configurado para as fontes de dados neste conjunto de dados.

Verifique se você adicionou uma ou mais fontes de dados para o gateway, conforme está descrito em [Adicionar uma fonte de dados](service-gateway-data-sources.md#add-a-data-source). Se o gateway não aparecer no portal de administração em **Gerenciar gateways**, limpe o cache do navegador ou saia do serviço e entre novamente.

## <a name="datasets"></a>Conjuntos de dados

### <a name="error-there-is-not-enough-space-for-this-row"></a>Erro: Não há espaço suficiente para esta linha.

Esse erro ocorrerá se você tiver uma única linha com um tamanho maior que 4 MB. Determine qual linha é proveniente da fonte de dados e tente filtrá-la ou reduza seu tamanho.

### <a name="error-the-server-name-provided-doesnt-match-the-server-name-on-the-sql-server-ssl-certificate"></a>Erro: O nome do servidor fornecido não corresponde ao nome do servidor no certificado SSL do SQL Server.

Esse erro pode ocorrer quando o nome comum do certificado é para o FQDN (nome de domínio totalmente qualificado) do servidor, mas você somente forneceu o nome NetBIOS do servidor. Essa situação causa uma incompatibilidade para o certificado. Para resolver esse problema, crie o nome do servidor na fonte de dados do gateway e no arquivo PBIX para usar o FQDN do servidor.

### <a name="error-you-dont-see-the-on-premises-data-gateway-present-when-you-configure-scheduled-refresh"></a>Erro: Você não vê o gateway de dados local presente ao configurar a atualização agendada.

Alguns cenários diferentes podem ser responsáveis por esse erro:

- O nome do servidor e do banco de dados não corresponde ao que foi inserido no Power BI Desktop e a fonte de dados configurada para o gateway. Esses nomes devem ser iguais. Eles não diferenciam maiúsculas de minúsculas.
- Sua conta não está listada na guia **Usuários** da fonte de dados na configuração do gateway. Você precisa ser adicionado a essa lista pelo administrador do gateway.
- O arquivo do Power BI Desktop contém dados de várias fontes e nem todas as fontes de dados estão configuradas com o gateway. É necessário ter cada fonte de dados definida com o gateway para que ele seja exibido na atualização agendada.

### <a name="error-the-received-uncompressed-data-on-the-gateway-client-has-exceeded-the-limit"></a>Erro: Os dados descompactados recebidos no cliente de gateway excederam o limite.

A limitação exata é de 10 GB de dados descompactados por tabela. Se você estiver tendo esse problema, há boas opções para otimizá-lo e evitá-lo. Em especial, reduza o uso de valores de cadeia de caracteres muito constantes e longos e, em vez disso, use uma chave normalizada. Ou remover a coluna, se ela não estiver em uso, ajuda.

## <a name="reports"></a>Relatórios

### <a name="error-report-could-not-access-the-data-source-because-you-do-not-have-access-to-our-data-source-via-an-on-premises-data-gateway"></a>Erro: O relatório não pôde acessar a fonte de dados porque você não tem acesso à nossa fonte de dados por meio de um gateway de dados local.

Esse erro geralmente é causado por um dos motivos a seguir:

- As informações da fonte de dados não correspondem às que estão no conjunto de dados subjacente. O servidor e o nome do banco de dados precisam corresponder à fonte de dados definida para o gateway de dados local e às informações fornecidas no Power BI Desktop. Se você usar um endereço IP no Power BI Desktop, a fonte de dados do gateway de dados local também precisará usar um endereço IP.
- Não há nenhuma fonte de dados disponível em nenhum gateway de sua organização. É possível configurar a fonte de dados em um gateway de dados local novo ou existente.

### <a name="error-data-source-access-error-please-contact-the-gateway-administrator"></a>Erro: Erro de acesso à fonte de dados. Entre em contato com o administrador do gateway.

Se este relatório usar uma conexão dinâmica do Analysis Services, talvez você tenha problemas ao passar um valor para EffectiveUserName que não seja válido ou que não tenha permissões no computador do Analysis Services. Normalmente, um problema de autenticação ocorre devido ao fato de que o valor passado para EffectiveUserName não corresponde a um nome UPN local.

Para confirmar o nome de usuário efetivo, siga estas etapas.

1. Encontre o nome de usuário efetivo nos [logs do gateway](/data-integration/gateway/service-gateway-tshoot#collect-logs-from-the-on-premises-data-gateway-app).
2. Depois de obter o valor que está sendo passado, valide se ele está correto. Se ele for seu usuário, será possível usar o comando a seguir em um prompt de comando para ver o UPN. O UPN tem a aparência de um endereço de email.

        whoami /upn

Se preferir, é possível ver o que o Power BI obtém do Azure Active Directory.

1. Navegue até [https://developer.microsoft.com/graph/graph-explorer](https://developer.microsoft.com/graph/graph-explorer).
2. Selecione **Entrar** no canto superior direito.
3. Execute a consulta a seguir. Você verá uma resposta JSON bem grande.

        https://graph.windows.net/me?api-version=1.5
4. Procure **userPrincipalName**.

Se o UPN do Azure Active Directory não corresponder ao UPN local do Active Directory, você poderá usar o recurso [Mapear nomes de usuário](service-gateway-enterprise-manage-ssas.md#map-user-names-for-analysis-services-data-sources) para substituí-lo por um valor válido. Ou será possível trabalhar com seu administrador de locatários ou com o administrador local do Active Directory para alterar o UPN.

## <a name="kerberos"></a>Kerberos

Se o servidor de banco de dados subjacente e o gateway de dados local não estiverem configurados adequadamente para a [delegação restrita de Kerberos](service-gateway-sso-kerberos.md), habilite o [log detalhado](/data-integration/gateway/service-gateway-performance#slow-performing-queries) no gateway. Em seguida, investigue com base nos erros ou rastreamentos nos arquivos de log do gateway como um ponto de partida para a solução de problemas. Para coletar os logs de gateway para exibição, confira [Coletar logs do aplicativo de gateway de dados local](/data-integration/gateway/service-gateway-tshoot#collect-logs-from-the-on-premises-data-gateway-app).

### <a name="impersonationlevel"></a>ImpersonationLevel

O ImpersonationLevel está relacionado à configuração de SPN ou à configuração de política local.

```
[DataMovement.PipeLine.GatewayDataAccess] About to impersonate user DOMAIN\User (IsAuthenticated: True, ImpersonationLevel: Identification)
```

**Solução**

Execute estas etapas para resolver o problema.

1. Configure um SPN para o gateway local.
2. Configure a delegação restrita em seu Active Directory.

### <a name="failedtoimpersonateuserexception-failed-to-create-windows-identity-for-user-userid"></a>FailedToImpersonateUserException: Falha ao criar a identidade do Windows para a ID de usuário

O FailedToImpersonateUserException ocorrerá se você não puder representar em nome de outro usuário. Esse erro também poderá ocorrer se a conta que você está tentando representar for de um domínio diferente do domínio no qual o domínio do serviço de gateway está. Essa é uma limitação.

**Solução**

* Verifique se a configuração está correta de acordo com as etapas na seção “ImpersonationLevel” anterior.
* Verifique se a ID de usuário que ele está tentando representar é de uma conta válida do Active Directory.

### <a name="general-error-1033-error-while-you-parse-the-protocol"></a>Erro geral: erro 1033 ao analisar o protocolo

Você receberá o erro 1033 quando sua ID externa configurada no SAP HANA não corresponder à credencial se o usuário for representado usando o UPN (alias@domain.com). Nos logs, você vê o “UPN Original 'alias@domain.com' substituído por um novo UPN 'alias@domain.com'” na parte superior dos logs de erro, conforme mostrado aqui:

```
[DM.GatewayCore] SingleSignOn Required. Original UPN 'alias@domain.com' replaced with new UPN 'alias@domain.com.'
```

**Solução**

* O SAP HANA exige que o usuário representado use o atributo sAMAccountName no Active Directory (alias do usuário). Se este atributo não estiver correto, você verá o erro 1033.

    ![sAMAccount](media/service-gateway-onprem-tshoot/sAMAccount.png)

* Nos logs, você vê sAMAccountName (alias) e não o UPN, que é o alias seguido pelo domínio (alias@doimain.com).

    ![sAMAccount](media/service-gateway-onprem-tshoot/sAMAccount-02.png)

```xml
      <setting name="ADUserNameReplacementProperty" serializeAs="String">
        <value>sAMAccount</value>
      </setting>
      <setting name="ADServerPath" serializeAs="String">
        <value />
      </setting>
      <setting name="CustomASDataSource" serializeAs="String">
        <value />
      </setting>
      <setting name="ADUserNameLookupProperty" serializeAs="String">
        <value>AADEmail</value>
```

### <a name="sap-aglibodbchdb-dllhdbodbc-communication-link-failure-10709-connection-failed-rte-1-kerberos-error-major-miscellaneous-failure-851968-minor-no-credentials-are-available-in-the-security-package"></a>[SAP AG][LIBODBCHDB DLL][HDBODBC] Falha de vínculo de comunicação:-10709 Falha de conexão (RTE:[-1] Erro do Kerberos. Principal: "Falhas diversas [851968]." Secundária: "Nenhuma credencial disponível no pacote de segurança.”

Você receberá a mensagem de erro “-10709 Falha na conexão” se sua delegação não estiver configurada corretamente no Active Directory.

**Solução**

* Certifique-se de que você tenha o servidor SAP Hana na guia Delegação no Active Directory para a conta de serviço do gateway.

   ![Guia Delegação](media/service-gateway-onprem-tshoot/delegation-in-AD.png)

## <a name="refresh-history"></a>Histórico de atualização

Quando você usa o gateway para uma atualização agendada, **Histórico de atualização** pode ajudá-lo a ver quais erros ocorreram. Ele também poderá fornecer dados úteis se você precisar criar uma solicitação de suporte. É possível exibir atualizações agendadas e sob demanda. As etapas a seguir mostram como você pode acessar o histórico de atualização.

1. No painel de navegação do Power BI, em **Conjuntos de Dados**, selecione um conjunto de dados. Abra o menu e selecione **Agendar atualização**.

    ![Como selecionar a atualização agendada](media/service-gateway-onprem-tshoot/scheduled-refresh.png)

2. Em **Configurações de...** &gt; **Agendar atualização**, selecione **Histórico de atualização**.

    ![Selecionar histórico de atualização](media/service-gateway-onprem-tshoot/scheduled-refresh-2.png)

    ![Exibição do histórico de atualização](media/service-gateway-onprem-tshoot/refresh-history.png)

Para obter mais informações sobre solucionar problemas de cenários de atualização, confira [Solucionar problemas de cenários de atualização](refresh-troubleshooting-refresh-scenarios.md).

## <a name="fiddler-trace"></a>Rastreamento do Fiddler

[Fiddler](http://www.telerik.com/fiddler) é uma ferramenta gratuita da Telerik que monitora o tráfego HTTP. Você pode ver a parte de trás e frente com o serviço do Power BI do computador cliente. Essa lista de tráfego pode mostrar erros e outras informações relacionadas.

![Usando o rastreamento Fiddler](media/service-gateway-onprem-tshoot/fiddler.png)

## <a name="next-steps"></a>Próximas etapas

* [Solucionar problemas do gateway de dados local](/data-integration/gateway/service-gateway-tshoot)
* [Definir as configurações de proxy do gateway de dados local](/data-integration/gateway/service-gateway-proxy)  
* [Gerenciar sua fonte de dados – Analysis Services](service-gateway-enterprise-manage-ssas.md)  
* [Gerenciar sua fonte de dados – SAP HANA](service-gateway-enterprise-manage-sap.md)  
* [Gerenciar sua fonte de dados – SQL Server](service-gateway-enterprise-manage-sql.md)  
* [Gerenciar sua fonte de dados – Importar/atualização agendada](service-gateway-enterprise-manage-scheduled-refresh.md)  

Mais perguntas? Experimente a [Comunidade do Power BI](http://community.powerbi.com/).
