---
title: Combinar arquivos (binários) no Power BI Desktop
description: Combinar facilmente fontes de dados de arquivos (binários) no Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/13/2020
ms.author: davidi
LocalizationGroup: Transform and shape data
ms.openlocfilehash: 7840894d123fae1f7e760b15f4756796ef2af16a
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83348633"
---
# <a name="combine-files-binaries-in-power-bi-desktop"></a>Combinar arquivos (binários) no Power BI Desktop

Aqui está uma abordagem poderosa para importar dados para o **Power BI Desktop**: Se você tiver vários arquivos com o mesmo esquema, combine-os em uma única tabela lógica. Essa técnica popular ficou mais conveniente e difundida.

Para iniciar o processo de combinação de arquivos da mesma pasta, selecione **Obter Dados**, escolha **Arquivo** > **Pasta** e selecione **Conectar**.

![Conectar-se ao arquivo da pasta, caixa de diálogo Obter Dados, Power BI Desktop](media/desktop-combine-binaries/combine-binaries_1.png)

Insira o caminho da pasta, selecione **OK**e selecione **Transformar Dados** para ver os arquivos da pasta no Editor do Power Query.

## <a name="combine-files-behavior"></a>Comportamento de combinar arquivos

Para combinar arquivos binários no Editor do Power Query, selecione **Conteúdo** (o primeiro rótulo de coluna) e selecione **Página Inicial** > **Combinar Arquivos**. Você pode também simplesmente selecionar o ícone **Combinar Arquivos** ao lado de **Conteúdo**.

![Comando Combinar Arquivos, Editor do Power Query, Power BI Desktop](media/desktop-combine-binaries/combine-binaries_2a.png)

A transformação *combinar arquivos* se comporta da seguinte maneira:

* A transformação de combinação de arquivos analisa cada arquivo de entrada para determinar o formato de arquivo correto a ser usado, como *texto*, *pasta de trabalho do Excel* ou *arquivo JSON*.
* A transformação permite selecionar um objeto específico do primeiro arquivo, por exemplo, uma pasta de trabalho do Excel, para ser extraído.
  
  ![Caixa de diálogo Combinar arquivos, Editor do Power Query, Power BI Desktop](media/desktop-combine-binaries/combine-binaries_3.png)
* A transformação de combinação de arquivos executa estas ações automaticamente:
  
  * Cria uma consulta de exemplo que executa todas as etapas de extração necessárias em um único arquivo.
  * Cria uma *consulta de função* que parametriza a entrada de arquivo/binário para a *consulta de exemplo*. A consulta de exemplo e a consulta de função são vinculadas, para que as alterações à consulta de exemplo sejam refletidas na consulta de função.
  * Aplica a *função de consulta* à consulta original com binários de entrada, como a consulta *Pasta*. Ela aplica a consulta de função para entradas binárias a cada linha e, em seguida, expande a extração de dados resultante como colunas de nível superior.

    ![Resultados da transformação de combinação de arquivos, Editor do Power Query, Power BI Desktop](media/desktop-combine-binaries/combine-binaries_4.png)

> [!NOTE]
> O escopo de sua seleção em uma pasta de trabalho do Excel afetará o comportamento de combinar binários. Por exemplo, você pode selecionar uma planilha específica para combinar essa planilha ou pode selecionar a raiz para combinar o arquivo completo. Selecionar uma pasta combina os arquivos encontrados nela. 

Com o comportamento da operação de combinar arquivos, você pode combinar facilmente todos os arquivos de determinada pasta com facilidade, desde que tenham o mesmo tipo de arquivo e estrutura (por exemplo, as mesmas colunas).

Além disso, também é possível aplicar etapas de transformação ou extração adicionais de forma fácil modificando a consulta de exemplo criada automaticamente, sem precisar se preocupar em modificar ou criar outras etapas da consulta de função. As alterações na consulta de exemplo são geradas automaticamente na consulta de função vinculada.

## <a name="next-steps"></a>Próximas etapas

Há muitos tipos de dados aos quais você pode se conectar por meio do Power BI Desktop. Para saber mais sobre fontes de dados, confira os seguintes recursos:

* [O que é o Power BI Desktop?](../fundamentals/desktop-what-is-desktop.md)
* [Fontes de dados no Power BI Desktop](../connect-data/desktop-data-sources.md)
* [Formatar e combinar dados com o Power BI Desktop](../connect-data/desktop-shape-and-combine-data.md)
* [Conectar-se a arquivos CSV no Power BI Desktop](../connect-data/desktop-connect-csv.md)
* [Inserir dados diretamente no Power BI Desktop](../connect-data/desktop-enter-data-directly-into-desktop.md)
