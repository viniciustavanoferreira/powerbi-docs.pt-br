---
title: Acessibilidade dos relatórios do Power BI Desktop
description: Recursos e sugestões para criar relatórios do Power BI Desktop acessíveis
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/17/2019
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 14e57f5b19fe4dccea9aa47d21c959eaf93a45ae
ms.sourcegitcommit: b53a6f5575f5f8bc443ecdca9c72525ce123518f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2019
ms.locfileid: "70185704"
---
# <a name="accessibility-in-power-bi-desktop-reports"></a>Acessibilidade dos relatórios do Power BI Desktop
O Power BI tem recursos que permitem que pessoas com deficiências consumam e interajam mais facilmente com os relatórios do Power BI Desktop. Esses recursos incluem a capacidade de consumir um relatório usando o teclado ou um leitor de tela, usar a tabulação para focar em vários objetos em uma página e o uso cuidadoso de marcadores nas visualizações.

![Usar diferentes marcadores para gráficos de linhas e de área para melhorar a acessibilidade](media/desktop-accessibility/accessibility-01.png)

## <a name="consuming-a-power-bi-desktop-report-with-a-keyboard-or-screen-reader"></a>Consumir um relatório do Power BI Desktop com um leitor de tela ou um teclado
Da versão de setembro de 2017 do **Power BI Desktop** em diante, você pode pressionar **Shift + ?** para mostrar uma janela que descreve os atalhos de teclado de acessibilidade disponíveis no **Power BI Desktop**.

![Pressione Shift +? no Power BI Desktop para mostrar os atalhos de teclado de acessibilidade](media/desktop-accessibility/accessibility-03.png)

Com as melhorias de acessibilidade, você pode consumir um relatório do Power BI usando um teclado ou um leitor de tela com as seguintes técnicas:

> [!NOTE]
> Ao exibir um relatório, geralmente você precisa desativar o modo de verificação.

Você pode alternar o foco entre as guias de páginas do relatório ou entre objetos em uma determinada página do relatório usando **Ctrl + F6**.

* Quando o foco estiver nas guias da página do relatório, use as teclas **Tab** ou de **Seta** para mover o foco de uma página de relatório para a próxima. O leitor de tela lê o título da página do relatório e se ele está selecionado no momento. Para carregar a página do relatório que está em foco, use a tecla **Enter** ou a barra de espaços.
* Quando o foco estiver em uma página de relatório carregada, use a tecla **Tab** para alternar o foco para cada objeto em uma página, o que inclui todas as caixas de texto, imagens, formas e gráficos. O leitor de tela lê o tipo de objeto e o título do objeto (se houver um). O leitor de tela também lerá uma descrição desse objeto se ela for fornecida pelo autor do relatório. 

Ao navegar entre os visuais, você pode pressionar **Alt + Shift + F10** para mover o foco para o cabeçalho de visual. O cabeçalho de visual contém várias opções, incluindo classificação, exportação dos dados por trás do gráfico e modo de Foco. 

![Pressione Alt + Shift + F10 no Power BI Desktop para mover o foco para o cabeçalho de visual](media/desktop-accessibility/accessibility-08.png)

Você pode pressionar **Alt + Shift + F11** para apresentar uma versão acessível da janela **Mostrar dados**. Essa janela permite que você explore os dados usados no visual em uma tabela HTML, usando os mesmos atalhos de teclado que normalmente são usados com o leitor de tela. 

![Pressione Alt + Shift + F11 no Power BI Desktop para exibir uma janela acessível Ver Dados para um visual](media/desktop-accessibility/accessibility-04.png)

> [!NOTE]
> O recurso **Mostrar dados** somente pode ser acessado em um leitor de tela com esse atalho de teclado. Se você abrir **Mostrar dados** por meio da opção no cabeçalho de visual, ele não poderá ser acessado em um leitor de tela. Ao usar **Mostrar dados**, ative o modo de verificação para aproveitar todas as teclas de acesso fornecidas pelo leitor de tela.

A partir da versão de julho de 2018 do **Power BI Desktop**, as segmentações de dados também passam a ter a funcionalidade de acessibilidade interna. Para ajustar o valor de uma segmentação ao selecioná-la, use **Ctrl + seta para a direita** (tecla Control e seta para a direita) para percorrer os vários controles na segmentação. Por exemplo, quando você pressiona inicialmente **CTRL + seta para a direita**, o foco está na borracha. Em seguida, pressionar a barra de espaços é equivalente a clicar no botão borracha, que apaga todos os valores na segmentação. 

Você pode percorrer os controles em uma segmentação de dados pressionando a tecla **Tab**. Pressionar a tecla **Tab** na borracha muda para o botão suspenso. Pressionar **Tab** outra vez move para o primeiro valor da segmentação (se houver vários valores para a segmentação, como um intervalo). 

![Pressione Ctrl + seta para a direita no Power BI Desktop para ajustar um elemento ou os valores em uma segmentação; pressione a barra de espaços para selecionar o elemento e ajustar seu valor](media/desktop-accessibility/accessibility-07.png)

Essas adições de acessibilidade permitem que os usuários consumam totalmente os relatórios do Power BI usando um leitor de tela e a navegação pelo teclado.

## <a name="tips-for-creating-accessible-reports"></a>Dicas para criar relatórios acessíveis
As dicas a seguir podem ajudá-lo a criar relatórios do **Power BI Desktop** que são mais acessíveis.

### <a name="general-tips-for-accessible-reports"></a>Dicas gerais para relatórios acessíveis

* Para visuais de **Linha**, **Área** e **Combinação**, bem como para visuais de **Dispersão** e de **Bolha**, ative a alternância **Mostrar marcadores** e use uma **Forma de marcador** diferente para cada linha.
  
  * Para ativar a alternância **Mostrar marcadores**, selecione a seção **Formato** no painel **Visualizações** e expanda a seção **Formas**. Role para baixo para localizar a alternância **Mostrar marcadores** e defina-a como **Ativada**.
  * Para personalizar as linhas individuais, localize a alternância **Personalizar série** e defina-a como **Ativada**. Em seguida, selecione o nome de cada linha (ou área, se estiver usando um gráfico de **Área**) na caixa suspensa na seção **Formas**. Abaixo da lista suspensa, você pode ajustar vários aspectos do marcador usado para a linha selecionada, incluindo seu tamanho, cor e forma.
  
    ![Usar diferentes marcadores para gráficos de linhas e de área para melhorar a acessibilidade](media/desktop-accessibility/accessibility-format-section.png)
  
  * Usar uma **Forma de marcador** diferente para cada linha torna mais fácil para os consumidores do relatório diferenciar as linhas (ou áreas) umas das outras.
* Como um lembrete do marcador anterior, não confie na cor para transmitir informações. Ao usar formas em gráficos de dispersão e de linha, não confie na formatação condicional para fornecer insights em tabelas e matrizes. 
* Escolha uma ordem de classificação intencional para cada visual em seu relatório. Quando os usuários de leitores de tela navegam nos dados por trás do gráfico, ele seleciona a mesma ordem de classificação que o visual.
* Selecione um tema de alto contraste e adequado para pessoas daltônicas na galeria de temas. Importe-o usando a versão prévia do recurso [**Temas**](desktop-report-themes.md).
* Para cada objeto em um relatório, forneça um texto alternativo. Isso garante que seus consumidores de relatório compreendam o que você está tentando comunicar com um visual. Inclusive ajuda se eles não conseguirem ver o visual, a imagem, a forma ou a caixa de texto. Você pode fornecer um texto alternativo para qualquer objeto em um relatório do **Power BI Desktop** selecionando o objeto (como um visual, forma e assim por diante) e, no painel **Visualizações**, selecionando a seção **Formato**. Em seguida, expanda **Geral**, role até a parte inferior e preencha a caixa de texto referente a **Texto alternativo**.
  
  ![O texto alternativo para qualquer objeto em um relatório pode ser adicionado em Visualizações > Formato > Geral > caixa de texto Alt](media/desktop-accessibility/accessibility-02.png)
  
  O texto Alt também pode ser alterado dinamicamente com uma expressão, por exemplo, refletindo os filtros aplicados a um visual. Você define uma expressão da mesma forma que faria para o título de um visual. [Formatação condicional para títulos visuais](desktop-conditional-format-visual-titles.md)
  
* Verifique se os relatórios têm contraste suficiente entre o texto e as cores da tela de fundo. Há várias ferramentas, como o [Analisador de Contraste de Cores](https://developer.paciellogroup.com/resources/contrastanalyser/), que você pode usar para verificar as cores do relatório. 
* Use fontes e tamanhos de texto que podem ser facilmente lidos. Um tamanho de texto pequeno, ou fontes que podem ser difíceis de serem lidas, não serão úteis para acessibilidade.
* Inclua um título, rótulos de eixo e rótulos de dados em todos os visuais.
* Use títulos significativos para todas as páginas de relatório.
* Evite formas e imagens decorativas em seu relatório, se possível, pois elas são incluídas na ordem de tabulação do relatório. Se você precisar incluir objetos decorativos em seu relatório, atualize o texto Alt do objeto para informar aos usuários de leitores de tela que eles são decorativos.

### <a name="arranging-items-in-field-buckets"></a>Organização de itens nos buckets de campo
Da versão de outubro de 2018 do **Power BI Desktop** em diante, também é possível navegar em **Campos** com um teclado e ele interage com os leitores de tela. 

Para melhorar o processo de criar relatórios com leitores de tela, um menu de contexto está disponível. O menu permite mover campos para cima ou para baixo na lista **Campos**. O menu também permite mover o campo para outras caixas, como **Legenda**, **Valor** ou outras.

![O menu de contexto no espaço Campos também permite que você movimente os campos para cima, para baixo ou para outra área](media/desktop-accessibility/accessibility-09.png)

## <a name="high-contrast-support-for-reports"></a>Suporte para alto contraste em relatórios

Quando você usa os modos de alto contraste no Windows, essas configurações e a paleta selecionada também são aplicadas aos relatórios no **Power BI Desktop**. 

![Configurações de alto contraste do Windows](media/desktop-accessibility/accessibility-05.png)

O **Power BI Desktop** detecta automaticamente qual tema de alto contraste o Windows está usando e aplica essas configurações a seus relatórios. Essas cores em alto contraste continuam no relatório quando ele é publicado no serviço do Power BI ou em outro lugar.

![Configurações de alto contraste do Windows](media/desktop-accessibility/accessibility-05b.png)

O serviço do Power BI também tenta detectar as configurações de alto contraste selecionadas para o Windows. A eficácia e a precisão dessa detecção dependem do navegador que mostra a serviço do Power BI. Se você desejar definir o tema manualmente no serviço do Power BI, selecione **Exibição** > **Cores de alto contraste** e, em seguida, selecione o tema que deseja aplicar ao relatório.

![Definindo o alto contraste no serviço do Power BI](media/desktop-accessibility/accessibility-06.png)

## <a name="considerations-and-limitations"></a>Considerações e limitações
Há alguns problemas conhecidos e algumas limitações com os recursos de acessibilidade. As descrições desses problemas e limitações estão na lista a seguir:

* Ao usar leitores de tela com o **Power BI Desktop**, a experiência será melhor se você abrir o leitor de tela de sua preferência antes de abrir qualquer arquivo no **Power BI Desktop**.
* Se você estiver usando o Narrator, haverá algumas limitações ao navegar em **Mostrar dados** como uma tabela HTML.

## <a name="keyboard-shortcuts"></a>Atalhos de teclado
Os atalhos de teclado são úteis para se movimentar pelos relatórios do Power BI usando o teclado. As tabelas a seguir descrevem os atalhos disponíveis em um relatório do Power BI. Além de usar estes atalhos de teclado no **Power BI Desktop**, eles também funcionam nas seguintes experiências:

* Caixa de diálogo **Explorador de Perguntas e Respostas**
* Caixa de diálogo **Introdução**
* Menu **Arquivo** e caixa de diálogo **Sobre**
* Barra de **Aviso**
* Caixa de diálogo **Restauração de Arquivo**
* Caixa de diálogo **Rostos tristes**

Em nosso esforço contínuo para melhorar a acessibilidade, a lista anterior de experiências também dá suporte a leitores de tela e configurações de alto contraste.


### <a name="frequently-used-shortcuts"></a>Atalhos usados com frequência
| Para executar esta ação           | Pressione                |
| :------------------- | :------------------- |
| Mover o foco entre as seções  | **Ctrl + F6** |
| Mover o foco para frente na seção | **Tab**         |
| Mover o foco para trás na seção | **Shift + Tab** |
| Selecionar ou limpar a seleção de um objeto | **Enter** ou **barra de espaços** |
| Selecionar vários objetos | **Ctrl + barra de espaços** |

### <a name="on-visual"></a>No visual
| Para executar esta ação           | Pressione                |
| :------------------- | :------------------- |
| Mover o foco para o menu visual | **Alt + Shift + F10** |
| Mostrar dados | **Alt + Shift + F11**  |
| Inserir um visual | **Ctrl + Seta para a direita** |
| Inserir uma camada | **Enter** |
| Sair de uma camada ou de um visual | **Esc** |
| Selecionar ou limpar a seleção de um ponto de dados | **Enter** ou **barra de espaços** |
| Seleção múltipla | **Ctrl + Enter** ou **Ctrl + barra de espaços** |
| Clique com o botão direito do mouse | <ul><li>Teclados Windows: **Tecla de contexto do Windows + F10**. A tecla de contexto do Windows fica entre a tecla Alt esquerda e a tecla de direção para a esquerda</li><li>Outros teclados: **Shift + F10**</li></ul> |
| Limpar seleção | **Ctrl + Shift + C** |

### <a name="table--matrix-navigation"></a>Navegação de tabela e matriz
| Para executar esta ação          | Pressione                |
| :------------------- | :------------------- |
| Mover o foco para cima/para baixo uma célula (em todas as células de todas as áreas)  | **Tecla de direção para cima** / **Tecla de direção para baixo** |
| Mover o foco para a esquerda/direita uma célula (em todas as células de todas as áreas)  | **Tecla de direção para a esquerda** / **Tecla de direção para a direita** |

### <a name="pane-navigation"></a>Navegação no painel
| Para executar esta ação           | Pressione                |
| :------------------- | :------------------- |
| Seleção múltipla | **Ctrl + barra de espaços** |
| Recolher uma tabela única | **Tecla de direção para a esquerda** |
| Expandir uma tabela única | **Tecla de direção para a direita** |
| Recolher todas as tabelas | **Alt + Shift + 1** |
| Expandir todas as tabelas | **Alt + Shift + 9** |
| Abrir um menu de contexto | <ul><li>Teclados Windows: **Tecla de contexto do Windows + F10**.  A tecla de contexto do Windows fica entre a tecla Alt esquerda e a tecla de direção para a esquerda</li><li>Outros teclados: **Shift + F10**</li></ul> |

### <a name="slicer"></a>Segmentação de Dados
| Para executar esta ação         | Pressione                |
| :------------------- | :------------------- |
| Interagir com uma segmentação | **Ctrl + tecla de direção para a direita** |

### <a name="selection-pane"></a>Painel de seleção
| Para executar esta ação           | Pressione                |
| :------------------- | :------------------- |
| Ativar o painel de seleção | **F6** |
| Mover um objeto para cima na disposição em camadas | **Ctrl + Shift + F** |
| Mover um objeto para baixo na disposição em camadas | **Ctrl + Shift + B** |
| Ocultar/mostrar (ativar/desativar) um objeto | **Ctrl + Shift + S** |

### <a name="dax-editor"></a>Editor do DAX
| Para executar esta ação          | Pressione                |
| :------------------- | :------------------- |
| Mover linha para cima/para baixo | **Alt + tecla de direção para cima** / **Tecla de direção para baixo** |
| Copiar linha acima/abaixo | **Shift + Alt + tecla de direção para cima** / **tecla de direção para baixo** |
| Inserir linha abaixo | **Ctrl + Enter** |
| Inserir linha acima | **Ctrl + Shift + Enter** |
| Ir para o colchete correspondente | **Ctrl + Shift +**  \ |
| Recuar linha/estender linha até a margem | **Ctrl + ]**  /  **[** |
| Inserir o cursor | **Alt + Clique** |
| Selecionar a linha atual | **Ctrl + I** |
| Selecionar todas as ocorrências da seleção atual | **Ctrl + Shift + L** |
| Selecionar todas as ocorrências da palavra atual | **Ctrl + F2** |

### <a name="enter-data"></a>Inserir dados
| Para executar esta ação           | Pressione                |
| :------------------- | :------------------- |
| Sair da grade editável | **Ctrl + Tab** |


## <a name="next-steps"></a>Próximas etapas
* [Usar Temas de Relatório no Power BI Desktop (Versão prévia)](desktop-report-themes.md)

