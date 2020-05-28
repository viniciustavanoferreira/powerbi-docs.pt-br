---
title: Usar o DirectQuery com fluxos de dados no Power BI (versão prévia)
description: Saiba como usar o DirectQuery com fluxos de dados no Power BI
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/19/2020
ms.author: davidi
LocalizationGroup: Data from files
ms.openlocfilehash: 9de8c9611b24eaa627b3ddf044f13d36d7b9a3d4
ms.sourcegitcommit: 250242fd6346b60b0eda7a314944363c0bacaca8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83694563"
---
# <a name="use-directquery-with-dataflows-in-power-bi-preview"></a>Usar o DirectQuery com fluxos de dados no Power BI (versão prévia)

Você pode usar o DirectQuery para se conectar diretamente aos fluxos de dados e, portanto, conectar-se diretamente ao seu fluxo de dados sem ter que importar os respectivos dados. 

O uso do DirectQuery com fluxos de dados permite os seguintes aprimoramentos aos seus processos de Power BI e de fluxo de dados:

* **Evitar agendas de atualização separadas** – o DirectQuery se conecta diretamente a um fluxo de dados, eliminando a necessidade de criar um conjunto de dados. Dessa forma, o uso do DirectQuery com seus fluxos de dados significa que não há mais necessidade de agendar atualizações separadamente para o fluxo de dados e o conjunto de dados a fim de garantir que os dados fiquem sincronizados.

* **Filtragem de dados** – o DirectQuery é útil para trabalhar em uma exibição filtrada de dados dentro de um fluxo de dados. Se você quiser filtrar os dados e, portanto, trabalhar com um subconjunto menor dos dados em seu fluxo de dados, poderá usar o DirectQuery (e o mecanismo de computação) para filtrar os dados do fluxo de dados e trabalhar com o subconjunto filtrado de que precisar.


## <a name="using-directquery-for-dataflows"></a>Usar o DirectQuery para fluxos de dados

O uso do DirectQuery com fluxos de dados de entrada é uma versão prévia do recurso disponível começando com a versão de maio de 2020 do Power BI Desktop. 

Também há pré-requisitos para usar o DirectQuery com fluxos de dados:

* O fluxo de dados precisa residir em um workspace habilitado para o Power BI Premium
* O **mecanismo de computação** precisa estar ativado. Para obter mais informações sobre o mecanismo de computação, confira [o mecanismo de computação aprimorado](service-dataflows-enhanced-compute-engine.md).

## <a name="enable-directquery-for-dataflows"></a>Habilitar o DirectQuery para fluxos de dados

Para garantir que o fluxo de dados esteja disponível para acesso pelo DirectQuery, o mecanismo de computação aprimorado precisa estar em seu estado otimizado. Para habilitar o DirectQuery para fluxos de dados, defina a nova opção **Configurações aprimoradas do mecanismo de computação** para **Otimizado**. A imagem a seguir mostra a configuração selecionada corretamente.

![Habilitar o mecanismo de computação aprimorado para fluxos de dados](media/service-dataflows-directquery/dataflows-directquery-01.png)

Depois de aplicar essa configuração, atualize o fluxo de dados para que a otimização entre em vigor. 


## <a name="considerations-and-limitations"></a>Considerações e limitações

Existem algumas limitações conhecidas com o DirectQuery e os fluxos de dados, que são explicadas na lista a seguir.

* O DirectQuery para fluxos de dados não funciona com a **versão prévia do recurso de metadados aprimorados** habilitada. Espera-se que essa exclusão seja removida em uma versão mensal futura do Power BI Desktop.
* Durante o período de versão prévia desse recurso, alguns clientes podem enfrentar problemas de tempo limite ou de desempenho ao usar o DirectQuery com fluxos de dados. Esses problemas estão sendo resolvidos ativamente durante esse período de versão prévia.


## <a name="next-steps"></a>Próximas etapas

Os artigos a seguir são úteis para ver cenários e obter mais informações ao usar fluxos de dados:

* [Preparação de dados de autoatendimento com fluxos de dados](service-dataflows-overview.md)
* [Como usar entidades computadas no Power BI Premium](service-dataflows-computed-entities-premium.md)
* [Como usar fluxos de dados com fontes de dados locais](service-dataflows-on-premises-gateways.md)
* [Recursos de desenvolvedor para fluxos de dados do Power BI](service-dataflows-developer-resources.md)
* [Integração entre fluxos de dados e o Azure Data Lake (versão prévia)](service-dataflows-azure-data-lake-integration.md)

Leia este artigo de visão geral para saber mais sobre o Common Data Service:
* [Common Data Service - visão geral ](https://docs.microsoft.com/powerapps/common-data-model/overview)
* [Saiba mais sobre o esquema Common Data Service e entidades no GitHub](https://github.com/Microsoft/CDM)

Artigos relacionados do Power BI Desktop:

* [Conectar-se a conjuntos de dados no serviço do Power BI no Power BI Desktop](../connect-data/desktop-report-lifecycle-datasets.md)
* [Visão geral da Consulta no Power BI Desktop](desktop-query-overview.md)

Artigos relacionados do serviço Power BI:
* [Configuração de atualização agendada](../connect-data/refresh-scheduled-refresh.md)
