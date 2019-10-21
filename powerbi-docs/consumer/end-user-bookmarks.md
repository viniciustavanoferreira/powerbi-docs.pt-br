---
title: Visão geral dos indicadores nos relatórios do serviço do Power BI
description: Tópico de visão geral da documentação para consultas de linguagem naturais de P e R do Power BI.
author: mihart
manager: kvivek
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 10/18/2019
ms.author: mihart
LocalizationGroup: Create reports
ms.openlocfilehash: 5383b06bbc40953ea9f4322562190b6a7b29db14
ms.sourcegitcommit: f34acbf9fb1ab568fd89773aaf412a847f88dd34
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72589441"
---
# <a name="what-are-bookmarks"></a>O que são indicadores?

[!INCLUDE [power-bi-service-new-look-include](../includes/power-bi-service-new-look-include.md)]

Os indicadores capturam a exibição atualmente configurada de uma página de relatório, incluindo filtros, segmentações e o estado dos visuais. Quando você seleciona um indicador, o Power BI direciona-o novamente para essa exibição. Há dois tipos de indicadores – aqueles que você cria por conta própria e aqueles criados pelos *designers* de relatórios.

## <a name="use-bookmarks-to-share-insights-and-build-stories-in-power-bi"></a>Usar indicadores para compartilhar insights e criar histórias no Power BI 
Há muitos usos para os indicadores. Digamos que você descubra um insight interessante e queira preservá-lo – crie um indicador para retornar a ele mais tarde. Precisa sair e deseja preservar seu trabalho atual? Crie um indicador. Você pode até mesmo marcar a exibição padrão do relatório, de modo que sempre que você retornar, essa exibição da página de relatório seja aberta primeiro. 

Você também pode criar uma coleção de indicadores, organizá-los na ordem desejada e, posteriormente, percorrer cada indicador em uma apresentação para realçar uma série de insights que contam uma história.  

![Mostre o Painel Indicadores selecionando-o na faixa de opções.](media/end-user-bookmarks/power-bi-select-bookmark.png)

## <a name="open-bookmarks"></a>Abrir indicadores
Para abrir o painel Indicadores, selecione **Indicadores** > **Mostrar mais indicadores** na barra de menus. Para retornar à exibição publicada original do relatório, selecione **Redefinir para padrão**.

### <a name="report-bookmarks"></a>Indicadores de relatório
Se o *designer* de relatórios incluir indicadores de relatório, você os encontrará com o título **Indicadores de relatório**. Esta página de relatório tem dois indicadores, B1 e B2. 

![Mostre Indicadores de relatório.](media/end-user-bookmarks/power-bi-report.png)

Selecione um indicador para alterar para essa exibição de relatório. 

![Vídeo mostrando os indicadores de relatório que estão sendo selecionados.](media/end-user-bookmarks/power-bi-bookmarks.gif)

### <a name="personal-bookmarks"></a>Indicadores pessoais

Quando você cria um indicador, os seguintes elementos são salvos com o indicador:

* A página atual
* Filtros
* A segmentação de dados, incluindo o tipo de segmentação de dados (por exemplo, menu suspenso ou lista) e o estado de segmentação de dados
* Estado de seleção visual (como filtros de realce cruzado)
* Ordem de classificação
* Local de análise
* Visibilidade (de um objeto, usando o painel **Seleção**)
* Os modos de foco ou de **Destaque** de qualquer objeto visível

Configure uma página de relatório da maneira que você deseja que ela seja exibida no indicador. Depois que a página de relatório e os visuais forem organizados como você deseja, selecione **Adicionar** no painel **Indicadores** para adicionar um indicador. Neste exemplo, adicionamos alguns filtros para a região e a data. 

![Adicione indicadores Pessoais.](media/end-user-bookmarks/power-bi-bookmark-personal.png)

O **Power BI** cria um indicador pessoal e dá a ele um nome genérico ou um nome que você inserir. Você pode *renomear*, *excluir* ou *atualizar* o indicador selecionando as reticências ao lado do nome dele e, em seguida, selecionando uma ação no menu que é exibido.

Depois de obter um indicador, basta exibi-lo selecionando o indicador no painel **Indicadores**. 

![Adicione indicadores Pessoais.](media/end-user-bookmarks/power-bi-bookmark-west.png)


<!--
## Arranging bookmarks
As you create bookmarks, you might find that the order in which you create them isn't necessarily the same order you'd like to present them to your audience. No problem, you can easily rearrange the order of bookmarks.

In the **Bookmarks** pane, simply drag-and-drop bookmarks to change their order, as shown in the following image. The yellow bar between bookmarks designates where the dragged bookmark will be placed.

![Change bookmark order by drag-and-drop](media/desktop-bookmarks/bookmarks_06.png)

The order of your bookmarks can become important when you use the **View** feature of bookmarks, as described in the next section. 

-->

## <a name="bookmarks-as-a-slide-show"></a>Indicadores como uma apresentação de slides
Para apresentar ou exibir indicadores, em ordem, selecione **Exibir** no painel **Indicadores** para iniciar uma apresentação de slides.

Quando se está no modo **Exibição**, há alguns recursos a observar:

- O nome do indicador aparece na barra de título de indicador, que aparece na parte inferior da tela.
- A barra de título de indicador tem setas que permitem que você mova para o indicador anterior ou para o próximo.
- Você pode sair do modo de **Exibição** selecionando **Sair** no painel **Indicadores** ou então selecionando o **X** encontrado na barra de título de indicador.

![Apresentação de slides dos indicadores](media/end-user-bookmarks/power-bi-slideshow.png)

Quando se está no modo **Exibição**, é possível fechar o painel **Indicadores** (clicando no X no painel) para fornecer mais espaço para a apresentação. E enquanto se está no modo de **Exibição**, todos os visuais são interativos e estão disponíveis para realce cruzado, exatamente como eles seriam ao interagir com eles fora desse modo. 

<!--
## Visibility - using the Selection pane
With the release of bookmarks, the new **Selection** pane is also introduced. The **Selection** pane provides a list of all objects on the current page and allows you to select the object and specify whether a given object is visible. 

![Enable the Selection pane](media/desktop-bookmarks/bookmarks_08.png)

You can select an object using the **Selection** pane. Also, you can toggle whether the object is currently visible by clicking the eye icon to the right of the visual. 

![Selection pane](media/desktop-bookmarks/bookmarks_09.png)

When a bookmark is added, the visible status of each object is also saved based on its setting in the **Selection** pane. 

It's important to note that **slicers** continue to filter a report page, regardless of whether they are visible. As such, you can create many different bookmarks, with different slicer settings, and make a single report page appear very different (and highlight different insights) in various bookmarks.


## Bookmarks for shapes and images
You can also link shapes and images to bookmarks. With this feature, when you click on an object, it will show the bookmark associated with that object. This can be especially useful when working with buttons; you can learn more by reading the article about [using buttons in Power BI](desktop-buttons.md). 

To assign a bookmark to an object, select the object, then expand the **Action** section from the **Format Shape** pane, as shown in the following image.

![Add bookmark link to an object](media/desktop-bookmarks/bookmarks_10.png)

Once you turn the **Action** slider to **On** you can select whether the object is a back button, a bookmark, or a Q&A command. If you select bookmark, you can then select which of your bookmarks the object is linked to.

There are all sorts of interesting things you can do with object-linked bookmarking. You can create a visual table of contents on your report page, or you can provide different views (such as visual types) of the same information, just by clicking on an object.

When you are in editing mode you can use ctrl+click to follow the link, and when not in edit mode, simply click the object to follow the link. 


## Bookmark groups

Beginning with the August 2018 release of **Power BI Desktop**, you can create and use bookmark groups. A bookmark group is a collection of bookmarks that you specify, which can be shown and organized as a group. 

To create a bookmark group, hold down the CTRL key and select the bookmarks you want to include in the group, then click the ellipses beside any of the selected bookmarks, and select **Group** from the menu that appears.

![Create a bookmark group](media/desktop-bookmarks/bookmarks_15.png)

**Power BI Desktop** automatically names the group *Group 1*. Fortunately, you can just double-click on the name and rename it to whatever you want.

![Rename a bookmark group](media/desktop-bookmarks/bookmarks_16.png)

With any bookmark group, clicking on the bookmark group's name only expands or collapses the group of bookmarks, and does not represent a bookmark by itself. 

When using the **View** feature of bookmarks, the following applies:

* If the selected bookmark is in a group when you select **View** from bookmarks, only the bookmarks *in that group* are shown in the viewing session. 

* If the selected bookmark is not in a group, or is on the top level (such as the name of a bookmark group), then all bookmarks for the entire report are played, including bookmarks in any group. 

To ungroup bookmarks, just select any bookmark in a group, click the ellipses, and then select **Ungroup** from the menu that appears. 

![Ungroup a bookmark group](media/desktop-bookmarks/bookmarks_17.png)

Note that selecting **Ungroup** for any bookmark from a group takes all bookmarks out of the group (it deletes the group, but not the bookmarks themselves). So to remove a single bookmark from a group, you need to **Ungroup** any member from that group, which deletes the grouping, then select the members you want in the new group (using CTRL and clicking each bookmark), and select **Group** again. 
-->





## <a name="limitations-and-considerations"></a>Limitações e considerações
Nesta versão dos **indicadores**, há algumas limitações e considerações a serem lembradas.

* A maioria dos visuais personalizados deve funcionar bem com indicadores. Se você tiver problemas com o uso de indicadores e de um visual personalizado, entre em contato com o criador do visual personalizado e peça que adicione suporte a indicadores ao seu visual. 
* Se você adicionar um visual em uma página de relatório depois de criar um indicador, o visual será exibido em seu estado padrão. Isso também significa que, se você introduzir uma segmentação em uma página em que você tiver criado indicadores anteriormente, a segmentação se comportará em seu estado padrão.
* Em geral, os indicadores não serão afetados se o *designer* de relatórios atualizar ou publicar novamente o relatório. No entanto, se o designer fizer alterações importantes no relatório, como remover os campos usados por um indicador, você receberá uma mensagem de erro na próxima vez que tentar abrir esse indicador. 

<!--
## Next steps
spotlight?
-->
