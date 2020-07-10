---
title: 'Tutorial: Introdução à criação no serviço do Power BI'
description: Introdução ao serviço online do Power BI (app.powerbi.com)
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: tutorial
ms.date: 07/02/2020
ms.author: maggies
LocalizationGroup: Get started
ms.openlocfilehash: ee3919be08cfb2af2ad0e82e9f0f35b5d13147c6
ms.sourcegitcommit: 20cfd157af587b3910a2b6deec9518dca4105d71
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/03/2020
ms.locfileid: "85943319"
---
# <a name="tutorial-get-started-creating-in-the-power-bi-service"></a>Tutorial: Introdução à criação no serviço do Power BI
Este tutorial é uma introdução a alguns dos recursos do *serviço do Power BI*. Nele, você se conecta a dados, cria um relatório e um dashboard e faz perguntas sobre seus dados. Você pode fazer muito mais com o serviço do Power BI, este tutorial é apenas uma prévia para despertar sua curiosidade. Para entender como o serviço do Power BI se adapta às outras ofertas do Power BI, recomendamos que leia [O que é Power BI](power-bi-overview.md).

Você é um *leitor* de relatório e não um criador? [Como explorar o serviço do Power BI](../consumer/end-user-experience.md) é um bom ponto de partida para você.

:::image type="content" source="media/service-get-started/power-bi-service-rearranged-dashboard.png" alt-text="Captura de tela do dashboard Exemplo Financeiro.":::

Neste tutorial, você concluirá as etapas a seguir:

> [!div class="checklist"]
> * Entrar em sua conta online do Power BI ou inscrever-se, caso ainda não tenha uma conta.
> * Abrir o serviço do Power BI.
> * Obter alguns dados e abra-os no modo de exibição de relatório.
> * Usar esses dados para criar visualizações e salvar como um relatório.
> * Criar um dashboard fixando blocos do relatório.
> * Adicionar outras visualizações ao seu dashboard usando a ferramenta de linguagem natural de P e R.
> * Redimensione, reorganize e edite detalhes dos blocos no dashboard.
> * Limpar os recursos excluindo o conjunto de dados, o relatório e o dashboard.

## <a name="sign-up-for-the-power-bi-service"></a>Inscreva-se no serviço do Power BI
Você precisa de uma licença do Power BI Pro para criar conteúdo no Power BI. Se você não tiver uma conta do Power BI, [inscreva-se para uma avaliação gratuita do Power BI Pro](https://app.powerbi.com/signupredirect?pbi_source=web) antes de começar.

## <a name="step-1-get-data"></a>Etapa 1: Obter dados

Geralmente, quando queremos criar um relatório do Power BI, começamos no Power BI Desktop. O Power BI Desktop oferece mais energia. Você pode transformar, formatar e modelar dados antes de começar a criar o relatório. Porém, desta vez, vamos começar do zero criando um relatório no serviço do Power BI.

Neste tutorial, obtemos dados de um arquivo simples do Microsoft Excel. Quer me acompanhar? [Baixar o arquivo do Exemplo Financeiro](https://go.microsoft.com/fwlink/?LinkID=521962).

1. Para começar, abra o serviço do Power BI (app.powerbi.com) em seu navegador. 

    Não tem uma conta? Sem preocupações, você pode [inscrever-se para uma avaliação gratuita do Power BI Pro](https://app.powerbi.com/signupredirect?pbi_source=web)

1. Selecione **Meu workspace** no painel de navegação.

1. Em **Meu workspace**, selecione **Novo** > **Carregar um arquivo**.

    A página **Obter Dados** é aberta.   

3. Na seção **Criar conteúdo**, verifique se **Arquivos** está selecionado e, em seguida, selecione o local em que você salvou o arquivo do Excel.
   
    :::image type="content" source="media/service-get-started/power-bi-service-get-data-local-file.png" alt-text="Captura de tela Criar conteúdo > Arquivos.":::

5. Navegue até o arquivo no seu computador e escolha **Abrir**.

5. Para este tutorial, selecionaremos **Importar** para adicionar o arquivo do Excel como um conjunto de dados, de modo que possamos usá-lo para criar relatórios e dashboards. Se você selecionar **Carregar**, a pasta de trabalho inteira do Excel será carregada no Power BI e você poderá abri-la e editá-la no Excel Online.
   
   :::image type="content" source="media/service-get-started/power-bi-import.png" alt-text="Captura de tela da escolha de Importação.":::
6. Quando seu conjunto de dados estiver pronto, selecione **Mais opções (...)** ao lado do conjunto de dados de exemplo financeiro e então selecione **Criar relatório**.
1. abrir o editor de relatório. 

    :::image type="content" source="media/service-get-started/power-bi-service-datasets.png" alt-text="Captura de tela de Todo o conteúdo > Criar relatório.":::

    A tela do relatório está em 	branco. Do lado direito estão os painéis **Filtros**, **Visualizações** e **Campos**.

    :::image type="content" source="media/service-get-started/power-bi-service-blank-report.png" alt-text="Captura de tela da tela de relatório em branco.":::

    > [!TIP]
    > Selecione o botão de navegação global no canto superior esquerdo para recolher o painel de navegação. Dessa forma, sua tela tem mais espaço.
    >
    >:::image type="content" source="media/service-get-started/power-bi-global-nav-button.png" alt-text="Botão de navegação global.":::
    >

7. No momento, você está no modo de exibição de edição. Observe a opção **Exibição de leitura** na barra de menus. 

    :::image type="content" source="media/service-get-started/power-bi-service-reading-view.png" alt-text="Captura de tela da opção de exibição de Leitura.":::

    No modo de exibição de Edição, você pode modificar relatórios, porque é o *proprietário* e o *criador* do relatório. Quando você compartilha seu relatório com colegas, geralmente eles só podem interagir com o relatório no modo de exibição de leitura. Eles são *consumidores* de relatórios em seu **Meu workspace**. 

## <a name="step-2-create-a-chart-in-a-report"></a>Etapa 2: Criar um gráfico em um relatório
Agora que você se conectou aos dados, comece a explorar. Quando você encontrar algo interessante, poderá salvá-lo na tela do relatório. Em seguida, poderá fixá-lo em um dashboard para monitorá-lo e ver como muda ao longo do tempo. Porém, primeiro o mais importantes.
    
1. No editor de relatórios, comece no painel **Campos**, do lado direito da página, para criar uma visualização. Selecione o campo **Vendas Brutas** e o campo **Data**.
   
   :::image type="content" source="media/service-get-started/power-bi-service-fields-pane-selected.png" alt-text="Captura de tela da lista Campos.":::

    O Power BI analisa os dados e cria uma visualização de gráfico de colunas. 

    > [!NOTE]
    > Se você tiver selecionado o campo **Data** primeiro, em vez de **Vendas Brutas**, verá uma tabela. Não se preocupe. Vamos alterar a visualização na próxima etapa.

    Alguns campos têm símbolos de sigma ao lado porque o Power BI detectou que eles contêm valores numéricos.

    :::image type="content" source="media/service-get-started/power-bi-sigma-fields.png" alt-text="Campos com símbolos de sigma.":::

2. Vamos mudar para um modo diferente de exibir esses dados. Gráficos de linhas são bons visuais para exibir valores ao longo do tempo. Selecione o ícone de **Gráfico de linhas** do painel **Visualizações**.
   
   :::image type="content" source="media/service-get-started/power-bi-service-select-line-chart.png" alt-text="Captura de tela do editor de Relatório com o gráfico de linhas selecionado.":::

3. Este gráfico parece interessante, então vamos *fixá-lo* em um dashboard. Focalize a visualização e selecione o ícone de alfinete.
   
   :::image type="content" source="media/service-get-started/power-bi-service-pin-visual.png" alt-text="Captura de tela do ícone de alfinete.":::

4. Como esse relatório é novo, você é solicitado a salvá-lo antes de fixar uma visualização no dashboard. Dê um nome ao relatório (como *Relatório de Exemplo Financeiro*) e escolha **Salvar**. 

    Agora, você está vendo o relatório na exibição de Leitura. 

6. Selecione o ícone **Alfinete** outra vez.
 
5. Selecione **Novo dashboard** e dê a ele o nome de *Dashboard de Exemplo Financeiro*, por exemplo. 
   
   :::image type="content" source="media/service-get-started/power-bi-pin.png" alt-text="Captura de tela do Nome do dashboard.":::
  
    Uma mensagem de êxito (perto do canto superior direito) informa que a visualização foi adicionada, como um bloco, ao dashboard.
   
    :::image type="content" source="media/service-get-started/power-bi-pin-success.png" alt-text="Captura de tela da caixa de diálogo Fixado ao dashboard.":::

    Agora que você fixou essa visualização, ela está armazenada no dashboard. Os dados permanecem atualizados para que você possa acompanhar o valor mais recente rapidamente. Porém, se você alterar o tipo de visualização no relatório, a visualização no dashboard não mudará.

7. Selecione **Ir para o dashboard** para ver o novo dashboard com o gráfico de linhas que você fixou nele como um bloco. 
   
   :::image type="content" source="media/service-get-started/power-bi-service-dashboard-tile.png" alt-text="Captura de tela do dashboard com visualização fixada.":::
   
8. Selecione o novo bloco em seu dashboard. O Power BI o leva de volta ao relatório no Modo de Exibição de Leitura.

1. Para voltar ao Modo de exibição de edição, selecione **Mais opções** (...) na barra de menus > **Editar**.

    :::image type="content" source="media/service-get-started/power-bi-service-edit-report.png" alt-text="Captura de tela de Selecionar Editar para editar o relatório.":::

    De volta ao Modo de Exibição de Edição você pode continuar a explorar e fixar blocos.

## <a name="step-3-explore-with-qa"></a>Etapa 3: Explorar com P e R

Para explorar seus dados rapidamente, tente fazer uma pergunta na caixa de P e R. P & A permite que você faça consultas em linguagem natural sobre seus dados. Em um dashboard, a caixa de P e R fica na parte superior (**Faça uma pergunta sobre seus dados**) na barra de menus. Em um relatório, está na barra de menus superior (**fazer uma pergunta**).

1. Para voltar ao dashboard, selecione **Meu workspace** na barra de cabeçalho preta do **Power BI**.

    :::image type="content" source="media/service-get-started/power-bi-service-go-my-workspace.png" alt-text="Captura de tela de Voltar para Meu workspace.":::

1. Em **Meu workspace**, selecione seu dashboard.

    :::image type="content" source="media/service-get-started/power-bi-service-dashboard-tab.png" alt-text="Captura de tela de selecionar seu dashboard.":::

1. Selecione **Fazer uma pergunta sobre seus dados**. As P e R oferecem automaticamente uma série de sugestões. 

    :::image type="content" source="media/service-get-started/power-bi-service-new-qanda.png" alt-text="Captura de tela da tela de P e R.":::

    > [!NOTE]
    > Se as sugestões não forem exibidas, ative a opção **Nova experiência de P e R**.

    :::image type="content" source="media/service-get-started/power-bi-new-qna-experience.png" alt-text="Captura de tela da ativação da nova experiência de P e R.":::

1. Algumas sugestões retornam um único valor. Por exemplo, selecione a **engrenagem qual é a média**.

    As P e R pesquisam uma resposta e a apresentam na forma de visualização de *cartão*.

3. Selecione **Fixar visual** e fixe essa visualização ao dashboard Exemplo Financeiro.

    :::image type="content" source="media/service-get-started/power-bi-qna-pin-tile.png" alt-text="Captura de tela de fixação do visual.":::

1. Volte para P e R e selecione **Mostrar todas as sugestões**.
1. Selecione **lucro total por país**. 

    :::image type="content" source="media/service-get-started/power-bi-qna-total-profit-country.png" alt-text="Captura de tela do lucro total por país.":::

1. Fixe o mapa no dashboard de Exemplo Financeiro também.

1. No dashboard, selecione o mapa que você acabou de fixar. Vê como ele abre P e R novamente? 
1. Coloque o cursor depois de *por país*, no caixa P e R e digite *como barra*. O Power BI cria um gráfico de barras com os resultados.

    :::image type="content" source="media/service-get-started/power-bi-qna-profit-country-bar.png" alt-text="Captura de tela da visualização de gráfico de barras.":::

1. Fixe o gráfico de barras em seu dashboard de Exemplo Financeiro também.

4. Selecione **Sair de P e R** para retornar ao dashboard, no qual você verá os novos blocos criados. 

   :::image type="content" source="media/service-get-started/power-bi-service-dashboard-qna.png" alt-text="Captura de tela do dashboard com visuais de P e R fixados.":::

   Você vê que, mesmo que tenha alterado o mapa para um gráfico de barras em P e R, esse bloco permaneceu como um mapa, pois era um mapa quando foi fixado. 

## <a name="step-4-reposition-tiles"></a>Etapa 4: Reposicionar blocos

Podemos reorganizar os blocos para fazer melhor uso do espaço do dashboard.

1. Arraste o canto inferior direito do bloco do gráfico de linhas *Vendas brutas* para cima, até que ele se ajuste na mesma altura que o bloco Vendas e, em seguida, solte-o.

    :::image type="content" source="media/service-get-started/power-bi-service-resize-tile.png" alt-text="Captura de tela do redimensionamento do bloco.":::

    Agora, os dois blocos têm a mesma altura.

1. Selecione **Mais opções (…)** para a média do bloco COGS > **Editar detalhes**. 

    :::image type="content" source="media/service-get-started/power-bi-tile-edit-details.png" alt-text="Captura de tela do menu Mais opções para um bloco.":::

1. Na caixa **Título**, digite *Custo Médio dos Produtos Vendidos* > **Aplicar**.

    :::image type="content" source="media/service-get-started/power-bi-tile-details-dialog.png" alt-text="Captura de tela da caixa de diálogo Editar detalhes.":::

1. Reorganize os outros visuais para ajustá-los.

    Ficou bem melhor.

    :::image type="content" source="media/service-get-started/power-bi-service-rearranged-dashboard.png" alt-text="Captura de tela do dashboard reorganizado.":::


## <a name="clean-up-resources"></a>Limpar recursos
Agora que você já concluiu o tutorial, é possível excluir o conjunto de dados, o relatório e o dashboard. 

1. Selecione **Meu workspace** na barra de cabeçalho do **Power BI** em preto.
2. Selecione **Mais opções (…)** ao lado do conjunto de dados de Exemplo Financeiro > **Excluir**.

    :::image type="content" source="media/service-get-started/power-bi-service-delete-dataset.png" alt-text="Captura de tela da exclusão do conjunto de dados.":::

    Você verá o aviso **Todos os relatórios e blocos de dashboard que contêm dados desse conjunto de dados também serão excluídos**.

4. Selecione **Excluir**.

## <a name="next-steps"></a>Próximas etapas

Melhore ainda mais a aparência dos dashboards adicionando mais blocos de visualização e [renomeando, redimensionando, vinculando e reposicionando os blocos existentes](../create-reports/service-dashboard-edit-tile.md).
