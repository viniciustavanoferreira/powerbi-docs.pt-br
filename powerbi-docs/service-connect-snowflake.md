---
title: Conectar-se ao Snowflake com o Power BI
description: Snowflake com SSO para o Power BI
author: cpopell
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 11/20/2019
ms.author: gepopell
LocalizationGroup: Connect to services
ms.openlocfilehash: 03e6e8efae5cd4a5f61e3d07bc0b3c524b3b0a46
ms.sourcegitcommit: d6a48e6f6e3449820b5ca03638b11c55f4e9319c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/18/2020
ms.locfileid: "77429339"
---
#  <a name="connecting-to-snowflake-in-power-bi-service"></a>Conectar-se ao Snowflake no Serviço do Power BI

## <a name="introduction"></a>Introdução

Há apenas uma diferença entre conectar-se ao Snowflake no serviço do Power BI e fazer isso usando outros conectores, que é a funcionalidade adicional oferecida para o AAD (com uma opção de SSO). Partes diferentes da integração exigem funções administrativas diferentes no Snowflake, no Power BI e no Azure. Você também pode optar por habilitar a autenticação do AAD sem usar o SSO. A autenticação Básica funciona de modo semelhante a outros conectores no serviço.

Se você tiver interesse em configurar a integração do AAD, bem como poder habilitar o SSO:
* Se você for o administrador do Snowflake, leia o artigo [SSO do Power BI para o Snowflake – Introdução](https://docs.snowflake.net/manuals/LIMITEDACCESS/oauth-powerbi.html) na documentação do Snowflake.
* (SSO) Se você for um administrador do Power BI, confira a seção "Configuração do Serviço do Power BI – Portal de Administração"
* (SSO) Se você for um criador de conjuntos de dados do Power BI, confira a seção "Configuração do Serviço do Power BI – Habilitando um conjunto de dados"

## <a name="power-bi-service-configuration"></a>Configuração do Serviço do Power BI

### <a name="admin-portal"></a>Portal de administração

Se você quiser habilitar o SSO, o administrador de locatários precisará acessar o Portal de Administração e aprovar o envio das credenciais do AAD do Power BI para o Snowflake.

![Configuração do administrador de locatários para o SSO do Snowflake](media/service-connect-snowflake/snowflakessotenant.png)

Navegue até o "Portal de Administração", selecione o item "Configurações de Locatário" na barra lateral, role para baixo até "Configurações de Integração" e você verá a opção do "SSO do Snowflake".

Conforme indicado, você precisa habilitar essa opção manualmente para consentir com o envio do token do AAD para os servidores do Snowflake. Para habilitá-la, clique no botão de alternância "Desabilitado", clique em "Aplicar" e aguarde até que a alteração das configurações entre em vigor. Pode levar até uma hora para que o serviço propague a configuração.

Quando isso acontecer, você poderá usar relatórios com SSO.

### <a name="configuring-a-dataset-with-aad"></a>Configurando um conjunto de dados com o AAD

Após um relatório baseado no conector do Snowflake ter sido publicado na Web, no serviço Web do Power BI, o criador do conjunto de dados precisará navegar até o workspace apropriado, selecionar "Conjuntos de dados" e selecionar "Configurações" (no menu "..." de ações adicionais ao lado do conjunto de dados relevante).

Devido à maneira como o Power BI funciona, o SSO só funciona quando nenhuma fonte de dados é executada por meio do gateway de dados local.

* Se estiver usando somente uma fonte do Snowflake em seu modelo de dados, você poderá usar o SSO se optar por não usar o gateway de dados local
* Se estiver usando uma fonte do Snowflake em conjunto com outra fonte, você poderá usar o SSO se nenhuma das fontes usar o gateway de dados local
* Se estiver usando uma fonte do Snowflake por meio do gateway de dados local, você poderá usar as credenciais do AAD, mas não o SSO. Isso poderá ser relevante caso você esteja tentando acessar uma VNet usando apenas um IP com o gateway instalado, em vez de todo o intervalo de IP do Power BI.
* Se estiver usando uma fonte do Snowflake em conjunto com outra fonte que requer um gateway, você precisará usar o Snowflake por meio do gateway de dados local também e não poderá usar o SSO.

Para obter mais informações sobre como usar o gateway de dados local, confira o artigo [O que é um gateway de dados local?](https://docs.microsoft.com/power-bi/service-gateway-onprem)

Se você não estiver usando o gateway, já estará tudo pronto. Se você tiver credenciais do Snowflake configuradas no gateway de dados local, mas estiver usando essa fonte de dados apenas em seu modelo, clique no botão de alternância na página Configurações do conjunto de dados para desativar o gateway para esse modelo de dados.

![Configuração do conjunto de dados para desativar o gateway](media/service-connect-snowflake/snowflake_gateway_toggle_off.png)

O criador do conjunto de dados precisa selecionar "Credenciais da fonte de dados" e entrar. O conjunto de dados pode ser conectado ao Snowflake com credenciais Básicas ou com o OAuth2 (AAD). Se você optar por usar o AAD, o conjunto de dados poderá ser habilitado para usar o SSO. Quando o primeiro usuário entrar no Snowflake para o conjunto de dados, ele precisará selecionar a opção de que outros usuários terão suas credenciais de Oauth2 usadas para recuperar dados. Isso habilitará o SSO do AAD. Independentemente de o usuário inicial entrar com a autenticação Básica ou o OAuth2 (AAD), as credenciais do AAD serão enviadas para o SSO. 

![Configuração do conjunto de dados para o SSO do Snowflake](media/service-connect-snowflake/snowflakessocredui.png)

Depois que isso for feito, todos os usuários adicionais deverão usar automaticamente a autenticação do AAD para se conectar aos dados desse conjunto de dados do Snowflake.

Se você optar por não habilitar o SSO, os usuários que atualizarem o relatório usarão as credenciais do usuário que entrou, como acontece com a maioria dos outros relatórios do Power BI.

### <a name="troubleshooting"></a>Solução de problemas

Se você tiver problemas com a integração, confira o [Guia de solução de problemas](https://docs.snowflake.net/manuals/LIMITEDACCESS/oauth-powerbi.html#troubleshooting) do Snowflake.

