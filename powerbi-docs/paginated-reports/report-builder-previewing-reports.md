---
title: Como visualizar relatórios no Construtor de Relatórios do Power BI
description: Enquanto você cria um relatório paginado do Construtor de Relatórios, é útil visualizar o relatório frequentemente para verificar se ele exibe o que você deseja.
ms.date: 06/06/2019
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.assetid: ba6b5bdd-d8c6-4aa8-ba32-3a10b11969d4
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: afbc31e3ece8bc72ad52bb2fe7c3d871b2f68e1b
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/05/2020
ms.locfileid: "78922932"
---
# <a name="previewing-reports-in-power-bi-report-builder"></a>Como visualizar relatórios no Construtor de Relatórios do Power BI
  Enquanto você cria um relatório paginado do Construtor de Relatórios, é útil visualizar o relatório frequentemente para verificar se ele exibe o que você deseja. Para visualizar o relatório, clique em **Executar**. O relatório é renderizado no modo de visualização.  
  
 O Construtor de Relatórios melhora a experiência de visualização usando sessões de edição quando conectado a um servidor de relatório. A sessão de edição cria um cache de dados e disponibiliza os conjuntos de dados em cache para visualizações de relatório repetidas. Uma sessão de edição não é um recurso que você interage diretamente, mas entender quando o conjunto de dados armazenados em cache é atualizado ajudará a melhorar o desempenho ao visualizar um relatório e entender por que o relatório é renderizado mais rápida ou lentamente.  

  
> [!NOTE]  
> Há algumas diferenças entre a visualização no Construtor de Relatórios e a exibição em um navegador. Por exemplo, um controle de calendário, que é adicionado a um relatório ao especificar um parâmetro de tipo Data/Hora, é diferente no Construtor de Relatórios e em um navegador. 
  
## <a name="improving-preview-performance"></a>Como melhorar o desempenho de visualização  
 O modo como você cria e atualiza relatórios afeta a rapidez com que o relatório é renderizado na visualização. Na primeira vez que você visualiza um relatório que se baseia em uma referência de servidor, uma sessão de edição é criada para você e os dados usados quando o relatório é executado são adicionados a um cache de dados que é armazenado. Quando você fizer alterações no relatório que não afetarem os dados, a cópia armazenada em cache dos dados será usada pelo relatório. Isso significa que você não verá os dados serem alterados sempre que visualizar o relatório. Se você desejar novos dados, clique no botão **Atualizar** na faixa de opções.  
  
 As seguintes ações farão com que o cache seja atualizado e diminuirão a velocidade de renderização de relatório da próxima em que o relatório for visualizado:  
  
-   Adicionar, alterar ou excluir um conjunto de dados. O conjunto de dados armazenados em cache contém todos os conjuntos de dados que um relatório usa. Alterar um conjunto de dados invalida o conjunto de dados armazenados em cache. Isso inclui alterar o nome, a consulta ou os campos no conjunto de dados.  
  
    > [!NOTE]  
    >  Se o conjunto de dados tiver um grande número de campos que você não pretende usar, considere atualizar o conjunto de dados para omitir esses campos. Embora isso crie uma nova sessão de edição e a primeira visualização do relatório fique mais lenta, o conjunto de dados armazenados em cache menor é, de modo geral, benéfico ao desempenho do servidor de relatório.  
  
-   Adicionar, alterar ou excluir uma fonte de dados. Isso inclui alterar o nome ou as propriedades da fonte de dados, a extensão de dados da fonte de dados ou as propriedades da conexão à fonte de dados.  
  
-   Alterar a fonte de dados que o relatório usa para uma fonte de dados diferentes.  
  
-   Alterar o idioma do relatório.  
  
-   Alterar os assemblies ou o código personalizado que usa o relatório.  
  
-   Adicionar, alterar ou excluir os parâmetros de consulta nos valores de parâmetro ou no relatório.  
  
 As alterações no layout do relatório e a formatação de dados não afetam o conjunto de dados armazenados em cache. É possível executar as seguintes ações sem atualizar o conjunto de dados armazenados em cache:  
  
-   Adicionar ou remover regiões de dados como tabelas, matrizes ou gráficos.  
  
-   Adicionar ou excluir colunas do relatório. Todos os campos no conjunto de dados estão disponíveis para uso no relatório. Adicionar ou remover campos no relatório não tem efeito no conjunto de dados.  
  
-   Alterar a ordem dos campos nas tabelas e matrizes.  
  
-   Adicionar, alterar ou excluir grupos de linhas e colunas.  
  
-   Adicionar, alterar ou excluir a formatação de valores de dados em campos.  
  
-   Adicionar, alterar ou excluir imagens, linhas ou caixas de texto.  
  
-   Alterar as quebras de página.  
  
A sessão de edição é criada na primeira vez que você visualiza um relatório. Por padrão, uma sessão de edição dura 7.200 segundos (duas horas). A sessão será redefinida como duas horas sempre que você executar o relatório. Quando a sessão de edição expira, o cache de dados é excluído. Se a sessão de edição expirar, uma será criada automaticamente na próxima vez que você visualizar o relatório.
  
Por padrão, o cache de dados pode conter até cinco conjuntos de dados. Se você usar muitas combinações diferentes de valores de parâmetro, o relatório poderá precisar de mais dados. Isso requer que o cache seja atualizado e o relatório será renderizado mais lentamente na próxima vez que você o visualizar. 
  
## <a name="concurrency-of-report-updates"></a>Simultaneidade das atualizações de relatório  
Com frequência, você visualiza um relatório como uma etapa na atualização e, em seguida, salva um relatório no serviço do Power BI. Ao atualizar um relatório, é possível que alguém esteja atualizando e salvando o relatório ao mesmo tempo. O relatório que for salvo por último será a versão do relatório que estará disponível para futuras exibições e atualizações. Isso significa que a versão do relatório que você visualizou talvez não seja a versão que você reabriu. Você tem a opção de salvar o relatório com um novo nome usando a opção **Salvar como** no menu do Construtor de Relatórios.  
  
## <a name="external-report-items"></a>Itens de relatório externos  
 Seu relatório pode incluir itens como imagens externas que são armazenadas separadamente do relatório. Como os itens são armazenados separadamente é possível que eles possam ser movidos para uma localização diferente ou ser excluídos. Se isso acontecer, a visualização do relatório poderá falhar. Você pode atualizar o relatório para indicar a localização atualizada do item ou, se o item foi excluído, substituí-lo por um item existente ou remover a referência ao item do relatório.  
  
## <a name="next-steps"></a>Próximas etapas

- [O que são os relatórios paginados no Power BI Premium?](paginated-reports-report-builder-power-bi.md)
  
