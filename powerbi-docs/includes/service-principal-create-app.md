---
title: Aplicativo de criação de entidade de serviço
description: Aplicativo de criação de entidade de serviço
services: powerbi
author: KesemSharabi
ms.author: kesharab
ms.topic: include
ms.date: 05/20/2020
ms.custom: include file
ms.openlocfilehash: 0fe3e1743cb8853d6626b59b748d70bfcc292dbd
ms.sourcegitcommit: cd64ddd3a6888253dca3b2e3fe24ed8bb9b66bc6
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/03/2020
ms.locfileid: "84315732"
---
1. Entre no [Microsoft Azure](https://ms.portal.azure.com/#allservices).

2. Pesquise **Registros de aplicativo** e clique no link **Registros de aplicativo**.

    ![registro de aplicativo do azure](media/embedded-service-principal/azure-app-registration.png)

3. Clique em **Novo registro**.

    ![novo registro](media/embedded-service-principal/new-registration.png)

4. Preencha as informações obrigatórias:
    * **Nome** – digite um nome para seu aplicativo
    * **Tipos de conta com suporte** – selecione os tipos de conta com suporte
    * (Opcional) **URI de redirecionamento** – insira um URI, se necessário

5. Clique em **Registrar**.

6. Após o registro, a *ID do Aplicativo* estará disponível na guia **Visão geral**. Copie e salve a *ID do Aplicativo* para uso posterior.

    ![id do aplicativo](media/embedded-service-principal/application-id.png)