---
title: Usar o mecanismo de computação aprimorado com fluxos de dados
description: Saiba como usar o mecanismo de computação aprimorado no Power BI Premium com fluxos de dados
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 01/08/2020
ms.author: davidi
LocalizationGroup: Data from files
ms.openlocfilehash: 1d2bd150d33d95f2ec8759f9e876b3920eede3b6
ms.sourcegitcommit: 4b926ab5f09592680627dca1f0ba016b07a86ec0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75840060"
---
# <a name="the-enhanced-compute-engine"></a>O mecanismo de computação aprimorado

O mecanismo de computação aprimorado do Power BI permite que os assinantes do Power BI Premium usem a capacidade de otimizar o uso de fluxos de dados. O uso do mecanismo de computação aprimorado oferece as seguintes vantagens:

* Reduz drasticamente o tempo de atualização necessário para etapas de ETL de longa execução em entidades computadas, como a execução de operações de *junções*, *contagens distintas*, *filtros* e *agrupar por*
* Executar consultas do DirectQuery em entidades (em fevereiro de 2020)

As seções a seguir descrevem como habilitar o mecanismo de computação aprimorado e responder a perguntas comuns.


## <a name="using-the-enhanced-compute-engine"></a>Com usar o mecanismo de computação aprimorado

O mecanismo de computação aprimorado é habilitado na página **Configurações de Capacidade** do serviço do Power BI, na seção **Fluxos de dados**. Por padrão, o mecanismo de computação aprimorado está **Desativado**. Para ativá-lo, **ative** a alternância, conforme mostrado na imagem a seguir, e salve as configurações. 

![Ativar o mecanismo de computação aprimorado](media/service-dataflows-enhanced-compute-engine/enhanced-compute-engine-01.png)

Depois de ativar o mecanismo de computação aprimorado, retorne aos fluxos de entrada e você deverá ver uma melhoria no desempenho de qualquer entidade computada que execute operações complexas, como *junções* ou *agrupar por*, para fluxos de dados criados com base nas entidades vinculadas existentes na mesma capacidade. 

Para fazer o melhor uso do mecanismo de computação, você deverá dividir o estágio de ETL em dois fluxos de dados separados da seguinte maneira:

* **Fluxo de dados 1**: esse fluxo de dados só deverá ingerir tudo o que é necessário de uma fonte de dados e colocá-la no fluxo de dados 2.
* **Fluxo de dados 2**: execute todas as operações de ETL nesse segundo fluxo de dados, mas referencie o fluxo de dados 1, que deverá estar na mesma capacidade. Além disso, execute primeiro as operações que podem ser particionadas (filtrar, agrupar por, contagem distinta, junção) antes de qualquer outra operação, a fim de garantir que o mecanismo de computação seja utilizado.

## <a name="common-questions-and-answers"></a>Perguntas comuns e respostas

**Pergunta:** Habilitei o mecanismo de computação aprimorado, mas minhas atualizações são mais lentas. Por que?

**Resposta:** Se você habilitar o mecanismo de computação aprimorado, haverá duas explicações possíveis que podem levar a tempos de atualização mais lentos:

 - Quando o mecanismo de computação aprimorado é habilitado, ele exige memória para funcionar corretamente. Assim, a memória disponível para executar uma atualização é reduzida e, portanto, aumenta a probabilidade de as atualizações serem colocadas na fila, o que, por sua vez, reduz o número de fluxos de dados que podem ser atualizados simultaneamente. Para resolver isso, ao habilitar a computação aprimorada, aumente a memória atribuída aos fluxos de dados, a fim de garantir que a memória disponível para as atualizações de fluxos de dados simultâneos permaneça a mesma.

 - Outro motivo que pode levar a atualizações mais lentas é que o mecanismo de computação funciona apenas nas entidades existentes e, se o fluxo de dados referenciar uma fonte de dados que não seja um fluxo de dados, você não verá nenhuma melhoria. Não haverá aumento de desempenho, pois, em alguns cenários de Big Data, a leitura inicial de uma fonte de dados será mais lenta, porque os dados precisam ser transmitidos para o mecanismo de computação aprimorado.  

**Pergunta:** Não consigo ver a alternância do mecanismo de computação aprimorado. Por que?

**Resposta:** O mecanismo de computação aprimorado está sendo lançado em estágios nas regiões em todo o mundo. Prevemos que todas as regiões terão suporte até o final de 2020.

**Pergunta:** Quais são os tipos de dados compatíveis com o mecanismo de computação?

**Resposta:** Atualmente, o mecanismo de computação aprimorado e os fluxos de dados dão suporte aos tipos de dados a seguir. Se o fluxo de dados não usar um dos seguintes tipos de dados, ocorrerá um erro durante a atualização:

* Data/Hora
* Número Decimal
* Texto
* Número inteiro
* Data/Hora/Fuso Horário
* Verdadeiro/Falso
* Data
* Hora

## <a name="next-steps"></a>Próximas etapas

Este artigo forneceu informações sobre como usar o mecanismo de computação aprimorado em fluxos de dados. Os seguintes artigos também podem ser úteis:

* [Preparação de dados de autoatendimento com fluxos de dados](service-dataflows-overview.md)
* [Criação e uso de fluxos de dados no Power BI](service-dataflows-create-use.md)
* [Como usar entidades computadas no Power BI Premium](service-dataflows-computed-entities-premium.md)
* [Recursos de desenvolvedor para fluxos de dados do Power BI](service-dataflows-developer-resources.md)

Confira mais informações sobre o Power Query e a atualização agendada nestes artigos:
* [Visão geral da Consulta no Power BI Desktop](desktop-query-overview.md)
* [Configuração de atualização agendada](refresh-scheduled-refresh.md)

Leia este artigo de visão geral para saber mais sobre o Common Data Service:
* [Common Data Service - visão geral ](https://docs.microsoft.com/powerapps/common-data-model/overview)

