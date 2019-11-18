---
title: Adicionar hiperlinks (URLs) a uma tabela
description: Este tópico ensina como adicionar hiperlinks (URLs) a uma tabela. Você usa Power BI Desktop para adicionar hiperlinks (URLs) a uma tabela ou matriz. Em seguida, no Serviço do Power BI ou no Power BI Desktop, é possível adicioná-los às suas matrizes e tabelas de relatório.
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 10/29/2019
ms.author: maggies
LocalizationGroup: Visualizations
ms.openlocfilehash: c53ce84610e68280c915d55466bc7cddd3c0cc92
ms.sourcegitcommit: d441d350504f8c6d9e100d229757add6237f0bef
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73060747"
---
# <a name="add-hyperlinks-urls-to-a-table"></a>Adicionar hiperlinks (URLs) a uma tabela
Este tópico ensina como adicionar hiperlinks (URLs) a uma tabela. Você usa Power BI Desktop para adicionar hiperlinks (URLs) a uma tabela ou matriz. Em seguida, no Serviço do Power BI ou no Power BI Desktop, é possível adicioná-los às suas matrizes e tabelas de relatório. 

![Tabela com hiperlinks](media/power-bi-hyperlinks-in-tables/hyperlinkedtable.png)

> [!NOTE]
> É possível criar hiperlinks em [blocos em painéis](service-dashboard-edit-tile.md) e em [caixas de texto em painéis](service-dashboard-add-widget.md) dinamicamente no Serviço do Power BI. Você pode criar hiperlinks em [caixas de texto nos relatórios](service-add-hyperlink-to-text-box.md) dinamicamente no Serviço do Power BI e no Power BI Desktop.
> 

## <a name="to-create-a-hyperlink-in-a-table-or-matrix-using-power-bi-desktop"></a>Para criar um hiperlink em uma tabela ou matriz usando o Power BI Desktop
É possível criar hiperlinks em tabelas e em matrizes no Power BI Desktop, mas não no serviço do Power BI. Também é possível criar hiperlinks no Excel Power Pivot antes de importar a pasta de trabalho no Power BI. Ambos os métodos são descritos abaixo.

## <a name="create-a-table-or-matrix-hyperlink-in-power-bi-desktop"></a>Criar um hiperlink de tabela ou matriz no Power BI Desktop
O procedimento para adicionar um hiperlink depende se você importou os dados ou os conectou usando DirectQuery. Ambos os cenários são descritos abaixo.

### <a name="for-data-imported-into-power-bi"></a>Para dados importados para o Power BI
1. Se o hiperlink ainda não existir como um campo no conjunto de dados, use o Power BI Desktop para adicioná-lo como uma [coluna personalizada](desktop-common-query-tasks.md).
2. Na exibição Dados, selecione a coluna e, na guia **Modelagem**, escolha **Categoria de Dados** no menu suspenso.
   
    ![Lista suspensa de categoria de dados](media/power-bi-hyperlinks-in-tables/pbi_data_category.png)
3. Selecione **URL da Web**.
4. Mude para o modo de exibição de relatório e crie uma tabela ou matriz usando o campo categorizado como uma URL da Web. Os hiperlinks estarão em azul e sublinhados.

    ![Links de azuis e sublinhados](media/power-bi-hyperlinks-in-tables/power-bi-table-with-hyperlinks2.png)

    > [!NOTE]
    > As URLS devem começar com determinados prefixos. Para obter a lista completa, confira [Considerações e solução de problemas](#considerations-and-troubleshooting).
    >
   
1. Se não quiser exibir uma URL longa em uma tabela, você poderá exibir um ícone de hiperlink  ![Ícone de Hiperlink](media/power-bi-hyperlinks-in-tables/power-bi-hyperlink-icon.png) em vez disso. Observe que você não consegue exibir ícones em matrizes.
   
    Selecione o gráfico para torná-lo ativo.

    Selecionar o ícone Formato ![Ícone de Rolo de tinta](media/power-bi-hyperlinks-in-tables/power-bi-paintroller.png) para abrir a guia Formatação.

    Expanda **Valores**, localize o **ícone de URL** e altere-o para **Ativado**.

    ![Ícone da URL Ativar](media/power-bi-hyperlinks-in-tables/power-bi-url-icon-on.png)

1. (Opcional) [Publique o relatório do Power BI Desktop no Serviço do Power BI](/learn/modules/publish-share-power-bi/2-publish-reports) e abra o relatório no Serviço do Power BI. Os hiperlinks funcionarão lá também.

### <a name="for-data-connected-with-directquery"></a>Para dados conectados com DirectQuery
Você não pode criar uma coluna no modo DirectQuery.  No entanto, se seus dados já contêm URLs, você pode transformá-los em hiperlinks.

1. Na exibição Relatório, crie uma tabela usando um campo que contém as URLs.
2. Selecione a coluna e, na guia **Modelagem**, escolha **Categoria de Dados**no menu suspenso.
3. Selecione **URL da Web**. Os hiperlinks estarão em azul e sublinhados.
4. (Opcional) [Publique o relatório do Power BI Desktop no Serviço do Power BI](/learn/modules/publish-share-power-bi/2-publish-reports) e abra o relatório no Serviço do Power BI. Os hiperlinks funcionarão lá também.

## <a name="create-a-table-or-matrix-hyperlink-in-excel-power-pivot"></a>Criar um hiperlink de tabela ou matriz no Excel Power Pivot
Outra maneira de adicionar hiperlinks às tabelas e matrizes do Power BI é criar hiperlinks no conjunto de dados antes de importar/conectar-se ao conjunto de dados no Power BI. Este exemplo usa uma pasta de trabalho do Excel.

1. Abra sua pasta de trabalho no Excel.
2. Selecione a guia **PowerPivot** e, em seguida, escolha **Gerenciar**.
   
   ![Abrir o PowerPivot no Excel](media/power-bi-hyperlinks-in-tables/createhyperlinkinpowerpivot2.png)
1. Quando o PowerPivot for aberto, selecione a guia **Avançado**.
   
   ![Guia Avançado do PowerPivot](media/power-bi-hyperlinks-in-tables/createhyperlinkinpowerpivot3.png)
4. Coloque o cursor na coluna que contém as URLs que você deseja transformar em hiperlinks nas tabelas do Power BI.
   
   > [!NOTE]
   > As URLS devem começar com determinados prefixos. Para obter a lista completa, confira [Considerações e solução de problemas](#considerations-and-troubleshooting).
   > 
   
5. No grupo **Propriedades de relatório** , selecione na lista suspensa **Categoria de dados** e escolha **URL do Web**. 
   
   ![Lista suspensa de categoria de dados no Excel](media/power-bi-hyperlinks-in-tables/createhyperlinksnew.png)

6. No Serviço do Power BI ou no Power BI Desktop, conecte-se a essa pasta de trabalho ou importe-a.
7. Crie uma visualização de tabela que contém o campo de URL.
   
   ![Criar uma tabela no Power BI com o campo de URL](media/power-bi-hyperlinks-in-tables/hyperlinksintables.gif)

## <a name="considerations-and-troubleshooting"></a>Considerações e solução de problemas

As URLS devem começar com uma das seguintes opções:
- http
- https
- -mailto
- file
- ftp
- news
- telnet

P: Posso usar uma URL personalizada como um hiperlink em uma tabela ou matriz?    
R: Não. Você pode usar um ícone de link. Se precisar de texto personalizado para os hiperlinks e a lista de URLs for pequena, use uma caixa de texto.


## <a name="next-steps"></a>Próximas etapas
[Visualizações em relatórios do Power BI](visuals/power-bi-report-visualizations.md)

[Conceitos básicos para designers no serviço do Power BI](service-basic-concepts.md)

Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)

