---
title: 'Exemplo de Rentabilidade do Cliente para o Power BI: Faça um tour'
description: 'Exemplo de Rentabilidade do Cliente para o Power BI: Faça um tour'
author: maggiesMSFT
manager: kfile
ms.reviewer: amac
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 07/05/2019
ms.author: maggies
LocalizationGroup: Samples
ms.openlocfilehash: ddda7d6aaacbcde2d71371b316d14a9cd411bd43
ms.sourcegitcommit: f05ba39a0e46cb9cb43454772fbc5397089d58b4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/26/2019
ms.locfileid: "68523419"
---
# <a name="customer-profitability-sample-for-power-bi-take-a-tour"></a>Exemplo de Rentabilidade do Cliente para o Power BI: Faça um tour

O pacote de conteúdo do exemplo de Rentabilidade do Cliente contém um painel, relatório e um conjunto de dados relacionados a uma empresa que fabrica materiais de marketing. Esse dashboard foi criado por uma diretora financeira para ver métricas-chave de seus cinco gerentes de unidade de negócios (ou executivos), produtos, clientes e margens brutas (GM). Rapidamente, é possível ver quais fatores estão afetando a lucratividade.

![Dashboard para o exemplo de Rentabilidade do Cliente](media/sample-customer-profitability/power-bi-dash.png)

Este exemplo faz parte de uma série que mostra como o Power BI pode ser usado com dados, relatórios e painéis orientados aos negócios. Ele foi criado pela [obviEnce](http://www.obvience.com/) usando dados reais, que foram mantidos anônimos. Os dados estão disponíveis em vários formatos: pacote de conteúdo, arquivo .pbix do Power BI Desktop ou pasta de trabalho do Excel. Confira [Exemplos para o Power BI](sample-datasets.md). 

Este tutorial explora o pacote de conteúdo de exemplo Rentabilidade do Cliente no serviço do Power BI. Como as experiências de relatório são muito semelhantes no Power BI Desktop e no serviço, você também pode acompanhar usando o arquivo de exemplo .pbix no Power BI Desktop. 

Você não precisa de uma licença do Power BI para explorar os exemplos no Power BI Desktop. Se você não tiver uma licença do Power BI Pro, poderá salvar a amostra em Meu Espaço de Trabalho no serviço do Power BI. 

## <a name="get-the-sample"></a>Obter o exemplo

Antes de usar o exemplo, primeiro você deve baixá-lo como um [pacote de conteúdo](#get-the-content-pack-for-this-sample), [arquivo .pbix](#get-the-pbix-file-for-this-sample) ou [pasta de trabalho do Excel](#get-the-excel-workbook-for-this-sample).

### <a name="get-the-content-pack-for-this-sample"></a>Obter o pacote de conteúdo para este exemplo

1. Abra o serviço do Power BI (app.powerbi.com), entre e abra o workspace em que você deseja salvar o exemplo.

   Se você não tiver uma licença do Power BI Pro, poderá salvar a amostra em Meu Espaço de Trabalho.

2. No canto inferior esquerdo, selecione **Obter Dados**.

   ![Selecionar Obter Dados](media/sample-datasets/power-bi-get-data.png)
3. Na página **Obter Dados** que aparece, selecione **Exemplos**.

4. Selecione **Exemplo de Rentabilidade do Cliente** e, em seguida, escolha **Conectar**.  

    ![Conectar-se ao exemplo](media/sample-customer-profitability/get-supplier-sample.png)
5. O Power BI importa o pacote de conteúdo e adiciona um novo dashboard, um relatório e um conjunto de dados ao seu workspace atual.

    ![Entrada do Exemplo de Lucratividade do Cliente](media/sample-customer-profitability/customer-profitability-sample-entry.png)

### <a name="get-the-pbix-file-for-this-sample"></a>Obter o arquivo. pbix para este exemplo

Como alternativa, você pode baixar o exemplo de Rentabilidade do Cliente como um [arquivo.pbix](http://download.microsoft.com/download/6/A/9/6A93FD6E-CBA5-40BD-B42E-4DCAE8CDD059/Customer%20Profitability%20Sample%20PBIX.pbix), que é projetado para uso com o Power BI Desktop.

### <a name="get-the-excel-workbook-for-this-sample"></a>Obter a pasta de trabalho do Excel para este exemplo

Se quiser exibir a fonte de dados deste exemplo, ela também está disponível como uma [Pasta de trabalho do Excel](http://go.microsoft.com/fwlink/?LinkId=529781). A pasta de trabalho contém planilhas do Power View que você pode exibir e modificar. Para ver os dados brutos, habilite os suplementos de Análise de Dados e, em seguida, selecione **Power Pivot > Gerenciar**. Para habilitar os suplementos Power View e Power Pivot, confira [Dar uma olhada nos exemplos do Excel dentro do próprio Excel](sample-datasets.md#optional-take-a-look-at-the-excel-samples-from-inside-excel-itself) para obter detalhes.

## <a name="what-is-our-dashboard-telling-us"></a>O que é nosso painel está dizendo?

No workspace em que você salvou o exemplo, localize o dashboard Rentabilidade do Cliente e selecione-o:

![Dashboard para o exemplo de Rentabilidade do Cliente](media/sample-customer-profitability/power-bi-dash.png)

### <a name="company-wide-dashboard-tiles"></a>Blocos de painel de toda a empresa
1. Abra o dashboard no serviço do Power BI. Esses blocos de dashboard dão à nossa diretora financeira métricas de empresa de alto nível importantes para ela. Quando ela vir algo interessante, pode selecionar um bloco para examinar os dados.

2. Examine os blocos no lado esquerdo do painel.

    ![Blocos para gerentes](media/sample-customer-profitability/power-bi-manager.png)

   Observe o seguintes detalhes:
   - A margem bruta da empresa é de 42,5%.
   - Ele tem 80 clientes.
   - Ela vende cinco produtos diferentes.
   - Ela teve sua menor variação percentual de receita para o orçamento em fevereiro, seguida pela mais alta em março.
   - A maioria da receita é proveniente das regiões leste e norte. A margem bruta nunca ultrapassou o orçamento, com as unidades de negócios ER-0 e MA-0 exigindo mais investigações.
   - A receita total para o ano é quase o orçamento.

### <a name="manager-specific-dashboard-tiles"></a>Blocos do painel específico do gerente
Os blocos no lado direito do painel fornecem uma pontuação da equipe. A diretora financeira precisa acompanhar seus gerentes e esses blocos apresentam uma visão geral de alto nível do lucro usando o percentual de GM. Se a tendência de percentual de GM for inesperada para qualquer gerente, ela poderá investigar mais.

![GM% para gerentes](media/sample-customer-profitability/power-bi-manager2.png)

Analisando os blocos do dashboard específicos para gerentes, podemos fazer as seguintes observações:

- Todos os executivos, exceto Carlos, já excederam suas metas de vendas. No entanto, as vendas reais de Carlos são as mais altas.
- O percentual de GM de Annelie é o mais baixo, mas podemos ver um aumento gradual desde março.
- Valery, por outro lado, viu uma queda significativa no percentual de GM.
- E Andrew teve um ano volátil.

## <a name="explore-the-dashboards-underlying-data"></a>Explore os dados subjacentes do painel
Este painel tem blocos que vinculam a um relatório e a uma pasta de trabalho do Excel.

### <a name="open-the-excel-online-data-source"></a>Abra a fonte de dados do Excel Online
Dois blocos neste dashboard, **Destino vs Real** e **Crescimento de receita ano a ano** foram fixados de uma pasta de trabalho do Excel. Quando você selecionar um desses blocos, o Power BI abrirá a fonte de dados – nesse caso, o Excel Online.

![Excel Online](media/sample-customer-profitability/power-bi-excel-online.png)

1. Selecione qualquer um dos blocos que foram fixados do Excel. O Excel Online é aberto dentro do serviço Power BI.
2. Observe que a pasta de trabalho tem três guias de dados. Abra **Receita**.
3. Vamos dar uma olhada para saber por que Carlos ainda não atingiu sua meta:  

    a. No controle deslizante **Executivo**, selecione **Carlos Grilo**.   

    b. A primeira Tabela Dinâmica informa que o crescimento de receita de Carlos para seu produto principal, Primus, diminuiu 152% com relação ao ano passado. O gráfico **Variação de Receita Ano a Ano** mostra que, na maioria dos meses, ele está abaixo do orçamento.  

    ![Tabela dinâmica](media/sample-customer-profitability/power-bi-pivotchart.png)

    ![Resultados de Carlos](media/sample-customer-profitability/power-bi-carlos.png)

4. Continue a explorar. Se encontrar algo interessante, selecione **Fixar** ![ícone de alfinete](media/sample-customer-profitability/power-bi-excel-pin.png) no canto superior direito para [fixá-lo a um dashboard](service-dashboard-pin-tile-from-excel.md).

5. Use a seta Voltar do navegador para retornar ao painel.

### <a name="open-the-underlying-power-bi-report"></a>Abra o relatório subjacente do Power BI
Muitos blocos no dashboard de exemplo Lucratividade do Cliente foram fixados do relatório de exemplo subjacente Lucratividade do Cliente.

1. Selecione um desses blocos para abrir o relatório no modo de exibição de leitura.

   Se o bloco foi criado em P e R, selecioná-lo abre a janela de P e R. Selecione **Sair de P e R** para voltar para o dashboard e tente um bloco diferente.

2. O relatório tem três páginas. Cada guia na parte inferior do relatório representa uma página diferente.

    ![Três guias na parte inferior](media/sample-customer-profitability/power-bi-report-tabs.png)

    * **Scorecard da Equipe** enfoca o desempenho dos cinco gerentes e seus registros de negócios.
    * **Análise de Margem do Setor** fornece uma maneira de analisar a rentabilidade comparado ao que está acontecendo em todo o setor.
    * **Scorecard Executivo** fornece uma visão de cada um dos gerentes formatada para exibição na Cortana.

### <a name="team-scorecard-page"></a>Página de pontuação da equipe
![Página do relatório Scorecard da Equipe](media/sample-customer-profitability/customer2.png)

Vejamos os dois membros da equipe em detalhes e quais informações podem ser obtidas: 

1. Na segmentação **Executivo** à esquerda, selecione nome de Andrew para filtrar a página do relatório e exibir apenas os dados sobre ele:

   * Para um KPI rápido, examine o **Status de Receita (Total do Ano)** ; está verde, o que significa que ele tem um bom desempenho.
   * O gráfico **% de Variação da Receita do Orçamento por Mês e Executivo** mostra que, exceto por uma queda em fevereiro, Andrew está indo bem. A região mais dominante de Andrew é o leste e ele lida com 49 clientes e com cinco de sete produtos. O percentual de GM de Andrew não é o mais alto nem o mais baixo.
   * O gráfico **RevenueTY e % de Receita Var para Orçamento por Mês** mostra um histórico de lucratividade estável. No entanto, se filtrar selecionando o quadrado referente a **Central** no mapa de árvore da região, você descobrirá que Andrew tem receita apenas em março e apenas em Indiana. Essa tendência é intencional ou é algo que precisa ser examinado?

2. Agora a diante com Valery. Na segmentação **Executivo**, selecione nome de Valery para filtrar a página do relatório e exibir apenas os dados sobre ela. 

   ![Dados de Valery](media/sample-customer-profitability/customer3.png)

   * Observe o KPI vermelho para **Status de Receita (Total do Ano)** . Este item definitivamente precisa de mais investigação.
   * A variação de receita também mostra um cenário preocupante – ela não está alcançando suas margens de receita.
   * Valery tem apenas nove clientes, lida com apenas dois produtos e trabalha quase exclusivamente com clientes da região norte. Essa especialização poderia explicar as amplas flutuações em sua métrica.
   * Selecionar o quadrado **Norte** no mapa de árvore mostra que a margem bruta de Valery na região norte é condizente com sua margem geral.
   * Selecionar outros quadrados de **Receita Total por Região** mostra uma história interessante: o percentual de GM dela varia de 23% a 79%. Os números de sua receita, em todas as regiões, exceto pela região norte, são extremamente sazonais.

3. Continue explorando para descobrir por que área de Valery não apresenta um bom desempenho. Examine as regiões, as outras unidades de negócios e a próxima página do relatório: **Análise de Margem do Setor**.

### <a name="industry-margin-analysis"></a>Análise de Margem do Setor
Esta página de relatório fornece uma fatia diferente dos dados. Examina a margem bruta para todo o setor, dividido por segmento. A diretora financeira usa essa página para comparar as métricas de unidade da empresa e de negócios com as métricas do setor para ajudar a explicar tendências e lucratividade. Você poderia se perguntar por que o gráfico **% de Margem Bruta por Mês e Executivo** está nesta página, já que é específico de uma equipe. Tê-la aqui, nos permite filtrar a página pelo gerente da unidade de negócios.  

![Página de relatório de análise de margem do setor](media/sample-customer-profitability/customer6.png)

1. Como a lucratividade varia por setor? Como os produtos e clientes dividem por setor? Para responder a essas perguntas, selecione um ou mais setores na parte superior esquerda (comece pelo setor CPG). Para limpar o filtro, selecione o ícone de borracha.

2. No gráfico de bolhas **% de Var de Receita para Orçamento, % de GM e RevenueTY por Setor**, a diretora financeira procura as bolhas maiores, porque elas têm o maior impacto na receita. Para ver facilmente o impacto de cada gerente por setor, filtre a página selecionando no nome de cada gerente no gráfico de área.

3. Conforme você seleciona cada gerente no gráfico, observe os seguintes detalhes:
   * A área de Andrew de influência abrange vários setores diferentes com diferentes amplamente % GM (a maioria do lado positivo) e % Var.
   * O gráfico de Annelie é semelhante, exceto pelo fato de que ela se concentra em apenas alguns segmentos de mercado, com foco no segmento Federal e no produto Gladius.
   * Carlos tem um foco claro no segmento de serviços, com bom lucro. Ele aumentou bastante o percentual de variação no segmento de Alta Tecnologia e um novo segmento para ele, Industrial, executado muito bem em relação ao orçamento.
   * Tina trabalha com alguns segmentos e tem o percentual de GM mais alto, mas o tamanho pequeno das suas bolhas mostra que o impacto sobre o resultado da empresa é mínimo.
   * Valery, que é responsável por apenas um produto, trabalha apenas com cinco segmentos de mercado. Sua influência do setor é sazonal, mas sempre produz uma grande bolha, indicando um impacto significativo sobre o resultado da empresa. Os segmentos de setor explicam o desempenho negativo?

### <a name="executive-scorecard"></a>Scorecard Executivo
Esta página está formatada como uma página de resposta da Cortana. Para saber mais, confira [Criar uma página de resposta personalizada para Cortana](service-cortana-answer-cards.md).

## <a name="dig-into-the-data-by-asking-questions-with-qa"></a>Investigue os dados fazendo perguntas em P e R
Para nossa análise, poderia ser útil determinar qual setor gera a maior parte da receita para Valery. Vamos usar P e R.

1. Selecione **Editar relatório** para abrir o relatório no modo de exibição de Edição. O modo de exibição de edição só estará disponível se você for o proprietário do relatório. Este modo de exibição às vezes é chamado de modo de *criador*. Por outro lado, se o relatório foi apenas compartilhado com você, não é possível abri-lo no modo de exibição de Edição.

2.  Na parte superior do painel, selecione **Fazer uma pergunta** para abrir a caixa de pergunta P e R.

    ![Fazer uma pergunta sobre seus dados](media/sample-customer-profitability/power-bi-ask-question.png)

3. Digite *receita total por setor para Valery* na caixa de perguntas. Observe como a visualização atualiza conforme você digita a pergunta.

    ![Digite a pergunta na caixa de perguntas](media/sample-customer-profitability/power-bi-qna.png)

   Como você pode ver, o setor de Distribuição é a maior área de receita para Valery.

### <a name="dig-deeper-by-adding-filters"></a>Aprofunde-se adicionando filtros
Vamos dar uma olhada no setor de Distribuição.  

1. Abra a página de relatório **Análise de Margem do Setor**.
2. Sem selecionar nenhuma visualização na página do relatório, expanda o painel de filtro à direita (se já não estiver expandido). O painel **Filtros** deve exibir apenas **Filtros de nível de página**.  

   ![Filtros de nível de página](media/sample-customer-profitability/power-bi-filters.png)
3. Localize o filtro para **Setor** e selecione a seta para expandir a lista. Vamos adicionar um filtro de página para o Setor de distribuição. Primeiro, limpe todas as seleções, desmarcando a caixa de seleção **Selecionar tudo**. Em seguida, selecione **Distribuição** somente.  

   ![filtro para distribuição](media/sample-customer-profitability/customer7.png)
4. O gráfico **% de Margem Bruta por Mês e Executivo** informa que apenas Valery e Tina têm clientes neste setor e Valery trabalhou com o setor apenas de junho a novembro.   
5. Selecione **Tina** e, em seguida, **Valery** na legenda do gráfico **Margem Bruta por Mês e Executivo**. Observe que a parte de Tina no gráfico **Receita Total por Produto** é muito pequena se comparada à de Valery.
6. Para ver a receita real, selecione a caixa de P e R no painel e insira a *receita total por executivo para distribuição por cenário*.  

     ![Digite a pergunta na caixa de pergunta P e R](media/sample-customer-profitability/power-bi-qna2.png)

    Podemos explorar de forma semelhante a outros setores e até mesmo adicionar clientes a nossos visuais para compreender as causas para o desempenho de Valery.

## <a name="next-steps-connect-to-your-data"></a>Próximas etapas: Conecte-se aos seus dados
Esse ambiente é seguro para teste, pois você pode optar por não salvar as alterações. Mas se você salvá-las, sempre é possível selecionar **Obter Dados** para ter uma nova cópia deste exemplo.

Esperamos que este tour tenha mostrado como os painéis, P e R e relatórios do Power BI podem fornecer informações sobre os dados de exemplo. Agora é sua vez – conecte-se aos seus próprios dados. Com o Power BI, é possível se conectar a uma grande variedade de fontes de dados. Para saber mais, confira [Introdução ao serviço do Power BI](service-get-started.md).

