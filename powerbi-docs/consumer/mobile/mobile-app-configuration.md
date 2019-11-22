---
title: Definições de configuração de aplicativos do Power BI
description: Como personalizar o comportamento do Power BI usando a ferramenta de MDM
author: paulinbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 11/07/2019
ms.author: painbar
ms.openlocfilehash: 7ed763d6c87e4b93ebecc474c9059ba83245368a
ms.sourcegitcommit: 50c4bebd3432ef9c09eacb1ac30f028ee4e66d61
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73925780"
---
# <a name="remotely-configure-power-bi-app-using-mobile-device-management-mdm-tool"></a>Configurar remotamente o aplicativo do Power BI usando a ferramenta de MDM (gerenciamento de dispositivo móvel)

O aplicativo Power BI Mobile para iOS e Android é compatível com configurações que permitem aos administradores do Office 365 e aos serviços de MDM (gerenciamento de dispositivos móveis), como o Intune, personalizar o comportamento do aplicativo.

O aplicativo Power BI Mobile é compatível com os cenários de configuração a seguir:

- Configuração de Servidor de Relatório (iOS e Android)
- Configurações de proteção de dados (iOS)

## <a name="report-server-configuration-ios-and-android"></a>Configuração de Servidor de Relatório (iOS e Android)

O aplicativo Power BI para iOS e Android permite aos administradores efetuar push remotamente da configuração do Servidor de Relatório para os dispositivos registrados.

| Key | Tipo | Descrição |
|---|---|---|
| com.microsoft.powerbi.mobile.ServerURL | Cadeia de caracteres | URL do Servidor de Relatório.<br><br>Deve começar com http/https.|
| com.microsoft.powerbi.mobile.ServerUsername | Cadeia de caracteres | [opcional]<br><br>O nome de usuário a ser usado para conectar o servidor.<br><br>Se não existir, o aplicativo solicitará ao usuário que digite o nome de usuário para a conexão.|
| com.microsoft.powerbi.mobile.ServerDisplayName | Cadeia de caracteres | [opcional]<br><br>O valor padrão é "Servidor de relatório"<br><br>Um nome amigável usado no aplicativo para representar o servidor. |
| com.microsoft.powerbi.mobile.OverrideServerDetails | Booliano | [opcional]<br><br>O valor padrão é True. Quando definido como True, substituirá qualquer definição do Servidor de Relatório que já estiver no dispositivo móvel. Os servidores existentes que já estão configurados serão excluídos. Substituir a definição para True também evita que o usuário remova essa configuração.<br><br>Se definido como False, adicionará os valores enviados por push, mantendo as configurações atuais. Se a mesma URL do servidor já estiver configurada no aplicativo móvel, o aplicativo deixará essa configuração como está. O aplicativo não solicita ao usuário para se autenticar novamente no mesmo servidor. |

## <a name="data-protection-settings-ios"></a>Configurações de proteção de dados (iOS)

O aplicativo Power BI para iOS oferece aos administradores a capacidade de personalizar a configuração padrão de acordo com configurações de segurança e privacidade. Você pode forçar os usuários a fornecerem o Face ID, o Touch ID ou uma senha ao acessarem o aplicativo do Power BI.

| Key | Tipo | Descrição |
|---|---|---|
| com.microsoft.powerbi.mobile.ForceDeviceAuthentication | Booliano | Valor padrão é False. <br><br>Biometria, como TouchID ou FaceID, pode ser necessária para que os usuários acessem o aplicativo em seus dispositivos. Quando for necessária, a biometria será usada, além da autenticação.<br><br>Se você está usando políticas de proteção de aplicativo, a Microsoft recomenda desabilitar essa configuração para evitar duplo prompt de acesso. |

## <a name="deploying-app-configuration-settings"></a>Implantando definições de configuração de aplicativos

Veja a seguir as etapas necessárias para criar uma política de configuração de aplicativo. Depois de criar a política de configuração, você pode atribuir suas configurações a grupos de usuários.

1. Conecte a ferramenta MDM.
2. Crie e nomeie uma nova política de configuração do aplicativo.
3. Escolha os usuários para os quais essa política de configuração de aplicativo será distribuída.
4. Crie pares de chave-valor para a configuração que você deseja enviar por push aos usuários.

O portal do Intune permite aos administradores implantar facilmente essas configurações no aplicativo do Power BI por meio de políticas de configuração de aplicativos. No entanto, qualquer provedor de MDM é compatível. Se você não estiver usando o Intune, precisará consultar a documentação de MDM sobre como implantar essas configurações.

## <a name="next-steps"></a>Próximas etapas

* Obtenha o aplicativo móvel do Power BI na [App Store]("https://apps.apple.com/app/microsoft-power-bi/id929738808) e no [Google Play](https://play.google.com/store/apps/details?id=com.microsoft.powerbim&amp;amp;clcid=0x409)
* Siga [@MSPowerBI no Twitter](https://twitter.com/MSPowerBI)
* Participe da conversa na [Comunidade do Power BI](https://community.powerbi.com/)
