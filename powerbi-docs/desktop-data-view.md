---
title: Exibição de Dados no Power BI Desktop
description: Exibição de Dados no Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Model your data
ms.openlocfilehash: 8e1babaa39a1f52a06c69dcb9aac2441ca02452b
ms.sourcegitcommit: 97597ff7d9ac2c08c364ecf0c729eab5d59850ce
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75761262"
---
# <a name="work-with-data-view-in-power-bi-desktop"></a>Trabalhar com a exibição Dados no Power BI Desktop
A **Exibição de Dados** ajuda a inspecionar, explorar e compreender os dados no modelo do **Power BI Desktop**. É diferente do modo como você exibe tabelas, colunas e dados no **Editor de Consultas**. Com a Exibição de Dados, você está olhando para seus dados *após* eles terem sido carregados no modelo.

Quando você está modelando seus dados, às vezes você deseja ver o que está realmente em uma tabela ou coluna, sem criar um elemento visual na tela de relatório, geralmente imediatamente abaixo do nível de linha. Isso é útil principalmente quando você está criando colunas calculadas e medidas ou quando você precisa identificar um tipo de dados ou uma categoria de dados.

Vamos examinar com mais detalhes alguns dos elementos encontrados na **Exibição de Dados**.

![Exibição de dados no Power BI Desktop](media/desktop-data-view/dataview_fullscreen.png)

1. **Ícone da Exibição de Dados** – selecionar esse ícone para inserir a Exibição de Dados.

2. **Grade de Dados** – mostra a tabela selecionada e todas as colunas e linhas presentes nela. As colunas ocultadas na **Exibição de Relatório** ficam esmaecidas. Você pode clicar com o botão direito do mouse em uma coluna para ver as opções.

3. **Faixa de opções de modelagem** – aqui você pode gerenciar relações, criar cálculos e alterar o tipo de dados, o formato e a categoria de dados de uma coluna.

4. **Barra de fórmulas** – insira fórmulas DAX para medidas e colunas calculadas.

5. **Pesquisa** – pesquise uma tabela ou coluna no modelo.

6. **Lista de campos** – selecione uma tabela ou coluna a ser exibida na grade de dados.

## <a name="filtering-in-data-view"></a>Filtragem na Exibição de Dados

Você também pode filtrar e classificar dados na **Exibição de Dados**. Cada coluna mostra um ícone que identifica a direção de classificação (se aplicada).

![Classificar e filtrar na Exibição de Dados no Power BI Desktop](media/desktop-data-view/dataview_sort-and-filter.png)

Você pode filtrar valores individuais ou usar a filtragem avançada com base nos dados da coluna. 

> [!NOTE]
> Quando um modelo do Power BI é criado em uma cultura diferente do que a sua interface do usuário atual (por exemplo, o modelo foi criado em inglês dos EUA e você está visualizando-lo em espanhol), a caixa de pesquisa não é exibida na interface do usuário da Exibição de Dados para algo diferente de campos de texto.
