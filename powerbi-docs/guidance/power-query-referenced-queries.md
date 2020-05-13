---
title: Referenciar consultas do Power Query
description: Diretrizes para referenciar consultas do Power Query.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/30/2019
ms.author: v-pemyer
ms.openlocfilehash: 242f1e44e3314af900d9f4d4e4fb7380b28b4103
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83278665"
---
# <a name="referencing-power-query-queries"></a>Referenciar consultas do Power Query

Este artigo destina-se aos modeladores de dados que trabalham com o Power BI Desktop. Ele fornece orientação quanto à definição de consultas do Power Query que referenciam outras consultas.

Vamos esclarecer o que isso significa: _Quando uma consulta referencia uma segunda consulta, é como se as etapas da segunda consulta fossem combinadas e executadas antes das etapas da primeira consulta._

Considere várias consultas: A **Consulta1** usa fonte de dados de um serviço Web, e sua carga está desabilitada. A **Consulta2**, **Consulta3** e **Consulta4** referenciam a **Consulta1**, e suas saídas são carregadas no modelo de dados.

![Exibição de dependências da consulta, mostrando as consultas descritas no parágrafo anterior.](media/power-query-referenced-queries/query-dependencies-web-service.png)

Quando o modelo de dados é atualizado, geralmente se pressupõe que o Power Query recupera o resultado da **Consulta1**, que é reutilizado pelas consultas referenciadas. Esse pensamento está incorreto. Na verdade, o Power Query executa a **Consulta2**, a **Consulta3** e a **Consulta4** separadamente.

Você pode considerar que a **Consulta2** tem as etapas da **Consulta1** inseridas nela. Esse também é o caso da **Consulta3** e **Consulta4**. O diagrama a seguir apresenta uma visão mais clara de como as consultas são executadas.

![Uma versão modificada da exibição de Dependências de consulta, exibindo a Consulta 2, Consulta 3 e Consulta 4. Cada uma das três consultas tem a Consulta 1 inserida.](media/power-query-referenced-queries/query-dependencies-web-service-concept.png)

A **Consulta1** é executada três vezes. As várias execuções podem resultar em uma lentidão na atualização de dados e um impacto negativo na fonte de dados.

O uso da função [Table.Buffer](/powerquery-m/table-buffer) na **Consulta1** não eliminará a recuperação de dados adicional. Essa função armazena uma tabela em buffer. E a tabela em buffer só pode ser usada na mesma execução de consulta. Portanto, no exemplo, se a **Consulta1** for armazenada em buffer quando a **Consulta2** for executada, os dados armazenados em buffer não poderão ser usados quando a **Consulta3** e a **Consulta4** forem executadas. Elas próprias armazenarão os dados em buffer duas vezes mais. (Esse resultado poderia, na verdade, ampliar o desempenho negativo, pois a tabela será armazenada em buffer para cada consulta referenciada.)

> [!NOTE]
> A arquitetura de cache do Power Query é complexa e não é o foco deste artigo. O Power Query pode armazenar em cache os dados recuperados de uma fonte de dados. No entanto, quando ele executa uma consulta, pode recuperar os dados da fonte de dados mais de uma vez.

## <a name="recommendations"></a>Recomendações

Em geral, recomendamos que você referencie consultas para evitar a duplicação de lógica nas suas consultas. No entanto, conforme descrito neste artigo, essa abordagem de design pode contribuir para a lentidão das atualizações de dados e para a sobrecarga das fontes de dados.

Em vez disso, recomendamos que você crie um [fluxo de dados](../transform-model/service-dataflows-overview.md). O uso de um fluxo de dados pode melhorar o tempo de atualização de dados e reduzir o impacto em suas fontes de dados.

Você pode criar o fluxo de dados para encapsular as transformações e os dados de origem. Como o fluxo de dados é um armazenamento persistente de dados no serviço do Power BI, sua recuperação de dados é rápida. Assim, mesmo quando as consultas referenciadas resultam em várias solicitações do fluxo de dados, os tempos de atualização de dados podem ser melhorados.

No exemplo, se a **Consulta1** for reformulada como uma entidade de fluxo de dados, a **Consulta2**, a **Consulta3** e a **Consulta4** poderão usá-la como uma fonte de dados. Com esse design, a entidade originada pela **Consulta1** será avaliada apenas uma vez.

## <a name="next-steps"></a>Próximas etapas

Para obter mais informações relacionadas a este artigo, confira os seguintes recursos:

- [Preparação de dados de autoatendimento no Power BI](../transform-model/service-dataflows-overview.md)
- [Criação e uso de fluxos de dados no Power BI](../transform-model/service-dataflows-create-use.md)
- Dúvidas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
- Sugestões? [Contribuir com ideias para aprimorar o Power BI](https://ideas.powerbi.com/)
