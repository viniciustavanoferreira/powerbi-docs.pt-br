---
title: arquivo de inclusão
description: arquivo de inclusão
services: powerbi
author: davidiseminger
ms.service: powerbi
ms.topic: include
ms.date: 04/28/2020
ms.author: davidi
ms.openlocfilehash: d56988986cfd994bb21c9bc25d024903719472cf
ms.sourcegitcommit: c772c544ce2e1e2a147b9b62e5579ac3cb59d54c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/29/2020
ms.locfileid: "82255829"
---
## <a name="single-sign-on"></a>Logon único

Depois de publicar um conjunto de dados DirectQuery do SQL do Azure no serviço, você poderá habilitar o SSO (logon único) usando o OAuth2 do Azure AD (Azure Active Directory) para os usuários finais.

Para habilitar o SSO, acesse as configurações para o conjunto de dados, abra a guia **Fontes de dados** e marque a caixa SSO.

![Configure as caixa de diálogo DQ do SQL do Azure](media/direct-query-sso/sso-dialog.png)

Quando a opção de SSO está habilitada e os usuários acessam os relatórios baseados na fonte de dados, o Power BI envia suas credenciais autenticadas do Azure AD nas consultas ao banco de dados SQL do Azure ou ao data warehouse. Com essa opção, o Power BI pode respeitar as configurações de segurança definidas no nível da fonte de dados.

A opção de SSO entra em vigor em todos os conjuntos de dados que usam essa fonte de dados. Isso não afeta o método de autenticação usado para cenários de importação.

