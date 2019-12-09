---
title: arquivo de inclusão
description: arquivo de inclusão
services: powerbi
author: davidiseminger
ms.service: powerbi
ms.topic: include
ms.date: 05/31/2019
ms.author: davidi
ms.openlocfilehash: eec30d11c1bd99271416ab1a3a2dbb581687e315
ms.sourcegitcommit: f77b24a8a588605f005c9bb1fdad864955885718
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2019
ms.locfileid: "74698292"
---
## <a name="single-sign-on"></a>Logon único

Depois de publicar um conjunto de dados DirectQuery do SQL do Azure para o serviço, você pode habilitar o logon único (SSO) por meio do OAuth2 do Azure Active Directory (Azure AD) para os usuários finais.

Para habilitar o SSO, acesse as configurações para o conjunto de dados, abra a guia **Fontes de dados** e marque a caixa SSO.

![Configure as caixa de diálogo DQ do SQL do Azure](media/direct-query-sso/sso-dialog.png)

Quando a opção de SSO está habilitada e os usuários acessam os relatórios baseados na fonte de dados, o Power BI envia suas credenciais autenticadas do Azure AD nas consultas ao banco de dados SQL do Azure ou ao data warehouse. Isso permite que o Power BI respeite as configurações de segurança que são configuradas no nível da fonte de dados.

A opção de SSO entra em vigor em todos os conjuntos de dados que usam essa fonte de dados. Isso não afeta o método de autenticação usado para cenários de importação.

> [!Note]
> Não há suporte para Autenticação Multifator do Microsoft Azure (MFA). Os usuários que quiserem usar o SSO com o DirectQuery para SQL do Microsoft Azure devem ser isentos de MFA.