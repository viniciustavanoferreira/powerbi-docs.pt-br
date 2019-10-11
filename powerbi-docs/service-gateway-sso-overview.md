---
title: Usar o logon único (SSO) para fontes de dados locais
description: Configure seu gateway para habilitar o SSO (logon único) do Power BI para fontes de dados locais.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 07/15/2019
LocalizationGroup: Gateways
ms.openlocfilehash: a99aad87763edce54996f0a485fde5498fb1df11
ms.sourcegitcommit: 9bf3cdcf5d8b8dd12aa1339b8910fcbc40f4cbe4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/05/2019
ms.locfileid: "71968605"
---
# <a name="overview-of-single-sign-on-sso-for-gateways-in-power-bi"></a>Visão geral de SSO (logon único) para gateways no Power BI

Você pode obter conectividade ininterrupta de logon único ao habilitar os relatórios do Power BI e painéis para serem atualizados em tempo real com base em dados locais, configurando o gateway de dados local tanto com delegação restrita do Kerberos quanto com SAML (Security Assertion Markup Language). O gateway de dados local dá suporte ao SSO com o DirectQuery, que é usado para a conexão às fontes de dados locais.

No momento, damos suporte para as seguintes fontes de dados:

* SQL Server ([Kerberos](service-gateway-sso-kerberos.md))
* SAP HANA ([Kerberos](service-gateway-sso-kerberos.md) e [SAML](service-gateway-sso-saml.md))
* SAP BW ([Kerberos](service-gateway-sso-kerberos.md))
* Teradata ([Kerberos](service-gateway-sso-kerberos.md))
* Spark ([Kerberos](service-gateway-sso-kerberos.md))
* Impala ([Kerberos](service-gateway-sso-kerberos.md))

No momento, não damos suporte ao SSO para [M-extensions](https://github.com/microsoft/DataConnectors/blob/master/docs/m-extensions.md).

Quando um usuário interage com um relatório do DirectQuery no serviço do Power BI, cada operação de filtro cruzado, de fatia, de classificação e de edição de relatório pode resultar em consultas de execução dinâmica com relação à fonte de dados local subjacente. Quando o SSO é configurado para a fonte de dados, as consultas são executadas na identidade do usuário que interage com o Power BI (isto é, por meio da experiência na Web ou de aplicativos móveis do Power BI). Dessa forma, cada usuário vê precisamente os dados para os quais têm permissões na fonte de dados subjacente. Com o logon único configurado, não há cache de dados compartilhados entre usuários diferentes.

## <a name="query-steps-when-running-sso"></a>Etapas de consulta ao executar SSO

Uma consulta executada com SSO é formada por três etapas, conforme mostrado no diagrama a seguir.

![Etapas de consulta SSO](media/service-gateway-sso-overview/sso-query-steps.png)

Veja abaixo mais detalhes sobre essas etapas:

1. Para cada consulta, o **serviço do Power BI** inclui o *nome UPN*, ou seja, o nome de usuário totalmente qualificado do usuário atualmente conectado no serviço do Power BI ao enviar uma solicitação de consulta ao gateway configurado.

2. O gateway precisa mapear o UPN do Azure Active Directory para uma identidade do Active Directory local.

   a.  Se o Azure AD DirSync (também conhecido como *Azure AD Connect*) for configurado, o mapeamento funcionará automaticamente no gateway.

   b.  Caso contrário, o gateway pode pesquisar e mapear o UPN do Azure AD para um usuário local do AD executando uma pesquisa no domínio do Active Directory local.

3. O processo do serviço do gateway representa o usuário local mapeado, abre a conexão ao banco de dados subjacente e envia a consulta. O gateway não precisa estar instalado no mesmo computador que o banco de dados.

## <a name="next-steps"></a>Próximas etapas

Agora que você entendeu as noções básicas de SSO pelo gateway, leia mais informações detalhadas sobre Kerberos e SAML:

* [Logon único (SSO) – Kerberos](service-gateway-sso-kerberos.md)
* [Logon único (SSO) – SAML](service-gateway-sso-saml.md)
