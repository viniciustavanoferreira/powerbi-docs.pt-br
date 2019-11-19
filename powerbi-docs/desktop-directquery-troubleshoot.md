---
title: Solução de problemas do modelo de DirectQuery no Power BI Desktop
description: Solucionar problemas do modelo de DirectQuery.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 10/24/2019
ms.author: v-pemyer
ms.openlocfilehash: 623a0bbd187a997003ce7b82cc76d5c4fbe9ce44
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/09/2019
ms.locfileid: "73868055"
---
# <a name="directquery-model-troubleshooting-in-power-bi-desktop"></a>Solução de problemas do modelo de DirectQuery no Power BI Desktop

Este artigo destina-se a modeladores de dados que desenvolvem modelos de DirectQuery do Power BI usando o Power BI Desktop ou o serviço do Power BI. Ele descreve como diagnosticar problemas de desempenho e como obter informações mais detalhadas para permitir que os relatórios sejam otimizados.

## <a name="performance-analyzer"></a>Performance Analyzer

É altamente recomendável que qualquer diagnóstico de problemas de desempenho comece no Power BI Desktop, e não no Power BI (no serviço ou no Servidor de Relatórios do Power BI). Isso ocorre porque é comum que os problemas de desempenho sejam baseados apenas no nível de desempenho da fonte de dados subjacente. Esses problemas são identificados e diagnosticados mais facilmente no ambiente bem mais isolado do Power BI Desktop, eliminando inicialmente alguns componentes (como o gateway do Power BI). Somente se for identificado que os problemas de desempenho não estão presentes com o Power BI Desktop, o foco de investigação deverá ser nas particularidades do relatório no Power BI. O [Performance Analyzer](desktop-performance-analyzer.md) é uma ferramenta útil para identificar problemas ao longo desse processo.

Da mesma forma, recomenda-se primeiro tentar isolar os problemas a um visual individual, em vez de muitos visuais em uma página.

Digamos que essas etapas (nos parágrafos anteriores deste tópico) tenham sido realizadas – agora temos um único visual em uma página do Power BI Desktop que ainda está lento. Para determinar quais consultas estão sendo enviadas para a fonte subjacente pelo Power BI Desktop, você pode usar o Performance Analyzer. Também é possível exibir informações de rastreamento/diagnóstico que podem ser emitidas pela fonte de dados subjacente. Esses rastreamentos também podem conter informações úteis sobre os detalhes de como a consulta foi executada e como ela pode ser melhorada.

Além disso, mesmo na ausência desses rastreamentos da fonte, é possível exibir as consultas enviadas pelo Power BI, juntamente com seus tempos de execução, conforme descrito a seguir.

## <a name="review-trace-files"></a>Examinar arquivos de rastreamento

Por padrão, o Power BI Desktop registra eventos durante uma determinada sessão em um arquivo de rastreamento chamado **FlightRecorderCurrent.trc**.

Para algumas fontes do DirectQuery, esse log inclui todas as consultas enviadas à fonte de dados subjacente (as fontes restantes de DirectQuery poderão ter suporte no futuro). As fontes que gravam consultas no log são as seguintes:

- SQL Server
- Banco de dados SQL do Azure
- SQL Data Warehouse do Azure
- Oracle
- Teradata
- SAP HANA

O arquivo de rastreamento pode ser encontrado na pasta **AppData** do usuário atual: _\\\<Usuário>\AppData\Local\Microsoft\Power BI Desktop\AnalysisServicesWorkspaces_

Veja como acessar facilmente essa pasta: No Power BI Desktop, selecione _Arquivo > Opções e configurações > Opções_ e, em seguida, selecione a página **Diagnóstico**. A janela de diálogo a seguir será exibida:

![A janela do Power BI Desktop está aberta e a página de Diagnóstico Global está selecionada. A seção Opções de Diagnóstico tem duas propriedades: Habilitar o rastreamento e Cache de geocódigo de bypass. A opção Habilitar o rastreamento está habilitada. A seção Coleta de Despejo de Memória tem um botão Habilitar Agora, bem como um link para abrir a pasta despejo/rastreamentos de memória.](media/desktop-directquery-troubleshoot/desktop-directquery-troubleshoot-desktop-file-options-diagnostics.png)

Ao selecionar o link **Abrir pasta de rastreamentos/despejo de memória** em Coleta de Despejo de Memória, a pasta a seguir é aberta: _\\\<Usuário>\AppData\Local\Microsoft\Power BI Desktop\Traces_

Ao navegar até a pasta pai, o conteúdo da pasta pai exibirá a pasta contendo _AnalysisServicesWorkspaces_, com uma subpasta do workspace para cada instância aberta do Power BI Desktop. Essas subpastas são nomeadas com um sufixo de inteiro, como _AnalysisServicesWorkspace2058279583_.

Dentro dessa pasta há uma subpasta _\Data_ que contém o arquivo de rastreamento FlightRecorderCurrent.trc da sessão atual do Power BI. A pasta de workspace correspondente é excluída quando a sessão associada do Power BI Desktop é encerrada.

Os arquivos de rastreamento podem ser abertos usando a ferramenta SQL Server Profiler, que está disponível como um download gratuito como parte do SQL Server Management Studio. Você pode obtê-la [neste local](/sql/ssms/download-sql-server-management-studio-ssms?view=sql-server-2017).

Depois de baixar e instalar o SQL Server Management Studio, execute o SQL Server Profiler.

![O SQL Server Profiler está aberto. Nenhum rastreamento foi adicionado ainda.](media/desktop-directquery-troubleshoot/desktop-directquery-troubleshoot-sql-server-profiler-trace.png)

Para abrir o arquivo de rastreamento, execute as seguintes etapas:

1. No SQL Server Profiler, selecione _Arquivo > Abrir > Rastreamento_
2. Insira o caminho até o arquivo de rastreamento da sessão atualmente aberta do Power BI, como abaixo: _\\\<Usuário>\AppData\Local\Microsoft\Power BI Desktop\AnalysisServicesWorkspaces\AnalysisServicesWorkspace2058279583\Data_
3. Abra _FlightRecorderCurrent.trc_

Todos os eventos da sessão atual são exibidos. Um exemplo anotado está mostrado abaixo, destacando os grupos de eventos. Cada grupo tem o seguinte:

- Um evento _Início da Consulta_ e um _Término da Consulta_, que representam o início e término de uma consulta DAX gerada pela interface do usuário (por exemplo, de um visual ou do preenchimento de uma lista de valores no filtro de interface do usuário)
- Um ou mais pares de eventos _Início do DirectQuery_ e _Término do DirectQuery_, que representam uma consulta enviada à fonte de dados subjacente, como parte da avaliação da consulta DAX

Observe que várias consultas DAX podem ser executadas em paralelo, portanto os eventos de grupos diferentes podem ser intercalados. O valor da ActivityID pode ser usado para determinar quais eventos pertencem ao mesmo grupo.

![O SQL Server Profiler está aberto. Nenhum rastreamento foi adicionado ainda.](media/desktop-directquery-troubleshoot/desktop-directquery-troubleshoot-sql-server-profiler-trace.png)

Outras colunas de interesse são as seguintes:

- **TextData:** os detalhes textuais do evento. Para eventos de _Início/Término da Consulta_, eles serão a consulta DAX. Para eventos de _Início/Término de DirectQuery_, serão a consulta SQL enviada à fonte subjacente. O valor de _TextData_ do evento atualmente selecionado também será exibido na região da parte inferior.
- **EndTime:** quando o evento foi concluído.
- **Duration:** o tempo, em milissegundos, necessário para executar a consulta DAX ou SQL.
- **Error:** indica se ocorreu um erro e, nesse caso, o evento também será exibido em vermelho.

Na imagem acima, algumas das colunas menos interessantes foram reduzidas para permitir que as colunas interessantes sejam vistas com mais facilidade.

A abordagem recomendada para capturar um rastreamento para ajudar a diagnosticar um problema de desempenho potencial é a seguinte:

- Abra uma única sessão do Power BI Desktop (para evitar a confusão de ter várias pastas de workspace)
- Realize o conjunto de ações desejadas no Power BI Desktop. Inclua algumas ações adicionais, para garantir que os eventos desejados sejam liberados no arquivo de rastreamento.
- Abra o SQL Server Profiler e examine o rastreamento, conforme descrito anteriormente. Lembre-se de que o arquivo de rastreamento será excluído com o fechamento do Power BI Desktop. Além disso, as ações adicionais no Power BI Desktop não aparecerão imediatamente – o arquivo de rastreamento deve ser fechado e reaberto para que os novos eventos sejam vistos.
- Mantenha sessões individuais razoavelmente pequenas (10 segundos de ações, não centenas) para facilitar a interpretação do arquivo de rastreamento (como há um limite no tamanho do arquivo de rastreamento, para sessões longas, há uma possibilidade de que os eventos antecipados sejam removidos).

## <a name="understand-queries-sent-to-the-source"></a>Entender as consultas enviadas à origem

O formato geral das consultas geradas e enviadas pelo Power BI Desktop utiliza subconsultas para cada uma das tabelas de modelo referenciadas, em que a subconsulta é definida pela consulta do Power Query. Por exemplo, suponha as seguintes tabelas TPC-DS em um banco de dados relacional do SQL Server:

![Um diagrama da exibição de modelo do Power BI Desktop mostra quatro tabelas, todas relacionadas. As tabelas são Item, Web_Sales, Customer e Date-dim.](media/desktop-directquery-troubleshoot/desktop-directquery-troubleshoot-model-view-diagram.png)

Considere o visual a seguir e sua configuração, observando que a medida **SalesAmount** é definida com a seguinte expressão:

```dax

SalesAmount = SUMX(Web_Sales, [ws_sales_price] * [ws_quantity])

```

![Um relatório do Power BI Desktop é composto por um gráfico de colunas empilhadas, exibindo o valor das vendas por categoria. O painel Filtros revela um filtro no ano 2000.](media/desktop-directquery-troubleshoot/desktop-directquery-troubleshoot-example-report.png)

A atualização desse visual resultará na consulta T-SQL mostrada após o parágrafo abaixo. Como você pode observar, há três subconsultas para as tabelas de modelo **Web_Sales**, **Item** e **Date_dim**. Cada uma dessas tabelas retorna todas as colunas da tabela do modelo, embora apenas quatro colunas sejam realmente referenciadas pelo visual. Essas subconsultas (que estão sombreadas) são exatamente a definição das consultas do Power Query. O uso de subconsultas dessa maneira não afetou o desempenho das fontes de dados com suporte pelo DirectQuery até o momento. Fontes de dados como o SQL Server otimizam as referências para outras colunas não utilizadas.

Um motivo para o Power BI empregar esse padrão é porque você pode definir uma consulta do Power Query para usar uma instrução de consulta específica. Portanto, ela é usada "conforme fornecida", sem que haja uma tentativa de reescrevê-la. Observe que esses padrões restringem o uso de instruções de consulta que usam CTEs (Expressões de Tabela Comuns) e procedimentos armazenados. Essas instruções não podem ser usadas em subconsultas.

![Uma consulta T-SQL muito detalhada mostra subconsultas inseridas, uma para cada tabela de modelo.](media/desktop-directquery-troubleshoot/desktop-directquery-troubleshoot-example-query.png)

## <a name="gateway-performance"></a>Desempenho do gateway

Para obter informações sobre como solucionar problemas de desempenho do gateway, leia o artigo [Solucionar problemas de gateways – Power BI](service-gateway-onprem-tshoot.md).

## <a name="next-steps"></a>Próximas etapas

Para obter mais informações sobre o DirectQuery, confira os seguintes recursos:

- [Usar o DirectQuery no Power BI Desktop](desktop-use-directquery.md)
- [Modelos de DirectQuery no Power BI Desktop](desktop-directquery-about.md)
- [Diretrizes sobre modelos de DirectQuery no Power BI Desktop](guidance/directquery-model-guidance.md)
- Dúvidas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
