---
title: Adicionar vários campos a uma segmentação de hierarquia
description: Saiba como criar uma segmentação de hierarquia que contém vários campos em uma hierarquia.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: how-to
ms.date: 06/11/2020
ms.author: maggies
LocalizationGroup: Create reports
ms.openlocfilehash: 2b9c4a8f4695f8d701eba535180194d29dd8bdec
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.contentlocale: pt-BR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85238176"
---
# <a name="add-multiple-fields-to-a-hierarchy-slicer"></a>Adicionar vários campos a uma segmentação de hierarquia

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-desktop](../includes/yes-desktop.md)] [!INCLUDE [yes-service](../includes/yes-service.md)]

Caso deseje filtrar vários campos relacionados em uma única segmentação, faça isso criando o que é chamado de segmentação de *hierarquia*. Você pode criar essas segmentações no Power BI Desktop ou no serviço do Power BI.

:::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-hierarchy.png" alt-text="Segmentação de hierarquia no Power BI":::

Quando você adiciona vários campos à segmentação, por padrão, ela exibe uma seta ou uma *divisa* ao lado dos itens que podem ser expandidos para mostrar os itens no próximo nível.

:::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-hierarchy-arrow.png" alt-text="Lista suspensa da segmentação de hierarquia no Power BI":::
 
 
Quando você seleciona um ou mais filhos para um item, você vê um círculo semisselecionado no item de nível superior.
 
:::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-hierarchy-semi-selected.png" alt-text="Segmentação de hierarquia de seleção única no Power BI":::

## <a name="format-the-slicer"></a>Formatar a segmentação

O comportamento da segmentação não foi alterado. Você também pode mudar o estilo da sua segmentação como desejar. Por exemplo, é possível defini-la para o modo de seleção única. Ou você pode alternar entre uma lista e um menu suspenso. 

:::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-hierarchy-dropdown.png" alt-text="Segmentação de hierarquia formatada como uma segmentação suspensa":::

### <a name="change-the-expandcollapse-icon"></a>Alterar o ícone expandir/recolher

As segmentações de hierarquia têm algumas outras opções de formatação. Você pode alterar o ícone expandir/recolher da seta padrão para um sinal de mais/menos ou um acento circunflexo.

1. Selecione a segmentação e **Formato**.
1. Expanda **Itens** e selecione **Ícone expandir/recolher**.
1. Escolha entre **Divisa**, **Mais/menos** ou **Acento circunflexo**.
 
    :::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-hierarchy-caret.png" alt-text="Selecionar um ícone expandir/recolher para a segmentação de hierarquia":::
 
### <a name="change-the-indentation"></a>Alterar o recuo

Caso o espaço esteja apertado no relatório, você pode reduzir a quantidade de recuo dos itens filhos. Por padrão, o recuo é de 15 pixels, mas você pode aumentá-lo ou diminuí-lo. 

1. Selecione a segmentação e **Formato**.
1. Expanda **Itens** e arraste **Recuo de layout de nível** para aumentar ou diminuir. Você também pode digitar apenas um número na caixa.

    :::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-indentation.png" alt-text="Definir o recuo da segmentação de hierarquia":::

## <a name="next-steps"></a>Próximas etapas

- [Segmentações no Power BI](../visuals/power-bi-visualization-slicers.md)
- Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)