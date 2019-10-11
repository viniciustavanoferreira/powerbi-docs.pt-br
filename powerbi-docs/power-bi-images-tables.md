---
title: Exibir imagens em uma tabela ou matriz de um relatório
description: No Power BI Desktop, crie uma coluna com hiperlinks para imagens. Em seguida, no Power BI Desktop ou no Serviço do Power BI, adicione esses hiperlinks a uma tabela de relatório, matriz, segmentação ou cartão de várias linhas para exibir a imagem.
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.custom: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 09/11/2019
ms.author: maggies
LocalizationGroup: Visualizations
ms.openlocfilehash: cbb04057c8065e998068dd6520539c830a659f72
ms.sourcegitcommit: d04b9e1426b8544ce16ef25864269cc43c2d9f7b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71715546"
---
# <a name="display-images-in-a-table-matrix-or-slicer-in-a-report"></a>Exibir imagens em uma tabela, matriz ou segmentação de um relatório

Uma boa maneira de aprimorar seus relatórios é adicionar imagens a eles. As imagens estáticas na página são boas para algumas finalidades. Mas, às vezes, você quer que as imagens sejam relacionadas aos dados no seu relatório. Este tópico ensina como exibir imagens em uma tabela, matriz, segmentação ou em um cartão de várias linhas. 

![Imagens de URL em uma tabela](media/power-bi-images-tables/power-bi-url-images-table.png)

## <a name="add-images-to-your-report"></a>Adicionar imagens ao relatório

1. Crie uma coluna com as URLs das imagens. Confira [Considerações](#considerations), mais adiante neste artigo, para obter os requisitos.

1. Selecione essa coluna. Na faixa de opções **Modelagem**, para **Categoria de dados**, selecione a **URL da Imagem**.

    ![Definir Categoria de dados para URL da Imagem](media/power-bi-images-tables/power-bi-set-url-image.png)

1. Adicione a coluna a uma tabela, matriz, segmentação ou a um cartão de várias linhas.

    ![Segmentação com imagens](media/power-bi-images-tables/power-bi-url-images-slicer.png)

## <a name="considerations"></a>Considerações

- A imagem precisa estar em um destes formatos de arquivo: .bmp, .jpg, .jpeg, .gif, .png ou .svg
- A URL precisa ser acessível anonimamente, não em um site que exija uma conexão, como o SharePoint. No entanto, se as imagens estiverem hospedadas no SharePoint ou no OneDrive, você poderá obter um código de inserção que aponte diretamente para elas. 


## <a name="next-steps"></a>Próximas etapas

[Layout e formatação da página](/learn/modules/visuals-in-power-bi/12-formatting)

[Conceitos básicos para designers no serviço do Power BI](service-basic-concepts.md)

Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)

