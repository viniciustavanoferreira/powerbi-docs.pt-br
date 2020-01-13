---
title: Diretrizes de dobragem de consultas no Power BI Desktop
description: Diretrizes para obter a dobragem de consultas do Power Query no Power BI Desktop.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/09/2019
ms.author: v-pemyer
ms.openlocfilehash: e8123bba9f68305e1944dbfb280b5255e4fb9b48
ms.sourcegitcommit: ef9ab7c0d84b926094c33e8aa2765cd43b844314
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75622153"
---
# <a name="query-folding-guidance-in-power-bi-desktop"></a>Diretrizes de dobragem de consultas no Power BI Desktop

Este artigo se destina a modeladores de dados que estão desenvolvendo modelos no Power BI Desktop. Ele fornece diretrizes de melhor prática sobre quando e como obter a dobragem de consultas do Power Query.

A _dobragem de consultas_ é a capacidade de uma consulta do Power Query gerar uma única instrução de consulta que recupera e transforma dados de origem. Para obter mais informações, confira [dobragem de consultas do Power Query](/power-query/power-query-folding).

## <a name="guidance"></a>Diretrizes

As diretrizes de dobragem de consultas diferem com base no modo de modelo.

Para uma tabela de modo de armazenamento **DirectQuery** ou **Duplo**, a consulta de Power Query deve obter a dobragem de consultas.

Para uma tabela de **importação**, pode ser possível obter a dobragem de consultas. Quando a consulta é baseada em uma fonte relacional e uma única instrução SELECT pode ser construída, você obtém o _melhor desempenho de atualização de dados_ garantindo que a dobragem de consultas ocorra. Se o mecanismo de mashup do Power Query ainda for necessário para processar as transformações, você deverá se esforçar para minimizar o trabalho necessário, especialmente para grandes conjuntos de dados.

A lista com marcadores a seguir apresenta diretrizes específicas.

- **Delegue o máximo de processamento possível para a fonte de dados:** Quando não for possível dobrar todas as etapas de uma consulta do Power Query, descubra a etapa que impede a dobragem de consultas. Quando possível, mova as etapas posteriores mais para o início da sequência para que possam ser fatoradas na dobragem de consultas. Observe que o mecanismo de mashup do Power Query pode ser inteligente o suficiente para reordenar as etapas de consulta ao gerar a consulta de origem.

    Para uma fonte de dados relacional, se a etapa que impede que a dobragem de consultas seja alcançada em uma única instrução SELECT ou na lógica de um procedimento armazenado, considere usar uma consulta SQL nativa, conforme descrito a seguir.

- **Usar uma consulta SQL nativa**: quando uma consulta Power Query recupera dados de uma fonte relacional, é possível para algumas fontes usar uma consulta SQL nativa. A consulta pode, na verdade, ser qualquer instrução válida, incluindo uma execução de procedimento armazenado. Se a instrução produzir vários conjuntos de resultados, somente o primeiro será retornado. Os parâmetros podem ser declarados na instrução, e recomendamos que você use a função [Value.NativeQuery](/powerquery-m/value-nativequery) M. Essa função foi projetada para passar valores de parâmetro de maneira segura e conveniente. É importante entender que o mecanismo de mashup do Power Query não pode dobrar etapas de consulta posteriores e, portanto, você deve incluir toda a lógica de transformação (ou tanto dela quanto possível) na instrução de consulta nativa.

    Há duas considerações importantes que você precisa se lembrar ao usar consultas SQL nativas:

    - Para uma tabela de modelo DirectQuery, a consulta deve ser uma instrução SELECT e não pode usar CTEs (Expressões de Tabela Comuns) ou um procedimento armazenado.
    - A atualização incremental não pode usar uma consulta SQL nativa. Assim, ela forçaria o mecanismo de mashup do Power Query a recuperar todas as linhas de origem e, em seguida, aplicar filtros para determinar as alterações incrementais.

    > [!IMPORTANT]
    > Uma consulta SQL nativa pode potencialmente fazer mais do que recuperar dados. Qualquer instrução válida pode ser executada (e, possivelmente, várias vezes), incluindo uma que modifica ou exclui dados. É importante que você aplique o princípio de privilégios mínimos para garantir que a conta usada para acessar o banco de dados tenha permissão de leitura apenas para os dados necessários.

- **Preparar e transformar dados na fonte:** Quando você identificar que determinadas etapas de consulta do Power Query não podem ser dobradas, talvez seja possível aplicar as transformações na fonte de dados. As transformações podem ser obtidas escrevendo-se um modo de exibição de banco de dados que transforma de maneira lógica os dados de origem. Ou ainda preparando e materializando os dados fisicamente, antes do Power BI consultá-los. Um data warehouse relacional é um excelente exemplo de dados preparados, geralmente consistindo em fontes previamente integradas de dados organizacionais.

## <a name="next-steps"></a>Próximas etapas

Para obter mais informações sobre este artigo, confira os seguintes recursos:

- Artigo sobre o conceito de [Dobragem de consultas](/power-query/power-query-folding) do Power Query
- [Atualização incremental no Power BI Premium](../service-premium-incremental-refresh.md)
- Dúvidas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
