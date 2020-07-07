---
title: Restringir o acesso a dados com a RLS (Segurança em Nível de Linha) no Power BI Desktop
description: Como configurar a segurança em nível de linha de conjuntos de dados importados e o DirectQuery no Power BI Desktop.
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: how-to
ms.custom: ''
ms.date: 01/31/2020
LocalizationGroup: Create reports
ms.openlocfilehash: 9036967c826dee83847c3bc3d4a903bbe749b2ce
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.contentlocale: pt-BR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85238641"
---
# <a name="restrict-data-access-with-row-level-security-rls-for-power-bi-desktop"></a>Restringir o acesso a dados com a RLS (Segurança em Nível de Linha) no Power BI Desktop

Você pode usar a RLS (segurança em nível de linha) com o Power BI Desktop pode ser usada para restringir o acesso a dados para determinados usuários. Os filtros restringem os dados no nível da linha. É possível definir filtros nas funções.

Agora é possível configurar a RLS de modelos de dados importados para o Power BI com o Power BI Desktop. Você também pode configurar RLS em conjuntos de dados que estão usando [DirectQuery](../connect-data/desktop-use-directquery.md), assim como o SQL Server. Anteriormente, você conseguia apenas implementar a RLS nos modelos do Analysis Services local fora do Power BI. Para as conexões dinâmicas do Analysis Services, configure a Segurança em nível de linha no modelo local. A opção de segurança não é exibida para conjuntos de dados com conexão dinâmica.

> [!IMPORTANT]
> Se você tiver definido funções e regras no serviço do Power BI, será necessário recriar essas funções no Power BI Desktop e publicar o relatório no serviço. Saiba mais sobre as opções da [RLS no serviço do Power BI](../admin/service-admin-rls.md).

[!INCLUDE [include-short-name](../includes/rls-desktop-define-roles.md)]

[!INCLUDE [include-short-name](../includes/rls-desktop-view-as-roles.md)]

[!INCLUDE [include-short-name](../includes/rls-limitations.md)]

[!INCLUDE [include-short-name](../includes/rls-faq.md)]

## <a name="next-steps"></a>Próximas etapas

Para obter mais informações relacionadas a este artigo, confira os seguintes recursos:

- [Segurança no nível da linha (RLS) com Power BI](../admin/service-admin-rls.md)
- [Diretrizes de RLS (Segurança em Nível de Linha) no Power BI Desktop](../guidance/rls-guidance.md)
- Dúvidas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
- Sugestões? [Contribuir com ideias para aprimorar o Power BI](https://ideas.powerbi.com/)
