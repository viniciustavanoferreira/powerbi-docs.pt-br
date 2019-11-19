---
title: Usar o Kerberos para logon único (SSO) no SAP HANA
description: Configurar o servidor do SAP HANA para habilitar o SSO de serviço do Power BI
author: mgblythe
ms.author: mblythe
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 10/10/2019
LocalizationGroup: Gateways
ms.openlocfilehash: bf255e97bbce8360de6fba314ac181b7633e6db3
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/09/2019
ms.locfileid: "73872358"
---
# <a name="use-kerberos-for-single-sign-on-sso-to-sap-hana"></a>Usar o Kerberos para logon único (SSO) no SAP HANA

Este artigo descreve como configurar a fonte de dados do SAP HANA para habilitar o SSO no serviço do Power BI.

> [!NOTE]
> Antes de tentar atualizar um relatório baseado em SAP HANA que usa o SSO do Kerberos, conclua as etapas deste artigo e as etapas contidas em [Configurar o SSO do Kerberos](service-gateway-sso-kerberos.md).

## <a name="enable-sso-for-sap-hana"></a>Habilitar o SSO para SAP HANA

Para habilitar o SSO para o SAP HANA, siga estas etapas:

1. Verifique se o servidor SAP HANA está executando a versão mínima necessária, que depende do nível de plataforma de servidor SAP HANA:
   - [HANA 2 SPS 01 Rev 012.03](https://launchpad.support.sap.com/#/notes/2557386)
   - [HANA 2 SPS 02 Rev 22](https://launchpad.support.sap.com/#/notes/2547324)
   - [HANA 1 SP 12 Rev 122.13](https://launchpad.support.sap.com/#/notes/2528439)

2. No computador do gateway, instale o driver ODBC mais recente do SAP HANA. A versão mínima é o HANA ODBC versão 2.00.020.00 de agosto de 2017.

3. Verifique se o servidor do SAP HANA foi configurado para SSO baseado em Kerberos. Para obter mais informações sobre como configurar o SSO para o SAP HANA usando o Kerberos, confira [Logon único usando o Kerberos](https://help.sap.com/viewer/b3ee5778bc2e4a089d3299b82ec762a7/2.0.03/1885fad82df943c2a1974f5da0eed66d.html) no Guia de Segurança do SAP HANA. Confira também os links dessa página, particularmente a Nota SAP 1837331 – INSTRUÇÕES de SSO do BD HANA Kerberos/Active Directory.

Também recomendamos seguir estas etapas adicionais, que podem produzir uma pequena melhora no desempenho:

1. No diretório de instalação do gateway, localize e abra este arquivo de configuração: Microsoft.PowerBI.DataMovement.Pipeline.GatewayCore.dll.config.

2. Localize a propriedade `FullDomainResolutionEnabled` e altere seu valor para `True`.

    ```xml
    <setting name=" FullDomainResolutionEnabled " serializeAs="String">
          <value>True</value>
    </setting>
    ```

Agora você pode [Executar um relatório do Power BI](service-gateway-sso-kerberos.md#run-a-power-bi-report).

## <a name="next-steps"></a>Próximas etapas

Para saber mais sobre o gateway de dados local e o DirectQuery, confira estes recursos:

* [O que é um gateway de dados local?](/data-integration/gateway/service-gateway-onprem)
* [DirectQuery no Power BI](desktop-directquery-about.md)
* [Fontes de dados com suporte do DirectQuery](desktop-directquery-data-sources.md)
* [DirectQuery e SAP BW](desktop-directquery-sap-bw.md)
* [DirectQuery e SAP HANA](desktop-directquery-sap-hana.md)
