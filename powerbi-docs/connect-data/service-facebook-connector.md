---
title: 'Serviço de terceiros: Conector do Facebook para Power BI Desktop'
description: 'Serviço de terceiros: Conector do Facebook para Power BI Desktop'
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 02/20/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 882cddf7728a27e78056a35c14fde20f00678e33
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83309534"
---
# <a name="use-the-facebook-connector-for-power-bi-desktop"></a>Usar o conector do Facebook para Power BI Desktop
O conector do Facebook no **Power BI Desktop** depende da API do Graph do Facebook. Por isso, os recursos e a disponibilidade podem variar ao longo do tempo.

Você pode ver um [tutorial sobre o Conector do Facebook para o Power BI Desktop](desktop-tutorial-facebook-analytics.md).

> [!IMPORTANT]
> **Aviso de substituição do conector de dados do Facebook:** a importação e a atualização de dados do Facebook no Excel não funcionarão mais adequadamente a partir de abril de 2020. Você pode usar o conector *Obter e Transformar (Power Query)* do Facebook até lá. Após essa data, você não poderá se conectar ao Facebook e receberá uma mensagem de erro. Nós recomendamos revisar ou remover qualquer consulta *Obter e Transformar (Power Query)* existente que use o conector do Facebook assim que possível para evitar resultados inesperados.


Em 30 de abril de 2015, o Facebook expirou a versão 1.0 da API do Graph. O Power BI usa a Graph API nos bastidores para o conector do Facebook, permitindo que você se conecte aos seus dados e os analise.

As consultas criadas antes de 30 de abril de 2015 podem não funcionar ou retornar menos dados. Após 30 de abril de 2015, o Power BI passou a usar a versão 2.8 em todas as chamadas para a API do Facebook. Se a consulta foi criada antes de 30 de abril de 2015 e você não a usou, provavelmente precisará autenticar novamente para aprovar o novo conjunto de permissões que solicitaremos.

Podemos tentar lançar atualizações de acordo com as alterações, o API pode ser alterado de forma que afeta os resultados das consultas que gerarmos. Em alguns casos, determinadas consultas podem não ter mais suporte. Devido a essa dependência, não podemos garantir os resultados de suas consultas com o uso desse conector.

Mais detalhes sobre a alteração na API do Facebook estão disponíveis [aqui](https://developers.facebook.com/docs/apps/changelog#v2_0).

