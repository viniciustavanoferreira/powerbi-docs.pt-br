---
title: Monitorar as métricas de uso de dashboards e relatórios
description: Como exibir, salvar e usar métricas de uso de relatórios e dashboards do Power BI.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 10/21/2019
LocalizationGroup: Dashboards
ms.openlocfilehash: 9aa2e11dd2068cae118336268c5c55ead1e25b8b
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/05/2020
ms.locfileid: "73871221"
---
# <a name="monitor-usage-metrics-for-power-bi-dashboards-and-reports"></a>Monitorar as métricas de uso de relatórios e dashboards do Power BI

Se você cria dashboards e relatórios, as métricas de uso ajudam a compreender seus impactos. Quando executa as métricas de uso de um painel ou de um relatório, você descobre como esses painéis e relatórios estão sendo usados em sua organização – quem os está usando, e para que finalidade.  

Relatórios de métricas de uso são somente leitura. No entanto, você pode copiar um relatório de métricas de uso. A cópia cria um relatório padrão do Power BI que você pode editar. Você também pode criar seus próprios relatórios no Power BI Desktop com base no conjunto de dados subjacente, que contém métricas de uso para todos os painéis ou todos os relatórios em um workspace. Para começar, o relatório copiado mostra as métricas apenas para o relatório ou painel selecionado. Você pode remover o filtro padrão e ter acesso ao conjunto de dados subjacente, com todas as métricas de uso do workspace selecionado. Você pode até ver os nomes de usuários específicos, se o seu administrador habilitou esse recurso.

![relatório de métricas de uso](media/service-usage-metrics/power-bi-dashboard-usage-metrics-update-3.png)

> [!NOTE]
> As métricas de uso acompanham o uso dos relatórios que são inseridos no SharePoint Online. No entanto, as métricas de uso não acompanham painéis e relatórios inseridos por meio do fluxo "o usuário tem credenciais" ou "o aplicativo tem credenciais". As métricas de uso também não acompanham o uso de relatórios inseridos por meio do recurso [Publicar na Web](service-publish-to-web.md).

## <a name="why-usage-metrics-are-important"></a>Por que as métricas de uso são importantes

Saber como seu conteúdo está sendo usado ajuda a demonstrar seu impacto e priorizar esforços. As métricas de uso podem mostrar que um dos relatórios é usado diariamente por um grande segmento da organização e pode mostrar que um dashboard criado não está sendo exibido. Esse tipo de comentário é imprescindível para orientar seus esforços de trabalho.

Você só pode executar relatórios de métricas de uso no serviço do Power BI. No entanto, se salvar um relatório de métricas de uso ou fixá-lo em um dashboard, você poderá abrir e interagir com ele em dispositivos móveis.

## <a name="prerequisites"></a>Pré-requisitos

- É necessária uma licença do Power BI Pro para executar e acessar os dados de métricas de uso. Entretanto, o recurso de métricas de uso captura informações de uso de todos os usuários, independentemente da licença.
- Para obter acesso às métricas de uso para um relatório ou painel específico, é necessário ter acesso de edição a esse relatório ou painel.
- Seu administrador do Power BI precisa ter habilitado métricas de uso para criadores de conteúdo. Ele também pode ter habilitado a coleta de dados por usuário em métricas de uso. Leia sobre como [habilitar essas opções no portal de administração](service-admin-portal.md#control-usage-metrics). 

## <a name="view-a-usage-metrics-report"></a>Exibir um relatório de métricas de uso

1. Inicie no workspace que contém o dashboard ou o relatório.
2. Na lista de conteúdo do workspace ou no dashboard ou relatório em si, selecione o ícone de **Métricas de uso** ![ícone de métricas de uso](media/service-usage-metrics/power-bi-usage-metrics-report-icon.png).

    ![Guia Dashboards](media/service-usage-metrics/power-bi-run-usage-metrics-report.png)

    ![selecionar Métricas de uso](media/service-usage-metrics/power-bi-run-usage-metrics-report2.png)
3. Na primeira vez que você fizer isso, o Power BI criará o relatório de métricas de uso e lhe informará quando ele estiver pronto.

    ![as métricas estão prontas](media/service-usage-metrics/power-bi-usage-metrics-ready.png)
4. Para conferir os resultados, selecione **Exibir métricas de uso**.

    As métricas de uso são um poderoso aliado enquanto você trabalha para implantar e manter relatórios e dashboards do Power BI. Está se perguntando quais páginas do seu relatório são mais úteis e quais você deveria descontinuar? Fatie por **Página de relatório** para descobrir. Gostaria de saber se você deve criar um layout para dispositivos móveis para seu dashboard? Fatie por **Plataformas** para descobrir quantos usuários estão acessando seu conteúdo por meio dos aplicativos móveis versus por meio do navegador da Web.

5. Opcionalmente, passe o mouse sobre uma visualização e selecione o ícone de fixar para adicionar a visualização a um dashboard. Ou, na barra de menus superior, selecione **Fixar esta Página em Tempo Real** para adicionar a página inteira a um painel. Do painel, você pode monitorar as métricas de uso mais facilmente ou compartilhá-las com outras pessoas.

    > [!NOTE]
    > Se você fixar um bloco de um relatório de métricas de uso em um painel, não será possível adicionar esse painel a um aplicativo.

### <a name="dashboard-usage-metrics-report"></a>Relatório de Métrica de uso do Dashboard

![Relatório de Métrica de uso do Dashboard](media/service-usage-metrics/power-bi-dashboard-usage-metrics-update-3.png)

### <a name="report-usage-metrics-report"></a>Relatório de Métrica de uso do Relatório

![Relatório de métricas de uso do Relatório](media/service-usage-metrics/power-bi-report-usage-metrics-update.png)

## <a name="about-the-usage-metrics-report"></a>Sobre o relatório de métrica de uso

Quando você seleciona **Métrica de uso** ou o ![ícone de métricas de uso](media/service-usage-metrics/power-bi-usage-metrics-report-icon.png) próximo a um relatório ou painel, o Power BI gera um relatório predefinido com métrica de uso para esse conteúdo nos últimos 90 dias.  O relatório é semelhante aos relatórios do Power BI que você já conhece. Você pode fatiar com base em como seus usuários finais tiveram acesso – se eles acessaram pela Web, por um aplicativo móvel etc. Conforme seus dashboards e relatórios evoluírem, o relatório de métricas de uso também evoluirá e será atualizado todos os dias com novos dados.  

Os relatórios de métricas de uso não são exibidos em **Recente**, **Espaços de trabalho**, **Favoritos** ou em outras listas de conteúdo. Eles não podem ser adicionados a um aplicativo. Se você fixar um bloco de um relatório de métricas de uso em um painel, não será possível adicionar esse painel a um aplicativo.

Para acessar os dados do relatório ou criar seus próprios relatórios em relação ao conjunto de dados subjacente, você tem duas opções: 

- Fazer uma cópia do relatório no serviço do Power BI. Confira [Salvar uma cópia do relatório de métricas de uso](#save-a-copy-of-the-usage-metrics-report) mais adiante neste artigo para obter detalhes.
- Conectar-se ao conjunto de dados do Power BI Desktop. Para cada workspace, o conjunto de relatórios tem o nome "Modelo de métricas de uso de relatório". Confira [Estabelecer uma conexão a um conjunto de dados publicado](desktop-report-lifecycle-datasets.md#establish-a-power-bi-service-live-connection-to-the-published-dataset) para obter detalhes.

    ![Conectar-se a um conjunto de dados de relatório de uso](media/service-usage-metrics/power-bi-usage-dataset.png)

## <a name="which-metrics-are-reported"></a>Quais métricas são relatadas?

| Metric | Dashboard | Relatório | Descrição |
| --- | --- | --- | --- |
| Segmentação do método de distribuição |sim |sim |Como os usuários têm acesso ao conteúdo. Há três métodos possíveis: os usuários podem acessar o dashboard ou o relatório sendo membros de um [workspace](consumer/end-user-experience.md), fazendo com que o conteúdo seja [compartilhado com eles](service-share-dashboards.md) ou instalando um aplicativo/pacote de conteúdo.  Observe que as exibições por meio de um aplicativo são contadas como um "pacote de conteúdo". |
| Segmentação de plataformas |sim |sim |O dashboard ou o relatório foi acessado pelo serviço do Power BI (powerbi.com) ou por um dispositivo móvel? O dispositivo móvel inclui todos os nossos aplicativos iOS, Android e Windows. |
| Segmentação da página de relatório |não |sim |Se o relatório tiver mais de uma página, segmente o relatório por página(s) que foi exibido. Se houver uma opção de lista "Em Branco", isso significará que uma página de relatório foi adicionada recentemente (em até 24 horas, o nome real da nova página será exibido na lista de segmentação) e/ou que páginas do relatório foram excluídas. "Em branco" captura esses tipos de situações. |
| Exibições por dia |sim |sim |Número total de exibições por dia – uma exibição é definida como um usuário que carrega uma página ou dasbhoard de relatório. |
| Visualizadores únicos por dia |sim |sim |Número de usuários *diferentes* que exibiram o dashboard ou relatório (com base na conta de usuário do AAD). |
| Exibições por usuário |sim |sim |Número de exibições nos últimos 90 dias, dividido por usuários individuais. |
| Compartilhamentos por dia |sim |não |Número de vezes que o dashboard foi compartilhado com outro usuário ou grupo. |
| Total de exibições |sim |sim |Número de exibições nos últimos 90 dias. |
| Total de visualizadores |sim |sim |Número de visualizadores únicos nos últimos 90 dias. |
| Total de compartilhamentos |sim |não |Número de vezes que o dashboard ou o relatório foi compartilhado nos últimos 90 dias. |
| Total na organização |sim |sim |Contagem de todos os dashboards ou relatórios em toda a organização que tiveram pelo menos uma exibição nos últimos 90 dias.  Usado para calcular a classificação. |
| Classificação: Total de exibições |sim |sim |Para o total de exibições de todos os dashboards ou relatórios na organização durante os últimos 90 dias, no qual este dashboard ou relatório é classificado. |
| Classificação: Total de compartilhamentos |sim |não |Para o total de compartilhamentos de todos os dashboards na organização durante os últimos 90 dias, no qual este dashboard ou relatório é classificado. |

## <a name="save-a-copy-of-the-usage-metrics-report"></a>Salvar uma cópia do relatório Métricas de uso

Use **Salvar como** para converter o relatório de métricas de uso em um relatório normal do Power BI que você pode personalizar para atender às suas necessidades específicas. Você também pode usar o Power BI Desktop para criar relatórios de métricas de uso personalizados com base no conjunto de dados subjacente. Confira [Estabelecer uma conexão a um conjunto de dados publicado](desktop-report-lifecycle-datasets.md#establish-a-power-bi-service-live-connection-to-the-published-dataset) para obter detalhes.

Ainda melhor, o conjunto de dados subjacente inclui os detalhes de uso de todos os dashboards ou relatórios no workspace. Isso abre mais possibilidades. Você pode, por exemplo, criar um relatório que compara todos os painéis em seu workspace com base no uso. Ou você pode criar um painel de métricas de uso para seu aplicativo do Power BI agregando o uso em todo o conteúdo distribuído nesse aplicativo.  Confira como remover o filtro e [ver todas as métricas de uso do workspace](#see-all-workspace-usage-metrics) mais adiante neste artigo.

### <a name="create-a-copy-of-the-usage-report"></a>Criar uma cópia do relatório de uso

Quando você cria uma cópia do relatório de uso pré-criado, somente leitura, o Power BI cria uma cópia editável do relatório. À primeira vista, ele parece ser o mesmo relatório. No entanto, agora você pode abrir o relatório no Modo de Exibição de Edição, adicionar novas visualizações, filtros e páginas, modificar ou excluir visualizações existentes e mais. O Power BI salva o novo relatório no workspace atual.

1. No relatório de métricas de uso pré-criado, selecione **Arquivo > Salvar como**. O Power BI cria um relatório do Power BI editável, salvo no workspace atual.

    ![Salvar como](media/service-usage-metrics/power-bi-save-as.png)
2. Abra o relatório no modo de edição e [interaja com ele como você faria com qualquer outro relatório do Power BI](service-interact-with-a-report-in-editing-view.md). Por exemplo, adicione novas páginas e crie novas visualizações, adicione filtros, formate as fontes e cores, etc.

    ![Abrir o relatório no Modo de Exibição de Edição](media/service-usage-metrics/power-vi-editing-view.png)
3. O novo relatório é salvo na guia **Relatórios** no espaço de trabalho atual e também adicionado à lista de conteúdo **Recente**.

    ![Guia Relatórios](media/service-usage-metrics/power-bi-new-report.png)

## <a name="see-all-workspace-usage-metrics"></a>Ver *todas* as métricas de uso do workspace

Para ver as métricas de todos os painéis ou de todos os relatórios no workspace, você precisa remover um filtro. Por padrão, o relatório é filtrado para exibir métricas somente para o painel ou relatório que você usou para criá-lo.

1. Selecione **Editar relatório** para abrir o novo relatório editável no Modo de Exibição de Edição.

    ![selecione Editar relatório](media/service-usage-metrics/power-bi-editing-view.png)
2. No painel Filtros, localize o bucket **Filtros de nível de relatório** e remova o filtro selecionando a borracha ao lado de **ReportGuid**.

    ![Remover o filtro](media/service-usage-metrics/power-bi-usage-report-clear-filter.png)

    Agora, seu relatório exibe as métricas de todo o workspace.

## <a name="power-bi-admin-controls-for-usage-metrics"></a>Controles de administração do Power BI para métricas de uso

Os relatórios de métrica de uso são um recurso que o administrador do Power BI ou do Office 365 pode ativar ou desativar. Os administradores têm controle granular sobre quais usuários terão acesso às métricas de uso. Elas são **ativadas** por padrão para todos os usuários na organização.

> [!NOTE]
> Somente administradores do locatário do Power BI podem ver o portal do administrador e editar as configurações. 

Por padrão, os dados por usuário estão habilitados para as métricas de uso e as informações de conta do consumidor do conteúdo estão incluídas no relatório de métricas. Se os administradores não quiserem expor essa informação para alguns ou todos os usuários, eles podem desabilitar o recurso para grupos de segurança especificados ou para toda a organização. Em seguida, as informações da conta serão mostradas no relatório como *Sem nome*.

Ao desabilitar as métricas de uso para toda a sua organização, os administradores podem usar a opção **excluir todo o conteúdo existente de métricas de uso** para excluir todos os relatórios e blocos de painéis existentes que foram criados usando os relatórios de métricas de uso. Esta opção remove todo o acesso aos dados de métricas de uso para todos os usuários da organização que já podem estar usando esses dados. A exclusão do conteúdo de métricas de uso existente é irreversível.

Confira [Controlar métricas de uso](service-admin-portal.md#control-usage-metrics) no artigo do portal de administração para obter detalhes sobre essas configurações. 

## <a name="usage-metrics-in-national-clouds"></a>Métricas de uso em nuvens nacionais

O Power BI está disponível em nuvens nacionais separadas. Essas nuvens oferecem os mesmos níveis de segurança, privacidade, conformidade e transparência que a versão global do Power BI, combinados com um modelo exclusivo para regulamentos locais sobre entrega de serviço, residência de dados, acesso e controle. Devido a esse modelo exclusivo para regulamentações locais, as métricas de uso não estão disponíveis em nuvens nacionais. Para obter mais informações, confira [nuvens nacionais](https://powerbi.microsoft.com/clouds/).

## <a name="considerations-and-limitations"></a>Considerações e limitações

### <a name="discrepancies-between-audit-logs-and-usage-metrics"></a>Discrepâncias entre os logs de auditoria e as métricas de uso

É importante entender as diferenças que podem ocorrer ao comparar as métricas de uso e os logs de auditoria, e por quê. Os *Logs de auditoria* são coletados usando dados do serviço do Power BI e as *métricas de uso* são coletadas no cliente. As contagens de agregação das atividades nos logs de auditoria nem sempre correspondem às métricas de uso, por estes motivos:

* Às vezes, as métricas de uso podem apresentar uma contagem inferior de atividades devido a conexões de rede inconsistentes, bloqueadores de anúncios ou outros problemas que podem interromper o envio de eventos do cliente.
* Certos tipos de modos de exibição não são incluídos em métricas de uso, conforme descrito anteriormente neste artigo.
* Às vezes, as métricas de uso podem apresentar uma contagem superior de atividades, em situações nas quais o cliente é atualizado sem a necessidade de envio de uma solicitação de volta ao serviço do Power BI.

### <a name="other-considerations"></a>Outras considerações

Você precisa exibir o conteúdo em seu workspace, de dentro desse workspace, pelo menos uma vez. Se não houver exibições do conteúdo do próprio workspace pelo menos uma vez, os dados não serão correlacionados das exibições do aplicativo no Relatório de Métricas de Uso. Para desbloquear o processamento de dados para este relatório, basta exibir o conteúdo do workspace pelo menos uma vez.


## <a name="frequently-asked-questions"></a>Perguntas frequentes

Além das possíveis diferenças entre métricas de uso e logs de auditoria, as perguntas e respostas sobre as métricas de uso a seguir podem ser úteis para usuários e administradores:

**P:**    Não consigo executar as métricas de uso em um dashboard ou relatório

**R:**    Você só pode ver métricas de uso para o conteúdo que você possui ou que tem permissões para editar.

**P:**    As métricas de uso capturam as exibições de dashboards e relatórios inseridos?

**R:**    Atualmente, as métricas de uso não dão suporte ao uso de captura para dashboards e relatórios inseridos, nem para o fluxo de [publicar na Web](service-publish-to-web.md). Nesses casos, recomendamos o uso das plataformas de análise da Web existentes para controlar o uso do aplicativo de hospedagem ou portal.

**P:**    Não consigo executar a métrica de uso em nenhum conteúdo.

**A1:**    Os administradores podem desligar esse recurso em sua organização.  Contate seu administrador para ver se é esse o caso.

**A2:**    As métricas de uso são um recurso do Power BI Pro.

**P:**    Os dados não parecem atualizados. Por exemplo, os métodos de distribuição não são exibidos, as páginas do relatório estão ausentes, etc.

**R:**    Pode levar até 24 horas para que os dados sejam atualizados.

**P:**    Há quatro relatórios no workspace, mas o relatório de métricas de uso exibe apenas três.

**R:**    O relatório de métricas de uso inclui somente os relatórios (ou painéis) que foram acessados nos últimos 90 dias.  Se um relatório (ou painel) não aparecer, provavelmente ele não foi usado em mais de 90 dias.

## <a name="next-steps"></a>Próximas etapas

[Como administrar o Power BI no portal de administração](service-admin-portal.md)

Mais perguntas? [Experimente a Comunidade do Power BI](https://community.powerbi.com/)
