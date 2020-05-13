---
title: Visão geral de SSO (logon único) para gateways no Power BI
description: Configure seu gateway para habilitar o SSO (logon único) do Power BI para fontes de dados locais.
author: arthiriyer
ms.author: arthii
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 10/10/2019
LocalizationGroup: Gateways
ms.openlocfilehash: 5eab21418eb1028d94ba2e50ffd6e736e6226018
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83301783"
---
# <a name="overview-of-single-sign-on-sso-for-gateways-in-power-bi"></a>Visão geral de SSO (logon único) para gateways no Power BI

Ao configurar o gateway de dados local, você obterá conectividade ininterrupta de logon único para atualizar os relatórios e os dashboards do Power BI em tempo real, com base em dados locais. Você tem a opção de configurar o seu gateway com a delegação restrita do [Kerberos](service-gateway-sso-kerberos.md) ou a SAML ([Security Assertion Markup Language](service-gateway-sso-saml.md)). O gateway de dados local dá suporte ao SSO usando [DirectQuery](desktop-directquery-about.md) ou para Atualização, que se conecta a fontes de dados locais. 

O Power BI é compatível com as seguintes fontes de dados:

* SQL Server (Kerberos)
* SAP HANA (Kerberos e SAML)
* Servidor de Aplicativos SAP BW (Kerberos)
* Servidor de Mensagens SAP BW (Kerberos) 
* Oracle (Kerberos) 
* Teradata (Kerberos)
* Spark (Kerberos)
* Impala (Kerberos)

No momento, não fornecemos suporte ao SSO para [extensões M](https://github.com/microsoft/DataConnectors/blob/master/docs/m-extensions.md).

Quando um usuário interagir com um relatório do DirectQuery no serviço do Power BI, cada operação de filtro cruzado, de fatia, de classificação e de edição de relatório poderá resultar em consultas que são executadas dinamicamente sobre à fonte de dados local subjacente. Quando o SSO é configurado para a fonte de dados, as consultas são executadas sob a identidade do usuário que interage com o Power BI (isto é, por meio da experiência na Web ou de aplicativos móveis do Power BI). Portanto, cada usuário enxerga precisamente os dados para os quais tem permissões na fonte de dados subjacente. 

Você também pode configurar um relatório para atualização no serviço do Power BI para usar o SSO. Quando você configura o SSO para essa fonte de dados, as consultas são executadas sob a identidade do proprietário do conjunto de dados dentro do Power BI. Portanto, a atualização ocorre com base nas permissões do proprietário do conjunto de dados na fonte de dados subjacente. A atualização usando o SSO atualmente está habilitada somente para fontes de dados que usam a delegação restrita de [Kerberos](service-gateway-sso-kerberos.md) 

## <a name="query-steps-when-running-sso"></a>Etapas de consulta ao executar SSO

Uma consulta executada com SSO é formada por três etapas, conforme mostrado no diagrama a seguir.

![Etapas de consulta SSO](media/service-gateway-sso-overview/sso-query-steps.png)

Veja abaixo mais detalhes sobre cada etapa:

1. Para cada consulta, o serviço do Power BI inclui o *nome UPN*, que representa o nome de usuário totalmente qualificado do usuário que está conectado no serviço do Power BI no momento em que ele envia uma solicitação de consulta ao gateway configurado.

2. O gateway deve mapear o UPN do Azure Active Directory para uma identidade local do Active Directory:

   a. Se o Azure AD DirSync (também conhecido como *Azure AD Connect*) for configurado, o mapeamento funcionará automaticamente no gateway.

   b.  Caso contrário, o gateway pode pesquisar e mapear o UPN do Azure AD para um usuário local do AD executando uma pesquisa no domínio do Active Directory local.

3. O processo do serviço do gateway representa o usuário local mapeado, abre a conexão com o banco de dados subjacente e, em seguida, envia a consulta. Não é necessário instalar o gateway no mesmo computador que o banco de dados.

## <a name="next-steps"></a>Próximas etapas

Agora que você entendeu as noções básicas de habilitar o SSO por meio do gateway, leia informações mais detalhadas sobre o Kerberos e o SAML:

* [Logon único (SSO) – Kerberos](service-gateway-sso-kerberos.md)
* [Logon único (SSO) – SAML](service-gateway-sso-saml.md)
