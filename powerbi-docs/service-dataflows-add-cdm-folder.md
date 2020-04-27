---
title: Adicionar uma pasta do CDM ao Power BI como um fluxo de dados
description: Configurar um workspace para armazenar sua definição de fluxo de dados e arquivos de dados no Azure Data Lake Storage Gen2
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/02/2019
ms.author: davidi
LocalizationGroup: Data from files
ms.openlocfilehash: cc47820e5903426d4f3635c78e0dc108049f897e
ms.sourcegitcommit: b2cb0b02bdc451bf11a92a68f2c4d560a811f563
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81439332"
---
# <a name="add-a-cdm-folder-to-power-bi-as-a-dataflow-preview"></a>Adicionar uma pasta do CDM ao Power BI como um fluxo de dados (versão prévia)

No Power BI, você pode adicionar pastas do Common Data Service (CDM) armazenadas no Azure Data Lake Storage Gen2 de sua organização como fluxos de dados. E depois de criar um fluxo de dados de uma pasta do CDM, você pode usar o **Power BI Desktop** e o **serviço do Power BI** para criar conjuntos de dados, relatórios, painéis e aplicativos baseados nos dados que você inseriu em pastas do CDM.

![Fluxo de dados da pasta CDM](media/service-dataflows-add-cdm-folder/dataflow-from-cdm-folder_01.jpg)

Há alguns requisitos para criar fluxos de dados a partir de pastas do CDM, conforme a lista a seguir descreve:

* Um administrador deve vincular a conta de armazenamento ADLS Gen2 dentro do Power BI antes que ela possa ser usada. Confira [Conectar Azure Data Lake Storage Gen2 para armazenamento de fluxo de dados](service-dataflows-connect-azure-data-lake-storage-gen2.md) para saber como vincular uma conta ADLS Gen2 ao Power BI.
* A criação de fluxos de dados de pastas do CDM está disponível *somente* na [nova experiência de workspace](service-create-the-new-workspaces.md). 
* Adicionar uma pasta do CDM ao Power BI requer que o usuário adicione a pasta para ter [autorização para a pasta do CDM e seus arquivos](https://go.microsoft.com/fwlink/?linkid=2029121).
* Você deve ter permissões de leitura e execução em todos os arquivos e pastas da pasta do CDM para adicioná-las ao Power BI.

As seções a seguir descrevem como criar um fluxo de dados de uma pasta do CDM.

## <a name="authorizing-users-for-cdm-folders-to-create-a-dataflow"></a>Como autorizar usuários para pastas CDM a fim de criar um fluxo de dados

Para criar um fluxo de dados de uma pasta do CDM, as seguintes permissões devem ser adicionadas:
* O usuário que acessará a pasta do CDM por meio do Power BI precisará estar listado na função de **Proprietário de Dados do Storage Blob** da conta de armazenamento.
* O usuário que acessará a pasta do CDM por meio do Power BI precisará ter as ACLs de **Acesso de Leitura** e de **Acesso de Execução** na pasta do CDM e nos arquivos e pastas contidos nela. 

## <a name="create-a-dataflow-from-a-cdm-folder"></a>Criar um fluxo de dados de uma pasta do CDM

Para começar a criar um fluxo de dados de uma pasta do CDM, inicie o **serviço do Power BI** e selecione um **workspace** no painel de navegação. Você também pode criar um novo workspace, no qual você pode criar seu novo fluxo de dados.

![Criar um fluxo de dados no serviço do Power BI](media/service-dataflows-add-cdm-folder/dataflow-from-cdm-folder_02.jpg)

Na tela exibida, selecione **Criar e anexar**, conforme mostrado na imagem a seguir.

![Criar e anexar um novo fluxo de dados](media/service-dataflows-add-cdm-folder/dataflow-from-cdm-folder_03.jpg)

A tela que aparece a seguir permite nomear seu fluxo de dados, fornecer uma descrição do fluxo de dados e fornecer o caminho para a pasta do CDM na conta do Azure Data Lake Gen2 de sua organização. Leia a seção no artigo que descreve [como obter o caminho da pasta do CDM](service-dataflows-configure-workspace-storage-settings.md#get-the-uri-of-stored-dataflow-files). 

![Fluxo de dados da pasta do CDM](media/service-dataflows-add-cdm-folder/dataflow-from-cdm-folder_01.jpg)

Depois de fornecer as informações, selecione **Criar e Anexar** para criar o fluxo de dados.

Os fluxos de dados das pastas do CDM são marcados com o ícone *externo* quando exibidos no Power BI. Na próxima seção, descrevemos as diferenças entre os fluxos de dados padrão e os fluxos de dados criados nas pastas do CDM.

Depois que as permissões estiverem definidas de forma correta, conforme descrito anteriormente neste artigo, você poderá se conectar ao seu fluxo de dados no **Power BI Desktop**.


## <a name="considerations-and-limitations"></a>Considerações e limitações

Ao trabalhar com permissões para um fluxo de dados criado a partir de uma pasta do CDM, o processo é semelhante às origens de dados externas no Power BI. As permissões são gerenciadas na fonte de dados e não no Power BI. As permissões devem ser definidas adequadamente na própria fonte de dados, como um fluxo de dados criado a partir de uma pasta do CDM, para funcionar corretamente com o Power BI.

As listas a seguir ajudam a esclarecer como os fluxos de dados das pastas do CDM operam com o Power BI.

Espaço de Trabalhos do Power BI Pro, Premium e Embedded:
* Os fluxos de dados de pastas do CDM não podem ser editados
* As permissões para ler um fluxo de dados criado a partir de uma pasta do CDM são gerenciadas pelo proprietário da pasta do CDM e não pelo Power BI

Power BI Desktop:
* Somente usuários autorizados para o espaço de trabalho no qual o fluxo de dados foi criado e para a pasta do CDM podem acessar seus dados no conector de fluxos de dados do Power BI


Existem algumas considerações adicionais também, descritas na lista a seguir:

* A criação de fluxos de dados de pastas do CDM está disponível *somente* na [nova experiência de workspace](service-create-the-new-workspaces.md)
* As entidades vinculadas não estão disponíveis para fluxos de dados criados a partir de pastas do CDM


Os clientes do **Power BI Desktop** não podem acessar os fluxos de dados armazenados na conta do Azure Data Lake Storage Gen2, a menos que sejam os proprietários do fluxo de dados ou recebam autorização explícita para a pasta do CDM do fluxo de dados. Considere a seguinte situação:

1.    Brenda cria um novo workspace e o configura para armazenar fluxos de dados de uma pasta do CDM.
2.    Davi, que também é membro do workspace criado por Brenda, deseja usar o Power BI Desktop e o conector de fluxo de dados para obter dados do fluxo de dados criado por Brenda.
3.    Davi recebe um erro porque não foi adicionado como usuário autorizado na pasta do CDM do fluxo de dados no data lake.

  ![Erro ao tentar usar o fluxo de dados](media/service-dataflows-configure-workspace-storage-settings/dataflow-storage-settings_08.jpg)

Para resolver esse problema, o Davi deve receber permissões de leitura para a pasta do CDM e seus arquivos. Você pode saber mais sobre como conceder acesso à pasta do CDM [neste artigo](https://go.microsoft.com/fwlink/?linkid=2029121).


## <a name="next-steps"></a>Próximas etapas

Este artigo forneceu diretrizes sobre como configurar o armazenamento de workspace para fluxos de dados. Para saber mais, confira os seguintes artigos:

Para saber mais sobre fluxos de dados, CDM e o Azure Data Lake Storage Gen2, confira os seguintes artigos:

* [Integração entre fluxos de dados e o Azure Data Lake (versão prévia)](service-dataflows-azure-data-lake-integration.md)
* [Definir configurações de fluxo de dados de workspace (versão prévia)](service-dataflows-configure-workspace-storage-settings.md)
* [Conectar-se ao Azure Data Lake Storage Gen2 para armazenamento de fluxo de dados (versão prévia)](service-dataflows-connect-azure-data-lake-storage-gen2.md)

Para saber mais sobre fluxos de dados em geral, confira estes artigos:

* [Criação e uso de fluxos de dados no Power BI](service-dataflows-create-use.md)
* [Como usar entidades computadas no Power BI Premium](service-dataflows-computed-entities-premium.md)
* [Como usar fluxos de dados com fontes de dados locais](service-dataflows-on-premises-gateways.md)
* [Recursos de desenvolvedor para fluxos de dados do Power BI](service-dataflows-developer-resources.md)

Para saber mais sobre o armazenamento do Azure, você pode ler estes artigos:
* [Guia de segurança do Armazenamento do Microsoft Azure](https://docs.microsoft.com/azure/storage/common/storage-security-guide)
* [Configuração de atualização agendada](refresh-scheduled-refresh.md)
* [Introdução às amostras do github do Serviços de Dados do Azure](https://aka.ms/cdmadstutorial)

Leia este artigo de visão geral para saber mais sobre o Common Data Service:
* [Common Data Service - visão geral ](https://docs.microsoft.com/powerapps/common-data-model/overview)
* [Pastas do CDM](https://go.microsoft.com/fwlink/?linkid=2045304)
* [Definição de arquivo de modelo do CDM](https://go.microsoft.com/fwlink/?linkid=2045521)

E você pode sempre tentar [fazer perguntas à Comunidade do Power BI](https://community.powerbi.com/).

