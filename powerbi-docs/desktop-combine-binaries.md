---
title: Combinar arquivos (binários) no Power BI Desktop
description: Combinar facilmente fontes de dados de arquivos (binários) no Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 09/26/2019
ms.author: davidi
LocalizationGroup: Transform and shape data
ms.openlocfilehash: 8a5b4c7cb484b296ccab395e18eb2b0089ffd5c7
ms.sourcegitcommit: e2c5d4561455c3a4806ace85defbc72e4d7573b4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71327813"
---
# <a name="combine-files-binaries-in-power-bi-desktop"></a>Combinar arquivos (binários) no Power BI Desktop
Uma abordagem eficiente para a importação de dados no **Power BI Desktop** é combinar vários arquivos, que têm o mesmo esquema, em uma única tabela lógica. Essa abordagem conveniente e popular se tornou mais conveniente e mais expansiva, como descrito neste artigo.

Para iniciar o processo de combinação de arquivos da mesma pasta, selecione **Obter Dados > Arquivo > Pasta**.

![](media/desktop-combine-binaries/combine-binaries_1.png)


## <a name="combine-files-behavior"></a>Comportamento de combinar arquivos
Você pode **combinar arquivos (binários)** selecionando **combinar arquivos** na guia de faixa de opções **Página Inicial** no **Editor de Consultas** ou na própria coluna.

![](media/desktop-combine-binaries/combine-binaries_2a.png)

A transformação **combinar arquivos** se comporta da seguinte maneira:

* A transformação **combinar arquivos** analisa cada arquivo de entrada e determina o formato de arquivo correto a ser usado, como *texto*, *pasta de trabalho do Excel* ou arquivo *JSON*.
* A transformação permite selecionar um objeto específico do primeiro arquivo, por exemplo, uma *pasta de trabalho do Excel*, para ser extraído.
  
  ![](media/desktop-combine-binaries/combine-binaries_3.png)
* Depois, **combinar arquivos** executa automaticamente estas consultas:
  
  * Cria uma consulta de exemplo que executa todas as etapas de extração necessárias em um único arquivo.
  * Cria uma *consulta de função* que parametriza a entrada de arquivo/binário para a *consulta de exemplo*. A consulta de exemplo e a consulta de função são vinculadas, para que as alterações à consulta de exemplo sejam refletidas na consulta de função.
  * Aplica a *consulta de função* à consulta original com binários de entrada (por exemplo, a consulta *Pasta*) para que ela aplique a consulta de função para entradas de binário em cada linha e expanda a extração de dados resultante como colunas de nível superior.
    
    ![](media/desktop-combine-binaries/combine-binaries_4.png)

> [!NOTE]
> O escopo de sua seleção em uma pasta de trabalho do Excel afetará o comportamento de combinar binários. Por exemplo, você pode selecionar uma planilha específica para combinar essa planilha ou pode selecionar a raiz para combinar o arquivo completo. Selecionar uma pasta combina os arquivos encontrados nela. 


Com o comportamento da operação **combinar arquivos**, combine todos os arquivos de determinada pasta com facilidade, desde que eles tenham o mesmo tipo de arquivo e estrutura (por exemplo, as mesmas colunas).

Além disso, aplique etapas de transformação ou extração adicionais de forma fácil modificando a *consulta de exemplo* criada automaticamente, sem precisar se preocupar em modificar ou criar outras etapas da *consulta de função*. As alterações à *consulta de exemplo* são geradas automaticamente na *consulta de função* vinculada.

## <a name="next-steps"></a>Próximas etapas
Há todos os tipos de dados aos quais você pode se conectar usando o Power BI Desktop. Para obter mais informações sobre fontes de dados, confira os seguintes recursos:

* [O que é o Power BI Desktop?](desktop-what-is-desktop.md)
* [Fontes de dados no Power BI Desktop](desktop-data-sources.md)
* [Formatar e combinar dados com o Power BI Desktop](desktop-shape-and-combine-data.md)
* [Conectar-se a arquivos CSV no Power BI Desktop](desktop-connect-csv.md)   
* [Inserir dados diretamente no Power BI Desktop](desktop-enter-data-directly-into-desktop.md)   

