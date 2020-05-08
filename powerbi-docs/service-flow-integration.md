---
title: Integração do Power BI com o Power Automate
description: Aprenda a criar fluxos do Power Automate disparados por alertas de dados do Power BI.
author: maggiesMSFT
ms.reviewer: ''
featuredvideoid: YhmNstC39Mw
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 02/25/2020
ms.author: maggies
LocalizationGroup: Get started
ms.openlocfilehash: aafba825c5bd4ece3c8b97256d5943f91b456cd7
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/05/2020
ms.locfileid: "77609699"
---
# <a name="power-automate-and-power-bi"></a>Power Automate e Power BI

O [Power Automate](https://docs.microsoft.com/power-automate/getting-started) é uma oferta de SaaS para automatizar os fluxos de trabalho entre o número crescente de serviços SaaS e aplicativos dos quais os usuários empresariais dependem. Com o Power Automate, é possível automatizar tarefas integrando seus aplicativos e serviços favoritos (incluindo o Power BI) para obter notificações, sincronizar arquivos, coletar dados e muito mais. Tarefas repetitivas se tornam fácil com a automação do fluxo de trabalho.

[Comece agora mesmo a usar o Power Automate.](https://docs.microsoft.com/power-automate/getting-started)

Assista a Sirui criar um fluxo do Power Automate que envia um email detalhado para colegas quando um alerta do Power BI é disparado. Em seguida, siga as instruções passo a passo abaixo do vídeo para testá-la por conta própria.

<iframe width="560" height="315" src="https://www.youtube.com/embed/YhmNstC39Mw" frameborder="0" allowfullscreen></iframe>

## <a name="create-a-flow-that-is-triggered-by-a-power-bi-data-alert"></a>Criar um fluxo disparado por um alerta de dados do Power BI

### <a name="prerequisites"></a>Pré-requisitos
Este tutorial mostra como criar dois fluxos diferentes; um de um modelo e um do zero. Para acompanhar, [crie um alerta de dados no Power BI](service-set-data-alerts.md), crie uma conta gratuita no Slack e [inscreva-se no Power Automate](https://flow.microsoft.com/#home-signup) (é gratuito!).

## <a name="create-a-flow-that-uses-power-bi---from-a-template"></a>Criar um fluxo que usa Power BI de um modelo
Nesta tarefa, usamos um modelo para criar um fluxo simples que é disparado por um alerta de dados (notificação) do Power BI.

1. Entre no Power Automate (flow.microsoft.com).
2. Selecione **Meus fluxos**.
   
   ![Barra de menus do Power Automate](media/service-flow-integration/power-bi-my-flows.png)
3. Selecione **Criar do modelo**.
   
    ![Barra de menus Meus fluxos](media/service-flow-integration/power-bi-template.png)
4. Use a caixa Pesquisar para localizar modelos do Power BI e selecione **Enviar um email para qualquer público quando um alerta de dados do Power BI for disparado > Continuar**.
   
    ![resultados da pesquisa](media/service-flow-integration/power-bi-flow-alert.png)


### <a name="build-the-flow"></a>Criar o fluxo
Este modelo tem um gatilho (alerta de dados do Power BI para novas medalhas olímpicas para Irlanda) e uma ação (enviar um email). Conforme você seleciona um campo, o Power Automate exibe o conteúdo dinâmico que pode ser incluído.  Neste exemplo, incluímos o valor e a URL do bloco no corpo da mensagem.

![modelo de fluxo](media/service-flow-integration/power-bi-template1.png)

1. No menu suspenso do gatilho, selecione um alerta de dados do Power BI. Selecione **Nova medalha para a Irlanda**. Para saber como criar um alerta, consulte [Alertas de dados no Power BI](service-set-data-alerts.md).
   
   ![lista suspensa de alertas](media/service-flow-integration/power-bi-trigger-flow.png)
2. Insira um ou mais endereços de email válido e, em seguida, selecione **Editar** (mostrado abaixo) ou **Adicionar conteúdo dinâmico**. 
   
   ![Tela Enviar um email](media/service-flow-integration/power-bi-flow-email.png)

3. O Power Automate cria um título e uma mensagem que você pode manter ou modificar. Todos os valores que você definiu quando criou o alerta no Power BI estão disponíveis para uso: basta colocar o cursor e selecionar na área cinza realçada. 

   ![Tela Enviar um email](media/service-flow-integration/power-bi-flow-email-default.png)

1.  Por exemplo, se você tiver criado um título do alerta no Power BI dizendo **Ganhamos outra medalha**, poderá selecionar **Título do alerta** para adicionar esse texto ao campo Assunto do email.

    ![criar o texto do email](media/service-flow-integration/power-bi-flow-message.png)

    E você pode aceitar o corpo do email padrão ou criar seu próprio. O exemplo acima contém algumas modificações na mensagem.

1. Ao terminar, selecione **Criar fluxo** ou **Salvar fluxo**.  O fluxo é criado e avaliado.  O Power Automate avisará se encontrar erros.
2. Se forem encontrados erros, selecione **Editar fluxo** para corrigi-los, caso contrário, selecione **Feito** para executar o novo fluxo.
   
   ![mensagem de êxito](media/service-flow-integration/power-bi-flow-running.png)
5. Quando o alerta de dados for disparado, um email será enviado para os endereços que você indicou.  
   
   ![email de alerta](media/service-flow-integration/power-bi-flow-email2.png)

## <a name="create-a-power-automate-that-uses-power-bi---from-scratch-blank"></a>Criar um Power Automate que usa o Power BI a partir do zero (em branco)
Nesta tarefa, criaremos um fluxo simples a partir do zero que é disparado por um alerta de dados (notificação) do Power BI.

1. Entre no Power Automate.
2. Selecione **Meus fluxos** > **Criar em branco**.
   
   ![Barra de menus superior do Power Automate](media/service-flow-integration/power-bi-my-flows.png)
3. Use a caixa Pesquisar para localizar um gatilho do Power BI e selecione **Power BI – quando um alerta orientado a dados for disparado**.

### <a name="build-your-flow"></a>Criar seu fluxo
1. No menu suspenso, selecione o nome do alerta.  Para saber como criar um alerta, consulte [Alertas de dados no Power BI](service-set-data-alerts.md).
   
    ![selecionar o nome do alerta](media/service-flow-integration/power-bi-totalstores2.png)
2. Selecione **Nova etapa** > **Adicionar uma ação**.
   
   ![adicionar uma nova etapa](media/service-flow-integration/power-bi-new-step.png)
3. Pesquise por **Outlook** e selecione **Criar evento**.
   
   ![criar o fluxo](media/service-flow-integration/power-bi-create-event.png)
4. Preencha os campos no evento. Conforme você seleciona um campo, o Power Automate exibe o conteúdo dinâmico que pode ser incluído.
   
   ![continuar criando o fluxo](media/service-flow-integration/power-bi-flow-event.png)
5. Selecione **Criar fluxo** quando terminar.  O Power Automate salva e avalia o fluxo. Se não houver nenhum erro, selecione **Feito** para executar esse fluxo.  O novo fluxo é adicionado à página **Meus fluxos**.
   
   ![Concluir o fluxo](media/service-flow-integration/power-bi-flow-running.png)
6. Quando o fluxo for disparado pelo alerta de dados do Power BI, você receberá uma notificação de eventos do Outlook semelhante a esta.
   
    ![O Power Automate dispara a notificação do Outlook](media/service-flow-integration/power-bi-flow-notice.png)

## <a name="next-steps"></a>Próximas etapas
* [Introdução ao Power Automate](https://docs.microsoft.com/power-automate/getting-started/)
* [Definir alertas de dados no serviço do Power BI](service-set-data-alerts.md)
* [Definir alertas de dados no seu iPhone](consumer/mobile/mobile-set-data-alerts-in-the-mobile-apps.md)
* [Definir alertas de dados no aplicativo móvel do Power BI para Windows 10](consumer/mobile/mobile-set-data-alerts-in-the-mobile-apps.md)
* Mais perguntas? [Experimente a Comunidade do Power BI](https://community.powerbi.com/)

