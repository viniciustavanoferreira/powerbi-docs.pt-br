---
title: Estender visuais com dicas de ferramentas de página de relatório
description: Orientações para trabalhar com as dicas de ferramenta da página de relatório.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/24/2019
ms.author: v-pemyer
ms.openlocfilehash: 826af7b224b901b6dc9f3926260b1d920836a792
ms.sourcegitcommit: 0ae9328e7b35799d5d9613a6d79d2f86f53d9ab0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/16/2020
ms.locfileid: "76040346"
---
# <a name="extend-visuals-with-report-page-tooltips"></a>Estender visuais com dicas de ferramentas de página de relatório

Este artigo é voltado a você como um autor de relatórios que elabora relatórios do Power BI. Ele fornece sugestões e recomendações para criar [dicas de ferramenta da página de relatório](../desktop-tooltips.md).

## <a name="suggestions"></a>Sugestões

As dicas de ferramenta da página de relatório podem aprimorar a experiência dos usuários de relatórios. Elas permitem que os usuários de relatórios tenham acesso a informações mais aprofundadas com rapidez e eficiência em um visual. Elas podem ser associadas a diferentes objetos de relatório:

- **Visuais:** Visual por visual, você pode configurar quais visuais revelarão a dica de ferramenta da página. Ao configurar cada visual, é possível fazer com que ele não revele nenhuma dica de ferramenta, mostre as dicas de ferramenta do visual por padrão (configuradas no painel de campos do visual) ou use uma dica de ferramenta de uma página específica.
- **Cabeçalhos de visual:** você pode configurar visuais específicos para exibir uma dica de ferramenta de página. Os usuários de seu relatório podem revelar a dica de ferramenta da página ao passar o cursor do mouse sobre o ícone de cabeçalho do visual — não se esqueça de instrui-los sobre esse ícone.

> [!NOTE]
> Um visual de relatório só pode revelar uma dica de ferramenta de da página quando os filtros da página de dica de ferramenta são compatíveis com o design do visual. Por exemplo, um visual que agrupa por _produto_ é compatível com uma página de dica de ferramenta que filtra por _produto_.
>
> As dicas de ferramentas de página não dão suporte à interatividade. Se quiser que os usuários do relatório interajam, crie uma [página de detalhamento](../desktop-drillthrough.md).
>
> Visuais personalizados não dão suporte a dicas de ferramenta de página.

Estes são alguns cenários de design sugeridos:

- [Perspectiva diferente](#different-perspective)
- [Adicionar detalhes](#add-detail)
- [Adicionar ajuda](#add-help)

### <a name="different-perspective"></a>Perspectiva diferente

Uma dica de ferramenta de página pode visualizar os mesmos dados que o visual de origem. Isso é feito usando os mesmos grupos visuais e dinâmicos, ou usando diferentes tipos de elementos visuais. As dicas de ferramenta de página também podem aplicar filtros diferentes daqueles aplicados ao visual de origem.

O exemplo a seguir mostra o que acontece quando o usuário do relatório passa o cursor sobre o valor **EnabledUsers**. O contexto de filtro do valor é o Yammer em novembro de 2018.

![Um visual de matriz exibe uma grade de valores agrupados por ano e mês nas linhas. O usuário do relatório passou o cursor do mouse sobre um único valor. Uma dica de ferramenta de página apareceu.](media/report-page-tooltips/suggestion-different-perspective.png)

Uma dica de ferramenta de página é revelada. Ela apresenta um visual de dados diferente (gráfico de colunas clusterizadas e linhas) e aplica um filtro de tempo contrastante. Observe que o contexto de filtro para o ponto de dados é novembro de 2018. Ainda assim, a dica de ferramenta de página exibe a tendência ao longo fr _um ano inteiro de meses_.

### <a name="add-detail"></a>Adicionar detalhes

Uma dica de ferramenta de página pode exibir mais detalhes e adicionar contexto.

O exemplo a seguir mostra o que acontece quando o usuário do relatório passa o cursor sobre o valor **Média de Pontos de Violação**, para o CEP 98022.

![Um visual de tabela exibe uma grade de valores e a tabela contém três colunas. Uma dica de ferramenta de página apareceu.](media/report-page-tooltips/suggestion-add-details.png)

Uma dica de ferramenta de página é revelada. Ela apresenta atributos e estatísticas específicos do CEP 98022.

### <a name="add-help"></a>Adicionar ajuda

Os cabeçalhos dos visuais podem ser configurados para revelar dicas de ferramenta de página para cabeçalhos de visuais. Você pode adicionar documentação de ajuda a uma dica de ferramenta da página usando caixas de texto com formatação avançada. Também é possível adicionar imagens e formas.

Curiosamente, botões, imagens, caixas de texto e formas também podem revelar uma dica de ferramenta de página de cabeçalho do visual.

O exemplo a seguir mostra o que acontece quando o usuário do relatório passa o cursor sobre o [ícone de cabeçalho do visual](../desktop-visual-elements-for-reports.md).

![Um usuário de relatório passou o cursor sobre o ícone de cabeçalho do visual (ícone de ponto de interrogação). Uma dica de ferramenta com formatação avançada apareceu.](media/report-page-tooltips/suggestion-add-help.png)

Uma dica de ferramenta de página é revelada. Ela apresenta um texto com formatação avançada em quatro caixas de texto e uma forma (linha). A dica de ferramenta da página fornece ajuda descrevendo cada acrônimo exibido no visual.

## <a name="recommendations"></a>Recomendações

No momento de design do relatório, recomendamos as seguintes práticas:

- **Tamanho da página:** configure a dica de ferramenta de página para ser pequena. Você pode usar a opção de **Dica de ferramenta** interna (320 pixels de largura, 240 pixels de altura). Ou você pode definir dimensões personalizadas. Tome cuidado para não usar um tamanho muito grande, pois isso pode ocultar os visuais na página de origem.
- **Exibição de página:** no designer de relatórios, defina o modo de exibição de página como **Tamanho real** (a exibição de página usa como padrão **Ajustar à página**). Dessa forma, você pode ver o tamanho real da dica de ferramenta da página ao criá-la.
- **Estilo:** considere projetar a dica de ferramenta de página usando o mesmo tema e estilo do relatório. Dessa forma, os usuários sentem que estão no mesmo relatório. Ou crie um estilo gratuito para suas dicas de ferramenta e certifique-se de aplicar esse estilo a todas as dicas de ferramenta de página.
- **Filtros de dica de ferramenta:** atribua filtros à dica de ferramenta de página para que você possa visualizar um resultado realista ao criá-lo. Não deixe de remover esses filtros antes de publicar o relatório.
- **Visibilidade da página:** sempre oculte páginas de dica de ferramenta – os usuários não devem navegar diretamente para elas.

## <a name="next-steps"></a>Próximas etapas

Para obter mais informações relacionadas a este artigo, confira os seguintes recursos:

- [Criar dicas de ferramenta com base nas páginas de relatório no Power BI Desktop](../desktop-tooltips.md)
- [Personalizando dicas de ferramenta no Power BI Desktop](../desktop-custom-tooltips.md)
- [Usar elementos visuais para aprimorar os relatórios do Power BI](../desktop-visual-elements-for-reports.md)
- Vídeo do Guy in a Cube: [Dica de ferramenta de página de relatório do Power BI – Como criar uma no Power BI Desktop](https://www.youtube.com/watch?v=URTA7JZsAtw)
- Dúvidas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
