---
title: Parte 1, Adicionar visualizações a um relatório do Power BI
description: Parte 1, Adicionar visualizações a um relatório do Power BI
author: mihart
ms.reviewer: rien
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/06/2020
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: fda9c63abbf20eb08adbebacc3f9351c80a2847b
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83148017"
---
# <a name="add-visuals-to-a-power-bi-report-part-1"></a>Adicionar visuais a um relatório do Power BI (parte 1)

[!INCLUDE[consumer-appliesto-nyyn](../includes/consumer-appliesto-nyyn.md)]    

[!INCLUDE [power-bi-visuals-desktop-banner](../includes/power-bi-visuals-desktop-banner.md)]

Este artigo apresenta uma breve introdução à criação de uma visualização em um relatório. Ele se aplica ao serviço do Power BI e ao Power BI Desktop. Para ver conteúdo mais avançado, [veja a Parte 2](power-bi-report-add-visualizations-ii.md) desta série.

## <a name="prerequisites"></a>Pré-requisitos

Este tutorial usa o [arquivo PBIX de Vendas e Marketing](https://download.microsoft.com/download/9/7/6/9767913A-29DB-40CF-8944-9AC2BC940C53/Sales%20and%20Marketing%20Sample%20PBIX.pbix).

1. Na seção superior esquerda da barra de menus do Power BI Desktop, selecione **Arquivo** > **Abrir**
   
2. Localize sua cópia do **Arquivo PBIX de exemplo de vendas e marketing**

1. Abra o **Arquivo PBIX de exemplo de vendas e marketing** na exibição de relatório ![Captura de tela do ícone de exibição de relatório](media/power-bi-visualization-kpi/power-bi-report-view.png).

1. Selecionar ![Captura de tela da guia amarela.](media/power-bi-visualization-kpi/power-bi-yellow-tab.png) para adicionar uma nova página.

> [!NOTE]
> Compartilhar seu relatório com um colega do Power BI exige que você tenha licenças de Power BI Pro individuais ou que o relatório seja salvo na capacidade Premium. Confira [compartilhamento de relatórios](../collaborate-share/service-share-reports.md)

## <a name="add-visualizations-to-the-report"></a>Adicionar visualizações ao relatório

1. Crie uma visualização selecionando um campo no painel **Campos** .

    Comece com um campo numérico como **Vendas** > **VendasTotais**. O Power BI cria um gráfico de colunas com uma coluna.

    ![Captura de tela de um gráfico de colunas com uma única coluna.](media/power-bi-report-add-visualizations-i/power-bi-column-chart.png)

    Ou comece com um campo de categoria, como **Nome** ou **Produto**. O Power BI cria uma tabela e adiciona esse campo ao espaço **Valores**.

    ![Captura de tela de uma tabela com quatro categorias](media/power-bi-report-add-visualizations-i/power-bi-product.png)

    Ou, comece com um campo com informações geográficas, como **Área Geográfica** > **Cidade**. O Power BI e o Bing Mapas criam uma visualização de mapa.

    ![Captura de tela de uma visualização de mapa.](media/power-bi-report-add-visualizations-i/power-bi-maps.png)

## <a name="change-the-type-of-visualization"></a>Alterar o tipo de visualização

 Crie uma visualização e, em seguida, alterar o tipo. 
 
 1. Selecione **Produto** > **Categoria** e **Produto** > **Contagem do Produto** para adicioná-los ao espaço **Valores**.

    ![Captura de tela do painel Campos com o espaço Valores destacado.](media/power-bi-report-add-visualizations-i/power-bi-create-visual.png)

1. Altere a visualização para um gráfico de colunas selecionando o ícone de **gráfico de colunas empilhadas**.

   ![Captura de tela do painel Visualizações com o ícone do gráfico de colunas empilhadas destacado.](media/power-bi-report-add-visualizations-i/power-bi-convert.png)

1. Para alterar a maneira como o visual é classificado, selecione **Mais ações** (...).  Use as opções de classificação para alterar a direção da classificação (crescente ou decrescente) e alterar a coluna que está sendo usada para classificar (**Classificar por**).

   ![Captura de tela da lista suspensa Mais ações.](media/power-bi-report-add-visualizations-i/power-bi-sort.png)
  
## <a name="next-steps"></a>Próximas etapas

 Continue em:

* [Parte 2: Adicionar visualizações a um relatório do Power BI](power-bi-report-add-visualizations-ii.md)

* [Interaja com as visualizações](../consumer/end-user-reading-view.md) no relatório.
