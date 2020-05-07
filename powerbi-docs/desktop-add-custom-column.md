---
title: Adicionar uma coluna personalizada no Power BI Desktop
description: Criar rapidamente uma nova coluna personalizada no Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 10/18/2019
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 443053bc973005d3e2a655b1222d049a4251e7d7
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/05/2020
ms.locfileid: "73878869"
---
# <a name="add-a-custom-column-in-power-bi-desktop"></a>Adicionar uma coluna personalizada no Power BI Desktop

No Power BI Desktop, adicione com facilidade uma nova coluna personalizada de dados ao modelo usando o Editor de Consultas. Com o Editor de Consultas, crie e renomeie sua coluna personalizada para criar [consultas de fórmula M do PowerQuery](https://docs.microsoft.com/powerquery-m/quick-tour-of-the-power-query-m-formula-language) a fim de definir a coluna personalizada. As consultas de fórmula M do PowerQuery têm um [conjunto de conteúdo de referência de função abrangente](https://docs.microsoft.com/powerquery-m/power-query-m-function-reference). 

Quando você cria uma coluna personalizada no Editor de Consultas, o Power BI Desktop a adiciona como uma **Etapa Aplicada** às **Configurações de Consulta** da consulta. Ela pode ser alterada, movida ou modificada a qualquer momento.

![Página Adicionar Coluna Personalizada](media/desktop-add-custom-column/add-custom-column_01.png)

## <a name="use-query-editor-to-add-a-custom-column"></a>Usar o Editor de Consultas para adicionar uma coluna personalizada

Para começar a criar uma coluna personalizada, siga estas etapas:

1. Inicie o Power BI Desktop e carregue alguns dados.

2. Na guia **Página Inicial** da faixa de opções, selecione **Editar Consultas** e, em seguida, selecione **Editar Consultas** no menu.

   ![Selecionar Editar Consultas](media/desktop-add-custom-column/add-column-from-example_02.png)

   A janela do **Editor de Consultas** será exibida. 

2. Na guia **Adicionar Coluna** da faixa de opções, selecione **Coluna Personalizada**.

   ![Selecionar Coluna Personalizada](media/desktop-add-custom-column/add-custom-column_02.png)

   A janela **Adicionar Coluna Personalizada** será exibida.

## <a name="the-add-custom-column-window"></a>A janela Adicionar Coluna Personalizada

A janela **Adicionar Coluna Personalizada** apresenta os seguintes recursos: 
- Uma lista de colunas disponíveis, na lista **Colunas disponíveis** à direita.

- O nome inicial da coluna personalizada, na caixa **Nome da nova coluna**. Você pode renomear essa coluna.

- As [consultas de fórmula M do PowerQuery](https://docs.microsoft.com/powerquery-m/power-query-m-function-reference), na caixa **Fórmula de coluna personalizada**. Crie essas consultas criando a fórmula na qual a nova coluna personalizada é definida. 

   ![Página Adicionar Coluna Personalizada](media/desktop-add-custom-column/add-custom-column_03.png)

## <a name="create-formulas-for-your-custom-column"></a>Criar fórmulas para a coluna personalizada

1. Selecione uma coluna na lista **Colunas disponíveis** à direita e, em seguida, selecione **Inserir** abaixo da lista para adicioná-las à fórmula de coluna personalizada. Adicione também uma coluna clicando duas vezes nela na lista.

2. Conforme você insere a fórmula e cria a coluna, observe o indicador na parte inferior da janela **Adicionar Coluna Personalizada**. 

   Se não houver erros, você verá uma marca de seleção verde e a mensagem *Nenhum erro de sintaxe foi detectado*.

   ![Verificação de sintaxe bem-sucedida na página Adicionar Coluna Personalizada](media/desktop-add-custom-column/add-custom-column_04.png)

   Se houver um erro de sintaxe, você verá um ícone de aviso amarelo, juntamente com um link para o local em que o erro ocorreu na fórmula.

   ![Erro na página Adicionar Coluna Personalizada](media/desktop-add-custom-column/add-custom-column_05.png)

3. Selecione **OK**. 

   O Power BI Desktop adiciona a coluna personalizada ao modelo e adiciona a etapa **Personalização Adicionada** à lista **Etapas Aplicadas** da consulta em **Configurações de Consulta**.

   ![Coluna personalizada adicionada às Configurações de Consulta](media/desktop-add-custom-column/add-custom-column_06.png)

4. Para modificar a coluna personalizada, clique duas vezes na etapa **Personalização Adicionada** na lista **Etapas Aplicadas**. 

   A janela **Adicionar Coluna Personalizada** será exibida com a fórmula de coluna personalizada que você criou.

## <a name="use-the-advanced-editor-for-custom-columns"></a>Usar o Editor Avançado para colunas personalizadas

Depois de criar a consulta, use também o **Editor Avançado** para modificar qualquer etapa da consulta. Para fazer isso, siga estas etapas:

1. Na janela do **Editor de Consultas**, selecione a guia **Exibir** na faixa de opções. 

2. Selecione **Editor Avançado**.

   A página do **Editor Avançado** será exibida, o que dá a você controle total sobre a consulta. 

   ![Página do Editor Avançado](media/desktop-add-custom-column/add-custom-column_07.png)

   
## <a name="next-steps"></a>Próximas etapas

- Você pode criar uma coluna personalizada de outras formas, como a criação de uma coluna com base nos exemplos fornecidos ao Editor de Consultas. Para obter mais informações, confira [Adicionar uma coluna de um exemplo no Power BI Desktop](desktop-add-column-from-example.md).

- Para obter informações de referência da linguagem M do Power Query, confira [Referência de função M do Power Query](/powerquery-m/power-query-m-function-reference).

