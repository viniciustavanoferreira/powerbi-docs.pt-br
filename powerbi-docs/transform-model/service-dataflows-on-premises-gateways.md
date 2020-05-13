---
title: Usar fluxos de dados com fontes de dados locais
description: Saiba como usar dados locais em fluxos de dados
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 01/08/2020
ms.author: davidi
LocalizationGroup: Data from files
ms.openlocfilehash: 1008cf34cd09d8039107794e10dcef845ec35110
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83322414"
---
# <a name="using-dataflows-with-on-premises-data-sources"></a>Usar fluxos de dados com fontes de dados locais

Com **fluxos de dados**, você pode criar uma coleção de dados de várias fontes, limpar os dados, transformá-los e, em seguida, carregá-los para o armazenamento do Power BI. Ao criar o fluxo de dados, você pode querer usar fontes de dados locais. Este artigo esclarece os requisitos associados à criação de fluxos de dados e como o **Gateway Corporativo** precisa ser configurado para ativar essas conexões.

![Fluxos de dados e gateways](media/service-dataflows-onpremises-gateways/onpremises-gateways_01.png)

## <a name="configuring-an-enterprise-gateway-for-use-with-dataflows"></a>Configurar um Gateway Corporativo para uso com fluxos de dados

Para criar um fluxo de dados usando um gateway, o usuário precisa ser o administrador do gateway corporativo ou o administrador precisa ter compartilhado com o usuário a fonte de dados que planeja usar. 


> [!NOTE]
> Os fluxos de dados só têm suporte usando os Gateways Corporativos.

## <a name="using-an-on-premises-data-source-in-a-dataflow"></a>Usar uma fonte de dados local em um fluxo de dados

Ao criar um fluxo de dados, selecione uma fonte de dados local na lista de fontes de dados, conforme mostrado na imagem a seguir.

![Escolher uma fonte de dados no local](media/service-dataflows-onpremises-gateways/onpremises-gateways_02a.png)

Depois de fazer sua seleção, você é solicitado a fornecer os detalhes da conexão para o Gateway Corporativo que será usado para acessar os dados locais. Você deve selecionar o próprio gateway e fornecer credenciais para o gateway selecionado.

![Fornecer detalhes da conexão](media/service-dataflows-onpremises-gateways/onpremises-gateways_03.png)

## <a name="monitoring-your-gateway"></a>Monitorar seu gateway

Você pode monitorar seu Gateway Corporativo para um fluxo de dados da mesma maneira que monitora gateways para um conjunto de dados.

Na tela de configurações do fluxo de dados no Power BI, você pode monitorar o status do gateway de um fluxo de dados e atribuir um gateway ao fluxo de dados, conforme mostrado na imagem a seguir.

![Monitorar o gateway](media/service-dataflows-onpremises-gateways/onpremises-gateways_01.png)

## <a name="changing-a-gateway"></a>Alterar um gateway

Você pode alterar o Gateway Corporativo usado para um determinado fluxo de dados de duas maneiras:

1. **Na ferramenta de autoria** – você pode alterar o gateway atribuído a todas as suas consultas usando a ferramenta de criação de fluxo de dados.

    > [!NOTE]
    > O fluxo de dados tentará localizar ou criar as fontes de dados necessárias usando o novo gateway. Se isso for impossível, você não poderá alterar o gateway até que todos os fluxos de dados necessários estejam disponíveis no gateway selecionado.

2. **Na tela de configurações** – você pode alterar o gateway atribuído usando a tela de configurações do fluxo de dados no serviço do Power BI.

Para saber mais sobre Gateways Corporativos, confira [Gateway de dados no local](../connect-data/service-gateway-onprem.md).

## <a name="considerations-and-limitations"></a>Considerações e limitações

Existem algumas limitações conhecidas para o uso de Gateways Corporativos e fluxos de dados:

* Cada fluxo de dados pode usar apenas um gateway. Como tal, todas as consultas devem ser configuradas usando o mesmo gateway.
* A alteração do gateway afeta todo o fluxo de dados.
* Se vários gateways forem necessários, a melhor prática é criar vários fluxos de dados (um para cada gateway) e usar os recursos de referência de computação ou entidade para unificar os dados.
* Os fluxos de dados só têm suporte usando os gateways corporativos. Os gateways pessoais não estarão disponíveis para seleção nas telas de listas suspensas e configurações.


## <a name="next-steps"></a>Próximas Etapas

Este artigo forneceu informações sobre como usar a fonte de dados local para fluxos de dados e como usar e configurar gateways para acessar esses dados. Os artigos a seguir também podem ser úteis

* [Preparação de dados de autoatendimento com fluxos de dados](service-dataflows-overview.md)
* [Criação e uso de fluxos de dados no Power BI](service-dataflows-create-use.md)
* [Como usar entidades computadas no Power BI Premium](service-dataflows-computed-entities-premium.md)
* [Recursos de desenvolvedor para fluxos de dados do Power BI](service-dataflows-developer-resources.md)

Confira mais informações sobre o Power Query e a atualização agendada nestes artigos:
* [Visão geral de Consulta no Power BI Desktop](desktop-query-overview.md)
* [Configuração de atualização agendada](../connect-data/refresh-scheduled-refresh.md)

Leia este artigo de visão geral para saber mais sobre o Common Data Service:
* [Common Data Service - visão geral ](https://docs.microsoft.com/powerapps/common-data-model/overview)
