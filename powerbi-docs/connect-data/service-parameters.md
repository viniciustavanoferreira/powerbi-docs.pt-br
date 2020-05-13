---
title: Editar configurações de parâmetro no serviço do Power BI
description: Os parâmetros de consulta são criados no Power BI Desktop, mas podem ser examinados e atualizados no serviço do Power BI
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 11/21/2018
ms.author: maggies
LocalizationGroup: Create reports
ms.openlocfilehash: 9dad3e306f895e8c8bf2930b8e032ec558f3f7fc
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83308338"
---
# <a name="edit-parameter-settings-in-the-power-bi-service"></a>Editar configurações de parâmetro no serviço do Power BI
Criadores de relatório adicionam parâmetros de consulta a relatórios no Power BI Desktop. Os parâmetros permitem que eles façam que partes dos relatórios dependam de um ou mais *valores* de parâmetro. Por exemplo, um criador de relatórios pode criar um parâmetro que restringe os dados a um único país/região ou um parâmetro que define os formatos aceitáveis para campos como datas, hora e texto.

![Guia Início mostrando a opção Gerenciar parâmetros no Desktop](media/service-parameters/power-bi-manage-parameters.png)

## <a name="review-and-edit-parameters-in-power-bi-service"></a>Revisar e editar parâmetros no serviço do Power BI

Como criador do relatório, você pode definir parâmetros na Área de Trabalho. Quando você [publica o relatório para o serviço do Power BI](../create-reports/desktop-upload-desktop-files.md), as seleções e as configurações de parâmetro vão com ele. Você pode examinar e editar algumas configurações de parâmetro no serviço do Power BI, não os parâmetros que restringem os dados disponíveis, mas os parâmetros que definem e descrevem os valores aceitáveis.

1. No serviço do Power BI, selecione o ícone de engrenagem ![ícone de engrenagem](media/service-parameters/power-bi-cog.png) e escolha **Configurações**.

2. Selecione a guia para os **Conjuntos de dados** e destaque um conjunto de dados na lista. 
    
    ![Janela Configurações com a guia Conjuntos de dados selecionada](media/service-parameters/power-bi-select-dataset2.png)

3. Expanda **Parâmetros**.  Se o conjunto de dados selecionado não tiver parâmetros, você verá uma mensagem com um link para Saiba mais sobre os parâmetros de consulta. No entanto, se o conjunto de dados tiver parâmetros, expandir **Parâmetros** revelará esses parâmetros. 

    ![Janela Configurações com a guia Parâmetros expandida](media/service-parameters/power-bi-settings.png)

    Examine as configurações do parâmetro e faça alterações, se necessário. Campos acinzentados não são editáveis. 


## <a name="next-steps"></a>Próximas etapas
Um modo específico para adicionar parâmetros simples é [modificando a URL](../collaborate-share/service-url-filters.md).