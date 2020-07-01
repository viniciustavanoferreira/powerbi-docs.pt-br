---
title: Títulos com base em expressão no Power BI Desktop
description: Crie títulos dinâmicos no Power BI Desktop que mudam com base em expressões programáticas usando a formatação programática condicional
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: how-to
ms.date: 04/10/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: e3b9e4fd1fea6c1fa76077b95ba6a93225753593
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85222046"
---
# <a name="expression-based-titles-in-power-bi-desktop"></a>Títulos com base em expressão no Power BI Desktop

É possível criar títulos dinâmicos e personalizados para os visuais do Power BI. Ao criar DAX (Expressões de Análise de Dados) com base em campos, variáveis ou outros elementos programáticos, os títulos dos visuais podem ser ajustados automaticamente, conforme o necessário. Essas alterações são baseadas em filtros, seleções ou outras interações e configurações do usuário.

![Captura de tela da opção de formatação condicional do Power BI Desktop](media/desktop-conditional-formatting-visual-titles/expression-based-title-01.png)

Criar títulos dinâmicos, às vezes chamados de *títulos com base em expressão*, é simples. 

## <a name="create-a-field-for-your-title"></a>Criar um campo para o título

Para criar um título com base em expressão, primeiro, crie um campo no modelo, a ser usado para o título. 

Há várias maneiras criativas de fazer com que o título do visual reflita o que você quer dizer ou expressar. Vamos ver alguns exemplos.

É possível criar uma expressão que muda com base no contexto de filtro do nome da marca do produto recebido pelo visual. A imagem a seguir mostra a fórmula DAX de um campo desse tipo.

![Captura de tela da fórmula DAX](media/desktop-conditional-formatting-visual-titles/expression-based-title-02.png)

Outro exemplo é usar um título dinâmico que muda com base no idioma ou na cultura do usuário. É possível criar títulos específicos a um idioma em uma medida DAX por meio da função `USERCULTURE()`. Essa função retorna o código da cultura do usuário, com base no sistema operacional ou nas configurações do navegador dele. É possível usar a seguinte instrução switch de DAX para selecionar o valor traduzido correto. 

```
SWITCH (
  USERCULTURE(),
  "de-DE", “Umsatz nach Produkt”,
  "fr-FR", “Ventes par produit”,
  “Sales by product”
)
```

Outra opção é recuperar a cadeia de caracteres de uma tabela de pesquisa que contém todas as traduções. Coloque essa tabela em seu modelo. 

Esses são apenas alguns exemplos de criação de títulos dinâmicos, com base em expressão, para visuais no Power BI Desktop. Você é livre para usar sua imaginação e criar seus títulos e modelos.


## <a name="select-your-field-for-your-title"></a>Selecionar um campo para o título

Após criar a expressão DAX para o campo criado no modelo, será necessário aplicá-lo ao título do visual.

Para selecionar o campo e aplicá-lo, acesse o painel **Visualizações**. Na área **Formato**, selecione **Título** para ver as opções de título do visual. 

Clique com o botão direito do mouse em **Texto do título** para ver um menu de contexto que permite selecionar **<em>fx</em>Formatação condicional**. Quando você seleciona este item de menu, uma caixa de diálogo **Texto do título** é exibida. 

![Captura de tela da caixa de diálogo Texto do título](media/desktop-conditional-formatting-visual-titles/expression-based-title-02b.png)

Nessa janela, é possível selecionar o campo que você criou para usar no título.

## <a name="limitations-and-considerations"></a>Limitações e considerações

Há algumas limitações à implementação atual de títulos com base em expressão para visuais:

* No momento, a formatação com base em expressão não é compatível com visuais em Python, R ou Key Influencers.
* O campo criado para o título precisa ser um tipo de dados String. Medidas que retornam números ou data/hora (ou qualquer outro tipo de dados) não são compatíveis no momento.
* Os títulos com base em expressão não são transferidos quando você fixa um visual em um dashboard.

## <a name="next-steps"></a>Próximas etapas

Este artigo descreveu como criar expressões DAX que transformam títulos de visuais em campos dinâmicos que mudam quando o usuário interage com relatórios. Talvez você ache os artigos a seguir úteis também.

* [Formatação condicional em tabelas](desktop-conditional-table-formatting.md)
* [Usar o detalhamento no Power BI Desktop](desktop-cross-report-drill-through.md)
* [Usar o detalhamento no Power BI Desktop](desktop-drillthrough.md)
