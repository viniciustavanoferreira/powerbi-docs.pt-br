---
title: Exibição de dados no Power BI Desktop
description: Exibição de dados no Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: how-to
ms.date: 05/05/2020
ms.author: davidi
LocalizationGroup: Model your data
ms.openlocfilehash: 6585c0e20fb0e63d366dfc8da17949ac03d42512
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85223747"
---
# <a name="work-with-data-view-in-power-bi-desktop"></a>Trabalhar com a exibição Dados no Power BI Desktop

A *exibição de Dados* ajuda você a inspecionar, explorar e compreender os dados no modelo do *Power BI Desktop*. É diferente do modo como você vê tabelas, colunas e dados no *Editor do Power Query*. Com a exibição de Dados, você examina seus dados *depois* que eles são carregados no modelo.

> [!NOTE]
> Como a exibição de Dados mostra os dados depois que eles são carregados no modelo, o ícone de exibição de Dados não estará visível se todas as fontes de dados forem baseadas no DirectQuery. 

Quando está modelando seus dados, às vezes, você deseja ver o que está realmente em uma tabela ou uma coluna, sem criar um visual na tela de relatório. Talvez você queira ver imediatamente abaixo do nível de linha. Essa habilidade é especialmente útil quando você está criando medidas e colunas calculadas ou precisa identificar um tipo ou uma categoria de dados.

Vamos examinar mais detalhadamente alguns dos elementos encontrados na exibição de Dados.

![Exibição de dados no Power BI Desktop](media/desktop-data-view/dataview_fullscreen.png)

1. **Ícone da exibição de Dados**. Selecione esse ícone para entrar na exibição de Dados.

2. **Grade de Dados**. Essa área mostra a tabela selecionada e todas as colunas e linhas presentes nela. As colunas ocultadas na exibição de *Relatório* ficam esmaecidas. Você pode clicar com o botão direito do mouse em uma coluna para ver as opções.

3. **Faixa de opções de modelagem**. Aqui, você pode gerenciar relações, criar cálculos e alterar o tipo de dados, o formato e a categoria de dados de uma coluna.

4. **Barra de fórmulas**. Insira fórmulas DAX (Data Analysis Expression) para medidas e colunas calculadas.

5. **Pesquisa**. Pesquise uma tabela ou uma coluna no modelo.

6. **Lista de campos**. Selecione uma tabela ou uma coluna a ser exibida na grade de dados.

## <a name="filtering-in-data-view"></a>Filtragem na exibição de Dados

Você também pode filtrar e classificar dados na exibição de Dados. Cada coluna mostra um ícone que identifica a direção de classificação, se aplicada.

![Classificar e filtrar na Exibição de Dados no Power BI Desktop](media/desktop-data-view/dataview_sort-and-filter.png)

Você pode filtrar valores individuais ou usar a filtragem avançada com base nos dados da coluna.

> [!NOTE]
> Quando um modelo do Power BI for criado em uma cultura diferente da interface do usuário atual, a caixa de pesquisa não será exibida na interface do usuário da exibição de Dados em nenhum item que não seja um campo de texto. Por exemplo, isso se aplica a um modelo criado no inglês dos EUA que você vê em espanhol.


## <a name="next-steps"></a>Próximas etapas

Você pode fazer de tudo com o Power BI Desktop. Para obter mais informações sobre seus recursos, consulte as seguintes fontes:

* [O que é o Power BI Desktop?](../fundamentals/desktop-what-is-desktop.md)
* [Visão geral de consulta com o Power BI Desktop](../transform-model/desktop-query-overview.md)
* [Tipos de dados no Power BI Desktop](desktop-data-types.md)
* [Formatar e combinar dados com o Power BI Desktop](desktop-shape-and-combine-data.md)
* [Tarefas comuns de consulta no Power BI Desktop](../transform-model/desktop-common-query-tasks.md)
