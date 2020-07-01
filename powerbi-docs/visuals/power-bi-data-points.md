---
title: Grandes conjuntos de dados, limites de pontos de dados e estratégias de dados
description: Limites de dados para visuais e estratégias de redução de dados
author: mihart
ms.reviewer: justyna
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: how-to
ms.date: 01/10/2020
ms.author: rien
LocalizationGroup: Visualizations
ms.openlocfilehash: 97bccec3ec0e92ebfcc6b9251cf5c17f176fbed1
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85240131"
---
# <a name="apply-data-point-limits-and-strategies-by-visual-type"></a>Aplicar limites de ponto de dados e estratégias por tipo de visual

[!INCLUDE[consumer-appliesto-yyyn](../includes/consumer-appliesto-yyyn.md)]    

Ao renderizar um visual no Power BI, a visualização deve ser rápida e precisa. Isso requer algoritmos subjacentes configurados para cada tipo de visual. Os visuais do Power BI devem ser flexíveis o suficiente para lidar com tamanhos diferentes de conjuntos de dados. Alguns conjuntos de dados têm apenas um alguns pontos de dados, enquanto outros conjuntos de dados têm petabytes de pontos de dados. Este artigo explica as estratégias usadas pelo Power BI para renderizar as visualizações.

## <a name="data-reduction-strategies"></a>Estratégias de redução de dados
Cada visual emprega uma ou mais *estratégias de redução de dados* para lidar com os volumes potencialmente grandes de dados sendo analisados. Até mesmo uma tabela simples emprega uma estratégia para evitar o carregamento de todo o conjunto de dados para o cliente.  A estratégia de redução usada varia de acordo com o tipo de visual. Cada visual seleciona as *estratégias de redução de dados* com suporte como parte da geração da solicitação de dados enviada ao servidor. 

Cada visual controla os parâmetros nessas estratégias para influenciar a quantidade total de dados.   

## <a name="strategies"></a>Estratégias
Para cada estratégia, existem padrões baseados na forma e tipo de dados que estão sendo visualizados. Mas os padrões podem ser substituídos, no painel de formatação do Power BI, para fornecer a experiência de usuário correta. 

* **Dados de Janelas** (segmentação): Permitir que os usuários percorram os dados em um visual, carregando progressivamente fragmentos do conjunto de dados geral.
* **TopN**: Mostrar apenas os primeiros N itens
* **Exemplos Simples**: Mostrar os itens primeiro, último e N uniformemente distribuídos entre eles.
* **BottomN**: Mostrar apenas os últimos N itens.  Útil para monitorar dados atualizados com frequência.
* **Amostragem de alta densidade** – um algoritmo de amostragem aprimorado que respeita melhor os valores discrepantes e/ou a forma de uma curva.
    * **Amostragem de linha compartimentalizada** – pontos de dados de amostra com base em valores discrepantes em compartimentos ao longo de um eixo
    * **Amostragem de pontos sobrepostos** – pontos de dados de amostra com base em valores sobrepostos para preservar valores discrepantes

## <a name="statistics"></a>Estatísticas
Determinados modelos podem fornecer estatísticas sobre o número de valores para determinadas colunas. Quando essas informações estão presentes, aproveitamos essas informações para fornecer melhor equilíbrio entre várias hierarquias, se um visual não substituir explicitamente a contagem de valores para uma estratégia.

Para saber mais, confira [Novidades no Analysis Services](https://docs.microsoft.com/sql/analysis-services/what-s-new-in-analysis-services?view=sql-server-2017)

## <a name="dynamic-limits"></a>Limites dinâmicos
Além das estratégias acima, visuais com duas hierarquias de colunas de agrupamento (eixo e legenda, ou categoria e série) usam uma estratégia adicional chamada *limites dinâmicos*.  Os limites dinâmicos são projetados para equilibrar melhor os pontos de dados. 

Os limites dinâmicos fornecem uma melhor seleção de pontos para dados esparsos do que os limites estáticos. Por exemplo, um visual pode ser configurado para selecionar 100 categorias e 10 séries com um total de 1000 pontos. Mas os dados reais têm 50 categorias e 20 séries.  No runtime da consulta, os limites dinâmicos selecionam todas as 20 séries para preencher os 1000 pontos solicitados.

Os limites dinâmicos são aplicados automaticamente quando o servidor é capaz, conforme detalhado abaixo:

* No Power BI Desktop com SSAS local versão 2016 ou superior [aproveitando os recursos de SuperDax do servidor](https://blogs.msdn.microsoft.com/analysisservices/2015/09/02/whats-new-in-microsoft-sql-server-analysis-services-tabular-models-in-sql-server-2016-ctp-2-3/)

* No serviço do Power BI Desktop ao usar um modelo importado, Direct Query, conecte-se ao vivo ao serviço ou conecte-se ao vivo ao AS PaaS. 

* No Power BI Service, ao se conectar por meio de um gateway local ao SSAS local, não podemos usar limites dinâmicos. O gateway local não oferece suporte à estratégia de limites dinâmicos que retorna uma estrutura diferente de conjuntos de resultados do SSAS local.  

## <a name="strategies-and-data-point-limits-by-visual-type"></a>Estratégias e limites de pontos de dados por tipo de visual

### <a name="area-chart"></a>Gráfico da área
Confira [Como funciona a amostragem de linhas](../create-reports/desktop-high-density-sampling.md#how-the-new-line-sampling-algorithm-works)

### <a name="barcolumn-chart"></a>Gráfico de barras/colunas
- Quando no modo categórico
    - Categorias: Virtualização usando a janela de 500 linhas de cada vez
    - Série: 60 superiores
    - Quando em modo escalar (pode usar limites dinâmicos)
        - Máximo de pontos: 10.000
        - Categorias: Exemplo de 500 valores
        - Série: 20 valores superiores

### <a name="card-multirow"></a>Cartão (várias linhas) 
- Valores: Virtualização usando a janela de 200 linhas de cada vez

### <a name="combo-chart"></a>Gráfico de combinação
 Usa as mesmas estratégias do gráfico de colunas. Observe que a linha no **gráfico de combinação** não usa o algoritmo de alta densidade usado pelo **gráfico de linhas**.

### <a name="power-bi-visuals"></a>Visuais do Power BI
Pode chegar a 30.000, mas cabe aos autores dos visuais indicar quais estratégias usar. O limite padrão é 1.000, mas o criador do visual pode alterá-lo até um máximo de 30.000.

### <a name="doughnut"></a>Rosca
- Máximo de pontos: 3,500
- Grupo: 500 superiores
- Detalhes: 20 superiores

### <a name="filled-map-choropleth"></a>Mapa coroplético preenchido 
O mapa preenchido pode usar estatísticas ou limites dinâmicos. O Power BI tenta usar a redução na seguinte ordem: limites dinâmicos, estatísticas e, por último, configuração. 
- Máximo de pontos: 10.000
- Categorias: 500 superiores
- Série (quando X e Y estão presentes): 20 superiores

### <a name="funnel"></a>Funil
- Máximo de pontos: 3,500
- Categorias: 3.500 superiores

### <a name="kpi"></a>KPI
- Eixo da tendência
- 3\.500 inferiores

### <a name="line-chart"></a>Gráfico de linhas
Confira [Como funciona a amostragem de linhas](../create-reports/desktop-high-density-sampling.md#how-the-new-line-sampling-algorithm-works)

### <a name="line-chart-high-density"></a>Gráfico de linhas, alta densidade
Confira [Amostragem de alta densidade](../create-reports/desktop-high-density-sampling.md)

### <a name="map"></a>Mapear 
- Máximo de pontos: 3,500

Dependendo da configuração, um mapa pode ter:
- Localização: 3.500 superiores
- Localização, Tamanho: 3.500 superiores
- Agregações de Localização, Latitude e Longitude (+ /-tamanho): 3.500 superiores
- Latitude, Longitude: consulte [Dispersão de alta densidade](../create-reports/desktop-high-density-scatter-charts.md)
- Latitude, Longitude, Tamanho: 3.500 superiores
- Legenda, Latitude, Longitude: consulte [Dispersão de alta densidade](../create-reports/desktop-high-density-scatter-charts.md)
- Legenda, Latitude, Longitude, Tamanho: 233 principais legendas, 15 principais latitudes e longitudes (estatísticas ou limites dinâmicos podem ser usados)
- Localização, Legenda, Latitude e Longitude como agregações (+ /-tamanho): 233 principais locais, 15 principais legendas (pode usar limites dinâmicos ou estatísticas)

### <a name="matrix"></a>Matriz
- Linhas: Virtualização usando a janela de 500 linhas de cada vez
- Colunas: Colunas de agrupamento dos 100 superiores 
- Valores: vários valores não contam em relação à redução de dados

### <a name="powerapps-visual"></a>Visual do PowerApps
Pode chegar a 30.000, mas cabe aos autores dos visuais indicar quais estratégias usar. O limite padrão é 1.000, mas o criador do visual pode alterá-lo até um máximo de 30.000.

### <a name="radial-gauge"></a>Medidor radial
Nenhuma estratégia de redução

### <a name="slicer"></a>Segmentação de Dados
- Valores: Virtualização usando a janela de 200 linhas de cada vez

### <a name="scatter-chart-high-density"></a>Gráficos de dispersão (alta densidade)
Confira [Dispersão de alta densidade](https://docs.microsoft.com/power-bi/visuals/desktop-high-density-scatter-charts)

### <a name="pie"></a>Pizza
- Máximo de pontos: 3,500
- Grupo: 500 superiores
- Detalhes: 20 superiores

### <a name="r--python-visuals"></a>Elementos visuais R & Python
Limite de 150.000 linhas. Se mais de 150.000 linhas forem selecionadas, somente as 150.000 linhas superiores serão usadas

### <a name="ribbon-chart"></a>Gráfico da faixa de opções
- Quando no modo categórico
    - Categorias: Virtualização (janelas de dados) usando a janela de 500 linhas de cada vez
    - Série: 60 superiores
    - Quando em modo escalar (pode usar limites dinâmicos)
        - Máximo de pontos: 10.000
        - Categorias: Exemplo de 500 valores
        - Série: 20 valores superiores

### <a name="shape-map-preview"></a>Mapa de formas (versão prévia)
O mapa de formas pode usar estatísticas ou limites dinâmicos. 
- Máximo de pontos: 1.500
- Categorias: 500 superiores

### <a name="table"></a>Tabela
- Valores: Virtualização (janelas de dados) usando a janela de 500 linhas de cada vez

### <a name="tree-map-could-use-statistics-or-dynamic-limits"></a>Mapa de árvore (pode usar estatísticas ou limites dinâmicos)
- Máximo de pontos: 3,500
- Grupo: 500 superiores
- Detalhes: 20 superiores

### <a name="waterfall-chart"></a>Gráfico de cascata
- Quando há apenas o bucket de categoria
    - Máximo de pontos: 3,500
    - Somente categoria – 3.500 superiores
- Quando a categoria e divisão estão presentes
    - Categoria: Virtualização (janelas de dados) usando a janela de 30 linhas de cada vez
    - Divisão – valores dos 200 superiores


## <a name="next-steps"></a>Próximas etapas
[Tipos de visualização](power-bi-report-visualizations.md)
