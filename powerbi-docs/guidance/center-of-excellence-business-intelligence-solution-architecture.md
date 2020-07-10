---
title: Arquitetura da solução de BI no Centro de Excelência
description: Saiba o que deve ser considerado ao projetar e desenvolver uma plataforma de BI robusta.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 07/02/2020
ms.author: v-pemyer
ms.openlocfilehash: 81dda3c2bc3558ba68a16ee3f3070e748f76f15b
ms.sourcegitcommit: 561f6de3e4621d9d439dd54fab458ddca78ace2c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/03/2020
ms.locfileid: "85939883"
---
# <a name="bi-solution-architecture-in-the-center-of-excellence"></a>Arquitetura da solução de BI no Centro de Excelência

Este artigo destina-se a profissionais e gerentes de TI. Você aprenderá sobre a arquitetura da solução de BI no COE e as diferentes tecnologias utilizadas. As tecnologias incluem Azure, Power BI e Excel. Juntos, podem ser utilizadas para fornecer uma plataforma de BI de nuvem orientada por dados e escalonável.

Criar uma plataforma de BI robusta é, de certa forma, como criar uma ponte; uma ponte que conecta dados de origem transformados e aprimorados a consumidores de dados. O design dessa estrutura complexa exige uma mentalidade de engenharia, embora possa ser uma das arquiteturas de TI mais criativas e recompensadoras que você pode criar.

A plataforma deve dar suporte a demandas específicas. Especificamente, deve ser dimensionada e executada para atender às expectativas dos serviços de negócios e dos consumidores de dados. Ao mesmo tempo, deve ser segura desde o início. Ela deve ser suficientemente resiliente para se adaptar a alterações, pois com certeza, com o tempo, novos dados e áreas de assunto deverão ser colocados online.

:::image type="content" source="media/center-of-excellence-business-intelligence-solution-architecture/azure-business-intelligence-platform.png" alt-text="Uma imagem mostra um diagrama de arquitetura de plataforma de BI, de fontes de dados a ingestão de dados, Big Data, repositório, data warehouse, relatórios e machine learning.":::

## <a name="frameworks"></a>Estruturas

Na Microsoft, desde o início, adotamos uma abordagem semelhante a sistemas, investindo em desenvolvimento de estrutura. As estruturas de processos técnicos e comerciais aumentam a reutilização do design e da lógica e fornecem um resultado consistente. Elas também oferecem flexibilidade na arquitetura, aproveitando muitas tecnologias e simplificam e reduzem a sobrecarga de engenharia por meio de processos repetíveis.

Aprendemos que as estruturas bem projetadas aumentam a visibilidade de linhagem de dados, análise de impacto, manutenção da lógica de negócios, gerenciamento da taxonomia e simplificação da governança. Além disso, o desenvolvimento tornou-se mais rápido e a colaboração em grandes equipes ficou mais responsiva e eficaz.

Descreveremos várias de nossas estruturas neste artigo.

## <a name="data-models"></a>Modelo de dados

Os modelos de dados fornecem controle sobre como os dados são estruturados e acessados. Para os serviços de negócios e consumidores de dados, os modelos de dados são sua interface com a plataforma de BI.

Uma plataforma de BI pode fornecer três tipos diferentes de modelos:

- Modelos corporativos
- Modelos de BI
- Modelos de ML (Machine Learning)

### <a name="enterprise-models"></a>Modelos corporativos

Os **modelos corporativos** são criados e mantidos pelos arquitetos de TI. Às vezes, são chamados de modelos dimensionais ou de datamarts. Normalmente, os dados são armazenados em formato relacional como tabelas de dados e dimensões. Essas tabelas armazenam dados limpos e aprimorados consolidados de muitos sistemas e representam uma fonte autoritativa para relatórios e análises.

Os modelos corporativos fornecem uma fonte de dados consistente e única para relatórios e BI. Eles são criados uma vez e compartilhados como um padrão corporativo. As políticas de governança garantem que os dados sejam seguros, portanto, o acesso a conjuntos de dados confidenciais, como informações do cliente ou finanças, é restrito de acordo com as necessidades. Eles adotam as convenções de nomenclatura, garantindo a consistência, estabelecendo, assim, a credibilidade e a qualidade dos dados.

Em uma plataforma de BI de nuvem, os modelos corporativos podem ser implantados em um [pool de SQL do Azure Synapse](/azure/synapse-analytics/sql-data-warehouse/sql-data-warehouse-overview-what-is#synapse-sql-pool-in-azure-synapse). O pool de SQL do Synapse então se torna a única versão da verdade que a organização pode contar para obter informações rápidas e robustas.

### <a name="bi-models"></a>Modelos de BI

Os **modelos de BI** representam uma camada semântica sobre modelos corporativos. Eles são criados e mantidos por desenvolvedores de BI e usuários corporativos. Os desenvolvedores de BI criam modelos de BI centrais que adquirem dados de modelos corporativos. Os usuários empresariais podem criar modelos independentes de menor escala ou estender os modelos de BI centrais com fontes de departamento ou externas. Os modelos de BI geralmente se concentram em uma única área de assunto e geralmente são amplamente compartilhados.

Os recursos de negócios são habilitados não apenas por dados, mas por modelos de BI que descrevem conceitos, relações, regras e padrões. Dessa forma, eles representam estruturas intuitivas e fáceis de entender que definem as relações de dados e encapsulam regras de negócio como cálculos. Eles também podem impor permissões de dados refinadas, garantindo que as pessoas certas tenham acesso aos dados corretos. Mais importante, eles aceleram o desempenho da consulta, fornecendo análises interativas extremamente responsivas, mesmo em terabytes de dados. Como os modelos corporativos, os modelos de BI adotam convenções de nomenclatura garantindo a consistência.

Em uma plataforma de BI de nuvem, os desenvolvedores de BI podem implantar modelos de BI para [capacidades do Azure Analysis Services](/azure/analysis-services/) ou do [Power BI Premium](../admin/service-premium-what-is.md#dedicated-capacities). É recomendável implantar para Power BI quando ele é usado como sua camada de relatório e análise. Esses produtos dão suporte a modos de armazenamento diferentes, permitindo que tabelas de modelo de dados armazenem em cache seus dados ou usem [DirectQuery](directquery-model-guidance.md), que é uma tecnologia que passa consultas para a fonte de dados subjacente. O DirectQuery é um modo de armazenamento ideal quando as tabelas de modelo representam grandes volumes de dados ou há a necessidade de fornecer resultados quase em tempo real. Os dois modos de armazenamento podem ser combinados: Os [modelos compostos](composite-model-guidance.md) combinam tabelas que usam modos de armazenamento diferentes em um único modelo.

Para modelos com consulta intensa, o [Azure Load Balancer](/azure/load-balancer/load-balancer-overview) pode ser usado para distribuir uniformemente a carga de consulta entre as réplicas de modelo. Ele também permite que você dimensione seus aplicativos e crie modelos de BI altamente disponíveis.

<!-- For more information on BI models, see [BI modeling and processing in the COE](https://TODO/).-->

### <a name="machine-learning-models"></a>Modelos de Machine Learning

Os [**modelos de ML (Machine Learning)** ](/windows/ai/windows-ml/what-is-a-machine-learning-model) são criados e mantidos por cientistas de dados. Eles são basicamente desenvolvidos com base em fontes brutas no data Lake.

Modelos de ML treinados podem revelar padrões em seus dados. Em muitas circunstâncias, esses padrões podem ser usados para fazer previsões que podem ser usadas para aprimorar os dados. Por exemplo, o comportamento de compra pode ser usado para prever a rotatividade de clientes ou os clientes de segmento. Os resultados da previsão podem ser adicionados aos modelos corporativos para permitir a análise por segmento de cliente.

Em uma plataforma de BI de nuvem, você pode usar o [Azure Machine Learning](/azure/machine-learning/overview-what-is-azure-ml) para treinar, implantar, automatizar, gerenciar e rastrear modelos de ML.

## <a name="data-warehouse"></a>Data warehouse

No cerne de uma plataforma de BI está o data warehouse, que hospeda seus modelos corporativos. É uma fonte de dados aprovados, como um sistema de registro e como um hub, que atende a modelos corporativos para relatórios, BI e ciência de dados.

Muitos serviços corporativos, incluindo aplicativos LOB (linha de negócios), podem contar com o data warehouse como uma fonte autoritativa e controlada de conhecimento empresarial.

Na Microsoft, nosso data warehouse é hospedado no ADLS Gen2 ([Azure Data Lake Storage Gen2](/azure/storage/blobs/data-lake-storage-introduction)) e no Azure Synapse Analytics.

:::image type="content" source="media/center-of-excellence-business-intelligence-solution-architecture/azure-data-warehouse.png" alt-text="Uma imagem mostra o Azure Synapse Analytics conectando-se ao Azure Data Lake Storage Gen2.":::

- O **ADLS Gen2** torna o Armazenamento do Azure a fundação para a criação de data lakes corporativos no Azure. Ele foi projetado para atender a vários petabytes de informações e, ao mesmo tempo, manter centenas de gigabits de taxa de transferência. Ele oferece, ainda, capacidade e transações de armazenamento de baixo custo. E, mais importante, tem suporte para acesso compatível com Hadoop, que permite gerenciar e acessar dados como faria com um HDFS (Sistema de Arquivos Distribuído). Na verdade, o [Azure HDInsight](/azure/hdinsight/), o [Azure Databricks](/azure/azure-databricks/what-is-azure-databricks) e o Azure Synapse Analytics podem acessar os dados armazenados no ADLS Gen2. Portanto, em uma plataforma do BI, é uma boa escolha armazenar dados de origem brutos, semiprocessados ou dados preparados e dados prontos para produção. Nós o usamos para armazenar todos os nossos dados corporativos.
- O **Azure Synapse Analytics** é um serviço de análise que reúne data warehouse corporativo e análise de Big Data. Ele oferece a liberdade para consultar dados da forma que você quiser, usando recursos sob demanda sem servidor ou provisionados em escala. O SQL do Synapse, um componente do Azure Synapse Analytics, dá suporte à análise completa baseada em T-SQL, portanto, é ideal para hospedar modelos corporativos que compreendem suas tabelas de dimensões e de dados. As tabelas podem ser carregadas com eficiência do ADLS Gen2 usando consultas [T-SQL do Polybase](/sql/relational-databases/polybase/polybase-guide) simples. Em seguida, você tem o poder de [MPP](/azure/synapse-analytics/sql-data-warehouse/massively-parallel-processing-mpp-architecture#synapse-sql-mpp-architecture-components) para executar a análise de alto desempenho.

### <a name="business-rules-engine-framework"></a>Estrutura do Mecanismo de Regras de Negócio

Desenvolvemos uma estrutura de **BRE (Mecanismo de Regras de Negócio)** para catalogar qualquer lógica de negócios que possa ser implementada na camada de data warehouse. Um BRE pode significar muitas coisas, porém, no contexto de um data warehouse, é útil para criar colunas calculadas em tabelas relacionais. Essas colunas calculadas geralmente são representadas como cálculos ou expressões matemáticas usando instruções condicionais.

A intenção é dividir a lógica de negócios do código de BI central. Tradicionalmente, as regras de negócios são embutidas em código em procedimentos armazenados do SQL, assim, quando as necessidades comerciais mudam, é necessário muito esforço de manutenção. Em um BRE, as regras de negócio são definidas uma vez e usadas várias vezes quando aplicadas a diferentes entidades de data warehouse. Se a lógica de cálculo precisar ser alterada, ela só precisará ser atualizada em um local, e não em vários procedimentos armazenados. Também há um benefício adicional: uma estrutura BRE orienta a transparência e a visibilidade da lógica de negócios implementada, que pode ser exposta por meio de um conjunto de relatórios que criam documentação de autoatualização.

## <a name="data-sources"></a>Fontes de dados

Um data warehouse pode consolidar dados de praticamente qualquer fonte de dados. Em geral, ele é criado em fontes de dados LOB, que costumam ser bancos de dados relacionais que armazenam dados específicos do assunto para vendas, marketing, finanças etc. Esses bancos de dados podem ser hospedados na nuvem ou residir localmente. Outras fontes de dados podem ser baseadas em arquivo, especialmente logs da Web ou dados de IOT adquiridos de dispositivos. Além do mais, os dados podem ser originados de fornecedores de SaaS (software como serviço).

Na Microsoft, alguns sistemas internos geram dados operacionais diretos para ADLS Gen2 usando formatos de arquivo brutos. Além do nosso data lake, outros sistemas de origem compreendem aplicativos LOB relacionais, pastas de trabalho do Excel, outras fontes baseadas em arquivo e o MDM (Gerenciamento de Dados Mestre) e repositórios de dados personalizados. Os repositórios de MDM nos permitem gerenciar nossos dados mestres para garantir versões autoritativas, padronizadas e validadas dos dados.

## <a name="data-ingestion"></a>Ingestão de dados

Periodicamente, e de acordo com o ritmo da empresa, os dados são ingeridos dos sistemas de origem e carregados no data warehouse. Pode ser uma vez por dia ou a intervalos mais frequentes. A ingestão de dados está preocupada com a extração, a transformação e o carregamento de dados. Ou talvez ao contrário: extração, carregamento e então transformação de dados. A diferença está no local em que a transformação acontece. As transformações são aplicadas para limpar, adequar, integrar e padronizar dados. Para obter mais informações, confira [ETL (extração, transformação e carregamento)](/azure/architecture/data-guide/relational-data/etl).

Por fim, a meta é carregar os dados certos em seu modelo corporativo da maneira mais rápida e eficiente possível.

Na Microsoft, usamos o ADF ([Azure Data Factory](/azure/data-factory/introduction)). Os serviços são usados para agendar e orquestrar validações de dados, transformações e carregamentos em massa de sistemas de origem externos em nosso data Lake. Eles são gerenciados por estruturas personalizadas para processar dados em paralelo e em escala. Além disso, o registro em log abrangente é feito para dar suporte à solução de problemas e ao monitoramento de desempenho e para disparar notificações de alerta quando condições específicas são atendidas.

Enquanto isso, o [Azure Databricks](/azure/azure-databricks/what-is-azure-databricks), uma plataforma de análise baseadas em Apache Spark otimizadas para a plataforma de serviços de nuvem do Azure, executa transformações especificamente para a ciência de dados. Também cria e executa modelos de ML usando Python notebooks. As pontuações desses modelos de ML são carregadas no data warehouse para integrar previsões com aplicativos e relatórios corporativos. Como o Azure Databricks acessa os arquivos do data Lake diretamente, ele elimina ou minimiza a necessidade de copiar ou adquirir dados.

:::image type="content" source="media/center-of-excellence-business-intelligence-solution-architecture/azure-data-ingestion.png" alt-text="Uma imagem mostra o Azure Data Factory adquirindo dados e orquestrando pipelines de dados com o Azure Databricks sobre o Azure Data Lake Storage Gen2.":::

### <a name="ingestion-framework"></a>Estrutura de ingestão

Desenvolvemos uma **estrutura de ingestão** como um conjunto de tabelas e procedimentos de configuração. Ela dá suporte a uma abordagem orientada por dados para a aquisição de grandes volumes de dados em alta velocidade e com o mínimo de código. Em suma, essa estrutura simplifica o processo de aquisição de dados para carregar o data warehouse.

A estrutura depende de tabelas de configuração que armazenam informações relacionadas à fonte de dados e ao destino de dados, como o tipo de fonte, o servidor, o banco de dados, o esquema e os detalhes relacionados à tabela. Essa abordagem de design significa que não precisamos desenvolver pipelines do AAF específicos nem pacotes do [SSIS (SQL Server Integration Services)](/sql/integration-services/sql-server-integration-services). Em vez disso, os procedimentos são escritos na linguagem escolhida para criar pipelines do ADF que são gerados e executados dinamicamente no tempo de execução. Portanto, a aquisição de dados se torna um exercício de configuração facilmente operacionalizado. Tradicionalmente, seriam necessários amplos recursos de desenvolvimento para criar pacotes ADF ou SSIS embutidos em código.

A estrutura de ingestão foi projetada para simplificar o processo de manipulação de alterações de esquema de origem upstream também. É fácil atualizar os dados de configuração, seja manual ou automaticamente, quando as alterações de esquema são detectadas para adquirir atributos recém-adicionados no sistema de origem.

### <a name="orchestration-framework"></a>Estrutura de orquestração

Desenvolvemos uma **estrutura de orquestração** para colocar em operação e orquestrar nossos pipelines de dados. Ela usa um design controlado por dados que depende de um conjunto de tabelas de configuração. Essas tabelas armazenam metadados que descrevem dependências de pipeline e como mapear dados de origem para estruturas de dados de destino. O investimento no desenvolvimento dessa estrutura adaptável já se pagou. Não há mais necessidade de embutir em código cada movimentação de dados.

## <a name="data-storage"></a>Armazenamento de dados

Um data lake pode armazenar grandes volumes de dados brutos para uso posterior, juntamente com transformações de dados de preparo.

Na Microsoft, usamos o ADLS Gen2 como a única fonte de verdade. Ele armazena dados brutos juntamente a dados preparados e dados prontos para produção. Ele fornece uma solução de data lake altamente escalonável e econômica para a análise de Big Data. Combinando o poder de um sistema de arquivos de alto desempenho com grande escala, ele é otimizado para cargas de trabalho de análise de dados, acelerando o tempo para obter insight.

O ADLS Gen2 fornece o melhor de dois mundos: é o armazenamento de BLOBs e um namespace de sistema de arquivos de alto desempenho, que configuramos com permissões de acesso refinadas.

Os dados refinados são então armazenados em um banco de dados relacional para fornecer um armazenamento de dados altamente escalonável e de alto desempenho para modelos corporativos, com segurança, governança e capacidade de gerenciamento. Os datamarts específicos do assunto são armazenados no Azure Synapse Analytics, sendo carregados pelo Azure Databricks ou por consultas T-SQL do Polybase.

## <a name="data-consumption"></a>Consumo de dados

Na camada de relatórios, os serviços de negócios consomem dados corporativos do data warehouse. Eles também acessam dados diretamente no data lake para tarefas de análise ad hoc ou de ciência de dados.

As permissões refinadas são impostas em todas as camadas: no data lake, nos modelos corporativos e nos modelos de BI. As permissões garantem que os consumidores de dados só possam ver os dados aos quais têm direitos de acesso.

Na Microsoft, usamos relatórios e dashboards do Power BI e [relatórios paginados do Power BI](../paginated-reports/paginated-reports-report-builder-power-bi.md). Alguns relatórios e uma análise ad hoc são feitos no Excel, especialmente para relatórios financeiros.

Publicamos dicionários de dados, que fornecem informações de referência sobre nossos modelos de dados. Eles são disponibilizados para nossos usuários para que eles possam descobrir informações sobre nossa plataforma de BI. Os dicionários documentam os designs do modelo, fornecendo descrições sobre entidades, formatos, estrutura, linhagem de dados, relações e cálculos. Usamos o [Catálogo de Dados do Azure](/azure/data-catalog/overview) para tornar nossas fontes de dados facilmente detectáveis e compreensíveis.

Normalmente, os padrões de consumo de dados diferem conforme a função:

- Os **analistas de dados** se conectam diretamente aos modelos de BI centrais. Quando os modelos de BI centrais contêm todos os dados e a lógica de que precisam, eles usam conexões dinâmicas para criar relatórios e dashboards do Power BI. Quando eles precisam estender os modelos com os dados departamentais, criam [modelos compostos](composite-model-guidance.md) do Power BI. Se houver a necessidade de relatórios em estilo de planilha, eles usarão o Excel para produzir relatórios baseados em modelos de BI centrais ou modelos de BI departamentais.
- Os **desenvolvedores de BI** e os autores de relatórios operacionais se conectam diretamente aos modelos corporativos. Eles usam o Power BI Desktop para criar relatórios analíticos de conexão dinâmica. Eles também podem criar relatórios de BI de tipo operacional como relatórios paginados do Power BI, gravando consultas SQL nativas para acessar dados dos modelos do Azure Synapse Analytics Enterprise usando o T-SQL ou modelos do Power BI usando DAX ou MDX.
- Os **cientistas de dados** se conectam diretamente aos dados no data Lake. Eles usam o Azure Databricks e Python notebooks para desenvolver modelos de ML, que geralmente são experimentais e exigem habilidades especializadas para uso em produção.

:::image type="content" source="media/center-of-excellence-business-intelligence-solution-architecture/azure-data-warehouse-consumption.png" alt-text="Uma imagem mostra o consumo do Azure Synapse Analytics com Power BI e Azure Machine Learning.":::

## <a name="next-steps"></a>Próximas etapas

Para obter mais informações sobre este artigo, confira os seguintes recursos:

- [Enterprise BI no Azure com o Azure Synapse Analytics](/azure/architecture/reference-architectures/data/enterprise-bi-synapse)
- Dúvidas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
- Sugestões? [Contribuir com ideias para aprimorar o Power BI](https://ideas.powerbi.com/)
