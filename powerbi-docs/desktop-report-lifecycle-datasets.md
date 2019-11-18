---
title: Conectar-se a conjuntos de dados no serviço do Power BI no Power BI Desktop
description: Use um conjunto de dados comum para vários relatórios do Power BI Desktop em vários workspaces e gerencie o ciclo de vida dos seus relatórios
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 08/29/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: de72cab51a4d43d1a07d6ada0bd77888952817ab
ms.sourcegitcommit: 8cc2b7510aae76c0334df6f495752e143a5851c4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73429806"
---
# <a name="connect-to-datasets-in-the-power-bi-service-from-power-bi-desktop"></a>Conectar-se a conjuntos de dados no serviço do Power BI no Power BI Desktop
Você pode estabelecer uma conexão dinâmica a um conjunto de dados compartilhado no serviço do Power BI e criar vários relatórios diferentes com base no mesmo conjunto de dados. Isso significa que você pode criar seu modelo de dados perfeito no Power BI Desktop e publicá-lo no serviço do Power BI. Em seguida, você e outros usuários podem criar vários relatórios diferentes (em arquivos .pbix separados) usando esse mesmo Common Data Service e salvá-los em workspaces diferentes. Esse recurso é chamado de **conexão dinâmica do serviço do Power BI**.

![Obtenha dados do serviço do Power BI](media/desktop-report-lifecycle-datasets/report-lifecycle_01.png)

São inúmeras as vantagens encontradas nesse recurso, incluindo práticas recomendadas, que discutiremos ao longo deste artigo. Há também algumas considerações e limitações, portanto, certifique-se de ler todo o conteúdo relacionado, que está disponível no fim deste artigo.

## <a name="using-a-power-bi-service-live-connection-for-report-lifecycle-management"></a>Uso da conexão dinâmica ao serviço do Power BI para gerenciamento do ciclo de vida do relatório
Um desafio causado pela popularidade do Power BI é a proliferação de relatórios, dashboards e modelos de dados subjacentes. Eis o porquê: é fácil criar relatórios atraentes no **Power BI Desktop** e depois compartilhar ([publicar](desktop-upload-desktop-files.md)) esses relatórios no **serviço do Power BI**, bem como criar excelentes dashboards a partir dos conjuntos de dados. Visto que muitas pessoas estavam agindo dessa forma, usando com frequência os mesmos (ou quase os mesmos) conjuntos de dados, saber qual relatório se baseou em qual conjunto de dados (e o quão atual cada conjunto de dados é) tornou-se um desafio. A **conexão dinâmica ao serviço do Power BI** lida com esse desafio e torna mais fácil e consistente criar, compartilhar e expandir a partir de relatórios e dashboards de conjuntos de dados comuns.

### <a name="create-a-dataset-everyone-can-use-then-share-it"></a>Crie um conjunto de dados que todos possam usar e compartilhe-o
Digamos que Anna (uma analista de negócios) pertence à sua equipe e é ótima na criação de modelos de dados muito bem feitos (geralmente chamados de conjuntos de dados). Com sua competência, Anna pode criar conjuntos de dados e relatórios e compartilhar os relatórios no **serviço do Power BI**.

![Publicar no serviço do Power BI](media/desktop-report-lifecycle-datasets/report-lifecycle_02a.png)

Todos adoram os relatórios e conjuntos de dados de Anna, e é aí que o problema começa: cada membro do grupo tentará criar *sua própria versão* do conjunto de dados e depois compartilhar seus próprios relatórios com a equipe. De repente, surge uma infinidade de relatórios (de diferentes conjuntos de dados) no workspace da equipe no **serviço do Power BI**. Qual deles é o mais recente? Os conjuntos de dados eram os mesmos ou quase os mesmos? Quais eram as diferenças? Com o recurso de **conexão dinâmica ao serviço do Power BI**, tudo isso pode mudar para melhor. Na próxima seção, veremos como os demais membros da equipe podem usar o conjunto de dados publicado de Anna em seus próprios relatórios e workspaces e usar o mesmo conjunto de dados consistente, verificado e publicado para criar seus próprios relatórios exclusivos.

### <a name="connect-to-a-power-bi-service-dataset-using-a-live-connection"></a>Conectar-se a um conjunto de dados do serviço do Power BI usando uma conexão dinâmica
Depois de criar o relatório (e o conjunto de dados no qual se baseou), Anna o publica no **serviço do Power BI** e ele será exibido no workspace da equipe no serviço do Power BI. Se ela o salvar em um *novo workspace de experiência*, poderá definir a permissão Criar para disponibilizá-lo para visualização e uso por todas as pessoas dentro e fora do workspace.

Para saber mais sobre novos workspaces de experiência, confira [workspaces](service-new-workspaces.md).

Outros membros dentro e fora do workspace de Anna podem agora estabelecer uma conexão dinâmica com o modelo de dados compartilhado dela (usando o recurso de **conexão dinâmica ao serviço do Power BI**) e criar seus próprios relatórios exclusivos usando o *conjunto de dados original* em *seus novos workspaces de experiência*.

Na imagem a seguir, veja como Anna cria relatórios no **Power BI Desktop** e os publica (inclui o modelo de dados correspondente) no **serviço do Power BI**. Em seguida, os demais membros poderão se conectar ao modelo de dados de Anna usando a **conexão dinâmica ao serviço do Power BI** e criar seus próprios relatórios exclusivos em seus próprios workspaces com base no conjunto de dados dela.

![Vários relatórios com base no mesmo conjunto de dados](media/desktop-report-lifecycle-datasets/report-lifecycle_03.png)

> [!NOTE]
> Se você salvar seu conjunto de dados em um [workspace compartilhado clássico](service-create-workspaces.md), somente os membros desse workspace poderão criar relatórios no seu conjunto de dados. Para estabelecer uma conexão dinâmica ao serviço do Power BI, o conjunto de dados ao qual você se conecta deve estar em um workspace compartilhado em que você é membro.
> 
> 

## <a name="step-by-step-for-using-the-power-bi-service-live-connection"></a>Passo a passo sobre como usar a conexão dinâmica ao serviço do Power BI
Agora que sabemos o quanto a **conexão dinâmica ao serviço do Power BI** é útil e como você pode usá-la como abordagem para melhores práticas de gerenciamento do ciclo de vida do relatório, vejamos as etapas necessárias para transformar os magníficos relatórios de Anna (e o conjunto de dados) em um conjunto de dados compartilhado que seus colegas de equipe do Power BI poderão usar.

### <a name="publish-a-power-bi-report-and-dataset"></a>Publicar um relatório do Power BI e o conjunto de dados
A primeira etapa do gerenciamento do ciclo de vida de relatórios usando uma **conexão dinâmica ao serviço do Power BI** é ter um relatório (e um conjunto de dados) que os colegas de equipe queiram usar. Sendo assim, Anna deve primeiro **publicar** o relatório do **Power BI Desktop**. Para fazer isso, ela deve selecionar **Publicar** na faixa de opções **Início** no Power BI Desktop.

![Publicar um relatório](media/desktop-report-lifecycle-datasets/report-lifecycle_02a.png)

Se Anna não estiver conectada à conta de serviço do Power BI, um pop-up solicitará que ela faça isso.

![Entrar no Power BI Desktop](media/desktop-report-lifecycle-datasets/report-lifecycle_04.png)

Após conectar-se, ela poderá escolher o destino no workspace no qual o relatório e o conjunto de dados serão publicados. Lembre-se de que, se Anna salvá-lo em um novo workspace de experiência, qualquer pessoa com permissão de build poderá ter acesso a esse conjunto de dados. A permissão de build é definida no serviço do Power BI, após a publicação. Se ela salvar o trabalho em um workspace clássico, somente membros com acesso ao workspace no qual há relatórios publicados poderão acessar seu conjunto de dados usando uma **conexão dinâmica ao serviço do Power BI**.

![Publicar no serviço do Power BI](media/desktop-report-lifecycle-datasets/report-lifecycle_05.png)

O processo de publicação é iniciado, e o **Power BI Desktop** mostra o andamento.

![Publicação em andamento](media/desktop-report-lifecycle-datasets/report-lifecycle_06.png)

Concluído o processo, o **Power BI Desktop** mostrará o sucesso da publicação e fornecerá alguns links de acesso ao relatório propriamente dito no **serviço do Power BI**, bem como um link para acessar **Insights rápidos** no relatório.

![Publicação bem-sucedida](media/desktop-report-lifecycle-datasets/report-lifecycle_07.png)

Agora que seu relatório com o conjunto de dados está no serviço do Power BI, você também pode *promovê-lo* para atestar sua qualidade e confiabilidade. Você ainda pode solicitar que ele seja *certificado* por uma autoridade central em seu locatário do Power BI. Com um desses endossos, seu conjunto de dados será sempre exibido no início da lista, quando as pessoas estiverem procurando conjuntos de dados. Se estiver interessado, você poderá ler mais sobre o processo de [promoção de seu conjunto de dados](service-datasets-promote.md). 

A última etapa é definir a *permissão de build* para o conjunto de dados no qual o relatório se baseia. A permissão de build determina quem pode ver e usar seu conjunto de dados. Você pode defini-la no workspace ou quando você compartilha um aplicativo do workspace. Leia mais sobre como definir a [permissão de build](service-datasets-build-permissions.md).

Em seguida, vejamos como os outros colegas de equipe com acesso ao workspace onde o relatório (e o conjunto de dados) foi publicado podem se conectar ao conjunto de dados e criar seus próprios relatórios.

### <a name="establish-a-power-bi-service-live-connection-to-the-published-dataset"></a>Estabelecer uma conexão dinâmica ao serviço do Power BI com o conjunto de dados publicado
Para estabelecer uma conexão com o relatório publicado e criar seu próprio relatório com base no conjunto de dados publicado, selecione **Obter dados** na faixa de opções **Página Inicial** no **Power BI Desktop** e selecione **Power BI** no painel à esquerda e, em seguida, selecione **Conjuntos de dados do Power BI**.

Caso não tenha acessado ainda o Power BI, você será solicitado a fazê-lo. Após fazer logon, uma janela mostrará os workspaces dos quais você é membro, permitindo selecionar o workspace que contém o conjunto de dados com o qual você deseja estabelecer uma **conexão dinâmica ao serviço do Power BI**.

Os conjuntos de dados na lista são todos os conjuntos de dados compartilhados que você tem permissão de build, em qualquer workspace. Você pode pesquisar um conjunto de dados específico e ver seu nome, proprietário, o workspace no qual ele reside e quando ele foi atualizado pela última vez. Também é possível ver os conjuntos de dados *endossados*, certificados ou promovidos, na parte superior da lista. 

![Lista de conjuntos de dados disponíveis](media/desktop-report-lifecycle-datasets/desktop-select-shared-dataset.png)

Ao selecionar **Carregar** na janela, é estabelecida uma conexão dinâmica ao conjunto de dados selecionado, isto é, os dados visualizados (os campos e seus valores) são carregados no **Power BI Desktop** em tempo real.

![Campos de conjunto de dados no painel Campos](media/desktop-report-lifecycle-datasets/report-lifecycle_10.png)

Agora, você (e outras pessoas) podem criar e compartilhar relatórios personalizados com base no mesmo conjunto de dados. Essa é uma excelente maneira de poder contar com uma pessoa experiente para criar um conjunto de dados bem estruturado (assim como Anna faz) e permitir que vários colegas de equipe utilizem o conjunto de dados compartilhado para criar seus próprios relatórios.

## <a name="limitations-and-considerations"></a>Limitações e considerações
Ao usar a **conexão dinâmica ao serviço do Power BI**, há algumas limitações e considerações a serem observadas.

* Somente os usuários com permissão de build para um conjunto de dados podem se conectar ao conjunto de dados publicado usando a **conexão dinâmica ao serviço do Power BI**. 
* Os usuários gratuitos só veem os conjuntos de dados de Meu Workspace e de workspaces Premium.
* Como essa é uma conexão dinâmica, a navegação à esquerda e a modelagem são desabilitadas. Esse comportamento é semelhante a quando conectado ao **SQL Server Analysis Services**, e é possível se conectar somente a um conjunto de dados em cada relatório.
* Por se tratar de uma conexão dinâmica, a RLS (segurança em nível de linha e de função) e outros comportamentos de conexão semelhantes são executados da mesma forma como quando conectado ao **SQL Server Analysis Services**.
* Se o proprietário modifica o arquivo .pbix original compartilhado, o conjunto de dados e o relatório compartilhado no **serviço do Power BI** são substituídos. Os relatórios baseados no conjunto de dados não são substituídos, mas as alterações ao conjunto de dados são refletidas no relatório.
* Membros de um workspace não podem substituir o relatório originalmente compartilhado. Tentar fazer isso resulta em um aviso solicitando que você renomeie o arquivo e o publique.
* Se você excluir o conjunto de dados compartilhado no **serviço do Power BI**, outros relatórios baseados no conjunto de dados não funcionarão corretamente nem exibirão seus visuais.
* Para Pacotes de conteúdo, é necessário primeiro criar uma cópia do pacote de conteúdo antes de usá-lo como base para o compartilhamento de relatórios e conjuntos de dados .pbix no **serviço do Power BI**.
* Para pacotes de conteúdo da *Minha Organização*, uma vez copiados, não é possível substituir o relatório criado no serviço e/ou um relatório criado como parte da cópia de um pacote de conteúdo com uma conexão dinâmica. Tentar fazer isso resulta em um aviso solicitando que você renomeie o arquivo e o publique. Nessa situação, você pode substituir apenas relatórios conectados publicados dinamicamente.
* A exclusão de um conjunto de dados compartilhado no **serviço do Power BI** significa que ninguém pode mais acessar o conjunto de dados do **Power BI Desktop**.
* Os relatórios que compartilham um conjunto de dados no serviço do Power BI não são compatíveis com implantações automatizadas que usam a API REST do Power BI.

