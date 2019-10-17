---
title: 'DAX: Uso apropriado de funções de erro'
description: Orientação sobre quando usar as funções de erro do DAX.
author: peter-myers
manager: asaxton
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 09/26/2019
ms.author: v-pemyer
ms.openlocfilehash: 0855a9ee4c699c4a3b65e4331b5af2fa68a5610c
ms.sourcegitcommit: 5e277dae93832d10033defb2a9e85ecaa8ffb8ec
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72021058"
---
# <a name="dax-appropriate-use-of-error-functions"></a>DAX: Uso apropriado de funções de erro

Este artigo destina-se a modeladores de dados que definem expressões DAX.

## <a name="background"></a>Tela de fundo

Ao escrever uma expressão DAX que pode gerar um erro de tempo de avaliação, considere usar duas funções DAX úteis.

- A função [ISERROR](/dax/iserror-function-dax), que usa uma única expressão e retorna TRUE caso a expressão resulte em um erro.
- A função [IFERROR](/dax/iferror-function-dax), que usa duas expressões. Se a primeira expressão resultar em erro, o valor da segunda expressão será retornado. Essa é, de fato, uma implementação mais otimizada de aninhamento da função ISERROR em uma função [IF](/dax/if-function-dax).

Contudo, embora essas funções possam ser úteis e contribuir para a escrita de expressões fáceis de entender, elas também podem diminuir significativamente o desempenho dos cálculos. Isso ocorre porque essas funções aumentam o número de verificações de mecanismos de armazenamento necessárias.

Observe que a maioria dos erros de tempo de avaliação ocorrem devido a valores BLANKs ou zero ou devido à conversão de tipos de dados inválidos.

## <a name="recommendations"></a>Recomendações

É melhor evitar o uso das funções ISERROR e IFERROR. Em vez disso, aplique estratégias defensivas ao desenvolver o modelo e escrever expressões. Isso inclui:

- **Garantir o carregamento de dados de qualidade no modelo:** Use as transformações do Power Query para remover ou substituir valores inválidos ou que estejam faltando e para definir os tipos de dados corretos. Uma transformação do Power Query também pode ser usada para filtrar linhas quando ocorrerem erros, como a conversão de dados inválida.

    A qualidade dos dados também podem ser controlada com a definição da propriedade **Permite Valor Nulo** da coluna do modelo como Desativada, o que fará a atualização dos dados falhar quando valores BLANKs forem encontrados. Observe que, se essa falha ocorrer, os dados carregados como resultado de uma atualização bem-sucedida serão mantidos nas tabelas.
- **Usar a função IF:** A expressão de teste lógico da função IF pode ser usada para determinar a possibilidade de ocorrência de um erro. Assim como as funções ISERROR e IFERROR, essa função pode resultar em verificações adicionais do mecanismo de armazenamento, mas provavelmente terá melhor desempenho do que elas, uma vez que nenhum erro precisará ser gerado.
- **Usar funções tolerantes a erros:** Algumas funções DAX testarão e compensarão condições de erro. Essas funções permitem inserir um resultado alternativo a ser retornado. A função [DIVIDE](/dax/divide-function-dax) é um exemplo disso. Para obter orientações adicionais sobre essa função, leia o artigo [DAX: função DIVIDE vs. operador de divisão (/)](dax-divide-function-operator.md).

## <a name="example"></a>Exemplo

A seguinte expressão de medida testa se um erro seria gerado. Ela retorna BLANK nesse caso (o que ocorre quando você não fornece a função IF com uma expressão value-if-false).
```dax
= IF(ISERROR([Profit] / [Sales]))
```
A próxima versão da expressão de medida foi aprimorada usando a função IFERROR, em vez das funções IF e ISERROR.
```dax
= IFERROR([Profit] / [Sales], BLANK())
```
No entanto, essa versão final da expressão de medida leva ao mesmo resultado, embora de forma mais eficiente e elegante.
```dax
= DIVIDE([Profit], [Sales])
```