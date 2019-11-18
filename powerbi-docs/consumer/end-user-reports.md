---
title: Relatórios no serviço do Power BI
description: Relatórios no serviço do Power BI para consumidores
author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 09/05/2019
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: 3f6f534b71ba6d8e8798418275c4758a95fc6fb5
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/09/2019
ms.locfileid: "73851218"
---
# <a name="reports-in-power-bi"></a>Relatórios no Power BI

[!INCLUDE [power-bi-service-new-look-include](../includes/power-bi-service-new-look-include.md)]

Um relatório do Power BI é uma exibição de um conjunto de dados em várias perspectivas, com visuais que representam as diferentes descobertas e informações obtidas por meio desse conjunto de dados.  Um relatório pode ter um único visual ou páginas repletas de visuais. Dependendo da sua função de trabalho, você pode ser alguém que *cria* relatórios. Você também pode ser alguém que *consome* ou usa relatórios. Este artigo é para *consumidores*.

![Captura de tela de uma página de relatório.](./media/end-user-reports/power-bi-report.png)

A. Esse relatório tem seis páginas (ou guias), e você está visualizando a página **Sentimento**.    
B. Nesta página estão cinco visuais diferentes e um título de página.    
C. O painel *Filtros* mostra a nós um filtro aplicado a todas as páginas do relatório. Para recolher o painel Filtros, selecione a seta ( **>** ).    
D. A faixa do Power BI exibe o nome do relatório e a data da última atualização. Selecione a seta para abrir um menu que também mostra o nome do proprietário do relatório.    
E. A barra de ação contém ações que você pode executar neste relatório.  Por exemplo, é possível adicionar um comentário, exibir um indicador ou exportar dados do relatório.  Selecione as reticências **Mais opções** (...) para revelar uma lista de funcionalidades de relatório adicionais.    

Se for novo no Power BI, você poderá obter uma boa base lendo [Conceitos básicos para consumidores do serviço do Power BI](end-user-basic-concepts.md). Os relatórios estão disponíveis para visualização, compartilhamento e anotações em dispositivos móveis. Para obter mais informações, consulte [Explorar relatórios nos aplicativos móveis do Power BI](mobile/mobile-reports-in-the-mobile-apps.md).

## <a name="advantages-of-reports"></a>Vantagens dos relatórios

O Power BI baseia um relatório em um único conjunto de dados. Os *designers* de relatório criam os visuais em um relatório que representa uma pepita de informações. Os visuais não são estáticos.  Eles são atualizados à medida que os dados subjacentes se alteram. Você pode interagir com os visuais e os filtros conforme examinar os dados para descobrir insight e procurar respostas. Assim como um dashboard, um relatório é altamente interativo e personalizável.

### <a name="safely-interact-with-content"></a>Interagir com o conteúdo de modo seguro

À medida que você explorar e interagir com seu conteúdo: filtrar, dividir, assinar e exportar, não é possível dividir os relatórios. Seu trabalho não afeta o conjunto de dados subjacente nem o conteúdo compartilhado original. Isso se aplica a dashboards, relatórios e aplicativos.

> [!NOTE]
> Lembre-se de que você não pode prejudicar os seus dados. O Power BI é um ótimo lugar para que você possa explorar e experimentar sem se preocupar em prejudicar algo.

### <a name="save-your-changes-or-revert-to-the-default-settings"></a>Salvar as alterações ou reverter para as configurações padrão

Isso não significa que não é possível salvar suas alterações. Você pode fazê-lo, mas essas alterações afetam apenas a sua exibição do conteúdo. Para reverter para a exibição padrão original do relatório, selecione **Redefinir para padrão**.

![Captura de tela do ícone Reverter ao padrão.](./media/end-user-reports/power-bi-reset.png)

## <a name="dashboards-versus-reports"></a>Dashboards versus relatórios

Os [dashboards](end-user-dashboards.md) costumam ser confundidos com relatórios, pois eles também são telas preenchidas com visuais. Mas existem algumas diferenças importantes.  

| **Funcionalidade** | **Dashboards** | **Relatórios** |
| --- | --- | --- |
| Páginas |Uma página |Uma ou mais páginas |
| Fontes de dados |Um ou mais relatórios e um ou mais conjuntos de dados por dashboard |Um único conjunto de dados por relatório |
| Filtragem |Não é possível filtrar ou fatiar |Diferentes maneiras de filtrar, realçar e fatiar |
| Definir alertas |Pode criar alertas para enviar por email quando o dashboard atende a determinadas condições |Não |
| Recurso |Pode definir um dashboard como o dashboard em destaque |Não é possível criar um relatório em destaque |
| Pode ver campos e tabelas do conjunto de dados subjacentes |Não. Pode exportar dados, mas não consegue ver tabelas de conjunto de dados e campos no dashboard de controle em si |Sim. Pode ver as tabelas de conjunto de dados e os campos e valores que você tem permissão para ver |
| Personalização |Não  |Pode filtrar, exportar, exibir conteúdo relacionado, adicionar indicadores, gerar códigos QR, analisar no Excel e muito mais |

<!--| Available in Power BI Desktop |No |Yes, can create and view reports in Desktop |
| Pinning |Can pin existing visuals (tiles) only from current dashboard to your other dashboards |Can pin visuals (as tiles) to any of your dashboards. Can pin entire report pages to any of your dashboards. | -->

## <a name="report-designers-and-report-consumers"></a>Designer de relatórios e consumidores de relatório

Dependendo da função, você pode ser alguém um *designer*, alguém que cria relatórios para seu próprio uso ou para compartilhar com colegas. Você deseja saber como criar e compartilhar relatórios.

Ou você pode ser um *consumidor*, alguém que recebe os relatórios de outras pessoas. Você deseja saber como entender e interagir com os relatórios. Se você for um *consumidor* de relatórios, estes links são para você:

* Comece com um [tour pelo serviço do Power BI](end-user-basic-concepts.md) para saber em que local encontrar relatórios e ferramentas de relatório.
* Saiba como [abrir um relatório](end-user-report-open.md) e todas as [interações disponíveis para os consumidores](end-user-reading-view.md).
* Familiarize-se com relatórios fazendo um tour em um dos nossos [exemplos](../sample-tutorial-connect-to-the-samples.md).  
* Para ver qual conjunto de dados o relatório está usando e quais painéis estão exibindo visuais do relatório (*marcações*), confira [Exibir conteúdo relacionado no serviço do Power BI](end-user-related.md).

> [!TIP]
> Se você não encontrar o que está procurando aqui, use o Sumário à esquerda para procurar todos os artigos de *Relatório*.

## <a name="next-steps"></a>Próximas etapas

[Abrir e exibir um relatório](end-user-report-open.md)    
[Dashboards no serviço do Power BI](end-user-dashboards.md)