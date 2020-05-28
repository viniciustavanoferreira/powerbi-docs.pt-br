---
title: Diretrizes de data/hora automática no Power BI Desktop
description: Orientação para o uso da funcionalidade de data/hora automática no Power BI Desktop.
author: peter-myers
manager: asaxton
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 10/23/2019
ms.author: v-pemyer
ms.openlocfilehash: 69084048b46c77452bf94f04fd79a97c4f09af5b
ms.sourcegitcommit: a72567f26c1653c25f7730fab6210cd011343707
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83565984"
---
# <a name="auto-datetime-guidance-in-power-bi-desktop"></a>Diretrizes de data/hora automática no Power BI Desktop

Este artigo se destina a modeladores de dados que estão desenvolvendo modelos de Importação ou Compostos no Power BI Desktop. Ele fornece orientações, recomendações e considerações de uso da opção de _Data/hora automática_ do Power BI Desktop em situações específicas. Confira uma visão geral e uma introdução sobre a _Data/hora automática_ em [Data/hora automática no Power BI Desktop](../transform-model/desktop-auto-date-time.md).

A opção de _Data/hora automática_ fornece inteligência de dados temporais conveniente, rápida e fácil de usar. Autores de relatórios podem trabalhar com a inteligência de dados temporais para filtrar, agrupar e detalhar os períodos do calendário.

## <a name="considerations"></a>Considerações

A lista com marcadores a seguir descreve as considerações, e possíveis limitações, relacionadas ao uso da opção de _Data/hora automática_.

- **Aplica-se a todas ou a nenhuma:** quando está habilitada, a opção de _Data/hora automática_ se aplica a todas as colunas de data (exceto pelas colunas calculadas) nas tabelas de importação que não são os &quot;muitos&quot; lados de uma relação. Essa opção não pode ser habilitada ou desabilitada coluna por coluna.
- **Somente períodos do calendário:** as colunas de ano e trimestre referem-se a períodos do calendário. Isso significa que o ano começa em 1º de janeiro e termina em 31 de dezembro. Não é possível personalizar a data de início (ou término) do ano.
- **Personalização:** não é possível personalizar os valores usados para descrever períodos. Também não é possível incluir colunas adicionais para descrever outros períodos, como semanas, por exemplo.
- **Filtragem por ano:** os valores de coluna de **Trimestre**, **Mês** e **Dia** não incluem o valor do ano. Por exemplo, a coluna do **Mês** contém apenas os nomes dos meses (ou seja, janeiro, fevereiro etc.). Os valores não são totalmente autodescritivos e, em alguns modelos de relatório, podem não comunicar o contexto do filtro de ano.

    É por isso que é importante que os filtros ou agrupamentos ocorram na coluna de **Ano**. Ao fazer a busca detalhada usando o ano, a hierarquia será filtrada, a menos que o nível de **Ano** seja intencionalmente removido. Se não houver filtro ou grupo por ano, um agrupamento por mês, por exemplo, resumirá os valores de todos os anos nesse mês.
- **Filtragem de data de tabela única:** como cada coluna de data produz sua própria tabela de data/hora automática (oculta), não é possível aplicar um filtro de hora a uma tabela e propagá-lo para várias tabelas de modelo. Esse tipo de filtragem é um requisito de modelagem comum ao relatar vários assuntos (tabelas do tipo fato), como vendas e orçamento de vendas. Ao usar a data/hora automática, o autor do relatório precisará aplicar filtros a cada coluna de data diferente.
- **Tamanho do modelo:** para cada coluna de data que gera uma tabela de data/hora automática oculta, isso resultará em um tamanho de modelo aumentado e também estenderá o tempo de atualização de dados.
- **Outras ferramentas de relatório:** Não é possível trabalhar com tabelas de data/hora automática ao:
  - usar [Analisar no Excel](../collaborate-share/service-analyze-in-excel.md);
  - usar designers de consulta do Analysis Services para relatórios paginados do Power BI;
  - conectar-se ao modelo usando designers de relatório que não são do Power BI.

## <a name="recommendations"></a>Recomendações

Recomendamos manter a opção de _Data/hora automática_ habilitada somente ao trabalhar com períodos de calendário e com requisitos de modelo simplistas em relação ao tempo. O uso dessa opção também pode ser conveniente ao criar modelos ad hoc ou ao realizar exploração ou criação de perfil de dados.

Quando sua fonte de dados já define uma tabela de dimensões de data, essa tabela deve ser usada para definir consistentemente o tempo dentro da sua organização. Se sua fonte de dados for um data warehouse, esse certamente será o caso. Do contrário, você pode gerar tabelas de datas no seu modelo usando as funções DAX [CALENDAR](/dax/calendar-function-dax) ou [CALENDARAUTO](/dax/calendarauto-function-dax). Você pode adicionar colunas calculadas para dar suporte aos requisitos conhecidos de agrupamento e filtragem de tempo. Essa abordagem de projeto pode permitir que você crie uma única tabela de datas que se propague para todas as tabelas de fatos, possivelmente resultando em uma única tabela para aplicar filtros de tempo. Leia mais informações sobre a criação de tabelas de datas no artigo [Definir e usar tabelas de datas no Power BI Desktop](../transform-model/desktop-date-tables.md).

Se a opção de _Data/hora automática_ não for relevante para seus projetos, recomendamos desativá-la globalmente. Isso garantirá que todos os novos arquivos do Power BI Desktop criados por você não habilitem a opção de _Data/hora automática_.

## <a name="next-steps"></a>Próximas etapas

Para obter mais informações relacionadas a este artigo, confira os seguintes recursos:

- [Data/hora automática no Power BI Desktop](../transform-model/desktop-auto-date-time.md)
- [Definir e usar tabelas de datas no Power BI Desktop](../transform-model/desktop-date-tables.md)
- Perguntas? [Experimente perguntar para a Comunidade do Power BI](https://community.powerbi.com/)
- Sugestões? [Contribuir com ideias para aprimorar o Power BI](https://ideas.powerbi.com/)
