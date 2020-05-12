---
title: Explorar relatórios nos aplicativos móveis do Power BI
description: Saiba mais sobre como exibir e interagir com relatórios nos aplicativos móveis do Power BI no telefone ou tablet. Você cria relatórios no serviço do Power BI ou Power BI Desktop e então interage com eles nos aplicativos móveis.
author: paulinbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 05/05/2020
ms.author: painbar
ms.openlocfilehash: f2aeb720221fa79aa95f9674aa1e3ac610b28c19
ms.sourcegitcommit: 220910f0b68cb1e265ccd5ac0cee4ee9c6080b26
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82841723"
---
# <a name="explore-reports-in-the-power-bi-mobile-apps"></a>Explorar relatórios nos aplicativos móveis do Power BI
Aplica-se a:

| ![iPhone](././media/mobile-reports-in-the-mobile-apps/ios-logo-40-px.png) | ![iPad](././media/mobile-reports-in-the-mobile-apps/ios-logo-40-px.png) | ![Telefone Android](././media/mobile-reports-in-the-mobile-apps/android-logo-40-px.png) | ![Tablet Android](././media/mobile-reports-in-the-mobile-apps/android-logo-40-px.png) | ![Dispositivos Windows 10](./media/mobile-reports-in-the-mobile-apps/win-10-logo-40-px.png) |
|:---: |:---: |:---: |:---: |:---: |
| iPhones |iPads |Telefones Android |Tablets Android |Dispositivos Windows 10 |

>[!NOTE]
>O suporte de aplicativo móvel Power BI para **telefones que usam o Windows 10 Mobile** será descontinuado em 16 de março de 2021. [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2121400)

Um relatório do Power BI é uma exibição interativa de seus dados, com visuais que representam diferentes descobertas e informações obtidas desses dados. A exibição de relatórios nos aplicativos móveis do Power BI é a terceira etapa de um processo de três etapas:

1. [Criar relatórios no Power BI Desktop](../../desktop-report-view.md). Você pode até mesmo [otimizar um relatório para telefones](mobile-apps-view-phone-report.md) no Power BI Desktop.
2. Publique esses relatórios para o serviço do Power BI [(https://powerbi.com)](https://powerbi.com) ou [Servidor de Relatórios do Power BI](../../report-server/get-started.md).  
3. Interagir com esses relatórios nos aplicativos móveis do Power BI.

## <a name="open-a-power-bi-report-in-the-mobile-app"></a>Abrir um relatório do Power BI no aplicativo móvel
Os relatórios do Power BI são armazenados em locais diferentes no aplicativo móvel, dependendo de onde eles foram obtidos. Eles podem estar em Aplicativos, Compartilhado comigo, Workspaces (incluindo Meu Workspace) ou em um servidor de relatório. Às vezes, você percorre um dashboard relacionado para obter um relatório e, às vezes, ele é listado.

Em listas e menus, você encontrará um ícone ao lado de um nome de relatório, que o ajuda a entender que o item é um relatório:

![Relatórios no Meu Workspace](./media/mobile-reports-in-the-mobile-apps/reports-my-workspace.png)

Há dois ícones para relatórios em aplicativos do Power BI Mobile:

* ![Ícone de Relatório](./media/mobile-reports-in-the-mobile-apps/report-default-icon.png) indica um relatório que aparecerá na orientação paisagem no aplicativo. Ele terá a mesma aparência que em um navegador.

* ![Ícone de relatório para telefone](./media/mobile-reports-in-the-mobile-apps/report-phone-icon.png) Indica um relatório que tem pelo menos uma página otimizada para telefone que aparecerá na orientação retrato.

> [!NOTE]
> Quando você segura o telefone na orientação paisagem, sempre obtém o layout de paisagem, mesmo que a página do relatório esteja no layout do dispositivo móvel.

Para ver um relatório no dashboard, toque em **Mais opções** (...) no canto superior direito do bloco e em **Abrir relatório**:
  
  ![Abrir relatório](./media/mobile-reports-in-the-mobile-apps/power-bi-android-open-report-tile.png)
  
  Nem todos os blocos podem ser abertos como relatórios. Por exemplo, os blocos criados ao fazer uma pergunta na caixa de P e R não abrem relatórios quando você toca neles.
  
## <a name="interact-with-reports"></a>Interagir com relatórios
Depois de abrir um relatório no aplicativo, você pode começar a trabalhar com ele. Você pode fazer muitas coisas com seus relatórios e seus dados. No rodapé do relatório, você encontrará ações que podem ser executadas no relatório. Ao tocar e tocar de modo prolongado nos dados mostrados no relatório, você também pode dividir os dados.

### <a name="single-tap-versus-double-tap-interaction"></a>Interação de toque simples versus toque duplo
Quando você baixa o aplicativo móvel do Power BI, ele é definido com a interação de toque simples. Isso significa que, quando você tocar em um visual para executar alguma ação, como a seleção um item de segmentação, o realce cruzado, o clique em um link ou um botão etc., o toque selecionará o visual e executará a ação desejada.

Se preferir, você poderá alternar para a interação de toque duplo. Com a interação de toque duplo, você primeiro toca em um visual para selecioná-lo e, em seguida, toca novamente no visual para executar a ação desejada.

Para alternar para a interação de toque duplo ou voltar para a interação de toque simples, acesse [Configurações de interação do aplicativo](./mobile-app-interaction-settings.md).

### <a name="single-select-versus-multi-select-mode-for-data-point-selection"></a>Modo de seleção simples versus seleção múltipla para seleção de ponto de dados

Em um relatório, toque em um ponto de dados para selecioná-lo. Você pode escolher se deseja usar o modo de seleção simples ou seleção múltipla. No modo de seleção simples, quando você toca em um ponto de dados para selecioná-lo, essa seleção substitui qualquer outra feita anteriormente. No modo de seleção múltipla, quando você toca em um ponto de dados para selecioná-lo, sua seleção é *adicionada* à atual, e o resultado combinado de todas as seleções é realçado em todos os visuais do relatório.

Para anular a seleção de um ponto de dados selecionado, basta tocar novamente nele.

Para alternar entre o modo de seleção simples e seleção múltipla, acesse [Configurações de interação do aplicativo](./mobile-app-interaction-settings.md).

### <a name="using-tap-and-long-tap"></a>Usando toque e toque longo
Um toque é o mesmo que um clique com o mouse. Portanto, se desejar realizar um realce cruzado do relatório com base em um ponto de dados, toque nesse ponto de dados.
Quando você toca em um valor de segmentação, o valor é selecionado e o restante do relatório é dividido por esse valor.
Quando você toca em um link, botão ou indicador, a ação definida pelo autor do relatório ocorrerá.

Você provavelmente observou que, quando você toca em um visual, uma borda é exibida. No canto superior direito da borda, você verá **Mais opções** (...). Se você tocar nas reticências, verá um menu das ações que você pode executar no visual:

![Visual e menu](./media/mobile-reports-in-the-mobile-apps/report-visual-menu.png)

### <a name="tooltip-and-drill-actions"></a>Dica de ferramenta e ações de detalhamento
Quando você realizar um toque longo (tocar e segurar) em um ponto de dados, será exibida uma dica de ferramenta mostrando os valores que esse ponto de dados representa:

![Dica de ferramenta](./media/mobile-reports-in-the-mobile-apps/report-tooltip.png)

Se o autor do relatório tiver configurado uma dica de ferramenta da página de relatório, a dica de ferramenta padrão será substituída por aquela da página de relatório:

![Dica de ferramenta de página de relatório](./media/mobile-reports-in-the-mobile-apps/report-page-tooltip.png)

> [!NOTE]
> As dicas de ferramentas de relatório são compatíveis com dispositivos com visores de pelo menos 640 pixels e 320 pixels. Se o dispositivo for menor, o aplicativo usará mostrará as dicas de ferramenta padrão.

Os autores de relatório podem definir hierarquias nos dados e relações entre as páginas de relatório. As hierarquias permitem fazer drill down, fazer drill up e detalhar outra página de relatório usando um visual e um valor. Assim, quando realizar toque longo em um valor, além da dica de ferramenta, as opções de análise relevantes serão exibidas no rodapé:

![Ações de detalhamento](./media/mobile-reports-in-the-mobile-apps/report-drill-actions.png)


Quando você toca em uma parte específica de um visual e então toca na opção *Detalhamento*, o Power BI leva a uma página diferente no relatório, filtrada com o valor tocado. O autor de um relatório pode definir uma ou mais opções de detalhamento, cada uma levando a uma página diferente. Nesse caso, você pode escolher para qual opção deseja exibir o detalhamento. O botão voltar retorna à página anterior.


Para obter mais informações, leia sobre como [adicionar detalhamento no Power BI Desktop](../../desktop-drillthrough.md).
   
   > [!IMPORTANT]
   > Nos aplicativos móveis do Power BI, as ações de detalhamento em visuais de matriz e de tabela são habilitadas somente por meio de valores de célula, não por meio de cabeçalhos de coluna ou linha.
   
   
   
### <a name="using-the-actions-in-the-report-footer"></a>Usando as ações no rodapé do relatório
No rodapé do relatório, você pode executar várias ações na página de relatório atual ou em todo o relatório. O rodapé dá acesso rápido às ações usadas com mais frequência. Você pode acessar outras ações tocando no botão **Mais opções** (...):

![Rodapé do relatório](./media/mobile-reports-in-the-mobile-apps/report-footer.png)

Você pode realizar estas ações usando o rodapé:
* Redefinir o filtro de relatório e as seleções de realce cruzado de volta para o estado original.
* Abrir o painel de conversa para exibir comentários ou adicionar comentários ao relatório.
* Abrir o painel de filtro para exibir e modificar o filtro aplicado ao relatório no momento.
* Listar todas as páginas no relatório. Tocar no nome de uma página carregará e apresentará essa página.
Você pode percorrer páginas de relatório passando o dedo da borda da tela para o centro.
* Exibir todas as ações de relatório.

#### <a name="all-report-actions"></a>Todas as ações de relatório
Ao tocar no botão de reticências **Mais opções** (...) no rodapé do relatório, você verá todas as ações que podem ser executadas em um relatório:


![Todas as ações de relatório](./media/mobile-reports-in-the-mobile-apps/power-bi-mobile-report-all-actions.png)

Algumas das ações podem ser desabilitadas, pois elas dependem das funcionalidades específicas do relatório.
Por exemplo:

**Indicadores** estarão presentes apenas se [indicadores](mobile-reports-in-the-mobile-apps.md#bookmarks) tiverem sido definidos no relatório. Indicadores pessoais que você pode definir no serviço do Power BI e indicadores definidos pelo criador do relatório são mostrados. Se um dos indicadores tiver sido definido como padrão, o relatório será aberto para essa exibição quando for carregado.

**Anotar e compartilhar** poderá estar desabilitado se houver uma [política de proteção do Intune](https://docs.microsoft.com/intune/app-protection-policies) em sua organização que proíba o compartilhamento usando um aplicativo móvel do Power BI.

**Convidar** estará habilitado somente se você tiver permissão para compartilhar o relatório com outras pessoas. Você terá permissão somente se for o proprietário do relatório ou se o proprietário tiver dado a você a permissão de recompartilhamento.

**Filtrar por local atual** estará habilitado se o autor do relatório tiver classificado o relatório com os dados geográficos. Para obter mais informações, leia sobre [como identificar dados geográficos em um relatório](https://docs.microsoft.com/power-bi/desktop-mobile-geofiltering).

A opção **Verificar para filtrar o relatório por código de barras** só estará habilitada se o conjunto de dados no seu relatório estiver marcado como **Código de barras**. Para obter mais informações, leia sobre [como marcar códigos de barras no Power BI Desktop](https://docs.microsoft.com/power-bi/desktop-mobile-barcodes).

### <a name="bookmarks"></a>Indicadores

O aplicativo móvel do Power BI dá suporte a indicadores de relatório que o criador do relatório definiu e a indicadores pessoais que você pode definir no serviço do Power BI. Você pode encontrar o menu de indicadores em **Mais opções** (…) na [barra de ferramentas de ações de relatório](mobile-reports-in-the-mobile-apps.md#all-report-actions).

Os indicadores padrão são indicados por um ícone especial. Para indicadores pessoais, você pode definir, remover a definição ou alterar a configuração padrão tocando em **Mais opções (...)** ao lado do indicador que deseja alterar e escolhendo **Tornar padrão** ou **Limpar padrão**.

![menu de indicadores](./media/mobile-reports-in-the-mobile-apps/power-bi-mobile-report-bookmark-menu.png)

Quando uma exibição de indicador de um relatório é aberta, o nome do indicador é exibido na parte superior do relatório.

![exibição de indicador](./media/mobile-reports-in-the-mobile-apps/power-bi-mobile-report-bookmark-title.png)

[Saiba mais sobre indicadores no serviço do Power BI](https://docs.microsoft.com/power-bi/consumer/end-user-bookmarks).

## <a name="configure-your-experience-with-reports"></a>Configurar a sua experiência com relatórios
O aplicativo móvel do Power BI tem várias configurações que permitem controlar a sua experiência com relatórios. No momento, é possível configurar as opções a seguir
* **Interação com visuais de relatório**: você pode optar por usar uma interação de toque simples ou toque duplo.
* **Método de atualização de dados**: você pode optar por ter um botão de atualização ou uma ação suspensa para atualizar os dados do relatório.
* **Visibilidade do rodapé do relatório**: você pode optar por ter um rodapé encaixado que sempre esteja visível ou um rodapé dinâmico que é ocultado e novamente exibido, dependendo das suas ações (rolagem, por exemplo).

Confira [Configurações de interação do aplicativo](./mobile-app-interaction-settings.md) para obter informações sobre como alterar essas configurações.


## <a name="next-steps"></a>Próximas etapas
* [Exibir e interagir com relatórios do Power BI otimizados para seu telefone](mobile-apps-view-phone-report.md)
* [Criar uma versão de um relatório otimizado para telefones](../../desktop-create-phone-report.md)
* Dúvidas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)

