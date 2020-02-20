---
title: Capacidade e SKUs na análise integrada do Power BI
description: Compreenda a capacidade e os SKUs na análise integrada do Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 02/11/2020
ms.openlocfilehash: f8c3bdf3e3f92d570205551a97389def2921fe98
ms.sourcegitcommit: 17aad73762579d6822383b27b96b1b63f87f2d6f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77260447"
---
# <a name="capacity-and-skus-in-power-bi-embedded-analytics"></a>Capacidade e SKUs na análise integrada do Power BI

Ao passar para a produção, a análise integrada do Power BI requer uma capacidade dedicada (SKU *A*, *EM* ou *P*) para publicar conteúdo inserido do Power BI.

A capacidade é um conjunto de recursos dedicado reservado para seu uso exclusivo. Ela permite publicar dashboards, relatórios e conjuntos de dados para seus usuários sem precisar comprar licenças por usuário. Ela também oferece desempenho confiável e constante para seu conteúdo.

>[!NOTE]
>Para publicação, você precisará de uma conta do Power BI Pro.

## <a name="what-is-embedded-analytics"></a>O que é a análise integrada?

A análise integrada do Power BI inclui duas soluções:
* *Power BI Embedded* – oferta do Azure
* Inserir o Power BI como parte do *Power BI Premium* – oferta do Office

### <a name="power-bi-embedded"></a>Power BI Embedded

O Power BI Embedded é voltado para ISVs e desenvolvedores que desejam inserir visuais em seus aplicativos.

Aplicativos que usam o Power BI Embedded permitem que os usuários consumam conteúdo armazenado na capacidade do Power BI Embedded.

### <a name="power-bi-premium"></a>Power BI Premium

O [Power BI Premium](../service-premium-what-is.md) é voltado para empresas que desejam uma solução de BI completa que ofereça uma visão unificada da organização, dos parceiros, dos clientes e dos fornecedores.

O Power BI Premium é um produto SaaS que permite aos usuários consumir conteúdo por meio de aplicativos móveis, de aplicativos desenvolvidos internamente ou no portal do Power BI (serviço do Power BI). Isso permite que o Power BI Premium forneça uma solução para aplicativos voltados para clientes internos e externos.

## <a name="capacity-and-skus"></a>Capacidade e SKUs

Cada capacidade oferece uma seleção de SKUs e cada SKU fornece diferentes camadas de recursos de memória e capacidade de computação. O tipo de SKU de que você precisa depende do tipo de solução que deseja implantar.

Antes de decidir qual SKU comprar, examine as informações nesta seção.
* Para entender quais cargas de trabalho são compatíveis com cada nível, confira o artigo [Configurar cargas de trabalho em uma capacidade Premium](../service-admin-premium-workloads.md)
* Use este link para [planejar e testar sua capacidade](../service-premium-capacity-optimize.md#testing-approaches)

### <a name="power-bi-embedded-skus"></a>SKUs do Power BI Embedded

O Power BI Embedded é fornecido com um SKU *A*.
* [Saiba com qual capacidade seu Power BI Embedded pode lidar](https://powerbi.microsoft.com/blog/power-bi-developer-community-june-july-update/#Capacity-Plan)
* [Compre um SKU *A*](../service-admin-premium-purchase.md#purchase-a-skus-for-testing-and-other-scenarios)

### <a name="power-bi-premium-skus"></a>SKUs do Power BI Premium

O Power BI Premium oferece dois SKUs, *P* e *EM*.
* [Entenda as diferenças entre os SKUs *P* e *EM*](../service-premium-what-is.md#subscriptions-and-licensing)
* [Compre um SKU Premium](../service-admin-premium-purchase.md)

### <a name="which-sku-should-i-use"></a>Qual SKU devo usar?

Esta tabela fornece um resumo dos recursos, da capacidade que eles exigem e do SKU específico necessário para cada um. 

</br>
<table>
<col width="20%">
<col width="20%">
<col width="20%">
<col width="20%">
<col width="20%">
<tbody>
<tr>
<td style="text-align: center"; colspan="2"><p><b>Recurso</b></p></td>
<td style="text-align: center">
<p><b>Power BI Embedded</b></p>
</td>
<td style="text-align: center"; colspan="2">
<p><b>Power BI Premium</b></p>
</td>
</tr>
<tr>
<td><p><em>O que é consumido?</em><p></td>
<td><p><em>O que está consumindo?</em><p></td>
<td style="text-align: center"><p><em>SKUs A</br>(Azure)</em></p></td>
<td style="text-align: center"><p><em>SKUs EM</br>(Office)</em></p></td>
<td style="text-align: center"><p><em>SKUs P</br>(Office)</em></p></td>
</tr>
<tr>
<td>Inserir artefatos de um workspace do Power BI</td>
<td>
</td>
<td style="text-align: center">✔</td>
<td style="text-align: center">✔</td>
<td style="text-align: center">✔</td>
</tr>
<tr>
<td rowspan="2">Relatórios do Power BI</td>
<td>Um aplicativo inserido para sua organização</br>(o usuário possui dados)</td>
<td style="text-align: center">✖</td>
<td style="text-align: center">✔</td>
<td style="text-align: center">✔</td>
</tr>
<tr>
<td>Um aplicativo inserido para seus clientes</br>(o aplicativo possui dados)</td>
<td style="text-align: center">✔</td>
<td style="text-align: center">✔</td>
<td style="text-align: center">✔</td>
</tr>
<tr>
<td rowspan="3">Conteúdo do Power BI<br>(com uma licença gratuita do Power BI)</td>
<td>Serviço do Power BI</td>
<td style="text-align: center">✖</td>
<td style="text-align: center">✖</td>
<td style="text-align: center">✔</td>
</tr>
<tr>
<td>Power BI Mobile</td>
<td style="text-align: center">✖</td>
<td style="text-align: center">✖</td>
<td style="text-align: center">✔</td>
</tr>
<tr>
<td>Aplicativos do MS Office</td>
<td style="text-align: center">✖</td>
<td style="text-align: center">✔</td>
<td style="text-align: center">✔</td>
</tr>
</tbody>
</table>

### <a name="capacity-considerations"></a>Considerações sobre a capacidade

A tabela abaixo lista as considerações de pagamento e uso por capacidade.

</br>
<table>
<tbody>
<tr>
<td></td>
<td style="text-align: center;"><p><strong>Power BI Embedded</strong></p></td>
<td style="text-align: center;" colspan="2"><p><strong>Power BI Premium</strong></p></td>
</tr>
<tr>
<td><p><strong>Oferta</strong></p></td>
<td style="text-align: center;"><p>Azure</p></td>
<td style="text-align: center;" colspan="2"><p>Office</p></td>
</tr>
<tr>
<td><p><strong>SKU</strong></p></td>
<td style="text-align: center;"><p>A</p></td>
<td style="text-align: center;"><p>EM</p></td>
<td style="text-align: center;"><p>P</p></td>
</tr>
<tr>
<td><p><strong>Billing</strong></td>
<td style="text-align: center;">A cada hora</td>
<td style="text-align: center;">Mensal</td>
<td style="text-align: center;">Mensal</td>
</tr>
<tr>
<td><p><strong>Compromisso</strong></td>
<td style="text-align: center;">Nenhum</td>
<td style="text-align: center;">Mensal ou anual</td>
<td style="text-align: center;">Mensal ou anual</td>
</tr>
<tr>
<td valign="top"><p><strong>Usage</strong></td>
<td style="text-align: center;">Os recursos do Azure podem ser:</br>- <a href="azure-pbie-scale-capacity.md">Escalados ou reduzidos verticalmente</a></br>- <a href="azure-pbie-pause-start.md">Pausados e retomados</a>
</td>
<td style="text-align: center;">Inserir em aplicativos e em</br> aplicativos da Microsoft</td>
<td style="text-align: center;">Inserir em aplicativos e</br> no serviço do Power BI</td>
</tr>
</tbody>
</table>

### <a name="sku-memory-and-computing-power"></a>Memória e capacidade de computação da SKU

A tabela a seguir descreve os recursos e limites de cada SKU.

| Nós de Capacidade | Total de núcleos virtuais | Núcleos virtuais de back-end | RAM (GB) | Núcleos virtuais de front-end | DirectQuery/Conexão Dinâmica (por s) | Paralelismo de atualização de modelo |
| --- | --- | --- | --- | --- | --- | --- |
| EM1/A1 | 1 | 0,5 | 2.5 | 0,5 | 3,75 | 1 |
| EM2/A2 | 2 | 1 | 5 | 1 | 7,5 | 2 |
| EM3/A3 | 4 | 2 | 10 | 2 | 15 | 3 |
| P1/A4 | 8 | 4 | 25 | 4 | 30 | 6 |
| P2/A5 | 16 | 8 | 50 | 8 | 60 | 12 |
| P3/A6 | 32 | 16 | 100 | 16 | 120 | 24 |
| P4 | 64 | 32 | 200 | 32 | 240 | 48 |
| P5 | 128 | 64 | 400 | 64 | 480 | 96 |
| | | | | | | |

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
>[Inserir para seus clientes](embed-sample-for-customers.md)

> [!div class="nextstepaction"]
>[Inserir para a organização](embed-sample-for-your-organization.md)

> [!div class="nextstepaction"]
> [Inserir de aplicativos](embed-from-apps.md)