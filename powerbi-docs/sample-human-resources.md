---
title: 'Exemplo de recursos humanos: Faça um tour'
description: 'Exemplo de Recursos Humanos do Power BI: Faça um tour'
author: maggiesMSFT
ms.reviewer: amac
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 07/05/2019
ms.author: maggies
LocalizationGroup: Samples
ms.openlocfilehash: 3f0c95673bd6a9a5af2a828869f38d32440b617a
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/09/2019
ms.locfileid: "73858857"
---
# <a name="human-resources-sample-for-power-bi-take-a-tour"></a>Exemplo de Recursos Humanos do Power BI: Faça um tour

O pacote de conteúdo de exemplo de Recursos Humanos contém um painel, relatório e conjunto de dados para um departamento de recursos humanos. Neste exemplo, o departamento de recursos humanos tem o mesmo modelo de relatório em diferentes empresas, mesmo quando eles diferem em setor ou tamanho. Este exemplo examina novas contratações, funcionários ativos e funcionários que saíram. Ele se esforça para descobrir tendências na estratégia de contratação. Nossos principais objetivos devem entender:

* Quem contratamos
* Desvios em nossa estratégia de contratação
* Tendências nas separações voluntárias

![Painel do exemplo de Recursos Humanos](media/sample-human-resources/hr1.png)

Este exemplo faz parte de uma série que mostra como o Power BI pode ser usado com dados, relatórios e painéis orientados aos negócios. Ele foi criado pela [obviEnce](http://www.obvience.com/) usando dados reais, que foram mantidos anônimos. Os dados estão disponíveis em vários formatos: pacote de conteúdo, arquivo .pbix do Power BI Desktop ou pasta de trabalho do Excel. Confira [Exemplos para o Power BI](sample-datasets.md). 

Este tutorial explora o pacote de conteúdo de exemplo de Recursos Humanos no serviço do Power BI. Como as experiências de relatório são muito semelhantes no Power BI Desktop e no serviço, você também pode acompanhar usando o arquivo de exemplo .pbix no Power BI Desktop. 

Você não precisa de uma licença do Power BI para explorar os exemplos no Power BI Desktop. Se você não tiver uma licença do Power BI Pro, poderá salvar a amostra em Meu Espaço de Trabalho no serviço do Power BI. 

## <a name="get-the-sample"></a>Obter o exemplo

Antes de usar o exemplo, primeiro você deve baixá-lo como um [pacote de conteúdo](#get-the-content-pack-for-this-sample), [arquivo .pbix](#get-the-pbix-file-for-this-sample) ou [pasta de trabalho do Excel](#get-the-excel-workbook-for-this-sample).

### <a name="get-the-content-pack-for-this-sample"></a>Obter o pacote de conteúdo para este exemplo

1. Abra o serviço do Power BI (app.powerbi.com), entre e abra o workspace em que você deseja salvar o exemplo.

   Se você não tiver uma licença do Power BI Pro, poderá salvar a amostra em Meu Espaço de Trabalho.

2. No canto inferior esquerdo, selecione **Obter Dados**.
   
   ![Selecionar Obter Dados](media/sample-datasets/power-bi-get-data.png)
3. Na página **Obter Dados** que aparece, selecione **Exemplos**.
   
4. Selecione o **Exemplo de Recursos Humanos** e, em seguida, escolha **Conectar**.  
   
   ![Conectar-se ao exemplo](media/sample-human-resources/pbi_hr_sample_connect.png)

5. O Power BI importa o pacote de conteúdo e adiciona um novo dashboard, um relatório e um conjunto de dados ao seu workspace atual.
   
   ![Entrada do exemplo de Recursos Humanos](media/sample-human-resources/hr-sample-entry.png)
  
### <a name="get-the-pbix-file-for-this-sample"></a>Obter o arquivo. pbix para este exemplo

Como alternativa, você pode baixar o exemplo de Recursos Humanos como um [arquivo.pbix](https://download.microsoft.com/download/6/9/5/69503155-05A5-483E-829A-F7B5F3DD5D27/Human%20Resources%20Sample%20PBIX.pbix), que é projetado para uso com o Power BI Desktop.

### <a name="get-the-excel-workbook-for-this-sample"></a>Obter a pasta de trabalho do Excel para este exemplo

Se quiser exibir a fonte de dados deste exemplo, ela também está disponível como uma [Pasta de trabalho do Excel](https://go.microsoft.com/fwlink/?LinkId=529780). A pasta de trabalho contém planilhas do Power View que você pode exibir e modificar. Para ver os dados brutos, habilite os suplementos de Análise de Dados e, em seguida, selecione **Power Pivot > Gerenciar**. Para habilitar os suplementos Power View e Power Pivot, confira [Dar uma olhada nos exemplos do Excel dentro do próprio Excel](sample-datasets.md#optional-take-a-look-at-the-excel-samples-from-inside-excel-itself) para obter detalhes.

## <a name="new-hires"></a>Novas contratações
Primeiro, vamos explorar as novas contratações.

1. No seu workspace, selecione a guia **Painéis** e abra o painel **Exemplo de Recursos Humanos**.
2. No painel, selecione o bloco **Contagem de novas contratações, Novas contratações no mesmo período do ano passado, Alteração de % de YoY de funcionários ativos Por mês**.  

   ![Bloco de Contagem de novas contratações](media/sample-human-resources/hr2.png)  

   O relatório de Exemplo de Recursos Humanos é aberto na página **Novas contratações** .  

   ![Página de Novas contratações](media/sample-human-resources/hr3.png)

3. Examine esses itens de interesse:

    * O gráfico de combinação **Contagem de novas contratações, Novas contratações no mesmo período do ano passado, Alteração de % de YoY de funcionários ativos por mês** mostra que contratamos mais pessoas a cada mês neste ano, comparado ao ano passado. Significativamente mais pessoas em alguns meses.
    * No gráfico de combinação **Contagem de novas contratações e Contagem de funcionários ativos por região e etnia**, observe que estamos contratando menos pessoas na região **Leste** .
    * O gráfico de cascata **Var. de YoY de novas contratações por faixa etária** mostra que estamos contratando principalmente pessoas mais jovens. Essa tendência pode ser devido à natureza principalmente de meio período dos trabalhos.
    * O gráfico de pizza **Contagem de novas contratações por gênero** mostra uma divisão praticamente uniforme.

    Você pode encontrar mais informações? Por exemplo, uma região em que a divisão de gênero não é uniforme. 

4. Selecione diferentes faixas etárias e gêneros nos gráficos para explorar as relações entre idade, gênero, região e grupo étnico.

5. Selecione **Exemplo de Recursos Humanos** no painel de navegação superior para retornar ao dashboard.

   ![Retornar ao painel](media/sample-human-resources/power-bi-breadcrumbs.png)

## <a name="compare-currently-active-and-former-employees"></a>Comparar os funcionários atuais e antigos
Vamos explorar os dados de funcionários ativos atuais e funcionários que não trabalham mais na empresa.

1. No painel, selecione o bloco **Contagem de funcionários ativos por faixa etária** .

   ![Bloco da Contagem de funcionários ativos por faixas etárias](media/sample-human-resources/pbi_hr_sample_activepie.png)

   O relatório de Exemplo de Recursos Humanos é aberto na página **Funcionários ativos vs. Separações**.  

   ![Página de funcionários ativos versus separações](media/sample-human-resources/hr5.png)

 2. Examine esses itens de interesse:

    * Os dois gráficos de combinação no lado esquerdo mostraram a alteração de ano a ano para funcionários ativos e separações. Temos mais funcionários ativos deste ano devido a contratação rápida, mas também mais separações do que o último ano.
    * Em agosto tivemos mais separações em comparação a outros meses. Selecione as diferentes faixas etárias, gêneros ou regiões para ver se você consegue encontrar quaisquer exceções.
    * Examinando os gráficos de pizza, observamos que temos uma divisão, até mesmo em nossos funcionários ativos por grupos de idade e gênero. Selecione diferentes faixas etárias para ver como a divisão de gênero é distinta por idade. Temos uma divisão até mesmo por gênero em cada faixa etária?

## <a name="reasons-for-separation"></a>Motivos para separação
Abra novamente no relatório no modo de Exibição de Edição. Você pode alterar os gráficos de pizza para mostrar separações de funcionário em vez de dados de funcionários ativos.

1. Selecione **Editar relatório** no canto superior esquerdo.

2. Selecione o gráfico de pizza **Contagem de funcionários ativos por faixa etária** .

3. Em **Campos**, selecione **Funcionários** para expandir a tabela **Funcionários**. Desmarque **Contagem de Funcionários Ativos** para remover esse campo.

4. Marque **Contagem de separação** na tabela **Funcionários** para adicioná-la à caixa **Valores** na área **Campos**.

5. Na tela do relatório, selecione a barra **Voluntário** no gráfico de barras **Contagem de separações por motivo de separação**. 

   Essa barra realça esses funcionários que deixaram a empresa voluntariamente nos outros visuais do relatório.

6. Selecione a fatia +50 do gráfico de pizza **Contagem de separações por faixa etária**.

7. Examine o gráfico de linhas no canto inferior direito. Este gráfico é filtrado para mostrar separações voluntárias.  

   ![Separações de funcionários acima de 50 anos](media/sample-human-resources/pbi_hr_sample_sepsover50.png)

   Observa a tendência no grupo etário +50. Durante a última parte do ano, mais funcionários acima de 50 anos deixam a empresa voluntariamente. É uma tendência a investigar melhor com mais dados.

8. Você também pode seguir as mesmas etapas para o gráfico de pizza **Contagem de funcionários ativos por gênero**, alterando-o para separações em vez de funcionários ativos. Examine os dados de separação voluntário por gênero para ver se você encontrar quaisquer outras informações.

9. Selecione **Exemplo de Recursos Humanos** no painel de navegação superior para retornar ao dashboard. Você pode optar por salvar as alterações feitas no relatório.

## <a name="bad-hires"></a>Contratações incorretas
A última área para explorar são as contratações incorretas. Contratações incorretas são definidas como funcionários que não duraram mais de 60 dias. Estamos contratando rapidamente, mas são bons candidatos?

1. Selecione o bloco do painel **Contratações incorretas como % de funcionários ativos por faixa etária** . O relatório abre a guia três, **Contratações incorretas**.

   ![Bloco de Contratações incorretas como percentual de funcionários ativos por faixa etária](media/sample-human-resources/hr7.png)  
2. Selecione **Noroeste** na segmentação **Região** à esquerda e **Masculino** no gráfico de rosca **Contagem de Contratações Incorretas por Sexo**. Examine outros gráficos na página **Contratações Incorretas**. Observe que há mais contratações incorretas de homens do que mulheres, em muitas contratações incorretas do Grupo A.

   ![Contratações incorretas no Noroeste](media/sample-human-resources/pbi_hr_sample_badhirespage.png)  

3. Se você examinar o gráfico de rosca **Contagem de contratações incorretas por gênero** e selecionar regiões diferentes na segmentação **Região**, observará que a região Leste é a única região com mais contratações incorretas femininas do que masculinas.  

4. Selecione o nome do dashboard no painel de navegação superior para retornar ao dashboard.

## <a name="ask-a-question-in-the-dashboard-qa-box"></a>Faça uma pergunta na caixa de pergunta P e R do painel
Na [caixa de pergunta P e R](power-bi-tutorial-q-and-a.md) no painel, você poderá fazer uma pergunta sobre seus dados usando linguagem natural. A P e R reconhece as palavras que você digita e descobre onde, em seu conjunto de dados, a resposta será encontrada.

1. Selecione a caixa de pergunta de P e R. Note que mesmo antes de começar a digitar, a P e R exibe sugestões para ajudá-lo a formar sua pergunta.

   ![Sugestões da caixa P e R](media/sample-human-resources/pbi_hr_sample_qabox.png)

2. Você pode escolher uma dessas sugestões ou inserir: *mostrar faixa etária, gênero e contratações incorretas no mesmo período do ano passado na região é leste*.  

   ![Respostas da caixa P e R](media/sample-human-resources/pbi_hr_sample_qa_answer.png)

   Observe que a maioria das contratações incorretas de mulheres estão abaixo de 30 anos.

## <a name="next-steps-connect-to-your-data"></a>Próximas etapas: Conecte-se aos seus dados
Esse ambiente é seguro para teste, pois você pode optar por não salvar as alterações. Mas se você salvá-las, sempre é possível selecionar **Obter Dados** para ter uma nova cópia deste exemplo.

Esperamos que este tour tenha mostrado como os painéis, P e R e relatórios do Power BI podem fornecer informações sobre os dados de exemplo. Agora é sua vez – conecte-se aos seus próprios dados. Com o Power BI, é possível se conectar a uma grande variedade de fontes de dados. Para saber mais, confira [Introdução ao serviço do Power BI](service-get-started.md).
