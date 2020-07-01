---
title: 'Tutorial: definir alertas de dados nos dashboards do serviço do Power BI'
description: Neste tutorial, você aprenderá como definir alertas para notificar quando os dados nos dashboards forem alterados além dos limites definidos por você no serviço do Microsoft Power BI.
author: mihart
ms.reviewer: ''
featuredvideoid: removed
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: how-to
ms.date: 04/18/2020
ms.author: mihart
LocalizationGroup: Dashboards
ms.openlocfilehash: 15efacda18980c4e79d91f291e1714eec69fef59
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85221409"
---
# <a name="tutorial-set-alerts-on-power-bi-dashboards"></a>Tutorial: definir alertas nos dashboards do Power BI

[!INCLUDE[consumer-appliesto-ynnn](../includes/consumer-appliesto-ynnn.md)]

[!INCLUDE [power-bi-service-new-look-include](../includes/power-bi-service-new-look-include.md)]

Defina alertas para receber notificações quando os dados nos dashboards forem alterados além ou aquém dos limites definidos por você. Os alertas só podem ser definidos em blocos fixos de visuais de relatório e apenas em medidores, KPIs e cartões. 

Os *consumidores* podem adicionar alertas aos blocos nos dashboards que eles criaram no **Meu workspace**. Os *consumidores* também podem adicionar alertas aos blocos em dashboards que foram compartilhados com eles em uma [capacidade Premium](end-user-license.md). Se você tiver uma licença do Power BI Pro, também poderá definir alertas sobre blocos em qualquer outro workspace.
Este recurso ainda está em evolução, portanto, confira a [seção abaixo: Dicas e solução de problemas](#tips-and-troubleshooting).

![bloco, cartão, KPI](media/end-user-alerts/card-gauge-kpi.png)

Apenas você poderá ver os alertas que definir, mesmo se compartilhar seu dashboard. Os alertas de dados são totalmente sincronizados nas plataformas; defina e exiba alertas de dados [nos aplicativos móveis do Power BI](mobile/mobile-set-data-alerts-in-the-mobile-apps.md) e no serviço do Power BI. 

> [!WARNING]
> Esses alertas fornecem informações sobre seus dados. Se você exibir os dados do Power BI em um dispositivo móvel e esse dispositivo for roubado, será recomendável usar o serviço do Power BI para desligar todos os alertas.
> 

Este tutorial aborda o seguinte.
> [!div class="checklist"]
> * Quem pode definir alertas
> * Quais visuais são compatíveis com alertas
> * Quem pode ver meus alertas
> * Se os alertas funcionam no Power BI Desktop e Mobile
> * Como criar um alerta
> * Onde os alertas serão recebidos

Se você não estiver inscrito no Power BI, [inscreva-se para uma avaliação gratuita](https://app.powerbi.com/signupredirect?pbi_source=web) antes de começar.

Este exemplo usa um bloco de cartão do dashboard do aplicativo de exemplo Vendas e Marketing. Este aplicativo está disponível no [Microsoft AppSource](https://appsource.microsoft.com). Para ajuda ao obter o aplicativo, confira [Instalar e usar aplicativos de Vendas e Marketing](end-user-app-marketing.md).

1. Em um medidor, KPI ou bloco de cartão do dashboard, selecione as reticências.
   
   ![bloco de cartão](media/end-user-alerts/power-bi-cards.png)
2. Selecione o ícone de sino ![ícone de Alerta](media/end-user-alerts/power-bi-bell-icon.png) ou **Gerenciar alertas** para adicionar um ou mais alertas para **% de unidades de participação no mercado**.

   ![bloco de cartão com reticências selecionadas](media/end-user-alerts/power-bi-ellipses.png)

   
1. No painel **Gerenciar alertas**, selecione **+ Adicionar regra de alerta**.  Verifique se o controle deslizante está definido como **Ligado** e dê um título ao seu alerta. Os títulos ajudam a reconhecer facilmente seus alertas.
   
   ![Janela Gerenciar alertas](media/end-user-alerts/power-bi-manage-alert.png)
4. Role para baixo e insira os detalhes do alerta.  Neste exemplo, criaremos um alerta que notificará uma vez por dia caso a participação de mercado aumente ou ultrapasse 35. Os alertas serão exibidos em nossa Central de Notificações. Além disso, o Power BI vai nos enviar um email.
   
   ![Janela Gerenciar alertas, definir Limite](media/end-user-alerts/power-bi-manage-alert-details.png)
5. Selecione **Salvar e fechar**.
 
   > [!NOTE]
   > Os alertas funcionam somente em dados que estão atualizados. Depois que os dados são atualizados, o Power BI verifica se foi definido um alerta para esses dados. Se os dados atingirem um limite de alerta, um alerta será disparado. 
   > 

## <a name="receiving-alerts"></a>Recebendo alertas
Quando os dados que estão sendo controlados atingem um dos limites que você definiu, várias coisas acontecerão. Primeiro, o Power BI verifica se passou mais de uma hora ou mais de 24 horas (dependendo da opção selecionada) desde o envio do último alerta. Enquanto os dados estiverem acima do limite, você receberá um alerta.

Em seguida, o Power BI enviará um alerta para o centro de notificações e, como opção, para o email. Cada alerta contém um link direto com seus dados. Selecione o link para ver o bloco relevante.  

1. Se tiver definido que o alerta deve lhe enviar um email, você verá algo parecido com isto na Caixa de Entrada. Esse é um alerta que definimos em um dashboard diferente, esse dashboard controla as tarefas concluídas pela equipe de Usabilidade.
   
   ![Email de alerta](media/end-user-alerts/power-bi-alert-email.png)
2. O Power BI adiciona uma mensagem à sua **Central de Notificações** e adiciona um novo ícone de alerta no bloco aplicável.
   
   ![Ícone de notificação no serviço do Power BI](media/end-user-alerts/power-bi-task-alert.png)
3. Abra a Central de Notificações para ver os detalhes do alerta.
   
    ![ler o alerta](media/end-user-alerts/power-bi-notification.png)
   
  

## <a name="managing-alerts"></a>Gerenciando alertas

Há várias maneiras de gerenciar seus alertas: No próprio bloco do dashboard, no menu Configurações do Power BI, em um bloco individual no [aplicativo móvel do Power BI no iPhone](mobile/mobile-set-data-alerts-in-the-mobile-apps.md) ou no [aplicativo móvel do Power BI para Windows 10](mobile/mobile-set-data-alerts-in-the-mobile-apps.md).

### <a name="from-the-tile-itself"></a>No próprio bloco

1. Se você precisar alterar ou remover um alerta para um bloco, abra novamente a janela **Gerenciar alertas** selecionando o ícone de sino ![ícone de Alerta](media/end-user-alerts/power-bi-bell-icon.png). Todos os alertas definidos para esse bloco são exibidos.
   
    ![Janela Gerenciar alertas](media/end-user-alerts/power-bi-manage-alerts.png).
2. Para modificar um alerta, selecione a seta à esquerda do nome do alerta.
   
    ![seta ao lado do nome do alerta](media/end-user-alerts/power-bi-modify-alert.png).
3. Para excluir um alerta, selecione a lixeira à direita do nome do alerta.
   
      ![ícone de lixeira selecionado](media/end-user-alerts/power-bi-alert-delete.png)

### <a name="from-the-power-bi-settings-menu"></a>No menu de configurações do Power BI

1. Selecione o ícone de engrenagem na barra de menus do Power BI.
   
    ![ícone de engrenagem](media/end-user-alerts/powerbi-gear-icon.png).
2. Em **Configurações**, selecione **Alertas**.
   
    ![Guia Alertas da janela Configurações](media/end-user-alerts/power-bi-alert-settings.png)
3. Aqui, é possível ativar e desativar alertas, abrir a janela **Gerenciar alertas** para fazer alterações ou excluir o alerta.

## <a name="tips-and-troubleshooting"></a>Dicas e solução de problemas 

* Se não for possível definir um alerta para um medidor, KPI ou cartão, fale com o administrador dos locatários para obter ajuda. Às vezes, os alertas são desativados ou ficam indisponíveis para o dashboard ou para tipos específicos de blocos de dashboard.
* Os alertas funcionam somente em dados que estão atualizados. Eles não funcionam em dados estáticos. A maioria dos exemplos fornecidos pela Microsoft são estáticos. 
* A capacidade de receber e exibir conteúdo compartilhado requer uma licença Power BI Pro ou Premium. Para obter mais informações, leia [Qual licença tenho?](end-user-license.md).
* Os alertas podem ser definidos em visuais criados com base em conjuntos de dados de streaming que estão fixados de um relatório em um dashboard. Os alertas não podem ser definidos em blocos de streaming criados diretamente no dashboard usando **Adicionar bloco** > **Dados de streaming personalizados**.


## <a name="clean-up-resources"></a>Limpar recursos
Instruções para excluir alertas são explicadas acima. Resumindo, selecione o ícone de engrenagem na barra de menus do Power BI. Em **Configurações**, selecione **Alertas** e exclua o alerta.

> [!div class="nextstepaction"]
> [Definir alertas de dados no seu dispositivo móvel](mobile/mobile-set-data-alerts-in-the-mobile-apps.md)


