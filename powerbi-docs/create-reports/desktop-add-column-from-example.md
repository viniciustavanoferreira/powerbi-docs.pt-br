---
title: Adicionar uma coluna de um exemplo no Power BI Desktop
description: Crie rapidamente uma coluna no Power BI Desktop usando colunas existentes como exemplos.
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/16/2019
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: b10bbaa4158e6c5392cb6ed937c54bdbb5d555d2
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83295320"
---
# <a name="add-a-column-from-examples-in-power-bi-desktop"></a>Adicionar uma coluna com base em exemplos no Power BI Desktop
Com o recurso *Adicionar coluna com base em exemplos* no Editor do Power Query, você pode adicionar novas colunas ao modelo de dados simplesmente fornecendo um ou mais valores de exemplo para as novas colunas. Crie os exemplos de coluna com base em uma seleção ou forneça a entrada com base em todas as colunas existentes na tabela.

![](media/desktop-add-column-from-example/add-column-from-example_01.png)

O uso de *Adicionar coluna com base em exemplos* ajuda você a criar colunas de maneira rápida e fácil e é excelente para as seguintes situações:

- Você conhece os dados que deseja inserir na nova coluna, mas não tem certeza de qual transformação ou coleção de transformações produzirá esse resultado.
- Você já conhece quais transformações são necessárias, mas não tem certeza do que selecionar na interface do usuário para fazer isso.
- Você já sabe tudo sobre as transformações necessárias com o uso de uma expressão de *Coluna Personalizada* na linguagem *M*, mas uma ou mais dessas expressões não está disponível na interface do usuário.

A adição de uma coluna com base em um exemplo é fácil e simples. As próximas seções mostram como é fácil fazer isso.

## <a name="add-a-new-column-from-examples"></a>Adicionar uma nova coluna com base em exemplos

Para obter os dados de exemplo da Wikipédia, selecione **Obter Dados** > **Web** na guia **Página Inicial** da faixa de opções do Power BI Desktop. 

![Obter Dados da Web](media/desktop-add-column-from-example/add-column-from-example_02.png)

Cole a seguinte URL na caixa de diálogo exibida e selecione **OK**: 

*https:\//wikipedia.org/wiki/List_of_states_and_territories_of_the_United_States*

Na caixa de diálogo **Navegador**, selecione a tabela **Estados dos Estados Unidos da América** e, em seguida, selecione **Transformar Dados**. A tabela é aberta no Editor do Power Query.

Ou para abrir os dados já carregados do Power BI Desktop, selecione **Editar Consultas** na guia **Página Inicial** da faixa de opções. Os dados serão abertos no Editor do Power Query. 

![Selecione Editar Consultas no Power BI Desktop](media/desktop-add-column-from-example/add-column-from-example_05.png)

Depois que os dados de exemplo forem abertos no Editor do Power Query, selecione a guia **Adicionar Coluna** na faixa de opções e, em seguida, selecione **Coluna com Base em Exemplos**. Selecione o ícone **Coluna com Base em Exemplos** para criar a coluna de todas as colunas existentes ou selecione a seta suspensa para escolher entre **De Todas as Colunas** ou **Da Seleção**. Para este passo a passo, use **De Todas as Colunas**.

![Selecionar Adicionar Coluna com Base em Exemplos](media/desktop-add-column-from-example/add-column-from-example_03.png)

## <a name="add-column-from-examples-pane"></a>Painel Adicionar Coluna com Base em Exemplos
Quando você seleciona **Adicionar Coluna** > **Com Base em Exemplos**, o painel **Adicionar Coluna com Base em Exemplos** é aberto na parte superior da tabela. A nova **Coluna 1** é exibida à direita das colunas existentes (talvez seja necessário rolar a página para ver todas elas). Quando você insere os valores de exemplo nas células em branco da **Coluna 1**, o Power BI cria regras e transformações para que correspondam aos exemplos e usa-as para preencher o restante da coluna.

Observe que **Coluna Com Base em Exemplos** também é exibida como uma **Etapa Aplicada** no painel **Configurações de Consulta**. Como sempre, o Editor do Power Query grava as etapas de transformação e aplica-as à consulta em ordem.

![Painel Adicionar Coluna com Base em Exemplos](media/desktop-add-column-from-example/add-column-from-example_04.png)

Conforme você digita o exemplo na nova coluna, o Power BI fornece uma visualização da futura aparência do restante da coluna, com base nas transformações criadas. Por exemplo, se você digitar *Alabama* na primeira linha, isso corresponderá ao valor **Alabama** na primeira coluna da tabela. Assim que você pressiona ENTER, o Power BI preenche o restante da nova coluna com base no valor da primeira coluna e nomeia a coluna **Nome e abreviação postal[12] – Cópia**.

Agora, acesse a linha **Massachusetts[E]** da nova coluna e exclua a parte **[E]** da cadeia de caracteres. O Power BI detectará a alteração e usará o exemplo para criar uma transformação. O Power BI descreve as transformações no painel **Adicionar Coluna com Base em Exemplos** e renomeia a coluna para **Texto Antes do Delimitador.** 

![Coluna transformada com base em exemplos](media/desktop-add-column-from-example/add-column-from-example_06.png)

À medida que você continua fornecendo exemplos, o Editor do Power Query os adiciona às transformações. Quando estiver satisfeito, selecione **OK** para confirmar as alterações. 

Renomeie a nova coluna como desejar clicando duas vezes no título da coluna ou clicando com o botão direito do mouse nela e selecionando **Renomear**. 

Assista a este vídeo para ver **Adicionar Coluna com Base em Exemplos** em ação, usando a fonte de dados de exemplo: 

[Power BI Desktop: Adicionar Coluna com Base em Exemplos](https://www.youtube.com/watch?v=-ykbVW9wQfw). 

## <a name="list-of-supported-transformations"></a>Lista de transformações compatíveis
Muitas mas nem todas as transformações estão disponíveis ao usar **Adicionar Coluna com Base em Exemplos**. A seguinte lista mostra as transformações compatíveis:

**Geral**

- Coluna Condicional

**Referência**
  
- Referência a uma coluna específica, incluindo cortar, limpar ou aplicar uma transformação de maiúsculas e minúsculas

**Transformações de texto**

- Combinar (dá suporte à combinação de cadeias de caracteres literais e a todos os valores da coluna)
- Substituir
- Tamanho
- Extrair   
  - Primeiros caracteres
  - Últimos caracteres
  - Intervalo
  - Texto antes do delimitador
  - Texto depois do delimitador
  - Texto entre delimitadores
  - Tamanho
  - Remover Caracteres
  - Manter Caracteres

> [!NOTE]
> Todas as transformações de *Texto* levam em consideração a necessidade potencial de cortar, limpar ou aplicar uma transformação de maiúsculas e minúsculas ao valor da coluna.

**Transformações de data**

- Dia
- Dia da semana
- Nome do dia da semana
- Dia do ano
- Mês
- Nome do mês
- Trimestre do ano
- Semana do mês
- Semana do ano
- Ano
- Idade
- Início do ano
- Fim do ano
- Início do mês
- Fim do mês
- Início do trimestre
- Dias do mês
- Fim do trimestre
- Início da semana
- Fim da semana
- Dia do mês
- Início do dia
- Fim do dia

**Transformações de hora**

- Hora
- Minuto
- Second  
- Para a hora local

> [!NOTE]
> Todas as transformações de *Data* e *Hora* levam em consideração a necessidade potencial de converter o valor da coluna para *Data* ou *Hora* ou *Data/Hora*.

**Transformações de número** 

- Valor absoluto
- Arco cosseno
- Arco seno
- Arco tangente
- Converter em número
- Cosseno
- Cubo
- Dividir
- Expoente
- Fatorial
- Divisão de inteiro
- É par
- É ímpar
- Ln
- Logaritmo de base 10
- Módulo
- Multiplicar
- Arredondar para baixo
- Arredondar para cima
- Sinal
- Seno
- Raiz quadrada
- Quadrado
- Subtrair
- Somar
- Tangente
- Particionamento/intervalos

