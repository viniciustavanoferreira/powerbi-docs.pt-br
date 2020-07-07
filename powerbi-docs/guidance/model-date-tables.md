---
title: Criar tabelas de data no Power BI Desktop
description: Técnicas e diretrizes para a criação de tabelas de data no Power BI Desktop.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/24/2020
ms.author: v-pemyer
ms.openlocfilehash: ad85ad56db907ca19af7dc14681eb34f8c2b9abc
ms.sourcegitcommit: 46a340937d9f01c6daba86a4ab178743858722ec
ms.contentlocale: pt-BR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85398054"
---
# <a name="create-date-tables-in-power-bi-desktop"></a>Criar tabelas de data no Power BI Desktop

Este artigo destina-se aos modeladores de dados que trabalham com o Power BI Desktop. Ele descreve boas práticas de design para a criação de tabelas de data em seus modelos de dados.

Para trabalhar com [funções de inteligência de dados temporais](/dax/time-intelligence-functions-dax) de linguagem DAX (Data Analysys Expressions), há um pré-requisito para o modelo: você deve ter pelo menos uma _tabela de data_ em seu modelo. Uma tabela de data é aquela que atende aos seguintes requisitos:

> [!div class="checklist"]
> - Ela deve ter uma coluna de tipo de dados de **data** (ou **data/hora**) – conhecida como _coluna de data_.
> - A coluna de data deve conter valores exclusivos.
> - A coluna de data não deve conter espaços em branco.
> - A coluna de data não deve ter nenhuma data ausente.
> - A coluna de data deve abranger os anos completos. Um ano não é necessariamente um ano civil (janeiro a dezembro).
> - A tabela de data deve ser [marcada como uma tabela de data](../transform-model/desktop-date-tables.md#setting-your-own-date-table).

Você pode usar qualquer uma das várias técnicas para adicionar uma tabela de data ao seu modelo:

- A opção de data/hora automática
- Power Query para se conectar a uma tabela de dimensão de data
- Power Query para gerar uma tabela de data
- DAX para gerar uma tabela de data
- DAX para clonar uma tabela de data existente

> [!TIP]
> Talvez a tabela de data seja o recurso mais consistente que você adicionará a qualquer um de seus modelos. Além disso, em uma organização, uma tabela de data deve ser definida de forma consistente. Portanto, independentemente da técnica que você decidir usar, recomendamos criar um [modelo do Power BI Desktop](../create-reports/desktop-templates.md) que inclua uma tabela de data totalmente configurada. Compartilhe o modelo com todos os modeladores em sua organização. Assim, sempre que alguém desenvolver um novo modelo, poderá começar com uma tabela de data definida consistentemente.

## <a name="use-auto-datetime"></a>Usar data/hora automática

A opção de [Data/hora automática](../transform-model/desktop-auto-date-time.md) fornece inteligência de dados temporais conveniente, rápida e fácil de usar. Autores de relatórios podem trabalhar com a inteligência de dados temporais para filtrar, agrupar e detalhar os períodos do calendário.

Recomendamos manter a opção de data/hora automática habilitada somente ao trabalhar com períodos de calendário e quando você tiver requisitos de modelo simplistas em relação ao tempo. O uso dessa opção também pode ser conveniente ao criar modelos ad hoc ou ao realizar exploração ou criação de perfil de dados. Porém, essa abordagem não dá suporte a um design de tabela de data única que possa propagar filtros para várias tabelas. Para obter mais informações, confira [Diretrizes de data/hora automática no Power BI Desktop](auto-date-time.md).

## <a name="connect-with-power-query"></a>Conectar-se com o Power Query

Quando sua fonte de dados já tiver uma tabela de data, recomendamos usá-la como a origem da tabela de data do modelo. Normalmente, esse é o caso quando você está se conectando a um data warehouse, pois ele terá uma tabela de dimensão de data. Dessa forma, seu modelo utiliza uma única fonte de verdade para o tempo em sua organização.

Caso você esteja desenvolvendo um modelo DirectQuery e sua fonte de dados não inclua uma tabela de data, recomendamos que você adicione uma tabela de data à fonte de dados. Ela deve atender a todos os requisitos de modelagem de uma tabela de data. Em seguida, você pode usar o Power Query para se conectar à tabela de data. Dessa forma, seus cálculos de modelo podem aproveitar os recursos de inteligência de dados temporais do DAX.

## <a name="generate-with-power-query"></a>Gerar com o Power Query

Você pode gerar uma tabela de data com o Power Query. Aqui estão duas entradas de blog que mostram como:

- [Criar uma dimensão de data com um script do Power Query](https://www.mattmasson.com/2014/02/creating-a-date-dimension-with-a-power-query-script/) por Matt Masson
- [Gerar uma tabela de dimensão de data no Power Query](https://blog.crossjoin.co.uk/2013/11/19/generating-a-date-dimension-table-in-power-query/) por Chris Webb

> [!TIP]
> Se você não tiver um data warehouse ou outra definição consistente para o tempo em sua organização, considere o uso do Power Query para publicar um [fluxo de dados](../transform-model/service-dataflows-overview.md). Em seguida, peça que todos os modeladores de dados se conectem ao fluxo de dados para adicionar tabelas de data a seus modelos. O fluxo de dados se torna a única fonte de verdade para o tempo em sua organização.

Se você precisar gerar uma tabela de data, considere fazer isso com o DAX. Talvez você ache mais fácil. Além disso, é provável que seja mais conveniente, porque o DAX inclui alguma inteligência interna para simplificar a criação e o gerenciamento de tabelas de data.

## <a name="generate-with-dax"></a>Gerar com o DAX

Você pode gerar uma tabela de data em seu modelo criando uma tabela calculada usando as funções DAX [CALENDAR](/dax/calendar-function-dax) ou [CALENDARAUTO](/dax/calendarauto-function-dax). Cada função retorna uma tabela de data de coluna única. Em seguida, você pode estender a tabela calculada com colunas calculadas para dar suporte aos requisitos de filtragem e agrupamento de intervalo de datas.

- Use a função **CALENDAR** quando desejar definir um intervalo de datas. Passe dois valores: a data de início e a data de término. Esses valores podem ser definidos por outras funções DAX, como `MIN(Sales[OrderDate])` ou `MAX(Sales[OrderDate])`.
- Use a função **CALENDARAUTO** quando desejar que o intervalo de datas abranja automaticamente todas as datas armazenadas no modelo. Você pode passar um único parâmetro opcional que seja o mês final do ano (se for um ano civil, que termina em dezembro, não será necessário passar um valor). Essa é uma função útil, pois garante que os anos completos das datas sejam retornados – esse é um requisito para uma tabela de data marcada. Além disso, você não precisa gerenciar a extensão da tabela para anos futuros: quando uma atualização de dados é concluída, ela dispara o recálculo da tabela. Um recálculo estenderá automaticamente o intervalo de datas da tabela quando as datas de um novo ano forem carregadas no modelo.

## <a name="clone-with-dax"></a>Clonar com DAX

Quando seu modelo já tiver uma tabela de data e você precisar de uma tabela de data adicional, você poderá clonar facilmente a tabela existente. Esse é o caso quando a data é uma [dimensão com função múltipla](star-schema.md#role-playing-dimensions). Você pode clonar uma tabela criando uma tabela calculada. A expressão da tabela calculada é simplesmente o nome da tabela de data existente.

## <a name="next-steps"></a>Próximas etapas

Para obter mais informações relacionadas a este artigo, confira os seguintes recursos:

- [Data/hora automática no Power BI Desktop](../transform-model/desktop-auto-date-time.md)
- [Diretrizes de data/hora automática no Power BI Desktop](auto-date-time.md)
- [Definir e usar tabelas de datas no Power BI Desktop](../transform-model/desktop-date-tables.md)
- [Preparação de dados de autoatendimento no Power BI](../transform-model/service-dataflows-overview.md)
- [Função CALENDAR (DAX)](/dax/calendar-function-dax)
- [Função CALENDARAUTO (DAX)](/dax/calendarauto-function-dax)
- Dúvidas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
- Sugestões? [Contribuir com ideias para aprimorar o Power BI](https://ideas.powerbi.com/)
