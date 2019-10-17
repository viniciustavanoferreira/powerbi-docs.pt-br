---
title: Conectar-se ao Microsoft Azure Consumption Insights com o Power BI
description: Microsoft Azure Consumption Insights para o Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggies
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 09/25/2019
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: e51f936e44e8c8ee3442aedfb2389675774c0a47
ms.sourcegitcommit: 5e277dae93832d10033defb2a9e85ecaa8ffb8ec
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72020422"
---
# <a name="connect-to-microsoft-azure-consumption-insights-with-power-bi"></a>Conectar-se ao Microsoft Azure Consumption Insights com o Power BI
Explore e monitore seus dados de consumo do Microsoft Azure no serviço do Power BI com o pacote de conteúdo do Power BI. Os dados são atualizados automaticamente uma vez por dia.

Conecte-se ao [Pacote de conteúdo do Microsoft Azure Consumption Insights](https://app.powerbi.com/getdata/services/azureconsumption) para o serviço do Power BI.

> [!NOTE]
> Para uma configuração mais personalizada, experimente usar o [conector do Azure Consumption Insights](desktop-connect-azure-consumption-insights.md) no Power BI Desktop.

## <a name="how-to-connect"></a>Como se conectar
1. No serviço do Power BI, selecione **Obter Dados** na parte inferior do painel de navegação esquerdo.
   
    ![Obter Dados](media/service-connect-to-azure-consumption-insights/getdata.png)
2. Na caixa **Serviços** , selecione **Obter**.
   
   ![Obter serviços](media/service-connect-to-azure-consumption-insights/services.png)
3. Selecione **Microsoft Azure Consumption Insights** \> **Obter agora**. 
   
   ![Obter agora](media/service-connect-to-azure-consumption-insights/mazureconsumption.png)
4. Forneça o número de meses de dados que deseja importar e seu número de registro do Azure Enterprise. Veja detalhes sobre [como encontrar esses parâmetros](#FindingParams) abaixo.
   
    ![Conectar-se ao Microsoft Azure Consumption Insights](media/service-connect-to-azure-consumption-insights/azureconsumptionparams.png)
5. Forneça sua Chave de acesso para se conectar. Você pode encontrar sua chave de registro no Portal do Azure EA. 
   
    ![Microsoft Azure Consumption Insights: chave](media/service-connect-to-azure-consumption-insights/msazureconsumptioncreds.png)
6. O processo de importação é iniciado automaticamente. Quando concluído, um painel, um relatório e um modelo novos aparecerão no Painel de Navegação. Selecione o painel para exibir os dados importados por você.
   
   ![Painel do Microsoft Azure Consumption Insights](media/service-connect-to-azure-consumption-insights/msazureconsumptiondashboard.png)

**E agora?**

* Tente [fazer uma pergunta na caixa de P e R](consumer/end-user-q-and-a.md) na parte superior do dashboard
* [Altere os blocos](service-dashboard-edit-tile.md) no dashboard.
* [Selecione um bloco](consumer/end-user-tiles.md) para abrir o relatório subjacente.
* Enquanto seu conjunto de dados está agendado para ser atualizado diariamente, você pode alterar o agendamento de atualização ou tentar atualizá-lo sob demanda usando **Atualizar Agora**

## <a name="whats-included"></a>O que está incluído
O pacote de conteúdo do Microsoft Azure Consumption Insights inclui dados de relatórios mensais para o intervalo de meses fornecido durante a conexão. O intervalo é uma janela móvel, portanto, as datas inclusas são atualizadas à medida que o conjunto de dados é atualizado.

## <a name="system-requirements"></a>Requisitos do sistema
O pacote de conteúdo exige acesso aos recursos do Enterprise no portal do Azure. 

<a name="FindingParams"></a>

## <a name="finding-parameters"></a>Localizando parâmetros
Os relatórios do Power BI estão disponíveis para EA Direto, Parceiros e Clientes Indiretos que podem exibir informações de cobrança. Leia abaixo para obter detalhes sobre a localização de cada um dos valores esperados pelo fluxo de conexão.

**Número de meses**

* O número de meses (1 a 36) dos dados, em relação a hoje, que você deseja importar.

**Número de registro**

* O número de registro do Azure Enterprise, que pode ser encontrado na tela inicial do [Azure Enterprise Portal](https://ea.azure.com/) em **Detalhes do Registro**.
  
    ![Número de registro](media/service-connect-to-azure-consumption-insights/params2.png)

**Tecla de acesso**

* Encontre sua chave de acesso no portal do Azure Enterprise, em **Baixar Uso** > **Chave de Acesso de API**.
  
    ![Chave de Acesso](media/service-connect-to-azure-consumption-insights/creds2.png)

**Ajuda adicional**

* Para obter ajuda adicional para configurar o Pacote Power BI do Azure Enterprise, acesse o Portal do Azure Enterprise e visualize o Arquivo de Ajuda da API em **Ajuda**. Veja também instruções adicionais em **Relatórios** -> **Baixar Uso** -> **Chave de Acesso da API**.
* Para uma configuração mais personalizada, experimente usar o [conector do Azure Consumption Insights](desktop-connect-azure-consumption-insights.md) no Power BI Desktop.

## <a name="next-steps"></a>Próximas etapas

[Conector do Azure Consumption Insights](desktop-connect-azure-consumption-insights.md) no Power BI Desktop

[Obter dados no Power BI](service-get-data.md)

