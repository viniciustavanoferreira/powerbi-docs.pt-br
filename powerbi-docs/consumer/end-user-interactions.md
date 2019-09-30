---
title: Entender a interação de elementos visuais em um relatório
description: Documentação para os usuários finais do Power BI que explica como os visuais interagem em uma página de relatório.
author: mihart
manager: kvivek
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 09/24/2019
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: b95df5c32d9058e4480d7af5e226a971ba581144
ms.sourcegitcommit: 02042995df12cc4e4b97eb8a369e62364eb5af36
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71256286"
---
# <a name="how-visuals-cross-filter-each-other-in-a-power-bi-report"></a>Como os visuais realizam filtragem cruzada entre si em um relatório do Power BI
Um dos melhores recursos do Power BI é a maneira com que todos os elementos visuais na página de um relatório são interconectados. Se você selecionar um ponto de dados em um dos elementos visuais, todos os outros visuais na página que contêm esses dados serão alterados, com base nessa seleção. 

![vídeo de interação de visuais](media/end-user-interactions/interactions.gif)

Por padrão, a seleção de um ponto de dados em uma visualização em uma página de relatório fará filtro cruzado, realce cruzado e detalhará as outras visualizações na página. 

Isso pode ser útil para identificar como um valor nos dados contribui para outro. Por exemplo, a seleção do segmento Moderação no gráfico de rosca realça a contribuição desse segmento em cada coluna no gráfico Total de unidades por Mês, além de filtrar o gráfico de linhas à direita.

![imagem da interação de visuais](media/end-user-interactions/power-bi-interactions.png)

Veja [Sobre filtragem e realce](../power-bi-reports-filters-and-highlighting.md). 

A interação exata dos visuais em uma página é definida pelo relatório *designer*. Designers têm opções para ativar e desativar a interações visuais e para alterar o comportamento padrão de filtragem cruzada, realce cruzado e análise. 
  
> [!NOTE]
> Os termos *filtro cruzado* e *realce cruzado* são usados para distinguir o comportamento descrito aqui do que acontece quando você usa o painel **Filtros** painel para filtrar e realçar visualizações.  

## <a name="considerations-and-troubleshooting"></a>Considerações e solução de problemas
- Se o relatório tem uma visualização que dá suporte ao [detalhamento](../power-bi-visualization-drill-down.md), por padrão, fazer uma busca detalhada em uma visualização não afeta as outras visualizações na página de relatório.     
- Se você usar o visualA para interagir com o visualB, os filtros no nível do visual do visualA serão aplicados ao visualB.

## <a name="next-steps"></a>Próximas etapas
[Como usar filtros de relatório](../power-bi-how-to-report-filter.md)
