---
title: Usar botões no Power BI
description: Você pode adicionar botões em relatórios do Power BI que fazem seus relatórios se comportarem como aplicativos e aprofundarem o envolvimento com usuários.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 03/12/2020
ms.author: maggies
LocalizationGroup: Create reports
ms.openlocfilehash: c703a4b67b642af5199413e80ff1e140905a2338
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/05/2020
ms.locfileid: "81439815"
---
# <a name="use-buttons-in-power-bi"></a>Usar botões no Power BI
Usar **botões** no Power BI permite que você crie relatórios que se comportam de modo semelhante a aplicativos e, assim, cria um ambiente envolvente para que os usuários possam focalizar, clicar em e interagir ainda mais com conteúdo do Power BI. Você pode adicionar botões a relatórios no **Power BI Desktop** e no **serviço do Power BI**. Quando você compartilha seus relatórios no serviço do Power BI, eles fornecem uma experiência semelhante ao aplicativo para seus usuários.

![Botões no Power BI](media/desktop-buttons/power-bi-buttons.png)

## <a name="create-buttons-in-reports"></a>Criar botões em relatórios

### <a name="create-a-button-in-power-bi-desktop"></a>Criar um botão no Power BI Desktop

Para criar um botão no **Power BI Desktop**, na faixa de opções **Inserir**, selecione **Botões**. Feito isso, será exibido um menu suspenso, no qual você pode selecionar o botão desejado de uma coleção de opções, conforme mostrado na imagem a seguir. 

![Adicionar um controle de botão no Power BI Desktop](media/desktop-buttons/power-bi-button-dropdown.png)

### <a name="create-a-button-in-the-power-bi-service"></a>Criar um botão no serviço do Power BI

Para criar um botão no **serviço do Power BI**, abra o relatório no Modo de exibição de edição. Selecione **Botões** na barra de menus superior e um menu suspenso será exibido, no qual você pode selecionar o botão desejado de uma coleção de opções, conforme mostrado na imagem a seguir. 

![Adicionar um controle de botão no serviço do Power BI](media/desktop-buttons/power-bi-button-service-dropdown.png)

## <a name="customize-a-button"></a>Personalizar um botão

Se você criar o botão no Power BI Desktop ou no serviço do Power BI, o restante do processo será o mesmo. Quando você seleciona o botão na tela de relatório, o painel **Visualizações** mostra várias maneiras de personalizar o botão de acordo com as suas necessidades. Por exemplo, você pode ativar ou desativar o **Texto do Botão** alternando o controle deslizante no cartão do painel **Visualizações**. Você também pode alterar o ícone do botão, o preenchimento do botão, o título e a ação executada quando os usuários o selecionam em um relatório, entre outras propriedades.

![Formatar um botão em um relatório do Power BI](media/desktop-buttons/power-bi-button-properties.png)

## <a name="set-button-properties-when-idle-hovered-over-or-selected"></a>Definir propriedades do botão quando ocioso, focalizado ou selecionado

Botões no Power BI têm três estados: padrão (como eles aparecem quando não focalizados ou selecionados), quando focalizados ou quando selecionados (conhecido como sendo *clicado*). Muitos dos cartões no painel **Visualizações** podem ser modificados individualmente com base em um desses três estados, fornecendo muita flexibilidade para personalizar os botões.

Os seguintes cartões no painel **Visualizações** permitem que você ajuste a formatação ou o comportamento de um botão com base em seus três estados:

* Texto do botão
* Ícone
* Estrutura de tópicos
* Preencher

Para selecionar como o botão deve ser exibido para cada estado, expanda um dos cartões e selecione na lista suspensa que aparece na parte superior do cartão. Na imagem a seguir, você vê o cartão **Ícone** expandido, com a lista suspensa selecionada para mostrar os três estados.

![Três estados de um botão em um relatório do Power BI](media/desktop-buttons/power-bi-button-format.png)


## <a name="select-the-action-for-a-button"></a>Selecionar a ação para um botão

Você pode selecionar qual ação é realizada quando o usuário seleciona um botão no Power BI. Você pode acessar as opções para ações de botão no cartão **Ação** no painel **Visualizações**.

![Ação de um botão no Power BI](media/desktop-buttons/power-bi-button-action.png)

Veja quais são as opções de ações do botão:

- **Voltar** retorna o usuário para a página anterior do relatório. Isso é útil para páginas de drill-through.
- **Indicador** apresenta a página do relatório associado a um indicador definido para o relatório atual. Saiba mais sobre [indicadores no Power BI](desktop-bookmarks.md). 
- **Drill-through (versão prévia)** navega o usuário até uma página de drill-through filtrada para sua seleção, sem usar indicadores. Saiba mais sobre os [botões de drill-through em relatórios](desktop-drill-through-buttons.md).
- **Navegação na página** navega o usuário até uma página diferente dentro do relatório, também sem usar indicadores. Confira [Criar navegação de página](#create-page-navigation) neste artigo para obter detalhes.
- **P e R** abre uma janela do **Explorador de P e R**. 

Determinados botões têm uma ação padrão selecionada automaticamente. Por exemplo, o tipo de botão **P e R** seleciona automaticamente **P e R** como a ação padrão. Saiba mais sobre o **Explorador de P e R** conferindo [esta postagem no blog](https://powerbi.microsoft.com/blog/power-bi-desktop-april-2018-feature-summary/#Q&AExplorer).

Experimente ou teste os botões que você cria para o relatório usando *CTRL+clique* no botão que você deseja usar. 

### <a name="create-page-navigation"></a>Criar navegação na página

Com a **Ação** do tipo **Navegação na página**, você pode criar rapidamente uma experiência de navegação inteira sem precisar salvar ou gerenciar nenhum indicador.

Para configurar um botão de navegação na página, crie um botão com **Navegação na página** como o tipo de ação e selecione a página **Destino**.

![Ação de navegação na página](media/desktop-buttons/power-bi-page-navigation.png)

Você pode criar rapidamente um painel de navegação personalizado. Você evita a necessidade de editar e gerenciar indicadores, se desejar alterar as páginas a serem exibidas no painel de navegação.

![Criar uma página de navegação](media/desktop-buttons/power-bi-build-navigation-pane.png)

Além disso, é possível formatar condicionalmente a dica de ferramenta como você pode fazer com outros tipos de botão.

## <a name="next-steps"></a>Próximas etapas
Para obter mais informações sobre os recursos que são semelhantes ou interagem com botões, consulte os seguintes artigos:

* [Usar o drill-through nos relatórios do Power BI](desktop-drillthrough.md)
* [Usar indicadores para compartilhar insights e criar histórias no Power BI](desktop-bookmarks.md)

