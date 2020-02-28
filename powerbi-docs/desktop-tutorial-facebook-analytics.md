---
title: 'Tutorial: Analisar dados do Facebook usando o Power BI Desktop'
description: Aprenda a importar dados do Facebook e usá-los no Power BI Desktop.
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: tutorial
ms.date: 01/23/2020
ms.author: davidi
LocalizationGroup: Learn more
ms.openlocfilehash: 1f5cedba1c32f152cd6e4a9f9f51d0355ac05ce5
ms.sourcegitcommit: f9909731ff5b6b69cdc58e9abf2025b7dee0e536
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77497273"
---
# <a name="tutorial-analyze-facebook-data-by-using-power-bi-desktop"></a>Tutorial: Analisar dados do Facebook usando o Power BI Desktop

Neste tutorial, você aprenderá a importar dados do Facebook e usá-los no Power BI Desktop. Você vai se conectar e importar dados da página do Facebook do Power BI, aplicará transformações aos dados importados e usará os dados nas visualizações do relatório.

> [!WARNING]
> Devido às restrições de permissão do Aplicativo Facebook, os recursos do conector descritos neste artigo não estão funcionando corretamente. Estamos trabalhando com o Facebook para retornar essa funcionalidade o quanto antes.


## <a name="connect-to-a-facebook-page"></a>Conectar-se a uma página do Facebook

Este tutorial usa dados da [página do Facebook do Microsoft Power BI](https://www.facebook.com/microsoftbi). Você não precisa de credenciais especiais para se conectar e importar dados dessa página, com exceção de uma conta pessoal do Facebook.

1. Abra o Power BI Desktop e selecione **Obter dados** na caixa de diálogo **Introdução** ou, na guia de faixa de opções **Página Inicial**, selecione **Obter Dados** e, em seguida, selecione **Mais**.
   
2. Na caixa de diálogo **Obter Dados**, selecione **Facebook** no grupo **Serviços Online** e, em seguida, selecione **Conectar**.
   
   ![Obter dados](media/desktop-tutorial-facebook-analytics/t_fb_getdataother.png)
   
   Surge uma caixa de diálogo para alertar você sobre os riscos de uso de um serviço de terceiros.
   
   ![Aviso de terceiros](media/desktop-tutorial-facebook-analytics/t_fb_connectingtotps.png)
   
3. Selecione **Continuar**. 
   
4. Na caixa de diálogo **Facebook**, insira o nome da página **microsoftbi** como o **nome de usuário**, selecione **Postagens** na lista suspensa **Conexão** e, em seguida, selecione **OK**.
   
   ![Conectar](media/desktop-tutorial-facebook-analytics/2.png)
   
5. Quando receber a solicitação para inserir credenciais, entre em sua conta do Facebook e permita acesso ao Power BI à sua conta.
   
   ![Credenciais](media/desktop-tutorial-facebook-analytics/facebookcredentials.png)

   Após a conexão com a página do Power BI no Facebook, você obterá uma visualização dos dados de postagens da página. 
   
   ![Visualização dos dados](media/desktop-tutorial-facebook-analytics/t_fb_1-loadpreview.png)
   
## <a name="shape-and-transform-the-imported-data"></a>Formatar e transformar os dados importados

Vamos supor que você quer ver e mostrar quais postagens têm mais comentários ao longo do tempo, mas percebe na visualização de dados de postagens que os dados de **created_time** estão difíceis de serem lidos e compreendidos, e não há dados de comentários. Para aproveitá-los ao máximo, formate e limpe os dados. Para fazer isso, você pode usar o Editor do Power Query do Power BI Desktop para editar os dados, antes ou depois de importá-los para o Power BI Desktop. 

### <a name="split-the-datetime-column"></a>Dividir a coluna de data e hora

Primeiro, separe os valores de data e hora na coluna **created_time** para facilitar a leitura. 

1. Na visualização de dados do Facebook, selecione **Editar**. 
   
   ![Edição da visualização dos dados](media/desktop-tutorial-facebook-analytics/t_fb_1-editpreview.png)
   
   O Editor do Power Query do Power BI Desktop é aberto em uma nova janela e exibe a visualização de dados da página do Power BI no Facebook. 
   
   ![Editor do Power Query](media/desktop-tutorial-facebook-analytics/t_fb_1-intoqueryeditor.png)
   
2. Selecione a coluna **created_time**. Observe que ela é um tipo de dados **Texto**, conforme indicado por um ícone **ABC** no cabeçalho da coluna. Clique com o botão direito do mouse no cabeçalho e selecione **Dividir Coluna** > **Por Delimitador** na lista suspensa. Ou selecione **Dividir Coluna** > **Por Delimitador** no grupo **Transformar** na guia **Página Inicial** da faixa de opções.  
   
   ![Dividir coluna por delimitador](media/desktop-tutorial-facebook-analytics/delimiter1.png)
   
3. Na caixa de diálogo **Dividir Coluna por Delimitador**, selecione **Personalizado** no menu suspenso, insira **T** (o caractere que inicia a parte de hora dos valores **created_time**) no campo de entrada e selecione **OK**. 
   
   ![Caixa de diálogo Dividir Coluna por Delimitador](media/desktop-tutorial-facebook-analytics/delimiter2.png)
   
   A coluna se divide em duas contendo as cadeias de caracteres antes e depois do delimitador *T*. As novas colunas são chamadas **created_time.1** e **created_time.2**, respectivamente. O Power BI detectou e alterou automaticamente os tipos de dados para **Data** na primeira coluna e **Hora** na segunda e formatou os valores de data e hora para facilitar a leitura.
   
4. Renomeie as duas colunas. Selecione a coluna **created_time.1** e, em seguida, **Renomear** no grupo **Qualquer Coluna** da guia **Transformar** na faixa de opções. Ou clique duas vezes no cabeçalho da coluna e insira o nome da nova coluna, **created_date**. Repita para a coluna **created_time.2** e renomeie-a para **created_time**.
   
   ![Novas colunas de data e hora](media/desktop-tutorial-facebook-analytics/delimiter3.png)
   
### <a name="expand-the-nested-column"></a>Expandir a coluna aninhada

Agora que os dados de data e hora estão como você quer, você pode expor os dados de comentários expandindo uma coluna aninhada. 

1. Selecione o ícone ![ícone de expansão](media/desktop-tutorial-facebook-analytics/14.png) na parte superior da coluna **object_link** para abrir a caixa de diálogo **Expandir/Agregar**. Selecione **connections** e depois **OK**. 
   
   ![Expandir object_link](media/desktop-tutorial-facebook-analytics/expand1.png)
   
   O título da coluna muda para **object_link.connections**.
2. Selecione o ![ícone de expansão](media/desktop-tutorial-facebook-analytics/14.png) na parte superior da coluna **object_link.connections**, selecione **comments** e depois **OK**. O título da coluna muda para **object_link.connections.comments**.
   
3. Selecione o ![ícone de expansão](media/desktop-tutorial-facebook-analytics/14.png) na parte superior da coluna **object_link.connections.comments** e desta vez selecione **Agregar**, em vez de **Expandir**, na caixa de diálogo. Selecione **Nº de Contagem de id** e depois **OK**. 
   
   ![Agregar comentários](media/desktop-tutorial-facebook-analytics/expand2.png)
   
   Agora, a coluna exibe o número de comentários para cada mensagem. 
   
4. Renomeie a coluna **Contagem de object_link.connections.comments.id** para **Número de comentários**.
   
5. Selecione a seta para baixo ao lado do cabeçalho de coluna **Número de comentários** e selecione **Classificar em Ordem Decrescente** para ver as Postagens com mais comentários primeiro. 
   
   ![Comentários por mensagem](media/desktop-tutorial-facebook-analytics/data-fixed.png)
   
### <a name="review-query-steps"></a>Rever as etapas de consulta

À medida que você formata e transforma os dados no **Editor do Power Query**, cada etapa é registrada na área **Etapas Aplicadas** do painel **Config. Consulta** no lado direito da janela do Editor do Power Query. Você pode retornar às **Etapas Aplicadas** para ver exatamente quais alterações você fez e editá-las, excluí-las ou reorganizá-las, se necessário. Tenha cuidado ao modificar essas etapas, pois alterar as etapas anteriores pode corromper as etapas posteriores. 

Depois de aplicar todas as transformações de dados, as **Etapas Aplicadas** devem ser exibidas como o seguinte:
   
   ![Etapas Aplicadas](media/desktop-tutorial-facebook-analytics/applied-steps.png)
   
   >[!TIP]
   >As **Etapas Aplicadas** são formadas por fórmulas escritas na [linguagem de fórmula M do Power Query](https://docs.microsoft.com/powerquery-m/quick-tour-of-the-power-query-m-formula-language). Para ver e editar as fórmulas, selecione **Editor Avançado** no grupo **Consulta** da guia **Página Inicial** da faixa de opções. 

### <a name="import-the-transformed-data"></a>Importar os dados transformados

Quando você estiver satisfeito com os dados, selecione **Fechar e Aplicar** > **Fechar e Aplicar** na guia **Página Inicial** da faixa de opções para importá-los no Power BI Desktop. 
   
   ![Fechar e Aplicar](media/desktop-tutorial-facebook-analytics/t_fb_1-loadandclose.png)
   
   Uma caixa de diálogo exibe o progresso do carregamento dos dados no modelo de dados do Power BI Desktop. 
   
   ![Carregar dados](media/desktop-tutorial-facebook-analytics/t_fb_1-loading.png)
   
   Após o carregamento dos dados, eles aparecerão na exibição **Relatório** como nova consulta no painel **Campos**.
   
   ![Nova consulta](media/desktop-tutorial-facebook-analytics/fb-newquery.png)
   
## <a name="use-the-data-in-report-visualizations"></a>Usar os dados nas visualizações de relatório 

Agora que você importou os dados da página do Facebook, conseguirá obter informações sobre seus dados de forma ágil e fácil usando as visualizações. Criar uma visualização é fácil. Basta selecionar um campo ou arrastá-lo do painel **Campos** para a tela do relatório.

### <a name="create-a-bar-chart"></a>Criar um gráfico de barras

1. Na exibição **Relatório** do Power BI Desktop, selecione **mensagem** no painel **Campos** ou arraste-o para a tela do relatório. Uma tabela com todas as mensagens de postagem é exibida na tela. 
   
   ![Nova consulta](media/desktop-tutorial-facebook-analytics/table-viz.png)
   
2. Com a tabela selecionada, selecione também **Número de comentários** no painel **Campos** ou arraste-o para a tabela. 
   
3. Selecione o ícone **Gráfico de barras empilhadas** no painel **Visualizações**. A tabela muda para um gráfico de barras mostrando o número de comentários por postagem. 
   
   ![Gráfico de barras](media/desktop-tutorial-facebook-analytics/barchart1.png)
   
4. Selecione **Mais opções** (...) ao lado da visualização e, em seguida, selecione **Classificar por** > **Número de comentários** para classificar a tabela por número decrescente de comentários. 

   Repare que a maioria dos comentários foi associada a mensagens **(Em branco)** (essas postagens podem ter sido histórias, links, vídeos ou outro conteúdo que não era texto). 
   
5. Para filtrar as linhas em branco, selecione **a mensagem é (Tudo)** no painel **Filtros**, selecione **Selecionar tudo** e selecione **(Em branco)** para cancelar a seleção. 

   A entrada do painel **Filtros** muda para **a mensagem não está (Em branco)** e a linha **(Em branco)** desaparece da visualização do gráfico.
   
   ![Filtrar linha em branco](media/desktop-tutorial-facebook-analytics/barchart3.png)
   
### <a name="format-the-chart"></a>Formatar o gráfico

A visualização está ficando mais interessante, mas não dá para ver muito do texto da postagem no gráfico. Para mostrar mais do texto da postagem:

1. Use as alças na visualização do gráfico para redimensioná-lo até o tamanho máximo. 
   
2. Com o gráfico selecionado, selecione o ícone **Formatar** (rolo de pintura) no painel **Visualizações**.
   
3. Selecione a seta para baixo ao lado de **eixo Y** e arraste o controle deslizante **Tamanho máximo** totalmente para a direita (**50%** ). 
4. Reduza o **Tamanho do texto** para **10**, para caber mais texto.
   
   ![Alterações de formatação](media/desktop-tutorial-facebook-analytics/barchart4.png)
   
   Agora, o gráfico mostra mais conteúdo da postagem. 
   
   ![Mostrar mais postagens](media/desktop-tutorial-facebook-analytics/barchart5.png)
   
O eixo X (número de comentários) do gráfico não mostra os valores exatos, e a parte de baixo do gráfico parece uma bagunça. Vamos usar os rótulos de dados: 

1. Selecione o ícone **Formatar** e defina o controle deslizante do **eixo X** como **Desativado**. 
   
2. Selecione o controle deslizante **Rótulos de dados** para **Ativado**. 

   Agora o gráfico mostra o número exato de comentários para cada postagem.
   
   ![Aplicar rótulos de dados](media/desktop-tutorial-facebook-analytics/barchart6.png)
   
### <a name="edit-the-data-type"></a>Editar o tipo de dados

Muito melhor, mas todos os rótulos de dados têm uma casa decimal **,0**, o que é perturbador e enganoso, já que **Número de postagens** deve ser um número inteiro. Para corrigi-los, você precisa alterar o tipo de dados da coluna **Número de postagens** para **Número Inteiro**:

1. Clique com o botão direito do mouse em **Query1** no painel **Campos** ou passe o mouse sobre ele e selecione **Mais opções** (...). 

2. No menu de contexto, selecione **Editar consulta**. Ou selecione **Editar Consultas** > **Editar Consultas** no grupo **Dados externos** da guia **Página Inicial** na faixa de opções. 
   
3. Na janela **Editor do Power Query**, selecione a coluna **Número de comentários** e altere o tipo de dados seguindo uma destas etapas: 
   - Selecione o ícone **1.2** ao lado do cabeçalho da coluna **Número de comentários** e selecione **Número inteiro** na lista suspensa
   - Clique com o botão direito do mouse no cabeçalho da coluna e, em seguida, selecione **Alterar Tipo** > **Número Inteiro**.
   - Selecione **Tipo de dados: Número Decimal** no grupo **Transformar** da guia **Página Inicial** ou no grupo **Qualquer Coluna** da guia **Transformar** e, em seguida, selecione **Número Inteiro**.
   
   O ícone no cabeçalho da coluna muda para **123**, indicando um tipo de dados de **Número Inteiro**.
   
   ![Alterar tipo de dados](media/desktop-tutorial-facebook-analytics/change-datatype.png)
   
3. Para aplicar as alterações, selecione **Arquivo** > **Fechar e Aplicar** ou **Arquivo** > **Aplicar** para manter a janela do **Editor do Power Query** aberta. 

   Após o carregamento das alterações, os rótulos de dados no gráfico se tornarão números inteiros.
   
   ![Gráfico com números inteiros](media/desktop-tutorial-facebook-analytics/vis-3.png)
   
### <a name="create-a-date-slicer"></a>Criar uma segmentação de dados de data

Vamos supor que você quer visualizar a quantidade de comentários em postagens ao longo do tempo. É possível criar uma visualização de segmentação de dados para filtrar os dados do gráfico de acordo com períodos diferentes. 

1. Selecione uma área em branco da tela e selecione o ícone de **Segmentação de dados** no painel **Visualizações**. 

   Uma visualização de segmentação de dados em branco é exibida.
   
   ![Selecionar o ícone de segmentação de dados](media/desktop-tutorial-facebook-analytics/slicer1.png)
   
2. Selecione o campo **created_date** no painel **Campos** ou arraste-o até a nova segmentação de dados. 

   A segmentação de dados muda para um controle deslizante de intervalo de datas, com base no tipo de dados **Data** do campo.
   
   ![Segmentação de controle deslizante de intervalo de datas](media/desktop-tutorial-facebook-analytics/slicer2.png)
   
3. Mova as alças do controle deslizante para selecionar intervalos de datas diferentes e observe a filtragem resultante dos dados do gráfico. Também é possível selecionar os campos de data na segmentação de dados e digitar datas específicas, ou escolhê-las em um calendário pop-up.
    
   ![Segmentar os dados](media/desktop-tutorial-facebook-analytics/slicer3.png)
   
### <a name="format-the-visualizations"></a>Formatar as visualizações

Dê ao gráfico um título mais descritivo e atrativo: 

1. com o gráfico selecionado, selecione o ícone **Formatar** no painel **Visualizações** e, em seguida, selecione a seta suspensa ao lado de **Título** para expandi-lo.

2. Altere o **Texto do título** para **Comentários por postagem**. 

3. Selecione a seta suspensa ao lado de **Cor da fonte** e selecione uma cor verde para corresponder às barras verdes da visualização.

4. Aumente o **Tamanho do texto** para **10 pt** e altere a **Família de fontes** para **Segoe (Bold)** .

5. Experimente outras opções e configurações de formatação para mudar a aparência de suas visualizações. 

   ![Visualizações](media/desktop-tutorial-facebook-analytics/vis-1.png)

## <a name="create-more-visualizations"></a>Criar mais visualizações

Como você pode ver, é fácil personalizar visualizações em seu relatório para apresentar os dados como você quer. Por exemplo, tente usar os dados importados do Facebook para criar este gráfico de linhas mostrando o número de comentários ao longo do tempo.

![Gráfico de linhas](media/desktop-tutorial-facebook-analytics/moreviz.png)

O Power BI Desktop fornece uma experiência perfeita de ponta a ponta, desde a obtenção de dados por meio de uma ampla variedade de fontes de dados e a modelagem desses dados para atender às suas necessidades de análise, até a visualização de tais dados de maneiras avançadas e interativas. Quando seu relatório estiver pronto, você poderá [carregá-lo no serviço do Power BI](desktop-upload-desktop-files.md) e criar dashboards baseados nele para compartilhar com outros usuários do Power BI.

## <a name="next-steps"></a>Próximas etapas
* [Leia outros tutoriais do Power BI Desktop](https://go.microsoft.com/fwlink/?LinkID=521937)
* [Assista a vídeos do Power BI Desktop](https://go.microsoft.com/fwlink/?LinkID=519322)
* [Visite o Fórum do Power BI](https://go.microsoft.com/fwlink/?LinkID=519326)
* [Leia o Blog do Power BI](https://go.microsoft.com/fwlink/?LinkID=519327)

