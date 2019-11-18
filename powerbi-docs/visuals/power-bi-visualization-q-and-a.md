---
title: Usar o visual de P e R do Power BI
description: Como configurar o visual de P e R do Power BI
author: mihart
manager: mohaali
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 10/19/2019
ms.author: mohaali
ms.openlocfilehash: a32c19f07a052aff74fec8062631ea8621d5de18
ms.sourcegitcommit: 23ad768020a9daf129f69a462a2d46d59d2349d2
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72775926"
---
# <a name="introduction-to-power-bi-qa-visual"></a>Introdução ao visual de P e R do Power BI

[!INCLUDE [power-bi-service-new-look-include](../includes/power-bi-service-new-look-include.md)]

## <a name="what-is-the-qa-visual"></a>O que é o visual de P e R

O visual de P e R permite que os usuários façam perguntas em idioma natural e obtenha respostas na forma de um visual. 

![Instruções a passo de visual de P e R](../natural-language/media/qna-visual-walkthrough.gif)

[!INCLUDE [power-bi-visuals-desktop-banner](../includes/power-bi-visuals-desktop-banner.md)]

O visual de P e R pode ser usado como uma ferramenta para permitir que os *consumidores* obtenham rapidamente respostas a seus dados e, para os *designers* criarem visuais no relatório, basta que cliquem duas vezes em qualquer lugar em um relatório e usem idioma natural para começar. Uma vez que ele se comporta como qualquer outro visual, o visual de P e R pode ser com filtrado/realçado de modo cruzado e também dá suporte a marcadores. O visual de P e R também dá suporte a temas e outras opções de formatação padrão disponíveis no Power BI.

O visual de P e R consiste em quatro componentes principais:

- A caixa de perguntas. É nela que os usuários digitam a pergunta e veem sugestões para ajudá-los a concluir a pergunta.
- Uma lista de perguntas sugeridas previamente preenchida.
- Ícone para converter o visual de P e R em um visual padrão. 
- Ícone para abrir a ferramenta de P e R que permite aos designers configurar o mecanismo de linguagem natural subjacente.

## <a name="prerequisites"></a>Pré-requisitos

1. Este tutorial usa o [exemplo de arquivo PBIX de Vendas e Marketing](http://download.microsoft.com/download/9/7/6/9767913A-29DB-40CF-8944-9AC2BC940C53/Sales%20and%20Marketing%20Sample%20PBIX.pbix). 

1. Na seção superior esquerda da barra de menus do Power BI Desktop, selecione **Arquivo** > **Abrir**
   
2. Localize sua cópia do **Arquivo PBIX de exemplo de vendas e marketing**

1. Abrir o arquivo no modo de exibição de relatório ![Captura de tela do ícone da exibição de relatório.](media/power-bi-visualization-kpi/power-bi-report-view.png).

1. Selecionar ![Captura de tela da guia amarela.](media/power-bi-visualization-kpi/power-bi-yellow-tab.png) para adicionar uma nova página.


Se você encontrar um erro ao criar um visual de P e R, confira a seção [limitações](../natural-language/q-and-a-limitations.md) para ver se há suporte para a configuração da fonte de dados.

## <a name="create-a-qa-visual-using-a-suggested-question"></a>Criar um visual de P e R usando uma pergunta sugerida
Neste exercício, selecionaremos uma das perguntas sugeridas para criar nosso visual de P e R. 

1. Comece em uma página de relatório em branco e selecione o ícone de visual de P e R no painel Visualizações.

    ![Painel Visualização com um ícone de visual de P e R descrito](media/power-bi-visualization-q-and-a/power-bi-icon.png)

2. Arraste a borda para redimensionar o visual.

    ![Visual de P e R na tela de relatório](media/power-bi-visualization-q-and-a/power-bi-qna.png)

3. Para criar o visual, selecione uma das perguntas sugeridas ou comece a digitar na caixa de pergunta. Neste exemplo, selecionamos **principais estados geográficos por soma de receita**. O Power BI faz o melhor para selecionar o tipo de visual a ser usado. Nesse caso, é um mapa.

    ![Mapa visual de P e R](media/power-bi-visualization-q-and-a/power-bi-map.png)

    Mas você pode informar o Power BI qual tipo de visual deve ser usado adicionando-o à sua consulta de linguagem natural. Saiba que nem todos os tipos de visuais funcionarão ou farão sentido com seus dados. Por exemplo, esses dados não produzirão um gráfico de dispersão útil. Porém, funciona como um mapa preenchido.

    ![Visual de P e R como um mapa preenchido](media/power-bi-visualization-q-and-a/power-bi-specify-map.png)

## <a name="create-a-qa-visual-using-a-natural-language-query"></a>Criar um visual de P e R usando uma consulta em idioma natural
No exemplo acima, selecionamos uma das perguntas sugeridas para criar nosso visual de P e R.  Neste exercício, vamos digitar nossa própria pergunta. À medida que digitamos nossa pergunta, o Power BI nos ajuda com preenchimento automático, sugestão e comentários.

Se você não tiver certeza de que tipo de perguntas deve ser feita ou que terminologia deve ser usada, expanda **Mostrar todas as sugestões** ou confira o painel Campos, que pode ser encontrado no lado direito da tela. Isso o ajudará a familiarizar-se com os termos e com o conteúdo do conjunto de dados de Vendas e Marketing.

![tela com Mostrar todas as sugestões e o painel Campos realçados](media/power-bi-visualization-q-and-a/power-bi-terminology.png)


1. Digite uma pergunta no campo de P e R. O Power BI adiciona um sublinhado vermelho às palavras que ele não reconhece. Sempre que possível, o Power BI ajuda a definir palavras não reconhecidas.  No primeiro exemplo abaixo, selecionar uma das sugestões funcionará para nós.  

    ![Como digitar uma pergunta na caixa de pergunta de P e R](media/power-bi-visualization-q-and-a/power-bi-red-suggest.png)

2. Conforme digitamos mais partes da uma pergunta, o Power BI informa se ele não entende a pergunta e tenta ajudar. No exemplo a seguir, o Power BI pergunta "Você quis dizer..." e sugere uma maneira diferente de formular a pergunta usando a terminologia do conjunto de seus. 

    ![Visual de P e R exibindo sugestões](media/power-bi-visualization-q-and-a/power-bi-define.png)

5. Com a ajuda do Power BI, conseguimos fazer uma pergunta com todos os termos reconhecíveis. O Power BI exibe os resultados como um gráfico de linhas. 

    ![Resultados visuais de P e R](media/power-bi-visualization-q-and-a/power-bi-type.png)


6. Vamos alterar o visual para um gráfico de colunas. 

    ![Visual de P e R com "como um gráfico de colunas" adicionado à pergunta](media/power-bi-visualization-q-and-a/power-bi-specify-visual.png)

## <a name="format-and-customize-the-qa-visual"></a>Formatar e personalizar o visual de P e R
O visual de P e R pode ser personalizado usando o painel de formatação e aplicando um tema. 

### <a name="apply-a-theme"></a>Aplicar um tema
Quando você seleciona um tema, ele é aplicado a toda a página do relatório. Há muitos temas disponíveis, experimente-os até encontrar a aparência desejada. 

1. Na barra de menus, selecione a guia **Página inicial** e escolha **Alternar tema**. 

    ![Desktop com o tema Alternar selecionado](media/power-bi-visualization-q-and-a/power-bi-themes.png)

    
    
2. Neste exemplo, selecionamos **Mais temas** > **Seguro para daltônicos**.

    ![Visual de P e R com tema para daltônicos aplicado](media/power-bi-visualization-q-and-a/power-bi-color-blind.png)

### <a name="format-the-qa-visual"></a>Formatar o visual de P e R
Formate o visual de P e R, o campo de pergunta e a maneira como as sugestões são exibidas. Você pode alterar tudo, desde a tela de fundo de um título até a cor de foco para palavras não reconhecidas. Aqui, adicionamos uma tela de fundo cinza à caixa de pergunta e alteramos os sublinhados para amarelo e verde. O título é centralizado e tem uma tela de fundo amarela. 

![Visual de P e R mostrando os resultados da formatação](media/power-bi-visualization-q-and-a/power-bi-q-and-a-format.png)

## <a name="convert-your-qa-visual-into-a-standard-visual"></a>Converter o visual de P e R em um visual padrão
Formatamos um pouco nosso gráfico de colunas seguro para daltônicos: adicionamos um título e uma borda. Agora estamos prontos para convertê-lo em um visual padrão em nosso relatório e para fixá-lo em um dashboard.

Selecione o ícone ![ícone engrenagem](media/power-bi-visualization-q-and-a/power-bi-convert-icon.png) para **Transformar esse resultado de P e R em um visual padrão**.

![Visual de P e R com seta apontando para o ícone de visual Padrão](media/power-bi-visualization-q-and-a/power-bi-visual-convert.png)

Este visual não é mais um visual de P e R, mas um gráfico de colunas padrão. Ele pode ser fixado em um dashboard. No relatório, esse visual comporta-se da mesma forma que outros visuais padrão. Observe que o painel Visualizações mostra um ícone de Gráfico de colunas selecionado. em vez do ícone de visual de P e R.

Se estiver usando o ***Serviço do Power BI***, agora você poderá fixar o visual em um dashboard selecionando o ícone de pino. 


![o serviço do Power BI com o ícone de pino realçado](media/power-bi-visualization-q-and-a/power-bi-pin.png)


## <a name="advanced-features-of-the-qa-visual"></a>Recursos avançados do visual de P e R
Selecionar o ícone de engrenagem abre o painel de Ferramentas de visuais de P e R. 

![Visual de P e R com o ícone Ferramenta selecionado](media/power-bi-visualization-q-and-a/power-bi-q-and-a-tooling.png)

Use o painel Ferramentas para ensinar à P e R termos que ele não reconhece, gerenciar esses termos e gerenciar as perguntas sugeridas para esse conjunto de dados e relatório. No painel Ferramentas, você também pode examinar as perguntas feitas usando este visual de P e R e ver as perguntas que foram sinalizadas pelos usuários. Para saber mais, confira [Ferramenta de P e R](../natural-language/q-and-a-tooling-intro.md).

![O painel de Ferramenta de P e R](media/power-bi-visualization-q-and-a/power-bi-q-and-a-tooling-pane.png)

## <a name="considerations-and-troubleshooting"></a>Considerações e solução de problemas
O visual de P e R integra-se ao Office e ao Bing para tentar fazer a correspondência de palavras comuns não reconhecidas com campos em seu conjunto de dados.  

## <a name="next-steps"></a>Próximas etapas

É possível integrar o idioma natural de várias maneiras. Para obter mais informações, consulte os seguintes artigos:

* [Ferramentas de P e R](../natural-language/q-and-a-tooling-intro.md)
* [Melhores práticas de P e R](../natural-language/q-and-a-best-practices.md)
