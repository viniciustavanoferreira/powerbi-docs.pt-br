---
title: RLS (segurança em nível de linha) com o Power BI
description: Como configurar a segurança em nível de linha para conjuntos de dados importados e DirectQuery para o serviço do Power BI.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.author: mblythe
ms.date: 09/09/2019
ms.custom: seodec18
LocalizationGroup: Administration
ms.openlocfilehash: 04a8c8a08d885427e9de43b719674fce4ac2ebbd
ms.sourcegitcommit: a97c0c34f888e44abf4c9aa657ec9463a32be06f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71074837"
---
# <a name="row-level-security-rls-with-power-bi"></a>RLS (segurança em nível de linha) com o Power BI

A RLS (segurança em nível de linha) com o Power BI pode ser usada para restringir o acesso a dados para determinados usuários. Os filtros restringem o acesso a dados no nível da linha e você pode definir filtros nas funções. Lembre-se de que, no serviço do Power BI, os membros de um workspace têm acesso a conjuntos de dados no workspace. A RLS não restringe esse acesso a dados.

É possível configurar a RLS de modelos de dados importados para o Power BI com o Power BI Desktop. Você também pode configurar RLS em conjuntos de dados que estão usando DirectQuery, como o SQL Server. Anteriormente, você conseguia apenas implementar a RLS nos modelos do Analysis Services local fora do Power BI. Para as conexões dinâmicas do Analysis Services, configure a Segurança em nível de linha no modelo local. A opção de segurança não será exibida para conjuntos de dados com conexão dinâmica.

[!INCLUDE [include-short-name](./includes/rls-desktop-define-roles.md)]

Por padrão, a filtragem de segurança em nível de linha usa filtros unidirecionais, independentemente se as relações forem definidas para unidirecional ou bidirecional. Habilite manualmente o filtro cruzado bidirecional com a segurança em nível de linha selecionando a relação e marcando a caixa de seleção **Aplicar filtro de segurança em ambas as direções**. Você deverá marcar essa caixa quando também tiver implementado a segurança dinâmica em nível de linha no nível do servidor, em que a segurança em nível de linha se baseia no nome de usuário ou na ID de logon.

Para obter mais informações, consulte [Filtragem cruzada bidirecional usando o DirectQuery no Power BI Desktop](desktop-bidirectional-filtering.md) e o artigo técnico [Protegendo o modelo semântico de BI de tabela](http://download.microsoft.com/download/D/2/0/D20E1C5F-72EA-4505-9F26-FEF9550EFD44/Securing%20the%20Tabular%20BI%20Semantic%20Model.docx).

![Aplicar filtro de segurança](media/service-admin-rls/rls-apply-security-filter.png)


[!INCLUDE [include-short-name](./includes/rls-desktop-view-as-roles.md)]

## <a name="manage-security-on-your-model"></a>Gerenciar a segurança no modelo

Para gerenciar a segurança no modelo de dados, é necessário fazer o seguinte.

1. Selecione as **reticências (...)** para um conjunto de dados.
2. Selecione **Segurança**.
   
   ![Aplicar filtro de segurança em ambos os sentidos](media/service-admin-rls/rls-security.png)

Você será levado à página da RLS para adicionar membros a uma função criada no Power BI Desktop. Somente os proprietários do conjunto de dados verão a opção Segurança disponível. Se o conjunto de dados está em um Grupo, somente os Administradores do grupo encontrarão a opção de segurança. 

Você só pode criar ou modificar funções no Power BI Desktop.

## <a name="working-with-members"></a>Trabalhando com membros

### <a name="add-members"></a>Adicionar membros

É possível adicionar um membro à função digitando o endereço de email, o nome do usuário, o grupo de segurança ou a lista de distribuição que você deseja adicionar. Não é possível adicionar Grupos criados no Power BI. Você pode adicionar membros [externos à sua organização](whitepaper-azure-b2b-power-bi.md#data-security-for-external-partners).

![Adicionar um membro](media/service-admin-rls/rls-add-member.png)

Você também pode ver quantos membros fazem parte da função pelo número entre parênteses ao lado do nome da função ou ao lado de Membros.

![Membros na função](media/service-admin-rls/rls-member-count.png)

### <a name="remove-members"></a>Remover membros

É possível remover membros selecionando o X ao lado do nome. 

![Remover membro](media/service-admin-rls/rls-remove-member.png)

## <a name="validating-the-role-within-the-power-bi-service"></a>Validando a função no serviço do Power BI

Você pode validar que a função definida está funcionando corretamente ao testar a função. 

1. Selecione as **reticências (...)** ao lado da função.
2. Selecione **Testar dados como função**

![Testar como função](media/service-admin-rls/rls-test-role.png)

Então, você verá os relatórios que estão disponíveis para essa função. Os painéis de controle não são apresentados nessa exibição. Na barra azul acima, você verá o que está sendo aplicado.

![Exibindo agora como <função>](media/service-admin-rls/rls-test-role2.png)

Você pode testar outras funções ou uma combinação de funções, selecionando **Exibindo agora como**.

![Testar outras funções](media/service-admin-rls/rls-test-role3.png)

Você pode optar por exibir dados como uma pessoa específica ou pode selecionar uma combinação de funções disponíveis para validar que estão funcionando. 

Para retornar à exibição normal, selecione **Voltar à Segurança de Nível de Linha**.

[!INCLUDE [include-short-name](./includes/rls-usernames.md)]

## <a name="using-rls-with-app-workspaces-in-power-bi"></a>Usando RLS com workspaces do aplicativo no Power BI

Se você publicar seu relatório do Power BI Desktop em um workspace do aplicativo no serviço do Power BI, as funções serão aplicadas aos membros somente leitura. Será necessário indicar que os membros só podem exibir o conteúdo do Power BI nas configurações de workspace do aplicativo.

> [!WARNING]
> Se você tiver configurado o workspace do aplicativo para que os membros tenham permissões de edição, as funções RLS não serão aplicadas a eles. Os usuários poderão ver todos os dados.

![Configurações de grupo](media/service-admin-rls/rls-group-settings.png)

[!INCLUDE [include-short-name](./includes/rls-limitations.md)]

[!INCLUDE [include-short-name](./includes/rls-faq.md)]

## <a name="next-steps"></a>Próximas etapas
[RLS (segurança em nível de linha) com o Power BI Desktop](desktop-rls.md)  

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)
