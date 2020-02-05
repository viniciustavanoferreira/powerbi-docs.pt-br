---
title: Formatação de tabela condicional no Power BI Desktop
description: Aplicar formatação personalizada a tabelas
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 12/26/2019
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: c79a8ddd68fa64b0a16663500a3f02e9a991835b
ms.sourcegitcommit: 8e3d53cf971853c32eff4531d2d3cdb725a199af
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/04/2020
ms.locfileid: "75730174"
---
# <a name="use-conditional-formatting-in-tables"></a>Usar a formatação condicional em tabelas 

Com a formatação condicional para tabelas no Power BI Desktop, você pode especificar cores de célula personalizadas, incluindo gradientes de cor, com base nos valores do campo. Você também pode representar valores de célula com barras de dados ou ícones de KPI ou como links da Web ativos. Você pode aplicar a formatação condicional a qualquer campo de texto ou de dados, desde que baseie a formatação em um campo que tenha valores numéricos, de nome de cor ou de código hexa ou de URL da Web. 

Para aplicar a formatação condicional, selecione uma visualização de **Tabela** ou **Matriz** no Power BI Desktop. Na seção **Campos** do painel **Visualizações**, clique com o botão direito do mouse ou selecione a seta para baixo ao lado do campo na lista **Valores** que deseja formatar. Selecione **Formatação condicional** e, em seguida, selecione o tipo de formatação a ser aplicado.

![Menu Formatação condicional](media/desktop-conditional-table-formatting/table-formatting-0-popup-menu.png)

> [!NOTE]
> A formatação condicional substitui qualquer cor da tela de fundo ou fonte personalizada aplicada à célula formatada condicionalmente.

Para remover a formatação condicional de uma visualização, selecione **Remover formatação condicional** do menu suspenso do campo e, em seguida, selecione o tipo de formatação a ser removido.

![Menu Remover formatação condicional](media/desktop-conditional-table-formatting/table-formatting-1-remove.png)

As seções a seguir descrevem cada uma das opções de formatação condicional. Você pode combinar mais de uma opção em uma só coluna de tabela.

## <a name="format-background-or-font-color"></a>Formatar tela de fundo ou a cor da fonte

Para formatar a cor da fonte ou da tela de fundo da célula, selecione **Formatação condicional** em um campo e, em seguida, selecione **Cor da tela de fundo** ou **Cor da fonte** no menu suspenso. 

![Selecionar Cor da tela de fundo ou Cor da fonte](media/desktop-conditional-table-formatting/table-formatting-1-color-by-rules-dialog.png)

A caixa de diálogo **Cor da tela de fundo** ou **Cor da fonte** será aberta, com o nome do campo que você está formatando no título. Depois de escolher as opções de formatação condicional, selecione **OK**. 

![Caixas de diálogo Cor da tela de fundo e Cor da fonte](media/desktop-conditional-table-formatting/table-formatting-2-diverging.png)

As opções **Cor da tela de fundo** e **Cor da fonte** são as mesmas, mas afetam a cor da tela de fundo e a cor da fonte da célula, respectivamente. Aplique a mesma formatação condicional ou outra à cor da fonte e à cor da tela de fundo de um campo. Se você definir a fonte e a tela de fundo de um campo com a mesma cor, a fonte será mesclada em segundo plano para que a coluna da tabela só mostre as cores.

## <a name="color-by-color-scale"></a>Cor por escala de cores

Para formatar a cor da tela de fundo ou da fonte da célula por escala de cores, no campo **Formatar por** da caixa de diálogo **Cor da tela de fundo** ou **Cor da fonte**, selecione **Escala de cores**. Em **Com base no campo**, selecione o campo no qual a formatação será baseada. Você pode basear a formatação no campo atual ou em qualquer campo do modelo que tenha dados numéricos ou de cores. 

Em **Resumo**, especifique o tipo de agregação que deseja usar para o campo selecionado. Em **Formatação padrão**, selecione uma formatação a ser aplicada aos valores em branco. 

Em **Mínimo** e **Máximo**, escolha se deseja aplicar o esquema de cores com base nos valores de campo mais baixos e mais altos ou nos valores personalizados inseridos. Clique na lista suspensa e selecione as amostras de cores que deseja aplicar aos valores mínimo e máximo. Marque a caixa de seleção **Divergente** para especificar também uma cor e um valor de **Centro**. 

![Definir a tela de fundo da célula com a escala de cores](media/desktop-conditional-table-formatting/table-formatting-1-diverging-table.png)

Uma tabela de exemplo com a formatação da tela de fundo de escala de cores na coluna **Acessibilidade** é semelhante a esta:

![Tabela de exemplo com a escala de cores da tela de fundo divergente](media/desktop-conditional-table-formatting/table-formatting-1-apply-color-to.png)

A tabela de exemplo com a formatação da fonte de escala de cores na coluna **Acessibilidade** é semelhante a esta:

![Tabela de exemplo com a escala de cores da fonte divergente](media/desktop-conditional-table-formatting/table-formatting-2-table.png)

## <a name="color-by-rules"></a>Colorir segundo regras

Para formatar a cor da tela de fundo ou da fonte da célula por regras, no campo **Formatar por** da caixa de diálogo **Cor da tela de fundo** ou **Cor da fonte**, selecione **Regras**. Novamente, **Com base no campo** mostra o campo no qual a formatação será baseada e **Resumo** mostra o tipo de agregação para o campo. 

Em **Regras**, insira um ou mais intervalos de valores e defina uma cor para cada um. Cada intervalo de valor tem uma condição de *valor If*, uma condição de valor *and* e uma cor. As fontes ou as telas de fundo da célula em cada intervalo de valores são coloridas com a cor especificada. O seguinte exemplo apresenta três regras:

![Colorir segundo regras](media/desktop-conditional-table-formatting/table-formatting-1-color-by-rules-if-value.png)

Uma tabela de exemplo com a formatação da cor da tela de fundo baseada em regras na coluna **Acessibilidade** é semelhante a esta:

![Tabela de exemplo com Colorir por regras](media/desktop-conditional-table-formatting/table-formatting-1-color-by-rules-table.png)

## <a name="color-by-color-values"></a>Cor por valores de cor

Se você tiver um campo ou uma medida com os dados de valores hexa ou de nomes de cor, use a formatação condicional para aplicar automaticamente essas cores à cor da tela de fundo ou da fonte de uma coluna. Use também uma lógica personalizada para aplicar cores à fonte ou à tela de fundo.

O campo pode usar qualquer valor de cor listado na especificação de cores CSS em [https://www.w3.org/TR/css-color-3/](https://www.w3.org/TR/css-color-3/). Esses valores de cores podem incluir:
- Códigos hexa de 3, 6 ou 8 dígitos, por exemplo, #3E4AFF. Verifique se você incluiu o símbolo # no início do código. 
- Valores RGB ou RGBA, como RGBA(234, 234, 234, 0,5).
- Valores HSL ou HSLA, como HSLA (123, 75%, 75%, 0,5).
- Nomes de cores, como Green, SkyBlue ou PeachPuff. 

A seguinte tabela tem um nome de cor associado a cada estado: 

![Tabela State com nomes das cores](media/desktop-conditional-table-formatting/conditional-table-formatting_01.png)

Para formatar a coluna **Cor** com base nos valores de campo, selecione **Formatação condicional** para o campo **Cor** e, em seguida, **Cor da tela de fundo** ou **Cor da fonte**. 

Na caixa de diálogo **Cor da tela de fundo** ou **Cor da fonte**, selecione **Valor do campo** no campo suspenso **Formatar por**.

![Formatar por valor Campo](media/desktop-conditional-table-formatting/conditional-table-formatting_02.png)

Uma tabela de exemplo com a formatação da cor de **Cor da tela de fundo** baseada no valor do campo no campo **Cor** é semelhante a esta:

![Tabela de exemplo com a formatação da tela de fundo por valor de campo](media/desktop-conditional-table-formatting/conditional-table-formatting_03.png)

Se você também usar **Valor do campo** para formatar a **Cor da fonte** da coluna, o resultado será uma cor sólida na coluna **Cor**:

![Formatar a fonte e a tela de fundo por valor de campo](media/desktop-conditional-table-formatting/conditional-table-formatting_04.png)

## <a name="color-based-on-a-calculation"></a>Cor baseada em um cálculo

Crie um cálculo DAX que produza valores diferentes com base nas condições da lógica de negócios selecionadas. A criação de uma fórmula DAX é geralmente mais rápida do que a criação de várias regras na caixa de diálogo de formatação condicional. 

Por exemplo, a seguinte fórmula DAX aplica valores de cores hexa a uma nova coluna **Classificação de acessibilidade**, com base nos valores existentes da coluna **Acessibilidade**:

![Cálculo DAX](media/desktop-conditional-table-formatting/conditional-table-formatting_05.png)

Para aplicar as cores, selecione a formatação condicional de **Cor da tela de fundo** ou **Cor da fonte** para a coluna **Acessibilidade** e baseie a formatação no **Valor do campo** da coluna **Classificação de acessibilidade**. 

![Basear a cor da tela de fundo em uma coluna calculada](media/desktop-conditional-table-formatting/conditional-table-formatting_06.png)

A tabela de exemplo com a cor da tela de fundo de **Acessibilidade** com base na **Classificação de acessibilidade** calculada é semelhante a esta:

![Tabela de exemplo com uma cor baseada em valor calculado](media/desktop-conditional-table-formatting/conditional-table-formatting_07.png)

Você pode criar muitas outras variações apenas usando a imaginação e um pouco do DAX.

## <a name="add-data-bars"></a>Adicionar barras de dados

Para mostrar barras de dados com base em valores de células, selecione **Formatação condicional** para o campo **Acessibilidade** e, em seguida, selecione **Barras de dados** no menu suspenso. 

Na caixa de diálogo **Barras de dados**, a opção **Mostrar somente a barra** está desmarcada por padrão e, portanto, as células da tabela mostram as barras e os valores reais. Para mostrar somente as barras de dados, marque a caixa de seleção **Mostrar somente a barra**.

Você pode especificar os valores **Mínimo** e **Máximo**, as cores da barra de dados e a direção e a cor do eixo. 

![Caixa de diálogo Barras de dados](media/desktop-conditional-table-formatting/table-formatting-3-default.png)

Com as barras de dados aplicadas à coluna **Acessibilidade**, a tabela de exemplo tem esta aparência:

![Tabela de exemplo com barras de dados](media/desktop-conditional-table-formatting/table-formatting-3-default-table-bars.png)

## <a name="add-icons"></a>Adicionar ícones

Para mostrar ícones com base em valores de células, selecione **Formatação condicional** para o campo e, em seguida, selecione **Ícones** no menu suspenso. 

Na caixa de diálogo **Ícones**, em **Formatar por**, selecione **Regras** ou **Valor do campo**. 

Para a formatação por regras, selecione um método **Com base em campo**, **Resumo**, **Layout do ícone**, **Alinhamento do ícone**, **Estilo** do ícone e uma ou mais **Regras**. Em **Regras**, insira uma ou mais regras com uma condição de *valor If* e uma condição de valor *and* e selecione um ícone a ser aplicado a cada regra. 

Para a formatação por valores de campo, selecione um método **Com base em campo**, **Resumo**, **Layout do ícone** e **Alinhamento do ícone**.

O seguinte exemplo adiciona ícones com base em três regras:

![Caixa de diálogo Ícones](media/desktop-conditional-table-formatting/table-formatting-1-default-table.png)

Selecione **OK**. Com os ícones aplicados à coluna **Acessibilidade** por regras, a tabela de exemplo terá esta aparência:

![Tabela de exemplo com ícones](media/desktop-conditional-table-formatting/table-formatting-1-default-dialog.png)

## <a name="format-as-web-urls"></a>Formatar como URLs da Web

Se você tiver uma coluna ou uma medida que contenha URLs de site, use a formatação condicional para aplicar essas URLs aos campos como links ativos. Por exemplo, a seguinte tabela tem uma coluna **Site** com URLs de site para cada estado:

![Tabela com uma coluna de URL da Web](media/desktop-conditional-table-formatting/table-formatting-1-diverging.png)

Para exibir cada nome de estado como um link ativo para o respectivo site, selecione **Formatação condicional** para o campo **Estado** e, em seguida, selecione **URL da Web**. Na caixa de diálogo **URL da Web**, em **Com base em campo**, selecione **Site** e, em seguida, **OK**. 

Com a formatação da **URL da Web** aplicada ao campo **Estado**, cada nome de estado é um link ativo para o respectivo site. A tabela de exemplo a seguir tem a formatação da **URL da Web** aplicada à coluna **Estado** e **Barras de dados** e uma **Formatação da tela de fundo** condicional aplicada à coluna **Acessibilidade**. 

![Tabela com a URL da Web, barras de dados e cor da tela de fundo](media/desktop-conditional-table-formatting/table-formatting-3-default-table.png)

## <a name="considerations-and-limitations"></a>Considerações e limitações
Há algumas considerações para ter em mente ao trabalhar com formatação condicional de tabelas:

- A formatação condicional aplica-se só aos valores de visuais de Tabela ou Matriz e não se aplica aos subtotais, aos totais gerais ou à linha **Total**. 
- Qualquer tabela que não tenha um agrupamento é exibida como uma só linha que não dá suporte à formatação condicional.
- Não será possível aplicar a formatação de gradiente com valores máximo/mínimo automáticos ou a formatação baseada em regra com as regras de percentual se os dados contiverem valores *NaN*. NaN significa "Não é um número", geralmente causado por um erro de divisão por zero. Você pode usar a [função DIVIDE() DAX](https://docs.microsoft.com/dax/divide-function-dax) para evitar esses erros.
- A formatação condicional precisa que uma agregação ou uma medida seja aplicada ao valor. É por isso que você vê 'Primeiro' ou 'Último' no exemplo de **Cor por valor**. Se você estiver criando seu relatório em um cubo multidimensional do Analysis Services, não poderá usar um atributo para formatação condicional, a menos que o proprietário do cubo tenha criado uma medida que forneça o valor.

## <a name="next-steps"></a>Próximas etapas

Para obter mais informações sobre a formatação de cores, confira [Dicas e truques para a formatação de cores no Power BI](visuals/service-tips-and-tricks-for-color-formatting.md)  

