---
title: Introdução ao Power BI Desktop
description: Introdução ao Power BI Desktop.
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: how-to
ms.date: 03/13/2020
ms.author: davidi
LocalizationGroup: Get started
ms.openlocfilehash: 409771c8786fb704fbf2a882353e8e3f20ec2437
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85222189"
---
# <a name="get-started-with-power-bi-desktop"></a>Introdução ao Power BI Desktop
Bem-vindo(a) ao guia de introdução ao Power BI Desktop. Este tour mostra como o Power BI Desktop funciona, o que ele é capaz de fazer e como você pode criar modelos de dados robustos e relatórios incríveis para ampliar seu business intelligence.

Para ter uma visão geral rápida de como o Power BI Desktop funciona e como usá-lo, confira as telas neste guia em apenas alguns minutos. Para ter uma compreensão mais detalhada, você pode ler cada seção, executar as etapas e criar seu próprio arquivo do Power BI Desktop para publicá-lo no [serviço do Power BI](https://app.powerbi.com/) e compartilhá-lo com outras pessoas.

![Relatório do Power BI Desktop](media/desktop-getting-started/hero-02.png)

Você também pode assistir ao vídeo [Introdução ao Power BI Desktop](https://www.youtube.com/watch?v=Qgam9M8I0xA) e baixar a pasta de trabalho do Excel [Exemplo Financeiro](https://go.microsoft.com/fwlink/?LinkID=521962) para acompanhar o vídeo.

## <a name="how-power-bi-desktop-works"></a>Como o Power BI Desktop funciona
Com o Power BI Desktop, você pode:
1. Conectar-se a dados, incluindo várias fontes de dados.
1. Formatar os dados com consultas que criam modelos de dados atraentes e repletos de insights.
1. Usar modelos de dados para criar visualizações e relatórios. 
1. Compartilhar seus arquivos de relatório para que outras pessoas aproveitem, criem com base neles e compartilhem. Você pode compartilhar arquivos *.pbix* do Power BI Desktop como qualquer outro arquivo, mas o método mais atraente é carregá-los no [serviço do Power BI](https://preview.powerbi.com/). 

O Power BI Desktop integra tecnologias comprovadas de visualização, mecanismo de consulta e modelagem de dados da Microsoft. Analistas de dados, entre outros, podem criar coleções de consultas, conexões de dados, modelos e relatórios e compartilhá-los facilmente com outras pessoas. Com a combinação do Power BI Desktop e do serviço do Power BI, novos insights do mundo dos dados são mais fáceis de modelar, criar, compartilhar e estender.

O Power BI Desktop centraliza, simplifica e agiliza o que seria um processo árduo, disperso e desconexo de design e criação de relatórios e repositórios de business intelligence.
Pronto para experimentar? Vamos começar.

> [!NOTE]
> Para dados e relatórios que precisam permanecer no local, há uma versão separada especializada do Power BI chamada [Servidor de Relatórios do Power BI](../report-server/get-started.md). O Servidor de Relatórios do Power BI usa uma versão especializada e separada do Power BI Desktop chamada Power BI Desktop para o Servidor de Relatórios do Power BI, que funciona somente com a versão do Servidor de Relatórios do Power BI. Este artigo descreve o Power BI Desktop padrão.

## <a name="install-and-run-power-bi-desktop"></a>Instalar e executar o Power BI Desktop
Para baixar o Power BI Desktop, acesse a [página de download do Power BI Desktop](https://powerbi.microsoft.com/desktop) e selecione **download gratuito**. Ou, para ver as opções de download, selecione [Ver opções de download ou idioma](https://www.microsoft.com/download/details.aspx?id=58494). 

Você também pode baixar o Power BI Desktop do serviço do Power BI. Selecione o ícone **Baixar** na barra de menus superior e, em seguida, selecione **Power BI Desktop**.

![Baixar o Power BI Desktop do serviço do Power BI](media/desktop-getting-started/gsg_download.png)

Na página da Microsoft Store, selecione **Obter** e siga os prompts para instalar o Power BI Desktop no computador. Inicie o Power BI Desktop no menu **Iniciar** do Windows ou no ícone na barra de tarefas do Windows.

Na primeira vez em que é iniciado, o Power BI Desktop exibe a tela **Bem-vindo**.

Na tela **Bem-vindo**, você pode **Obter dados**, ver **Fontes recentes**, abrir relatórios recentes, **Abrir outros relatórios** ou selecionar outros links. Você também pode escolher se deseja sempre mostrar a tela **Bem-vindo** na inicialização. Selecione o ícone fechar para fechar a tela **Bem-vindo**.

![Tela de Boas-vindas do Power BI Desktop](media/desktop-getting-started/designer_gsg_startsplashscreen.png)

Ao longo do lado esquerdo do Power BI Desktop, há ícones referentes às três exibições Power BI Desktop: **Relatório**, **Dados**e **Relações**, de cima para baixo. A exibição atual é indicada pela barra amarela à esquerda, e você pode alterar as exibições selecionando qualquer um dos ícones. 

![Os três ícones de exibição de Power BI Desktop](media/desktop-getting-started/designer_gsg_viewtypes.png)

**Relatório** é a exibição padrão. 

![Exibição Relatório do Power BI Desktop](media/desktop-getting-started/designer_gsg_blankreport.png)

O Power BI Desktop também inclui o **Editor do Power Query**, que é aberto em uma janela separada. No **Editor do Power Query**, é possível criar consultas e transformar dados e, em seguida, carregar esse modelo de dados refinado no Power BI Desktop para criar relatórios.

## <a name="connect-to-data"></a>Conectar aos dados
Com o Power BI Desktop instalado, você está pronto para se conectar ao mundo dos dados, que está em constante expansão. Para ver os diferentes tipos de fontes de dados disponíveis, selecione **Obter Dados** > **Mais** na guia **Página Inicial** do Power BI Desktop e, na janela **Obter Dados**, percorra a lista de **Todas** as fontes de dados. Neste tour rápido, você se conecta a duas fontes de dados da **Web** diferentes.

![Selecionar fonte de dados da Web em Obter Dados ](media/desktop-getting-started/getdataweb.png)

Imagine que você seja um analista de dados que trabalha para um varejista que vende óculos. Você quer ajudar seu cliente a direcionar promoções de óculos de sol a locais onde o sol brilha com mais frequência. A página [Best and worst states for retirement](https://www.bankrate.com/retirement/best-and-worst-states-for-retirement/) (Melhores e piores lugares para aposentados) tem dados interessantes sobre esse assunto.

Na guia **Página Inicial** do Power BI Desktop, selecione **Obter Dados** > **Web** para se conectar a uma fonte de dados da Web. 

![Selecionar fonte de dados da Web](media/desktop-getting-started/gsg_syw_2.png)

Na caixa de diálogo **Da Web**, cole o endereço *https:\//www.bankrate.com/retirement/best-and-worst-states-for-retirement/* no campo **URL** e selecione **OK**. 

![Colar endereço Web na caixa de diálogo Da Web](media/desktop-getting-started/gettingstarted_8.png)

Se solicitado, na tela **Acessar Conteúdo da Web**, selecione **Conectar** para usar o acesso anônimo. 

A funcionalidade de consulta do Power BI Desktop começa a trabalhar e entra em contato com o recurso da Web. A janela **Navegador** retorna o que foi encontrado na página da Web, nesse caso, uma tabela chamada **Ranking of best and worst states for retirement**, e um documento. Você está interessado na tabela, então vamos selecioná-la para ter uma versão prévia.

Neste ponto, você pode selecionar **Carregar** para carregar a tabela ou **Transformar dados** para fazer alterações na tabela antes de carregá-la.

![Versão prévia da tabela da página da Web](media/desktop-getting-started/datasources_fromnavigatordialog.png)

Quando você seleciona **Transformar dados**, o Editor do Power Query é iniciado, com uma exibição representativa da tabela. O painel **Configurações de Consulta** está à direita, ou você sempre pode mostrá-lo selecionando **Configurações de Consulta** na guia **Exibição** do Editor do Power Query. 

![Editor do Power Query com Configurações de Consulta](media/desktop-getting-started/designer_gsg_editquery.png)

Para obter mais informações sobre como se conectar a dados, veja [Conectar-se a dados no Power BI Desktop](../connect-data/desktop-connect-to-data.md).

## <a name="shape-data"></a>Formatar dados
Agora que se conectou a uma fonte de dados, você pode ajustar os dados para que atendam às nossas necessidades. Para *formatar* dados, você fornece ao Editor do Power Query instruções passo a passo para ajustar os dados enquanto os carrega e apresenta. A formatação não afeta a fonte de dados original, apenas essa exibição específica dos dados. 

> [!NOTE]
> Os dados da tabela usados neste guia podem mudar ao longo do tempo. Deste modo, as etapas que você deve executar podem ser diferentes, exigindo que você seja criativo a respeito de como ajustar as etapas ou os resultados – e tudo isso faz parte da diversão do aprendizado. 

Formatar pode significar *transformar* dados, como renomear colunas ou tabelas, remover linhas ou colunas ou alterar tipos de dados. O Editor do Power Query captura essas etapas em sequência, em **Etapas Aplicadas** no painel **Configurações de Consulta**. Sempre que essa consulta se conecta à fonte de dados, essas etapas são executadas para que os dados sempre sejam formatados da maneira que você especificar. Esse processo ocorre sempre que você usa a consulta no Power BI Desktop, ou para qualquer pessoa que usa sua consulta compartilhada, como no serviço do Power BI. 

Observe que as **Etapas Aplicadas** nas **Configurações de Consulta** já contêm algumas etapas. Você pode selecionar cada etapa para ver seu efeito no Editor do Power Query. Primeiro, você especificou uma fonte da Web e, em seguida, exibiu a tabela na janela do **Navegador**. Na terceira etapa, **Tipo alterado**, o Power BI reconheceu dados de número inteiro ao importá-los e alterou automaticamente o **tipo de dados** original de *Texto* da Web para **Números inteiros**. 

![Painel de Configurações de Consulta com três Etapas Aplicadas](media/desktop-getting-started/designer_gsg_appliedsteps_changedtype.png)

Se você precisar alterar um tipo de dados, selecione a coluna ou as colunas a serem alteradas. Mantenha pressionada a tecla **Shift** para selecionar várias colunas adjacentes, ou **Ctrl** para selecionar colunas não adjacentes. Clique com o botão direito do mouse em um cabeçalho de coluna, selecione **Tipo de Alteração** e escolha um novo tipo de dados no menu, ou use a lista ao lado de **Tipo de Dados** no grupo **Transformar** da guia **Página Inicial** e selecione um novo tipo de dados.

![Alterar tipo de dados](media/desktop-getting-started/designer_gsg_changedatatype.png)

> [!NOTE]
> O Editor do Power Query no Power BI Desktop usa a faixa de opções ou os menus de clique com o botão direito do mouse para as tarefas disponíveis. A maioria das tarefas que você pode selecionar nas guias **Página Inicial** ou **Transformar** da faixa de opções também está disponível com um clique do botão direito do mouse em um item e a seleção no menu que é exibido.

Agora, você pode aplicar suas próprias alterações e transformações aos dados e vê-los em **Etapas Aplicadas**. 

Por exemplo, para vendas de óculos sol, você está mais interessado na classificação do clima, portanto, você decide classificar a tabela pela coluna **Clima** em vez de **Classificação geral**. Clique na seta suspensa ao lado do cabeçalho **Clima** e selecione **Classificar em ordem crescente**. Agora, os dados aparecem classificados segundo o clima e a etapa **Linhas Classificadas** aparece em **Etapas Aplicadas**. 

![Classificar linhas em ordem crescente](media/desktop-getting-started/shapecombine-changetype-b.png)

Você não está muito interessado em vender óculos de sol aos estados com os piores climas, portanto, decide removê-los da tabela. No grupo **Reduzir Linhas** da guia **Página Inicial**, selecione **Remover Linhas** > **Remover Linhas Inferiores**. Na caixa de diálogo **Remover Linhas Inferiores**, digite *10* e, em seguida, selecione **OK**. 

![Remover Linhas Inferiores](media/desktop-getting-started/pbi_gsg_getdata3.png)

As 10 linhas com os piores climas são removidas da tabela e a etapa **Linhas Inferiores Removidas** aparece em **Etapas Aplicadas**.

Você decide que a tabela tem informações extras demais, das quais você não precisa, e opta por remover as colunas **Acessibilidade**, **Crimes**, **Cultura** e **Bem-estar**. Selecione o cabeçalho de cada coluna que deseja remover. Mantenha pressionada a tecla **Shift** para selecionar várias colunas adjacentes, ou **Ctrl** para selecionar colunas não adjacentes. 

Em seguida, no grupo **Gerenciar Colunas** da guia **Página Inicial**, selecione **Remover Colunas**. Você também pode clicar com o botão direito do mouse em um dos cabeçalhos de coluna selecionados e selecionar **Remover Colunas** no menu. As colunas selecionadas são removidas e a etapa **Colunas Removidas** aparece em **Etapas Aplicadas**.

![Remover Colunas](media/desktop-getting-started/pbi_gsg_getdata3a.png)

Pensando bem, **Acessibilidade** pode ser um fator relevante para vendas de óculos de sol. Você gostaria de ter essa coluna de volta. Você pode desfazer facilmente a última etapa no painel **Etapas Aplicadas**, selecionando o ícone de exclusão **X** ao lado da etapa. Agora, refaça a etapa, selecionando apenas as colunas que deseja excluir. Para ter mais flexibilidade, você pode excluir cada coluna em uma etapa separada. 

Você pode clicar com o botão direito do mouse em qualquer etapa no painel **Etapas Aplicadas** e optar por excluí-la, renomeá-la, movê-la para cima ou para baixo na sequência, ou adicionar ou excluir etapas depois dela. Para etapas intermediárias, o Power BI Desktop avisará caso a alteração possa afetar etapas posteriores e interromper a consulta.  

![Modificar Etapas Aplicadas](media/desktop-getting-started/designer_gsg_install.png)

Por exemplo, se você não quisesse mais classificar a tabela por **Clima**, poderia tentar excluir a etapa **Linhas Classificadas**. O Power BI Desktop avisa que a exclusão dessa etapa pode fazer com que a consulta seja interrompida. Você removeu as 10 linhas inferiores depois de classificar por clima, portanto, se remover a classificação, linhas diferentes serão removidas. Você também receberá um aviso se selecionar a etapa **Linhas Classificadas** e tentar adicionar uma nova etapa intermediária nesse ponto.  

![Aviso de exclusão de etapa](media/desktop-getting-started/deletestepwarning.png)

Por fim, você altera o título da tabela para que ela faça referência a vendas de óculos de sol em vez de aposentadoria. Em **Propriedades** no painel **Configurações de Consulta**, substitua o título antigo por *Melhores estados para vendas de óculos de sol*.

A consulta concluída com seus dados formatados tem esta aparência:

![Consulta concluída](media/desktop-getting-started/shapecombine_querysettingsfinished.png)

Para obter mais informações sobre como formatar dados, confira [Formatar e combinar dados no Power BI Desktop](../connect-data/desktop-shape-and-combine-data.md).

## <a name="combine-data"></a>Combinar dados
Os dados sobre vários estados são interessantes e serão úteis para a criação de consultas e esforços de análise adicionais. Mas há um problema: a maioria dos dados usa uma abreviação de duas letras para códigos de estado, em vez de utilizar o nome completo do estado. Para usar esses dados, você precisa ter alguma maneira de associar os nomes de estado às suas abreviações.

Você está com sorte. Outra fonte de dados pública faz exatamente isso, mas os dados precisarão de uma boa quantidade de formatação antes que você possa *combiná-los* com sua tabela de óculos de sol.

Para importar os dados de abreviações de estado para o Editor do Power Query, selecione **Nova Fonte** > **Web** no grupo **Nova Consulta** na guia **Página Inicial** da faixa de opções. 

![Nova fonte](media/desktop-getting-started/pbi_gettingstartedsplash_resized.png)

Na caixa de diálogo **Da Web**, insira a URL do site de abreviações de estado: *https:\//en.wikipedia.org/wiki/List_of_U.S._state_abbreviations*.

Na janela do **Navegador**, selecione a tabela **Codes and abbreviations for U.S. states, federal district, territories, and other regions** e, em seguida, selecione **OK**. A tabela é aberta no Editor do Power Query.

Remova todas as colunas, exceto **Nome e status da região**, **Nome e status da região 2** e **ANSI**. Para manter apenas essas colunas, mantenha pressionado **Ctrl** e selecione as colunas. Em seguida, clique com o botão direito do mouse em um dos cabeçalhos de coluna e selecione **Remover Outras Colunas** ou, no grupo **Gerenciar Colunas** da guia **Página Inicial**, selecione **Remover Outras Colunas**. 

Clique na seta suspensa ao lado do cabeçalho da coluna **Nome e status da região 2** e selecione **Filtros** > **É igual a**. Na caixa de diálogo **Filtrar Linhas**, clique no campo **Inserir ou selecionar um valor** ao lado de **É igual a** e selecione **Estado**. 

Selecione **Ou** e, ao lado do segundo campo **é igual a**, selecione **State ("Commonwealth")** . Selecione **OK**. 

![Filtrar linhas](media/desktop-getting-started/filterrows.png)

Com valores extras como **Federal district** e **island** removidos, agora você tem uma lista dos 50 estados dos Estados Unidos e suas abreviações oficiais de duas letras. Você pode renomear as colunas para que façam mais sentido, por exemplo **Nome do estado**, **Status** e **Abreviação**, clicando com o botão direito do mouse nos cabeçalhos de coluna e selecionando **Renomear**.

Observe que todas essas etapas são registradas em **Etapas Aplicadas** no painel **Configurações de Consulta**.

Sua tabela formatada agora tem esta aparência:

![Tabela de códigos de estado formatada](media/desktop-getting-started/statecodes.png)

Renomeie a tabela como *Códigos de estado* no campo **Propriedades** das **Configurações de consulta**. 

Com a tabela **Códigos de estado** formatada, você pode *combinar* essas duas tabelas em uma. Como as tabelas que você tem agora são resultado de consultas aplicadas aos dados, elas também são chamadas de *consultas*. Há duas maneiras principais de combinar consultas: *mesclar* e *acrescentar*. 

Quando tem uma ou mais colunas que gostaria de adicionar a outra consulta, você *mescla* as consultas. Quando tem linhas adicionais de dados que deseja adicionar a uma consulta existente, você *acrescenta* a consulta.

Nesse caso, você deseja *mesclar* a consulta de **Códigos de estado** com a consulta **Melhores estados para óculos de sol**. Para mesclar as consultas, alterne para a consulta **Melhores estados para óculos de sol** selecionando-a no painel **Consultas** no lado esquerdo do Editor do Power Query. Em seguida, selecione **Mesclar Consultas** no grupo **Combinar** na guia **Página Inicial** da faixa de opções.

Na janela **Mesclar**, clique no campo para selecionar **Códigos de estado** entre as outras consultas disponíveis. Selecione a coluna de forma a corresponder a cada tabela, neste caso, **Estado** da consulta **Melhores estados para óculos de sol** e **Nome do estado** da consulta **Códigos de estado**. 

Se vir uma caixa de diálogo **Níveis de privacidade**, selecione **Ignorar verificações de níveis de privacidade para este arquivo** e, em seguida, selecione **Salvar**. Selecione **OK**. 

![Mesclar consultas](media/desktop-getting-started/shapecombine_merge.png)

Uma nova coluna chamada **Códigos de estado** aparece à direita da tabela **Melhores estados para óculos de sol**. Ela contém a consulta de código de estado que você mesclou com a consulta de melhores estados para vendas de óculos de sol. Todas as colunas da tabela mesclada são condensadas na coluna **Códigos de estado**. Você pode *expandir* tabela mesclada e incluir apenas as colunas desejadas. 

![Coluna de consulta mesclada](media/desktop-getting-started/mergedquery.png)

Para expandir a tabela mesclada e selecionar quais colunas incluir, selecione o ícone **Expandir** no cabeçalho da coluna. Na caixa de diálogo **Expandir**, selecione somente a coluna **Abreviação**. Desmarque **Usar nome da coluna original como prefixo** e, em seguida, selecione **OK**. 

![Escolher coluna expandida da tabela mesclada](media/desktop-getting-started/shapecombine_mergeexpand.png)

> [!NOTE]
> Você pode brincar com as maneiras de formatar a tabela **Códigos de estado**. Experimente um pouco e, se não gostar dos resultados, basta excluir essa etapa da lista **Etapas Aplicadas** no painel **Configurações de Consulta**. Você pode refazer essas ações livremente, quantas vezes desejar, até que o processo de expansão tenha a aparência desejada.

Para obter uma descrição mais completa dessas etapas de formatação e combinação de dados, veja [Formatar e combinar dados no Power BI Desktop](../connect-data/desktop-shape-and-combine-data.md).

Agora, você tem uma consulta (tabela) que combina duas fontes de dados, cada uma das quais foi formatada de acordo com nossas necessidades. Essa consulta pode servir como base para muitas conexões de dados adicionais interessantes, como dados demográficos, níveis de riqueza ou oportunidades de lazer em qualquer estado.

![Consultas formatadas e combinadas](media/desktop-getting-started/mergedcolumn.png)

Por enquanto, você tem dados suficientes para criar um relatório interessante no Power BI Desktop. Como este é um marco, aplique as alterações no **Editor do Power Query** e carregue-as no Power BI Desktop selecionando **Fechar & Aplicar** na guia **Página Inicial** da faixa de opções. Você também pode selecionar apenas **Aplicar** para manter a consulta aberta no Editor do Power Query enquanto trabalha no Power BI Desktop. 

![Fechar e aplicar alterações](media/desktop-getting-started/shapecombine_closeandapply.png)

Você pode fazer mais alterações em uma tabela depois que ela é carregada no Power BI Desktop e pode recarregar o modelo para aplicar as alterações feitas. Para reabrir o **Editor do Power Query** no Power BI Desktop, selecione **Editar Consultas** na guia **Página Inicial** da faixa de opções do Power BI Desktop. 

## <a name="build-reports"></a>Criar relatórios
Na exibição de **Relatório** do Power BI Desktop, você pode criar relatórios e visualizações. A exibição **Relatório** tem seis áreas principais:

![Exibição Relatório do Power BI Desktop](media/desktop-getting-started/designer_gsg_reportview.png)

1. A faixa de opções na parte superior, que exibe tarefas comuns associadas a relatórios e visualizações.
2. A área de tela na parte intermediária, em que as visualizações são criadas e organizadas.
3. A guia de páginas na parte inferior, que permite selecionar ou adicionar páginas de relatório.
4. O painel **Filtros**, em que é possível filtrar visualizações de dados.
5. O painel **Visualizações**, no qual você pode adicionar, alterar ou personalizar visualizações e aplicar o detalhamento.
6. O painel **Campos**, que mostra os campos disponíveis em suas consultas. Você pode arrastar esses campos para a tela, o painel **Filtros** ou o painel **Visualizações** para criar ou modificar visualizações.

Você pode expandir e recolher os painéis **Filtros**, **Visualizações** e **Campos** selecionando as setas na parte superior dos painéis. Recolher os painéis fornece mais espaço na tela para criar visualizações interessantes. 

![Expandir ou recolher painéis](media/desktop-getting-started/designer_gsg_collapsepanes.png)

Para criar uma visualização simples, basta selecionar qualquer campo na lista de campos ou arrastar o campo da lista **Campos** para a tela. Por exemplo, arraste o campo **Estado** de **Melhores estados para vendas de óculos de sol** para a tela e veja o que acontece.

![Arrastar campo de Estado para criar uma visualização de mapa](media/desktop-getting-started/designer_gsg_reportfirstdrag.png)

Veja só! O Power BI Desktop reconheceu que o campo **Estado** continha dados de localização geográfica e criou automaticamente uma visualização baseada em mapa. A visualização mostra os pontos de dados dos 40 estados de seu modelo de dados. 

O painel **Visualizações** mostra informações sobre a visualização e permite modificá-las. 

![O painel Visualização](media/desktop-getting-started/designer_gsg_visualizationtypes.png)

1. Os ícones mostram o tipo de visualização criada. Você pode alterar o tipo de uma visualização selecionada selecionando um ícone diferente ou pode criar uma visualização selecionando um ícone sem nenhuma visualização existente selecionada. 
2. A opção **Campos** no painel **Visualização** permite arrastar campos de dados para **Legenda** e para outras caixas de campo no painel. 
3. A opção **Formato** permite aplicar formatação e outros controles às visualizações. 

As opções disponíveis nas áreas **Campos** e **Formato** dependem do tipo de visualização e dos dados que você tem.

Você deseja que a visualização do mapa mostre apenas os 10 estados com melhor clima. Para mostrar apenas os 10 primeiros estados, no painel **Filtros**, passe o mouse sobre **Estado é (Todos)** e expanda a seta que aparece. Em **Tipo de filtro**, clique no menu suspenso e selecione **N Superior**. Em **Mostrar itens**, selecione **Inferior**, porque você deseja mostrar os itens com as classificações numéricas mais baixas, e digite *10* no próximo campo.

Arraste o campo **Clima** do painel **Campos** para o campo **Por valor** e, em seguida, selecione **Aplicar filtro**. 

![Filtro dos 10 com melhor clima](media/desktop-getting-started/gsg_share5.png)

Agora, você vê apenas os 10 estados com melhor clima na visualização de mapa. 

Renomeie sua visualização selecionando o ícone **Formato** no painel **Visualização**, selecionando **Título** e digitando *10 estados com melhor clima* em **Texto do título**. 

![Alterar o título](media/desktop-getting-started/designer_gsg_report1.png)

Para adicionar uma visualização que mostra os nomes dos 10 estados com melhor clima e suas classificações de 1 a 10, selecione uma área em branco da tela e, em seguida, selecione o ícone **Gráfico de colunas** no painel **Visualização**. No painel **Campos**, selecione **Estado** e **Clima**. Um gráfico de colunas mostra os 40 estados em sua consulta, da classificação numérica mais alta para a mais baixa, ou do pior para o melhor clima. 

![Visualização de gráfico de colunas](media/desktop-getting-started/gsg_share7.png)

Para alternar a ordem da classificação para que o número 1 seja exibido primeiro, selecione as reticências de **Mais opções** no canto superior direito da visualização e selecione **Classificar em ordem crescente** no menu. 

![Classificação crescente](media/desktop-getting-started/shapecombine_mergequeries.png)

Para limitar a tabela aos 10 primeiros estados, aplique o mesmo filtro de 10 últimos, como fez para a visualização de mapa. 

Renomeie a visualização da mesma maneira que fez para a visualização de mapa. Além disso, na seção **Formato** do painel **Visualização**, altere **Eixo Y** > **Título do eixo** de **Clima** para *Classificação do clima* para torná-lo mais compreensível. Em seguida, deixe o seletor do **Eixo Y** **Desativado** e deixe **Rótulos de dados** **Ativado**. 

Agora, os 10 estados com melhor clima aparecem na ordem classificada junto com suas classificações numéricas. 

![Gráfico de colunas concluídas](media/desktop-getting-started/shapecombine_changetype.png)

Você pode criar visualizações semelhantes, ou outras visualizações, para os campos **Acessibilidade** e **Classificação geral**, ou pode combinar vários campos em uma visualização. Há todos os tipos de relatórios e visualizações interessantes que você pode criar. Essas visualizações de **Tabela** e **Gráfico de colunas de linha e em cluster** mostram os 10 estados com melhor clima, juntamente com suas classificações gerais e de acessibilidade:

![Visualizações de tabela e linha e de coluna em cluster](media/desktop-getting-started/designer_gsg_report2costofliving.png)

Você pode mostrar visualizações diferentes em páginas de relatório diferentes. Para adicionar uma nova página, selecione o símbolo **+** ao lado das páginas existentes na barra de páginas ou selecione **Inserir** > **Nova Página** na guia **Página Inicial** da faixa de opções. Para renomear uma página, clique duas vezes no nome dela na barra de páginas ou clique com o botão direito do mouse e selecione **Renomear Página** e digite o novo nome. Para ir para uma página diferente do relatório, selecione a página na barra de páginas. 

![Barra de páginas](media/desktop-getting-started/pages.png)

Você pode adicionar caixas de texto, imagens e botões às páginas do relatório no grupo **Inserir** da guia **Página Inicial**. Para definir opções de formatação para visualizações, selecione uma visualização e, em seguida, selecione o ícone **Formato** no painel **Visualizações**. Para configurar tamanhos, planos de fundo e outras informações de página, selecione o ícone **Formato** sem nenhuma visualização selecionada.

Ao terminar de criar suas páginas e visualizações, selecione **Arquivo** > **Salvar** e salve o relatório. 

![Página de relatório concluído do Power BI Desktop](media/desktop-getting-started/finished-report.png)

Para obter mais informações sobre relatórios, veja [Exibição de Relatório no Power BI Desktop](../create-reports/desktop-report-view.md).

## <a name="share-your-work"></a>Compartilhar seu trabalho
Agora que tem um relatório do Power BI Desktop, você pode compartilhá-lo com outras pessoas. Existem algumas maneiras de compartilhar seu trabalho. Você pode distribuir o arquivo *.pbix* do relatório como qualquer outro arquivo, carregar o arquivo *.pbix* do serviço do Power BI ou publicar diretamente do Power BI Desktop no serviço do Power BI. Você precisa ter uma conta do Power BI para publicar ou carregar relatórios no serviço do Power BI. 

Para publicar no serviço do **Power BI** usando o Power BI Desktop, na guia **Página Inicial** da faixa de opções, selecione **Publicar**.

![Selecione Publicar](media/desktop-getting-started/gsg_syw_1.png)

Você poderá ser solicitado a entrar no Power BI ou a selecionar um destino.

Quando o processo de publicação estiver concluído, você verá a caixa de diálogo a seguir:

![Publicação no Power BI bem-sucedida](media/desktop-getting-started/gsg_syw_3.png)

Quando você seleciona o link para abrir o relatório no Power BI, seu relatório é aberto no site do Power BI em **Meu Workspace** > **Relatórios**. 

Outra maneira de compartilhar seu trabalho é carregá-lo de dentro do serviço do **Power BI** . Vá para *https:\//app.powerbi.com* para abrir o Power BI em um navegador. Em sua **Página Inicial** do Power BI, selecione **Obter dados** no canto inferior esquerdo para iniciar o processo de carregamento de seu relatório do Power BI Desktop.

![Selecione Obter dados na Página Inicial do Power BI](media/desktop-getting-started/pbi_gsg_getdata1.png)

Na página seguinte, selecione **Obter** na seção **Arquivos**.

![Obter arquivos](media/desktop-getting-started/pbi_gsg_getdata2.png)

Na página seguinte, selecione **Arquivo Local**. Navegue até o arquivo *.pbix* do Power BI Desktop e selecione-o e, em seguida, selecione **Abrir**. 

Depois que o arquivo for importado, você poderá vê-lo listado em **Meu Workspace** > **Relatórios** no painel esquerdo do serviço do Power BI.

![Arquivo do Power BI Desktop importado para o Power BI](media/desktop-getting-started/pbi_gsg_getdata4.png)

Quando você seleciona o arquivo, a primeira página do relatório é exibida. Você pode selecionar diferentes páginas nas guias à esquerda do relatório. 

É possível fazer alterações em um relatório no serviço do **Power BI** selecionando **Mais opções** > **Editar** na parte superior da tela do relatório. Para salvar suas alterações, selecione **Salvar uma cópia**.

![Editar um relatório e salvar uma cópia](media/desktop-getting-started/gsg_share4.png)

Há todos os tipos de elementos visuais interessantes que você pode criar no serviço do **Power BI** por meio do seu relatório, que você pode fixar a um *dashboard*. Para saber mais sobre dashboards no serviço do **Power BI**, confira [Dicas para criar um ótimo dashboard](../create-reports/service-dashboards-design-tips.md). Para obter mais informações sobre como criar, compartilhar e modificar dashboards, veja [Compartilhar um dashboard](../collaborate-share/service-share-dashboards.md).

Para compartilhar um relatório ou dashboard, selecione **Compartilhar** na parte superior da página abrir relatório ou dashboard, ou selecione o ícone **Compartilhar** ao lado do nome do relatório ou dashboard nas listas **Meu Workspace** > **Relatórios** ou **Meu Workspace** > **Dashboards**.

Preencha a tela **Compartilhar relatório** ou **Compartilhar dashboard** para enviar um email ou obter um link para compartilhar seu relatório ou dashboard com outras pessoas. 

![Compartilhar relatório](media/desktop-getting-started/gsg_share6.png)

Há muitas combinações e visualizações atraentes relacionadas a dados que você pode criar com o Power BI Desktop e com o serviço do Power BI. 

## <a name="next-steps"></a>Próximas etapas
O Power BI Desktop dá suporte à conexão a uma porta de diagnóstico. A porta de diagnóstico permite que outras ferramentas se conectem e executem rastreamentos para fins de diagnóstico. Ao usar a porta de diagnóstico, *não há suporte para a realização de alterações ao modelo. Alterações ao modelo podem levar a dados corrompidos e a perda de dados.*

Para obter mais informações sobre as diversas funcionalidades do Power BI Desktop, confira os seguintes recursos:

* [Visão geral da Consulta no Power BI Desktop](../transform-model/desktop-query-overview.md)
* [Fontes de dados no Power BI Desktop](../connect-data/desktop-data-sources.md)
* [Conectar-se a dados no Power BI Desktop](../connect-data/desktop-connect-to-data.md)
* [Tutorial: Formatar e combinar dados com o Power BI Desktop](../connect-data/desktop-shape-and-combine-data.md)
* [Tarefas comuns de consulta no Power BI Desktop](../transform-model/desktop-common-query-tasks.md)   
