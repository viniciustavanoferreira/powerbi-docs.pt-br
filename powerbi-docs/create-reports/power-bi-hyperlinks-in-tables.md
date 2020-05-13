---
title: Adicionar hiperlinks (URLs) a uma tabela ou matriz
description: Este tópico ensina a adicionar hiperlinks (URLs) a uma tabela. Use o Power BI Desktop para adicionar hiperlinks (URLs) a um conjunto de dados. Em seguida, no Power BI Desktop ou no serviço do Power BI, é possível adicionar esses hiperlinks às suas matrizes e tabelas de relatório.
author: maggiesMSFT
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 02/13/2020
ms.author: maggies
LocalizationGroup: Visualizations
ms.openlocfilehash: 6b98e99191363c6a33aa4ee99adff2ab72f48641
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83344815"
---
# <a name="add-hyperlinks-urls-to-a-table-or-matrix"></a>Adicionar hiperlinks (URLs) a uma tabela ou matriz
Este tópico ensina a adicionar hiperlinks (URLs) a uma tabela. Use o Power BI Desktop para adicionar hiperlinks (URLs) a um conjunto de dados. É possível adicionar esses hiperlinks às suas matrizes e tabelas de relatório no serviço do Power BI ou no Power BI Desktop. Em seguida, você pode exibir a URL ou um ícone de link ou formatar outra coluna como texto de link.

![Tabela com hiperlinks](media/power-bi-hyperlinks-in-tables/power-bi-url-link-text.png)

Você também pode criar hiperlinks em [caixas de texto nos relatórios](service-add-hyperlink-to-text-box.md) no serviço do Power BI e no Power BI Desktop. E, no serviço do Power BI, é possível adicionar hiperlinks a [blocos em painéis](service-dashboard-edit-tile.md) e a [caixas de texto em painéis](service-dashboard-add-widget.md). 


## <a name="format-a-url-as-a-hyperlink-in-power-bi-desktop"></a>Formatar uma URL como hiperlink no Power BI Desktop

É possível formatar um campo com URLs como hiperlinks no Power BI Desktop, mas não no serviço do Power BI. Também é possível [formatar hiperlinks no Excel Power Pivot](#create-a-table-or-matrix-hyperlink-in-excel-power-pivot) antes de importar a pasta de trabalho no Power BI.

1. No Power BI Desktop, se ainda não houver um campo com um hiperlink em seu conjunto de dados, adicione-o como uma [coluna personalizada](../transform-model/desktop-common-query-tasks.md).

    > [!NOTE]
    > Você não pode criar uma coluna no modo DirectQuery.  No entanto, se seus dados já contêm URLs, você pode transformá-los em hiperlinks.

2. Na exibição de Dados ou de Relatório, selecione a coluna. 

3. Na guia **Modelagem**, selecione **Categoria de Dados** > **URL da Web**.
   
    ![Lista suspensa de categoria de dados](media/power-bi-hyperlinks-in-tables/power-bi-format-web-url.png)

    > [!NOTE]
    > As URLS devem começar com determinados prefixos. Confira [Considerações e solução de problemas](#considerations-and-troubleshooting) neste artigo para obter a lista completa.

## <a name="create-a-table-or-matrix-with-a-hyperlink"></a>Criar uma tabela ou matriz com um hiperlink

1. Depois de [formatar um hiperlink como uma URL](#format-a-url-as-a-hyperlink-in-power-bi-desktop), alterne para a exibição de Relatório.
2. Crie uma tabela ou matriz com o campo que você categorizou como uma URL da Web. Os hiperlinks estão em azul e sublinhados.

    ![Links de azuis e sublinhados](media/power-bi-hyperlinks-in-tables/power-bi-url-blue-underline.png)


## <a name="display-a-hyperlink-icon-instead-of-a-url"></a>Exibir um ícone de hiperlink em vez de uma URL

Se não quiser exibir uma URL longa em uma tabela, você poderá exibir um ícone de hiperlink ![Ícone de Hiperlink](media/power-bi-hyperlinks-in-tables/power-bi-hyperlink-icon.png) em vez disso. 

> [!NOTE]
> Não é possível exibir ícones em uma matriz.
   
1. Primeiro, [crie uma tabela com um hiperlink](#create-a-table-or-matrix-with-a-hyperlink).

2. Selecione a tabela para torná-la ativa.

    Selecione o ícone **Formato** ![ícone rolo de pintura](media/power-bi-hyperlinks-in-tables/power-bi-paintroller.png) para abrir a guia Formato.

    Expanda **Valores**, localize o **ícone de URL** e altere-o para **Ativado**.

    ![Ícone da URL Ativar](media/power-bi-hyperlinks-in-tables/power-bi-url-icon-on.png)

1. (Opcional) [Publique o relatório](desktop-upload-desktop-files.md) do Power BI Desktop no serviço do Power BI. Quando você abre o relatório no serviço do Power BI, os hiperlinks também funcionam.

## <a name="format-link-text-as-a-hyperlink"></a>Formatar o texto do link como hiperlink

Você também pode formatar outro campo em uma tabela como hiperlink e não ter uma coluna para a URL. Nesse caso, você não formata a coluna como uma URL da Web.

> [!NOTE]
> Não é possível formatar outro campo como hiperlink em uma matriz.

1. Se ainda não houver um campo como um hiperlink no conjunto de dados, use o Power BI Desktop para adicioná-lo como uma [coluna personalizada](../transform-model/desktop-common-query-tasks.md). De novo, você não pode criar uma coluna no modo DirectQuery.  No entanto, se seus dados já contêm URLs, você pode transformá-los em hiperlinks.

2. Na exibição de Dados ou de Relatório, selecione a coluna que contém a URL. 

3. Na guia **Modelagem**, selecione **Categoria de Dados**. Verifique se a coluna está formatada como **Não categorizado**.

2. Na exibição de Relatório, crie uma tabela ou uma matriz com a coluna da URL e a coluna que você pretende formatar como texto de link.

3. Com a tabela selecionada, selecione o ícone **Formato** ![ícone rolo de pintura](media/power-bi-hyperlinks-in-tables/power-bi-paintroller.png) para abrir a guia Formato.

4. Expanda **Formatação condicional**, certificando-se de que o nome na caixa seja a coluna que você quer como texto do link. Localize a **URL da Web** e altere-a para **Ativado**.

    ![URL da Web de formatação condicional](media/power-bi-hyperlinks-in-tables/power-bi-format-conditional-web-url.png)

    > [!NOTE]
    > Caso você não veja a opção **URL da Web**, verifique se a coluna que contém os hiperlinks *não* está formatada como **URL da Web** na caixa suspensa **Categoria de Dados**.

5. Na caixa de diálogo **URL da Web**, selecione o campo que contém a URL na caixa **Com base no campo** > **OK**.

    ![Caixa de diálogo URL da Web](media/power-bi-hyperlinks-in-tables/power-bi-format-web-url-dialog.png)

    Agora, o texto nessa coluna está formatado como o link.

    ![Texto formatado como hiperlink](media/power-bi-hyperlinks-in-tables/power-bi-url-link-text.png)

1. (Opcional) [Publique o relatório](desktop-upload-desktop-files.md) do Power BI Desktop no serviço do Power BI. Quando você abre o relatório no serviço do Power BI, os hiperlinks também funcionam.

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
   
5. No grupo **Propriedades de relatório**, selecione na lista suspensa **Categoria de dados** e escolha **URL do Web**. 
   
   ![Lista suspensa de categoria de dados no Excel](media/power-bi-hyperlinks-in-tables/createhyperlinksnew.png)

6. No serviço do Power BI ou no Power BI Desktop, conecte-se ou importe essa pasta de trabalho.
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
[Visualizações em relatórios do Power BI](../visuals/power-bi-report-visualizations.md)

[Conceitos básicos para designers no serviço do Power BI](../fundamentals/service-basic-concepts.md)

Mais perguntas? [Experimente a Comunidade do Power BI](https://community.powerbi.com/)
