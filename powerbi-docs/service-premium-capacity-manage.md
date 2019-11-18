---
title: Gerenciar as capacidades do Microsoft Power BI Premium
description: Descreve as tarefas de gerenciamento para as capacidades do Power BI Premium.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/10/2019
ms.custom: seodec18
LocalizationGroup: Premium
ms.openlocfilehash: a2b51d2a03a9d3b88d31bc7d7d232fef0b2251d6
ms.sourcegitcommit: 8cc2b7510aae76c0334df6f495752e143a5851c4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73431729"
---
# <a name="managing-premium-capacities"></a>Gerenciamento de capacidades Premium

O gerenciamento do Power BI Premium envolve a criação, o gerenciamento e o monitoramento de capacidades Premium. Este artigo fornece uma visão geral das capacidades; confira [Configurar e gerenciar capacidades](service-admin-premium-manage.md) para obter instruções passo a passo.

## <a name="creating-and-managing-capacities"></a>Criar e gerenciar capacidades

A página **Configurações de Capacidade** do Portal de administração do Power BI exibe o número de núcleos virtuais comprados e as capacidades Premium disponíveis. A página possibilita aos Administradores globais do Office 365 e aos administradores de serviços do Power BI criar capacidades Premium com base em núcleos virtuais disponíveis ou modificar capacidades Premium existentes.

Ao criar uma capacidade Premium, os administradores devem definir:

- Nome da capacidade (exclusivo no locatário).
- Administradores de capacidades.
- Tamanho da capacidade.
- Região da residência de dados.

Pelo menos um Administrador de capacidade deve ser atribuído. Os usuários atribuídos como Administradores de capacidades podem:

- Atribuir espaços de trabalho à capacidade.
- Gerenciar permissões de usuário para adicionar Administradores de capacidade adicionais ou usuários com permissões de atribuição (para permitir que eles atribuam espaços de trabalho à capacidade).
- Gerenciar cargas de trabalho para configurar o uso máximo de memória para cargas de trabalho paginadas de relatórios e fluxos de dados.
- Reiniciar a capacidade para redefinir todas as operações em caso de sobrecarga do sistema.

Os Administradores de capacidade não podem acessar o conteúdo do espaço de trabalho, a menos que estejam explicitamente atribuídos nas permissões do espaço de trabalho. Eles também não têm acesso a todas as áreas de administração do Power BI (a menos que sejam explicitamente atribuídas), como métricas de uso, logs de auditoria ou configurações de locatário. É importante ressaltar que os Administradores de capacidade não têm permissões para criar novas capacidades ou dimensionar as capacidades existentes. Os administradores são atribuídos por capacidade e isso garante que eles possam visualizar e gerenciar apenas as capacidades às quais estão atribuídos.

O tamanho da capacidade é escolhido em uma lista disponível de opções do SKU, que é restrita pelo número de núcleos virtuais disponíveis no pool. É possível criar várias capacidades a partir do pool e elas podem ser originárias de um ou mais SKUs adquiridos. Por exemplo, o SKU de uma P3 (32 núcleos virtuais) pode ser usado para criar três capacidades: uma P2 (16 núcleos virtuais) e duas P1 (2 x 8 núcleos virtuais). É possível obter desempenho e dimensionamento aprimorados com a criação de capacidades de tamanho menor, conforme descrito no artigo [Otimização de capacidades Premium](service-premium-capacity-optimize.md). A imagem a seguir mostra um exemplo de configuração para a organização fictícia Contoso, que é composta por cinco capacidades Premium (3 x P1 e 2 x P3), cada uma contendo workspaces e vários workspaces com capacidade compartilhada.

![Uma configuração de exemplo para a organização fictícia Contoso](media/service-premium-capacity-manage/contoso-organization-example.png)

Uma capacidade Premium pode ser atribuída a uma região que não seja a região inicial do locatário do Power BI, conhecida como Multi-Geo. A Multi-Geo fornece controle administrativo sobre quais datacenters em regiões geográficas definidas seu conteúdo do Power BI reside. A lógica por trás de uma implantação multi-geográfica, normalmente, visa à conformidade corporativa ou governamental e não ao desempenho e ao dimensionamento. O carregamento de relatórios e painéis ainda envolve solicitações de metadados para a região de residência. Para saber mais, confira [Suporte Multi-Geo para o Power BI Premium](service-admin-premium-multi-geo.md).

Os administradores de serviços do Power BI e os Administradores Globais do Office 365 podem modificar as capacidades Premium. Especificamente, podem:

- Alterar o tamanho da capacidade para reduzir ou ampliar o dimensionamento dos recursos.
- Adicionar ou remover Administradores de capacidade.
- Adicionar ou remover usuários que têm permissões de atribuição.
- Adicionar ou remover cargas de trabalho adicionais.
- Alterar regiões.

São necessárias permissões de atribuição para atribuir um espaço de trabalho a uma capacidade Premium específica. As permissões podem ser concedidas a toda a organização, usuários específicos ou grupos.

Por padrão, as capacidades Premium dão suporte às cargas de trabalho associadas à execução de consultas do Power BI. As capacidades Premium também dão suporte a cargas de trabalho adicionais: **IA (Serviços Cognitivos)** , **Relatórios Paginados** e **Fluxos de Dados**. Cada carga de trabalho permite a configuração da memória máxima (como um percentual do total de memória disponível), que pode ser usada pela carga de trabalho. É importante entender que o aumento da alocação máxima de memória pode afetar o número de modelos ativos que podem ser hospedados e a taxa de transferência de atualizações. 

A memória é dinamicamente alocada para fluxos de dados, mas é alocada estaticamente para relatórios paginados. O motivo para alocar estaticamente a memória máxima é que os relatórios paginados são executados em um espaço contido e seguro da capacidade. Deve-se tomar cuidado ao configurar a memória de relatórios paginados, pois isso reduz a memória disponível para o carregamento de modelos. Para saber mais, confira as [Configurações de memória padrão](service-admin-premium-workloads.md#default-memory-settings).

As capacidades Premium podem ser excluídas, mas isso não levará à exclusão de seus espaços de trabalho e conteúdo. Em vez disso, os espaços de trabalho atribuídos são movidos para a capacidade compartilhada. Se a capacidade Premium é criada em uma região diferente, o espaço de trabalho é movido para a capacidade compartilhada da região de origem.

### <a name="assigning-workspaces-to-capacities"></a>Atribuir espaços de trabalho às capacidades

Os workspaces podem ser atribuídos a uma capacidade Premium no Portal de administração do Power BI ou no painel **Workspace**.

Os Administradores de capacidade, além dos Administradores globais do Office 365 ou os administradores de serviços do Power BI, podem atribuir espaços de trabalho em massa no Portal de administração do Power BI. A atribuição em massa pode se aplicar a:

- **Espaços de trabalho por usuários**: todos os espaços de trabalho desses usuários, incluindo espaços de trabalho pessoais, são atribuídos à capacidade Premium. Isso inclui a reatribuição de espaços de trabalho quando eles já estão atribuídos a uma capacidade Premium diferente. Além disso, os usuários também recebem permissões de atribuição de espaços de trabalho.

- **Workspaces específicos**
- **Espaços de trabalho de toda a organização**: todos os espaços de trabalho, incluindo espaços de trabalho pessoais, são atribuídos à capacidade Premium. Todos os usuários atuais e futuros recebem permissões de atribuição de espaços de trabalho. Essa abordagem não é recomendada. Dê preferência a uma abordagem mais direcionada.

Um espaço de trabalho pode ser adicionado a uma capacidade Premium usando o painel **Espaço de trabalho** desde que o usuário seja um administrador do espaço de trabalho e tenha permissões de atribuição.

![Usar o painel Espaço de trabalho para atribuir um espaço de trabalho a uma capacidade Premium](media/service-premium-capacity-manage/assign-workspace-capacity.png)

Os administradores de espaços de trabalho podem remover um espaço de trabalho de uma capacidade (para uma capacidade compartilhada) sem a permissão de atribuição. A remoção de espaços de trabalho de capacidades dedicadas realoca efetivamente o espaço de trabalho em uma capacidade compartilhada. Observe que a remoção de um espaço de trabalho de uma capacidade Premium pode ter consequências negativas, resultando, por exemplo, na indisponibilidade do conteúdo compartilhado para usuários licenciados do Power BI Free, ou na suspensão da atualização agendada quando eles excederem os limites compatíveis com as capacidades compartilhadas.

No serviço do Power BI, um espaço de trabalho atribuído a uma capacidade Premium é facilmente identificado pelo ícone de losango que ilustra o nome do espaço de trabalho.

![Identificar um espaço de trabalho atribuído a uma capacidade Premium](media/service-premium-capacity-manage/premium-diamond-icon.png)

## <a name="monitoring-capacities"></a>Monitorar capacidades

O monitoramento de capacidades Premium fornece aos administradores uma compreensão de como as capacidades são executadas. As capacidades podem ser monitoradas usando o Portal de administração do Power BI ou o aplicativo **Métricas de capacidade do Power BI Premium** (Power BI).

### <a name="power-bi-admin-portal"></a>Portal de administração do Power BI

No Portal de administração de cada capacidade, a guia **Integridade** oferece métricas de resumo para a capacidade e cada carga de trabalho habilitada. As métricas mostram uma média dos últimos sete dias.  

No nível da capacidade, as métricas representam o valor cumulativo de todas as cargas de trabalho ativadas. São fornecidas as seguintes métricas:

- **UTILIZAÇÃO DA CPU**: fornece a utilização média da CPU como uma porcentagem do total disponível da CPU para a capacidade.  
- **USO DA MEMÓRIA**: fornece o uso médio da memória (em GB) como um total da memória disponível para a capacidade. 

Para cada carga de trabalho habilitada são fornecidos o uso da memória e a utilização da CPU, além de uma série de métricas específicas da carga de trabalho. Por exemplo, para a carga de trabalho Fluxo de dados, a **Contagem Total** mostra as atualizações totais para cada fluxo de dados e a **Duração Média** mostra a duração média da atualização do fluxo de dados.

![Guia Integridade da capacidade no portal](media/service-premium-capacity-manage/admin-portal-health-dataflows.png)

Para saber mais sobre todas as métricas disponíveis para cada carga de trabalho, confira [Monitorar capacidades no portal de administração](service-admin-premium-monitor-portal.md).

Os recursos de monitoramento no Portal de administração do Power BI foram projetados para fornecer um resumo rápido das principais métricas de capacidade. Para realizar um monitoramento mais detalhado, recomenda-se usar o aplicativo **Métricas de capacidade do Power BI Premium**.

### <a name="power-bi-premium-capacity-metrics-app"></a>Aplicativo Métricas de capacidade do Power BI Premium

O aplicativo [Métricas de capacidade do Power BI Premium](https://appsource.microsoft.com/product/power-bi/pbi_pcmm.pbi-premiumcapacitymonitoring?tab=Overview) é um aplicativo do Power BI disponível para administradores de capacidade e é instalado como qualquer outro aplicativo do Power BI. Ele conta com um painel e um relatório.

![Aplicativo Métricas de capacidade do Power BI Premium](media/service-premium-capacity-manage/capacity-metrics-app.png)

Quando o aplicativo abre, o painel é carregado para apresentar vários blocos que expressam uma exibição agregada sobre todas as capacidades das quais o usuário é um Administrador de capacidade. O layout do painel contém cinco seções principais:

- **Visão geral**: versão do aplicativo, número de capacidades e espaços de trabalho
- **Resumo do sistema**: métricas de memória e CPU
- **Resumo do conjunto de dados**: número de conjuntos de dados, DQ/LC, métricas de atualização e consulta
- **Resumo do fluxo de dados**: número de fluxos de dados e métricas do conjunto de dados
- **Resumo do relatório paginado**: atualizar e exibir métricas

O relatório subjacente, do qual os blocos do painel foram fixados, pode ser acessado clicando em qualquer bloco do painel. Ele oferece uma perspectiva mais detalhada de cada uma das seções do painel e dá suporte à filtragem interativa. 

É possível executar a filtragem com a definição de segmentações por intervalo de datas, capacidade, espaço de trabalho e carga de trabalho (relatório, conjunto de dados, fluxo de dados) e a escolha de elementos nos recursos visuais do relatório para filtrar a página do relatório. A filtragem cruzada é uma técnica avançada para restringir períodos de tempo, capacidades, espaços de trabalho, conjuntos de dados, etc. específicos e pode ser muito útil durante a execução da análise de causa raiz.

Para saber mais sobre o painel e as métricas de relatório no aplicativo, confira [Monitorar as capacidades Premium com o aplicativo](service-admin-premium-monitor-capacity.md).

### <a name="interpreting-metrics"></a>Interpretar métricas

As métricas devem ser monitoradas para se estabelecer um entendimento básico do uso de recursos e da atividade da carga de trabalho. Se a capacidade ficar lenta, é importante entender quais métricas monitorar e quais conclusões tirar.

O ideal seria que as consultas fossem concluídas em um segundo para oferecer experiências dinâmicas para relatar usuários e permitir uma taxa de transferência de consulta mais elevada. Normalmente, é uma preocupação menor quando os processos em segundo plano (incluindo atualizações) levam mais tempo para concluir.

Em geral, relatórios lentos podem ser uma indicação de uma capacidade com superaquecimento. Quando os relatórios não carregam, é indicação de uma capacidade superaquecida. Em qualquer situação, a causa raiz pode ser atribuível a muitos fatores, incluindo:

- **Falha em consultas** certamente indica pressão da memória e que não foi possível carregar um modelo na memória. O serviço do Power BI tentará carregar um modelo por 30 segundos antes de falhar.

- **Tempos de espera excessivos em consultas** podem derivar de vários motivos:
  - A necessidade do serviço do Power BI primeiro remover o modelo e depois carregar o modelo a ser consultado (lembre-se de que taxas mais altas de remoção do conjunto de dados não são apenas uma indicação de estresse da capacidade, a menos que sejam acompanhadas por longos tempos de espera de consulta que indicam ultrapaginação de memória).
  - Tempos de carregamento do modelo (especialmente a espera para carregar um modelo grande na memória).
  - Consultas de execução prolongada.
  - Muitas conexões LC\DQ (excedendo os limites de capacidade).
  - Saturação da CPU.
  - Designs complexos de relatórios com um número excessivo de recursos visuais em uma página (lembre-se de que cada visual é uma consulta).

- As **longas durações das consultas** podem indicar que os designs do modelo não estão otimizados, especialmente quando vários conjuntos de dados estão ativos em uma capacidade e apenas um conjunto de dados está produzindo longas durações de consultas. Isso sugere que a capacidade tem recursos suficientes e que o conjunto de dados em questão está abaixo do ideal ou é apenas lento. As consultas de execução prolongada podem ser problemáticas, pois podem bloquear o acesso aos recursos exigidos por outros processos.
- Os **longos tempos de espera de atualização** indicam memória insuficiente devido a muitos modelos ativos que consomem memória ou que uma atualização problemática está bloqueando outras atualizações (excedendo os limites de atualizações paralelas).

Uma explicação mais detalhada de como usar as métricas é abordada no artigo [Otimização de capacidades Premium](service-premium-capacity-optimize.md).

## <a name="acknowledgements"></a>Agradecimentos

Este artigo foi escrito por Peter Myers, MVP de plataforma de dados e especialista independente de BI da [Bitwise Solutions](https://www.bitwisesolutions.com.au/).

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Otimização de capacidades Premium](service-premium-capacity-optimize.md)   
> [!div class="nextstepaction"]
> [Configurar cargas de trabalho em uma capacidade Premium](service-admin-premium-workloads.md)   

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)

