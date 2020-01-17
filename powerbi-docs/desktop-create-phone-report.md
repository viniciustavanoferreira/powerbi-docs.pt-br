---
title: Otimizar relatórios para os aplicativos móveis do Power BI
description: Aprenda a otimizar as páginas de relatório para aplicativos móveis do Power BI criando uma versão de retrato do relatório, especificamente para telefones e tablets.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/18/2019
ms.author: maggies
LocalizationGroup: Create reports
ms.openlocfilehash: 2dca4094ed0c21c421aa2fef89353e6f210b3ea4
ms.sourcegitcommit: 97597ff7d9ac2c08c364ecf0c729eab5d59850ce
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75761469"
---
# <a name="optimize-power-bi-reports-for-the-mobile-app"></a>Otimizar relatórios do Power BI para o aplicativo móvel
É possível melhorar a experiência de exibição de relatórios nos aplicativos móveis criando um layout de retrato. No Power BI Desktop e no serviço do Power BI, você reorganiza e redimensiona os visuais de relatório para obter uma experiência ideal no modo retrato.  

Está procurando informações sobre como exibir relatórios em um dispositivo móvel? Experimente este início rápido: [Explorar painéis e relatórios nos aplicativos móveis do Power BI](consumer/mobile/mobile-apps-quickstart-view-dashboard-report.md).

![Relatório otimizado em um telefone](media/desktop-create-phone-report/desktop-create-phone-report-1.png)

Você pode criar [visuais dinâmicos](#optimize-a-visual-for-any-size) e [segmentações de dados dinâmicas](#enhance-slicers-to-work-well-in-phone-reports) que são redimensionadas em qualquer lugar. Se você adicionar filtros ao relatório, eles aparecerão automaticamente no relatório otimizado.

## <a name="lay-out-a-portrait-version-of-a-report-page"></a>Criar uma versão de retrato de uma página de relatório

Após criar um relatório, é possível otimizá-lo para telefones e tablets.

1. Na exibição de **Relatório** no Power BI Desktop, na guia **Exibir**, selecione **Layout do Telefone**.  
   
    ![Ícone de Layout para Telefone](media/desktop-create-phone-report/desktop-create-phone-report-3.png)
   
    No serviço do Power BI, selecione **Editar relatório** > **Layout do Celular**.

    Você verá uma tela em branco em forma de telefone. Todos os elementos visuais na página do relatório original são listados no painel **Visualizações** à direita.

1. Para adicionar um visual ao layout do telefone, arraste-o do painel **Visualizações** para a tela do telefone.
   
    Relatórios de telefone usam um layout de grade. Ao arrastar elementos visuais para a tela do telefone, eles se ajustam à grade.
   
    ![Arrastar e soltar um visual](media/desktop-create-phone-report/desktop-create-phone-report-4.gif)
   
    Você pode adicionar alguns ou todos os elementos visuais da página de relatório mestre à página de relatório do telefone. Você pode adicionar cada visual apenas uma vez e não precisa incluir todos os visuais.

1. Você pode redimensionar os elementos visuais na grade, como você faria para blocos em dashboards e dashboards móveis.
   
   A grade do relatório para telefone é dimensionada em telefones de tamanhos diferentes para que o relatório fique bom em telefones com telas pequenas e grandes.
   
   ![Redimensionar um visual](media/desktop-create-phone-report/desktop-create-phone-report-5.gif)

## <a name="optimize-a-visual-for-any-size"></a>Otimizar um visual para qualquer tamanho
É possível definir os elementos visuais em seu painel ou relatório como *dinâmico*. Os visuais mudam dinamicamente para exibir o máximo de dados e insights, independentemente do tamanho da tela. 

À medida que o tamanho de um elemento visual muda, o Power BI prioriza a exibição de dados. Por exemplo, é possível remover automaticamente o preenchimento e mover a legenda para a parte superior do visual, de modo que ele continue informativo, mesmo quando fica menor.

![Redimensionamento do visual responsivo](media/desktop-create-phone-report/desktop-create-phone-report-6.gif)

Você opta por ativar a capacidade de resposta para cada visual. Leia mais sobre a [otimização de visuais](visuals/desktop-create-responsive-visuals.md).

## <a name="considerations-when-creating-phone-report-layouts"></a>Considerações ao criar layouts de relatório do telefone
* Para relatórios com várias páginas, você pode otimizar todas as páginas ou apenas algumas. 
* Se você tiver definido uma cor da tela de fundo para uma página de relatório, o relatório de telefone terá a mesma cor da tela de fundo.
* Você não pode modificar as configurações de formatação apenas para o telefone. A formatação é consistente entre os layouts mestres e móveis. Por exemplo, tamanhos de fonte serão os mesmos.
* Para alterar um elemento visual, como alterar sua formatação, seu conjunto de dados, seus filtros ou qualquer outro atributo, retorne ao modo de criação de relatórios regular.
* O Power BI fornece títulos e nomes de página padrão para relatórios de telefone no aplicativo móvel. Se você tiver criado elementos visuais de texto para títulos e nomes de página em seu relatório, considere não adicioná-los aos seus relatórios do telefone.     

## <a name="remove-a-visual-from-the-phone-layout"></a>Remover um visual do layout do telefone
* Para remover um visual, selecione o **X** na parte superior direita do visual na tela do telefone ou selecione-o e pressione **Excluir**.
  
   Remover o visual aqui apenas o remove da tela de layout do telefone. O visual e o relatório original não são afetados.
  
   ![Removendo um visual](media/desktop-create-phone-report/desktop-create-phone-report-7.gif)

## <a name="enhance-slicers-to-work-well-in-phone-reports"></a>Melhorar as segmentações funcionar bem em relatórios de telefone
As segmentações oferecem filtragem de dados de relatório na tela. Ao criar segmentações no modo de criação de relatórios regular, você pode modificar algumas configurações de segmentação para torná-los mais utilizáveis em relatórios de telefone:

* Decida se os leitores de relatório podem selecionar apenas um ou vários itens.
* Coloque uma caixa ao redor da segmentação para facilitar a verificação do relatório.
* Torne a segmentação vertical, horizontal ou *responsiva*. 

Se você fizer a segmentação responsiva, à medida que altera seu tamanho e sua forma, ela mostrará mais ou menos opções. Ela pode ser alta, baixa, larga ou estreita. Se você a fizer pequena o suficiente, ela se tornará apenas um ícone de filtro na página do relatório. 

![Segmentação responsiva do Power BI](media/desktop-create-phone-report/desktop-create-phone-report-8.png)

Leia mais sobre a [criação de segmentações responsivas](power-bi-slicer-filter-responsive.md).

## <a name="publish-a-phone-report"></a>Publicar um relatório de telefone
Para publicar a versão de telefone de um relatório, você [publica o relatório principal do Power BI Desktop no serviço do Power BI](desktop-upload-desktop-files.md) e a versão do telefone publica ao mesmo tempo.
  
Leia mais sobre [compartilhamento e permissões no Power BI](service-how-to-collaborate-distribute-dashboards-reports.md).

## <a name="view-optimized-and-unoptimized-reports-on-a-phone-or-tablet"></a>Exibir relatórios otimizados e não otimizados em um telefone ou tablet
Nos aplicativos móveis em telefones, o Power BI detecta automaticamente relatórios de telefone otimizados e não otimizados. Se houver um relatório otimizado para telefone, o aplicativo de telefone do Power BI abrirá automaticamente o relatório no modo de relatório do telefone.

Se um relatório otimizado para telefone não existir, o relatório será aberto na exibição de paisagem não otimizada.  

Quando estiver em um relatório do telefone, alterar a orientação do telefone para paisagem abrirá o relatório no modo de exibição não otimizado com o layout do relatório original, independentemente de o relatório ser otimizado ou não.

Se você otimizar apenas algumas páginas, os leitores encontrarão uma mensagem no modo retrato, indicando que o relatório está disponível em paisagem.

![Página do telefone não otimizada](media/desktop-create-phone-report/desktop-create-phone-report-9.png)

Leitores de relatórios podem girar seus telefones ou tablets para o lado para ver a página em modo paisagem. Leia mais sobre a [interação com relatórios do Power BI otimizados para o modo retrato](consumer/mobile/mobile-apps-view-phone-report.md).

## <a name="next-steps"></a>Próximas etapas
* [Criar uma exibição de telefone de um dashboard no Power BI](service-create-dashboard-mobile-phone-view.md).
* [Exibir relatórios do Power BI otimizados para seu telefone](consumer/mobile/mobile-apps-view-phone-report.md).
* [Criar visuais dinâmicos otimizados para qualquer tamanho](visuals/desktop-create-responsive-visuals.md).
* Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/).

