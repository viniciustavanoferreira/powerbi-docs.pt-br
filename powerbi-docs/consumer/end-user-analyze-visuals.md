---
title: Usar o recurso Analisar para explicar flutuações em visuais de relatório
description: Obtenha insights com facilidade em aumentos ou diminuições no Power BI Desktop
author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 06/23/2019
ms.author: mihart
LocalizationGroup: Create reports
ms.openlocfilehash: 4ffeed66c514882eae0c05bc41dd29f186c2ded9
ms.sourcegitcommit: caf60154a092f88617eb177bc34fb784f2365962
ms.contentlocale: pt-BR
ms.lasthandoff: 06/25/2020
ms.locfileid: "85363787"
---
# <a name="use-the-analyze-feature-to-explain-fluctuations-in-report-visuals-preview"></a>Usar o recurso Analisar para explicar flutuações em visuais de relatório (versão prévia)

[!INCLUDE[consumer-appliesto-ynnn](../includes/consumer-appliesto-ynnn.md)]

Muitas vezes nos visuais de relatório, você vê um grande aumento e, em seguida, uma queda brusca nos valores e questiona a causa dessas flutuações. Com o recurso **Analisar** no **serviço do Power BI**, você pode descobrir a causa em apenas alguns cliques.

Por exemplo, considere o visual a seguir, que mostra o *Total de unidades* por *Mês* e *Fabricante*. A VanArsdel tem um desempenho superior ao de seus concorrentes, mas teve uma queda brusca em junho de 2014. Nesses casos, você pode explorar os dados para explicar a alteração ocorrida. 

![Visual com aumentos e diminuições](media/end-user-analyze-visuals/power-bi-line-chart.png)

É possível pedir ao serviço do Power BI para explicar aumentos, diminuições ou distribuições incomuns em visuais e obter análises rápidas, automatizadas e repletas de insights sobre seus dados. Basta clicar com o botão direito do mouse em um ponto de dados e selecionar **Analisar > Explicar a diminuição** (ou o aumento, se a barra anterior era menor) ou **Analisar > Encontrar o local em que a distribuição é diferente**, e o insight será fornecido em uma janela fácil de usar.

![Insights mostrados no visual](media/end-user-analyze-visuals/power-bi-decrease.png)

O recurso Analisar é contextual e baseia-se no ponto de dados imediatamente anterior – como a coluna ou a barra anterior.

> [!NOTE]
> Esse recurso está em versão prévia e sujeito a alterações. O recurso de insight está habilitado por padrão (você não precisa marcar uma caixa Versão Prévia para habilitá-lo).

### <a name="which-factors-and-categories-are-chosen"></a>Quais fatores e categorias são escolhidos

Depois de examinar as diferentes colunas, o Power BI seleciona e exibe aquelas que mostram a maior alteração na contribuição relativa. Para cada uma, os valores que tiveram a alteração mais significativa na contribuição são destacados na descrição. Além disso, os valores que tiveram os maiores aumentos e diminuições reais também são indicados.

Para ver todos os insights gerados pelo Power BI, use a barra de rolagem. A ordem é classificada com o colaborador mais significativo exibido primeiro. 

## <a name="using-insights"></a>Usando insights
Para usar os insights a fim de explicar as tendências observadas nos visuais, clique com o botão direito do mouse em qualquer ponto de dados em um gráfico de barras ou de linhas e selecione **Analisar**. Depois, escolha a opção mostrada: **explicar o aumento**, **explicar a diminuição** ou **explicar a diferença**.

Em seguida, o Power BI executa seus algoritmos de aprendizado de máquina nos dados e preenche uma janela com um visual e uma descrição que indica quais categorias mais influenciaram o aumento, a diminuição ou a diferença.  Neste exemplo, o primeiro insight é um gráfico de cascata.

![janela pop-up de Insights](media/end-user-analyze-visuals/power-bi-insight.png)

Selecionando os ícones pequenos na parte inferior do visual de cascata, você pode optar por fazer com que os insights exibam um gráfico de dispersão, gráfico de colunas empilhadas ou gráfico de faixa de opções.

![trio de visuais de insights](media/end-user-analyze-visuals/power-bi-options.png)

Use os ícones *polegar para cima* e *polegar para baixo* na parte superior da página para fornecer comentários sobre o visual e o recurso.  

![ícones de polegar para cima e polegar para baixo](media/end-user-analyze-visuals/power-bi-thumbs.png)


Use os insights quando o relatório estiver no modo de exibição de Leitura ou de Edição, tornando-o versátil para a análise de dados e para a criação de visuais que podem ser adicionados com facilidade aos relatórios. Se o relatório estiver aberto no modo de exibição de Edição, você verá um ícone de adição ao lado dos ícones de polegar. Selecione o ícone de adição para adicionar o insight ao relatório como um novo visual. 

![trio de visuais de insights](media/end-user-analyze-visuals/power-bi-add-visual.png)

## <a name="details-of-the-results-returned"></a>Detalhes dos resultados retornados

Os detalhes retornados pelos insights destinam-se a realçar o que estava diferente entre os dois períodos para ajudá-lo a entender a alteração entre eles.  

O algoritmo obtém todas as outras colunas no modelo e calcula a divisão por essa coluna para os períodos *antes* e *depois*, determinando o tamanho da alteração ocorrida nessa divisão e retornando as colunas com a maior alteração. Por exemplo, *Estado* foi selecionado no insight de cascata acima, pois a colaboração da Louisiana, do Texas e do Colorado caiu de 13% a 19% de junho para julho e causou a maior parte da diminuição no *Total de unidades*.  

Para cada insight retornado, há quatro visuais que podem ser exibidos. Três desses visuais destinam-se a realçar a alteração na contribuição entre os dois períodos. Por exemplo, para obter a explicação do aumento do *2º trimestre* para o *3º trimestre*. O gráfico de faixa de opções mostra a alteração antes e depois do ponto de dados selecionado.

### <a name="the-scatter-plot"></a>O gráfico de dispersão

O visual de gráfico de dispersão mostra o valor da medida no primeiro período (no eixo x) em relação ao valor da medida no segundo período (no eixo y), para cada valor da coluna (*Estado*, nesse caso). Os pontos de dados estarão na região verde se tiverem aumentado e na região vermelha se tiverem diminuído. 

A linha pontilhada mostra o melhor ajuste, e os pontos de dados acima dessa linha aumentaram mais do que a tendência geral, enquanto os que estão abaixo dela aumentaram menos.  

![Gráfico de dispersão com linha pontilhada](media/end-user-analyze-visuals/power-bi-scatter.png)

Observe que os itens de dados cujo valor estava em branco em qualquer período não são exibidos no gráfico de dispersão.

### <a name="the-100-stacked-column-chart"></a>O gráfico de colunas 100% empilhadas

O visual de gráfico de colunas 100% empilhadas mostra o valor da contribuição para o total (100%) do ponto de dados selecionado e do anterior. Isso permite uma comparação lado a lado da contribuição de cada ponto de dados. Neste exemplo, as dicas de ferramenta mostram a contribuição real para o valor selecionado, Texas. Como a lista de estados é longa, as dicas de ferramentas ajudam você a ver os detalhes. Usando as dicas de ferramenta, vemos que o Texas contribuiu com quase o mesmo percentual para o total de unidades (31% e 32%), mas o número real do total de unidades diminuiu de 89 para 71. Lembre-se de que o eixo Y é uma porcentagem, e não um total, e cada banda de coluna é uma porcentagem, não um valor. 

![Gráfico de colunas 100% empilhadas](media/end-user-analyze-visuals/power-bi-stacked.png)

### <a name="the-ribbon-chart"></a>O gráfico de faixa de opções

O visual de gráfico de faixa de opções mostra o valor da medida antes e depois. Ele é muito útil mostrar as alterações nas contribuições quando a *ordenação* dos colaboradores é alterada (por exemplo, *LA* caiu de colaborador número dois para o número onze).  E, embora *TX* seja representado por uma ampla faixa de opções na parte superior, indicando que se trata do colaborador mais significativo antes e depois, a queda mostra que o valor da colaboração caiu durante o período selecionado e depois.

![gráfico de faixa de opções](media/end-user-analyze-visuals/power-bi-ribbon-tooltip.png)

### <a name="the-waterfall-chart"></a>O gráfico de cascata

O quarto visual é um gráfico de cascata, que mostra os aumentos ou as diminuições reais entre os períodos. Esse visual mostra claramente um colaborador significativo para a redução de junho de 2014 – nesse caso, **Estado**. E a particularidade da influência do **Estado** no total de unidades é que os declínios na Louisiana, no Texas e no Colorado tiveram o papel mais significativo.      

![gráfico de cascata](media/end-user-analyze-visuals/power-bi-insight.png)


 



## <a name="considerations-and-limitations"></a>Considerações e limitações
Como esses insights são baseados na alteração em relação ao ponto de dados anterior, eles não estão disponíveis quando o primeiro ponto de dados é selecionado em um visual. 

O recurso **Analisar** não está disponível para todos os tipos de visual. 

A seguinte lista é a coleção de cenários sem suporte no momento para **Analisar – explicar aumento/diminuição/diferença**:

* Filtros TopN
* Filtros Incluir/excluir
* Filtros de medida
* Medidas não numéricas
* Uso de "Mostrar valor como"
* Medidas filtradas – medidas filtradas são cálculos no nível do visual com um filtro específico aplicado (por exemplo, *Total de Vendas na França*) e são usadas em alguns dos visuais criados pelo recurso de insights
* Colunas categóricas no eixo X, a menos que ele defina uma classificação por coluna que seja escalar. Se você estiver usando uma hierarquia, todas as colunas na hierarquia ativa deverão corresponder a essa condição


## <a name="next-steps"></a>Próximas etapas
[Gráficos de cascata](../visuals/power-bi-visualization-waterfall-charts.md)    
[Gráficos de dispersão](../visuals/power-bi-visualization-scatter.md)
[Gráficos de colunas](../visuals/power-bi-report-visualizations.md)
[Gráficos de faixa de opções](../visuals/desktop-ribbon-charts.md)
