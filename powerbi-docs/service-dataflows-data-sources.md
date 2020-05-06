---
title: Saiba como se conectar a fluxos de dados no Power BI
description: Saiba mais os fluxos de dados funcionam no Power BI
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 09/20/2019
ms.author: davidi
LocalizationGroup: Data from files
ms.openlocfilehash: 650fb243152d9bf2ca2ecfc37143145d734b78fe
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/05/2020
ms.locfileid: "73872678"
---
# <a name="connect-to-data-sources-for-power-bi-dataflows"></a>Conectar-se a fontes de dados para fluxos de dados do Power BI

Com os fluxos de dados do Power BI, você pode se conectar a várias fontes de dados para criar fluxos de dados ou adicionar novas entidades a um fluxo de dados existente.

Este artigo lista várias fontes de dados disponíveis para criar fluxos de dados ou a serem adicionadas a eles e descreve como criar esses fluxos de dados usando essas fontes de dados.

Para obter uma visão geral de como criar e usar fluxos de dados, confira [Criando e usando fluxos de dados no Power BI](service-dataflows-create-use.md).

## <a name="create-a-dataflow-from-a-data-source"></a>Criar um fluxo de dados usando uma fonte de dados

Para conectar-se aos dados, no **serviço do Power BI** selecione o item de menu **+ Criar**, em seguida, selecione **fluxo de dados** no menu que aparece. Após a seleção, a imagem a seguir será exibida na tela do serviço do Power BI. 

![Adicionar novo fluxo de dados ou entidade](media/service-dataflows-data-sources/dataflows-data-sources_01.png)

Se o fluxo de dados já existir, você poderá adicionar novas entidades a ele selecionando **Adicionar entidades**, conforme mostrado abaixo, ou selecionando **Obter dados** na ferramenta de criação de fluxo de dados.

![Adicionar entidades a um fluxo de dados existente](media/service-dataflows-data-sources/dataflows-data-sources_02.png)

A imagem a seguir mostra o botão **Obter dados** na ferramenta de criação de fluxo de dados. 

![Adicionar entidades usando Obter Dados](media/service-dataflows-data-sources/dataflows-data-sources_03.png)


## <a name="data-sources-for-dataflows"></a>Fontes de dados para fluxos de dados

Você pode exibir as fontes de dados disponíveis selecionando **Obter Dados** na ferramenta de criação de fluxo de dados, que exibirá uma caixa de diálogo para selecionar as categorias e cada fonte de dados, conforme mostrado na imagem a seguir.


![Categorias da opção obter dados para fluxos de dados](media/service-dataflows-data-sources/dataflows-data-sources_04.png)

As fontes de dados para fluxos de dados são organizadas nas categorias a seguir, que aparecem na parte superior da caixa de diálogo **Obter dados**:

* Todas as categorias
* Arquivo
* Banco de Dados
* Power BI
* Azure
* Serviços online
* Outros

A categoria **Todas as categorias** contém todas as fontes de dados de todas as categorias. 

A categoria **Arquivo** inclui as seguintes conexões de dados disponíveis para fluxos de dados:

* Acesso
* Excel
* JSON
* Texto/CSV
* XML

A categoria **Banco de dados** inclui as seguintes conexões de dados disponíveis para fluxos de dados:

* Banco de dados IBM DB2
* Banco de dados MySQL
* Banco de dados Oracle
* Banco de dados PostgreSQL
* Banco de dados do SQL Server
* Banco de dados Sybase
* Teradata
* Vertica

A categoria **Power BI** inclui as seguintes conexões de dados disponíveis para fluxos de dados:

* Fluxos de dados do Power BI

A categoria **Azure** inclui as seguintes conexões de dados disponíveis para fluxos de dados:

* Blobs do Azure
* Azure Data Explorer
* SQL Data Warehouse do Azure
* Banco de Dados SQL do Azure
* Tabelas do Azure

A categoria **Serviços Online** inclui as seguintes conexões de dados disponíveis para fluxos de dados:

* Amazon Redshift
* Common Data Service for Apps
* Microsoft Exchange Online
* Objetos do Salesforce
* Relatórios do Salesforce
* Lista do SharePoint Online
* Smartsheet

O **outros** categoria inclui as seguintes conexões de dados disponíveis para fluxos de dados:

* Active Directory
* OData
* Lista do SharePoint
* API Web
* Página da Web
* Tabela em branco
* Consulta em Branco


## <a name="connecting-to-a-data-source"></a>Conectando-se a uma fonte de dados

Para conectar-se a uma fonte de dados, selecione-a. Usaremos um exemplo para mostrar como funciona o processo, mas cada conexão de dados para fluxos de dados tem um processo semelhante. Conectores diferentes podem exigir credenciais específicas ou outras informações, mas o fluxo é semelhante. Em nosso exemplo, você verá na imagem a seguir que o **Common Data Service for Apps** está selecionado na categoria **Serviços online** de conexão de dados.

![Selecione o Common Data Service for Apps](media/service-dataflows-data-sources/dataflows-data-sources_05.png)

Uma janela de conexão para a conexão de dados selecionado é exibida. Se forem necessárias credenciais, será solicitado que você as forneça. A imagem a seguir mostra uma URL do servidor sendo inserida para conectar-se a um servidor do Common Data Service for Apps.

![Credenciais ou URLs para conexões de dados](media/service-dataflows-data-sources/dataflows-data-sources_06.png)

Depois que as informações de conexão de URL ou de recurso do servidor forem fornecidas, selecione **Entrar** para inserir as credenciais a serem usadas para o acesso a dados, em seguida, selecione **Avançar**.

O **Power Query Online** inicia e estabelece a conexão com a fonte de dados e, em seguida, apresenta as tabelas disponíveis dessa fonte de dados na janela **Navegador**, mostrada na imagem a seguir.

![A janela do navegador mostra as tabelas na fonte de dados](media/service-dataflows-data-sources/dataflows-data-sources_07.png)

Você pode selecionar as tabelas e os dados a serem carregados marcando a caixa de seleção ao lado de cada um no painel esquerdo. Para carregar os dados, selecione **OK** na parte inferior do painel **Navegador**. Será exibida uma caixa de diálogo do Power Query Online, na qual você pode editar consultas e realizar outras transformações desejadas nos dados selecionados.

![Editar consultas e transformar no Editor do Power Query](media/service-dataflows-data-sources/dataflows-data-sources_08.png)

Isso é tudo para ela. Outras fontes de dados têm fluxos semelhantes e usam o Power Query Online para editar e transformar os dados inseridos no fluxo de dados.

## <a name="connecting-to-additional-data-sources"></a>Conectando-se a fontes de dados adicionais

Há conectores de dados adicionais que não são mostrados na interface do usuário de fluxos de dados do Power BI, mas são permitidos mediante algumas etapas adicionais. 

Você pode executar as seguintes etapas para criar uma conexão com um conector que não é exibido na interface do usuário:

1. Abra o **Power BI Desktop** e selecione **Obter Dados**.
2. Abra o **Editor do Power Query** no Power BI Desktop e, em seguida, clique com o botão direito do mouse na consulta relevante e abra o **Editor Avançado**, conforme mostrado na imagem a seguir. Agora você pode copiar o script M que aparece no Editor Avançado.

    ![Copiar o script M do Editor Avançado do Power BI Desktop](media/service-dataflows-data-sources/dataflows-data-sources_09.png) 

3. Abra o fluxo de dados do Power BI e selecione **Obter dados** para uma consulta em branco, conforme mostrado na imagem a seguir.

    ![Criar uma consulta em branco para um fluxo de dados](media/service-dataflows-data-sources/dataflows-data-sources_10.png) 

4. Cole a consulta copiada na consulta em branco para o fluxo de dados.

    ![Copie o script M na janela do editor](media/service-dataflows-data-sources/dataflows-data-sources_11.png) 

E, em seguida, o script conecta-se à fonte de dados especificada. 

A lista a seguir mostra quais conectores você pode usar no momento copiando e colando a consulta M em uma consulta em branco:

* Azure Analysis Services
* Adobe Analytics
* ODBC
* OLE DB
* Pasta
* Pasta do SharePoint Online
* Pasta do SharePoint
* HDFS do Hadoop
* Azure HDInsight (HDFS)
* Arquivo HDFS do Hadoop
* Informix (beta)

Basta fazer isso para conectar-se a fontes de dados no Power BI Desktop.


## <a name="next-steps"></a>Próximas Etapas

Este artigo mostrou a quais fontes de dados você pode se conectar para fluxos de dados. Os artigos a seguir oferecem mais detalhes sobre cenários de uso comuns para fluxos de dados. 

* [Preparação de dados de autoatendimento no Power BI](service-dataflows-overview.md)
* [Criação e uso de fluxos de dados no Power BI](service-dataflows-create-use.md)
* [Como usar entidades computadas no Power BI Premium](service-dataflows-computed-entities-premium.md)
* [Como usar fluxos de dados com fontes de dados locais](service-dataflows-on-premises-gateways.md)
* [Recursos de desenvolvedor para fluxos de dados do Power BI](service-dataflows-developer-resources.md)
* [Integração entre fluxos de dados e o Azure Data Lake (versão prévia)](service-dataflows-azure-data-lake-integration.md)

Confira mais informações sobre o Power Query e a atualização agendada nestes artigos:
* [Visão geral de Consulta no Power BI Desktop](desktop-query-overview.md)
* [Configuração de atualização agendada](refresh-scheduled-refresh.md)

Leia este artigo de visão geral para saber mais sobre o Common Data Service:
* [Common Data Service - visão geral ](https://docs.microsoft.com/powerapps/common-data-model/overview)

