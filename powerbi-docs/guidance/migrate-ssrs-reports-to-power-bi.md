---
title: Migrar relatórios do SQL Server Reporting Services para o Power BI
description: Orientações para ajudar você a migrar relatórios do SSRS (SQL Server Reporting Services) para o Power BI.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 01/03/2020
ms.author: v-pemyer
ms.openlocfilehash: f8b7cc302cd4a26aa099f723f47865723dccb7c9
ms.sourcegitcommit: b59ec11a4a0a3d5be2e4d91548d637d31b3491f8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2020
ms.locfileid: "78290626"
---
# <a name="migrate-sql-server-reporting-services-reports-to-power-bi"></a>Migrar relatórios do SQL Server Reporting Services para o Power BI

Este artigo destina-se a autores de relatórios do SSRS (SQL Server Reporting Services) e a administradores do Power BI. Ele fornece orientações para ajudar você a migrar seus relatórios [RDL (Report Definition Language)](/sql/reporting-services/reports/report-definition-language-ssrs) para o Power BI.

> [!NOTE]
> Só é possível migrar relatórios RDL. No Power BI, relatórios RDL são chamados de _relatórios paginados_.

As orientações estão divididas em quatro estágios. Recomendamos que primeiro você leia o artigo inteiro antes de migrar os relatórios.

1. [Antes de iniciar](#before-you-start)
1. [Estágio pré-migração](#pre-migration-stage)
1. [Estágio de migração](#migration-stage)
1. [Estágio pós-migração](#post-migration-stage)

Você pode efetuar a migração sem que haja tempo de inatividade para os servidores do SSRS e sem interromper os usuários de seus relatórios. É importante entender que nenhum dado ou relatório precisa ser removido. Ou seja, você pode manter seu ambiente atual em vigor até que esteja pronto para que ele seja desativado.

## <a name="before-you-start"></a>Antes de começar

Antes de iniciar a migração, você precisa verificar se o seu ambiente atende a determinados pré-requisitos. Descreveremos esses pré-requisitos e também apresentaremos uma ferramenta de migração útil.

### <a name="preparing-for-migration"></a>Preparando para a migração

Ao se preparar para migrar seus relatórios para o Power BI, verifique primeiro se sua organização tem uma assinatura do [Power BI Premium](../service-premium-what-is.md). É necessário ter essa assinatura para hospedar e executar seus relatórios paginados do Power BI.

### <a name="supported-versions"></a>Versões com suporte

Você pode migrar instâncias do SSRS em execução no local ou em máquinas virtuais hospedadas por provedores de nuvem, como o Azure.

A lista a seguir descreve as versões do SQL Server com suporte para migração para o Power BI:

> [!div class="checklist"]
> - SQL Server 2012
> - SQL Server 2014
> - SQL Server 2016
> - SQL Server 2017
> - SQL Server 2019

A migração do Servidor de Relatórios do Microsoft Power BI também é possível.

### <a name="migration-tool"></a>Ferramenta de migração

Recomendamos que você use a [Ferramenta de Migração RDL](https://github.com/microsoft/RdlMigration) para ajudar a preparar e migrar seus relatórios. Essa ferramenta foi desenvolvida pela Microsoft para ajudar os clientes a migrar relatórios RDL de seus servidores do SSRS para o Power BI. Ela está disponível no GitHub e é acompanhada por explicação de ponta a ponta do cenário de migração.

A ferramenta automatiza as seguintes tarefas:

- Verifica [fontes de dados sem suporte](../paginated-reports-data-sources.md) e [recursos de relatório sem suporte](../paginated-reports-faq.md#what-paginated-report-features-in-ssrs-arent-yet-supported-in-power-bi)
- Converte _recursos compartilhados_ em _recursos inseridos_:
  - **Fontes de dados** compartilhadas se tornam fontes de dados inseridas
  - **Conjuntos de dados** compartilhados se tornam conjuntos de dados inseridos
- Publica os relatórios (que são aprovados em verificações) como relatórios paginados em um workspace especificado do Power BI (na capacidade Premium)

Ela não modifica nem remove relatórios existentes. Após a conclusão, a ferramenta gera um resumo de todas as ações concluídas — com ou sem êxito.

Com o passar do tempo, a ferramenta pode ser aprimorada pela Microsoft. Incentivamos a comunidade a contribuir e a aprimorá-la também.

## <a name="pre-migration-stage"></a>Estágio pré-migração

Depois de verificar se sua organização atende aos pré-requisitos, você está pronto para iniciar o estágio _Pré-migração_. Este estágio tem três fases:

1. Descobrir
1. Avaliar
1. Preparar

### <a name="discover"></a>Descobrir

O objetivo da fase _Descobrir_ é identificar as instâncias existentes do SSRS. Esse processo envolve examinar a rede para identificar todas as instâncias do SQL Server em sua organização.

Você pode usar o [Microsoft Assessment and Planning Toolkit](https://www.microsoft.com/download/details.aspx?id=7826). Também conhecido como "MAP Toolkit", ele descobre e emite relatórios sobre suas instâncias, versões e recursos instalados do SQL Server. Trata-se de uma ferramenta avançada de inventário, avaliação e relatório que pode simplificar o processo de planejamento da migração.

### <a name="assess"></a>Avaliar

Depois de descobrir suas instâncias do SSRS, o objetivo da fase _Avaliar_ é saber quais relatórios – ou itens de servidor – do SSRS não podem ser migrados.

Somente relatórios RDL podem ser migrados de seus servidores do SSRS para o Power BI. Cada relatório RDL migrado se tornará um relatório paginado do Power BI.

No entanto, os seguintes tipos de itens do SSRS não podem ser migrados para o Power BI:

- Fontes de dados compartilhadas <sup>1</sup>
- Conjuntos de dados compartilhados <sup>1</sup>
- Recursos, como arquivos de imagem
- KPIs (SSRS 2016 ou posterior – somente Edição Enterprise)
- Relatórios móveis (SSRS 2016 ou posterior – somente Edição Enterprise)
- Modelos de relatório (preterido)
- Partes de relatório (preterido)

<sup>1</sup> A [Ferramenta de Migração de RDL](https://github.com/microsoft/RdlMigration) converte automaticamente fontes de dados compartilhadas e conjuntos de dados compartilhados, desde que eles estejam usando fontes de dados com suporte.

Se seus relatórios RDL dependerem de recursos [ainda sem suporte dos relatórios paginados do Power BI](../paginated-reports-faq.md#what-paginated-report-features-in-ssrs-arent-yet-supported-in-power-bi), você poderá planejar desenvolvê-los novamente como [relatórios do Power BI](../consumer/end-user-reports.md). Mesmo que seus relatórios RDL possam ser migrados, recomendamos que você considere modernizá-los como relatórios do Power BI quando fizer sentido.

Se os seus relatórios RDL precisarem recuperar dados de _fontes de dados locais_, eles não poderão usar o SSO (logon único). Atualmente, toda a recuperação de dados dessas fontes será feita usando o contexto de segurança da _conta de usuário da fonte de dados do gateway_. Não é possível para o SSAS (SQL Server Analysis Services) impor a RLS (segurança em nível de linha) por usuário.

De modo geral, os relatórios paginados do Power BI são otimizados para **impressão** ou **geração de PDF**. Os relatórios do Power BI são otimizados para **exploração e interatividade**. Para obter mais informações, confira [Quando usar relatórios paginados no Power BI](report-paginated-or-power-bi.md).

### <a name="prepare"></a>Preparar

O objetivo da fase _Preparar_ envolve a preparação de tudo. Ela inclui a configuração do ambiente do Power BI, o planejamento de como você protegerá e publicará os relatórios e ideias para desenvolver novamente os itens do SSRS que não serão migrados.

1. Verifique se a [carga de trabalho Relatórios Paginados](../service-admin-premium-workloads.md#paginated-reports) está habilitada em sua capacidade Premium do Power BI e se ela tem memória suficiente.
1. Verifique o suporte para as [fontes de dados](../paginated-reports-data-sources.md) de seu relatório e configure um [Power BI Gateway](../service-gateway-onprem.md) para permitir a conectividade com qualquer fonte de dados local.
1. Familiarize-se com a segurança do Power BI e planeje [como você reproduzirá suas pastas e permissões do SSRS](/sql/reporting-services/security/secure-folders) com [workspaces do Power BI e funções de workspace](../service-new-workspaces.md).
1. Familiarize-se com o compartilhamento do Power BI e planeje como você distribuirá conteúdo publicando [aplicativos do Power BI](../service-create-distribute-apps.md).
1. Considere usar [conjuntos de dados compartilhados do Power BI](../service-datasets-build-permissions.md) no lugar de suas fontes de dado compartilhadas do SSRS.
1. Use o [Power BI Desktop](../desktop-what-is-desktop.md) para desenvolver relatórios otimizados para dispositivos móveis, possivelmente usando o [visual personalizado Power KPI](https://appsource.microsoft.com/product/power-bi-visuals/WA104381083?tab=Overview) em vez dos KPIs e relatórios móveis do SSRS.
1. Reavalie o uso do campo interno **UserID** em seus relatórios. Se você depender do **UserID** para proteger os dados do relatório, entenda que, para os relatórios paginados (quando hospedados no serviço do Power BI), ele retorna o UPN (nome principal do usuário). Portanto, em vez de retornar o nome da conta do NT, por exemplo _AW\mblythe_, o campo interno retornará algo como _m.blythe&commat;adventureworks.com_. Você precisará revisar suas definições de conjunto de dados e, possivelmente, a fonte de dados. Depois de revisado e publicado, recomendamos que você teste os relatórios exaustivamente para garantir que as permissões de dados funcionem conforme o esperado.
1. Reavalie o uso do campo interno **ExecutionTime** em seus relatórios. Para relatórios paginados (quando hospedados no serviço do Power BI), o campo interno retorna a data/hora _em UTC (tempo universal coordenado)_ . Isso pode afetar os valores padrão de parâmetro de relatório e os rótulos de tempo de execução de relatório (normalmente adicionados aos rodapés de relatório).
1. Se sua fonte de dados for SQL Server (local), verifique se os relatórios não estão usando visualizações de mapa. A visualização de mapa depende de tipos de dados espaciais do SQL Server, e não há suporte para eles no gateway. Para obter mais informações, confira [Diretrizes de recuperação de dados para relatórios paginados (tipos de dados complexos do SQL Server)](report-paginated-data-retrieval.md#sql-server-complex-data-types).
1. Certifique-se de que os autores de relatório tenham o [Power BI Report Builder](../report-builder-power-bi.md) instalado e que versões posteriores possam ser distribuídas facilmente em toda a sua organização.

## <a name="migration-stage"></a>Estágio de migração

Depois de preparar seu ambiente e os relatórios do Power BI, você estará pronto para o estágio de _Migração_.

Há duas opções de migração: _manual_ e _automatizada_. A migração manual é adequada para um pequeno número de relatórios ou para relatórios que exigem modificação antes da migração. A migração automatizada é adequada para a migração de um grande número de relatórios.

### <a name="manual-migration"></a>Migração manual

Qualquer pessoa com permissão para acessar a instância do SSRS e o workspace do Power BI pode migrar manualmente os relatórios para o Power BI. Estas são as etapas a serem seguidas:

1. Abra o portal do SSRS que contém os relatórios que você deseja migrar.
1. Baixe cada definição de relatório, salvando os arquivos .rdl localmente.
1. Abra a _versão mais recente_ do Power BI Report Builder e conecte-se ao serviço do Power BI usando suas credenciais do Azure AD.
1. Abra cada relatório no Power BI Report Builder e, em seguida:
   1. Verifique se todas as fontes de dados e conjuntos de dados estão inseridos na definição do relatório e se são [fontes de dados com suporte](../paginated-reports-data-sources.md).
   1. Visualize o relatório para garantir que seja renderizado corretamente.
   1. Escolha a opção _Salvar como_ e, em seguida, selecione _serviço do Power BI_.
   1. Selecione o workspace que conterá o relatório.
   1. Verifique se o relatório é salvo. Se determinados recursos no design do relatório ainda não tiverem suporte, a ação de salvar falhará. Você será notificado dos motivos. Em seguida, você precisará revisar o design do relatório e tentar salvar novamente.

### <a name="automated-migration"></a>Migração automatizada

Há duas opções para a migração automatizada. Você pode usar:

- A Ferramenta de Migração de RDL
- As APIs disponíveis publicamente para SSRS e Power BI

A [Ferramenta de Migração de RDL](#migration-tool) já foi descrita neste artigo.

Você também pode usar as APIs do SSRS e do Power BI disponíveis publicamente para automatizar a migração de seu conteúdo. Embora a Ferramenta de Migração de RDL já use essas APIs, você pode desenvolver uma ferramenta personalizada adequada para seus requisitos exatos.

Para obter mais informações sobre as APIs, confira:

- [Referência da API REST do Power BI](../developer/rest-api-reference.md)
- [APIs REST do SQL Server Reporting Services](/sql/reporting-services/developer/rest-api)

## <a name="post-migration-stage"></a>Estágio pós-migração

Depois de concluir a migração com êxito, você pode prosseguir para o estágio _Pós-migração_. Este estágio envolve efetuar uma série de tarefas pós-migração para garantir que tudo esteja funcionando corretamente e com eficiência.

### <a name="configure-data-sources"></a>Configurar fonte de dados

Após os relatórios terem sido migrados para o Power BI, você precisará garantir que suas fontes de dados estejam configuradas corretamente. Isso pode envolver a atribuição de fontes de dados de gateway e o [armazenamento seguro de credenciais de fonte de dados](../paginated-reports-data-sources.md#azure-sql-database-authentication). Isso não é feito pela Ferramenta de Migração de RDL.

### <a name="review-report-performance"></a>Examinar o desempenho do relatório

É altamente recomendável que você conclua as ações a seguir para garantir a melhor experiência possível para os usuários do relatório:

1. Teste os relatórios em cada [navegador com suporte do Power BI](../power-bi-browsers.md) para confirmar se eles são renderizados corretamente.
1. Execute testes para comparar os tempos de renderização de relatório no SSRS e no Power BI. Verifique se os relatórios do Power BI são renderizados em um tempo aceitável.
1. Se os relatórios do Power BI não forem renderizados em decorrência de memória insuficiente, aloque [recursos adicionais à capacidade Premium do Power BI](../service-admin-premium-workloads.md#paginated-reports).
1. Para relatórios de renderização longa, considere fazer com que o Power BI os entregue aos usuários como [assinaturas de email com relatórios anexos](../consumer/paginated-reports-subscriptions.md).
1. Para relatórios do Power BI baseados em conjuntos de dados do Power BI, examine os designs de modelo para garantir que eles sejam totalmente otimizados.

### <a name="reconcile-issues"></a>Reconciliar problemas

A fase pós-migração é crucial para reconciliar problemas e solucionar preocupações de desempenho. Adicionar a carga de trabalho de relatórios paginados a uma capacidade pode levar a um desempenho lento – para os relatórios paginados _e outros conteúdos_ armazenados na capacidade.

Para obter mais informações sobre esses problemas, incluindo etapas específicas para entender e atenuá-los, consulte os seguintes artigos:

- [Otimização de capacidades Premium](../service-premium-capacity-optimize.md)
- [Monitorar capacidades Premium no aplicativo](../service-admin-premium-monitor-capacity.md)

## <a name="next-steps"></a>Próximas etapas

Para obter mais informações sobre este artigo, confira os seguintes recursos:

- [O que são os relatórios paginados no Power BI Premium?](../paginated-reports-report-builder-power-bi.md)
- [Diretrizes de recuperação de dados para relatórios paginados](report-paginated-data-retrieval.md)
- [Quando usar relatórios paginados no Power BI](report-paginated-or-power-bi.md)
- [Relatórios paginados no Power BI: perguntas frequentes](../paginated-reports-faq.md)
- [Perguntas Frequentes do Power BI Premium](../service-premium-faq.md)
- [Ferramenta de Migração de RDL](https://github.com/microsoft/RdlMigration)
- Dúvidas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
- Sugestões? [Contribuir com ideias para aprimorar o Power BI](https://ideas.powerbi.com/)

Os parceiros do Power BI estão disponíveis para ajudar sua organização a ter sucesso com o processo de migração. Para envolver um parceiro do Power BI, visite o [portal de parceiro de Power BI](https://powerbi.microsoft.com/partners/).
