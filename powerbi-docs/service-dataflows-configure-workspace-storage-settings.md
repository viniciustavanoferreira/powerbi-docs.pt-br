---
title: Definir configurações de fluxo de dados de workspace
description: Configurar um workspace no Power BI para armazenar sua definição de fluxo de dados e arquivos de dados no Azure Data Lake Storage Gen2
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/02/2019
ms.author: davidi
LocalizationGroup: Data from files
ms.openlocfilehash: 54c0936510c3d383df32fd8b1f99816726f74d9f
ms.sourcegitcommit: 8cc2b7510aae76c0334df6f495752e143a5851c4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73431990"
---
# <a name="configure-workspace-dataflow-settings-preview"></a>Definir configurações de fluxo de dados de workspace (versão prévia)

Com o Power BI e os fluxos de dados, você pode armazenar um arquivo de definição de fluxo de dados e arquivos de dados de um workspace em sua conta do Azure Data Lake Storage Gen2. Os administradores de workspace podem configurar o Power BI para fazer isso, e este artigo explica as etapas necessárias para chegar lá. 

Antes de configurar o local de armazenamento de fluxo de dados do workspace, administrador global da sua empresa deve conectar a conta de armazenamento da sua organização ao Power BI e habilitar as permissões de atribuição de armazenamento para essa conta de armazenamento. *[Conectar-se ao Azure Data Lake Storage Gen2 para armazenamento de fluxo de dados (versão prévia)](service-dataflows-connect-azure-data-lake-storage-gen2.md)* 

Há duas maneiras de definir as configurações de armazenamento de fluxo de dados do workspace: 

* Durante a criação do workspace
* Editando um workspace existente

Vamos dar uma olhada em cada uma nas seções a seguir. 

> [!IMPORTANT]
> A configuração de armazenamento de fluxo de dados do workspace só poderá ser alterada se o workspace não contiver um fluxo de dados. Além disso, esse recurso está disponível somente na nova experiência de workspace. Você pode aprender mais sobre o novo workspace no artigo [Criar novos workspaces (versão prévia) no Power BI](service-create-the-new-workspaces.md).

## <a name="create-a-new-workspace-configure-its-dataflow-storage"></a>Criar um novo workspace, configurar seu armazenamento de fluxo de dados

Para criar um novo workspace no serviço do Power BI, selecione **Workspaces > Criar workspace**.

![Adicionar novo workspace](media/service-dataflows-configure-workspace-storage-settings/dataflow-storage-settings_01.jpg)

Na caixa de diálogo Criar um workspace, uma caixa amarela intitulada **Visualizar workspaces aprimorados** poderá ser exibida. Nessa área, selecione **Experimente agora**.

![Visualizar workspaces aprimorados](media/service-dataflows-configure-workspace-storage-settings/dataflow-storage-settings_02.jpg)

Na caixa de diálogo exibida, você pode dar um nome exclusivo seu novo workspace. Não selecione **Salvar** ainda, pois você precisa fazer configurações avançadas.

![Dê um nome ao novo workspace](media/service-dataflows-configure-workspace-storage-settings/dataflow-storage-settings_03.jpg)

Em seguida, expanda a área **Avançado** da caixa de diálogo **Criar um workspace**, em que você pode ativar a configuração **Armazenamento de fluxo de dados (versão prévia)** .

![Configurações avançadas para o novo workspace](media/service-dataflows-configure-workspace-storage-settings/dataflow-storage-settings_04.jpg)

Selecione **Salvar** para criar o novo workspace. Qualquer fluxo de dados novo criado nesse workspace agora armazena seu arquivo de definição (o arquivo Model.json) e os dados da conta do Azure Data Lake Storage Gen2 da sua organização. 

## <a name="update-dataflow-storage-for-an-existing-workspace"></a>Atualizar o armazenamento de fluxo de dados para um workspace

Como alternativa à criação um novo workspace, você pode atualizar um workspace existente para armazenar o arquivo de definição e os dados na conta do Azure Data Lake Storage Gen2 da sua organização. Lembre-se de que a configuração de armazenamento de fluxo de dados só poderá ser alterada se o workspace já não contiver um fluxo de dados.

Para editar um workspace, selecione as reticências **(...)** e, em seguida, selecione **Editar workspace**. 

![Editar workspace](media/service-dataflows-configure-workspace-storage-settings/dataflow-storage-settings_05.jpg)

Na janela **Editar workspace** exibida, expanda **Avançado**, depois ative o **armazenamento de fluxo de dados (versão prévia)** definindo como **Ativado**. 

![Armazenamento de fluxo de dados definido como Ativado](media/service-dataflows-configure-workspace-storage-settings/dataflow-storage-settings_06.jpg)

Depois, **Salvar**, e qualquer fluxo de dados novo criado nesse workspace agora armazena seu arquivo de definição e os dados da conta do Azure Data Lake Storage Gen2 da sua organização.


## <a name="get-the-uri-of-stored-dataflow-files"></a>Obter o URI de arquivos de fluxo de dados armazenados

Depois de criar um fluxo de dados em um workspace atribuído à conta do Azure Data Lake da sua organização, você pode acessar seus arquivos de definição e de dados diretamente. A localização deles está disponível na página **Configurações de fluxo de dados**. Para chegar lá, siga estas etapas:

Selecione as reticências **(...)**  ao lado de um fluxo de dados listado em **Fluxos de dados** no workspace. No menu que aparece, selecione **Configurações**.

![Obter o URI de arquivos de fluxo de dados](media/service-dataflows-configure-workspace-storage-settings/dataflow-storage-settings_07.jpg)

Nas informações exibidas, o local da pasta do CDM do fluxo de dados aparece em **Local de armazenamento do fluxo de dados**, conforme mostrado na imagem a seguir.

![Local de arquivos de fluxo de dados](media/service-dataflows-configure-workspace-storage-settings/dataflow-storage-settings_08.jpg)

> [!NOTE]
> O Power BI configura o proprietário do fluxo de dados com permissões de leitura para a pasta do CDM onde os arquivos de fluxo de dados são armazenados. Conceder acesso a outras pessoas ou serviços para o local de armazenamento do fluxo de dados exige que o proprietário da conta de armazenamento conceda acesso no Azure.



## <a name="considerations-and-limitations"></a>Considerações e limitações

Determinados recursos de fluxo de dados não são compatíveis quando o armazenamento de fluxo de dados está no Azure Data Lake Storage Gen2: 

workspaces do Power BI Pro, Premium e Embedded:
* O recurso **entidades vinculadas** só tem suporte somente entre workspaces na mesma conta de armazenamento
* Permissões de workspace não se aplicam a fluxos de dados armazenados no Azure Data Lake Storage Gen2; somente o proprietário do fluxo de dados pode acessá-lo.
* Caso contrário, todos os recursos de preparação de dados são os mesmos para fluxos de dados no armazenamento do Power BI


Existem algumas considerações adicionais também, descritas na lista a seguir:

* Depois que um local de armazenamento de fluxo de dados for configurado, ele não poderá ser alterado.
* Somente o proprietário de um fluxo de dados armazenado no Azure Data Lake Storage Gen2 pode acessar seus dados.
* Não há suporte para fontes de dados local, em capacidades compartilhadas do Power BI, em fluxos de dados armazenados no Azure Data Lake Storage Gen2 da sua organização.

Os clientes do **Power BI Desktop** não podem acessar os fluxos de dados armazenados na conta do Azure Data Lake Storage Gen2, a menos que sejam os proprietários do fluxo de dados. Considere a seguinte situação:

1.  Brenda cria um workspace e o configura para armazenar fluxos de dados no data lake da organização.
2.  Davi, que também é membro do workspace criado por Brenda, deseja usar o Power BI Desktop e o conector de fluxo de dados para obter dados do fluxo de dados criado por Brenda.
3.  Davi recebe um erro porque não foi adicionado como usuário autorizado à pasta do CDM do fluxo de dados no data lake.

    ![Erro ao tentar usar o fluxo de dados](media/service-dataflows-configure-workspace-storage-settings/dataflow-storage-settings_08.jpg)


## <a name="next-steps"></a>Próximas etapas

Este artigo forneceu diretrizes sobre como configurar o armazenamento de workspace para fluxos de dados. Para saber mais, confira os seguintes artigos:

Para saber mais sobre fluxos de dados, CDM e o Azure Data Lake Storage Gen2, confira os seguintes artigos:

* [Integração entre fluxos de dados e o Azure Data Lake (versão prévia)](service-dataflows-azure-data-lake-integration.md)
* [Adicionar uma pasta do CDM ao Power BI como um fluxo de dados (versão prévia)](service-dataflows-add-cdm-folder.md)
* [Conectar-se ao Azure Data Lake Storage Gen2 para armazenamento de fluxo de dados (versão prévia)](service-dataflows-connect-azure-data-lake-storage-gen2.md)

Para saber mais sobre fluxos de dados em geral, confira estes artigos:

* [Criação e uso de fluxos de dados no Power BI](service-dataflows-create-use.md)
* [Uso de entidades computadas no Power BI Premium (versão prévia)](service-dataflows-computed-entities-premium.md)
* [Uso de fluxos de dados com fontes de dados locais (versão prévia)](service-dataflows-on-premises-gateways.md)
* [Recursos de desenvolvedor para fluxos de dados do Power BI (versão prévia)](service-dataflows-developer-resources.md)

Para saber mais sobre o armazenamento do Azure, você pode ler estes artigos:

* [Guia de segurança do Armazenamento do Microsoft Azure](https://docs.microsoft.com/azure/storage/common/storage-security-guide)
* [Introdução às amostras do github do Serviços de Dados do Azure](https://aka.ms/cdmadstutorial)

Leia este artigo de visão geral para saber mais sobre o Common Data Service:

* [Common Data Service - visão geral ](https://docs.microsoft.com/powerapps/common-data-model/overview)
* [Pastas do CDM](https://go.microsoft.com/fwlink/?linkid=2045304)
* [Definição de arquivo de modelo do CDM](https://go.microsoft.com/fwlink/?linkid=2045521)

E você pode sempre tentar [fazer perguntas à Comunidade do Power BI](http://community.powerbi.com/).
