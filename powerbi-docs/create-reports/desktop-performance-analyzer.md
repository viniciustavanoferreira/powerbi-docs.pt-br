---
title: Usar o Performance Analyzer para examinar o desempenho do elemento de relatório no Power BI Desktop
description: Descubra como os visuais e elementos de relatório estão sendo executados em termos de uso de recursos e capacidade de resposta
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/23/2020
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: fd172cc41dce432e7e8f2c7f9b9f3ff67caaef4b
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83348242"
---
# <a name="use-performance-analyzer-to-examine-report-element-performance"></a>Usar o Performance Analyzer para examinar o desempenho do elemento de relatório

No **Power BI Desktop**, você pode descobrir como cada um de seus elementos de relatório, como visuais e fórmulas DAX, estão sendo executados. Usando o **Performance Analyzer**, você pode ver e registrar logs que medem como cada um de seus elementos de relatório é executado quando os usuários interagem com eles e quais aspectos de seu desempenho consomem mais (ou menos) recursos.

![Analisador de desempenho](media/desktop-performance-analyzer/performance-analyzer-01.png)

O Performance Analyzer inspeciona e exibe a duração necessária para atualizar ou atualizar todos os visuais que as interações do usuário iniciam e apresenta as informações para que você possa exibir, fazer drill down ou exportar os resultados. O Performance Analyzer pode ajudar a identificar visuais que estão afetando o desempenho de seus relatórios e o motivo do impacto.

## <a name="displaying-the-performance-analyzer-pane"></a>Exibir o painel do Performance Analyzer

No **Power BI Desktop**, selecione a faixa de opções **Exibir**. Na área **Mostrar** da faixa de opções **Exibir**, você pode marcar a caixa de seleção ao lado do **Performance Analyzer** para exibir o painel do Performance Analyzer.

![Selecionar o Performance Analyzer na faixa de opções Exibir](media/desktop-performance-analyzer/performance-analyzer-02.png)

Depois de selecionado, o Performance Analyzer será exibido em seu próprio painel, à direita da tela do relatório.

## <a name="using-performance-analyzer"></a>Usar o Performance Analyzer

O Performance Analyzer mede o tempo de processamento (incluindo o tempo para criar ou atualizar um visual) necessário para atualizar os elementos de relatório iniciados como resultado de qualquer interação do usuário que resulte na execução de uma consulta. Por exemplo, ajustar uma segmentação requer que o visual dela seja modificado e que uma consulta seja enviada para o modelo de dados, além de requerer os visuais afetados que devem ser atualizados como resultado das novas configurações. 

Para que o Performance Analyzer comece a gravar, basta selecionar **Iniciar gravação**

![Iniciar a gravação](media/desktop-performance-analyzer/performance-analyzer-03.png)

As ações executadas no relatório são exibidas e registradas no painel do Performance Analyzer, na ordem em que o visual é carregado pelo Power BI. Por exemplo, talvez os usuários tenham dito que um relatório demora muito para ser atualizado. Ou determinados visuais em um relatório demoram muito para serem exibidos quando uma segmentação é ajustada. O Performance Analyzer pode informar qual visual é o culpado e identificar quais aspectos do visual estão demorando mais para serem processados. 

Depois de iniciar a gravação, o botão **Iniciar gravação** fica esmaecido (inativo, pois você já começou a gravar) e o botão **Parar** fica ativo. 

O Performance Analyzer coleta e exibe as informações de medição do desempenho em tempo real. Portanto, sempre que você clica em um visual, move uma segmentação ou interage de qualquer outra maneira, o Performance Analyzer exibe imediatamente os resultados de desempenho em seu painel.

Se o painel tiver mais informações que possam ser exibidas, uma barra de rolagem será exibida para navegar até informações adicionais.

Cada interação tem um identificador de seção no painel, descrevendo a ação que iniciou as entradas do log. Na imagem a seguir, a interação era que os usuários alterassem uma segmentação.

![Seções baseadas no tipo de interação](media/desktop-performance-analyzer/performance-analyzer-04.png)

As informações de log de cada visual inclui o tempo gasto (duração) para concluir as seguintes categorias de tarefas:

* **Consulta DAX** – se uma consulta DAX foi exigida, esse é o tempo entre o visual enviar a consulta e o Analysis Services retornar os resultados.
* **Exibição do visual** – o tempo necessário para o visual ser desenhado na tela, incluindo o tempo necessário para recuperar imagens da Web ou geocodificação. 
* **Outro** – tempo exigido pelo Visual para preparar consultas, aguardar a conclusão de outros visuais ou executar outros processamentos em segundo plano.

Os valores de **Duração (MS)** indicam a diferença entre um carimbo de data/hora *inicial* e *final* para cada operação. A maioria das operações de tela e visuais é executada sequencialmente em um thread de interface do usuário, que é compartilhado por várias operações. As durações relatadas incluem o tempo gasto na fila enquanto outras operações são concluídas. O [exemplo de Performance Analyzer](https://github.com/microsoft/powerbi-desktop-samples/tree/master/Performance%20Analyzer) no GitHub e sua [documentação](https://github.com/microsoft/powerbi-desktop-samples/blob/master/Performance%20Analyzer/Power%20BI%20Performance%20Analyzer%20Export%20File%20Format.docx) associada fornecem detalhes sobre como os elementos visuais consultam dados e como eles são renderizados.


![elementos de informações de log](media/desktop-performance-analyzer/performance-analyzer-06.png)

Depois de interagir com os elementos do relatório que você deseja medir com o Performance Analyzer, você poderá selecionar o botão **Parar**. As informações do desempenho continuarão no painel depois de você selecionar **Parar** para analisar.

Para limpar as informações no painel do Performance Analyzer, selecione **Limpar**. Todas as informações são apagadas e não são salvas quando você seleciona **Limpar**. Confira a próxima seção para aprender a salvar informações em logs. 

## <a name="refreshing-visuals"></a>Atualizar visuais

Você pode selecionar **Atualizar visuais** no painel do Performance Analyzer para atualizar todos os visuais na página atual do relatório e, assim, fazer o Performance Analyzer coletar informações sobre todos esses visuais.

Você também pode atualizar visuais individuais. Quando o Performance Analyzer está gravando, você pode selecionar **Atualizar este visual** encontrado no canto superior direito de cada visual para atualizá-lo e capturar suas informações de desempenho.

![atualizar um visual individual](media/desktop-performance-analyzer/performance-analyzer-07.png)

## <a name="saving-performance-information"></a>Salvar informações de desempenho

Você pode salvar as informações que o Performance Analyzer cria sobre um relatório selecionando o botão **Exportar**. A seleção de **Exportar** cria um arquivo .json com informações do painel do Performance Analyzer. 

![Salvar o arquivo de log do Performance Analyzer](media/desktop-performance-analyzer/performance-analyzer-05.png)


## <a name="next-steps"></a>Próximas etapas
Para obter mais informações sobre o **Power BI Desktop** e como começar, confira os artigos a seguir.

* [O que é o Power BI Desktop?](../fundamentals/desktop-what-is-desktop.md)
* [Visão geral de Consulta com o Power BI Desktop](../transform-model/desktop-query-overview.md)
* [Fontes de dados no Power BI Desktop](../connect-data/desktop-data-sources.md)
* [Conectar-se a dados no Power BI Desktop](../connect-data/desktop-connect-to-data.md)
* [Formatar e combinar dados com o Power BI Desktop](../connect-data/desktop-shape-and-combine-data.md)
* [Tarefas comuns de consulta no Power BI Desktop](../transform-model/desktop-common-query-tasks.md)   

Para obter informações sobre o exemplo do Performance Analyzer, confira os recursos a seguir.

* [Exemplo do Performance Analyzer](https://github.com/microsoft/powerbi-desktop-samples/tree/master/Performance%20Analyzer)
* [Documentação de exemplo do Performance Analyzer](https://github.com/microsoft/powerbi-desktop-samples/blob/master/Performance%20Analyzer/Power%20BI%20Performance%20Analyzer%20Export%20File%20Format.docx)
