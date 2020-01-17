---
title: 'Serviço de terceiros: Conector do Facebook para Power BI Desktop'
description: 'Serviço de terceiros: Conector do Facebook para Power BI Desktop'
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: dcfc695d0371cce21a827ddfe71b3b4b05863935
ms.sourcegitcommit: 97597ff7d9ac2c08c364ecf0c729eab5d59850ce
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75762406"
---
# <a name="use-the-facebook-connector-for-power-bi-desktop"></a>Usar o conector do Facebook para Power BI Desktop
O conector do Facebook no **Power BI Desktop** depende da API do Graph do Facebook. Por isso, os recursos e a disponibilidade podem variar ao longo do tempo.

Você pode ver um [tutorial sobre o Conector do Facebook para o Power BI Desktop](desktop-tutorial-facebook-analytics.md).

Em 30 de abril de 2015, o Facebook expirou a versão 1.0 da API do Graph. O Power BI usa a Graph API nos bastidores para o conector do Facebook, permitindo que você se conecte aos seus dados e os analise.

As consultas criadas antes de 30 de abril de 2015 podem não funcionar ou retornar menos dados. Após 30 de abril de 2015, o Power BI passou a usar a versão 2.8 em todas as chamadas para a API do Facebook. Se a consulta foi criada antes de 30 de abril de 2015 e você não a usou, provavelmente precisará autenticar novamente para aprovar o novo conjunto de permissões que solicitaremos.

Podemos tentar lançar atualizações de acordo com as alterações, o API pode ser alterado de forma que afeta os resultados das consultas que gerarmos. Em alguns casos, determinadas consultas podem não ter mais suporte. Devido a essa dependência, não podemos garantir os resultados de suas consultas com o uso desse conector.

Mais detalhes sobre a alteração na API do Facebook estão disponíveis [aqui](https://developers.facebook.com/docs/apps/changelog#v2_0).

