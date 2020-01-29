---
title: Dicas de design de relatório no Construtor de Relatórios do Power BI
description: Use as dicas a seguir para ajudar a criar seus relatórios paginados no Power BI Report Builder.
ms.date: 06/06/2019
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.assetid: c1490ff0-5b8a-43c1-8d22-e459395db4f6
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 3b436156d6bd36fe5da7b9b4404227ca1a6de336
ms.sourcegitcommit: 3d6b27e3936e451339d8c11e9af1a72c725a5668
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2020
ms.locfileid: "76160525"
---
# <a name="report-design-tips-in-power-bi-report-builder"></a>Dicas de design de relatório no Construtor de Relatórios do Power BI
  Use as dicas a seguir para ajudar a criar seus relatórios paginados no Power BI Report Builder.  
  
   
  
##  <a name="DesigningReports"></a> Como criar relatórios  
  
-   Um relatório bem projetado transmite informações que resultam em ações. Identifique as perguntas que o relatório ajuda a responder. Mantenha essas perguntas em mente ao projetar o relatório.  
  
-   Para criar visualizações de dados efetivas, pense em como exibir informações que sejam de fácil entendimento para o usuário do relatório. Escolha uma região de dados que seja uma boa correspondência para os dados que deseja visualizar. Por exemplo, um gráfico transmite informações resumidas e agregadas efetivamente melhor do que uma tabela que inclui muitas páginas de informações detalhadas. Você pode visualizar os dados de um conjunto de dados em qualquer região de dados, que inclui gráficos, mapas, indicadores, minigráficos, barras de dados e dados de tabela em vários layouts de grade com base em um Tablix. 
  
-   Se você pretende entregar o relatório em um formato de exportação específico, teste o formato de exportação no início do design. O suporte de recursos varia de acordo com o renderizador escolhido.  
  
-   Quando você cria layouts complexos, crie o layout em estágios. Use retângulos como contêineres para organizar os itens de relatório. Crie regiões de dados diretamente na área de design para maximizar a área de trabalho e, conforme você conclui cada uma delas, arraste-a para o contêiner de retângulo. Usando retângulos como contêineres, você pode posicionar todo o seu conteúdo em uma única etapa. Os retângulos também ajudam a controlar a forma como os itens de relatório são renderizados em cada página.  
  
-   Para reduzir a desordem em um relatório, considere o uso da visibilidade condicional para itens de relatório específicos e deixe o usuário escolher se ele deseja mostrar os itens. Defina a visibilidade com base em um parâmetro ou uma alternância de caixa de texto. Adicione caixas de texto oculto condicionalmente para mostrar resultados de expressão provisórios. Quando um relatório exibe dados inesperados, você pode mostrar esses resultados provisórios para ajudar a depurar expressões.  
  
-   Ao trabalhar com itens aninhados em células ou retângulos Tablix, você pode definir diferentes cores da tela de fundo para o contêiner e os itens contidos. Por padrão, a cor da tela de fundo é **Sem cor**. Os itens com uma cor da tela de fundo específica se tornam visíveis em itens com uma cor da tela de fundo definida como **Sem cor**. Essa técnica pode ajudá-lo a selecionar o item certo para definir as propriedades de exibição, como a visibilidade de borda em células Tablix.  
  
 Para obter mais informações sobre os aspectos a serem considerados durante o design de seu relatório, confira [Como planejar um relatório no Construtor de Relatórios](report-builder-planning-report.md)).  
  
##  <a name="NamingConventions"></a> Convenções de nomenclatura para relatórios, fontes de dados e conjuntos de dados  
  
-   Use convenções de nomenclatura para fontes de dados e conjuntos de dados que documentam a fonte de dados.  
  
    1.  **Fontes de dados.** Caso você não deseje usar um servidor ou um banco de dados real devido a motivos de segurança, use um alias que indique ao usuário qual é a fonte de dados.  
  
    2.  **Conjuntos de dados.** Use um nome que indique em qual fonte de dados ele se baseia.  
  
##  <a name="Data"></a> Como trabalhar com os dados  
  
-   Como uma primeira etapa, exiba todos os dados com os quais deseja trabalhar no painel de dados do relatório. Ao refinar as perguntas às quais o relatório foi projetado para responder, pense em como limitar os dados nos conjuntos de dados do relatório para apenas os que são necessários.  
  
-   Em geral, inclua apenas os dados que serão exibidas em um relatório. Use variáveis de consulta nas consultas do conjunto de dados para permitir que o usuário escolha quais dados ele deseja ver no relatório. Se você estiver criando conjuntos de dados compartilhados, forneça filtros com base nos parâmetros de relatório para fornecer a mesma funcionalidade.  
  
-   Se você for um editor de consultas experiente, entenda que, para quantidades intermediárias de dados, talvez você deseje agrupar dados no relatório e não na consulta. Se você fizer todo o agrupamento na consulta, o relatório tenderá a ser uma apresentação do conjunto de resultados da consulta. Por outro lado, para exibir valores agregados para grandes quantidades de dados em um gráfico ou uma matriz, não há necessidade de incluir dados detalhados.  
  
-   Dependendo de seus requisitos, você pode exibir os nomes e as localizações de fontes de dados do relatório, o texto de comando de consulta do conjunto de dados e os valores de parâmetro no relatório. A primeira pergunta que muitos usuários novos fazem é sobre a origem dos dados. Para reduzir a desordem no relatório, você pode ocultar caixas de texto condicionalmente com esse tipo de informação e permitir que os usuários escolham se desejam visualizá-lo. Tente adicionar essas informações na última página do relatório. Defina a visibilidade da caixa de texto com base em um parâmetro que o usuário possa alterar.  
  
##  <a name="DesignSurface"></a> Como interagir com a área de design do relatório  
 A área de design do relatório não é WYSIWIG. Quando você coloca itens de relatório na área de design, sua localização relativa afeta a maneira como os itens são exibidos na página do relatório renderizado. O espaço em branco é preservado.  
  
-   Use guias de alinhamento e botões de layout para alinhar e organizar itens na área de design do relatório. Por exemplo, alinhe as partes superiores ou as bordas dos itens selecionados, expanda um item para que ele corresponda ao tamanho de outro item ou ajuste o espaçamento entre itens.  
  
-   Use as teclas de direção para ajustar a posição e o tamanho dos itens selecionados na área de design. Por exemplo, as seguintes combinações de teclas são muito úteis:  
  
    -   **Teclas de direção** Movem o item de relatório selecionado.  
  
    -   **CTRL+Teclas de direção** Deslocam o item de relatório selecionado.  
  
    -   **CTRL+SHIFT+Teclas de direção** Aumentam ou diminuem o tamanho do item de relatório selecionado.  
  
-   Para adicionar um item a um retângulo, use a ponta esquerda superior do mouse para apontar para a localização inicial do item no contêiner do retângulo. Use atalhos de teclado para ajudar a posicionar os objetos selecionados. O retângulo se expande automaticamente para acomodar o tamanho dos itens contidos.  
  
-   Para adicionar vários itens a uma célula Tablix, primeiro adicione um retângulo e, em seguida, adicione os itens.  
  
     Por padrão, cada célula Tablix contém uma caixa de texto. Quando você adiciona um retângulo a uma célula, o retângulo substitui a caixa de texto. Por exemplo, posicione indicadores aninhados em um retângulo em uma célula Tablix para ajudar a controlar como o tamanho de um gráfico ou um indicador é expandido quando você altera a altura da linha na qual a célula se encontra.  
  
-   Use o controle **Zoom** para ajustar a exibição da área de design. Você pode trabalhar com a página inteira ou seções menores da página.  
  
-   Para arrastar campos do painel de dados do relatório para o painel Agrupamento, evite arrastar o campo por outros itens de relatório na área de design, pois isso seleciona os outros itens e desmarca a região de dados Tablix. Arraste o campo para baixo no painel de dados do relatório e, em seguida, para o painel Agrupamento.  
  
###  <a name="Selecting"></a> Como selecionar itens  
 Para ajudar a selecionar o objeto desejado na área de design do relatório, use a tecla ESC, o menu de contexto de atalho, o painel Propriedades e o painel Agrupamento.  
  
-   -   Pressione ESC para percorrer a pilha de itens de relatório que ocupam o mesmo espaço na área de design.  
  
    -   Em alguns itens de relatório, experimente usar o menu de contexto de atalho para selecionar o item de relatório ou a parte do item de relatório desejada.  
  
    -   O painel Propriedades exibe as propriedades da seleção atual.  
  
    -   Para trabalhar com grupos de linhas e grupos de colunas em uma região de dados Tablix, selecione o grupo no painel Agrupamento.  

  
##  <a name="ReportItems"></a> Como trabalhar com tipos específicos de itens de relatório  
  
###  <a name="Parameters"></a> Como trabalhar com parâmetros  
  
-   O objetivo principal dos parâmetros de relatório é filtrar os dados na fonte de dados e recuperar apenas o que é necessário para os fins do relatório.  
  
-   Para parâmetros de relatório, encontre um equilíbrio entre habilitar a interatividade e ajudar um usuário a obter os resultados desejados. Por exemplo, você pode definir valores padrão de um parâmetro para valores que você sabe que são populares.  
  
###  <a name="Text"></a> Como trabalhar com texto  
  
-   Quando você cola multilinhas em uma caixa de texto, o texto é adicionado como uma execução de texto. Cada execução de texto só pode ser formatada como uma unidade. Para formatar cada linha de maneira independente, insira uma nova linha pressionando RETURN na execução de texto, conforme necessário. Em seguida, você pode aplicar formatação e estilos a cada linha de texto independente na caixa de texto.  
  
-   Defina propriedades de formato e ações em uma caixa de texto ou no texto do espaço reservado na caixa de texto. Se houver apenas uma linha de texto, será mais eficiente definir propriedades na caixa de texto do que no texto.  
  
###  <a name="Expressions"></a> Como trabalhar com expressões  
  
-   Entenda os formatos de expressões simples e complexas. Digite o formato de expressão simples diretamente nas caixas de texto, nas propriedades no painel Propriedade ou nas localizações em caixas de diálogo que aceitam uma expressão.
  
-   Quando você cria uma expressão, ela ajuda a criar cada parte de maneira independente e verificar seu valor. Em seguida, você pode combinar todas as partes em uma expressão final. Uma técnica útil é adicionar uma caixa de texto a uma célula de matriz, exibir cada parte da expressão e definir a visibilidade condicional na caixa de texto. Para controlar o estilo de borda e a cor quando a caixa de texto é ocultada, primeiro coloque a caixa de texto em um retângulo e, em seguida, defina o estilo de borda e a cor do retângulo para que correspondam à matriz.  
  
###  <a name="Indicators"></a> Como trabalhar com indicadores  
  
-   Por padrão, um indicador mostra, pelo menos, três estados. Depois de adicionar um indicador a um relatório, você poderá configurá-lo adicionando ou removendo estados. Para facilitar a exibição pelos usuários, escolha um indicador que varie por cor e forma.  
  
##  <a name="Rendering"></a> Como controlar a renderização de itens de relatório na página do relatório  
  
-   Na área de design do relatório, os itens de relatório crescem para acomodar o conteúdo do conjunto de dados, da expressão, do sub-relatório ou do texto associado.  
  
    -   Quando você posiciona um item na página do relatório, a distância entre o item e todos os itens que começam à sua direita torna-se a distância mínima que precisa ser mantida conforme um item de relatório cresce na horizontal. Da mesma forma, a distância entre um item e o item acima dele torna-se uma distância mínima que precisa ser mantida conforme o item superior cresce na vertical.  
  
    -   Um item em um relatório cresce para acomodar seus dados e empurra os itens pares (itens dentro do mesmo contêiner pai) para fora do caminho usando as seguintes regras:  
  
    -   Cada item é movido para baixo para manter o espaço mínimo entre ele mesmo e os itens que terminam acima dele.  
  
    -   Cada item é movido para a direita para manter o espaço mínimo entre ele mesmo e os itens que terminam à sua esquerda. Para sistemas com layouts da direita para a esquerda, cada item é movido para a esquerda para manter o espaço mínimo entre ele mesmo e os itens que terminam à sua direita.  
  
    -   Os contêineres se expandem para acomodar o crescimento dos itens filho. Para um item selecionado, no painel Propriedades, a propriedade Parent identifica o contêiner do item. Use também o painel Estrutura de Tópicos do Documento para ver a hierarquia de independência dos itens de relatório.  
  
    -   A barra de ferramentas **Layout** fornece vários botões para ajudar a alinhar bordas, centros e espaçamento para itens de relatório. Para habilitar a barra de ferramentas **Layout**, no menu **Exibir**, aponte para **Barras de Ferramentas** e, em seguida, clique em **Layout**.  
  
-   Se você pretende salvar o relatório como um arquivo .pdf, a largura do relatório precisará ser definida explicitamente como um valor que forneça os resultados desejados no formato de arquivo de exportação. Por exemplo, defina a largura da página do relatório exatamente como 7,9375 polegadas e as margens esquerda e direita como 0,5 polegada.  
  
-   Use **Layout de Impressão** e **Configuração de Página** na barra de ferramentas do Visualizador de Relatórios para renderizar um relatório em uma exibição compatível com impressão. Para ajudar a remover as páginas em branco desnecessárias, faça o seguinte:  
  
    1.  Remova todo o espaço em branco extra entre as regiões de dados e nas bordas do relatório.  
  
    2.  Reduza as margens da página na caixa de diálogo **Propriedades do Relatório**.  
  
    3.  Use **Retângulos** como contêineres para ajudar a controlar a maneira como os itens de relatório são renderizados.  
  
    4.  Em cabeçalhos de coluna, altere a propriedade da caixa de texto WritingMode para usar o texto vertical.  

 Para saber mais, confira [Evitar páginas em branco ao imprimir relatórios paginados](guidance/report-paginated-blank-page.md).

 A combinação desse comportamento, das propriedades de largura e altura dos itens de relatório, do tamanho do corpo do relatório, da definição de largura e altura da página, das configurações de margem do relatório pai e do suporte específico do renderizador para paginação determinam quais itens de relatório se ajustam em conjunto em uma página renderizada.
 
## <a name="next-steps"></a>Próximas etapas

- [O que são os relatórios paginados no Power BI Premium?](paginated-reports-report-builder-power-bi.md)  
