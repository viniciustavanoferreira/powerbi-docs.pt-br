---
title: 'Relatórios paginados no Power BI: Perguntas frequentes'
description: Este artigo responde a perguntas frequentes sobre relatórios paginados. Esses relatórios oferecem uma saída altamente formatada e visualmente perfeita otimizada para impressão ou geração de PDF.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 04/29/2020
ms.openlocfilehash: 3677e29e4ca9bc13bf0c7397d854dea62ec5f70f
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82584999"
---
# <a name="paginated-reports-in-power-bi-faq"></a>Relatórios paginados no Power BI: Perguntas frequentes 

Este artigo responde a perguntas frequentes sobre relatórios paginados. Esses relatórios oferecem uma saída altamente formatada e visualmente perfeita otimizada para impressão ou geração de PDF. Eles são chamados de "paginados" porque são formatados de modo a se adaptarem a várias páginas. Os relatórios paginados são baseados na tecnologia de relatório RDL no SQL Server Reporting Services. 

Este artigo responde a muitas perguntas comuns que as pessoas têm sobre relatórios paginados no Power BI Premium e sobre o Construtor de Relatórios, a ferramenta autônoma para criação de relatórios paginados. Você precisa de uma licença do Power BI Pro para publicar um relatório no serviço. É possível publicar e compartilhar relatórios paginados em Meu Workspace ou em workspaces, desde que o workspace esteja em uma capacidade do Power BI Premium. 

## <a name="administration"></a>Administração

### <a name="what-size-premium-capacity-do-i-need-for-paginated-reports"></a>Qual o tamanho da capacidade Premium que preciso para relatórios paginados?

A carga de trabalho de relatórios paginados está disponível em SKUs P1 – P3.  Você também pode usá-la com SKUs de A4 a A6 para cenários de teste/desenvolvimento ou inseridos.

### <a name="what-is-the-maximum-memory-threshold-i-can-put-for-paginated-reports-in-my-capacity"></a>Qual é o limite máximo de memória que posso colocar para relatórios paginados na minha capacidade?

Você pode usar até 100% da memória para essa carga de trabalho.

### <a name="how-does-user-access-work-for-paginated-reports"></a>Como funciona o acesso de usuário para relatórios paginados?

O acesso do usuário para relatórios paginados é o mesmo que o acesso do usuário para todos os outros conteúdos no serviço do Power BI 

### <a name="how-do-i-turn-onoff-my-paginated-reports-workload"></a>Como fazer para ativar/desativar minha carga de trabalho de relatórios paginados?

O administrador de capacidade pode ativar ou desativar a carga de trabalho de relatórios paginados na página do portal de administração de capacidade.  Por padrão, a carga de trabalho estará ativa para quaisquer novas funcionalidades criadas, mas não consumirá memória até que você carregue seu primeiro relatório paginado.  

### <a name="how-can-i-monitor-usage-of-paginated-reports-in-my-tenant"></a>Como posso monitorar o uso de relatórios paginados no meu locatário?

Os logs de auditoria do Office 365 detalham o uso desse tipo de relatório nos seguintes eventos: 

- Exibir relatório do Power BI
- Excluir relatório do Power BI
- Criar relatório do Power BI
- Relatório do Power BI baixado

O campo ReportType tem o valor "PaginatedReport" para identificar os relatórios paginados em oposição aos relatórios do Power BI.

Além disso, os logs de auditoria fornecem os seguintes eventos para relatórios paginados:

- Conjunto de dados do Power BI associado ao gateway
- Descobrir a fonte de dados do Power BI
- TakeOverDatasource

### <a name="can-i-monitor-this-workload-through-the-premium-capacity-monitoring-app"></a>Posso monitorar essa carga de trabalho por meio do aplicativo de Monitoramento da Capacidade Premium?

Sim, o monitoramento está disponível como uma nova guia com os mesmos detalhes relevantes para seus conjuntos de dados do Power BI.

### <a name="do-i-need-a-pro-license-to-create-and-publish-paginated-reports"></a>Preciso de uma licença Pro para criar e publicar relatórios paginados?

Você pode carregar relatórios paginados para Meu Workspace sem uma licença do Pro, desde que ele tenha a capacidade Premium.  No caso de outros workspaces, você deve ter uma licença do Pro para criar e publicar conteúdo para eles. Recomendamos o download e uso do Construtor de Relatórios do Power BI até mesmo sem a licença do Pro, mas saiba que não será possível publicar os relatórios paginados criados sem ela. 

### <a name="what-if-i-have-a-paginated-report-in-a-workspace-and-the-paginated-report-workload-is-turned-off"></a>E se eu tiver um relatório paginado em um workspace e a carga de trabalho de relatório paginado estiver desativada?

Você recebe uma mensagem de erro e não pode exibir seu relatório até que a carga de trabalho seja ativada novamente. Você pode ainda excluir o relatório do workspace.

### <a name="what-is-the-default-memory-for-each-of-the-premium-skus-that-support-paginated-reports"></a>Qual é a memória padrão para cada um dos SKUs Premium compatíveis com os relatórios paginados?

Memória padrão em cada SKU Premium para relatórios paginados:

- **P1/A4**: Padrão de 20%; mínimo de 10%
- **P2/A5**: Padrão de 20%; mínimo de 5%
- **P3/A6**: Padrão de 20%; mínimo de 2,5%

Os administradores de locatário do Power BI podem modificar o percentual máximo de memória padrão no Portal de Administração. Confira a seção de carga de trabalho de **Relatórios Paginados** em **Power BI Premium** na guia **Configurações de capacidade**.

:::image type="content" source="media/paginated-reports-faq/paginated-reports-capacity-settings.png" alt-text="Guia de configurações de capacidade de relatórios paginados":::

## <a name="general"></a>Geral

### <a name="when-should-i-use-a-paginated-report-vs-a-power-bi-report"></a>Quando devo usar um relatório paginado ao invés de um relatório do Power BI?

Os relatórios paginados são melhores para cenários que exigem uma saída altamente formatada e visualmente perfeita otimizada para impressão ou geração de PDF.  Um demonstrativo de resultados é um bom exemplo do tipo de relatório que você provavelmente deseja criar como um relatório paginado.  

Os relatórios do Power BI são otimizados para exploração e interatividade.  Um relatório de vendas em que diferentes vendedores desejam dividir os dados no mesmo relatório para sua região/setor/cliente específico e ver como a alteração dos números seria melhor atendida por um relatório do Power BI.

Para obter mais informações, confira [Quando usar relatórios paginados no Power BI](../guidance/report-paginated-or-power-bi.md).

### <a name="the-documentation-says-power-bi-report-builder-is-the-preferred-authoring-tool-can-i-create-paginated-reports-in-sql-server-data-tools-for-power-bi"></a>A documentação indica que o Construtor de Relatórios do Power BI é a ferramenta de criação de preferência. Posso criar relatórios paginados no SQL Server Data Tools para o Power BI?

Sim, mas o serviço do Power BI permite somente que você carregue um único item por vez, portanto, muitos dos cenários que os autores usam com o SSDT (SQL Server Data Tools) ainda não são compatíveis. Confira a [lista completa de recursos sem suporte](#what-paginated-report-features-in-ssrs-arent-yet-supported-in-power-bi) disponíveis posteriormente nesta seção de perguntas frequentes.  

### <a name="what-versions-of-report-builder-do-you-support"></a>Quais versões do Construtor de Relatórios têm suporte?

Lançamos o Construtor de Relatórios do Power BI como a principal ferramenta de criação para relatórios paginados no serviço do Power BI. Instale o [Construtor de Relatórios do Power BI no Centro de Download da Microsoft](https://go.microsoft.com/fwlink/?linkid=2086513).

### <a name="how-do-i-move-existing-reports-i-have-saved-in-sql-server-reporting-services-to-power-bi"></a>Como fazer para mover os relatórios existentes que salvei no SQL Server Reporting Services para o Power BI?

Um projeto no GitHub agora dá suporte à migração de conteúdo do SQL Server Reporting Services para o Power BI.  Veja detalhes sobre a ferramenta e baixe-a aqui: [https://github.com/microsoft/RdlMigration](https://github.com/microsoft/RdlMigration)

### <a name="can-i-open-reports-and-publish-directly-to-the-service"></a>Posso abrir relatórios e publicar diretamente no serviço?

Sim. E adicionamos suporte para abrir e publicar relatórios diretamente no serviço no Construtor de Relatórios do Power BI.

### <a name="what-paginated-report-features-in-ssrs-arent-yet-supported-in-power-bi"></a>Quais recursos de relatórios paginados no SSRS ainda não são compatíveis com o Power BI?

No momento, os relatórios paginados não são compatíveis com os seguintes itens:

- Fontes de dados compartilhados
- Conjuntos de dados compartilhados
- Detalhamento e ações de clique para outros relatórios
- Relatórios vinculados
- Fontes personalizadas

Você recebe uma mensagem de erro se tentar carregar um arquivo que tenha um recurso não suportado no serviço do Power BI, que não seja alternar/classificar.

### <a name="what-data-sources-do-you-support-currently-for-paginated-reports"></a>Quais fontes de dados têm suporte atualmente para relatórios paginados?

Confira o artigo [Fontes de dados com suporte para relatórios paginados do Power BI](paginated-reports-data-sources.md) para ver uma lista de fontes de dados. 

### <a name="what-authentication-methods-do-you-support"></a>Quais métodos de autenticação têm suporte?

Damos suporte ao SSO para o Azure Analysis Services, o Banco de Dados SQL do Azure e fontes de dados do Power BI.  Também damos suporte a OAuth para o Banco de Dados SQL do Azure e o Azure Analysis Services.  Para as outras fontes de dados, você precisa armazenar um nome de usuário e uma senha com a fonte de dados no portal ou gateway.  

### <a name="can-i-use-a-power-bi-dataset-as-a-data-source-for-my-paginated-report"></a>Posso usar um conjunto de dados do Power BI como fonte de dados para meu relatório paginado?

Sim, damos suporte a conjuntos de dados do Power BI como fontes de dados para seus relatórios paginados.

### <a name="can-i-use-stored-procedures-through-the-gateway"></a>Posso usar procedimentos armazenados pelo gateway?

Sim, os procedimentos armazenados pelo Gateway têm suporte para fontes de dados do SQL Server, incluindo aquelas que usam parâmetros.

### <a name="what-export-formats-are-available-for-my-report-in-the-power-bi-service"></a>Quais formatos de exportação estão disponíveis para o meu relatório no serviço do Power BI?

Você pode exportar para Microsoft Excel, Microsoft Word, Microsoft PowerPoint, PDF, .CSV, XML e MHTML.

### <a name="can-i-print-paginated-reports"></a>Posso imprimir relatórios paginados?

Sim, a impressão está disponível para relatórios paginados, incluindo uma experiência de visualização de impressão nova e aprimorada. 

### <a name="are-e-mail-subscriptions-available-for-paginated-reports"></a>As assinaturas de email estão disponíveis para relatórios paginados?

Sim, as assinaturas de email são totalmente compatíveis com relatórios paginados e incluem suporte para seis diferentes formatos de arquivo e valores de parâmetro.

### <a name="can-i-run-custom-code-in-my-report"></a>Posso executar um código personalizado no meu relatório?

Sim, oferecemos suporte à capacidade de executar código em seus relatórios, como no SSRS.

### <a name="can-i-use-power-bi-embedded-to-embed-my-paginated-reports-into-an-app-im-hosting"></a>Posso usar o Power BI Embedded para inserir meus relatórios paginados em um aplicativo que estou hospedando?

A incorporação de SaaS, incluindo o suporte à Inserção Segura, já está disponível. Para a inserção de PaaS, veja o tutorial [Inserir relatórios paginados do Power BI em um aplicativo para seus clientes](../developer/embed-paginated-reports-customers.md).

### <a name="can-i-drill-through-from-a-power-bi-report-to-a-paginated-report"></a>Posso fazer uma consulta detalhada de um relatório do Power BI para um relatório paginado?

Sim, isso pode ser feito usando parâmetros de URL com seus relatórios paginados.

### <a name="can-i-share-my-paginated-report-content-through-a-power-bi-app"></a>Posso compartilhar meu conteúdo de relatório paginado por meio de um aplicativo do Power BI?

Sim, os relatórios paginados podem ser implantados com os aplicativos de workspace v1 e v2. 

### <a name="will-other-report-specific-features-in-power-bi-like-pinning-to-report-tiles-to-dashboards-work-with-paginated-reports"></a>Outros recursos específicos de relatório no Power BI, como a fixação de relatórios de blocos a painéis, funcionam com relatórios paginados?

A intenção é que os relatórios suportem os mesmos cenários principais no serviço, tanto quanto possível.  De maneira ideal, embora a ferramenta para criá-los seja diferente, na perspectiva do consumidor eles são apenas mais um relatório em uma lista no portal. Eles não se importam com o modo como os relatórios foram criados, pois conseguem fazer o que precisam.  Um bom exemplo dessa paridade de recursos é o suporte ao comentário planejado. Embora o recurso possa funcionar de maneira um pouco diferente para cada tipo de relatório, você poderá usar os comentários para ambos.

### <a name="is-there-a-report-viewer-control-for-paginated-reports-in-the-power-bi-service"></a>Existe um controle de visualizador de relatórios para relatórios paginados no serviço do Power BI?

Não, um controle de visualizador de relatórios não está disponível no momento.

### <a name="can-you-search-for-paginated-reports-from-the-new-home-experience-in-the-power-bi-service"></a>Você pode pesquisar relatórios paginados a partir da nova experiência inicial no serviço do Power BI?

Sim, agora é possível pesquisar seus relatórios paginados na Página Inicial.  Também é possível vê-los em outras partes da nova experiência com a Página Inicial.

## <a name="considerations-and-troubleshooting"></a>Considerações e solução de problemas
Descubra o que você precisa ter em mente ao trabalhar com os campos DateTime em relatórios paginados.

- Atualmente, há algumas limitações de globalização relacionadas aos parâmetros de DateTime. Todos os parâmetros de DateTime no serviço do Power BI são buscados no formato dos EUA (MM/DD/AAAA), independentemente de como você cria o DataTime no Power BI Report Builder.

## <a name="next-steps"></a>Próximas etapas

- [Instale o Construtor de Relatórios do Power BI no Centro de Download da Microsoft](https://go.microsoft.com/fwlink/?linkid=2086513)
- [Tutorial: Criar um relatório paginado](paginated-reports-quickstart-aw.md)
