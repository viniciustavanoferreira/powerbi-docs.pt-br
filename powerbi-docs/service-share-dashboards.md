---
title: Compartilhe os painéis e os relatórios do Power BI com colegas e outras pessoas
description: Como compartilhar relatórios e dashboards do Power BI com colegas dentro e fora de sua organização e o que você precisa saber sobre compartilhamento.
author: maggiesMSFT
manager: kfile
ms.reviewer: lukaszp
featuredvideoid: 0tUwn8DHo3s
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/24/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: d82b03325991276924f25da5511baadfe53127e1
ms.sourcegitcommit: f05ba39a0e46cb9cb43454772fbc5397089d58b4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/26/2019
ms.locfileid: "68523001"
---
# <a name="share-power-bi-dashboards-and-reports-with-coworkers-and-others"></a>Compartilhe os painéis e os relatórios do Power BI com colegas e outras pessoas
O *compartilhamento* é uma boa maneira de conceder acesso a algumas pessoas aos dashboards e relatórios. O Power BI também oferece [várias outras maneiras para colaborar e distribuir painéis e relatórios](service-how-to-collaborate-distribute-dashboards-reports.md).

![Ícone de compartilhamento em uma lista de painéis favoritos](media/service-share-dashboards/power-bi-share-dash-report-favorites.png)

Com o compartilhamento, se você compartilhar o conteúdo dentro ou fora de sua organização, você precisará de uma [licença do Power BI Pro](service-features-license-type.md). Os destinatários também precisarão de licenças do Power BI Pro, a menos que o conteúdo esteja em uma [capacidade Premium](service-premium-what-is.md). 

É possível compartilhar dashboards e relatórios da maioria dos locais no serviço do Power BI: Favoritos, Recentes, Compartilhado comigo (se o proprietário permitir), Meu Workspace ou outros workspaces. Quando você compartilha um painel ou relatório, as pessoas com as quais você o compartilha poderão exibi-lo e interagir com ele, mas não poderão editá-lo. Elas veem os mesmos dados que você no painel ou relatório, a menos que a [RLS (segurança em nível de linha)](service-admin-rls.md) seja aplicada. Os colegas com quem você compartilha também podem compartilhá-lo com os colegas deles, se você permitir. As pessoas de fora da organização também podem exibir e interagir com o dashboard ou o relatório, mas não podem compartilhá-los. 

Você também pode [compartilhar um dashboard de qualquer um dos aplicativos móveis do Power BI](consumer/mobile/mobile-share-dashboard-from-the-mobile-apps.md). No entanto, não é possível compartilhar dashboards do Power BI Desktop.

## <a name="video-share-a-dashboard"></a>Vídeo: Compartilhar um painel
Veja Amanda compartilhar seu dashboard com os colegas dentro e fora da empresa dela. Em seguida, siga as instruções passo a passo abaixo do vídeo para testá-la por conta própria.

<iframe width="560" height="315" src="https://www.youtube.com/embed/0tUwn8DHo3s?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP" frameborder="0" allowfullscreen></iframe>

## <a name="share-a-dashboard-or-report"></a>Compartilhar um painel ou relatório

1. Em uma lista de painéis ou relatórios ou em um painel ou relatório, selecione **Compartilhar** ![Ícone de compartilhamento](media/service-share-dashboards/power-bi-share-icon.png).

2. Na caixa superior, insira os endereços de email completos dos indivíduos, grupos de distribuição ou grupos de segurança. Você não pode compartilhar com listas de distribuição dinâmicas. 
   
   Você pode compartilhar com as pessoas cujos endereços estejam fora da organização, mas verá um aviso.
   
   ![Aviso sobre o compartilhamento externo](media/service-share-dashboards/power-bi-share-dialog-warning.png) 
 
   >[!NOTE]
   >A caixa de entrada é compatível com, no máximo, 100 usuários ou grupos. Se for necessário compartilhar com um grande número de usuários, considere criar o dashboard em um workspace e [distribuí-lo como um aplicativo](service-create-distribute-apps.md).
   > 
   > 


3. Adicione uma mensagem, se desejar. É opcional.
4. Para permitir que seus colegas de trabalho compartilhem o conteúdo com outras pessoas, marque a opção **Permitir que os destinatários compartilhem seu dashboard (ou relatório)** .
   
   A permissão de compartilhamento por outras pessoas é chamada *novo compartilhamento*. Se você permitir, elas poderão compartilhar novamente por meio do serviço e dos aplicativos móveis do Power BI ou encaminhar o convite por email para outras pessoas em sua organização. O convite expira após um mês. As pessoas de fora da sua organização não podem compartilhar novamente. Como o proprietário do conteúdo, você pode desativar o novo compartilhamento e pode também revogá-lo individualmente. Confira [Impedir o compartilhamento ou impedir que outras pessoas compartilhem](#stop-sharing-or-stop-others-from-sharing).

5. Selecione **Compartilhar.**
   
   ![Selecionar o botão Compartilhar](media/service-share-dashboards/power-bi-share-dialog-share.png)  
   
   O Power BI envia um convite por email para os indivíduos, mas não para grupos, com um link para o conteúdo compartilhado. Você verá uma notificação de **Êxito**. 
   
   Quando os destinatários de sua organização clicarem no link, o Power BI adicionará o painel ou relatório às suas páginas de lista **Compartilhado comigo**. Eles podem selecionar seu nome para ver todo o conteúdo que você compartilhou com eles. 
   
   ![Página de lista Compartilhado comigo](media/service-share-dashboards/power-bi-shared-with-me-dashboards-reports.png)
   
   Quando os destinatários fora de sua organização clicarem no link, eles verão o painel ou relatório, mas não no portal normal do Power BI. Para saber mais, confira [Compartilhar um dashboard ou relatório com pessoas fora de sua organização](#share-a-dashboard-or-report-with-people-outside-your-organization).

## <a name="who-has-access-to-a-dashboard-or-report-you-shared"></a>Quem tem acesso a um painel ou relatório que você compartilhou?
Às vezes, você precisa ver as pessoas com quem você compartilhou e ver com quem elas o compartilharam:

1. Na lista de painéis e relatórios ou no próprio painel ou relatório, selecione **Compartilhar** ![Ícone de compartilhamento](media/service-share-dashboards/power-bi-share-icon.png). 
2. Na caixa de diálogo **Compartilhar dashboard** ou **Compartilhar relatório**, clique em **Acessar**.
   
    ![Caixa de diálogo Compartilhar dashboard, guia Acessar](media/service-share-dashboards/power-bi-share-dialog-access.png)

    As pessoas externas à sua organização são listadas como **Convidado**.

## <a name="stop-sharing-or-stop-others-from-sharing"></a>Impedir o compartilhamento ou impedir que outras pessoas compartilhem
Somente o proprietário do painel ou relatório pode ativar e desativar o novo compartilhamento.

### <a name="if-you-havent-sent-the-sharing-invitation-yet"></a>Se você ainda não enviou o convite de compartilhamento
* Desmarque a caixa de seleção **Permitir que os destinatários compartilhem seu dashboard (ou relatório)** na parte inferior do convite antes de enviá-lo.

### <a name="if-youve-already-shared-the-dashboard-or-report"></a>Se você já compartilhou o painel ou relatório
1. Na lista de painéis e relatórios ou no próprio painel ou relatório, selecione **Compartilhar** ![Ícone de compartilhamento](media/service-share-dashboards/power-bi-share-icon.png). 
2. Na caixa de diálogo **Compartilhar dashboard** ou **Compartilhar relatório**, clique em **Acessar**.
   
    ![Caixa de diálogo Compartilhar dashboard, guia Acessar](media/service-share-dashboards/power-bi-share-dialog-access.png)
3. Selecione as reticências ( **...** ) ao lado de **Ler e compartilhar novamente** e selecione:
   
   ![Reticências de Ler e compartilhar novamente](media/service-share-dashboards/power-bi-change-access.png)
   
   * **Ler** para impedir que a pessoa compartilhe-o com outras pessoas.
   * **Remover o acesso** para impedir que a pessoa veja o conteúdo compartilhado.

4. Na caixa de diálogo **Remover acesso**, decida se quer remover o acesso ao conteúdo relacionado, como relatórios e conjuntos de dados. Se você remover os itens com um ![ícone de aviso do Power BI](media/service-share-dashboards/power-bi-warning-icon.png), também será melhor remover o conteúdo relacionado, porque ele não será exibido corretamente.

    ![Caixa de diálogo de aviso de compartilhamento do Power BI](media/service-share-dashboards/power-bi-sharing-warning-dialog.png)

## <a name="share-a-dashboard-or-report-with-people-outside-your-organization"></a>Compartilhar um painel ou relatório com pessoas fora de sua organização
Quando você compartilha com pessoas fora da organização, elas recebem um email com um link para o dashboard ou relatório compartilhado e precisam entrar no Power BI para vê-lo. Se não tiverem uma licença do Power BI Pro, elas poderão inscrever-se para receber uma depois de clicar no link.

Depois de entrar, elas poderão ver o dashboard ou relatório compartilhado em sua própria janela do navegador, e não no portal do Power BI normal. Para acessar o dashboard ou relatório posteriormente, eles precisam indicar o link.

Elas não podem editar nenhum conteúdo nesse painel ou relatório. Embora eles possam interagir com os gráficos e alterar filtros ou segmentações, não podem salvar suas alterações. 

Somente os destinatários diretos podem ver o painel ou relatório compartilhado. Por exemplo, se você enviou o email para Vicki@contoso.com, somente Valentina poderá ver o dashboard. Ninguém mais pode ver o dashboard, mesmo que tenha o link. Vicki precisa usar o mesmo endereço de email para acessar. Se alguém entrar com qualquer outro endereço de email, não poderá acessar o dashboard.

Pessoas fora de sua organização não poderão ver os dados se a segurança em nível de linha ou de função for implementada nos modelos tabulares locais do Analysis Services.

Se você enviar um link em um aplicativo móvel do Power BI para pessoas fora da organização, quando elas clicarem no link, o dashboard será aberto em um navegador, e não no aplicativo móvel do Power BI.

Se você [Permitir que os usuários externos convidados editem e gerenciem o conteúdo da organização](service-admin-portal.md#export-and-sharing-settings), a experiência de apenas consumo padrão não se aplicará a eles. [Saiba mais](service-admin-azure-ad-b2b.md).

## <a name="limitations-and-considerations"></a>Limitações e considerações
Coisas para se lembrar a respeito do compartilhamento de painéis e relatórios:

* Em geral, você e seus colegas veem os mesmos dados no painel ou relatório. Portanto, se você tiver permissões para ver mais dados do que eles, eles poderão ver todos os seus dados no painel ou relatório. No entanto, se a [RLS (segurança em nível de linha)](service-admin-rls.md) for aplicada ao conjunto de dados subjacente a um painel ou relatório, as credenciais de cada pessoa serão usadas para determinar quais dados elas podem acessar.
* Todas as pessoas com quem você compartilha o dashboard podem vê-lo e interagir com os relatórios relacionados no [Modo de Exibição de Leitura](consumer/end-user-reading-view.md#reading-view). Elas não podem criar relatórios nem salvar alterações nos relatórios existentes.
* Ninguém pode ver nem baixar o conjunto de dados, mas é possível acessá-lo diretamente usando o recurso Analisar no Excel. Um administrador pode restringir a capacidade de usar o Analisar no Excel de todos em um grupo. No entanto, a restrição é para todos nesse grupo, para cada espaço de trabalho ao qual ele pertence.
* Qualquer pessoa pode [atualizar os dados](refresh-data.md) manualmente.
* Se você usar o Office 365 para email, poderá compartilhar com os membros de um grupo de distribuição inserindo o endereço de email associado ao grupo de distribuição.
* Os colegas de trabalho que têm o mesmo domínio de email que você e os colegas cujos domínios são diferentes, mas estão registrados no mesmo locatário, podem compartilhar o dashboard com outras pessoas. Por exemplo, se os domínios contoso.com e contoso2.com estiverem registrados no mesmo locatário e o endereço de email for konrads@contoso.com, tanto ravali@contoso.com quanto gustav@contoso2.com poderão ser compartilhados, desde que você tenha concedido permissão para compartilhar.
* Se seus colegas de trabalho já tiverem acesso a um dashboard ou relatório específico, você poderá enviar um link direto copiando a URL quando estiver no dashboard ou relatório. Por exemplo: `https://powerbi.com/dashboards/g12466b5-a452-4e55-8634-xxxxxxxxxxxx`
* Da mesma forma, se seus colegas de trabalho já tiverem acesso a um dashboard específico, você poderá [enviar um link direto para o relatório subjacente](service-share-reports.md). 
* Você pode compartilhar com, no máximo, 100 usuários ou grupos em uma única ação de compartilhamento. No entanto, pode-se conceder acesso a mais de 500 usuários a um item. Para isso, compartilhe várias vezes especificando os usuários individualmente ou compartilhe com um grupo de usuários que contém todos os usuários.

## <a name="troubleshoot-sharing"></a>Solucionar problemas de compartilhamento

### <a name="my-dashboard-recipients-see-a-lock-icon-in-a-tile-or-a-permission-required-message"></a>Destinatários do meu painel verão um ícone de bloqueio em um bloco ou uma mensagem "A permissão necessária"

As pessoas com as quais você compartilha poderão ver um bloco bloqueado em um painel ou uma mensagem "Permissão necessária" ao tentarem exibir um relatório.

![Bloco do Power BI bloqueado](media/service-share-dashboards/power-bi-locked_tile_small.png)

Nesse caso, você precisa conceder a permissão para o conjunto de dados subjacente:

1. Vá para a guia **Conjuntos de dados** na sua lista de conteúdo.

1. Selecione as reticências ( **...** ) ao lado do conjunto de dados e, em seguida, selecione **Gerenciar permissões**.

    ![Gerenciar permissões](media/service-share-dashboards/power-bi-sharing-manage-permissions.png)

1. Selecione **Adicionar usuário**.

    ![Selecionar Adicionar usuário](media/service-share-dashboards/power-bi-share-dataset-add-user.png)

1. Insira os endereços de email completos dos indivíduos, grupos de distribuição ou grupos de segurança. Você não pode compartilhar com listas de distribuição dinâmicas.

    ![Adicionar endereços de email](media/service-share-dashboards/power-bi-add-user-dataset.png)


1. Selecione **Adicionar**.

### <a name="i-cant-share-a-dashboard-or-report"></a>Não consigo compartilhar um painel ou relatório como favorito

Para compartilhar um dashboard ou relatório, você precisa de permissão para compartilhar novamente o conteúdo subjacente, ou seja, todos os relatórios e conjuntos de dados relacionados. Se você vir uma mensagem informando que não é possível compartilhar, peça ao autor do relatório para dar a você permissão para compartilhar novamente os relatórios e conjuntos de dados.

![Mensagem "Não é possível compartilhar"](media/service-share-dashboards/power-bi-sharing-unable-to-share.png)


## <a name="next-steps"></a>Próximas etapas
* Tem comentários? Vá para o [site da comunidade do Power BI](https://community.powerbi.com/) para fazer sugestões.
* [Como devo colaborar e compartilhar relatórios e dashboards?](service-how-to-collaborate-distribute-dashboards-reports.md)
* [Compartilhar um relatório do Power BI filtrado](service-share-reports.md).
* Dúvidas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/).

