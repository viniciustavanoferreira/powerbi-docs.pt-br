---
title: Tipos de filtros nos relatórios do Power BI
description: Adicionar um filtro de página, um filtro de visualização ou um filtro de relatório a um relatório no Power BI
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 06/25/2019
ms.author: maggies
LocalizationGroup: Reports
ms.openlocfilehash: c96b4ebae574a3b6a6fa54c5f5dc99b5bc948a90
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/05/2020
ms.locfileid: "73874415"
---
# <a name="types-of-filters-in-power-bi-reports"></a>Tipos de filtros nos relatórios do Power BI

Os filtros não se comportam da mesma forma, pois não são criados de forma igual. O modo como você os cria influencia como eles se comportam no novo painel de filtros no modo de edição. Neste artigo, descrevemos os diferentes tipos de filtros: as diferentes maneiras de criá-los e para que eles são úteis. Veja como [adicionar filtros para relatórios](power-bi-report-add-filter.md). 

![Painel de filtros](media/power-bi-report-filter-types/power-bi-filter-pane.png)

Vamos começar com os dois tipos de filtro mais comuns: manual e automático.

## <a name="manual-filters"></a>Filtros manuais 

Os filtros manuais são os filtros que criadores de relatório arrastam e soltam em qualquer lugar no novo painel de filtros. Os usuários com permissão de edição para o relatório podem editar, excluir, limpar, ocultar, bloquear, renomear ou classificar este filtro no novo painel.

## <a name="automatic-filters"></a>Filtros automáticos 

Os filtros automáticos são os filtros adicionados automaticamente ao nível de visual do painel de filtro quando você cria um visual. Estes filtros são baseados nos campos que compõem seu visual. Os usuários com permissão de edição para o relatório podem editar, limpar, ocultar, bloquear, renomear ou classificar este filtro no novo painel. Eles não podem excluir filtros automáticos, porque o visual se refere a esses campos.

## <a name="more-advanced-filters"></a>Filtros mais avançados

Esses tipos de filtro s seguir são menos comuns, mas é importante entendê-los se forem exibidos em seu relatório. Além disso, você pode achá-los úteis ao criar o filtro para seu relatório.

## <a name="include-and-exclude-filters"></a>Filtros de inclusão e exclusão

Os filtros incluir e excluir são adicionados automaticamente ao painel de filtros quando você usa a funcionalidade de inclusão ou exclusão de um visual. Os usuários com permissão de edição para o relatório podem excluir, bloquear, ocultar ou classificar este filtro no novo painel. Eles não podem possível editar, limpar ou renomear um filtro de inclusão ou exclusão, pois ele está associado à funcionalidade incluir e excluir do visual.

![Filtro de exclusão](media/power-bi-report-filter-types/power-bi-filters-exclude.png)

## <a name="drill-down-filters"></a>Filtros de drill-down

Os filtros de drill-down são adicionados automaticamente ao painel de filtros quando você usa a funcionalidade de drill-down de um visual em seu relatório. Os usuários com permissão de edição para o relatório podem editar ou limpar o filtro no novo painel. Eles não podem excluir, ocultar, bloquear, renomear ou classificar este filtro porque ele está associado à funcionalidade de drill-down de visuais. Para remover o filtro de drill-dow, clique no botão de drill up do visual.

![Filtro de drill-down](media/power-bi-report-filter-types/power-bi-filters-drill-down.png)

## <a name="cross-drill-filters"></a>Filtros de drill cruzado

Os filtros de drill cruzado são adicionados automaticamente ao novo painel quando um filtro de drill-down é passado para outro visual na página do relatório por meio do recurso de filtro ou realce cruzado. Os usuários com permissão de edição para o relatório não podem excluir, limpar, ocultar, bloquear, renomear ou classificar este filtro, pois ele está associado à funcionalidade de drill-down dos visuais. Eles também não podem editar este filtro porque ele vem de um drilling down em outro visual. Para remover o filtro de drill-dow, clique no botão de drill up do visual que está passando o filtro.

## <a name="drillthrough-filters"></a>Filtros de Detalhamento

Os filtros de detalhamento são passados de uma página para outra por meio do recurso de detalhamento. Eles aparecem no painel de detalhamento. Há dois tipos de filtros de detalhamento. O primeiro tipo é aquele que invoca o detalhamento. Os editores do relatório podem editar, excluir, limpar, ocultar ou bloquear esse tipo de filtro. O segundo tipo é o filtro de detalhamento que é passado para o destino, com base nos filtros de nível de página da página de origem. Os editores do relatório podem editar, excluir ou limpar, esse tipo transitório de filtro de detalhamento. Eles não podem bloquear ou ocultar esse filtro para os usuários finais.

## <a name="url-filters"></a>Filtros de URL

Os filtros de URL são adicionados ao novo painel adicionando um parâmetro de consulta da URL. Os usuários com permissão de edição para o relatório podem editar, excluir ou limpar o filtro no novo painel. Eles não podem ocultar, bloquear ou classificar este filtro porque ele está associado ao parâmetro de URL. Para remover o filtro, você pode remover o parâmetro de URL. Aqui está um exemplo de URL com um parâmetro:

app.powerbi.com/groups/me/apps/*app-id*/reports/*report-id*/ReportSection?filter=Stores~2FStatus%20eq%20'Off'

![Filtro de URL](media/power-bi-report-filter-types/power-bi-filter-url.png)

Leia mais sobre [filtros de URL](service-url-filters.md).

## <a name="pass-through-filters"></a>Filtros de passagem

Os filtros de passagem são filtros de nível visual criados por meio de P e R. Os autores podem excluir, ocultar ou classificar esses filtros no novo painel. No entanto, eles não podem renomear, editar, limpar ou bloquear esses filtros.

![Filtro de passagem com P e R](media/power-bi-report-filter-types/power-bi-filters-qna.png)

## <a name="comparing-filter-types"></a>Comparação de tipos de filtro

Esta tabela compara o que os autores podem fazer com os diferentes tipos de filtros.

| Tipo de filtro | Editar | Limpar | Excluir | Ocultar | Bloquear | Classificação | Renomear |
|----|----|----|----|----|----|----|----|
| Filtros manuais | Y | Y | Y | Y | Y | Y | Y |
| Filtros automáticos | Y | Y | N | Y | Y | Y | Y |
| Incluir/Excluir filtros | N | N | Y | Y | Y | Y | N |
| Filtros de drill-down | Y | Y | N | N | N | N | N |
| Filtros de drill cruzado | N | N | N | N | N | N | N |
| Filtros de detalhamento (invoca detalhamento) | Y | Y | Y | Y | Y | N | N |
| Filtros de detalhamento (transitório) | Y | Y | Y | N | N | N | N |
| Filtros de URL: transitório | Y | Y | Y | N | N | N | N |
| Filtros de passagem | N | N | Y | Y | N | Y | N |



## <a name="next-steps"></a>Próximas etapas

[Adicionar filtros a relatórios](power-bi-report-add-filter.md)

[Faça um tour pelo painel Filtros do relatório](consumer/end-user-report-filter.md)

[Filtros e realce em relatórios](power-bi-reports-filters-and-highlighting.md)

Mais perguntas? [Experimente a Comunidade do Power BI](https://community.powerbi.com/)

