---
title: Criar linhas de referência dinâmica para visuais
description: Criar linhas de referência dinâmica para elementos visuais no serviço do Power BI
author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 11/14/2018
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: ab8fb8daa46a21676925de16a068f2d2029954d2
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/09/2019
ms.locfileid: "73855908"
---
# <a name="create-dynamic-reference-lines-for-visuals-in-the-power-bi-service"></a>Criar linhas de referência dinâmica para visuais no serviço do Power BI

Com o painel **Análise** no **serviço do Power BI**, você pode adicionar *linhas de referência* dinâmica às visualizações e destacar tendências ou ideias importantes.

![](media/service-analytics-pane/power-bi-analytics-pane.png)

> [!NOTE]
> O painel **Análise** só aparece quando você seleciona um visual na tela do relatório.
> 
> 

## <a name="use-the-analytics-pane"></a>Usar o painel Análise
Com o painel **Análise**, você pode criar os seguintes tipos de linhas de referência dinâmica (nem todas as linhas estão disponíveis para todos os tipos de visual):

* Linha constante do eixo X
* Linha constante do eixo Y
* Linha mínima
* Linha máxima
* Linha média
* Linha mediana
* Linha percentil


Para exibir as linhas de referência dinâmica disponíveis para um visual, siga estas etapas:

1. Escolha ou crie um visual e, então, selecione o ícone **Análise** ![](media/service-analytics-pane/power-bi-analytics-icon.png)no painel **Visualizações**.

2. Selecione a seta para baixo para o tipo de linha que você deseja criar para expandir suas opções. Nesse caso, selecionaremos a **Linha Média**.
   
   ![adicionar linha média](media/service-analytics-pane/power-bi-add.png)

3. Para criar uma nova linha, selecione **+ Adicionar** e decida a medida que será usada para criar a linha.  A lista suspensa **Medida** é preenchida automaticamente com os dados disponíveis da visualização selecionada. Vamos usar a **Contagem de armazenamento aberto**.

5. Você tem todos os tipos de opções para a linha, como cor, transparência, estilo e posição (relativa aos elementos de dados do visual). Se desejar rotular a linha, dê a ela um título e, em seguida, mova o controle deslizante **Rótulo de dados** para **Ativado**.  Nesse caso, daremos à linha o título *Nº méd. de lojas abertas* e personalizaremos algumas das outras opções, conforme mostrado abaixo.
   
   ![personalizar a análise de linha média](media/service-analytics-pane/power-bi-average-line2.png)

1. Observe o número que aparece ao lado do item **Linha média** no painel **Análise**. Isso indica o número de linhas dinâmicas atualmente presentes no visual, bem como o tipo. Se adicionarmos uma **Linha constante** como uma meta de contagem de loja igual a 9, veja que o painel **Análise** agora mostra que também temos uma linha de referência **Linha constante** aplicada nesse visual.
   
   ![](media/service-analytics-pane/power-bi-reference-lines.png)
   

Há muitas ideias interessantes que você pode destacar ao criar linhas de referência dinâmica com o painel **Análise**.

## <a name="considerations-and-troubleshooting"></a>Considerações e solução de problemas

Se o visual que você selecionou não puder ter linhas de referência dinâmica aplicadas a ele (neste caso, um visual de **Mapa**), você verá o seguinte quando selecionar o painel **Análise**.
   
![a análise não está disponível](media/service-analytics-pane/power-bi-no-lines.png)

A capacidade de usar linhas de referência dinâmica baseia-se no tipo de visual que está sendo usado. A seguinte lista mostra quais linhas dinâmicas estão atualmente disponíveis para os visuais:

Uso total de linhas dinâmicas estão disponíveis nos seguintes elementos visuais:

* Gráfico da área
* Gráfico de linhas
* Gráfico de dispersão
* Gráfico de colunas agrupadas
* Gráfico de barras agrupadas

Os elementos visuais a seguir só podem usar uma *linha constante* do painel **Análise**:

* Área empilhada
* Barra empilhada
* Coluna empilhada
* Barra 100% empilhada
* Coluna 100% empilhada

Para os seguintes elementos visuais, uma *linha de tendência* atualmente é a única opção:

* Linha não empilhada
* Gráfico de colunas agrupadas

Por fim, elementos visuais não cartesianos atualmente não podem aplicar linhas dinâmicas do painel **Análise**, como:

* Matriz
* Gráfico de pizza
* Donut
* Table

## <a name="next-steps"></a>Próximas etapas
[Painel de análise no Power BI Desktop](desktop-analytics-pane.md)

Mais perguntas? [Experimente a Comunidade do Power BI](https://community.powerbi.com/)

