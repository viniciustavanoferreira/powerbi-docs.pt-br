---
title: Fontes de dados do Power BI
description: Fontes de dados do Power BI
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 08/29/2019
ms.author: davidi
LocalizationGroup: Get started
ms.openlocfilehash: 021b5f0856ef4ff3730102efda88fd089a36dfcf
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83320068"
---
# <a name="data-sources-for-the-power-bi-service"></a>Fontes de dados do serviço do Power BI
Dados são o coração do Power BI. Digamos que você está explorando dados. Você pode fazer isso criando gráficos e dashboards ou fazendo perguntas com **P e R**. As visualizações e respostas resultantes estarão obtendo dados subjacentes de um conjunto de dados. Mas de onde vem esse conjunto de dados? Bem, ele vem de uma fonte de dados.

Neste artigo, vamos abordar os tipos de fontes de dados aos quais você pode se conectar usando o serviço do Power BI. Tenha em mente que há muitos outros tipos de fontes de dados dos quais você pode obter dados. Se você escolher essas fontes de dados, talvez seja necessário primeiro usar os recursos de consulta avançada de dados e modelagem do Power BI Desktop ou do Excel. Veremos mais sobre essas opções mais adiante. Por enquanto, vamos examinar os diferentes tipos de fontes de dados disponíveis diretamente no site do serviço do Power BI.

Você pode obter dados de qualquer uma das fontes de dados no Power BI, selecionando **Obter Dados** no canto inferior esquerdo da página.

![](media/service-get-data/pbi-getdata-navigation-link.png) 

Depois de selecionar **Obter Dados**, você poderá escolher os dados que deseja acessar

![](media/service-get-data/pbi-getdata-startscreen.png)

## <a name="discover-content"></a>Descobrir conteúdo
![](media/service-get-data/pbi-getdata-discovercontent.png)

A seção **Descobrir conteúdo** contém todos os dados e relatórios que você precisa já preparados para você. No Power BI há dois tipos de pacotes de conteúdo: Organizacional e Serviços. 

**Organizacional**: Se você e outros usuários da organização têm uma conta do Power BI Pro, vocês podem criar, compartilhar e usar pacotes de conteúdo. Para saber mais, veja [Introdução aos pacotes de conteúdo organizacional](../collaborate-share/service-organizational-content-pack-introduction.md).

**Serviços**: há, literalmente, dezenas de serviços com pacotes de conteúdo para o Power BI e muitos outros estão sendo adicionados o tempo todo. A maioria dos serviços exige que você tenha uma conta. Para obter mais informações, confira [Conectar-se a serviços que você usa com o Power BI](service-connect-to-services.md).

## <a name="create-new-content"></a>Criar conteúdo

A seção **Criar novo conteúdo** contém opções para criar e importar conteúdo por conta própria. No Power BI, há duas maneiras de criar ou importar seu próprio conteúdo: Arquivos e Bancos de Dados. 

### <a name="files"></a>Arquivos
![](media/service-get-data/pbi_getdata_files.png)

**Excel** ( *.xlsx* e *.xlsm*) – No Excel, uma pasta de trabalho pode incluir diferentes tipos de dados. Por exemplo, ela pode incluir dados que você mesmo inseriu em planilhas. Também pode incluir dados consultados e carregado de fontes de dados externas usando o Power Query. O Power Query está disponível por meio do **Obter e Transformar** no Excel 2016 ou do Power Pivot. Você pode importar dados de tabelas em planilhas ou importar dados de um modelo de dados. Para obter mais informações, confira [Obter dados de arquivos para o Power BI](service-get-data-from-files.md).

**Power BI Desktop** ( *.pbix*) – você pode usar o Power BI Desktop para consultar e carregar dados de fontes de dados externas e criar relatórios. Você também pode estender o modelo de dados com medidas e relações ou importar seu arquivo do Power BI Desktop para o site do Power BI. O Power BI Desktop é melhor para usuários mais avançados. Normalmente, esses usuários são aqueles que têm uma boa compreensão de suas fontes de dados. Eles também entendem conceitos de modelagem de dados, bem como transformação e consulta de dados. Para saber mais, veja [Conectar-se a dados no Power BI Desktop](desktop-connect-to-data.md).

**Valores separados por vírgula** ( *.csv*) – são arquivos de texto simples com linhas de dados. Cada linha pode conter um ou mais valores, cada um separado por uma vírgula. Por exemplo, um *.csv* que contém dados de nome e endereço pode ter muitas linhas. Cada linha pode ter valores para nome, sobrenome, endereço, cidade, estado e assim por diante. Você não pode importar dados para um arquivo *.csv*, mas muitos aplicativos, como o Excel, podem salvar dados de tabela simples como um arquivo *.csv*.

Para outros tipos de arquivo, como tabela XML ( *.xml*) ou arquivos de texto ( *.txt*), você pode usar **Obter e Transformar** para consultar, transformar e carregar dados em um arquivo do Excel ou do Power BI Desktop. Você pode importar o arquivo do Excel ou do Power BI Desktop para o Power BI.

O local em que você armazena seus arquivos também faz uma diferença significativa. O OneDrive for Business fornece maior nível de flexibilidade e integração com o Power BI. Está bem manter os arquivos em sua unidade local. No entanto, se você precisa atualizar os dados, há algumas etapas adicionais. Para obter mais informações, confira os links de artigos abaixo.

### <a name="databases"></a>Bancos de dados
![](media/service-get-data/pbi_getdata_databases.png)

**Bancos de dados na nuvem** – no serviço do Power BI, você pode se conectar de forma dinâmica ao:

* Banco de Dados SQL do Azure
* SQL Data Warehouse do Azure
* Spark no Azure HDInsight

As conexões do Power BI com esses bancos de dados ocorrem de forma dinâmica. Digamos que você se conecte a um Banco de Dados SQL do Azure. Então, você começa a explorar os dados criando relatórios no Power BI. Sempre que você fatia os dados ou adiciona outro campo a uma visualização, o Power BI faz uma consulta diretamente ao banco de dados. Para saber mais, veja [Azure e Power BI](service-azure-and-power-bi.md).

**Bancos de dados locais** – por meio do serviço do Power BI, você pode se conectar diretamente aos bancos de dados de modelo de tabela do SQL Server Analysis Services. Para fazer isso, você precisará de um gateway do Power BI Enterprise. Se você não tem certeza de como se conectar ao modelo de banco de dados de tabela da sua organização, verifique com o administrador ou o departamento de TI. Para saber mais, confira [Dados dinâmicos do SQL Server Analysis Services no Power BI](sql-server-analysis-services-tabular-data.md).

Para outros tipos de bancos de dados em sua organização, você precisará usar o Power BI Desktop ou o Excel para se conectar, consultar e carregar dados em um modelo de dados. Então, você poderá importar o arquivo para o Power BI, em um conjunto de dados existente. Se você configurar uma atualização agendada, o Power BI usará as informações de conexão e configuração do arquivo para conectar-se diretamente à fonte de dados e consultar atualizações. Em seguida, o Power BI carregará essas atualizações no conjunto de dados. Para saber mais, veja [Conectar-se a dados no Power BI Desktop](desktop-connect-to-data.md).

## <a name="what-if-my-data-comes-from-a-different-source"></a>E se meu dados vierem de uma fonte diferente?
Há centenas de fontes de dados diferentes que você pode usar com o Power BI. Não importa o local em que você obtém seus dados, contanto que eles estejam em um formato que possa ser consumido pelo serviço do Power BI. Com os dados consumíveis, o serviço do Power BI poderá criar relatórios e dashboards, responder perguntas com **P e R** e assim por diante.

Algumas fontes de dados já têm dados formatados para o serviço do Power BI. Essas fontes são como pacotes de conteúdo de provedores de serviços, como Google Analytics e Twilio. Os bancos de dados de modelos de tabela do SQL Server Analysis Services também estão prontos para uso. Você também pode se conectar de forma dinâmica a bancos de dados na nuvem, como o Banco de Dados SQL do Azure e o Spark no HDInsight.

Em outros casos, pode ser necessário consultar e carregar os dados em um arquivo. Por exemplo, digamos que você tenha dados de logística em sua organização. Você pode armazenar esses dados em um banco de dados de data warehouse em um servidor. No serviço do Power BI, você não pode se conectar a esse banco de dados e começar a explorar os dados, a menos que se trate de um modelo de banco de dados de tabela. Mas, você pode usar o Power BI Desktop ou o Excel para consultar e carregar esses dados de logística em um modelo de dados que, em seguida, você salva como um arquivo. Depois, você pode importar esse arquivo para o Power BI, em um conjunto de dados existente.

Você deve estar pensando, "Mas os dados de logística desse banco de dados são alterados diariamente. Como faço para atualizar meu conjunto de dados do Power BI?" Quando você importa os dados para o conjunto de dados, você também importa as informações de conexão do arquivo do Power BI Desktop ou do Excel.

Digamos que você configure uma atualização agendada ou faça uma atualização manual no conjunto de dados. O Power BI usa as informações de conexão do conjunto de dados, juntamente com algumas outras configurações, para se conectar diretamente ao banco de dados. Em seguida, ele consulta se há atualizações e carrega essas atualizações em um conjunto de dados. Uma observação adicional: provavelmente você precisará de um gateway do Power BI para proteger qualquer transferência de dados entre o servidor local e o Power BI. Quando a transferência for concluída, todas as visualizações dos relatórios e dashboards serão automaticamente atualizadas.

Observe que, mesmo que não seja possível se conectar diretamente à fonte de dados por meio do serviço do Power BI, ainda será possível colocar esses dados no Power BI. Somente serão necessárias algumas etapas a mais e talvez alguma ajuda do departamento de TI. Veja [Fontes de dados no Power BI Desktop](desktop-data-sources.md) para saber mais.

## <a name="some-more-details"></a>Mais alguns detalhes
Você verá os termos conjunto de dados e fonte de dados com muita frequência no Power BI. Geralmente, eles são usados como sinônimos. Mas eles realmente são duas coisas diferentes, embora sejam relacionadas.

Você cria um **conjunto de dados** automaticamente no Power BI ao usar **Obter Dados**. Com o **Obter Dados**, você se conecta e importa dados de um pacote de conteúdo, um arquivo ou se conecta a uma fonte de dados dinâmica. Um conjunto de dados contém informações sobre a fonte de dados e suas credenciais. Em muitos casos, ele também inclui um subconjunto de dados copiados da fonte de dados. Quando você cria visualizações em relatórios e dashboards, você está geralmente analisando dados no conjunto de dados.

Uma **fonte de dados** é o local do qual os dados de um conjunto de dados são provenientes. Por exemplo, os dados podem vir de:

* Um serviço online, como Google Analytics ou QuickBooks
* Um banco de dados na nuvem como o Banco de Dados SQL do Azure
* Um banco de dados ou um arquivo de um computador local ou servidor da sua organização

## <a name="data-refresh"></a>Atualização de dados
Talvez você salve os arquivos em uma unidade local ou uma unidade em outro lugar da sua organização. Você pode precisar de um gateway do Power BI para atualizar o conjunto de dados no Power BI. O computador que armazena o arquivo precisará estar ligado quando ocorrer uma atualização. Você pode importar novamente o arquivo ou usar a opção Publicar do Excel ou do Power BI Desktop, mas esses não são processos automatizados.

Se você salvar os arquivos no OneDrive for Business ou no SharePoint – Sites de Equipe, poderá conectar-se a eles ou importá-los para o Power BI. Assim, o conjunto de dados, os relatórios e o dashboard estarão sempre atualizados. Como o OneDrive e o Power BI estão na nuvem, o Power BI pode se conectar diretamente ao seu arquivo salvo. Ele se conecta uma vez a cada hora e verifica se há atualizações. O conjunto de dados e as visualizações serão atualizados automaticamente se houver atualizações.

Pacotes de conteúdo de serviços são atualizados automaticamente. Na maioria dos casos, eles são atualizados uma vez por dia. Você pode atualizar manualmente, mas a exibição dos dados atualizados dependerá do provedor de serviço. As atualizações em pacotes de conteúdo provenientes de pessoas da sua organização dependerão das fontes de dados usadas. Elas também dependerão de como a pessoa que criou o pacote de conteúdo configurou a atualização.

O Banco de Dados SQL do Azure, o SQL Data Warehouse do Azure e o Spark no Azure HDInsight são fontes de dados na nuvem. O serviço do Power BI também está na nuvem, portanto o Power BI pode se conectar a essas fontes de dados de forma dinâmica, usando o **DirectQuery**. O que você vê no Power BI está sempre sincronizado e não é necessário configurar uma atualização agendada.

Ao se conectar ao SQL Server Analysis Services por meio do Power BI, uma conexão dinâmica semelhante a um banco de dados do Azure na nuvem é estabelecida. A diferença é que o banco de dados fica em um servidor da sua organização. Esse tipo de conexão exige um gateway do Power BI, que é configurado pelo departamento de TI.

A atualização de dados é uma parte muito importante do Power BI e é muito profunda para ser abordada aqui. Se desejar obter um entendimento completo, confira [Atualização de dados no Power BI](refresh-data.md).

## <a name="considerations-and-limitations"></a>Considerações e limitações
Para todas as fontes de dados usadas no serviço do Power BI, considere as seguintes limitações. Existem outras limitações que se aplicam a recursos específicos, mas a lista a seguir é aplicável ao serviço do Power BI completo:

* **Limite de tamanho do conjunto de dados** – há um limite de 1 GB para o conjunto de dados armazenados em capacidades compartilhadas no serviço do Power BI. Se você precisar de conjuntos de dados maiores, poderá usar o [Power BI Premium ](../admin/service-premium-what-is.md).

* **Valores distintos em uma coluna** – ao armazenar em cache um conjunto de dados do Power BI (às vezes chamado de modo "Importar"), há um limite de 1.999.999.997 no número de valores distintos que podem ser armazenados em uma coluna.

* **Limite de linha**: ao usar o **DirectQuery** , o Power BI impõe um limite nos resultados da consulta que são enviados para sua fonte de dados subjacente. Se a consulta enviada para a fonte de dados retornar mais de 1 milhão de linhas, você verá um erro e a consulta falhará. Os dados subjacentes ainda podem conter mais de 1 milhão de linhas. É improvável que você se depare com esse limite, pois a maioria dos relatórios agrega os dados em conjuntos menores de resultados.

* **Limite de coluna** – o número máximo de colunas permitido em um conjunto de dados, em todas as tabelas no conjunto de dados, é de 16.000 colunas. Esse limite se aplica ao serviço do Power BI e aos conjuntos de dados usados no Power BI Desktop. O Power BI controla o número de colunas e tabelas no conjunto de dados dessa forma, o que significa que o número máximo de colunas é 16.000 menos um para cada tabela no conjunto de registros.
