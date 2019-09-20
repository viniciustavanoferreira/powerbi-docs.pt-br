---
title: Usar o detalhamento entre relatórios no Power BI Desktop
description: Saiba como fazer uma detalhamento de um relatório para outro no Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 09/10/2019
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: e735d45a7a49c4a0365e35d5bb95957c6145f934
ms.sourcegitcommit: db4fc5da8e65e0a3dc35582d7142a64ad3405de7
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70903769"
---
# <a name="use-cross-report-drillthrough-in-power-bi-desktop"></a>Usar o detalhamento entre relatórios no Power BI Desktop

Com o recurso de detalhamento entre relatórios no Power BI Desktop, você pode saltar contextualmente de um relatório para outro. Isso vale desde que os relatórios estejam dentro do mesmo espaço de trabalho ou aplicativo no serviço do Power BI. Use o detalhamento entre relatórios para conectar dois ou mais relatórios que tenham conteúdo relacionado e passar o contexto de filtro junto com a conexão entre relatórios. Neste artigo, você aprenderá a configurar um detalhamento entre relatórios para relatórios do Power BI, e saberá qual será a experiência dos usuários quando usarem o detalhamento entre relatórios.

![Captura de tela da opção de detalhamento do Power BI Desktop](media/desktop-cross-report-drill-through/cross-report-drill-through-01.png)

É importante entender as definições a seguir antes de começarmos a configurar e usar o detalhamento entre relatórios:

* **Visual de origem:** O visual que invoca a ação de detalhamento usando o menu de contexto visual.
* **Relatório de origem:** O relatório que contém o visual de origem para detalhamento entre relatórios.
* **Página de destino:** A página na qual um usuário chega depois de iniciar uma ação de detalhamento.
* **Relatório de destino:** O relatório que contém a página de destino para detalhamento entre relatórios.


> [!NOTE]
> Os relatórios compartilhados individualmente em *Meu Espaço de Trabalho*, que são relatórios que aparecem como *[Compartilhados comigo](service-share-dashboards.md#share-a-dashboard-or-report)* , só podem ser acessados no espaço de trabalho do qual foram originalmente compartilhados. 


## <a name="enable-cross-report-drillthrough"></a>Habilitar o detalhamento entre relatórios

Para habilitar um relatório como o destino de um detalhamento entre relatórios, você deve habilitar o recurso para esse relatório na janela **Opções**. Acesse **Arquivo** > **Opções e configurações** > **Opções** e acesse as **Configurações do relatório** perto da parte inferior da página à esquerda.

Marque a caixa de seleção **Permitir que os visuais deste relatório usem destinos de detalhamento de outros relatórios**, conforme mostra a imagem a seguir.

![Captura de tela da janela Opções, com Configurações do relatório realçada](media/desktop-cross-report-drill-through/cross-report-drill-through-02.png)

Agora o detalhamento entre relatórios está habilitado.

## <a name="set-up-cross-report-drillthrough"></a>Configurar o detalhamento entre relatórios

A configuração do detalhamento entre relatórios é semelhante à configuração do detalhamento dentro de um relatório. O detalhamento é habilitado na página de destino, permitindo que outros visuais usem a página habilitada para detalhamento. Para obter as etapas de criação do detalhamento em um único relatório, confira [Usar o detalhamento no Power BI Desktop](desktop-drillthrough.md).

Para iniciar o processo de instalação, execute algumas etapas iniciais:

* Configure uma página de destino de detalhamento, que poderá ser acessada de outros relatórios no espaço de trabalho ou aplicativo.
* Permita que um relatório veja as páginas de detalhamento de fora do próprio relatório.

Encontre as opções de detalhamento na seção **Campos** do painel **Visualizações**, conforme mostra a imagem a seguir.

![Captura de tela do painel Visualizações, com as opções de Detalhamento realçadas](media/desktop-cross-report-drill-through/cross-report-drill-through-03.png)

A primeira etapa para habilitar o detalhamento de uma página é validar os modelos de dados dos relatórios de origem e de destino. Verifique se: 

* Os campos que você deseja passar existem nos dois modelos de dados.
* Os nomes dos campos, e os nomes das tabelas aos quais eles pertencem, são idênticos (as cadeias de caracteres também devem corresponder, e diferenciam maiúsculas de minúsculas).

Por exemplo, se você quiser passar um filtro no campo *País* dentro da tabela *Geografia*, os dois modelos devem ter uma tabela *Geografia* e um campo *País* dentro dessa tabela. Caso contrário, você deverá atualizar o nome do campo ou o nome da tabela no modelo subjacente. Simplesmente atualizar o nome de exibição dos campos não funcionará corretamente para detalhamento entre relatórios. (Observe que os esquemas em cada relatório não precisam ser exatamente iguais).

Para começar a configuração, você precisa preparar a página de destino. No Power BI Desktop, acesse a página e verifique se a opção de ativação/desativação de detalhar **Relatório cruzado** está definida como **Ativado**. 

![Captura de tela da opção de ativação/desativação de Relatório cruzado definida como Ativado](media/desktop-cross-report-drill-through/cross-report-drill-through-03.png)

Em seguida, arraste para a tela os campos que você quer usar como o destino do detalhamento. Selecione se você quer que o campo seja usado como uma categoria ou resumido como uma medida. Neste ponto, você pode selecionar se quer desabilitar a opção **Manter todos os filtros** para o visual. Se você não quiser passar outros filtros aplicados do visual de origem para o visual de detalhamento de destino, selecione **Desativado**.

> [!NOTE]
> Se você estiver usando a página apenas para detalhamento entre relatórios, exclua o botão **Voltar** que é adicionado automaticamente. O botão **Voltar** só funciona para navegação dentro de um único relatório. 

Depois de configurar o visual, salve o relatório se você estiver no serviço do Power BI, ou salve e publique o relatório se você estiver usando Power BI Desktop.

A seção anterior descreveu como habilitar o detalhamento entre relatórios para Power BI Desktop (na janela **Opções**). Se você estiver usando o serviço do Power BI para criar um destino de detalhamento entre relatórios, para habilitar o detalhamento entre relatórios você deverá: 

1. Selecionar o espaço de trabalho onde estão o relatório de destino e o relatório de origem.
2. Selecionar **Relatórios**.
3. Selecionar o ícone **Configurações** para o relatório de origem.
4. Verificar se a opção de ativação/desativação de detalhamento entre relatórios está em **Ativado**.
5. Salvar seu relatório.

Isso é tudo. Seu relatório está pronto para a experiência de detalhamento entre relatórios. 

Na próxima seção, vamos ver a experiência da perspectiva do usuário.

## <a name="cross-report-drillthrough-experience"></a>Experiência do detalhamento entre relatórios

Ao configurar a experiência de detalhamento entre relatórios de um relatório, você pode colocar em prática o recurso.

Selecione o relatório de origem no serviço do Power BI e, depois, selecione um visual que usa o campo ou campos da maneira que você especificou ao configurar a página de destino. Em seguida, clique com o botão direito do mouse em um ponto de dados para abrir o menu de contexto visual, e selecione **Detalhamento**.

![Captura de tela do relatório de origem no serviço do Power BI, com Detalhamento realçado](media/desktop-cross-report-drill-through/cross-report-drill-through-01.png)

Em seguida, você verá os resultados na página de detalhamento entre relatórios de destino, assim como você os configurou quando criou o destino. Os resultados são filtrados de acordo com as configurações de detalhamento.

> [!IMPORTANT]
> O Power BI armazena em cache os destinos de detalhamento entre relatórios. Se você fizer alterações, atualize o navegador, caso não veja os destinos de detalhamento. 

Os destinos entre relatórios são formatados da seguinte maneira: 

`Target Page Name [Target Report Name]`

Após a seleção da página de destino na qual você quer aplicar o detalhamento, o Power BI acessa essa página. Ele passa o contexto de filtro com base nas configurações da página de destino. 

O contexto de filtro do visual de origem pode incluir o seguinte: 

* Filtros no nível do relatório, da página e do visual que afetam o visual de origem. 
* Filtro e realce cruzados que afetam o visual de origem. 
* Segmentações de dados na página e segmentações de dados de sincronização.
* Parâmetros de URL.

Ao chegar ao relatório de destino para detalhamento, o Power BI aplica apenas os filtros dos campos nos quais encontra correspondências exatas de cadeias de caracteres para nome de campo e nome de tabela. O Power BI não aplica filtros temporários do relatório de destino. No entanto, ele aplica o seu indicador pessoal padrão, se houver um. Por exemplo, se o seu indicador pessoal padrão incluir um filtro no nível do relatório para *País = EUA*, o Power BI aplicará esse filtro primeiro, antes de aplicar o contexto de filtro do visual de origem. 

Para o detalhamento entre relatórios, o Power BI passa o contexto de filtro para todas as páginas padrão no relatório de destino. O Power BI não passa o contexto de filtro para páginas de dica de ferramenta, pois essas páginas são filtradas com base no visual de origem que invoca a dica de ferramenta.

Se você quiser retornar ao relatório de origem após a ação de detalhamento entre relatórios, use o botão **Voltar** do navegador. 

## <a name="next-steps"></a>Próximas etapas

Você também pode estar interessado nos seguintes artigos:

* [Usando segmentações no Power BI Desktop](visuals/power-bi-visualization-slicers.md)
* [Usar o detalhamento no Power BI Desktop](desktop-drillthrough.md)

