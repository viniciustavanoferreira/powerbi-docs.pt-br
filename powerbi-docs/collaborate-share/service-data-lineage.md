---
title: Linhagem de dados
description: Em projetos modernos de BI (business intelligence), entender o fluxo de dados da fonte de dados para o destino é um desafio crucial para muitos clientes.
author: paulinbar
ms.reviewer: ''
ms.service: powerbi
ms.topic: conceptual
ms.date: 02/27/2020
ms.author: painbar
LocalizationGroup: ''
ms.openlocfilehash: fc1f55fbadfaa6c25dd9140a41064eaa876013df
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/05/2020
ms.locfileid: "81525389"
---
# <a name="data-lineage"></a>Linhagem de dados
Em projetos modernos de BI (business intelligence), entender o fluxo de dados da fonte de dados para o destino pode ser um desafio. O desafio será ainda maior se você tiver criado projetos analíticos avançados que abrangem uma variedade de fontes de dados, artefatos e dependências. Perguntas como "o que acontecerá se eu alterar esses dados?" ou "por que este relatório não está atualizado?" podem ser difíceis de responder. Elas podem exigir uma equipe de especialistas ou uma investigação profunda para serem entendidas. Desenvolvemos uma exibição de linhagem de dados para ajudar você a responder a essas perguntas.

![Exibição da linhagem de dados do Power BI](media/service-data-lineage/service-data-lineage-view.png)
 
O Power BI tem vários tipos de artefatos, como dashboards, relatórios, conjuntos de dados e fluxos de dados. Muitos conjuntos de dados e fluxos de dados se conectam a fontes de dados externas, como o SQL Server, e a conjuntos de dados externos em outros workspaces. Quando um conjunto de dados é externo a um workspace do qual você é proprietário, ele pode estar em um workspace que seja propriedade de uma pessoa na TI ou de outro analista. Em última análise, as fontes de dados e os conjuntos de dados externos dificultam saber a origem dos dados. Para projetos complexos e para aqueles mais simples, apresentamos a exibição de linhagem.

Na exibição de linhagem, você vê as relações de linhagem entre todos os artefatos de um workspace e todas as dependências externas. Ela mostra as conexões entre todos os artefatos do workspace, incluindo conexões a fluxos de dados, upstream e downstream.

## <a name="explore-lineage-view"></a>Explorar a exibição de linhagem

Todo workspace, seja novo ou clássico, tem automaticamente uma exibição de linhagem. Você precisa, no mínimo, de uma função Colaborador no workspace para exibi-la. Confira [Permissões](#permissions) neste artigo para obter detalhes.

* Para acessar a exibição de linhagem, acesse a exibição de lista do workspace. Toque na seta ao lado de **Exibição de lista** e selecione **Exibição de linhagem**.

   ![Alternar para a exibição de linhagem](media/service-data-lineage/service-data-lineage-view-select.png)

Nessa exibição, você vê todos os artefatos do workspace e como os dados fluem de um artefato para outro.

**Fontes de dados**

Você vê as fontes de dados das quais os conjuntos de dados e os fluxos de dados obtêm os dados. Nos cartões da fonte de dados, você vê mais informações que podem ajudar a identificar a origem. Por exemplo, para o Azure SQL Server, você também vê o nome do banco de dados.

![Fonte de dados da exibição de linhagem sem gateway](media/service-data-lineage/service-data-lineage-data-source-card.png)
 
**Gateways**

Se uma fonte de dados estiver conectada por meio de um gateway local, as informações do gateway serão adicionadas ao cartão da fonte de dados. Caso tenha permissões, seja como administrador do gateway ou como um usuário da fonte de dados, você verá mais informações, como o nome do gateway.

![Fonte de dados da exibição de linhagem com gateway](media/service-data-lineage/service-data-lineage-data-gateway-card.png)

**Conjuntos de dados e fluxos de dados**
 
Em conjuntos de dados e fluxos de dados, você pode se eles foram certificados ou promovidos e a hora da última atualização.

![Conjuntos de dados promovidos e certificados na exibição de linhagem](media/service-data-lineage/service-data-lineage-promoted-certified.png)
 
Se um relatório no workspace for criado em um conjunto de dados ou fluxo de dados que esteja localizado em outro workspace, você verá o nome do workspace de origem no cartão do conjunto ou fluxo de dados. Selecione o nome do workspace de origem para acessá-lo.

* Em qualquer artefato, selecione **Mais opções (...)** para exibir o menu de opções. Ele apresenta todas as mesmas ações disponíveis na exibição de lista.

Para ver mais metadados em qualquer artefato, selecione o próprio cartão do artefato. Informações adicionais sobre o artefato são exibidas em um painel lateral. Na imagem a seguir, o painel lateral exibe os metadados de um conjunto de dados selecionado.

![Painel lateral com mais informações](media/service-data-lineage/service-data-lineage-side-pane.png)
 
## <a name="show-lineage-for-any-artifact"></a>Mostrar a linhagem de qualquer artefato 

Digamos que você deseje ver a linhagem de um artefato específico.

* Selecione as setas duplas abaixo do artefato.

   ![Realçar a linhagem de um artefato específico](media/service-data-lineage/service-data-lineage-specific-artifact.png)

   O Power BI realça todos os artefatos relacionados a esse artefato e esmaece o restante. 

## <a name="navigation-and-full-screen"></a>Navegação e tela inteira 

A exibição de linhagem é uma tela interativa. Use o mouse e o touchpad para navegar na tela e ampliá-la ou reduzi-la.

* Para ampliá-la e reduzi-la, use o menu no canto inferior direito, o mouse ou o touchpad.
* Para ter mais espaço para o próprio grafo, use a opção de tela inteira no canto inferior direito. 

    ![Ampliar ou reduzir, ou tela inteira](media/service-data-lineage/service-data-lineage-zoom.png)

## <a name="permissions"></a>Permissões

* Você precisa de uma licença do Power BI Pro para ver a exibição de linhagem.
* A exibição de linhagem só está disponível para os usuários com acesso ao workspace.
* Os usuários precisam ter uma função de Administrador, Membro ou Colaborador no workspace. Usuários com a função Espectador não podem alternar para a exibição de linhagem.


## <a name="considerations-and-limitations"></a>Considerações e limitações

- A exibição de linhagem não está disponível no Internet Explorer. Confira [Navegadores compatíveis com o Power BI](../power-bi-browsers.md) para obter detalhes.

## <a name="next-steps"></a>Próximas etapas

* [Introdução aos conjuntos de dados entre workspaces (versão prévia)](../service-datasets-across-workspaces.md)
* [Análise do impacto do conjunto de dados](service-dataset-impact-analysis.md)
