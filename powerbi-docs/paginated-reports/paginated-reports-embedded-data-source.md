---
title: Fontes de dados inseridas para relatórios paginados no serviço do Power BI (versão prévia)
description: Neste artigo, você aprenderá como criar e modificar uma fonte de dados incorporada em um relatório paginado no serviço do Power BI.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 03/02/2020
ms.openlocfilehash: 83fadfe5f690a87563d20b9c6385b9a37193b9c9
ms.sourcegitcommit: ced8c9d6c365cab6f63fbe8367fb33e6d827cb97
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/07/2020
ms.locfileid: "78921759"
---
# <a name="create-an-embedded-data-source-for-paginated-reports-in-the-power-bi-service"></a>Criar uma fonte de dados incorporada para relatórios paginados no serviço do Power BI

Neste artigo, você aprenderá como criar e modificar uma fonte de dados incorporada para um relatório paginado no serviço do Power BI. Você define uma fonte de dados incorporada em um único relatório e a usa somente nesse relatório. Atualmente, os relatórios paginados publicados no serviço do Power BI precisam de conjuntos de dados e fontes de dados incorporadas. Eles podem se conectar às seguintes fontes de dados:

- Azure Analysis Services
- Banco de Dados SQL do Azure e 
- SQL Data Warehouse do Azure
- SQL Server
- SQL Server Analysis Services
- Oracle 
- Teradata 

Para as seguintes fontes de dados, use a opção [Conexão do SQL Server Analysis Services](../service-premium-connect-tools.md):

- Conjuntos de dados do Power BI Premium

Os relatórios paginados se conectam a fontes de dados locais por meio de um [gateway do Power BI](../service-gateway-onprem.md). Você configura o gateway após publicar o relatório no serviço do Power BI.

Confira [Dados de relatório no Construtor de Relatórios do Power BI](report-builder-data.md) para obter mais informações.

## <a name="create-an-embedded-data-source"></a>Criar uma fonte de dados incorporados
  
1. Abra o Construtor de Relatórios do Power BI.

1. Na barra de ferramentas do painel Dados do Relatório, selecione **Novo** > **Fonte de Dados**. A caixa de diálogo **Propriedades da Fonte de Dados** é aberta.

    ![Nova Fonte de Dados](media/paginated-reports-embedded-data-source/power-bi-paginated-new-data-source.png)
  
2.  Na caixa de texto **Nome**, digite um nome para a fonte de dados ou aceite o padrão.  
  
3.  Selecione **Usar uma conexão inserida no meu relatório**.  
  
1.  Na lista **Selecionar tipo de conexão**, selecione um tipo de fonte de dados. 

1.  Especifique uma cadeia de conexão usando um dos seguintes métodos:  
  
    -   Digite a cadeia de conexão diretamente na caixa de texto **Cadeia de Conexão**. 
  
     -   Selecione **Compilar** para abrir a caixa de diálogo **Propriedades de Conexão** para a fonte de dados escolhida na etapa 2.  
  
        Preencha os campos na caixa de diálogo **Propriedades de Conexão** conforme apropriado para o tipo de fonte de dados. As propriedades da conexão incluem o tipo de fonte de dados, o nome da fonte de dados e as credenciais a serem usadas. Depois de especificar valores nessa caixa de diálogo, selecione **Testar Conectividade** para verificar se a fonte de dados está disponível e se as credenciais especificadas estão corretas.  
  
4.  Selecione **Credenciais**.  
  
     Especifique as credenciais a serem usadas para essa fonte de dados. O proprietário da fonte de dados escolhe o tipo de credenciais que têm suporte. Para obter mais informações, confira [Especificar informações de credenciais e conexões para fontes de dados de relatório](https://docs.microsoft.com/sql/reporting-services/report-data/specify-credential-and-connection-information-for-report-data-sources).
  
5.  Selecione **OK**.  
  
     A fonte de dados é exibida no painel Dados do Relatório.  
     
## <a name="limitations-and-considerations"></a>Limitações e considerações

Os relatórios paginados que se conectam aos conjuntos de dados do Power BI seguem as regras para conjuntos de dados compartilhados no Power BI com algumas pequenas alterações.  Para que os usuários exibam corretamente os relatórios paginados usando conjuntos de dados do Power BI e garantam que a Segurança em Nível de Linha (RLS) esteja habilitada e imposta para os visualizadores, certifique-se de seguir estas regras:

### <a name="classic-apps-and-workspaces"></a>Aplicativos clássicos e workspaces

- .rdl no mesmo workspace que o conjunto de dados (mesmo proprietário): Compatível
- .rdl em um workspace diferente daquele do conjunto de dados (mesmo proprietário): Compatível
- .rdl compartilhado: Você precisará atribuir a permissão de leitura a cada usuário que estiver vendo o relatório no nível do conjunto de dados
- Aplicativo compartilhado: Você precisará atribuir a permissão de leitura a cada usuário que estiver vendo o relatório no nível do conjunto de dados
- .rdl no mesmo workspace que o conjunto de dados (outro usuário): Compatível
- .rdl em um workspace diferente daquele do conjunto de dados (outro usuário): você precisará atribuir a permissão de leitura a cada usuário que estiver vendo o relatório no nível do conjunto de dados
- Segurança em nível de função: Você precisará atribuir a permissão de leitura a cada usuário que estiver vendo o relatório no nível do conjunto de dados para que ela seja imposta.

### <a name="new-experience-apps-and-workspaces"></a>Novos aplicativos e workspaces

- .rdl no mesmo workspace que o conjunto de dados: Compatível
- .rdl em um workspace diferente daquele do conjunto de dados (mesmo proprietário): Compatível
- .rdl compartilhado: Você precisará atribuir a permissão de leitura a cada usuário que estiver vendo o relatório no nível do conjunto de dados
- Aplicativo compartilhado: Você precisará atribuir a permissão de leitura a cada usuário que estiver vendo o relatório no nível do conjunto de dados
- .rdl no mesmo workspace que o conjunto de dados (outro usuário) - Compatível
- .rdl em um workspace diferente daquele do conjunto de dados (outro usuário): Você precisará atribuir a permissão de leitura a cada usuário que estiver vendo o relatório no nível do conjunto de dados
- Segurança em nível de função: Você precisará atribuir a permissão de leitura a cada usuário que estiver vendo o relatório no nível do conjunto de dados para que ela seja imposta

## <a name="next-steps"></a>Próximas etapas

- [Criar um conjunto de dados inseridos para um relatório paginado no serviço do Power BI](paginated-reports-create-embedded-dataset.md)
- [O que são os relatórios paginados no Power BI Premium?](paginated-reports-report-builder-power-bi.md)
