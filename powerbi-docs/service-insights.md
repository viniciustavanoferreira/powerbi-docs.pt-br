---
title: Gerar informações sobre os dados automaticamente com o Power BI
description: Saiba como obter informações sobre seus conjuntos de dados e blocos de painéis.
author: maggiesMSFT
ms.reviewer: ''
featuredvideoid: et_MLSL2sA8
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 08/06/2019
ms.author: maggies
LocalizationGroup: Dashboards
ms.openlocfilehash: 5f571cabcc413947713cd232863b3ecad910436d
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/05/2020
ms.locfileid: "73872236"
---
# <a name="generate-data-insights-automatically-with-power-bi"></a>Gerar informações sobre os dados automaticamente com o Power BI
Você tem um novo conjunto de dados e não sabe exatamente por onde começar?  Você precisa criar um painel rapidamente?  Deseja procurar informações que você pode ter perdido?

Execute insights rápidos para gerar visualizações interativas e interessantes com base em seus dados. Os Insights Rápidos podem ser executados em um conjunto de dados inteiro (insights rápidos) ou em um bloco de painéis específico (insights com escopo). Você pode até mesmo executar insights em um insight!

> [!NOTE]
> O Insights não funciona com DirectQuery; ele apenas funciona com os dados carregados no Power BI.
> 

O recurso de insights tem como base um crescente [conjunto de algoritmos analíticos avançados](service-insight-types.md) desenvolvido em conjunto com a Microsoft Research, os quais continuaremos a utilizar para permitir que mais pessoas encontrem informações em seus dados de maneiras novas e intuitivas.

## <a name="run-quick-insights-on-a-dataset"></a>Executar insights rápidos em um conjunto de dados
Veja a Amanda executar insights rápidos em um conjunto de dados, abrir um insight no modo de foco, fixar um desses insights como um bloco no painel dela e, em seguida, obter insights para um bloco do painel.

<iframe width="560" height="315" src="https://www.youtube.com/embed/et_MLSL2sA8" frameborder="0" allowfullscreen></iframe>


Agora é sua vez. Explore insights usando o [exemplo de Análise de Qualidade de Fornecedor](sample-supplier-quality.md).

1. Na guia **Conjuntos de dados**, selecione **Mais opções** (...) e **Obter insights rápidos**.
   
    ![Guia Conjuntos de dados](media/service-insights/power-bi-ellipses.png)
   
    ![Menu de reticências](media/service-insights/power-bi-tab.png)
2. O Power BI usa [vários algoritmos](service-insight-types.md) para pesquisar tendências no conjunto de dados.
   
    ![Caixa de diálogo Procurando por insights](media/service-insights/pbi_autoinsightssearching.png)
3. Em poucos segundos, suas informações estão prontas.  Selecione **Exibir insights** para exibir as visualizações.
   
    ![Mensagem de êxito](media/service-insights/pbi_autoinsightsuccess.png)
   
    > [!NOTE]
    > Alguns conjuntos de dados não podem gerar insights porque os dados não são estatisticamente significativos.  Para saber mais, veja [Otimizar seus dados para insights](service-insights-optimize.md).
    > 
    
4. As visualizações são exibidas em uma tela especial dos **Insights Rápidos** com até 32 cartões de insights separados. Cada cartão contém um gráfico e uma breve descrição.
   
    ![Tela Insights Rápidos](media/service-insights/power-bi-insights.png)

## <a name="interact-with-the-insight-cards"></a>Interagir com os cartões de insights

1. Passe o mouse sobre um cartão e selecione o ícone de alfinete para adicionar a visualização a um dashboard.

2. Passe o mouse sobre um cartão, selecione **Mais opções** (...) e **Exibir insights**. 

    A tela de insights é aberta no Modo de foco.
   
    ![Modo de foco do insight](media/service-insights/power-bi-insight-focus.png)
3. No modo de Foco você pode:
   
   * Filtrar as visualizações. Se o painel **Filtros** ainda não estiver aberto, expanda-o selecionando a seta no lado direito da janela.

       ![Menu expandido Filtros de Insight](media/service-insights/power-bi-insights-filter-new.png)
   * Fixe o cartão de insight em um dashboard selecionando **Fixar visual**.
   * Execute insights no próprio cartão, que geralmente é denominado como *insights com escopo*. No canto superior direito, selecione o ícone de lâmpada ![ícone Obter Insights](media/service-insights/power-bi-bulb-icon.png) ou **Obter Insights**.
     
       ![Ícone Obter Insights](media/service-insights/pbi-autoinsights-tile.png)
     
     O insight é exibido à esquerda e novos cartões, com base apenas nos dados daquele único insight, são exibidos à direita.
     
       ![Insights sobre insights](media/service-insights/power-bi-insights-on-insights-new.png)
4. Para voltar à tela original de insights, no canto superior esquerdo, selecione **Sair do modo de foco**.

## <a name="run-insights-on-a-dashboard-tile"></a>Executar insights em um bloco do painel
Em vez de buscar insights em um conjunto de dados inteiro, restrinja sua pesquisa para realizar um insight com escopo nos dados usados para criar um único bloco de dashboard. 

1. Abra um dashboard.
2. Passe o mouse sobre um bloco. Selecione **Mais opções** (...) e **Exibir insights**. O bloco é aberto no [modo de foco](service-focus-mode.md) com os cartões de insights exibidos à direita.    
   
    ![Modo de foco](media/service-insights/pbi-insights-tile.png)    
3. Algum insight desperta seu interesse? Selecione esse cartão de insights para se aprofundar ainda mais. O insight selecionado aparece à esquerda e novos insights, com base apenas nos dados daquele único insight, são exibidos à direita.    
4. Continue examinando seus dados e, quando encontrar um insight interessante, fixe-o ao seu painel selecionando **Fixar visual** no canto superior direito.

## <a name="next-steps"></a>Próximas etapas
- Se você for proprietário de um conjunto de dados, [otimize-o para os Insights Rápidos](service-insights-optimize.md).
- Saiba mais sobre os [tipos de Insights Rápidos disponíveis](service-insight-types.md).

Mais perguntas? [Experimente a Comunidade do Power BI](https://community.powerbi.com/).

