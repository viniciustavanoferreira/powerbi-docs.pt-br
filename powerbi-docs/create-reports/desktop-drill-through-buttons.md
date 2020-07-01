---
title: Criar um botão de drill-through no Power BI
description: Você pode adicionar botões de drill-through em relatórios do Power BI que fazem seus relatórios se comportarem como aplicativos e aprofundarem o envolvimento com usuários.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 05/26/2020
ms.author: maggies
LocalizationGroup: Create reports
ms.openlocfilehash: a6de32e93b79b45d700ad5de1607f580dff836cf
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85239270"
---
# <a name="create-a-drill-through-button-in-power-bi"></a>Criar um botão de drill-through no Power BI

Você pode criar um botão de *detalhamento* no Power BI que faça o detalhamento em uma página com dados filtrados para um contexto específico.

Uma maneira de fazer o detalhamento em um relatório é clicar com o botão direito do mouse em um visual. Se você quiser que a ação de detalhar seja mais óbvia, poderá criar um botão para isso. Um botão pode aumentar a capacidade de descoberta de cenários de detalhamento importantes em seus relatórios. Você pode determinar condicionalmente grande parte do visual e da ação do botão. Por exemplo, você poderá mostrar texto diferente em um botão se determinadas condições forem atendidas. Leia para mais detalhes. 

Neste exemplo, depois que você selecionar a barra de palavras no gráfico, o botão **Ver detalhes** estará habilitado.

![Botão Ver detalhes](media/desktop-drill-through-buttons/power-bi-drill-through-visual-button.png)

Ao selecionar o botão **Ver detalhes**, você detalhará a página Análise da cesta de compras. Como você pode ver no visual à esquerda, a página de drill-through agora está filtrada para o Word.

![Visual filtrado](media/desktop-drill-through-buttons/power-bi-drill-through-destination.png)

## <a name="set-up-a-drill-through-button"></a>Configurar um botão de drill-through

Para configurar um botão de drill-through, primeiro você precisa [configurar uma página de drill-through válida](desktop-drillthrough.md) dentro do seu relatório. Em seguida, você precisará criar um botão com **Executar consulta drill-through** como o tipo de ação e selecionar a página de drill-through como o **Destino**.

Como o botão de detalhamento tem dois estados (habilitado versus desabilitado), você vê duas opções de dica de ferramenta.

![Configurar o botão de drill-through](media/desktop-drill-through-buttons/power-bi-create-drill-through-button.png)

Se você deixar as caixas de dicas de ferramenta em branco, o Power BI vai gerar automaticamente as dicas de ferramenta. Essas dicas de ferramenta são baseadas nos campos de destino e drill-through.

Veja um exemplo da dica de ferramenta gerada automaticamente quando o botão é desabilitado:

"Para detalhar a Análise da cesta de compras (a página de destino), selecione um único ponto de dados do produto (o campo de detalhamento)."

![Dica de ferramenta gerada automaticamente desabilitada](media/desktop-drill-through-buttons/power-bi-drill-through-tooltip-disabled.png)

Além disso, veja um exemplo da dica de ferramenta gerada automaticamente quando o botão é habilitado:

"Clique para detalhar a Análise da cesta de compras (a página de destino)."

![Dica de ferramenta gerada automaticamente habilitada](media/desktop-drill-through-buttons/power-bi-drill-through-visual-button.png)

No entanto, se você quiser fornecer dicas de ferramenta personalizadas, sempre poderá inserir uma cadeia de caracteres estática. Você também pode aplicar a [formatação condicional a dicas de ferramenta](#set-formatting-for-tooltips-conditionally).

## <a name="pass-filter-context"></a>Passar contexto do filtro

O botão funciona como o detalhamento regular: você pode passar filtros em campos adicionais realizando a filtragem cruzada dos visuais que contêm o campo de detalhamento. Por exemplo, usando **Ctrl** + **clique** e a filtragem cruzada, você pode passar vários filtros na Loja para a página de drill-through porque suas seleções realizam filtragem cruzada com o visual que contém o Produto, o campo de drill-through:

![Passar contexto de filtro](media/desktop-drill-through-buttons/power-bi-cross-filter-drill-through-button.png)

Após selecionar o botão de detalhamento, você vê filtros na Loja e no Produto sendo transmitidos por meio da página de destino:

![Filtros nesta página](media/desktop-drill-through-buttons/power-bi-button-filters-passed-through.png)

### <a name="ambiguous-filter-context"></a>Contexto de filtro ambíguo

Como o botão de drill-through não está vinculado a um único visual, se a sua seleção for ambígua, o botão será desabilitado.

Neste exemplo, o botão está desabilitado porque dois visuais contêm uma única seleção no Produto. Há uma ambiguidade sobre qual ponto de dados de qual visual para associar a ação de drill-through para:

![Contexto de filtro ambíguo](media/desktop-drill-through-buttons/power-bi-button-disabled-ambiguity.png)

## <a name="customize-formatting-for-disabled-buttons"></a>Personalizar a formatação de botões desabilitados
Você pode personalizar as opções de formatação para o estado desabilitado dos botões de detalhamento.


:::image type="content" source="media/desktop-drill-through-buttons/drill-through-customize-disabled-button.png" alt-text="Personalizar a formatação do botão desabilitado":::
 
Essas opções de formatação incluem:
- **Controles de texto do botão**: texto, cor, preenchimento, alinhamento, tamanho e família de fontes

    :::image type="content" source="media/desktop-drill-through-buttons/drill-through-disabled-button-text.png" alt-text="Formatar texto do botão desabilitado":::

- **Controles de preenchimento do botão**: cor, transparência e *nova* imagem de preenchimento (confira na próxima seção)

    :::image type="content" source="media/desktop-drill-through-buttons/drill-through-disabled-button-fill.png" alt-text="Preenchimento do botão desabilitado":::

- **Controles de ícone**: forma, preenchimento, alinhamento, cor da linha, transparência e peso

    :::image type="content" source="media/desktop-drill-through-buttons/drill-through-disabled-button-icon.png" alt-text="Ícones do botão desabilitado":::

- **Controles de contorno**: cor, transparência, peso, bordas arredondadas

     :::image type="content" source="media/desktop-drill-through-buttons/drill-through-disabled-button-outline.png" alt-text="Contorno do botão desabilitado":::

## <a name="set-formatting-for-button-text-conditionally"></a>Definir condicionalmente a formatação para o texto do botão
Você pode usar a formatação condicional para alterar o texto do botão com base no valor selecionado de um campo. Para fazer isso, você precisa criar uma medida que gere a cadeia de caracteres desejada com base na função DAX SELECTEDVALUE.

Veja uma medida de exemplo que vai gerar “Ver detalhes de produto” se um único valor Produto NÃO estiver selecionado; caso contrário, ela vai gerar “Ver detalhes para [o Produto selecionado]”:

```dax
String_for_button = If(SELECTEDVALUE('Product'[Product], 0) == 0, "See product details", "See details for " & SELECTEDVALUE('Product'[Product]))
```

Depois de criar essa medida, selecione a opção **Formatação condicional** do texto do botão:

![Selecione a Formatação condicional](media/desktop-drill-through-buttons/power-bi-button-conditional-tooltip.png)

Em seguida, selecione a medida que você criou para o texto do botão:

![Valor baseado em campo](media/desktop-drill-through-buttons/power-bi-conditional-measure.png)

Quando um único produto está selecionado, no texto do botão se lê:

"Ver detalhes para Word"

![Quando um único valor é selecionado](media/desktop-drill-through-buttons/power-bi-conditional-button-text.png)

Quando nenhum ou mais de um produto está selecionado, o botão é desabilitado. O texto do botão indica:

"Ver detalhes do produto"

![Quando vários valores estão selecionados](media/desktop-drill-through-buttons/power-bi-button-conditional-text-2.png)

## <a name="set-formatting-for-tooltips-conditionally"></a>Definir condicionalmente a formatação para dicas de ferramenta

Você poderá formatar condicionalmente a dica de ferramenta para o botão de detalhamento quando ele estiver habilitado ou desabilitado. Se você usou a formatação condicional para definir dinamicamente o destino do detalhamento, talvez queira que a dica de ferramenta para o estado do botão seja mais informativa, com base na seleção do usuário final. Aqui estão alguns exemplos:

- Você pode definir a dica de ferramenta de estado desabilitado para ser prescritiva dependendo do caso, usando uma medida personalizada. Por exemplo, se você quiser que o usuário selecione um único produto *e* uma única loja antes que possa detalhar a página Análise de mercado, poderá criar uma medida com a seguinte lógica:

    Se o usuário não tiver selecionado um único produto ou uma única loja, a medida retornará: "Selecione um único produto, Ctrl + clique para selecionar também uma única loja."

    Se o usuário tiver selecionado um único produto, mas não uma única loja, a medida retornará: "Ctrl + clique para selecionar também uma única loja."

- Da mesma forma, você pode definir a dica de ferramenta de estado habilitado para que seja específica da seleção do usuário. Por exemplo, se você quiser que o usuário saiba para qual produto e loja a página de detalhamento será filtrada, poderá criar uma medida que retorna:

    "Clique para detalhar o [nome da página de detalhamento] para ver mais detalhes sobre vendas do [nome do produto] em lojas [nome da loja]."


## <a name="set-the-drill-through-destination-conditionally"></a>Configurar o destino do detalhamento condicionalmente

Você pode usar a formatação condicional para definir o destino do detalhamento com base no resultado de uma medição.

Aqui estão alguns cenários em que você pode desejar que o botão de destino do detalhamento seja condicional:

- Convém habilitar o detalhamento de uma página **quando várias condições são atendidas**. Caso contrário, o botão será desabilitado.

    Por exemplo, você deseja que os usuários selecionem um único produto *e* uma única loja antes que possam detalhar a página de detalhes do mercado. Caso contrário, o botão será desabilitado.

    :::image type="content" source="media/desktop-drill-through-buttons/drill-through-select-product-store.png" alt-text="Selecionar um produto e uma loja":::
 
- Você deseja que o botão **dê suporte a vários destinos de detalhamento** com base nas seleções do usuário.

    Por exemplo, digamos que você tenha vários destinos (detalhes do mercado e detalhes da loja) que os usuários podem detalhar. Você pode fazer com que eles selecionem um destino específico para detalhar antes que o botão se torne habilitado para esse destino de detalhamento.

    :::image type="content" source="media/desktop-drill-through-buttons/drill-through-select-product-destination.png" alt-text="Selecionar produto e destino":::
 
- Você também pode ter **casos interessantes de um cenário híbrido** para dar suporte a vários destinos de detalhamento e condições específicas em que deseja que o botão seja desabilitado. Leia os detalhes sobre essas três opções.

### <a name="disable-the-button-until-multiple-conditions-are-met"></a>Desabilitar o botão até que várias condições sejam atendidas

Vamos examinar o primeiro caso, em que você deseja manter o botão desabilitado até que condições adicionais sejam atendidas. Você precisa criar uma medida DAX básica que produza uma cadeia de caracteres vazia (""), a menos que a condição tenha sido atendida. Quando é atendida, gera o nome da página de destino de detalhamento.

Aqui está um exemplo de medida DAX que requer a seleção de uma loja antes que o usuário possa detalhar um produto na página de detalhes da loja:

```dax
Destination logic = If(SELECTEDVALUE(Store[Store], “”)==””, “”, “Store details”)
```

Depois de criar essa medida, selecione o botão de formatação condicional (fx) ao lado de **Destino** para o botão:

:::image type="content" source="media/desktop-drill-through-buttons/drill-through-select-formula.png" alt-text="Selecionar o botão de formatação condicional":::
 
Para a última etapa, selecione a medida DAX criada como o valor de campo para o destino:

:::image type="content" source="media/desktop-drill-through-buttons/drill-through-based-formula.png" alt-text="Destino com base no campo"::: 

Agora você vê que o botão está desabilitado mesmo quando um único produto é selecionado porque a medida também exige que você selecione uma única loja:

:::image type="content" source="media/desktop-drill-through-buttons/drill-through-button-disabled.png" alt-text="Botão de detalhamento desabilitado":::

### <a name="support-multiple-destinations"></a>Suporte para vários destinos
 
Para o outro caso comum em que você deseja dar suporte a vários destinos, comece criando uma tabela de coluna única com os nomes dos destinos de detalhamento:

:::image type="content" source="media/desktop-drill-through-buttons/drill-through-create-table.png" alt-text="Criar uma tabela":::

O Power BI usa correspondência exata da cadeia de caracteres para definir o destino de detalhamento. Portanto, verifique novamente se os valores inseridos estão alinhados de forma exata com os nomes da página de detalhamento.

Depois de criar a tabela, adicione à página como uma segmentação de seleção única:

:::image type="content" source="media/desktop-drill-through-buttons/drill-through-slicer.png" alt-text="Segmentação do detalhamento":::
 
Se você precisar de mais espaço vertical, converta a segmentação em uma lista suspensa. Remova o cabeçalho da segmentação e adicione uma caixa de texto com o título ao lado:

:::image type="content" source="media/desktop-drill-through-buttons/drill-through-drop-down-slicer.png" alt-text="Segmentação do detalhamento sem cabeçalho":::
 
Como alternativa, altere a segmentação de lista da orientação vertical para horizontal:

:::image type="content" source="media/desktop-drill-through-buttons/drill-through-horizontal-slicer.png" alt-text="Segmentação horizontal":::

Para a entrada de destino da ação de detalhamento, selecione o botão de formatação condicional (fx) ao lado de **Destino** para o botão:

:::image type="content" source="media/desktop-drill-through-buttons/drill-through-select-formula.png" alt-text="Selecionar o botão de formatação condicional":::
 
Selecione o nome da coluna que você criou. Nesse caso, **Selecionar um destino**:

:::image type="content" source="media/desktop-drill-through-buttons/drill-through-select-destination.png" alt-text="Selecionar um destino":::
 
Agora, você vê que o botão de detalhamento só é habilitado com a seleção de um produto *e* um destino:

:::image type="content" source="media/desktop-drill-through-buttons/drill-through-select-product-destination.png" alt-text="Selecionar produto e destino":::
 
### <a name="hybrid-of-the-two-scenarios"></a>Híbrido dos dois cenários

Se você estiver interessado em um híbrido dos dois cenários, poderá criar e fazer referência a uma medida DAX para adicionar mais lógica à seleção de destino.

Aqui está um exemplo de medida DAX que requer que o usuário selecione uma loja antes que possa detalhar um produto em qualquer página de detalhamento:

```dax
Destination logic = If(SELECTEDVALUE(Store[Store], “”)==””, “”, SELECTEDVALUE(‘Table'[Select a destination]))
```

Selecione a medida DAX criada como o valor de campo para o destino.
Neste exemplo, o usuário precisaria selecionar um produto, uma loja *e* uma página de destino antes que o botão de detalhamento fosse habilitado:

:::image type="content" source="media/desktop-drill-through-buttons/drill-through-product-store-destination.png" alt-text="Selecionar produto, loja e destino":::

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

