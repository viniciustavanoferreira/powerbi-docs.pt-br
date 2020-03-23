---
title: Inserir relatórios com a guia Power BI para o Microsoft Teams
description: Com a guia Power BI para o Microsoft Teams, você pode facilmente inserir relatórios interativos em canais e chats.
author: LukaszPawlowski-MS
ms.author: lukaszp
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
LocalizationGroup: Share your work
ms.date: 03/12/2020
ms.openlocfilehash: fe8b5ed0e3cdf0003986ffe6eab18e97e83f3dec
ms.sourcegitcommit: 6bbc3d0073ca605c50911c162dc9f58926db7b66
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79381182"
---
# <a name="embed-report-with-the-power-bi-tab-for-microsoft-teams"></a>Inserir relatório com a guia Power BI para o Microsoft Teams

Com a guia Power BI atualizada para o Microsoft Teams, você pode facilmente inserir relatórios interativos em canais e chats do Microsoft Teams.

Use a guia Power BI para o Microsoft Teams para ajudar seus colegas a localizar os dados que sua equipe usa e discutir os dados nos canais da equipe.

## <a name="requirements"></a>Requisitos

Para a guia **Power BI para o Microsoft Teams** funcionar, é necessário o seguinte:

- Uma licença do Power BI Pro ou o relatório encontra-se em uma [capacidade do Power BI Premium (EM ou SKU P)](service-premium-what-is.md) com uma licença do Power BI.
- A guia Power BI para o Microsoft Teams.
- O usuário precisa entrar no serviço do Power BI para ativar sua licença do Power BI a fim de consumir o relatório.
- O usuário precisa ter permissão para exibir o relatório.

## <a name="embed-your-report"></a>Insira seu relatório
Para inserir o relatório em um canal ou chat do Microsoft Teams, adicione-o conforme descrito abaixo.

1. Abra o canal desejado ou participe de um chat no Microsoft Teams e selecione o ícone **+** .

    ![Adicione uma guia a um canal ou chat](media/service-embed-report-microsoft-teams/service-embed-report-microsoft-teams-add.png)

2. Selecione a guia Power BI.

    ![Lista de guias do Microsoft Teams mostrando o Power BI](media/service-embed-report-microsoft-teams/service-embed-report-microsoft-teams-tab.png)

3. Use as opções fornecidas para escolher um relatório de um aplicativo de Workspace, Compartilhado comigo ou Power BI

    ![Configurações da guia Power BI para o Microsoft Teams](media/service-embed-report-microsoft-teams/service-embed-report-microsoft-teams-tab-settings.png)

4. O nome da guia é atualizado automaticamente para corresponder ao nome do relatório, mas você pode alterá-lo. 

5. Pressione **Salvar**.

## <a name="supported-reports"></a>Relatórios com suporte

A guia habilita a inserção dos relatórios a seguir:

- Relatórios interativos e paginados
- Relatórios no Meu workspace, nova experiência de workspace e workspaces clássicos
- Relatórios em aplicativos do Power BI


## <a name="grant-access-to-reports"></a>Conceder acesso aos relatórios

A inserção de um relatório no Microsoft Teams não concede automaticamente aos usuários permissão para ver o relatório. É necessário [permitir que os usuários vejam o relatório no Power BI](service-share-dashboards.md). Você pode usar um grupo do Office 365 para sua equipe para facilitar. 

> [!IMPORTANT]
> Certifique-se de examinar quem pode ver o relatório dentro do serviço do Power BI e de conceder acesso aos que não aparecem na lista.

Uma maneira de garantir que todos em sua equipe tenham acesso aos relatórios inseridos é colocá-los em um único workspace no Power BI e fornecer acesso ao workspace para o grupo do Office 365 da sua equipe.

## <a name="start-a-conversation"></a>Iniciar uma conversa

Quando você adiciona uma guia de relatório do Power BI ao Teams, o Teams automaticamente cria uma conversa de guia para acompanhar o relatório. 

- Selecione **Mostrar conversa de guia** no canto superior direito.

    ![Ícone de Mostrar conversa de guia](media/service-embed-report-microsoft-teams/power-bi-teams-conversation-icon.png)

    O primeiro comentário é um link para o relatório. Todos no canal do Teams podem ver e discutir o relatório na conversa.

    ![Conversa de guia](media/service-embed-report-microsoft-teams/power-bi-teams-conversation-tab.png)

## <a name="known-issues-and-limitations"></a>Limitações e problemas conhecidos

- O Power BI não dá suporte aos mesmos idiomas localizados que o Microsoft Teams. Como resultado, você não verá a localização correta no relatório inserido.
- Os dashboards do Power BI não podem ser inseridos na guia Power BI para o Microsoft Teams.
- Um usuário sem uma licença do Power BI ou permissão para o relatório verá uma mensagem "O conteúdo não está disponível".
- Você pode encontrar problemas se usar o Internet Explorer 10. <!--You can look at the [browsers support for Power BI](consumer/end-user-browsers.md) and for [Office 365](https://products.office.com/office-system-requirements#Browsers-section). -->
- Os [filtros de URL](service-url-filters.md) não têm suporte com a guia Power BI do Microsoft Teams.
- Em nuvens nacionais, a nova guia Power BI não está disponível. Pode estar disponível uma versão mais antiga que não dá suporte a novos workspaces, experiência no workspace ou relatórios em aplicativos do Power BI. 
- Depois que a guia é salva, o nome dela não pode ser alterado por meio das configurações da guia. Use a opção de renomear para alterá-lo.

## <a name="next-steps"></a>Próximas etapas
- [Compartilhar um painel com seus colegas e com outras pessoas](service-share-dashboards.md)  
- [Criar e distribuir um aplicativo no Power BI](service-create-distribute-apps.md)  
- [O que é o Power BI Premium?](service-premium-what-is.md)

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
