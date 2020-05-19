---
title: Parte 2, Adicionar visualizações a um relatório do Power BI
description: Parte 2, Adicionar visualizações a um relatório do Power BI
author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/06/2020
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: c8b0012224d145f40cb6b9784da1a40957efce50
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83277768"
---
# <a name="add-visuals-to-a-power-bi-report-part-2"></a>Adicionar visuais a um relatório do Power BI (parte 2)

[!INCLUDE[consumer-appliesto-nyyn](../includes/consumer-appliesto-nyyn.md)]    

[!INCLUDE [power-bi-visuals-desktop-banner](../includes/power-bi-visuals-desktop-banner.md)]

Na [Parte 1](power-bi-report-add-visualizations-i.md), você criou uma visualização básica marcando as caixas de seleção ao lado dos nomes de campo.  Na parte 2, você aprenderá como usar o arrastar e soltar e fazer uso integral dos painéis **Campos** e **Visualizações** para criar e modificar as visualizações.


## <a name="create-a-new-visualization"></a>Criar uma nova visualização
Neste tutorial, vamos examinar nosso conjunto de dados de Análise de Varejo e criar algumas visualizações chave.

## <a name="prerequisites"></a>Pré-requisitos

Este tutorial usa o [Arquivo PBIX de exemplo de análise de varejo](https://download.microsoft.com/download/9/6/D/96DDC2FF-2568-491D-AAFA-AFDD6F763AE3/Retail%20Analysis%20Sample%20PBIX.pbix).

1. Na seção superior esquerda da barra de menus do Power BI Desktop, selecione **Arquivo** > **Abrir**
   
2. Encontre sua cópia do **arquivo PBIX de exemplo de Análise de Varejo**

1. Abra o **arquivo PBIX de exemplo de Análise de Varejo** na exibição de relatório ![Captura de tela do ícone de exibição de relatório](media/power-bi-visualization-kpi/power-bi-report-view.png).

1. Selecionar ![Captura de tela da guia amarela.](media/power-bi-visualization-kpi/power-bi-yellow-tab.png) para adicionar uma nova página.

## <a name="add-visualizations-to-the-report"></a>Adicionar visualizações ao relatório

Crie uma visualização selecionando um campo no painel **Campos** . O tipo de visualização criada dependerá do tipo de campo selecionado. O Power BI usa o tipo de dados para determinar qual visualização empregar na exibição dos resultados. Você pode alterar a visualização usada selecionando um ícone diferente no painel Visualizações. Lembre-se de que nem todas as visualizações são capazes de exibir seus dados. Por exemplo, os dados geográficos não serão bem exibidos usando um gráfico de funil ou um gráfico de linhas. 


### <a name="add-an-area-chart-that-looks-at-this-years-sales-compared-to-last-year"></a>Adicionar um gráfico de área que examine as vendas deste ano em comparação com o ano passado

1. Na tabela **Vendas**, selecione **Vendas deste Ano** > **Valor** e **Vendas do Ano Passado**. O Power BI cria um gráfico de colunas.  Esse gráfico é interessante e você deseja investigar mais a fundo. O que torna as vendas semelhantes por mês?  
   
   ![Captura de tela mostrando um gráfico de colunas](media/power-bi-report-add-visualizations-ii/power-bi-start.png)

2. Na tabela Tempo, arraste **FiscalMonth** para a área **Eixo**.  
   ![Captura de tela mostrando o gráfico de colunas tendo o FiscalMonth como eixo](media/power-bi-report-add-visualizations-ii/power-bi-fiscalmonth.png)

3. [Mude a visualização](power-bi-report-change-visualization-type.md) para um gráfico de área.  Há muitos tipos de visualização dentre as quais escolher – veja as [descrições de cada uma, dicas de melhores práticas e tutoriais](power-bi-visualization-types-for-reports-and-q-and-a.md) para ajudar a decidir qual tipo usar. Do painel Visualizações, selecione o ícone de gráfico de área ![Ícone de Gráfico de área do painel Visualizações](media/power-bi-report-add-visualizations-ii/power-bi-area-chart.png).

4. Classifique a visualização selecionando **Mais ações** e escolhendo **Classificar por** >  **FiscalMonth**.

5. [Redimensione a visualização](power-bi-visualization-move-and-resize.md) selecionando a visualização, captando um dos círculos da estrutura de tópicos e arrastando-o. Torne-a grande o suficiente para eliminar a barra de rolagem e pequeno o suficiente para nos dar espaço suficiente para adicionar outra visualização.
   
   ![captura de tela do visual de gráfico de área](media/power-bi-report-add-visualizations-ii/pbi_part2_7b.png)
6. [Salve o relatório](../create-reports/service-report-save.md).

### <a name="add-a-map-visualization-that-looks-at-sales-by-location"></a>Adicionar uma visualização do mapa que analisa as vendas por local

1. Na tabela **Loja**, selecione **Território**. Arraste **Pontuação Total** na área Tamanho. O Power BI reconhece que a Região é um local e cria uma visualização de mapa.  
   ![Gráfico da área](media/power-bi-report-add-visualizations-ii/power-bi-map1.png)

2. Adicione uma legenda.  Para ver os dados por nome de loja, arraste a **Cadeia** > **de Lojas** para a área de Legenda.  
   ![tela de relatório com uma seta da Cadeia na lista de campos para a Cadeia no bucket de Legenda](media/power-bi-report-add-visualizations-ii/power-bi-chain.png)

> [!NOTE]
> Compartilhar seu relatório com um colega do Power BI exige que você tenha licenças de Power BI Pro individuais ou que o relatório seja salvo na capacidade Premium. Confira [compartilhamento de relatórios](../collaborate-share/service-share-reports.md).

## <a name="next-steps"></a>Próximas etapas
* Mais sobre [Visualizações nos relatórios do Power BI](power-bi-report-visualizations.md).  
* Mais perguntas? [Experimente a Comunidade do Power BI](https://community.powerbi.com/)

