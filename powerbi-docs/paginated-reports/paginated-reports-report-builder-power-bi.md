---
title: O que são os relatórios paginados no Power BI Premium?
description: Os relatórios paginados, o formato longo de relatório padrão no SQL Server Reporting Services, agora estão disponíveis no serviço do Power BI. Esses relatórios podem ser impressos ou compartilhados. Você pode controlar o layout do relatório de maneira exata. Eles exibem todos os dados em uma tabela, por exemplo, mesmo se a tabela abranger várias páginas.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: overview
ms.date: 11/27/2019
ms.openlocfilehash: 924c2850efe1e9e09a8f6f350be616695ab061ea
ms.sourcegitcommit: 8eeb784fd46321680367ac913ef976aeedaa7766
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/03/2020
ms.locfileid: "80621546"
---
# <a name="what-are-paginated-reports-in-power-bi-premium"></a>O que são os relatórios paginados no Power BI Premium?

Os relatórios paginados, o formato longo de relatório padrão no SQL Server Reporting Services, agora estão disponíveis no serviço do Power BI. Esses relatórios podem ser impressos ou compartilhados. Eles são chamados de "paginados" porque são formatados de modo a se adaptarem bem a uma página. Eles exibem todos os dados em uma tabela, mesmo que a tabela abranja várias páginas. Às vezes são chamados de "pixel perfeito" porque você pode controlar o layout de página do relatório de maneira exata. Os relatórios paginados são baseados na tecnologia de relatório RDL no SQL Server Reporting Services. O Construtor de Relatórios é a ferramenta autônoma para a criação de relatórios paginados. 

Os relatórios paginados podem ter muitas páginas. Por exemplo, esse relatório tem 563 páginas. Cada página é disposta exatamente, com uma página por fatura e cabeçalhos e rodapés repetidos.

![Paginado](media/paginated-reports-report-builder-power-bi/power-bi-paginated-wwi-report-page.png)

Você pode visualizar o relatório no Construtor de Relatórios e publicá-lo no serviço do Power BI, `https://app.powerbi.com`. Você precisa de uma licença do Power BI Pro para publicar um relatório no serviço. É possível publicar e compartilhar relatórios paginados em Meu Workspace ou em workspaces, desde que o workspace esteja em uma capacidade do Power BI Premium. Além disso, um administrador do Power BI precisa habilitar relatórios paginados na [seção de capacidades Premium](../service-admin-premium-workloads.md#paginated-reports) no portal de administração do Power BI. 

## <a name="create-reports-in-power-bi-report-builder"></a>Criar relatórios no Construtor de Relatórios do Power BI

Os relatórios paginados têm sua própria ferramenta de design, o Construtor de Relatórios do Power BI. É uma ferramenta nova que compartilha a mesma base que as ferramentas que você usou anteriormente para criar relatórios paginados para o Servidor de Relatórios do Power BI ou o SSRS (SQL Server Reporting Services). Na verdade, os relatórios paginados criados para SSRS 2016 e 2017 ou para o Servidor de Relatórios do Power BI local são compatíveis com o serviço do Power BI. O serviço do Power BI mantém compatibilidade com versões anteriores para que você possa encaminhar seus relatórios e atualizar qualquer relatório paginado de versões anteriores. Nem todos os recursos de relatório estão disponíveis no lançamento. Veja [Limitações e considerações](#limitations-and-considerations) neste artigo para obter detalhes.
     
## <a name="report-from-a-variety-of-data-sources"></a>Relatório de uma variedade de fontes de dados

Um único relatório paginado pode ter várias fontes de dados diferentes. Ele não tem um modelo de dados subjacente, ao contrário dos relatórios do Power BI. Para a versão inicial de relatórios paginados no serviço do Power BI, você cria fontes de dados inseridas e conjuntos de dados no próprio relatório. Por enquanto, não é possível usar fontes de dados compartilhadas ou conjuntos de dados compartilhados. Você pode criar relatórios no Construtor de Relatórios no computador local. Se um relatório se conectar a dados locais, depois de carregar o relatório no serviço do Power BI, você precisará criar um gateway e redirecionar a conexão de dados. Aqui estão as fontes de dados às quais você pode se conectar no momento:

- Banco de Dados SQL do Azure e Data Warehouse (via Basic e oAuth)
- Azure Analysis Services (via SSO)
- SQL Server por meio de um gateway
- SSAS (SQL Server Analysis Services) via gateway
- Conjuntos de dados do Power BI
- Oracle
- Teradata

## <a name="design-your-report"></a>Projetar seu relatório  

### <a name="create-paginated-reports-with-matrix-chart-and-free-form-layouts"></a>Crie relatórios paginados com matriz, gráfico e layouts de forma livre

Os relatórios de tabela funcionam bem para dados baseados em colunas. Os relatórios de matriz, como relatórios de tabela cruzada ou Tabela Dinâmica, são bons para dados resumidos. Os relatórios de gráficos apresentam dados em um formato gráfico e os relatórios de *lista* de forma livre podem apresentar quase qualquer outro item, como faturas. 
  
Você pode começar com um dos assistentes do Construtor de Relatórios. Os assistentes de Tabela, Matriz e Gráfico orientam você durante a criação da conexão de fonte de dados inseridos e o conjunto de dados inseridos. Em seguida, você pode arrastar e soltar campos para criar uma consulta de conjunto de dados, selecionar um layout e estilo e personalizar seu relatório.  
  
Com o Assistente de mapa, você cria relatórios que exibem dados agregados em um plano de fundo geográfico ou geométrico. Os dados de mapa podem ser dados espaciais de uma consulta Transact-SQL ou um shapefile do Environmental Systems Research Institute, Inc. (ESRI). Você também pode adicionar um plano de fundo do bloco de mapa do Microsoft Bing.  

### <a name="add-more-to-your-report"></a>Adicionar mais ao seu relatório

Modifique seus dados filtrando, agrupando e classificando dados ou adicionando fórmulas ou expressões. Adicione gráficos, medidores, minigráficos e indicadores para resumir dados em um formato visual.  Use parâmetros e filtros para filtrar dados para exibições personalizadas. Insira ou referencie imagens e outros recursos, incluindo conteúdo externo.  

Tudo em um relatório paginado, do relatório em si até cada caixa de texto, imagem, tabela e gráfico, tem uma matriz de propriedades que você pode definir para tornar o relatório exatamente como você deseja.

## <a name="creating-a-report-definition"></a>Como criar uma definição de relatório

Quando você cria um relatório paginado, realmente está criando uma *definição de relatório*. Ele não contém os dados. Especifica onde obter os dados, quais dados devem ser obtidos e como exibir os dados. Quando você executa o relatório, o processador de relatório usa a definição de relatório que você especificou, recupera os dados e combina-os com o layout do relatório para gerar o relatório. Carregue a definição de relatório para o serviço do Power BI, `https://app.powerbi.com`, para Meu workspace ou um workspace compartilhado com seus colegas. Se a fonte de dados de relatório está no local, depois de carregar o relatório, redirecione a conexão de fonte de dados para passar por um gateway. 

## <a name="view-your-paginated-report"></a>Exibir o relatório paginado
Você exibe seu relatório paginado no serviço do Power BI em um navegador e também nos aplicativos móveis do Power BI. Do serviço do Power BI, você pode exportar o relatório para vários formatos, como HTML, MHTML, PDF, XML, CSV, TIFF, Word e Excel. Você também pode compartilhá-lo com outras pessoas.  

## <a name="create-a-subscription-to-your-report"></a>Criar uma assinatura para seu relatório

Agora você pode configurar assinaturas de email para você e outras pessoas para relatórios paginados no serviço do Power BI. Em geral, o processo é o mesmo que assinar relatórios e dashboards no serviço do Power BI. Na configuração de assinaturas, escolha a frequência com que você deseja receber os emails: diariamente, semanalmente ou por hora. A assinatura contém um anexo em PDF da saída do relatório completa.

Confira o artigo [Obter uma assinatura para você e para outras pessoas de um relatório paginado no serviço do Power BI](../consumer/paginated-reports-subscriptions.md) para obter detalhes. 

## <a name="limitations-and-considerations"></a>Limitações e considerações

Aqui estão alguns outros recursos que não têm suporte na versão inicial:

- Fixar páginas de relatório ou visuais em painéis do Power BI. Você ainda pode fixar visualizações a um painel do Power BI de um relatório paginado local em um Servidor de Relatórios do Microsoft Power BI ou em um Servidor de Relatórios do Reporting Services. Confira [Fixar itens do Reporting Services em painéis do Power BI](https://docs.microsoft.com/sql/reporting-services/pin-reporting-services-items-to-power-bi-dashboards) para obter mais informações.
- Mapas do Documento.
- Sub-relatórios e relatórios detalhados.  No entanto, você pode considerar o uso de parâmetros de URL com relatórios paginados para chegar aos cenários de detalhamento.
- Fontes de dados compartilhadas e conjuntos de dados compartilhados.

 
## <a name="next-steps"></a>Próximas etapas

- [Instale o Construtor de Relatórios do Power BI no Centro de Download da Microsoft](https://go.microsoft.com/fwlink/?linkid=2086513)
- [Tutorial: Criar um relatório paginado](paginated-reports-quickstart-aw.md)
- [Inserir dados diretamente em um relatório paginado](paginated-reports-enter-data.md)
- [Tutorial: Inserir relatórios paginados do Power BI em um aplicativo para seus clientes](../developer/embed-paginated-reports-customers.md)