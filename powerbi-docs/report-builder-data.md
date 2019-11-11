---
title: Dados de relatório no Construtor de Relatórios do Power BI
description: A primeira etapa na criação de um relatório no Construtor de Relatórios Paginados do Power BI é criar fontes de dados e conjuntos de dados que representem os dados subjacentes do relatório.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.custom: seodec18
ms.date: 06/06/2019
ms.openlocfilehash: cbcb710a806c400ea33ac4d605614b5325277d07
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/09/2019
ms.locfileid: "73860430"
---
# <a name="report-data-in-power-bi-report-builder"></a>Dados de relatório no Construtor de Relatórios do Power BI

Os dados de relatório podem ser provenientes de várias fontes de dados em sua organização. A primeira etapa na criação de um relatório do Construtor de Relatórios do Power BI é criar fontes de dados e conjuntos de dados que representem os dados subjacentes do relatório. Cada fonte de dados inclui informações de conexão de dados. Cada conjunto de dados inclui um comando de consulta que define o conjunto de campos a ser usado como os dados de uma fonte de dados. Para visualizar os dados de cada conjunto de dados, adicione uma região de dados, como uma tabela, uma matriz, um gráfico ou um mapa. Quando o relatório é processado, as consultas são executadas na fonte de dados e cada região de dados é expandida, conforme necessário, para exibir os resultados da consulta do conjunto de dados.  

Saiba como [Criar uma fonte de dados inserida para relatórios paginados no Construtor de Relatórios do Power BI](paginated-reports-embedded-data-source.md).


##  <a name="BkMk_ReportDataTerms"></a> Termos  
  
- **Conexão de dados.** Também conhecida como *fonte de dados*. Uma conexão de dados inclui propriedades de nome e de conexão que dependem do tipo de conexão. Por design, uma conexão de dados não inclui credenciais. Uma conexão de dados não especifica quais dados serão recuperados da fonte de dados externa. Para fazer isso, especifique uma consulta quando você criar um conjunto de dados.  
  
- **Cadeia de conexão.** Uma cadeia de conexão é uma versão de cadeia de caracteres das propriedades de conexão que são necessárias para se conectar a uma fonte de dados. As propriedades de conexão variam de acordo com o tipo de conexão de dados.  
  
- **Fonte de dados inserida.** Também conhecida como *fonte de dados específica do relatório*. Uma fonte de dados que é definida em um relatório e usada apenas por esse relatório.  
  
- **Credenciais.** As credenciais são as informações de autenticação que precisam ser fornecidas para permitir acesso a dados externos.  
  
##  <a name="BkMk_ReportDataTips"></a> Dicas para especificar dados de relatório

 Use as informações a seguir para criar sua estratégia de dados de relatório.  
  
- **Filtrar dados** Os dados de relatório podem ser filtrados na consulta ou no relatório. Use conjuntos de dados e variáveis de consulta para criar parâmetros em cascata e proporcione a um usuário a capacidade de refinar as escolhas de milhares de seleções a um número mais gerenciável. Filtre os dados de uma tabela ou um gráfico com base em valores de parâmetros ou outros valores especificados.  
  
- **Parâmetros** Os comandos da consulta de conjunto de dados que incluem variáveis de consulta criam automaticamente parâmetros de relatório correspondentes. Crie também parâmetros manualmente. Quando você exibe um relatório, a barra de ferramentas do relatório exibe os parâmetros. Os usuários podem selecionar valores para controlar os dados ou a aparência do relatório. Para personalizar os dados de relatório para públicos-alvo específicos, crie conjuntos de parâmetros de relatório com diferentes valores padrão vinculados à mesma definição de relatório ou use o campo interno **UserID**. 
  
- **Agrupar e agregar dados** Os dados de relatório podem ser agrupados e agregados na consulta ou no relatório. Se você agregar valores na consulta, poderá continuar combinando valores no relatório dentro das restrições do que é significativo.  
  
- **Classificar dados** Os dados de relatório podem ser classificados na consulta ou no relatório. Em tabelas, adicione também um botão de classificação interativo para permitir que o usuário controle a ordem de classificação.  
  
- **Dados baseados em expressão** Como a maioria das propriedades de relatório pode ser baseada em expressão e as expressões podem incluir referências a campos de conjunto de dados e parâmetros de relatório, você pode escrever expressões avançadas para controlar os dados e a aparência do relatório. Proporcione a um usuário a capacidade de controlar os dados vistos pela definição de parâmetros.  
  
- **Exibir dados de um conjunto de dados** Os dados de um conjunto de dados normalmente são exibidos em uma ou mais regiões de dados, por exemplo, uma tabela e um gráfico.  
  
- **Exibir dados de vários conjuntos de dados** Escreva expressões em uma região de dados com base em um conjunto de dados que procuram valores ou agregações em outros conjuntos de dados. Inclua sub-relatórios em uma tabela com base em um conjunto de dados para exibir os dados de outra fonte de dados.  
  
 Use a lista a seguir para ajudar a definir fontes de dados para um relatório.  
  
- Entenda a arquitetura da camada de dados de software de sua organização e os problemas potenciais decorrentes dos tipos de dados. Entenda como as extensões de dados e as extensões de processamento de dados podem afetar os resultados da consulta. Os tipos de dados variam de acordo com a fonte, os provedores e os tipos de dados armazenados no arquivo de definição de relatório (.rdl).  
  
- As fontes de dados e os conjuntos de dados são criados em um relatório e publicados no serviço do Power BI. Depois que eles forem publicados, você poderá configurar as credenciais diretamente no serviço do Power BI ou no Gateway Corporativo. 

## <a name="next-steps"></a>Próximas etapas

- [O que são os relatórios paginados no Power BI Premium?](paginated-reports-report-builder-power-bi.md)  
