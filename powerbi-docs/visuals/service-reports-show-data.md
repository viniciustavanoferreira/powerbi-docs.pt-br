---
title: Mostrar os dados que foram usados para criar a visualização do Power BI
description: Este documento explica como mostrar os dados usados para criar um visual no Power BI e como exportá-los para um arquivo .csv.
author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/4/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 5417511b12c85cb467c3613671a1e101541c9609
ms.sourcegitcommit: 6272c4a0f267708ca7d38a45774f3bedd680f2d6
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/06/2020
ms.locfileid: "73880634"
---
# <a name="show-the-data-that-was-used-to-create-the-visualization"></a>Mostrar dados que foram usados para criar a visualização
## <a name="show-data"></a>Mostrar dados
Uma visualização do Power BI é construída usando dados dos conjuntos de dados. Se você estiver interessado em ver o que acontece nos bastidores, o Power BI permitirá *exibir* os dados usados para criar o visual. Ao selecionar **Mostrar Dados**, o Power BI exibirá os dados abaixo (ou ao lado) da visualização.

Você também pode exportar os dados usados para criar a visualização como um arquivo .xlsx ou .csv e exibi-los no Excel. Para obter mais informações, consulte [Exportar dados de visualizações do Power BI](power-bi-visualization-export-data.md).

> [!NOTE]
> As opções *Mostrar Dados* e *Exportar Dados* estão disponíveis no serviço do Power BI e no Power BI Desktop. No entanto, o Power BI Desktop fornece uma camada adicional de detalhes; [*Mostrar Registros* exibe as linhas reais do conjunto de dados](../desktop-see-data-see-records.md).
> 
> 

## <a name="using-show-data"></a>Como usar *Mostrar Dados* 
1. No Power BI Desktop, selecione uma visualização para torná-la ativa.

2. Selecione **Mais ações** (...) e escolha **Mostrar dados**. 
    ![exibir opção para Mostrar Dados](media/service-reports-show-data/power-bi-more-action.png)


3. Por padrão, os dados são exibidos abaixo do visual.
   
   ![exibição vertical do visual e de dados](media/service-reports-show-data/power-bi-show-data-below.png)

4. Para alterar a orientação, selecione o layout vertical ![captura de tela pequena do ícone usado para alterar o layout vertical](media/service-reports-show-data/power-bi-vertical-icon-new.png) no canto superior direito da visualização.
   
   ![exibição horizontal do visual e de dados](media/service-reports-show-data/power-bi-show-data-side.png)
5. Para exportar os dados para um arquivo .csv, selecione as elipses e escolha **Exportar dados**.
   
    ![selecionar Exportar dados](media/service-reports-show-data/power-bi-export-data-new.png)
   
    Para obter mais informações sobre como exportar os dados para o Excel, consulte [Exportar dados de visualizações do Power BI](power-bi-visualization-export-data.md).
6. Para ocultar os dados, desmarque **Explorar** > **Mostrar dados**.

## <a name="using-show-records"></a>Como usar Mostrar registros
Também é possível enfocar um registro de dados em uma visualização e detalhar os dados atrás dele. 

1. Para usar **Ver registros**, selecione uma visualização para torná-la ativa. 

2. Na faixa de opções Área de Trabalho, selecione a guia para **Ferramentas visuais** > **Dados/Análise** > **Ver registros**. 

    ![Captura de tela com Ver registros selecionado.](media/service-reports-show-data/power-bi-see-record.png)

3. Selecione um ponto de dados ou linha na visualização. Neste exemplo, selecionamos a quarta coluna da esquerda. O Power BI nos mostra o registro do conjunto de dados para esse ponto de dados.

    ![Captura de tela do único registro do conjunto de dados.](media/service-reports-show-data/power-bi-row.png)

4. Selecione **Voltar para o relatório** para retornar à tela de relatório da Área de Trabalho. 

## <a name="considerations-and-troubleshooting"></a>Considerações e solução de problemas

- Se o botão **Ver registros** na faixa de opções estiver desabilitado e esmaecido, isso significará que a visualização selecionada não oferece suporte a Ver Registros.
- Você não pode alterar os dados na exibição Ver Registros e salvá-los novamente no relatório.
- Não é possível usar Ver Registros quando seu visual usa uma medida calculada.
- Não é possível usar Ver Registros quando você está conectado a um modelo MD (multidimensional) dinâmico.  

## <a name="next-steps"></a>Próximas etapas
[Exportar dados de visualizações do Power BI](power-bi-visualization-export-data.md)    

Mais perguntas? [Experimente a Comunidade do Power BI](https://community.powerbi.com/)

