---
title: Conectar-se ao QuickBooks Online com o Power BI
description: QuickBooks Online para o Power BI
author: paulinbar
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 05/04/2020
ms.author: painbar
LocalizationGroup: Connect to services
ms.openlocfilehash: 4c21c36694f36e4d6f95b8edc920648313dc8a7a
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83348495"
---
# <a name="connect-to-quickbooks-online-with-power-bi"></a>Conectar-se ao QuickBooks Online com o Power BI
Quando você se conecta aos seus dados do QuickBooks Online por meio do Power BI, você obtém imediatamente um painel e relatórios do Power BI que fornecem informações sobre o fluxo de caixa de sua empresa, rentabilidade, clientes e muito mais. Use o painel e os relatórios como fornecidos, ou então personalize-os para realçar as informações que mais importam a você. Os dados são atualizados automaticamente uma vez por dia.

Conecte-se ao [aplicativo de modelo do QuickBooks Online](https://dxt.powerbi.com/getdata/services/quickbooks-online) para o Power BI.

>[!NOTE]
>Para importar seus dados do QuickBooks Online no Power BI, você precisa ser um administrador em sua conta do QuickBooks Online e entrar com suas credenciais da conta de administrador. Você não pode usar esse conector com o software QuickBooks Desktop. 

## <a name="how-to-connect"></a>Como se conectar

[!INCLUDE [powerbi-service-apps-get-more-apps](../includes/powerbi-service-apps-get-more-apps.md)]

3. Selecione **QuickBooks Online**e **Obter**.
   
   ![Obter o QuickBooks](media/service-connect-to-quickbooks-online/qbo.png)

4. Em **Instalar este aplicativo do Power BI?** , selecione **Instalar**.

    ![Instalar o QuickBooks](media/service-connect-to-quickbooks-online/power-bi-install-quickbooks.png)

4. No painel **Aplicativos**, selecione o bloco **QuickBooks**.

   ![Selecionar o bloco QuickBooks](media/service-connect-to-quickbooks-online/power-bi-quickbooks-tile.png)

6. Em **Introdução a seu novo aplicativo**, selecione **Conectar**.

    ![Introdução ao novo aplicativo](media/service-connect-to-zendesk/power-bi-new-app-connect-get-started.png)

4. Selecione **oAuth2** como o Método de Autenticação e selecione **Entrar**. 
5. Quando solicitado, insira suas credenciais do QuickBooks Online e siga o processo de autenticação do QuickBooks Online. Se você já tiver entrado no QuickBooks Online em seu navegador, talvez suas credenciais não sejam solicitadas.
   >[!NOTE]
   >Você precisa ter credenciais de administrador para a conta do QuickBooks Online.
6. Selecione a empresa que você deseja conectar ao Power BI na próxima tela.
   
   ![Quase pronto no QuickBooks](media/service-connect-to-quickbooks-online/pbi_qbo_almost.png)

7. Selecione **Autorizar** na próxima tela para iniciar o processo de importação. O processo pode levar alguns minutos, dependendo do tamanho dos dados de sua empresa. 
   
   ![Autorizar o QuickBooks](media/service-connect-to-quickbooks-online/pbi_qbo_authorizesm.png)
   
8. Após o Power BI importar os dados, você verá a lista de conteúdo do seu aplicativo QuickBooks: um novo dashboard, relatório e conjunto de dados.
9. Selecione o dashboard do QuickBooks para iniciar o processo de exploração. O Power BI criou esse dashboard automaticamente para exibir os dados importados.

    ![Dashboard do QuickBooks](media/service-connect-to-quickbooks-online/power-bi-connect-quickbooks-sample.png)

**E agora?**

* Tente [fazer uma pergunta na caixa de P e R](../consumer/end-user-q-and-a.md) na parte superior do dashboard
* [Altere os blocos](../create-reports/service-dashboard-edit-tile.md) no dashboard.
* [Selecione um bloco](../consumer/end-user-tiles.md) para abrir o relatório subjacente.
* Enquanto seu conjunto de dados será agendado para ser atualizado diariamente, você pode alterar o agendamento de atualização ou tentar atualizá-lo sob demanda usando **Atualizar Agora**

## <a name="troubleshooting"></a>Solução de problemas
**"Opa! Ocorreu um erro.”**

Se você receber essa mensagem depois de selecionar **Autorizar**:

“Ops! Ocorreu um erro.” Feche esta janela e tente novamente.

O aplicativo já foi assinado para esta empresa por outro usuário. Entre em contato com [email do administrador] para fazer alterações nesta assinatura."

![Ops! Ocorreu um erro](media/service-connect-to-quickbooks-online/pbi_qbo_oopssm.png)

... esse erro significa que outro administrador em sua empresa já se conectou aos dados da empresa com o Power BI. Peça ao admin que compartilhe o painel com você. Atualmente, apenas um usuário administrador pode se conectar a um determinado conjunto de dados corporativos do QuickBooks Online para o Power BI. Depois que o Power BI cria o dashboard, o administrador pode compartilhá-lo com vários colegas no mesmos locatários do Power BI.

**"Este aplicativo não está configurado para permitir conexões por meio de seu país"**

Atualmente o Power BI só dá suporte às edições estadunidenses do QuickBooks Online. 

![Este aplicativo não está configurado para permitir conexões por meio de seu país](media/service-connect-to-quickbooks-online/pbi_qbo_countrynotsupported.png)

## <a name="next-steps"></a>Próximas etapas
[O que é o Power BI?](../fundamentals/power-bi-overview.md)

[Conceitos básicos para designers no serviço do Power BI](../fundamentals/service-basic-concepts.md)
