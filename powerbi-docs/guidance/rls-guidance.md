---
title: Diretrizes de RLS (Segurança em Nível de Linha) no Power BI Desktop
description: Diretrizes para impor a RLS (Segurança em Nível de Linha) em seus modelos de dados com o Power BI Desktop.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/18/2020
ms.author: v-pemyer
ms.openlocfilehash: 308e34e5bf70a9999939c99667075b2e468b4df4
ms.sourcegitcommit: eff98b49e794c7c07670dcfb871f43cb06ed9d3a
ms.contentlocale: pt-BR
ms.lasthandoff: 06/19/2020
ms.locfileid: "85095605"
---
# <a name="row-level-security-rls-guidance-in-power-bi-desktop"></a>Diretrizes de RLS (Segurança em Nível de Linha) no Power BI Desktop

Este artigo destina-se aos modeladores de dados que trabalham com o Power BI Desktop. Ele descreve boas práticas de design para impor a RLS em seus modelos de dados.

É importante entender as _linhas de tabela_ dos filtros de RLS. Elas não podem ser configuradas para restringir o acesso a objetos de modelo, incluindo tabelas, colunas ou medidas.

> [!NOTE]
> Este artigo não descreve a RLS ou como configurá-la. Para obter mais informações, confira [Restringir o acesso a dados com a RLS (Segurança em Nível de Linha) no Power BI Desktop](../create-reports/desktop-rls.md).
>
> Além disso, ele não aborda a aplicação de RLS em conexões dinâmicas a modelos hospedados externamente com o Azure Analysis Services ou o SQL Server Analysis Services. Nesses casos, a RLS é imposta pelo Analysis Services. Quando o Power BI se conecta com SSO (logon único), o Analysis Services impõe a RLS (a menos que a conta tenha privilégios de administrador).

## <a name="create-roles"></a>Criar Funções

É possível criar várias funções. Quando você estiver considerando as necessidades de permissão para um único usuário de relatório, procure criar uma única função que conceda todas essas permissões, em vez de um design em que um usuário de relatório será membro de várias funções. Isso porque um usuário de relatório pode ser mapeado para várias funções, seja diretamente usando sua conta de usuário ou indiretamente pela associação de grupo de segurança. Os mapeamentos de função múltipla podem gerar resultados inesperados.

Quando um usuário de relatório é atribuído a várias funções, os filtros de RLS se tornam aditivos. Isso significa que os usuários de relatório podem ver linhas de tabela que representam a união desses filtros. Além disso, em alguns cenários, não é possível garantir que um usuário de relatório não veja linhas em uma tabela. Portanto, ao contrário das permissões aplicadas a objetos de banco de dados SQL Server (e outros modelos de permissão), o princípio "quando negado, sempre negado" não se aplica.

Considere um modelo com duas funções: A primeira função, denominada **Workers**, restringe o acesso a todas as linhas da tabela **Payroll** por meio da seguinte expressão de regra:

```dax
FALSE()
```

> [!NOTE]
> Uma regra não retornará nenhuma linha de tabela quando sua expressão for avaliada como **false**.

Contudo, uma segunda função, denominada **Managers**, permite o acesso a todas as linhas da tabela **Payroll** por meio da seguinte expressão de regra:

```dax
TRUE()
```

Cuidado: se um usuário de relatório for mapeado para ambas as funções, ele verá todas as linhas da tabela **Salary**.

## <a name="optimize-rls"></a>Otimizar a RLS

A RLS funciona aplicando filtros automaticamente a todas as consultas DAX, e esses filtros podem ter um impacto negativo no desempenho da consulta. Portanto, uma RLS eficiente se resume a um bom design de modelo. É importante seguir as diretrizes de design de modelo, conforme discutido nos seguintes artigos:

- [Entender o esquema em estrela e a importância para o Power BI](star-schema.md)
- Todos os artigos sobre diretrizes de relações encontrados na [Documentação de diretrizes do Power BI](https://docs.microsoft.com/power-bi/guidance/)

Em geral, costuma ser mais eficiente impor filtros de RLS em tabelas de tipo de dimensão, e não em tabelas de tipo de fato. E é preciso haver relações bem projetadas a fim de garantir que os filtros de RLS se propaguem para outras tabelas de modelo. Portanto, evite usar a função DAX [LOOKUPVALUE](https://docs.microsoft.com/dax/lookupvalue-function-dax) quando as relações de modelo puderem obter o mesmo resultado.

Sempre que os filtros de RLS forem aplicados em tabelas do DirectQuery e houver relações com outras tabelas do DirectQuery, não se esqueça de otimizar o banco de dados de origem. Isso pode envolver a criação de índices apropriados ou o uso de colunas computadas persistentes. Para obter mais informações, confira as [Diretrizes de modelo do DirectQuery no Power BI Desktop](directquery-model-guidance.md).

### <a name="measure-rls-impact"></a>Medir impacto da RLS

É possível medir o impacto no desempenho dos filtros de RLS no Power BI Desktop usando o [Performance Analyzer](../create-reports/desktop-performance-analyzer.md). Primeiro, determine as durações das consultas de visuais de relatório quando a RLS não for imposta. Em seguida, use o comando **Exibir Como** na guia da faixa de opções **Modelagem** para impor a RLS e determinar e comparar as durações das consultas.

## <a name="configure-role-mappings"></a>Configurar mapeamentos de função

Depois da publicação no Power BI, você deve mapear membros para funções de conjunto de dados. Somente proprietários de conjunto de dados ou administradores de workspace podem adicionar membros a funções. Para obter mais informações, confira [RLS (Segurança em Nível de Linha) com o Power BI (Gerenciar a segurança em seu modelo)](../admin/service-admin-rls.md#manage-security-on-your-model).

Os membros podem ser contas de usuário ou grupos de segurança. Sempre que possível, é recomendável mapear grupos de segurança para funções de conjunto de dados. Isso envolve o gerenciamento de associações de grupo de segurança no Azure Active Directory. Possivelmente, ele delega a tarefa aos seus administradores de rede.

## <a name="validate-roles"></a>Validar funções

Teste cada função para garantir que ela filtre o modelo corretamente. É possível fazer isso facilmente usando o comando **Exibir Como** na guia da faixa de opções **Modelagem**.

Quando o modelo tiver regras dinâmicas usando a função DAX [USERNAME](https://docs.microsoft.com/dax/username-function-dax), teste os valores esperados _e inesperados_. Durante a inserção de conteúdo do Power BI – especificamente usando o cenário [O aplicativo possui dados](../developer/embedded/embedding.md#embedding-for-your-customers) – a lógica do aplicativo pode passar qualquer valor como um nome de usuário de identidade eficaz. Sempre que possível, garanta que valores acidentais ou mal-intencionados resultem em filtros que não retornam linhas.

Considere um exemplo usando o Power BI Embedded, em que o aplicativo passa a função de trabalho do usuário como o nome de usuário efetivo: "Manager" ou "Worker". Os gerentes podem ver todas as linhas, mas os trabalhadores só podem ver linhas em que o valor da coluna **Type** é "Internal".

A seguinte expressão de regra é definida:

```dax
IF(
    USERNAME() = "Worker",
    [Type] = "Internal",
    TRUE()
)
```

O problema com essa expressão de regra é que todos os valores, exceto "Worker", retornam _todas as linhas da tabela_. Portanto, um valor acidental, como "Wrker", retorna de forma não intencional todas as linhas da tabela. Desse modo, é mais seguro escrever uma expressão que testa cada valor esperado. Na seguinte expressão de regra aprimorada, um valor inesperado fará com que a tabela não retorne nenhuma linha.

```dax
IF(
    USERNAME() = "Worker",
    [Type] = "Internal",
    IF(
        USERNAME() = "Manager",
        TRUE(),
        FALSE()
    )
)
```

## <a name="design-partial-rls"></a>Criar RLS parcial

Às vezes, os cálculos precisam de valores que não são restritos por filtros de RLS. Por exemplo, um relatório pode precisar exibir uma proporção de receita obtida para a região de vendas do usuário de relatório sobre _toda a receita obtida_.

Embora não seja possível que uma expressão DAX substitua a RLS – na verdade, ela não pode nem mesmo determinar que a RLS é imposta – você pode usar uma tabela de modelo de resumo. A tabela de modelo de resumo é consultada para recuperar a receita de "todas as regiões" e não é restrita por nenhum filtro de RLS.

Vejamos como você pode implementar esse requisito de design. Primeiro, considere o seguinte design de modelo:

:::image type="content" source="media/rls-guidance/mixed-rls-model.png" alt-text="É mostrada uma imagem de um diagrama de modelo. Ele é descrito nos parágrafos a seguir.":::

O modelo consiste em quatro tabelas:

- A tabela **Salesperson** armazena uma linha por vendedor. Ela inclui a coluna **EmailAddress**, que armazena o endereço de email para cada vendedor. Essa tabela fica oculta.
- A tabela **Sales** armazena uma linha por pedido. Ela inclui a medida **Revenue % All Region**, que é projetada para retornar uma proporção de receita obtida pela região do usuário de relatório em relação à receita obtida por todas as regiões.
- A tabela **Date** armazena uma linha por data e permite filtrar e agrupar ano e mês.
- **SalesRevenueSummary** é uma tabela calculada. Ela armazena a receita total para cada data de pedido. Essa tabela fica oculta.

A seguinte expressão define a tabela calculada **SalesRevenueSummary**:

```dax
SalesRevenueSummary =
SUMMARIZECOLUMNS(
    Sales[OrderDate],
    "RevenueAllRegion", SUM(Sales[Revenue])
)
```

> [!NOTE]
> Uma [tabela de agregação](../transform-model/desktop-aggregations.md) pode atingir o mesmo requisito de design.

A seguinte regra de RLS é aplicada à tabela **Salesperson**:

```dax
[EmailAddress] = USERNAME()
```

Cada uma das três relações de modelo é descrita na seguinte tabela:

|Relação|Descrição|
|---------|---------|
|![Terminador de fluxograma 1.](media/common/icon-01-red-30x30.png)|Há uma relação muitos para muitos entre as tabelas **Salesperson** e **Sales**. A regra de RLS filtra a coluna **EmailAddress** da tabela oculta **Salesperson** usando a função DAX [USERNAME](https://docs.microsoft.com/dax/username-function-dax). O valor da coluna **Region** (para o usuário do relatório) se propaga para a tabela **Sales**.|
|![Terminador de fluxograma 2.](media/common/icon-02-red-30x30.png)|Há uma relação um-para-muitos entre as tabelas **Date** e **Sales**.|
|![Terminador de fluxograma 3.](media/common/icon-03-red-30x30.png)|Há uma relação um-para-muitos entre as tabelas **Date** e **SalesRevenueSummary**.|

A seguinte expressão define a medida **Revenue % All Region**:

```dax
Revenue % All Region =
DIVIDE(
    SUM(Sales[Revenue]),
    SUM(SalesRevenueSummary[RevenueAllRegion])
)
```

> [!NOTE]
> Tome cuidado para evitar a divulgação de fatos confidenciais. Caso haja apenas duas regiões nesse exemplo, é possível que um usuário de relatório calcule a receita da outra região.

## <a name="avoid-using-rls"></a>Evitar o uso de RLS

Evite usar a RLS sempre que isso fizer sentido. Se você tiver apenas um pequeno número de regras de RLS simplistas que aplicam filtros estáticos, considere publicar vários conjuntos de dados em vez disso. Nenhum dos conjuntos de dados define funções porque cada conjunto contém dados para um público específico de usuários de relatório, que tem as mesmas permissões de dados. Em seguida, crie um workspace por público e atribua permissões de acesso ao workspace ou aplicativo.

Por exemplo, uma empresa que tem apenas duas regiões de vendas decide publicar um conjunto de dados _para cada região_ a workspaces diferentes. Os conjuntos de dados não impõem RLS. No entanto, eles usam [parâmetros de consulta](https://docs.microsoft.com/power-query/power-query-query-parameters) para filtrar os dados de origem. Dessa forma, o mesmo modelo é publicado em cada workspace – eles têm apenas valores de parâmetro de conjunto de dados diferentes. Os vendedores recebem acesso a apenas um dos workspaces (ou aplicativos publicados).

Há várias vantagens quando a RLS é evitada:

- **Desempenho de consulta aprimorado:** isso pode resultar em uma melhoria do desempenho devido a menos filtros.
- **Modelos menores:** embora isso resulte em mais modelos, eles têm um tamanho menor. Modelos menores podem melhorar a capacidade de resposta da atualização de dados e de consulta, especialmente se o recurso de hospedagem enfrentar pressão sobre os recursos. Além disso, é mais fácil manter tamanhos de modelo abaixo dos limites impostos pela sua capacidade. Por fim, é mais fácil balancear as cargas de trabalho entre diferentes capacidades, pois você pode criar workspaces em – ou movê-los para – diferentes capacidades.
- **Recursos adicionais:** recursos do Power BI que não funcionam com a RLS, como [Publicar na Web](../collaborate-share/service-publish-to-web.md), podem ser usados.

No entanto, há desvantagens quando a RLS é evitada:

- **Vários workspaces:** é necessário um workspace para cada público de usuários de relatório. Se os aplicativos forem publicados, isso também significará que há um aplicativo por público de usuários de relatório.
- **Duplicação de conteúdo:** é preciso criar relatórios e dashboards em cada workspace. Isso requer esforço e tempo adicionais de configuração e manutenção.
- **Usuários com privilégios elevados:** os usuários com privilégios elevados, que pertencem a vários públicos de usuários de relatório, não podem ver uma exibição consolidada dos dados. Eles precisarão abrir vários relatórios (de diferentes workspaces ou aplicativos).

## <a name="troubleshoot-rls"></a>Solucionar problemas de RLS

Se a RLS produzir resultados inesperados, verifique se há os seguintes problemas:

- Existem relações incorretas entre tabelas de modelo, em termos de mapeamentos de coluna e direções de filtro.
- A propriedade de relação **Aplicar filtro de segurança em ambas as direções** não está definida corretamente. Para saber mais, confira [Diretrizes de relações bidirecionais](relationships-bidirectional-filtering.md).
- As tabelas não contêm dados.
- Valores incorretos foram carregados nas tabelas.
- O usuário está mapeado para várias funções.
- O modelo inclui tabelas de agregação, e as regras de RLS não filtram consistentemente as agregações e os detalhes. Para obter mais informações, confira [Usar agregações no Power BI Desktop (RLS para agregações)](../transform-model/desktop-aggregations.md#rls-for-aggregations).

Quando um usuário específico não consegue ver dados, pode ser porque seu UPN não está armazenado ou foi inserido da forma incorreta. Isso pode ocorrer abruptamente porque sua conta de usuário foi alterada como resultado de uma alteração de nome.

> [!TIP]
> Para fins de teste, adicione uma medida que retorne a função DAX [USERNAME](https://docs.microsoft.com/dax/username-function-dax). Você pode nomeá-la como "Quem sou eu". Em seguida, adicione a medida a um visual de cartão em um relatório e publique-a no Power BI.

Quando um usuário específico consegue ver todos os dados, é possível que ele esteja acessando os relatórios diretamente no workspace e que seja o proprietário do conjunto de dados. A RLS só é imposta quando:

- O relatório é aberto em um aplicativo.
- O relatório é aberto em um workspace, e o usuário é mapeado para a [função Espectador](../collaborate-share/service-new-workspaces.md#roles-in-the-new-workspaces).

## <a name="next-steps"></a>Próximas etapas

Para obter mais informações relacionadas a este artigo, confira os seguintes recursos:

- [Segurança no nível da linha (RLS) com Power BI](../admin/service-admin-rls.md)
- [Restringir o acesso a dados com a RLS (Segurança em Nível de Linha) no Power BI Desktop](../create-reports/desktop-rls.md)
- [Modelar relações no Power BI Desktop](../transform-model/desktop-relationships-understand.md)
- Dúvidas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
- Sugestões? [Contribuir com ideias para aprimorar o Power BI](https://ideas.powerbi.com/)
