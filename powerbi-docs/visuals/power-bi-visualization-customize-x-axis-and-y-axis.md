---
title: Personalizar as propriedades dos eixos x e y
description: Personalizar as propriedades dos eixos x e y
author: mihart
ms.reviewer: ''
featuredvideoid: 9DeAKM4SNJM
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 12/3/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 830fbe945405f8ad7aadd7ceac9fb1967daad22b
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/05/2020
ms.locfileid: "75758096"
---
# <a name="customize-x-axis-and-y-axis-properties"></a>Personalizar as propriedades dos eixos X e Y

[!INCLUDE [power-bi-visuals-desktop-banner](../includes/power-bi-visuals-desktop-banner.md)]

Neste tutorial, você aprenderá várias maneiras diferentes de personalizar os eixos X e Y de seus visuais. Nem todos os visuais têm eixos. Gráficos de pizza, por exemplo, não têm eixos. E as opções de personalização variam de visual para visual. Existem muitas opções para abordar em um único artigo, então vamos dar uma olhada em algumas das personalizações mais usadas e familiarizarmo-nos com o painel **Formato** do visual na tela de relatório do Power BI.  

Assista à Amanda personalizar os eixos X e Y. Ela também demonstrará as diferentes maneiras de controlar a concatenação ao fazer drill down e drill up.

> [!NOTE]
> Este vídeo usa uma versão mais antiga do Power BI.

<iframe width="560" height="315" src="https://www.youtube.com/embed/9DeAKM4SNJM" frameborder="0" allowfullscreen></iframe>

## <a name="prerequisites"></a>Pré-requisitos

- Power BI Desktop

- [Exemplo de Análise de Varejo ](https://download.microsoft.com/download/9/6/D/96DDC2FF-2568-491D-AAFA-AFDD6F763AE3/Retail%20Analysis%20Sample%20PBIX.pbix)


## <a name="add-a-new-visualization"></a>Adicionar uma nova visualização

Antes de personalizar a visualização, você precisa compilá-la.

1. No Power BI Desktop, abra a amostra de Análise de Varejo.  

2. Na parte inferior, selecione o ícone amarelo de adição para adicionar uma nova página. 

    ![sinal de mais amarelo](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-new-page-icon.png)

1. No painel de **Visualizações**, selecione o ícone do gráfico de colunas empilhadas. Isso adiciona um modelo vazio à tela de relatório.

    ![Captura de tela do painel de Visualizações e um gráfico de colunas empilhadas vazio](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-column-chart.png)

1. Para definir os valores do eixo X, no painel **Campos**, selecione **Time** > **FiscalMonth**.

1. Para definir os valores do eixo Y, no painel **Campos**, selecione **Vendas** > **Vendas do Ano Passado** e selecione **Vendas** > **Vendas deste Ano** > **Valor**.

    ![Captura de tela do gráfico de colunas empilhadas preenchido.](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-build-visual.png)

    Agora você pode personalizar o eixo X. O Power BI fornece opções quase ilimitadas para formatar sua visualização. 

## <a name="customize-the-x-axis"></a>Personalizar o eixo X
Há muitos recursos que são personalizáveis para o eixo X. Você pode adicionar e modificar os rótulos de dados e o título do eixo X. Para categorias, você pode modificar a largura, o tamanho e o preenchimento de barras, colunas, linhas e áreas. Para valores, você pode modificar as unidades de exibição, as casas decimais e as linhas de grade. O exemplo a seguir mostra a personalização de um gráfico de colunas. Vamos adicionar algumas personalizações para você familiarizar-se com as opções e então poder explorar o restante por conta própria.

### <a name="customize-the-x-axis-labels"></a>Personalizar os rótulos do eixo X
Os rótulos do eixo X são exibidos abaixo das colunas no gráfico. No momento, eles são cinza-claro, pequenos e difíceis de ler. Vamos mudar isso.

1. No painel **Visualizações**, selecione **Formato** (ícone de rolo de tinta ![Captura de tela do ícone de rolo de tinta.](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-paintroller-icon.png) ) para revelar as opções de personalização.

2. Expanda as opções de eixo X.

   ![Captura de tela das opções de eixo X.](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-axis-x.png)

3. Mova o controle deslizante do **eixo X** para **Ativado**.

    ![Captura de tela na segmentação Ativada.](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-slider-on.png)

    Alguns motivos pelos quais você pode querer definir o eixo X como **Desligado** é se a visualização for autoexplicativa sem rótulos ou se você tiver uma página de relatório cheia e precisar liberar espaço para exibir mais dados.

4. Formatar a fonte, o tamanho e a cor do texto:

    - **Cor**: selecione preto

    - **Tamanho do texto**: insira *14*

    - **Família de fontes**: selecione **Arial Black**

    - **Preenchimento interno**: Insira *40%*

        ![Captura de tela com rótulos em um ângulo](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-formatting-x.png)
    
5. Talvez você não goste da maneira como o texto do eixo X é exibido em uma diagonal. Você tem várias opções. 
    - Altere o tamanho do texto para algo menor que 14.
    - Aumente a visualização. 
    - Exiba menos colunas e adicione uma barra de rolagem aumentando **largura mínima da categoria**. 
    
    Aqui, selecionamos a segunda opção e capturamos uma das barras de redimensionamento para deixar a visualização mais larga. Agora, ela acomoda o texto de 14 pontos sem necessidade de exibir o texto em um ângulo ou com uma barra de rolagem. 

   ![Painel de gráfico e formatação com rótulos horizontais](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-stretch.png)

### <a name="customize-the-x-axis-title"></a>Personalizar o título do eixo X
Quando o título do eixo X está **Ligado**, o título do eixo X é exibido abaixo dos rótulos do eixo X. 

1. Comece virando o título do eixo X para **Ligado**.  

    ![Controle deslizante do título](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-title-on.png)

    A primeira coisa que você observará é que sua visualização agora tem um título de eixo X padrão.  Nesse caso, é o **FiscalMonth**.

   ![Gráfico com título exibido na parte inferior](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-x-title.png)

1. Formatar a fonte, o tamanho e a cor do texto do título:

    - **Cor do título**: selecione laranja

    - **Título do eixo**: Digite *Mês Fiscal* (com um espaço)

    - **Tamanho de texto do título**: Insira *18*

    Depois de concluir as personalizações, o gráfico de colunas empilhadas tem a aparência a seguir:

    ![Captura de tela do gráfico de colunas empilhadas personalizado.](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-x-title-formatted.png)

1. Salve as alterações e vá para a próxima seção. Se você precisar reverter todas as alterações, selecione **Reverter ao Padrão** na parte inferior do painel de personalização do **eixo X**. Em seguida, você personalizará o eixo Y.

## <a name="customize-the-y-axis"></a>Personalizar o eixo Y
Há muitos recursos que podem ser personalizados para o eixo Y. Você pode adicionar e modificar os rótulos de dados, o título do eixo Y e as linhas de grade. Para valores, você pode modificar as unidades de exibição, as casas decimais, o ponto inicial e o ponto de extremidade. Para categorias, você pode modificar a largura, o tamanho e o preenchimento de barras, colunas, linhas e áreas. 

O exemplo a seguir continua a nossa personalização de um gráfico de colunas. Vamos fazer algumas alterações para você familiarizar-se com as opções e então poder explorar o restante por conta própria.

### <a name="customize-the-y-axis-labels"></a>Personalizar os rótulos do eixo Y
Os rótulos do eixo Y são exibidos à esquerda por padrão. No momento, eles são cinza-claro, pequenos e difíceis de ler. Vamos mudar isso.

1. Expanda as opções de eixo Y.

   ![Captura de tela das opções de eixo Y.](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-axis-y.png)

1. Mova a segmentação do **eixo Y** para **Ativado**.  

    ![Captura de tela na segmentação Ativada.](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-y-axis-on.png)

    Um motivo pelo qual você talvez queira desativar o eixo Y é para economizar espaço para mais dados.

1. Formatar a fonte, o tamanho e a cor do texto:

    - **Cor**: selecione preto

    - **Tamanho do texto**: Insira *10*

    - **Unidades de exibição**: Selecione **Milhões**

    ![Gráfico após a formatação do eixo Y](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-formatting-y.png)

### <a name="customize-the-y-axis-title"></a>Personalizar o título do eixo Y
Quando o título do eixo Y está **Ligado**, o título do eixo y é exibido ao lado dos rótulos do eixo Y. Para essa visualização, o fato de ter um título de eixo Y não melhora o visual; portanto, deixe o **Título** **Desativado**. Adicionaremos títulos do eixo Y a um visual de dois eixos posteriormente neste tutorial. 

### <a name="customize-the-gridlines"></a>Personalizar as linhas de grade
Destacaremos as linhas de grade, alterando a cor e aumentando o traço:

- **Cor**: selecione laranja

- **Traço**: insira *2*

Depois de todas essas personalizações, o gráfico de colunas deve ser parecido com isto:

![Captura de tela do gráfico com o eixo Y personalizado.](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-gridline.png)

## <a name="customizing-visualizations-with-dual-y-axes"></a>Personalizar visualizações de eixo Y duplo

Algumas visualizações podem se beneficiar de ter dois eixos Y. Os gráficos de combinação são um bom exemplo. Antes que possamos formatar eixos Y duplos, criaremos um gráfico de combinação que compara tendências para vendas e margem bruta.  

### <a name="create-a-chart-with-two-y-axes"></a>Crie um gráfico com dois eixos Y

1. Selecione o gráfico de colunas e altere-o para um gráfico de *Linhas e colunas empilhadas*. Esse tipo de visual dá suporte a um valor de gráfico de linha única e a vários valores de colunas empilháveis. 

    ![Captura de tela do painel de Visualizações, com o ícone do gráfico de colunas empilhadas e linhas destacado.](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-combo.png)
   

2. Arraste **Vendas** >  **% de Margem Bruta no Ano Passado** do painel Campos para o bucket **Valores da Linha**.

    ![Captura de tela do gráfico de colunas empilhadas e linhas com todos os três valores claramente representados.](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-add-line.png)

    
3. Reformate a visualização para remover os rótulos do eixo X angulares. 

   ![Painel de Formato e gráfico de combinação com tamanho da fonte reduzido para 12](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-font-size.png)

   O Power BI cria dois eixos Y permitindo que os valores sejam dimensionados de forma diferente. O eixo esquerdo calcula os dólares das vendas e o eixo direito calcula o percentual da margem bruta.

### <a name="format-the-second-y-axis"></a>Formatar o segundo eixo Y
Como começamos com uma visualização com um eixo Y formatado, o Power BI criou o segundo eixo Y usando as mesmas configurações. Mas podemos alterar isso. 

1. No painel **Visualizações**, selecione o ícone de rolo de tinta para exibir as opções de formato.

1. Expanda as opções de eixo Y.

1. Role a tela para baixo até encontrar a opção **Mostrar secundário**. Verifique se está **Ativada**. Nosso eixo Y secundário representa o gráfico de linhas.

   ![Captura de tela da opção Mostrar secundário.](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-show-secondary.png)

1. (Opcional) Personalize a cor, o tamanho e as unidades de exibição da fonte para os dois eixos. Se você mudar a **Posição** para o eixo da coluna ou o eixo de linha, os dois eixos trocarão de lado.

### <a name="add-titles-to-both-axes"></a>Adicionar títulos a ambos os eixos

Com uma visualização complexa, convém adicionar títulos de eixos.  Os títulos ajudam seus colegas a compreender a história que a sua visualização está mostrando.

1. Alterne **Título** para **Ativado** para o **Eixo Y (Coluna)** e o **Eixo Y (Linha)** .

1. Defina o **Estilo** para **Mostrar somente o título** de ambos.

   ![Captura de tela das opções Título e Estilo.](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-show-title.png)

1. Seu gráfico de combinação agora mostra eixos duplos, ambos com títulos.

   ![Captura de tela do gráfico de eixos Y duplo personalizado.](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-titles-on.png)

1. Formate os títulos. Neste exemplo, resumimos um dos títulos e reduzimos o tamanho da fonte para ambos. 
    - Tamanho da fonte: **9**
    - Reduzimos o **Título do eixo** para o primeiro eixo Y (o gráfico de colunas): Vendas no ano passado e neste ano

    ![Captura de tela do gráfico de combinação com títulos completos sendo exibidos.](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-dual.png)



Para obter mais informações, confira [Dicas e truques para formatação de cores no Power BI](service-tips-and-tricks-for-color-formatting.md) e [Personalizar títulos de visualização, legendas e planos de fundo](power-bi-visualization-customize-title-background-and-legend.md). Procure também novas atualizações para formatar títulos em breve. 

## <a name="next-steps"></a>Próximas etapas

- [Visualizações em relatórios do Power BI](power-bi-report-visualizations.md)

Mais perguntas? [Experimente a Comunidade do Power BI](https://community.powerbi.com/)
