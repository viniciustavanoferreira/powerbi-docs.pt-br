---
title: 'DAX: Usar SELECTEDVALUE em vez de VALUES'
description: Orientações sobre como usar as funções SELECTEDVALUE.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/20/2019
ms.author: v-pemyer
ms.openlocfilehash: 6aef2c06cc62668ea7dea9fe404e294d1a5faa93
ms.sourcegitcommit: 8e3d53cf971853c32eff4531d2d3cdb725a199af
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/04/2020
ms.locfileid: "74700468"
---
# <a name="dax-use-selectedvalue-instead-of-values"></a>DAX: Usar SELECTEDVALUE em vez de VALUES

Como modelador de dados, às vezes você pode precisar escrever uma expressão DAX que testa se uma coluna é filtrada por um valor específico.

Em versões anteriores do DAX, esse requisito era alcançado com segurança usando um padrão envolvendo três funções DAX. As funções são [IF](/dax/if-function-dax), [HASONEVALUE](/dax/hasonevalue-function-dax) e [VALUES](/dax/values-function-dax). A definição de medida a seguir é um exemplo. Ela calcula o valor do imposto sobre vendas, mas apenas para vendas feitas a clientes australianos.

```dax
Australian Sales Tax =
IF(
    HASONEVALUE(Customer[Country-Region]),
    IF(
        VALUES(Customer[Country-Region]) = "Australia",
        [Sales] * 0.10
    )
)
```

No exemplo, a função HASONEVALUE retorna TRUE somente quando um único valor filtra a coluna **País-Região**. Quando for TRUE, a função VALUES será comparada com o texto literal "Austrália". Quando a função VALUES retorna TRUE, a medida **Vendas** será multiplicada por 0,10 (representando 10%). Se a função HASONEVALUE retornar FALSE — porque mais de um valor filtra a coluna – a primeira função IF retornará BLANK.

O uso do HASONEVALUE é uma técnica defensiva. Isso é necessário porque é possível que vários valores filtrem a coluna **País-Região**. Nesse caso, a função VALUES retorna uma tabela com várias linhas. A comparação de uma tabela de várias linhas com um valor escalar resulta em um erro.

## <a name="recommendation"></a>Recomendação

Recomendamos que você use a função [SELECTEDVALUE](/dax/selectedvalue-function). Ele alcança o mesmo resultado que o padrão descrito neste artigo, mas de forma ainda mais eficiente e elegante.

Usando a função SELECTEDVALUE, a definição da medida de exemplo agora é reescrita.

```dax
Australian Sales Tax =
IF(
    SELECTEDVALUE(Customer[Country-Region]) = "Australia",
    [Sales] * 0.10
)
```

> [!TIP]
> É possível passar um valor de _resultado alternativo_ na função SELECTEDVALUE. O valor de resultado alternativo é retornado quando nenhum filtro — ou vários filtros — são aplicados à coluna.

## <a name="next-steps"></a>Próximas etapas

Para obter mais informações sobre este artigo, confira os seguintes recursos:

- [Referência do DAX (Data Analysis Expressions)](/dax/)
- Dúvidas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
