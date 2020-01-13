---
title: Digitalizar um código de barras no aplicativo móvel do Power BI
description: A digitalização de códigos de barras no mundo real o leva para as informações de BI filtradas no aplicativo móvel do Power BI.
author: paulinbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 12/02/2019
ms.author: painbar
ms.openlocfilehash: ee3cfec0c735ad52f9a036e75f61c1ab0400567b
ms.sourcegitcommit: 02b05932a119527f255e1eacc745a257044e392f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/19/2019
ms.locfileid: "75217792"
---
# <a name="scan-a-barcode-with-your-device-from-the-power-bi-mobile-app"></a>Digitalizar um código de barras com seu dispositivo no aplicativo móvel do Power BI
A digitalização de códigos de barras no mundo real o leva para as informações de BI filtradas no aplicativo móvel do Power BI.


Aplica-se a:

| ![iPhone](./media/mobile-apps-quickstart-view-dashboard-report/iphone-logo-30-px.png) | ![Android](./media/mobile-apps-quickstart-view-dashboard-report/android-logo-30-px.png) | 
|:--- |:--- |
| iPhone | Android (celular, tablet) | 

Digamos que um colega tenha [marcado um campo de código de barras em um relatório do Power BI Desktop](../../desktop-mobile-barcodes.md) e compartilhou esse relatório com você. 

![](media/mobile-apps-scan-barcode-iphone/power-bi-barcode-scanner.png)

Quando você digitaliza o código de barras de um produto com o scanner no aplicativo do Power BI no seu dispositivo, você vê o relatório (ou a lista de relatórios) com esse código de barras. Você pode abrir o relatório filtrado nesse código de barras.

## <a name="scan-a-barcode-with-the-power-bi-scanner"></a>Digitalizar um código de barras com o scanner do Power BI
1. Na barra de navegação, toque em **Mais opções** (…) e, em seguida, toque em **Scanner**.

    ![](media/mobile-apps-scan-barcode-iphone/power-bi-scanner.png)

2. Se a câmera não estiver habilitada, você precisa aprovar o aplicativo do Power BI para usar a câmera. Essa é uma única aprovação. 
4. Aponte o scanner para um código de barras em um produto. Você verá uma lista dos relatórios associados a esse código de barras.
5. Toque no nome do relatório para abri-lo no dispositivo, filtrado automaticamente de acordo com esse código de barras.

## <a name="filter-by-other-barcodes-while-in-a-report"></a>Filtrar por outros códigos de barras enquanto estiver em um relatório
Ao observar um relatório filtrado por um código de barras no dispositivo, é recomendável filtrar o mesmo relatório por um código de barras diferente.

* Se o ícone de código de barras tiver um filtro ![](media/mobile-apps-scan-barcode-iphone/power-bi-barcode-filtered-icon-black.png), o filtro estará ativo e o relatório já será filtrado por um código de barras. 
* Se o ícone não contiver um filtro ![](media/mobile-apps-scan-barcode-iphone/power-bi-barcode-unfiltered-icon.png), o filtro não estará ativo e o relatório não será filtrado por um código de barras. 

De qualquer forma, toque no ícone para abrir um pequeno menu com um scanner flutuante.

* Focalize o scanner no novo item para alterar o filtro do relatório para um valor de código de barras diferente. 
* Selecione **Limpar filtro de código de barras** para voltar ao relatório não filtrado.
* Selecione **Filtrar por códigos de barras recentes** para mudar o filtro de relatório para um dos códigos de barras digitalizados na sessão atual.

## <a name="issues-with-scanning-a-barcode"></a>Problemas com a digitalização de um código de barras
Aqui estão algumas mensagens que você poderá ver quando digitalizar um código de barras em um produto.

### <a name="couldnt-filter-report"></a>“Não foi possível filtrar o relatório...”
O relatório que você escolher filtrar baseia-se em um modelo de dados que não inclui esse valor de código de barras. Por exemplo, o produto “água mineral” não está incluído no relatório.  

### <a name="allsome-of-the-visuals-in-the-report-dont-contain-any-value"></a>Todos/alguns dos visuais no relatório não contém nenhum valor
O valor de código de barras digitalizado já existe em seu modelo, mas todos ou alguns dos visuais no relatório não contêm esse valor e, portanto, a filtragem retornará um estado vazio. Tente procurar em outras páginas do relatório ou editar seus relatórios no Power BI Desktop para que ele contenha esse valor 

### <a name="looks-like-you-dont-have-any-reports-that-can-be-filtered-by-barcodes"></a>“Parece que você não tem relatórios que possam ser filtrados por códigos de barras”.
Isso significa que você não tem nenhum relatório habilitado para código de barras. O scanner de código de barras pode filtrar apenas relatórios que têm uma coluna marcada como **Código de barras**.  

Verifique se você ou o proprietário do relatório marcou uma coluna como **Código de barras** no Power BI Desktop. Saiba mais sobre como [marcar um campo de código de barras no Power BI Desktop](../../desktop-mobile-barcodes.md)

### <a name="couldnt-filter-report---looks-like-this-barcode-doesnt-exist-in-the-report-data"></a>“Não foi possível filtrar o relatório – parece que esse código de barras não existe nos dados do relatório.”
O relatório que você escolher filtrar baseia-se em um modelo de dados que não inclui esse valor de código de barras. Por exemplo, o produto “água mineral” não está incluído no relatório. Você poderá digitalizar um produto diferente, escolher outro relatório (se houver mais de um relatório disponível) ou exibir o relatório não filtrado. 

## <a name="next-steps"></a>Próximas etapas
* [Marcar um campo de código de barras no Power BI Desktop](../../desktop-mobile-barcodes.md)
* [Blocos de Dashboard no Power BI](../end-user-tiles.md)
* [Dashboards no Power BI](../end-user-dashboards.md)

