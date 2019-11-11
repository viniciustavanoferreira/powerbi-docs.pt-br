---
title: Encontrar usuários do Power BI que entraram
description: Se for um administrador de locatários e quiser ver quem entrou no Power BI, você poderá usar os relatórios de acesso e de uso do Azure Active Directory para ter essa visibilidade.
author: mgblythe
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 09/09/2019
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: 63257953b89a6c96ce451783193656f9dfacf5bd
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/09/2019
ms.locfileid: "73873737"
---
# <a name="find-power-bi-users-that-have-signed-in"></a>Encontrar usuários do Power BI que entraram

Se for um administrador de locatários e quiser ver quem entrou no Power BI, use os [relatórios de acesso e uso do Azure Active Directory](/azure/active-directory/reports-monitoring/concept-sign-ins) para ter essa visibilidade.

> [!NOTE]
> O relatório de **Entradas** fornece informações úteis, mas não identifica o tipo de licença que cada usuário tem. Use o centro de administração do Microsoft 365 para ver as licenças.

## <a name="requirements"></a>Requisitos

Qualquer usuário (inclusive os não administradores) pode ver um relatório de suas próprias entradas, mas você deve atender aos requisitos a seguir para ver um relatório para todos os usuários.

* Seu locatário deve ter uma licença do Azure Active Directory Premium associada a ele.

* Você deve ter uma das seguintes funções: Administrador Global, Administrador de Segurança ou Leitor de Segurança.

## <a name="use-the-azure-portal-to-view-sign-ins"></a>Usar o Portal do Azure para exibir entradas

Para exibir a atividade de entrada, siga estas etapas.

1. No **Portal do Azure**, selecione **Azure Active Directory**.

1. Em **Monitoramento**, selecione **Entradas**.
   
    ![Captura de tela da interface do usuário do Azure com o Azure Active Directory e opções de Entradas realçadas.](media/service-admin-access-usage/azure-portal-sign-ins.png)

1. Filtre o aplicativo segundo **Microsoft Power BI** ou **Power BI Gateway** e selecione **Aplicar**.

    O **Microsoft Power BI** filtra a atividade de conexão relacionada ao serviço, enquanto o **Power BI Gateway** filtra atividades de conexão específicas para o gateway de dados local.
   
    ![Captura de tela do filtro Entradas com o campo Aplicativos realçado.](media/service-admin-access-usage/sign-in-filter.png)

## <a name="export-the-data"></a>Exportar os dados

É possível [baixar um relatório de conexão](/azure/active-directory/reports-monitoring/quickstart-download-sign-in-report) em qualquer um dos dois formatos: um arquivo CSV ou um arquivo JSON.

![Captura de tela do botão de download.](media/service-admin-access-usage/download-sign-in-data-csv.png)

Na parte superior do relatório **Entradas**, selecione **Baixar** e, em seguida, selecione uma das seguintes opções:

* **CSV** para baixar um arquivo CSV dos dados filtrados no momento.

* **JSON** para baixar um arquivo JSON dos dados filtrados no momento.

## <a name="data-retention"></a>Retenção de dados

Dados relacionados às entradas estão disponíveis por até 30 dias. Para obter mais informações, confira [Políticas de retenção de relatórios do Azure Active Directory](/azure/active-directory/reports-monitoring/reference-reports-data-retention).

## <a name="next-steps"></a>Próximas etapas

[Usando a auditoria em sua organização](service-admin-auditing.md)

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)