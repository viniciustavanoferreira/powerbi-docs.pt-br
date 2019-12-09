---
title: Fontes de dados com suporte para relatórios paginados do Power BI
description: Neste artigo, você aprenderá sobre as fontes de dados compatíveis para relatórios paginados no serviço do Power BI e como se conectar a fontes de dados do Banco de Dados SQL do Azure.
author: onegoodsausage
ms.author: andremi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 12/03/2019
ms.openlocfilehash: f7662cbd2fb0085ad2e6fda6a33577d1cc29ddfb
ms.sourcegitcommit: e492895259aa39960063f9b337a144a60c20125a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74831262"
---
# <a name="supported-data-sources-for-power-bi-paginated-reports"></a>Fontes de dados com suporte para relatórios paginados do Power BI

Este artigo apresenta as fontes de dados compatíveis para relatórios paginados no serviço do Power BI e como se conectar a fontes de dados do Banco de Dados SQL do Azure. Algumas fontes de dados têm suporte nativo. Você pode se conectar a outras pessoas por meio de gateways de dados.

## <a name="natively-supported-data-sources"></a>Fontes de dados com suporte nativo

Os relatórios paginados oferecem suporte nativo à seguinte lista de fontes de dados:

| Fonte de dados | Autenticação | Observações |
| --- | --- | --- |
| Banco de Dados SQL do Azure <br>SQL Data Warehouse do Azure | Básico, logon único (SSO), OAuth2 |   |
| Instância Gerenciada do SQL do Azure | Básico | por meio do ponto de extremidade público usando a Extensão do Banco de Dados SQL do Azure  |
| Azure Analysis Services | SSO, OAuth2 |   |
| Conjunto de dados do Power BI | SSO | Conjuntos de dados do Power BI Premium e não Premium |
| Conjunto de dados do Power BI Premium (XMLA) | SSO |   |
| Inserir Dados | N/D | Os dados são inseridos no relatório. |

Exceto para o Banco de Dados SQL do Azure, todas as fontes estão prontas para uso depois que você carrega o relatório para o serviço do Power BI. As fontes de dados assumem como padrão o uso de SSO (logon único), quando aplicável. Para o Azure Analysis Services, você pode alterar o tipo de autenticação para OAuth2.

Para fontes de dados do Banco de Dados SQL do Azure, você precisa fornecer mais informações, conforme descrito na seção [Autenticação do Banco de Dados SQL do Azure](#azure-sql-database-authentication).

## <a name="other-data-sources"></a>Outras fontes de dados

Além das fontes de dados com suporte nativo acima, as seguintes fontes de dados podem ser acessadas por meio de um [gateway de dados do Power BI](service-gateway-onprem.md):

- SQL Server
- SQL Server Analysis Services
- Oracle
- Teradata

Para relatórios paginados, o Banco de Dados SQL do Azure e o Azure Analysis Services atualmente não podem ser acessados por meio de um gateway de dados do Power BI.

## <a name="azure-sql-database-authentication"></a>Autenticação do Banco de Dados SQL do Azure

Para fontes de dados do Banco de Dados SQL do Azure, você precisa definir um tipo de autenticação antes de executar o relatório. Isso se aplica somente quando você usa uma fonte de dados pela primeira vez em um workspace. Na primeira vez, você vê a seguinte mensagem:

![Publicando no Power BI](media/paginated-reports-data-sources/power-bi-paginated-publishing.png)

Se você não fornecer nenhuma credencial, ocorrerá um erro ao executar o relatório. Selecione **Continuar** para ir para a página **Credenciais da fonte de dados** para o relatório que você acabou de carregar:

![Configurações para o Banco de Dados SQL do Azure](media/paginated-reports-data-sources/power-bi-paginated-settings-azure-sql.png)

Selecione o link **Editar credenciais** para uma determinada fonte de dados para abrir a caixa de diálogo **Configurar**:

![Configurar o Banco de Dados SQL do Azure](media/paginated-reports-data-sources/power-bi-paginated-configure-azure-sql.png)

Para fontes de dados do Banco de Dados SQL do Azure, aqui estão os tipos de autenticação com suporte:

- Básico (nome de usuário e senha)
- SSO (logon único)
- OAuth2 (token AAD armazenado)

Para que o SSO e o OAuth2 funcionem corretamente, o servidor do Banco de Dados SQL do Azure ao qual a fonte de dados está se conectando precisa ter o [suporte à autenticação do AAD habilitado](https://docs.microsoft.com/azure/sql-database/sql-database-aad-authentication-configure). Para o método de autenticação OAuth2, o AAD gera um token e o armazena para acesso futuro à fonte de dados. Para usar o [método de autenticação de SSO](https://docs.microsoft.com/power-bi/service-azure-sql-database-with-direct-connect#single-sign-on) em vez disso, selecione a opção de SSO logo abaixo, **Usuários finais usam suas próprias credenciais de OAuth2 ao acessarem essa fonte de dados por meio de DirectQuery**.
  
## <a name="next-steps"></a>Próximas etapas

[Exibir um relatório paginado no serviço do Power BI](consumer/paginated-reports-view-power-bi-service.md)

Mais perguntas? [Experimente a Comunidade do Power BI](https://community.powerbi.com/)
