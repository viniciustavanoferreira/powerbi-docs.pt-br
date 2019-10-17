---
title: Definir informações de contato para relatórios e painéis
description: Saiba como definir informações de contato para relatórios e painéis.
author: LukaszPawlowski-MS
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 10/08/2010
ms.author: lukaszp
LocalizationGroup: Common tasks
ms.openlocfilehash: b64bc2566be8787ad4bb4916ed8b8c8731a87ed7
ms.sourcegitcommit: d02de4ca33d865aee3e3e764b98f221950cb0a10
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/10/2019
ms.locfileid: "72245482"
---
# <a name="set-contact-information-for-reports-and-dashboards-in-the-power-bi-service"></a>Definir informações de contato para relatórios e painéis no serviço do Power BI
Este artigo ensina como definir informações de contato para um painel ou relatório no serviço do Power BI.

> [!NOTE]
> É possível definir informações de contato para itens em um workspace clássico ou novo. Não é possível definir informações de contato para itens no Meu Workspace. O cartão de informações é mostrado quando um relatório ou painel é exibido na [nova aparência](service-new-look.md).

Você pode adicionar vários usuários ou grupos ao contato de um item. Eles podem ser:
* Uma pessoa
* Um grupo do Office 365
* Um grupo de segurança habilitado para email
* Uma lista de distribuição

Por padrão, a pessoa que cria um novo relatório ou painel é definida como o contato. Se você definir um valor, ele substituirá o padrão. É claro que você pode remover todas as pessoas ou grupos da lista de contatos. Quando você fizer isso para workspaces clássicos, será mostrado o Grupo do Office 365 do workspace. Para novos workspaces de experiências, será usada a [lista de contatos do workspace](service-create-the-new-workspaces.md#workspace-contact-list). Se a lista de contatos do workspace não estiver definida, os administradores de workspace serão mostrados.

As informações de contato são mostradas para as pessoas que visualizam o item. 

 ![contato do relatório de serviço](media/service-item-contact/service-report-contact.png)

Quando você clica na lista de contatos, um email é criado para que você possa fazer perguntas ou obter ajuda. 

 ![email de contato do serviço](media/service-item-contact/service-contact-email.png)
 
As informações da lista de contatos também são usadas em outros locais. Por exemplo, são mostradas em alguns cenários de erro na caixa de diálogo de erro. Mensagens de email automatizadas relacionadas ao item, como solicitações de acesso, são enviadas para a lista de contatos. 

> [!NOTE]
> Ao publicar um aplicativo, as informações de contato de itens individuais são definidas para a pessoa que publicou ou atualizou o aplicativo. Você pode definir a URL de suporte do aplicativo para que os usuários do aplicativo obtenham a ajuda de que precisam.

## <a name="set-contact-information-for-a-report"></a>Definir informações de contato para um relatório
1. Em seu workspace, selecione a guia **Relatórios**.
2. Localize o relatório desejado e selecione o ícone **Configurações**.
3. Localize o campo de entrada **Contato** e defina um valor.

     ![configuração de contato do relatório de serviço](media/service-item-contact/service-report-contact-setting.png)

## <a name="set-contact-information-for-a-dashboard"></a>Definir informações de contato para um painel
1. Em seu workspace, selecione a guia **Dashboards**.
2. Localize o painel desejado e selecione o ícone **Configurações**
3. Localize o campo de entrada **Contato** e defina um valor.

     ![configuração de contato do painel de serviço](media/service-item-contact/service-dashboard-contact-setting.png)

## <a name="limitations-and-considerations"></a>Limitações e considerações
* O contato é definido automaticamente para novos itens criados no serviço do Power BI. Os itens existentes mostrarão o padrão do workspace.
* Você pode definir qualquer usuário ou grupo na lista de contatos, mas eles não recebem automaticamente a permissão para o item. Use o compartilhamento ou dê ao usuário que precise dele acesso ao workspace por meio de uma função. 


## <a name="next-steps"></a>Próximas etapas

Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)
