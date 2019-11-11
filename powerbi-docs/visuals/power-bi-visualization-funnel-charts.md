---
title: Gráficos de funil
description: Gráficos de funil no Power BI
author: mihart
ms.reviewer: ''
featuredvideoid: maTzOJSRB3g
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/12/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 1394d71a5a2e811da23e18b9ee0d98f171f19083
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/09/2019
ms.locfileid: "73880828"
---
# <a name="funnel-charts"></a>Gráficos de funil

[!INCLUDE [power-bi-visuals-desktop-banner](../includes/power-bi-visuals-desktop-banner.md)]

Um gráfico de funil ajuda você a visualizar um processo linear com estágios conectados sequenciais. Por exemplo, um funil de vendas que acompanha clientes pelos estágios: Oportunidade \> Oportunidade qualificada \> Cliente potencial \> Contrato \> Fechamento.  Em um relance, a forma do funil transmite a integridade do processo que você está controlando.

Cada estágio de funil representa um percentual do total. Portanto, na maioria dos casos, um gráfico de funil tem a forma de um funil – com o primeiro estágio sendo o maior, e cada estágio subsequente, menor do que seu antecessor.  Um funil em forma de pera também é útil - ele pode identificar um problema no processo.  Mas, em geral, o primeiro estágio, o estágio de "entrada", é o maior.

![exemplo de funil azul](media/power-bi-visualization-funnel-charts/funnelplain.png)

## <a name="when-to-use-a-funnel-chart"></a>Quando usar um gráfico de funil
Os gráficos de funil são uma ótima opção:

* Quando os dados são sequenciais e se movimentam em pelo menos 4 estágios.
* Quando o número de "itens" no primeiro for maior que o número no estágio final.
* calcular o potencial (receita de vendas/negociações/etc.) por estágios.
* calcular e controlar as taxas de conversão e retenção.
* revelar afunilamentos em um processo linear.
* controlar o fluxo de trabalho do carrinho de compras.
* rastrear o progresso e o sucesso das campanhas de propaganda/marketing.

## <a name="working-with-funnel-charts"></a>Como trabalhar com gráficos de funil
Gráficos de funil:

* Podem ser classificados.
* Vários suportes.
* Podem ser realçados e cruzados por outras visualizações na mesma página de relatório.
* Podem ser usados para destacar e cruzar outras visualizações na mesma página de relatório.
   > [!NOTE]
   > Assista a este vídeo para ver Will criar um gráfico de funil usando o exemplo de Vendas e Marketing. Em seguida, siga as etapas abaixo do vídeo para tentar você mesmo, usando o arquivo PBIX de exemplo de Análise de Oportunidade
   > 
   > 
## <a name="prerequisite"></a>Pré-requisito

Este tutorial usa o [arquivo PBIX de exemplo de Análise de Oportunidade](https://download.microsoft.com/download/9/1/5/915ABCFA-7125-4D85-A7BD-05645BD95BD8/Opportunity%20Analysis%20Sample%20PBIX.pbix
).

1. Na seção superior esquerda da barra de menus, selecione **Arquivo** > **Abrir**
   
2. Encontre sua cópia do **arquivo PBIX de exemplo de Análise de Oportunidade**

1. Abra o **arquivo PBIX de exemplo de Análise de Oportunidade** na exibição de relatório ![Captura de tela do ícone de exibição de relatório](media/power-bi-visualization-kpi/power-bi-report-view.png).

1. Selecionar ![Captura de tela da guia amarela.](media/power-bi-visualization-kpi/power-bi-yellow-tab.png) para adicionar uma nova página.


## <a name="create-a-basic-funnel-chart"></a>Criar um gráfico de funil básico
Assista a este vídeo para ver Will criar um gráfico de funil usando o exemplo de Vendas e Marketing.

<iframe width="560" height="315" src="https://www.youtube.com/embed/qKRZPBnaUXM" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>


Agora crie seu próprio gráfico de funil que mostra o número de oportunidades que temos em cada um de nossos estágios de vendas.

1. Comece em uma página de relatório em branco e selecione o campo **SalesStage** \> **Sales Stage**.
   
    ![selecionar estágio de vendas](media/power-bi-visualization-funnel-charts/funnelselectfield-new.png)

1. Selecione o ícone de funil ![ícone de gráfico de funil](media/power-bi-visualization-funnel-charts/power-bi-funnel-icon.png) para converter o gráfico de colunas em um gráfico de funil.

2. No painel **Campos**, selecione **Fato** \> **Contagem de Oportunidades**.
   
    ![criar o gráfico de funil](media/power-bi-visualization-funnel-charts/power-bi-funnel-2.png)
4. Passar o mouse sobre uma barra exibe uma variedade de informações.
   
   * O nome do estágio
   * Número de oportunidades no momento deste estágio
   * Taxa de conversão geral (% do cliente potencial) 
   * Passo a passo (também conhecido como taxa de eliminação), que é % do estágio anterior (nesse caso, Estágio de Proposta/Estágio de Solução)
     
     ![detalhes da barra Proposta](media/power-bi-visualization-funnel-charts/funnelhover-new.png)

6. [Salve o relatório](../service-report-save.md).

## <a name="highlighting-and-cross-filtering"></a>Realce e filtragem cruzada
Para obter informações sobre como usar o painel Filtros, veja [Adicionar um filtro a um relatório](../power-bi-report-add-filter.md).

Realçar uma barra em um funil faz a filtragem cruzada das outras visualizações na página do relatório e vice-versa. Para acompanhar, adicione mais alguns elementos visuais à página do relatório que contém o gráfico de funil.

1. No funil, selecione a barra **Proposta**. Isso destaca de forma cruzada as outras visualizações na página. Use CTRL para fazer uma seleção múltipla.
   
   ![breve vídeo mostrando interações de visuais](media/power-bi-visualization-funnel-charts/funnelchartnoowl.gif)
2. Para definir as preferências de como os visuais são realçados e filtrados de forma cruzada entre si, veja [Interações de visuais no Power BI](../service-reports-visual-interactions.md)

## <a name="next-steps"></a>Próximas etapas

[Medidores no Power BI](power-bi-visualization-radial-gauge-charts.md)

[Tipos de visualização no Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)
