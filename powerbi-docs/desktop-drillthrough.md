---
title: Usar o detalhamento no Power BI Desktop
description: Saiba como fazer uma busca detalhada dos dados em uma nova página de relatório no Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 04/10/2019
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: e093788683d10bc11c09d63ba327611a67f311c0
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/09/2019
ms.locfileid: "73879905"
---
# <a name="use-drillthrough-in-power-bi-desktop"></a>Usar o detalhamento no Power BI Desktop
Com o **detalhamento** no **Power BI Desktop**, você pode criar uma página em seu relatório que tem como foco uma entidade específica, como um fornecedor, cliente ou fabricante. Os usuários podem clicar com o botão direito em um ponto de dados em outras páginas do relatório. Em seguida, podem detalhar até a página com foco para obter detalhes filtrados para esse contexto.

![Usando o detalhamento](media/desktop-drillthrough/drillthrough_01.png)

## <a name="using-drillthrough"></a>Usando o detalhamento
1. Para usar o **detalhamento**, crie uma página de relatório que tem os visuais desejados para o tipo de entidade para o qual fornecerá o detalhamento. 

    Por exemplo, se estiver interessado em fornecer o detalhamento de fabricantes, poderá criar uma página de detalhamento com visuais que mostram o total de vendas, o total de unidades enviadas, vendas por categoria, vendas por região e assim por diante. Dessa forma, quando você executar uma consulta drill-through para a página, os visuais serão específicos do fabricante selecionado.

2. Em seguida, na página de detalhamento, na seção **Campos** do painel **Visualizações**, arraste o campo para o qual você deseja habilitar o detalhamento no contêiner **Filtros de detalhamento**.

    ![Área de detalhamento](media/desktop-drillthrough/drillthrough_02.png)

    Quando você adiciona um campo ao contêiner **Filtros de detalhamento**, o **Power BI Desktop** cria automaticamente um visual do botão *Voltar*. Esse elemento visual transforma-se em um botão nos relatórios publicados. Os usuários que estão consumindo o relatório no **serviço do Power BI** podem usar esse botão para voltar à página do relatório de origem.

    ![Imagem do detalhamento](media/desktop-drillthrough/drillthrough_03.png)

## <a name="use-your-own-image-for-a-back-button"></a>Use sua própria imagem para um botão Voltar    
 Como o botão Voltar é uma imagem, você pode substituir a imagem desse elemento visual por qualquer imagem desejada. Ele ainda funcionará como um botão Voltar para que os consumidores do relatório possam voltar para a página original. Para usar sua própria imagem para um botão Voltar, execute as seguintes etapas:

1. Na guia **Página Inicial**, selecione **Imagem**. Em seguida, localize a imagem e coloque-a na página de detalhamento.

2. Selecione a nova imagem na página de detalhamento. Na seção **Formatar Imagem**, defina o controle deslizante **Link** como **Ligado** e, em seguida, defina o **Tipo** como **Voltar**. Sua imagem agora funciona como um botão Voltar.

    ![Usar imagem para voltar](media/desktop-drillthrough/drillthrough_05.png)

    
     Agora os usuários podem clicar com o botão direito em um ponto de dados no seu relatório e obter um menu de contexto que dá suporte ao detalhamento para essa página. 

    ![Menu de detalhamento](media/desktop-drillthrough/drillthrough_04.png)

    Quando os consumidores do relatório escolherem o detalhamento, a página é filtrada para mostrar informações sobre o ponto de dados de origem do clique com o botão direito do mouse. Por exemplo, digamos que eles clicaram com o botão direito em um ponto de dados sobre a Contoso (um fabricante) e selecionaram para detalhar. A página de detalhamento para a qual eles vão está filtrada para Contoso.

## <a name="pass-all-filters-in-drillthrough"></a>Passar todos os filtros no detalhamento

Começando com a versão de maio de 2018 do **Power BI Desktop**, você pode passar todos os filtros aplicados para a janela de detalhamento. Por exemplo, você pode selecionar apenas uma determinada categoria de produtos e os visuais filtrados para essa categoria e, em seguida, selecionar o detalhamento. Provavelmente você vai querer saber como esse detalhamento ficará com todos esses filtros aplicados.

Para manter todos os filtros aplicados, na seção **Detalhamento** do painel **Visualizações**, defina o botão de alternância **Passar todos os filtros** para **habilitado**. 

![Manter todos os filtros](media/desktop-drillthrough/drillthrough_06.png)

Nas versões do **Power BI Desktop** anteriores à de maio de 2018, o comportamento é o mesmo de quando esse botão de alternância está definido como **desabilitado**.

Em seguida, ao fazer o detalhamento em um visual, você poderá ver quais filtros foram aplicados como resultado da aplicação de filtros temporários no visual de origem. Na janela de detalhamento, esses filtros transitórios são mostrados em itálico. 

![Filtros transitórios em itálico](media/desktop-drillthrough/drillthrough_07.png)

Isso poderia ser feito com páginas de dicas de ferramenta, mas essa seria uma experiência estranha porque a dica de ferramenta não pareceria estar funcionando corretamente. Por esse motivo, fazer isso com dicas de ferramenta não é recomendado.

## <a name="add-a-measure-to-drillthrough"></a>Adicionar uma medida ao detalhamento

Além de passar todos os filtros para a janela de detalhamento, você também pode adicionar uma medida ou uma coluna numérica resumida para a área de detalhamento. Arraste o campo de detalhamento para o cartão de detalhamento para aplicá-lo. 

![Adicionar uma medida ao detalhamento](media/desktop-drillthrough/drillthrough_08.png)

Quando você adiciona uma medida ou uma coluna numérica resumida, você pode fazer uma busca detalhada até a página quando o campo é usado na área *Valor* de um visual.

E isso é tudo o que é necessário para usar o **detalhamento** em seus relatórios. É uma ótima maneira de obter uma exibição expandida das informações de entidade selecionadas para o filtro de detalhamento.

## <a name="next-steps"></a>Próximas etapas

Você também pode estar interessado nos seguintes artigos:

* [Usar o detalhamento no Power BI Desktop](desktop-cross-report-drill-through.md)
* [Usando segmentações no Power BI Desktop](visuals/power-bi-visualization-slicers.md)

