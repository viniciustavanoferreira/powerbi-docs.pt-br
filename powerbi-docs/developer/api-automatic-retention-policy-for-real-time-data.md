---
title: APIs do Power BI que usam a política de retenção automática para dados em tempo real
description: Saiba mais sobre a política de retenção automática no serviço do Power BI
author: rkarlin
ms.author: rkarlin
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 06/08/2018
ms.openlocfilehash: 07726535246f8b115402373c315062151177d27c
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "61347286"
---
# <a name="automatic-retention-policy-for-real-time-data"></a>Política de retenção automática para dados em tempo real

A política de retenção automática no serviço Power BI é um parâmetro de cadeia de caracteres de consulta que permite que uma política de retenção padrão limpe automaticamente os dados antigos, mantendo um fluxo constante de novos dados direcionados ao dashboard. A primeira política de retenção é chamada de *PEPS (primeiro a entrar, primeiro a sair)*. Quando está habilitada, os dados são coletados em uma tabela até que esta atinja 200.000 linhas. Depois que os dados ultrapassam 200.000 linhas, as linhas mais antigas são descartadas do conjunto de dados. Isso mantém entre 200.000 e 210.000 linhas apenas com os dados mais recentes.  
  
<center>

![política de retenção](media/api-Automatic-retention-policy-for-real-time-data/retention-policy.png) 

</center>

As políticas de retenção são habilitadas quando você cria pela primeira vez seus conjuntos de dados. Tudo o que você precisa fazer é adicionar o parâmetro de consulta "default retention policy" à sua chamada de conjuntos de dados POST e defini-lo como *basicFIFO*.  
  
    POST https://api.powerbi.com/v1.0/myorg/datasets?defaultRetentionPolicy={None | basicFIFO}