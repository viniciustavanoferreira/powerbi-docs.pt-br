---
title: Alterar como um gráfico é classificado em um relatório
description: Altere como um gráfico é classificado em um relatório do Power BI
author: mihart
manager: kvivek
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 08/21/2019
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: 98a91b0651e7a357f0ba0462f6ba8734c64ab162
ms.sourcegitcommit: 52aa112ac9194f4bb62b0910c4a1be80e1bf1276
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/16/2019
ms.locfileid: "70302742"
---
# <a name="change-how-a-chart-is-sorted-in-a-power-bi-report"></a>Altere como um gráfico é classificado em um relatório do Power BI
Em um relatório do Power BI, você pode classificar a maioria das visualizações em ordem alfabética pelos nomes das categorias no gráfico, ou pelos valores numéricos de cada categoria. Por exemplo, este gráfico é classificado pela categoria **nome de loja**.

![gráfico de barras classificado pelo eixo X em ordem alfabética](media/end-user-change-sort/pbi_chartsortcategory.png)

É fácil alterar a classificação de uma categoria (nome do repositório) para um valor (vendas por pés quadrados).

1. Selecione as reticências (...) e escolha **Classificar por > Vendas por metro quadrado**.
2. Se necessário, selecione as reticências novamente e escolha **Classificar em ordem decrescente**.

   ![vídeo mostrando a seleção classificar por e depois em ordem crescente, decrescente](media/end-user-change-sort/sort.gif)

> [!NOTE]
> Nem todos os visuais podem ser classificados. Por exemplo, os seguintes visuais não podem ser classificados: mapa de árvore, mapa, mapa coroplético, dispersão, medidor, cartão e cascata.

## <a name="saving-changes-you-make-to-sort-order"></a>Salvar as alterações feitas na ordem de classificação
Os relatórios do Power BI retêm os filtros, divisões, classificações e outras alterações de exibição de dados que você fizer. Portanto, se você sair de um relatório e retornar mais tarde, suas alterações serão salvas.  Se você quiser reverter as alterações para as configurações do designer do relatório, selecione **Redefinir para padrão** na barra de menus superior. 

![classificação persistente](media/end-user-change-sort/power-bi-reset.png)

Se, no entanto, o botão **Redefinir para padrão** estiver esmaecido, significará que o designer do relatório desabilitou a funcionalidade de salvar (persistir) as alterações.

<a name="other"></a>
## <a name="sorting-using-other-criteria"></a>Classificando o uso de outros critérios
Às vezes, você deseja classificar seu visual usando um campo diferente ou outros critérios.  Por exemplo, talvez você queira classificar por mês (e não em ordem alfabética) ou talvez queira classificar por números inteiros em vez de por dígitos (exemplo, 0, 1, 9, 20 e não 0, 1, 20, 9).  

Em alguns casos, é permitido classificar o visual da maneira desejada, por exemplo, por mês.  Caso não seja possível, o motivo poderá ser que o conjunto de dados subjacente ao relatório precisa de alguns ajustes. Peça para o designer do relatório atualizar o conjunto de dados.

## <a name="next-steps"></a>Próximas etapas
Mais sobre [Visualizações nos relatórios do Power BI](end-user-visualizations.md).

[Power BI – conceitos básicos](end-user-basic-concepts.md)
