---
title: Duas maneiras de compartilhar um relatório filtrado do Power BI
description: Aprenda duas maneiras de filtrar um relatório do Power BI e compartilhá-lo com colegas de trabalho em sua organização.
author: maggiesMSFT
manager: kfile
ms.reviewer: lukaszp
featuredvideoid: 0tUwn8DHo3s
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 09/06/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: c5bc8b32ae61870b794875c1d1720cd07dcf97f8
ms.sourcegitcommit: 6a44cb5b0328b60ebe7710378287f1e20bc55a25
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70877721"
---
# <a name="two-ways-to-share-a-filtered-power-bi-report"></a>Duas maneiras de compartilhar um relatório filtrado do Power BI
O *compartilhamento* é uma boa maneira de conceder acesso a algumas pessoas aos dashboards e relatórios. Se você deseja compartilhar uma versão filtrada de um relatório? Talvez um relatório que mostre apenas os dados para uma cidade específica, vendedor ou ano. Tente filtrar um relatório e compartilhá-lo ou criar uma URL personalizada. O relatório é filtrado quando os destinatários o abrem pela primeira vez. Eles poderão remover o filtro modificando a URL. 

![Relatório filtrado](media/service-share-reports/power-bi-share-filter-pane-report.png)

O Power BI também oferece [outras maneiras para colaborar e distribuir seus relatórios](service-how-to-collaborate-distribute-dashboards-reports.md). Com o compartilhamento, você e os destinatários precisarão de uma [licença do Power BI Pro](service-features-license-type.md) ou então o conteúdo precisará estar em uma [capacidade Premium](service-premium-what-is.md). 

## <a name="two-ways-to-filter-a-report"></a>Duas maneiras para filtrar um relatório

Para ambas as técnicas de filtragem, estamos usando o aplicativo de modelo Exemplo de vendas e marketing. Quer testá-lo? Você também pode instalar o [aplicativo de modelo Exemplo de vendas e marketing](https://appsource.microsoft.com/product/power-bi/microsoft-retail-analysis-sample.salesandmarketingsample?tab=Overview).

### <a name="set-a-filter"></a>Definir um filtro

Abra um relatório no [Modo de exibição de edição](consumer/end-user-reading-view.md) e aplique um filtro.

Neste exemplo, estamos filtrando a página Categoria de Acumulado no Ano do aplicativo de modelo Exemplo de vendas e marketing para mostrar apenas valores onde **Região** igual a **Central**. 
 
![Painel de filtro do relatório](media/service-share-reports/power-bi-share-report-filter.png)

Salve o relatório.

### <a name="create-a-filter-in-the-url"></a>Criar um filtro na URL

Quando você adiciona o filtro ao fim da URL da página de relatório, o comportamento é um pouco diferente. A página filtrada parece igual. No entanto, o Power BI adiciona o filtro ao relatório todo e remove os outros valores do painel de filtro.  

Adicione o seguinte ao final da URL da página de relatório:
   
    ?filter=*tablename*/*fieldname* eq *value*
   
O campo deve ser do tipo número, datetime ou cadeia de caracteres. Os valores de *tablename* ou *fieldname* não podem conter espaços.
   
Em nosso exemplo, o nome da tabela é **Área geográfica**, o nome do campo é **Região** e o valor que queremos filtrar é **Central**:
   
    ?filter=Geo/Region eq 'Central'

O navegador adiciona caracteres especiais para representar barras, espaços e apóstrofes, portanto, você acaba com algo parecido com isso:
   
    app.powerbi.com/groups/xxxx/reports/xxxx/ReportSection4d00c3887644123e310e?filter=Geo~2FRegion%20eq%20'Central'

![Relatório com filtro de URL](media/service-share-reports/power-bi-share-report-filter-url.png)

Salve o relatório.

Confira o artigo [Filtrar um relatório usando parâmetros da cadeia de consulta na URL](service-url-filters.md) para obter muito mais detalhes.

## <a name="share-the-filtered-report"></a>Compartilhar o relatório filtrado

1. Quando você [compartilhar o relatório](service-share-dashboards.md), desmarque a caixa de seleção **Enviar notificação por email aos destinatários**.

    ![Caixa de diálogo Compartilhar relatório](media/service-share-reports/power-bi-share-report-dialog.png)

4. Envie o link com o filtro que você criou anteriormente.

## <a name="next-steps"></a>Próximas etapas
* [Maneiras de compartilhar seu trabalho no Power BI](service-how-to-collaborate-distribute-dashboards-reports.md)
* [Compartilhar um dashboard](service-share-dashboards.md)
* Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/).
* Tem comentários? Vá para o [site da comunidade do Power BI](https://community.powerbi.com/) para fazer sugestões.

