---
title: Melhores práticas para pipelines de implantação
description: Melhores práticas para pipelines de implantação no Power BI
author: KesemSharabi
ms.author: kesharab
ms.topic: conceptual
ms.service: powerbi
ms.subservice: powerbi-service
ms.date: 05/06/2020
ms.openlocfilehash: e76d820e804a19db148e0db4c2702e002ee2c017
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83275905"
---
# <a name="deployment-pipelines-best-practices-preview"></a>Melhores práticas para pipelines de implantação (versão prévia)

Este artigo fornece orientações para criadores do BI que gerenciam conteúdo durante todo o ciclo de vida dele. O foco é a utilização dos pipelines de implantação como uma ferramenta de gerenciamento do ciclo de vida de conteúdo do BI.

Este artigo é dividido em quatro partes:

* **Preparação de conteúdo** – Prepare seu conteúdo para o gerenciamento do ciclo de vida.

* **Desenvolvimento** – Saiba quais as melhores formas de criar conteúdo no estágio de desenvolvimento de pipelines de implantação.

* **Teste** – Entenda como usar o estágio de teste da implantação de pipelines para testar seu ambiente.

* **Produção** – Utilize o estágio de produção de pipelines de implantação ao disponibilizar seu conteúdo para consumo.

## <a name="content-preparation"></a>Preparação de conteúdo

Prepare seu conteúdo para um gerenciamento contínuo durante todo o ciclo de vida. Não deixe de revisar as informações desta seção antes de fazer o seguinte:

* Liberar seu conteúdo para produção

* Começar a usar um pipeline de implantação para um workspace específico

* Publicar seu trabalho

### <a name="treat-each-workspace-as-a-complete-package-of-analytics"></a>Tratar cada workspace como um pacote completo de análise

O ideal é que um workspace tenha uma exibição completa de um aspecto (como departamento, unidade de negócios, projeto ou vertical) da organização. Isso facilita o gerenciamento de permissões para diferentes usuários e permite que as versões de conteúdo de todo o workspace sejam controladas de acordo com um cronograma planejado.  

Caso você esteja usando [conjuntos de dados centralizados](../connect-data/service-datasets-across-workspaces.md) que são usados em toda a organização, recomendamos a criação de dois tipos de workspaces:

* **Workspaces de modelagem e de dados** – esses workspaces contêm todos os conjuntos de dados centralizados

* **Workspaces de relatório** – esses workspaces contêm todos os relatórios e dashboards dependentes

### <a name="plan-your-permission-model"></a>Criar seu modelo de permissão

Um pipeline de implantação é um objeto do Power BI, com [permissões](deployment-pipelines-process.md#permissions) próprias. Além disso, o pipeline contém workspaces com permissões próprias.

Para implementar um fluxo de trabalho fácil e seguro, defina quem pode acessar cada parte do pipeline. Algumas considerações:

* Quem deve ter acesso ao pipeline?

* Quais operações os usuários com acesso ao pipeline podem executar em cada estágio?

* Quem está revisando o conteúdo no estágio de teste?

* Os revisores do estágio de teste devem ter acesso ao pipeline?

* Quem supervisionará a implantação no estágio de produção?

* Qual workspace você está atribuindo?

* A qual estágio você está atribuindo seu workspace?

* Você precisa alterar as permissões do workspace que está atribuindo?

### <a name="connect-different-stages-to-different-databases"></a>Conectar diferentes estágios a diferentes bancos de dados

Um banco de dados de produção deve estar sempre estável e disponível. É melhor não sobrecarregá-lo com consultas feitas por criadores de BI para seus conjuntos de dados de teste ou desenvolvimento. Crie bancos de dados separados para teste e para desenvolvimento. Isso ajuda a proteger os dados de produção, sem sobrecarregar o banco de dados de desenvolvimento com todos os dados de produção, o que causa lentidão no processo.

>[!NOTE]
>Caso sua organização esteja usando [conjuntos de dados centralizados compartilhados](../connect-data/service-datasets-share.md), você pode ignorar essa recomendação.

### <a name="use-parameters-in-your-model"></a>Usar parâmetros em seu modelo

Como não é possível editar fontes de conjuntos de dados no serviço do Power BI, recomendamos o uso de [parâmetros](https://docs.microsoft.com/power-query/power-query-query-parameters) para armazenar detalhes de conexão, como nomes de instância e de bancos de dados, em vez de usar uma cadeia de conexão estática. Isso permite que você gerencie as conexões por meio do portal da Web do serviço do Power BI ou [usando APIs](https://docs.microsoft.com/rest/api/power-bi/datasets/updateparametersingroup), em um estágio posterior.

Nos pipelines de implantação, você pode configurar regras de parâmetros a fim de definir valores específicos para os estágios de desenvolvimento, teste e produção.

Se você não usar parâmetros para a cadeia de conexão, poderá definir regras de fonte de dados a fim de especificar uma cadeia de conexão para determinado conjunto de dados. Porém, nos pipelines de implantação, não há suporte para isso em todas as fontes de dados. Para verificar se você pode configurar regras para sua fonte de dados, confira [Limitações da regra de conjunto de dados](deployment-pipelines-get-started.md#dataset-rule-limitations).

Os parâmetros têm outros usos, como fazer alterações em consultas, em filtros e no texto exibido no relatório.

## <a name="development"></a>Desenvolvimento

Esta seção fornece orientações para trabalhar com o estágio de desenvolvimento de pipelines de implantação.

### <a name="use-power-bi-desktop-to-edit-your-reports-and-datasets"></a>Usar o Power BI Desktop para editar seus relatórios e conjuntos de dados

Considere o Power BI Desktop como seu ambiente de desenvolvimento local. O Power BI Desktop permite que você experimente, explore e revise as atualizações para seus relatórios e conjuntos de dados. Após a conclusão do trabalho, você poderá carregar a nova versão no estágio de desenvolvimento. Devido aos motivos a seguir, recomendamos a edição de arquivos .pbix no Desktop (não no serviço do Power BI):

* Será mais fácil colaborar com outros criadores no mesmo arquivo .pbix se todas as alterações forem feitas na mesma ferramenta.

 * Fazer alterações online, baixar o arquivo .pbix e carregá-lo novamente causa a duplicação de relatórios e de conjuntos de dados.

* Você pode usar o controle de versão para manter seus arquivos .pbix atualizados.

### <a name="version-control-for-pbix-files"></a>Controle de versão para arquivos .pbix

Se você quiser gerenciar o histórico de versão de seus relatórios e conjuntos de dados, use a [sincronização automática do Power BI com o OneDrive](../connect-data/service-connect-to-files-in-app-workspace-onedrive-for-business.md). Isso mantém os arquivos atualizados com a versão mais recente. Também permite que você recupere versões mais antigas, se necessário.

>[!NOTE]
>Use a sincronização automática com o OneDrive (ou qualquer outro repositório) somente com os arquivos .pbix no estágio de desenvolvimento dos pipelines de implantação. Não sincronize arquivos .pbix nos estágios de teste e produção dos pipelines de implantação. Isso pode causar problemas com a implantação de conteúdo no pipeline.

### <a name="separate-modeling-development-from-report-and-dashboard-development"></a>Separar o desenvolvimento de modelagem do desenvolvimento de relatório e dashboard

Para implantações de escala empresarial, recomendamos separar o desenvolvimento de conjuntos de dados do desenvolvimento de relatórios e painéis. Para alterar apenas um relatório ou um conjunto de dados, use a opção de implantação seletiva dos pipelines de implantação.  

Essa abordagem deve começar pelo Power BI Desktop, criando um arquivo .pbix separado para conjuntos de dados e relatórios. Por exemplo, você pode criar um arquivo .pbix de conjunto de dados e carregá-lo no estágio de desenvolvimento. Depois, os autores de relatório podem criar um .pbix somente para o relatório e [conectá-lo ao conjunto de dados publicado](../connect-data/service-datasets-discover-across-workspaces.md) usando uma conexão dinâmica. Essa técnica permite que diferentes criadores trabalhem separadamente na modelagem e nas visualizações e as implantem de forma independente na produção.

Com um [conjunto de](../connect-data/service-datasets-share.md)dados compartilhado, você também pode usar esse método em workspaces.

### <a name="manage-your-models-using-xmla-readwrite-capabilities"></a>Gerenciar seus modelos usando recursos de leitura/gravação XMLA

A separação do desenvolvimento de modelagem do desenvolvimento de relatório e dashboard permite que você use recursos avançados, como controle do código-fonte, mescla de alterações de comparação e processos automatizados. Essas mudanças devem ser feitas no estágio de desenvolvimento, de modo que o conteúdo finalizado possa ser implantado nos estágios de teste e de produção. Isso permite que as alterações passem por um processo unificado com outros itens dependentes, antes que elas sejam implantadas na produção.

Você pode separar o desenvolvimento de modelagem das visualizações, gerenciando um [conjunto de dados compartilhado](../connect-data/service-datasets-share.md) em um workspace externo por meio de recursos de leitura/gravação XMLA. O conjunto de dados compartilhado pode se conectar a vários relatórios em diversos workspaces gerenciados em vários pipelines.

## <a name="test"></a>Teste

Esta seção fornece orientações para trabalhar com o estágio de teste dos pipelines de implantação.

### <a name="simulate-your-production-environment"></a>Simular seu ambiente de produção

Além de verificar a qualidade dos novos relatórios ou dashboards, também é importante ver como eles são executados pela perspectiva de um usuário final. O estágio de teste dos pipelines de implantação permite simular um ambiente de produção real para fins de teste.

Garanta que estes três fatores sejam abordados em seu ambiente de teste:

* Volume de dados

* Volume de uso

* Uma capacidade semelhante à de produção

Durante o teste, você pode usar a mesma capacidade do estágio de produção. Porém, isso pode tornar a produção instável no teste de carga. Para evitar uma produção instável, teste outra capacidade com recursos semelhantes à capacidade de produção no estágio de teste. Para evitar custos extras, você pode usar as [capacidades do Azure](../developer/embedded/azure-pbie-create-capacity.md) para pagar apenas pelo tempo de teste.

![diagrama das melhores práticas para pipelines de implantação](media/deployment-pipelines-best-practices/deployment-pipelines-best-practices-diagram.png)

### <a name="use-dataset-rules-with-a-real-life-data-source"></a>Usar regras de conjunto de dados com uma fonte de dados real

Caso você use o estágio de teste para simular um uso de dados real, recomendamos separar as fontes de dados de desenvolvimento e de teste. O banco de dados de desenvolvimento deve ser relativamente pequeno, e o banco de dados de teste deve ser o mais semelhante possível ao de produção. Use [regras de fonte de dados](deployment-pipelines-get-started.md#step-4---create-dataset-rules) para mudar as fontes de dados no estágio de teste.

Controlar a quantidade de dados que você importa da fonte de dados será útil se você estiver usando um banco de dados de produção no estágio de teste. Para isso, adicione um parâmetro à sua consulta de fonte de dados no Power BI Desktop. Use regras de parâmetro para controlar a quantidade de dados importados ou edite o valor do parâmetro.
Você também poderá usar essa abordagem se não quiser sobrecarregar sua capacidade.

### <a name="measure-performance"></a>Medir o desempenho

Ao simular um estágio de produção, [verifique as interações e a carga do relatório](../guidance/monitor-report-performance.md) e descubra se as alterações causaram impacto nelas.

Você também precisa [monitorar a carga da capacidade](../admin/service-admin-premium-monitor-capacity.md), para que possa capturar cargas elevadas antes que elas atinjam a produção.  

>[!NOTE]
>É recomendável monitorar as cargas da capacidade novamente após implantar atualizações no estágio de produção.

### <a name="check-related-items"></a>Verificar itens relacionados

Itens relacionados podem ser afetados por alterações em conjuntos de dados ou relatórios. Durante o teste, verifique se as alterações não afetam ou interrompem o desempenho dos itens existentes, que podem depender daqueles que foram atualizados.

Você pode localizar facilmente os itens relacionados usando a [exibição de linhagem](../collaborate-share/service-data-lineage.md) do workspace.

### <a name="test-your-app"></a>Testar seu aplicativo

Se você estiver distribuindo conteúdo para os usuários finais por meio de um aplicativo, examine a nova versão do aplicativo antes que esteja em produção. Como cada estágio do pipeline de implantação tem um workspace próprio, você pode publicar e atualizar aplicativos facilmente para os estágios de desenvolvimento e de teste. Isso permite que você teste o aplicativo do ponto de vista do usuário final.

>[!IMPORTANT]
>O processo de implantação não inclui a atualização do conteúdo ou das configurações do aplicativo. Para alterar o conteúdo ou as configurações, você precisa atualizar manualmente o aplicativo no estágio do pipeline necessário.

## <a name="production"></a>Produção

Esta seção fornece orientações para o estágio de produção dos pipelines de implantação.

### <a name="manage-who-can-deploy-to-production"></a>Gerenciar quem pode fazer implantações na produção

Como a implantação na produção deve ser tratada com cuidado, é recomendável que apenas pessoas específicas gerenciem essa operação delicada. Porém, provavelmente você deseja que todos os criadores do BI de um workspace específico tenham acesso ao pipeline. Isso pode ser gerenciado por meio das [permissões do workspace](deployment-pipelines-process.md#permissions) de produção.  

Para implantar conteúdo entre os estágios, os usuários precisam ter permissões de membro ou de administrador para ambos. Verifique se apenas as pessoas que você deseja que façam implantações na produção têm permissões do workspace de produção. Outros usuários podem ter funções de visualizador ou colaborador do workspace de produção. Eles poderão ver o conteúdo de dentro do pipeline, mas não poderão implantá-lo.

Além disso, você deve limitar o acesso ao pipeline habilitando permissões de pipeline apenas para usuários que fazem parte do processo de criação de conteúdo.

### <a name="set-rules-to-ensure-production-stage-availability"></a>Definir regras para garantir a disponibilidade do estágio de produção

As [regras de conjunto de dados](deployment-pipelines-get-started.md#step-4---create-dataset-rules) são uma forma poderosa de garantir que os dados na produção estejam sempre conectados e disponíveis aos usuários. Depois que as regras de conjunto de dados são aplicadas, as implantações podem ser feitas, e você tem a garantia de que os usuários finais verão as informações relevantes sem problemas.

Certifique-se de que você definiu regras do conjunto de dados de produção para fontes de dados e parâmetros definidos no conjunto de dados.

### <a name="update-the-production-app"></a>Atualizar o aplicativo de produção

A implantação em um pipeline atualiza o conteúdo do workspace, mas não atualiza o aplicativo associado automaticamente. Se você estiver usando um aplicativo para distribuição de conteúdo, não se esqueça de atualizá-lo após a implantação na produção, de modo que os usuários finais possam usar imediatamente a versão mais recente.  

### <a name="quick-fixes-to-content"></a>Correções rápidas no conteúdo

No caso de bugs na produção que precisem de uma correção rápida, não tente carregar uma nova versão do .pbix diretamente no estágio de produção ou fazer alteração online no serviço do Power BI. Implantar em estágios anteriores de teste e desenvolvimento não é possível quando já existe conteúdo nesses estágios. Além disso, a implantação de uma correção sem testá-la primeiro é uma prática inadequada. Portanto, a maneira correta de tratar esse problema é implementar a correção no estágio de desenvolvimento e enviá-la por push para o restante dos estágios do pipeline de implantação. Isso permite verificar se a correção funciona, antes de implantá-la na produção. Implantá-la no pipeline leva só alguns minutos.

## <a name="next-steps"></a>Próximas etapas

>[!div class="nextstepaction"]
>[Introdução aos pipelines de implantação](deployment-pipelines-overview.md)

>[!div class="nextstepaction"]
>[Introdução aos pipelines de implantação](deployment-pipelines-get-started.md)

>[!div class="nextstepaction"]
>[Compreender o processo de pipelines de implantação](deployment-pipelines-process.md)

>[!div class="nextstepaction"]
>[Solução de problemas de pipelines de implantação](deployment-pipelines-troubleshooting.md)
