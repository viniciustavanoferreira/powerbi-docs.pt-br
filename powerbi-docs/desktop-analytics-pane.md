---
title: Usar o painel Análise do Power BI Desktop
description: Criar linhas de referência dinâmica para elementos visuais no Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/10/2020
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 4ad843078e452502a94aa7d60b3304528fd25496
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/05/2020
ms.locfileid: "76038834"
---
# <a name="use-the-analytics-pane-in-power-bi-desktop"></a>Usar o painel Análise do Power BI Desktop

Com o painel **Análise** no Power BI Desktop, você pode adicionar *linhas de referência* dinâmicas aos visuais e destacar tendências ou insights importantes. O ícone e o painel **Análise** estão localizados na área **Visualizações** do Power BI Desktop.

![Painel Análise, Visualizações, Power BI Desktop](media/desktop-analytics-pane/analytics-pane_1.png)

> [!NOTE]
> O painel **Análise** só aparece quando você seleciona um visual na tela do Power BI Desktop.

## <a name="search-within-the-analytics-pane"></a>Pesquisar no painel de análise

A partir da versão de fevereiro de 2018 do Power BI Desktop (versão 2.55.5010.201 ou posterior), você poderá pesquisar dentro do painel **Análise**, que é uma subseção do painel **Visualizações**. A caixa de pesquisa é exibida quando você seleciona o ícone **Análise**.

![Caixa de pesquisa, painel Análise, Visualizações, Power BI Desktop](media/desktop-analytics-pane/analytics-pane_1b.png)

## <a name="use-the-analytics-pane"></a>Usar o painel Análise

Com o painel **Análise**, você pode criar os seguintes tipos de linhas de referência dinâmicas:

* Linha constante do eixo X
* Linha constante do eixo Y
* Linha mínima
* Linha máxima
* Linha média
* Linha mediana
* Linha percentil
* Sombreamento de simetria

> [!NOTE]
> Nem todas as linhas estão disponíveis para todos os tipos de visual.

As seções a seguir mostram como você pode usar o painel **Análise** e as linhas de referência dinâmica em suas visualizações.

Para exibir as linhas de referência dinâmica disponíveis para um visual, siga estas etapas:

1. Escolha ou crie um visual e, então, selecione o ícone **Análise** na seção **Visualizações**.

    ![Exibir análise de um visual, painel Visualizações, Power BI Desktop](media/desktop-analytics-pane/analytics-pane_2.png)

2. Selecione o tipo de linha que você deseja criar para expandir as opções. Nesse caso, selecionaremos **Linha média**.

    ![Linha média, painel Análise, visualizações, Power BI Desktop](media/desktop-analytics-pane/analytics-pane_3.png)

3. Para criar uma nova linha, selecione **+&nbsp;Adicionar**. Em seguida, dê um nome à linha. Clique duas vezes na caixa de texto e informe seu nome.

    Agora você tem vários tipos de opções para sua linha. Você pode especificar a **Cor**, o percentual de **Transparência**, o **Estilo da linha** e a **Posição** (em comparação com os elementos de dados do visual). Você também pode escolher se deseja incluir o **Rótulo de dados**. Para especificar a medida visual na qual sua linha deve se basear, selecione a lista suspensa **Medida**, que é preenchida automaticamente com elementos de dados do visual. Aqui, vamos selecionar **Cultura** como a medida, rotulá-la *Média de cultura* e personalizar algumas das outras opções.

    ![Linha média de cultura, painel Análise, visualizações, Power BI Desktop](media/desktop-analytics-pane/analytics-pane_4.png)

4. Se você quer que um rótulo de dados seja exibido, altere **Rótulo de dados** de **Desativado** para **Ativado**. Ao fazer isso, você obterá uma vasta gama de opções adicionais para o rótulo de dados.

    ![Configurações de rótulo de dados, painel Análise, visualizações, Power BI Desktop](media/desktop-analytics-pane/analytics-pane_5.png)

5. Observe o número que aparece ao lado do item **Linha média** no painel **Análise**. Isso indica o número de linhas dinâmicas atualmente presentes no visual, bem como o tipo. Se adicionarmos uma **Linha máxima** a **Acessibilidade**, o painel **Análise** mostrará que agora também temos uma linha de referência dinâmica da **Linha máxima** aplicada a esse visual.

    ![Totais de linha máxima e linha média, painel Análise, visualizações, Power BI Desktop](media/desktop-analytics-pane/analytics-pane_6.png)

Se o visual selecionado não puder ter linhas de referência dinâmica aplicadas a ele (neste caso, um visual de **Mapa**), você verá a mensagem a seguir quando selecionar o painel **Análise**.

![Análise indisponível para um visual de mapa, painel Análise, visualizações, Power BI Desktop](media/desktop-analytics-pane/analytics-pane_7.png)

Você pode destacar muitos insights interessantes pela criação de linhas de referência dinâmicas com o painel **Análise**.

Estamos planejando mais recursos e funcionalidades, incluindo a expansão dos visuais que podem ter linhas de referência dinâmicas aplicadas a eles. Verifique com frequência para ver as novidades.

## <a name="apply-forecasting"></a>Aplicar previsão

Se você tiver dados de tempo em sua fonte de dados, poderá usar o recurso de *previsão*. Basta selecionar um visual e expandir a seção **Previsão** do painel **Análise**. Você pode especificar várias entradas para modificar a previsão, como o **Tamanho da previsão** ou o **Intervalo de confiança**. A imagem a seguir mostra um visual de linha básico com a aplicação de previsão. Use sua imaginação (e experimente com a previsão) para ver como ela pode se aplicar aos seus modelos.

![Recurso de previsão, painel Análise, visualizações, Power BI Desktop](media/desktop-analytics-pane/analytics-pane_8.png)

> [!NOTE]
> O recurso de previsão só está disponível para visuais de gráfico de linhas.

## <a name="limitations"></a>Limitações

A capacidade de usar linhas de referência dinâmica baseia-se no tipo de visual que está sendo usado. As listas a seguir descrevem essas limitações mais especificamente.

Você pode usar *linha constante do eixo X*, *linha constante do eixo Y* e *sombreamento de simetria* no seguinte elemento visual:

* Gráfico de dispersão

O uso de *linha constante*, *linha mínima*, *linha máxima*, *linha média*, *linha mediana* e *linha de percentil* está disponível nestes visuais:

* Gráfico da área
* Gráfico de barras clusterizado
* Gráfico de colunas clusterizado
* Gráfico de linhas
* Gráfico de dispersão

Os elementos visuais a seguir só podem usar uma *linha constante* do painel **Análise**:

* Gráfico de áreas empilhadas
* Gráfico de barras empilhadas
* Gráfico de colunas empilhadas
* Gráfico de cascata
* Gráfico de barras empilhadas 100%
* Gráfico de colunas empilhadas 100%

Os elementos visuais a seguir poderão usar uma *linha de tendência* se houver dados de tempo:

* Gráfico da área
* Gráfico de colunas clusterizado
* Gráfico de linhas
* Gráfico de linhas e colunas clusterizadas

Por fim, não é possível atualmente aplicar linhas dinâmicas a muitos visuais, incluindo (dentre outros):

* Funil
* Gráfico de linhas e colunas clusterizadas
* Gráfico de linhas e colunas empilhadas
* Gráfico da faixa de opções
* Visuais não cartesianos, como gráfico de rosca, medidor, matriz, gráfico de pizza e tabela

A *linha de percentil* só fica disponível com o uso de dados importados no Power BI Desktop, ou quando conectado ao vivo a um modelo em um servidor que está executando o **Analysis Service 2016** ou versão posterior, o **Azure Analysis Services** ou um conjunto de dados no serviço do Power BI.

## <a name="next-steps"></a>Próximas etapas

Você pode fazer de tudo com o Power BI Desktop. Para obter mais informações sobre seus recursos, consulte as seguintes fontes:

* [Novidades no Power BI Desktop](desktop-latest-update.md)
* [Obter o Power BI Desktop](desktop-get-the-desktop.md)
* [O que é o Power BI Desktop?](desktop-what-is-desktop.md)
* [Visão geral de consulta com o Power BI Desktop](desktop-query-overview.md)
* [Tipos de dados no Power BI Desktop](desktop-data-types.md)
* [Formatar e combinar dados com o Power BI Desktop](desktop-shape-and-combine-data.md)
* [Realizar tarefas comuns no Power BI Desktop](desktop-common-query-tasks.md)
