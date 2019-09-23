---
title: Parte 2, Adicionar visualizações a um relatório do Power BI
description: Parte 2, Adicionar visualizações a um relatório do Power BI
author: mihart
manager: kvivek
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 08/23/2018
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: c42d96fea37a6309908dd357425c3d0504e18397
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "61410033"
---
# <a name="part-2-add-visualizations-to-a-power-bi-report"></a>Parte 2, Adicionar visualizações a um relatório do Power BI
Na [Parte 1](power-bi-report-add-visualizations-ii.md), você criou uma visualização básica marcando as caixas de seleção ao lado dos nomes de campo.  Na parte 2, você aprenderá como usar o arrastar e soltar e fazer uso integral dos painéis **Campos** e **Visualizações** para criar e modificar as visualizações.

### <a name="prerequisites"></a>Pré-requisitos
- [Parte 1](power-bi-report-add-visualizations-ii.md)
- Power BI Desktop – visualizações podem ser adicionadas a relatórios usando o serviço Power BI ou Power BI Desktop. Este tutorial usa o Power BI Desktop. 
- [Exemplo de Análise de Varejo](http://download.microsoft.com/download/9/6/D/96DDC2FF-2568-491D-AAFA-AFDD6F763AE3/Retail%20Analysis%20Sample%20PBIX.pbix)

## <a name="create-a-new-visualization"></a>Criar uma nova visualização
Neste tutorial, vamos examinar nosso conjunto de dados de Análise de Varejo e criar algumas visualizações chave.

### <a name="open-a-report-and-add-a-new-blank-page"></a>Abra um relatório e adicione uma nova página em branco.
1. Abra o arquivo .PBIX de amostra de análise de varejo no Power BI Desktop. 
   ![](media/power-bi-report-add-visualizations-ii/power-bi-open-desktop.png)   

2. Adicione uma nova página selecionando o ícone de sinal de adição amarelo na parte inferior da tela.

### <a name="add-a-visualization-that-looks-at-this-years-sales-compared-to-last-year"></a>Adicione uma visualização que examina o débito no último ano de vendas deste ano.
1. Na tabela **Vendas**, selecione **Vendas deste Ano** > **Valor** e **Vendas do Ano Passado**. O Power BI cria um gráfico de colunas.  Isso é interessante e você deseja investigar. O que torna as vendas semelhantes por mês?  
   
   ![](media/power-bi-report-add-visualizations-ii/power-bi-barchart.png)
2. Na tabela Tempo, arraste **FiscalMonth** para a área **Eixo**.  
   ![](media/power-bi-report-add-visualizations-ii/power-bi-month.png)
3. [Mude a visualização](power-bi-report-change-visualization-type.md) para um gráfico Área.  Há muitos tipos de visualização dentre as quais escolher – veja as [descrições de cada uma, dicas de melhores práticas e tutoriais](power-bi-visualization-types-for-reports-and-q-and-a.md) para ajudar a decidir qual tipo usar. No painel de visualizações, selecione o ícone do gráfico Área ![](media/power-bi-report-add-visualizations-ii/power-bi-areachart.png).
4. Classifique a visualização selecionando as reticências e escolhendo **Classificar por FiscalMonth**.
5. [Redimensione a visualização](power-bi-visualization-move-and-resize.md) selecionando a visualização, captando um dos círculos da estrutura de tópicos e arrastando-o. Torne-a grande o suficiente para eliminar a barra de rolagem e pequeno o suficiente para nos dar espaço suficiente para adicionar outra visualização.
   
   ![](media/power-bi-report-add-visualizations-ii/pbi_part2_7b.png)
6. [Salve o relatório](../service-report-save.md).

### <a name="add-a-map-visualization-that-looks-at-sales-by-location"></a>Adicionar uma visualização do mapa que analisa as vendas por local
1. Na tabela **Loja**, selecione **Território**. O Power BI reconhece que a Região é um local e cria uma visualização de mapa.  
   ![](media/power-bi-report-add-visualizations-ii/power-bi-map.png)
2. Arraste **Pontuação Total** na área Tamanho.  
   ![](media/power-bi-report-add-visualizations-ii/power-bi-map2.png)
3. Adicione uma legenda.  Para ver os dados por nome de loja, arraste a **Cadeia** para a área Legenda.  
   ![](media/power-bi-report-add-visualizations-ii/power-bi-legend.png)

## <a name="next-steps"></a>Próximas etapas
* Mais sobre [Visualizações nos relatórios do Power BI](power-bi-report-visualizations.md).  
* Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)

