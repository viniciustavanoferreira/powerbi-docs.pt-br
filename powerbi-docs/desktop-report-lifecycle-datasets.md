---
title: Conectar-se a conjuntos de dados no serviço do Power BI no Power BI Desktop
description: Use um conjunto de dados comum para vários relatórios do Power BI Desktop em vários workspaces e gerencie o ciclo de vida dos seus relatórios
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/13/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 278aa4c28db97c348e683b759e8a7f9415f19c3e
ms.sourcegitcommit: 7e845812874b3347bcf87ca642c66bed298b244a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79206828"
---
# <a name="connect-to-datasets-in-the-power-bi-service-from-power-bi-desktop"></a>Conectar-se a conjuntos de dados no serviço do Power BI no Power BI Desktop

Você pode estabelecer uma conexão dinâmica a um conjunto de dados compartilhado no *serviço do Power BI* e criar vários relatórios diferentes com base no mesmo conjunto de dados. Você pode criar seu modelo de dados perfeito no Power BI Desktop e publicá-lo no serviço do Power BI. Em seguida, você e outros usuários podem criar vários relatórios diferentes em arquivos *.pbix* separados usando esse Common Data Model e salvá-los em workspaces diferentes. Esse recurso é chamado de *conexão dinâmica do serviço do Power BI*.

![Obtenha dados do serviço do Power BI](media/desktop-report-lifecycle-datasets/report-lifecycle_01.png)

São inúmeras as vantagens encontradas nesse recurso, incluindo práticas recomendadas, que discutiremos ao longo deste artigo. Recomendamos que você revise as [considerações e limitações](#limitations-and-considerations) deste recurso.

## <a name="using-a-power-bi-service-live-connection-for-report-lifecycle-management"></a>Uso da conexão dinâmica ao serviço do Power BI para gerenciamento do ciclo de vida do relatório

Um desafio causado pela popularidade do Power BI é a proliferação de relatórios, dashboards e modelos de dados subjacentes. É fácil criar relatórios atraentes no Power BI Desktop e depois [publicar](desktop-upload-desktop-files.md) esses relatórios no serviço do Power BI, bem como criar excelentes dashboards a partir dos conjuntos de dados. Visto que muitas pessoas estavam fazem dessa forma, usando com frequência os mesmos ou quase os mesmos conjuntos de dados, saber qual relatório se baseou em qual conjunto de dados, e o quão atual cada conjunto de dados é, pode se tornar um desafio. A conexão dinâmica ao serviço do Power BI lida com esse desafio e torna mais fácil e consistente criar, compartilhar e expandir a partir de relatórios e dashboards de conjuntos de dados comuns.

### <a name="create-a-dataset-everyone-can-use-then-share-it"></a>Crie um conjunto de dados que todos possam usar e compartilhe-o

Digamos que Sara seja uma analista de negócios em sua equipe. Sara é ótima na criação de modelos de dados muito bem feitos, geralmente chamados de conjuntos de dados. Ela pode criar conjuntos de dados e relatórios e compartilhar os relatórios no serviço do Power BI.

![Publicar no serviço do Power BI](media/desktop-report-lifecycle-datasets/report-lifecycle_02a.png)

Todos adoraram o relatório e o conjunto de adora da Sara. É aí que começa o problema. Cada membro do grupo tentará criar *sua própria versão* do conjunto de dados e depois compartilhar seus próprios relatórios com a equipe. De repente, surge uma infinidade de relatórios, de diferentes conjuntos de dados, no workspace da equipe no serviço do Power BI. Qual deles é o mais recente? Os conjuntos de dados eram os mesmos ou quase os mesmos? Quais eram as diferenças? Com o recurso de conexão dinâmica ao serviço do Power BI, tudo isso pode mudar para melhor. Na próxima seção, veremos como os demais membros da equipe podem usar o conjunto de dados publicado de Anna em seus próprios relatórios e workspaces e usar o mesmo conjunto de dados consistente, verificado e publicado para criar seus próprios relatórios exclusivos.

### <a name="connect-to-a-power-bi-service-dataset-using-a-live-connection"></a>Conectar-se a um conjunto de dados do serviço do Power BI usando uma conexão dinâmica

Sara cria um relatório e o conjunto de base no qual ele se baseia. Em seguida, ela o publica no serviço do Power BI. O relatório aparece no workspace da equipe no serviço do Power BI. Se Sara salvá-lo em um *workspace da nova experiência*. Ela poderá definir a *permissão Criar* para disponibilizá-lo para visualização e uso por todas as pessoas dentro e fora do workspace.

Para saber mais sobre novos workspaces de experiência, confira [workspaces](service-new-workspaces.md).

Agora outros membros de dentro e fora do workspace da Sara podem estabelecer uma conexão dinâmica com o modelo de dados compartilhado usando o recurso de conexão dinâmica ao serviço do Power BI. Eles podem criar seus próprios relatórios exclusivos a partir do *conjunto de dados original* em *seus próprios workspaces da nova experiência*.

Na imagem a seguir, veja como Sara cria relatórios no Power BI Desktop e os publica, o que inclui o modelo de dados correspondente, no serviço do Power BI. Em seguida, os demais membros podem se conectar ao modelo de dados de Sara usando a conexão dinâmica ao serviço do Power BI e podem criar seus próprios relatórios exclusivos em seus próprios workspaces com base no conjunto de dados dela.

![Vários relatórios com base no mesmo conjunto de dados](media/desktop-report-lifecycle-datasets/report-lifecycle_03.png)

> [!NOTE]
> Se você salvar seu conjunto de dados em um [workspace compartilhado clássico](service-create-workspaces.md), somente os membros desse workspace poderão criar relatórios no seu conjunto de dados. Para estabelecer uma conexão dinâmica ao serviço do Power BI, o conjunto de dados ao qual você se conecta deve estar em um workspace compartilhado em que você é membro.
> 
> 

## <a name="step-by-step-for-using-the-power-bi-service-live-connection"></a>Passo a passo sobre como usar a conexão dinâmica ao serviço do Power BI

Agora que sabemos o quanto a conexão dinâmica ao serviço do Power BI é útil e como você pode usá-la como abordagem para melhores práticas de gerenciamento do ciclo de vida do relatório, vejamos as etapas necessárias para transformar os magníficos relatórios de Sara, e o conjunto de dados, em um conjunto de dados compartilhado que seus colegas de equipe do Power BI poderão usar.

### <a name="publish-a-power-bi-report-and-dataset"></a>Publicar um relatório do Power BI e o conjunto de dados

A primeira etapa do gerenciamento do ciclo de vida de relatórios usando uma conexão dinâmica ao serviço do Power BI é ter um relatório, e um conjunto de dados, que os colegas de equipe queiram usar. Sendo assim, Sara deve primeiro *publicar* o relatório do Power BI Desktop. Selecione **Publicar** na faixa de opções **Página inicial** no Power BI Desktop.

![Publicar um relatório](media/desktop-report-lifecycle-datasets/report-lifecycle_02a.png)

Se Sara não estiver conectada à conta de serviço do Power BI, o Power BI solicitará que ela faça isso.

![Entrar no Power BI Desktop](media/desktop-report-lifecycle-datasets/report-lifecycle_04.png)

Após conectar-se, ela poderá escolher o destino no workspace no qual o relatório e o conjunto de dados serão publicados. Lembre-se de que, se Anna salvá-lo em um novo workspace de experiência, qualquer pessoa com permissão de build poderá ter acesso a esse conjunto de dados. A permissão de build é definida no serviço do Power BI, após a publicação. Se ela salvar o trabalho em um workspace clássico, somente membros com acesso ao workspace no qual há relatórios publicados poderão acessar seu conjunto de dados usando uma conexão dinâmica ao serviço do Power BI.

![Publicar no serviço do Power BI](media/desktop-report-lifecycle-datasets/report-lifecycle_05.png)

O processo de publicação é iniciado, e o Power BI Desktop mostra o andamento.

![Publicação em andamento](media/desktop-report-lifecycle-datasets/report-lifecycle_06.png)

Concluído o processo, o Power BI Desktop mostrará o sucesso da publicação e fornecerá alguns links de acesso ao relatório propriamente dito no serviço do Power BI, bem como um link para acessar insights rápidos sobre o relatório.

![Publicação bem-sucedida](media/desktop-report-lifecycle-datasets/report-lifecycle_07.png)

Agora que seu relatório com o conjunto de dados está no serviço do Power BI, você também pode *promovê-lo*. A promoção significa que você atesta sua qualidade e confiabilidade. Você ainda pode solicitar que ele seja *certificado* por uma autoridade central em seu locatário do Power BI. Com um desses endossos, seu conjunto de dados sempre aparece no início da lista, quando as pessoas estiverem procurando conjuntos de dados. Para obter mais informações, confira [Promover seu conjunto de dados](service-datasets-promote.md).

A última etapa é definir a permissão Criar para o conjunto de dados no qual o relatório se baseia. A permissão de build determina quem pode ver e usar seu conjunto de dados. Você pode defini-la no workspace ou quando você compartilha um aplicativo do workspace. Para obter mais informações, confira [Permissão Criar para conjuntos de dados compartilhados](service-datasets-build-permissions.md).

Em seguida, vejamos como os outros colegas de equipe com acesso ao workspace onde o relatório, e o conjunto de dados, foi publicado podem se conectar ao conjunto de dados e criar seus próprios relatórios.

### <a name="establish-a-power-bi-service-live-connection-to-the-published-dataset"></a>Estabelecer uma conexão dinâmica ao serviço do Power BI com o conjunto de dados publicado

Para estabelecer uma conexão com o relatório publicado e criar seu próprio relatório com base no conjunto de dados publicado, selecione **Obter dados** na faixa de opções **Página Inicial** no Power BI Desktop e selecione **Power Platform** no painel à esquerda e, em seguida, selecione **Conjuntos de dados do Power BI**.

Se você não estiver conectado, o Power BI solicitará que você faça o login. Depois de conectado, o Power BI mostra os workspaces dos quais você é membro. Você pode selecionar qual workspace contém o conjunto de conjuntos no qual você deseja estabelecer uma conexão dinâmica do serviço do Power BI.

Os conjuntos de dados na lista são todos os conjuntos de dados compartilhados que você tem permissão de build, em qualquer workspace. Você pode pesquisar um conjunto de dados específico e ver seu nome, proprietário, o workspace no qual ele reside e quando ele foi atualizado pela última vez. Também é possível ver **ENDOSSADO** para os conjuntos de dados, certificados ou promovidos, na parte superior da lista.

![Lista de conjuntos de dados disponíveis](media/desktop-report-lifecycle-datasets/desktop-select-shared-dataset.png)

Ao selecionar **Criar**, você estabelece uma conexão dinâmica com o conjunto de ativos selecionado. O Power BI Desktop carrega os campos e os valores que você vê no Power BI Desktop em tempo real.

![Campos de conjunto de dados no painel Campos](media/desktop-report-lifecycle-datasets/report-lifecycle_10.png)

Agora você e outras pessoas podem criar e compartilhar relatórios personalizados com base no mesmo conjunto de dados. Essa abordagem é uma ótima maneira de ter uma pessoa experiente para criar um conjunto de dados bem formado, como o que a Sara fez. Os colegas de equipe podem usar esse conjunto de dados compartilhado para criar seus próprios relatórios.

## <a name="limitations-and-considerations"></a>Limitações e considerações

Ao usar a conexão dinâmica ao serviço do Power BI, há algumas limitações e considerações a serem observadas.

* Somente os usuários com permissão de build para um conjunto de dados podem se conectar ao conjunto de dados publicado usando a conexão dinâmica ao serviço do Power BI.
* Os usuários gratuitos só veem os conjuntos de dados de **Meu Workspace** e de workspaces Premium.
* Como essa conexão é uma conexão dinâmica, a navegação à esquerda e a modelagem são desabilitadas. Você só pode se conectar a um conjunto de dados em cada relatório. Esse comportamento é semelhante ao comportamento quando conectado ao *SQL Server Analysis Services*.
* Como essa conexão é uma conexão dinâmica, a RLS (segurança em nível de linha) e outros comportamentos de conexão são aplicados. É o mesmo que ocorre quando se está conectado ao SQL Server Analysis Services.
* Se o proprietário modifica o arquivo *.pbix* original compartilhado, o conjunto de dados e o relatório compartilhado no serviço do Power BI são substituídos. Os relatórios baseados no conjunto de dados não são substituídos, mas as alterações ao conjunto de dados são refletidas no relatório.
* Membros de um workspace não podem substituir o relatório originalmente compartilhado. Tentar fazer isso resulta em um aviso solicitando que você renomeie o arquivo e o publique.
* Se você excluir o conjunto de dados compartilhado no serviço do Power BI, outros relatórios baseados no conjunto de dados não funcionarão corretamente nem exibirão seus visuais.
* Para Pacotes de conteúdo, é necessário primeiro criar uma cópia do pacote de conteúdo antes de usá-lo como base para o compartilhamento de relatórios e conjuntos de dados *.pbix* no serviço do Power BI.
* Para pacotes de conteúdo da *Minha Organização*, uma vez copiados, não é possível substituir o relatório criado no serviço ou um relatório criado como parte da cópia de um pacote de conteúdo com uma conexão dinâmica. Tentar fazer isso resulta em um aviso solicitando que você renomeie o arquivo e o publique. Nessa situação, você pode substituir apenas relatórios conectados publicados dinamicamente.
* A exclusão de um conjunto de dados compartilhado no serviço do Power BI significa que ninguém pode mais acessar o conjunto de dados do Power BI Desktop.
* Os relatórios que compartilham um conjunto de dados no serviço do Power BI não são compatíveis com implantações automatizadas que usam a API REST do Power BI.
