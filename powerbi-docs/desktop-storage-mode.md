---
title: Usar o modo de armazenamento no Power BI Desktop
description: Use o modo de armazenamento para controlar se os dados são armazenados em cache na memória para relatórios no Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/29/2020
ms.author: davidi
LocalizationGroup: Transform and shape data
ms.openlocfilehash: 6ba03c90e8d0da1b07821001834e04b681e9cc99
ms.sourcegitcommit: 7e845812874b3347bcf87ca642c66bed298b244a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79201299"
---
# <a name="manage-storage-mode-in-power-bi-desktop"></a>Gerenciar o modo de armazenamento no Power BI Desktop

No Microsoft Power BI Desktop, é possível especificar o modo de armazenamento de uma tabela. O modo de armazenamento permite controlar se o Power BI Desktop armazena os dados da tabela em cache na memória para criar relatórios. 

Definir o modo de armazenamento oferece muitas vantagens. Você pode definir o modo de armazenamento de cada tabela individualmente em seu modelo. Essa ação habilita um único conjunto de dados, que fornece os seguintes benefícios:

* **Desempenho de consulta**: conforme os usuários interagem com os visuais nos relatórios do Power BI, as consultas DAX (Data Analysis Expressions) são enviadas para o conjunto de dados. O armazenamento de dados em cache na memória com a configuração adequada do modo de armazenamento pode melhorar o desempenho da consulta e a interatividade dos relatórios.

* **Grandes conjuntos de dados**: tabelas que não estejam armazenadas em cache não consomem memória para fins de cache. Você pode habilitar a análise interativa em conjuntos de dados de grande escala, que são caros ou grandes demais para armazenar completamente em cache na memória. É possível escolher quais tabelas valem a pena ser armazenadas em cache e quais não valem.

* **Otimização de atualização de dados**: não é necessário atualizar tabelas que não estão armazenadas em cache. É possível reduzir os períodos de atualização armazenando em cache apenas os dados necessários para atender aos contratos de nível de serviço e os requisitos empresariais.

* **Requisitos quase em tempo real**: as tabelas com requisitos quase em tempo real podem se beneficiar de não serem armazenadas em cache, para reduzir a latência de dados.

* **Write-back**: o write-back permite que os usuários empresariais explorem cenários hipotéticos alterando os valores das células. Aplicativos personalizados podem aplicar as alterações à fonte de dados. As tabelas não armazenadas em cache podem exibir as alterações de imediato, o que permite análise instantânea dos efeitos.

A definição do modo de armazenamento no Power BI Desktop é um dos três recursos relacionados:

* **Modelos compostos**: permite que um relatório tenha duas ou mais conexões de dados, incluindo conexões DirectQuery ou Importação, em qualquer combinação. Para obter mais informações, confira [Usar modelos compostos no Power BI Desktop](desktop-composite-models.md).

* **Relações muitos-para-muitos**: Com modelos compostos, você pode estabelecer *relações muitos para muitos* entre tabelas. Em uma relação de muitos para muitos, os requisitos são removidos para valores exclusivos nas tabelas. Elas também removem as soluções alternativas anteriores, como introduzir novas tabelas somente para estabelecer relações. Para mais informações, confira [Relações muitos para muitos no Power BI Desktop](desktop-many-to-many-relationships.md).

* **Modo de armazenamento**: com o modo de armazenamento, agora você pode especificar quais visuais exigem uma consulta de fontes de dados de back-end. Visuais que não exigem uma consulta serão importados, mesmo se forem baseados no DirectQuery. Esse recurso ajuda a melhorar o desempenho e reduzir a carga de back-end. Antes, mesmo visuais simples como as segmentações iniciavam consultas enviadas para fontes de back-end. 

## <a name="use-the-storage-mode-property"></a>Usar a propriedade Modo de armazenamento

A propriedade **Modo de armazenamento** pode ser definida em cada tabela de seu modelo e controla como o Power BI armazena em cache os dados da tabela.

Para definir a propriedade **Modo de armazenamento** ou exibir sua configuração atual: 

1. na exibição **Modelo**, selecione a tabela cujas propriedades deseja exibir ou definir. 
2. No painel **Propriedades**, expanda a seção **Avançado** e expanda a lista suspensa **Modo de armazenamento**.

   ![Selecione a propriedade Modo de armazenamento](media/desktop-storage-mode/storage-mode-02.png)

Defina a propriedade **Modo de armazenamento** com um destes três valores:

* **Importação**: as tabelas importadas com essa configuração são armazenadas em cache. As consultas enviadas para o conjunto de dados do Power BI que retornam dados das tabelas de Importação só podem ser atendidas por dados armazenados em cache.

* **DirectQuery**: as tabelas com essa configuração não são armazenadas em cache. As consultas enviadas para o conjunto de dados do Power BI (por exemplo, as consultas DAX) e que retornam dados de tabelas do DirectQuery só podem ser atendidas por meio da execução de consultas sob demanda para a fonte de dados. As consultas enviadas à fonte de dados usam a linguagem de consulta para essa fonte de dados, por exemplo, SQL.

* **Dupla**: tabelas com essa configuração podem se comportar como armazenadas em cache ou não, dependendo do contexto da consulta enviada para o conjunto de dados do Power BI. Em alguns casos, você atende às consultas de dados armazenados em cache. Em outros casos, você atende às consultas executando uma consulta sob demanda para a fonte de dados.

Alterar o **Modo de armazenamento** de uma tabela para **Importação** é uma operação *irreversível*. Após definida, essa propriedade não pode ser alterada para **DirectQuery** ou **Dupla**.

> [!NOTE]
> Você pode usar o modo de armazenamento **Duplo** no Power BI Desktop e no serviço do Power BI.


## <a name="constraints-on-directquery-and-dual-tables"></a>Restrições em tabelas duplas e do DirectQuery

As tabelas duplas têm as mesmas restrições de função que as tabelas DirectQuery. Essas restrições incluem transformações em M limitadas e as funções restritas do DAX em colunas calculadas. Para mais informações, confira [Implicações do uso do DirectQuery](desktop-directquery-about.md#implications-of-using-directquery).

## <a name="propagation-of-the-dual-setting"></a>Propagação da configuração Dupla
Considere o seguinte modelo simples, em que todas as tabelas são de uma única fonte que dá suporte à Importação e DirectQuery.

![Exemplo da exibição de relações para o modo de armazenamento](media/desktop-storage-mode/storage-mode-04.png)

Digamos que, inicialmente, todas as tabelas nesse modelo estejam definidas como **DirectQuery**. Se você alterar o **Modo de armazenamento** da tabela **SurveyResponse** para **Importação**, a seguinte janela de aviso aparecerá:

![Janela de aviso do modo de armazenamento](media/desktop-storage-mode/storage-mode-05.png)

Você pode definir as tabelas de dimensão (**Cliente**, **Geografia** e **Data**) como **Dupla** para reduzir o número de relações fracas no conjunto de dados e aprimorar o desempenho. Normalmente, relações fracas envolvem pelo menos uma tabela do DirectQuery, na qual a lógica de associação não pode ser enviada por push aos sistemas de origem. Como as tabelas Duplas podem atuar como tabelas do DirectQuery ou de Importação, essa situação é evitada.

A lógica de propagação é projetada para ajudar com os modelos que contêm muitas tabelas. Digamos que você tenha um modelo com 50 tabelas e que apenas determinadas tabelas de fatos (transacionais) precisem ser armazenadas em cache. A lógica no Power BI Desktop descobre o conjunto mínimo de tabelas de dimensões que precisa ser definido como **Duplo** para que você não precise fazer isso.

A lógica de propagação percorre somente em direção a um dos lados das relações de um para muitos.

## <a name="storage-mode-usage-example"></a>Exemplo de uso do modo de armazenamento
Continuemos com o exemplo da seção anterior e imaginemos a aplicação das seguintes configurações de propriedade do modo de armazenamento:

| Tabela                   | Modo de armazenamento         |
| ----------------------- |----------------------| 
| Vendas                 | DirectQuery          | 
| SurveyResponse        | Importar               | 
| Data                  | Dupla                 | 
| Cliente              | Dupla                 | 
| Geografia             | Dupla                 | 


Definir essas propriedades do modo de armazenamento resultará nos comportamentos a seguir, supondo que a tabela **Vendas** tenha um volume de dados significativos:
* O Power BI Desktop armazena as tabelas de dimensões (**Data**, **Cliente** e **Geografia**) em cache. Portanto, os tempos de carregamento iniciais do relatório são rápidos ao recuperar os valores de segmentação a serem exibidos.
* O Power BI Desktop não armazena a tabela **Vendas** em cache. Sem armazenar essa tabela em cache, o Power BI Desktop fornece os seguintes resultados:
    * Os tempos de atualização de dados são aprimorados e o consumo de memória é reduzido.
    * Consultas de relatório que se baseiam na tabela **Vendas** são executadas no modo **DirectQuery**. Essas consultas podem levar mais tempo, mas são mais próximas do tempo real, pois nenhuma latência de cache é introduzida.

* As consultas de relatório com base na tabela **SurveyResponse** são retornadas do cache na memória e, portanto, são relativamente rápidas.

## <a name="queries-that-hit-or-miss-the-cache"></a>Consultas que acertam ou erram o cache

Se conectar o SQL Profiler à porta de diagnóstico do Power BI Desktop, você poderá ver quais consultas têm ocorrências ou perdas no cache na memória executando um rastreamento com base nos eventos a seguir:

* Eventos de Consultas\Início da Consulta
* Processamento de Consulta\Início da Consulta Vertipaq SE
* Processamento de Consulta\Início de DirectQuery

Para todo evento *Início da Consulta*, verifique outros eventos com a mesma *ActivityID*. Por exemplo, se não houver nenhum evento *Início de DirectQuery*, mas houver um evento *Início da Consulta Vertipaq SE*, a consulta será atendida pelo cache.

As consultas que fizerem referência às tabelas Duplas retornarão dados do cache, se possível; caso contrário, serão revertidas para o DirectQuery.

Seguindo com o exemplo anterior, a consulta a seguir se refere apenas a uma coluna da tabela **Data**, que está no modo **Duplo**. Portanto, a consulta deve ter uma ocorrência no cache:

![Script para diagnóstico do modo de armazenamento](media/desktop-storage-mode/storage-mode-06.png)

A consulta a seguir se refere apenas a uma coluna da tabela **Vendas**, que está no modo **DirectQuery**. Portanto, ela *não* deve ter uma ocorrência no cache:

![Script para diagnóstico do modo de armazenamento](media/desktop-storage-mode/storage-mode-07.png)

A consulta a seguir é interessante porque combina as duas colunas. Esta consulta não tem ocorrência no cache. Inicialmente, você pode esperar que ela recupere os valores **CalendarYear** do cache e os valores **SalesAmount** da fonte e depois combine os resultados, mas isso seria uma abordagem menos eficiente do que enviar a operação SUM/GROUP BY para o sistema de origem. Se a operação for propagada para a fonte, o número de linhas retornadas provavelmente será muito menor: 

![Script para diagnóstico do modo de armazenamento](media/desktop-storage-mode/storage-mode-08.png)

> [!NOTE]
> Esse comportamento é diferente das [relações de muitos para muitos](desktop-many-to-many-relationships.md) no Power BI Desktop ao combinar tabelas armazenadas e não armazenadas em cache.

## <a name="caches-should-be-kept-in-sync"></a>Os caches devem ser mantidos em sincronia

As consultas exibidas na seção anterior mostram que as tabelas Duplas às vezes têm ocorrências no cache e outras vezes não. Como resultado, se o cache estiver desatualizado, diferentes valores poderão ser retornados. A execução da consulta não tenta ocultar os problemas de dados, filtrando, por exemplo, os resultados de DirectQuery para coincidir com os valores armazenados em cache. É sua responsabilidade conhecer seus fluxos de dados, e o projeto deve ser feito de acordo com isso. Existem técnicas estabelecidas para lidar com tais casos na origem, se necessário.

O modo de armazenamento **Duplo** é uma otimização de desempenho. Ele só deve ser usado de maneira a não comprometer a capacidade de atender aos requisitos empresariais. Para um comportamento alternativo, considere o uso das técnicas descritas em [Relações muitos para muitos no Power BI Desktop](desktop-many-to-many-relationships.md).

## <a name="data-view"></a>Exibição de dados
Se pelo menos uma tabela no conjunto de dados tiver o modo de armazenamento definido como **Importação** ou **Duplo**, a exibição **Dados** poderá ser exibida.

![Exibição de dados no Power BI Desktop](media/desktop-storage-mode/storage-mode-03.png)

Quando você seleciona tabelas Duplas e de Importação na exibição de **Dados**, elas mostram dados armazenados em cache. As tabelas do DirectQuery não mostram dados e é exibida uma mensagem informando que elas não podem ser mostradas.


## <a name="limitations-and-considerations"></a>Limitações e considerações

Existem algumas limitações para esta versão do modo de armazenamento e sua correlação com os modelos compostos.

As seguintes fontes de conexão dinâmica (multidimensionais) não podem ser usadas com os modelos compostos:

* SAP HANA
* SAP Business Warehouse
* SQL Server Analysis Services
* Conjuntos de dados do Power BI
* Azure Analysis Services

Ao se conectar a essas fontes multidimensionais usando o DirectQuery, não é possível se conectar também a outra fonte do DirectQuery, nem a combinar com os dados importados.

As limitações existentes no uso do DirectQuery ainda se aplicam ao usar modelos compostos. Muitas dessas limitações agora são por tabela, dependendo do modo de armazenamento da tabela. Por exemplo, uma coluna calculada em uma tabela importada pode se referir a outras tabelas, mas uma coluna calculada em uma tabela do DirectQuery ainda fica restrita para se referir apenas às colunas na mesma tabela. Outras limitações se aplicam ao modelo como um todo se quaisquer das tabelas no modelo forem DirectQuery. Por exemplo, os recursos QuickInsights e P e R não estarão disponíveis em um modelo se qualquer uma das tabelas nele tiver um modo de armazenamento do DirectQuery. 

## <a name="next-steps"></a>Próximas etapas

Para obter mais informações sobre modelos compostos e DirectQuery, confira os seguintes artigos:
* [Modelos compostos no Power BI Desktop](desktop-composite-models.md)
* [Relações muitos para muitos no Power BI Desktop](desktop-many-to-many-relationships.md)
* [Usar DirectQuery no Power BI](desktop-directquery-about.md)
* [Fontes de dados com suporte do DirectQuery no Power BI](desktop-directquery-data-sources.md)
