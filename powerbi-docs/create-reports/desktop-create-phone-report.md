---
title: Otimizar relatórios para os aplicativos móveis do Power BI
description: Aprenda a otimizar as páginas de relatório para aplicativos móveis do Power BI criando uma versão de retrato do relatório, especificamente para telefones e tablets.
author: paulinbar
ms.reviewer: ''
ms.custom: contperfq4
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: how-to
ms.date: 06/15/2020
ms.author: painbar
LocalizationGroup: Create reports
ms.openlocfilehash: b9161813c291a3feb8c01e4201972337f8e96fcb
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.contentlocale: pt-BR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85221770"
---
# <a name="optimize-power-bi-reports-for-the-mobile-app"></a>Otimizar relatórios do Power BI para o aplicativo móvel
Os usuários móveis podem exibir qualquer página de relatório do Power BI na orientação paisagem. No entanto, os autores de relatório podem criar uma exibição adicional otimizada para dispositivos móveis que é exibida na orientação retrato. Essa opção de design, disponível no Power BI Desktop e no serviço do Power BI, permite aos autores selecionar e reorganizar apenas os visuais que façam sentido para os usuários móveis em trânsito.

![Relatório otimizado para dispositivos móveis](media/desktop-create-phone-report/desktop-mobile-optimized-report.png).

O Power BI fornece uma série de recursos que ajudam você a criar versões otimizadas para dispositivos móveis de seus relatórios:
* Uma exibição de layout móvel na qual você pode criar seu relatório otimizado para dispositivos móveis arrastando e soltando visuais em uma tela de emulador de telefone.
* Visuais e segmentações que podem ser otimizados para uso em telas pequenas e móveis.

Esses recursos possibilitam o design e a criação de relatórios atraentes e interativos, otimizados para dispositivos móveis.

## <a name="create-a-mobile-optimized-portrait-version-of-a-report-page"></a>Criar uma versão retrato otimizada para dispositivos móveis de uma página de relatório

A primeira etapa é projetar e criar o relatório na exibição da Web normal. Depois de criar o relatório, você poderá otimizá-lo para telefones e tablets.

Para criar a exibição otimizada para dispositivos móveis, abra a exibição de layout móvel:
   * No Power BI Desktop, selecione a faixa de opções **Exibir** e escolha **Layout móvel**.
   * Na serviço do Power BI, escolha **Mais opções (...) > Editar relatório > Layout Móvel**.

   Você vê uma tela rolável com formato de telefone e um painel **Visualizações**, que lista todos os visuais que estão na página do relatório original.

   ![Exibição de layout móvel](media/desktop-create-phone-report/desktop-mobile-layout.png).

* Cada visual no painel **Visualizações** aparece com um nome para facilitar a identificação.
* Cada visual também tem um indicador de visibilidade. O indicador de visibilidade de um visual é alterado de acordo com o status de visibilidade do visual no estado atual da exibição de relatório da Web. O indicador de visibilidade é útil ao trabalhar com indicadores.

## <a name="add-visuals-to-the-mobile-layout-canvas"></a>Adicionar visuais à tela de layout móvel
Para adicionar um visual ao layout móvel, arraste-o do painel **Visualizações** para a tela do telefone. Quando você arrasta o visual para a tela, ele se ajusta à grade. Como alternativa, você pode clicar duas vezes no visual no painel de visualização, e o visual será adicionado à tela.

É possível adicionar alguns ou todos os visuais da página de relatório da Web à página de relatório otimizada para dispositivos móveis. Você pode adicionar cada visual apenas uma vez e não precisa incluir todos eles.

>[!NOTE]
> Você pode arrastar e soltar visuais ocultos na tela. Eles serão colocados, mas não mostrados, a menos que seu status de visibilidade seja alterado na exibição de relatório da Web atual.

Os visuais podem ser dispostos em camadas um sobre o outro para criar relatórios interativos usando indicadores ou para criar relatórios atraentes, colocando visuais em camadas sobre imagens.

Depois de colocar um visual na tela, você poderá redimensioná-lo arrastando as alças que aparecem ao lado da borda do visual quando você o seleciona. Para manter a taxa de proporção do visual durante o redimensionamento, pressione a tecla **Shift** ao arrastar as alças de redimensionamento.

A imagem a seguir ilustra como arrastar e soltar visuais do painel **Visualizações** na tela e como redimensionar e sobrepor alguns deles.

   ![Arrastar e soltar, redimensionar e sobrepor visuais](media/desktop-create-phone-report/desktop-mobile-layout-overlay-resize.gif)

A grade do relatório para telefone é dimensionada em telefones de tamanhos diferentes para que o relatório fique bom em telefones com telas pequenas e grandes.

## <a name="remove-visuals-from-the-mobile-layout-canvas"></a>Remover visuais da tela de layout móvel
Para remover um visual do layout móvel, clique no **X** no canto superior direito do visual na tela do telefone ou selecione o visual e pressione **Excluir**.

Você pode remover todas as visualizações da tela clicando na borracha no painel **Visualização**.

A remoção de visuais da tela de layout móvel os remove somente da tela. Os visuais ainda aparecem no painel de visualização, e o relatório original permanece inalterado.

## <a name="configure-visuals-and-slicers-for-use-in-mobile-optimized-reports"></a>Configurar visuais e segmentações para uso em relatórios otimizados para dispositivos móveis

### <a name="visuals"></a>Visuais

Muitos visuais, especialmente os de tipo gráfico, são responsivos por padrão.  Isso significa que eles podem mudar dinamicamente para exibir o máximo de dados e insights, independentemente do tamanho da tela.

O Power BI dá prioridade aos dados conforme o tamanho de um visual muda. Por exemplo, é possível remover automaticamente o preenchimento e mover a legenda para a parte superior do visual, de modo que ele continue informativo, mesmo quando fica menor.

![Redimensionamento do visual responsivo](media/desktop-create-phone-report/desktop-mobile-layout-responsive-visual.gif)
 
Se, por algum motivo, você quiser desativar a capacidade de resposta, poderá fazer isso na seção **Geral** das configurações de formato do visual.

### <a name="slicers"></a>Segmentações

As segmentações oferecem filtragem de dados de relatório na tela. Ao criar segmentações no modo de criação de relatórios regular, você pode modificar algumas configurações de segmentação para torná-las mais utilizáveis em relatórios otimizados para dispositivos móveis:
* Você pode decidir se deseja permitir que os leitores de relatório selecionem apenas um item ou vários.
* Você pode tornar a segmentação vertical, horizontal ou responsiva (as segmentações responsivas devem ser horizontais).

Se você fizer a segmentação responsiva, à medida que altera seu tamanho e sua forma, ela mostrará mais ou menos opções. Ela pode ser alta, baixa, larga ou estreita. Se você a fizer pequena o suficiente, ela se tornará apenas um ícone de filtro na página do relatório.

![Segmentação responsiva do Power BI](media/desktop-create-phone-report/desktop-create-phone-report-8.gif)
 
Leia mais sobre a [criação de segmentações responsivas](power-bi-slicer-filter-responsive.md).

## <a name="publish-a-mobile-optimized-report"></a>Publicar um relatório otimizado para dispositivos móveis
Para publicar uma versão otimizada para dispositivos móveis de um relatório, [publique o relatório principal do Power BI Desktop para o serviço do Power BI](desktop-upload-desktop-files.md). Isso publica a versão otimizada para dispositivos móveis ao mesmo tempo.

## <a name="viewing-optimized-and-unoptimized-reports-on-a-phone-or-tablet"></a>Exibir relatórios otimizados e não otimizados em um telefone ou tablet

Nos aplicativos móveis do Power BI, os relatórios otimizados para dispositivos móveis são indicados por um ícone especial.

![Ícone de relatório otimizado para dispositivos móveis](media/desktop-create-phone-report/desktop-create-phone-report-optimized-icon.png)

Em telefones, o aplicativo detecta automaticamente se o relatório é otimizado para dispositivos móveis ou não.
* Se houver um relatório otimizado para dispositivos móveis, o aplicativo abrirá automaticamente o relatório nesse modo de otimização.
* Se não houver um relatório otimizado para dispositivos móveis, o relatório será aberto na exibição de paisagem não otimizada.

Segurar um telefone na orientação paisagem abre o relatório na exibição não otimizada com o layout de relatório original, independentemente de o relatório ser otimizado ou não.

Se você otimizar apenas algumas páginas, quando os leitores chegarem a uma página não otimizada, eles deverão alternar para a exibição de paisagem. Ao virarem o telefone ou o tablet de lado, eles poderão ver a página no modo paisagem. [Leia mais sobre a interação com relatórios do Power BI otimizados para o modo retrato](../consumer/mobile/mobile-apps-view-phone-report.md).

![Página do telefone não otimizada](media/desktop-create-phone-report/desktop-create-phone-report-9.png)

## <a name="considerations-when-creating-mobile-optimized-layouts"></a>Considerações ao criar layouts otimizados para dispositivos móveis
* Em relatórios com várias páginas, você pode otimizar todas elas ou apenas algumas.
* Se você tiver definido uma cor da tela de fundo para uma página de relatório, o relatório otimizado para dispositivos móveis terá a mesma cor da tela de fundo.
* Não é possível modificar as configurações de formatação apenas para o relatório otimizado. A formatação é consistente entre os layouts mestres e móveis. Por exemplo, os tamanhos de fonte serão os mesmos.
* Para alterar um visual, como a formatação, o conjunto de dados, os filtros ou qualquer outro atributo dele, retorne ao modo de criação de relatórios da Web.

## <a name="next-steps"></a>Próximas etapas
* [Criar uma exibição de telefone de um dashboard no Power BI](service-create-dashboard-mobile-phone-view.md).
* [Exibir relatórios do Power BI otimizados para seu telefone](../consumer/mobile/mobile-apps-view-phone-report.md).
* [Documentação do Power BI sobre a criação de relatórios e dashboards](https://docs.microsoft.com/power-bi/create-reports/).
* Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/).