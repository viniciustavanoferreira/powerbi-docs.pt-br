---
title: 'DAX: Referências de coluna e de medida'
description: Diretrizes sobre como se referir a colunas em medidas em suas expressões DAX.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 12/18/2019
ms.author: v-pemyer
ms.openlocfilehash: 3ca49008639f7e3e084c8d045bc911aff57b7b21
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/05/2020
ms.locfileid: "75498727"
---
# <a name="dax-column-and-measure-references"></a>DAX: Referências de coluna e de medida

Como um modelador de dados, suas expressões DAX se referirão a medidas e colunas de modelo. As medidas e colunas são sempre associadas a tabelas de modelo, mas essas associações são diferentes. Assim, temos recomendações diferentes sobre como você fará referência a elas em suas expressões.

## <a name="columns"></a>Colunas

Uma coluna é um objeto de nível de tabela e os nomes de coluna devem ser exclusivos em uma tabela. Portanto, é possível que o mesmo nome de coluna seja usado várias vezes em seu modelo, desde que essas colunas pertençam a tabelas diferentes. Há mais uma regra: um nome de coluna não pode ter o mesmo nome que um nome de medida ou nome de hierarquia existente na mesma tabela.

Em geral, o DAX não forçará o uso de uma referência _totalmente qualificada_ para uma coluna. Uma referência totalmente qualificada significa que o nome da tabela precede o nome da coluna.

Aqui está um exemplo de uma definição de coluna calculada usando apenas referências de nome de coluna. As colunas **Vendas** e **Custo** pertencem a uma tabela chamada **Ordens**.

```dax
Profit = [Sales] - [Cost]
```

A mesma definição pode ser reescrita com referências de coluna totalmente qualificadas.

```dax
Profit = Orders[Sales] - Orders[Cost]
```

Às vezes, no entanto, será necessário usar referências de coluna totalmente qualificadas quando o Power BI detectar alguma ambiguidade. Se isso ocorrer ao inserir uma fórmula, você será alertado por um ondulado vermelho e uma mensagem de erro. Além disso, algumas funções DAX, como a função DAX [LOOKUPVALUE](/dax/lookupvalue-function-dax), exigem o uso de colunas totalmente qualificadas.

Recomendamos que você sempre qualifique totalmente suas referências de coluna. Os motivos são fornecidos na seção [Recomendações](#recommendations).

## <a name="measures"></a>Medidas

Uma medida é um objeto de nível de modelo. Por esse motivo, os nomes de medidas devem ser exclusivos no modelo. No entanto, no painel **Campos**, os autores de relatório verão cada medida associada a uma única tabela de modelo. Essa associação é definida por motivos superficiais e você pode configurá-la definindo a propriedade **Tabela Inicial** para a medida. Para obter mais informações, confira [Medidas no Power BI Desktop (organizando suas medidas)](../desktop-measures.md#organizing-your-measures).

É possível usar uma medida totalmente qualificada em suas expressões. O IntelliSense do DAX oferecerá até mesmo a sugestão de fazê-lo. No entanto, isso não é necessário e não é uma prática recomendada. Se você alterar a tabela inicial de uma medida, qualquer expressão que usar uma referência de medida totalmente qualificada para ela será interrompida. Em seguida, você precisará editar cada fórmula quebrada para remover (ou atualizar) a referência de medida.

Recomendamos que você nunca qualifique suas referências de medida. Os motivos são fornecidos na seção [Recomendações](#recommendations).

## <a name="recommendations"></a>Recomendações

Nossas recomendações são simples e fáceis de lembrar:

- Sempre usar referências de coluna totalmente qualificadas
- Nunca usar referências de medida totalmente qualificadas

Eis o motivo:

- **Entrada de fórmula**: as expressões serão aceitas, pois não haverá referências ambíguas a serem resolvidas. Além disso, você atenderá ao requisito para as funções DAX que exigem referências de coluna totalmente qualificadas.
- **Robustez**: as expressões continuarão a funcionar, mesmo quando você alterar uma propriedade de tabela inicial de uma medida.
- **Legibilidade**: as expressões serão rápidas e fáceis de entender. Você determinará rapidamente se é uma coluna ou uma medida, pois saberá se ela é totalmente qualificada ou não.

## <a name="next-steps"></a>Próximas etapas

Para obter mais informações sobre este artigo, confira os seguintes recursos:

- [Referência do DAX (Data Analysis Expressions)](/dax/)
- Dúvidas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
