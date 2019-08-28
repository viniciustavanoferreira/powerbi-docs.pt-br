---
title: Criar novos espaços de trabalho - Power BI
description: Saiba como criar novos espaços de trabalho, em coleções de dashboards, relatórios e relatórios paginados criados para fornecer métricas importantes para sua organização.
author: maggiesMSFT
manager: kfile
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/18/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: d0c0781ea5d3864f1cf3627cd42d53cca632102d
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "61141688"
---
# <a name="create-the-new-workspaces-in-power-bi"></a>Criar novos espaços de trabalho no Power BI

Power BI está introduzindo uma nova experiência de espaço de trabalho. Espaços de trabalho ainda são o lugar para colaborar com colegas para criar coleções de dashboards, relatórios e relatórios paginados. Em seguida, você pode agrupar dessa coleção em um *aplicativo* e distribuí-lo para toda a organização ou para pessoas ou grupos específicos. 

Aqui está o que é diferente. Novos espaços de trabalho, você pode:

- Atribuir funções de workspace a grupos de usuários: grupos de segurança, listas de distribuição, grupos do Office 365 e indivíduos.
- Criar um workspace no Power BI sem criar um grupo do Office 365.
- Usar funções de workspaces mais granulares para obter um gerenciamento de permissões mais flexível em um workspace.

> [!NOTE]
> Para impor a segurança em nível de linha (RLS) para procurar conteúdo em um espaço de trabalho de usuários do Power BI Pro, continue a usar [espaços de trabalho clássicos](service-create-workspaces.md). Selecione o **os membros só podem exibir o conteúdo do Power BI** opção. Como alternativa, publicar um aplicativo do Power BI aos usuários, ou usar o compartilhamento para distribuir o conteúdo. A função de visualizador disponível em breve permitirá esse cenário no futuro em novos espaços de trabalho de experiência de espaço de trabalho.

Para obter mais informações, consulte o [novos espaços de trabalho](service-new-workspaces.md) artigo.

## <a name="create-one-of-the-new-app-workspaces"></a>Criar um dos novos workspaces de aplicativo

1. Comece criando o workspace de aplicativo. Selecione **Workspaces** > **Criar workspace do aplicativo**.
   
     ![Criar workspace do aplicativo](media/service-create-the-new-workspaces/power-bi-create-app-workspace.png)

2. Estiver criando automaticamente um espaço de trabalho atualizado, a menos que você aceitar **reverter para o clássico**.
   
     ![Nova experiência de espaço de trabalho](media/service-create-the-new-workspaces/power-bi-new-workspace.png)
     
     Se você selecionar **reverter para o clássico**, você cria um espaço de trabalho com base em um grupo do Office 365. Use esta opção se você precisar de **os membros só podem exibir o conteúdo do Power BI** opção para impor a segurança de nível de linha (RLS) para os membros do espaço de trabalho.

2. Nomeie o workspace. Se o nome não estiver disponível, edite-a para criar um nome exclusivo.
   
     O aplicativo para o espaço de trabalho terá o mesmo nome e ícone do espaço de trabalho.
   
1. Aqui estão alguns itens opcionais que você pode definir para seu espaço de trabalho:

    Carregar uma **imagem de espaço de trabalho**. Arquivos podem ser o formato. png ou. jpg. Tamanho do arquivo deve ter menos de 45 KB.
    
    [Adicionar um **lista de contatos**](#workspace-contact-list). Por padrão, os administradores do espaço de trabalho são os contatos. 
    
    [Especifique um **espaço de trabalho do OneDrive** ](#workspace-onedrive) digitando-se apenas o nome de um existente grupo do Office 365, não a URL. Agora esse espaço de trabalho pode usar o local de armazenamento de arquivos desse grupo do Office 365. 

    ![Especifique um local do OneDrive](media/service-create-the-new-workspaces/power-bi-new-workspace-onedrive.png)

    Para atribuir o espaço de trabalho para um **capacidade dedicada**, no **Premium** guia select **capacidade dedicada**.
     
    ![Capacidade dedicada](media/service-create-the-new-workspaces/power-bi-workspace-premium.png)

1. Selecione **Salvar**.

    O Power BI cria o workspace e o abre. Ele é exibido na lista de workspaces dos quais você é membro. 

## <a name="workspace-contact-list"></a>Lista de contatos do workspace

A nova lista de contatos do espaço de trabalho permite que você especifique quais usuários recebem a notificação sobre problemas que ocorrem no espaço de trabalho. Por padrão, qualquer usuário ou grupo especificado como um administrador do workspace é notificado, mas você pode personalizar a lista. Os usuários ou grupos listados na lista de contatos serão mostrados na interface do usuário (IU) para ajudar os usuários a obter ajuda relacionada ao workspace.

1. Acessar o novo **lista de contatos** configuração em uma das duas maneiras:

    No **criar um espaço de trabalho** painel ao criar pela primeira vez.

    No painel de navegação à esquerda, selecione a seta ao lado **espaços de trabalho**, selecione as reticências (...) próximo ao nome do espaço de trabalho > **configurações de espaço de trabalho**. O **configurações** painel é aberto.

    ![Configurações do workspace](media/service-create-the-new-workspaces/power-bi-workspace-settings.png)

2. Sob **Advanced** > **lista de contatos**, aceite o padrão **admins. do espaço de trabalho**, ou adicionar sua própria lista de **usuários específicos ou grupos**. 
3. Selecione **Salvar**.

## <a name="workspace-onedrive"></a>Workspace OneDrive

O recurso do OneDrive do espaço de trabalho permite que você configure um grupo do Office 365 cujo armazenamento de arquivos de biblioteca de documentos do SharePoint está disponível para usuários do espaço de trabalho. Você pode criar o grupo de fora do Power BI pela primeira vez. 

O Power BI não sincroniza as permissões de usuários ou grupos que estão configurados para ter acesso ao workspace com a associação ao grupo do Office 365. A prática recomendada é dar ao grupo do Office 365 mesmo, cujo configurar nesse grupo de configuração do Office 365, o armazenamento de arquivos [acesso ao espaço de trabalho](#give-access-to-your-workspace). Em seguida, gerencie o acesso do espaço de trabalho por meio do gerenciamento de associação de grupo do Office 365. 

1. Acessar o novo **espaço de trabalho do OneDrive** configuração em uma das duas maneiras:

    No **criar um espaço de trabalho** painel ao criar pela primeira vez.

    No painel de navegação à esquerda, selecione a seta ao lado **espaços de trabalho**, selecione as reticências (...) próximo ao nome do espaço de trabalho > **configurações de espaço de trabalho**. O **configurações** painel é aberto.

    ![Configurações do workspace](media/service-create-the-new-workspaces/power-bi-workspace-settings.png)

2. Sob **Advanced** > **espaço de trabalho do OneDrive**, digite o nome do grupo do Office 365 que você criou anteriormente. Power BI seleciona automaticamente o OneDrive para o grupo.

    ![Especifique um local do OneDrive](media/service-create-the-new-workspaces/power-bi-new-workspace-onedrive.png)

3. Selecione **Salvar**.

### <a name="access-the-workspace-onedrive-location"></a>Acessar o espaço de trabalho local do OneDrive

Depois de configurar o local do OneDrive, você pode obtê-lo de alguns locais diferentes no espaço de trabalho:

- Selecione **espaços de trabalho** > *nome do espaço de trabalho* > no botão de reticências ( **...** ) menu > **arquivos**. 

    ![Local dos arquivos de espaço de trabalho](media/service-new-workspaces/power-bi-new-workspace-files.png)

- Selecione as reticências ( **...** ) menu no canto superior direito do espaço de trabalho > **arquivos**.

    ![Local dos arquivos de espaço de trabalho](media/service-new-workspaces/power-bi-new-workspace-files-2.png)
    
- No **obter dados** > **arquivos** experiência. O **OneDrive – Business** entrada é seu próprio OneDrive for Business. A segunda do OneDrive é aquele em que você adicionou.

    ![Local dos arquivos de espaço de trabalho - obter dados](media/service-new-workspaces/power-bi-new-workspace-get-data-onedrive.png)

## <a name="add-content-to-your-app-workspace"></a>Adicionar conteúdo ao seu workspace de aplicativo

Depois de criar um novo espaço de trabalho de experiência de espaço de trabalho, é hora de adicionar conteúdo a ela. Adição de conteúdo é semelhante em espaços de trabalho novo e clássicos. Use o botão Criar ou usar obter dados para adicionar conteúdo ao seu espaço de trabalho.

1. No **boas-vindas** tela para seu novo espaço de trabalho, você pode adicionar conteúdo. 

    ![Nova tela de boas-vindas do workspace](media/service-create-the-new-workspaces/power-bi-workspace-welcome-screen.png)

1. Por exemplo, selecione **Exemplos** > **Exemplo de rentabilidade do cliente**.

> [!NOTE]
> Novos espaços de trabalho, você não pode consumir pacotes de conteúdo organizacional ou pacotes de conteúdo de terceiros. Os aplicativos estão disponíveis para pacotes de todo o conteúdo de terceiros, você usou anteriormente. Use espaços de trabalho clássicos se você precisar continuar usando os pacotes de conteúdo. Pacotes de conteúdo são preteridos, portanto, é uma prática recomendada usar aplicativos em vez disso.

Quando você exibe conteúdo na lista de conteúdo de um workspace de aplicativo, o nome do workspace de aplicativo é listado como o proprietário.

### <a name="connecting-to-third-party-services-in-new-workspaces"></a>Conectar-se aos serviços de terceiros em novos espaços de trabalho

Na nova experiência de workspaces, estamos mudando o foco para *aplicativos*. Os aplicativos de serviços de terceiros facilitam para que os usuários obtenham dados dos serviços que usam, como o Microsoft Dynamics CRM, o Salesforce ou o Google Analytics.

A nova experiência de espaço de trabalho, é possível criar ou consumir pacotes de conteúdo organizacional. Em vez disso, é possível usar os aplicativos fornecidos para conectar-se aos serviços de terceiros ou pedir para suas equipes internas fornecerem aplicativos para quaisquer pacotes de conteúdo que você está usando no momento. 

## <a name="give-access-to-your-workspace"></a>Conceder acesso ao seu espaço de trabalho

1. Na lista de conteúdo do espaço de trabalho, porque você é um administrador você pode ver uma nova ação, **acesso**.

    ![Lista de conteúdo de espaços de trabalho](media/service-create-the-new-workspaces/power-bi-workspace-content-list.png)

1. Selecione **Acessar**.

1. Adicione grupos de segurança, listas de distribuição, grupos do Office 365 ou indivíduos nesses workspaces como membros, colaboradores ou administradores. Consulte [Funções nos novos workspaces](service-new-workspaces.md#roles-in-the-new-workspaces) para obter uma explicação das diferentes funções.

    ![Os workspaces adicionam membros, administradores, colaboradores](media/service-create-the-new-workspaces/power-bi-access-add-members.png)

9. Selecione **Adicionar** > **Fechar**.


## <a name="distribute-an-app"></a>Distribuir um aplicativo

Se você quiser distribuir o conteúdo oficial para um grande público dentro de sua organização, você pode publicar um aplicativo do seu espaço de trabalho.  Quando o conteúdo estiver pronto, escolha quais painéis e relatórios que você deseja publicar e, em seguida, publicá-lo como um *aplicativo*. Você pode criar um aplicativo de cada workspace.

Leia sobre [publicando um aplicativo a partir de novos espaços de trabalho](service-create-distribute-apps.md)

## <a name="next-steps"></a>Próximas etapas
* Leia sobre [organizar o trabalho na nova experiência de espaços de trabalho no Power BI](service-new-workspaces.md)
* [Criar espaços de trabalho clássicos](service-create-workspaces.md)
* [Publicar um aplicativo de novos espaços de trabalho no Power BI](service-create-distribute-apps.md)
* Dúvidas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)
