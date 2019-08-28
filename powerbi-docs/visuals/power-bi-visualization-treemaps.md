---
title: Mapas de árvore no Power BI
description: Mapas de árvore no Power BI
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: IkJda4O7oGs
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/24/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 4c28071917dbe5669e6e35bd416236ef7047eb24
ms.sourcegitcommit: 58c649ec5fd2447a0f9ca4c4d45a0e9fff2f1b6a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/27/2019
ms.locfileid: "67408845"
---
# <a name="treemaps-in-power-bi"></a>Mapas de árvore no Power BI

O treemaps exibe dados hierárquicos, como um conjunto de retângulos aninhados. Cada nível da hierarquia é representado por um retângulo colorido (ramificação) que contém retângulos menores (folhas). O Power BI baseia o tamanho do espaço dentro de cada retângulo no valor da medida. Os retângulos são organizados no tamanho da parte superior esquerda (maior) à parte inferior direita (menor).

![Captura de tela de um mapa de árvore de Contagem de produtos por categoria e fabricante.](media/power-bi-visualization-treemaps/pbi-nancy-viz-treemap.png)

Por exemplo, se estiver analisando as vendas, você pode ter ramificações de nível superior para as categorias de roupas: **Urbano**, **Rural**, **Jovem** e **Misto**. O Power BI dividiria os retângulos de categoria em folhas para os fabricantes de roupas nessa categoria. Essas folhas seriam dimensionadas e sombreadas com base no número de itens vendidos.

Na ramificação **Urbana** acima, muitas roupas **VanArsdel** foram vendidas. Menos **Natura** e **Fama** foram vendidas. Apenas algumas **Leo** foram vendidas. Portanto, a ramificação **Urbana** do mapa de árvore teria:

* O maior retângulo para **VanArsdel** no canto superior esquerdo.

* Retângulos levemente menores para **Natura** e **Fama**.

* Muitos outros retângulos para todas as outras roupas vendidas.

* Um pequeno retângulo para **Leo**.

Você poderia comparar o número de itens vendidos em outras categorias de roupas comparando o tamanho e o sombreamento de cada nó folha; retângulos maiores e mais escuros indicam valor mais alto.

Deseja ver alguém criar um mapa de árvore primeiro? Pule para 2:10 neste vídeo para assistir Amanda criar um mapa de árvore.

<iframe width="560" height="315" src="https://www.youtube.com/embed/IkJda4O7oGs" frameborder="0" allowfullscreen></iframe>

## <a name="when-to-use-a-treemap"></a>Quando usar um mapa de árvore

Os treemps são uma ótima opção:

* Para exibir grandes quantidades de dados hierárquicos.

* Quando um gráfico de barras não puder lidar efetivamente com grande número de valores.

* Para mostrar as proporções entre cada parte e o todo.

* Para mostrar o padrão da distribuição da medida em cada nível das categorias na hierarquia.

* Para mostrar atributos usando a codificação de cor e tamanho.

* Para identificar padrões, exceções, colaboradores mais importantes e exceções.

## <a name="prerequisites"></a>Pré-requisitos

* O serviço do Power BI ou o Power BI Desktop

* Relatório Exemplo de Análise de Varejo

## <a name="get-the-retail-analysis-sample-report"></a>Obter o relatório de exemplo de Análise de Varejo

Essas instruções usam o exemplo de análise de varejo. Criar uma visualização requer permissões de edição para o conjunto de dados e o relatório. Felizmente, os exemplos do Power BI são todos editáveis. Se alguém compartilhar um relatório com você, é possível criar visualizações em relatórios. Para acompanhar, obtenha o [Relatório de exemplo de Análise de Varejo](../sample-datasets.md).

Após obter o conjunto de dados do **Exemplo de Análise de Varejo**, você pode começar a usar.

## <a name="create-a-basic-treemap"></a>Criar um mapa de árvore básico

Crie um relatório e adicione um mapa de árvore básico.

1. No **Meu Workspace**, selecione **Conjuntos de dados** > **Criar um relatório**.

    ![Captura de tela de conjuntos de dados > Criar um relatório.](media/power-bi-visualization-treemaps/power-bi-create-a-report.png)

1. No painel **Campos**, selecione a medida **Vendas** > **Vendas do Ano Passado**.

   ![Captura de tela de vendas > Vendas do Ano Passado selecionada e o visual resultante.](media/power-bi-visualization-treemaps/treemapfirstvalue_new.png)

1. Selecione o ícone de mapa de árvore ![Captura de tela do ícone do mapa de árvore](media/power-bi-visualization-treemaps/power-bi-treemap-icon.png) para converter o gráfico em um mapa de árvore.

   ![Captura de tela do mapa de árvore sem configuração.](media/power-bi-visualization-treemaps/treemapconvertto_new.png)

1. Arraste **Item** > **Categoria** para a seção **Grupo**.

    O Power BI cria um mapa de árvore no qual o tamanho dos retângulos se baseia no total de vendas e a cor representa a categoria. Na essência que você criou uma hierarquia que descreve visualmente o tamanho relativo do total de vendas por categoria. A categoria **Masculino** tem as maiores vendas e categoria **Meias e Roupa Íntima** tem as vendas mais baixas.

    ![Captura de tela do mapa de árvore configurado.](media/power-bi-visualization-treemaps/power-bi-complete.png)

1. Arraste **Repositório** > **Cadeia** para a seção **Detalhes** para concluir o mapa de árvore. Agora você pode comparar as vendas do ano passado por categoria e cadeia.

   ![Captura de tela do mapa de árvore com Loja > Cadeia adicionada aos detalhes.](media/power-bi-visualization-treemaps/power-bi-details.png)

   > [!NOTE]
   > Saturação da cor e os Detalhes não podem ser usados ao mesmo tempo.

1. Focalize uma área **Rede** para revelar a dica de ferramenta para essa parte da **Categoria**.

    Por exemplo, focalizando **Fashions Direct** no retângulo **090-Home** revela a dica de ferramenta para a parte Fashion Direct da categoria de Home.

   ![Captura de tela da dica de ferramenta da Página Inicial exibida.](media/power-bi-visualization-treemaps/treemaphoverdetail_new.png)

1. Adicione o mapa de árvore como um [bloco do painel (fixe o visual)](../service-dashboard-tiles.md).

1. Salve [o relatório](../service-report-save.md).

## <a name="highlighting-and-cross-filtering"></a>Realce e filtragem cruzada

Para obter informações sobre como usar o painel **Filtros**, veja [Adicionar um filtro a um relatório](../power-bi-report-add-filter.md).

Realçar uma **Categoria** ou **Detalhe** em um mapa de árvore filtra e destaca de forma cruzada as outras visualizações na página do relatório e vice-versa. Para acompanhar, adicione alguns visuais a esta página do relatório ou copie o mapa de árvore para uma das outras páginas neste relatório.

1. No mapa de árvore, selecione uma **Categoria** ou uma **Cadeia** de dentro de uma **Categoria**. Isso destacará de forma cruzada as outras visualizações na página. Selecionando **050-Shoes**, por exemplo, mostra que as vendas do ano passado de sapatos foram **US$3.640,471** com a **Fashions Direct** representando **US$ 2.174,185** dessas vendas.

   ![Captura de tela do relatório de Visão Geral de Vendas da Loja mostrando o realce cruzado.](media/power-bi-visualization-treemaps/treemaphiliting.png)

1. No gráfico de pizza das **Últimas vendas do ano por cadeia**, selecionar a fatia **Fashions Direct** realiza a filtragem cruzada de um mapa de árvore.
   ![Demonstração de GIF do recurso de filtragem cruzada.](media/power-bi-visualization-treemaps/treemapnoowl.gif)

1. Para gerenciar como os gráficos são filtrados e realçados de forma cruzada entre si, veja [Alterar como os visuais interagem em um relatório do Power BI](../service-reports-visual-interactions.md).

## <a name="next-steps"></a>Próximas etapas

* [Gráficos de cascata no Power BI](power-bi-visualization-waterfall-charts.md)

* [Tipos de visualização no Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)
