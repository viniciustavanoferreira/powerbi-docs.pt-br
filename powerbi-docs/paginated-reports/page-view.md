---
title: Definir exibições de relatório para relatórios paginados – Power BI
description: Neste artigo, você aprenderá sobre as diferentes exibições de relatório disponíveis para relatórios paginados no serviço do Power BI.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: ''
ms.topic: conceptual
ms.date: 05/14/2020
ms.openlocfilehash: 3816cfe4e1b61b9445e16d7c322c5ba19aa2bc3d
ms.sourcegitcommit: 21b06e49056c2f69a363d3a19337374baa84c83f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83407922"
---
# <a name="set-report-views-for-paginated-reports-in-the-power-bi-service"></a>Definir exibições de relatório para relatórios paginados no serviço do Power BI

Quando você renderiza um relatório paginado no serviço do Power BI, a exibição padrão é baseado em HTML e interativo. Outra exibição de relatório para formatos de página fixa como PDF é a nova opção de Exibição da Página.

**Exibição interativa padrão**

![Exibição padrão](media/page-view/power-bi-paginated-default-view.png)

**Exibição da Página**

![Exibição da Página](media/page-view/power-bi-paginated-page-view.png)

Na Exibição da Página, o relatório renderizado é diferente em comparação com a exibição padrão. Algumas propriedades e conceitos em relatórios paginados se aplicam somente a páginas fixas. A exibição é semelhante a quando o relatório é impresso ou exportado. Você ainda pode alterar alguns elementos, como valores de parâmetro, mas ele não tem outros recursos interativos, como alternâncias e classificação de colunas.

A Exibição da Página dá suporte a todos os recursos compatíveis com o Visualizador de PDF do navegador, como ampliar, reduzir e ajustar à página.

## <a name="switch-to-page-view"></a>Alternar para Exibição da Página

Quando você abre um relatório paginado, ele é renderizado na exibição interativa por padrão. Se o relatório tiver parâmetros, selecione os parâmetros e veja o relatório.

1. Selecione **Exibição** na barra de ferramentas > **Exibição da Página**.

    ![Alternar para Exibição da Página](media/page-view/power-bi-paginated-page-view-dropdown.png)

2. Você pode alterar as configurações da exibição de página selecionando as **Configurações de Página** no menu **Exibição** na barra de ferramentas. 

    ![Selecionar Configurações de Página](media/page-view/power-bi-paginated-page-settings-dropdown.png)
    
    A caixa de diálogo **Configurações de Página** tem opções para definir o **Tamanho da Página** e a **Orientação** para a Exibição da Página. Depois de aplicar as configurações de página, as mesmas opções se aplicarão quando você imprimir a página posteriormente.
   
    ![Caixa de diálogo Configurações de Página](media/page-view/power-bi-paginated-page-settings-dialog.png)

3. Para voltar para a exibição interativa, selecione **Padrão** na caixa suspensa **Exibição**.

## <a name="browser-support"></a>Suporte ao navegador

A Exibição da Página é compatível com os navegadores Google Chrome e Microsoft Edge. Verifique se a exibição de PDFs no navegador está habilitada. Essa é a configuração padrão para esses navegadores.

A Exibição da Página não é compatível com o Internet Explorer nem com o Safari, então a opção está desabilitada. Ela também não é compatível com navegadores em dispositivos móveis nem nos aplicativos móveis nativos do Power BI.  


## <a name="next-steps"></a>Próximas etapas

- [Exibir um relatório paginado no serviço do Power BI](../consumer/paginated-reports-view-power-bi-service.md)
- [O que são os relatórios paginados no Power BI Premium?](paginated-reports-report-builder-power-bi.md)
