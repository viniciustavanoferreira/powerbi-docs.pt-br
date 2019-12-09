---
title: Solucionar problemas de entrada no Power BI Desktop
description: Soluções para problemas comuns de entrada no Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: troubleshooting
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Troubleshooting
ms.openlocfilehash: bfe0e217edc65c3edb5d78d9399ef2b9b376e286
ms.sourcegitcommit: f77b24a8a588605f005c9bb1fdad864955885718
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/03/2019
ms.locfileid: "73879555"
---
# <a name="troubleshooting-sign-in-for-power-bi-desktop"></a>Solucionar problemas de entrada no Power BI Desktop
Em alguns momentos, talvez você tente entrar no **Power BI Desktop**, mas receba erros. Há dois motivos principais para problemas de conexão: **erros de autenticação de proxy** e **erros de redirecionamento de URL sem HTTPS**. 

Para determinar qual problema está causando o problema de entrada, a primeira etapa é entrar em contato com seu administrador e fornecer informações de diagnóstico para que eles possam determinar a causa do problema. Ao rastrear problemas associados ao seu problema de entrada, os administradores podem determinar qual dos erros a seguir se aplica a você. 

Vamos analisar cada um desses problemas. Ao final deste artigo há uma discussão sobre como capturar um *rastreamento* no Power BI Desktop, o que pode ajudar a rastrear a solução de problemas.


## <a name="proxy-authentication-required-error"></a>Erro de Autenticação de Rede Necessária

A tela a seguir mostra um exemplo do erro *Autenticação de Proxy Necessária*.

![Erro de entrada para o erro de Autenticação de Proxy](media/desktop-troubleshooting-sign-in/desktop-tshoot-sign-in_01.png)

As exceções a seguir em arquivos de rastreamento do *Power BI Desktop* são associadas este erro:

* *Microsoft.PowerBI.Client.Windows.Services.PowerBIWebException*
* *HttpStatusCode: ProxyAuthenticationRequired*

Quando esse erro ocorre, o motivo mais provável é que um servidor de autenticação de proxy em sua rede está bloqueando as solicitações Web emitidas pelo **Power BI Desktop**. 

Se sua rede usar um servidor de autenticação de proxy, o administrador poderá corrigir esse problema incluindo em uma lista de permissão os seguintes domínios do servidor de autenticação de proxy:

* app.powerbi.com
* api.powerbi.com
* domínios no namespace *.analysis.windows.net

Para clientes que fazem parte de uma nuvem governamental, a correção desse problema pode ser feita incluindo em uma lista de permissão os seguintes domínios do servidor de autenticação de proxy:

* app.powerbigov.us
* api.powerbigov.us
* domínios no namespace *.analysis.usgovcloudapi.net

## <a name="non-https-url-redirect-not-supported-error"></a>Erro de falta de suporte de redirecionamento de URL sem HTTPS

As versões atuais do **Power BI Desktop** usam a versão atual da autenticação ADAL (Biblioteca de Autenticação do Active Directory), que não permite um redirecionamento para URLs sem proteção (sem HTTPS). 

As exceções a seguir em arquivos de rastreamento do *Power BI Desktop* são associadas este erro:

* *Microsoft.IdentityModel.Clients.ActiveDirectory.AdalServiceException: redirecionamento de URL sem HTTPS não tem suporte no modo de exibição da Web*
* *ErrorCode: non_https_redirect_failed*

Se *ErrorCode: non_https_redirect_failed* ocorrer, significa que uma ou mais páginas de redirecionamento ou provedores da cadeia de redirecionamento não é um ponto de extremidade HTTPS protegido, ou que um emissor de certificado de um ou mais redirecionamentos não está entre as raízes confiáveis do dispositivo. Todos os provedores em qualquer cadeia de redirecionamento de entrada deve usar uma URL com HTTPS. Para resolver esse problema, contate o administrador e solicite o uso de URLs protegidas em seus sites de autenticação. 

## <a name="how-to-collect-a-trace-in-power-bi-desktop"></a>Como coletar um rastreamento no Power BI Desktop

Para coletar um rastreamento no **Power BI Desktop**, execute estas etapas:

1. Habilite o rastreamento em **Power BI Desktop** acessando **Arquivo > Opções e configurações > Opções** e, depois, selecione **Diagnóstico** nas opções do painel esquerdo. No painel exibido, marque a caixa ao lado de **Habilitar o rastreamento**, conforme mostra a imagem a seguir. Talvez seja necessário reiniciar o **Power BI Desktop**.
   
   ![Habilitar o rastreamento no Power BI Desktop](media/desktop-troubleshooting-sign-in/desktop-tshoot-sign-in_02.png)

2. Em seguida, execute as etapas que reproduzem o erro. Quando isso ocorre, o **Power BI Desktop** adiciona eventos ao log de rastreamento, que é armazenado no computador local.

3. Navegue até a pasta Traces em seu computador local. Encontre essa pasta selecionando o link em **Diagnóstico**, onde você habilitou o rastreamento, mostrado como *Abrir pasta de rastreamento/despejo de memória* na imagem anterior. Geralmente, isso é encontrado neste caminho no computador local:

    `C:\Users/<user name>/AppData/Local/Microsoft/Power BI Desktop/Traces`

A pasta pode conter muitos arquivos de rastreamento. Envie apenas os arquivos recentes ao seu administrador, para facilitar a identificação rápida do erro. 

