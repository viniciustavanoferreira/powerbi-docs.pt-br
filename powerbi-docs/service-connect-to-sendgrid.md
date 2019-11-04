---
title: Conectar-se ao SendGrid com o Power BI
description: SendGrid para o Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 08/29/2019
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: c9b844d153cab35938f5070ce4950c57f7964771
ms.sourcegitcommit: d441d350504f8c6d9e100d229757add6237f0bef
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73060529"
---
# <a name="connect-to-sendgrid-with-power-bi"></a>Conectar-se ao SendGrid com o Power BI
O pacote de conteúdo do SendGrid para o Power BI permite que você extraia informações e estatísticas de sua conta do SendGrid. Com o pacote de conteúdo do SendGrid, é possível visualizar suas estatísticas do SendGrid em um painel.

[!INCLUDE [include-short-name](./includes/service-deprecate-content-packs.md)]

Conecte-se ao [pacote de conteúdo do SendGrid](https://app.powerbi.com/getdata/services/sendgrid) para o Power BI.

## <a name="how-to-connect"></a>Como se conectar
1. Selecione **Obter Dados** na parte inferior do painel de navegação esquerdo.
   
   ![](media/service-connect-to-sendgrid/pbi_getdata.png) 
2. Na caixa **Serviços** , selecione **Obter**.
   
   ![](media/service-connect-to-sendgrid/pbi_getservices.png) 
3. Selecione o pacote de conteúdo do **SendGrid** e clique em **Obter**.
   
   ![](media/service-connect-to-sendgrid/sendgrid.png) 
4. Quando solicitado, forneça seu nome de usuário e senha do SendGrid. Selecione **Entrar**.
   
   ![](media/service-connect-to-sendgrid/pbi_sendgridsignin.png)
5. Depois que o Power BI importar os dados, você verá um painel, relatório e conjunto de dados novos no painel de navegação esquerdo, preenchidos com suas estatísticas de email correspondentes aos últimos 90 dias. Novos itens são marcados com um asterisco amarelo \*.
   
   ![](media/service-connect-to-sendgrid/pbi_sendgriddash.png)

**E agora?**

* Tente [fazer uma pergunta na caixa de P e R](consumer/end-user-q-and-a.md) na parte superior do dashboard
* [Altere os blocos](service-dashboard-edit-tile.md) no dashboard.
* [Selecione um bloco](consumer/end-user-tiles.md) para abrir o relatório subjacente.
* Enquanto seu conjunto de dados será agendado para ser atualizado diariamente, você pode alterar o agendamento de atualização ou tentar atualizá-lo sob demanda usando **Atualizar Agora**

## <a name="whats-included"></a>O que está incluído
As métricas a seguir estão disponíveis no painel do SendGrid:

* Estatísticas globais de email - Solicitações, Entregues, Devolvidos, Bloqueados por Spam, Relatório de Spam, etc.
* Estatísticas de email por categoria
* Estatísticas de email por geografia
* Estatísticas de email por ISP
* Estatísticas de email por dispositivo, cliente ou navegador

## <a name="next-steps"></a>Próximas etapas
[O que é o Power BI?](fundamentals/power-bi-overview.md)

[Obter dados](service-get-data.md)

