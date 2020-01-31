---
title: Segurança em nível de linha dinâmica com o modelo de tabela do Analysis Services
description: Segurança em nível de linha dinâmica com o modelo de tabela do Analysis Services
author: davidiseminger
ms.reviewer: davidi
editor: davidi
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: tutorial
ms.date: 01/17/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 1b90357aa6d8f66612857e8247a8b48dc2c2c369
ms.sourcegitcommit: 02342150eeab52b13a37b7725900eaf84de912bc
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2020
ms.locfileid: "76539549"
---
# <a name="implement-row-level-security-in-an-analysis-services-tabular-model"></a>Implementar segurança em nível de linha em um modelo de tabela do Analysis Services

Usando um conjunto de dados de exemplo para trabalhar com as etapas abaixo, este tutorial mostra como implementar a [**segurança em nível de linha**](service-admin-rls.md) em um *Modelo Tabular do Analysis Services* e usá-lo em um relatório do Power BI.

* Crie uma tabela de segurança no banco de dados [AdventureworksDW2012](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)
* Criar o modelo de tabela com as tabelas de fatos e dimensões necessárias
* Definir as permissões e as funções de usuário
* Implantar o modelo em uma instância da *tabela do Analysis Services*
* Criar um relatório do Power BI Desktop que mostra dados personalizados ao usuário que está acessando o relatório
* Implantar o relatório no *serviço do Power BI*
* Criar um novo dashboard baseado no relatório
* Compartilhar o dashboard com seus colegas

Este tutorial requer o banco de dados [AdventureworksDW2012](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks).

## <a name="task-1-create-the-user-security-table-and-define-data-relationship"></a>Tarefa 1: criar a tabela de segurança de usuário e definir a relação de dados

Há vários artigos publicados que descrevem como definir a segurança dinâmica em nível de linha com o modelo *tabular do SSAS (SQL Server Analysis Services)* . Para nossa amostra, usamos [Implementar a segurança dinâmica usando filtros de linha](/analysis-services/tutorial-tabular-1200/supplemental-lesson-implement-dynamic-security-by-using-row-filters).

Estas etapas exigem o uso do banco de dados relacional AdventureworksDW2012.

1. No AdventureworksDW2012, crie a tabela `DimUserSecurity` conforme mostrado abaixo. É possível usar o [SSMS (SQL Server Management Studio)](/sql/ssms/download-sql-server-management-studio-ssms) para criar a tabela.

   ![Criar tabela DimUserSecurity](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/createusersecuritytable.png)

1. Depois de criar e salvar a tabela, você precisa estabelecer a relação entre a coluna `SalesTerritoryID` da tabela de `DimUserSecurity` e a coluna `SalesTerritoryKey` da tabela `DimSalesTerritory`, conforme mostrado abaixo.

   No SSMS, clique com o botão direito do mouse em **DimUserSecurity** e selecione **Design**. Em seguida, selecione **Designer de Tabela** > **Relações...** . Quando terminar, salve a tabela.

   ![Relações de Chaves Estrangeiras](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/createusersecuritytable_keys.png)

1. Adicione usuários à tabela. Clique com o botão direito do mouse em **DimUserSecurity** e selecione **Editar as 200 Primeiras Linhas**. Depois de adicionar os usuários, a tabela `DimUserSecurity` deve ser semelhante ao seguinte exemplo:

   ![Tabela DimUserSecurity com usuários de exemplo](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/createusersecuritytable_users.png)

   Você verá esses usuários em tarefas futuras.

1. Em seguida, faça uma *junção interna* com a tabela `DimSalesTerritory`, que mostra os detalhes da região associados ao usuário. O código SQL aqui faz a junção interna e a imagem mostra como a tabela é exibida.

    ```sql
    select b.SalesTerritoryCountry, b.SalesTerritoryRegion, a.EmployeeID, a.FirstName, a.LastName, a.UserName from [dbo].[DimUserSecurity] as a join [dbo].[DimSalesTerritory] as b on a.[SalesTerritoryID] = b.[SalesTerritoryKey]
    ```

   A tabela unida mostra quem responsável por cada região de vendas, graças à relação criada na etapa 2. Por exemplo, você pode ver que *Rita Santos* é responsável pela *Austrália*.

## <a name="task-2-create-the-tabular-model-with-facts-and-dimension-tables"></a>Tarefa 2: criar o modelo de tabela com tabelas de fatos e dimensão

Depois de implementar o data warehouse relacional, será necessário definir o modelo tabular. É possível criar o modelo usando o [SSDT (SQL Server Data Tools)](/sql/ssdt/sql-server-data-tools). Para obter mais informações, confira [Criar um novo projeto de modelo tabular](/sql/analysis-services/lesson-1-create-a-new-tabular-model-project).

1. Importe todas as tabelas necessárias no modelo, conforme mostrado abaixo.

    ![SQL Server importado para uso com ferramentas de dados](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/ssdt_model.png)

1. Depois de importar as tabelas necessárias, você precisa definir uma função chamada *SalesTerritoryUsers* com a permissão Leitura. Selecione o menu **Modelo** no SQL Server Data Tools e, em seguida, selecione **Funções**. No **Gerenciador de Funções**, selecione **Novo**.

1. Em **Membros** no **Gerenciador de Funções**, adicione os usuários que você definiu na tabela `DimUserSecurity` na [Tarefa 1](#task-1-create-the-user-security-table-and-define-data-relationship).

    ![Adicionar usuários no Gerenciador de Funções](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/rolemanager.png)

1. Em seguida, adicione as funções apropriadas às tabelas `DimSalesTerritory` e `DimUserSecurity`, conforme mostrado abaixo na guia **Filtros de Linha**.

    ![Adicionar funções a Filtros de Linha](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/rolemanager_complete.png)

1. A função `LOOKUPVALUE` retorna valores para uma coluna na qual o nome de usuário do Windows corresponde ao que a função `USERNAME` retorna. Em seguida, você pode restringir as consultas para as quais os valores retornados de `LOOKUPVALUE` correspondem aos da mesma tabela ou da tabela relacionada. Na coluna **Filtro DAX**, digite a seguinte fórmula:

    ```sql
        =DimSalesTerritory[SalesTerritoryKey]=LOOKUPVALUE(DimUserSecurity[SalesTerritoryID], DimUserSecurity[UserName], USERNAME(), DimUserSecurity[SalesTerritoryID], DimSalesTerritory[SalesTerritoryKey])
    ```

    Nesta fórmula, a função `LOOKUPVALUE` retorna todos os valores para a coluna `DimUserSecurity[SalesTerritoryID]`, em que o `DimUserSecurity[UserName]` é igual ao nome de usuário do Windows conectado no momento e `DimUserSecurity[SalesTerritoryID]` é igual a `DimSalesTerritory[SalesTerritoryKey]`.

    > [!IMPORTANT]
    > Ao usar a segurança em nível de linha, a função DAX [USERELATIONSHIP](/dax/userelationship-function-dax) não é compatível.

   O conjunto de retornos `LOOKUPVALUE` de `SalesTerritoryKey` de vendas é usado para restringir as linhas mostradas no `DimSalesTerritory`. Somente as linhas em que o valor `SalesTerritoryKey` está nas IDs que a função `LOOKUPVALUE` retorna são exibidas.

1. Para a tabela `DimUserSecurity`, na coluna **Filtro DAX**, adicione a seguinte fórmula:

    ```sql
        =FALSE()
    ```

    Essa fórmula especifica que todas as colunas são resolvidas para `false`. Ou seja, as colunas da tabela `DimUserSecurity` não podem ser consultadas.

Agora, é necessário processar e implantar o modelo. Para saber mais, confira [Implantar](/sql/analysis-services/lesson-13-deploy).

## <a name="task-3-add-data-sources-within-your-on-premises-data-gateway"></a>Tarefa 3: adicionar fontes de dados ao Gateway de dados local

Depois que o modelo tabular for implantado e estiver pronto para consumo, você precisará adicionar uma conexão de fonte de dados ao servidor tabular do Analysis Services local.

1. Para permitir que o serviço do Power BI acesse o serviço de análise local, é necessário ter um [gateway de dados local](service-gateway-onprem.md) instalado e configurado no seu ambiente.

1. Depois de configurar o gateway corretamente, é necessário criar uma conexão de fonte de dados à instância de tabela do *Analysis Services*. Para mais informações, confira [Gerenciar sua fonte de dados – Analysis Services](service-gateway-enterprise-manage-ssas.md).

   ![Criar conexão de fonte de dados](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/pbi_gateway.png)

Após a conclusão desse procedimento, o gateway está configurado e pronto para interagir com sua fonte de dados do Analysis Services local.

## <a name="task-4-create-report-based-on-analysis-services-tabular-model-using-power-bi-desktop"></a>Tarefa 4: criar relatórios baseados no modelo tabular do Analysis Services usando o Power BI Desktop

1. Inicie o Power BI Desktop e selecione **Obter Dados** > **Banco de Dados**.

1. Na lista de fontes de dados, selecione o **Banco de Dados do SQL Server Analysis Services** e selecione **Conectar**.

   ![Conectar-se ao banco de dados do SQL Server Analysis Services](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/getdata.png)

1. Preencha os detalhes da instância de tabela do Analysis Services e selecione **Conexão dinâmica**. Selecione **OK**.
  
   ![Detalhes do Analysis Services](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/getdata_connectlive.png)

   Com o Power BI, a segurança dinâmica funciona apenas com uma conexão dinâmica.

1. Você pode ver que o modelo implantado está na instância do Analysis Services. Selecione o respectivo modelo e selecione **OK**.

   Agora, o Power BI Desktop exibe todos os campos disponíveis à direita da tela no painel **Campos**.

1. No painel **Campos**, selecione a medida **SalesAmount** na tabela **FactInternetSales** e a dimensão **SalesTerritoryRegion** na tabela **SalesTerritory**.

1. Para manter esse relatório simples, não adicionaremos mais nenhuma coluna. Para ter uma representação mais significativa dos dados, altere a visualização para **Gráfico de rosca**.

   ![Visualização de gráfico de rosca](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/donut_chart.png)

1. Quando o relatório estiver pronto, você poderá publicá-lo diretamente no portal do Power BI. Na faixa de opções **Página Inicial** do Power BI Desktop, selecione **Publicar**.

## <a name="task-5-create-and-share-a-dashboard"></a>Tarefa 5: Criar e compartilhar um dashboard

Você criou o relatório e fez a publicação no serviço do **Power BI**. Agora você pode usar o exemplo criado nas etapas anteriores para demonstrar o cenário de segurança do modelo.

Na função de *Gerente de vendas*, a usuária Graça pode ver os dados de todas as diferentes regiões de vendas. Graça cria esse relatório e publica-o no serviço do Power BI. Esse relatório foi criado nas tarefas anteriores.

Depois de Graça publicar o relatório, a próxima etapa é criar um dashboard no serviço do Power BI chamado *TabularDynamicSec* com base no relatório. Na imagem a seguir, observe que Graça consegue ver os dados correspondentes a todas as regiões de vendas.

   ![Dashboard de serviço do Power BI](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/donut_chart_1.png)

Agora, Graça compartilha o dashboard com sua colega, Rita, responsável pelas vendas na região da Austrália.

   ![Compartilhar um dashboard do Power BI](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/pbi_dashboard.png)

Quando o Rita faz logon no serviço do Power BI e vê o dashboard compartilhado que Graça criou, somente as vendas da região da Austrália ficam visíveis.

Parabéns! O serviço do Power BI mostra a segurança em nível de linha dinâmica definida no modelo tabular do Analysis Services local. O Power BI usa a propriedade `EffectiveUserName` para enviar as atuais credenciais de usuário do Power BI à fonte de dados local para executar as consultas.

## <a name="task-6-understand-what-happens-behind-the-scenes"></a>Tarefa 6: Entender o que acontece nos bastidores

Esta tarefa pressupõe que você esteja familiarizado com o [SQL Server Profiler](/sql/tools/sql-server-profiler/sql-server-profiler), já que você precisa capturar um rastreamento do criador de perfil do SQL Server na instância tabular do SSAS local.

A sessão é inicializada assim que a usuária, Rita, acessa o dashboard no serviço do Power BI. Você pode ver que a função **salesterritoryusers** funciona imediatamente com o nome de usuário efetivo **<EffectiveUserName>rita@contoso.com</EffectiveUserName>**

       <PropertyList><Catalog>DefinedSalesTabular</Catalog><Timeout>600</Timeout><Content>SchemaData</Content><Format>Tabular</Format><AxisFormat>TupleFormat</AxisFormat><BeginRange>-1</BeginRange><EndRange>-1</EndRange><ShowHiddenCubes>false</ShowHiddenCubes><VisualMode>0</VisualMode><DbpropMsmdFlattened2>true</DbpropMsmdFlattened2><SspropInitAppName>PowerBI</SspropInitAppName><SecuredCellValue>0</SecuredCellValue><ImpactAnalysis>false</ImpactAnalysis><SQLQueryMode>Calculated</SQLQueryMode><ClientProcessID>6408</ClientProcessID><Cube>Model</Cube><ReturnCellProperties>true</ReturnCellProperties><CommitTimeout>0</CommitTimeout><ForceCommitTimeout>0</ForceCommitTimeout><ExecutionMode>Execute</ExecutionMode><RealTimeOlap>false</RealTimeOlap><MdxMissingMemberMode>Default</MdxMissingMemberMode><DisablePrefetchFacts>false</DisablePrefetchFacts><UpdateIsolationLevel>2</UpdateIsolationLevel><DbpropMsmdOptimizeResponse>0</DbpropMsmdOptimizeResponse><ResponseEncoding>Default</ResponseEncoding><DirectQueryMode>Default</DirectQueryMode><DbpropMsmdActivityID>4ea2a372-dd2f-4edd-a8ca-1b909b4165b5</DbpropMsmdActivityID><DbpropMsmdRequestID>2313cf77-b881-015d-e6da-eda9846d42db</DbpropMsmdRequestID><LocaleIdentifier>1033</LocaleIdentifier><EffectiveUserName>rita@contoso.com</EffectiveUserName></PropertyList>

Com base na solicitação de nome de usuário efetivo, o Analysis Services converte a solicitação para a credencial real `contoso\rita` depois de consultar o Active Directory local. Assim que o Analysis Services obtém a credencial, o Analysis Services retorna os dados que o usuário tem permissão para exibir e acessar.

Se ocorrer mais atividades com o dashboard, com o SQL Profiler, você verá uma consulta específica voltada para o modelo de tabela do Analysis Services como uma consulta DAX. Por exemplo, se Rita passar do dashboard para o relatório subjacente, a consulta a seguir ocorrerá.

   ![A consulta DAX volta para o modelo do Analysis Services](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/profiler1.png)

Você também pode ver abaixo a consulta DAX sendo executada para popular os dados do relatório.
   
   ```sql
   EVALUATE
     ROW(
       "SumEmployeeKey", CALCULATE(SUM(Employee[EmployeeKey]))
     )
   
   <PropertyList xmlns="urn:schemas-microsoft-com:xml-analysis">``
             <Catalog>DefinedSalesTabular</Catalog>
             <Cube>Model</Cube>
             <SspropInitAppName>PowerBI</SspropInitAppName>
             <EffectiveUserName>rita@contoso.com</EffectiveUserName>
             <LocaleIdentifier>1033</LocaleIdentifier>
             <ClientProcessID>6408</ClientProcessID>
             <Format>Tabular</Format>
             <Content>SchemaData</Content>
             <Timeout>600</Timeout>
             <DbpropMsmdRequestID>8510d758-f07b-a025-8fb3-a0540189ff79</DbpropMsmdRequestID>
             <DbPropMsmdActivityID>f2dbe8a3-ef51-4d70-a879-5f02a502b2c3</DbPropMsmdActivityID>
             <ReturnCellProperties>true</ReturnCellProperties>
             <DbpropMsmdFlattened2>true</DbpropMsmdFlattened2>
             <DbpropMsmdActivityID>f2dbe8a3-ef51-4d70-a879-5f02a502b2c3</DbpropMsmdActivityID>
           </PropertyList>
   ```

## <a name="considerations"></a>Considerações

* A segurança em nível de linha local com o Power BI só está disponível com a conexão dinâmica.

* As alterações nos dados após o processamento do modelo seriam imediatamente disponibilizadas para os usuários que estão acessando o relatório com a conexão dinâmica por meio do serviço do Power BI.

