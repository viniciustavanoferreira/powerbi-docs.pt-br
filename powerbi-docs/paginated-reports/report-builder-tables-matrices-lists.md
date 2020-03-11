---
title: Tabelas, matrizes e listas no Construtor de Relatórios do Power BI
description: No Power BI Report Builder, tabelas, matrizes e listas são regiões de dados que exibem dados de relatórios paginados em células organizadas em linhas e colunas.
ms.date: 06/06/2019
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.assetid: 9dcf3fc8-bf9c-4a14-a03d-e78254aa4098
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 02ac131325dab59590cb88c524ace68a1226fc69
ms.sourcegitcommit: ced8c9d6c365cab6f63fbe8367fb33e6d827cb97
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/07/2020
ms.locfileid: "78921483"
---
# <a name="tables-matrixes-and-lists-in-power-bi-report-builder"></a>Tabelas, matrizes e listas no Construtor de Relatórios do Power BI
 No Construtor de Relatórios, tabelas, matrizes e listas são *regiões de dados* que exibem dados de relatórios paginados em células organizadas em linhas e colunas. As células geralmente contêm dados de texto como texto, datas e números, mas também podem conter medidores, gráficos ou itens de relatório, como imagens. Coletivamente, tabelas, matrizes e listas são frequentemente denominadas regiões de dados *Tablix*.  
  
 Os modelos de lista, matriz e tabela são criados na região de dados Tablix, que é uma grade flexível que pode exibir dados em células. Em modelos de tabela e matriz, as células são organizadas em linhas e colunas. Como os modelos são variações da região de dados Tablix genérica subjacente, você pode exibir dados na combinação de formatos de modelo e alterar a tabela, a matriz ou a lista para incluir os recursos de outra região de dados à medida que desenvolve seu relatório. Por exemplo, se adicionar uma tabela e perceber que ela não atende às suas necessidades, você poderá adicionar grupos de colunas para transformar a tabela em uma matriz.  
  
 As regiões de dados de tabela e matriz podem exibir relações de dados complexos, incluindo medidores, matrizes, listas, gráficos e tabelas aninhadas. As tabelas e as matrizes têm um layout tabular e seus dados vêm de um único conjunto de dados criado em uma única fonte de dados. A principal diferença entre tabelas e matrizes é que as tabelas podem incluir somente grupos de linhas, enquanto as matrizes têm grupos de linhas e grupos de colunas.  
  
 As listas são um pouco diferentes. Elas dão suporte a um layout livre e podem incluir várias tabelas ou matrizes pares, cada uma usando os dados de um conjunto de dados diferente. As listas também podem ser usadas para formulários, como faturas.  
  
 As imagens a seguir mostram relatórios simples com uma tabela, matriz ou lista.  

![Tabela, matriz e lista do Construtor de Relatórios](media/report-builder-tables-matrices-lists/report-builder-table-matrix-list.png)
  
##  <a name="Table"></a> Tabelas  
 Use uma tabela para exibir dados de detalhes, organizar os dados em grupos de linhas ou ambos. O modelo de Tabela contém três colunas com uma linha de cabeçalho de tabela e uma linha de detalhes para os dados. A figura a seguir mostra o modelo de tabela inicial, selecionado na área de design:  

![Modelo de tabela do Construtor de Relatórios na área de design, selecionado](media/report-builder-tables-matrices-lists/report-builder-new-table.png)
  
 É possível agrupar dados por um único campo, por vários campos ou escrevendo sua própria expressão. Você pode criar grupos aninhados ou independentes, grupos adjacentes e exibir valores agregados para dados agrupados ou adicionar totais a grupos. Por exemplo, se a tabela tiver um grupo de linhas chamado **Categoria**, você poderá adicionar um subtotal para cada grupo, bem como um total geral para o relatório. Para melhorar a aparência da tabela e realçar dados que deseja enfatizar, você pode mesclar células e aplicar formatação a dados e títulos da tabela.  
  
 Você inicialmente pode ocultar detalhes ou dados agrupados e incluir alternâncias de drill down para permitir que um usuário escolha interativamente quantos dados mostrar.  
  
##  <a name="Matrix"></a> Matrizes  
 Use uma matriz para exibir resumos de dados agregados, agrupados em linhas e colunas, semelhantes a uma Tabela Dinâmica ou a tabela de referência cruzada. O número de linhas e colunas para grupos é determinado pelo número de valores exclusivos para cada grupo de linhas e colunas. A figura a seguir mostra o modelo de matriz inicial, selecionado na área de design:  

![Nova matriz do Construtor de Relatórios adicionada da Caixa de Ferramentas, selecionada](media/report-builder-tables-matrices-lists/report-builder-new-matrix.png)
 
 Você pode agrupar dados por vários campos ou expressões em grupos de linhas e colunas. No tempo de execução, quando os dados de relatório e as regiões de dados são combinados, uma matriz cresce horizontal e verticalmente na página à medida que colunas para grupos de colunas e linhas para grupos de linhas são adicionadas. As células da matriz exibem valores de agregação que estão no escopo para a interseção dos grupos de linhas e colunas aos quais a célula pertence. Por exemplo, se a matriz tiver um grupo de linhas (Categoria) e dois grupos de colunas (Território e Ano) que exibem a soma das vendas, o relatório exibirá duas células com somas de vendas para cada valor no grupo Categoria. O escopo das células são as duas interseções: Categoria e Território; Categoria e Ano. A matriz pode incluir grupos aninhados e adjacentes. Os grupos aninhados têm uma relação pai-filho e os grupos adjacentes têm uma relação de par. Você pode adicionar subtotais a todos os níveis de linha aninhada e grupos de colunas dentro da matriz.  
  
 Para tornar os dados da matriz mais legíveis e realçar os dados que deseja enfatizar, você pode mesclar células ou dividir horizontal e verticalmente e aplicar formatação a dados e títulos de grupos.  
  
 Você também pode incluir alternâncias de drill down que inicialmente ocultam dados de detalhes. O usuário pode, em seguida, clicar nas alternâncias para exibir mais ou menos detalhes conforme necessário.  
  
##  <a name="List"></a> Listas  
 Use uma lista para criar um layout livre. Você não está limitado a um layout de grade e pode colocar campos livremente dentro da lista. Você pode usar uma lista para criar um formulário para exibir muitos campos de conjunto de dados ou como um contêiner para exibir várias regiões de dados lado a lado para dados agrupados. Por exemplo, você pode definir um grupo para uma lista, adicionar uma tabela, gráfico e imagem, além de exibir valores na tabela e no formato de gráfico para cada valor de grupo, assim como faria para um registro de funcionário ou de paciente.  

![Nova lista do Construtor de Relatórios adicionada da Caixa de Ferramentas, selecionada](media/report-builder-tables-matrices-lists/report-builder-new-list.png)
  
##  <a name="PreparingData"></a> Preparação dos dados  
 Uma tabela, matriz e regiões de dados de lista exibem dados de um conjunto de dados. Você pode preparar os dados na consulta que recupera os dados para o conjunto de dados ou definindo propriedades de tabela, matriz ou lista.  
  
 As linguagens de consulta, como Transact-SQL, que você usa para recuperar os dados para os conjuntos de dados de relatório podem preparar os dados aplicando filtros para incluir apenas um subconjunto dos dados, substituindo valores nulos ou em branco por constantes que tornam o relatório mais legível, classificando e agrupando dados.  
  
 Se escolher preparar os dados na tabela, matriz ou região de dados de lista de um relatório, você definirá propriedades na região de dados ou nas células dentro da região de dados. Se você quiser filtrar ou classificar os dados, defina as propriedades na região de dados. Por exemplo, para classificar os dados, você especifica as colunas para classificação e a direção de classificação. Se quiser fornecer um valor alternativo para um campo, você poderá definir os valores do texto da célula que exibe o campo. Por exemplo, para exibir o espaço em branco quando um campo estiver vazio ou nulo, use uma expressão para definir o valor.  
  
##  <a name="BuildingConfiguringTableMatrixList"></a> Como criar e configurar uma tabela, matriz ou lista  
 Ao adicionar tabelas ou matrizes a seu relatório, você pode usar o Assistente de tabelas e matrizes ou criá-las manualmente usando os modelos do Construtor de Relatórios. As listas são criadas manualmente usando o modelo de lista.  
  
 O assistente orienta você pelas etapas para criar e configurar rapidamente uma tabela ou matriz. Depois de concluir o assistente ou se criar as regiões de dados Tablix do zero, você ainda poderá configurar e refinar. As caixas de diálogo, disponíveis nos menus de atalho nas regiões de dados, facilitam definir as propriedades mais comumente usadas para quebras de página, capacidade de repetição e visibilidade de cabeçalhos e rodapés, opções de exibição, filtros e classificação. Entretanto, a região de dados Tablix fornece uma grande quantidade de propriedades adicionais, que podem ser definidas apenas no painel Propriedades do Construtor de Relatórios. Por exemplo, se quiser exibir uma mensagem quando o conjunto de dados para uma tabela, matriz ou lista estiver vazio, especifique o texto da mensagem na propriedade Tablix NoRowsMessage no painel Propriedades.  
  
##  <a name="ChangingBetweenTablixTemplates"></a> Como alterar entre modelos Tablix  
 Você não é limitado por sua escolha de modelo Tablix inicial. Conforme adiciona grupos, totais e rótulos, talvez você queira modificar o design Tablix. Por exemplo, você pode começar com uma tabela e, em seguida, excluir a linha de detalhes e adicionar grupos de colunas.  
  
 Você pode continuar a desenvolver uma tabela, matriz ou lista adicionando um recurso Tablix. Os recursos Tablix incluem exibição de dados de detalhes ou agregações para dados agrupados em linhas e colunas. Você pode criar grupos aninhados, grupos adjacentes independentes ou grupos recursivos. Você pode filtrar e classificar dados agrupados e combinar grupos facilmente com a inclusão de várias expressões de grupo em uma definição de grupo  
  
 Você também pode adicionar totais de um grupo ou totais gerais para a região de dados. Você pode ocultar linhas ou colunas para simplificar um relatório e permitir que o usuário alterne a exibição dos dados ocultos, como em um relatório drill down. 

## <a name="next-steps"></a>Próximas etapas

- [O que são os relatórios paginados no Power BI Premium?](paginated-reports-report-builder-power-bi.md)
