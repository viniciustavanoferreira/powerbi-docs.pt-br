---
title: Conceito visual do Power BI
description: O artigo descreve como o visual se integra com o Power BI
author: zBritva
ms.author: v-ilgali
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 36742917829013a6efca9d74f88b01bc686437a8
ms.sourcegitcommit: f77b24a8a588605f005c9bb1fdad864955885718
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2019
ms.locfileid: "74700836"
---
# <a name="power-bi-visual-concept"></a>Conceito visual do Power BI

O artigo explica como um usuário e um visual interagem com Power BI e como um usuário interage com o visual do Power BI. No diagrama, você vê quais ações influenciam diretamente para o visual ou por meio de Power BI (por exemplo, o usuário seleciona indicadores).

![Visual do Power BI](./media/visual-concept.svg)

## <a name="the-visual-gets-update-from-power-bi"></a>O visual obtém a atualização do Power BI

O visual tem o método `update`, que geralmente contém a lógica principal do visual e é responsável por renderizar o gráfico ou visualizar os dados.

Mais atualizações entram com a chamada do método `update`.

### <a name="user-interacts-with-visual-through-power-bi"></a>O usuário interage com o visual por meio do Power BI

* O usuário abre o painel de propriedades visuais.

    O Power BI busca objetos e propriedades com suporte do visual `capabilities.json` e, para receber valores reais de propriedades, o Power BI chama o método `enumerateObjectInstances` do visual.

    O visual precisa retornar valores reais de propriedades.

    Para obter mais informações, [leia sobre as funcionalidades visuais](capabilities.md).

* [O usuário altera a propriedade do visual](../../visuals/power-bi-visualization-customize-title-background-and-legend.md) no painel de formato.

    Depois de alterar o valor de uma propriedade, o Power BI chama o método `update` do visual e passa o novo `options` com os novos valores dos objetos para o método de atualização.

    Para obter mais informações, [leia sobre objetos e propriedades do visual](objects-properties.md).

* O usuário redimensiona o visual.

    Quando um usuário altera um tamanho do visual, o Power BI chama o método `update` com o novo objeto `option`. As opções têm o objeto `viewport` aninhado com nova largura e altura do visual.

* O usuário aplica o filtro de relatório, de página ou de nível visual.

    O Power BI filtra os dados de acordo com as condições de filtro e chama o método `update` do visual para fornecer novos dados.

    O visual obtém uma nova atualização de `options` com novos dados em um dos objetos aninhados. Isso depende da configuração de mapeamento de exibição de dados do visual.

    Para obter mais informações, [leia sobre mapeamentos de exibição de dados](dataview-mappings.md).

* O usuário seleciona o ponto de dados em outro visual do relatório.

    O Power BI filtra ou realça os pontos de dados selecionados e chama o método `update` do visual.

    O visual obtém novos dados filtrados ou os mesmos dados com a matriz de destaques.

    Para obter mais informações, [leia como realçar dados em visuais](highlight.md).

* O usuário seleciona o indicador no painel de indicadores do relatório.

    Podem ocorrer duas ações:

    1. O Power BI chama a função passada registrada pelo método `registerOnSelectionCallback` e a função de retorno de chamada obtém matrizes de seleções para o indicador correspondente.

    2. O Power BI chama o método `update` com o objeto de filtro correspondente dentro de `options`.

    Em ambos os casos, o visual precisa alterar o estado de visualização de acordo com as seleções recebidas ou o objeto de filtro.

    Para obter mais detalhes sobre indicadores, [leia como lidar com indicadores](filter-api.md).

    Para obter mais informações sobre filtros, [leia como os visuais do Power BI podem filtrar dados em outros visuais](filter-api.md).

### <a name="user-interacts-with-visual-directly"></a>O usuário interage diretamente com o visual

* O usuário passa o mouse sobre o elemento de dados

    O visual pode exibir informações adicionais sobre o ponto de dados por meio da API de Dicas de Ferramenta do Power BI.
    O usuário passa o mouse no elemento visual O visual pode manipular o evento e exibir dados no elemento de dica de ferramenta.

    O visual pode exibir a dica de ferramenta padrão ou a dica de ferramenta de página de relatório.

    Para obter mais informações, leia o guia [como adicionar dicas de ferramentas](add-tooltips.md).

* O usuário altera as propriedades visuais (por exemplo, o usuário expande a árvore e o visual salva o estado nas propriedades)

    O visual pode salvar os valores das propriedades por meio da API do Power BI. Por exemplo, quando o usuário interage com o visual. E o visual precisa salvar ou atualizar valores de propriedade. O visual pode chamar o método `presistProperties` para isso.

* O usuário clica no link de URL.

    Por padrão, o visual não pode abrir a URL. Para abrir a URL em uma nova guia, o visual deve chamar o método `launchURL` e passar a URL como parâmetro.

    Para obter mais informações, leia sobre [iniciar API da URL](launch-url.md).

* O usuário aplica o filtro por meio do visual

    O visual chama `applyJSONFilter` e passa as condições de filtro para a filtragem de dados em outro visual.

    O visual pode usar vários tipos de filtro, como o filtro básico, o filtro avançado ou o filtro de tupla.

    Para obter mais informações sobre filtros, [leia como os visuais do Power BI podem filtrar dados em outros visuais](filter-api.md).

* O usuário clica/seleciona elementos no visual.

    Para obter mais informações sobre seleções, [leia como o visual interage](selection-api.md).

### <a name="the-visual-interacts-with-power-bi"></a>O visual interage com o Power BI

* O visual solicita mais dados do Power BI.

    O visual pode processar dados por partes. O método da API FetchMoreData solicita o próximo fragmento do conjunto de dados.

    Para obter mais informações sobre `fetchMoreData`, [leia como buscar mais dados do Power BI](fetch-more-data.md)

* Serviço de eventos

    O Power BI pode exportar relatórios para PDF ou enviá-los por email (somente elementos visuais certificados têm suporte). Para notificar o Power BI que a renderização foi concluída e está pronta para capturar o PDF/email, o visual deve chamar a API de Eventos de Renderização.

    Para obter mais informações, [leia sobre como exportar relatórios do Power BI para PDF](../../consumer/end-user-pdf.md)

    Encontre mais [informações sobre o Serviço de Eventos](event-service.md)

## <a name="next-steps"></a>Próximas etapas

Você é um desenvolvedor da Web e está interessado em criar suas próprias visualizações e adicioná-las ao AppSource? Confira [Desenvolvimento de um Visual do Power BI](./custom-visual-develop-tutorial.md) e saiba como [publicar visuais do Power BI no AppSource](../office-store.md).
