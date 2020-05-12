---
title: P e R de limitações do Power BI
description: Limitações atuais de P e R do Power BI
author: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/21/2020
ms.author: maggies
ms.openlocfilehash: b71fd2986fb79adf88493416ac8234f2656aefa9
ms.sourcegitcommit: a199dda2ab50184ce25f7c9a01e7ada382a88d2c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82866761"
---
# <a name="limitations-of-power-bi-qa"></a>P e R de limitações do Power BI

A P e R do Power BI atualmente tem algumas limitações.

## <a name="data-sources"></a>Fontes de dados

### <a name="supported-data-sources"></a>Fontes de dados com suporte

A P e R do Power BI oferece suporte às seguintes configurações de fontes de dados no serviço do Power BI:

- Modo de importação
- Live Connect para Azure Analysis Services
- Conexão dinâmica com o SQL Server Analysis Services (com um gateway)
- Conjuntos de dados do Power BI.

Em cada uma dessas configurações, também há suporte para segurança em nível de linha.

### <a name="data-sources-not-supported"></a>Não há suporte para fontes de dados

No momento, P e R do Power BI não oferece suporte às seguintes configurações:

- Segurança em nível de objeto com qualquer tipo de fonte de dados
- DirectQuery com relação a qualquer fonte. Uma solução alternativa é usar a conexão dinâmica com o Azure Analysis Services, que usa o DirectQuery.
- Modelos compostos
- Reporting Services 

## <a name="tooling-limitations"></a>Limitações de ferramentas

A nova caixa de diálogo de ferramentas permite que os usuários personalizem e aprimorem a linguagem natural em P e R. Para saber mais sobre ferramentas, leia a [introdução a ferramentas de P e R](q-and-a-tooling-intro.md).

## <a name="review-question-limitations"></a>Limitações de perguntas de revisão

As perguntas de revisão armazenam apenas as perguntas feitas em relação a seu modelo de dados por até 28 dias. Ao usar a nova funcionalidade de perguntas de revisão, você pode notar que algumas perguntas não são registradas. Por concepção, elas não são registradas, pois o mecanismo de linguagem natural executa uma série de etapas de limpeza de dados para garantir que cada tecla pressionada por um usuário não seja gravada nem exibida.

Os administradores do locatário podem usar as configurações de administração de locatário para gerenciar a capacidade de armazenar perguntas. As permissões são baseadas em grupos de segurança. 

Os usuários também podem impedir que suas perguntas sejam registradas selecionando **Configurações** > **Geral** e desmarcando **Permitir P e R para registrar meu enunciado**. 

## <a name="teach-qa-limitations"></a>Limitações do recurso Ensinar P e R

O recurso Ensinar P e R permite que você corrija dois tipos de erros:

- Atribuir uma palavra a um campo.
- Atribuir uma condição de filtro a uma palavra.

No momento, não há suporte para a redefinição de um termo reconhecido nem para a definição de outros tipos de condições ou frases. Além disso, ao definir condições de filtragem, você só pode usar um subconjunto limitado de linguagem, incluindo:

- País, que é EUA
- País, que não é EUA
- Produtos > 100
- Produtos maior que 100
- Produtos = 100
- Produtos é igual a 100
- Produtos < 100
- Produtos menor que 100

> [!NOTE]
> A Ferramenta de P e R só dá suporte ao modo de importação. Ela ainda não dá suporte para a conexão a uma fonte de dados local ou Azure Analysis Services. Essa limitação atual será removida nas versões subsequentes do Power BI.

### <a name="statements-not-supported"></a>Instruções sem suporte

- No momento, não há suporte para o uso de medidas em condições. Em vez disso, converta medidas em colunas calculadas para fazê-las funcionar.
- Não há suporte para várias condições. Como uma solução alternativa, crie uma coluna calculada DAX que avalie um Booliano de instrução de várias condições e use esse campo em vez disso.
- Se você não especificar uma condição de filtro quando P e R solicitar um subconjunto de dados, não será possível salvar a definição, mesmo que a instrução inteira não tenha sublinhados em vermelho.

## <a name="next-steps"></a>Próximas etapas

Há diversas melhores práticas para melhorar o mecanismo de linguagem natural. Para obter mais informações, confira as [Melhores práticas de P e R](q-and-a-best-practices.md).