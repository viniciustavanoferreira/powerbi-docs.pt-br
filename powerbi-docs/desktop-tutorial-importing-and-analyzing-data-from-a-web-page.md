---
title: 'Tutorial: Importar e analisar os dados de uma página da Web'
description: 'Tutorial: Importar e analisar dados de uma página da Web com o Power BI Desktop'
author: davidiseminger
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: tutorial
ms.date: 01/13/2020
ms.author: davidi
LocalizationGroup: Learn more
ms.openlocfilehash: ef1d72754d7f77d7cb3c835c1a2b94e0f7e324f4
ms.sourcegitcommit: 0ae9328e7b35799d5d9613a6d79d2f86f53d9ab0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/16/2020
ms.locfileid: "76039353"
---
# <a name="tutorial-analyze-webpage-data-by-using-power-bi-desktop"></a>Tutorial: Analisar dados de uma página da Web com o Power BI Desktop

Como fã de futebol de longa data, você deseja criar um relatório dos vencedores da relatar os vencedores Campeonato Europeu da UEFA (Eurocopa) ao longo dos anos. Com o Power BI Desktop, você pode importar esses dados de uma página da Web para um relatório e criar visualizações que mostram os dados. Neste tutorial, você aprenderá a usar o Power BI Desktop para:

- Conectar-se a uma fonte de dados da Web e navegar entre as tabelas disponíveis.
- Formatar e transformar dados no Editor do Power Query.
- Nomear uma consulta e importá-la em um relatório do Power BI Desktop.
- Criar e personalizar um mapa e uma visualização de gráfico de pizza.

## <a name="connect-to-a-web-data-source"></a>Conectar-se a uma fonte de dados da Web

Você pode obter os dados dos vencedores da UEFA na tabela de resultados da página do Campeonato Europeu de Futebol na Wikipédia, em https://en.wikipedia.org/wiki/UEFA_European_Football_Championship. 

![Tabela de resultados da Wikipédia](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage1.png)

As conexões Web são estabelecidas usando apenas a autenticação básica. Os sites da Web que exigem autenticação podem não funcionar corretamente com o conector da Web.

Para importar os dados:

1. Na guia de faixa de opções **Início** do Power BI Desktop, clique na seta suspensa ao lado de **Obter Dados** e, em seguida, selecione **Web**.

   ![Faixa de opções Obter Dados de](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/get-data-web3.png) 

   >[!NOTE]
   >Também é possível selecionar o próprio item **Obter Dados** ou, ainda, selecionar **Obter Dados** na caixa de diálogo de introdução do Power BI Desktop e, em seguida, selecionar **Web** na seção **Todos** ou **Outros** da caixa de diálogo **Obter Dados** e selecionar **Conectar**.

1. Na caixa de diálogo **Da Web**, cole a URL `https://en.wikipedia.org/wiki/UEFA_European_Football_Championship` na caixa de texto **URL** e, em seguida, selecione **OK**.

    ![Caixa de diálogo Obter Dados de](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/get-data-web2.png)

   Depois de se conectar à página da Web da Wikipédia, a caixa de diálogo **Navegador** mostra uma lista de tabelas disponíveis na página. Você pode selecionar qualquer um dos nomes de tabela para visualizar seus dados. A tabela **Resultados[editar]** tem os dados desejados, embora não estejam exatamente na forma que você quer. Você reformatará e limpará os dados antes de carregá-los em seu relatório.

   ![Caixa de diálogo Navegador](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/tutorialimanaly_navigator.png)

   >[!NOTE]
   >O painel **Visualização** mostra a tabela mais recente selecionada, mas todas as tabelas selecionadas serão carregadas no Editor do Power Query quando você selecionar **Transformar Dados** ou **Carregar**.

1. Selecione a tabela **Resultados[editar]** na lista do **Navegador** e, em seguida, selecione **Transformar Dados**.

   Uma visualização da tabela é aberta no **Editor do Power Query**, na qual é possível aplicar transformações para limpar os dados.

   ![Editor do Power Query](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage3.png)

## <a name="shape-data-in-power-query-editor"></a>Formatar dados no Power Query Editor

Você quer tornar os dados mais fáceis de examinar exibindo apenas os anos e os países que venceram. Você pode usar o Editor do Power Query para executar essas etapas de formatação e limpeza de dados.

Primeiro, remova todas as colunas da tabela com exceção de duas. Renomeie essas colunas como *Ano* e *País* mais tarde no processo.

1. Na grade do **Editor do Power Query**, selecione as colunas. Segure Ctrl para selecionar vários itens.

1. Clique com o botão direito e selecione **Remover Outras Colunas** ou selecione **Remover Colunas** > **Remover Outras Colunas** no grupo **Gerenciar Colunas** na guia de faixa de opções **Página Inicial** para remover todas as outras colunas da tabela.

   ![Menu suspenso de Remover outras colunas](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/get-data-web6.png)

   ou

   ![Faixa de opções Remover Outras Colunas](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage4.png)

Em seguida, remova a palavra extra *Details* das células da primeira coluna.

1. Selecione a primeira coluna.

1. Clique com o botão direito do mouse e selecione **Substituir Valores** ou selecione **Substituir Valores** do grupo **Transformar** na guia **Página Inicial** da faixa de opções. Essa opção também pode ser encontrada no grupo **Qualquer Coluna** na guia **Transformar**.

   ![Menu suspenso de Substituir Valores](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/get-data-web7.png) 

   ou

   ![Faixa de opções Substituir Valores](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/get-data-web8a.png)

1. Na caixa de diálogo **Substituir Valores**, digite **Detalhes** na caixa de texto **Valor a Localizar**, deixe a caixa de texto **Substituir Por** vazia e, depois, selecione **OK** para excluir a palavra *Details* dessa coluna.

   ![Remover uma palavra da coluna](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage6.png)

Algumas células contêm apenas a palavra "Ano" em vez dos valores de ano. Você pode filtrar a coluna para exibir apenas linhas que não contêm a palavra "Ano".

1. Selecione a seta suspensa de filtro na coluna.

1. No menu suspenso, role para baixo e desmarque a caixa de seleção ao lado da opção **Ano** e, depois, selecione **OK**.

   ![Filtrar dados](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage7.png)

Como você está apenas observando os dados dos vencedores finais, pode renomear a segunda coluna como **País**. Para renomear a coluna:

1. Clique duas vezes ou toque e segure o cabeçalho da segunda coluna, ou
   - Clique com botão direito no cabeçalho da coluna e selecione **Renomear**, ou
   - Selecione a *coluna e selecione **Renomear** no grupo **Qualquer Coluna** na guia **Transformar** da faixa de opções.

   ![Menu suspenso de Renomear](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage7a.png) 
  
   ou

   ![Faixa de opções Renomear](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/get-data-web8.png)

1. Digite **Country** no cabeçalho e pressione **Enter** para renomear a coluna.

Você também deseja filtrar linhas como "2020", que têm valores nulos na coluna **País**. Você pode usar o menu de filtragem, como você fez com os valores de **Year** ou pode:

1. Clicar com o botão direito do mouse na célula **Country** na linha **2020**, que tem o valor *nulo*.

1. Selecione **Filtros de Texto** > **Não é igual a** no menu de contexto para remover qualquer linha que contiver o valor da célula.

   ![Filtro de texto](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/get-data-web11.png)

## <a name="import-the-query-into-report-view"></a>Importar a consulta para a Exibição de Relatório

Agora que formatou os dados da maneira desejada, você está pronto para nomear sua consulta "Euro Cup Winners" e importá-la para seu relatório.

1. No painel **Configurações de Consulta** , na caixa de texto **Nome** , digite **Vencedores da Eurocopa**.

   ![Nomear a consulta](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage8.png)

1. Selecione **Fechar e Aplicar** > **Fechar e Aplicar** na guia **Início** da faixa de opções.

   ![Fechar e Aplicar](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage9.png)

A consulta é carregada na exibição de *Relatório* do Power BI Desktop, podendo ser vista no painel **Campos**.

   ![Painel Campos](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage11.png)

>[!TIP]
>Você sempre pode voltar ao Editor do Power Query para editar e refinar sua consulta:
>- Selecionando as reticências ( **...** ) de **Mais opções** ao lado de **Euro Cup Winners** no painel **Campos** e selecionando **Editar Consulta**, ou
>- Selecionando **Editar Consultas** > **Editar Consultas** no grupo **Dados externos** da guia de faixa de opções **Início** na Exibição de Relatório. 

## <a name="create-a-visualization"></a>Criar uma visualização

Para criar uma visualização com base em seus dados:

1. Selecione o campo **Country** no painel **Campos** ou arraste-o para a tela de relatório. O Power BI Desktop reconhece os dados como nomes de países e cria automaticamente uma visualização de **Mapa**.

   ![Visualização de mapa](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/get-data-web14.png)

1. Amplie o mapa arrastando as alças nos cantos para que os nomes de todos os países vencedores fiquem visíveis.  

   ![Ampliar o mapa](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage14.png)

1. O mapa mostra pontos de dados idênticos para todos os países que venceram um torneio da Eurocopa. Para fazer com que o tamanho de cada ponto de dados reflita a frequência com que o país venceu, arraste o campo **Year** para **Arrastar os campos de dados aqui** em **Tamanho** na parte inferior do painel **Visualizações**. O campo é alterado automaticamente para uma medida de **Contagem de Anos** e a visualização de mapa agora mostra pontos de dados maiores para os países que venceram mais torneios.

   ![Arrastar a Contagem de Anos para Tamanho](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage15.png)

## <a name="customize-the-visualization"></a>Personalizar a visualização

Como você pode ver, é muito fácil criar visualizações com base em seus dados. Também é fácil personalizar suas visualizações para apresentar melhor os dados das maneiras que você deseja.

### <a name="format-the-map"></a>Formatar o mapa

Você pode alterar a aparência de uma visualização selecionando-a e, em seguida, selecionando o ícone de **Formato** (rolete de pintura) no painel **Visualizações**. Por exemplo, os pontos de dados "Alemanha" na visualização podem ser enganosos, porque a Alemanha Ocidental venceu dois torneios e a Alemanha venceu um, e o mapa sobrepõe os dois pontos em vez de separá-los ou uni-los. Você pode colorir esses dois pontos de forma diferente para realçar esse fato. Você também pode optar por dar ao mapa um título mais descritivo e atrativo.

1. Com a visualização selecionada, selecione o ícone **Formato** e, em seguida, selecione **Cores dos dados** para expandir as opções de cores de dados.

   ![Formatar cores de dados](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/get-data-web15.png)

1. Defina **Mostrar Tudo** como **Ativado** e, em seguida, selecione o menu suspenso próximo a **Alemanha Ocidental** e escolha a cor amarela.

   ![Alterar cor](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/get-data-web16.png)

1. Selecione **Título** para expandir as opções de título e, no campo **Texto do título**, digite **Euro Cup Winners** no lugar do título atual.

1. Altere a **Cor da fonte** para vermelho, o **Tamanho do texto** para **12** e a **Família de fontes** para **Segoe (Negrito)** .

   ![Formatar cores de dados](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/get-data-web17.png)

Agora, sua visualização de mapa é semelhante ao seguinte:

![Visualização de mapa formatada](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/get-data-web18.png)

### <a name="change-the-visualization-type"></a>Altere o tipo de visualização

É possível alterar o tipo de uma visualização selecionando-a e, em seguida, selecionando um ícone diferente na parte superior do painel **Visualizações**. Por exemplo, sua visualização de mapa não tem os dados da União Soviética e da Tchecoslováquia, porque esses países não existem mais no mapa do mundo. Outro tipo de visualização, como um gráfico de pizza ou de mapa de árvore, pode ser mais precisa, porque mostra todos os valores.

Para alterar o mapa para um gráfico de pizza, selecione-o e, em seguida, selecione o ícone **Gráfico de pizza** no painel **Visualizações**.

![Mudar a visualização para um gráfico de pizza](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/get-data-web19.png)

>[!TIP]
>- Você pode usar as opções de formatação de **Cores de dados** para deixar "Germany" e "West Germany" com a mesma cor. 
>- Para agrupar os países com mais vitórias no gráfico de pizza, selecione as reticências ( **...** ) no canto superior direito da visualização e, em seguida, selecione **Classificar por Contagem de Anos**.

O Power BI Desktop fornece uma experiência perfeita de ponta a ponta, desde a obtenção de dados por meio de uma ampla variedade de fontes de dados e a modelagem desses dados para atender às suas necessidades de análise, até a visualização de tais dados de maneiras avançadas e interativas. Quando seu relatório estiver pronto, você poderá [carregá-lo no Power BI](desktop-upload-desktop-files.md) e criar painéis baseados nele, que poderão ser compartilhados com outros usuários do Power BI.

## <a name="see-also"></a>Consulte também

* [Leia outros tutoriais do Power BI Desktop](/guided-learning/)
* [Assista a vídeos do Power BI Desktop](desktop-videos.md)
* [Visite o Fórum do Power BI](https://go.microsoft.com/fwlink/?LinkID=519326)
* [Leia o Blog do Power BI](https://go.microsoft.com/fwlink/?LinkID=519327)

