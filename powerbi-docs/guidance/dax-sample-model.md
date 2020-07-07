---
title: Modelo de exemplo DAX
description: Modelo de exemplo DAX para dar suporte a artigos de referência.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/25/2020
ms.author: v-pemyer
ms.openlocfilehash: 470bfcd4d9131c98412c504e4aba7daf6a995890
ms.sourcegitcommit: e8b12d97076c1387088841c3404eb7478be9155c
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85785177"
---
# <a name="dax-sample-model"></a>Modelo de exemplo DAX

O modelo de exemplo do Power BI Desktop **Adventure Works DW 2020** foi projetado para dar suporte ao aprendizado de DAX. O modelo se baseia no [exemplo de data warehouse da Adventure Works](/sql/samples/adventureworks-install-configure#data-warehouse-downloads) para AdventureWorksDW2017 – no entanto, os dados foram modificados para atender aos objetivos do modelo de exemplo.

## <a name="scenario"></a>Cenário

:::image type="content" source="media/dax-sample-model/adventure-works-logo-150x150.png" alt-text="Uma imagem do logotipo da empresa Adventure Works é mostrada.":::

A empresa Adventure Works representa um fabricante de bicicleta que vende bicicletas e acessórios para mercados globais. Os dados de data warehouse da empresa são armazenados em um Banco de Dados SQL do Azure.

## <a name="model-structure"></a>Estrutura do modelo

O modelo tem sete tabelas:

|Tabela|Descrição|
|-----|-------|
|**Cliente**|Descreve os clientes e sua localização geográfica. Os clientes compram produtos online (vendas pela Internet).|
|**Data**|Há três relacionamentos entre as tabelas **Date** e **Sales** para data do pedido, data de remessa e data de vencimento. O relacionamento de data do pedido está ativo. A empresa relata as vendas usando um ano fiscal que começa em 1º de julho de cada ano. A tabela é marcada como uma tabela de data usando a coluna **Date**.|
|**Product**|Armazena apenas os produtos acabados.|
|**Reseller**|Descreve revendedores e sua localização geográfica. O revendedor vende produtos para seus clientes.|
|**Vendas**|Armazena linhas no intervalo de linhas de ordem de venda. Todos os valores financeiros estão em dólares americanos (USD). A data da ordem mais antiga é 1º de julho de 2017, e a data da ordem mais recente é 15 de junho de 2020.|
|**Sales Order**|Descreve a ordem de venda e os números de linha da ordem, bem como o canal de vendas, que é **Reseller** ou **Internet**. Essa tabela tem uma relação um-para-um com a tabela **Sales**.|
|**Sales Territory**|As regiões de vendas são organizadas em grupos (América do Norte, Europa e Pacífico), países e regiões. Somente os Estados Unidos vendem produtos no nível da região.|

O modelo não contém nenhum cálculo DAX.

## <a name="download-sample"></a>Baixar exemplo

Você pode baixar o arquivo de modelo de exemplo do Power BI Desktop [aqui](https://aka.ms/dax-docs-sample-file).

## <a name="next-steps"></a>Próximas etapas

Para obter mais informações sobre este artigo, confira os seguintes recursos:

- [Referência do DAX (Data Analysis Expressions)](/dax/)
- Dúvidas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
- Sugestões? [Contribuir com ideias para aprimorar o Power BI](https://ideas.powerbi.com/)
