---
title: Limitações da entidade de serviço
description: Limitações da entidade de serviço
services: powerbi
author: KesemSharabi
ms.author: kesharab
ms.topic: include
ms.date: 06/06/2020
ms.custom: include file
ms.openlocfilehash: 8e50a529bfd398a4075ebf049ee4aec1bcf48b4d
ms.sourcegitcommit: cd64ddd3a6888253dca3b2e3fe24ed8bb9b66bc6
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/03/2020
ms.locfileid: "84315733"
---
## <a name="considerations-and-limitations"></a>Considerações e limitações

* A entidade de serviço só funciona com [novos workspaces](../collaborate-share/service-create-the-new-workspaces.md).
* Não há suporte para **Meu Workspace** ao usar a entidade de serviço.
* É necessária capacidade dedicada ao passar para produção.
* Você não pode entrar no portal do Power BI usando a entidade de serviço.
* Direitos de administrador do Power BI são necessários para habilitar a entidade de serviço nas configurações do desenvolvedor no portal do administrador do Power BI.
* Os aplicativos [inseridos para sua organização](../developer/embedded/embed-sample-for-your-organization.md) não podem usar a entidade de serviço.
* Não há suporte para gerenciamento de [fluxos de dados](../transform-model/service-dataflows-overview.md).
* No momento, a entidade de serviço não dá suporte a nenhuma API de administrador.
* Ao usar uma entidade de serviço com uma fonte de dados do [Azure Analysis Services](https://docs.microsoft.com/azure/analysis-services/analysis-services-overview), a própria entidade de serviço precisa ter permissões de uma instância do Azure Analysis Services. O uso de um grupo de segurança que contenha a entidade de serviço para essa finalidade não funciona.