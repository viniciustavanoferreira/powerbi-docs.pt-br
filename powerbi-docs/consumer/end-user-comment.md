---
title: Adicionar comentários a dashboards e relatórios
description: Este documento mostra como adicionar comentários a um dashboard, relatório ou visual e como usar comentários para conversar com colaboradores.
author: mihart
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 02/18/2020
ms.author: mihart
LocalizationGroup: Consumer
ms.openlocfilehash: 59ba4d0e62613ed25569efd0602815e3d98aec4d
ms.sourcegitcommit: f9909731ff5b6b69cdc58e9abf2025b7dee0e536
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77496501"
---
# <a name="add-comments-to-a-dashboard-or-report"></a>Adicionar comentários a um dashboard ou relatório

[!INCLUDE[consumer-appliesto-ynny](../includes/consumer-appliesto-ynny.md)]

[!INCLUDE [power-bi-service-new-look-include](../includes/power-bi-service-new-look-include.md)]

Adicione um comentário pessoal ou inicie uma conversa sobre um dashboard ou relatório com seus colegas. O recurso **comentário** é apenas uma das maneiras como um *consumidor* pode colaborar com outras pessoas. 

![vídeo de comentários](media/end-user-comment/comment.gif)

> [!NOTE]
> A colaboração com outras pessoas, incluindo a adição de comentários a relatórios compartilhados, exige uma licença Power BI Pro ou Premium. [Qual tipo de licença eu tenho?](end-user-license.md)

## <a name="how-to-use-the-comments-feature"></a>Como usar o recurso Comentários
É possível adicionar comentários a um dashboard inteiro, a visuais individuais em um dashboard, a uma página de relatório, a um relatório paginado e a visuais individuais em uma página de relatório. Adicione um comentário geral ou um comentário direcionado a colegas específicos.  

Quando você adiciona um comentário a um relatório, o Power BI captura o filtro atual e os valores de segmentação. Isso significa que, quando você seleciona ou responde a um comentário, a página de relatório ou o visual de relatório podem ser alterados para mostrar as seleções de filtro e segmentação que estavam ativas quando o comentário foi adicionado pela primeira vez.  

![vídeo de relatório com filtros](media/end-user-comment/power-bi-comment.gif)

Por que isso é importante? Digamos que um colega aplicou um filtro que revelou um insight interessante e quer compartilhá-lo com a equipe. Sem esse filtro selecionado, o comentário pode não fazer sentido.

Se estiver usando um relatório paginado, você só poderá deixar um comentário geral sobre o relatório.  O suporte para deixar comentários em visuais de relatórios paginados individuais não está disponível.

### <a name="add-a-general-comment-to-a-dashboard-or-report"></a>Adicionar um comentário geral a um dashboard ou relatório
Os processos para adicionar comentários a um painel ou relatório são semelhantes.  Neste exemplo, estamos usando um dashboard. 

1. Abra um dashboard ou relatório do Power BI e selecione o ícone **Comentários**. Isso abre a caixa de diálogo Comentários.

    ![ícone de comentários](media/end-user-comment/power-bi-comment-menu.png)

    Aqui podemos ver que o criador do dashboard já adicionou um comentário geral.  Qualquer pessoa com acesso a esse dashboard pode ver este comentário.

    ![ícone de comentários](media/end-user-comment/power-bi-first-comments.png)

2. Para responder, selecione **Responder**, digite sua resposta e selecione **Postar**.  

    ![Ícone de Resposta a Comentários](media/end-user-comment/power-bi-comment-reply.png)

    Por padrão, o Power BI direciona sua resposta ao colega que iniciou o thread de comentários, neste caso, Alberto R. 

    ![Comentário com resposta](media/end-user-comment/power-bi-respond.png)

 3. Se você quiser adicionar um comentário que não faça parte de um thread existente, digite-o no campo de texto superior.

    ![Ícone de Resposta a Comentários](media/end-user-comment/power-bi-new-comments.png)

    Os comentários a esse dashboard agora têm esta aparência.

    ![Conversas de comentários](media/end-user-comment/power-bi-conversation.png)

### <a name="add-a-comment-to-a-specific-dashboard-or-report-visual"></a>Adicionar um comentário a um visual de dashboard ou relatório específico
Além de adicionar comentários a um dashboard inteiro ou a uma página de relatório inteira, você pode adicionar comentários a blocos individuais do dashboard e visuais individuais de relatório. Os processos são semelhantes e, neste exemplo, estamos usando um relatório.

1. Passe o mouse sobre o visual e selecione **Mais opções** (...).    
2. No menu suspenso, selecione **Abrir os comentários**.

    ![“Adicionar um comentário” é a primeira opção](media/end-user-comment/power-bi-report-comment.png)  

3.  A caixa de diálogo **Comentários** será aberta e os outros visuais da página ficam acinzentados. Esse visual ainda não tem nenhum comentário. 

    ![Adicionar um comentário para si mesmo](media/end-user-comment/power-bi-comment-column.png)  

4. Digite seu comentário e selecione **Postar**.

    ![Adicionar um comentário para si mesmo](media/end-user-comment/power-bi-comment-logistics.png)  

    - Em uma página de relatório, selecionar um comentário feito em um visual realça esse visual (veja acima).

    - Em um painel, o ícone de gráfico ![comentário com ícone de gráfico](media/end-user-comment/power-bi-comment-chart-icon.png) informa que o comentário está vinculado a um visual específico. Os comentários que se aplicam a todo o dashboard não têm um ícone especial. A seleção do ícone de gráfico realça o visual relacionado no dashboard.
    

    ![visual relacionado realçado](media/end-user-comment/power-bi-highlight.png)

5. Selecione **Fechar** para voltar para o dashboard ou relatório.

### <a name="get-your-colleagues-attention-by-using-the--sign"></a>Consiga a atenção de seus colegas usando o sinal @
Se você estiver criando comentários de dashboard, relatório, bloco ou visual, chame a atenção de seus colegas usando o símbolo "\@".  Quando você digita o símbolo "\@", o Power BI abre uma lista suspensa na qual você pode procurar e selecionar pessoas de sua organização. Qualquer nome verificado precedido pelo símbolo "\@" aparece em fonte azul. 

Esta é uma conversa que estou tendo com o *designer* da visualização. Ele usa o símbolo @ para garantir que eu veja o comentário. Eu sei que esse comentário é para mim. Ao abrir o dashboard do aplicativo no Power BI, eu seleciono **Comentários** no cabeçalho. O painel **Comentários** exibe nossa conversa.

![Adicionar uma menção de comentário](media/end-user-comment/power-bi-comment-convo.png)  



## <a name="next-steps"></a>Próximas etapas
Voltar para as [visualizações para consumidores](end-user-visualizations.md)    
<!--[Select a visualization to open a report](end-user-open-report.md)-->
