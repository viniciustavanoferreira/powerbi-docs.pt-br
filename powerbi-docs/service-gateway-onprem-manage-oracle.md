---
title: Gerenciar sua fonte de dados – Oracle
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
ms.openlocfilehash: 3e3e51bf13a904e46552529d9131dbbb4665cb7d
ms.sourcegitcommit: 73228d0a9038b8369369c059ad06168d2c5ff062
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/02/2019
ms.locfileid: "68730248"
---
# <a name="manage-your-data-source---oracle"></a>Gerenciar sua fonte de dados – Oracle

[!INCLUDE [gateway-rewrite](includes/gateway-rewrite.md)]

Depois de [instalar o gateway de dados local](/data-integration/gateway/service-gateway-install), será necessário [adicionar fontes de dados](service-gateway-data-sources.md#add-a-data-source) que possam ser usadas com o gateway. Este artigo aborda como trabalhar com gateways e fontes de dados Oracle para a atualização agendada ou para o DirectQuery.

## <a name="installing-the-oracle-client"></a>Instalando o cliente Oracle

Para que o gateway possa se conectar ao servidor Oracle, o Provedor de dados Oracle para .NET (ODP.NET) precisa ser instalado e configurado. Isso faz parte do ODAC (Oracle Data Access Components).

Para versões de **32 bits** do Power BI Desktop, use o seguinte link para baixar e instalar o cliente Oracle de **32 bits**:

* [ODAC (Oracle Data Access Components) de 32 bits com Ferramentas de desenvolvimento da Oracle para Visual Studio (12.1.0.2.4)](http://www.oracle.com/technetwork/topics/dotnet/utilsoft-086879.html)

Para versões de **64 bits** do Power BI Desktop ou para o gateway de dados local, use o seguinte link para baixar e instalar o cliente Oracle de **64 bits**:

* [ODAC de 64 bits, 12.2c versão 1 (12.2.0.1.0) para Windows x64](http://www.oracle.com/technetwork/database/windows/downloads/index-090165.html)

Após a instalação, você precisará configurar o arquivo tnsnames.ora com as informações apropriadas para seu banco de dados. O Power BI Desktop e o gateway sairão do net_service_name definido no arquivo tnsnames.ora. Se não estiver configurado, você não poderá se conectar. O caminho padrão de tnsnames.ora é `[Oracle Home Directory]\Network\Admin\tnsnames.ora`. Para saber mais sobre como configurar arquivos tnsnames.ora, consulte [Oracle: Parâmetros de Nomenclatura Local (tnsnames.ora)](https://docs.oracle.com/cd/B28359_01/network.111/b28317/tnsnames.htm).

### <a name="example-tnsnamesora-file-entry"></a>Exemplo de entrada de arquivo tnsnames.ora

O formato básico de uma entrada em tnsname.ora é o seguinte.

```
net_service_name=
 (DESCRIPTION=
   (ADDRESS=(protocol_address_information))
   (CONNECT_DATA=
     (SERVICE_NAME=service_name)))
```

Aqui está um exemplo de informações de servidor e porta preenchidas.

```
CONTOSO =
  (DESCRIPTION =
    (ADDRESS = (PROTOCOL = TCP)(HOST = oracleserver.contoso.com)(PORT = 1521))
    (CONNECT_DATA =
      (SERVER = DEDICATED)
      (SERVICE_NAME = CONTOSO)
    )
  )
```

## <a name="add-a-data-source"></a>Adicionar uma fonte de dados

Para obter informações sobre como adicionar uma fonte de dados, consulte [Adicionar uma fonte de dados](service-gateway-data-sources.md#add-a-data-source). Selecione Oracle para o **Tipo de Fonte de Dados**.

![Adicionar a fonte de dados Oracle](media/service-gateway-onprem-manage-oracle/data-source-oracle.png)

Depois de selecionar o tipo de fonte de dados Oracle, você preencherá as informações da fonte de dados, que incluem o **Servidor** e o **Banco de dados**.  

Também é necessário escolher um **Método de Autenticação**.  Ele pode ser **Windows** ou **Básico**.  Use **Básico** se for usar uma conta criada com a autenticação do Oracle em vez da autenticação do Windows. Em seguida, insira as credenciais que serão usadas para esta fonte de dados.

> [!NOTE]
> Todas as consultas à fonte de dados serão executadas com essas credenciais. Para saber mais sobre como as credenciais são armazenadas, confira [Armazenar credenciais criptografadas na nuvem](service-gateway-data-sources.md#store-encrypted-credentials-in-the-cloud).

![Preencher as configurações de fonte de dados](media/service-gateway-onprem-manage-oracle/data-source-oracle2.png)

Selecione **Adicionar** depois de preencher tudo. Agora você pode usar esta fonte de dados para a atualização agendada ou para o DirectQuery, em relação a um servidor Oracle local. Você verá *Conexão Bem-sucedida* se tiver êxito.

![Exibindo o status da conexão](media/service-gateway-onprem-manage-oracle/datasourcesettings4.png)

### <a name="advanced-settings"></a>Configurações avançadas

Opcionalmente, você pode configurar o nível de privacidade para sua fonte de dados. Ele controla como os dados podem ser combinados. É usado somente para a atualização agendada. Não se aplica ao DirectQuery. Para saber mais sobre os níveis de privacidade para sua fonte de dados, confira [Níveis de privacidade (Power Query)](https://support.office.com/article/Privacy-levels-Power-Query-CC3EDE4D-359E-4B28-BC72-9BEE7900B540).

![Definir o nível de privacidade](media/service-gateway-onprem-manage-oracle/datasourcesettings9.png)

## <a name="using-the-data-source"></a>Usando a fonte de dados

Depois de criar a fonte de dados, ela estará disponível para uso com as conexões do DirectQuery ou por meio da atualização agendada.

> [!WARNING]
> Os nomes do servidor e do banco de dados devem corresponder entre o Power BI Desktop e a fonte de dados no gateway de dados local.

O vínculo entre o conjunto de dados e a fonte de dados no gateway baseia-se nos nomes do servidor e do banco de dados. Eles devem corresponder. Por exemplo, se você fornecer um Endereço IP como nome do servidor no Power BI Desktop, terá de usar o endereço IP como fonte de dados na configuração do gateway. Esse nome também deve corresponder a um alias definido no arquivo tnsnames.ora. Para obter mais informações sobre o arquivo tnsnames.ora, consulte [Instalando o cliente Oracle](#installing-the-oracle-client).

Isso acontece para o DirectQuery e a atualização agendada.

### <a name="using-the-data-source-with-directquery-connections"></a>Usando a fonte de dados com conexões do DirectQuery

É preciso verificar se os nomes do servidor e do banco de dados correspondem entre o Power BI Desktop e a fonte de dados configurada para o gateway. Para que seja possível publicar os conjuntos de dados do DirectQuery, você também precisará verificar se o usuário está listado na guia **Usuários** da fonte de dados. A seleção, para o DirectQuery, ocorre no Power BI Desktop quando você importa dados pela primeira vez. Para obter mais informações sobre o uso do DirectQuery, consulte [Usar o DirectQuery no Power BI Desktop](desktop-use-directquery.md).

Após a publicação, por meio do Power BI Desktop ou do recurso **Obter Dados**, seus relatórios deverão começar a funcionar. Pode levar vários minutos, após a criação da fonte de dados no gateway, para que a conexão seja utilizável.

### <a name="using-the-data-source-with-scheduled-refresh"></a>Usando a fonte de dados com a atualização agendada

Se estiver listado na guia **Usuários** da fonte de dados configurada no gateway e houver a correspondência entre os nomes do servidor e do banco de dados, você verá o gateway como uma opção a ser usada com a atualização agendada.

![Exibir os usuários](media/service-gateway-onprem-manage-oracle/powerbi-gateway-enterprise-schedule-refresh.png)

## <a name="troubleshooting"></a>Solução de problemas

Você poderá encontrar vários erros do Oracle quando a sintaxe de nomenclatura estiver incorreta ou não estiver configurada corretamente.

* ORA-12154: TNS: não foi possível resolver o identificador de conexão especificado  
* ORA-12514: O ouvinte TNS no momento não sabe sobre o serviço solicitado no descritor de conexão  
* ORA-12541: TNS: nenhum ouvinte  
* ORA-12170: TNS: ocorrência de tempo limite de conexão  
* ORA-12504: O ouvinte TNS não recebeu SERVICE_NAME em CONNECT_DATA  

Esses erros poderão ocorrer se o cliente Oracle não estiver instalado ou não estiver configurado corretamente. Se ele estiver instalado, verifique se o arquivo tnsnames.ora está configurado corretamente e se você está usando o net_service_name adequado. Você também precisará garantir que o net_service_name seja o mesmo entre o computador que está usando o Power BI Desktop e o computador que está executando o gateway. Para obter mais informações, consulte [Instalando o cliente Oracle](#installing-the-oracle-client).

> [!NOTE]
> Você também poderá enfrentar um problema devido à compatibilidade entre a versão do servidor Oracle e a versão do cliente Oracle. Normalmente, eles deverão corresponder.

Para obter informações adicionais de solução de problemas relativas ao gateway, veja [Solução de problemas do gateway de dados local](/data-integration/gateway/service-gateway-tshoot).

## <a name="next-steps"></a>Próximas etapas

* [Solucionar problemas de gateways – Power BI](service-gateway-onprem-tshoot.md)
* [Power BI Premium](service-premium.md)

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)

