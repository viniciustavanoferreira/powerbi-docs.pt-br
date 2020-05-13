---
title: Exibir relatórios do Power BI otimizados para seu telefone
description: Leia sobre a interação com páginas de relatório otimizadas para exibição em aplicativos do Power BI.
author: paulinbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 05/05/2020
ms.author: painbar
ms.openlocfilehash: d3584ebc5233ccffc007118ac87ada49e906b34c
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83273513"
---
# <a name="view-power-bi-reports-optimized-for-your-phone"></a>Exibir relatórios do Power BI otimizados para seu telefone

Aplica-se a:

| ![iPhone](./media/mobile-apps-view-phone-report/ios-logo-40-px.png) | ![Telefone Android](./media/mobile-apps-view-phone-report/android-logo-40-px.png) |
|:--- |:--- |
| iPhones |Telefones Android |

Quando você exibe um relatório do Power BI em seu telefone, o Power BI verifica se o relatório foi otimizado para telefones. Em caso afirmativo, o Power BI abre automaticamente o relatório otimizado na Exibição Retrato.

![Relatório no modo retrato](./media/mobile-apps-view-phone-report/07-power-bi-phone-report-portrait.png)

Caso não haja um relatório otimizado para telefone, o relatório será aberto, mas no modo de exibição de paisagem não otimizada. Mesmo em um relatório otimizado para telefones, se você mudar a orientação do telefone, o relatório será aberto na exibição não otimizada com o layout original do relatório. Se somente algumas páginas forem otimizadas, você encontrará uma mensagem na exibição de retrato, indicando que o relatório está disponível em paisagem.

![Página de relatório não otimizada](./media/mobile-apps-view-phone-report/06-power-bi-phone-report-page-not-optimized.png)

Todos os outros recursos de relatórios do Power BI ainda funcionam em relatórios otimizados para telefones. Leia mais sobre o que você pode fazer em:

* [Relatórios sobre iPhones](mobile-reports-in-the-mobile-apps.md). 
* [Relatórios sobre telefones Android](mobile-reports-in-the-mobile-apps.md).

## <a name="filter-the-report-page-on-a-phone"></a>Filtrar a página de relatório em um telefone
Se um relatório otimizado para telefone tiver filtros definidos, quando ele for exibido em um telefone, será possível utilizar esses filtros. O relatório é aberto em seu telefone, filtrado para os valores que estão sendo filtrados no relatório na Web. Você verá uma mensagem informando que existem filtros ativos na página. É possível alterar os filtros no seu telefone.

1. Toque no ícone de filtro ![Ícone de filtro do telefone](./media/mobile-apps-view-phone-report/power-bi-phone-filter-icon.png) na parte inferior da página.

2. Use a filtragem básica ou avançada para ver os resultados em que você está interessado.
   
    ![Filtro avançado do relatório de telefone do BI do telefone](./media/mobile-apps-view-phone-report/power-bi-iphone-advanced-filter-toronto.png)

## <a name="cross-highlight-visuals"></a>Elementos visuais com realce cruzado
O realce cruzado de visuais na Exibição Retrato funciona da maneira que no serviço do Power BI e em telefones na Exibição Paisagem: quando você seleciona dados em um visual, dados relacionados são realçados em outros visuais nessa página.

Leia mais sobre [filtragem e realce no Power BI](../../create-reports/power-bi-reports-filters-and-highlighting.md).

## <a name="select-visuals"></a>Selecionar elementos visuais
Em relatórios de telefone quando você seleciona um elemento visual, o relatório realça o elemento visual e foca nele, neutralizando gestos da tela.

Com o visual selecionado, você executar ações como rolar no elemento visual. Para cancelar a seleção de um elemento visual, basta tocar em qualquer parte fora da área do elemento visual.

## <a name="open-visuals-in-focus-mode"></a>Abrir elementos visuais em modo de foco
Os relatórios do telefone também oferecem um modo de foco: Você obtém uma exibição mais ampla de um único visual e o explora com mais facilidade.

* Em um relatório de telefone, toque no botão de reticências ( **...** ) no canto superior direito de um visual > **Expandir para o modo de foco**.
  
    ![Expandir para o modo de foco](././media/mobile-apps-view-phone-report/power-bi-phone-report-focus-mode.png)

O que você faz no modo de foco é transferido para a tela de relatório e vice-versa. Por exemplo, se você realçar um valor em um visual e, em seguida, retornar para o relatório inteiro, o relatório será filtrado para o valor realçado no visual.

Algumas ações somente são possíveis no modo de foco, devido às restrições de tamanho de tela:

* **Detalhar** as informações exibidas em um visual. Leia mais sobre como [fazer drill-down e up](mobile-apps-view-phone-report.md#drill-down-in-a-visual) em um relatório de telefone abaixo.
* **Classifique** os valores no elemento visual.
* **Reverter**: desmarque as etapas de exploração que você efetuou em um visual e reverta para a definição estabelecida quando o relatório foi criado.
  
    Para limpar toda a exploração de um visual, toque no botão de reticências ( **...** ) > **Reverter**.
  
    ![Reverter](././media/mobile-apps-view-phone-report/power-bi-phone-report-revert-levels.png)
  
    A reversão está disponível no nível do relatório, limpando toda a exploração de todos os visuais ou, no nível do visual, limpando toda a exploração do visual selecionado.   

## <a name="drill-down-in-a-visual"></a>Fazer drill down em um visual
Se os níveis hierárquicos forem definidos em um visual, você poderá fazer drill down nas informações detalhadas exibidas em um visual e, em seguida, fazer backup. [Adicione o drill-down em um visual](../end-user-drill.md) no serviço do Power BI ou no Power BI Desktop.

Há alguns tipos de drill down:

### <a name="drill-down-on-a-value"></a>Drill down em um valor
1. Dê um toque longo (tocar e segurar) em um ponto de dados de um visual.
2. A dica de ferramenta será exibida e, se a hierarquia for definida, o rodapé da dica de ferramenta mostrará a seta de drill down e up.
3. Toque na seta para baixo para fazer drill down

    ![Tocar em drill down](././media/mobile-apps-view-phone-report/report-drill-down.png)
    
4. Toque na seta para cima para fazer drill up.

### <a name="drill-to-next-level"></a>Analisar o próximo nível
1. Em um relatório em um telefone, toque no botão de reticências ( **...** ) no canto superior direito > **Expandir para o modo de foco**.
   
    ![Expandir para o modo de foco](././media/mobile-apps-view-phone-report/power-bi-phone-report-focus-mode.png)
   
    Neste exemplo, as barras mostram os valores de estados.
2. Toque no ícone Explorar ![ícone Explorar](./media/mobile-apps-view-phone-report/power-bi-phone-report-explore-icon.png) no canto inferior esquerdo.
   
    ![Modo de exploração](./media/mobile-apps-view-phone-report/power-bi-phone-report-explore-mode.png)
3. Toque em **Mostrar o próximo nível** ou em **Expandir para o próximo nível**.
   
    ![Expandir para o próximo nível](./media/mobile-apps-view-phone-report/power-bi-phone-report-expand-levels.png)
   
    Agora as barras mostram os valores para as cidades.
   
    ![Níveis expandidos](./media/mobile-apps-view-phone-report/power-bi-phone-report-expanded-levels.png)
4. Se você tocar na seta no canto superior esquerdo, você voltará ao relatório de telefone com os valores ainda expandidos para um nível inferior.
   
    ![Ainda expandido para um nível inferior](./media/mobile-apps-view-phone-report/power-bi-back-to-phone-report-expanded-levels.png)
5. Para voltar ao nível original, toque no botão de reticências ( **...** ) novamente > **Reverter**.
   
    ![Reverter](././media/mobile-apps-view-phone-report/power-bi-phone-report-revert-levels.png)

## <a name="drill-through-from-a-value"></a>Executar uma consulta drill-through de um valor
O drill-through conecta os valores de uma página de relatório a outras páginas de relatório. Quando você executa uma consulta drill-through de um ponto de dados para outra página de relatório, os valores de ponto de dados são usados para filtrar a página detalhada ou eles estarão no contexto dos dados selecionados.
Os autores de relatório podem [definir o drill-through](https://docs.microsoft.com/power-bi/desktop-drillthrough) ao criar o relatório.

1. Dê um toque longo (tocar e segurar) em um ponto de dados de um visual.
2. A dica de ferramenta será exibida e, se o drill-through estiver definido, o rodapé da dica de ferramenta mostrará a seta de drill-through.
3. Toque na seta para fazer drill-through

    ![Tocar em drill-through](././media/mobile-apps-view-phone-report/report-drill-through1.png)

4. Escolher a página de relatório para fazer drill-through

    ![Escolher página do relatório](././media/mobile-apps-view-phone-report/report-drill-through2.png)

5. Use o botão Voltar no cabeçalho do aplicativo para voltar à página na qual você iniciou a navegação.


## <a name="next-steps"></a>Próximas etapas
* [Criar relatórios otimizados para os aplicativos móveis do Power BI](../../create-reports/desktop-create-phone-report.md)
* [Criar uma exibição de telefone de um dashboard no Power BI](../../create-reports/service-create-dashboard-mobile-phone-view.md)
* [Criar visuais responsivos otimizados para qualquer tamanho](../../visuals/desktop-create-responsive-visuals.md)
* Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
