---
title: Visualizações de cartão (blocos de números grandes)
description: Criar uma Visualização de cartão no Power BI
author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/10/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 37b7a85534e1ad8f1f301994dea895e098758d1b
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/09/2019
ms.locfileid: "73870987"
---
# <a name="card-visualizations"></a>Visualizações de cartão

[!INCLUDE [power-bi-visuals-desktop-banner](../includes/power-bi-visuals-desktop-banner.md)]

Às vezes, um único número é a coisa mais importante que você deseja acompanhar no seu painel ou relatório do Power BI, como as vendas totais, a fatia de mercado ano após ano ou o total de oportunidades. Esse tipo de visualização é chamado de *Cartão*. Assim como em quase todas as visualizações nativas do Power BI, os cartões podem ser criados usando o editor de relatório ou P e R.

![visualização de cartão](media/power-bi-visualization-card/pbi-opptuntiescard.png)

## <a name="prerequisite"></a>Pré-requisito

Este tutorial usa o [arquivo PBIX de exemplo de Análise de Varejo](https://download.microsoft.com/download/9/6/D/96DDC2FF-2568-491D-AAFA-AFDD6F763AE3/Retail%20Analysis%20Sample%20PBIX.pbix)

1. Na seção superior esquerda da barra de menus, selecione **Arquivo** \> **Abrir**
   
2. Encontre sua cópia do **arquivo PBIX de exemplo de Análise de Varejo**

1. Abra o **arquivo PBIX de exemplo de Análise de Varejo** na exibição de relatório ![Captura de tela do ícone de exibição de relatório](media/power-bi-visualization-kpi/power-bi-report-view.png).

1. Selecionar ![Captura de tela da guia amarela.](media/power-bi-visualization-kpi/power-bi-yellow-tab.png) para adicionar uma nova página.

## <a name="option-1-create-a-card-using-the-report-editor"></a>Opção 1: Criar um cartão usando o editor de relatório

O primeiro método para criar um cartão é usar o editor de relatórios no Power BI Desktop.

1. Comece em uma página de relatório em branco e selecione **Armazenar** \> campo **Contagem de armazenamento aberto**.

    O Power BI cria um gráfico de colunas com um número.

   ![exemplo de gráfico de bloco com número](media/power-bi-visualization-card/pbi-overview-chart.png)

2. No painel de Visualizações, selecione o ícone de cartão.

   ![exemplo de cartão de título com número](media/power-bi-visualization-card/power-bi-card-visualization.png)

Agora, você criou com êxito um cartão com o editor de relatórios. Abaixo, temos a segunda opção para criar um cartão usando a caixa de perguntas de P e R.

## <a name="option-2-create-a-card-from-the-qa-question-box"></a>Opção 2: Criar um cartão a partir de uma caixa de perguntas de P e R
A caixa de perguntas de P e R é outra opção a ser usada ao criar um cartão. A caixa de perguntas de P e R está disponível na exibição de relatórios do Power BI Desktop.

1. Comece em uma página de relatório em branco

1. Na parte superior da janela, selecione o ícone **Fazer uma pergunta**. 

    O Power BI criará um cartão e uma caixa para sua pergunta. 

   ![local do ícone fazer uma pergunta](media/power-bi-visualization-card/power-bi-q-and-a-overview.png)

2. Por exemplo, digite "Total de vendas para Tina" na caixa de perguntas.

    A caixa da pergunta o ajuda dando sugestões e reformulações e, por fim, exibe o número total.  

   ![exemplo de caixa de perguntas](media/power-bi-visualization-card/power-bi-q-and-a-box.png)

   ![exemplo de cartão do método de pergunta](media/power-bi-visualization-card/power-bi-q-and-a-card.png)

Agora, você criou com êxito um cartão com a caixa de perguntas de P e R. Abaixo, estão as etapas para formatar seu cartão para suas necessidades específicas.

## <a name="format-a-card"></a>Formatar um cartão
Você tem várias opções para alterar rótulos, texto, cor e muito mais. A melhor maneira de aprender é criar um cartão e, em seguida, explorar o painel de formatação. Aqui estão algumas das opções de formatação disponíveis. 

O painel Formatação está disponível ao interagir com o cartão em um relatório. 

1. Comece selecionando o ícone de rolo de tinta para abrir o painel Formatação. 

    ![cartão com rolo de tinta destacado](media/power-bi-visualization-card/power-bi-format-card-2.png)

2. Com o cartão selecionado, expanda **Rótulo de dados** e altere a cor, o tamanho e a família de fontes. Se você tivesse milhares de repositórios, poderia usar **Exibir unidades** para mostrar o número de repositórios por milhares e controlar as casas decimais também. Por exemplo, 125,8K em vez de 125.832,00.

    ![exemplo de cartão com formato de dados](media/power-bi-visualization-card/power-bi-card-format-2.png)

3.  Expanda **Rótulo de categoria** e altere a cor e o tamanho.

    ![exemplo de cartão com categoria](media/power-bi-visualization-card/power-bi-card-format-category.png)

4. Expanda **Plano de fundo** e mova o controle deslizante para ligado.  Agora você pode alterar a cor da tela de fundo e a transparência.

    ![controle deslizante definido como LIGADO](media/power-bi-visualization-card/power-bi-format-color-2.png)

5. Continue para explorar as opções de formatação até que seu cartão esteja exatamente como você deseja. 

## <a name="considerations-and-troubleshooting"></a>Considerações e solução de problemas
Se uma caixa de perguntas não for exibida, entre em contato com o administrador do sistema ou de locatário.    

## <a name="next-steps"></a>Próximas etapas
[Gráficos de combinação no Power BI](power-bi-visualization-combo-chart.md)

[Tipos de visualização no Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)
