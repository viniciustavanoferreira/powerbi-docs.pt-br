---
title: Solução de problemas de pipelines de implantação
description: Solucionar problemas de pipelines de implantação no Power BI
author: KesemSharabi
ms.author: kesharab
ms.topic: troubleshooting
ms.service: powerbi
ms.subservice: powerbi-service
ms.date: 05/06/2020
ms.openlocfilehash: e41a13fac3e0ffea5171d2927cc0f3b9debbeef1
ms.sourcegitcommit: a453ba52aafa012896f665660df7df7bc117ade5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/27/2020
ms.locfileid: "85485865"
---
# <a name="deployment-pipelines-troubleshooting-preview"></a>Solução de problemas de pipelines de implantação (versão prévia)

Use este artigo para solucionar problemas em pipelines de implantação.

## <a name="general"></a>Geral

### <a name="whats-deployment-pipelines-in-power-bi"></a>O que são os pipelines de implantação no Power BI

Para entender o que são os pipelines de implantação no Power BI, confira a [Visão geral dos pipelines de implantação](deployment-pipelines-overview.md).

### <a name="how-do-i-get-started-with-deployment-pipelines"></a>Como posso começar a usar pipelines de implantação?

Comece a usar os pipelines de implantação por meio das [instruções de introdução](deployment-pipelines-get-started.md).

### <a name="why-cant-i-see-the-deployment-pipelines-button"></a>Por que não consigo ver o botão de pipelines de implantação?

Se as seguintes condições não forem atendidas, você não poderá acessar o botão de pipelines de implantação.

* Você é um [usuário do Power BI Pro](../admin/service-admin-purchasing-power-bi-pro.md)

* Você pertence a uma organização que tem capacidade Premium

* Um workspace só pode ser atribuído a um único pipeline

* Você é administrador de um novo workspace

## <a name="licensing"></a>Licenças

### <a name="what-licenses-are-needed-to-work-with-deployment-pipelines"></a>Quais licenças são necessárias para trabalhar com pipelines de implantação?

Para usar pipelines de implantação, você precisa ser um [usuário Pro](../admin/service-admin-purchasing-power-bi-pro.md) com capacidade [Premium](../admin/service-premium-what-is.md). Para obter mais informações, confira [Como acessar os pipelines de implantação](deployment-pipelines-get-started.md#accessing-deployment-pipelines).

### <a name="what-type-of-capacity-can-i-assign-to-a-workspace-in-a-pipeline"></a>Que tipo de capacidade posso atribuir a um workspace em um pipeline?

Todos os workspaces em um pipeline de implantação devem residir em uma capacidade dedicada para que o pipeline seja funcional. No entanto, você pode usar diferentes capacidades para workspaces variados em um pipeline. Também é possível usar tipos de capacidade diferentes para workspaces diferentes no mesmo pipeline.

Para desenvolvimento e teste, você pode usar uma capacidade A ou EM com uma conta do Power BI Pro para cada usuário.

Para workspaces de produção, você precisará de uma capacidade P. Se você for um ISV distribuindo conteúdo por meio de aplicativos incorporados, também poderá usar as capacidades A ou EM para produção.

## <a name="technical"></a>Técnico

### <a name="why-cant-i-see-all-my-workspaces-when-i-try-to-assign-a-workspace-to-a-pipeline"></a>Por que não consigo ver todos os meus workspaces quando tento atribuir um workspace a um pipeline?

Para atribuir um workspace a um pipeline, as seguintes condições devem ser atendidas:

* O workspace é uma [nova experiência de workspace](../collaborate-share/service-create-the-new-workspaces.md)

* Você é um administrador do workspace

* O workspace não está atribuído a outro pipeline

* O workspace reside em uma [capacidade premium](../admin/service-premium-what-is.md)

Os workspaces que não atenderem a essas condições não serão exibidos na lista de workspaces que você pode selecionar.

### <a name="how-can-i-assign-workspaces-to-all-the-stages-in-a-pipeline"></a>Como posso atribuir workspaces a todos os estágios de um pipeline?

É possível atribuir um workspace por pipeline. Depois que um workspace é atribuído a um pipeline, você pode implantá-lo nos próximos estágios do pipeline. Durante a primeira implantação, um novo workspace é criado com cópias dos itens no estágio de origem. As relações dos itens copiados são mantidas. Para obter mais informações, confira como [atribuir um workspace a um pipeline de implantação](deployment-pipelines-get-started.md#step-2---assign-a-workspace-to-a-deployment-pipeline).

### <a name="why-did-my-first-deployment-fail"></a>Por que minha primeira implantação falhou?

Sua primeira implantação pode ter falhado por vários motivos. Alguns desses motivos são listados na tabela abaixo.

|Erro  |Ação  |
|---------|---------|
|Você não tem [permissões de capacidade premium](deployment-pipelines-process.md#creating-a-premium-capacity-workspace).     |Para obter permissões de capacidade premium, peça a um administrador de capacidade para adicionar seu workspace a uma capacidade ou solicite permissões de atribuição para a capacidade. Depois que o workspace estiver em uma capacidade, reimplante-o.        |
|Você não tem permissões de workspace.     |Para implantar, você precisa ser um membro do workspace. Peça ao administrador do workspace para conceder a você as permissões apropriadas.         |
|O administrador do Power BI desabilitou a criação de workspaces.     |Entre em contato com o administrador do Power BI para obter suporte.         |
|O workspace não é uma [nova experiência de workspace](../collaborate-share/service-create-the-new-workspaces.md).     |Crie seu conteúdo na nova experiência de workspace. Se você tiver conteúdo em um workspace clássico, poderá [atualizá-lo](../collaborate-share/service-upgrade-workspaces.md) para uma nova experiência de workspace.         |
|Você está usando a [implantação seletiva](deployment-pipelines-get-started.md#selective-deployment) e não está selecionando o conjunto de dados do seu conteúdo.     |Realize uma destas ações: </br></br>Desmarque o conteúdo que está vinculado ao seu conjunto de dados. Seu conteúdo não selecionado (como relatórios ou dashboards) não será copiado para o próximo estágio. </br></br>Selecione o conjunto de dados que está vinculado ao conteúdo selecionado. Seu conjunto de dados será copiado para o próximo estágio.         |

### <a name="im-getting-a-warning-that-i-have-unsupported-artifacts-in-my-workspace-when-im-trying-to-deploy-how-can-i-know-which-artifacts-are-not-supported"></a>Eu recebo um aviso de que tenho "artefatos sem suporte" em meu workspace quando tento implantar. Como posso saber quais artefatos não têm suporte?

Para obter uma lista abrangente de itens e artefatos que não têm suporte em pipelines de implantação, confira as seguintes seções:

* [Itens sem suporte](deployment-pipelines-process.md#unsupported-items)

* [Propriedades de item que não são copiadas](deployment-pipelines-process.md#item-properties-that-are-not-copied)

### <a name="why-did-my-deployment-fail-due-to-broken-rules"></a>Por que a minha implantação falhou devido a regras desfeitas?

Se você tiver problemas ao configurar regras de conjuntos de dados, acesse [regras de conjunto de dados](deployment-pipelines-get-started.md#step-4---create-dataset-rules) e siga as [limitações da regra de conjunto de dados](deployment-pipelines-get-started.md#dataset-rule-limitations).

Se a sua implantação foi bem-sucedida anteriormente e, de repente, está falhando com regras desfeitas, isso pode ser devido à republicação de um conjunto de dados. As seguintes alterações no conjunto de dados de fonte resultam em uma implantação com falha:

**Regras de parâmetro**

* Um parâmetro removido

* Um nome de parâmetro alterado

**Regras de fonte de dados**

Suas regras de conjunto de dados têm valores ausentes. Isso pode ter ocorrido caso seu conjunto de dados tenha sido alterado.

![regra desfeita](media/deployment-pipelines-troubleshooting/broken-rule.png)

Quando uma implantação bem-sucedida anteriormente falha devido a links desfeitos, um aviso é exibido. Você pode clicar em **Configurar regras** para navegar até o painel de configurações de implantação, no qual o conjunto de dados com falha está marcado. Quando você clica no conjunto de dados, as regras desfeitas são marcadas.

Para implantar com êxito, corrija ou remova as regras desfeitas e reimplante-as.

### <a name="how-can-i-change-the-data-source-in-the-pipeline-stages"></a>Como posso alterar a fonte de dados nos estágios do pipeline?

Não é possível alterar a conexão da fonte de dados no serviço do Power BI.

Se quiser alterar a fonte de dados nos estágios de teste ou de produção, você poderá usar [regras de conjunto de dados](deployment-pipelines-get-started.md#step-4---create-dataset-rules) ou [APIs](https://docs.microsoft.com/rest/api/power-bi/datasets/updateparametersingroup). As regras de conjunto de dados entrarão em vigor somente após a próxima implantação.

### <a name="i-fixed-a-bug-in-production-but-now-i-cant-click-the-deploy-to-previous-stage-button-why-is-it-greyed-out"></a>Corrigi um bug em produção, mas agora não consigo clicar no botão "implantar no estágio anterior". Por que ele está esmaecido?

Só é possível fazer implantações em estágios anteriores que estejam vazios. Se você tiver conteúdo no estágio de teste, não poderá implantar em estágios anteriores à produção.

Depois de criar o pipeline, use o estágio de desenvolvimento para desenvolver seu conteúdo e os estágios de teste para revisá-lo e testá-lo. Você pode corrigir bugs nesses estágios e, em seguida, implantar o ambiente corrigido no estágio de produção.

>[!NOTE]
>A implantação em estágios anteriores só dá suporte à [implantação completa](deployment-pipelines-get-started.md#deploying-all-content). Ela não permite a [implantação seletiva](deployment-pipelines-get-started.md#selective-deployment)

### <a name="does-deployment-pipelines-support-multi-geo"></a>Os pipelines de implantação dão suporte a várias áreas geográficas?

Há suporte para várias áreas geográficas. Pode levar mais tempo para implantar conteúdo entre os estágios em diferentes áreas geográficas.

## <a name="permissions"></a>Permissões

### <a name="what-is-the-deployment-pipelines-permissions-model"></a>O que é o modelo de permissões de pipelines de implantação?

O modelo de permissões de pipelines de implantação é descrito na seção [permissões](deployment-pipelines-process.md#permissions).

### <a name="who-can-deploy-content-between-stages"></a>Quem pode implantar conteúdo entre os estágios?

O conteúdo pode ser implantado em um estágio vazio ou em um estágio que contenha conteúdo. O conteúdo deve residir em uma [capacidade premium](../admin/service-premium-what-is.md).

* **Implantar em um estágio vazio** – Qualquer [usuário Pro](../admin/service-admin-purchasing-power-bi-pro.md) que seja membro ou administrador no workspace de origem.

* **Implantar em um estágio com conteúdo** – Qualquer [usuário Pro](../admin/service-admin-purchasing-power-bi-pro.md) que é membro de ambos os workspaces nos estágios de implantação de origem e de destino.

* **Substituir um conjunto de dados** – A implantação substitui cada conjunto de dados que é incluído no estágio de destino, mesmo que ele não tenha sido alterado. O usuário deve ser o proprietário de todos os conjuntos de dados do estágio de destino especificados na implantação.

### <a name="which-permissions-do-i-need-to-configure-dataset-rules"></a>De quais permissões preciso para configurar as regras de conjunto de dados?

Para configurar regras de conjunto de dados em pipelines de implantação, você deve ser o proprietário do conjunto de dados.

### <a name="why-cant-i-see-workspaces-in-the-pipeline"></a>Por que não consigo ver os workspaces no pipeline?

As permissões de pipeline e workspace são gerenciadas separadamente. Você pode ter permissões de pipeline, mas não permissões de workspace. Para obter mais informações, confira a seção [Permissões](deployment-pipelines-process.md#permissions).

## <a name="next-steps"></a>Próximas etapas

>[!div class="nextstepaction"]
>[Introdução aos pipelines de implantação](deployment-pipelines-overview.md)

>[!div class="nextstepaction"]
>[Introdução aos pipelines de implantação](deployment-pipelines-get-started.md)

>[!div class="nextstepaction"]
>[Compreender o processo de pipelines de implantação](deployment-pipelines-process.md)

>[!div class="nextstepaction"]
>[Melhores práticas para pipelines de implantação](deployment-pipelines-best-practices.md)