---
title: "Usar rótulos de hierarquia embutida no Power BI Desktop"
description: "Usar rótulos de hierarquia embutida no Power BI Desktop"
services: powerbi
documentationcenter: 
author: davidiseminger
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 09/06/2017
ms.author: davidi
ms.openlocfilehash: 470b25af4ee59542d010d3e649d25da7305319ad
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/15/2017
---
# <a name="use-inline-hierarchy-labels-in-power-bi-desktop"></a>Usar rótulos de hierarquia embutida no Power BI Desktop
O **Power BI Desktop** dá suporte para o uso de **rótulos de hierarquia embutida**, que são o primeiro de dois recursos para melhorar a análise hierárquica. O segundo recurso, que atualmente está em desenvolvimento, é a capacidade de usar rótulos de hierarquia aninhados (fique atento – nossas atualizações ocorrem com frequência).   

## <a name="how-inline-hierarchy-labels-work"></a>Como os rótulos de hierarquia em linha funcionam
Com os rótulos de hierarquia em linha, você pode ver os rótulos de hierarquia quando expande visuais usando o recurso **Expandir Tudo**. Um grande benefício de ver os rótulos de hierarquia é que você também pode optar por **classificar** de acordo com esses diferentes rótulos de hierarquia quando expandir seus dados hierárquicos.

### <a name="using-the-built-in-expand-all-feature-without-sorting-by-hierarchy-labels"></a>Usando o recurso interno Expandir Tudo (sem classificar segundo rótulos de hierarquia)
Antes de vermos os rótulos de hierarquia em linha em ação, vamos analisar o comportamento do recurso **Expandir Tudo** padrão. Fazer isso nos ajudará a compreender (e apreciar) o quanto os rótulos de hierarquia em linha podem ser úteis.

A imagem a seguir mostra um visual de gráfico de barras representando vendas anuais. Quando clica com o botão direito do mouse, você pode escolher **Expandir Tudo**.

![](media/desktop-inline-hierarchy-labels/inlinehierarchy_4.png)

Quando **Expandir Tudo** é selecionado, o visual expande a hierarquia de datas de *Ano* para *Trimestre*, conforme mostrado na imagem a seguir.

![](media/desktop-inline-hierarchy-labels/inlinehierarchy_5.png)

Observe que os rótulos *Ano* e *Trimestre* são exibidos em conjunto... esse esquema de rotulação continua conforme você **Expande Tudo** até o final da hierarquia.

![](media/desktop-inline-hierarchy-labels/inlinehierarchy_6.png)

É assim que a hierarquia interna de *Data*, associada a campos que têm um tipo de dados *data/hora*, se comporta. Vamos para a próxima seção para ver como o novo recurso de rótulos de hierarquia em linha é diferente.

### <a name="using-inline-hierarchy-labels"></a>Usando rótulos de hierarquia em linha
Agora vamos examinar um gráfico diferente – usando dados com hierarquias informais. No visual a seguir, temos um gráfico de barras com **Valor de Vendas**, usando *Cor* como eixo. Nesses dados, *Cor* e *Classe* formam uma hierarquia informal. A partir daqui, você pode selecionar novamente *Expandir Tudo* para fazer o drill down da hierarquia.

![](media/desktop-inline-hierarchy-labels/inlinehierarchy_7.png)

Selecionar **Expandir Tudo** mostra o próximo nível com a exibição embutida dos rótulos de hierarquia. Por padrão, hierarquias embutidas são classificadas pelo valor de medida – nesse caso, **SalesAmount**. Com os rótulos de hierarquia em linha habilitados, você pode optar por classificar os dados pela hierarquia selecionando as reticências no canto superior direito (o **...**) e, em seguida, selecionando **Classificar por > Classe da Cor**, conforme mostrado na imagem a seguir.

![](media/desktop-inline-hierarchy-labels/inlinehierarchy_8.png)

Após **Classe da Cor** ser selecionado, os dados são classificados com base na seleção de hierarquia informal, conforme mostrado na imagem a seguir.

![](media/desktop-inline-hierarchy-labels/inlinehierarchy_9.png)

> [!NOTE]
> O recurso de rótulo de hierarquia embutido ainda não permite que a hierarquia de tempo interna seja classificada por valor; ela é classificada somente pela ordem da hierarquia.
> 
> 

## <a name="troubleshooting"></a>Solução de problemas
É possível que os visuais fiquem travados em um estado de nível de hierarquia em linha expandida. Em alguns casos, você pode perceber que alguns de seus visuais estão travados no modo em que foram expandidos, e nesse caso fazer o drill up não funciona. Isso pode acontecer se você tiver seguido as etapas seguintes (a solução está *abaixo* das etapas):

Etapas que podem fazer com que os visuais fiquem travados em um estado expandido:

1. Você habilita o recurso **rótulo de hierarquia em linha**
2. Você cria alguns visuais com hierarquias
3. Em seguida, você **Expande Tudo** e salva o arquivo
4. Depois, você *desabilita* o **rótulo de hierarquia em linha** e reinicia o Power BI Desktop
5. Você abre o arquivo novamente

Se você tiver executado essas etapas e seus visuais tiverem travado no modo expandido, você pode fazer o seguinte para solucionar o problema:

1. Habilite novamente o recurso **rótulo de hierarquia em linha** e reinicie o Power BI Desktop
2. Abra novamente o arquivo e faça o drill up até a parte superior dos visuais afetados
3. Salve o arquivo
4. Desabilite o recurso **rótulo de hierarquia em linha** e reinicie o Power BI Desktop
5. Abra o arquivo novamente

Você também pode excluir seu visual e criá-lo novamente.
