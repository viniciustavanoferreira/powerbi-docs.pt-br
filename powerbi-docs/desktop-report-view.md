---
title: Exibição de Relatório no Power BI Desktop
description: Exibição de Relatório no Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 09/19/2019
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 06b8c9d0be2ec8bc5b350767263bfc5e0ab4ec81
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/09/2019
ms.locfileid: "73877861"
---
# <a name="report-view-in-power-bi-desktop"></a>Exibição de Relatório no Power BI Desktop
Se você já trabalhou com o Power BI, você sabe como é fácil criar relatórios que fornecem ideias e perspectivas dinâmicas sobre seus dados. O Power BI também conta com recursos mais avançados no Power BI Desktop. Com o Power BI Desktop, você pode criar consultas avançadas, efetuar mashup de dados provenientes de várias fontes, criar relações entre tabelas e muito mais.

O Power BI Desktop inclui um **Modo de Exibição de Relatório**, no qual você pode quantas páginas de relatório desejar com visualizações. O Modo de Exibição de Relatório oferece praticamente a mesma experiência de design que aquela encontrada no Modo de Exibição de Edição de um relatório no serviço do Power BI. Você pode mover as visualizações de um lugar para outro, copiar e colar, mesclar, etc.

A diferença entre eles é que ao usar o Power BI Desktop, você pode trabalhar com suas consultas e modelar seus dados para garantir que os dados deem suporte às melhores ideias em seus relatórios. Você pode, então, salvar o seu arquivo do Power BI Desktop onde quiser, seja em sua unidade local ou na nuvem.

## <a name="lets-take-a-look"></a>Vamos dar uma olhada!
Quando carregar dados pela primeira vez no Power BI Desktop, você verá o **Modo de Exibição de Relatório** com uma tela em branco.

![Power BI Desktop](media/desktop-report-view/pbi_reportviewinpbidesigner_reportview.png)

Você pode alternar entre o **Modo de Exibição de Relatório**, o **Modo de Exibição de Dados** e o **Modo de Exibição de Relação** selecionando os ícones no painel de navegação esquerdo:

![Ícone de Exibição de Relatório](media/desktop-report-view/pbi_reportviewinpbidesigner_changeview.png)

Depois de adicionar alguns dados, você pode adicionar campos a uma nova visualização na tela.

![Adicionar um elemento visual arrastando-o do painel Campos](media/desktop-report-view/pbid_reportview_addvis.gif)

Para alterar o tipo da visualização, você poderá selecioná-la no grupo **Visualizar** na faixa de opções, ou então você pode clicar com o botão direito do mouse e selecionar um tipo diferente no ícone **Alterar tipo de visualização**.

![Alterar um elemento visual selecionando um novo](media/desktop-report-view/pbid_reportview_changevis.gif)

> [!TIP]
> Certifique-se de experimentar os diferentes tipos de visualização. É importante que sua visualização transmita com clareza as informações presentes em seus dados.

Um relatório terá pelo menos uma página em branco para ser iniciado. As páginas são exibidas no painel de navegação à esquerda da tela. Você pode adicionar todos os tipos de visualizações a uma página, mas é importante não exagerar. Um excesso de visualizações em uma página dará a ela uma aparência congestionada e tornará difícil encontrar as informações corretas. Você pode adicionar novas páginas ao seu relatório. Basta clicar em **Nova Página** na faixa de opções.

![Ícone de Nova Página](media/desktop-report-view/pbidesignerreportviewnewpage.png)

Para excluir uma página, clique no **X** na guia da página na parte inferior do Modo de Exibição de Relatório.

![Adicionar uma página a um relatório](media/desktop-report-view/pbi_reportviewinpbidesigner_deletepage.png)

> [!NOTE]
> Visualizações e relatórios não podem ser anexados a um dashboard por meio do Power BI Desktop. Para fazer isso, você precisará [Publicar por meio do Power BI Desktop](desktop-upload-desktop-files.md) para o seu site do Power BI.

## <a name="copy-and-paste-between-reports"></a>Copiar e colar entre relatórios

Você pode usar um elemento visual de um relatório do Power BI Desktop em outro, simplesmente copiando e colando-o em outro relatório. Basta usar o atalho de teclado **Ctrl+C** para copiar o visual do seu relatório e, depois, no outro relatório do Power BI Desktop, use **Ctrl+V** para colar o elemento visual. Selecione para copiar um elemento visual por vez ou todos de uma página, e cole no relatório de destino do Power BI Desktop. 

A capacidade de copiar e colar elementos visuais é útil para pessoas que criam e atualizam vários relatórios frequentemente. Ao copiar entre arquivos, as configurações e formatação definidas explicitamente no painel de formatação serão utilizadas, enquanto os elementos visuais que dependem do tema ou das configurações padrão são atualizados automaticamente de acordo com o tema do relatório de destino. Portanto, quando você consegue deixar a formatação do visual exatamente como quer, pode copiar e colar esse visual em novos relatórios e preservar todo o trabalho de formatação.

Se os campos do modelo forem diferentes, você verá um erro no visual e um aviso sobre quais campos não existem. O erro é semelhante à experiência exibida ao excluir um campo no modelo usado por um visual. 

![Erro ao copiar/colar o visual – nenhum campo de dados](media/desktop-report-view/report-view_07.png)

Para corrigir o erro, basta substituir os campos inválidos pelos campos que você deseja usar do modelo do relatório no qual você colou o visual. Se você estiver usando um visual personalizado, também deverá importar esse visual personalizado para o relatório de destino.




## <a name="hide-report-pages"></a>Ocultar páginas de relatório

Quando você cria um relatório, também poderá ocultar as páginas de um relatório. Isso poderá ser útil se você precisar criar dados subjacentes ou elementos visuais em um relatório, mas não quiser que essas páginas fiquem visíveis para outras pessoas, como quando você cria tabelas ou elementos visuais de suporte que são usados em outras páginas do relatório. Há muitas outras razões criativas para você talvez querer criar uma página de relatório e, em seguida, ocultá-la de um relatório que quiser publicar. 

Ocultar uma página de relatório é fácil. Basta clicar na guia da página de relatório e selecionar **Ocultar** no menu que é exibido.

![Opção Ocultar Página](media/desktop-report-view/report-view_05.png)

Há algumas considerações para ter em mente ao ocultar uma página de relatório:

* Você ainda pode ver um relatório oculto quando estiver no **Power BI Desktop**, embora o título da página esteja esmaecido. Na imagem a seguir, a página 4 estará oculta.

    ![página esmaecida que está oculta](media/desktop-report-view/report-view_06.png)

* Você *não pode* ver uma página de relatório oculta ao exibir o relatório no **serviço do Power BI**.

* Ocultar uma página de relatório *não* é uma medida de segurança. A página ainda pode ser acessada por usuários e seu conteúdo ainda será acessível usando o detalhamento e outros métodos.

* Quando uma página é oculta, quando está no modo de Visualização, nenhuma seta de navegação do modo de exibição será mostrada.

