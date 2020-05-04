---
title: Usar metadados de conjunto de dados avançados no Power BI Desktop (versão prévia)
description: Este artigo descreve como usar metadados aprimorados de conjunto de dados no Power BI.
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 03/31/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 301d6397e4a3ae4498234bae3ad8a49aa7552722
ms.sourcegitcommit: 20f15ee7a11162127e506b86d21e2fff821a4aee
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/29/2020
ms.locfileid: "82584679"
---
# <a name="using-enhanced-dataset-metadata-preview"></a>Usar metadados aprimorados de conjunto de dados (versão prévia)

Quando o Power BI Desktop cria relatórios, ele também cria metadados de conjunto de dados nos arquivos PBIX e PBIT correspondentes. Anteriormente, os metadados eram armazenados em um formato específico para Power BI Desktop. Eles usavam expressões e fontes de dados M codificadas em base 64 e suposições eram feitas sobre como esses metadados eram armazenados.

Com o lançamento do recurso de **metadados aprimorados de conjunto de dados**, muitas dessas limitações foram removidas. Com o recurso **metadados aprimorados de conjunto de dados** habilitado, os metadados criados pelo Power BI Desktop usam um formato semelhante ao usado para modelos tabulares do Analysis Services, com base no [Modelo de Objeto Tabular](https://docs.microsoft.com/bi-reference/tom/introduction-to-the-tabular-object-model-tom-in-analysis-services-amo).


O recurso **metadados aprimorados de conjunto de dados** é estratégico e fundamental, pois a funcionalidade futura do Power BI será criada com base nos metadados dela. Algumas funcionalidades adicionais que têm muito a se beneficiar do recurso metadados aprimorados de conjunto de dados incluem [leitura/gravação XMLA](https://docs.microsoft.com/power-platform-release-plan/2019wave2/business-intelligence/xmla-readwrite) para o gerenciamento de conjuntos de dados do Power BI e a migração de cargas de trabalho do Analysis Services para o Power BI para se beneficiar de recursos da próxima geração.



## <a name="enable-enhanced-dataset-metadata"></a>Habilitar metadados aprimorados de conjunto de dados

O recurso **metadados aprimorados de conjunto de dados** está em versão prévia no momento. Para habilitar os metadados aprimorados de conjunto de dados, no Power BI Desktop, selecione **Arquivo > Opções e configurações > opções > versões prévias dos recursos** e marque a caixa de seleção **Armazenar conjuntos de dados usando o formato de metadados aprimorados**, conforme mostrado na imagem a seguir. 

![Habilitar a versão prévia do recurso](media/desktop-enhanced-dataset-metadata/enhanced-dataset-metadata-01.png)

Você deverá reiniciar o Power BI Desktop.

![Prompt Reiniciar](media/desktop-enhanced-dataset-metadata/enhanced-dataset-metadata-02.png)

Depois que a versão prévia do recurso estiver habilitada, o Power BI Desktop tentará atualizar os arquivos PBIX e PBIT que usam o formato de metadados anterior. 

> [!IMPORTANT]
> Habilitar o recurso **metadados aprimorados de conjunto de dados** resulta em uma atualização irreversível para os relatórios. Todos os relatórios do Power BI carregados ou criados com o Power BI Desktop, depois de habilitados os **metadados aprimorados de conjunto de dados**, são irreversivelmente convertidos no formato aprimorado de metadados do conjunto de dados.

## <a name="considerations-and-limitations"></a>Considerações e limitações

Na versão prévia, as limitações a seguir se aplicam quando o recurso de versão prévia do recurso está habilitado.

### <a name="unsupported-features-and-connectors"></a>Recursos e conectores sem suporte
Ao abrir um arquivo PBIX ou PBIT existente que não foi atualizado, a atualização falhará se o conjunto de dados contiver qualquer um dos recursos ou conectores a seguir. Se essa falha ocorrer, não deverá haver nenhum impacto imediato na experiência do usuário e o Power BI Desktop continuará usando o formato de metadados anterior.

* Scripts do Python
* Conectores personalizados
* Azure DevOps Server
* Conector do BI
* Denodo
* Dremio
* Exasol
* Indexima
* IRIS
* Jethro ODBC
* Kyligence Enterprise
* Mark Logic ODBC
* Qubole Presto
* Team Desk
* Expressões M que contêm determinadas combinações de caracteres, como "\\n" em nomes de colunas
* Ao usar conjuntos de dados com o recurso **metadados aprimorados de conjunto de dados** habilitado, as fontes de dados de SSO (logon único) não podem ser configuradas no serviço do Power BI

Além disso, os arquivos PBIX e PBIT que foram atualizados com êxito para usar os **metadados aprimorados de conjunto de dados** *não podem* usar os recursos ou conectores acima na versão atual.

### <a name="lineage-view"></a>Exibição de linhagem
Atualmente, os conjuntos de dados que usam o novo formato de metadados não mostram links para os fluxos de entrada na exibição de linhagem do serviço do Power BI.

## <a name="next-steps"></a>Próximas etapas

Você pode fazer de tudo com o Power BI Desktop. Para obter mais informações sobre seus recursos, consulte as seguintes fontes:

* [O que é o Power BI Desktop?](desktop-what-is-desktop.md)
* [Novidades no Power BI Desktop](desktop-latest-update.md)
* [Visão geral de consulta com o Power BI Desktop](desktop-query-overview.md)
* [Tipos de dados no Power BI Desktop](desktop-data-types.md)
* [Formatar e combinar dados com o Power BI Desktop](desktop-shape-and-combine-data.md)
* [Tarefas comuns de consulta no Power BI Desktop](desktop-common-query-tasks.md)

