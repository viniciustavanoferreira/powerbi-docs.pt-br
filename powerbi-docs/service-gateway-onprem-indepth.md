---
title: Detalhes sobre o gateway de dados local
description: Este artigo examina o gateway local mais detalhadamente. Ele explica como o serviço funciona com o Azure Active Directory e o Active Directory local ao trabalhar com o Analysis Services
author: mgblythe
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 07/15/2019
ms.author: mblythe
LocalizationGroup: Gateways
ms.openlocfilehash: e8807feeccccebab8837ac571ae4340c5c0c9b1a
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/09/2019
ms.locfileid: "73881584"
---
# <a name="on-premises-data-gateway-in-depth"></a>Detalhes sobre o gateway de dados local

[!INCLUDE [gateway-rewrite](includes/gateway-rewrite.md)]

Movemos as informações deste artigo para vários artigos nos documentos gerais e nos do Power BI. Siga os links em cada título para encontrar o conteúdo relevante.

## <a name="how-the-gateway-works"></a>Como funciona o gateway

Confira [Arquitetura do gateway de dados local](/data-integration/gateway/service-gateway-onprem-indepth).

## <a name="list-of-available-data-source-types"></a>Relação dos tipos de fonte de dados disponíveis

Confira [Gerenciar fontes de dados](service-gateway-data-sources.md).

## <a name="authentication-to-on-premises-data-sources"></a>Autenticação em fontes de dados locais

Confira [Autenticação em fontes de dados locais](/data-integration/gateway/service-gateway-onprem-indepth#authentication-to-on-premises-data-sources).

## <a name="authentication-to-a-live-analysis-services-data-source"></a>Autenticação em uma fonte de dados dinâmica do Analysis Services

Confira [Autenticação em uma fonte de dados dinâmica do Analysis Services](service-gateway-enterprise-manage-ssas.md#authentication-to-a-live-analysis-services-data-source).

## <a name="role-based-security"></a>Segurança baseada em função

Confira [Segurança baseada em função](service-gateway-enterprise-manage-ssas.md#role-based-security).

## <a name="row-level-security"></a>Segurança em nível de linha

Confira [Segurança em nível de linha](service-gateway-enterprise-manage-ssas.md#row-level-security).

## <a name="what-about-azure-active-directory"></a>E quanto ao Azure Active Directory?

Confira [Azure Active Directory](/data-integration/gateway/service-gateway-onprem-indepth#azure-active-directory).

## <a name="how-do-i-tell-what-my-upn-is"></a>Como saber qual é a minha UPN?

Confira [Como saber qual é a minha UPN?](/data-integration/gateway/service-gateway-onprem-indepth#how-do-i-tell-what-my-upn-is).

## <a name="map-user-names-for-analysis-services-data-sources"></a>Mapear nomes de usuário para fontes de dados do Analysis Services

Confira [Maper nomes de usuário para fontes de dados do Analysis Services](service-gateway-enterprise-manage-ssas.md#map-user-names-for-analysis-services-data-sources).

## <a name="synchronize-an-on-premises-active-directory-with-azure-active-directory"></a>Sincronizar um Active Directory local com o Azure Active Directory

Confira [Sincronizar um Active Directory local com o Azure Active Directory](/data-integration/gateway/service-gateway-onprem-indepth#synchronize-an-on-premises-active-directory-with-azure-active-directory).

## <a name="what-to-do-next"></a>O que fazer em seguida?

Consulte os artigos sobre fontes de dados:

[Gerenciar fontes de dados](service-gateway-data-sources.md)
[Gerenciar sua fonte de dados – Analysis Services](service-gateway-enterprise-manage-ssas.md)  
[Gerenciar sua fonte de dados – SAP HANA](service-gateway-enterprise-manage-sap.md)  
[Gerenciar sua fonte de dados – SQL Server](service-gateway-enterprise-manage-sql.md)  
[Gerenciar sua fonte de dados – Oracle](service-gateway-onprem-manage-oracle.md)  
[Gerenciar sua fonte de dados – Importar/Atualização agendada](service-gateway-enterprise-manage-scheduled-refresh.md)  

## <a name="where-things-can-go-wrong"></a>O que pode dar errado

Confira [Solucionar problemas do gateway de dados local](/data-integration/gateway/service-gateway-tshoot) e [Solucionar problemas de gateways – Power BI](service-gateway-onprem-tshoot.md).

## <a name="sign-in-account"></a>Conta de entrada

Confira [Conta de entrada](/data-integration/gateway/service-gateway-onprem-indepth#sign-in-account).

## <a name="windows-service-account"></a>Conta do Serviço Windows

Confira [Alterar a conta de serviço do gateway de dados local](/data-integration/gateway/service-gateway-service-account).

## <a name="ports"></a>Portas

Confira [Portas](/data-integration/gateway/service-gateway-communication#ports).

## <a name="forcing-https-communication-with-azure-service-bus"></a>Forçar a comunicação HTTPS com o Barramento de Serviço do Azure

Confira [Forçar a comunicação HTTPS com o Barramento de Serviço do Azure](/data-integration/gateway/service-gateway-communication#force-https-communication-with-azure-service-bus).

## <a name="support-for-tls-12"></a>Suporte para TLS 1.2

Confira [TLS 1.2 para tráfego de gateway](/data-integration/gateway/service-gateway-communication#tls-12-for-gateway-traffic).

## <a name="how-to-restart-the-gateway"></a>Como reiniciar o gateway

Confira [Reiniciar um gateway](/data-integration/gateway/service-gateway-restart).

## <a name="next-steps"></a>Próximas etapas

[O que é o gateway de dados local?](service-gateway-onprem.md)

Mais perguntas? [Experimente a Comunidade do Power BI](https://community.powerbi.com/)