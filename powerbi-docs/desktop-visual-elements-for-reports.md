---
title: Usar elementos visuais para aprimorar os relatórios do Power BI
description: Usar elementos visuais, como papéis de parede e cabeçalhos visuais, para aprimorar relatórios
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 87d530bdf966e549e67427f68fa8b23895120e48
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "65514064"
---
# <a name="use-visual-elements-to-enhance-power-bi-reports"></a>Usar elementos visuais para aprimorar os relatórios do Power BI

Com o **Power BI Desktop**, você pode usar elementos visuais, como papel de parede e cabeçalhos visuais aprimorados para visualizações, para melhorar a aparência dos relatórios.

![Adicionar papel de parede e pequenos cabeçalhos visuais para aprimorar relatórios](media/desktop-visual-elements-for-reports/visual-elements-for-reports_01.png)

A partir da versão de julho de 2018 do **Power BI Desktop**, passa a ser possível aplicar melhorias nos relatórios, tornando as análises e relatórios ainda mais atraentes do que nunca. Dentre as melhorias tratadas neste artigo estão: 

* A aplicação de um **papel de parede** a relatórios para que o plano de fundo realce ou destaque os elementos da história que você deseja contar com os dados
* O uso melhorado de **cabeçalhos visuais** para visualizações individuais com o propósito de criar elementos visuais perfeitamente alinhados na tela do relatório. 

As seções a seguir descrevem como usar esses aprimoramentos e como aplicá-los aos relatórios.

## <a name="using-wallpaper-in-power-bi-reports"></a>Uso do papel de parede em relatórios do Power BI

Você pode formatar a área cinzenta fora da página do relatório usando um **papel de parede**. A seta na imagem a seguir mostra onde se aplica a área do papel de parede. 

![O papel de parede preenche a área cinzenta ao redor de um relatório](media/desktop-visual-elements-for-reports/visual-elements-for-reports_02.png)

É possível definir um papel de parede para cada página do relatório ou usar o mesmo papel de parede para todas as páginas. Para definir o papel de parede, toque ou clique no ícone de **Formatação** quando nenhum elemento visual estiver selecionado no relatório e o cartão do **papel de parede** aparecerá no painel.

![Área do papel de parede no Painel de formatação](media/desktop-visual-elements-for-reports/visual-elements-for-reports_03.png)

É possível aplicar uma cor como **papel de parede** selecionando a lista suspensa **Cor** ou o botão **Adicionar imagem** para selecionar uma imagem a ser aplicada como papel de parede. Também é possível aplicar transparência ao papel de parede, seja a uma cor ou imagem, usando o controle deslizante **Transparência**.

Vale lembrar as seguintes definições pertencentes ao **papel de parede**:

* A área cinzenta externa à área do relatório é o **papel de parede**
* A área da tela onde você pode inserir os elementos visuais é conhecida como a **página** do relatório, que pode ser modificada no **Painel Formatar** usando a lista suspensa **Plano de fundo da página**.

A **página** do relatório sempre fica em primeiro plano (em relação ao papel de parede), enquanto o **papel de parede** fica por trás, sendo o elemento mais ao fundo da página do relatório. Ao aplicar transparência à página, os elementos visuais do relatório também ficam transparentes, permitindo que o papel de parede fique visível no segundo plano através dos elementos visuais.

As configurações padrão para todos os novos relatórios são as seguintes:

* A **página** do relatório é definida como **branco** e a transparência como **100%**
* O **papel de parede** é definido para **branco** e a transparência para **0%**

Se você definir a transparência do plano de fundo da página para mais de 50%, uma borda pontilhada aparecerá enquanto você estiver criando ou editando o relatório, para mostrar o limite da borda da tela do relatório. 

![Uma transparência superior a 50% resulta em uma borda pontilhada](media/desktop-visual-elements-for-reports/visual-elements-for-reports_04.png)

É importante observar que o limite pontilhado *só* aparece ao editar o relatório e *não* é exibido para as pessoas que estiverem visualizando o relatório publicado, da forma como aparece ao ser exibido no **Serviço do Power BI**.

> [!NOTE]
> Se você usa telas de fundo de cor escura para papel de parede e define a cor do texto como branca ou muito clara, esteja ciente de que o recurso **Exportar para PDF** não inclui o papel de parede; portanto, qualquer exportação com fontes brancas ficará quase invisível no arquivo PDF exportado. Consulte [exportar para PDF](desktop-export-to-pdf.md) para obter mais informações em **Exportar para PDF**.


## <a name="using-improved-visual-headers-in-power-bi-reports"></a>Uso de cabeçalhos visuais aprimorados em relatórios do Power BI

A partir da versão de julho de 2018 do **Power BI Desktop**, os cabeçalhos dos elementos visuais nos relatórios passam a ter uma melhoria significativa. Os principais aprimoramentos se referem ao cabeçalho, que foi desconectado do elemento visual para que a posição dele possa ser ajustada com base em sua preferência de layout e posicionamento, e que ele agora é exibido dentro do próprio elemento visual, em vez de ficar flutuante sobre este. 

O cabeçalho é exibido por padrão dentro do elemento visual, alinhado com o título. Na imagem a seguir, você pode ver o cabeçalho (os ícones de fixação, de expansão e de reticências) dentro do elemento visual e alinhados à direita, ao longo da mesma posição horizontal que o título do elemento visual.

![Os cabeçalhos visuais agora podem ficar dentro de um elemento visual ou serem movidos](media/desktop-visual-elements-for-reports/visual-elements-for-reports_05.png)

Se o elemento visual não tiver um título, o cabeçalho flutuará acima da parte superior dele, alinhado à direita, conforme a imagem a seguir. 

![Cabeçalhos visuais flutuando sobre elementos visuais na ausência de títulos](media/desktop-visual-elements-for-reports/visual-elements-for-reports_07.png)

Se o elemento visual estiver totalmente posicionado na parte superior do relatório, o cabeçalho visual então se encaixa na parte inferior do elemento visual. 

![Cabeçalhos visuais se encaixam na parte inferior ao encostar na parte superior do relatório](media/desktop-visual-elements-for-reports/visual-elements-for-reports_08.png)

Todo elemento visual também tem um cartão na seção de **Formatação** do painel de **Visualizações** chamado **Cabeçalho visual**. Nesse cartão, é possível ajustar todo tipo de característica do cabeçalho visual

![Todo elemento visual tem um cartão de Cabeçalho visual no Painel de formatação](media/desktop-visual-elements-for-reports/visual-elements-for-reports_09.png)

> [!NOTE]
> A exibição dos botões de alternância não afetam o relatório durante a criação ou edição. É necessário publicar o relatório e exibi-lo no modo de leitura para ver o efeito. Esse comportamento garante que as várias opções fornecidas nos cabeçalhos visuais sejam importantes durante a edição, especialmente os ícones de aviso que alertam quanto a problemas durante a edição.

Para os relatórios que aparecem apenas no **Serviço do Power BI**, é possível ajustar o uso de cabeçalhos visuais acessando **Meu workspace &gt; Relatórios** e selecionando o ícone **Configurações**. Lá você verá as definições do relatório para o qual selecionou **Configurações** e pode ajustá-las a partir daí, conforme mostrado na imagem a seguir.

![Configurações no serviço do Power BI para uso de cabeçalhos visuais aprimorados](media/desktop-visual-elements-for-reports/visual-elements-for-reports_10.png)

### <a name="enabling-improved-visual-headers-for-existing-reports"></a>Habilitar cabeçalhos visuais aprimorados para relatórios existentes

O novo cabeçalho visual é o comportamento padrão para todos os novos relatórios. Para os relatórios existentes, é preciso habilitar esse comportamento no **Power BI Desktop** acessando **Arquivo > Opções e configurações > Opções** e depois, na seção **Configurações do relatório**, habilitar a caixa de seleção **Usar o cabeçalho visual moderno com as opções de estilo atualizadas**.

![Os relatórios existentes devem ter marcada a caixa de seleção Opções para usar os cabeçalhos visuais aprimorados](media/desktop-visual-elements-for-reports/visual-elements-for-reports_06.png)


## <a name="next-steps"></a>Próximas etapas
Para obter mais informações sobre o **Power BI Desktop** e como começar, confira os artigos a seguir.

* [O que é o Power BI Desktop?](desktop-what-is-desktop.md)
* [Visão geral de Consulta com o Power BI Desktop](desktop-query-overview.md)
* [Fontes de dados no Power BI Desktop](desktop-data-sources.md)
* [Conectar-se a dados no Power BI Desktop](desktop-connect-to-data.md)
* [Formatar e combinar dados com o Power BI Desktop](desktop-shape-and-combine-data.md)
* [Tarefas comuns de consulta no Power BI Desktop](desktop-common-query-tasks.md)   

