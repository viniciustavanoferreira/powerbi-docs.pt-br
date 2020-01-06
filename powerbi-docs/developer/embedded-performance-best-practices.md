---
title: Práticas recomendadas de desempenho do Power BI Embedded
description: Este artigo fornece uma orientação para as práticas recomendadas de análise integrada
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 12/12/2018
ms.openlocfilehash: c3e2327131ae82fa025236c9242476466b6d9074
ms.sourcegitcommit: 6272c4a0f267708ca7d38a45774f3bedd680f2d6
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/06/2020
ms.locfileid: "73864049"
---
# <a name="power-bi-embedded-performance-best-practices"></a>Práticas recomendadas de desempenho do Power BI Embedded

Este artigo fornece recomendações para renderização mais rápida de relatórios, painéis e blocos em seu aplicativo.

> [!Note]
> O tempo de carregamento depende principalmente dos elementos relevantes para o relatório e dos próprios dados, como visuais, tamanho e complexidade das consultas e medidas calculadas dos dados. Para saber mais, confira o tópico [Práticas recomendadas de desempenho do Power BI](../power-bi-reports-performance.md).

## <a name="update-tools-and-sdk-packages"></a>Atualizar ferramentas e pacotes SDK

Mantenha as ferramentas e os pacotes SDK atualizados.

* Use sempre a versão mais recente do [Power BI Desktop](https://powerbi.microsoft.com/desktop/).

* Instale a versão mais recente do [SDK cliente do Power BI](https://github.com/Microsoft/PowerBI-JavaScript). Estamos sempre lançando mais aprimoramentos, portanto dê uma conferida de vez em quando.

## <a name="embed-parameters"></a>Inserir parâmetros

O método `powerbi.embed(element, config)` recebe um elemento e uma configuração. O parâmetro de configuração inclui campos que afetam o desempenho.

### <a name="embed-url"></a>URL de inserção

Evite gerar a URL de inserção sozinho. Em vez disso, obtenha a URL de Inserção chamando a API [Obter relatórios](/rest/api/power-bi/reports/getreportsingroup), [Obter painéis](/rest/api/power-bi/dashboards/getdashboardsingroup) ou [Obter blocos](/rest/api/power-bi/dashboards/gettilesingroup). Adicionamos um novo parâmetro à URL chamado **_config_** , que é usado para aprimoramentos de desempenho.

### <a name="permissions"></a>Permissões

Forneça permissões de **Exibição**, caso prefira não inserir um relatório no modo de edição. Dessa forma, o código de inserção não inicializa componentes usados no modo de edição.

### <a name="filters-bookmarks-and-slicers"></a>Filtros, indicadores e segmentações

Normalmente, os visuais de relatório são salvos com os dados armazenados em cache. Os dados armazenados em cache são usados para oferecer desempenho percebido. Os relatórios renderizam dados armazenados em cache enquanto as consultas são executadas. Se forem fornecidos filtros, marcadores ou segmentação, os dados armazenados em cache não serão relevantes, e os visuais serão renderizados somente após o término da consulta visual.

Se você inserir relatórios com os mesmos filtros, indicadores e segmentações, salve o relatório com os filtros, indicadores e segmentações já aplicados a fim de melhorar o desempenho. Isso renderiza o relatório com os dados armazenados em cache, o que inclui os filtros, indicadores e as segmentações.

## <a name="switching-between-reports"></a>Como alternar entre relatórios

Se inserir vários relatórios no mesmo iframe, não gere um novo iframe para cada relatório. Em vez disso, use `powerbi.embed(element, config)` com uma configuração diferente para inserir o novo relatório.

> [!NOTE]
> A alternância entre relatórios em um cenário do tipo "o aplicativo possui dados" pode não ser muito eficaz devido à necessidade de gerar um novo token de inserção.

## <a name="query-caching"></a>Cache de consulta

As organizações com a capacidade do Power BI Premium ou do Power BI Embedded podem aproveitar o cache de consulta para acelerar os relatórios associados a um conjunto de dados.

[Saiba mais sobre o cache de consulta no Power BI](../power-bi-query-caching.md).

## <a name="preload"></a>Pré-carregamento

Use o `powerbi.preload()` para melhorar o desempenho do usuário final. O método `powerbi.preload()` baixa JavaScript, arquivos CSS e outros artefatos que são usados posteriormente para inserir um relatório.

Chame o `powerbi.preload()` se você não inserir o relatório imediatamente. Por exemplo, se o conteúdo do Power BI Embedded não aparecer na página inicial, use `powerbi.preload()` para baixar e armazenar em cache os artefatos usados para inserir o conteúdo.

## <a name="bootstrapping-the-iframe"></a>Como inicializar o iframe

> [!NOTE]
> É necessário ter a versão 2.9 do [cliente SDK do Power BI](https://github.com/Microsoft/PowerBI-JavaScript) para inicializar o iframe.

O `powerbi.bootstrap(element, config)` permite que você comece a inserção antes de todos os parâmetros necessários estarem disponíveis. A API de inicialização prepara e inicializa o iframe.
Ao usar a API de inicialização, ainda é necessário chamar o `powerbi.embed(element, config)` no mesmo elemento HTML.

Por exemplo, um dos casos de uso para esse recurso é executar a inicialização do iframe e as chamadas de back-end para inserção em paralelo.
> [!TIP]
> Use a API de inicialização quando for possível gerar o iframe antes que ele fique visível para o usuário final.

[Saiba mais sobre a inicialização de iframe](https://github.com/Microsoft/PowerBI-JavaScript/wiki/Bootstrap-For-Better-Performance).

## <a name="measure-performance"></a>Medir o desempenho

### <a name="performance-events"></a>Eventos de desempenho

Para medir o desempenho inserido, você pode usar dois eventos:

1. Evento carregado: o tempo até que o relatório seja inicializado (o logotipo de Power BI desaparecerá quando o carregamento for concluído).
2. Evento renderizado: o tempo até que o relatório seja totalmente renderizado usando dados reais. O evento renderizado é disparado sempre que o relatório é renderizado novamente (ou seja, após a aplicação de filtros). Para medir um relatório, faça os cálculos no primeiro evento gerado.

Os dados armazenados em cache são renderizados quando disponíveis, mas nenhum evento adicional é gerado.

[Saiba mais sobre a manipulação de eventos](https://github.com/Microsoft/PowerBI-JavaScript/wiki/Handling-Events).

### <a name="performance-analyzer"></a>Performance Analyzer

Para verificar o desempenho de elementos do relatório, você pode usar o recurso Performance Analyzer no Power BI Desktop.
Com o Performance Analyzer, você pode exibir e fazer registros em log, que medem o desempenho de cada um dos elementos do relatório.

[Saiba mais sobre o Performance Analyzer](../desktop-performance-analyzer.md).

> [!NOTE]
> Lembre-se sempre de comparar o desempenho do relatório inserido com o desempenho no site do powerbi.com. Isso pode ajudá-lo a entender a origem dos problemas de desempenho

## <a name="next-steps"></a>Próximas etapas

* [Práticas recomendadas de desempenho de relatório do Power BI](../power-bi-reports-performance.md)
* [Como solucionar problemas do Power BI Embedded](embedded-troubleshoot.md)
* [Perguntas frequentes do Power BI Embedded](embedded-faq.md)
