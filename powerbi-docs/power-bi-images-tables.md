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
ms.openlocfilehash: 2ebbc277f2a269ebaf2d1bdb99f1aa800576b466
ms.sourcegitcommit: ba085b248c54e8fb1fd8eb2bb23a814e3fdd7ff6
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70936483"
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

[Adicionar formas estáticas, caixas de texto e imagens a um relatório](https://docs.microsoft.com/power-bi/guided-learning/visualizations?tutorial-step=11)

[Conceitos básicos para designers no serviço do Power BI](service-basic-concepts.md)

Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)

