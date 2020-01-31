---
title: Definir configurações de interação de relatório
description: Saiba como substituir as configurações de interação padrão para relatórios.
author: paulinbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 01/21/2020
ms.author: painbar
ms.openlocfilehash: fee89c65328b70e1f312b39fbad75d7148bd92f2
ms.sourcegitcommit: 02342150eeab52b13a37b7725900eaf84de912bc
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2020
ms.locfileid: "76542279"
---
# <a name="configure-report-interaction-settings"></a>Definir configurações de interação de relatório

## <a name="overview"></a>Visão geral

O aplicativo móvel Power BI tem várias definições de "interação" configuráveis que permitem controlar como você interage com seus dados e definir como os elementos do aplicativo móvel Power BI se comportam. No momento, há configurações para
* [Interação de toque simples versus duplo em visuais de relatório](#single-tap)
* [Rodapé de relatório encaixado versus dinâmico](#docked-report-footer-android-phones) (Android)
* [Atualização de relatório iniciada por botão versus atualização por pull](#report-refresh-android-phones) (Android)

Para obter as configurações de interação, toque na imagem do seu perfil para abrir o [painel lateral](./mobile-apps-home-page.md#header), escolher **Configurações** e localizar a seção **Interação**.

![Configurações de interação](./media/mobile-app-interaction-settings/powerbi-mobile-app-interactions-section.png)

>[!NOTE]
>As configurações de interação para o botão Atualizar e para encaixar o rodapé do relatório atualmente não têm efeito sobre os relatórios do Servidor de Relatório. Isso será alterado na versão de janeiro de 2020 do Servidor de Relatório.

## <a name="interaction-settings"></a>Configurações de interação

### <a name="single-tap"></a>Toque simples
Quando você baixa o aplicativo móvel do Power BI, ele é definido com a interação de toque simples. Isso significa que, quando você tocar em um visual para executar alguma ação, como a seleção um item de segmentação, o realce cruzado, o clique em um link ou um botão etc., o toque selecionará o visual e executará a ação desejada.

Se preferir, você poderá desativar a interação de toque simples. Você então terá uma interação de toque duplo. Com a interação de toque duplo, você primeiro toca em um visual para selecioná-lo e, em seguida, toca novamente no visual para executar a ação desejada.

### <a name="docked-report-footer-android-phones"></a>Rodapé de relatório encaixado (telefones Android)

A configuração de rodapé de relatório encaixado determina se o rodapé do relatório permanece encaixado (ou seja, fixo e sempre visível) na parte inferior do relatório ou oculto, reaparecendo com base em suas ações no relatório, como rolagem.

Em telefones Android, a configuração de rodapé de relatório encaixado está **ativada** por padrão, o que significa que o rodapé do relatório fica encaixado e sempre visível na parte inferior do relatório. Alterne a configuração para **desativada** se você preferir um rodapé de relatório dinâmico que apareça e desapareça dependendo de suas ações no relatório.

### <a name="report-refresh-android-phones"></a>Atualização de relatório (telefones Android)

A configuração de atualização de relatório define como você inicia as atualizações de relatório. Você pode optar por ter um botão de atualização em todos os cabeçalhos de relatório ou usar a ação de pull para atualizar (puxar ligeiramente de cima para baixo) na página do relatório para atualizar o relatório. A figura a seguir ilustra as duas alternativas. 

![Botão Atualizar versus atualizar por pull](./media/mobile-app-interaction-settings/powerbi-mobile-app-interactions-refresh-button-versus-pull.png)

Em telefones Android, um botão Atualizar é adicionado por padrão.

Para alterar a configuração de atualização do relatório, acesse o item Atualizar Relatório nas configurações de interação. A configuração atual é mostrada. Toque no valor para abrir uma janela pop-up em que você pode escolher um novo valor.

![Definir atualização](./media/mobile-app-interaction-settings/powerbi-mobile-app-interactions-set-refresh.png)

## <a name="remote-configuration"></a>Configuração remota

Um administrador também pode configurar as interações remotamente usando uma ferramenta de MDM com um arquivo de configuração de aplicativos. Dessa forma, é possível padronizar a experiência de interação do relatório em toda a organização ou para grupos de usuários específicos na organização. Confira [Configurar a interação usando gerenciamento de dispositivo móvel](./mobile-app-configuration.md) para obter detalhes.


## <a name="next-steps"></a>Próximas etapas
* [Como interagir com relatórios](./mobile-reports-in-the-mobile-apps.md#interact-with-reports)
* [Configurar a interação usando o gerenciamento de dispositivo móvel](./mobile-app-configuration.md)
