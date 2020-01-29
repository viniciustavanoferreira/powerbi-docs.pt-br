---
title: Parâmetros de relatório no Construtor de Relatórios do Power BI
description: Este tópico descreve os usos comuns de parâmetros de relatório do Power BI Report Builder, as propriedades que podem ser definidas, entre outros.
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.custom: ''
ms.date: 06/06/2019
ms.openlocfilehash: 5a7e91c03b11902f324d6a7c639a03f7652acf16
ms.sourcegitcommit: 3d6b27e3936e451339d8c11e9af1a72c725a5668
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2020
ms.locfileid: "76160847"
---
# <a name="report-parameters-in-power-bi-report-builder"></a>Parâmetros de relatório no Construtor de Relatórios do Power BI

Este tópico descreve os usos comuns de parâmetros de relatório do Power BI Report Builder, as propriedades que podem ser definidas, entre outros. Os parâmetros de relatório permitem controlar os dados de relatório, conectar relatórios relacionados e variar a apresentação do relatório. Use parâmetros de relatório em relatórios paginados criados no Construtor de Relatórios.

## <a name="bkmk_Common_Uses_for_Parameters"></a> Usos comuns de parâmetros

 Veja a seguir algumas das maneiras mais comuns de usar parâmetros.  
  
**Controlar os dados de relatório paginado**
  
- Filtre os dados de relatório paginado na fonte de dados escrevendo consultas de conjunto de dados que contenham variáveis.  
  
- Permita que os usuários especifiquem valores para personalizar os dados em um relatório paginado. Por exemplo, forneça dois parâmetros para a data de início e a data de término dos dados de vendas.  
  
**Variar a apresentação do relatório**
  
- Permita que os usuários especifiquem valores para ajudar a personalizar a aparência de um relatório. Por exemplo, forneça um parâmetro booliano para indicar se deseja expandir ou recolher todos os grupos de linhas aninhados em uma tabela.  
  
- Permita que usuários personalizem os dados de relatório e a aparência incluindo parâmetros em uma expressão.  
  
## <a name="UserInterface"></a> Como exibir um relatório com parâmetros

Ao exibir um relatório que tenha parâmetros, a barra de ferramentas visualizador de relatório exibe cada parâmetro para que você possa especificar valores de forma interativa. A ilustração a seguir mostra a área de parâmetro para um relatório com parâmetros @ReportMonth, @ReportYear, @EmployeeID, @ShowAll, @ExpandTableRows, @CategoryQuota e @SalesDate.  

![Exibir um relatório com parâmetros](media/report-builder-parameters/report-builder-parameters-power-bi-service.png "Exibir um relatório com parâmetros")
  
1. **Painel de parâmetros** A barra de ferramentas do Visualizador de Relatórios exibe um prompt e um valor padrão para cada parâmetro. Você pode personalizar o layout dos parâmetros no painel de parâmetros.  
  
2. **@SalesDate parâmetro** o parâmetro @SalesDate é o tipo de dados **DateTime**. O prompt Selecione a Data é exibido ao lado da caixa de texto. Para modificar a data, digite uma nova data na caixa de texto ou use o controle de calendário.  
  
3. **@ShowAll parâmetro** o parâmetro @ShowAll é o tipo de dados **booliano**. Use os botões de opção para especificar **True** ou **False**.  
  
4. **Identificador Mostrar ou Ocultar Área de Parâmetros** Na barra de ferramentas do Visualizador de Relatórios, clique nessa seta para mostrar ou ocultar o painel de parâmetros.  
  
5. **@CategoryQuota parâmetro** o parâmetro @CategoryQuota é o tipo de dados **Float**, portanto, ele usa um valor numérico.  @CategoryQuota é definido para permitir vários valores.  
  
6. **Exibir Relatório** Depois de inserir valores de parâmetro, clique em **Exibir Relatório** para executar o relatório. Se todos os parâmetros tiverem valores padrão, o relatório será executado automaticamente na primeira exibição.  
  
## <a name="bkmk_Create_Parameters"></a> Como criar parâmetros

Você pode criar parâmetros de relatório de algumas maneiras diferentes.
  
> [!NOTE]
>  Nem todas as fontes de dados dão suporte a parâmetros.
  
**Consulta de conjunto de dados ou procedimento armazenado com parâmetros**
  
 Adicione uma consulta de conjunto de dados que contenha variáveis ou um procedimento armazenado de conjunto de dados que contenha parâmetros de entrada. Um parâmetro de conjunto de dados é criado para cada variável ou parâmetro de entrada. Por sua vez, um parâmetro de relatório é criado para cada parâmetro de conjunto de dados.  
  
![Propriedades do conjunto de dados dos parâmetros do Construtor de Relatórios](media/report-builder-parameters/report-builder-parameter-dataset.png "Propriedades do conjunto de dados dos parâmetros do Construtor de Relatórios")

  
 Esta imagem do Construtor de Relatórios mostra:  
  
1.  Os parâmetros do relatório no painel Dados do Relatório.  
  
2.  O conjunto de dados com os parâmetros.  
  
3.  O painel Parâmetros.  
  
4.  Os parâmetros listados na caixa de diálogo Propriedades do Conjunto de Dados.  
  
**Criar um parâmetro manualmente**
  
Crie um parâmetro manualmente por meio do painel de dados do relatório. Configure os parâmetros de relatório, de modo que um usuário possa inserir valores de maneira interativa para ajudar a personalizar o conteúdo ou a aparência de um relatório. Configure também os parâmetros de relatório, de modo que um usuário não possa alterar os valores pré-configurados.  
  
> [!NOTE]  
>  Como os parâmetros são gerenciados de maneira independente no servidor, a nova publicação de um relatório principal com novas configurações de parâmetros não substitui as configurações de parâmetros existentes no relatório.  

### <a name="parameter-values"></a>Valores de parâmetros

 Veja a seguir as opções para selecionar valores de parâmetro no relatório.  
  
- Selecione um único valor de parâmetro em uma lista suspensa.  
  
- Selecione vários valores de parâmetros em uma lista suspensa.  
  
- Selecione um valor em uma lista suspensa para um parâmetro, que determina os valores que estão disponíveis na lista suspensa para outro parâmetro. Esses são parâmetros em cascata. Os parâmetros em cascata permitem que você filtre sucessivamente valores de parâmetros de milhares de valores para um número gerenciável. Confira mais informações em [Usar parâmetros em cascata nos relatórios paginados](guidance/paginated-report-cascading-parameter.md).
  
- Execute o relatório sem precisar primeiro selecionar um valor de parâmetro porque um valor padrão foi criado para o parâmetro.  
  
## <a name="bkmk_Report_Parameters"></a> Propriedades do parâmetro de relatório

 Altere as propriedades de parâmetro de relatório usando a caixa de diálogo Propriedades do Relatório. A seguinte tabela resume as propriedades que podem ser definidas para cada parâmetro:  
  
|Property|Descrição|  
|--------------|-----------------|  
|Nome|Digite um nome que diferencia maiúsculas de minúsculas para o parâmetro. O nome precisa começar com uma letra e pode conter letras, números e um sublinhado (_). O nome não pode conter espaços. Para parâmetros gerados automaticamente, o nome corresponde ao parâmetro na consulta de conjunto de dados. Por padrão, os parâmetros criados manualmente são semelhantes a ReportParameter1.|  
|Prompt|O texto exibido ao lado do parâmetro na barra de ferramentas do Visualizador de Relatórios.|  
|Tipo de dados|Um parâmetro de relatório precisa ser um dos seguintes tipos de dados:<br /><br /> **Boolean**. O usuário seleciona True ou False usando um botão de opção.<br /><br /> **DateTime**. O usuário seleciona uma data em um controle de calendário.<br /><br /> **Integer**. O usuário digita valores em uma caixa de texto.<br /><br /> **Float**. O usuário digita valores em uma caixa de texto.<br /><br /> **Text**. O usuário digita valores em uma caixa de texto.<br /><br /> Quando os valores disponíveis são definidos para um parâmetro, o usuário escolhe valores em uma lista suspensa, mesmo quando o tipo de dados é **DateTime**.|  
|Permitir valor em branco|Selecione essa opção se o valor do parâmetro puder ser uma cadeia de caracteres vazia ou um espaço em branco.<br /><br /> Se você especificar valores válidos para um parâmetro e desejar que um valor em branco seja um dos valores válidos, você precisará incluí-lo como um dos valores especificados. A seleção dessa opção não inclui automaticamente um espaço para os valores disponíveis.|  
|Permitir valor nulo|Selecione essa opção se o valor do parâmetro puder ser nulo.<br /><br /> Se você especificar valores válidos para um parâmetro e desejar que um nulo seja um dos valores válidos, você precisará incluir o nulo como um dos valores especificados. A seleção dessa opção não inclui automaticamente um nulo para os valores disponíveis.|  
|Permitir vários valores|Forneça valores disponíveis para criar uma lista suspensa na qual os usuários possam fazer suas escolhas. Essa é uma boa maneira de garantir que somente os valores válidos sejam enviados na consulta de conjunto de dados.<br /><br /> Selecione essa opção se o valor do parâmetro puder ser vários valores que são exibidos em uma lista suspensa. Valores nulos não são permitidos. Quando essa opção é selecionada, caixas de seleção são adicionadas à lista de valores disponíveis em uma lista suspensa de parâmetros. A parte superior da lista inclui uma caixa de seleção **Selecionar Tudo**. Os usuários podem marcar os valores desejados.<br /><br /> Se os dados que fornecem os valores forem alterados rapidamente, a lista vista pelo usuário poderá não ser a mais atual.|  
|Visível|Selecione essa opção para exibir o parâmetro de relatório na parte superior do relatório quando ele for executado. Essa opção permite que os usuários selecionem valores de parâmetro em tempo de execução.|  
|Oculto|Selecione essa opção para ocultar o parâmetro de relatório no relatório publicado. Os valores de parâmetro de relatório ainda podem ser definidos em uma URL de relatório, em uma definição de assinatura ou no servidor de relatório.|  
|Interno|Selecione essa opção para ocultar o parâmetro de relatório. No relatório publicado, o parâmetro de relatório só pode ser exibido na definição de relatório.|  
|Valores disponíveis|Se você tiver especificado valores disponíveis para um parâmetro, os valores válidos sempre serão exibidos como uma lista suspensa. Por exemplo, se você fornecer valores disponíveis para um parâmetro **DateTime**, uma lista suspensa para datas será exibida no painel de parâmetros em vez de em um controle de calendário.<br /><br /> Para garantir que uma lista de valores seja consistente entre um relatório e os sub-relatórios, você pode definir uma opção na fonte de dados para usar uma única transação para todas as consultas nos conjuntos de dados associados a uma fonte de dados.<br /><br /> **Observação de segurança** Em qualquer relatório que inclua um parâmetro do tipo de dados **Text**, use uma lista de valores disponíveis (também conhecida como uma lista de valores válidos) e garanta que qualquer usuário que execute o relatório tenha somente as permissões necessárias para exibir os dados no relatório.|  
|Valores padrão|Defina valores padrão em uma consulta ou uma lista estática.<br /><br /> Quando cada parâmetro tem um valor padrão, o relatório é executado automaticamente na primeira exibição.|  
|Avançado|Defina o atributo de definição de relatório **UsedInQuery**, um valor que indica se esse parâmetro afeta direta ou indiretamente os dados em um relatório.<br /><br /> **Determinar automaticamente quando atualizar**<br /> Escolha essa opção quando desejar que o processador de relatório determine uma configuração para esse valor. O valor será **True** se o processador de relatório detectar uma consulta de conjunto de dados com uma referência direta ou indireta a esse parâmetro ou se o relatório tiver sub-relatórios.<br /><br /> **Atualizar sempre**<br /> Escolha essa opção quando o parâmetro de relatório é usado direta ou indiretamente em uma expressão de parâmetro ou uma consulta de conjunto de dados. Essa opção define **UsedInQuery** como True.<br /><br /> **Nunca atualizar**<br /> Escolha essa opção quando o parâmetro de relatório não é usado direta ou indiretamente em uma expressão de parâmetro ou uma consulta de conjunto de dados. Essa opção define **UsedInQuery** como False.<br /><br /> **Cuidado** Use a opção **Nunca Atualizar** com cuidado. No servidor de relatório, **UsedInQuery** é usado para ajudar a controlar as opções de cache para dados de relatório e para relatórios renderizados e as opções de parâmetro para relatórios de instantâneo. Se você definir **Nunca Atualizar** incorretamente, poderá fazer com que dados de relatório ou relatórios incorretos sejam armazenados em cache ou fazer com que um relatório de instantâneos tenha dados inconsistentes. |  
  
##  <a name="bkmk_Dataset_Parameters"></a> Consulta de conjunto de dados  
 Para filtrar os dados na consulta de conjunto de dados, você pode incluir uma cláusula de restrição que limita os dados recuperados especificando valores a serem incluídos ou excluídos do conjunto de resultados.  
  
 Use o designer de consultas da fonte de dados para ajudar a criar uma consulta parametrizada.  
  
-   Para consultas Transact-SQL, fontes de dados diferentes dão suporte a diferentes tipos de sintaxe para parâmetros. O suporte abrange parâmetros que são identificados na consulta por posição ou por nome. No designer de consultas relacional, é necessário selecionar a opção de parâmetro para um filtro a fim de criar uma consulta parametrizada.   
  
-   Para consultas que são baseadas em uma fonte de dados multidimensional, como o Microsoft SQL Server Analysis Services, você pode especificar se deseja criar um parâmetro com base em um filtro especificado no designer de consultas. 
  
##  <a name="bkmk_Manage_Parameters"></a> Gerenciamento de parâmetros para um relatório publicado  
 Quando você cria um relatório, os parâmetros de relatório são salvos na definição de relatório. Quando você publica um relatório, os parâmetros de relatório são salvos e gerenciados separadamente da definição de relatório.  
  
 Para um relatório publicado, você pode usar o seguinte:  
  
-   **Propriedades de parâmetro de relatório.** Altere os valores do parâmetro de relatório diretamente no servidor de relatório de maneira independente da definição de relatório.  
  
-   **Assinaturas de relatório.** Você pode especificar valores de parâmetro para filtrar dados e entregar relatórios por meio de assinaturas. 
  
 As propriedades de parâmetro para um relatório publicado serão preservadas se a definição de relatório for publicada novamente. Se a definição de relatório for publicada novamente como o mesmo relatório e os nomes de parâmetros e os tipos de dados permanecerem os mesmos, as configurações de propriedade serão mantidas. Se você adicionar ou excluir parâmetros da definição de relatório ou alterar o tipo de dados ou o nome de um parâmetro existente, talvez você precise alterar as propriedades de parâmetro no relatório publicado.  
  
 Nem todos os parâmetros podem ser modificados em todos os casos. Se um parâmetro de relatório obtiver um valor padrão de uma consulta de conjunto de dados, esse valor não poderá ser modificado para um relatório publicado e não poderá ser modificado no servidor de relatório. O valor que é usado em tempo de execução é determinado quando a consulta é executada ou, no caso de parâmetros baseados em expressão, quando a expressão é avaliada.  
  
 As opções de execução de relatório podem afetar como os parâmetros são processados. Um relatório que é executado como um instantâneo não pode usar parâmetros que são derivados de uma consulta, a menos que a consulta inclua valores padrão para os parâmetros.  
  
##  <a name="bkmk_Parameters_Subscription"></a> Parâmetros para uma assinatura  
 Você pode definir uma assinatura para um relatório sob demanda ou para um instantâneo e especificar os valores de parâmetro a serem usados durante o processamento da assinatura.  
  
-   **Relatório sob demanda.**  Para um relatório sob demanda, você pode especificar um valor de parâmetro diferente do valor publicado para cada parâmetro listado para o relatório. Por exemplo, suponha que você tenha um relatório de Serviço de Chamada que usa um parâmetro *Período de Tempo* para retornar solicitações de atendimento ao cliente para o dia, a semana ou o mês atual. Se o valor do parâmetro padrão para o relatório for definido como **hoje**, sua assinatura poderá usar outro valor de parâmetro (como **semana** ou **mês**) para produzir um relatório que contenha estatísticas semanais ou mensais.  
  
## <a name="next-steps"></a>Próximas etapas

- [O que são os relatórios paginados no Power BI Premium?](paginated-reports-report-builder-power-bi.md)  
- [Usar parâmetros em cascata nos relatórios paginados](guidance/paginated-report-cascading-parameter.md)
