---
title: 'DAX: Evite usar FILTER como argumento de filtro'
description: Diretrizes sobre como usar a função FILTER como um argumento de filtro.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 12/30/2019
ms.author: v-pemyer
ms.openlocfilehash: 6abcb77e3eb534e8b5d20c1d5567c117cbb97ffe
ms.sourcegitcommit: 3d6b27e3936e451339d8c11e9af1a72c725a5668
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2020
ms.locfileid: "76161422"
---
# <a name="dax-avoid-using-filter-as-a-filter-argument"></a>DAX: Evite usar FILTER como argumento de filtro

Como modelador de dados, você frequentemente escreverá expressões DAX que precisam ser avaliadas em um contexto de filtro modificado. Por exemplo, você pode escrever uma definição de medida para calcular as vendas de "produtos de alta margem". Descreveremos esse cálculo mais adiante neste artigo.

> [!NOTE]
> Este artigo é especialmente relevante para cálculos de modelo que aplicam filtros a tabelas de importação.

As funções DAX [CALCULATE](/dax/calculate-function-dax) e [CALCULATETABLE](/dax/calculatetable-function-dax) são funções importantes e úteis. Elas permitem que você escreva cálculos que removem ou adicionam filtros ou modificam os caminhos das relações. Isso é feito com a transmissão dos argumentos de filtro, que são expressões boolianas, expressões de tabela ou funções de filtro especiais. Abordaremos apenas as expressões boolianas e de tabela neste artigo.

Considere a definição de medida a seguir, que calcula as vendas de produtos vermelhos usando uma expressão de tabela. Ela substituirá todos os filtros que possam ser aplicados à tabela **Product**.

```dax
Red Sales =
CALCULATE(
    [Sales],
    FILTER('Product', 'Product'[Color] = "Red")
)
```

A função CALCULATE aceita uma expressão de tabela retornada pela função DAX [FILTER](/dax/filter-function-dax), que avalia a expressão de filtro para cada linha da tabela **Produto**. Ela chega ao resultado correto: o resultado das vendas de produtos vermelhos. No entanto, isso pode ser alcançado de forma muito mais eficiente com uma expressão booliana.

Esta é uma definição de medida aprimorada, que usa uma expressão booliana em vez da expressão de tabela. A função [KEEPFILTERS](/dax/keepfilters-function-dax) DAX garante que quaisquer filtros existentes aplicados à coluna **Cores** são preservados e não substituídos.

```dax
Red Sales =
CALCULATE(
    [Sales],
    KEEPFILTERS('Product'[Color] = "Red")
)
```

Recomendamos que você transmita argumentos de filtro como expressões boolianas, sempre que possível. Isso porque as tabelas de modelo de importação são repositórios de coluna na memória. Elas são explicitamente otimizadas para filtrar colunas com eficiência dessa maneira.

No entanto, há restrições que se aplicam a expressões boolianas quando elas são usadas como argumentos de filtro. Elas:

- Não podem comparar colunas com outras colunas
- Não é possível referenciar uma medida
- Não podem usar funções CALCULATE aninhadas
- Não podem usar funções que examinam ou retornam uma tabela

Isso significa que você precisará usar expressões de tabela para requisitos de filtro mais complexos.

Considere agora outra definição de medida.

```dax
High Margin Product Sales =
CALCULATE(
    [Sales],
    FILTER(
        'Product',
        'Product'[ListPrice] > 'Product'[StandardCost] * 2
    )
)
```

A definição de um _produto de margem alta_ é aquela que tem um preço de lista que excede o dobro do custo padrão. Neste exemplo, a função FILTER precisa ser usada. Isso porque a expressão de filtro é muito complexa para uma expressão booliana.

Veja a seguir mais um exemplo. O requisito desta vez é calcular as vendas, mas apenas para os meses que obtiveram um lucro.

```dax
Sales for Profitable Months =
CALCULATE(
    [Sales],
    FILTER(
        VALUES('Date'[Month]),
        [Profit] > 0)
    )
)
```

Neste exemplo, a função FILTER também precisa ser usada. Isso porque ela exige a avaliação da medida **Profit** para eliminar os meses que não obtiveram um lucro. Não é possível usar uma medida em uma expressão booliana quando ela é usada como um argumento de filtro.

## <a name="recommendations"></a>Recomendações

Para obter o melhor desempenho, recomendamos que você use expressões boolianas como argumentos de filtro, sempre que possível.

Portanto, a função FILTER só deve ser usada quando necessário. Você pode usá-la para fazer comparações de colunas complexas de filtro. Essas comparações de coluna podem envolver:

- Medidas
- Outras colunas
- O uso da função DAX [OR](/dax/or-function-dax) ou do operador lógico OR (||)

## <a name="next-steps"></a>Próximas etapas

Para obter mais informações sobre este artigo, confira os seguintes recursos:

- [Referência do DAX (Data Analysis Expressions)](/dax/)
- [Funções de filtro (DAX)](/dax/filter-function-dax)
- Dúvidas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
