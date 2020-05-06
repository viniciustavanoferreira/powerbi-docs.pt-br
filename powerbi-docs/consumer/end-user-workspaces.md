---
title: Como o conteúdo é organizado em workspaces
description: Saiba mais sobre workspaces e funções de workspace
author: mihart
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/22/2020
ms.author: mihart
LocalizationGroup: Consumers
ms.openlocfilehash: 801b5cf5400bbe1cc0487eef596ea3d1cdc5fb1e
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82120129"
---
# <a name="collaborate-in-workspaces"></a>Colaborar em workspaces

 *Workspaces* são locais para colaborar com colegas em um conteúdo específico. Os workspaces são criados por *designers* do Power BI para armazenar coleções de dashboards e relatórios. Em seguida, o designer pode agrupar essa coleção em um *aplicativo* e distribuí-lo para toda a organização ou para pessoas ou grupos específicos. 

 Todos que usam o serviço do Power BI também têm um **Meu workspace**.  Meu workspace é a sua área restrita pessoal na qual você pode criar conteúdo para uso próprio.

 Você pode ver seus workspaces na **Página Inicial** do Power BI ou selecionando **Workspace** ou **Meu workspace** no painel de navegação à esquerda.

 ![painel de navegação mostrando dois tipos de workspaces](media/end-user-workspaces/power-bi-home.png)

## <a name="types-of-workspaces"></a>Tipos de espaços de trabalho
O **Meu Workspace** armazena todo o conteúdo que você tem e cria. Pense nele como sua área restrita pessoal ou como área de trabalho para seu próprio conteúdo. Para muitos *consumidores* do Power BI, o **Meu workspace** permanece vazio porque seu trabalho não envolve criar conteúdo. Os *consumidores*, por definição, consomem dados criados por outras pessoas e usam esses dados para tomar decisões de negócios. Se você acha que está criando conteúdo, considere ler os [artigos do Power BI para designers](../create-reports/index.yml).

Os **espaços de trabalho de aplicativo** contêm todo o conteúdo para o aplicativo específico. Quando um *designer* cria um aplicativo, ele agrupa todo o conteúdo necessário para que o aplicativo seja utilizado. O conteúdo poderá incluir dashboards, relatórios e conjuntos de dados. Nem todo aplicativo conterá essas três partes de conteúdo. Um aplicativo pode conter apenas um dashboard, três de cada tipo de conteúdo ou até mesmo vinte relatórios. Isso tudo depende do que o *designer* inclui no aplicativo. É mais comum que os workspaces de aplicativo para *consumidores* não incluam os conjuntos de dados.

O workspace de aplicativo Vendas em números abaixo contém três relatórios e um dashboard. 

![painel de navegação mostrando dois tipos de workspaces](media/end-user-workspaces/power-bi-app-workspace.png)

## <a name="roles-in-the-workspaces"></a>Funções nos workspaces

As funções determinam o que a pessoa pode fazer em um workspace, para que as equipes possam colaborar.  Ao conceder acesso a um novo workspace, os *designers* adicionam indivíduos ou grupos a uma das funções de workspace: **Visualizador**, **Membro**, **Colaborador**, ou **Administrador**. 


Como *consumidor* do Power BI, geralmente, você interagirá nos workspaces usando a função **Visualizador**. Mas um *designer* também pode atribuir a você a função **Membro** ou **Colaborador**. A função Visualizador permite ver o conteúdo (dashboards, relatórios, aplicativos) criado por outras pessoas e compartilhado com você, bem como interagir com ele. Como a função Visualizador não pode acessar o conjunto de dados subjacente, essa é uma forma segura de interagir com o conteúdo e não precisar se preocupar com "danos" aos dados subjacentes.


Para obter uma lista detalhada do que você pode fazer como *consumidor* com a função Visualizador, confira [Recursos do Power BI para consumidores](end-user-features.md).


### <a name="workspace-roles"></a>Funções de workspace
Estas são as capacidades das quatro funções: administradores, membros, colaboradores e visualizadores. Todos esses recursos, exceto exibição e interação, exigem uma licença Power BI Pro.

|Funcionalidade   | Administrador  | Membro  | Colaborador  | Visualizador |
|---|---|---|---|---|
| Atualizar e excluir o workspace.  | X  |   |   |   | 
| Adicionar/remover pessoas, incluindo outros administradores.  | X  |   |   |   |
| Adicionar membros ou outras pessoas com permissões inferiores.  |  X | X  |   |   |
| Publicar e atualizar um aplicativo. |  X | X  |   |   |
| Compartilhar um item ou um aplicativo.<sup>1</sup> |  X | X  |   |   |
| Permitir que outras pessoas compartilhem itens novamente.<sup>1</sup> |  X | X  |   |   |
| Destacar aplicativos na página inicial de colegas |  X | X  |   |   |
| Destacar dashboards e relatórios na página inicial de colegas |  X | X  | X |   |
| Criar, editar e excluir conteúdo no workspace.  |  X | X  | X  |   |
| Publicar relatórios no workspace, excluir conteúdo.  |  X | X  | X  |   |
| Criar um relatório em outro workspace com base em um conjunto de dados neste workspace.<sup>1</sup> |  X | X  | X  |   |
| Copiar um relatório. | X | X | X |  |
| Exibir e interagir com um item.<sup>2</sup> |  X | X  | X  | X  |
| Ler dados armazenados em fluxo de trabalho do workspace | X | X | X | X |

1. Os Colaboradores e os Membros podem compartilhar itens em um workspace quando têm permissões Recompartilhar.

2. Mesmo se você não tiver uma licença do Power BI Pro, poderá ver itens e interagir com eles no serviço do Power BI se os itens estiverem em um workspace na capacidade Premium.

## <a name="licensing-workspaces-and-capacity"></a>Licenciamento, workspaces e capacidade
O licenciamento também desempenha um papel para determinar o que você pode e não pode fazer em um workspace. Muitos recursos exigem que o usuário tenha uma licença do Power BI *Pro*. A maioria dos *consumidores* trabalha com uma licença *gratuita*. 

Se você tiver uma licença gratuita e o workspace estiver armazenado na *capacidade Premium*, poderá ver o conteúdo desse workspace e interagir com ele. Um ícone de losango identifica os workspaces e os aplicativos que estão armazenados na capacidade Premium.

![Workspaces selecionados](media/end-user-workspaces/power-bi-diamond.png) Para saber mais, confira [Qual licença eu tenho?](end-user-license.md).



## <a name="next-steps"></a>Próximas etapas
* [Aplicativos no Power BI](end-user-apps.md)    

* Dúvidas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)

