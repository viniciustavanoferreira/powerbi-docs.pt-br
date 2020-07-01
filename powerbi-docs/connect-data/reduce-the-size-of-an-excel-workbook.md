---
title: Reduza o tamanho de uma pasta de trabalho do Excel para exibi-lo no Power BI
description: Reduza o tamanho de uma pasta de trabalho do Excel para exibi-lo no Power BI
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 01/10/2019
ms.author: davidi
LocalizationGroup: Data from files
ms.openlocfilehash: 7755834f5d76392f7212073f958d3c4070dcaca7
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85234774"
---
# <a name="reduce-the-size-of-an-excel-workbook-to-view-it-in-power-bi"></a>Reduza o tamanho de uma pasta de trabalho do Excel para exibi-lo no Power BI
Você pode carregar qualquer pasta de trabalho do Excel menor do que 1 GB no Power BI. Uma pasta de trabalho do Excel pode ter duas partes: um modelo de dados e o restante do relatório — conteúdo da planilha principal. Se o relatório atender os seguintes limites de tamanho, você pode salvá-lo no **OneDrive for Business**, conecte-o do Power BI e exiba-o no Excel Online:

* A pasta de trabalho como um todo pode ter até 1 GB.
* O conteúdo da planilha principal pode ter até 30 MB.

## <a name="what-makes-core-worksheet-contents-larger-than-30-mb"></a>O que deixa o conteúdo da planilha principal com mais de 30 MB
Veja a seguir alguns elementos que podem deixar o conteúdo da planilha principal com mais de 30 MB:

* Imagens.
* Células sombreadas. [Remova um formato de sombreamento de célula](https://support.office.com/article/Add-or-change-the-background-color-of-cells-ac10f131-b847-428f-b656-d65375fb815e).
* Planilhas coloridas. [Remova uma tela de fundo de folha](https://support.office.com/article/add-or-remove-a-sheet-background-3577a762-8450-4556-96a2-cc265abc00a8).
* Caixas de texto.
* Clip-art.

Considere remover esses elementos, se possível. 

Se o relatório tiver um modelo de dados, você terá algumas outras opções: 

* Remover dados de planilhas do Excel e armazená-lo no modelo de dados. Consulte "Remover dados de planilhas" abaixo para obter detalhes. 
* [Crie um Modelo de Dados com eficiência de memória](https://support.office.com/article/Create-a-memory-efficient-Data-Model-using-Excel-2013-and-the-Power-Pivot-add-in-951c73a9-21c4-46ab-9f5e-14a2833b6a70) para reduzir o tamanho geral do relatório.

Para fazer essas alterações, você precisa editar a pasta de trabalho no Excel.

Leia mais sobre [limites de tamanho do arquivo para pastas de trabalho do Excel no SharePoint Online](https://support.office.com/article/File-size-limits-for-workbooks-in-SharePoint-Online-9e5bc6f8-018f-415a-b890-5452687b325e).

## <a name="remove-data-from-worksheets"></a>Remover dados das planilhas
Se você importar dados para o Excel da guia Power Query ou os dados do Excel, a pasta de trabalho pode ter os mesmos dados em uma tabela do Excel e no modelo de dados. As tabelas grandes nas planilhas do Excel podem deixar o conteúdo da planilha principal com mais de 30 MB. Remover a tabela no Excel e manter os dados no modelo de dados podem reduzir significativamente o conteúdo da planilha principal do relatório. 

Quando você importar dados para o Excel, siga estas dicas:

* **No Power Query**: Desmarque a caixa **Carregar em planilha**.
  
  Os dados são importados apenas no modelo de dados, sem dados em planilhas do Excel.
* Na guia **Dos Dados do Excel**, se você marcou anteriormente **Tabela** no assistente de importação: vá para **Conexões Existentes** \> clique na conexão \> **Apenas Criar Conexão**. Exclua a tabela ou tabelas criadas durante a importação inicial original.
* **Guia de dados na guia do Excel**: não verificar a **tabela** na caixa **Importar dados** .

## <a name="workbook-size-optimizer"></a>Otimizador de tamanho da pasta de trabalho
Se a sua pasta de trabalho contiver um modelo de dados, você poderá executar o otimizador de tamanho da pasta de trabalho para reduzir o tamanho da pasta de trabalho. [Baixe o Otimizador de Tamanho da Pasta de Trabalho](https://www.microsoft.com/download/details.aspx?id=38793).

## <a name="related-info"></a>Informações relacionadas
[Criar um Modelo de dados eficiente em memória](https://support.office.com/article/Create-a-memory-efficient-Data-Model-using-Excel-2013-and-the-Power-Pivot-add-in-951c73a9-21c4-46ab-9f5e-14a2833b6a70)

[Usar os links do OneDrive for Business no Power BI Desktop](desktop-use-onedrive-business-links.md)

