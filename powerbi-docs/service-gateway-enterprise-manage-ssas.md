---
title: Gerenciar sua fonte de dados – Analysis Services
description: Como gerenciar o gateway de dados local e as fontes de dados que pertencem ao gateway. Isso é para o Analysis Services em ambos o modo de tabela e o multidimensional.
author: arthiriyer
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 07/15/2019
ms.author: arthii
LocalizationGroup: Gateways
ms.openlocfilehash: ea6d4186d2f02665201f2161f50e06ad8f0f45a6
ms.sourcegitcommit: f77b24a8a588605f005c9bb1fdad864955885718
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2019
ms.locfileid: "74699396"
---
# <a name="manage-your-data-source---analysis-services"></a>Gerenciar sua fonte de dados – Analysis Services

[!INCLUDE [gateway-rewrite](includes/gateway-rewrite.md)]

Depois de [instalar o gateway de dados local](/data-integration/gateway/service-gateway-install), será necessário [adicionar fontes de dados](service-gateway-data-sources.md#add-a-data-source) que possam ser usadas com o gateway. Este artigo aborda como trabalhar com gateways e fontes de dados do SSAS (SQL Server Analysis Services) que são usadas para a atualização agendada ou para conexões dinâmicas.

Para saber mais sobre como configurar uma conexão dinâmica com o Analysis Services, [assista a este vídeo](https://www.youtube.com/watch?v=GPf0YS-Xbyo&feature=youtu.be).

> [!NOTE]
> Se você tiver uma fonte de dados do Analysis Services, precisará instalar o gateway em um computador associado ao mesmo domínio/floresta que o servidor do Analysis Services.

## <a name="add-a-data-source"></a>Adicionar uma fonte de dados

Para obter informações sobre como adicionar uma fonte de dados, consulte [Adicionar uma fonte de dados](service-gateway-data-sources.md#add-a-data-source). Se você estiver se conectando a um servidor de tabela ou multidimensional, selecione **Analysis Services** para o **Tipo da Fonte de Dados**.

![Adicionar a fonte de dados do Analysis Services](media/service-gateway-enterprise-manage-ssas/datasourcesettings2-ssas.png)

Preencha as informações sobre a fonte de dados, que incluem o **Servidor** e o **Banco de Dados**. As informações inseridas para **Nome de usuário** e **Senha** serão usadas pelo gateway para se conectar à instância do Analysis Services.

> [!NOTE]
> A conta do Windows inserida deve ter permissões de Administrador do Servidor para a instância à qual você está se conectando. Se a senha dessa conta estiver configurada para expirar, os usuários poderão receber um erro de conexão se a senha não estiver atualizada para a fonte de dados. Para saber mais sobre como as credenciais são armazenadas, confira [Armazenar credenciais criptografadas na nuvem](service-gateway-data-sources.md#store-encrypted-credentials-in-the-cloud).

![Preencher as configurações de fonte de dados](media/service-gateway-enterprise-manage-ssas/datasourcesettings3-ssas.png)

Depois de preencher tudo, selecione **Adicionar**. Agora você pode usar esta fonte de dados para atualização agendada ou conexões dinâmicas em uma instância local do Analysis Services. Você verá *Conexão Bem-sucedida* se tiver êxito.

![Exibindo o status da conexão](media/service-gateway-enterprise-manage-ssas/datasourcesettings4.png)

### <a name="advanced-settings"></a>Configurações avançadas

Opcionalmente, você pode configurar o nível de privacidade para sua fonte de dados. Essa configuração controla como os dados podem ser combinados. Ela é usada somente para a atualização agendada. A configuração de nível de privacidade não se aplica a conexões dinâmicas. Para saber mais sobre os níveis de privacidade para sua fonte de dados, confira [Níveis de privacidade (Power Query)](https://support.office.com/article/Privacy-levels-Power-Query-CC3EDE4D-359E-4B28-BC72-9BEE7900B540).

![Definir o nível de privacidade](media/service-gateway-enterprise-manage-ssas/datasourcesettings9.png)

## <a name="user-names-with-analysis-services"></a>Nomes de usuário com o Analysis Services

<iframe width="560" height="315" src="https://www.youtube.com/embed/Qb5EEjkHoLg" frameborder="0" allowfullscreen></iframe>

Cada vez que um usuário interage com um relatório conectado ao Analysis Services, o nome de usuário efetivo é passado para o gateway e, em seguida, para seu servidor local do Analysis Services. O endereço de email que você usa para entrar no Power BI é passado para o Analysis Services como o usuário efetivo. Ele é passado na propriedade de conexão [EffectiveUserName](https://msdn.microsoft.com/library/dn140245.aspx#bkmk_auth). 

O endereço de email deve corresponder a um nome UPN definido no domínio do Active Directory local. O UPN é uma propriedade de uma conta do Active Directory. A conta do Windows deverá estar presente em uma função do Analysis Services. Se não for possível encontrar uma correspondência no Active Directory, a conexão não será bem-sucedida. Para saber mais sobre Active Directory e a nomenclatura de usuário, consulte [Atributos de nomenclatura de usuário](https://msdn.microsoft.com/library/ms677605.aspx).

Você também pode [mapear seu nome de conexão do Power BI com um UPN do diretório local](service-gateway-enterprise-manage-ssas.md#map-user-names-for-analysis-services-data-sources).

## <a name="map-user-names-for-analysis-services-data-sources"></a>Mapear nomes de usuário para fontes de dados do Analysis Services

<iframe width="560" height="315" src="https://www.youtube.com/embed/eATPS-c7YRU" frameborder="0" allowfullscreen></iframe>

O Power BI possibilita o mapeamento de nomes de usuário para fontes de dados do Analysis Services. É possível configurar regras para mapear um nome de usuário conectado com o Power BI para um nome passado para EffectiveUserName na conexão do Analysis Services. O recurso Mapear nomes de usuário é uma ótima maneira de solucionar problemas quando seu nome de usuário no Azure AD (Azure Active Directory) não corresponde a um UPN na instância o Active Directory local. Por exemplo, se seu endereço de email fosse nancy@contoso.onmicrsoft.com, você o mapearia para nancy@contoso.com e esse valor seria passado para o gateway.

É possível mapear nomes de usuário para o Analysis Services de duas maneiras diferentes:

* Remapeamento manual do usuário
* Pesquisa de propriedade do Active Directory local para remapear UPNs do Azure AD para usuários do Active Directory (mapeamento de pesquisa do Active Directory)

É possível executar o mapeamento manual usando a segunda abordagem, mas fazer isso seria um pouco demorado e difícil de manter. Isso é especialmente difícil quando a correspondência de padrões não é suficiente. Os exemplos são quando os nomes de domínio são diferentes entre o Azure AD e o Active Directory local ou quando os nomes de conta de usuário são diferentes entre o Azure AD e o Active Directory. É por isso que não é recomendável realizar o mapeamento manual com a segunda abordagem.

Descrevemos essas duas abordagens, em ordem, nas duas seções a seguir.

### <a name="manual-user-name-remapping"></a>Remapeamento manual de nomes de usuário

Para fontes de dados do Analysis Services, é possível configurar regras personalizadas do UPN. As regras personalizadas ajudarão se os seus nomes de conexão do serviço do Power BI não correspondem ao UPN do diretório local. Por exemplo, se você entrar no Power BI com john@contoso.com, mas seu UPN do diretório local for john@contoso.local, será possível configurar uma regra de mapeamento para fazer com que john@contoso.local seja passado para o Analysis Services.

Para chegar à tela de Mapeamento de UPN, siga estas etapas.

1. Vá para o ícone de engrenagem e selecione **Gerenciar Gateways**.
2. Expanda o gateway que contém a fonte de dados do Analysis Services. Caso contrário, se você ainda não tiver criado a fonte de dados do Analysis Services, poderá fazer isso agora.
3. Selecione a fonte de dados e, em seguida, selecione a guia **Usuários**.
4. Selecione **Mapear nomes de usuário**.

    ![Tela de mapeamento de UPN](media/service-gateway-enterprise-manage-ssas/gateway-enterprise-map-user-names_02.png)

Você verá opções para adicionar regras e testar um determinado usuário.

> [!NOTE]
> Você pode alterar inadvertidamente um usuário que não pretendia alterar. Por exemplo, se **Substituir (valor original)** for contoso.com e **Por (Novo nome)** for @contoso.local, todos os usuários com uma credencial que contém @contoso.com serão substituídos por @contoso.local. Além disso, se **Substituir (Nome original)** for dave@contoso.com e **Por (Novo nome)** for dave@contoso.local, um usuário com a credencial de v-dave@contoso.com será enviado como v-dave@contoso.local.

### <a name="active-directory-lookup-mapping"></a>Mapeamento de pesquisa do Active Directory

Para realizar a pesquisa de propriedade do Active Directory local para remapear os UPNs do Azure AD para usuários do Active Directory, siga as etapas nesta seção. Em primeiro lugar, vamos examinar como isso funciona.

No serviço do Power BI, ocorre o seguinte:

* Para cada consulta feita por um usuário do Azure AD do Power BI para um servidor SSAS local, uma cadeia de caracteres UPN é passada, tal como firstName.lastName@contoso.com.

> [!NOTE]
> Quaisquer mapeamentos manuais de usuário UPN definidos na configuração de fonte de dados do Power BI ainda são aplicados *antes* de o nome de usuário ser enviado para o gateway de dados local.

No gateway de dados local com o mapeamento de usuário personalizado configurável, sita estas etapas.

1. Localize o Active Directory para pesquisar. Você pode usar automático ou configurável.
2. Consulte o atributo da pessoa do Active Directory, como Email, no serviço do Power BI. O atributo é baseado em uma cadeia de caracteres UPN de entrada como firstName.lastName@contoso.com.
3. Se a pesquisa do Active Directory falhar, ela tentará usar o UPN repassado como EffectiveUser para o SSAS.
4. Se a pesquisa do Active Directory for bem-sucedida, ela recuperará o UserPrincipalName dessa pessoa do Active Directory.
5. Ela passa o email UserPrincipalName como EffectiveUser para o SSAS, tal como Alias@corp.on-prem.contoso.

Para configurar o gateway para executar a pesquisa do Active Directory:

1. [Baixe e instale o gateway mais recente](/data-integration/gateway/service-gateway-install).

2. No gateway, altere o serviço do gateway de dados local para ser executado com uma conta de domínio, em vez de uma conta de serviço local. Caso contrário, a pesquisa do Active Directory não funcionará corretamente em runtime. Vá para o [aplicativo de gateway de dados local](/data-integration/gateway/service-gateway-app) em seu computador e acesse **Configurações de serviço** > **Alterar conta de serviço**. Certifique-se de ter a chave de recuperação para esse gateway, porque é preciso restaurá-lo no mesmo computador, a menos que você deseje criar um novo gateway em vez disso. Reinicie o serviço do gateway para que a alteração entre em vigor.

3. Vá até a pasta de instalação do gateway, *C:\Arquivos de Programas\Gateway de dados local* como um administrador para garantir que você tem permissões de gravação e edite. Abra o arquivo *Microsoft.PowerBI.DataMovement.Pipeline.GatewayCore.dll.config*.

4. Edite os dois valores de configuração a seguir de acordo com *suas* configurações de atributo do Active Directory para seus usuários do Active Directory. Os valores de configuração a seguir são exemplos. Especifique os valores com base em sua configuração do Active Directory. Essas configurações diferenciam maiúsculas de minúsculas, então garanta que elas correspondam aos valores no Active Directory.

    ![Configurações do Azure AD](media/service-gateway-enterprise-manage-ssas/gateway-enterprise-map-user-names_03.png)

    Se nenhum valor for fornecido para a configuração do ADServerPath, o gateway usará o catálogo global padrão. Você também pode especificar vários valores para o ADServerPath. Cada valor deve ser separado por ponto e vírgula como mostrado no exemplo a seguir:

    ```xml
    <setting name="ADServerPath" serializeAs="String">
        <value> >GC://serverpath1; GC://serverpath2;GC://serverpath3</value>
    </setting>
    ```

    O gateway analisa os valores para ADServerPath da esquerda para a direita até encontrar uma correspondência. Se nenhuma correspondência for encontrada, o UPN original será usado. Verifique se a conta que executa o serviço de gateway (PBIEgwService) tem permissões de consulta para todos os servidores do Active Directory que você especifica no ADServerPath.

    O gateway dá suporte a dois tipos de ADServerPath, como mostrado nos exemplos a seguir:

    **WinNT**

    ```xml
    <value="WinNT://usa.domain.corp.contoso.com,computer"/>
    ```

    **GC**

    ```xml
    <value> GC://USA.domain.com </value>
    ```

5. Reinicie o serviço do gateway de dados local para que a alteração da configuração entre em vigor.

### <a name="work-with-mapping-rules"></a>Trabalhar com regras de mapeamento

Para criar uma regra de mapeamento, insira um valor para **Nome original** e **Novo nome** e, em seguida, selecione **Adicionar**.

| Campo | Descrição |
| --- | --- |
| Substituir (Nome original) |O endereço de email que você usou para entrar no Power BI. |
| Com (Novo nome) |O valor pelo qual você deseja substituí-lo. O resultado da substituição é o que é passado para a propriedade EffectiveUserName da conexão do Analysis Services. |

![Criar uma regra de mapeamento](media/service-gateway-enterprise-manage-ssas/gateway-enterprise-map-user-names-effective-user-names.png)

Ao selecionar um item na lista, você poderá optar por reordenar usando os ícones de divisa. Ou você pode excluir a entrada.

![Reordenar um item na lista](media/service-gateway-enterprise-manage-ssas/gateway-enterprise-map-user-names-entry-selected.png)

### <a name="use-a-wildcard"></a>Usar um curinga

Você pode usar um caractere curinga (*) para sua cadeia de caracteres **Substituir (Nome original)** . Ele só pode ser usado sozinho e não com qualquer outra parte da cadeia de caracteres. Use um caractere curinga se desejar tirar todos os usuários e passe um único valor para a fonte de dados. Essa abordagem é útil quando você deseja que todos os usuários em sua organização usem o mesmo usuário no seu ambiente local.

### <a name="test-a-mapping-rule"></a>Testar uma regra de mapeamento

Para validar pelo que um nome original é substituído, insira um valor ou o **Nome original**. Selecione **Testar regra**.

![Testando uma regra de mapeamento](media/service-gateway-enterprise-manage-ssas/gateway-enterprise-test-mapping-rule.png)

> [!NOTE]
> Levará alguns minutos para que o serviço comece a usar regras que foram salvas. A regra funciona imediatamente no navegador.

### <a name="limitations-for-mapping-rules"></a>Limitações das regras de mapeamento

O mapeamento refere-se à fonte de dados específica que está sendo configurada. Não se trata de uma configuração global. Caso você tenha várias fontes de dados do Analysis Services, será necessário mapear os usuários para cada fonte de dados.

## <a name="authentication-to-a-live-analysis-services-data-source"></a>Autenticação em uma fonte de dados dinâmica do Analysis Services

Cada vez que um usuário interage com o Analysis Services, o nome de usuário efetivo é passado para o gateway e, em seguida, para o servidor local do Analysis Services. O UPN, que normalmente é o endereço de email que você usa para entrar na nuvem, é passado para o Analysis Services como o usuário efetivo. O nome UPN é passado na propriedade de conexão EffectiveUserName. 

Esse endereço de email deve corresponder a um UPN definido no domínio do Active Directory local. O UPN é uma propriedade de uma conta do Active Directory. Essa conta do Windows deve estar presente em uma função do Analysis Services para que ela tenha acesso ao servidor. Se nenhuma correspondência for encontrada no Active Directory, a conexão não será bem-sucedida.

O Analysis Services também poderá fornecer a filtragem com base nessa conta. A filtragem pode ocorrer com a segurança baseada em função ou com a segurança em nível de linha.

## <a name="role-based-security"></a>Segurança baseada em função

Modelos fornecem segurança baseada em funções de usuário. Funções são definidas para um projeto de modelo específico durante a criação no SQL Server Data Tools – Business Intelligence ou depois que um modelo é implantado usando o SQL Server Management Studio. As funções contêm membros organizados por nome de usuário do Windows ou por grupo do Windows. As funções definem as permissões de que um usuário dispõe para consultar ou executar ações no modelo. A maioria dos usuários pertence a uma função com permissões de leitura. Outras funções são destinadas a administradores com permissões para processar itens e gerenciar funções, tanto de banco de dados quanto de outros tipos.

## <a name="row-level-security"></a>Segurança em nível de linha

A segurança em nível de linha é específica para a segurança em nível de linha do Analysis Services. Os modelos podem fornecem segurança dinâmica no nível de linha. Em vez de ter pelo menos uma função à qual os usuários pertencem, a segurança dinâmica não é requerida para nenhum modelo de tabela. Em um nível elevado, a segurança dinâmica define o acesso de leitura de um usuário aos dados diretamente para uma linha específica em uma tabela específica. De modo similar ao que ocorre nas funções, a segurança dinâmica no nível de linha depende de um nome de usuário do Windows.

A capacidade do usuário de consultar e exibir dados de modelo é determinada por:

- As funções às quais sua conta de usuário do Windows pertence como membro.
- Segurança em nível de linha dinâmica, se estiver configurada.

A implementação de segurança dinâmica em nível de linha e a segurança baseada em função em modelos está além do escopo deste artigo. Para saber mais, confira [Funções (SSAS de tabela)](https://msdn.microsoft.com/library/hh213165.aspx) e [Funções de segurança (Analysis Services – dados multidimensionais)](https://msdn.microsoft.com/library/ms174840.aspx) no MSDN. Para obter uma compreensão mais profunda sobre a segurança do modelo de tabela, baixe e leia o [white paper Protegendo o modelo semântico de BI de tabela](https://msdn.microsoft.com/library/jj127437.aspx).

## <a name="what-about-azure-ad"></a>E quanto ao Azure AD?

Os serviços em nuvem da Microsoft usam o [Azure AD](/azure/active-directory/fundamentals/active-directory-whatis) para cuidar da autenticação de usuários. O Azure AD é o locatário que contém nomes de usuário e grupos de segurança. Normalmente, um endereço de email usado para a entrada de um usuário é o mesmo que o UPN da conta.

## <a name="what-is-the-role-of-my-local-active-directory-instance"></a>Qual é a função da minha instância do Active Directory local?

Para que o Analysis Services determine se um usuário que se conecta a ele pertence a uma função com permissões para leitura de dados, o servidor precisa converter o nome de usuário efetivo passado do Azure AD para o gateway e, em seguida, para o servidor do Analysis Services. O servidor do Analysis Services passa o nome de usuário efetivo para um DC (controlador de domínio) do Active Directory do Windows. O Active Directory DC, em seguida, valida que o nome de usuário efetivo é um UPN válido em uma conta local. Ele retorna o nome de usuário do Windows do usuário para o servidor do Analysis Services.

EffectiveUserName não pode ser usado em um servidor do Analysis Services que não foi ingressado em domínio. O servidor do Analysis Services deve ser ingressado em um domínio para evitar erros de conexão.

## <a name="how-do-i-tell-what-my-upn-is"></a>Como saber qual é a minha UPN?

Talvez você não saiba o que é o UPN e talvez você não seja um administrador de domínio. Você pode usar o comando a seguir em sua estação de trabalho para descobrir o UPN para sua conta.

    whoami /upn

O resultado é semelhante a um endereço de email, mas é o UPN que está em sua conta de domínio. Se você usar uma fonte de dados do Analysis Services para conexões dinâmicas e se esse UPN não corresponder ao endereço de email usado para entrar no Power BI, convém examinar como [mapear nomes de usuário](#map-user-names-for-analysis-services-data-sources).

## <a name="synchronize-an-on-premises-active-directory-with-azure-ad"></a>Sincronizar um Active Directory local com o Azure AD

Se você planejar usar conexões dinâmicas do Analysis Services, suas contas do Active Directory local deverão corresponder ao Azure AD. O UPN deve ser correspondente entre as contas.

Os serviços de nuvem conhecem apenas as contas no Azure AD. Não importa se você adicionou uma conta na instância do Active Directory local. Se a conta não existir no Azure AD, ela não poderá ser usada. Há diferentes maneiras pelas quais você poderá corresponder suas contas do Active Directory local ao Azure AD:

- É possível adicionar contas manualmente ao Azure AD.

   É possível criar uma conta no portal do Azure ou no Centro de administração do Microsoft 365 e o nome da conta corresponde ao UPN da conta do Active Directory local.

- Você pode usar a ferramenta [Azure AD Connect](/azure/active-directory/hybrid/how-to-connect-sync-whatis) para sincronizar contas locais ao seu locatário do Azure AD.

   A ferramenta do Azure AD Connect fornece opções para a sincronização de diretório e configuração da autenticação. As opções incluem sincronização de hash de senha, autenticação de passagem e federação. Se você não for um administrador de locatários nem um administrador de domínio local, entre em contato com seu administrador de TI para ajudar com a configuração.

   O uso do Azure AD Connect garante que o UPN corresponda entre o Azure AD e a instância do Active Directory local.

> [!NOTE]
> A sincronização de contas com a ferramenta Azure AD Connect cria novas contas em seu locatário do Azure AD.

## <a name="use-the-data-source"></a>Usar a fonte de dados

Depois de criar a fonte de dados, ela está disponível para uso com as conexões dinâmicas ou por meio da atualização agendada.

> [!NOTE]
> Os nomes do servidor e do banco de dados devem corresponder entre o Power BI Desktop e a fonte de dados no gateway de dados local.

O vínculo entre o conjunto de dados e a fonte de dados no gateway baseia-se nos nomes do servidor e do banco de dados. Esses nomes devem corresponder. Por exemplo, se você fornecer um endereço IP como nome do servidor no Power BI Desktop, precisará usar o endereço IP como fonte de dados na configuração do gateway. Se você usar *SERVER\INSTANCE* no Power BI Desktop, também precisará usar o mesmo na fonte de dados configurada para o gateway.

Esse requisito é o caso para conexões dinâmicas e a atualização agendada.

### <a name="use-the-data-source-with-live-connections"></a>Usar a fonte de dados com conexões dinâmicas

Verifique se os nomes do servidor e do banco de dados correspondem entre o Power BI Desktop e a fonte de dados configurada para o gateway. Você também precisa se certificar de que o usuário esteja listado na guia **Usuários** da fonte de dados para publicar os conjuntos de dados de conexão dinâmica. A seleção para conexões dinâmicas ocorre no Power BI Desktop quando você importa os dados pela primeira vez.

Após a publicação, por meio do Power BI Desktop ou do recurso **Obter Dados**, seus relatórios deverão começar a funcionar. Pode levar vários minutos após a criação da fonte de dados no gateway para que a conexão seja utilizável.

### <a name="use-the-data-source-with-scheduled-refresh"></a>Usar a fonte de dados com a atualização agendada

Se estiver listado na guia **Usuários** da fonte de dados configurada no gateway e houver a correspondência entre os nomes do servidor e do banco de dados, você verá o gateway como uma opção a ser usada com a atualização agendada.

![Exibir os usuários](media/service-gateway-enterprise-manage-ssas/powerbi-gateway-enterprise-schedule-refresh.png)

### <a name="limitations-of-analysis-services-live-connections"></a>Limitações das conexões dinâmicas do Analysis Services

Você pode usar uma conexão dinâmica em instâncias de tabela ou multidimensionais.

| **Versão do servidor** | **SKU necessário** |
| --- | --- |
| 2012 SP1 CU4 ou posterior |Business Intelligence e SKU Enterprise |
| 2014 |Business Intelligence e SKU Enterprise |
| 2016 |SKU Standard ou superior |

* Os recursos de conversão e formatação no nível de célula não são compatíveis.
* Ações e Conjuntos Nomeados não são expostos no Power BI. Mas você ainda pode se conectar a cubos multidimensionais que também contêm ações ou conjuntos nomeados e criar visuais e relatórios.

## <a name="next-steps"></a>Próximas etapas

* [Solução de problemas do gateway de dados local](/data-integration/gateway/service-gateway-tshoot)
* [Solucionar problemas de gateways – Power BI](service-gateway-onprem-tshoot.md)

Mais perguntas? Experimente a [Comunidade do Power BI](https://community.powerbi.com/).

