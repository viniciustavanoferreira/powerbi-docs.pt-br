---
title: Atualizar, excluir e extrair um aplicativo de modelo do Power BI
description: Como atualizar, excluir e extrair um aplicativo de modelo.
author: teddybercovitz
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 06/10/2019
ms.author: tebercov
ms.openlocfilehash: 273734493c761739f9780e6a7fe6e781900723f9
ms.sourcegitcommit: 7d52401f50944feaaa112c84113ee47f606dbf68
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/13/2019
ms.locfileid: "67125868"
---
# <a name="update-delete-and-extract-template-app"></a>Atualizar, excluir e extrair um aplicativo de modelo

Agora que o aplicativo está em produção, você poderá recomeçar na fase de teste, sem interromper o aplicativo em produção.
## <a name="update-your-app"></a>Atualizar o aplicativo


1. No painel **Gerenciamento de versão**, selecione **Criar aplicativo**.
2. Volte ao processo de criação do aplicativo.
3. Depois de definir **Identidade Visual**, **Conteúdo**, **Controle** e **Acesso**, selecione novamente **Criar aplicativo**.
4. Selecione **Fechar** e volte a **Gerenciamento de versão**.

   Você verá que tem duas versões agora: A versão em produção e uma nova versão em teste.

    ![Duas versões de um aplicativo de modelo](media/service-template-apps-update-extract-delete/power-bi-template-app-update.png)

5. Quando estiver pronto para promover o aplicativo à pré-produção para testes adicionais fora do locatário, volte ao painel Release Management e selecione **Promover aplicativo** ao lado de **Teste**.
6. Seu link agora está ativo. Envie-o novamente para o Portal do Cloud Partner (CPP), seguindo as etapas em [atualização de oferta do Aplicativo do Power BI](https://docs.microsoft.com/azure/marketplace/cloud-partner-portal/power-bi/cpp-update-existing-offer).
7. No CPP, é preciso **publicar** sua oferta novamente e validá-la mais uma vez.

>[!NOTE]
>Promova seu aplicativo para o estágio de produção somente depois que seu aplicativo for aprovado pelo Portal do Cloud Partner e você o publicar.

## <a name="extract-workspace"></a>Extrair workspace
Reverter para a versão anterior de um aplicativo de modelo agora é mais fácil do que nunca com o recurso de extração. As etapas a seguir irão extrair uma versão de aplicativo específica de vários estágios de liberação em um novo workspace:

1. No painel de gerenciamento de versão, pressione mais **(...)** e, em seguida, **Extrair**.

    ![extrair a versão do aplicativo de modelo](media/service-template-apps-update-extract-delete/power-bi-template-app-extract.png) ![extrair a versão do aplicativo de modelo](media/service-template-apps-update-extract-delete/power-bi-template-app-extract-dialog.png)
2. Na caixa de diálogo, insira o nome para o workspace extraído. um novo workspace será adicionado.

A versão do workspace é redefinida e você pode continuar a desenvolver e distribuir o aplicativo de modelo a partir do workspace recém-extraído.

## <a name="delete-template-app-version"></a>Excluir a versão do aplicativo de modelo
Um workspace de aplicativo de modelo é a origem de um aplicativo de modelo distribuído ativo. Para proteger os usuários do aplicativo de modelo, não é possível excluir um workspace sem primeiro remover todas as versões do aplicativo criadas no workspace.
A exclusão de uma versão do aplicativo também exclui a url do aplicativo, que não funcionará mais.

1. No painel de gerenciamento de versão, selecione as reticências **(...)**  e, em seguida, **Excluir**.
 ![Excluir a versão do aplicativo de modelo](media/service-template-apps-update-extract-delete/power-bi-template-app-delete.png)
 ![Excluir a versão do aplicativo de modelo](media/service-template-apps-update-extract-delete/power-bi-template-app-delete-dialog.png)

>[!NOTE]
>Certifique-se de não excluir a versão do aplicativo que está sendo usada pelos clientes ou **AppSource** ou ela deixará de funcionar.

## <a name="next-steps"></a>Próximas etapas

Veja como os clientes interagem com o aplicativo de modelo em [Instalar, personalizar e distribuir aplicativos de modelo em sua organização](service-template-apps-install-distribute.md).

Confira a [oferta do Aplicativo do Power BI](https://docs.microsoft.com/azure/marketplace/cloud-partner-portal/power-bi/cpp-power-bi-offer) para obter mais detalhes sobre como distribuir o aplicativo.
