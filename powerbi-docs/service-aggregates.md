---
title: Trabalhar com agregações (soma, média etc.) no serviço do Power BI
description: Saiba como alterar a agregação em um gráfico (soma, média, máximo etc.) no serviço do Power BI.
author: mgblythe
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/03/2019
ms.author: mblythe
ms.custom: seodec18
LocalizationGroup: Reports
ms.openlocfilehash: 595b5743450aeb8ae6f6e60157742e3563a28fdd
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/09/2019
ms.locfileid: "73873303"
---
# <a name="work-with-aggregates-sum-average-and-so-on-in-the-power-bi-service"></a>Trabalhar com agregações (soma, média etc.) no serviço do Power BI

## <a name="what-is-an-aggregate"></a>O que é uma agregação?

Às vezes, você deseja combinar matematicamente valores nos dados. A operação matemática pode ser soma, média, máximo, contagem etc. Quando você combina valores nos dados, isso é chamado de *agregação*. O resultado dessa operação matemática é um *agregado*.

Quando o serviço do Power BI e o Power BI Desktop criam visualizações, eles podem agregar os dados. Geralmente, a agregação é exatamente o que você precisa, mas outras vezes, talvez você deseje agregar os valores de maneira diferente.  Por exemplo, uma soma em vez de uma média. Há várias maneiras diferentes de gerenciar e alterar a agregação que o Power BI usa em uma visualização.

Primeiro, vamos dar uma olhada em *tipos* de dados porque o tipo de dados determina como e se o Power BI pode agregá-lo.

## <a name="types-of-data"></a>Tipos de dados

A maioria dos conjuntos de dados tem mais de um tipo de dados. No nível mais básico, os dados são numéricos ou não. O Power BI pode agregar dados numéricos usando uma soma, média, contagem, mínimo, variação e muito mais. O serviço pode, inclusive, agregar dados textuais, geralmente chamados de dados *categóricos*. Se você tentar agregar um campo categórico colocando-o em um bucket somente numérico como **Valores** ou **Dicas de ferramenta**, o Power BI contará as ocorrências de cada categoria ou as ocorrências distintas de cada categoria. Tipos especiais de dados, como datas, têm algumas de suas próprias opções de agregação: mais antigo, mais recente, primeiro e último.

No exemplo abaixo:

- **Unidades Vendidas** e **Preço de Fabricação** são colunas que contêm dados numéricos

- **Segmento**, **País**, **Produto**, **Mês** e **Nome do Mês** contêm dados categóricos

   ![Captura de tela de um conjunto de dados de exemplo.](media/service-aggregates/power-bi-aggregate-chart.png)

Ao criar uma visualização no Power BI, o serviço agregará campos numéricos (o padrão é *soma*) em algum campo categórico.  Por exemplo, "Unidades Vendidas ***por Produto***", "Unidades Vendidas ***por Mês***" e "Preço de Fabricação ***por Segmento***". O Power BI refere-se a alguns campos numéricos como **medidas**. É fácil identificar medidas no editor de relatório do Power BI – a lista **Campos** mostra medidas com o símbolo ∑ ao lado. Confira [O editor de relatório... Faça um tour](service-the-report-editor-take-a-tour.md) para obter mais informações.

![Captura de tela do Power BI com a lista Campos em destaque.](media/service-aggregates/power-bi-aggregate-fields.png)

## <a name="why-dont-aggregates-work-the-way-i-want-them-to"></a>Por que as agregações não funcionam do jeito que eu quero?

Trabalhar com agregações no serviço do Power BI pode ser confuso. Talvez você tenha um campo numérico e o Power BI não permita que você altere a agregação. Ou talvez você tenha um campo, como um ano, e você não deseja agregá-lo, apenas contar o número de ocorrências.

Normalmente, o problema subjacente é a definição de campo no conjunto de dados. Talvez o proprietário do conjunto de dados tenha definido o campo como texto e explique por que o Power BI não pode somar ou calcular a média. Infelizmente, [somente o proprietário do conjunto de dados pode alterar a maneira como um campo é categorizado](desktop-measures.md). Portanto, se você tiver permissões de proprietário no conjunto de dados, no Desktop ou no programa usado para criar o conjunto de dados (por exemplo, Excel), poderá corrigir esse problema. Caso contrário, precisará entrar em contato com o proprietário do conjunto de dados para obter ajuda.  

Há uma seção especial no final deste artigo chamada [**Considerações e solução de problemas**](#considerations-and-troubleshooting). Ela apresenta dicas e orientações. Se você não encontrar sua resposta lá, poste sua pergunta no [fórum da Comunidade do Power BI](https://community.powerbi.com). Você receberá uma resposta rápida diretamente da equipe do Power BI.

## <a name="change-how-a-numeric-field-is-aggregated"></a>Mudar a forma como um campo numérico é agregado

Digamos que você tenha um gráfico que soma as unidades vendidas para produtos diferentes, mas preferiria ter a média.

1. Crie um **Gráfico de colunas clusterizado** que use uma medida e uma categoria. Neste exemplo, estamos usando Unidades Vendidas por Produto.  Por padrão, o Power BI cria um gráfico que soma as unidades vendidas (arraste a medida para o contêiner **Valor**) para cada produto (arraste a categoria para o contêiner **Eixo**).

   ![Captura de tela do gráfico, painel Visualizações e lista de Campos com Soma em destaque.](media/service-aggregates/power-bi-aggregate-sum.png)

1. No painel **Visualizações**, clique com o botão direito do mouse na medida e selecione o tipo de agregação necessário. Nesse caso, estamos selecionando **Média**. Caso não veja a agregação de que precisa, confira a seção [**Considerações e solução de problemas**](#considerations-and-troubleshooting).

   ![Captura de tela da lista de agregação com Média selecionada e em destaque.](media/service-aggregates/power-bi-aggregate-average.png)

   > [!NOTE]
   > As opções disponíveis na lista suspensa variarão dependendo 1) do campo selecionado e 2) da maneira como o proprietário do conjunto de dados categorizou esse campo.

1. A visualização agora usa agregados por média.

   ![A captura de tela do gráfico agora exibindo a Média de Unidades Vendidas por Produto.](media/service-aggregates/power-bi-aggregate-average-2.png)

## <a name="ways-to-aggregate-your-data"></a>Maneiras de agregar os dados

Algumas das opções que podem estar disponíveis para um campo de agregação:

- **Não resumir**. Com essa opção escolhida, o Power BI trata cada valor nesse campo separadamente e não os resume. Use essa opção se você tiver uma coluna de ID numérica que o serviço não deva somar.

- **Soma**. Adiciona todos os valores nesse campo.

- **Média**. Usa uma média aritmética dos valores.

- **Mínimo**. Mostra o menor valor.

- **Máximo**. Mostra o maior valor.

- **Contagem (Não em branco).** Conta o número de valores nesse campo que não estão em branco.

- **Contagem (Distinto).** Conta o número de valores diferentes nesse campo.

- **Desvio padrão.**

- **Variação**.

- **Mediana**.  Mostra o valor mediano (meio). Esse valor tem o mesmo número de itens acima e abaixo.  Se houver duas medianas, o Power BI obterá suas médias.

Por exemplo, esses dados:

| País | Quantidade |
|:--- |:--- |
| EUA |100 |
| REINO UNIDO |150 |
| Canadá |100 |
| Alemanha |125 |
| França | |
| Japão |125 |
| Austrália |150 |

Daria os seguintes resultados:

- **Não resumir**: cada valor é exibido separadamente

- **Soma**: 750

- **Média**: 125

- **Máximo**:  150

- **Mínimo**: 100

- **Contagem (não em branco):** 6

- **Contagem (distinta):** 4

- **Desvio padrão:** 20,4124145...

- **Variação:** 416,666...

- **Valor mediano:** 125

## <a name="create-an-aggregate-using-a-category-text-field"></a>Criar uma agregação usando um campo de categoria (texto)

Você também pode agregar um campo não numérico. Por exemplo, se tiver um campo de nome do produto, poderá adicioná-lo como um valor e, em seguida, defini-lo como **Contagem**, **Contagem distinta**, **Primeiro** ou **Último**.

1. Arraste o campo **Produto** para o contêiner **Valores**. O contêiner **Valores** normalmente é usado para campos numéricos. O Power BI reconhece que esse campo é um campo de texto, define a agregação como **Não resumir** e apresenta uma tabela de coluna única.

   ![Captura de tela do campo Produto na caixa Valores.](media/service-aggregates/power-bi-aggregate-value.png)

1. Se você alterar a agregação do padrão **Não resumir** para **Contagem (Distinta)** , o Power BI contará o número de diferentes produtos. Nesse caso, há quatro.
  
   ![Captura de tela da contagem distinta de produtos.](media/service-aggregates/power-bi-aggregate-count.png)

1. Se você alterar a agregação para **Contagem**, o Power BI contará o número total. Neste caso, há sete entradas para **Produto**.

   ![Captura de tela da contagem de produtos.](media/service-aggregates/power-bi-aggregate-count-2.png)

1. Arrastando o mesmo campo (nesse caso, **Produto**) para o contêiner **Valores** e deixando a agregação padrão **Não resumir**, o Power BI divide a contagem por produto.

   ![Captura de tela do produto e da contagem de produtos.](media/service-aggregates/power-bi-aggregate-final.png)

## <a name="considerations-and-troubleshooting"></a>Considerações e solução de problemas

P:  Por que não vejo uma opção **Não resumir**?

R:  O campo selecionado provavelmente é uma medida calculada ou uma medida avançada criada no Excel ou no [Power BI Desktop](desktop-measures.md). Cada medida calculada tem sua própria fórmula embutida em código. Não é possível alterar a agregação que o Power BI usa. Por exemplo, se ela for uma soma, só poderá ser uma soma. A lista **Campos** mostra *medidas calculadas* com o símbolo de calculadora.

P:  Meu campo **é** numérico. Por que as únicas opções exibidas são **Contagem** e **Contagem distinta**?

R1:  A explicação provável é que o proprietário do conjunto de dados *não* classificou o campo como um número. Por exemplo, se um conjunto de dados tiver um campo **ano**, o proprietário do conjunto de valores poderá categorizar o valor como texto. É mais provável que Power BI conte o campo **ano** (por exemplo, o número de pessoas nascidas em 1974). É menos provável que o Power BI some ou calcule a média dele. Se você for o proprietário, poderá abrir o conjunto de dados no Power BI Desktop e usar a guia **Modelagem** para alterar o tipo de dados.

R2: Se o campo tiver um ícone de calculadora, isso significa que é *uma medida calculada*. Cada medida calculada tem sua própria fórmula embutida em código que apenas o proprietário do conjunto de dados pode alterar. O cálculo que o Power BI usa pode ser uma agregação simples, como uma média ou soma. Também pode ser algo mais complicado, como um "percentual de contribuição para a categoria pai" ou "total acumulado desde o início do ano". O Power BI não vai somar nem calcular a média dos resultados. Em vez disso, ele apenas recalculará (usando a fórmula embutida em código) para cada ponto de dados.

R3:  Outra possibilidade é que você soltou o campo em um *bucket* que permite somente valores categóricos.  Nesse caso, as únicas opções serão contagem e contagem distinta.

R4:  E uma quarta possibilidade é que você está usando o campo para um eixo. Em um eixo de gráfico de barras, por exemplo, o Power BI mostra uma barra para cada valor distinto – ele não agrega os valores de campo.

>[!NOTE]
>A exceção a essa regra são os gráficos de dispersão, que *exigem* valores agregados para os eixos X e Y.

P:  Por que não é possível agregar campos de texto de fontes de dados do SSAS (SQL Server Analysis Services)?

R:  As conexões dinâmicas com modelos multidimensionais do SSAS não permitem nenhuma agregação do lado do cliente, incluindo primeiro, último, média, mínimo, máximo e soma.

P:  Tenho um gráfico de dispersão e *não* quero que meu campo seja agregado.  Como posso fazer isso?

R:  Adicione o campo ao bucket **Detalhes** e não aos buckets dos eixos X ou Y.

P:  Quando adiciono um campo numérico a uma visualização, a maioria deles usa soma como padrão, mas outros usam média ou contagem ou alguma outra agregação como padrão.  Por que a agregação padrão nem sempre é a mesma?

R:  Os proprietários do conjunto de dados pode definir o resumo padrão para cada campo. Se você for um proprietário de conjunto de dados, altere o resumo padrão na guia **Modelagem** do Power BI Desktop.

P:  Sou o proprietário de um conjunto de dados e quero garantir que um campo nunca é agregado.

R:  No Power BI Desktop, na guia **Modelagem**, defina **Tipo de dados** como **Texto**.

P:  Não consigo ver **Não resumir** como uma opção em minha lista suspensa.

R:  Tente remover o campo e adicioná-lo novamente.

Mais perguntas? [Experimente a Comunidade do Power BI](https://community.powerbi.com/)