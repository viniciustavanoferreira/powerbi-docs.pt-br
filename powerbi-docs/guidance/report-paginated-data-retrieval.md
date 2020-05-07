---
title: Diretrizes de recuperação de dados para relatórios paginados
description: Diretrizes para a criação de fontes de dados e conjuntos de dados para relatórios paginados do Power BI.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 02/16/2020
ms.author: v-pemyer
ms.openlocfilehash: 067171f7ec74beccdb5a312c1cac5bbc6c87541f
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/05/2020
ms.locfileid: "79377640"
---
# <a name="data-retrieval-guidance-for-paginated-reports"></a>Diretrizes de recuperação de dados para relatórios paginados

Este artigo se destina aos autores de relatórios que elaboram [relatórios paginados](../paginated-reports/paginated-reports-report-builder-power-bi.md) do Power BI. Ele fornece recomendações para ajudar você a criar uma recuperação de dados eficaz e eficiente.

## <a name="data-source-types"></a>Tipos de fontes de dados

Os relatórios paginados oferecem suporte nativo a fontes de dados relacionais e analíticas. Essas fontes são categorizadas ainda mais, como sendo baseadas em nuvem ou locais. As fontes de dados locais – independentemente de elas serem hospedadas localmente ou em uma máquina virtual – exigem um gateway de dados para que Power BI possa se conectar. Baseado em nuvem significa que Power BI pode se conectar diretamente usando uma conexão com a Internet.

Caso você possa escolher o tipo de fonte de dados (o que possivelmente acontecerá em um novo projeto), recomendamos que use fontes de dados baseadas em nuvem. Os relatórios paginados podem se conectar com menor latência de rede, especialmente quando as fontes de dados residem na mesma região que seu locatário do Power BI. Além disso, é possível se conectar a essas fontes usando o SSO (logon único). Isso significa que a identidade do usuário do relatório pode fluir para a fonte de dados, permitindo que as permissões de nível de linha por usuário sejam impostas. Atualmente, o SSO não tem suporte para fontes de dados locais (o que significa que o SQL Server Analysis Services não pode impor permissões de nível de linha por usuário).

> [!NOTE]
> Embora atualmente não seja possível se conectar a bancos de dados locais usando o SSO, você ainda pode impor permissões de nível de linha. Isso é feito passando o campo interno **UserID** para um parâmetro de consulta de conjunto de dados. A fonte de dados precisará armazenar valores de nome UPN de modo que possa filtrar os resultados da consulta corretamente.
>
> Por exemplo, considere que cada vendedor é armazenado como uma linha na tabela **Vendedor**.  A tabela tem colunas para UPN, assim como a região de vendas do vendedor. No momento da consulta, a tabela é filtrada pelo UPN do usuário do relatório. Também é relacionada a fatos de vendas usando uma junção interna. Dessa forma, a consulta filtra efetivamente as linhas de fatos de vendas para aquelas da região de vendas do usuário do relatório.

### <a name="relational-data-sources"></a>Fontes de dados relacionais

Em geral, as fontes de dados relacionais são adequadas para relatórios de estilo operacional, como faturas de vendas. Elas também são adequadas para relatórios que precisam recuperar conjuntos de dados muito grandes (com mais de 10.000 linhas). As fontes de dados relacionais também podem definir procedimentos armazenados, que podem ser executados por conjuntos de dados do relatório. Os procedimentos armazenados oferecem vários benefícios:

- Parametrização
- Encapsulamento de lógica de programação, permitindo uma preparação de dados mais complexa (por exemplo, tabelas temporárias, cursores ou funções escalares definidas pelo usuário)
- Melhor manutenção, permitindo que a lógica de procedimento armazenado seja atualizada facilmente. Em alguns casos, isso pode ser feito sem a necessidade de modificar e republicar relatórios paginados (desde que os nomes de coluna e tipos de dados permaneçam inalterados).
- Melhor desempenho, já que os planos de execução são armazenados em cache para reutilização
- Reutilização de procedimentos armazenados em vários relatórios

No Power BI Report Builder, você pode usar o designer de consulta relacional para construir graficamente uma instrução de consulta, mas apenas para fontes de dados da Microsoft.

### <a name="analytic-data-sources"></a>Fontes de dados analíticas

As fontes de dados analíticas são adequadas para relatórios operacionais e analítico. Elas podem fornecer resultados de consulta resumidos rapidamente, mesmo em volumes de dados muito grandes. As medidas de modelo e KPIs podem encapsular regras de negócio complexas para obter um resumo dos dados. No entanto, essas fontes de dados não são adequadas para relatórios que precisam recuperar conjuntos de dados muito grandes (com mais de 10.000 linhas).

No Power BI Report Builder, você tem a opção de dois designers de consulta: O designer de consulta DAX do Analysis Services e o designer de consulta MDX do Analysis Services. Esses designers podem ser usados para fontes de dados de conjunto de dados do Power BI ou qualquer modelo do SQL Server Analysis Services ou do Azure Analysis Services, seja tabular ou multidimensional.

Sugerimos que você use o designer de consulta DAX, desde que ele atenda totalmente às suas necessidades de consulta. Se o modelo não definir as medidas necessárias, você precisará alternar para o modo de consulta. Nesse modo, é possível personalizar a instrução de consulta adicionando expressões (para obter o resumo).

O designer de consulta MDX requer que seu modelo inclua medidas. O designer tem dois recursos que não são compatíveis com o designer de consulta DAX. Especificamente, ele permite que você:

- Defina membros calculados em nível de consulta (no MDX).
- Configure regiões de dados para solicitar [agregações de servidor](/sql/reporting-services/report-design/report-builder-functions-aggregate-function) em grupos que não são de detalhes. Se o relatório precisar apresentar resumos de medidas semiaditivas ou não aditivas (como cálculos de inteligência de tempo ou contagens distintas), provavelmente será mais eficiente usar agregações de servidor do que recuperar linhas de detalhes de baixo nível e fazer com que resumos sejam computados no relatório.

## <a name="query-result-size"></a>Tamanho dos resultados da consulta

Em geral, recuperar apenas os dados exigidos por seu relatório é uma melhor prática. Portanto, não recupere colunas ou linhas que não são exigidas pelo relatório.

Para limitar as linhas, você sempre deve aplicar os filtros mais restritivos e definir consultas de agregação. As consultas de agregação agrupam e resumem os dados de origem para recuperar resultados de detalhamento mais alto. Por exemplo, considere que seu relatório precisa apresentar um resumo das vendas dos vendedores. Em vez de recuperar todas as linhas de ordens de venda, crie uma consulta de conjunto de dados que agrupe por vendedor e resuma as vendas de cada grupo.

## <a name="expression-based-fields"></a>Campos baseados em expressão

É possível estender um conjunto de dados de um relatório com campos baseados em expressões. Por exemplo, se seu conjunto de dados contém nome e sobrenome do cliente, talvez você queira um campo que concatene os dois campos para produzir o nome completo do cliente. Para obter esse cálculo, você tem duas opções. Você pode:

- Criar um _campo calculado_, que é um campo de conjunto de dados baseado em uma expressão.
- Injetar uma expressão diretamente na consulta do conjunto de dados (usando o idioma nativo da sua fonte de dados), o que resulta em um campo de conjunto de dados regular.

É recomendável a última opção, sempre que possível. É melhor injetar expressões diretamente em sua consulta de conjunto de dados por dois bons motivos:

- É possível que sua fonte de dados seja otimizada para avaliar a expressão com mais eficiência do que Power BI (isso acontece especialmente em bancos de dados relacionais).
- O desempenho do relatório melhora porque o Power BI não precisa materializar campos calculados antes da renderização do relatório. Os campos calculados podem estender visivelmente o tempo de renderização do relatório quando os conjuntos de dados recuperam um grande número de linhas.

## <a name="field-names"></a>Nomes de campo

Quando você cria um conjunto de dados, seus campos são automaticamente nomeados de acordo com as colunas de consulta. É possível que esses nomes não sejam simples nem intuitivos. Também é possível que os nomes das colunas de consulta de fonte contenham caracteres proibidos em identificadores de objeto RDL (linguagem de definição de relatórios) (como espaços e símbolos). Nesse caso, os caracteres proibidos são substituídos por um caractere de sublinhado (_).

Recomendamos que você primeiro verifique se todos os nomes de campo são simples e concisos, mas ainda significativos. Caso não sejam, sugerimos renomeá-los _antes_ de iniciar o layout do relatório. Isso porque os campos renomeados não reproduzem as alterações nas expressões usadas no layout do relatório. Se você decidir renomear campos depois de iniciar o layout do relatório, precisará localizar e atualizar todas as expressões rompidas.

## <a name="filter-vs-parameter"></a>Filtro ou parâmetro

É provável que seus designs de relatórios paginados tenham parâmetros de relatório. Os parâmetros de relatório normalmente são usados para solicitar que o usuário do relatório filtre o relatório. Como autor de um relatório paginado, você tem duas maneiras de fazer a filtragem de relatórios. Você pode mapear um parâmetro de relatório para:

- Um _filtro_ de conjunto de dados. Nesse caso, os valores de parâmetros de relatório são usados para filtrar os dados já recuperados pelo conjunto de dados.
- Um _parâmetro_ de conjunto de dados. Nesse caso, os valores de parâmetros de relatório são injetados na consulta nativa enviada à fonte de dados.

> [!NOTE]
> Todos os conjuntos de dados do relatório são armazenados em cache _por sessão_ por até 10 minutos _após o último uso_. Um conjunto de dados pode ser reutilizado ao enviar novos valores de parâmetros (filtragem), renderizar o relatório em um formato diferente ou interagir com o design do relatório de alguma forma, como alternando a visibilidade ou classificando.

Considere, em seguida, um exemplo de um relatório de vendas que tem um único parâmetro de relatório para filtrar o relatório por um único ano. O conjunto de dados recupera vendas para _todos os anos_. Isso é feito porque o parâmetro do relatório é mapeado para os filtros do conjunto de dados. O relatório exibe os dados para o ano solicitado, que é um subconjunto dos dados do conjunto de dados. Quando o usuário do relatório altera o parâmetro do relatório para um ano diferente – e, em seguida, exibe o relatório – o Power BI não precisa recuperar nenhum dado de origem. Em vez disso, ele aplica um filtro diferente ao conjunto de dados já armazenado em cache. Depois que o conjunto de dados é armazenado em cache, a filtragem pode ser muito rápida.

Agora, considere um design de relatório diferente. Desta vez, o design do relatório mapeia o parâmetro do relatório de ano de vendas para um parâmetro de conjunto de dados. Assim, o Power BI injeta o valor ano na consulta nativa e o conjunto de dados recupera os dados somente para esse ano. Sempre que o usuário do relatório altera o valor do parâmetro do relatório ano – e, em seguida, exibe o relatório – o conjunto de dados recupera um novo resultado da consulta apenas para esse ano.

As duas abordagens de design podem filtrar dados do relatório. Além disso, os dois designs podem funcionar bem para seus designs de relatório. No entanto, um design otimizado dependerá dos volumes de dados previstos, da volatilidade dos dados e dos comportamentos previstos dos usuários do relatório.

É recomendável a _filtragem do conjunto de dados_ quando você prevê que um subconjunto diferente das linhas do conjunto de dados será reutilizado muitas vezes (isso diminui o tempo de renderização, pois novos dados não precisam ser recuperados). Nesse cenário, você reconhece que o custo da recuperação de um conjunto de dados maior pode ser compensado por causa do número de vezes que ele será reutilizado. Portanto, é útil para consultas cuja geração é demorada. Mas tome cuidado: armazenar em cache grandes conjuntos de dados por usuário pode afetar negativamente o desempenho e a taxa de transferência da capacidade.

Recomendamos a _parametrização do conjunto de dados_ quando você prevê que é improvável que um subconjunto diferente de linhas do conjunto de dados seja solicitado – ou quando o número de linhas do conjunto de dados a serem filtradas provavelmente seja muito grande (e ineficiente para cache). Essa abordagem de design também funciona bem quando o armazenamento de dados é volátil. Nesse caso, cada alteração de valor de parâmetro do relatório resultará na recuperação de dados atualizados.

## <a name="non-native-data-sources"></a>Fontes de dados não nativas

Se você precisar desenvolver relatórios paginados com base em fontes de dados que não têm [suporte nativo dos relatórios paginados](../paginated-reports/paginated-reports-data-sources.md), poderá primeiro desenvolver um modelo de dados do Power BI Desktop. Dessa forma, você pode se conectar a mais de 100 [fontes de dados do Power BI](../power-bi-data-sources.md). Depois da publicação no serviço do Power BI, você pode desenvolver um relatório paginado que se conecta ao conjunto de dados do Power BI.

## <a name="data-integration"></a>Integração de dados

Se você precisar combinar dados de várias fontes de dados, terá duas opções:

- **Combinar conjuntos de dados do relatório**: Se as fontes de dados tiverem [suporte nativo dos relatórios paginados](../paginated-reports/paginated-reports-data-sources.md), você poderá considerar a criação de campos calculados que usam as funções [Lookup](/sql/reporting-services/report-design/report-builder-functions-lookup-function) ou [LookupSet](/sql/reporting-services/report-design/report-builder-functions-lookupset-function) do Report Builder.
- **Desenvolver um modelo do Power BI Desktop**: No entanto, é mais eficiente que você desenvolva um modelo de dados no Power BI Desktop. Você pode usar Power Query para combinar consultas com base em qualquer [fonte de dados com suporte](../power-bi-data-sources.md). Depois da publicação no serviço do Power BI, você pode desenvolver um relatório paginado que se conecta ao conjunto de dados do Power BI.

## <a name="sql-server-complex-data-types"></a>Tipos de dados complexos do SQL Server

Como o SQL Server é uma fonte de dados local, o Power BI deve se conectar por meio de um gateway. No entanto, o gateway não dá suporte à recuperação de dados para tipos de dados complexos. Os tipos de dados complexos incluem tipos internos, como os [tipos de dados espaciais](/sql/relational-databases/spatial/spatial-data-sql-server) GEOMETRY e GEOGRAPHY, além de [hierarchyid](/sql/t-sql/data-types/hierarchyid-data-type-method-reference). Eles também podem incluir tipos definidos pelo usuário implementados por meio de uma classe de um assembly no CLR (Common Language Runtime) do Microsoft.NET Framework.

A plotagem de dados espaciais e da análise na visualização do mapa precisa de dados espaciais do SQL Server. Portanto, não é possível trabalhar com a visualização de mapa quando SQL Server é sua fonte de dados. Para que não restem dúvidas, isso funcionará se sua fonte de dados for um Banco de Dados SQL do Azure, porque o Power BI não se conecta por meio de um gateway.

## <a name="data-related-images"></a>Imagens relacionadas a dados

As imagens podem ser usadas para adicionar logotipos ou imagens ao layout do relatório. Quando as imagens se relacionam com as linhas recuperadas por um conjunto de dados do relatório, você tem duas opções:

- É possível que os dados da imagem também possam ser recuperados da fonte de dados (caso já estejam armazenados em uma tabela).
- Quando as imagens são armazenadas em um servidor Web, você pode usar uma expressão dinâmica para criar o caminho da URL da imagem.

Para obter mais informações e sugestões, confira [Diretrizes de imagem para relatórios paginados](report-paginated-image.md).

## <a name="redundant-data-retrieval"></a>Recuperação de dados redundantes

É possível que o relatório recupere dados redundantes. Isso pode acontecer quando você exclui campos de consulta de conjunto de dados ou quando o relatório tem conjuntos de dados não utilizados. Evite essas situações. Elas resultam em uma sobrecarga desnecessária nas fontes de dados, na rede e nos recursos de capacidade do Power BI.

### <a name="deleted-query-fields"></a>Campos de consulta excluídos

Na página **Campos** da janela **Propriedades do conjunto de dados**, é possível excluir os _campos de consulta_ do conjunto de dados (os campos de consulta são mapeados para colunas recuperadas pela consulta do conjunto de dados). No entanto, o Report Builder não remove as colunas correspondentes da consulta do conjunto de dados.

Caso você precise excluir campos de consulta do seu conjunto de dados, recomendamos que remova as colunas correspondentes da consulta de conjunto de dados. O Report Builder removerá automaticamente os campos de consulta redundantes. Se você for excluir campos de consulta, lembre-se também de modificar a instrução de consulta do conjunto de dados para remover as colunas.

### <a name="unused-datasets"></a>Conjuntos de dados não utilizados

Quando um relatório é executado, todos os conjuntos de dados são avaliados, mesmo que não estejam associados a objetos do relatório. Por esse motivo, remova todos os conjuntos de dados de teste ou desenvolvimento antes de publicar um relatório.

## <a name="next-steps"></a>Próximas etapas

Para obter mais informações relacionadas a este artigo, confira os seguintes recursos:

- [Fontes de dados com suporte para relatórios paginados do Power BI](../paginated-reports/paginated-reports-data-sources.md)
- Dúvidas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
- Sugestões? [Contribuir com ideias para aprimorar o Power BI](https://ideas.powerbi.com/)
