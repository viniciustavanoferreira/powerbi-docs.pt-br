---
title: Solucionar problemas de compartilhamento de dashboards e relatórios
description: Como resolver problemas para compartilhar relatórios e dashboards do Power BI com colegas dentro e fora de sua organização.
author: maggiesMSFT
ms.reviewer: lukaszp
featuredvideoid: 0tUwn8DHo3s
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: troubleshooting
ms.date: 06/23/2020
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: ef78847829ef292a16856a1597a53c95e7d20708
ms.sourcegitcommit: a453ba52aafa012896f665660df7df7bc117ade5
ms.contentlocale: pt-BR
ms.lasthandoff: 06/27/2020
ms.locfileid: "85486684"
---
# <a name="troubleshoot-sharing-dashboards-and-reports"></a>Solucionar problemas de compartilhamento de dashboards e relatórios

Aqui estão alguns problemas comuns que poderão surgir quando você estiver compartilhando um dashboard ou relatório ou quando outra pessoa estiver compartilhando com você. 

## <a name="dashboard-recipients-see-a-lock-icon-in-a-tile"></a>Os destinatários do dashboard veem um ícone de cadeado em um bloco

As pessoas com as quais você compartilha poderão ver um bloco bloqueado em um painel ou uma mensagem "Permissão necessária" ao tentarem exibir um relatório.

![Bloco do Power BI bloqueado](media/service-share-dashboards/power-bi-locked_tile_small.png)

Nesse caso, você precisa conceder a permissão para o conjunto de dados subjacente.

1. Vá para a guia **Conjuntos de dados** na sua lista de conteúdo.

1. Selecione as reticências ( **...** ) ao lado do conjunto de dados e, em seguida, selecione **Gerenciar permissões**.

    ![Gerenciar permissões](media/service-share-dashboards/power-bi-sharing-manage-permissions.png)

1. Selecione **Adicionar usuário**.

    ![Selecionar Adicionar usuário](media/service-share-dashboards/power-bi-share-dataset-add-user.png)

1. Insira os endereços de email completos dos indivíduos, grupos de distribuição ou grupos de segurança. Você não pode compartilhar com listas de distribuição dinâmicas.

    ![Adicionar endereços de email](media/service-share-dashboards/power-bi-add-user-dataset.png)

1. Selecione **Adicionar**.

## <a name="i-cant-share-a-dashboard-or-report"></a>Não consigo compartilhar um painel ou relatório como favorito

Para compartilhar um dashboard ou relatório, você precisa de permissão para compartilhar novamente o conteúdo subjacente, ou seja, todos os relatórios e conjuntos de dados relacionados. Se você vir uma mensagem informando que não é possível compartilhar, peça ao autor do relatório para dar a você permissão para compartilhar novamente os relatórios e conjuntos de dados.

![Mensagem "Não é possível compartilhar"](media/service-share-dashboards/power-bi-sharing-unable-to-share.png)

## <a name="i-dont-have-access-to-a-dashboard-or-report"></a>Não tenho acesso a um dashboard ou relatório

Caso você veja a mensagem "Solicitar acesso" ao selecionar o link para um relatório ou dashboard, isso significa que você não tem permissão para exibi-lo. Você precisa [solicitar acesso a ele](service-request-access.md).

## <a name="next-steps"></a>Próximas etapas

- [Compartilhar relatórios e dashboards do Power BI com colegas e outras pessoas](service-share-dashboards.md)
- [Como devo colaborar e compartilhar relatórios e dashboards?](service-how-to-collaborate-distribute-dashboards-reports.md)
-  [Compartilhar um relatório do Power BI filtrado](service-share-reports.md)
- Dúvidas? [Experimente a Comunidade do Power BI](https://community.powerbi.com/)
