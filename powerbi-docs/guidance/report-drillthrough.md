---
title: Usar o detalhamento de página de relatório
description: Orientações para trabalhar com o detalhamento da página de relatório.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/28/2019
ms.author: v-pemyer
ms.openlocfilehash: 853f6d7f5cd6696be55edeea101bc0ca51922ad3
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83278067"
---
# <a name="use-report-page-drillthrough"></a>Usar o detalhamento de página de relatório

Este artigo é voltado a você como um autor de relatórios que elabora relatórios do Power BI. Ele fornece sugestões e recomendações para criar [detalhamentos da página de relatório](../create-reports/desktop-drillthrough.md).

É recomendável que você projete seu relatório para permitir que os usuários alcancem o seguinte fluxo:

1. Exibir uma página do relatório.
2. Identificar um elemento visual para analisar mais profundamente.
3. Clicar com o botão direito do mouse no elemento visual para detalhamento.
4. Executar uma análise complementar.
5. Coltar à página do relatório de origem.

## <a name="suggestions"></a>Sugestões

Sugerimos que você considere dois tipos de cenários de detalhamento:

- [Profundidade adicional](#additional-depth)
- [Perspectiva mais ampla](#broader-perspective)

### <a name="additional-depth"></a>Profundidade adicional

Quando a página do relatório exibe resultados resumidos, uma página de detalhamento pode levar os usuários do relatório para os detalhes no nível da transação. Essa abordagem de design permite que eles exibam as transações de suporte somente quando necessário.

O exemplo a seguir mostra o que acontece quando um usuário de relatório faz um detalhamento de um resumo de vendas mensal. A página de detalhamento contém uma lista detalhada de pedidos para um mês específico.

![Um visual de matriz intitulado "Resumo de vendas" agrupa as vendas por ano e por mês nas linhas e por país nas colunas. Também é exibida uma página de detalhamento.](media/report-drillthrough/suggestion-drillthrough-add-depth.png)

### <a name="broader-perspective"></a>Perspectiva mais ampla

Uma página de detalhamento pode atingir o oposto da profundidade adicional. Esse cenário é ótimo para detalhar uma exibição holística.

O exemplo a seguir mostra o que acontece quando um usuário de relatório faz um detalhamento usando o CEP. A página de detalhamento exibe informações gerais sobre esse CEP.

![Um visual de tabela tem três colunas: CEP, Média de Pontos de Violação e Classificação Média da Taxa. Também é exibida a página de detalhamento.](media/report-drillthrough/suggestion-drillthrough-broader-perspective.png)

## <a name="recommendations"></a>Recomendações

No momento de design do relatório, recomendamos as seguintes práticas:

- **Estilo:** considere projetar a página de detalhamento usando o mesmo tema e estilo do relatório. Dessa forma, os usuários sentem que estão no mesmo relatório.
- **Filtros de detalhamento:** defina filtros de detalhamento para que você possa visualizar um resultado realista ao criar a página de detalhamento. Não deixe de remover esses filtros antes de publicar o relatório.
- **Funcionalidades adicionais:** uma página de detalhamento é como qualquer página de relatório. Você pode até mesmo aprimorá-la com funcionalidades interativas adicionais, incluindo segmentações ou filtros.
- **Valores em branco:** evite adicionar visuais que podem exibir valores em branco ou gerar erros quando os filtros de detalhamento são aplicados.
- **Visibilidade da página:** considere ocultar as páginas de detalhamento. Se você decidir manter uma página de detalhamento visível, adicione um botão que permita aos usuários limpar os filtros de detalhamento definidos anteriormente. Atribua um [indicador](../create-reports/desktop-bookmarks.md) ao botão. O indicador deve ser configurado para remover todos os filtros.
- **Botão Voltar:** Um botão [Voltar](../create-reports/desktop-buttons.md) é adicionado automaticamente quando você atribui um filtro de detalhamento. É uma boa ideia mantê-lo. Dessa forma, os usuários do relatório podem retornar facilmente para a página de origem.
- **Descoberta:** ajude a promover a conscientização sobre a página de detalhamento definindo o texto do ícone do cabeçalho visual ou adicionando instruções a uma caixa de texto. Você também pode criar uma sobreposição, conforme descrito [nesta postagem de blog](https://alluringbi.com/2019/10/23/overlays-for-true-self-serve-reporting/).

> [!TIP]
> Também é possível configurar o detalhamento para seus relatórios paginados do Power BI. Você pode fazer isso para adicionar links a relatórios do Power BI. Os links podem definir [parâmetros de URL](https://powerbi.microsoft.com/blog/url-parameters-for-paginated-reports-are-now-available/).

## <a name="next-steps"></a>Próximas etapas

Para obter mais informações relacionadas a este artigo, confira os seguintes recursos:

- [Usar o detalhamento no Power BI Desktop](../create-reports/desktop-drillthrough.md)
- Dúvidas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
- Sugestões? [Contribuir com ideias para aprimorar o Power BI](https://ideas.powerbi.com/)
