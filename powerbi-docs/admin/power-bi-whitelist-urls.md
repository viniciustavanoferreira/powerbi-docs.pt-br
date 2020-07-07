---
title: Adicionar URLs do Power BI à lista de permissões
description: Este artigo lista as portas e os pontos de extremidade de URL a serem adicionados à sua lista de permissões para conexão com o Power BI.
author: kfollis
ms.author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 06/25/2020
ms.custom: seodec18
ms.openlocfilehash: 38e6668c0fb15d1279923b77042cdedebe6dd139
ms.sourcegitcommit: a453ba52aafa012896f665660df7df7bc117ade5
ms.contentlocale: pt-BR
ms.lasthandoff: 06/27/2020
ms.locfileid: "85485060"
---
# <a name="add-power-bi-urls-to-your-allow-list"></a>Adicionar URLs do Power BI à sua lista de permissões
[//]: # "suparnap, miwehnia, natham são contatos para manter essa lista"

O serviço do Power BI requer conectividade com a Internet. Os pontos de extremidade listados nas tabelas deste artigo devem ser acessíveis para clientes que usam o serviço do Power BI.

Para usar o serviço do Power BI, é necessário conseguir se conectar aos pontos de extremidade marcados como **obrigatórios** nas tabelas abaixo e aos pontos de extremidade marcados como **obrigatórios** nos sites vinculados. Se o link para um site externo se referir a uma seção específica, será necessário apenas analisar os pontos de extremidade nessa seção.

Os pontos de extremidade marcados como **opcionais** também podem ser adicionados às listas de permissões para habilitar uma funcionalidade específica.

O serviço do Power BI requer apenas que a porta TCP 443 seja aberta para os pontos de extremidade listados.

Caracteres curinga (*) representam todos os níveis sob o domínio raiz, e usaremos N/D quando as informações não estiverem disponíveis. A coluna **Destino(s)** lista os nomes de domínios e os links para sites externos que contêm mais informações sobre o ponto de extremidade.

>[!Important]
>As informações nas tabelas abaixo não se aplicam ao Power BI Alemanha, Power BI China operado pela 21Vianet ou Power BI for US Government. Leia [Conectar os serviços de nuvem do Azure globais e governamentais](service-govus-overview.md#connect-government-and-global-azure-cloud-services) para saber mais sobre a comunicação entre os serviços de nuvem.

## <a name="authentication"></a>Autenticação

O Power BI depende dos pontos de extremidade necessários nas seções de identidade e autenticação do Microsoft 365. Para usar o Power BI, conecte-se aos pontos de extremidade no site vinculado abaixo.

| Linha | Finalidade | Destino(s) | Porta(s) |
| --- | --- | --- | --- |
| 1 | **Obrigatório:** Autenticação e identidade | Confira a documentação com as [URLs do Microsoft 365 Common e do Office Online](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges#microsoft-365-common-and-office-online)  | N/D |

## <a name="general-site-usage"></a>Uso geral do site

Para o uso geral do Power BI, conecte-se aos pontos de extremidade na tabela e nos sites vinculados abaixo.

| Linha | Finalidade | Destino(s) | Porta(s) |
| --- | --- | --- | --- |
| 1 | **Obrigatório:** APIs de back-end | api.powerbi.com | TCP 443 |
| 2 | **Obrigatório:** APIs de back-end | *.analysis.windows.net | TCP 443 |
| 3 | **Obrigatório:** APIs de back-end | *.pbidedicated.windows.net | TCP 443 |
| 4 | **Obrigatório:** CDN (Rede de Distribuição de Conteúdo) | content.powerapps.com | TCP 443 |
| 5 | **Obrigatório:** integração do Microsoft 365 | Confira a documentação com as [URLs do Microsoft 365 Common e do Office Online](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges#microsoft-365-common-and-office-online) | N/D |
| 6 | **Obrigatório:** Portal | *.powerbi.com | TCP 443 |
| 7 | **Obrigatório:** Telemetria do serviço | dc.services.visualstudio.com | TCP 443 |
| 8 | **Opcional:** Mensagens informativas | dynmsg.modpim.com | TCP 443 |
| 9 | **Opcional:** pesquisas NPS | nps.onyx.azure.net | TCP 443 |
| | | |

## <a name="administration"></a>Administração

Para executar funções administrativas no Power BI, conecte-se aos pontos de extremidade nos sites vinculados abaixo.

| Linha | Finalidade | Destino(s) | Porta(s) |
| --- | --- | --- | --- |
| 1 | **Obrigatório:** Para gerenciar usuários e exibir logs de auditoria | Confira a documentação com as [URLs do Microsoft 365 Common e do Office Online](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges#microsoft-365-common-and-office-online) | N/D |
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
| 1 | **Obrigatório:** integração do Excel | Confira a documentação com as [URLs do Microsoft 365 Common e do Office Online](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges#microsoft-365-common-and-office-online) | N/D |
| | | |

## <a name="power-bi-visuals"></a>Visuais do Power BI

O Power BI depende de determinados pontos de extremidade para exibir e acessar visuais. Você deve poder se conectar aos pontos de extremidade na tabela e nos sites vinculados abaixo.

| Linha | Finalidade | Destino(s) | Porta(s) |
| --- | --- | --- | --- |
| 1 | **Obrigatório:** Importar um visual personalizado da interface do Marketplace ou de um arquivo | *.azureedge.net <br> *.blob.core.windows.net <br> *.osi.office.net <br> *.msecnd.net <br> store.office.com <br> web.vortex.data.microsoft.com <br> store-images.s-microsoft.com | TCP 443 |
| 2 | **Opcional:** Bing Mapas | bing.com <br> platform.bing.com <br> *.virtualearth.net | TCP 443 |
| 3 | **Opcional:** PowerApps | Consulte a [seção Serviços necessários](https://docs.microsoft.com/powerapps/maker/canvas-apps/limits-and-config#required-services) no site de requisitos de sistema do PowerApps | N/D |
| 4 | **Opcional:** Visio | Confira a documentação das [URLs Online do Microsoft 365 Common and Office](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges#microsoft-365-common-and-office-online), bem como do [SharePoint Online e OneDrive for Business](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges#sharepoint-online-and-onedrive-for-business) | N/D |
| | | |

## <a name="related-external-sites"></a>Sites externos relacionados

O Power BI contém links para outros sites relacionados. Esses sites hospedam documentação, suporte, solicitações de novos recursos e muito mais. O acesso a esses sites não afetará a funcionalidade do Power BI, portanto, adicioná-los à lista de permissões é opcional.

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
