---
title: Usar Exibição de modelagem no Power BI Desktop
description: Usar a Exibição de Modelagem para ver conjuntos de dados complexos em um formato visual no Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Transform and shape data
ms.openlocfilehash: b9df4398c410f52e3d5cdd51a99a40de107f5867
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/05/2020
ms.locfileid: "75760872"
---
# <a name="work-with-modeling-view-in-power-bi-desktop"></a>Trabalhar com a exibição de Modelagem no Power BI Desktop

Com a **exibição de Modelagem** no **Power BI Desktop**, você pode ver conjuntos de dados complexos que contêm muitas tabelas e trabalhar com eles.


## <a name="using-modeling-view"></a>Usando a Exibição de Modelagem

Para acessar a Exibição de Modelagem, selecione o ícone de Exibição de Modelagem localizado no lado esquerdo do **Power BI Desktop**, conforme mostrado na imagem a seguir.

![Ícone de Exibição de Modelagem no Power BI Desktop](media/desktop-modeling-view/modeling-view_02.png)

## <a name="creating-separate-diagrams"></a>Criando diagramas separados

Com a Exibição de Modelagem, você pode criar diagramas do modelo, que contêm apenas um subconjunto das tabelas no modelo. Isso pode ajudar a fornecer uma exibição mais clara das tabelas com as quais você deseja trabalhar e facilita o trabalho com conjuntos de dados complexos. Para criar um novo diagrama com apenas um subconjunto das tabelas, clique no sinal **+** , ao lado da guia **Todas as tabelas**, na parte inferior da janela do Power BI Desktop.

![Criar um novo diagrama clicando no sinal + na seção de guias](media/desktop-modeling-view/modeling-view_03.png)

Você pode arrastar uma tabela da lista **Campos** para a superfície do diagrama. Clique com botão direito do mouse na tabela e selecione **Adicionar tabelas relacionadas**, no menu exibido.

![Clique com o botão direito do mouse em uma tabela e selecione Adicionar tabelas relacionadas](media/desktop-modeling-view/modeling-view_04.png)

Quando você fizer isso, as tabelas relacionadas à tabela original serão exibidas no novo diagrama. A imagem a seguir mostra como as tabelas relacionadas são exibidas após a seleção da opção de menu **Adicionar tabelas relacionadas**.

![Mostrando tabelas relacionadas](media/desktop-modeling-view/modeling-view_05.png)

## <a name="setting-common-properties"></a>Configurando propriedades comuns

Para selecionar vários objetos ao mesmo tempo na Exibição de Modelagem, mantenha pressionada a tecla **Ctrl** e clique em várias tabelas. Quando você seleciona várias tabelas, elas ficam realçadas na Exibição de Modelagem. Quando várias tabelas são realçadas, as alterações aplicadas no painel **Propriedades** se aplicam a todas as tabelas selecionadas.

Por exemplo, para alterar o [modo de armazenamento](desktop-storage-mode.md) de várias tabelas na exibição de diagrama, mantenha pressionada a tecla **Ctrl**, selecione tabelas e altere a configuração do modo de armazenamento no painel **Propriedades**.

![Segure a tecla CTRL para selecionar várias tabelas, defina as propriedades comuns nas tabelas selecionadas](media/desktop-modeling-view/modeling-view_06.png)


## <a name="next-steps"></a>Próximas etapas

Os artigos a seguir tratam mais sobre os modelos de dados e também descrevem detalhadamente o DirectQuery.

* [Agregações no Power BI Desktop (versão prévia)](desktop-aggregations.md)
* [Modelos compostos no Power BI Desktop](desktop-composite-models.md)
* [Modo de armazenamento no Power BI Desktop (prévia)](desktop-storage-mode.md)
* [Relações muitos para muitos no Power BI Desktop](desktop-many-to-many-relationships.md)


Artigos do DirectQuery:

* [Usar o DirectQuery no Power BI](desktop-directquery-about.md)
* [Fontes de dados com suporte do DirectQuery no Power BI](desktop-directquery-data-sources.md)
