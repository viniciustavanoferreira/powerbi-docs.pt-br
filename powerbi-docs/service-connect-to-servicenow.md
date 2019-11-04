---
title: Conectar-se ao ServiceNow com o Power BI
description: ServiceNow para o Power BI
author: KesemSharabi
ms.author: sarinas
manager: rkarlin
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 10/16/2017
LocalizationGroup: Connect to services
ms.openlocfilehash: 4abf01163dbf454ee75b04e5d519ec2292b6e80c
ms.sourcegitcommit: d441d350504f8c6d9e100d229757add6237f0bef
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73060780"
---
# <a name="connect-to-servicenow-with-power-bi-for-incident-reporting"></a>Conectar-se ao ServiceNow com o Power BI para relatórios de incidentes
O ServiceNow oferece vários produtos e soluções, incluindo negócios, operações e gerenciamento de TI para melhorar os negócios. Este pacote de conteúdo inclui vários relatórios e insights sobre seus incidentes abertos, recentemente resolvidos e fechados recentemente.  

Conectar-se ao pacote de conteúdo do Power BI para [Incidentes do ServiceNow](https://app.powerbi.com/getdata/services/servicenow).

## <a name="how-to-connect"></a>Como se conectar
1. Selecione **Obter Dados** na parte inferior do painel de navegação esquerdo.
   
   ![](media/service-connect-to-servicenow/pbi_getdata.png) 
2. Na caixa **Serviços** , selecione **Obter**.
   
   ![](media/service-connect-to-servicenow/pbi_getservices.png) 
3. Selecione **Incidentes do ServiceNow** \> **Obter**.
   
   ![](media/service-connect-to-servicenow/connect.png)
4. Forneça a URL de sua instância do ServiceNow e o intervalo de dias/registros a ser trazido. Observe que quando um limite for atingido a importação será interrompida.
   
   ![](media/service-connect-to-servicenow/params.png)
5. Quando solicitado, insira as credenciais **básicas** do ServiceNow. Observe que o logon único não tem suporte atualmente, obtenha mais detalhes sobre os requisitos de sistema abaixo.
   
   ![](media/service-connect-to-servicenow/creds.png)
6. Quando o fluxo de logon estiver concluído, o processo de importação será iniciado. Quando concluído, um novo painel, relatório e modelo aparecerão no Painel de Navegação. Selecione o painel para exibir os dados importados por você.
   
    ![](media/service-connect-to-servicenow/dashboard.png)

**E agora?**

* Tente [fazer uma pergunta na caixa de P e R](consumer/end-user-q-and-a.md) na parte superior do dashboard
* [Altere os blocos](service-dashboard-edit-tile.md) no dashboard.
* [Selecione um bloco](consumer/end-user-tiles.md) para abrir o relatório subjacente.
* Enquanto seu conjunto de dados será agendado para ser atualizado diariamente, você pode alterar o agendamento de atualização ou tentar atualizá-lo sob demanda usando **Atualizar Agora**

## <a name="system-requirements"></a>Requisitos de sistema
Para se conectar, você precisará:  

* De uma conta que possa acessar yourorganization.service-now.com com a autenticação Básica (o Logon Único não tem suporte nesta versão)  
* A conta deve ter acesso de leitura e de função rest_service à tabela de incidentes  

## <a name="troubleshooting"></a>Solução de problemas
Se você estiver acessando um erro de credencial durante o carregamento, examine os requisitos de acesso acima. Se você tiver as permissões corretas e ainda estiver tendo problemas, trabalhe com seu administrador do ServiceNow para garantir que tenha permissões adicionais que podem ser necessárias para sua instância personalizada.

Se você estiver vendo tempos de carregamento longos, examine o número de incidentes e o número de dias especificado durante a conexão e considere reduzi-lo.

## <a name="next-steps"></a>Próximas etapas
[O que é o Power BI?](fundamentals/power-bi-overview.md)

[Conceitos básicos para designers no serviço do Power BI](service-basic-concepts.md)

