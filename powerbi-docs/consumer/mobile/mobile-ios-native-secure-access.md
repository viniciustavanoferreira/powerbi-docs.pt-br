---
title: Proteger dados do Power BI com identificação nativa de dispositivo
description: Saiba como configurar seu aplicativo iOS para exigir identificação adicional antes de acessar os dados do Power BI
author: paulinbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 03/11/2020
ms.author: painbar
ms.openlocfilehash: 5b23fa4d238a9ef6128fba3fdab4f473890f94f1
ms.sourcegitcommit: 480bba9c745cb9af2005637e693c5714b3c64a8a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/11/2020
ms.locfileid: "79114853"
---
# <a name="protect-power-bi-app-with-face-id-touch-id-or-passcode"></a>Proteger o aplicativo do Power BI com Face ID, Touch ID ou senha 

Em muitos casos, os dados gerenciados no Power BI são confidenciais e precisam ser protegidos e acessados somente por usuários autorizados. 

O aplicativo iOS do Power BI permite proteger seus dados por meio da configuração de identificação adicional. Você precisará fornecer o Face ID, o Touch ID ou uma senha sempre que iniciar o aplicativo ou quando você trazer o aplicativo do segundo para o primeiro plano.

| ![iPhone](./media/tutorial-mobile-apps-ios-qna/iphone-logo-50-px.png) | ![iPad](./media/tutorial-mobile-apps-ios-qna/ipad-logo-50-px.png) |
|:--- |:--- |
| iPhones |iPads |

## <a name="turn-on-face-id-touch-id-or-passcode-in-app-setting"></a>Ativar o Face ID, o Touch ID ou a senha na configuração do aplicativo

Para usar identificação adicional no Power BI, acesse a configuração do aplicativo em **Privacidade e Segurança**. Você verá a opção para ativar o Face ID, o Touch ID ou a senha, com base nos recursos do seu dispositivo.

![Página de configuração do aplicativo iOS do Power BI](./media/mobile-ios-native-secure-access/mobile-ios-native-secured-setting.png)

Depois que essa configuração for ativada, sempre que você iniciar o Power BI ou colocá-lo em primeiro plano, ele pedirá que você forneça sua ID antes de acessar o aplicativo. 

A decisão de pedir o Face ID, o Touch ID ou a senha é feita pelo iOS, com base na capacidade do dispositivo. Se o dispositivo for compatível com o Face ID, você precisará usar o Face ID. Se ele for compatível com o Touch ID, você precisará usar o Touch ID. Se não for compatível com nenhum deles, você precisará fornecer uma senha.

![Face ID do iOS do Power BI](./media/mobile-ios-native-secure-access/mobile-ios-native-secured-faceid.png)

## <a name="use-mdm-to-enforce-face-id-touch-id-or-passcode"></a>Usar MDM para impor Face ID, Touch ID ou senha

Algumas organizações têm políticas de segurança e requisitos de conformidade que impõem identificação adicional antes de permitir acesso a dados corporativos confidenciais. 

O aplicativo móvel iOS do Power BI permite aos administradores controlar essa configuração enviando as definições de configuração de aplicativos por push do Microsoft Intune e de outras soluções de MDM (gerenciamento de dispositivo móvel). Os administradores podem usar a política de proteção de aplicativo para ativar essa configuração para todos os usuários ou para um grupo de usuários.

|Key  |Tipo  |Descrição  |
|---------|---------|---------|
| com.microsoft.powerbi.mobile.ForceDeviceAuthentication | Booliano | Valor padrão é False. <br>Quando definido como True, o aplicativo forçará os usuários a se identificarem com Face ID, Touch ID ou senha antes de exibir dados do Power BI no aplicativo. Usuários que não têm Face ID, Touch ID ou uma senha configurada em seu dispositivo, precisarão configurar antes de poder acessar o Power BI.  |

## <a name="next-steps"></a>Próximas etapas

[Usar MDM para configurar o aplicativo iOS do Power BI remotamente](mobile-app-configuration.md)
