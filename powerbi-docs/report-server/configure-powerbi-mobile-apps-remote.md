---
title: Configurar o acesso do aplicativo móvel a um Servidor de Relatório remotamente
description: Saiba como configurar aplicativos móveis remotamente para o seu servidor de relatório.
author: paulinbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 11/07/2019
ms.author: painbar
ms.openlocfilehash: b84d7a23cf947b18302c761ff5f78143bf3356aa
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/05/2020
ms.locfileid: "73925861"
---
# <a name="configure-power-bi-mobile-app-access-to-report-server-remotely"></a>Configurar o acesso do aplicativo móvel do Power BI a um Servidor de Relatório remotamente

Aplica-se a:

| ![iPhone](./media/configure-powerbi-mobile-apps-remote/ios-logo-40-px.png) | ![Telefone Android](./media/configure-powerbi-mobile-apps-remote/android-logo-40-px.png) |
|:--- |:--- |
| iOS |Android |

Neste artigo, você aprenderá a usar a ferramenta de MDM da sua organização para configurar o acesso de aplicativo móvel do Power BI a um Servidor de Relatório. Para configurar o acesso, os administradores de TI criam uma política de configuração do aplicativo com as informações necessárias a serem enviadas por push ao aplicativo. 

 Com a conexão do Servidor de Relatório já configurada, os usuários do aplicativo móvel do Power BI podem se conectar com o Servidor de Relatório da organização mais facilmente. 

## <a name="create-the-app-configuration-policy-in-mdm-tool"></a>Criar a política de configuração do aplicativo na ferramenta MDM 

Como administrador, veja as etapas a serem seguidas no Microsoft Intune para criar a política de configuração do aplicativo. As etapas e a experiência de criação da política de configuração de aplicativo podem ser diferentes em outras ferramentas MDM. 

1. Conecte a ferramenta MDM. 
2. Crie e nomeie uma nova política de configuração do aplicativo. 
3. Escolha os usuários para os quais essa política de configuração de aplicativo será distribuída. 
4. Crie pares chave-valor. 

A tabela a seguir indica os pares.

|Chave  |Type  |Descrição  |
|---------|---------|---------|
| com.microsoft.powerbi.mobile.ServerURL | Cadeia de caracteres | URL do Servidor de Relatório <br> Deve começar com http/https |
| com.microsoft.powerbi.mobile.ServerUsername | Cadeia de caracteres | [opcional] <br> O nome de usuário a ser usado para conectar o servidor. <br> Se não existir, o aplicativo solicitará ao usuário que digite o nome de usuário para a conexão.| 
| com.microsoft.powerbi.mobile.ServerDisplayName | Cadeia de caracteres | [opcional] <br> O valor padrão é "Servidor de relatório" <br> Um nome amigável usado no aplicativo para representar o servidor | 
| com.microsoft.powerbi.mobile.OverrideServerDetails | Booliano | O valor padrão é True <br>Quando definido como "True", substituirá qualquer definição do Servidor de Relatório que já estiver no dispositivo móvel. Os servidores existentes que já estão configurados serão excluídos. <br> Substituir a definição para True também evita que o usuário remova essa configuração. <br> Se definido como "False", adicionará os valores enviados por push, mantendo as configurações atuais. <br> Se a mesma URL do servidor já estiver configurada no aplicativo móvel, o aplicativo deixará essa configuração como está. O aplicativo não solicita ao usuário para se autenticar novamente no mesmo servidor. |

Veja um exemplo de definição de política de configuração usando o Intune.

![Definições de configuração do Intune](media/configure-powerbi-mobile-apps-remote/power-bi-ios-remote-configuration-settings.png)

## <a name="end-users-connecting-to-report-server"></a>Conexão de usuários finais a um Servidor de Relatório

 Digamos que você publica a política de configuração de aplicativo de uma lista de distribuição. Quando os usuários e dispositivos dessa lista de distribuição iniciarem o aplicativo móvel, eles terão a experiência descrita a seguir. 

1. Uma mensagem informará que o aplicativo móvel está configurado com um Servidor de Relatório. Toque em **Entrar**.

    ![Entrar no servidor de relatório](media/configure-powerbi-mobile-apps-remote/power-bi-config-server-sign-in.png)

2.  Na página **Conectar-se ao servidor**, os detalhes do servidor de relatório já estão preenchidos. Eles tocam em **Conectar**.

    ![Detalhes do servidor de relatório preenchidos](media/configure-powerbi-mobile-apps-remote/power-bi-ios-remote-configure-connect-server.png)

3. Eles digitam uma senha para autenticar e, em seguida, tocam em **Entrar**. 

    ![Detalhes do servidor de relatório preenchidos](media/configure-powerbi-mobile-apps-remote/power-bi-config-server-address.png)

Agora, é possível exibir e interagir com as KPIs e os relatórios do Power BI armazenados no Servidor de Relatório.

## <a name="next-steps"></a>Próximas etapas

- [Habilitar acesso remoto ao Power BI Mobile com o Proxy de Aplicativo do Azure AD](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy-integrate-with-power-bi)
- [Visão geral do administrador](admin-handbook-overview.md)  
- [Instalar o Servidor de Relatório do Power BI](install-report-server.md)  

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)

