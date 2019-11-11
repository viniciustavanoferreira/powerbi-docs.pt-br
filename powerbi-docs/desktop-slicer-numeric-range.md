---
title: Usar a segmentação de intervalo numérico no Power BI Desktop
description: Saiba como usar uma segmentação para restringir a intervalos numéricos no Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/19/2019
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 535dbe2b1765d788e59d928f7303ce4696aa163b
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/09/2019
ms.locfileid: "73879691"
---
# <a name="use-the-numeric-range-slicer-in-power-bi-desktop"></a>Usar a segmentação de intervalo numérico no Power BI Desktop
Com a segmentação de intervalo numérico, você pode aplicar todos os tipos de filtros a qualquer coluna numérica em seu modelo de dados. Há três opções para filtrar seus dados numéricos: entre números, menor ou igual a um número ou maior ou igual a um número. Isso pode parecer simples, mas é uma maneira eficiente de filtrar seus dados.

![Visual com segmentação de intervalo numérico](media/desktop-slicer-numeric-range/desktop-slicer-numeric-range-0.png)

## <a name="use-the-numeric-range-slicer"></a>Usar a segmentação de intervalo numérico
Você pode usar a segmentação de intervalo numérico como usaria qualquer outra segmentação. Basta criar um visual de **segmentação** para o relatório e depois selecionar um valor numérico para o valor **Campo**. Na imagem a seguir, selecionamos o campo **LineTotal**.

![Criar uma segmentação de intervalo numérico](media/desktop-slicer-numeric-range/desktop-slicer-numeric-range-1-create.png)

Selecione o link de seta para baixo no canto superior direito da **segmentação de intervalo numérico** e um menu será exibido.

![Menu de segmentação de intervalo numérico](media/desktop-slicer-numeric-range/desktop-slicer-numeric-range-2-between.png)

Para o intervalo numérico, você pode selecionar uma das três opções a seguir:

* **Entre**
* **Menor ou igual a**
* **Maior ou igual a**

Ao selecionar **Entre** no menu, um controle deslizante é exibido. Você pode usar o controle deslizante para selecionar valores numéricos que se enquadram entre os números. Às vezes, a granularidade da movimentação da barra de segmentação torna difícil parar exatamente nesse número. Você também pode usar o controle deslizante e selecionar qualquer uma das caixas para digitar os valores desejados. Essa opção é conveniente quando você deseja segmentar em números específicos. 

Na imagem a seguir, a página de relatório filtra para valores de **LineTotal** que variam entre 2.500,00 e 6.000,00.

![Segmentação de intervalo numérico com Entre](media/desktop-slicer-numeric-range/desktop-slicer-numeric-range-3-between-range.png)

Quando você seleciona **menor ou igual a**, a alça esquerda (valor mais baixo) da barra de controle deslizante desaparece e você pode ajustar apenas o limite superior da barra de controle deslizante. Na imagem a seguir, definimos o máximo da barra deslizante como 5928,19.

![Segmentação de intervalo numérico com Menor que](media/desktop-slicer-numeric-range/desktop-slicer-numeric-range-4-less-than.png)

Por fim, se você selecionar **Maior ou igual a**, a alça da barra de controle deslizante direita (valor mais alto) desaparecerá. Em seguida, você pode ajustar o valor mais baixo, como mostrado na imagem a seguir. Agora apenas os itens com **LineTotal** maior ou igual a 4902,99 são exibidos nos visuais na página do relatório.

![Segmentação de intervalo numérico com Maior que](media/desktop-slicer-numeric-range/desktop-slicer-numeric-range-5-greater-than.png)

## <a name="snap-to-whole-numbers-with-the-numeric-range-slicer"></a>Ajustar para números inteiros com a segmentação de intervalo numérico

Uma segmentação de intervalo numérico será ajustada a números inteiros se o tipo de dados do campo subjacente for um **Número Inteiro**. Esse recurso permite que a segmentação se alinhe corretamente a números inteiros. Os campos de **Número Decimal** permitem inserir ou selecionar frações de um número. A formatação definida na caixa de texto corresponde ao conjunto de formatação no campo, mesmo que seja possível digitar ou selecionar números mais precisos.

## <a name="display-formatting-with-the-date-range-slicer"></a>Exibir a formatação com a segmentação de intervalo de datas

Quando você usa uma segmentação de dados para exibir ou definir um intervalo de datas, as datas são exibidas no formato de **Data Abreviada**. A localidade do sistema operacional ou do navegador do usuário determina o formato de data. Assim, será o formato de exibição, não importa quais sejam as configurações de tipo de dados para os dados ou o modelo subjacente. 

Você pode, por exemplo, ter um formato de data longo para o tipo de dados subjacente. Nesse caso, um formato de data como *dddd, MMMd, aaaa* formataria uma data em outros visuais ou circunstâncias como *quarta-feira, 14 de março de 2001*. Porém, na segmentação de intervalo de datas, essa data é exibida na segmentação como *14/03/2001*.

A exibição do formato **Data Abreviada** na segmentação garante que o comprimento da cadeia de caracteres permaneça consistente e compacto na segmentação. 

## <a name="limitations-and-considerations"></a>Limitações e considerações
As seguintes considerações e limitações aplicam-se à **segmentação de intervalo numérico**:

* A **segmentação de intervalo numérico** filtra todas as linhas subjacentes nos dados, não qualquer valor agregado. Por exemplo, digamos que você use um campo de *Valor de Vendas*. A segmentação então filtra cada transação com base no valor das vendas, não na soma do valor das vendas de cada ponto de dados de um visual.
* No momento, isso não funciona com medidas.
* Você pode digitar qualquer número de caixas de texto em uma segmentação de numérica, mesmo que ela esteja fora do intervalo de valores da coluna subjacente. Essa opção permitirá que você configure os filtros se souber que os dados podem mudar no futuro.
