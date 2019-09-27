---
title: 'Tutorial: Criar um modelo de Machine Learning no Power BI (versão prévia)'
description: Neste tutorial, você cria um modelo de Machine Learning no Power BI.
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.custom: connect-to-services
ms.topic: tutorial
ms.date: 03/29/2019
ms.author: davidi
LocalizationGroup: Connect to services
ms.openlocfilehash: 611d6f6c923e6cb68af94840c4266a0b6dee7651
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "61406165"
---
# <a name="tutorial-build-a-machine-learning-model-in-power-bi-preview"></a>Tutorial: Criar um modelo de Machine Learning no Power BI (versão prévia)

Neste artigo do tutorial, você usa o **Machine Learning Automatizado** para criar e aplicar um modelo de previsão binária no Power BI. O tutorial inclui orientações para a criação de um fluxo de dados do Power BI e o uso das entidades definidas no fluxo de dados para treinar e validar um modelo de machine learning diretamente no Power BI. Em seguida, usamos esse modelo na pontuação para gerar previsões.

Primeiro, você criará um modelo de machine learning de Previsão Binária para prever a intenção de compra de compradores online com base em um conjunto de atributos da sessão online. Usamos um conjunto de dados de machine learning de referência neste exercício. Depois de treinar um modelo, o Power BI gera automaticamente um relatório de validação explicando os resultados do modelo. Em seguida, você pode examinar o relatório de validação e aplicar o modelo aos seus dados para pontuação.

Este tutorial consiste nas seguintes etapas:

> [!div class="checklist"]
> * Criar um fluxo de dados de entrada
> * Criar e treinar um modelo de machine learning
> * Examinar o relatório de validação do modelo
> * Aplicar o modelo a uma entidade de fluxo de dados
> * Usar a saída pontuada do modelo em um relatório do Power BI

## <a name="create-a-dataflow-with-the-input-data"></a>Criar um fluxo de dados de entrada

A primeira parte deste tutorial é criar um fluxo de dados com dados de entrada. Esse processo consiste em algumas etapas, conforme mostrado nas seções a seguir, começando pela obtenção de dados.

### <a name="get-data"></a>Obter dados

A primeira etapa na criação de um fluxo de dados é ter suas fontes de dados prontas. Em nosso caso, usamos um conjunto de dados de machine learning de um conjunto de sessões online, algumas das quais culminaram em uma compra. O conjunto de dados contém um conjunto de atributos sobre essas sessões que usaremos para treinar nosso modelo.

Você pode baixar o conjunto de dados no site UC Irvine.  Para os fins deste tutorial, também temos isso disponível no link a seguir: [online_shoppers_intention.csv](https://raw.githubusercontent.com/santoshc1/PowerBI-AI-samples/master/Tutorial_AutomatedML/online_shoppers_intention.csv).

### <a name="create-the-entities"></a>Criar as entidades

Para criar as entidades em seu fluxo de dados, entre no serviço do Power BI e navegue até um workspace na capacidade dedicada que tenha a versão prévia de IA habilitada.

Se você ainda não tem um espaço de trabalho, pode criar um escolhendo **Espaços de trabalho** no menu de navegação à esquerda no serviço do Power BI e marcando **Criar espaço de trabalho do aplicativo** na parte inferior do painel exibido. Um painel é exibido à direita para inserir os detalhes do espaço de trabalho. Insira um nome para o espaço de trabalho e escolha **Avançado**. Confirme se o espaço de trabalho utiliza a Capacidade dedicada usando o botão de opção e se está atribuído a uma instância de capacidade dedicada que tenha a visualização de IA habilitada. Depois, selecione **Salvar**.

![Criar um workspace](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-01.png)

Após criar o espaço de trabalho, é possível escolher **Ignorar** na parte inferior direita da tela de Boas-vindas, conforme mostrado na imagem a seguir.

![Ignorar se você tem um espaço de trabalho](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-02.png)

Escolha a guia **Fluxos de dados (versão prévia)** . Escolha o botão **Criar** no canto superior direito do espaço de trabalho. Em seguida, escolha **Fluxo de dados**.

![Criar o fluxo de dados](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-03.png)

Selecione **Adicionar novas entidades**. Isso inicia o editor do **Power Query** no navegador.

![Adicionar nova entidade](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-04.png)

Escolha **Arquivo de texto/CSV** como uma fonte de dados, conforme mostrado na imagem a seguir.

![Arquivo de texto/CSV escolhido](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-05.png)

Na opção **Conectar-se a uma Fonte de Dados** que aparece a seguir, cole o link para o arquivo *online_shoppers_intention.csv* na caixa **URL ou caminho do arquivo** e escolha **Avançar**.

`https://raw.githubusercontent.com/santoshc1/PowerBI-AI-samples/master/Tutorial_AutomatedML/online_shoppers_intention.csv`

![Caminho do arquivo](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-06.png)

O Power Query Editor mostra uma versão prévia dos dados do arquivo CSV. Escolha **Transformar tabela** na faixa de opções de comandos e escolha **Usar a primeira linha como cabeçalho** no menu exibido. Isso adiciona a etapa de consulta _Cabeçalhos promovidos_ à seção **Etapas aplicadas** à direita da tela. Você pode renomear a consulta com um nome mais amigável alterando o valor na caixa **Nome** localizada no painel direito. Por exemplo, altere o nome da consulta para _Visitantes online_.

![Alterar para um nome amigável](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-07.png)

Alguns dos tipos de dados de atributo neste conjunto de dados são _numéricos_ ou _Boolianos_, embora possam ser interpretados como cadeias de caracteres pelo **Power Query**. Escolha o ícone do tipo de atributo na parte superior de cada cabeçalho de coluna para alterar as colunas listadas abaixo para os seguintes tipos:

* **Número decimal:** Administrative_Duration; Informational_Duration; ProductRelated_Duration; BounceRates; ExitRates; PageValues; SpecialDay
* **Verdadeiro/Falso:** Weekend; Revenue

![Alterar tipo de dados](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-08.png)

O modelo **Previsão Binária** que treinaremos exige um campo booliano como um rótulo que identifica os resultados das observações anteriores. Nesse conjunto de dados, o atributo _Receita_ indica compra e esse atributo já está disponível como um Booliano. Portanto, não precisamos adicionar uma coluna calculada ao rótulo. Em outros conjuntos de dados, talvez seja necessário transformar os atributos de rótulo existentes em uma coluna booliana.

Escolha o botão **Concluído** para fechar o Power Query Editor. Isso mostra a lista de entidades com os dados de _Visitantes online_  que adicionamos. Escolha **Salvar** no canto superior direito, dê um nome para o fluxo de dados e, em seguida, escolha **Salvar** no diálogo, conforme mostrado na imagem a seguir.

![Salvar o fluxo de dados](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-09.png)

### <a name="refresh-the-dataflow"></a>Atualizar fluxo de dados

Salvar o fluxo de dados resulta na exibição de uma notificação informando que seu fluxo de dados foi salvo. Escolha **Atualizar agora** para utilizar os dados da origem no fluxo de dados.

![Atualizar agora](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-10.png)

Selecione **Fechar** no canto superior direito e aguarde até que a atualização do fluxo de dados termine.

Também é possível atualizar seu fluxo de dados usando os comandos **Ações**. O fluxo de dados exibe o carimbo de data/hora de quando a atualização é concluída.

![Carimbo de data/hora da atualização](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-11.png)

## <a name="create-and-train-a-machine-learning-model"></a>Criar e treinar um modelo de machine learning

Escolha o fluxo de dados após a atualização ser concluída. Para adicionar um modelo de machine learning, selecione o botão **Aplicar modelo ML** na lista **Ações** da entidade base que contém seus dados de treinamento e informações de rótulo e, em seguida, escolha **Adicionar um modelo de machine learning**.

![Adicionar um modelo de machine learning](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-12.png)

A primeira etapa para criar nosso modelo de machine learning é identificar os dados históricos, incluindo o campo de rótulo que você deseja prever. O modelo será criado de acordo com o que foi aprendido com esses dados.

No caso do conjunto de dados que estamos usando, este é o campo **Receita**. Escolha **Receita** como o valor do “Campo de resultado histórico” e, em seguida, escolha **Avançar**.

![Escolher dados históricos](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-13.png)

Em seguida, devemos escolher o tipo de modelo de machine learning a ser criado. O Power BI analisa os valores no campo de resultado histórico que você identificou e sugere os tipos de modelos de machine learning que podem ser criados para prever esse campo.

Nesse caso, como estamos prevendo um resultado binário de um usuário fazer ou não uma compra, escolha **Previsão Binária** para o tipo de modelo e escolha Avançar.

![Previsão binária escolhida](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-14.png)

Em seguida, o Power BI faz uma verificação preliminar dos dados e sugere as entradas que o modelo pode usar. Você tem a opção de personalizar os campos de entrada usados no modelo. Em nosso conjunto de dados coletados, para escolher todos os campos, marque a caixa de seleção ao lado do nome da entidade. Escolha **Avançar** para aceitar as entradas.

![Selecione Avançar](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-15.png)

Na etapa final, devemos dar um nome ao modelo, além de rótulos amigáveis para os resultados que serão usados no relatório gerado automaticamente que resumirá os resultados da validação do modelo. Em seguida, precisamos dar o nome _Previsão de intenção de compra_ ao modelo e os rótulos _Compra_ e _Não compra_ a verdadeiro e falso, respectivamente. Depois, selecione **Salvar**.

![Salvar o modelo](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-16.png)

Nosso modelo de machine learning já está pronto para treinamento. Escolha **Atualizar agora** para começar a treinar o modelo.

![Atualizar agora](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-17.png)

O processo de treinamento começará dando exemplos, normalizando seus dados históricos e dividindo seu conjunto de dados em duas novas entidades *Dados de treinamento da previsão de intenção de compra* e *Dados de teste da previsão de intenção de compra*.

Dependendo do tamanho do conjunto de dados, o processo de treinamento pode levar de alguns minutos a algumas horas. Neste ponto, você pode ver o modelo na guia **Modelos de machine learning** do fluxo de dados. O status _Pronto_ indica que o modelo foi colocado na fila para treinamento ou está em treinamento.

![Pronto para treinamento](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-18.png)

Embora o modelo esteja em treinamento, você não poderá exibir ou editar o fluxo de dados. Pode, entretanto, confirmar que o modelo está sendo treinado e validado por meio do status do fluxo de dados. Isso é exibido como uma atualização de dados em andamento na guia **Fluxos de dados** do espaço de trabalho.

![Em andamento](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-19.png)

Após a conclusão do treinamento do modelo, o fluxo de dados exibe um tempo de atualização corrigido. Você pode confirmar se o modelo está treinado navegando até a guia **Modelos de machine learning** no fluxo de dados. O modelo que você criou deve exibir o status **Treinado** e o horário do **Último treino** já deve estar atualizado.

![Último treino em](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-20.png)

## <a name="review-the-model-validation-report"></a>Examinar o relatório de validação do modelo

Para examinar o relatório de validação do modelo, nos **Modelos de machine learning**, selecione o botão **Exibir o relatório de desempenho e aplicar o modelo** na coluna **Ações** do modelo. Este relatório descreve qual a probabilidade do seu modelo de machine learning ser executado.

Na página **Desempenho do modelo** do relatório, escolha **Principais influenciadores** para exibir os principais indicadores do modelo. Você pode escolher um dos indicadores para ver como a distribuição de resultados está associada a esse indicador.

![Desempenho do modelo](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-21.png)

Usar a segmentação **Limite de probabilidade** na página Desempenho do modelo para examinar sua influência na Precisão e Recall do modelo.

![Limite de probabilidade](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-22.png)

As outras páginas do relatório descrevem as métricas de desempenho estatístico para o modelo.

O relatório também contém uma página Detalhes do Treinamento, que descreve as diferentes iterações executadas, como os recursos foram extraídos das entradas e os hiperparâmetros do modelo final usado.

## <a name="apply-the-model-to-a-dataflow-entity"></a>Aplicar o modelo a uma entidade de fluxo de dados

Selecione o botão **Aplicar modelo** na parte superior do relatório para chamar esse modelo após atualizar o fluxo de dados. Na caixa de diálogo **Aplicar**, especifique a entidade de destino que tem os dados de origem aos quais o modelo deve ser aplicado.

![Aplicar o modelo](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-23.png)

Quando solicitado, você deve **Atualizar** o fluxo de dados para exibir os resultados do modelo.

A aplicação do modelo criará uma nova entidade, com o sufixo **enriched <nome_modelo>** anexado à entidade à qual você aplicou o modelo. No nosso caso, aplicar o modelo à entidade **Visitantes online** criará a **Previsão de intenção de compra enriquecida de Visitantes online**, que inclui a saída prevista do modelo.

A aplicação de um modelo de Previsão Binária adiciona três colunas com resultado previsto, pontuação de probabilidade e os principais influenciadores específicos do registro para a previsão, cada um deles tem um prefixo com o nome da coluna especificado.

![Três colunas de resultados](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-24.png)

Devido a um problema conhecido, as colunas de saída pontuadas na entidade enriquecida só podem ser acessadas no Power BI Desktop. Para visualizá-las no serviço, você deve usar uma entidade de visualização especial.

Após finalizar a conclusão da atualização do fluxo de dados, é possível escolher a entidade **Visualização da previsão de intenção de compra enriquecida de Visitantes online** para visualizar os resultados.

![Exibir os resultados](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-25.png)

## <a name="using-the-scored-output-from-the-model-in-a-power-bi-report"></a>Usar a saída pontuada do modelo em um relatório do Power BI

Para usar a saída pontuada a partir do modelo de machine learning, conecte-se ao fluxo de dados no Power BI Desktop usando o conector Fluxo de dados. A entidade **Previsão de intenção de compra enriquecida de Visitantes online** já pode ser usada para incorporar as previsões a partir do modelo nos relatórios do Power BI.

## <a name="next-steps"></a>Próximas etapas

Neste tutorial, você criou e aplicou um modelo de previsão binária no Power BI usando estas etapas:

* Criar um fluxo de dados de entrada
* Criar e treinar um modelo de machine learning
* Examinar o relatório de validação do modelo
* Aplicar o modelo a uma entidade de fluxo de dados
* Usar a saída pontuada do modelo em um relatório do Power BI

Para saber mais sobre a automação do Microsoft Azure Machine Learning no Power BI, confira [Machine Learning Automatizada no Power BI (versão prévia)](service-machine-learning-automated.md).
