---
title: Usar metadados de conjunto de dados avançados no Power BI Desktop (versão prévia)
description: Este artigo descreve como usar metadados aprimorados de conjunto de dados no Power BI.
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/11/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 0a09311c5fdb1a8b2e008996d993015f33ee9b5f
ms.sourcegitcommit: a07fa723bb459494c60cf6d749b4554af723482a
ms.contentlocale: pt-BR
ms.lasthandoff: 06/12/2020
ms.locfileid: "84739243"
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

## <a name="report-backup-files"></a>Arquivos de backup de relatório

A atualização de um relatório para usar o recurso **metadados de conjunto de dados aprimorados** é irreversível. No entanto, durante a atualização, um arquivo de backup de relatório é criado para salvar uma versão do relatório em seu formato original (pré-atualização). O arquivo de backup é removido após 30 dias. 

Para localizar o arquivo de relatório de backup, faça o seguinte:

1. Navegue até o seguinte local: ```C:\Users\<user>\AppData\Local\Microsoft\Power BI Desktop\TempSaves\Backup```. Se estiver usando a versão Microsoft Store do Power BI Desktop, use o seguinte local: ```C:\Users\<user>\Microsoft\Power BI Desktop Store App\TempSaves\Backups``` 

2. Localize uma cópia do relatório com o nome e o carimbo de data/hora do arquivo original.

3. Copie o arquivo para um local que você preferir, para preservá-lo.

4. Verifique se a versão prévia do recurso do **formato de metadados aprimorados** está desabilitada no Power BI Desktop se você optar por abrir ou usar esse arquivo original. 

O arquivo de backup é criado quando o relatório é atualizado, portanto, as alterações feitas após a atualização não são incluídas. Novos relatórios criados quando o recurso do **formato de metadados aprimorados** está habilitado não têm um arquivo de backup.


## <a name="considerations-and-limitations"></a>Considerações e limitações

Na versão prévia, as limitações a seguir se aplicam quando o recurso de versão prévia do recurso está habilitado.

### <a name="unsupported-features-and-connectors"></a>Recursos e conectores sem suporte

As seguintes limitações se aplicam:

Ao abrir um arquivo PBIX ou PBIT existente que não foi atualizado, a atualização falhará se o conjunto de dados contiver qualquer um dos recursos ou conectores a seguir. Se essa falha ocorrer, não deverá haver nenhum impacto imediato na experiência do usuário e o Power BI Desktop continuará usando o formato de metadados anterior.

* Todos os conectores personalizados (limitação de versão de maio de 2020)
* Scripts do Python
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

Se você estiver usando a versão do Power BI Desktop de **junho de 2020** (ou posterior), *haverá* suporte para todos os conectores personalizados e internos no Power BI Desktop e no serviço do Power BI. Durante o processo de publicação ao usar a versão de junho de 2020 ou posterior, se o gateway encontrar problemas, o conjunto de dados será publicado com êxito, mas os usuários deverão republicar o relatório para atualizar os dados. A caixa de diálogo **Configurações de fonte de dados** é o único indicador de que ocorreram problemas com o processo de publicação.

Relatórios que usam conectores ou recursos sem suporte não serão atualizados para o novo formato. Os relatórios que já foram atualizados ou criados após a habilitação desse novo recurso não darão suporte à adição de conectores ou recursos sem suporte listados. 

Não há suporte para consultas com fontes de dados dinâmicas. Os relatórios com fontes de dados dinâmicas não serão atualizados para o novo formato e os relatórios que já foram atualizados ou criados recentemente com o recurso habilitado não darão suporte à adição de fontes de dados dinâmicas. Uma consulta terá uma fonte de dados dinâmica se a fonte for alterada dependendo de um parâmetro, entrada de função ou função volátil. 

Não há suporte para consultas com erros em etapas de upstream ou ramificações. 

Além disso, os arquivos PBIX e PBIT que já foram atualizados com êxito para usar **metadados aprimorados de conjunto de dados** *não podem* usar os recursos acima (ou conectores sem suporte).

### <a name="lineage-view"></a>Exibição de linhagem
Atualmente, os conjuntos de dados que usam o novo formato de metadados não mostram links para os fluxos de entrada na exibição de linhagem do serviço do Power BI.

## <a name="next-steps"></a>Próximas etapas

Você pode fazer de tudo com o Power BI Desktop. Para obter mais informações sobre seus recursos, consulte as seguintes fontes:

* [O que é o Power BI Desktop?](../fundamentals/desktop-what-is-desktop.md)
* [Novidades no Power BI Desktop](../fundamentals/desktop-latest-update.md)
* [Visão geral de consulta com o Power BI Desktop](../transform-model/desktop-query-overview.md)
* [Tipos de dados no Power BI Desktop](desktop-data-types.md)
* [Formatar e combinar dados com o Power BI Desktop](desktop-shape-and-combine-data.md)
* [Tarefas comuns de consulta no Power BI Desktop](../transform-model/desktop-common-query-tasks.md)
