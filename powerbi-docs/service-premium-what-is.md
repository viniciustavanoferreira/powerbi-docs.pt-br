---
title: O que é o Microsoft Power BI Premium?
description: O Power BI Premium oferece capacidades dedicadas para sua organização, oferecendo desempenho mais confiável e maiores volumes de dados, sem exigir a aquisição de licenças por usuário.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 09/17/2019
ms.custom: seodec18
LocalizationGroup: Premium
ms.openlocfilehash: c46b58369c334ff5364cee00bb5c3f8cd025adf0
ms.sourcegitcommit: 57e45f291714ac99390996a163436fa1f76db427
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/26/2019
ms.locfileid: "71305854"
---
# <a name="what-is-power-bi-premium"></a>O que é o Power BI Premium?

O Power BI Premium oferece recursos dedicados e aprimorados para executar o serviço do Power BI para sua organização. Por exemplo:

> [!div class="checklist"]
> * Maior dimensionamento e desempenho
> * Flexibilidade para licença por capacidade
> * Unifique o BI corporativo e de autoatendimento
> * Estenda o BI local com o Servidor de Relatórios do Power BI
> * Suporte para residência de dados por região (Multi-Geo)
> * Compartilhe dados com qualquer pessoa sem comprar uma licença por usuário

Este artigo apresenta os principais recursos do Power BI Premium. Quando necessário, serão fornecidos links para outros artigos com informações mais detalhadas.

## <a name="subscriptions-and-licensing"></a>Assinaturas e licenciamento

O Power BI Premium é uma assinatura do Office 365 de nível de locatário disponível em duas famílias de SKU (Unidade de Manutenção de Estoque):

- SKUs **EM** (EM1-EM3) para inserção, exigindo um compromisso anual cobrado mensalmente. Os SKUs EM1 e EM2 estão disponíveis somente por meio de planos de licenciamento por volume. Não é possível comprá-los diretamente.
- SKUs **P** (P1-P3) para recursos corporativos e de inserção, exigindo um compromisso mensal ou anual, cobrado mensalmente, com a inclusão de uma licença para instalar o Servidor de Relatórios do Power BI local.

Uma abordagem alternativa é comprar uma assinatura do **Azure Power BI Embedded**, que tem uma única família de SKU **A** (A1-A6) somente para fins de inserção e de teste de capacidade. Todos os SKUs oferecem núcleos virtuais para criar capacidades, mas os SKUs EM estão restritos para inserção de menor escala. As SKUs EM1, EM2, A1 e A2 com menos de quatro núcleos virtuais não são executadas em uma infraestrutura dedicada.

Embora o foco deste artigo esteja nos SKUs P, muito do que foi descrito também é relevante para os SKUs A. Em contraste com os SKUs da assinatura Premium, os SKUs do Azure não exigem nenhum compromisso de tempo e são cobrados por hora. Elas oferecem elasticidade total, permitindo escala vertical/horizontal, pausa, retomada e exclusão. 

O Azure Power BI Embedded está amplamente fora do escopo deste artigo, mas é descrito na seção [Abordagens de Teste](service-premium-capacity-optimize.md#testing-approaches) do artigo Como otimizar capacidades Premium como uma opção prática e econômica para testar e medir cargas de trabalho. Para saber mais sobre os SKUs do Azure, confira [Documentação do Azure Power BI Embedded](https://azure.microsoft.com/services/power-bi-embedded/).

### <a name="purchasing"></a>Compra

As assinaturas do Power BI Premium são compradas por administradores no centro de administração do Microsoft 365. Especificamente, apenas administradores globais do Office 365 ou de Cobrança podem comprar SKUs. Quando adquiridos, o locatário recebe um número correspondente de núcleos virtuais a ser atribuído a capacidades, conhecido como *pool de núcleos virtuais*. Por exemplo, adquirir um SKU P3 fornece ao locatário 32 núcleos virtuais. Para saber mais, confira [Como comprar o Power BI Premium](service-admin-premium-purchase.md).

## <a name="dedicated-capacities"></a>Capacidades dedicadas

Com o Power BI Premium, você obtém *capacidades dedicadas*. Em contraste com uma capacidade compartilhada em que cargas de trabalho são executadas em recursos computacionais compartilhados com outros clientes, uma capacidade dedicada é para uso exclusivo de uma organização. Ela é isolada com recursos computacionais dedicados que oferecem desempenho confiável e consistente para conteúdo hospedado. 

Os workspaces residem dentro de capacidades. Cada usuário do Power BI tem um workspace pessoal, conhecido como **Meu workspace**. Espaços de trabalho adicionais, conhecidos como **Espaços de Trabalho do Aplicativo**, podem ser criados para habilitar a colaboração e a implantação. Por padrão, os workspaces, incluindo os pessoais, são criados na capacidade compartilhada. Quando você tem capacidades Premium, o Meu workspaces e os Workspaces do Aplicativo podem ser atribuídos a capacidades Premium.

### <a name="capacity-nodes"></a>Nós de capacidade

Conforme descrito na seção [Assinaturas e Licenciamento](#subscriptions-and-licensing), há duas famílias de SKU do Power BI Premium: **EM** e **P**. Todos os SKUs do Power BI Premium estão disponíveis como *nós* de capacidade, cada um representando uma quantidade definida de recursos compostos por processador, memória e armazenamento. Além de recursos, cada SKU tem limites operacionais sobre o número de conexões DirectQuery e Conexão Dinâmica por segundo e sobre o número de atualizações de modelo paralelo.

O processamento é realizado por um número definido de núcleos virtuais, dividido igualmente entre o back-end e o front-end.

Os **núcleos virtuais de back-end** são responsáveis pela funcionalidade básica do Power BI, incluindo o processamento de consultas, o gerenciamento de cache, a execução de serviços R, a atualização de modelo, o processamento de idioma natural (P e R) e a renderização de relatórios e imagens do servidor. Os núcleos virtuais de back-end recebem uma quantidade fixa de memória que é usada principalmente para hospedar modelos, também conhecidos como conjuntos de dados ativos.

Os **núcleos virtuais de front-end** são responsáveis pelo gerenciamento de documentos de relatório, dashboard e serviço Web, gerenciamento de direitos de acesso, agendamento, APIs, uploads e downloads e geralmente por tudo o que está relacionado às experiências do usuário.

O armazenamento é definido como **100 TB por nó de capacidade**.

Os recursos e limites de cada SKU Premium (e o SKU A de tamanho equivalente) são descritos na tabela a seguir:

| Nós de Capacidade | Total de núcleos virtuais | Núcleos virtuais de back-end | RAM (GB) | Núcleos virtuais de front-end | DirectQuery/Conexão Dinâmica (por s) | Paralelismo de atualização de modelo |
| --- | --- | --- | --- | --- | --- | --- |
| EM1/A1 | 1 | 0,5 | 2.5 | 0,5 | 3,75 | 1 |
| EM2/A2 | 2 | 1 | 5 | 1 | 7,5 | 2 |
| EM3/A3 | 4 | 2 | 10 | 2 | 15 | 3 |
| P1/A4 | 8 | 4 | 25 | 4 | 30 | 6 |
| P2/A5 | 16 | 8 | 50 | 8 | 60 | 12 |
| P3/A6 | 32 | 16 | 100 | 16 | 120 | 24 |
| | | | | | | |

### <a name="capacity-workloads"></a>Cargas de trabalho de capacidade

Cargas de trabalho de capacidade são serviços disponibilizados aos usuários. Por padrão, as capacidades Premium e Azure dão suporte apenas a uma carga de trabalho do conjunto de dados associada à execução de consultas do Power BI. A carga de trabalho do conjunto de dados não pode ser desabilitada. Outras cargas de trabalho podem ser habilitadas para [IA (Serviços Cognitivos)](https://powerbi.microsoft.com/blog/easy-access-to-ai-in-power-bi-preview/), [Fluxos de dados](service-dataflows-overview.md#dataflow-capabilities-on-power-bi-premium) e [Relatórios paginados](paginated-reports-save-to-power-bi-service.md). Essas cargas de trabalho são compatíveis apenas com assinaturas Premium. 

Cada carga de trabalho adicional permite a configuração da memória máxima (como um percentual do total de memória disponível) que pode ser usada pela carga de trabalho. Os valores padrão para a memória máxima são determinados por SKU. É possível maximizar os recursos disponíveis de sua capacidade habilitando apenas as cargas de trabalho adicionais quando elas são usadas. E você poderá alterar as configurações de memória apenas quando tiver determinado que as configurações padrão não estão atendendo aos requisitos de recursos de capacidade. As cargas de trabalho podem ser habilitadas e configuradas para uma capacidade por administradores de capacidade usando as **Configurações de capacidade** no [portal de administração](service-admin-portal.md) ou usando as [APIs REST de capacidades](https://docs.microsoft.com/rest/api/power-bi/capacities).  

![Habilitar cargas de trabalho](media/service-admin-premium-workloads/admin-portal-workloads.png)

Para saber mais, confira [Configurar cargas de trabalho em uma capacidade Premium](service-admin-premium-workloads.md). 

### <a name="how-capacities-function"></a>Como as capacidades funcionam

O serviço do Power BI sempre faz o melhor uso dos recursos de capacidade e, ao mesmo tempo, não excede os limites impostos sobre a capacidade.

As operações de capacidade são classificadas como *interativas* ou *em segundo plano*. Operações interativas incluem a renderização de solicitações e a resposta às interações do usuário (filtragem, perguntas e respostas, consultas etc.). Em geral, a consulta do modelo de importação faz uso intensivo de recursos de memória, enquanto a consulta de modelos DirectQuery e de Conexão Dinâmica faz uso intensivo da CPU. As operações em segundo plano incluem o fluxo de dados e as atualizações de modelo de importação, além de armazenamento em cache de consultas de dashboard.

É importante entender que as operações interativas são sempre priorizadas em vez de operações em segundo plano para garantir a melhor experiência do usuário possível. Se houver recursos insuficientes, serão adicionadas operações em segundo plano a uma fila para processamento quando os recursos forem liberados. Operações em segundo plano, como atualizações de conjunto de dados, podem ser interrompidas no meio do processo pelo serviço do Power BI e adicionadas a uma fila.

Modelos de importação devem ser totalmente carregados na memória para que possam ser consultados ou atualizados. O serviço do Power BI gerencia o uso de memória usando algoritmos sofisticados para verificar o uso máximo de memória disponível e pode gerar uma confirmação excessiva da capacidade: Embora seja possível que uma capacidade armazene muitos modelos de importação (até 100 TB por capacidade Premium), quando seu armazenamento em disco combinado excede a memória compatível (e é necessária uma memória adicional para consulta e atualização), então eles não poderão ser carregados na memória ao mesmo tempo.

Modelos de importação, portanto, são carregados no e removidos da memória de acordo com o uso. Um modelo de importação é carregado quando é consultado (operação interativa) e ainda não está na memória ou quando deve ser atualizado (operação em segundo plano).

A remoção de um modelo de memória é conhecida como *remoção*. É uma operação que o Power BI pode executar rapidamente dependendo do tamanho dos modelos. Se a capacidade não estiver enfrentando nenhuma pressão de memória, os modelos serão simplesmente carregados na memória e permanecerão lá. No entanto, quando uma memória insuficiente estiver disponível para carregar um modelo, o serviço do Power BI precisará liberar memória primeiro. Ele libera memória por meio da detecção de modelos que se tornaram inativos procurando modelos que não foram usados nos últimos três minutos \[[1](#endnote-1)\] e, em seguida, removendo-os. Se não houver nenhum modelo inativo para remover, o serviço do Power BI buscará remover modelos carregados para operações em segundo plano. Um último recurso, após 30 segundos de tentativas falhas \[[1](#endnote-1)\], é falhar a operação interativa. Nesse caso, o usuário de relatório é notificado sobre a falha com uma sugestão para tentar novamente em breve. Em alguns casos, os modelos podem ser descarregados da memória devido a operações de serviço.

É importante enfatizar que a remoção do conjunto de dados é um comportamento normal e esperado. Ela busca maximizar o uso de memória carregando e descarregando modelos cujos tamanhos combinados podem exceder a memória disponível. Isso ocorre por design e é transparente para os usuários de relatório. Altas taxas de remoção não necessariamente significam que a capacidade tem recursos insuficientes. Elas poderão, contudo, tornar-se uma preocupação se a capacidade de resposta da consulta ou da atualização estiver apresentando problemas devido a altas taxas de remoção.

As atualizações de modelos de importação sempre fazem uso intensivo de memória, pois os modelos devem ser carregados na memória. É necessário ter memória adicional para processamento. Uma atualização completa pode usar aproximadamente o dobro da quantidade de memória exigida pelo modelo. Isso garante que o modelo possa ser consultado até mesmo quando estiver sendo processado, pois as consultas são enviadas para o modelo existente até que a atualização tenha sido concluída e os dados do modelo novo estejam disponíveis. Uma atualização incremental exigirá menos memória e poderia ser concluída mais rapidamente; portanto, isso poderá reduzir substancialmente a pressão sobre os recursos de capacidade. As atualizações também podem fazer uso intensivo da CPU para modelos, principalmente aqueles com transformações complexas de Power Query ou colunas/tabelas calculadas que são complexas ou baseadas em grandes tabelas.

As atualizações, como consultas, exigem que o modelo seja carregado na memória. Se não houver memória suficiente, o serviço do Power BI tentará remover modelos inativos e, se não for possível (pois todos os modelos estão ativos), o trabalho de atualização será enfileirado. Normalmente, as atualizações fazem uso intensivo da CPU, ainda mais do que as consultas. Por esse motivo, há limites de capacidade sobre o número de atualizações simultâneas, definidos como 1,5x o número de núcleos virtuais de back-end, arredondados para cima. Se houver atualizações simultâneas demais, uma atualização agendada será enfileirada. Quando essas situações ocorrem, demora mais para a atualização ser concluída. Atualizações sob demanda, como aquelas disparadas por uma solicitação de usuário ou por uma chamada à API, serão repetidas três vezes \[[1](#endnote-1)\]. Se ainda não houver recursos suficientes, a atualização falhará.

Notas da seção:   
<a name="endnote-1"></a>\[1\] Sujeito a alteração.

### <a name="regional-support"></a>Suporte regional

Ao criar uma capacidade, os Administradores globais do Office 365 e os administradores de serviços do Power BI podem especificar uma região em que os workspaces atribuídos à capacidade residirão. Isso é conhecido como **Multi-Geo**. Com o Multi-Geo, as organizações poderão atender aos requisitos de residência de dados implantando conteúdo em datacenters em uma região específica, mesmo se ela for diferente da região na qual a Assinatura do Office 365 reside. Para saber mais, confira [Suporte Multi-Geo para o Power BI Premium](service-admin-premium-multi-geo.md).

### <a name="capacity-management"></a>Gerenciamento de capacidade

O gerenciamento de capacidades Premium envolve a criação ou a exclusão de capacidades, a atribuição de administradores e de workspaces, a configuração de cargas de trabalho, o monitoramento e a realização de ajustes para otimizar o desempenho da capacidade. 

Os Administradores globais do Office 365 e os administradores de serviços do Power BI podem criar capacidades Premium com base em núcleos virtuais disponíveis ou modificar capacidades Premium existentes. Quando uma capacidade é criada, seu tamanho e região geográfica são especificados e pelo menos um administrador de capacidade é atribuído. 

Quando forem criadas capacidades, a maioria das tarefas administrativas será concluída no [portal de Administração](service-admin-portal.md).

![Portal de administração](media/service-premium-what-is/premium-admin-portal.png)

Os administradores de capacidade podem atribuir workspaces à capacidade, gerenciar permissões de usuário e atribuir outros administradores. Os administradores de capacidade também podem configurar cargas de trabalho, ajustar alocações de memória e, se necessário, reiniciar uma capacidade, redefinindo operações no caso de uma sobrecarga de capacidade.

![Portal de administração](media/service-premium-what-is/premium-admin-portal-mgmt.png)

Os administradores de capacidade também podem verificar se uma capacidade está sendo executada sem problemas. Eles podem monitorar a integridade da capacidade diretamente no portal do Administrador ou usando o aplicativo de métricas de capacidade Premium.

Para saber mais sobre como criar capacidades, atribuir administradores e atribuir workspaces, confira [Como gerenciar capacidades Premium](service-premium-capacity-manage.md). Para saber mais sobre as funções, confira [Funções de administrador relacionadas ao Power BI](service-admin-administering-power-bi-in-your-organization.md#administrator-roles-related-to-power-bi).

### <a name="monitoring"></a>Monitoramento

O monitoramento de capacidades Premium fornece aos administradores uma compreensão de como as capacidades são executadas. As capacidades podem ser monitoradas usando o portal do Administrador e o [aplicativo Métricas de Capacidade do Power BI Premium](https://app.powerbi.com/groups/me/getapps/services/capacitymetrics).

O monitoramento no portal oferece uma exibição rápida com métricas de alto nível que indicam cargas colocadas e os recursos utilizados por sua capacidade, em média, durante os últimos sete dias. 

![Portal de administração](media/service-premium-what-is/premium-admin-portal-health.png)

O aplicativo **Métricas de Capacidade do Power BI Premium** oferece as informações mais detalhadas sobre o desempenho de suas capacidades. O aplicativo oferece um dashboard de alto nível e relatórios mais detalhados.

![Dashboard do aplicativo de métricas](media/service-admin-premium-monitor-capacity/app-dashboard.png)

No painel do aplicativo, é possível clicar em uma célula de métrica para abrir um relatório aprofundado. Os relatórios oferecem métricas e capacidade de filtragem aprofundadas para fazer drill down nas informações mais importantes de que você precisa para manter suas capacidades em execução sem problemas.

![Contagens de tempo de espera de picos periódicos de consulta indicam uma possível saturação da CPU](media/service-premium-capacity-scenarios/peak-query-wait-times.png)

Para saber mais sobre capacidades de monitoramento, confira [Monitoramento no portal do Administrador do Power BI](service-admin-premium-monitor-portal.md) e [Monitoramento com o aplicativo Métricas de Capacidade do Power BI Premium](service-admin-premium-monitor-capacity.md).

### <a name="optimizing-capacities"></a>Como otimizar capacidades

Fazer o melhor uso das capacidades é essencial para garantir que os usuários obtenham desempenho e que você esteja obtendo o máximo de valor do seu investimento no Premium. Ao monitorar as principais métricas, os administradores podem determinar a melhor maneira de solucionar problemas de gargalos e tomar as medidas necessárias. Para saber mais, confira [Como otimizar capacidades Premium](service-premium-capacity-optimize.md) e [Cenários de capacidade Premium](service-premium-capacity-scenarios.md).

### <a name="capacities-rest-apis"></a>APIs REST de capacidades

As APIs REST do Power BI incluem uma coleção de [APIs de Capacidades](https://docs.microsoft.com/rest/api/power-bi/capacities). Com as APIs, os administradores podem gerenciar de maneira programática muitos aspectos de suas capacidades Premium, incluindo a habilitação e a desabilitação de cargas de trabalho, a atribuição de workspaces a uma capacidade e muito mais.

## <a name="large-datasets"></a>Grandes conjuntos de dados

Dependendo do SKU, o Power BI Premium é compatível com o carregamento de arquivos de modelo do Power BI Desktop (.pbix) até o máximo de **10 GB** de tamanho. Quando carregado, o modelo poderá ser publicado em um workspace atribuído a uma capacidade Premium. O conjunto de dados pode ser atualizado para até **12 GB** de tamanho.

### <a name="size-considerations"></a>Considerações sobre tamanho

Grandes modelos podem fazer uso intensivo de recursos. Você deve ter pelo menos um SKU P1 para todos os modelos maiores que 1 GB. Embora a publicação de grandes modelos em workspaces com suporte de SKUs A até A3 talvez funcione, atualizá-los não funcionará.

A tabela a seguir descreve os SKUs recomendados para vários tamanhos .pbix:

   |SKU  |Tamanho de .pbix   |
   |---------|---------|
   |P1    | < 3 GB        |
   |P2    | < 6 GB        |
   |P3, P4, P5    | até 10 GB   |

O SKU A4 do Power BI Embedded é igual ao SKU P1, o A5 = P2 e o A6 = P3. A publicação de grandes modelos em SKUs A e EM pode retornar erros que não são específicos para o erro de limitação de tamanho do modelo na capacidade compartilhada. Erros de atualização de modelos grandes em SKUs A e EM provavelmente são resultados de atingimento de tempos limite. 

Os arquivos .pbix representam dados em um *estado altamente compactado*. Os dados provavelmente expandirão várias vezes quando carregados na memória e, a partir daí, eles podem expandir várias vezes mais durante a atualização de dados.

A atualização agendada de grandes conjuntos de dados pode demorar muito tempo e usar muitos recursos. É importante não agendar muitas atualizações sobrepostas. Recomendamos configurar a [atualização incremental](service-premium-incremental-refresh.md), pois ela é mais rápida e confiável e consome menos recursos.

A carga inicial do relatório de grandes conjuntos de dados poderá demorar muito tempo se um período já tiver transcorrido desde a última vez em que o conjunto de dados foi usado. Uma barra de carregamento para relatórios demorados exibe o progresso do carregamento.

Enquanto as restrições de tempo e memória por consulta são muito maiores na capacidade Premium, é recomendável usar filtros e segmentações de dados para limitar os visuais para exibir apenas o que é necessário.

## <a name="incremental-refresh"></a>Atualização incremental

A atualização incremental fornece uma parte integral de ter e manter grandes conjuntos de dados no Power BI Premium. A atualização incremental tem muitos benefícios, por exemplo, atualizações são mais rápidas porque somente os dados que foram alterados precisam ser atualizados. As atualizações são mais confiáveis porque não é necessário manter conexões longas com fontes de dados voláteis. O consumo de recursos é reduzido porque um número menor de dados para atualização reduz o consumo geral da memória e de outros recursos. As políticas de atualização incremental são definidas no **Power BI Desktop** e aplicadas quando publicadas em um workspace em uma capacidade Premium. 

![Detalhes da atualização](media/service-premium-incremental-refresh/refresh-details.png)

Para saber mais, confira [Atualização incremental no Power BI Premium](service-premium-incremental-refresh.md).

## <a name="paginated-reports"></a>Relatórios paginados

Os relatórios paginados, compatíveis nos SKUs P1-P3 e A4-A6, são baseados na tecnologia de linguagem RDL no SQL Server Reporting Services. Embora baseados na tecnologia RDL, não são os mesmos que os do Servidor de Relatórios do Power BI, que é uma plataforma de relatório que pode ser baixada e instalada localmente, além de estar incluída no Power BI Premium. Os relatórios paginados são formatados para se ajustarem bem em uma página que pode ser impressa ou compartilhada. Os dados serão exibidos em uma tabela, mesmo se a tabela abranger várias páginas. Usando o aplicativo gratuito de Área de Trabalho do Windows do [**Construtor de Relatórios do Power BI**](https://go.microsoft.com/fwlink/?linkid=2086513), os usuários criam relatórios paginados e os publicam no serviço.

No Power BI Premium, relatórios paginados são uma carga de trabalho que deve ser habilitada para uma capacidade usando o portal do administrador. Os administradores de capacidade podem habilitar e especificar a quantidade de memória como um percentual dos recursos de memória geral da capacidade. Diferentemente de outros tipos de cargas de trabalho, o Premium executa relatórios paginados em um espaço contido dentro da capacidade. A memória máxima especificada para este espaço será usada se a carga de trabalho estiver ou não ativa. O padrão é 20%. 

Para saber mais, confira [Relatórios paginados no Power BI Premium](paginated-reports-report-builder-power-bi.md). Para saber mais sobre como habilitar a carga de trabalho de Relatórios paginados, confira [Configurar cargas de trabalho](service-admin-premium-workloads.md).

## <a name="power-bi-report-server"></a>Servidor de Relatórios do Power BI
 
Incluído com o Power BI Premium, o Servidor de Relatórios do Power BI é um servidor de relatório *local* com um portal da Web. É possível criar seu ambiente de BI localmente e distribuir relatórios protegidos pelo firewall da sua organização. O Servidor de Relatório permite aos usuários acesso a funcionalidades de criação de relatório avançadas, interativas e corporativas do SQL Server Reporting Services. Os usuários podem explorar dados visuais e descobrir rapidamente padrões para tomar decisões melhores e mais rápidas. O Servidor de Relatório oferece governança nos seus próprios termos. Se e quando chegar o momento, o Servidor de Relatórios do Power BI facilitará a migração para a nuvem, na qual sua organização poderá aproveitar completamente a funcionalidade do Power BI Premium.

Para saber mais, confira [Servidor de Relatórios do Power BI](report-server/get-started.md).

## <a name="unlimited-content-sharing"></a>Compartilhamento de conteúdo ilimitado

Com o Premium, qualquer pessoa, dentro ou fora da organização, pode exibir todo o conteúdo do Power BI, incluindo relatórios paginados e interativos, sem comprar licenças individuais. 

![Compartilhamento de conteúdo](media/service-premium-what-is/premium-sharing.png)

O Premium possibilita a distribuição difundida de conteúdo por usuários do Pro, sem precisar de licenças do Pro para os destinatários que veem o conteúdo. As licenças Pro são necessárias para criadores de conteúdo. Os criadores conectam-se a fontes de dados, modelam dados e criam relatórios e dashboards empacotados como aplicativos de workspace. 

Para saber mais, confira [Licenciamento do Power BI](service-admin-licensing-organization.md).

## <a name="tool-connectivity-preview"></a>Conectividade da ferramenta (versão prévia)

Nos bastidores, o **mecanismo Vertipaq do Analysis Services** da Microsoft comprovado para empresas habilita os conjuntos de dados do Power BI. O Analysis Services oferece capacidade de programação e aplicativo cliente e suporte à ferramenta por meio de bibliotecas de cliente e APIs que dão suporte ao protocolo XMLA de padrão aberto. No momento, os conjuntos de dados do Power BI Premium dão suporte a operações *somente leitura* da Microsoft e a ferramentas e aplicativos cliente de terceiros por meio de **pontos de extremidade XMLA**. 

As ferramentas da Microsoft, como o SQL Server Management Studio e o SQL Server Profiler, e aplicativos de terceiros, como o DAX Studio, e os aplicativos de visualização de dados podem se conectar a conjuntos de dados Premium e consultá-los usando XMLA, DAX, MDX, DMVs e eventos de rastreamento. 

![SSMS](media/service-premium-what-is/connect-tools-ssms-dax.png)

Para saber mais, confira [Conectar-se a conjuntos de dados com ferramentas e aplicativos cliente](service-premium-connect-tools.md).

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Como gerenciar capacidades Premium](service-premium-capacity-manage.md)

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)

||||||
