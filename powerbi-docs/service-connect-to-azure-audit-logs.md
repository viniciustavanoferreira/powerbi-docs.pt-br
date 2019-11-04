---
title: Conectar-se aos Logs de Auditoria do Azure com o Power BI
description: Logs de Auditoria do Azure para o Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 08/29/2019
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: 42b56cbad4c47b8cc8133a1f35511ea48ac24055
ms.sourcegitcommit: d441d350504f8c6d9e100d229757add6237f0bef
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73060606"
---
# <a name="connect-to-azure-audit-logs-with-power-bi"></a>Conectar-se aos Logs de Auditoria do Azure com o Power BI
Com o pacote de conteúdo de Logs de Auditoria do Azure, você pode analisar e visualizar as informações armazenadas nos logs de auditoria. O Power BI recupera seus dados, cria um painel inicial e cria relatórios com base nesses dados.

[!INCLUDE [include-short-name](./includes/service-deprecate-content-packs.md)]

[Conecte-se ao pacote de conteúdo dos Logs de Auditoria do Azure](https://app.powerbi.com/getdata/services/azure-audit-logs) ou leia mais sobre a [integração dos Logs de Auditoria do Azure](https://powerbi.microsoft.com/integrations/azure-audit-logs) com o Power BI.

## <a name="how-to-connect"></a>Como se conectar
1. Selecione **Obter Dados** na parte inferior do painel de navegação esquerdo.  
   
    ![](media/service-connect-to-azure-audit-logs/getdata.png)
2. Na caixa **Serviços** , selecione **Obter**.  
   
    ![](media/service-connect-to-azure-audit-logs/services.png) 
3. Selecione **Logs de Auditoria do Azure** > **Obter**.  
   
   ![](media/service-connect-to-azure-audit-logs/azureauditlogs.png)
4. Quando solicitado, insira a **ID da assinatura do Azure**. Consulte detalhes sobre como localizar sua [ID da assinatura](#FindingParams) abaixo.   
   
    ![](media/service-connect-to-azure-audit-logs/parameters.png)
5. Para o **Método de Autenticação**, selecione **oAuth2** \> **Entrar**.
   
    ![](media/service-connect-to-azure-audit-logs/creds.png)
6. Insira as credenciais da conta para concluir o processo de entrada.
   
    ![](media/service-connect-to-azure-audit-logs/login.png)
7. O Power BI recuperará seus dados do Log de Auditoria do Azure e criará um relatório e painel prontos para uso. 
   
    ![](media/service-connect-to-azure-audit-logs/dashboard.png)

**E agora?**

* Tente [fazer uma pergunta na caixa de P e R](consumer/end-user-q-and-a.md) na parte superior do dashboard
* [Altere os blocos](service-dashboard-edit-tile.md) no dashboard.
* [Selecione um bloco](consumer/end-user-tiles.md) para abrir o relatório subjacente.
* Enquanto seu conjunto de dados será agendado para ser atualizado diariamente, você pode alterar o agendamento de atualização ou tentar atualizá-lo sob demanda usando **Atualizar Agora**

## <a name="system-requirements"></a>Requisitos de sistema
O pacote de conteúdo de logs de Auditoria do Azure requer acesso aos Logs de Auditoria no portal do Azure. Mais detalhes [aqui](/azure/azure-resource-manager/resource-group-audit/).

<a name="FindingParams"></a>

## <a name="finding-parameters"></a>Localizando parâmetros
Há duas maneiras fáceis de localizar sua ID da Assinatura.

1. De https://portal.azure.com -&gt; Procurar -&gt; Assinaturas -&gt; ID da Assinatura
2. De https://manage.windowsazure.com -&gt; Configurações -&gt; ID da Assinatura

A ID da assinatura será um conjunto longo de números e caracteres, semelhantes ao exemplo da Etapa \#4 acima. 

## <a name="troubleshooting"></a>Solução de problemas
Se você estiver vendo um erro de credenciais ou de tentativa de atualização devido às credenciais inválidas, tente excluir todas as instâncias do pacote de conteúdo dos logs de Auditoria do Azure e reconectar.

## <a name="next-steps"></a>Próximas etapas
[O que é o Power BI?](fundamentals/power-bi-overview.md)  
[Conceitos básicos para designers no serviço do Power BI](service-basic-concepts.md)  

