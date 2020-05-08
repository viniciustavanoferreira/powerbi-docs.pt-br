---
title: Separar relatórios de modelos no Power BI Desktop
description: Diretrizes para separar relatórios de modelos no Power BI Desktop.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 04/11/2020
ms.author: v-pemyer
ms.openlocfilehash: dad451da460abed65a69990394522f268d7f21cd
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/05/2020
ms.locfileid: "81525229"
---
# <a name="separate-reports-from-models-in-power-bi-desktop"></a>Separar relatórios de modelos no Power BI Desktop

Ao criar uma solução do Power BI Desktop, uma das primeiras tarefas que você precisa fazer é obter dados. A obtenção de dados pode resultar em dois resultados distintos. Ela poderia:

- Criar uma [conexão dinâmica](../desktop-report-lifecycle-datasets.md) a um modelo já publicado, que poderia ser um conjunto de dados do Power BI ou um modelo do Analysis Services hospedado remotamente.
- Iniciar o desenvolvimento de um novo modelo, que pode ser um modelo de importação, DirectQuery ou composto.

Este artigo se preocupa com o segundo cenário. Ele fornece orientação sobre se um relatório e um modelo devem ou não ser combinados em um único arquivo do Power BI Desktop.

## <a name="single-file-solution"></a>Solução de arquivo único

Uma _solução de arquivo único_ funciona bem quando há apenas um relatório com base no modelo. Nesse caso, é provável que o modelo e o relatório sejam esforços da mesma pessoa. Definimos isso como uma solução de _BI pessoal_, embora o relatório possa ser compartilhado com outras pessoas. Essas soluções podem representar relatórios com escopo de função ou avaliações de um desafio comercial a serem realizadas uma única vez, geralmente descritas como _relatórios ad hoc_.

:::image type="content" source="media/report-separate-from-model/single-file-solution.png" alt-text="Um arquivo contém um modelo e um relatório, desenvolvidos pela mesma pessoa." border="true":::

## <a name="separate-report-files"></a>Separar arquivos de relatório

Faz sentido colocar o desenvolvimento de modelos e o de relatórios em arquivos separados do Power BI Desktop quando:

- Os modeladores de dados e os autores de relatórios são pessoas diferentes.
- Entende-se que um modelo será a fonte de vários relatórios, agora ou no futuro.

:::image type="content" source="media/report-separate-from-model/separate-report-files.png" alt-text="Há três arquivos PBIX. O primeiro contém apenas um modelo. Os outros dois contêm apenas relatórios e eles se conectam dinamicamente ao modelo hospedado no serviço do Power BI. Os relatórios são desenvolvidos por pessoas diferentes." border="true":::

Os modeladores de dados ainda podem usar a experiência de criação de relatório do Power BI Desktop para testar e validar seus próprios designs de modelo. No entanto, logo após publicarem o arquivo no serviço do Power BI, eles deverão remover o relatório do workspace. E eles precisam se lembrar de remover o relatório cada vez que republicarem e substituírem o conjunto de dados.

### <a name="preserve-the-model-interface"></a>Preservar a interface do modelo

Às vezes, as alterações de modelo são inevitáveis. Os modeladores de dados precisam tomar cuidado então para não causarem falhas na interface do modelo. Se o fizerem, visuais de relatório ou blocos de dashboard relacionados poderão apresentar falhas. Os visuais com falhas aparecem como erros e podem resultar em frustração para os criadores e consumidores de relatórios. E pior: eles podem reduzir a confiança nos dados.

Portanto, gerencie as alterações aos modelos com cuidado. Se possível, evite as seguintes alterações:

- Renomeação de tabelas, colunas, hierarquias, níveis de hierarquia ou medidas.
- Modificação de tipos de dados de coluna.
- Modificação de expressões de medida para que elas retornem um tipo de dados diferente.
- Mudança de medidas para uma tabela base diferente. Isso ocorre porque mover uma medida pode causar falha em medidas no escopo do relatório que qualificam totalmente as medidas com o respectivo nome de tabela inicial. Não recomendamos que você escreva expressões DAX usando nomes de medidas totalmente qualificados. Para obter mais informações, confira [DAX: referências de coluna e de medida](dax-column-measure-references.md).

Adicionar novas tabelas, colunas, hierarquias, níveis de hierarquia ou medidas é seguro, com uma exceção: É possível que um novo nome de medida possa entrar em conflito com um nome de medida no escopo do relatório. Para evitar o conflito, recomendamos que os autores de relatórios adotem uma convenção de nomenclatura ao definir medidas em seus relatórios. Eles podem prefixar nomes de medidas no escopo do relatório com um sublinhado ou outro caractere.

Se você precisar fazer alterações da falha em seus modelos, recomendamos:

- [Exibir conteúdo relacionado para o conjunto de dados](../consumer/end-user-related.md#view-related-content-for-a-dataset) no serviço do Power BI.
- Explorar a exibição de [Linhagem de dados](../collaborate-share/service-data-lineage.md) no serviço do Power BI.

As duas opções permitem que você identifique rapidamente os relatórios e dashboards relacionados. A exibição de linhagem de dados é provavelmente a melhor opção, porque é fácil ver a pessoa de contato para cada artefato relacionado. Na verdade, trata-se de um hiperlink que abre uma mensagem de email endereçada ao contato.

Recomendamos que você entre em contato com o proprietário de cada artefato relacionado para informá-los sobre eventuais alterações da falha planejadas. Desse modo, eles podem estar preparados e prontos para corrigir e republicar os próprios relatórios, ajudando a minimizar o tempo de inatividade e a frustração.

## <a name="next-steps"></a>Próximas etapas

Para obter mais informações relacionadas a este artigo, confira os seguintes recursos:

- [Conectar-se a conjuntos de dados no serviço do Power BI no Power BI Desktop](../desktop-report-lifecycle-datasets.md)
- [Exibir conteúdo relacionado no serviço do Power BI](../consumer/end-user-related.md)
- [Linhagem de dados](../collaborate-share/service-data-lineage.md)
- Dúvidas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
- Sugestões? [Contribuir com ideias para aprimorar o Power BI](https://ideas.powerbi.com/)
