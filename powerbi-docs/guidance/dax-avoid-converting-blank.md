---
title: 'DAX: Evite converter BLANKs em valores'
description: Orientações sobre como converter BLANKs em valores.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/24/2019
ms.author: v-pemyer
ms.openlocfilehash: aea24e96acadbf9fee9e6dbf3aa395e09ef8e541
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83279631"
---
# <a name="dax-avoid-converting-blanks-to-values"></a>DAX: Evite converter BLANKs em valores

Como modelador de dados, ao escrever expressões de medida, você pode se deparar com casos em que um valor significativo não pode ser retornado. Nesses casos, você pode se sentir tentado a retornar um valor, como zero. Sugerimos que você determine cuidadosamente se esse design é eficiente e prático.

Considere a seguinte definição de medida que converte explicitamente os resultados BLANK em zero.

```dax
Sales (No Blank) =
IF(
    ISBLANK([Sales]),
    0,
    [Sales]
)
```

Considere outra definição de medida que também converte explicitamente resultados BLANK em zero.

```dax
Profit Margin =
DIVIDE([Profit], [Sales], 0)
```

A função [DIVIDE](/dax/divide-function-dax) divide a medida de **Lucro** pela medida de **Vendas**. Caso o resultado seja zero ou BLANK, o terceiro argumento — o resultado alternativo (que é opcional) — será retornado. Neste exemplo, como zero é passado como resultado alternativo, a medida sempre retornará um valor.

Esses designs de medida são ineficientes e levam a designs de relatório insatisfatórios.

Quando eles são adicionados a um visual de relatório, o Power BI tenta recuperar todos os agrupamentos dentro do contexto de filtro. A avaliação e a recuperação de resultados de consulta grandes geralmente resultam em lentidão na renderização do relatório. Cada medida de exemplo transforma efetivamente um cálculo esparso em um denso, forçando o Power BI a usar mais memória do que o necessário.

Além disso, ter muitos agrupamentos muitas vezes sobrecarrega os usuários do relatório.

Vejamos o que acontece quando a medida de **Margem** de lucro é adicionada a um visual de tabela, agrupando por cliente.

![Um visual de tabela tem três colunas: Cliente, Vendas e Margem de lucro. A tabela exibe cerca de 10 linhas de dados, mas a barra de rolagem vertical indica que há muitas linhas que podem ser exibidas. A coluna Vendas não exibe nenhum valor. A coluna Margem de lucro exibe apenas zero.](media/dax-avoid-converting-blank/table-visual-poor.png)

O visual da tabela exibe um número enorme de linhas. (Na verdade, há 18.484 clientes no modelo e, portanto, a tabela tenta exibir todos eles.) Observe que os clientes do modo de exibição não tiveram nenhuma venda. Ainda assim, como a medida **Margem de lucro** sempre retorna um valor, eles são exibidos.

> [!NOTE]
> Quando há muitos pontos de dados a serem exibidos em um visual, o Power BI pode usar estratégias de redução de dados para remover ou resumir resultados de consultas grandes. Para obter mais informações, confira [Limites de ponto de dados e estratégias por tipo de visual](../visuals/power-bi-data-points.md).

Vejamos o que acontece quando a definição da medida **Margem de lucro** é aprimorada. Agora, ela retorna um valor somente quando a medida **Vendas** não é BLANK (nem zero).

```dax
Profit Margin =
DIVIDE([Profit], [Sales])
```

O visual de tabela agora exibe somente os clientes que fizeram vendas no contexto de filtro atual. A medida aprimorada resulta em uma experiência mais eficiente e prática para os usuários de seu relatório.

![O mesmo visual de tabela agora exibe quatro linhas de dados. Cada linha é referente a um cliente que tem um valor de vendas, e os valores de Margem de lucro são diferentes de zero.](media/dax-avoid-converting-blank/table-visual-good.png)

> [!TIP]
> Quando necessário, você pode configurar um visual para exibir todos os agrupamentos (que retornam valores ou BLANK) dentro do contexto de filtro habilitando a opção [Mostrar Itens Sem Dados](../create-reports/desktop-show-items-no-data.md).

## <a name="recommendation"></a>Recomendação

Recomendamos que suas medidas retornem BLANK quando um valor significativo não puder ser retornado.

Essa abordagem de design é eficiente, permitindo que o Power BI renderize relatórios mais rapidamente. Além disso, retornar BLANK é melhor porque os visuais de relatório eliminam, por padrão, os agrupamentos quando os resumos são BLANK.

## <a name="next-steps"></a>Próximas etapas

Para obter mais informações sobre este artigo, confira os seguintes recursos:

- [Referência do DAX (Data Analysis Expressions)](/dax/)
- Dúvidas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)

