---
title: Usar uma segmentação ou um filtro de tempo relativo no Power BI
description: Saiba como usar uma segmentação ou um filtro para restringir intervalos de tempo relativos no Power BI.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 04/22/2020
ms.author: maggies
LocalizationGroup: Create reports
ms.openlocfilehash: 4f0bfdbf3eb3856f872c872fbe0880ad39839e07
ms.sourcegitcommit: a199dda2ab50184ce25f7c9a01e7ada382a88d2c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82867589"
---
# <a name="use-a-relative-time-slicer-and-filter-in-power-bi"></a>Usar uma segmentação e um filtro de tempo relativo no Power BI

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-desktop](../includes/yes-desktop.md)] [!INCLUDE [yes-service](../includes/yes-service.md)]

Com cenários emergentes de rápida atualização, a capacidade de filtrar para uma janela de tempo menor pode ser útil. Usando a segmentação de tempo relativo ou o filtro de tempo relativo, é possível aplicar filtros baseados em tempo a qualquer coluna de data ou tempo do modelo de dados. Por exemplo, é possível usar a segmentação de dados de tempo relativo para mostrar apenas exibições de vídeo nos últimos minuto ou hora. 

:::image type="content" source="media/slicer-filter-relative-time/power-bi-relative-time.gif" alt-text="Exemplo de tempo relativo":::

Você não precisa usar o recurso em conjunto com o recurso de [atualização automática de página](../desktop-automatic-page-refresh.md). No entanto, muitos cenários de tempo relativo combinam bem com o recurso de atualização automática de página.  

> [!NOTE]
> Quando você aplica um filtro de tempo relativo ou uma segmentação na página ou no nível de relatório, todos os visuais nessa página ou no relatório são filtrados para o mesmo intervalo de tempo, usando um tempo de *âncora* compartilhado. Como os visuais podem ter tempos de execução um pouco diferentes, esse tempo de âncora compartilhado garante que os visuais sejam sincronizados em sua página ou em seu relatório. Leia mais sobre o [tempo de âncora](#understanding-anchor-time) neste artigo.

## <a name="turn-on-relative-time-preview"></a>Ativar versão prévia de tempo relativo

O filtro de tempo relativo está em versão prévia, portanto você precisa ativar a opção de recurso. Acesse **Arquivo** > **Opções e Configurações** > **Opções**. Em **Configurações globais** > **Versão prévia dos recursos**, verifique se **Filtro de tempo relativo** está selecionado.

:::image type="content" source="media/slicer-filter-relative-time/power-bi-relative-time-set-preview.png" alt-text="Definir a opção de versão prévia de tempo relativo":::

## <a name="create-a-relative-time-slicer-or-filter"></a>Criar uma segmentação ou um filtro de tempo relativo

Depois de habilitar o recurso, você poderá arrastar e soltar o campo de data ou hora para a caixa de campo de uma segmentação de dados ou para a zona de destino no painel Filtros. 

### <a name="create-a-slicer"></a>Criar uma segmentação

1. Arraste um campo de data ou hora para a tela.

2. Selecione o tipo de visualização **Segmentação**.

    :::image type="content" source="media/slicer-filter-relative-time/power-bi-relative-time-create-slicer.png" alt-text="Criar uma segmentação de tempo":::

### <a name="create-a-filter"></a>Crie um filtro
 
- Arraste um campo de data ou hora para o painel Filtros, por **este visual**, **esta página** ou **todas as páginas**.

### <a name="set-relative-time"></a>Definir o tempo relativo 

Em seguida, altere o tipo de filtro para **Tempo Relativo**.

:::image type="content" source="media/slicer-filter-relative-time/power-bi-relative-time-set.png" alt-text="Alterar para tempo relativo":::
 
Veja como ele aparece em uma segmentação:

:::image type="content" source="media/slicer-filter-relative-time/power-bi-relative-time-slicer.png" alt-text="Tempo relativo em uma segmentação":::

Veja como ele aparece em um cartão de filtro: 

:::image type="content" source="media/slicer-filter-relative-time/power-bi-relative-time-filter.png" alt-text="Tempo relativo em um filtro":::
 
Com esse novo tipo de filtro, você tem a opção de filtrar com base em **Último**, **Próximo** ou **Este período de tempo**: 

:::image type="content" source="media/slicer-filter-relative-time/power-bi-relative-time-last-next.png" alt-text="Escolher Último, Próximo ou Este período de tempo":::
 
Especifique a janela de tempo usando um número inteiro e uma unidade de tempo: **Minutos** ou **Horas**.
 
:::image type="content" source="media/slicer-filter-relative-time/power-bi-relative-time-minutes-hours.png" alt-text="Escolher minutos ou horas":::

Se você precisar economizar espaço na tela, também poderá criar o filtro de tempo relativo como um cartão de filtro no painel Filtros.

:::image type="content" source="media/slicer-filter-relative-time/power-bi-relative-time-set-filter.png" alt-text="Definir tempo relativo em um filtro":::
 
## <a name="understanding-anchor-time"></a>Entendendo o tempo de âncora

Quando um filtro é aplicado ao nível de página ou de relatório, todos os visuais nessa página ou no relatório são sincronizados com o mesmo intervalo de tempo exato. Essas consultas são todas emitidas em relação a um tempo chamado de *tempo de âncora*. O tempo de âncora é atualizado automaticamente nas seguintes condições:

- Carregamento inicial de página.
- Atualização manual.
- Atualização automática ou de alteração de página de detecção.
- Uma alteração no modelo.

### <a name="anchor-time-exceptions"></a>Exceções de tempo de âncora

- A filtragem de tempo relativo usando o visual de P E R não é relativa a esse tempo de âncora, até que você converta o visual de P e R em um visual padrão. No entanto, os outros visuais de IA, como os influenciadores principais e a árvore de decomposição, são sincronizados com o tempo de âncora. 
- Além disso, filtros de data relativa ou segmentações não são relativos ao tempo de âncora, a menos que na presença de filtros de tempo relativo. Se um filtro de data relativa e de tempo relativo estiver na mesma página, o filtro de data relativa respeitará o tempo de âncora.

## <a name="limitations-and-considerations"></a>Limitações e considerações

No momento, as limitações e considerações a seguir aplicam-se ao filtro e à segmentação de tempo relativo.

- **Considerações sobre o fuso horário**: os modelos de dados do Power BI não incluem informações de fuso horário. Os modelos podem armazenar horários, mas não há nenhuma indicação do fuso horário em que estão localizados. A segmentação e o filtro sempre se baseiam no horário em UTC. Se você definir um filtro em um relatório e enviá-lo para um colega em um fuso horário diferente, ambos verão os mesmos dados. A menos que você ou seu colega esteja no fuso horário UTC, ambos precisarão considerar a diferença de horário. Use o Editor de Consultas para converter dados capturados em um fuso horário local em UTC.
- Este novo tipo de filtro tem suporte no Power BI Desktop, no serviço do Power BI, no Power BI Embedded e nos aplicativos móveis do Power BI. No entanto, há algumas limitações de suporte conhecidas:

    - Não há suporte para ele por meio da API de Inserção.
    - Não há suporte ele para publicar na Web.

- **Cache de consulta**: utilizamos o cache do cliente. Portanto, digamos que você especifique "último 1 minuto" e "últimos 5 minutos" e, em seguida, volte para "último 1 minuto". Nesse ponto, você verá os mesmos resultados de quando ele foi executado pela primeira vez, a menos que você atualize a página ou a página seja atualizada automaticamente.

## <a name="next-steps"></a>Próximas etapas

- [Usar uma segmentação e um filtro de data relativa no Power BI](../visuals/desktop-slicer-filter-date-range.md)
- [Segmentações no Power BI](../visuals/power-bi-visualization-slicers.md)

