---
title: Power BI e ExpressRoute
description: Power BI e ExpressRoute
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 09/09/2019
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: c7d12bf6a1a2a02c988f8351a1844be1080ad2b8
ms.sourcegitcommit: a97c0c34f888e44abf4c9aa657ec9463a32be06f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71074788"
---
# <a name="power-bi-and-expressroute"></a>Power BI e ExpressRoute

O **ExpressRoute** é um serviço do Azure que permite criar conexões privadas entre datacenters do Azure (nos quais o Power BI reside) e sua infraestrutura local ou criar conexões privadas entre datacenters do Azure e seu ambiente de colocação.

Com o **Power BI** e o **ExpressRoute**, é possível criar uma conexão de rede privada de sua organização para o Power BI (ou usando as instalações de colocação de um ISP), ignorando a Internet para proteger melhor seus dados e conexões confidenciais do Power BI.

Para obter mais informações, consulte [Visão geral de ExpressRoute](/azure/expressroute/expressroute-introduction). O Power BI está em conformidade com o ExpressRoute, exceto em alguns casos em que o Power BI recebe ou envia dados pela Internet pública. Para obter uma lista de URLs que o Power BI usa, consulte [URLs do Power BI](power-bi-whitelist-urls.md).

![Diagrama do ExpressRoute](media/service-admin-power-bi-expressroute/pbi_expressroute_1.png)