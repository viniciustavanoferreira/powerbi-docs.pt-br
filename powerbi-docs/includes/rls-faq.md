---
ms.openlocfilehash: 0592cb7ef076f8094aca565d955cc238b2181068
ms.sourcegitcommit: f6ac9e25760561f49d4257a6335ca0f54ad2d22e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/16/2019
ms.locfileid: "69560965"
---
## <a name="faq"></a>PERGUNTAS FREQUENTES
**Pergunta:** E se eu já tiver criado funções e regras para um conjunto de dados no serviço do Power BI? Elas ainda funcionariam se eu não fizesse nada?  
**Resposta:** Não, os visuais não seriam renderizados corretamente. Você precisará recriar as funções e regras no Power BI Desktop e, em seguida, publicá-las no serviço do Power BI.

**Pergunta:** Posso criar essas funções para fontes de dados do Analysis Services?  
**Resposta:** Sim, isso é possível se você importou os dados no Power BI Desktop. Se você estiver usando uma conexão dinâmica, não poderá configurar a RLS no serviço do Power BI. Isso é definido no modelo local do Analysis Services.

**Pergunta:** Posso usar a RLS para limitar as colunas ou as medidas acessíveis por meus usuários?  
**Resposta:** Não, se um usuário tiver acesso a uma linha específica de dados, ele poderá ver todas as colunas de dados dessa linha.

**Pergunta:** A RLS permite ocultar dados detalhados, mas conceder acesso aos dados resumidos nos visuais?  
**Resposta:** Não. Você protege linhas individuais de dados, mas os usuários sempre podem ver os detalhes ou os dados resumidos.

