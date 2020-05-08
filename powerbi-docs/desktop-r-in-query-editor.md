---
title: Uso do R no Editor do Power Query
description: Uso do R no Editor do Power Query do Power BI Desktop para análise avançada.
author: davidiseminger
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/28/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: a157b674cd96c10081168ac5258e5b2f6145f09d
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/05/2020
ms.locfileid: "77464846"
---
# <a name="use-r-in-power-query-editor"></a>Uso do R no Editor do Power Query

[A linguagem R](https://mran.microsoft.com/documents/what-is-r) é uma linguagem de programação poderosa que muitos estatísticos, cientistas de dados e analistas de dados usam. Você pode usar R no Editor do Power Query do Power BI Desktop para:

* preparar modelos de dados.

* criar relatórios.

* Faça a limpeza de dados, a modelagem de dados avançada e a análise de conjunto de dados, que inclui a conclusão de dados ausentes, previsões, clustering e muito mais.  

## <a name="install-r"></a>Instalar o R

É possível baixar o R gratuitamente na [página de downloads do Revolution R Open](https://mran.revolutionanalytics.com/download/) e no [Repositório CRAN](https://cran.r-project.org/bin/windows/base/).

## <a name="install-mice"></a>Instalar o mice

Como pré-requisito, você precisa instalar a [biblioteca do mice](https://www.rdocumentation.org/packages/mice/versions/3.5.0/topics/mice) em seu ambiente de R. Sem o mice, o código do script de exemplo não funcionará corretamente. O pacote do mice implementa um método para lidar com os dados ausentes.

Para instalar a biblioteca do mice:

1. Inicie o programa R.exe (por exemplo, C:\Arquivos de Programas\Microsoft\R Open\R-3.5.3\bin\R.exe).  

2. Execute o comando install no prompt do R:

   ``` 
   install.packages('mice') 
   ```

## <a name="use-r-in-power-query-editor"></a>Uso do R no Editor do Power Query

Para demonstrar o uso de R no Editor do Power Query, usaremos um conjunto de dados de exemplo de mercado de ações contido em um arquivo.csv e seguiremos as seguintes etapas:

1. [Baixe o arquivo EuStockMarkets_NA.csv](https://download.microsoft.com/download/F/8/A/F8AA9DC9-8545-4AAE-9305-27AD1D01DC03/EuStockMarkets_NA.csv). Lembre-se do local em que você o salvou.

1. Carregue o arquivo no Power BI Desktop. Na guia **Página Inicial**, selecione **Obter Dados** > **Texto/CSV**.

   ![Selecione Texto/CSV](media/desktop-r-in-query-editor/r-in-query-editor_1.png)

1. Selecione o arquivo EuStockMarkets_NA.csv e, em seguida, escolha **Abrir**. Os dados CSV são exibidos na caixa de diálogo **Arquivo de Texto/CSV**.

   ![Selecione o arquivo CSV](media/desktop-r-in-query-editor/r-in-query-editor_2.png)

1. Selecione **Carregar** para carregar os dados do arquivo. Após o Power BI ter carregado os dados, a nova tabela aparecerá no painel **Campos**.

   ![Dados no painel Campos](media/desktop-r-in-query-editor/r-in-query-editor_3.png)

1. Para abrir o Editor do Power Query, na faixa de opções **Página Inicial**, selecione **Editar Consultas**.

   ![Selecionar Editar Consultas](media/desktop-r-in-query-editor/r-in-query-editor_4.png)

1. Na guia **Transformar**, selecione o botão **Executar Script R**. O editor **Executar Script R** é exibido. As linhas 15 e 20 têm dados ausentes, assim como outras linhas que você não pode ver na imagem. As etapas a seguir mostram como o R completa essas linhas para você.

   ![Selecione Executar Script R](media/desktop-r-in-query-editor/r-in-query-editor_5d.png)

1. Para este exemplo, insira o seguinte código de script na caixa **Script** da janela **Executar Script R**. Substitua *&lt;Seu caminho de arquivo&gt;* pelo caminho para EuStockMarkets_NA.csv no sistema de arquivos local, por exemplo, C:/Usuários/John Doe/Documentos/Microsoft/EuStockMarkets_NA.csv.

    ```r
       dataset <- read.csv(file="<Your File Path>/EuStockMarkets_NA.csv", header=TRUE, sep=",")
       library(mice)
       tempData <- mice(dataset,m=1,maxit=50,meth='pmm',seed=100)
       completedData <- complete(tempData,1)
       output <- dataset
       output$completedValues <- completedData$"SMI missing values"
    ```

    > [!NOTE]
    > Talvez você precise substituir uma variável chamada *output* para criar corretamente o conjunto de dados com os filtros aplicados.

7. Selecione **OK**. O Editor do Power Query exibe um aviso sobre a privacidade dos dados.

   ![Aviso de privacidade de dados](media/desktop-r-in-query-editor/r-in-query-editor_6.png)
8. Dentro da mensagem de aviso, selecione **Continuar**. Na caixa de diálogo **Níveis de privacidade** que é exibida, defina todas as fontes de dados como **Público** para que os scripts de R funcionem corretamente no serviço do Power BI. 

   ![Caixa de diálogo Níveis de privacidade](media/desktop-r-in-query-editor/r-in-query-editor_7.png)

   Para obter mais informações sobre as configurações de privacidade e suas implicações, confira [Níveis de privacidade do Power BI Desktop](desktop-privacy-levels.md).

 9. Selecione **Salvar** para executar o script. 

   Observe uma nova coluna no painel **Campos** chamada **completedValues**. Nessa coluna, há alguns elementos de dados ausentes, como nas linhas 15 e 18. Veja como o R lida com isso na próxima seção.

   Com apenas cinco linhas de script de R, o Editor do Power Query preencheu os valores ausentes com um modelo preditivo.

## <a name="create-visuals-from-r-script-data"></a>Criar elementos visuais com base em dados de script R

Agora, podemos criar um visual para ver como o código do script de R com a biblioteca do mice completa os valores ausentes.

![Visual do script de R](media/desktop-r-in-query-editor/r-in-query-editor_8a.png)

Você pode salvar todos os visuais completos em um arquivo .pbix do Power BI Desktop e usar o modelo de dados e os respectivos scripts de R no serviço do Power BI.

> [!NOTE]
> Você pode [baixar um arquivo .pbix](https://download.microsoft.com/download/F/8/A/F8AA9DC9-8545-4AAE-9305-27AD1D01DC03/Complete%20Values%20with%20R%20in%20PQ.pbix) com todas essas etapas concluídas.

Depois de carregar o arquivo .pbix no serviço do Power BI, você precisará executar etapas adicionais para habilitar a atualização de dados de serviço e os visuais atualizados:  

* **Habilitar a atualização agendada para o conjunto de dados**: para habilitar a atualização agendada para a pasta de trabalho que contém seu conjunto de dados com scripts de R, confira [Configurando a atualização agendada](refresh-scheduled-refresh.md). Este artigo também inclui informações sobre gateways pessoais.

* **Instalar um gateway pessoal**: você precisa de um gateway pessoal instalado no computador no qual o arquivo e o R estão localizados. O serviço do Power BI acessa essa pasta de trabalho e renderiza novamente todos os visuais que foram atualizados. Para obter mais informações, confira [Usar gateways pessoais no Power BI](service-gateway-personal-mode.md).

## <a name="limitations"></a>Limitações

Há algumas limitações para consultas que incluem scripts de R criados no Editor do Power Query:

* Todas as configurações de fonte de dados do R devem ser definidas como **públicas**. Todas as outras etapas em uma consulta do Editor do Power Query também devem ser públicas. 

   Para obter as configurações de fonte de dados, no Power BI Desktop, selecione **Arquivo** > **Opções e configurações** > **Configurações de fonte de dados**.

   ![Selecione Configurações de fonte de dados](media/desktop-r-in-query-editor/r-in-query-editor_9.png)

   Na caixa de diálogo **Configurações de fonte de dados**, selecione uma ou mais fontes de dados e, em seguida, selecione **Editar Permissões**. Defina o **Nível de Privacidade** como **Público**.

   ![Caixa de diálogo Configurações de fonte de dados](media/desktop-r-in-query-editor/r-in-query-editor_10.png)  
  
* Para agendar a atualização do conjunto de dados ou dos visuais de R, habilite a atualização agendada e instale um gateway pessoal no computador que contém a pasta de trabalho e o R. 

Há inúmeras coisas que você pode fazer com o R e com consultas personalizadas. Explore e formate seus dados exatamente como você deseja que eles apareçam.

## <a name="next-steps"></a>Próximas etapas

* [Introdução ao R](https://mran.microsoft.com/documents/what-is-r) 

* [Executar scripts do R no Power BI Desktop](desktop-r-scripts.md) 

* [Usar um IDE R externo com o Power BI](desktop-r-ide.md) 

* [Criar visuais usando pacotes de R no serviço do Power BI](service-r-packages-support.md)
