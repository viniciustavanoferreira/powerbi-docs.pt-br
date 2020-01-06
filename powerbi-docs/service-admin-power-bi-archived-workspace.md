---
title: Workspace Arquivado do Power BI
description: Workspace Arquivado do Power BI depois de gerenciar locatários do Office 365
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 09/18/2019
ms.author: kfollis
LocalizationGroup: Administration
ms.openlocfilehash: 403bf213cc2da7ad803780946e606433166e3484
ms.sourcegitcommit: 6272c4a0f267708ca7d38a45774f3bedd680f2d6
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/06/2020
ms.locfileid: "74699948"
---
# <a name="power-bi-archived-workspace"></a>Workspace Arquivado do Power BI

> [!IMPORTANT]
> O Power BI não tem mais suporte para o recurso Workspace Arquivado, que será removido no final de 2019. Se estiver usando o Workspace Arquivado, recrie imediatamente o conteúdo que deseja manter, em um novo espaço de trabalho no locatário atual. Não conte com o acesso contínuo ao Workspace Arquivado. O Power BI não tem mais suporte para a capacidade relacionada, [tomada de controle externa de um locatário do Microsoft Azure AD](service-admin-faq.md#what-is-the-process-to-manage-a-tenant-created-by-microsoft-for-my-users).

Com o Power BI, qualquer pessoa pode inscrever-se e começar a usar o serviço em alguns minutos.  Posteriormente, o departamento de TI da sua organização pode optar por assumir o gerenciamento do Power BI para usuários em sua organização.  Se esse controle ocorrer, você se beneficia do gerenciamento central de usuários e permissões em sua organização. Você também poderá aproveitar a entrada simplificada usando o mesmo nome de usuário e senha utilizados para outros serviços em sua organização.

Qualquer conteúdo que tenha sido criado antes do início do gerenciamento do Power BI por seu departamento de TI será colocado em um Workspace Arquivado do Power BI, que pode ser acessado no painel de navegação do [Power BI](https://app.powerbi.com). Você deve começar a criação de conteúdo novo Power BI em Meu Workspace, que é protegido e gerenciado pelo departamento de TI da sua organização.  O workspace arquivado continuará a existir, mas há restrições sobre as ações que podem ser executadas no conteúdo do Workspace Arquivado.  Para remover essas restrições, você precisará migrar o conteúdo do seu Workspace Arquivado para o Meu Workspace, gerenciado pelo departamento de TI.

## <a name="restrictions-in-your-archived-workspace"></a>Restrições em seu Workspace Arquivado

O Power BI não exclui o conteúdo do Workspace arquivado. Você pode continuar a obter dados, criar relatórios e painéis e atualizar conjuntos de dados. Usuários existentes com os quais você compartilhou conteúdo ainda poderão exibir o conteúdo em seu Workspace Arquivado. No entanto, há algumas restrições sobre o conteúdo em seu Workspace Arquivado:

* **OneDrive for Business**: para conjunto de dados em seu Workspace Arquivado, você não poderá obter dados ou atualizá-los pelo OneDrive for Business.  Se você tentar se conectar a essa fonte, você receberá um aviso.

* **Compartilhando dashboards**: Não é possível compartilhar painéis com outros usuários por meio do Workspace Arquivado.  Todos os usuários que já têm acesso continuarão a exibir painéis compartilhados, acessando seu Workspace Arquivado.

* **Criando grupos**: Não é possível criar grupos no Workspace Arquivado.

* **Acesso em aplicativos móveis do Power BI**: embora você ainda possa exibir o conteúdo na Web no Workspace Arquivado, esse conteúdo não aparece mais nos aplicativos móveis do Power BI.

## <a name="migrating-content-in-your-archived-workspace"></a>Migração de conteúdo no Workspace Arquivado

Para continuar usando o Power BI, você deverá criar novo conteúdo em Meu Workspace. Você também deve planejar migrar qualquer conteúdo em seu Workspace Arquivado para o Meu Workspace.  Como migrar o conteúdo depende do tipo de conteúdo:

* **Conjuntos de dados do Excel ou do Power BI Desktop**: migre esses conjuntos de dados alternando do Workspace Arquivado para Meu Workspace e carregue novamente o arquivo do Excel ou do Power BI Desktop selecionando o botão **Meus Dados**.  Se você configurar a atualização agendada, você precisará reconfigurar as configurações para o novo conjunto de dados no Meu Workspace.

* **Outros conjuntos de dados**: alterne para Meu Workspace e clique no botão **Obter Dados** para se reconectar a todos os outros conjuntos de dados criados no Workspace Arquivado.  Talvez seja necessário inserir novamente as informações de conexão ou segurança.

* **Relatórios**: os relatórios contidos nos arquivos do Excel ou Power BI Desktop serão recriados automaticamente depois que você carregar novamente o arquivo do Excel ou Power BI Desktop correspondente. Os relatórios instalados como parte de um pacote de conteúdo também serão recriados quando você se reconectar ao pacote de conteúdo. Se você criar seus próprios relatórios por meio do serviço Power BI, recrie esses relatórios no Meu Workspace.

* **Dashboards**: dashboards instalados como parte dos pacotes de conteúdo são recriados automaticamente quando você se reconectar ao pacote de conteúdo no Meu Workspace. Se você criar seus próprios painéis por meio do serviço Power BI, recrie esses painéis no Meu Workspace.

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)

