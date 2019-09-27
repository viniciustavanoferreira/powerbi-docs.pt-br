---
title: Práticas recomendadas para fluxos de dados do Power BI
description: Práticas recomendadas para fluxos de dados do Power BI
author: mohaali
manager: mohaali
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 09/19/2019
ms.author: davidi
LocalizationGroup: Data from files
ms.openlocfilehash: c499a83b87eb15031d75974084468f418a17804a
ms.sourcegitcommit: 200291eac5769549ba5c47ef3951e2f3d094426e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71142300"
---
# <a name="dataflows-best-practice"></a>Prática recomendada para fluxos de dados

Este artigo fornece as práticas recomendadas para criação de fluxos de dados no Power BI. Use estas diretrizes para aprender a criar fluxos de dados e aplicar essas práticas a seus próprios fluxos de dados.

> [!NOTE]
> As recomendações deste artigo são orientações. Para cada prática recomendada neste artigo, pode haver motivos legítimos para se desviar das orientações. 
> 
> 

### <a name="split-ingestion-and-transformation-to-use-the-enhanced-compute-engine"></a>Dividir a ingestão e a transformação para usar o mecanismo de computação aprimorado

Ao criar fluxos de dados, você pode ficar tentado a criar um único fluxo de dados com todas as entidades, transformações, junções e aprimoramentos em um só lugar. Para conjuntos de dados menores, um único fluxo de dados pode ser eficaz. Mas, ao lidar com volumes de dados maiores, a execução de junções ou certas transformações pode apresentar restrições ou limitação de memória. Para solucionar esses problemas, lançamos um mecanismo aprimorado para usuários do Power BI Premium que atende a volumes de dados muito maiores. O mecanismo de computação aprimorado funciona apenas em entidades vinculadas ou computadas. Portanto, a criação de um fluxo de dados separado para ingestão e um fluxo de dados vinculado para executar todas as mesclagens e transformações complexas pode se beneficiar do mecanismo aprimorado.

A divisão de fluxos de dados também é benéfica para diagnosticar e depurar problemas de atualização, especialmente ao trabalhar com fontes que têm limites de restrição.

### <a name="perform-actions-that-can-use-the-enhanced-compute-engine"></a>Executar ações que podem usar o mecanismo de computação aprimorado

Assegure a utilização do mecanismo de computação aprimorado garantindo a execução de junções e transformações de filtro primeiro em uma entidade computada antes de executar outros tipos de transformações.

### <a name="split-dataflows-when-connecting-to-sharepoint"></a>Dividir os fluxos de dados ao se conectar ao SharePoint

Ao trabalhar com o SharePoint e se conectar a vários arquivos, você pode notar falhas esporádicas. O SharePoint limita as solicitações para garantir uma operação confiável e responsiva. Como consequência, ao se conectar a arquivos do Excel pelo SharePoint, você pode sentir-se inclinado a baixar todos os arquivos em um único fluxo de dados. Se você estiver baixando muitos arquivos, mais de 20, crie dois fluxos de dados ou mais para dividir a carga de atualização, e superar a limitação do SharePoint.

### <a name="avoid-scheduling-refresh-for-linked-entities-inside-the-same-workspace"></a>Evite a atualização de agendamento de entidades vinculadas dentro do mesmo espaço de trabalho

Se você estiver sendo bloqueado regularmente em seus fluxos de dados que contêm entidades vinculadas, talvez seja resultado do bloqueio do fluxo de dados dependente e correspondente dentro do mesmo espaço de trabalho durante a atualização do fluxo de dados. Esse bloqueio fornece precisão transacional e garante que os dois fluxos de dados sejam atualizados com êxito, mas pode impedir a edição. 

Se você configurar um agendamento separado para o fluxo de dados vinculado, os fluxos de dados poderão ser atualizados desnecessariamente e impedirão a edição do fluxo de dados. Há duas recomendações para evitar esse problema: 

* Evite definir uma agenda de atualização para um fluxo de dados vinculado no mesmo espaço de trabalho que o fluxo de dados de origem
* Se você quiser configurar um agendamento de atualização separadamente, e quiser evitar o comportamento de bloqueio, separe o fluxo de dados em um espaço de trabalho separado.

### <a name="create-a-separate-workspace-for-ingestion-transformation"></a>Criar um espaço de trabalho separado para ingestão e transformação

Para fornecer acesso aos dados do fluxo de dados subjacente a vários usuários, sem permitir acesso aos dados brutos do sistema de origem subjacente, crie um espaço de trabalho separado que tenha todos os dados que você precisa compartilhar e atribua permissões. No momento, não há suporte para permissões de fluxo de dados individual.

### <a name="ensure-capacity-is-in-the-same-region"></a>Verifique se a capacidade está na mesma região

No momento, os fluxos de dados não dão suporte a várias regiões geográficas. A capacidade Premium deve estar na mesma região que seu locatário do Power BI.

### <a name="separate-on-premises-sources-from-cloud-sources"></a>Separar as fontes locais das fontes na nuvem

Além das práticas recomendadas descritas anteriormente, você pode criar um fluxo de dados separado para cada tipo de fonte, como local, na nuvem, SQL Server, Spark, Dynamics e assim por diante. É altamente recomendável dividir o fluxo de dados por tipo de fonte de dados. Essa separação por tipo de origem facilita a solução rápida de problemas e evita limites internos ao atualizar seus fluxos de dados.

### <a name="separate-dataflows-into-a-separate-capacity"></a>Separar os fluxos de dados em uma capacidade separada

Se você estiver enfrentando limites de restrição ou estiver vendo falhas regulares em seus fluxos de dados devido a limites de memória em sua capacidade, considere separar seus fluxos de dados ou escalar verticalmente sua capacidade Premium para obter memória adicional.

## <a name="next-steps"></a>Próximas etapas

Este artigo forneceu informações sobre as práticas recomendadas para fluxos de dados. Confira mais informações úteis sobre fluxos de dados nos artigos a seguir:

* [Preparação de dados de autoatendimento com fluxos de dados](service-dataflows-overview.md)
* [Criação e uso de fluxos de dados no Power BI](service-dataflows-create-use.md)
* [Como usar entidades computadas no Power BI Premium](service-dataflows-computed-entities-premium.md)
* [Como usar fluxos de dados com fontes de dados locais](service-dataflows-on-premises-gateways.md)

Para saber mais sobre o desenvolvimento do CDM e recursos do tutorial, confira o seguinte:
* [Common Data Service - visão geral ](https://docs.microsoft.com/powerapps/common-data-model/overview)
* [Pastas do CDM](https://go.microsoft.com/fwlink/?linkid=2045304)
* [Definição de arquivo de modelo do CDM](https://go.microsoft.com/fwlink/?linkid=2045521)


Confira mais informações sobre o Power Query e a atualização agendada nestes artigos:
* [Visão geral da Consulta no Power BI Desktop](desktop-query-overview.md)
* [Configuração de atualização agendada](refresh-scheduled-refresh.md)
