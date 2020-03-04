---
title: Monitorar o desempenho de relatórios no Power BI
description: Orientações sobre como monitorar o desempenho de relatórios no Power BI.
author: peter-myers
manager: asaxton
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 02/16/2020
ms.author: v-pemyer
ms.openlocfilehash: b1ab74ec7f7f6594450ec2cf95528d06dc45f613
ms.sourcegitcommit: 032a77f2367ca937f45e7e751997d7b7d0e89ee2
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77610008"
---
# <a name="monitor-report-performance-in-power-bi"></a>Monitorar o desempenho de relatórios no Power BI

Monitore o desempenho de relatórios no Power BI Desktop usando o [aplicativo de Métricas do Power BI Premium](../service-premium-metrics-app.md), descubra onde estão os gargalos e como você pode melhorar o desempenho do relatório.

O monitoramento do desempenho é relevante nas seguintes situações:

- A atualização do modelo de dados de importação está lenta.
- Seus relatórios do DirectQuery ou LiveConnection estão lentos.
- Os cálculos do seu modelo estão lentos.

Consultas ou recursos visuais de relatórios lentos devem ser um ponto focal da otimização contínua.

## <a name="use-query-diagnostics"></a>Usar o Diagnóstico de Consulta

Use o [Diagnóstico de Consulta](/power-query/QueryDiagnostics) no Power BI Desktop para determinar o que o Power Query está fazendo ao visualizar ou aplicar consultas. Além disso, use a função _Diagnosticar a Etapa_ para registrar informações detalhadas de avaliação para cada etapa da consulta. Os resultados são disponibilizados em um Power Query, e você pode aplicar transformações para entender melhor a execução da consulta.

> [!NOTE]
> Atualmente, o Diagnóstico de Consulta é uma versão prévia do recurso, e você deve habilitá-lo em _Opções e Configurações_. Uma vez habilitado, seus comandos estão disponíveis na janela do Editor do Power Query, na guia da faixa de opções **Ferramentas**.

![A imagem mostra a guia da faixa de opções Ferramentas do Editor do Power Query. A faixa de opções exibe os comandos Etapa de Diagnóstico, Iniciar Diagnóstico e Parar Diagnóstico.](media/monitor-report-performance/power-query-diagnotics.png)

## <a name="use-performance-analyzer"></a>Usar o Performance Analyzer

Use o [Performance Analyzer](../desktop-performance-analyzer.md) no Power BI Desktop para descobrir o desempenho de cada um de seus elementos de relatório, como visuais e fórmulas DAX. Isso é especialmente útil para determinar se é a consulta ou a renderização visual que está contribuindo para os problemas de desempenho.

## <a name="use-sql-server-profiler"></a>Usar o SQL Server Profiler

Você também pode usar o [SQL Server Profiler](/sql/tools/sql-server-profiler/sql-server-profiler) para identificar consultas que estão lentas.

> [!NOTE]
> O SQL Server Profiler está disponível como parte do [SQL Server Management Studio](/sql/ssms/download-sql-server-management-studio-ssms).

Use o SQL Server Profiler quando sua fonte de dados for:

- SQL Server
- SQL Server Analysis Services
- Azure Analysis Services

> [!CAUTION]
> O Power BI Desktop dá suporte à conexão a uma porta de diagnóstico. A porta de diagnóstico permite que outras ferramentas façam conexões para executar rastreamentos para fins de diagnóstico. Não há suporte para a realização de alterações no modelo de dados do Power Desktop. Alterações no modelo podem levar a dados corrompidos e a perda de dados.

Para criar um rastreamento do SQL Server Profiler, siga estas instruções:

1. Abra o relatório do Power BI Desktop (para facilitar a localização da porta na próxima etapa, feche todos os outros relatórios abertos).
1. Para determinar a porta que está sendo usada pelo Power BI Desktop, no PowerShell (com privilégios de administrador) ou no prompt de comando, digite o seguinte comando:
    ```powershell
    netstat -b -n
    ```
    O resultado será uma lista de aplicativos e suas portas abertas. Procure a porta usada pelo **msmdsrv.exe** e anote-a para uso posterior. É a sua instância do Power BI Desktop.
1. Para conectar o SQL Server Profiler ao relatório de Power BI Desktop:
    1. Abra o SQL Server Profiler.
    1. No SQL Server Profiler, no menu _Arquivo_, selecione _Novo Rastreamento_.
    1. Em **Tipo de Servidor**, selecione _Analysis Services_.
    1. Em **Nome do Servidor**, insira _localhost:[porta anotada anteriormente]_ .
    1. Clique em _Executar_ – agora o rastreamento do SQL Server Profiler está funcionando e criando um perfil ativo das consultas do Power BI Desktop.
1. À medida que as consultas do Power BI Desktop forem executadas, você verá suas respectivas durações e tempos de CPU. Dependendo do tipo de fonte de dados, você poderá ver outros eventos indicando como a consulta foi executada. Usando essas informações, é possível determinar quais consultas são os gargalos.

Uma vantagem de usar o SQL Server Profiler é poder salvar um rastreamento de banco de dados SQL Server (relacional). O rastreamento pode se tornar uma entrada para o [Orientador de Otimização do Mecanismo de Banco de Dados](/sql/relational-databases/performance/start-and-use-the-database-engine-tuning-advisor). Dessa forma, você pode receber recomendações sobre como ajustar sua fonte de dados.

## <a name="monitor-premium-metrics"></a>Monitorar métricas Premium

Para os recursos do Power BI Premium, use o **aplicativo de Métricas do Power BI Premium** para monitorar a integridade e a capacidade da sua assinatura do Power BI Premium. Para obter mais informações, confira [Aplicativo d Métricas do Power BI Premium](../service-premium-metrics-app.md).

## <a name="next-steps"></a>Próximas etapas

Para obter mais informações sobre este artigo, confira os seguintes recursos:

- [Diagnóstico de Consulta](/power-query/QueryDiagnostics)
- [Performance Analyzer](../desktop-performance-analyzer.md)
- [Aplicativo de Métricas do Power BI Premium](../service-premium-metrics-app.md)
- Dúvidas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
- Sugestões? [Contribuir com ideias para aprimorar o Power BI](https://ideas.powerbi.com/)
