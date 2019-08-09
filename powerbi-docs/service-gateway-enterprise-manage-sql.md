---
title: Gerenciar sua fonte de dados –SQL
description: Como gerenciar o gateway de dados local e as fontes de dados que pertencem ao gateway.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 07/15/2019
ms.author: mblythe
LocalizationGroup: Gateways
ms.openlocfilehash: 2c21792f97445b336709038f7ec2ec39d041312b
ms.sourcegitcommit: 73228d0a9038b8369369c059ad06168d2c5ff062
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/02/2019
ms.locfileid: "68730046"
---
# <a name="manage-your-data-source---sql-server"></a>Gerenciar sua fonte de dados – SQL Server

[!INCLUDE [gateway-rewrite](includes/gateway-rewrite.md)]

Depois de [instalar o gateway de dados local](/data-integration/gateway/service-gateway-install), é necessário [adicionar fontes de dados](service-gateway-data-sources.md#add-a-data-source) que possam ser usadas com o gateway. Este artigo aborda como trabalhar com gateways e fontes de dados SQL Server que são usadas para a atualização agendada ou para o DirectQuery.

## <a name="add-a-data-source"></a>Adicionar uma fonte de dados

Para obter informações sobre como adicionar uma fonte de dados, consulte [Adicionar uma fonte de dados](service-gateway-data-sources.md#add-a-data-source).

![Selecionar a fonte de dados do SQL Server](media/service-gateway-enterprise-manage-sql/datasourcesettings2.png)

> [!NOTE]
> Ao usar o DirectQuery, o gateway só é compatível com o **SQL Server 2012 SP1** e versões subsequentes.

Em seguida, você deverá preencher as informações sobre a fonte de dados, que incluem o **Servidor** e o **Banco de Dados**.  

Também é necessário escolher um **Método de Autenticação**. Ele pode ser **Windows** ou **Básico**. Convém escolher **Básico** se você pretender usar a Autenticação do SQL em vez da Autenticação do Windows. Em seguida, insira as credenciais que serão usadas para esta fonte de dados.

> [!NOTE]
> Todas as consultas à fonte de dados serão executadas com essas credenciais, a menos que o SSO (logon único) do Kerberos esteja configurado e habilitado para a fonte de dados. Com SSO, conjuntos de dados de importação usam as credenciais armazenadas, mas conjuntos de dados de DirectQuery usam o usuário atual do Power BI para executar consultas usando o SSO. Para saber mais sobre como as credenciais são armazenadas, consulte [Armazenar credenciais criptografadas na nuvem](service-gateway-data-sources.md#store-encrypted-credentials-in-the-cloud) ou o artigo sobre como [usar o Kerberos para SSO (logon único) do Power BI para fontes de dados locais](service-gateway-sso-kerberos.md).

![Preencher as configurações de fonte de dados](media/service-gateway-enterprise-manage-sql/datasourcesettings3.png)

Selecione **Adicionar** depois de preencher tudo. Agora você pode usar esta fonte de dados para atualização agendada, ou para o DirectQuery, em um SQL Server local. Você verá *Conexão Bem-sucedida* se tiver êxito.

![Exibindo o status da conexão](media/service-gateway-enterprise-manage-sql/datasourcesettings4.png)

### <a name="advanced-settings"></a>Configurações avançadas

Opcionalmente, você pode configurar o nível de privacidade para sua fonte de dados. Ele controla como os dados podem ser combinados. É usado somente para a atualização agendada. Não se aplica ao DirectQuery. Para saber mais sobre os níveis de privacidade para sua fonte de dados, confira [Níveis de privacidade (Power Query)](https://support.office.com/article/Privacy-levels-Power-Query-CC3EDE4D-359E-4B28-BC72-9BEE7900B540).

![Definir o nível de privacidade](media/service-gateway-enterprise-manage-sql/datasourcesettings9.png)

## <a name="using-the-data-source"></a>Usando a fonte de dados

Depois de criar a fonte de dados, ela estará disponível para uso com as conexões do DirectQuery ou por meio da atualização agendada.

> [!NOTE]
> Os nomes do servidor e do banco de dados devem corresponder entre o Power BI Desktop e a fonte de dados no gateway de dados local.

O vínculo entre o conjunto de dados e a fonte de dados no gateway baseia-se nos nomes do servidor e do banco de dados. Eles devem corresponder. Por exemplo, se você fornecer um Endereço IP como nome do servidor no **Power BI Desktop**, terá de usar o endereço IP como fonte de dados na configuração do gateway. Se usar *SERVIDOR\INSTÂNCIA* no Power BI Desktop, você precisará usar a mesma coisa na fonte de dados configurada para o gateway.

Isso acontece para o DirectQuery e a atualização agendada.

### <a name="using-the-data-source-with-directquery-connections"></a>Usando a fonte de dados com conexões do DirectQuery

É preciso verificar se os nomes do servidor e do banco de dados correspondem entre o **Power BI Desktop** e a fonte de dados configurada para o gateway. Para que seja possível publicar os conjuntos de dados do DirectQuery, você também precisará verificar se o usuário está listado na guia **Usuários** da fonte de dados. A seleção, para o DirectQuery, ocorre no Power BI Desktop quando você importa dados pela primeira vez. Para obter mais informações sobre o uso do DirectQuery, consulte [Usar o DirectQuery no Power BI Desktop](desktop-use-directquery.md).

Após a publicação, por meio do Power BI Desktop ou do recurso **Obter Dados**, seus relatórios deverão começar a funcionar. Pode levar vários minutos, após a criação da fonte de dados no gateway, para que a conexão seja utilizável.

### <a name="using-the-data-source-with-scheduled-refresh"></a>Usando a fonte de dados com a atualização agendada

Se estiver listado na guia **Usuários** da fonte de dados configurada no gateway e houver a correspondência entre os nomes do servidor e do banco de dados, você verá o gateway como uma opção a ser usada com a atualização agendada.

![Exibir os usuários](media/service-gateway-enterprise-manage-sql/powerbi-gateway-enterprise-schedule-refresh.png)

## <a name="next-steps"></a>Próximas etapas

* [Conectar-se a dados locais no SQL Server](service-gateway-sql-tutorial.md)
* [Solução de problemas do gateway de dados local](/data-integration/gateway/service-gateway-tshoot)
* [Solucionar problemas de gateways – Power BI](service-gateway-onprem-tshoot.md)
* [Use o Kerberos para SSO (logon único) do Power BI para fontes de dados locais](service-gateway-sso-kerberos.md)

Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)

