---
title: Alterar como um gráfico é classificado em um relatório
description: Altere como um gráfico é classificado em um relatório do Power BI
author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: how-to
ms.date: 06/25/2020
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: 10db78c01ea074e2b3fab71715a3df92ae207f8e
ms.sourcegitcommit: e8b12d97076c1387088841c3404eb7478be9155c
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85782503"
---
# <a name="change-how-a-chart-is-sorted-in-a-power-bi-report"></a>Altere como um gráfico é classificado em um relatório do Power BI

[!INCLUDE[consumer-appliesto-ynnn](../includes/consumer-appliesto-ynnn.md)]


> [!IMPORTANT]
> **Este artigo é destinado a usuários do Power BI que não têm permissões de edição no relatório ou no conjunto de dados e que trabalham apenas na versão online do Power BI (o serviço do Power BI). Se você é um *designer* de relatórios, *administrador* ou *proprietário*, este artigo pode não ter todas as informações de que você precisa. Como alternativa, leia [Classificar por coluna no Power BI Desktop](../create-reports/desktop-sort-by-column.md)** .

No serviço do Power BI, é possível alterar a aparência de um visual classificando-o por diferentes campos de dados. Ao alterar a maneira como você classifica um visual, é possível realçar as informações que você deseja transmitir. Se estiver usando dados numéricos (como valores de vendas) ou dados de texto (como nomes de estado), você pode classificar suas visualizações da forma que quiser. O Power BI oferece muita flexibilidade para a classificação e menus rápidos para você usar. 

Não é possível classificar visuais em um dashboard. Mas, em um relatório do Power BI, você pode classificar a maioria das visualizações por um e, às vezes, dois campos de cada vez. Em determinados tipos de visuais, a classificação não está disponível: mapas de árvore, medidores, mapas etc. 

## <a name="get-started"></a>Introdução

Para começar, abra um relatório que foi compartilhado com você. Selecione um visual (que pode ser classificado) e escolha **Mais ações** (...).  Há três opções de classificação: **Classificação decrescente**, **Classificação crescente** e **Classificar por**. 
    

![gráfico de barras classificado pelo eixo X em ordem alfabética](media/end-user-change-sort/power-bi-more-actions.png)

### <a name="sort-alphabetically-or-numerically"></a>Classificar em ordem alfabética ou numericamente

Os visuais podem ser classificados em ordem alfabética, segundo os nomes textuais das categorias no visual, ou pelos valores numéricos de cada categoria. Por exemplo, este gráfico é classificado alfabeticamente pela categoria **Nome** da loja no eixo X.

![gráfico de barras classificado pelo eixo X em ordem alfabética](media/end-user-change-sort/powerbi-sort-category.png)

É fácil alterar a classificação de uma categoria (nome do repositório) para um valor (vendas por pés quadrados). Selecione **Mais ações** (...) e escolha **Classificar por**. Selecione um valor numérico usado no visual.  Neste exemplo, selecionamos **Vendas por pé quadrado**.

![Captura de tela mostrando a seleção de uma classificação e de um valor](media/end-user-change-sort/power-bi-sort-value.png)

Se necessário, altere a ordem de classificação entre crescente e decrescente.  Selecione **Mais ações** (...) novamente e escolha **Classificação decrescente** ou **Classificação crescente**. O campo usado para classificar ficará em negrito e terá uma barra amarela.

   ![vídeo mostrando a seleção classificar por e depois em ordem crescente, decrescente](media/end-user-change-sort/sort.gif)

> [!NOTE]
> Nem todos os visuais podem ser classificados. Por exemplo, os seguintes visuais não podem ser classificados: mapa de árvore, mapa, mapa coroplético, dispersão, medidor, cartão e cascata.

## <a name="sorting-by-multiple-columns"></a>Classificar por várias colunas
Os dados nesta tabela são classificados por **Número de clientes**.  Sabemos disso por causa da pequena seta abaixo da palavra *Número*. A seta está apontando para baixo, o que significa que a coluna está sendo classificada em ordem *decrescente*.

![captura de tela mostrando a primeira coluna sendo usada para classificação](media/end-user-change-sort/power-bi-sort-first.png)


Para adicionar mais colunas à ordem de classificação, pressione Shift e clique no cabeçalho da coluna que você deseja adicionar em seguida na ordem de classificação. Por exemplo, se você clicar em **Número de clientes** e pressionar Shift enquanto clica em **Receita total**, a tabela será classificada primeiro pelos clientes e, em seguida, pela receita. O contorno vermelho mostra áreas em que a ordem de classificação foi alterada.

![captura de tela mostrando a segunda coluna sendo usada para classificação](media/end-user-change-sort/power-bi-sort-second.png)

Se você pressionar Shift e clicar uma segunda vez na mesma coluna, isso alterará a direção da classificação nessa coluna. Além disso, se você pressionar Shift e clicar em uma coluna adicionada anteriormente à ordem de classificação, isso moverá a coluna para trás na ordem de classificação.


## <a name="saving-changes-you-make-to-sort-order"></a>Salvar as alterações feitas na ordem de classificação
Os relatórios do Power BI retêm os filtros, as segmentações, as classificações e outras alterações de exibição de dados que você faz – mesmo que você esteja trabalhando na [Exibição de leitura](end-user-reading-view.md). Portanto, se você sair de um relatório e retornar mais tarde, suas alterações de classificação serão salvas.  Se você quiser reverter as alterações para as configurações do *designer* do relatório, selecione **Redefinir para padrão** na barra de menus superior. 

![classificação persistente](media/end-user-change-sort/power-bi-reset.png)

No entanto, se o botão **Redefinir para padrão** estiver esmaecido, significará que o *designer* do relatório desabilitou a funcionalidade de salvar (persistir) as alterações.

<a name="other"></a>
## <a name="considerations-and-troubleshooting"></a>Considerações e solução de problemas

### <a name="sorting-using-other-criteria"></a>Classificando o uso de outros critérios
Às vezes, você deseja classificar o visual usando um campo diferente (não incluído no visual) ou outros critérios.  Por exemplo, talvez você queira classificar por mês em ordem sequencial (e não em ordem alfabética) ou talvez queira classificar por números inteiros em vez de por dígitos (exemplo, 0, 1, 9, 20 e não 0, 1, 20, 9).  

Somente a pessoa que projetou o relatório pode fazer essas alterações para você. As informações de contato do *designer* podem ser encontradas ao selecionar o nome do relatório na barra de cabeçalho.

![Lista suspensa mostrando as informações de contato](media/end-user-change-sort/power-bi-contact.png)

Se você é um *designer* e tem permissões de edição de conteúdo, leia [Classificar por coluna no Power BI Desktop](../create-reports/desktop-sort-by-column.md) para saber como atualizar o conjunto de dados e habilitar esse tipo de classificação.

## <a name="next-steps"></a>Próximas etapas
Mais sobre [Visualizações nos relatórios do Power BI](end-user-visualizations.md).

[Power BI – conceitos básicos](end-user-basic-concepts.md)
