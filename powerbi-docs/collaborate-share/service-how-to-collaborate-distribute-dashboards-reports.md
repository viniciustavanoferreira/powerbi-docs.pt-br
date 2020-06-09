---
title: Maneiras de compartilhar seu trabalho no Power BI
description: No Power BI, você pode trabalhar em colaboração e compartilhar painéis, relatórios, blocos e aplicativos de diferentes maneiras. Cada maneira tem suas vantagens.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 03/12/2020
LocalizationGroup: Share your work
ms.openlocfilehash: 68ead14063c290c8ec9db5cb24814b93e493ea6b
ms.sourcegitcommit: 49daa8964c6e30347e29e7bfc015762e2cf494b3
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84272944"
---
# <a name="ways-to-share-your-work-in-power-bi"></a>Maneiras de compartilhar seu trabalho no Power BI

Você criou painéis e relatórios. Talvez você também tenha colaborado neles com seus colegas de trabalho. Agora você deseja que outras pessoas tenham acesso a eles. Qual é a melhor maneira de distribuí-los? Nesse artigo, comparamos essas opções para colaborar e compartilhar no Power BI:

* Colabore com colegas de trabalho para criar relatórios e dashboards significativos em *workspaces*.
* Agrupe esses dashboards e relatórios em *aplicativos* e distribua-os para um grupo maior ou para toda a organização.
* Crie *conjuntos de dados compartilhados* que seus colegas de trabalho possam usar como base para seus próprios relatórios, em seus próprios workspaces.
* Compartilhe dashboards ou relatórios com algumas pessoas, por meio do serviço ou de aplicativos móveis do Power BI.
* Anotar e compartilhar dos aplicativos móveis do Power BI.
* Inserir um relatório no Microsoft Teams.
* Imprima relatórios.
* *Insira* relatórios em portais seguros ou sites públicos.
* Criar um *aplicativo de modelo* que você possa distribuir a usuários externos do Power BI por meio do Microsoft AppSource.

Não importa qual opção você escolher, para compartilhar seu conteúdo você precisa de uma [licença do Power BI Pro](../fundamentals/service-features-license-type.md) ou então o conteúdo precisa estar em uma [capacidade Premium](../admin/service-premium-what-is.md). Os requisitos de licença variam para os colegas que exibem o conteúdo que você compartilha, dependendo da opção escolhida. As seções a seguir apresentam mais detalhes. 

![Aplicativos no serviço do Power BI](media/service-how-to-collaborate-distribute-dashboards-reports/power-bi-apps-new-look.png)

*Aplicativos de serviço do Power BI*

## <a name="collaborate-in-a-workspace"></a>Colaborar em um workspace

Quando as equipes trabalham juntas, elas precisam de acesso aos mesmos documentos para uma colaboração rápida. Nos workspaces do Power BI, as equipes se reúnem para compartilhar a propriedade e o gerenciamento de dashboards, relatórios, conjuntos de dados e pastas de trabalho. Às vezes, os usuários do Power BI organizam seus workspaces com base em estruturas organizacionais; outras vezes, eles os criam para projetos específicos. Ainda assim, outras organizações usam vários workspaces para armazenar versões diferentes de relatórios ou de dashboards que elas usam. 

Os workspaces fornecem funções que determinam quais permissões seus colegas de trabalho têm. Você pode usar essas funções para determinar quem pode gerenciar todo o workspace ou editar e distribuir seu conteúdo.

![Workspaces](media/service-how-to-collaborate-distribute-dashboards-reports/power-bi-workspace.png)

É comum você colocar conteúdo no Meu Workspace e compartilhá-lo. Mas os workspaces são melhores para colaboração do que o Meu Workspace, porque eles permitem a propriedade conjunta do conteúdo. Você e toda a sua equipe podem fazer atualizações facilmente ou conceder acesso aos outros. O Meu workspace é mais bem usado por indivíduos para conteúdo pessoal ou pontual.

Vamos imaginar que você tem um dashboard concluído que precisa compartilhar com seus colegas. Qual é a melhor maneira de conceder acesso ao dashboard a eles? A resposta depende de vários fatores. 

- Se os colegas precisarem manter o dashboard atualizado ou precisarem de acesso a todo o conteúdo do workspace, considere adicioná-los ao workspace. 
- Se os colegas precisam apenas ver esse dashboard e não todo o conteúdo do workspace, você tem alternativas. Se algumas pessoas precisam apenas de um dashboard específico, o compartilhamento do dashboard pode ser a melhor solução.
- Entretanto, se o dashboard fizer parte de um conjunto maior de conteúdo que você precisa distribuir para muitos colegas, então a publicação de um *aplicativo* provavelmente será a melhor opção.

O Power BI tem uma nova experiência de workspace. Leia [Criar os novos workspaces](service-create-the-new-workspaces.md) para ver como eles foram alterados. 

## <a name="distribute-insights-in-an-app"></a>Distribuir insights em um aplicativo

Digamos que você deseja distribuir o dashboard para um público-alvo amplo da sua organização. Você e seus colegas criaram um *workspace* e, em seguida, criaram e refinaram dashboards, relatórios e conjuntos de dados no workspace. Agora você seleciona os painéis e relatórios desejados e os publica como um aplicativo, em um grupo ou em toda a sua organização.

![Ícone Publicar aplicativo](media/service-how-to-collaborate-distribute-dashboards-reports/power-bi-publish-app.png)

Os aplicativos são fáceis de descobrir e instalar no serviço do Power BI ([https://app.powerbi.com](https://app.powerbi.com)). Você pode enviar aos usuários corporativos um link direto para o aplicativo ou eles podem pesquisar por ele no AppSource. Se o administrador do Power BI der permissão, você poderá instalar um aplicativo automaticamente em contas do Power BI de seus colegas de trabalho. Leia mais sobre [publicação de aplicativos](service-create-distribute-apps.md).

Após instalarem um aplicativo, eles poderão vê-lo em seu navegador ou dispositivo móvel.

Para que seus usuários exibam seu aplicativo, eles também precisam ter uma licença do Power BI Pro ou o aplicativo precisa ser armazenado em uma capacidade do Power BI Premium. Leia [O que é o Power BI Premium?](../admin/service-premium-what-is.md) para obter detalhes.

É possível publicar aplicativos para as pessoas que estão fora de sua organização também. Eles podem ver e interagir com o conteúdo do aplicativo, mas não podem compartilhá-lo com outras pessoas. Agora você pode criar *aplicativos de modelo* e implantá-los para qualquer cliente do Power BI.

## <a name="share-a-dataset"></a>Compartilhar um conjunto de dados

Sejamos francos, algumas pessoas têm maior habilidade na criação de modelos de dados bem projetado de alta qualidade em seus relatórios. Talvez você seja essa pessoa. Toda a organização pode se beneficiar do uso dos mesmos modelos de dados bem projetados. Os *conjuntos de dados compartilhados* preenchem essa função. Quando você cria um relatório com um modelo de dados que todos devem usar, você pode salvar o relatório no serviço do Power BI e dar às pessoas certas a permissão para usá-lo. Em seguida, eles podem criar relatórios com base no seu conjunto de dados. Dessa forma, todas as pessoas baseiam os relatórios nos mesmos dados, observando a mesma "versão da verdade".

![Encontrar um conjunto de dados compartilhado](media/service-how-to-collaborate-distribute-dashboards-reports/power-bi-shared-datasets.png)

Leia mais sobre [criação e uso de conjuntos de dados compartilhados](../connect-data/service-datasets-across-workspaces.md).

## <a name="share-dashboards-and-reports"></a>Compartilhar dashboards e relatórios

Digamos que você tenha finalizado um dashboard e um relatório em seu próprio Meu Workspace ou em um workspace e deseje que outras pessoas tenham acesso a ele. Uma maneira de fazer isso é *compartilhá-lo*. 

![Compartilhar um relatório](media/service-how-to-collaborate-distribute-dashboards-reports/power-bi-share-report.png)

É necessário ter uma licença do Power BI Pro para compartilhar o conteúdo e as pessoas com quem você o compartilha também precisam ou o conteúdo precisa estar em um espaço de trabalho em uma [capacidade Premium](../admin/service-premium-what-is.md). Quando você compartilha um dashboard ou relatório, os destinatários podem exibi-lo e interagir com ele, mas não podem editá-lo. Eles veem os mesmos dados que você no dashboard ou relatam e obtêm acesso a todos os dados no conjunto de dados subjacente, a menos que a [RLS (segurança em nível de linha)](../admin/service-admin-rls.md) seja aplicada. Os colegas com quem você o compartilha podem compartilhá-lo com os colegas deles, se você permitir. 

Você também pode compartilhar com pessoas de fora da sua organização. Elas também podem exibir o dashboard ou relatório ou interagir com ele também, mas não podem compartilhá-lo. 

Saiba mais sobre [como compartilhar painéis e relatórios](service-share-dashboards.md) no serviço Power BI. Você também pode adicionar um filtro em um link e [compartilhar uma exibição filtrada do relatório](service-share-reports.md).

## <a name="annotate-and-share-from-the-power-bi-mobile-apps"></a>Anotar e compartilhar dos aplicativos móveis do Power BI

Nos aplicativos móveis do Power BI para dispositivos iOS e Android, você pode fazer anotações em um bloco, relatório ou visual e, em seguida, compartilhar isso com qualquer pessoa por email.

![Anotar e compartilhar em aplicativos móveis](media/service-how-to-collaborate-distribute-dashboards-reports/power-bi-iphone-annotate.png)

Você está compartilhando um instantâneo do bloco, relatório ou visual e seus destinatários veem exatamente como ele era quando você enviou o email. O email também contém um link para o dashboard ou relatório. Se eles tiverem uma licença do Power BI Pro ou se o conteúdo estiver em uma [capacidade Premium](../admin/service-premium-what-is.md) e você já tiver compartilhado o objeto com eles, eles poderão abri-lo. Envie instantâneos de blocos para qualquer pessoa &#151; não apenas para seus colegas, no mesmo domínio de email.

Mais informações sobre [anotação e compartilhamento de blocos, relatórios e visuais](../consumer/mobile/mobile-annotate-and-share-a-tile-from-the-mobile-apps.md) nos aplicativos móveis do iOS e Android.

Também é possível [compartilhar um instantâneo de um bloco](../consumer/mobile/mobile-windows-10-phone-app-get-started.md) no aplicativo do Power BI para dispositivos Windows 10.

## <a name="embed-a-report-in-microsoft-teams"></a>Inserir um relatório no Microsoft Teams

Aumente a colaboração controlada por dados em sua organização inserindo seus relatórios do Power BI e relatórios paginados do Power BI no Microsoft Teams. Você pode adicionar guias separadas do Power BI para cada relatório individual e dar a cada guia o nome do relatório ou qualquer outro nome. Seus colegas podem ver seus relatórios nas guias do Power BI no Teams. Eles também podem abrir a janela Conversa e comentar sobre o relatório no Teams. Leia mais sobre como [inserir um relatório no Microsoft Teams](service-embed-report-microsoft-teams.md).

## <a name="print-or-save-as-pdf-or-other-static-file"></a>Imprimir ou salvar como PDF ou outro arquivo estático

Você pode imprimir ou salvar como PDF (ou outro formato de arquivo estático) um dashboard inteiro, um bloco do dashboard, uma página de relatório ou uma visualização do serviço do Power BI. Relatórios podem ser impressos somente com uma página por vez – não é possível imprimir o relatório inteiro ao mesmo tempo. Mais sobre como [imprimir ou salvar como um arquivo estático](../consumer/end-user-print.md).

## <a name="embed-reports-in-secure-portals-or-public-web-sites"></a>Inserir relatórios em portais seguros ou sites públicos

### <a name="embed-in-secure-portals"></a>Inserir em portais seguros

Você pode inserir relatórios do Power BI em portais ou sites em que os usuários esperam vê-los.  
As opções **Inserir no SharePoint Online** e **Inserção** no serviço do Power BI permitem que você insira relatórios para seus usuários internos com segurança. 

- A opção **Inserir no SharePoint Online** funciona com a web part do Power BI para o SharePoint Online. Ela fornece uma experiência de logon único com controle de como o relatório é inserido. 
- A opção **Inserção** funciona com qualquer portal ou site compatível com a inserção de conteúdo usando uma URL ou um iFrame. 

Qualquer que seja a opção escolhida, o Power BI aplicará todas as permissões e a segurança de dados antes que os usuários vejam o conteúdo. A pessoa que está exibindo o relatório precisa da licença apropriada. Mais informações sobre as opções [Inserção no SharePoint Online](service-embed-report-spo.md) e [Inserção](service-embed-secure.md) no Power BI.

### <a name="publish-to-public-web-sites"></a>Publicar em sites públicos

Com a opção **Publicar na Web**, você pode publicar relatórios do Power BI em toda a Internet inserindo elementos visualizações interativas em postagens em blogs, sites, mídia social e outras comunicações online, em qualquer dispositivo. Qualquer pessoa na Internet pode ver seus relatórios, e você não tem controle sobre quem pode ver o que você publicou. Eles não precisam de uma licença do Power BI. A publicação na Web só está disponível para relatórios que você pode editar. Você não pode publicar relatórios na Web se eles são compartilhados com você ou se estiverem em um aplicativo. Mais sobre a [publicação na Web](service-publish-to-web.md).

>[!Warning]
>Use [Publicar na Web](service-publish-to-web.md) apenas para compartilhar o conteúdo publicamente, não internamente.

## <a name="create-and-deploy-template-apps"></a>Criar e implantar aplicativos de modelo

Os *aplicativos de modelo* são projetados para serem distribuídos publicamente, geralmente no Microsoft AppSource. Você cria um aplicativo e com pouco ou quase nenhum código, você pode implantá-lo para qualquer cliente do Power BI. Os clientes se conectam em seus próprios dados e criam instâncias de suas próprias contas. Leia mais sobre [aplicativos de modelo do Power BI](../connect-data/service-template-apps-overview.md).


## <a name="next-steps"></a>Próximas etapas

* [Compartilhar dashboards com colegas e outras pessoas](service-share-dashboards.md)
* [Criar e publicar um aplicativo no Power BI](service-create-distribute-apps.md)
* [Inserir o relatório em um site ou portal seguro](service-embed-secure.md)

Tem comentários? Vá para o [site da comunidade do Power BI](https://community.powerbi.com/) para fazer sugestões.

Mais perguntas? [Experimente a Comunidade do Power BI](https://community.powerbi.com/)
