---
title: Uso do R no Editor do Power Query
description: Uso do R no Editor de Consultas do Power BI Desktop para análise avançada
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 08/14/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: e2a970ecbf7b341d4feaba4e90a862841ba8bb17
ms.sourcegitcommit: f6ac9e25760561f49d4257a6335ca0f54ad2d22e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/16/2019
ms.locfileid: "69560901"
---
# <a name="use-r-in-query-editor"></a>Uso do R no Editor de Consultas

O [**R**](https://mran.microsoft.com/documents/what-is-r) é uma linguagem de programação poderosa que muitos estatísticos, cientistas de dados e analistas de dados usam. Você pode usar o **R** no **Editor de Consultas** do Power BI Desktop para:

* Preparar modelos de dados

* Criar relatórios

* Faça a limpeza de dados, a modelagem de dados avançada e a análise de conjunto de dados, que inclui a conclusão de dados ausentes, previsões, clustering e muito mais.  

## <a name="install-r"></a>Instalar o R

É possível baixar o **R** gratuitamente da [página de download do Revolution Open](https://mran.revolutionanalytics.com/download/) e do [Repositório CRAN](https://cran.r-project.org/bin/windows/base/).

### <a name="install-mice"></a>Instalar o mice

Você precisa ter a [biblioteca **mice**](https://www.rdocumentation.org/packages/mice/versions/3.5.0/topics/mice) instalada em seu ambiente de R. Sem o **mice**, o código do script de exemplo não funcionará corretamente. O pacote da **mice** implementa um método para lidar com os dados ausentes.

Instalar a **mice**:

1. Inicie o programa R.exe (por exemplo, C:\Program Files\Microsoft\R Open\R-3.5.3\bin\R.exe)  

2. Executar o comando de instalação:

   ``` 
   >  install.packages('mice') 
   ```

## <a name="use-r-in-query-editor"></a>Uso do R no Editor de Consultas

Para demonstrar o uso do **R** no **Editor de Consultas**, usaremos um conjunto de dados de exemplo de mercado de ações contido em um arquivo .csv e seguiremos as seguintes etapas:

1. [Baixe o arquivo **EuStockMarkets_NA.csv**](http://download.microsoft.com/download/F/8/A/F8AA9DC9-8545-4AAE-9305-27AD1D01DC03/EuStockMarkets_NA.csv). Lembre-se do local em que você o salvou.

1. Carregue o arquivo no **Power BI Desktop**: na faixa de opções **Página Inicial**, selecione **Obter Dados > Texto/CSV**.

   ![](media/desktop-r-in-query-editor/r-in-query-editor_1.png)

1. Salve o arquivo e, em seguida, escolha **Abrir**. Os dados CSV são exibidos na caixa de diálogo **Arquivo de texto/CSV**.

   ![](media/desktop-r-in-query-editor/r-in-query-editor_2.png)

1. Depois que os dados forem carregados, você poderá vê-los no painel **Campos**.

   ![](media/desktop-r-in-query-editor/r-in-query-editor_3.png)

1. Para abrir o **Editor de Consultas**, na faixa de opções **Página Inicial**, selecione **Editar Consultas**.

   ![](media/desktop-r-in-query-editor/r-in-query-editor_4.png)

1. Na faixa de opções **Transformar**, selecione o botão **Executar o Script R**. O editor **Executar Script R** é exibido.  

   As linhas 15 e 20 têm dados ausentes, assim como outras linhas que você não pode ver na imagem. As etapas a seguir mostram como o R completa essas linhas para você.

   ![](media/desktop-r-in-query-editor/r-in-query-editor_5d.png)

1. Para este exemplo, insira o código de script a seguir. Substitua "&lt;seu caminho de arquivo&gt;" pelo caminho para **EuStockMarkets_NA.csv** no sistema de arquivos local, por exemplo, C:/Users/John Doe/Documents/Microsoft/EuStockMarkets_NA.csv

    ```r
       dataset <- read.csv(file="<Your File Path>/EuStockMarkets_NA.csv", header=TRUE, sep=",")
       library(mice)
       tempData <- mice(dataset,m=1,maxit=50,meth='pmm',seed=100)
       completedData <- complete(tempData,1)
       output <- dataset
       output$completedValues <- completedData$"SMI missing values"
    ```

7. Ao selecionar **OK**, o **Editor de Consultas** exibirá um aviso sobre a privacidade dos dados.

   ![](media/desktop-r-in-query-editor/r-in-query-editor_6.png)
8. Para que os scripts de R funcionem corretamente no serviço do Power BI, todas as fontes de dados precisam ser definidas como **públicas**. Para obter mais informações sobre as configurações de privacidade e suas implicações, confira [Níveis de privacidade](desktop-privacy-levels.md).

   ![](media/desktop-r-in-query-editor/r-in-query-editor_7.png)

   Depois de selecionar **Salvar**, o script é executado. Observe uma nova coluna no painel **Campos** chamada **completedValues**. Observe que há alguns elementos de dados ausentes, como nas linhas 15 e 18. Veja como o R lida com isso na próxima seção.

   Com apenas cinco linhas de script R, o **Editor de Consultas** preencheu os valores ausentes com um modelo preditivo.

## <a name="create-visuals-from-r-script-data"></a>Criar elementos visuais com base em dados de script R

Agora, podemos criar um visual para ver como o código de script do R preencheu os valores ausentes usando a biblioteca **mice**, conforme mostrado na imagem a seguir:

![](media/desktop-r-in-query-editor/r-in-query-editor_8a.png)

Você pode salvar todos os visuais concluídos em um arquivo .pbix do **Power BI Desktop** e usar o modelo de dados e os respectivos scripts do R no serviço do Power BI.

> [!NOTE]
> Você pode [baixar um arquivo .pbix](http://download.microsoft.com/download/F/8/A/F8AA9DC9-8545-4AAE-9305-27AD1D01DC03/Complete%20Values%20with%20R%20in%20PQ.pbix) com todas essas etapas concluídas.

Depois de carregar o arquivo .pbix no serviço do Power BI, você precisará executar etapas adicionais para habilitar a atualização de dados de serviço e os visuais atualizados:  

* **Habilitar atualização agendada para o conjunto de dados** – para habilitar a atualização agendada para a pasta de trabalho que contém o conjunto de dados com scripts R, confira [Configurar a atualização agendada](refresh-scheduled-refresh.md), que também inclui informações sobre o **Gateway Pessoal**.

* **Instalar o gateway pessoal** – você precisa de um **gateway pessoal** instalado no computador onde o arquivo e o **R** estão localizados. O serviço do Power BI acessa essa pasta de trabalho e renderiza novamente todos os visuais que foram atualizados. Para obter mais informações, confira [instalar e configurar o Gateway Pessoal](service-gateway-personal-mode.md).

## <a name="limitations"></a>Limitações

Existem algumas limitações para consultas que incluem scripts R criados no **Editor de Consultas**:

* Todas as configurações de fonte de dados do R devem ser definidas como **públicas**. Todas as outras etapas em uma consulta do **Editor de Consultas** também devem ser públicas. Para obter as configurações de fonte de dados, no **Power BI Desktop**, selecione **Arquivo > Opções e configurações > Configurações de fonte de dados**.

  ![](media/desktop-r-in-query-editor/r-in-query-editor_9.png)

  Na caixa de diálogo **Configurações de Fonte de Dados**, selecione as fontes de dados e, em seguida, **Editar Permissões...** .  Defina o **Nível de Privacidade** como **Público**.

  ![](media/desktop-r-in-query-editor/r-in-query-editor_10.png)    
* Para habilitar a atualização agendada do conjunto de dados ou dos elementos visuais R, você precisa habilitar a **Atualização agendada** e ter um **Gateway Pessoal** instalado no computador que hospeda a pasta de trabalho e o **R**. Para obter mais informações sobre ambos, confira a seção anterior deste artigo, que fornece links, para saber mais sobre cada um.

Há inúmeras coisas que você pode fazer com R e consultas personalizadas, então, explore e modele seus dados da maneira como deseja que eles sejam mostrados.

## <a name="next-steps"></a>Próximas etapas

* [Introdução ao R](https://mran.microsoft.com/documents/what-is-r) 

* [Executar scripts do R no Power BI Desktop](desktop-r-scripts.md) 

* [Usar um IDE R externo com o Power BI](desktop-r-ide.md) 

* [Pacotes do R no serviço do Power BI](service-r-packages-support.md)
