---
title: Visão geral da entidade de serviço
description: Visão geral da entidade de serviço
services: powerbi
author: KesemSharabi
ms.author: kesharab
ms.topic: include
ms.date: 04/05/2020
ms.custom: include file
ms.openlocfilehash: 7fc4412a66602fe3a6548c3e1afb06de788da90d
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82616087"
---
A entidade de serviço é um método de autenticação que pode ser usado para permitir que o aplicativo Azure AD acesse o conteúdo e as APIs do serviço do Power BI.

Quando você cria um aplicativo do Azure AD (Azure Active Directory), é criado um [objeto da entidade de serviço](https://docs.microsoft.com/azure/active-directory/develop/app-objects-and-service-principals#service-principal-object). O objeto da entidade de serviço, também conhecida simplesmente como *entidade de serviço*, permite que o Azure AD autentique seu aplicativo. Quando estiver autenticado, o aplicativo poderá acessar os recursos de locatário do Azure AD.

Para fazer a autenticação, a entidade de serviço usa a *ID do Aplicativo* no Azure AD e uma das opções a seguir:
* Segredo do aplicativo
* Certificado