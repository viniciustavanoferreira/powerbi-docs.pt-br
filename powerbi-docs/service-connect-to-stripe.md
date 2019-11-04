---
title: Conectar-se ao Stripe com o Power BI
description: Stripe para o Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 08/29/2019
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: b0e8739e93d24ba10b0ffc72042b847cce1d5fe9
ms.sourcegitcommit: d441d350504f8c6d9e100d229757add6237f0bef
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73060763"
---
# <a name="connect-to-stripe-with-power-bi"></a>Conectar-se ao Stripe com o Power BI
Visualize e explore seus dados do Stripe para o Power BI com o pacote de conteúdo para o Power BI. O pacote de conteúdo do Stripe para o Power BI recebe dados por pull sobre Clientes, Encargos, Eventos e Faturas. Os dados incluem os dez mil eventos e cinco mil encargos mais recentes nos últimos 30 dias. O conteúdo será atualizado automaticamente uma vez por dia em uma agenda sob seu controle. 

[!INCLUDE [include-short-name](./includes/service-deprecate-content-packs.md)]

Conecte-se ao [pacote de conteúdo do Stripe para o Power BI](https://app.powerbi.com/getdata/services/stripe).

## <a name="how-to-connect"></a>Como se conectar
1. Selecione Obter Dados na parte inferior do painel de navegação esquerdo.  
   
    ![](media/service-connect-to-stripe/getdata.png)
2. Na caixa **Serviços** , selecione **Obter**.  
   
    ![](media/service-connect-to-stripe/services.png)  
3. Selecione **Stripe** &gt; **Obter**.  
   
    ![](media/service-connect-to-stripe/stripe.png)  
4. Forneça sua [chave de API](https://dashboard.stripe.com/account/apikeys) do Stripe para se conectar.  
   
    ![](media/service-connect-to-stripe/creds.png)
5. O processo de importação será iniciado automaticamente. Quando concluído, um novo painel, relatório e modelo aparecerão no Painel de Navegação, marcados com um asterisco. Selecione o painel para exibir os dados importados por você.
   
    ![](media/service-connect-to-stripe/dashboard.png)

**E agora?**

* Tente [fazer uma pergunta na caixa de P e R](consumer/end-user-q-and-a.md) na parte superior do dashboard
* [Altere os blocos](service-dashboard-edit-tile.md) no dashboard.
* [Selecione um bloco](consumer/end-user-tiles.md) para abrir o relatório subjacente.
* Enquanto seu conjunto de dados será agendado para ser atualizado diariamente, você pode alterar o agendamento de atualização ou tentar atualizá-lo sob demanda usando **Atualizar Agora**

## <a name="next-steps"></a>Próximas etapas
[O que é o Power BI?](fundamentals/power-bi-overview.md)

[Obter dados para o Power BI](service-get-data.md)

