---
title: Introdução à ferramenta de P e R para treinar a P e R do Power BI (versão prévia)
description: Introdução a ferramentas de P e R do Power BI
author: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 04/17/2020
ms.author: maggies
ms.openlocfilehash: 6178c9f157578110a09abf3fcbebccba54339f13
ms.sourcegitcommit: a199dda2ab50184ce25f7c9a01e7ada382a88d2c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82865979"
---
# <a name="intro-to-qa-tooling-to-train-power-bi-qa-preview"></a>Introdução à ferramenta de P e R para treinar a P e R do Power BI (versão prévia)

Com as *ferramentas* de P e R do Power BI, você pode melhorar a experiência de idioma natural para seus usuários. Como um designer ou administrador, você interage com o mecanismo de linguagem natural e faz melhorias em três áreas: 

- Examinar as perguntas que seus usuários fizeram.
- Ensinar P e R para entender as perguntas.
- Gerenciar os termos que você ensinou ao P e R.

Além dessas funcionalidades de ferramenta dedicadas, a guia **Modelagem** no Power BI Desktop oferece mais opções:  

- Sinônimos
- Rótulos de linha
- Ocultar de P e R
- Configurando o esquema linguístico (avançado)

## <a name="get-started-with-qa-tooling"></a>Introdução à ferramenta de P e R

A ferramenta de P e R só está disponível no Power BI Desktop e, no momento, dá suporte apenas ao modo de importação.

1. Abra o Power BI Desktop e use P e R para criar um visual. 
2. No canto do visual, selecione o ícone de engrenagem. 

    ![Engrenagem de visual de P e R](media/q-and-a-tooling-intro/qna-visual-gear.png)

    A página guia de introdução é aberta.  

    ![Introdução a P e R](media/q-and-a-tooling-intro/qna-tooling-dialog.png)

### <a name="review-questions"></a>Examinar perguntas

Selecione **Perguntas de revisão** para ver uma lista de conjuntos de valores que estão sendo usados no serviço do Power BI para seu locatário. A página **Perguntas de revisão** também exibe o proprietário do conjunto de dados, o workspace e a data da última atualização. Aqui, você pode selecionar um conjunto de dados e ver que perguntas os usuários estão fazendo. Os dados também mostram as palavras que não foram reconhecidas. Todos os dados mostrados aqui são dos últimos 28 dias.

![Perguntas de revisão de P e R](media/q-and-a-tooling-intro/qna-tooling-review-questions.png)

### <a name="teach-qa"></a>Ensinar P e R

A seção **Ensinar P e R** permite treinar o P e R para reconhecer palavras. Para começar, você digita uma pergunta que contém uma ou mais palavras que o P e R não reconhece. O P e R solicita a definição desse termo. Insira um filtro ou um nome de campo que corresponda ao que a palavra representa. O P e R então reinterpreta a pergunta original. Se você estiver satisfeito com os resultados, poderá salvar sua entrada. Para saber mais, confira [Ensinar P e R](q-and-a-tooling-teach-q-and-a.md)

![Visualização de sinônimo de Ensinar P e R](media/q-and-a-tooling-intro/qna-tooling-teach-fixpreview.png)

### <a name="manage-terms"></a>Gerenciar termos

Tudo o que você salvou da seção Ensinar P e R aparece aqui, assim, você pode revisar ou excluir os termos que definiu. No momento, não é possível editar uma definição existente, portanto, para redefinir um termo, exclua e recrie-o.

![Gerenciar termos de P e R](media/q-and-a-tooling-intro/qna-manage-terms.png)

### <a name="suggest-questions"></a>Sugerir perguntas

Sem fazer nenhuma configuração, o visual de P e R vai sugerir várias perguntas para começar. Essas perguntas são geradas automaticamente com base em seu modelo de dados. Em **Sugerir perguntas**, é possível substituir as perguntas geradas automaticamente com suas próprias perguntas. 

Para iniciar, digite a pergunta que você deseja adicionar na caixa de texto. Na seção de visualização, você verá como será o resultado no visual de P e R. 

:::image type="content" source="media/q-and-a-tooling-intro/power-bi-qna-suggest-questions.png" alt-text="Sugerir perguntas de P e R":::
 
Selecione o botão **Adicionar** para adicionar essa pergunta a **Suas perguntas sugeridas**. Cada pergunta extra é adicionada ao final desta lista. As perguntas aparecerão no visual de P e R na mesma ordem que na lista. 

:::image type="content" source="media/q-and-a-tooling-intro/power-bi-qna-save-suggest-questions.png" alt-text="Salvar perguntas sugeridas":::
 
Selecione **Salvar** para mostrar a lista de perguntas sugeridas no visual de P e R. 


## <a name="other-qa-settings"></a>Outras configurações de P e R

### <a name="bulk-synonyms"></a>Sinônimos em massa

A guia **Modelagem** do Power BI Desktop tem mais opções para melhorar a experiência de P e R. 

1. No Power BI Desktop, selecione modo de exibição Modelagem.

2. Selecione um campo ou uma tabela para exibir o painel **Propriedades**.  Esse painel é exibido no lado direito da tela e lista várias ações do P e R. Uma opção é **Sinônimos**. Na caixa **Sinônimos**, é possível definir rapidamente alternativas para a tabela ou o campo selecionado. Você também pode definir sinônimos na seção **Ensinar P e R** da caixa de diálogo ferramentas, mas geralmente é mais rápido definir sinônimos aqui para muitos campos em uma tabela.

    ![Sinônimos no painel Modelagem de P e R](media/q-and-a-tooling-intro/qna-modelling-pane-synonyms.png)

3. Para definir vários sinônimos para um único campo, use vírgulas para denotar o próximo sinônimo.

### <a name="hide-from-qa"></a>Ocultar de P e R

Você também pode ocultar campos e tabelas para que não apareçam nos resultados de P e R. 

1. No Power BI Desktop, selecione modo de exibição Modelagem.

2. Selecione um campo ou tabela para exibir o painel **Propriedades** e **Ative** **Está oculto**.

    O P e R respeita essa configuração e garante que o campo não seja reconhecido pelo P e R. Por exemplo, talvez você queira ocultar campos de ID e as chaves estrangeiras para evitar campos duplicados desnecessários com o mesmo nome. Mesmo que você oculte o campo, ainda poderá usá-lo no Power BI Desktop em visuais fora do P e R.

### <a name="set-a-row-label"></a>Definir um rótulo de linha

Um rótulo de linha permite que você defina qual coluna (ou *campo*) melhor identifica uma única linha em uma tabela. Por exemplo, para uma tabela chamada "Cliente", o rótulo de linha geralmente é "Nome de Exibição". Fornecer esses metadados extras permite ao P e R plotar um visual mais útil quando os usuários digitam '"Mostrar vendas por cliente". Em vez de tratar "cliente" como uma tabela, ele pode usar "Nome de Exibição" e exibir um gráfico de barras mostrando as vendas de cada cliente. Você só pode definir a exibição de Modelagem do rótulo de linha. 

1. No Power BI Desktop, selecione modo de exibição Modelagem.

2. Selecione uma tabela para exibir o painel **Propriedades**.

3. Na caixa **Rótulo de linha**, selecione um campo.

## <a name="configure-the-linguistic-schema-advanced"></a>Configurar o esquema linguístico (avançado)

No Power BI, você pode treinar completamente e aprimorar o mecanismo de idioma natural dentro do P e R, incluindo a alteração da pontuação e a ponderação dos resultados do idioma natural subjacente. Para saber como, confira [Editar esquema linguístico do P e R e adicionar frases](q-and-a-tooling-advanced.md).

## <a name="next-steps"></a>Próximas etapas

Há diversas melhores práticas para melhorar o mecanismo de linguagem natural. Para obter mais informações, confira as [Melhores práticas de P e R](q-and-a-best-practices.md).
