---
title: Usar uma segmentação ou um filtro de datas relativas no Power BI Desktop
description: Saiba como usar uma segmentação ou um filtro para restringir intervalos de datas relativas no Power BI Desktop
author: mihart
manager: kvivek
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/24/2019
ms.author: mihart
LocalizationGroup: Create reports
ms.openlocfilehash: e1dfda3c759d225019cc50d36cfe746976bd797a
ms.sourcegitcommit: cc4b18d55b2dca8fdb1bef00f53a0a808c41432a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68867083"
---
# <a name="use-a-relative-date-slicer-and-filter-in-power-bi-desktop"></a>Usar uma segmentação e um filtro de datas relativas no Power BI Desktop

Com a **segmentação de datas relativas** ou o **filtro de datas relativas**, aplique filtros baseados em tempo a qualquer coluna de data do modelo de dados. Por exemplo, você pode usar a **segmentação de datas relativas** para mostrar apenas os dados de vendas ocorridos nos últimos 30 dias (ou mês, meses do calendário e assim por diante). Quando você atualizar os dados, o período relativo aplicará automaticamente a restrição de datas relativas apropriada.

![Captura de tela de um relatório com uma seta apontando para uma segmentação de datas relativas.](media/desktop-slicer-filter-date-range/relative-date-range-slicer-filter-01.png)

## <a name="use-the-relative-date-range-slicer"></a>Usar a segmentação de intervalo de datas relativas

Use a segmentação de datas relativas como qualquer outra segmentação. Crie um visual de **segmentação** para o relatório e, em seguida, selecione um valor de data no valor **Campo**. Na imagem a seguir, selecionamos o campo *OrderDate*.

![Captura de tela do painel de visualizações com setas apontando para o ícone do visual de segmentação e a área Campo.](media/desktop-slicer-filter-date-range/relative-date-range-slicer-filter-02.png)

Selecione a segmentação em sua tela e, em seguida, o acento circunflexo no canto superior direito do visual da segmentação. Se o visual tiver dados de data, o menu exibirá a opção para **Relativo**.

![Captura de tela do visual da segmentação com um destaque em torno do acento circunflexo e uma seta apontando para Relativo.](media/desktop-slicer-filter-date-range/relative-date-range-slicer-filter-03.png)

Na segmentação de datas relativas, selecione *Relativo*.

Em seguida, selecione as configurações.

Na primeira configuração da *segmentação de datas relativas*, você tem as seguintes opções:

![Captura de tela das opções de configuração relativa com a primeira configuração destacada.](media/desktop-slicer-filter-date-range/relative-date-range-slicer-filter-04.png)

* Último

* Avançar

* Este

A segunda configuração (no meio) da *segmentação de datas relativas* permite inserir um número para definir o intervalo de datas relativas.

![Captura de tela das opções de configuração relativa com a segunda configuração destacada.](media/desktop-slicer-filter-date-range/relative-date-range-slicer-filter-04a.png)

A terceira configuração permite escolher a medida de data. Você tem as seguintes opções:

![Captura de tela das opções de configuração relativa com a terceira configuração destacada.](media/desktop-slicer-filter-date-range/relative-date-range-slicer-filter-05.png)

* Dias

* Semanas

* Semanas (calendário)

* Meses

* Meses (calendário)

* Anos

* Anos (Calendário)

Se você selecionar **Meses** nessa lista e inserir *2* na configuração do meio, acontecerá o seguinte:

* se hoje for 20 de julho

* os dados incluídos nos visuais restringidos pela segmentação mostrarão dados dos dois meses anteriores

* começando em 21 de maio até 20 de julho (data de hoje)

Em comparação, se você selecionou *Meses (calendário)* , os visuais restringidos mostrarão dados de 1º de maio a 30 de junho (os dois últimos meses do calendário completos).

## <a name="using-the-relative-date-range-filter"></a>Usando o filtro de intervalo de datas relativas

Você também pode criar um filtro de intervalo de datas relativas para a página de relatório ou para o relatório inteiro. Para fazer isso, arraste um campo de data para as áreas **Filtros no nível de página** ou **Filtros no nível de relatório** do painel **Campo**:

![Captura de tela do campo OrderDate, que está sendo arrastado para a área dos filtros de nível de página.](media/desktop-slicer-filter-date-range/relative-date-range-slicer-filter-06.png)

Uma vez lá, você pode alterar o intervalo de datas relativas. Isso é semelhante a como você pode personalizar a **segmentação de datas relativas**. Selecione **Filtragem de datas relativas** na lista suspensa **Tipo de Filtro**.

![Captura de tela mostrando a lista suspensa Tipo de Filtro e o ponteiro do mouse sobre a filtragem de Data Relativa.](media/desktop-slicer-filter-date-range/relative-date-range-slicer-filter-07.png)

Depois que selecionar **Filtragem de datas relativas**, você verá três seções a serem modificadas, incluindo uma caixa numérica intermediária, como a segmentação.

![Captura de tela dos filtros de nível de relatório com setas apontando para a opção Mostrar itens quando o valor.](media/desktop-slicer-filter-date-range/relative-date-range-slicer-filter-08.png)

## <a name="limitations-and-considerations"></a>Limitações e considerações

No momento, as limitações e considerações a seguir aplicam-se ao filtro e à **segmentação de intervalo de datas relativas**.

* Os modelos de dados do **Power BI** não incluem informações de fuso horário. Os modelos podem armazenar horários, mas não há nenhuma indicação do fuso horário em que estão localizados.

* A segmentação e o filtro sempre se baseiam no horário em UTC. Se você definir um filtro em um relatório e enviá-lo para um colega em um fuso horário diferente, ambos verão os mesmos dados. A menos que você esteja no fuso horário UTC, você e seu colega devem considerar a diferença de horário.

* É possível converter dado capturados em um fuso horário local em UTC usando o **Editor de Consultas**.

## <a name="next-steps"></a>Próximas etapas

Saiba como [usar agrupamento e compartimentalização no Power BI Desktop](../desktop-grouping-and-binning.md).
