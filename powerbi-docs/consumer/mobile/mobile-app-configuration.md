---
title: Definições de configuração de aplicativos iOS do Power BI
description: Como personalizar o comportamento do Power BI para iOS usando a ferramenta de MDM
author: paulinbar
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 06/07/2019
ms.author: mshenhav
ms.openlocfilehash: bc9c6dd8cd892ab0304cc5a99a3bb780486f32f0
ms.sourcegitcommit: c0f4d00d483121556a1646b413bab75b9f309ae9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/29/2019
ms.locfileid: "70160149"
---
# <a name="remotely-configure-power-bi-ios-app-using-mobile-device-management-mdm-tool"></a>Configurar remotamente o aplicativo iOS do Power BI usando a ferramenta de MDM (gerenciamento de dispositivo móvel)

O aplicativo Power BI Mobile para iOS é compatível com configurações que permitem aos administradores do Office 365 e de MDM (gerenciamento de dispositivo móvel), como o Intune, personalizar o comportamento do aplicativo.

O aplicativo Power BI Mobile para iOS é compatível com os cenários de configuração a seguir:

- Configuração de Servidor de Relatório
- Configurações de proteção de dados

## <a name="report-server-configuration"></a>Configuração de Servidor de relatório

O aplicativo iOS do Power BI permite aos administradores remotamente efetuarem push de configuração do Servidor de Relatório com dispositivos registrados.

| Key | Tipo | Descrição |
|---|---|---|
| com.microsoft.powerbi.mobile.ServerURL | Cadeia de caracteres | URL do Servidor de Relatório.<br><br>Deve começar com http/https.|
| com.microsoft.powerbi.mobile.ServerUsername | Cadeia de caracteres | [opcional]<br><br>O nome de usuário a ser usado para conectar o servidor.<br><br>Se não existir, o aplicativo solicitará ao usuário que digite o nome de usuário para a conexão.|
| com.microsoft.powerbi.mobile.ServerDisplayName | Cadeia de caracteres | [opcional]<br><br>O valor padrão é "Servidor de relatório"<br><br>Um nome amigável usado no aplicativo para representar o servidor. |
| com.microsoft.powerbi.mobile.OverrideServerDetails | Booliano | [opcional]<br><br>O valor padrão é True. Quando definido como True, substituirá qualquer definição do Servidor de Relatório que já estiver no dispositivo móvel. Os servidores existentes que já estão configurados serão excluídos. Substituir a definição para True também evita que o usuário remova essa configuração.<br><br>Se definido como False, adicionará os valores enviados por push, mantendo as configurações atuais. Se a mesma URL do servidor já estiver configurada no aplicativo móvel, o aplicativo deixará essa configuração como está. O aplicativo não solicita ao usuário para se autenticar novamente no mesmo servidor. |

## <a name="data-protection-setting"></a>Configuração de proteção de dados

O aplicativo iOS do Power BI oferece aos administradores a capacidade de personalizar a configuração padrão de acordo com configurações de segurança e privacidade. Você pode forçar os usuários a fornecerem o Face ID, o Touch ID ou uma senha ao acessar o aplicativo do Power BI.

| Key | Tipo | Descrição |
|---|---|---|
| com.microsoft.powerbi.mobile.ForceDeviceAuthentication | Booliano | Valor padrão é False. <br><br>Biometria, como TouchID ou FaceID, pode ser necessária para que os usuários acessem o aplicativo em seus dispositivos. Quando for necessária, a biometria será usada, além da autenticação.<br><br>Se você está usando políticas de proteção de aplicativo, a Microsoft recomenda desabilitar essa configuração para evitar duplo prompt de acesso. |

## <a name="deploying-app-configuration-settings"></a>Implantando definições de configuração de aplicativos

As etapas a seguir permitirão que você crie uma política de configuração de aplicativos. Depois que a política de configuração for criada, você poderá atribuir as configurações a grupos de usuários.

1. Conecte a ferramenta MDM.

2. Crie e nomeie uma nova política de configuração do aplicativo.

3. Escolha os usuários para os quais essa política de configuração de aplicativo será distribuída.

4. Crie pares de chave-valor para a configuração que você deseja enviar por push aos usuários.

O portal do Intune permite aos administradores implantar facilmente essas configurações no aplicativo iOS do Power BI por meio de políticas de configuração de aplicativos.
No entanto, qualquer provedor de MDM é compatível. Se você não estiver usando o Intune, precisará consultar a documentação do MDM sobre como implantar essas configurações.

## <a name="next-steps"></a>Próximas etapas

* Baixe o [aplicativo móvel do Power BI para iPhone](http://go.microsoft.com/fwlink/?LinkId=522062)
* Siga [@MSPowerBI no Twitter](https://twitter.com/MSPowerBI)
* Participe da conversa na [Comunidade do Power BI](http://community.powerbi.com/)
