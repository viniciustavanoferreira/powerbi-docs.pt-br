---
title: Usar o DirectQuery no Power BI Desktop
description: Use o DirectQuery, também chamado de Conexão dinâmica, no Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 02/13/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: d8432ae10afab6cbf12c017a8f315fd55825212d
ms.sourcegitcommit: d6a48e6f6e3449820b5ca03638b11c55f4e9319c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/18/2020
ms.locfileid: "77427221"
---
# <a name="use-directquery-in-power-bi-desktop"></a>Usar o DirectQuery no Power BI Desktop
Com o *Power BI Desktop*, quando você se conecta à sua fonte de dados, sempre é possível importar uma cópia dos dados para o Power BI Desktop. Para algumas fontes de dados, uma abordagem alternativa está disponível: conectar-se diretamente à fonte de dados usando o DirectQuery.

## <a name="supported-data-sources"></a>Fontes de dados com suporte
Para obter uma listagem completa das fontes de dados que dão suporte ao DirectQuery, confira [Fontes de dados compatíveis com o DirectQuery](power-bi-data-sources.md).

## <a name="how-to-connect-using-directquery"></a>Como se conectar usando o DirectQuery
Quando você usa **Obter Dados** para se conectar a uma fonte de dados compatível com o DirectQuery, a caixa de diálogo de conexão permite que você selecione como deseja se conectar. Por exemplo, no Power BI Desktop, na faixa de opções **Página Inicial**, selecione **Obter Dados** > **SQL Server**. Na caixa de diálogo **Banco de Dados do SQL Server**, o **modo de Conectividade de Dados** mostra as opções **Importar** e **DirectQuery**:

![Opções Importar e DirectQuery, caixa de diálogo Banco de Dados do SQL Server, Power BI Desktop](media/desktop-use-directquery/directquery_sqlserverdb.png)

Estas são as diferenças entre a seleção de **Importar** e **DirectQuery**:

- **Importação**: as tabelas e as colunas selecionadas são importadas para o Power BI Desktop. Conforme você cria ou interage com uma visualização, o Power BI Desktop usa os dados importados. Para ver todas as alterações de dados subjacentes ocorridas desde a importação inicial ou a atualização mais recente, atualize os dados, o que importará o conjunto de dados completo novamente.

- **DirectQuery**: nenhum dado é importado ou copiado para o Power BI Desktop. Para fontes relacionais, as tabelas e colunas selecionadas aparecem na lista **Campos**. Para fontes multidimensionais, como SAP Business Warehouse, as dimensões e medidas do cubo selecionado aparecem na lista **Campos**. Conforme você cria uma visualização ou interage com ela, o Power BI Desktop consulta a fonte de dados subjacente, de modo que você sempre esteja vendo dados atuais.

Muitas transformações e modelagem de dados estão disponíveis ao usar o DirectQuery, embora com algumas limitações. Ao criar uma visualização ou interagir com ela, consulte a fonte subjacente. O tempo necessário para atualizar a visualização depende do desempenho da fonte de dados subjacente. Quando os dados necessários para atender à solicitação foram solicitados recentemente, o Power BI Desktop usa os dados recentes para reduzir o tempo necessário para mostrar a visualização. Se você selecionar **Atualizar** na faixa de opções **Página Inicial**, todas as visualizações serão atualizadas com os dados atuais.

O artigo [Power BI e DirectQuery](desktop-directquery-about.md) descreve o DirectQuery em detalhes. Para obter mais informações sobre benefícios, limitações e considerações importantes ao usar o DirectQuery, confira as seções a seguir.

## <a name="benefits-of-using-directquery"></a>Benefícios do uso do DirectQuery
Há alguns benefícios no uso do DirectQuery:

- O DirectQuery permite criar visualizações de conjuntos de dados muito grandes, nos casos em que, de outro modo, seria impraticável importar primeiro todos os dados com pré-agregação.
- As alterações de dados subjacentes podem exigir uma atualização dos dados. Para alguns relatórios, a necessidade de exibir dados atuais pode exigir transferências de dados grandes, tornando a reimportação de dados impraticável. Por outro lado, os relatórios do DirectQuery sempre usam dados atuais.
- A limitação do conjunto de dados de 1 GB *não* se aplica ao DirectQuery.

## <a name="limitations-of-directquery"></a>Limitações do DirectQuery
Atualmente, há algumas limitações no uso do DirectQuery:

- Se a consulta do **Editor de Consultas** for excessivamente complexa, ocorrerá um erro. Para corrigir o erro, exclua a etapa que apresenta problemas no **Editor de Consultas** ou *importe* os dados, em vez de usar o DirectQuery. Para fontes multidimensionais, como o SAP Business Warehouse, não há nenhum **Editor de Consultas**.

- As funcionalidades de inteligência de dados temporais não estão disponíveis no DirectQuery. Por exemplo, não há suporte ao tratamento especial de colunas de data (como ano, trimestre, mês ou dia) no modo DirectQuery.

- As limitações são colocadas em expressões DAX permitidas em medidas para garantir que as consultas enviadas à fonte de dados subjacente tenham um desempenho aceitável.

- Há um limite de um milhão de linhas para retornar dados ao usar o DirectQuery, a menos que você use a capacidade Premium. O limite não afeta as agregações nem os cálculos usados para criar o conjunto de dados retornado com o DirectQuery. Ele só afeta as linhas retornadas. As capacidades Premium podem definir limites máximos de linha, como descrito [nesta postagem](https://powerbi.microsoft.com/blog/five-new-power-bi-premium-capacity-settings-is-available-on-the-portal-preloaded-with-default-values-admin-can-review-and-override-the-defaults-with-their-preference-to-better-fence-their-capacity/). 

    Por exemplo, você pode agregar 10 milhões de linhas com a consulta que é executada na fonte de dados. A consulta retornará com precisão os resultados dessa agregação para o Power BI usando o DirectQuery se os dados retornados do Power BI forem inferiores a 1 milhão de linhas. Se mais de 1 milhão linhas forem retornadas do DirectQuery, Power BI retornará um erro (exceto na capacidade Premium e se a contagem de linhas estiver abaixo do limite definido pelo administrador).

## <a name="important-considerations-when-using-directquery"></a>Considerações importantes ao usar o DirectQuery
Os três seguintes pontos devem ser levados em consideração ao usar o DirectQuery:

- **Desempenho e carga**: todas as solicitações do DirectQuery são enviadas ao banco de dados de origem e, portanto, o tempo necessário para atualizar um visual depende de quanto tempo essa fonte de back-end leva para fornecer uma resposta com os resultados das consultas. Cinco segundos ou menos é o tempo de resposta recomendado (com os dados solicitados sendo retornados) para uso do DirectQuery em visuais; o tempo recomendado máximo é de 30 segundos. Se levar mais, e a experiência de um usuário consumindo o relatório se tornará muito ruim. Depois que um relatório for publicado no serviço do Power BI, qualquer consulta que levar mais tempo do que alguns minutos atingirá o tempo limite e o usuário receberá um erro.
  
    Carregar o banco de dados de origem também deve ser considerado, com base no número de usuários do Power BI que consumirá o relatório publicado. O uso da RLS (**Segurança em Nível de Linha**) também pode ter um impacto significativo. Um bloco de dashboard não RLS compartilhado por vários usuários resulta em uma só consulta ao banco de dados. No entanto, o uso da RLS em um bloco de dashboard geralmente significa que a atualização de um bloco exige uma consulta *por usuário*, aumentando de maneira significativa a carga no banco de dados de origem e potencialmente afetando o desempenho.
  
    O Power BI cria consultas que são tão eficientes quanto possível. Em determinadas situações, no entanto, a consulta gerada pode não ser eficiente o suficiente para evitar uma falha na atualização. Um exemplo dessa situação é quando uma consulta gerada recupera um número excessivamente grande de linhas da fonte de dados de back-end. Nesse caso, ocorre o seguinte erro:

    ```output
    The resultset of a query to external data source has exceeded
    ```
  
    Essa situação pode ocorrer com um gráfico simples que inclui uma coluna de cardinalidade muito alta, com a opção de agregação definida como **Não resumir**. O visual precisa ter somente colunas com uma cardinalidade abaixo de 1 milhão ou precisa aplicar os filtros apropriados.

- **Segurança**: por padrão, todos os usuários que consomem um relatório publicado conectam-se à fonte de dados de back-end usando as credenciais inseridas após a publicação no serviço do Power BI. Esse processo é o mesmo para dados importados: todos os usuários veem os mesmos dados, independentemente das regras de segurança definidas na fonte de back-end.

    Os clientes que desejam implementar a segurança por usuário com as fontes do DirectQuery devem usar a RLS ou configurar a autenticação restrita ao Kerberos na fonte. O Kerberos não está disponível para todas as fontes. [Saiba mais sobre a RLS](service-admin-rls.md). [Saiba mais sobre o Kerberos no DirectQuery](service-gateway-sso-kerberos.md).

- **Recursos compatíveis**: Alguns recursos do Power BI Desktop não são compatíveis com o modo DirectQuery ou têm limitações. Além disso, algumas funcionalidades do serviço do Power BI (como *Insights Rápidos*) não estão disponíveis para conjuntos de dados que usam o DirectQuery. Ao determinar se o DirectQuery deve ser usado, considere essas limitações de recursos.

## <a name="publish-to-the-power-bi-service"></a>Publicar no serviço do Power BI
Os relatórios criados com o DirectQuery podem ser publicados no serviço do Power BI.

Se a fonte de dados usada não precisar do **gateway de dados local** (**Banco de Dados SQL do Azure**, **SQL Data Warehouse do Azure** ou **Redshift**), você precisará fornecer as credenciais antes que o serviço do Power BI mostre o relatório publicado. Siga estas instruções para fornecer as credenciais:

1. Entre no [Power BI](https://www.powerbi.com/).
2. No serviço do Power BI, selecione o ícone de engrenagem de **Configurações** e escolha o item de menu **Configurações**.

    ![Configurações, serviço do Power BI](media/desktop-use-directquery/directquery_pbiservicesettings.png)

3. Na página **Configurações** do serviço do Power BI, selecione a guia **Conjuntos de dados**, escolha o conjunto de dados que usa o DirectQuery e selecione **Editar credenciais**.

4. Adicione as credenciais. Caso contrário, ocorrerá um erro quando você abrir um relatório publicado ou explorar um conjunto de dados criado com uma conexão do DirectQuery.

Para fazer uma conexão de dados para fontes de dados que não sejam o **Banco de Dados SQL do Azure**, o **SQL Data Warehouse do Azure**, o **Redshift** ou o **Snowflake Data Warehouse** que usem o DirectQuery, instale um **Gateway de dados local** e registre a fonte de dados. Para obter mais informações, confira [O que é um gateway de dados local?](service-gateway-onprem.md)

## <a name="next-steps"></a>Próximas etapas
Para obter mais informações sobre o DirectQuery, confira os seguintes recursos:

- [Usar o DirectQuery no Power BI](desktop-directquery-about.md)
- [Fontes de dados com suporte do DirectQuery](power-bi-data-sources.md)
- [DirectQuery e SAP BW (Business Warehouse)](desktop-directquery-sap-bw.md)
- [DirectQuery e SAP HANA](desktop-directquery-sap-hana.md)
- [O que é um gateway de dados local?](service-gateway-onprem.md)
