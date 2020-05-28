---
title: Criar um botão de drill-through no Power BI
description: Você pode adicionar botões de drill-through em relatórios do Power BI que fazem seus relatórios se comportarem como aplicativos e aprofundarem o envolvimento com usuários.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/19/2020
ms.author: maggies
LocalizationGroup: Create reports
ms.openlocfilehash: 562e011bf280930fdcaf19cc87edc97b2bec131b
ms.sourcegitcommit: 250242fd6346b60b0eda7a314944363c0bacaca8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83694035"
---
# <a name="create-a-drill-through-button-in-power-bi"></a>Criar um botão de drill-through no Power BI

Ao criar um botão no Power BI, você pode selecionar a ação **Executar uma consulta drill-through**. Esse tipo de ação cria um botão que executa uma consulta drill-through em uma página de foco para obter detalhes filtrados para um contexto específico.

Um botão de drill-through poderá ser útil se você desejar aumentar a capacidade de descoberta de cenários de drill-through importantes em seus relatórios.

Neste exemplo, depois que o usuário seleciona a barra de palavras no gráfico, o botão **Ver detalhes** está habilitado.

![Botão Ver detalhes](media/desktop-drill-through-buttons/power-bi-drill-through-visual-button.png)

Ao selecionar o botão **Ver detalhes**, eles executam uma consulta drill-through na página Análise da Cesta de Compras. Como você pode ver no visual à esquerda, a página de drill-through agora está filtrada para o Word.

![Visual filtrado](media/desktop-drill-through-buttons/power-bi-drill-through-destination.png)

## <a name="set-up-a-drill-through-button"></a>Configurar um botão de drill-through

Para configurar um botão de drill-through, primeiro você precisa [configurar uma página de drill-through válida](desktop-drillthrough.md) dentro do seu relatório. Em seguida, você precisará criar um botão com **Executar consulta drill-through** como o tipo de ação e selecionar a página de drill-through como o **Destino**.

Como o botão de drill-through tem dois estados (quando executar consulta drill-through está habilitado versus desabilitado), você pode ver que há duas opções de dica de ferramenta.

![Configurar o botão de drill-through](media/desktop-drill-through-buttons/power-bi-create-drill-through-button.png)

Se você deixar as caixas de dicas de ferramenta em branco, o Power BI vai gerar automaticamente as dicas de ferramenta. Essas dicas de ferramenta são baseadas nos campos de destino e drill-through.

Veja um exemplo da dica de ferramenta gerada automaticamente quando o botão é desabilitado:

"Para executar uma consulta drill-through na Análise da Cesta de Compras (a página de destino), selecione um único ponto de dados do Produto (o campo de drill-through)."

![Dica de ferramenta gerada automaticamente desabilitada](media/desktop-drill-through-buttons/power-bi-drill-through-tooltip-disabled.png)

Além disso, veja um exemplo da dica de ferramenta gerada automaticamente quando o botão é habilitado:

"Clique para executar uma consulta drill-through na Análise da Cesta de Compras (a página de destino)."

![Dica de ferramenta gerada automaticamente habilitada](media/desktop-drill-through-buttons/power-bi-drill-through-visual-button.png)

No entanto, se você quiser fornecer dicas de ferramenta personalizadas, sempre poderá inserir uma cadeia de caracteres estática. Ainda não damos suporte à formatação condicional para dicas de ferramenta.

Você pode usar a formatação condicional para alterar o texto do botão com base no valor selecionado de um campo. Para fazer isso, você precisa criar uma medida que gere a cadeia de caracteres desejada com base na função DAX SELECTEDVALUE.

Veja uma medida de exemplo que vai gerar “Ver detalhes de produto” se um único valor Produto NÃO estiver selecionado; caso contrário, ela vai gerar “Ver detalhes para [o Produto selecionado]”:

```
String_for_button = If(SELECTEDVALUE('Product'[Product], 0) == 0), "See product details", "See details for " & SELECTEDVALUE('Product'[Product]))
```

Depois de criar essa medida, selecione a opção **Formatação condicional** do texto do botão:

![Selecione a Formatação condicional](media/desktop-drill-through-buttons/power-bi-button-conditional-tooltip.png)

Em seguida, selecione a medida que você criou para o texto do botão:

![Valor baseado em campo](media/desktop-drill-through-buttons/power-bi-conditional-measure.png)

Quando um único produto está selecionado, no texto do botão se lê:

"Ver detalhes para Word"

![Quando um único valor é selecionado](media/desktop-drill-through-buttons/power-bi-conditional-button-text.png)

Quando nenhum produto está selecionado ou mais de um produto está selecionado, o botão é desabilitado e no texto dele se lê:

"Ver detalhes do produto"

![Quando vários valores estão selecionados](media/desktop-drill-through-buttons/power-bi-button-conditional-text-2.png)

## <a name="pass-filter-context"></a>Passar contexto do filtro

O botão funciona como um drill-through normal, de modo que você também pode passar filtros em campos adicionais realizando filtragem cruzada dos visuais que contêm o campo de drill-through. Por exemplo, usando **Ctrl** + **clique** e a filtragem cruzada, você pode passar vários filtros na Loja para a página de drill-through porque suas seleções realizam filtragem cruzada com o visual que contém o Produto, o campo de drill-through:

![Passar contexto de filtro](media/desktop-drill-through-buttons/power-bi-cross-filter-drill-through-button.png)

Ao selecionar o botão de drill-through, você vê filtros na Loja e no Produto sendo passados por meio da página de destino:

![Filtros nesta página](media/desktop-drill-through-buttons/power-bi-button-filters-passed-through.png)

### <a name="ambiguous-filter-context"></a>Contexto de filtro ambíguo

Como o botão de drill-through não está vinculado a um único visual, se a sua seleção for ambígua, o botão será desabilitado.

Neste exemplo, o botão está desabilitado porque dois visuais contêm uma única seleção no Produto. Há uma ambiguidade sobre qual ponto de dados de qual visual para associar a ação de drill-through para:

![Contexto de filtro ambíguo](media/desktop-drill-through-buttons/power-bi-button-disabled-ambiguity.png)

## <a name="limitations"></a>Limitações

- Esse botão não permite vários destinos usando um único botão.
- Esse botão só dá suporte a drill-throughs dentro do mesmo relatório; em outras palavras, ele não dá suporte ao drill-through de relatório cruzado.
- A formatação de estado desabilitada para o botão está associada às classes de cor em seu tema de relatório. Saiba mais sobre [classes de cor](desktop-report-themes.md#setting-structural-colors).
- A ação de drill-through funciona para todos os visuais internos e com *alguns* visuais importados do AppSource. No entanto, não há garantia de que funcione com *todos* os visuais importados do AppSource.

## <a name="next-steps"></a>Próximas etapas
Para obter mais informações sobre os recursos que são semelhantes ou interagem com botões, consulte os seguintes artigos:

* [Criar botões](desktop-buttons.md)
* [Usar o drill-through nos relatórios do Power BI](desktop-drillthrough.md)
* [Usar indicadores para compartilhar insights e criar histórias no Power BI](desktop-bookmarks.md)

