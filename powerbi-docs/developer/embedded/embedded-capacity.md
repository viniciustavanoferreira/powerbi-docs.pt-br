---
title: Capacidade e SKUs na análise integrada do Power BI
description: Compreenda a capacidade e os SKUs na análise integrada do Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 05/17/2020
ms.openlocfilehash: 1e2426b12bf6205e5ed2fc6cfb0540c67740df7d
ms.sourcegitcommit: 2cb249fc855e369eed1518924fbf026d5ee07eb1
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/24/2020
ms.locfileid: "83813613"
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

O [Power BI Premium](../../admin/service-premium-what-is.md) é voltado para empresas que desejam uma solução de BI completa que ofereça uma visão unificada da organização, dos parceiros, dos clientes e dos fornecedores.

O Power BI Premium é um produto SaaS que permite aos usuários consumir conteúdo por meio de aplicativos móveis, de aplicativos desenvolvidos internamente ou no portal do Power BI (serviço do Power BI). Isso permite que o Power BI Premium forneça uma solução para aplicativos voltados para clientes internos e externos.

## <a name="capacity-and-skus"></a>Capacidade e SKUs

Cada capacidade oferece uma seleção de SKUs e cada SKU fornece diferentes camadas de recursos de memória e capacidade de computação. O tipo de SKU de que você precisa depende do tipo de solução que deseja implantar.

Para entender quais cargas de trabalho são compatíveis com cada nível, confira o artigo [Configurar cargas de trabalho em uma capacidade Premium](../../admin/service-admin-premium-workloads.md)

Use os links a seguir para planejar e testar sua capacidade:
* [Planejamento da capacidade](embedded-capacity-planning.md)
* [Abordagens do teste](../../admin/service-premium-capacity-optimize.md#testing-approaches)

### <a name="power-bi-embedded-skus"></a>SKUs do Power BI Embedded

O Power BI Embedded é fornecido com um [*a* SKU](../../admin/service-admin-premium-purchase.md#purchase-a-skus-for-testing-and-other-scenarios).

### <a name="power-bi-premium-skus"></a>SKUs do Power BI Premium

O Power BI Premium oferece dois SKUs, *P* e *EM*.
* [Entenda as diferenças entre os SKUs *P* e *EM*](../../admin/service-premium-what-is.md#subscriptions-and-licensing)
* [Compre um SKU Premium](../../admin/service-admin-premium-purchase.md)

### <a name="which-sku-should-i-use"></a>Qual SKU devo usar?

A tabela abaixo fornece um resumo dos recursos, da capacidade que eles exigem e do SKU específico necessário para cada um.

Nesta tabela, um aplicativo personalizado refere-se a um aplicativo Web criado usando análise integrada. Ao fazer a inserção como desenvolvedor a um aplicativo Web personalizado (usando os SDKs .NET ou JavaScript, ou as APIs REST), você tem a capacidade de controlar e personalizar a experiência de usuário. Essa capacidade não está disponível quando você usa outras opções de incorporação, como serviço do Power BI e Power BI Mobile.


|         |         |         |
|---------|---------|---------|
|**Cenário**</br><p></p>|**Azure**</br>(Um SKU)|**Office**</br>(SKUs EM e P)|
|[Inserir para seus clientes](embed-sample-for-customers.md)</br>(o aplicativo possui dados)     |✔        |✔        |
|[Inserir para a organização](embed-sample-for-your-organization.md)</br>(o usuário possui dados)     |✖        |✔         |
|Aplicativos do Microsoft 365</br>(anteriormente conhecidos como aplicativos do Office 365)<ul><li>[Inserir no Teams](../../collaborate-share/service-embed-report-microsoft-teams.md)</li><li>[Inserir no SharePoint](../../collaborate-share/service-embed-report-spo.md)</li></ul>     |✖        |✔        |
|[Incorporação de URL segura](../../collaborate-share/service-embed-secure.md)</br>(inserir do serviço do Power BI)     |✖        |✔        |

>[!NOTE]
>* Uma [licença do Power BI Pro](../../admin/service-admin-purchasing-power-bi-pro.md) é necessária para publicar conteúdo em um workspace do aplicativo Power BI.
>* Somente o **SKU P** permite que usuários Power BI gratuito consumam conteúdo compartilhado e aplicativos do Power BI no serviço do Power BI.

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
<td style="text-align: center"><p>Azure</p></td>
<td style="text-align: center" colspan="2"><p>Office</p></td>
</tr>
<tr>
<td><p><strong>SKU</strong></p></td>
<td style="text-align: center"><p>A</p></td>
<td style="text-align: center"><p>EM</p></td>
<td style="text-align: center"><p>P</p></td>
</tr>
<tr>
<td><p><strong>Billing</strong></td>
<td style="text-align: center">A cada hora</td>
<td style="text-align: center">Mensal</td>
<td style="text-align: center">Mensal</td>
</tr>
<tr>
<td><p><strong>Compromisso</strong></td>
<td style="text-align: center">Nenhum</td>
<td style="text-align: center">Anual</td>
<td style="text-align: center">Mensal ou anual</td>
</tr>
<tr>
<td valign="top"><p><strong>Usage</strong></td>
<td style="text-align: center">Os recursos do Azure podem ser:<li><a href="azure-pbie-scale-capacity.md">Escalados ou reduzidos verticalmente</a></li><li><a href="azure-pbie-pause-start.md">Pausados e retomados</a>
</td></li>
<td style="text-align: center">Inserir em aplicativos e em</br> aplicativos da Microsoft</td>
<td style="text-align: center">Inserir em aplicativos e</br> no serviço do Power BI</td>
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