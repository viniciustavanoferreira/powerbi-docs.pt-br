---
title: Manutenção planejada do Power BI
description: Informações para administradores sobre como a manutenção planejada para o Power BI afeta a organização e as próximas etapas que eles podem precisar executar.
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 06/19/2020
ms.author: kfollis
ms.custom: MC
ROBOTS: NOINDEX
LocalizationGroup: Admin
ms.openlocfilehash: cc9364129159b5527d309f125d42e661d0b4c206
ms.sourcegitcommit: a58d10ca62bc55e83b58cf8e8495ac01a4bd6532
ms.contentlocale: pt-BR
ms.lasthandoff: 06/20/2020
ms.locfileid: "85120542"
---
# <a name="power-bi-planned-maintenance"></a>Manutenção planejada do Power BI

A manutenção planejada para a serviço do Power BI é uma parte necessária do nosso compromisso em fornecer um produto confiável aos nossos clientes. Quando a manutenção planejada estiver acontecendo, o serviço do Power BI não estará disponível para sua organização por algum tempo. Os usuários podem não conseguir acessar o serviço do Power BI, e as operações em segundo plano podem não ter êxito. Após a janela de manutenção, esperamos que o serviço funcione normalmente e que as operações interativas e em segundo plano sejam bem-sucedidas.  

A manutenção está planejada para ocorrer fora do horário comercial normal, a fim de ajudar a minimizar qualquer impacto em sua organização. Para organizações que têm usuários em todo o mundo, reconhecemos que "fora do horário comercial normal" pode afetá-las de maneira diferente. Pedimos desculpas por qualquer efeito para seus usuários. Estamos trabalhando duro para aprimorar o Power BI e minimizar essas janelas de manutenção.

Se a sua organização for afetada, enviaremos um aviso com antecedência. Os administradores do Microsoft 365 verão um aviso antecipado no Centro de mensagens de Microsoft 365 e receberão email. Além disso, os clientes com contratos de Suporte Premier serão notificados por meio da equipe de contas da Microsoft.

## <a name="actions-to-take-now"></a>Ações a serem executadas agora

* Os administradores do Microsoft 365 devem [conferir no Centro de mensagens](https://admin.microsoft.com/Adminportal/Home#/MessageCenter) se há notificações sobre a manutenção planejada do Power BI. Compartilhe a mensagem com pessoas que devem ficar cientes do assunto, mas que podem não ter acesso ao Centro de mensagens.
* Se você não for um administrador do Microsoft 365, entre em contato com seu departamento de TI ou com suas equipes de suporte internas para perguntar sobre qualquer manutenção futura.

## <a name="actions-to-take-when-maintenance-is-complete"></a>Ações a serem executadas quando a manutenção for concluída

* Os usuários devem atualizar qualquer janela aberta do navegador.
* Os usuários do aplicativo Power BI Mobile precisarão verificar se estão usando a versão mais recente e sair e entrar novamente no aplicativo. Confira a loja de aplicativos do seu telefone ou nossa página do [Power BI Mobile](https://powerbi.microsoft.com/mobile/).
* Os clientes que estavam editando ou publicando de forma ativa relatórios que usam visuais organizacionais, localmente ou no OneDrive e SharePoint, precisarão reimportar o visual por meio do repositório de visuais da organização ou baixar um PBIX atualizado antes da republicação. Para obter mais informações sobre visuais organizacionais, confira [Visuais da organização](service-admin-portal.md#organization-visuals).
* Se as pastas de trabalho do Excel que usam o recurso Analisar no Excel não forem atualizadas, poderá ser necessário atualizar a cadeia de conexão ou baixar novamente a conexão ODC para esse conjunto de dados. Para obter mais informações, confira [Analisar no Excel](../collaborate-share/service-analyze-in-excel.md#connect-to-power-bi-data).
* A conexão a links para o Power BI inseridos no conteúdo pode falhar quando a manutenção é feita. Por exemplo, um link inserido no SharePoint ou no Teams pode resultar em um erro de usuário. Para resolver esse problema, você precisa regenerar o link inserido no Power BI e atualizar os locais onde eles são usados. Para obter mais informações sobre links inseridos, confira [Inserir uma web part de relatório no SharePoint Online](../collaborate-share/service-embed-report-spo.md) e [Colaborar no Microsoft Teams com o Power BI](../collaborate-share/service-embed-report-microsoft-teams.md).

## <a name="next-steps"></a>Próximas etapas

* [Habilitar notificações de interrupção de serviço](service-interruption-notifications.md)
* [Acompanhar alteração futura no Centro de mensagens](https://docs.microsoft.com/microsoft-365/admin/manage/message-center?view=o365-worldwide)
