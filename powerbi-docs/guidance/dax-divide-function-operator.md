---
title: 'DAX: Função DIVIDE versus operador dividir (/)'
description: Orientação sobre quando usar a função de divisão DAX.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 09/09/2019
ms.author: v-pemyer
ms.openlocfilehash: 91acaa3a2252250e2a10674bae0e9be81f142696
ms.sourcegitcommit: f1f57c5bc6ea3057007ed8636ede50188ed90ce1
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74410931"
---
# <a name="dax-divide-function-vs-divide-operator-"></a>DAX: Função DIVIDE versus operador dividir (/)

Como modelador de dados, quando você escreve uma expressão DAX para dividir um numerador por um denominador, você pode optar por usar a função [DIVIDE](/dax/divide-function-dax) ou o operador de divisão (/ – barra).

Ao usar a função DIVIDE, você deve passar as expressões de numerador e denominador. Opcionalmente, você pode passar um valor que representa um _resultado alternativo_.

```dax
DIVIDE(<numerator>, <denominator> [,<alternateresult>])
```

A função DIVIDE foi criada para lidar automaticamente com casos de divisão por zero. Se um resultado alternativo não for passado e o denominador for zero ou ficar EM BRANCO, a função retornará EM BRANCO. Se um resultado alternativo for passado, ele será retornado, em vez de EM BRANCO.

A função de divisão é conveniente porque poupa sua expressão de primeiro testar o valor do denominador. A função também é otimizada para testar o valor do denominador, em vez da função [IF](/dax/if-function-dax). O ganho de desempenho é significativo, já que a verificação para divisão por zero é dispendiosa. Usar mais DIVIDE leva a uma expressão mais concisa e elegante.

## <a name="example"></a>Exemplo

A expressão de medida a seguir produz uma divisão segura, mas envolve o uso de quatro funções DAX.

```dax
Profit Margin =
IF(
    OR(
        ISBLANK([Sales]),
        [Sales] == 0
    ),
    BLANK(),
    [Profit] / [Sales]
)
```

Essa expressão de medida leva ao mesmo resultado, embora mais eficiente e elegante.

```dax
Profit Margin =
DIVIDE([Profit], [Sales])
```

## <a name="recommendations"></a>Recomendações

Recomendamos que você use a função DIVIDE sempre que o denominador for uma expressão que _poderia_ retornar zero ou EM BRANCO.

No caso de o denominador ser um valor constante, recomendamos usar o operador de divisão. Neste caso, a divisão tem sucesso garantido e sua expressão terá um desempenho melhor porque evitará testes desnecessários.

Considere cuidadosamente se a função DIVIDE deve retornar um valor alternativo. Para medidas, geralmente é um design melhor que elas retornam EM BRANCO. Retornar EM BRANCO é melhor porque os visuais de relatório eliminam, por padrão, os agrupamentos quando os resumos estão EM BRANCO. Isso permite que o visual se concentre em grupos nos quais existem dados. Quando necessário, você pode configurar o visual para exibir todos os grupos (que retornam valores ou EM BRANCO) dentro do contexto de filtro habilitando a opção "Mostrar Itens Sem Dados".

## <a name="next-steps"></a>Próximas etapas

Para obter mais informações sobre este artigo, confira os seguintes recursos:

- [Referência do DAX (Data Analysis Expressions)](/dax/)
- Dúvidas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
