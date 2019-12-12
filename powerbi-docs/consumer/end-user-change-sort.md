---
title: Alterar como um gráfico é classificado em um relatório
description: Altere como um gráfico é classificado em um relatório do Power BI
author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 12/01/2019
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: fdd43320fec2b96aa708cb5bb1a21e269a117d2a
ms.sourcegitcommit: e492895259aa39960063f9b337a144a60c20125a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74830605"
---
# <a name="change-how-a-chart-is-sorted-in-a-power-bi-report"></a>Altere como um gráfico é classificado em um relatório do Power BI

[!INCLUDE [power-bi-service-new-look-include](../includes/power-bi-service-new-look-include.md)]


> [!IMPORTANT]
> **Este artigo destina-se a usuários do Power BI que não têm permissões de edição para o relatório ou conjunto de relatórios. Para obter instruções mais detalhadas sobre a classificação, leia [Classificar por coluna no Power BI Desktop](../desktop-sort-by-column.md)** .

No serviço do Power BI, é possível alterar a aparência de um visual classificando-o por diferentes campos de dados. Ao alterar a maneira como você classifica um visual, é possível realçar as informações que você deseja transmitir.

Visuais em um dashboard não podem ser classificados, mas em um relatório do Power BI, você pode classificar a maioria das visualizações 

Se estiver usando dados numéricos (como valores de vendas) ou dados de texto (como nomes de estado), você pode classificar suas visualizações da forma que quiser. O Power BI oferece muita flexibilidade para a classificação e menus rápidos para você usar. 

## <a name="get-started"></a>Introdução

Para começar, selecione qualquer visual e escolha **Mais ações** (...).  Há três opções de classificação: **Classificação decrescente**, **Classificação crescente** e **Classificar por**. 
    

![gráfico de barras classificado pelo eixo X em ordem alfabética](media/end-user-change-sort/power-bi-more-actions.png)

### <a name="sort-alphabetically-or-numerically"></a>Classificar em ordem alfabética ou numericamente

Os visuais podem ser classificados em ordem alfabética segundo os nomes das categorias no visual ou pelos valores numéricos de cada categoria. Por exemplo, este gráfico é classificado alfabeticamente pela categoria **Nome** da loja no eixo X.

![gráfico de barras classificado pelo eixo X em ordem alfabética](media/end-user-change-sort/powerbi-sort-category.png)

É fácil alterar a classificação de uma categoria (nome do repositório) para um valor (vendas por pés quadrados). Selecione **Mais ações** (...) e escolha **Classificar por**. Selecione um valor numérico usado no visual.  Neste exemplo, selecionamos **Vendas por pé quadrado**.

![Captura de tela mostrando a seleção de uma classificação e de um valor](media/end-user-change-sort/power-bi-sort-value.png)

Se necessário, altere a ordem de classificação entre crescente e decrescente.  Selecione **Mais ações** (...) novamente e escolha **Classificação decrescente** ou **Classificação crescente**. O campo usado para classificar ficará em negrito e terá uma barra amarela.

   ![vídeo mostrando a seleção classificar por e depois em ordem crescente, decrescente](media/end-user-change-sort/sort.gif)

> [!NOTE]
> Nem todos os visuais podem ser classificados. Por exemplo, os seguintes visuais não podem ser classificados: mapa de árvore, mapa, mapa coroplético, dispersão, medidor, cartão e cascata.

## <a name="saving-changes-you-make-to-sort-order"></a>Salvar as alterações feitas na ordem de classificação
Os relatórios do Power BI retêm os filtros, divisões, classificações e outras alterações de exibição de dados que você fizer. Portanto, se você sair de um relatório e retornar mais tarde, suas alterações de classificação serão salvas.  Se você quiser reverter as alterações para as configurações do designer do relatório, selecione **Redefinir para padrão** na barra de menus superior. 

![classificação persistente](media/end-user-change-sort/power-bi-reset.png)

No entanto, se o botão **Redefinir para padrão** estiver esmaecido, significará que o *designer* do relatório desabilitou a funcionalidade de salvar (persistir) as alterações.

<a name="other"></a>
## <a name="considerations-and-troubleshooting"></a>Considerações e solução de problemas

### <a name="sorting-using-other-criteria"></a>Classificando o uso de outros critérios
Às vezes, você deseja classificar o visual usando um campo diferente (não incluído no visual) ou outros critérios.  Por exemplo, talvez você queira classificar por mês em ordem sequencial (e não em ordem alfabética) ou talvez queira classificar por números inteiros em vez de por dígitos (exemplo, 0, 1, 9, 20 e não 0, 1, 20, 9).  Somente a pessoa que projetou o relatório pode fazer essas alterações para você. As informações de contato do *designer* podem ser encontradas ao selecionar o nome do relatório na barra de cabeçalho.

![Lista suspensa mostrando as informações de contato](media/end-user-change-sort/power-bi-contact.png)

## <a name="next-steps"></a>Próximas etapas
Mais sobre [Visualizações nos relatórios do Power BI](end-user-visualizations.md).

[Power BI – conceitos básicos](end-user-basic-concepts.md)
