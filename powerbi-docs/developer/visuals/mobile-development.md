---
title: Desenvolvimento móvel
description: Como criar visuais do Power BI compatíveis com dispositivos móveis
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 03/12/2019
ms.openlocfilehash: 38e6ac3be143381304f1fdfc8e1427b91f398a9a
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82196619"
---
# <a name="how-to-create-mobile-friendly-power-bi-visuals"></a>Como criar visuais do Power BI compatíveis com dispositivos móveis
O consumo móvel tem uma função importante no Power BI. Um dos pontos fortes é permanecer conectado aos seus dados a qualquer momento, em qualquer lugar.

Como desenvolvedor que cria visuais do Power BI, as restrições exclusivas de cada dispositivo móvel precisam ser levadas em conta para alcançar o máximo de usuários possível e proporcionar a melhor experiência móvel.

Use o [aplicativo do Power BI para Windows, iOS e Android](/power-bi/consumer/mobile/mobile-apps-for-mobile-devices) para oferecer aos usuários empresariais uma visão abrangente dos dados em qualquer lugar e ao alcance deles.

## <a name="requirements"></a>Requisitos

Os seguintes requisitos são essenciais para o desenvolvimento de visuais compatíveis com dispositivos móveis:

- Renderizar

  Os visuais do Power BI precisam ser renderizados em todos os dispositivos móveis compatíveis, incluindo navegadores e aplicativos compatíveis, sem erros em relatórios, dashboards ou quando executados no modo de **foco**. 

- Interativo

  A funcionalidade interativa precisa ser fornecida da mesma maneira que é fornecida para dispositivos de desktop. Todos os eventos processados em navegadores da área de trabalho precisam ter suporte ou ter manipuladores de eventos comparáveis em dispositivos móveis.
  
  Por exemplo, a navegação básica e a seleção de pontos de dados devem ter a mesma funcionalidade encontrada nos navegadores da área de trabalho. Se um visual der suporte à seleção múltipla com **CTRL**, o desenvolvedor precisará considerar a possibilidade de adicionar um manipulador de eventos semelhante aos dispositivos móveis.

  A tabela a seguir fornece uma lista de eventos correspondentes em dispositivos móveis.

  | Nome do evento de mouse | Nome do evento de toque |
  |:----------------:|:----------------:|
  | `click` | `click` |
  | `mousemove` | `touchmove` |
  | `mousedown` | `touchstart` |
  | `mouseup` | `touchend` |
  | `dblclick` | usar uma biblioteca externa |
  | `contextmenu` | usar uma biblioteca externa |
  | `mouseover` | `touchmove` |
  | `mouseout` | `touchmove` (ou uma biblioteca externa) |
  | `wheel` | `NaN` |

  > [!NOTE]
  > Nem todos os dispositivos móveis ou de tela touch dão suporte a eventos de mouse (ou prefixados com *mouse*). Nesses casos, processe os eventos de *mouse* e de *toque* ao mesmo tempo.

## <a name="optional"></a>Opcional
Os itens a seguir são considerados opcionais e usados para criar uma melhor experiência do usuário final.

- Renderizar

  Para dar suporte a tamanhos de visuais menores, tente adicionar opções de formato que o usuário poderá alterar para ajustar o tamanho de cada elemento. Por exemplo, adicione opções de formato de rótulos para uso em relatórios e dashboards. Isso permite que os usuários personalizem um visual especificamente para os dispositivos móveis.
  
  As mesmas configurações também podem ser aplicadas aos visuais em navegadores da área de trabalho e, se necessário, substituídas para adaptar o visual a telas menores.

  > [!NOTE]
  > Para otimizar um visual no modo de **foco**, as orientações de tamanho de tela retrato e paisagem precisam ser consideradas; confira [Exibir o conteúdo no modo de foco](/power-bi/consumer/end-user-focus).

- Interativo

  Considere a possibilidade de adicionar manipuladores de eventos específicos de dispositivos móveis, como arrastar e rolar.

- Failover

  Um visual deverá mostrar um erro descritivo se não puder ser renderizado no dispositivo móvel.

## <a name="supported-browsers-and-devices"></a>Navegadores e dispositivos com suporte
O visual do Power BI precisará ser renderizado em todos os dispositivos que dão suporte a aplicativos do Power BI. Para obter mais informações, confira [Navegadores compatíveis com o Power BI](/power-bi/power-bi-browsers) e [Aplicativos móveis do Power BI](/power-bi/consumer/mobile/mobile-apps-for-mobile-devices).

Ao testar os modelos mais recentes de dispositivos Windows, iOS e Android, o desenvolvedor precisa considerar a maioria desses aspectos de qualidade.

## <a name="next-steps"></a>Próximas etapas
Para começar, confira [Tutorial: Como desenvolver um visual no Power BI](/power-bi/developer/visuals/custom-visual-develop-tutorial).
