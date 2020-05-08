---
title: Quando usar relatórios paginados no Power BI
description: Orientações sobre quando usar relatórios paginados do Power BI.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 01/04/2020
ms.author: v-pemyer
ms.openlocfilehash: 049b6ac14c6d35d68815eac32520a4eaa654ad42
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/05/2020
ms.locfileid: "78920729"
---
# <a name="when-to-use-paginated-reports-in-power-bi"></a>Quando usar relatórios paginados no Power BI

Este artigo é destinado a autores de relatórios que elaboram relatórios para o Power BI. Ele fornece sugestões para ajudar a escolher quando desenvolver [relatórios paginados do Power BI](../paginated-reports/paginated-reports-report-builder-power-bi.md).

> [!NOTE]
> A publicação de relatórios paginados do Power BI requer uma assinatura do Power BI Premium. Os relatórios serão renderizados somente quando estiverem em um workspace em uma capacidade dedicada que tenha a [carga de trabalho Relatórios Paginados habilitada](../service-admin-premium-workloads.md#paginated-reports).

Os relatórios paginados do Power BI são otimizados para **impressão** ou **geração de PDF**. Eles também possibilitam produzir layouts altamente formatados e perfeitos no nível do pixel. Sendo assim, relatórios paginados são ideais para relatórios operacionais, como faturas de vendas.

Em contraste, os relatórios do Power BI são otimizados para **exploração e interatividade**. Além disso, eles podem apresentar seus dados usando uma ampla gama de visuais extremamente modernos. Os relatórios do Power BI são ideais, portanto, para relatórios analíticos, permitindo que os usuários explorem dados e descubram relações e padrões.

Recomendamos que você considere usar um relatório paginado do Power BI quando:

- Souber que o relatório precisa ser impresso ou apresentado como um documento PDF.
- Os layouts de grade de dados podem ser expandidos e estourar. Considere que uma tabela, ou matriz, em um relatório do Power BI não pode ser redimensionada dinamicamente para exibir todos os dados — ela fornecerá barras de rolagem. Mas, se for impressa, não será possível rolar para revelar dados fora de exibição.
- Os recursos e as funcionalidades de paginação do Power BI funcionam em seu favor. Muitos cenários com relatórios desse tipo são descritos posteriormente neste artigo.

## <a name="legacy-reports"></a>Relatórios herdados

Quando você já tem relatórios [RDL (Report Definition Language)](/sql/reporting-services/reports/report-definition-language-ssrs) do SSRS (SQL Server Reporting Services), você pode optar por desenvolvê-los novamente como [relatórios do Power BI](../consumer/end-user-reports.md) ou migrá-los como relatórios paginados para o Power BI. Para obter mais informações, confira [Migrar relatórios do SQL Server Reporting Services para o Power BI](migrate-ssrs-reports-to-power-bi.md).

Depois de publicados em um workspace do Power BI, os relatórios paginados ficam disponíveis lado a lado com os relatórios do Power BI. Em seguida, eles podem ser distribuídos facilmente usando [aplicativos do Power BI](../service-create-distribute-apps.md).

Você pode considerar desenvolver novamente os relatórios do SSRS em vez de migrá-los. Isso vale especialmente para relatórios destinados a fornecer experiências analíticas. Nesses casos, os relatórios do Power BI provavelmente fornecerão melhores experiências para os usuários.

## <a name="paginated-report-scenarios"></a>Cenários dom relatórios paginados

Há muitos cenários convincentes nos quais você pode favorecer o desenvolvimento de um relatório paginado do Power BI. Muitos deles são recursos ou funcionalidades sem suporte dos relatórios do Power BI.

- **Pronto para impressão**: relatórios paginados são otimizados para impressão ou geração de PDF. Quando necessário, as regiões de dados podem ser expandidas e estourar para várias páginas de forma controlada. Os layouts do relatório podem definir margens e cabeçalhos e rodapés de página.
- **Renderizar formatos**: o Power BI pode renderizar relatórios paginados em formatos diferentes. Os formatos incluem Microsoft Excel, Microsoft Word, Microsoft PowerPoint, PDF, CSV, XML e MHTML. (O formato MHTML é usado pelo serviço do Power BI para renderizar relatórios.) Os usuários do relatório podem optar por exportar para o formato que preferirem.
- **Layout de precisão**: você pode criar layouts altamente formatados e perfeitos no nível do pixel — com o tamanho e o local exatos configurados em frações de centímetros ou polegadas.
- **Layout dinâmico**: você pode produzir layouts altamente responsivos configurando muitas propriedades do relatório para usar expressões VB.NET. As expressões têm acesso a muitas das bibliotecas principais do .NET Framework.
- **Layout específico para renderização**: você pode usar expressões para modificar o layout do relatório com base no formato de renderização aplicado. Por exemplo, você pode configurar o relatório para desabilitar a alternância de visibilidade (para efetuar drill down e drill up) quando ele é renderizado usando um formato não interativo, como PDF.
- **Consultas nativas**: você não precisa desenvolver um conjunto de dados do Power BI primeiro. É possível criar consultas nativas (ou usar procedimentos armazenados) para qualquer [fonte de dados com suporte](../paginated-reports/paginated-reports-data-sources.md). As consultas podem incluir parametrização.
- **Designers de consultas gráficas**: o Power BI Report Builder inclui designers de consultas gráficas para ajudar você a escrever e testar suas consultas de conjuntos de dados.
- **Conjuntos de dados estáticos**: você pode definir um conjunto de dados e inserir dados diretamente em sua definição de relatório. Essa funcionalidade é especialmente útil para dar suporte a uma demonstração ou para fornecer uma POC (prova de conceito).
- **Integração de dados**: você pode combinar dados de diferentes fontes de dados ou com conjuntos de dados estáticos. Isso é feito criando campos personalizados usando expressões VB.NET.
- **Parametrização**: você pode criar experiências de parametrização altamente personalizadas, incluindo parâmetros controlados por dados e em cascata. Também é possível definir padrões de parâmetro. Essas experiências podem ser criadas para ajudar os usuários dos relatórios a configurar rapidamente os filtros apropriados. Além disso, os parâmetros não precisam filtrar os dados do relatório; eles podem ser usados para dar suporte a cenários "hipotéticos" ou à filtragem dinâmica ou estilo.
- **Dados de imagem**: o relatório pode renderizar imagens quando elas são armazenadas em formato binário em uma fonte de dados.
- **Código personalizado**: você pode desenvolver blocos de código de funções VB.NET em seu relatório e usá-los em qualquer expressão do relatório.
- **Sub-relatórios**: você pode inserir outros relatórios paginados do Power BI (do mesmo workspace) em seu relatório.
- **Grades de dados flexíveis**: você tem um controle refinado sobre os layouts de grade usando a região de dados Tablix. Ela também dá suporte a layouts complexos, incluindo grupos aninhados e adjacentes. Além disso, ela pode ser configurada para repetir os títulos quando impressos em várias páginas. Ela pode, ainda, inserir um sub-relatório ou outras visualizações, incluindo barras de dados, minigráficos e indicadores.
- **Tipos de dados espaciais**: a região de dados do mapa pode visualizar [tipos de dados espaciais do SQL Server](/sql/relational-databases/spatial/spatial-data-sql-server). Assim, os tipos de dados GEOGRAPHY e GEOMETRY podem ser usados para visualizar pontos, linhas ou polígonos. Também é possível visualizar polígonos definidos em arquivos de forma ESRI.
- **Medidores modernos**: medidores radiais e lineares podem ser usados para exibir valores e status de KPI. Eles podem até mesmo ser inseridos em regiões de dados da grade, repetindo-se dentro de grupos.
- **Renderização de HTML**: você pode exibir texto com formatação avançada quando ele é armazenado como HTML.
- **Mala direta**: você pode usar espaços reservados de caixa de texto para injetar valores de dados no texto. Dessa forma, você pode produzir um relatório de mala direta.
- **Recursos de interatividade**: os recursos interativos incluem a alternância da visibilidade (para efetuar drill down e drill up), links, classificação interativa e dicas de ferramenta. Você também pode adicionar links que detalham para relatórios do Power BI ou outros relatórios paginados do Power BI. Os links podem até mesmo ir para outro local dentro do mesmo relatório.
- **Assinaturas**: o Power BI pode entregar relatórios paginados segundo um cronograma por email, com relatório anexos em qualquer formato com suporte.
- **Layouts por usuário**: você pode criar layouts de relatório responsivos com base no usuário autenticado que abre o relatório. Você pode criar o relatório para filtrar dados de forma diferente, ocultar regiões ou visualizações de dados, aplicar formatos diferentes ou definir padrões de parâmetro específicos do usuário.

## <a name="next-steps"></a>Próximas etapas

Para obter mais informações relacionadas a este artigo, confira os seguintes recursos:

- [O que são os relatórios paginados no Power BI Premium?](../paginated-reports/paginated-reports-report-builder-power-bi.md)
- [Migrar relatórios do SQL Server Reporting Services para o Power BI](migrate-ssrs-reports-to-power-bi.md)
- Dúvidas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
- Sugestões? [Contribuir com ideias para aprimorar o Power BI](https://ideas.powerbi.com/)
