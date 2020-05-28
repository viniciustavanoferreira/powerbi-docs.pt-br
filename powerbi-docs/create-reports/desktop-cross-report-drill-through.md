---
title: Usar o detalhamento entre relatórios no Power BI Desktop
description: Saiba como fazer uma detalhamento de um relatório para outro no Power BI Desktop
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/16/2019
ms.author: maggies
LocalizationGroup: Create reports
ms.openlocfilehash: 178ad340a9a3ccd9d6427dc6bad03b6d8d08ce90
ms.sourcegitcommit: 250242fd6346b60b0eda7a314944363c0bacaca8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83694058"
---
# <a name="use-cross-report-drillthrough-in-power-bi"></a>Usar o detalhamento entre relatórios no Power BI

Com o recurso de *detalhamento entre relatórios* do Power BI, você pode saltar contextualmente de um relatório para outro no mesmo workspace ou aplicativo do serviço do Power BI. Use o detalhamento entre relatórios para conectar dois ou mais relatórios que tenham um conteúdo relacionado e transmitir o contexto de filtro junto com a conexão entre relatórios. 

Para iniciar o detalhamento entre relatórios, selecione um ponto de dados em um *visual de origem* de um *relatório de origem* e, em seguida, selecione o destino **Detalhamento** entre relatórios no menu de contexto. 

![Opção de detalhamento entre relatórios do Power BI](media/desktop-cross-report-drill-through/cross-report-drill-through-01.png)

A ação de detalhamento abre a *página de destino* no *relatório de destino*. 

![Destino de detalhamento entre relatórios do Power BI Desktop](media/desktop-cross-report-drill-through/cross-report-drill-through-01a.png)

Este artigo mostra como configurar e usar o detalhamento entre relatórios nos relatórios do Power BI.

> [!NOTE]
> Não é possível usar o detalhamento entre relatórios com [relatórios Compartilhados comigo](../collaborate-share/service-share-dashboards.md#share-a-dashboard-or-report) compartilhados individualmente. Para usar o detalhamento entre relatórios, é necessário acessar os relatórios em workspaces dos quais você é membro.

## <a name="enable-cross-report-drillthrough"></a>Habilitar o detalhamento entre relatórios

A primeira etapa para habilitar o detalhamento entre relatórios é validar os modelos de dados dos relatórios de origem e destino. Embora os esquemas de cada relatório não precisem ser os mesmos, os campos que você deseja transmitir precisam existir em ambos os modelos de dados. Os nomes dos campos e os nomes das tabelas aos quais eles pertencem precisam ser idênticos. As cadeias de caracteres precisam ser correspondentes e diferenciar maiúsculas de minúsculas.

Por exemplo, se você desejar transmitir um filtro em um campo **State** de uma tabela **US States**, ambos os modelos precisarão ter uma tabela **US States** e um campo **State** dentro dessa tabela. Caso contrário, você deverá atualizar o nome do campo ou o nome da tabela no modelo subjacente. Simplesmente atualizar o nome de exibição dos campos não funcionará corretamente para detalhamento entre relatórios.

Depois de validar os modelos, permita que o relatório de origem use o detalhamento entre relatórios. 

1. No Power BI Desktop, acesse **Arquivo** > **Opções e configurações** > **Opções**. 
1. No painel de navegação à esquerda da janela **Opções**, na parte inferior da seção **Arquivo atual**, selecione **Configurações do relatório**. 
1. Na parte inferior direita, em **Detalhamento entre relatórios**, selecione **Permitir que os visuais deste relatório usem destinos de detalhamento de outros relatórios**. 
1. Selecione **OK**. 
   
   ![Habilitar o detalhamento entre relatórios no Power BI Desktop](media/desktop-cross-report-drill-through/cross-report-drill-through-02.png)

Habilite também o detalhamento entre relatórios por meio do serviço do Power BI.
1. No serviço do Power BI, selecione o workspace que contém seus relatórios de origem e destino.
1. Ao lado do nome do relatório de origem na lista de workspaces, selecione o símbolo **Mais opções** e, em seguida, selecione **Configurações**. 
1. Próximo à parte inferior do painel **Configurações**, em **Detalhamento entre relatórios**, selecione **Permitir que os visuais deste relatório usem destinos de detalhamento de outros relatórios** e, em seguida, selecione **Salvar**.
   
   ![Habilitar o detalhamento entre relatórios no serviço do Power BI](media/desktop-cross-report-drill-through/cross-report-drill-through-02a.png)

## <a name="set-up-a-cross-report-drillthrough-target"></a>Configurar um destino de detalhamento entre relatórios

A configuração de uma página de destino para o detalhamento entre relatórios é semelhante à configuração do detalhamento em um relatório. A habilitação do detalhamento na página de destino permite que outros visuais sejam direcionados à página para detalhamento. Para criar o detalhamento em um só relatório, confira [Usar o detalhamento no Power BI Desktop](desktop-drillthrough.md).

Configure um destino para o detalhamento entre relatórios no Power BI Desktop ou no serviço do Power BI. 
1. Edite o arquivo de destino e, na página destino do relatório de destino, selecione a seção **Campos** do painel **Visualizações**. 
1. Em **Detalhamento**, defina a alternância **Entre relatórios** para **Ativado**. 
1. Arraste os campos que deseja usar como destinos de detalhamento em **Adicionar campos de detalhamento aqui**. Para cada campo, selecione se deseja permitir o detalhamento quando o campo é usado como uma categoria ou quando ele é resumido como uma medida. 
1. Selecione se deseja **Manter todos os filtros** do visual. Caso não deseje transmitir os filtros aplicados ao visual de origem para o visual de destino, selecione **Desativado**.
   
   ![Painel Visualizações, com as opções de Detalhamento realçadas](media/desktop-cross-report-drill-through/cross-report-drill-through-03.png)
   
1. Se estiver usando a página apenas para o detalhamento entre relatórios, exclua o botão **Voltar**, que é adicionado automaticamente à tela. O botão **Voltar** só funciona para a navegação em um relatório. 
1. Depois de configurar a página de destino, salve o relatório se estiver no serviço do Power BI ou salve o relatório e publique-o se estiver usando o Power BI Desktop.

É isso. Seus relatórios estão prontos para o detalhamento entre relatórios. 

## <a name="use-cross-report-drillthrough"></a>Usar detalhamento de relatório cruzado

Para usar o detalhamento entre relatórios, selecione o relatório de origem no serviço do Power BI e, em seguida, selecione um visual que use o campo de detalhamento da maneira que você especificou ao configurar a página de destino. Clique com o botão direito do mouse em um ponto de dados para abrir o menu de contexto do visual, selecione **Detalhamento** e, em seguida, selecione o destino de detalhamento. Os destinos do detalhamento entre relatórios são formatados como **Nome da página [nome do relatório]** .

![Opção de detalhamento entre relatórios do Power BI](media/desktop-cross-report-drill-through/cross-report-drill-through-01.png)

Você verá os resultados na página de detalhamento entre relatórios de destino, assim como você os configurou quando criou o destino. Os resultados são filtrados de acordo com as configurações de detalhamento.

![Destino de detalhamento entre relatórios do Power BI Desktop](media/desktop-cross-report-drill-through/cross-report-drill-through-01a.png)

> [!IMPORTANT]
> O Power BI armazena em cache os destinos de detalhamento entre relatórios. Se você fizer alterações, atualize o navegador, caso não veja os destinos de detalhamento conforme esperado. 

Se você definir **Manter todos os filtros** como **Ativado** ao configurar a página de destino, o contexto de filtro do visual de origem poderá incluir o seguinte: 

- Filtros no nível do relatório, da página e do visual que afetam o visual de origem 
- Filtro e realce cruzados que afetam o visual de origem 
- Segmentações e segmentações de sincronização na página
- Parâmetros de URL

Quando você aterrissa no relatório de destino para detalhamento, o Power BI aplica somente os filtros dos campos que têm correspondências exatas de cadeias de caracteres no nome do campo e no nome da tabela. 

O Power BI não aplica filtros temporários por meio do relatório de destino, mas aplica o indicador pessoal padrão, caso você tenha um. Por exemplo, se o indicador pessoal padrão incluir um filtro no nível do relatório para *Country = US*, o Power BI aplicará esse filtro antes de aplicar o contexto de filtro do visual de origem. 

Para o detalhamento entre relatórios, o Power BI transmite o contexto de filtro para as páginas padrão no relatório de destino. O Power BI não passa o contexto de filtro para páginas de dica de ferramenta, pois essas páginas são filtradas com base no visual de origem que invoca a dica de ferramenta.

Se você quiser retornar ao relatório de origem após a ação de detalhamento entre relatórios, use o botão **Voltar** do navegador. 

## <a name="next-steps"></a>Próximas etapas

Você também pode estar interessado nos seguintes artigos:

- [Segmentações no Power BI](../visuals/power-bi-visualization-slicers.md)
- [Usar o detalhamento no Power BI Desktop](desktop-drillthrough.md)
