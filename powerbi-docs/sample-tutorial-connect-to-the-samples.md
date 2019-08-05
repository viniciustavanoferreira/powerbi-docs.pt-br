---
title: Conectar-se aos exemplos no serviço do Power BI
description: Saiba como instalar e explorar os exemplos no serviço do Power BI.
author: maggiesMSFT
manager: kfile
ms.reviewer: amac
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 07/19/2019
ms.author: maggies
LocalizationGroup: Samples
ms.openlocfilehash: 3577c19342d9f2dc5b0e3ab9908f47f82430e6db
ms.sourcegitcommit: 012f05efc4e97aeb6178fb2fc820b73bcc1ce920
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68391514"
---
#  <a name="connect-to-the-samples-in-the-power-bi-service"></a>Conectar-se aos exemplos no serviço do Power BI

Este tutorial mostra como: 
- importar um pacote de conteúdo de exemplo, adicioná-lo ao serviço do Power BI e abrir o conteúdo. Um *pacote de conteúdo* é um tipo de exemplo em que o conjunto de dados é fornecido em um pacote com um dashboard e um relatório. 
- Abra um arquivo .pbix de exemplo no Power BI Desktop.

Se você quiser mais informações básicas, veja [Conjuntos de dados de exemplo para Power BI](sample-datasets.md). Neste artigo, você aprenderá sobre os exemplos: como obtê-los, em que local salvá-los, como usá-los e algumas das histórias de cada um deles. 

## <a name="prerequisites"></a>Pré-requisitos
As amostras estão disponíveis para o serviço Power BI e no Power BI Desktop. Para acompanhar, usaremos o exemplo de análise de varejo.

O pacote de conteúdo de exemplo de *Análise de Varejo* usado neste tutorial consiste em um painel, um relatório e um conjunto de dados.
Para familiarizar-se com esse pacote de conteúdo específico e com seu cenário, veja [Exemplo de análise de varejo para Power BI: Faça um tour](sample-retail-analysis.md) antes de começar.

## <a name="samples-in-the-power-bi-service"></a>Exemplos no serviço do Power BI

1. Abra o serviço do Power BI (app.powerbi.com), entre e abra o workspace em que você deseja salvar o exemplo. 

    Se você não tiver uma licença do Power BI Pro, poderá salvar a amostra em Meu Espaço de Trabalho.

2. Selecione **Obter Dados** na parte inferior do painel de navegação esquerdo. 

   ![Selecionar Obter Dados](media/sample-datasets/power-bi-get-data.png)

   Se você não vir **Obter Dados**, expanda o painel de navegação selecionando o seguinte ícone na parte superior do painel: ![ícone de hambúrguer](media/sample-tutorial-connect-to-the-samples/expand-nav.png).

5. Na página **Obter Dados** que aparece, selecione **Exemplos**.
   
6. Selecione **Exemplo de Análise de Varejo** e escolha **Conectar**.   
   
   ![Botão Conectar](media/sample-tutorial-connect-to-the-samples/pbi_retailanalysissampleconnect.png)

## <a name="what-was-imported"></a>O que foi importado?
Com os pacotes de conteúdo de exemplo, quando você seleciona **Conectar**, o Power BI obtém uma cópia desse pacote de conteúdo e armazenando-a para você na nuvem. Porque a pessoa que criou o pacote de conteúdo incluiu um conjunto de dados, um relatório e um dashboard – isso é o que você obtém quando seleciona **Conectar**. 

1. Ao selecionar **Conectar**, O Power BI cria o novo dashboard e o lista na guia **Dashboards**. 
   
   ![Entrada Exemplo de Análise de Varejo](media/sample-retail-analysis/retail-entry.png)
2. Abra a guia **Relatórios**. Aqui você verá um novo relatório chamado *Exemplo de Análise de Varejo*.
   
   ![Entrada de relatório Exemplo de Análise de Varejo](media/sample-tutorial-connect-to-the-samples/power-bi-new-report.png)
   
   Confira a guia **Conjuntos de dados**; também há um novo conjunto de dados.
   
   ![Entrada do conjunto de dados de Exemplo de Análise de Varejo](media/sample-tutorial-connect-to-the-samples/power-bi-new-dataset.png)

## <a name="explore-your-new-content"></a>Explore o novo conteúdo
Agora, explore o dashboard, o conjunto de dados e o relatório por conta própria. Há várias maneiras diferentes de navegar para seus dashboards, relatórios e conjuntos de dados. Uma dessas maneiras é descrita no procedimento a seguir.  

1. Volte para a guia **Dashboards** e selecione o dashboard **Exemplo de Análise de Varejo** para abri-lo.       

   O dashboard é aberto com uma variedade de blocos de visualização.   
 
1. Selecione um dos blocos no dashboard para abrir o relatório subjacente. Neste exemplo, selecionaremos o gráfico de área, **Vendas deste ano, vendas do ano passado por mês fiscal**.  

   ![Dashboard de exemplo de Análise de Varejo com visual realçado](media/sample-tutorial-connect-to-the-samples/power-bi-dashboards2new.png)

   O relatório é aberto na página que contém o gráfico de área selecionado. Nesse caso, a página **Vendas mensais do distrito** do relatório.
   
   ![Página relatório de Vendas Mensais do Distrito](media/sample-tutorial-connect-to-the-samples/power-bi-report.png)
   
   > [!NOTE]
   > Se o bloco tiver sido criado usando [P e R do Power BI](power-bi-tutorial-q-and-a.md), a página de P e R será aberta. Se o bloco foi [fixado do Excel](service-dashboard-pin-tile-from-excel.md), o Excel Online será aberto dentro do Power BI.
   > 
   > 
1. Quando uma pessoa compartilha um pacote de conteúdo com os colegas, ela normalmente deseja compartilhar apenas os insights, em vez de fornecer acesso direto aos dados. Na guia **Conjuntos de dados**, você tem várias opções para explorar seu conjunto de dados. No entanto, você não pode exibir as linhas e colunas de seus dados como no Power BI Desktop ou no Excel. 
   
   ![Entrada do conjunto de dados de Exemplo de Análise de Varejo](media/sample-tutorial-connect-to-the-samples/power-bi-new-dataset.png)
   
1. Uma maneira de explorar o conjunto de dados é criar suas próprias visualizações e relatórios do zero. Selecione o ícone de gráfico ![Ícone de Gráfico](media/sample-tutorial-connect-to-the-samples/power-bi-chart-icon4.png) para abrir o conjunto de dados no modo de edição de relatório.
     
   ![Novo relatório](media/sample-tutorial-connect-to-the-samples/power-bi-report-editing.png)

1. Outra maneira de explorar o conjunto de dados é executar os [Insights rápidos](consumer/end-user-insights.md). Selecione as reticências (...) e, em seguida, escolha **Obter insights rápidos**. Quando os insights estiverem prontos, selecione **Exibir insights**.
     
    ![Relatório de Insights](media/sample-tutorial-connect-to-the-samples/power-bi-insights.png)

## <a name="samples-in-power-bi-desktop"></a>Exemplos no Power BI Desktop 
Quando você abre o arquivo de exemplo .pbix no Power BI Desktop pela primeira vez, ele é exibido no modo de exibição de relatório em que você pode explorar, criar e modificar qualquer número de páginas do relatório com visualizações. O modo de exibição de Relatório oferece praticamente a mesma experiência de design que aquela encontrada no modo de exibição Editar de um relatório no serviço Power BI. Você pode mover as visualizações de um lugar para outro, copiar e colar, mesclar, etc. 

Ao contrário da edição de um relatório no serviço do Power BI, no Power BI Desktop você também pode trabalhar com suas consultas e modelar seus dados para garantir que os dados ofereçam suporte a insights melhores em seus relatórios. Você pode, então, salvar o seu arquivo do Power BI Desktop onde quiser, seja em sua unidade local ou na nuvem.

1. Baixe o [arquivo .pbix de exemplo de Análise de Varejo](http://download.microsoft.com/download/9/6/D/96DDC2FF-2568-491D-AAFA-AFDD6F763AE3/Retail%20Analysis%20Sample%20PBIX.pbix) e abra-o no Power BI Desktop. 

    ![Exemplo no modo de exibição de relatório do Power BI](media/sample-tutorial-connect-to-the-samples/power-bi-samples-desktop.png)

1. O arquivo é aberto no modo de exibição de relatório. Observe as quatro guias na parte inferior do editor de relatório. Elas representam as quatro páginas deste relatório. Para este exemplo, a página **Novas lojas** está selecionada no momento. 

    ![Guia Novas Lojas realçada](media/sample-tutorial-connect-to-the-samples/power-bi-sample-tabs.png).

1. Para um mergulho no editor de relatórios, confira [Faça um tour do editor de relatórios](service-the-report-editor-take-a-tour.md).

## <a name="whats-in-your-report"></a>O que há em seu relatório?
Ao baixar um arquivo .pbix de exemplo, você baixou não apenas um relatório, mas também o *conjunto de dados subjacente*. Quando você abre o arquivo, o Power BI Desktop carrega os dados com suas consultas e relacionamentos associados. Você pode exibir os dados e os relacionamentos subjacentes, mas não pode exibir as consultas subjacentes no Editor de Consultas.


1. Alterne para [Exibição de Dados](desktop-data-view.md) selecionando o ícone de tabela ![ícone de tabela](media/sample-tutorial-connect-to-the-samples/power-bi-data-icon.png).
 
    ![Exibição de dados da área de trabalho](media/sample-tutorial-connect-to-the-samples/power-bi-desktop-sample-data.png)

    Na Exibição de dados, você pode inspecionar, explorar e entender os dados em seu modelo do Power BI Desktop. É diferente do modo como você exibe tabelas, colunas e dados no Editor de Consultas. Os dados na exibição de dados já estão carregados no modelo.

    Quando você está modelando seus dados, às vezes deseja ver o que realmente está nas linhas e colunas de uma tabela sem criar um visual na tela do relatório. Isso é especialmente verdadeiro quando você está criando colunas calculadas e medidas, ou quando você precisa identificar um tipo de dados ou uma categoria de dados.

1. Alterne para a [exibição de Relacionamentos](desktop-relationship-view.md) selecionando o ícone a seguir: ![Ícone de exibição de relacionamento](media/sample-tutorial-connect-to-the-samples/power-bi-desktop-relationship-icon.png).
 
    ![Exibição de relações no Power BI Desktop](media/sample-tutorial-connect-to-the-samples/power-bi-relationships.png)

    A Exibição de Relações mostra todas as tabelas, colunas e relações em seu modelo. Aqui você pode exibir, alterar e criar relações.

## <a name="next-steps"></a>Próximas etapas
Esse ambiente é seguro para teste, pois você pode optar por não salvar as alterações. Mas se você salvá-las, sempre é possível selecionar **Obter Dados** para ter uma nova cópia deste exemplo.

Esperamos que este tour tenha mostrado como os painéis, conjuntos de dados, relacionamentos e relatórios do Power BI podem fornecer informações sobre os dados de exemplo. Agora é sua vez – conecte-se aos seus próprios dados. Com o Power BI, é possível se conectar a uma grande variedade de fontes de dados. Para saber mais, confira [Introdução ao serviço do Power BI](service-get-started.md) e [Introdução ao Power BI Desktop](desktop-getting-started.md).  

Para obter mais informações, veja:  
- [Conceitos básicos para designers no serviço do Power BI](service-basic-concepts.md)
- [Exemplos para o serviço do Power BI](sample-datasets.md)
- [Fontes de dados do Power BI](service-get-data.md)

Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)
