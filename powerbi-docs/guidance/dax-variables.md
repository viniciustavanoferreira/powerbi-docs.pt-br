---
title: 'DAX: Usar variáveis para melhorar as fórmulas'
description: Orientações sobre como usar variáveis em expressões DAX.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/23/2019
ms.author: v-pemyer
ms.openlocfilehash: f352cbbd7c42aa54ae876e73c0ed821eccda59c8
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/05/2020
ms.locfileid: "74700698"
---
# <a name="dax-use-variables-to-improve-your-formulas"></a>DAX: Usar variáveis para melhorar as fórmulas

Para um modelador de dados, escrever e depurar alguns cálculos DAX pode ser desafiador. É comum que requisitos de cálculos complexos envolvam escrever expressões compostas ou complexas. Expressões compostas podem envolver o uso de muitas funções aninhadas e, possivelmente, a reutilização da lógica de expressão.

Usar variáveis em suas fórmulas DAX ajuda você a escrever cálculos complexos e eficientes. As variáveis podem:

- [Melhorar o desempenho](#improve-performance)
- [Melhorar a legibilidade](#improve-readability)
- [Simplificar a depuração](#simplify-debugging)
- [Reduzir a complexidade](#reduce-complexity)

Neste artigo, demonstraremos os três primeiros benefícios usando uma medida de exemplo para o crescimento de vendas ano a ano (YoY). (A fórmula para o crescimento de vendas YoY é: vendas no período _menos vendas no mesmo período do ano anterior, _dividido por_ vendas para o mesmo período do ano anterior.)

Vamos começar com a definição da medida a seguir.

```dax
Sales YoY Growth % =
DIVIDE(
    ([Sales] - CALCULATE([Sales], PARALLELPERIOD('Date'[Date], -12, MONTH))),
    CALCULATE([Sales], PARALLELPERIOD('Date'[Date], -12, MONTH))
)
```

A medida produz o resultado correto, mas agora vamos ver como ela pode ser melhorada.

## <a name="improve-performance"></a>Melhorar o desempenho

Observe que a fórmula repete a expressão que calcula "o mesmo período no ano anterior". Essa fórmula não é eficiente, pois exige que o Power BI avalie a mesma expressão duas vezes. A definição da medida pode se tornar mais eficiente usando uma variável.

A definição de medida a seguir representa uma melhoria. Ela usa uma expressão para atribuir o resultado do "mesmo período do ano anterior" a uma variável chamada **SalesPriorYear**. Em seguida, a variável é usada duas vezes na expressão RETURN.

```dax
Sales YoY Growth % =
VAR SalesPriorYear =
    CALCULATE([Sales], PARALLELPERIOD('Date'[Date], -12, MONTH))
RETURN
    DIVIDE(([Sales] - SalesPriorYear), SalesPriorYear)
```

A medida continua produzindo o resultado correto e faz isso em cerca de metade do tempo de consulta.

## <a name="improve-readability"></a>Melhorar a legibilidade

Na definição de medida anterior, observe como a escolha do nome da variável torna a expressão RETURN mais simples de entender. A expressão é curta e autodescritiva.

## <a name="simplify-debugging"></a>Simplificar a depuração

As variáveis também podem ajudar a depurar uma fórmula. Para testar uma expressão atribuída a uma variável, você reescreve temporariamente a expressão RETURN para gerar a variável.

A definição de medida a seguir retorna apenas a variável **SalesPriorYear**. Observe como ele comenta a expressão RETURN pretendida. Essa técnica permite que você a reverta facilmente quando a depuração for concluída.

```dax
Sales YoY Growth % =
VAR SalesPriorYear =
    CALCULATE([Sales], PARALLELPERIOD('Date'[Date], -12, MONTH))
RETURN
    --DIVIDE(([Sales] - SalesPriorYear), SalesPriorYear)
    SalesPriorYear
```

## <a name="reduce-complexity"></a>Reduzir a complexidade

Em versões anteriores do DAX, ainda não havia suporte para variáveis. Expressões complexas que introduziam novos contextos de filtro precisavam usar as funções DAX [EARLIER](/dax/earlier-function-dax) ou [EARLIEST](/dax/earliest-function-dax) para referenciar contextos de filtro externos. Os modeladores de dados consideravam essas funções difíceis de entender e usar.

As variáveis sempre são avaliadas fora dos filtros que sua expressão RETURN aplica. Por esse motivo, quando você usa uma variável em um contexto de filtro modificado, ela chega ao mesmo resultado que a função EARLIEST. Portanto, o uso das funções EARLIER ou EARLIEST pode ser evitado. Isso significa que agora você pode escrever fórmulas que são menos complexas e mais fáceis de entender.

Considere a seguinte definição de coluna calculada adicionada à tabela **Subcategoria**. Ela avalia uma classificação para cada subcategoria de produto com base nos valores da coluna **Vendas da subcategoria**.

```dax
Subcategory Sales Rank =
COUNTROWS(
    FILTER(
        Subcategory,
        EARLIER(Subcategory[Subcategory Sales]) < Subcategory[Subcategory Sales]
    )
) + 1
```

A função EARLIER é usada para fazer referência ao valor da coluna **Vendas da subcategoria**_no contexto da linha atual_.

A definição da coluna calculada pode ser aprimorada usando uma variável em vez da função EARLIER. A variável **CurrentSubcategorySales** armazena o valor da coluna **Vendas da subcategoria**_no contexto da linha atual_ e a expressão RETURN a usa em um contexto de filtro modificado.

```dax
Subcategory Sales Rank =
VAR CurrentSubcategorySales = Subcategory[Subcategory Sales]
RETURN
    COUNTROWS(
        FILTER(
            Subcategory,
            CurrentSubcategorySales < Subcategory[Subcategory Sales]
        )
    ) + 1
```

## <a name="next-steps"></a>Próximas etapas

Para obter mais informações sobre este artigo, confira os seguintes recursos:

- Artigo sobre a [VAR](/dax/var-dax) de DAX
- Dúvidas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
