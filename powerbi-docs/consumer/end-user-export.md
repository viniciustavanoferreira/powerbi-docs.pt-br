---
title: Exportar dados de um visual do Power BI
description: Exporte dados de um visual de relatório e visual de painel e exiba-os no Excel.
author: mihart
ms.reviewer: cmfinlan
featuredvideoid: jtlLGRKBvXY
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 02/20/2020
ms.author: mihart
LocalizationGroup: Consumers
ms.openlocfilehash: 6f653bd14f71d0d8409dbb8c3653515198cc6c40
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83279447"
---
# <a name="export-data-from-a-visual"></a>Exportar dados de um visual

[!INCLUDE[consumer-appliesto-yyny](../includes/consumer-appliesto-yyny.md)]

[!INCLUDE [power-bi-service-new-look-include](../includes/power-bi-service-new-look-include.md)]

Se desejar ver os dados usados para criar um visual, [você poderá exibi-los no Power BI](end-user-show-data.md) ou exportá-los para o Excel. A opção de exportação de dados requer um determinado tipo de licença e permissões de edição ao conteúdo. Se não for possível exportar, verifique com o administrador do Power BI. A exportação de dados exige uma licença do Power BI Pro, uma licença de usuário Pro, ou uma licença de usuário Pro, nas organizações que tenham licença com a capacidade Premium. Normalmente, esse tipo de licença é usado por *designers*, mas não por *consumidores* de relatórios. Para saber mais, veja o tópico [Qual licença eu tenho?](end-user-license.md)


## <a name="from-a-visual-on-a-power-bi-dashboard"></a>A partir de um visual em um painel do Power BI

1. Comece em um painel do Power BI. Aqui estamos usando o painel do aplicativo ***Exemplo de Vendas e marketing***. Você pode [baixar esse aplicativo em AppSource.com](https://appsource.microsoft.com/en-us/product/power-bi/microsoft-retail-analysis-sample.salesandmarketingsample
).

    ![Painel do aplicativo](media/end-user-export/power-bi-dashboards.png)

2. Passe o mouse sobre um visual para revelar **Mais opções** (...) e clique para exibir o menu de ação.

    ![Menu que aparece quando as reticências são selecionadas](media/end-user-export/power-bi-options-menu.png)

3. Selecione **Exportar para .csv**.

4. O que acontece em seguida depende do navegador que você está usando. Você pode ser solicitado a salvar o arquivo ou pode ver um link para o arquivo exportado na parte inferior do navegador. 

    ![Navegador Chrome mostrando o link de arquivo exportado](media/end-user-export/power-bi-dashboard-exports.png)

5. Abra o arquivo no Excel. 

    > [!NOTE]
    > Caso você não tenha permissões nos dados, não poderá exportá-los nem os abrir no Excel.  

    ![Acumulado do Total de Unidades no Excel](media/end-user-export/power-bi-excel.png)


## <a name="from-a-visual-in-a-report"></a>A partir de um visual em um relatório
Você pode exportar dados de um visual em um relatório como formato .csv ou .xlsx (Excel). 

1. Em um painel, selecione um bloco para abrir o relatório subjacente.  Neste exemplo, estamos selecionando o mesmo visual mostrado acima, *% da Variação Acumulada do Total de Unidades*. 

    ![Bloco do painel realçado](media/end-user-export/power-bi-export-reports.png)

    Como esse bloco foi criado no relatório *Exemplo de Vendas e marketing*, esse é o relatório aberto. E ele é aberto na página que contém o visual do bloco selecionado. 

2. Selecione o visual no relatório. Observe o painel **Filtros** à direita. Esse visual tem filtros aplicados. Para saber mais sobre filtros, confira [Usar filtros em um relatório](end-user-report-filter.md).

    ![Painel de filtro selecionado](media/end-user-export/power-bi-export-filter.png)


3. Selecione **Mais opções (...)** no canto superior direito da visualização. Escolha **Exportar dados**.

    ![Opção Exportar dados selecionada no menu suspenso](media/end-user-export/power-bi-export-report.png)

4. Você verá opções para exportar Dados resumidos ou Dados subjacentes. Se você estiver usando o aplicativo *Exemplo de vendas e marketing*, **Dados subjacentes** será desabilitada. Mas você pode encontrar relatórios onde ambas as opções estão habilitadas. Veja a seguir uma explicação da diferença.

    **Dados resumidos**: selecione essa opção se quiser exportar dados do que você vê atualmente no visual.  Esse tipo de exportação mostra somente os dados que foram usados para criar o estado atual do visual. Se o visual tiver filtros aplicados, os dados exportados também serão filtrados. Por exemplo, para esse visual, sua exportação incluirá apenas dados de 2014 e da região central, e apenas dados para quatro dos fabricantes: VanArsdel, Natura, Aliqui e Pirum. Se o visual tiver agregações (soma, média etc.), a exportação também será agregada. 
  

    **Dados subjacentes**: selecione essa opção se quiser exportar dados para o que você vê no visual **mais** dados adicionais do conjunto de dados subjacente.  Isso pode incluir dados contidos no conjunto de dados, mas não usados no visual. Se o visual tiver filtros aplicados, os dados exportados também serão filtrados.  Se o visual tiver agregações (soma, média etc.), a exportação removerá a agregação, essencialmente, nivelando os dados. 

    ![Menu onde você escolhe dados subjacentes ou resumidos](media/end-user-export/power-bi-export-underlying.png)

5. O que acontece em seguida depende do navegador que você está usando. Você pode ser solicitado a salvar o arquivo ou pode ver um link para o arquivo exportado na parte inferior do navegador. 

    ![Arquivo exportado sendo exibido no navegador Microsoft Edge](media/end-user-export/power-bi-export-edge-browser.png)

    > [!NOTE]
    > Caso você não tenha permissões nos dados, não poderá exportá-los nem os abrir no Excel.  


6. Abra o arquivo no Excel. Compare a quantidade de dados exportados com os dados que exportamos do mesmo visual no painel. A diferença é que essa exportação inclui **Dados subjacentes**. 

    ![Exemplo do Excel](media/end-user-export/power-bi-underlying.png)

## <a name="next-steps"></a>Próximas etapas

[Exibir os dados usados para criar um visual](end-user-show-data.md)