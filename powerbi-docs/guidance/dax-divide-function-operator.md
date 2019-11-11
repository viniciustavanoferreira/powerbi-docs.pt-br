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
ms.openlocfilehash: c96518bb8de7f323b51a7e1e3f34f9d9bf056c79
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/09/2019
ms.locfileid: "73875380"
---
# <a name="dax-divide-function-vs-divide-operator-"></a>DAX: Função DIVIDE versus operador dividir (/)

Este artigo destina-se a modeladores de dados que definem expressões DAX.

## <a name="background"></a>Tela de fundo

Ao escrever uma expressão DAX para dividir um numerador por um denominador, você pode optar por usar a função [DIVIDE](/dax/divide-function-dax) ou o operador de divisão (/ – barra).

Ao usar a função DIVIDE, você deve passar as expressões de numerador e denominador. Opcionalmente, você pode passar um valor que represente um resultado alternativo.

```dax

DIVIDE(<numerator>, <denominator> [,<alternateresult>])

```

A função DIVIDE foi projetada para lidar automaticamente com casos de divisão por zero. Se um resultado alternativo não for passado e o denominador for zero ou ficar EM BRANCO, a função retornará EM BRANCO. Se um resultado alternativo for passado, ele será retornado, em vez de EM BRANCO.

A função de divisão é conveniente porque poupa sua expressão de primeiro testar o valor do denominador. A função também é otimizada para testar o valor do denominador, em vez da função [IF](/dax/if-function-dax). O ganho de desempenho é significativo, já que a verificação para divisão por zero é dispendiosa. Usar DIVIDE também leva a uma expressão mais concisa e elegante.

## <a name="example"></a>Exemplo

A expressão de medida a seguir produz uma divisão segura, mas envolve o uso de quatro funções DAX.

```dax

=IF(OR(ISBLANK([Sales]), [Sales] == 0), BLANK(), [Profit] / [Sales])

```

Essa expressão de medida leva ao mesmo resultado, embora mais eficiente e elegante.

```dax

=DIVIDE([Profit], [Sales])

```

## <a name="recommendations"></a>Recomendações

Recomendamos que você use a função DIVIDE sempre que o denominador for uma expressão que _poderia_ retornar zero ou EM BRANCO.

No caso de o denominador ser um valor constante, recomendamos usar o operador de divisão. Neste caso, a divisão tem sucesso garantido e sua expressão terá um desempenho melhor porque evitará testes desnecessários.

Você deve considerar cuidadosamente se a função DIVIDE deve retornar um valor alternativo. Para medidas, geralmente é um design melhor que elas retorna EM BRANCO. Isso ocorre porque os visuais de relatório eliminam por padrão os agrupamentos quando os resumos estão EM BRANCO. Isso permite que o visual se concentre em grupos nos quais existem dados. Quando necessário, você pode configurar o visual para exibir todos os grupos (que retornam valores ou EM BRANCO) dentro do contexto de filtro habilitando a opção "Mostrar Itens Sem Dados".
