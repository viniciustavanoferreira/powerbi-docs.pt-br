---
title: Realizar tarefas comuns de consulta no Power BI Desktop
description: Realizar tarefas comuns de consulta no Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/09/2020
ms.author: davidi
LocalizationGroup: Transform and shape data
ms.openlocfilehash: 8921737fac842d040d014244e2ce80e9bc158b23
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/05/2020
ms.locfileid: "76040204"
---
# <a name="perform-common-query-tasks-in-power-bi-desktop"></a>Realizar tarefas comuns de consulta no Power BI Desktop

Na janela do Editor do Power Query do Power BI Desktop, há uma série de tarefas usadas frequentemente. Este artigo demonstra essas tarefas comuns e fornece links para mais informações.

As tarefas comuns de consulta demonstradas aqui são estas:

* Conectar aos dados
* Formatar e combinar dados
* Agrupar linhas
* Dinamizar colunas
* Criar colunas personalizadas
* Fórmulas de consulta

Usaremos algumas conexões de dados para concluir essas tarefas. Os dados estão disponíveis para conexão ou download, caso você deseje executar essas tarefas por conta própria.

A primeira conexão de dados é [uma pasta de trabalho do Excel](https://download.microsoft.com/download/5/7/0/5701F78F-C3C2-450C-BCCE-AAB60C31051D/PBI_Edu_ELSi_Enrollment_v2.xlsx), que pode ser baixada e gravada localmente. A outra é um recurso da Web que também é usado em outros artigos do Power BI Desktop:

<https://www.bankrate.com/retirement/best-and-worst-states-for-retirement/>

As tarefas de consulta comuns começam nas etapas necessárias para conectar-se às duas fontes de dados.

## <a name="connect-to-data"></a>Conectar aos dados

Para se conectar aos dados no Power BI Desktop, selecione **Página Inicial** e **Obter Dados**. O Power BI Desktop apresenta um menu com as fontes de dados mais comuns. Para obter uma lista completa de fontes de dados às quais o Power BI Desktop pode se conectar, selecione o botão **Mais...** na parte inferior do menu. Para saber mais, confira [Fontes de dados no Power BI Desktop](desktop-data-sources.md).

![Menu de fontes de dados mais comuns, botão Obter Dados, Power BI Desktop](media/desktop-common-query-tasks/commonquerytasks_getdata.png)

Para começar, selecione **Excel**, especifique a pasta de trabalho do Excel mencionada anteriormente e, depois, selecione **Abrir**. O Power Query inspeciona a pasta de trabalho e apresenta os dados encontrados na caixa de diálogo **Navegador**, após a seleção de uma tabela.

![Fonte de dados do Excel, caixa de diálogo Navegador, Obter Dados, Power BI Desktop](media/desktop-common-query-tasks/commonquerytasks_navigator.png)

Você pode selecionar **Transformar Dados** para editar, ajustar ou *formatar* os dados antes de carregá-los no Power BI Desktop. A edição é útil principalmente quando você trabalha com conjuntos grandes de dados os quais você quer reduzir antes do carregamento.

Conectar-se a diferentes tipos de dados é igualmente fácil. Convém também se conectar a um recurso da Web. Escolha **Obter Dados** > **Mais** e, em seguida, selecione **Outros** > **Web** > **Conectar**.

![Fonte de dados da Web, caixa de diálogo Obter Dados, Power BI Desktop](media/desktop-common-query-tasks/commonquerytasks_getdata_other.png)

Digite a URL da página da Web na caixa de diálogo **Da Web** exibida.

![Caixa de diálogo Da Web, fonte de dados da Web, Obter Dados, Power BI Desktop](media/desktop-common-query-tasks/datasources_fromwebbox.png)

Selecione **OK**. Assim como antes, o Power BI Desktop inspeciona os dados da página da Web e mostra as opções de visualização na caixa de diálogo **Navegador**. Quando você seleciona uma tabela, ela exibe uma visualização dos dados.

Outras conexões de dados são semelhantes. Se for necessário autenticar-se para fazer uma conexão de dados, o Power BI Desktop solicitará a você as credenciais apropriadas.

Para ver uma demonstração passo a passo da conexão a dados no Power BI Desktop, confira [Conectar-se a dados no Power BI Desktop](desktop-connect-to-data.md).

## <a name="shape-and-combine-data"></a>Formatar e combinar dados

Você pode facilmente formatar e combinar dados com o Editor do Power Query. Esta seção inclui alguns exemplos de como você pode formatar dados. Para ver uma demonstração mais completa de formatação e combinação de dados, confira [Formatar e combinar dados com o Power BI Desktop](desktop-shape-and-combine-data.md).

Na seção anterior, você se conectou a dois conjuntos de dados: uma pasta de trabalho do Excel e um recurso da Web. Após o carregamento dos dados no Editor do Power Query, selecione a consulta da página da Web nas consultas disponíveis no painel **Consultas**, conforme mostrado aqui:

![Painel Consultas, Editor do Power Query, Power BI Desktop](media/desktop-common-query-tasks/commonquerytasks_querypaneloaded.png)

Ao formatar dados, você transforma uma fonte de dados na forma e formato que atendem às suas necessidades.

No Editor do Power Query, é possível encontrar vários comandos na faixa de opções e em um menu de contexto. Por exemplo, quando você clica com o botão direito em uma coluna, o menu de contexto permite a remoção dessa coluna. Também é possível selecionar a coluna e depois selecionar o botão **Remover Colunas** na guia **Página Inicial** da faixa de opções.

![Comando Remover Colunas, Editor do Power Query, Power BI Desktop](media/desktop-common-query-tasks/commonquerytasks_removecolumns.png)

Você pode formatar os dados de muitas outras maneiras nesta consulta. Você pode remover qualquer quantidade de linhas da parte superior ou inferior. Ou você pode adicionar colunas, dividir colunas, substituir valores e outras tarefas de moldagem. Com esses recursos, você pode direcionar o Editor do Power Query para obter os dados como quiser.

## <a name="group-rows"></a>Agrupar linhas

No Editor do Power Query, você pode agrupar os valores de várias linhas em um único valor. Esse recurso pode ser útil ao resumir o número de produtos oferecidos, o total de vendas ou a contagem de alunos.

Neste exemplo, você agrupa linhas em um conjunto de dados de matrículas acadêmicas. Os dados são da pasta de trabalho do Excel. Ela foi formatada no Editor do Power Query para mostrar apenas as colunas necessárias, o nome da tabela foi alterado e outras transformações foram feitas.

Vamos descobrir quantas agências cada estado tem. (As agências podem incluir distritos escolares, outras agências educacionais, como distritos de serviços regionais e muito mais.) Selecione a coluna **ID da Agência – NCES Atribuído \[Distrito\] Último ano disponível**, selecione o botão **Agrupar por** na guia **Transformar** ou na guia **Página Inicial** da faixa de opções. (**Agrupar por** está disponível nas duas guias.)

![Caixa de diálogo Agrupar por, Editor do Power Query, Power BI Desktop](media/desktop-common-query-tasks/commonquerytasks_groupby.png)

A caixa de diálogo **Agrupar por** é exibida. Quando o Editor do Power Query agrupa linhas, ela cria uma nova coluna na qual coloca os resultados de **Agrupar por**. É possível ajustar a operação **Agrupar Por** das seguintes maneiras:

1. A lista suspensa sem rótulo especifica a coluna a ser agrupada. O Editor do Power Query padroniza esse valor para a coluna selecionada, mas você pode alterá-lo para qualquer coluna na tabela.
2. **Nome da nova coluna**: o Editor do Power Query sugere um nome para a nova coluna com base na operação que ele aplica à coluna que está sendo agrupada. No entanto, você pode nomear a nova coluna como quiser.
3. **Operação**: Você pode escolher a operação aplicada pelo Editor do Power Query, como **Soma**, **Mediano** ou **Contar Linhas Distintas**. O valor padrão é **Contar Linhas**.
4. **Adicionar agrupamento** e **Adicionar agregação**: Esses botões só estarão disponíveis se você selecionar a opção **Avançado**. Em uma única operação, você pode fazer operações de agrupamento (ações **Group By**) em várias colunas e criar várias agregações usando esses botões. Com base em suas seleções nessa caixa de diálogo, o Editor do Power Query cria uma nova coluna que opera em várias colunas.

Selecione **Adicionar agrupamento** ou **Adicionar agregação** para adicionar mais agrupamentos ou agregações a uma operação **Agrupar por**. Para remover um agrupamento ou agregação, selecione o ícone de reticências ( **...** ) à direita da linha e, em seguida, **Excluir**. Vá em frente e experimente a operação **Agrupar por** usando os valores padrão para ver o que acontece.

![Caixa de diálogo Agrupar por, Editor do Power Query, Power BI Desktop](media/desktop-common-query-tasks/commonquerytasks_groupbynumbered.png)

Quando você seleciona **OK**, o Power Query executa a operação **Agrupar por** e retorna os resultados. Uau, veja só – Ohio, Texas, Illinois e Califórnia têm mais de mil agências cada uma!

![Contar coluna, operação Agrupar por, Editor do Power Query, Power BI Desktop](media/desktop-common-query-tasks/commonquerytasks_groupedresult.png)

E com o Editor do Power Query, sempre é possível remover a última operação de formatação. No painel **Configurações de Consulta**, em **Etapas Aplicadas**, basta selecionar o **X** ao lado da etapa concluída recentemente. Então, vá em frente e experimente. Se você não gostar dos resultados, refaça até que o Editor do Power Query formate seus dados do jeito que você quer.

## <a name="pivot-columns"></a>Dinamizar colunas

É possível dinamizar colunas e criar uma tabela que contém valores agregados para cada valor exclusivo em uma coluna. Por exemplo, para saber quantos produtos diferentes você tem em cada categoria de produto, é possível criar rapidamente uma tabela que faz isso.

Vejamos um exemplo. A tabela **Products_by_Categories** a seguir foi formatada para exibir apenas cada produto exclusivo (por nome) e a qual categoria cada produto pertence. Para criar uma nova tabela que mostra uma contagem de produtos para cada categoria (com base na coluna **CategoryName** ), selecione a coluna e selecione **Transformar** > **Dinamizar Coluna**.

![Comando Coluna Dinâmica, Editor do Power Query, Power BI Desktop](media/desktop-common-query-tasks/pivotcolumns_pivotbutton.png)

A caixa de diálogo **Dinamizar Coluna** é exibida, permitindo que você saiba quais valores de coluna serão usados para criar novas colunas (1). (Se o nome da coluna desejado **CategoryName** não aparecer, selecione-o na lista suspensa.) Ao expandir as **Opções avançadas** (2), você pode selecionar a função que será aplicada aos valores agregados (3).

![Caixa de diálogo Dinamizar Coluna, Editor do Power Query, Power BI Desktop](media/desktop-common-query-tasks/pivotcolumns_pivotdialog.png)

Quando você seleciona **OK**, o Power Query exibe a tabela de acordo com as instruções de transformação fornecidas na caixa de diálogo **Dinamizar Coluna**.

![Resultado de Dinamizar Coluna, Editor do Power Query, Power BI Desktop](media/desktop-common-query-tasks/pivotcolumns_pivotcomplete.png)

## <a name="create-custom-columns"></a>Criar colunas personalizadas

No Editor do Power Query, você pode criar fórmulas personalizadas que operam em várias colunas em sua tabela. Em seguida, você pode posicionar os resultados dessas fórmulas em uma nova coluna (personalizada). O Editor do Power Query facilita a criação de colunas personalizadas.

Com os dados da pasta de trabalho do Excel no Editor do Power Query, acesse a guia **Adicionar Coluna** na faixa de opções e, em seguida, selecione **Coluna Personalizada**.

![Comando Adicionar Coluna Personalizada, Editor do Power Query, Power BI Desktop](media/desktop-common-query-tasks/commonquerytasks_customcolumn.png)

A caixa de diálogo a seguir é exibida. Neste exemplo, criamos uma coluna personalizada chamada *Percent ELL* que calcula o percentual entre o total de alunos que são ELL (English Language Learners, aprendizes do idioma inglês).

![Caixa de diálogo Coluna Personalizada, Editor do Power Query, Power BI Desktop](media/desktop-common-query-tasks/customcolumn_addcustomcolumndialog.png)

Assim como ocorre com qualquer outra etapa aplicada no Editor do Power Query, se a nova coluna personalizada não fornecer os dados que você está procurando, exclua a etapa. No painel **Configurações de Consulta**, em **Etapas Aplicadas**, basta selecionar o **X** ao lado da etapa **Personalização Adicionada**.

![Etapas aplicadas, painel Configurações de Consulta, Editor do Power Query, Power BI Desktop](media/desktop-common-query-tasks/customcolumn_addedappliedstep.png)

## <a name="query-formulas"></a>Fórmulas de consulta

Você pode editar as etapas geradas pelo Editor do Power Query. Você também pode criar fórmulas personalizadas, que permitem que você se conecte e formate seus dados com mais precisão. Sempre que o Editor do Power Query executa uma ação nos dados, a fórmula associada à ação é exibida na barra de fórmulas. Para exibir a barra de fórmulas, acesse a guia **Exibir** da faixa de opções e selecione a **Barra de Fórmulas**.

![Opção Barra de Fórmulas, Editor do Power Query, Power BI Desktop](media/desktop-common-query-tasks/queryformulas_formulabar.png)

O Editor do Power Query mantém todas as etapas aplicadas de cada consulta como texto, assim você pode exibi-las ou modificá-las. Você pode exibir ou modificar o texto de qualquer consulta usando o **Editor Avançado**. Basta selecionar **Exibir** e, em seguida, **Editor Avançado**.

![Comando Editor Avançado, Editor do Power Query, Power BI Desktop](media/desktop-common-query-tasks/queryformulas_advancededitorbutton.png)

Veja aqui o **Editor Avançado**, com as etapas de consulta associadas à consulta **USA\_StudentEnrollment** exibida. Essas etapas são criadas na Linguagem de Fórmula do Power Query, frequentemente designada como *M*. Para saber mais, confira [Saiba mais sobre as fórmulas do Power Query](https://support.office.com/article/learn-about-power-query-formulas-6bc50988-022b-4799-a709-f8aafdee2b2f). Para exibir a própria especificação da linguagem, confira [Especificação da linguagem M do Power Query](/powerquery-m/power-query-m-language-specification).

![Caixa de diálogo Editor Avançado, Editor do Power Query, Power BI Desktop](media/desktop-common-query-tasks/queryformulas_advancededitor.png)

O Power BI Desktop fornece um amplo conjunto de categorias de fórmula. Para saber mais e obter uma referência completa de todas as fórmulas do Editor do Power Query, confira [Referência da função M do Power Query](/powerquery-m/power-query-m-function-reference).

## <a name="next-steps"></a>Próximas etapas

Você pode fazer de tudo com o Power BI Desktop. Para saber mais sobre seus recursos, confira os seguintes recursos:

* [O que é o Power BI Desktop?](desktop-what-is-desktop.md)
* [Visão geral de consulta com o Power BI Desktop](desktop-query-overview.md)
* [Fontes de dados no Power BI Desktop](desktop-data-sources.md)
* [Conectar-se a dados no Power BI Desktop](desktop-connect-to-data.md)
* [Formatar e combinar dados com o Power BI Desktop](desktop-shape-and-combine-data.md)
