---
title: Conectar dados tabulares do Analysis Services no Power BI Desktop
description: Com o Power BI Desktop, você pode se conectar a seus modelos tabulares do SQL Server Analysis Services e obter dados deles usando uma conexão dinâmica ou selecionando itens para importação para o Power BI Desktop.
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/28/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: ac15a732f3d388fd5dafa61d33eec1d82022da54
ms.sourcegitcommit: cde65bb8b1bed1ee8cf512651afeb829ddc155de
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77464223"
---
# <a name="connect-to-analysis-services-tabular-data-in-power-bi-desktop"></a>Conectar dados tabulares do Analysis Services no Power BI Desktop
Com o Power BI Desktop, há duas maneiras de obter e se conectar aos dados de seus modelos tabulares do SQL Server Analysis Services: explorar usando uma conexão dinâmica ou selecionar itens e importá-los para o Power BI Desktop.

Vamos ver isso mais de perto.

**Explorar usando uma conexão dinâmica**: ao usar uma conexão dinâmica, os itens em sua perspectiva ou modelo tabular, como tabelas, colunas e medidas, aparecem na lista do painel **Campos** do Power BI Desktop. Você pode usar as ferramentas avançadas de relatório e visualização do Power BI Desktop para explorar seu modelo tabular de maneiras novas e altamente interativas.

Quando é feita uma conexão dinâmica, nenhum dado do modelo tabular é importado para o Power BI Desktop. Cada vez que você interage com uma visualização, o Power BI Desktop consulta o modelo tabular e calcula os resultados que você vê. Você está sempre vendo os dados mais recentes disponíveis no modelo tabular, do último processamento ou das tabelas do DirectQuery disponíveis no modelo tabular. 

Lembre-se de que os modelos tabulares são altamente seguros. Itens que aparecem no Power BI Desktop dependem de suas permissões para o modelo tabular ao qual você está conectado.

Quando você tiver criado relatórios dinâmicos na Área de Trabalho do Power BI, você pode compartilhá-los pela publicação em seu site do Power BI. Quando você publica um arquivo do Power BI Desktop com uma conexão dinâmica em um modelo tabular no site do Power BI, um gateway de dados local deve ser instalado e configurado por um administrador. Para saber mais, veja [Gateway de dados local](service-gateway-onprem.md).

**Selecionar itens e importá-los para o Power BI Desktop**: quando se conecta com essa opção, você pode selecionar itens como tabelas, colunas e medidas em seu modelo tabular ou perspectiva e carregá-los em um modelo do Power BI Desktop. Use o Editor do Power Query do Power BI Desktop para formatar melhor o que você deseja, bem como seus recursos de modelagem para modelar ainda mais os dados. Como nenhuma conexão dinâmica entre o Power BI Desktop e o modelo tabular é mantida, você pode explorar o modelo do Power BI Desktop offline ou publicar em seu site do Power BI.

## <a name="to-connect-to-a-tabular-model"></a>Para conectar-se a um modelo tabular
1. No Power BI Desktop, na guia **Página Inicial**, selecione **Obter Dados** > **Mais** > **Banco de dados**.
   
1. Selecione **Banco de dados do SQL Server Analysis Services** e, em seguida, selecione **Conectar**.
   
   ![Selecione o banco de dados do SQL Server Analysis Services](media/desktop-analysis-services-tabular-data/pbid_sqlas_getdata_as.png)
3. Na janela **Banco de dados do SQL Server Analysis Services**, insira o nome do **Servidor**, escolha um modo de conexão e, em seguida, selecione **OK**.
   
   ![Janela do banco de dados do SQL Server Analysis Services](media/desktop-analysis-services-tabular-data/pbid_sqlas_getdata_as_server.png)
4. Essa etapa na janela do **Navegador** depende do modo de conexão selecionado:

   - Se você estiver se conectando dinamicamente, selecione uma perspectiva ou um modelo tabular.
  
      ![Selecione uma perspectiva ou um modelo tabular do Navegador](media/desktop-analysis-services-tabular-data/pbid_sqlas_getdata_as_live.png)
   - Se você optar por selecionar itens e obter dados, selecione uma perspectiva ou um modelo tabular e, em seguida, selecione uma tabela ou coluna específica para ser carregada. Para formatar seus dados antes do carregamento, selecione **Editar Consultas** para abrir o Editor do Power Query. Quando estiver pronto, selecione **Carregar** para importar os dados para o Power BI Desktop.

      ![Selecione a tabela ou a coluna do Navegador para ser carregada](media/desktop-analysis-services-tabular-data/pbid_sqlas_getdata_as_select.png)

## <a name="frequently-asked-questions"></a>Perguntas frequentes
**Pergunta:** Preciso de um gateway de dados local?

**Resposta:** Depende. Se você usa o Power BI Desktop para se conectar dinamicamente a um modelo tabular, mas não tem intenção de fazer uma publicação no site do Power BI, não é necessário ter um gateway. Por outro lado, se pretende publicar em seu site do Power BI, é necessário ter um gateway de dados para garantir a comunicação segura entre o serviço do Power BI e o servidor local do Analysis Services. Certifique-se de falar com o administrador do servidor do Analysis Services antes de instalar um gateway de dados.

Se escolher selecionar itens e obter dados, você importará dados do modelo tabular diretamente para seu arquivo do Power BI Desktop; portanto, não será necessário ter um gateway.

**Pergunta:** Qual é a diferença entre a conexão dinâmica com um modelo tabular do serviço do Power BI e a conexão dinâmica no Power BI Desktop?

**Resposta:** Durante a conexão dinâmica com um modelo tabular de seu site no serviço do Power BI com um banco de dados local do Analysis Services em sua organização, é necessário ter um gateway de dados local para proteger a comunicação entre eles. Durante a conexão dinâmica com um modelo de tabela do Power BI Desktop, não é necessário ter um gateway, pois o Power BI Desktop e o servidor do Analysis Services ao qual você está se conectando estão sendo executados localmente em sua organização. No entanto, se o arquivo do Power BI Desktop for publicado no seu site do Power BI, será necessário um gateway.

**Pergunta:** Se eu criei uma conexão dinâmica, posso me conectar a uma outra fonte de dados no mesmo arquivo do Power BI Desktop?

**Resposta:** Não. Você não pode explorar dados dinâmicos e conectar-se a outro tipo de fonte de dados no mesmo arquivo. Se você já tiver importado dados ou se conectado a uma fonte de dados diferente em um arquivo do Power BI Desktop, você precisará criar um arquivo para explorar dinamicamente.

**Pergunta:** Se eu criei uma conexão dinâmica, posso editar o modelo ou a consulta no Power BI Desktop?

**Resposta:** É possível criar medidas de nível de relatório no Power BI Desktop, mas todos os outros recursos de consulta e de modelagem ficam desabilitados ao explorar dados dinâmicos.

**Pergunta:** Se eu criei uma conexão dinâmica, ela é segura?

**Resposta:** Sim. Suas credenciais atuais do Windows são usadas para se conectar ao servidor do Analysis Services. Não é possível usar credenciais Básicas ou armazenadas no serviço do Power BI ou Power BI Desktop ao explorar dinamicamente.

**Pergunta:** No Navegador, vejo um modelo e uma perspectiva. Qual é a diferença?

**Resposta:** Uma perspectiva é uma exibição específica de um modelo tabular. Ela pode incluir somente determinadas tabelas, colunas ou medidas dependendo de uma necessidade de análise de dados exclusiva. Um modelo tabular sempre contém pelo menos uma perspectiva, que pode incluir tudo no modelo. Se você não tem certeza de qual perspectiva deve selecionar, contate seu administrador.

**Pergunta:** Existe algum recurso do Analysis Services que muda a maneira em que o Power BI se comporta?

**Resposta:** Sim. Dependendo dos recursos que seu modelo de tabela usa, a experiência no Power BI Desktop pode ser alterada. Alguns exemplos incluem:
* Você pode ver medidas no modelo agrupadas na parte superior da lista do painel **Campos** em vez de em tabelas ao lado das colunas. Não se preocupe, você ainda pode usá-las normalmente, só é mais fácil encontrá-las dessa maneira.

* Se o modelo de tabela tiver grupos de cálculo definidos, você poderá usá-los apenas em conjunto com medidas de modelo, e não com medidas implícitas criadas adicionando campos numéricos a um visual. O modelo também pode ter tido o sinalizador **DiscourageImplicitMeasures** definido manualmente, o que tem o mesmo efeito. Para saber mais, confira [Grupos de cálculo no Analysis Services](https://docs.microsoft.com/analysis-services/tabular-models/calculation-groups#benefits).

## <a name="to-change-the-server-name-after-initial-connection"></a>Para alterar o nome do servidor após a conexão inicial
Após você criar um arquivo do Power BI Desktop com uma conexão dinâmica de exploração, pode haver alguns casos em que você deseja alternar a conexão para um servidor diferente. Por exemplo, se você criou o arquivo do Power BI Desktop ao se conectar a um servidor de desenvolvimento e, antes da publicação para o serviço do Power BI, você deseja alternar a conexão para o servidor de produção.

Para alterar o nome do servidor:

1. Selecione **Editar Consultas** na guia **Página Inicial**.

2. Na janela **Banco de dados do SQL Server Analysis Services**, insira o nome do novo **Servidor** e, em seguida, selecione **OK**.

   
## <a name="troubleshooting"></a>Solução de problemas 
A lista a seguir descreve todos os problemas conhecidos de conexão com o SSAS (SQL Server Analysis Services) ou com o Azure Analysis Services: 

* **Erro: não foi possível carregar o esquema do modelo**: esse erro normalmente ocorre quando o usuário que se conecta ao Analysis Services não tem acesso ao banco de dados/modelo.

