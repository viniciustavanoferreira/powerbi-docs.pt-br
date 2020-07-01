---
title: Conectar a Microsoft Sustainability Calculator
description: Microsoft Sustainability Calculator para Power BI
author: joshthor3222
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: how-to
ms.date: 01/06/2020
ms.author: v-tikid
LocalizationGroup: Connect to services
ms.openlocfilehash: cffb7ecc195f5ce803ec2dfc81c794bac75c9448
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85230027"
---
# <a name="connect-the-microsoft-sustainability-calculator"></a>Conectar a Microsoft Sustainability Calculator
Obter insights sobre as emissões de carbono da sua infraestrutura de TI para tomar decisões de computação mais sustentáveis

A Microsoft Sustainability Calculator fornece novos insights sobre os dados de emissões de carbono associados aos serviços do Azure. Os responsáveis por reportar e impulsionar a sustentabilidade em suas organizações agora podem quantificar o impacto de cada assinatura do Azure, bem como ver a economia de carbono estimada ao executar essas cargas de trabalho no Azure em relação aos datacenters locais. Esses dados podem ser usados para relatórios de gases de efeito estufa das emissões de escopo 3. O acesso à Microsoft Sustainability Calculator exigirá sua ID de locatário e a chave de acesso, normalmente disponíveis por meio do administrador do Azure da sua organização.

Para usar esse aplicativo, você precisará de informações do Azure Enterprise Portal. Os administradores do sistema da sua empresa podem ajudá-lo a obter essas informações. Leia essas instruções e obtenha as informações necessárias antes de instalar o aplicativo. 

Essa versão do conector é compatível apenas com registros empresariais de [https://ea.azure.com](https://ea.azure.com/). Atualmente, não há suporte para registros da China.

## <a name="how-to-connect"></a>Como se conectar
[!INCLUDE [powerbi-service-apps-get-more-apps](../includes/powerbi-service-apps-get-more-apps.md)]

1. Selecione **Microsoft Sustainability Calculator** \> **Obter agora**.
1. Em **Instalar este aplicativo do Power BI?** selecione **Instalar**.
1. No painel **Aplicativos**, selecione o bloco **Microsoft Sustainability Calculator**.
1. Em **Introdução a seu novo aplicativo**, selecione **Conectar**.

    ![Introdução ao novo aplicativo](media/service-connect-to-zendesk/power-bi-new-app-connect-get-started.png)

1. Insira o **Nome da empresa, o número de registro do usuário** e **Número de meses \> Entrar**. Veja detalhes sobre [como encontrar esses parâmetros](#finding-parameters) abaixo.

    ![Registro da empresa](media/service-connect-to-microsoft-sustainability-calculator/company-enrollment.png)

1. No **Método de autenticação**, selecione **Chave** e, para **Nível de privacidade**, selecione **Organizacional**.
1. Para **Chave**, insira sua **Chave de acesso \> Entrar**.

    ![Entrada de Chave de Acesso](media/service-connect-to-microsoft-sustainability-calculator/access-key-entry.png)

1. O processo de importação é iniciado automaticamente. Quando concluído, um dashboard, um relatório e um modelo novos aparecerão no **Painel de Navegação**. Selecione o relatório para exibir os dados importados por você.

## <a name="finding-parameters"></a>Localizando parâmetros

Para localizar a **ID de registro** e a **Chave de acesso** da sua empresa, trabalhe com o administrador do Azure para obter as informações necessárias. O administrador irá

1. Fazer logon no [Azure Enterprise Portal](https://ea.azure.com), clicar em **Gerenciar** na faixa de opções à esquerda e obter o **Número de Registro**, conforme mostrado abaixo
2. No [Azure Enterprise Portal](https://ea.azure.com), clicar em **Relatórios** e, em seguida, Chave de Acesso da API, conforme mostrado abaixo para obter a Chave da Conta de Registro Principal

## <a name="using-the-app"></a>Usar o aplicativo

Para atualizar os parâmetros a qualquer momento, navegue até as configurações de **Conjunto de dados**, acesse os parâmetros associados ao workspace do aplicativo e atualize a ID do locatário, o nome da empresa ou os meses de dados. Depois de aplicar os parâmetros, clique em **Atualizar** para recarregar os dados com os novos parâmetros aplicados.