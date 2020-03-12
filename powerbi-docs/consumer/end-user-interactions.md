---
title: Entender a interação de elementos visuais em um relatório
description: Documentação para os usuários finais do Power BI que explica como os visuais interagem em uma página de relatório.
author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 03/11/2020
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: fb7bf439cdf2f7ebd6058aba6b147f800b9cf258
ms.sourcegitcommit: 480bba9c745cb9af2005637e693c5714b3c64a8a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/11/2020
ms.locfileid: "79113035"
---
# <a name="how-visuals-cross-filter-each-other-in-a-power-bi-report"></a>Como os visuais realizam filtragem cruzada entre si em um relatório do Power BI

[!INCLUDE[consumer-appliesto-yyny](../includes/consumer-appliesto-yyny.md)]

Um dos melhores recursos do Power BI é a maneira com que todos os elementos visuais na página de um relatório são interconectados. Se você selecionar um ponto de dados em um dos elementos visuais, todos os outros visuais na página que contêm esses dados serão alterados, com base nessa seleção. 

![vídeo de interação de visuais](media/end-user-interactions/interactions.gif)

## <a name="how-visuals-interact-with-each-other"></a>Como os visuais interagem

Por padrão, a seleção de um ponto de dados em um visual em uma página de relatório fará filtro cruzado ou realce cruzado dos outros visuais na página. A interação exata dos visuais em uma página é definida pelo relatório *designer*. Os *designers* têm opções para ativar e desligar as interações visuais e alterar o comportamento padrão de filtragem cruzada, realce cruzado e [drilling](end-user-drill.md). 

Caso ainda não tenha encontrado as hierarquias nem o drilling, saiba tudo sobre eles lendo [Fazer drill down no Power BI](end-user-drill.md). 

### <a name="cross-filtering-and-cross-highlighting"></a>Filtragem cruzada e destaque cruzado

A filtragem cruzada e o realce cruzado podem ser úteis para identificar como um valor nos dados contribui para outro. Os termos *filtro cruzado* e *realce cruzado* são usados para distinguir o comportamento descrito aqui do que acontece quando você usa o painel **Filtros** para filtrar e realçar visuais.  

Vamos definir esses termos ao examinarmos as páginas de relatório abaixo. O gráfico de rosca "Volume total da categoria por segmento" contém dois valores: "Moderação" e "Conveniência". 

![Página de relatório](media/end-user-interactions/power-bi-interactions-before.png)

1. Vamos ver o que acontece quando selecionamos **Moderação**.

    ![Página de relatório após a seleção do segmento Moderação do gráfico de rosca](media/end-user-interactions/power-bi-interactions-after.png)

2. A **filtragem cruzada** remove os dados não aplicáveis. A seleção de **Moderação** no gráfico de rosca faz a filtragem cruzada do gráfico de linhas. Agora, o gráfico de linhas só exibe pontos de dados para o segmento Moderação. 

3. O **destaque cruzado** retém todos os pontos de dados originais, mas esmaece a parte que não se aplica à seleção. A seleção de **Moderação** no gráfico de rosca faz o destaque cruzado do gráfico de colunas. O gráfico de colunas esmaece todos os dados que se aplicam ao segmento Conveniência e realça todos os dados que se aplicam ao segmento Moderação. 


## <a name="considerations-and-troubleshooting"></a>Considerações e solução de problemas
- Se o relatório tiver um visual que dá suporte ao [drilling](end-user-drill.md), por padrão, o drilling de um visual não afetará os outros visuais na página de relatório. No entanto, o *designer* do relatório pode alterar esse comportamento. Sendo assim, verifique seus visuais com drilling aplicado para ver se **filtros de drilling de outros visuais** foram ativados pelo *designer* do relatório.
    
- Os filtros no nível do visual são retidos quando há a filtragem cruzada e o destaque cruzado de outros visuais na página de relatório. Portanto, se o visualA tiver filtros no nível do visual aplicados pelo Designer de Relatórios ou por você e você usar o visualA para interagir com o visualB, os filtros no nível do visual do visualA serão aplicados ao visualB.

    ![Página de relatório após a seleção do segmento Moderação do gráfico de rosca](media/end-user-interactions/power-bi-visual-filters.png)

## <a name="next-steps"></a>Próximas etapas
[Como usar filtros de relatório](../power-bi-how-to-report-filter.md)    


[Sobre filtragem e realce](end-user-report-filter.md). 
