---
ms.openlocfilehash: cd0696b44e285119193059304c89cfa04c755771
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/05/2020
ms.locfileid: "71409347"
---
## <a name="faq"></a>Perguntas frequentes
**Pergunta:** E se eu já tiver criado funções e regras para um conjunto de dados no serviço do Power BI? Elas ainda funcionariam se eu não fizesse nada?  
**Resposta:** Não, os visuais não seriam renderizados corretamente. Você precisará recriar as funções e regras no Power BI Desktop e, em seguida, publicá-las no serviço do Power BI.

**Pergunta:** Posso criar essas funções para fontes de dados do Analysis Services?  
**Resposta:** Sim, isso é possível se você importou os dados no Power BI Desktop. Se você estiver usando uma conexão dinâmica, não poderá configurar a RLS no serviço do Power BI. Isso é definido no modelo local do Analysis Services.

**Pergunta:** Posso usar a RLS para limitar as colunas ou as medidas acessíveis por meus usuários?  
**Resposta:** Não, se um usuário tiver acesso a uma linha específica de dados, ele poderá ver todas as colunas de dados dessa linha.

**Pergunta:** A RLS permite ocultar dados detalhados, mas conceder acesso aos dados resumidos nos visuais?  
**Resposta:** Não. Você protege linhas individuais de dados, mas os usuários sempre podem ver os detalhes ou os dados resumidos.

**Pergunta:** Minha fonte de dados já tem funções de segurança definidas (por exemplo, funções do SQL Server ou funções do SAP BW). Qual é a relação entre essas funções e a RLS?  
**Resposta:** A resposta depende de você estar importando dados ou usando o DirectQuery. Se você estiver importando dados para o conjunto de dados do Power BI, as funções de segurança em sua fonte de dados não serão usadas. Nesse caso, você deve definir a RLS para impor regras de segurança para usuários que se conectam ao Power BI. Se você estiver usando o DirectQuery, as funções de segurança em sua fonte de dados serão usadas. Quando um usuário abre um relatório, o Power BI envia uma consulta para a fonte de dados subjacente, que aplica as regras de segurança aos dados com base nas credenciais do usuário.
