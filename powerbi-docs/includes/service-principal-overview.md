---
ms.openlocfilehash: 26f4b82301915524b65d9d2d6b39d61b54ed0321
ms.sourcegitcommit: 8eeb784fd46321680367ac913ef976aeedaa7766
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/03/2020
ms.locfileid: "80621599"
---
A entidade de serviço é um método de autenticação que pode ser usado para permitir que o aplicativo Azure AD acesse o conteúdo e as APIs do serviço do Power BI.

Quando você cria um aplicativo do Azure AD (Azure Active Directory), é criado um [objeto da entidade de serviço](https://docs.microsoft.com/azure/active-directory/develop/app-objects-and-service-principals#service-principal-object). O objeto da entidade de serviço, também conhecida simplesmente como *entidade de serviço*, permite que o Azure AD autentique seu aplicativo. Quando estiver autenticado, o aplicativo poderá acessar os recursos de locatário do Azure AD.

Para fazer a autenticação, a entidade de serviço usa a *ID do Aplicativo* no Azure AD e uma das opções a seguir:
* Segredo do aplicativo
* Certificado