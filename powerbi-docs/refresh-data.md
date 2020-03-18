---
title: Atualizar dados no Power BI
description: Este artigo descreve as funcionalidades de atualização de dados do Power BI e suas dependências no nível conceitual.
author: maggiesMSFT
ms.reviewer: kayu
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 10/14/2019
ms.author: maggies
LocalizationGroup: Data refresh
ms.openlocfilehash: 810077e8c651d3d6faf91eecb6fd320c24a69d2f
ms.sourcegitcommit: a175faed9378a7d040a08ced3e46e54503334c07
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79488788"
---
# <a name="data-refresh-in-power-bi"></a>Atualizar dados no Power BI

O Power BI permite que você vá rapidamente dos dados para insights e, então, para a ação. Ainda assim, você precisa garantir que os dados em seus relatórios e dashboards do Power BI sejam recentes. Frequentemente, saber como atualizar os dados é essencial para fornecer resultados precisos.

Este artigo descreve as funcionalidades de atualização de dados do Power BI e suas dependências no nível conceitual. Ele também traz melhores práticas e dicas para evitar problemas comuns com a atualização. O conteúdo estabelece uma base para ajudar você a entender como a atualização de dados funciona. Para obter instruções passo a passo direcionadas para configurar a atualização de dados, confira os tutoriais e guias de instruções listados na seção “Próximas etapas”, no final do artigo.

## <a name="understanding-data-refresh"></a>Entendendo a atualização de dados

Sempre que você atualiza os dados, o Power BI precisa consultar as fontes de dados subjacentes, possivelmente carregar os dados de origem em um conjunto de dados e, em seguida, atualizar as visualizações em seus relatórios ou dashboards que se baseiam no conjunto de dados atualizado. Todo o processo é composto por várias fases, dependendo dos modos de armazenamento de seus conjuntos de dados, conforme explicado nas seções a seguir.

Para entender como o Power BI atualiza os dashboards, relatórios e conjuntos de dados, você precisa conhecer os seguintes conceitos:

- **Modos de armazenamento e tipos de conjuntos de dados**: os modos de armazenamento e os tipos de conjuntos de dados com suporte do Power BI têm requisitos de atualização diferentes. Você pode escolher entre reimportar os dados para o Power BI para ver as alterações que ocorreram ou consultar os dados diretamente na fonte.
- **Tipos de atualização do Power BI**: independentemente das informações específicas sobre o conjunto de dados, conhecer os diferentes tipos de atualização pode ajudar você a entender onde o Power BI pode gastar o tempo durante uma operação de atualização. E combinar esses detalhes com informações específicas sobre o modo de armazenamento ajuda a entender o que exatamente o Power BI faz quando você seleciona **Atualizar agora** para um conjunto de dados.

### <a name="storage-modes-and-dataset-types"></a>Modos de armazenamento e tipos de conjuntos de dados

Um conjunto de dados do Power BI pode operar de um dos modos a seguir para acessar dados de uma variedade de fontes de dados. Para mais informações, veja o [modo de Armazenamento no Power BI Desktop](desktop-storage-mode.md).

- Modo de importação
- Modo DirectQuery
- Modo LiveConnect
- Modo de envio por push

O diagrama a seguir ilustra diferentes fluxos de dados com base no modo de armazenamento. O aspecto mais significativo é que apenas os conjuntos de dados no Modo de importação exigem atualização dos dados de origem. Eles exigem a atualização porque apenas este tipo de conjunto de dados importa dados de suas fontes de dados. Os dados importados podem ser atualizados de modo regular ou ad hoc. Conjuntos de dados nos modos DirectQuery e LiveConnect com o Analysis Services não importam dados, eles consultam a fonte de dados subjacente a cada interação do usuário. Conjuntos de dados no modo de envio por push não acessam nenhuma fonte de dados diretamente, mas esperam que você envie os dados por push para o Power BI. Os requisitos de atualização de conjunto de dados variam dependendo do tipo de conjunto de dados/modo de armazenamento.

![Modos de armazenamento e tipos de conjuntos de dados](media/refresh-data/storage-modes-dataset-types-diagram.png)

#### <a name="datasets-in-import-mode"></a>Conjuntos de dados no Modo de importação

O Power BI importa os dados das fontes de dados originais para o conjunto de dados. As consultas de relatório e de dashboard do Power BI enviadas para o conjunto de dados retornam resultados das tabelas e colunas importadas. Você pode considerar esse conjunto de dados uma cópia pontual. Como o Power BI copia os dados, você precisa atualizar o conjunto de dados para buscar as alterações nas fontes de dados subjacentes.

Como o Power BI armazena os dados em cache, o tamanho do conjunto de dados no Modo de importação pode ser significativo. Confira a tabela a seguir para conhecer os tamanhos máximos do conjunto de dados por capacidade. Fique bem abaixo dos tamanhos máximos dos conjuntos de dados para evitar problemas de atualização que poderão ocorrer se os conjuntos de dados exigirem mais do que os recursos máximos disponíveis durante uma operação de atualização.

| Tipo de capacidade | Tamanho máximo do conjunto de dados |
| --- | --- |
| Compartilhado, A1, A2 ou A3 | 1 GB |
| A4 ou P1 | 3 GB |
| A5 ou P2 | 6 GB |
| A6 ou P3 | 10 GB |
| | |

#### <a name="datasets-in-directqueryliveconnect-mode"></a>Conjuntos de dados no modo DirectQuery/LiveConnect

O Power BI não importa dados usando conexões que operam no modo DirectQuery/LiveConnect. Em vez disso, o conjunto de dados retorna resultados da fonte de dados subjacente sempre que um relatório ou dashboard o consulta. O Power BI transforma e encaminha as consultas à fonte de dados.

Embora os modos DirectQuery e LiveConnect sejam semelhantes porque o Power BI encaminha as consultas para a fonte, é importante observar que o Power BI não precisa transformar as consultas no modo LiveConnect. As consultas vão diretamente para a instância do Analysis Services que hospeda o banco de dados, sem consumir recursos em uma capacidade compartilhada ou uma capacidade Premium.

Uma vez que o Power BI não importa os dados, você não precisa executar uma atualização de dados. No entanto, o Power BI ainda executa atualizações de bloco e, possivelmente, atualizações de relatório, conforme explicado na próxima seção sobre tipos de atualização. Um bloco é um visual de relatório fixado em um dashboard. As atualizações dos blocos do dashboard acontecem aproximadamente de hora em hora para que eles mostrem resultados recentes. Você pode alterar o agendamento nas configurações do conjunto de dados, conforme mostrado na captura de tela abaixo, ou forçar uma atualização do dashboard manualmente usando a opção **Atualizar agora**.

![Agendamento de atualização](media/refresh-data/refresh-schedule.png)

> [!NOTE]
> A seção **Atualização do cache agendada** da guia **Conjuntos de dados** não está disponível para conjuntos de dados no modo de importação. Esses conjuntos de dados não exigem uma atualização de bloco separada porque o Power BI atualiza os blocos automaticamente durante cada atualização de dados agendada ou sob demanda.

#### <a name="push-datasets"></a>Conjuntos de dados por push

Conjuntos de dados por push não contêm uma definição formal de fonte de dados e, portanto, não exigem que você execute uma atualização de dados no Power BI. Você os atualiza enviando os dados por push para o conjunto de dados usando um serviço ou processo externo, como o Azure Stream Analytics. Essa é uma abordagem comum para a análise em tempo real com o Power BI. O Power BI ainda executa atualizações de cache para os blocos usados acima de um conjunto de dados por push. Para ver um passo a passo detalhado, confira [Tutorial: Stream Analytics e Power BI: um dashboard de análise em tempo real para dados de streaming](/azure/stream-analytics/stream-analytics-power-bi-dashboard).

> [!NOTE]
> O Modo de envio por push tem várias limitações, conforme documentado em [Limitações da API REST do Power BI](developer/automation/api-rest-api-limitations.md).

### <a name="power-bi-refresh-types"></a>Tipos de atualização do Power BI

Uma operação de atualização do Power BI pode ser composta por vários tipos de atualização, incluindo atualização de dados, atualização do OneDrive, atualização dos caches de consulta, atualização do bloco e atualização dos visuais de relatório. Embora o Power BI determine automaticamente quais são as etapas de atualização necessárias para um determinado conjunto de dados, você precisa saber como elas contribuem para a complexidade e a duração de uma operação de atualização. Para obter uma referência rápida, confira a tabela a seguir.

| Modo de armazenamento | Atualização de dados | Atualização do OneDrive | Caches de consulta | Atualização de bloco | Visuais de relatório |
| --- | --- | --- | --- | --- | --- |
| Importar | Agendada e sob demanda | Sim, para conjuntos de dados conectados | Se habilitada na capacidade Premium | Automaticamente e sob demanda | Não |
| DirectQuery | Não aplicável | Sim, para conjuntos de dados conectados | Se habilitada na capacidade Premium | Automaticamente e sob demanda | Não |
| LiveConnect | Não aplicável | Sim, para conjuntos de dados conectados | Se habilitada na capacidade Premium | Automaticamente e sob demanda | Sim |
| Push | Não aplicável | Não aplicável | Não é prático | Automaticamente e sob demanda | Não |
| | | | | | |

#### <a name="data-refresh"></a>Atualização de dados

Para usuários do Power BI, atualização de dados normalmente significa importar dados das fontes de dados originais para um conjunto de dados, seja com base em um agendamento de atualização ou sob demanda. Você pode executar várias atualizações de conjuntos de dados diariamente, o que poderá ser necessário se os dados de origem subjacentes forem alterados com frequência. O Power BI limita os conjuntos de dados na capacidade compartilhada a oito atualizações diárias. Se o conjunto de dados residir em uma capacidade Premium, você poderá executar até 48 atualizações por dia nas configurações do conjunto de dados. Para obter mais informações, confira [Configurar a atualização agendada](#configure-scheduled-refresh) mais adiante neste artigo.

Também é importante ressaltar que a limitação da capacidade compartilhada quanto às atualizações diárias se aplica às atualizações agendadas e da API, combinadas. Você também pode disparar uma atualização sob demanda selecionando **Atualizar agora** no menu do conjunto de dados, como ilustrado na captura de tela a seguir. As atualizações sob demanda não estão incluídas na limitação de atualizações. Observe também que os conjuntos de dados em uma capacidade Premium não impõem limitações para atualizações de API. Se tiver interesse em criar sua própria solução de atualização usando a API REST do Power BI, confira [Conjuntos de Dados – Atualizar Conjunto de Dados](/rest/api/power-bi/datasets/refreshdataset).

![Atualizar agora](media/refresh-data/refresh-now.png)

> [!NOTE]
> As atualizações de dados precisam ser concluídas em menos de 2 horas na capacidade compartilhada. Se os conjuntos de dados precisarem de operações de atualização mais longas, considere mover o conjunto de dados para uma capacidade Premium. No Premium, a duração máxima da atualização é de 5 horas.

#### <a name="onedrive-refresh"></a>Atualização do OneDrive

Se você tiver criado seus conjuntos de dados e relatórios com base em um arquivo do Power BI Desktop, pasta de trabalho do Excel ou arquivo de valores separados por vírgula (.csv) no OneDrive ou no SharePoint Online, o Power BI executará outro tipo de atualização, conhecida como atualização do OneDrive. Para obter mais informações, confira [Obter dados de arquivos para o Power BI](service-get-data-from-files.md).

Diferente de uma atualização de conjunto de dados durante a qual o Power BI importa dados de uma fonte de dados para um conjunto de dados, a atualização do OneDrive sincroniza relatórios e conjuntos de dados com seus arquivos de origem. Por padrão, o Power BI verifica de hora em hora se um conjunto de dados conectado a um arquivo no OneDrive ou SharePoint Online requer sincronização.

> [!IMPORTANT]
> Tenha cuidado ao lidar com o gerenciamento de arquivos no OneDrive. Quando você define um arquivo do OneDrive como a fonte de dados, o Power BI referencia a ID do item do arquivo quando ele executa a atualização, que pode causar problemas em alguns cenários. Considere o cenário em que você tem um arquivo mestre _A_ e uma cópia de produção desse arquivo _B_ e você configura a atualização do OneDrive para o arquivo B. Se você _copiar_ o arquivo A no arquivo B, a operação de cópia excluirá o arquivo B antigo e criará um arquivo B com uma ID de item diferente, o que interromperá a atualização do OneDrive. Você deve atualizar e substituir o arquivo B, que mantém a mesma ID de item.

Você pode mover o arquivo para outro local (usando arrastar e soltar, por exemplo) e a atualização continuará funcionando porque o PBI ainda conhece a fileID. No entanto, se você copiar esse arquivo para outro local, uma instância do arquivo e uma fileID serão criadas. Portanto, sua referência do arquivo do Power BI não é mais válida e a atualização falhará.

Para examinar ciclos de sincronização anteriores, verifique a guia do OneDrive no histórico de atualização. A captura de tela a seguir mostra um ciclo de sincronização concluído para um conjunto de dados de exemplo.

![Histórico de atualização](media/refresh-data/refresh-history.png)

Conforme ilustrado na captura de tela acima, o Power BI identificou essa atualização do OneDrive como uma atualização **Agendada**, mas não é possível configurar o intervalo de atualização. Só é possível desativar a atualização do OneDrive nas configurações do conjunto de dados. Desativar a atualização é útil quando você não quer que seus conjuntos de dados e relatórios no Power BI acompanhem as alterações dos arquivos de origem automaticamente.

Observe que a página de configurações do conjunto de dados mostra as seções **Credenciais do OneDrive** e **Atualização do OneDrive** apenas quando o conjunto de dados está conectado a um arquivo no OneDrive ou SharePoint Online, conforme mostrado na captura de tela a seguir. Conjuntos de dados que não estão conectados aos arquivos de origem no OneDrive ou SharePoint Online não mostram essas seções.

![Credenciais e atualização do OneDrive](media/refresh-data/onedrive-credentials-refresh.png)

Se desabilitar a atualização do OneDrive para um conjunto de dados, você ainda poderá sincronizar seu conjunto de dados sob demanda selecionando **Atualizar agora** no menu do conjunto de dados. Como parte da atualização sob demanda, o Power BI verifica se o arquivo de origem no OneDrive ou SharePoint Online é mais recente do que o conjunto de dados no Power BI e, se esse for o caso, sincroniza o conjunto de dados. O **Histórico de atualização** lista essas atividades como atualizações sob demanda na guia **OneDrive**.

Tenha em mente que a atualização do OneDrive não efetua pull de dados das fontes de dados originais. A atualização do OneDrive simplesmente atualiza os recursos no Power BI com os metadados e dados do arquivo .pbix, .xlsx ou .csv, como ilustra o diagrama a seguir. Para garantir que o conjunto de dados tenha os dados mais recentes das fontes de dados, o Power BI também dispara uma atualização de dados como parte de uma atualização sob demanda. Você poderá ver isso no **Histórico de atualização** se alternar para a guia **Agendado**.

![Diagrama de atualização do OneDrive](media/refresh-data/onedrive-refresh-diagram.png)

Se você mantiver a atualização do OneDrive habilitada para um conjunto de dados conectado ao OneDrive ou SharePoint Online e quiser executar a atualização de dados de forma programada, não deixe de configurar o agendamento para que o Power BI execute a atualização de dados após a atualização do OneDrive. Por exemplo, se tivesse criado seu próprio serviço ou processo para atualizar o arquivo de origem no OneDrive ou SharePoint Online toda noite à 1h, você poderia configurar a atualização agendada para as 2h30 para dar ao Power BI tempo suficiente para concluir a atualização do OneDrive antes de iniciar a atualização de dados.

#### <a name="refresh-of-query-caches"></a>Atualização de caches de consulta

Se o conjunto de dados residir em uma capacidade Premium, você poderá melhorar o desempenho dos relatórios e dashboards associados habilitando o cache de consulta, como mostrado na captura de tela a seguir. O cache de consulta instrui a capacidade de Premium a usar o seu serviço de cache local para manter os resultados da consulta, evitando fazer com que fonte de dados subjacente calcule esses resultados. Para obter mais informações, confira [Cache de consulta no Power BI Premium](power-bi-query-caching.md).

![Cache de consulta](media/refresh-data/query-caching.png)

Após uma atualização de dados, no entanto, os resultados da consulta armazenados em cache anteriormente deixam de ser válidos. O Power BI descarta esses resultados armazenados em cache e precisa recriá-los. Por esse motivo, o cache de consulta pode não ser tão vantajoso para relatórios e dashboards associados a conjuntos de dados que você atualiza com muita frequência, como 48 vezes por dia.

#### <a name="tile-refresh"></a>Atualização de bloco

O Power BI mantém um cache para cada visual de bloco em seus dashboards e atualiza proativamente os caches de bloco quando dados são alterados. Em outras palavras, a atualização dos blocos ocorre automaticamente após uma atualização de dados. Isso vale para operações de atualização agendadas e sob demanda. Também é possível forçar uma atualização do bloco selecionando **Mais opções** (...) no canto superior direito de um dashboard e selecionando **Atualizar os blocos do dashboard**.

![Atualizar blocos do dashboard](media/refresh-data/refresh-dashboard-tiles.png)

Como isso acontece automaticamente, você pode considerar a atualização do bloco uma parte intrínseca da atualização de dados. Entre outras coisas, você poderá notar que a duração da atualização aumenta com o número de blocos. A sobrecarga da atualização de bloco pode ser significativa.

Por padrão, o Power BI mantém um cache único para cada bloco, mas se você usar a segurança dinâmica para restringir o acesso a dados com base em funções de usuário, conforme abordado no artigo sobre [RLS (segurança em nível de linha) com o Power BI](service-admin-rls.md), o Power BI deverá manter um cache para cada função e cada bloco. O número de caches de bloco é multiplicado pelo número de funções.

A situação poderá ficar ainda mais complexa se o conjunto de dados usar uma conexão ativa com um modelo de dados do Analysis Services com RLS, como destacado no tutorial [Segurança em nível de linha dinâmica com o modelo de tabela do Analysis Services](desktop-tutorial-row-level-security-onprem-ssas-tabular.md). Nessa situação, o Power BI precisa manter e atualizar um cache para cada bloco e para cada usuário que já visualizou o dashboard. Não é incomum que a parte correspondente à atualização de blocos de uma operação de atualização de dados desse tipo ultrapasse muito o tempo necessário para buscar os dados na fonte. Para obter detalhes sobre a atualização de blocos, confira [Solução de problemas de erros de bloco](refresh-troubleshooting-tile-errors.md).

#### <a name="refresh-of-report-visuals"></a>Atualização de visuais de relatório

Esse processo de atualização é menos importante porque só é relevante para conexões dinâmicas com o Analysis Services. Para essas conexões, o Power BI armazena em cache o último estado dos visuais do relatório para que, quando você exibir o relatório novamente, o Power BI não precise consultar o modelo de tabela do Analysis Services. Quando você interage com o relatório, por exemplo, ao alterar um filtro, o Power BI consulta o modelo de tabela e atualiza os visuais do relatório automaticamente. Se suspeitar de que um relatório está mostrando dados obsoletos, você também poderá selecionar o botão Atualizar do relatório para disparar uma atualização de todos os visuais, como mostrado na captura de tela a seguir.

![Atualizar visuais de relatório](media/refresh-data/refresh-report-visuals.png)

## <a name="review-data-infrastructure-dependencies"></a>Examinar as dependências da infraestrutura de dados

Independentemente de modos de armazenamento, nenhuma atualização de dados poderá ser bem-sucedida a menos que as fontes de dados subjacentes sejam acessíveis. Há três cenários principais de acesso a dados:

- Um conjunto de dados usa fontes de dados que residem localmente
- Um conjunto de dados usa fontes de dados na nuvem
- Um conjunto de dados usa dados de fontes locais e na nuvem

### <a name="connecting-to-on-premises-data-sources"></a>Conexão com fontes de dados locais

Se o conjunto de dados usar uma fonte de dados que o Power BI não pode acessar com uma conexão de rede direta, você precisará configurar uma conexão de gateway para este conjunto de dados antes de habilitar uma agenda de atualização ou executar uma atualização de dados sob demanda. Para obter mais informações sobre gateways de dados e como eles funcionam, confira [O que são gateways de dados locais?](service-gateway-onprem.md)

Você tem as seguintes opções:

- Escolher um gateway de dados corporativos com a definição de fonte de dados necessária
- Implantar um gateway de dados pessoal

> [!NOTE]
> Há uma lista dos tipos de fonte de dados que exigem um gateway de dados no artigo [Gerenciar sua fonte de dados – Importar/Atualização Agendada](service-gateway-enterprise-manage-scheduled-refresh.md).

#### <a name="using-an-enterprise-data-gateway"></a>Usando um gateway de dados corporativos

A Microsoft recomenda usar um gateway de dados corporativos em vez de um gateway pessoal para conectar um conjunto de dados a uma fonte de dados local. Certifique-se de que o gateway esteja configurado corretamente, o que significa que o gateway deve ter as atualizações mais recentes e todas as definições de fonte de dados necessárias. Uma definição de fonte de dados fornece ao Power BI informações de conexão sobre uma determinada fonte, incluindo os pontos de extremidade de conexão, o modo de autenticação e as credenciais. Para obter mais informações sobre como gerenciar fontes de dados em um gateway, confira [Gerenciar sua fonte de dados – Importar/Atualização Agendada](service-gateway-enterprise-manage-scheduled-refresh.md).

Conectar um conjunto de dados a um gateway corporativo é relativamente simples se você é um administrador de gateway. Com permissões de administrador, você pode atualizar imediatamente o gateway e adicionar fontes de dados ausentes, se necessário. De fato, você pode adicionar uma fonte de dados ausente ao seu gateway diretamente na página de configurações do conjunto de dados. Expanda o botão de alternância para exibir as fontes de dados e selecione o link **Adicionar ao gateway**, como mostrado na captura de tela a seguir. Por outro lado, se você não for um administrador de gateway, deverá contatar um administrador de gateway para adicionar a definição de fonte de dados necessária.

> [!NOTE]
> Somente administradores de gateway podem adicionar fontes de dados a um gateway. O administrador do gateway também deve adicionar sua conta de usuário à lista de usuários com permissões para usar a fonte de dados. A página de configurações do conjunto de dados permite que você selecione um gateway empresarial com uma fonte de dados correspondente que você tem permissão para usar.

![Adicionar ao gateway](media/refresh-data/add-to-gateway.png)

Verifique se você mapeou a definição de fonte de dados correta para sua fonte de dados. Como ilustra a captura de tela acima, os administradores de gateway podem criar várias definições em um único gateway se conectando à mesma fonte de dados, cada um com credenciais diferentes. No exemplo mostrado, um proprietário de conjunto de dados do departamento de vendas escolheria a definição de fonte de dados de vendas de AdventureWorksProducts, enquanto um proprietário de conjunto de dados no departamento de suporte mapearia o conjunto de dados para definição de fonte de dados de suporte do AdventureWorksProducts. Se os nomes de definição de fonte de dados não forem intuitivos, entre em contato com seu administrador do gateway para esclarecer qual definição escolher.

> [!NOTE]
> Um conjunto de dados só pode usar uma conexão de gateway. Em outras palavras, não é possível acessar fontes de dados locais usando várias conexões de gateway. Dessa forma, você precisa adicionar todas as definições de fonte de dados necessárias ao mesmo gateway.

#### <a name="deploying-a-personal-data-gateway"></a>Implantando um gateway de dados pessoal

Se não tiver acesso a um gateway de dados corporativos e for a única pessoa que gerencia conjuntos de dados, de forma que não precisa compartilhar as fontes de dados com outras pessoas, você poderá implantar um gateway de dados no modo pessoal. Na seção **Conexão de gateway**, em **Você não tem um gateway pessoal instalado**, selecione **Instalar agora**. O gateway de dados pessoal tem várias limitações, conforme documentado em [Gateway de dados local (modo pessoal)](service-gateway-personal-mode.md).

Diferente de um gateway de dados corporativos, você não precisa adicionar definições de fonte de dados para um gateway pessoal. Em vez disso, você gerencia a configuração de fonte de dados usando a seção **Credenciais da fonte de dados** nas configurações do conjunto de dados, como mostrado na captura de tela a seguir.

![Configurar credenciais da fonte de dados para o gateway](media/refresh-data/configure-data-source-credentials-gateway.png)

> [!NOTE]
> O gateway de dados pessoal não dá suporte a conjuntos de dados no modo DirectQuery/LiveConnect. A página de configurações do conjunto de dados pode solicitar que você o instale, mas se tiver apenas um gateway pessoal, você não poderá configurar uma conexão de gateway. Certifique-se de que você tem um gateway de dados corporativos para dar suporte a esses tipos de conjuntos de dados.

### <a name="accessing-cloud-data-sources"></a>Acessando fontes de dados de nuvem

Conjuntos de dados que usam fontes de dados de nuvem, como o Azure SQL DB, não exigem um gateway de dados quando o Power BI pode estabelecer uma conexão de rede direta com a fonte. Da mesma forma, você pode gerenciar a configuração dessas fontes de dados usando a seção **Credenciais da fonte de dados** nas configurações do conjunto de dados. Como mostrado na captura de tela a seguir, você não precisa configurar uma conexão de gateway.

![Configurar credenciais da fonte de dados sem um gateway](media/refresh-data/configure-data-source-credentials.png)

### <a name="accessing-on-premises-and-cloud-sources-in-the-same-source-query"></a>Acessando fontes locais e na nuvem na mesma consulta de origem

Um conjunto de dados pode obter dados de várias fontes, as quais podem residir localmente ou na nuvem. No entanto, conforme mencionado anteriormente, um conjunto de dados pode usar apenas uma conexão de gateway. Embora as fontes de dados de nuvem não exijam necessariamente um gateway, o gateway é necessário se o conjunto de dados se conecta a fontes locais e na nuvem em uma única consulta de mashup. Nesse cenário, o Power BI também precisa usar um gateway para as fontes de dados de nuvem. O diagrama a seguir ilustra como um conjunto de dados desse tipo acessa suas fontes de dados.

![Fontes de dados locais e na nuvem](media/refresh-data/cloud-on-premises-data-sources-diagram.png)

> [!NOTE]
> Se um conjunto de dados usar consultas de mashup separadas para se conectar a fontes locais e de nuvem, o Power BI usará uma conexão de gateway para acessar as fontes locais e uma conexão de rede direta para as fontes de nuvem. Se uma consulta de mashup mesclar ou acrescentar dados de fontes locais e de nuvem, o Power BI passará a usar a conexão de gateway mesmo para as fontes de nuvem.

Conjuntos de dados do Power BI se baseiam no Power Query para acessar e recuperar dados de origem. A lista de mashup a seguir mostra um exemplo básico de consulta que mescla dados de uma fonte local e uma fonte de nuvem.

```
Let

    OnPremSource = Sql.Database("on-premises-db", "AdventureWorks"),

    CloudSource = Sql.Databases("cloudsql.database.windows.net", "AdventureWorks"),

    TableData1 = OnPremSource{[Schema="Sales",Item="Customer"]}[Data],

    TableData2 = CloudSource {[Schema="Sales",Item="Customer"]}[Data],

    MergedData = Table.NestedJoin(TableData1, {"BusinessEntityID"}, TableData2, {"BusinessEntityID"}, "MergedData", JoinKind.Inner)

in

    MergedData
```

Há duas opções para configurar um gateway de dados de modo a dar suporte à mesclagem ou ao acréscimo de dados de fontes locais e de nuvem:

- Adicionar uma definição de fonte de dados para a fonte de nuvem ao gateway de dados, além das fontes de dados locais.
- Marcar a caixa de seleção **Permitir que as fontes de dados de nuvem do usuário sejam atualizadas por meio deste cluster de gateway**.

![Atualizar usando o cluster de gateway](media/refresh-data/refresh-gateway-cluster.png)

Se você habilitar a caixa de seleção **Permitir que as fontes de dados de nuvem do usuário sejam atualizadas por meio deste cluster de gateway na configuração do gateway**, como mostrado na captura de tela acima, o Power BI poderá usar a configuração que o usuário definiu para a fonte de nuvem em **Credenciais da fonte de dados** nas configurações do conjunto de dados. Isso pode ajudar a reduzir a sobrecarga da configuração do gateway. Por outro lado, se quiser ter mais controle sobre as conexões que o gateway estabelece, você não deverá marcar esta caixa de seleção. Nesse caso, você precisa adicionar uma definição de fonte de dados explícita para cada fonte de nuvem a que deseja dar suporte ao seu gateway. Também é possível marcar a caixa de seleção e adicionar definições explícitas de fonte de dados para suas fontes de nuvem a um gateway. Nesse caso, o gateway usa as definições de fonte de dados para todas as fontes correspondentes.

### <a name="configuring-query-parameters"></a>Configurando parâmetros de consulta

As consultas de mashup, ou M, que você cria usando o Power Query podem variar em complexidade, indo de etapas simples a constructos parametrizados. A lista a seguir mostra um pequeno exemplo de consulta de mashup que usa dois parâmetros chamados _SchemaName_ e _TableName_ para acessar uma determinada tabela em um banco de dados AdventureWorks.

```
let

    Source = Sql.Database("SqlServer01", "AdventureWorks"),

    TableData = Source{[Schema=SchemaName,Item=TableName]}[Data]

in

    TableData
```

> [!NOTE]
> Parâmetros de consulta têm suporte apenas para conjuntos de dados no Modo de importação. O modo DirectQuery/LiveConnect não dá suporte a definições de parâmetro de consulta.

Para garantir que um conjunto de dados com parâmetros acesse os dados corretos, você precisa definir os parâmetros da consulta de mashup nas configurações do conjunto de dados. Também é possível atualizar os parâmetros de maneira programática usando a [API REST do Power BI](/rest/api/power-bi/datasets/updateparametersingroup). A captura de tela a seguir mostra a interface do usuário para configurar os parâmetros de consulta para um conjunto de dados que usa a consulta de mashup acima.

![Configurar parâmetros de consulta](media/refresh-data/configure-query-parameters.png)

> [!NOTE]
> Atualmente, o Power BI não tem suporte para definições de fonte de dados com parâmetros, também conhecidas como fontes de dados dinâmicas. Por exemplo, não é possível parametrizar a função de acesso a dados Sql.Database("SqlServer01", "AdventureWorks"). Se o conjunto de dados depender de fontes de dados dinâmicas, o Power BI informará que detectou fontes de dados desconhecidas ou sem suporte. Você precisará substituir os parâmetros em suas funções de acesso a dados por valores estáticos se quiser que o Power BI seja capaz de identificar e se conectar às fontes de dados. Para obter mais informações, confira [Solucionando problemas de fonte de dados sem suporte para atualização](service-admin-troubleshoot-unsupported-data-source-for-refresh.md).

## <a name="configure-scheduled-refresh"></a>Configurar a atualização agendada

Estabelecer a conectividade entre o Power BI e suas fontes de dados é, de longe, a tarefa mais desafiadora da configuração de uma atualização de dados. As etapas restantes são relativamente simples e incluem configurar o agendamento de atualização e habilitar notificações de falha de atualização. Para obter instruções passo a passo, confira o guia de instruções [Configurando a atualização agendada](refresh-scheduled-refresh.md).

### <a name="setting-a-refresh-schedule"></a>Configurando um agendamento de atualização

Na seção **Atualização agendada**, você define a frequência e os slots de tempo para atualizar o conjunto de dados. Conforme mencionado anteriormente, você poderá configurar até oito slots de tempo diários se estiver na capacidade compartilhada ou 48 slots no Power BI Premium. A captura de tela a seguir mostra um agendamento de atualização com intervalo de doze horas.

![Configurar a atualização agendada](media/refresh-data/configure-scheduled-refresh.png)

Após a configuração de um agendamento de atualização, a página de configurações do conjunto de dados informa o horário da próxima atualização, como na captura de tela acima. Se você quiser atualizar os dados mais cedo, por exemplo, para testar sua configuração de gateway e fonte de dados, execute uma atualização sob demanda usando a opção **Atualizar agora** no menu de conjunto de dados no painel de navegação. As atualizações sob demanda não afetam o próximo horário da atualização agendada.

Observe também que o horário de atualização configurado talvez não seja o horário exato em que o Power BI iniciará o próximo processo agendado. O Power BI inicia as atualizações agendadas com base no melhor esforço. O objetivo é iniciar a atualização dentro de 15 minutos do slot de horário agendado, mas um atraso de até uma hora poderá ocorrer se o serviço não puder alocar os recursos necessários mais cedo.

> [!NOTE]
> O Power BI desativa seu agendamento de atualização após quatro falhas consecutivas ou quando o serviço detecta um erro irrecuperável que requer uma atualização de configuração, como credenciais inválidas ou vencidas. Não é possível alterar o limite de falhas consecutivas.

### <a name="getting-refresh-failure-notifications"></a>Obtendo notificações de falha de atualização

Por padrão, o Power BI envia notificações de falha de atualização por email para o proprietário do conjunto de dados para que ele possa agir de maneira ágil no caso de problemas de atualização. O Power BI também lhe envia uma notificação quando o serviço desabilita seu agendamento devido a falhas consecutivas. A Microsoft recomenda que você deixe a caixa de seleção **Enviar-me emails de notificação de falha na atualização** habilitada.

Também é recomendável especificar destinatários adicionais usando a caixa de texto **Enviar um email a esses usuários quando a atualização falhar.** Os destinatários especificados recebem notificações de falha de atualização além do proprietário do conjunto de dados. Pode ser um colega que cuida de seus conjuntos de dados enquanto você está em férias. Também pode ser o alias de email de sua equipe de suporte que cuida de problemas de atualização para seu departamento ou sua organização. O envio de notificações de falha de atualização para outras pessoas além do proprietário do conjunto de dados é útil para que os problemas sejam percebidos e resolvidos em tempo hábil.

Observe que o Power BI não apenas envia notificações de falhas de atualização, mas também quando o serviço pausa uma atualização agendada devido à inatividade. Após dois meses, se nenhum usuário tiver visitado nenhum dashboard ou relatório criado com base no conjunto de dados, o Power BI considerará o conjunto de dados inativo. Nesta situação, o Power BI envia uma mensagem de email ao proprietário do conjunto de dados indicando que o serviço de agendar atualização do conjunto de dados está em pausa. Veja na captura de tela a seguir um exemplo de notificação.

![Email de atualização em pausa](media/refresh-data/email-paused-refresh.png)

Para retomar a atualização agendada, visite um relatório ou dashboard criado usando o conjunto de dados ou atualize-o manualmente usando a opção **Atualizar agora**.

### <a name="checking-refresh-status-and-history"></a>Verificando o status e o histórico de atualização

Além das notificações de falha, é uma boa ideia verificar seus conjuntos de dados periodicamente para ver se há erros de atualização. Uma maneira rápida é exibir a lista de conjuntos de dados em um workspace. Conjuntos de dados com erros mostram um pequeno ícone de aviso. Selecione o ícone de aviso para obter informações adicionais, como na seguinte captura de tela. Para obter mais informações sobre como solucionar erros de atualização específicos, confira [Solucionar problemas em cenários de atualização](refresh-troubleshooting-refresh-scenarios.md).

![Aviso de status de atualização](media/refresh-data/refresh-status-warning.png)

O ícone de aviso ajuda a indicar problemas atuais no conjunto de dados, mas também é uma boa ideia verificar ocasionalmente o histórico de atualização. Como o nome indica, o histórico de atualização permite que você examine o status de êxito ou falha de ciclos de sincronização anteriores. Por exemplo, um administrador de gateway pode ter atualizado um conjunto expirado de credenciais de banco de dados. Como você pode ver na captura de tela a seguir, o histórico de atualização mostra quando uma atualização afetada começou a funcionar novamente.

![Mensagens do histórico de atualização](media/refresh-data/refresh-history-messages.png)

> [!NOTE]
> Há um link para exibir o histórico de atualização nas configurações do conjunto de dados. Também é possível recuperar um histórico de atualização de maneira programática usando a [API REST do Power BI](/rest/api/power-bi/datasets/getrefreshhistoryingroup). Usando uma solução personalizada, você pode monitorar o histórico de atualização de vários conjuntos de dados de forma centralizada.

## <a name="automatic-page-refresh"></a>Atualização automática de página

A atualização automática de página funciona em um nível de página de relatório e permite que os autores de relatório definam um intervalo de atualização para visuais em uma página que está ativa apenas quando a página é consumida. A atualização automática de página está disponível apenas para fontes de dados DirectQuery. O intervalo mínimo de atualização depende do tipo de espaço de trabalho em que o relatório está publicado e das configurações de capacidade do administrador para espaços de trabalho Premium e [espaços de trabalho inseridos](developer/embedded/embedding.md).

Saiba mais no artigo sobre [atualização de página automática](desktop-automatic-page-refresh.md).

## <a name="best-practices"></a>Práticas recomendadas

Verificar regularmente o histórico de atualização de seus conjuntos de dados é uma das melhores práticas mais importantes que você pode adotar para garantir que os relatórios e dashboards usem dados atuais. Se descobrir problemas, resolva-os imediatamente e faça o acompanhamento com os proprietários da fonte de dados e os administradores do gateway, se necessário.

Além disso, considere as seguintes recomendações para estabelecer e manter processos de atualização de dados confiáveis para seus conjuntos de dados:

- Agende suas atualizações para horários menos ocupados, especialmente se os conjuntos de dados estiverem no Power BI Premium. Se distribuir os ciclos de atualização de seus conjuntos de dados em uma janela de tempo mais ampla, você poderá ajudar a evitar picos que, de outra forma, poderiam sobrecarregar os recursos disponíveis. Atrasos no início de um ciclo de atualização são um indicador de sobrecarga de recursos. Se uma capacidade Premium for esgotada completamente, o Power BI poderá até mesmo ignorar um ciclo de atualização.
- Lembre-se dos limites de atualização. Se os dados de origem forem alterados com frequência ou o volume de dados for significativo, considere usar o modo DirectQuery/LiveConnect em vez do Modo de importação se o aumento da carga na fonte e o impacto sobre o desempenho da consulta forem aceitáveis. Evite atualizar constantemente um conjunto de dados no Modo de importação. No entanto, o modo DirectQuery/LiveConnect tem várias limitações, como um limite de um milhão de linhas para retornar dados e um limite de tempo de resposta de 225 segundos para executar consultas, conforme documentado em [Usar o DirectQuery no Power BI Desktop](desktop-use-directquery.md). Essas limitações podem exigir que você use o Modo de importação de qualquer maneira. Para volumes de dados muito grandes, considere usar [agregações no Power BI](desktop-aggregations.md).
- Verifique se o seu tempo de atualização do conjunto de dados não ultrapassa a duração máxima de atualização. Use o Power BI Desktop para verificar a duração da atualização. Se demorar mais de 2 horas, considere mover o conjunto de dados para o Power BI Premium. Talvez o conjunto de dados não seja atualizável na capacidade compartilhada. Considere também usar a [atualização incremental no Power BI Premium](service-premium-incremental-refresh.md) para conjuntos de dados com mais de 1 GB ou que demoram várias horas para serem atualizados.
- Otimize seus conjuntos de dados de modo a incluir somente as tabelas e colunas que seus relatórios e dashboards usam. Otimize as consultas de mashup e, se possível, evite definições de fontes de dados dinâmicas e cálculos de DAX caros. Especificamente, evite funções DAX que testam todas as linhas de uma tabela devido ao alto consumo de memória e à sobrecarga de processamento.
- Aplique as mesmas configurações de privacidade do Power BI Desktop para garantir que o Power BI possa gerar consultas de fonte eficientes. Tenha em mente que o Power BI Desktop não publica configurações de privacidade. Você precisa reaplicar manualmente as configurações nas definições da fonte de dados após publicar seu conjunto de dados.
- Limite o número de visuais em seus dashboards, especialmente se você usa [RLS (segurança em nível de linha)](service-admin-rls.md). Conforme explicado anteriormente neste artigo, um número excessivo de blocos de dashboard pode aumentar significativamente a duração da atualização.
- Use uma implantação de gateway de dados corporativos confiável para conectar seus conjuntos de dados a fontes de dados locais. Se observar falhas de atualização relacionadas ao gateway, como gateway não disponível ou sobrecarregado, confira os administradores do gateway para adicionar mais gateways a um cluster existente ou implantar um novo cluster (escalar verticalmente versus expandir).
- Use gateways de dados separados para os conjuntos de dados de importação e os de DirectQuery/LiveConnect, para que importações de dados durante a atualização agendada não afetem o desempenho de relatórios e dashboards baseados em conjuntos de dados de DirectQuery/LiveConnect, que consultam as fontes de dados a cada interação do usuário.
- Certifique-se de que o Power BI possa enviar notificações de falha de atualização para sua caixa de correio. Filtros de spam podem bloquear as mensagens de email ou movê-las para uma pasta separada em que você pode não notá-las imediatamente.


## <a name="next-steps"></a>Próximas etapas

[Configuração de atualização agendada](refresh-scheduled-refresh.md)  
[Ferramentas para solucionar problemas de atualização](service-gateway-onprem-tshoot.md)  
[Solucionar problemas de atualização](refresh-troubleshooting-refresh-scenarios.md)  

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
