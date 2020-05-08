---
title: O que é o Power BI Desktop?
description: Saiba mais sobre o Power BI Desktop e como começar a usá-lo.
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: overview
ms.date: 12/16/2019
ms.author: davidi
LocalizationGroup: Get started
ms.openlocfilehash: bd95dfcc5d621b5ae4988e187d7cc6d9478feb58
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/05/2020
ms.locfileid: "75731079"
---
# <a name="what-is-power-bi-desktop"></a>O que é o Power BI Desktop?

O *Power BI Desktop* é um aplicativo gratuito que pode ser instalado no computador local e que permite que você se conecte aos seus dados, transforme-os e visualize-os. Com o Power BI Desktop, você pode se conectar a várias fontes de dados diferentes e combiná-las (geralmente chamado de *modelagem*) em um modelo de dados. Esse modelo de dados permite que você crie visuais e coleções de visuais que podem ser compartilhados como relatórios com outras pessoas em sua organização. A maioria dos usuários que trabalha em projetos de business intelligence usa o Power BI Desktop para criar relatórios e, em seguida, usa o *serviço do Power BI* para compartilhar os relatórios com outras pessoas.

![Power BI Desktop](media/desktop-what-is-desktop/what-is-desktop_01.png)

Os usos mais comuns do Power BI Desktop são os seguintes:

* Conectar aos dados
* Transformar e limpar esses dados para criar um modelo de dados
* Criar visuais, como gráficos, que fornecem representações visuais dos dados
* Criar relatórios que são conjuntos de visuais em uma ou mais páginas do relatório
* Compartilhar relatórios com outras pessoas usando o serviço do Power BI

As pessoas responsáveis por essas tarefas geralmente são consideradas *analistas de dados* (às vezes, chamados de *analistas*) ou profissionais de business intelligence (geralmente conhecidos como *criadores de relatórios*). No entanto, muitas pessoas que não se consideram analistas nem criadores de relatórios usam o Power BI Desktop para criar relatórios interessantes ou para extrair dados de várias fontes e criar modelos de dados, que podem ser compartilhados com colegas de trabalho e organizações.

Há três exibições disponíveis no Power BI Desktop que são selecionadas no lado esquerdo da tela. As exibições, mostradas na ordem em que aparecem, são as seguintes:
* **Relatório**: nessa exibição, você cria relatórios e visuais, na qual passa a maior parte do seu tempo de criação.
* **Dados**: nessa exibição, você vê tabelas, medidas e outros dados usados no modelo de dados associado ao relatório e transforma os dados para o melhor uso no modelo do relatório.
* **Modelo**: nessa exibição, você vê e gerencia as relações entre tabelas no modelo de dados.

A seguinte imagem mostra as três exibições, que ficam do lado esquerdo da tela:

![Exibições do Power BI Desktop](media/desktop-what-is-desktop/what-is-desktop-07.png)
 

## <a name="connect-to-data"></a>Conectar aos dados
Para começar a usar o Power BI Desktop, a primeira etapa é se conectar aos dados. Há muitos diferentes tipos de fontes de dados aos quais você pode se conectar por meio do Power BI Desktop. 

Para se conectar aos dados:

1. Na faixa de opções **Página Inicial**, selecione **Obter Dados** > **Mais**. 

   A janela **Obter Dados** será exibida, mostrando as muitas categorias às quais o Power BI Desktop pode se conectar.

   ![Obter Dados no Power BI Desktop](media/desktop-what-is-desktop/what-is-desktop_02.png)

2. Quando você seleciona um tipo de dados, o sistema solicita informações, como a URL e as credenciais, necessárias para o Power BI Desktop se conectar à fonte de dados em seu nome.

   ![Conectar-se a um banco de dados SQL Server no Power BI Desktop](media/desktop-what-is-desktop/what-is-desktop_03.png)

3. Depois que você se conectar a uma ou mais fontes de dados, o ideal será transformar os dados, de modo que sejam úteis para você.

## <a name="transform-and-clean-data-create-a-model"></a>Transformar e limpar os dados, criar um modelo

No Power BI Desktop, limpe e transforme os dados usando o [Editor do Power Query](https://docs.microsoft.com/power-bi/desktop-query-overview) interno. Com o Editor do Power Query, faça alterações nos dados, como alterar um tipo de dados, remover colunas ou combinar dados de várias fontes. É como o trabalho de um escultor: você começa com um grande bloco de argila (ou dados) e, em seguida, remove partes ou adiciona outras, conforme necessário, até que a forma dos dados fique como desejado. 

Para iniciar o Editor do Power Query:

- Selecione **Editar Consultas** > **Editar Consultas** na faixa de opções **Página Inicial**.

   A janela do **Editor do Power Query** será exibida.

   ![Editor do Power Query no Power BI Desktop](media/desktop-getting-started/designer_gsg_editquery.png)

Cada etapa executada na transformação de dados (como renomear uma tabela, transformar um tipo de dados ou excluir uma coluna) é registrada pelo Editor do Power Query. Toda vez que essa consulta se conecta à fonte de dados, essas etapas são executadas, de modo que os dados sempre sejam formatados da maneira que você especificar.

A imagem a seguir mostra a janela do **Editor do Power Query**, com uma consulta que foi formatada e transformada em um modelo.

 ![Janela do Editor do Power Query](media/desktop-getting-started/shapecombine_querysettingsfinished.png)

Depois que os dados estiverem como você desejar, é possível criar visuais. 

## <a name="create-visuals"></a>Criar visuais 

Quando você tiver um modelo de dados, arraste *campos* para a tela do relatório para criar *visuais*. Um visual é uma representação gráfica dos dados no modelo. Há muitos tipos diferentes de visuais para escolher no Power BI Desktop. O visual a seguir mostra um gráfico de colunas simples. 

![Um visual no Power BI Desktop](media/desktop-what-is-desktop/what-is-desktop_04.png)

Para criar ou alterar um visual: 

- No painel **Visualizações**, selecione o ícone do visual. 

   ![O painel Visualizações no Power BI Desktop](media/desktop-what-is-desktop/what-is-desktop_05.png)

   Se você já tiver um visual selecionado na tela do relatório, o visual selecionado será alterado para o tipo selecionado. 

   Se nenhum visual estiver selecionado na tela, um visual será criado com base na seleção.


## <a name="create-reports"></a>Criar relatórios

Com mais frequência, o ideal será criar uma coleção de visuais que mostram vários aspectos dos dados que você usou para criar o modelo no Power BI Desktop. Um conjunto de visuais em um arquivo do Power BI Desktop é chamado de *relatório*. Um relatório pode ter uma ou mais páginas, assim como um arquivo do Excel pode ter uma ou mais planilhas. 

Com o Power BI Desktop, você pode criar relatórios complexos e visualmente sofisticados, usando dados de várias fontes, tudo em um só relatório que você pode compartilhar com outras pessoas em sua organização.

Na imagem a seguir, você verá a primeira página de um relatório do Power BI Desktop, chamada **Visão geral**, como vista na guia na parte inferior da imagem. 

![Relatório de exemplo do Power BI Desktop](media/desktop-what-is-desktop/what-is-desktop_01.png)

## <a name="share-reports"></a>Compartilhar relatórios

Depois que um relatório estiver pronto para ser compartilhado com outras pessoas, você poderá *publicar* o relatório no serviço do Power BI e disponibilizá-lo para qualquer pessoa em sua organização que tenha uma licença do Power BI. 

Para publicar um relatório do Power BI Desktop: 

1. Selecione **Publicar** na faixa de opções **Página Inicial**.

   ![Publicar um relatório por meio do Power BI Desktop](media/desktop-what-is-desktop/what-is-desktop_06.png)

   O Power BI Desktop conecta você ao serviço do Power BI com a sua conta do Power BI. 

2. O Power BI solicita a você que selecione o local no serviço do Power BI em que deseja compartilhar o relatório, como seu workspace, um workspace da equipe ou algum outro local no serviço do Power BI. 

   Você deve ter uma licença do Power BI para compartilhar relatórios para o serviço do Power BI.


## <a name="next-steps"></a>Próximas etapas

Para começar a usar o Power BI Desktop, primeiro, baixe e instale o aplicativo. Há duas maneiras de obter o Power BI Desktop:

* [Obter o Power BI Desktop por meio da Windows Store](https://aka.ms/pbidesktopstore)
* [Baixar o Power BI Desktop pela Web](https://docs.microsoft.com/power-bi/desktop-get-the-desktop#download-power-bi-desktop-directly)

