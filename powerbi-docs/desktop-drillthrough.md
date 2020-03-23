---
title: Configurar o drill-through nos relatórios do Power BI
description: Saiba como usar o drill-through para executar uma consulta drill down nos dados em uma nova página de relatório nos relatórios do Power BI
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 03/12/2020
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 5a494341ff6ee9c5fe4b2c2119749f58f2fd540d
ms.sourcegitcommit: 7e845812874b3347bcf87ca642c66bed298b244a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79201437"
---
# <a name="set-up-drill-through-in-power-bi-reports"></a>Configurar o drill-through nos relatórios do Power BI
Com o *drill-through* nos relatórios do Power BI, você pode criar uma página em seu relatório que tenha como foco uma entidade específica, como um fornecedor, cliente ou fabricante. Quando seus leitores de relatório usam o drill-through, clique com o botão direito do mouse em um ponto de dados em outras páginas de relatório e execute uma consulta drill-through na página de foco para obter detalhes filtrados para esse contexto. Você também pode [criar um botão que executa uma consulta drill-through](desktop-drill-through-buttons.md) para obter detalhes quando se clica neles.

Você pode configurar o drill-through em seus relatórios no Power BI Desktop ou no serviço do Power BI.

![Usar drill-through](media/desktop-drillthrough/power-bi-drill-through-right-click.png)

## <a name="set-up-the-drill-through-destination-page"></a>Configurar a página de destino de drill-through
1. Para configurar o drill-through, crie uma página de relatório que tenha os visuais desejados para o tipo de entidade para o qual você fornecerá o drill-through. 

    Por exemplo, vamos supor que você deseje executar uma consulta drill-through para fabricantes. Nesse caso, você poderá criar uma página de drill-through com visuais que mostram o total de vendas, o total de unidades enviadas, vendas por categoria, vendas por região e assim por diante. Dessa forma, quando você executa uma consulta drill-through nessa página, os visuais são específicos do fabricante selecionado.

2. Em seguida, na página de drill-through, na seção **Campos** do painel **Visualizações**, arraste o campo para o qual você deseja habilitar o drill-through na caixa **Filtros de drill-through**.

    ![Caixa Drill-through](media/desktop-drillthrough/drillthrough_02.png)

    Quando você adiciona um campo à caixa **Filtros de drill-through**, o Power BI cria automaticamente um visual do botão *voltar*. Esse elemento visual transforma-se em um botão nos relatórios publicados. Os usuários que consomem seu relatório no serviço do Power BI usam esse botão para voltar para a página do relatório de origem.

    ![Imagem de drill-through](media/desktop-drillthrough/drillthrough_03.png)

> [!IMPORTANT]
> Você pode configurar e fazer o detalhamento em uma página do mesmo relatório, no entanto, não é possível detalhar uma página em um relatório diferente.  



## <a name="use-your-own-image-for-a-back-button"></a>Use sua própria imagem para um botão Voltar    
 Como o botão Voltar é uma imagem, você pode substituir a imagem desse elemento visual por qualquer imagem desejada. Ele ainda funciona como um botão voltar para que os consumidores do relatório possam voltar para a página original. 

Para usar sua própria imagem para um botão voltar, siga estas etapas:

1. Na guia **Página Inicial**, selecione **Imagem**. Em seguida, localize a imagem e coloque-a na página de drill-through.

2. Selecione a nova imagem na página de drill-through. No painel **Formatar imagem**, defina o controle deslizante **Ação** como **Ativado** e, em seguida, defina o **Tipo** como **Voltar**. Sua imagem agora funciona como um botão Voltar.

    ![Carregar imagem e definir o Tipo como Voltar](media/desktop-drillthrough/drillthrough_05.png)

    
     Agora os usuários podem clicar com o botão direito do mouse em um ponto de dados no seu relatório e obter um menu de contexto que dá suporte ao drill-through dessa página. 

    ![Menu de drill-through](media/desktop-drillthrough/drillthrough_04.png)

    Quando os consumidores do relatório escolherem o detalhamento, a página é filtrada para mostrar informações sobre o ponto de dados de origem do clique com o botão direito do mouse. Por exemplo, vamos supor que eles clicaram com o botão direito do mouse em um ponto de dados sobre a Contoso, um fabricante e selecionaram para detalhar. A página de drill-through que eles acessam está filtrada para Contoso.

## <a name="pass-all-filters-in-drill-through"></a>Passar todos os filtros em drill-through

Você pode passar todos os filtros aplicados para a janela de drill-through. Por exemplo, você pode selecionar apenas uma determinada categoria de produtos e os visuais filtrados para essa categoria e, em seguida, selecionar o drill-through. Provavelmente você vai querer saber como esse drill-through ficará com todos esses filtros aplicados.

Para manter todos os filtros aplicados, na seção **Drill-through** do painel **Visualizações**, defina o **Manter todos os filtros** como **Ativado**. 

![Manter todos os filtros](media/desktop-drillthrough/drillthrough_06.png)

Em seguida, ao fazer o detalhamento em um visual, você poderá ver quais filtros foram aplicados como resultado da aplicação de filtros temporários no visual de origem. Na seção **Drill-through** do painel **Visualização**, esses filtros transitórios são mostrados em itálico. 

![Filtros transitórios em itálico](media/desktop-drillthrough/drillthrough_07.png)

Embora você pudesse fazer isso com páginas de dicas de ferramenta, essa seria uma experiência estranha, porque a dica de ferramenta não pareceria estar funcionando corretamente. Por esse motivo, fazer isso com dicas de ferramenta não é recomendado.

## <a name="add-a-measure-to-drill-through"></a>Adicionar uma medida ao drill-through

Além de passar todos os filtros para a janela de drill-through, você também pode adicionar uma medida ou uma coluna numérica resumida para a área de drill-through. Arraste o campo de drill-through para o cartão **Drill-through** a fim de aplicá-lo. 

![Adicionar uma medida ao drill-through](media/desktop-drillthrough/drillthrough_08.png)

Quando você adiciona uma medida ou uma coluna numérica resumida, você pode fazer uma busca detalhada até a página quando o campo é usado na área *Valor* de um visual.

E isso é tudo o que é necessário para usar o drill-through em seus relatórios. É uma ótima maneira de obter uma exibição expandida das informações de entidade selecionadas para o filtro de drill-through.

## <a name="next-steps"></a>Próximas etapas

Você também pode estar interessado nos seguintes artigos:

* [Usar o drill-through entre relatórios no relatório Power BI](desktop-cross-report-drill-through.md)
* [Usando segmentações no Power BI Desktop](visuals/power-bi-visualization-slicers.md)

