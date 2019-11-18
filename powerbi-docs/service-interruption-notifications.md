---
title: Notificações de interrupção de serviço
description: Saiba mais sobre como receber notificações por email quando há uma interrupção ou degradação do serviço do Power BI.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 09/16/2019
ms.author: mblythe
ms.openlocfilehash: f1d1a22f676873e3a68edf891c4b23522904ddd9
ms.sourcegitcommit: ef6de7067ecb2bbc86d912784376a1627acc478d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73169023"
---
# <a name="service-interruption-notifications"></a>Notificações de interrupção de serviço

É crucial ter informações sobre a disponibilidade de seus aplicativos de negócios críticos. O Power BI fornece notificação de incidente para que você possa, opcionalmente, receber emails se houver uma interrupção ou degradação do serviço. Embora o SLA (contrato de nível de serviço) de 99,9% do Power BI torne raras essas ocorrências, queremos que você fique informado. A captura de tela a seguir mostra o tipo de email que você receberá se habilitar notificações:

![Email de notificação de atualização](media/service-interruption-notifications/refresh-notification-email.png)

Neste momento, enviamos emails para os seguintes _cenários de confiabilidade_:

- Confiabilidade de relatório aberto
- Confiabilidade de atualização do modelo
- Confiabilidade de atualização de consulta

Notificações são enviadas quando há um _atraso estendido_ em operações como abertura de relatórios, atualização de conjuntos de dados ou execuções de consultas. Depois que um incidente é resolvido, você recebe um email de acompanhamento.

> [!NOTE]
> Este recurso no momento está disponível apenas para capacidades dedicadas no Power BI Premium. Ele não está disponível para capacidade compartilhada ou inserida.

## <a name="enable-notifications"></a>Habilitar notificações

Um administrador de locatário do Power BI habilita as notificações no portal de administração:

1. Identifique ou crie um grupo de segurança habilitado para email que deva receber notificações.

1. No portal de administração, selecione **Configurações do locatário**. Em **Configurações de ajuda e suporte**, expanda **Receber notificações por email para interrupções ou incidentes de serviço**.

1. Habilite as notificações, insira um grupo de segurança e selecione **Aplicar**.

    ![Habilitar notificações de serviço](media/service-interruption-notifications/enable-notifications.png)

> [!NOTE]
> O Power BI envia notificações da conta no-reply-powerbi@microsoft.com. Verifique se essa conta está na lista de permissões para que as notificações não acabem em uma pasta de spam ou lixo eletrônico.

## <a name="next-steps"></a>Próximas etapas

[Opções de suporte do Power BI Pro e do Power BI Premium](service-support-options.md)

Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)
