---
title: Usando tabelas calculadas no Power BI Desktop
description: Tabelas calculadas no Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: how-to
ms.date: 05/06/2020
ms.author: davidi
LocalizationGroup: Model your data
ms.openlocfilehash: 3f23f18002ce12c3b6706469f36bde077e117941
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85237874"
---
# <a name="create-calculated-tables-in-power-bi-desktop"></a>Criar tabelas calculadas no Power BI Desktop
Na maioria das vezes, você cria tabelas importando dados para o modelo por meio de uma fonte de dados externa. Porém, as *tabelas calculadas* permitem que você adicione novas tabelas com base nos dados que já carregou no modelo. Em vez de consultar e carregar valores nas colunas da nova tabela por meio de uma fonte de dados, você cria uma fórmula [DAX (Data Analysis Expressions)](/dax/index) que define os valores da tabela.

O DAX é uma linguagem de fórmulas usada para trabalhar com os dados relacionais, como no Power BI Desktop. DAX inclui uma biblioteca de mais de 200 funções, operadores e construtores, fornecendo enorme flexibilidade na criação de fórmulas para calcular os resultados de praticamente qualquer análise de dados exigida. As tabelas calculadas são melhores para cálculos intermediários e para dados que você deseja armazenar como parte do modelo, em vez de cálculos rápidos ou como resultados de uma consulta. Por exemplo, você pode optar entre a *união* convencional ou a *união cruzada* de duas tabelas existentes.

Assim como outras tabelas do Power BI Desktop, as tabelas calculadas podem ter relações com outras tabelas. As colunas da tabela calculada têm tipos de dados, formatação e podem pertencer a uma categoria de dados. Você pode nomear suas colunas como desejar e adicioná-las a uma visualização de relatório, assim como outros campos. As tabelas calculadas serão recalculadas se qualquer uma das tabelas das quais efetuam pull dos dados for atualizada, a menos que a tabela use dados de uma tabela que utilize o DirectQuery. Com o DirectQuery, a tabela refletirá as alterações somente depois que o conjunto de dados for atualizado. Se uma tabela precisar usar o DirectQuery, será melhor ter a tabela calculada no DirectQuery também.

## <a name="create-a-calculated-table"></a>Criar uma tabela calculada

Crie tabelas calculadas usando o recurso **Nova Tabela** na Exibição de Relatório ou na Exibição de Dados do Power BI Desktop.

Por exemplo, imagine que você seja um gerente de pessoal que tenha uma tabela **Northwest Employees** e outra tabela **Southwest Employees**. Você deseja combinar as duas tabelas em uma só tabela chamada **Western Region Employees**.

**Northwest Employees**

 ![](media/desktop-calculated-tables/calctables_nwempl.png)

**Southwest Employees**

 ![](media/desktop-calculated-tables/calctables_swempl.png)

Na Exibição de Relatório ou na Exibição de Dados do Power BI Desktop, no grupo **Cálculos** da guia **Modelagem**, selecione **Nova Tabela**. É um pouco mais fácil fazer isso na Exibição de Dados, pois você pode ver imediatamente a nova tabela calculada.

 ![Nova tabela na Exibição de Dados](media/desktop-calculated-tables/calctables_formulabarempty.png)

Insira a seguinte fórmula na barra de fórmulas:

```dax
Western Region Employees = UNION('Northwest Employees', 'Southwest Employees')
```

Uma tabela chamada **Western Region Employees** será criada e exibida da mesma forma que qualquer outra tabela no painel **Campos**. Você pode criar relações com outras tabelas, adicionar medidas e colunas calculadas e adicionar os campos aos relatórios, assim como você faz com qualquer outra tabela.

 ![Nova tabela calculada](media/desktop-calculated-tables/calctables_westregionempl.png)

 ![Nova tabela no painel Campos](media/desktop-calculated-tables/calctables_fieldlist.png)

## <a name="functions-for-calculated-tables"></a>Funções para tabelas calculadas

Você pode definir uma tabela calculada por qualquer expressão DAX que retorne uma tabela, incluindo uma referência simples a outra tabela. Por exemplo:

```dax
New Western Region Employees = 'Western Region Employees'
```

Este artigo fornece apenas uma breve introdução às tabelas calculadas. Você pode usar tabelas calculadas com o DAX para solucionar muitos problemas analíticos. Estas são algumas das funções mais comuns de tabela DAX que podem ser usadas:

* DISTINCT
* VALUES
* CROSSJOIN
* UNION
* NATURALINNERJOIN
* NATURALLEFTOUTERJOIN
* INTERSECT
* CALENDAR
* CALENDARAUTO

Confira a [Referência de funções DAX](/dax/dax-function-reference) para obter essas e outras funções DAX que retornam tabelas.

