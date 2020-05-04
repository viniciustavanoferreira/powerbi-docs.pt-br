---
title: URLs do Power BI para a lista de permissões
description: Este artigo lista os pontos de extremidade de URL e as portas em uma lista segura para conexão com o Power BI.
author: kfollis
ms.author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 01/29/2020
ms.custom: seodec18
ms.openlocfilehash: 1426cb2926641ca93bcbff3e55ea151f829f290a
ms.sourcegitcommit: 1059c6222458f189fb5301dcb689dad2b2c00bc1
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2020
ms.locfileid: "82191604"
---
# <a name="power-bi-urls-for-whitelisting"></a>URLs do Power BI para a lista de permissões
[//]: # "suparnap e miwehnia são contatos para manter esta lista"

**O serviço online do Power BI**, também conhecido como aplicativo SaaS (Software como serviço) do Power BI, requer conectividade com a Internet. Os pontos de extremidade abaixo devem ser acessíveis para clientes que usam o serviço online do Power BI.

Para usar o serviço online do Power BI, é necessário conseguir se conectar aos pontos de extremidade marcados como **necessários** nas tabelas abaixo e a quaisquer pontos de extremidade marcados como **necessários** nos sites vinculados. Se o link para um site externo se referir a uma seção específica, será necessário apenas analisar os pontos de extremidade nessa seção.

Os pontos de extremidade marcados como **opcionais** também podem ser adicionados à **lista de permissões** para uma funcionalidade específica funcionar.

O serviço online do Power BI requer apenas que a porta TCP 443 seja aberta para os pontos de extremidade listados.

Caracteres curinga (*) representam todos os níveis sob o domínio raiz, e usaremos N/D quando as informações não estiverem disponíveis. A coluna **Destino(s)** é uma lista com domínios/FQDN e links para sites externos, que contêm mais informações sobre o ponto de extremidade.

>[!Important]
>As informações nas tabelas abaixo não representam a **nuvem do Governo dos EUA**, **a nuvem da Alemanha** ou a **nuvem da China**.

## <a name="authentication"></a>Autenticação

O Power BI depende dos pontos de extremidade necessários nas seções de identidade e autenticação do Office 365. Para usar o Power BI, conecte-se aos pontos de extremidade no site vinculado abaixo.

| Linha | Finalidade | Destino(s) | Porta(s) |
| --- | --- | --- | --- |
| 1 | **Obrigatório:** Autenticação e identidade | Confira a documentação do Office 365 do [Office Online e URLs comuns](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges#microsoft-365-common-and-office-online)  | N/D |

## <a name="general-site-usage"></a>Uso geral do site

Para o uso geral do Power BI, conecte-se aos pontos de extremidade na tabela e nos sites vinculados abaixo.

| Linha | Finalidade | Destino(s) | Porta(s) |
| --- | --- | --- | --- |
| 1 | **Obrigatório:** APIs de back-end | *.analysis.windows.net | TCP 443 |
| 2 | **Obrigatório:** APIs de back-end | *.pbidedicated.windows.net | TCP 443 |
| 3 | **Obrigatório:** integração do Office 365 | Confira a documentação do Office 365 do [Office Online e URLs comuns](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges#microsoft-365-common-and-office-online) | N/D |
| 4 | **Obrigatório:** Portal | app.powerbi.com | TCP 443 |
| 5 | **Obrigatório:** Telemetria do serviço | dc.services.visualstudio.com | TCP 443 |
| 6 | **Opcional:** Mensagens informativas | dynmsg.modpim.com | TCP 443 |
| 7 | **Opcional:** pesquisas NPS | nps.onyx.azure.net | TCP 443 |
| 8 | **Opcional:** CDN (Rede de Distribuição de Conteúdo) | content.powerapps.com | TCP 443 |
| | | |

## <a name="administration"></a>Administração

Para executar funções administrativas no Power BI, conecte-se aos pontos de extremidade nos sites vinculados abaixo.

| Linha | Finalidade | Destino(s) | Porta(s) |
| --- | --- | --- | --- |
| 1 | **Obrigatório:** Para gerenciar usuários e exibir logs de auditoria | Confira a documentação do Office 365 do [Office Online e URLs comuns](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges#microsoft-365-common-and-office-online) | N/D |
| | | |

## <a name="getting-data"></a>Obtendo dados

Para obter dados de fontes de dados específicas, como o OneDrive, você deve ser capaz de se conectar aos pontos de extremidade na tabela abaixo. O acesso a URLs e domínios de Internet adicionais pode ser necessário para fontes de dados específicas usadas na sua organização.

| Linha | Finalidade | Destino(s) | Porta(s) |
| --- | --- | --- | --- |
| 1 | **Obrigatório:** AppSource (aplicativos internos ou externos no Power BI) | appsource.microsoft.com <br> *.s-microsoft.com  | TCP 443 |
| 2 | **Opcional:** Entrar e obter dados para os pacotes de conteúdo | Depende dos pacotes de conteúdo usados | Depende dos pacotes de conteúdo usados |
| 3 | **Opcional:** Importar arquivos do OneDrive pessoal | Consulte o site [URLs e portas necessárias para o OneDrive](https://docs.microsoft.com/onedrive/required-urls-and-ports) | N/D |
| 4 | **Opcional:** vídeo de tutorial do Power BI em 60 segundos | *.doubleclick.net <br> *.ggpht.com <br> *.google.com <br> *.googlevideo.com <br> *.youtube.com <br> *.ytimg.com <br> fonts.gstatic.com | TCP 443 |
| 5 | **Opcional:** fontes de dados de streaming do PubNub | Consulte a [documentação do PubNub](https://support.pubnub.com/support/solutions/articles/14000043522) | N/D |
| | | |

## <a name="dashboard-and-report-integration"></a>Integração do dashboard e do relatório

O Power BI depende de determinados pontos de extremidade para dar suporte aos seus dashboards e relatórios. Você deve poder se conectar aos pontos de extremidade na tabela e nos sites vinculados abaixo.

| Linha | Finalidade | Destino(s) | Porta(s) |
| --- | --- | --- | --- |
| 1 | **Obrigatório:** integração do Excel | Confira a documentação do Office 365 do [Office Online e URLs comuns](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges#microsoft-365-common-and-office-online) | N/D |
| | | |

## <a name="power-bi-visuals"></a>Visuais do Power BI

O Power BI depende de determinados pontos de extremidade para exibir e acessar visuais. Você deve poder se conectar aos pontos de extremidade na tabela e nos sites vinculados abaixo.

| Linha | Finalidade | Destino(s) | Porta(s) |
| --- | --- | --- | --- |
| 1 | **Obrigatório:** Importar um visual personalizado da interface do Marketplace ou de um arquivo | *.azureedge.net <br> *.blob.core.windows.net <br> *.osi.office.net <br> *.msecnd.net <br> store.office.com <br> web.vortex.data.microsoft.com <br> store-images.s-microsoft.com | TCP 443 |
| 2 | **Opcional:** Bing Mapas | bing.com <br> platform.bing.com <br> *.virtualearth.net | TCP 443 |
| 3 | **Opcional:** PowerApps | Consulte a [seção Serviços necessários](https://docs.microsoft.com/powerapps/maker/canvas-apps/limits-and-config#required-services) no site de requisitos de sistema do PowerApps | N/D |
| 4 | **Opcional:** Visio | Confira a documentação do Office 365 para [Office Online e URLs comuns](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges#microsoft-365-common-and-office-online), bem como [SharePoint Online e OneDrive for Business](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges#sharepoint-online-and-onedrive-for-business) | N/D |
| | | |

## <a name="related-external-sites"></a>Sites externos relacionados

O Power BI contém links para outros sites relacionados. Esses sites hospedam documentação, suporte, solicitações de novos recursos e muito mais. O acesso a esses sites não afetará a funcionalidade do Power BI, portanto, a lista de permissões é opcional.

| Linha | Finalidade | Destino(s) | Porta(s) |
| --- | --- | --- | --- |
| 1 | **Opcional:** Site da comunidade | community.powerbi.com <br> oxcrx34285.i.lithium.com | TCP 443 |
| 2 | **Opcional:** Site de documentação | docs.microsoft.com <br> img-prod-cms-rt-microsoft-com.akamaized.net <br> statics-uhf-eas.akamaized.net <br> cdnssl.clicktale.net <br> ing-district.clicktale.net | TCP 443 |
| 3 | **Opcional:** Site de download (para o Power BI Desktop etc.) | download.microsoft.com | TCP 443 |
| 4 | **Opcional:** Redirecionamentos externos | aka.ms <br> go.microsoft.com | TCP 443 |
| 5 | **Opcional:** Site de comentários sobre ideias| ideas.powerbi.com <br> powerbi.uservoice.com | TCP 443 |
| 6 | **Opcional:** site do Power BI – página de aterrissagem, links para saber mais, site de suporte, links de download, demonstração do parceiro e assim por diante. | powerbi.microsoft.com | TCP 443 |
| 7 | **Opcional:** Central de desenvolvedores do Power BI | dev.powerbi.com | TCP 443 |
| 8 | **Opcional:** Site de suporte | support.powerbi.com <br> s3.amazonaws.com <br> *.olark.com <br> logx.optimizely.com <br> mscom.demdex.net <br> tags.tiqcdn.com | TCP 443 |
| | | |
