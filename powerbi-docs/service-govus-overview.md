---
title: Clientes do Power BI for US Government – Visão geral
description: Os clientes do Power BI for US Government podem adicionar uma assinatura do Power BI Pro ao plano do Microsoft 365 Government. Saiba como se inscrever e examinar a disponibilidade de recursos nesta descrição de serviço.
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/07/2020
ms.author: kfollis
LocalizationGroup: Get started
ms.openlocfilehash: a9a5f3fd5304e64209b6069741dffcc3fa9b07c8
ms.sourcegitcommit: c772c544ce2e1e2a147b9b62e5579ac3cb59d54c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/29/2020
ms.locfileid: "82256150"
---
# <a name="power-bi-for-us-government-customers"></a>Clientes do Power BI for US Government
Este artigo se destina aos clientes do Governo dos EUA que estão implantando o Power BI como parte de um plano do Office 365 Government. Os planos governamentais são projetados para as necessidades exclusivas das organizações que devem atender aos padrões de conformidade e segurança dos EUA. O serviço do Power BI projetado para os clientes do Power BI for US Government é diferente da versão comercial do serviço do Power BI. As funcionalidades e diferenças do recurso estão descritas nas seções a seguir.

## <a name="add-power-bi-to-your-office-365-government-plan"></a>Inclusão do Power BI ao seu plano do Office 365 Government

Antes de assinar e atribuir licenças aos usuários para o Power BI for US Government, é preciso se inscrever em um plano do Office 365 Government. Se sua organização já tiver um plano do Office 365 Government, passe para [Comprar uma assinatura governamental do Power BI Pro](#purchase-a-power-bi-pro-government-subscription).

### <a name="enroll-in-office-365-government-plan"></a>Inscrever-se no plano do Office 365 Government

Caso seja um novo cliente, será preciso validar a qualificação da sua organização antes de se inscrever em um plano governamental.  Comece preenchendo o [formulário de validação de qualificação do Office 365 para o Governo](https://www.microsoft.com/microsoft-365/government/eligibility-validation). Para garantir a seleção do plano adequado para sua organização, confira as [descrições de serviço do Office 365 para o Governo dos EUA](https://docs.microsoft.com/office365/servicedescriptions/office-365-platform-service-description/office-365-us-government/office-365-us-government).

> [!NOTE]
> Se você já tiver implantado o Power BI em um ambiente comercial e quiser migrar para a nuvem do Governo dos EUA, será preciso adicionar uma nova assinatura do Power BI Pro a seu plano do Office 365 Government. Em seguida, replique os dados comerciais no serviço do Power BI for US Government, remova as atribuições de licença comercial das contas de usuário e atribua a elas uma licença governamental do Power BI Pro.
>
>
## <a name="government-cloud-instances"></a>Instâncias de nuvem do governo
O Office 365 fornece diversos ambientes para que as agências governamentais atendam aos vários requisitos de conformidade. Confira detalhes específicos do que é fornecido em cada ambiente nas descrições de serviço vinculadas.

* A [GCC (Nuvem da Comunidade Governamental) do Office 365](https://docs.microsoft.com/office365/servicedescriptions/office-365-platform-service-description/office-365-us-government/gcc) foi projetada para o governo federal, estadual e local.

* A [GCC High (Nuvem da Comunidade Governamental High) do Office 365](https://docs.microsoft.com/office365/servicedescriptions/office-365-platform-service-description/office-365-us-government/gcc-high-and-dod) foi projetada para as agências federais, os setores de defesa e aeroespacial e outras organizações que mantêm informações controladas não confidenciais. Esse ambiente é adequado para organizações de segurança nacional e empresas que têm dados ITAR (Normas de Tráfego Internacional de Armas) ou requisitos DFARS (Suplemento do Regulamento de Aquisição Federal para a Defesa).

* O [ambiente do Office 365 DoD](https://docs.microsoft.com/office365/servicedescriptions/office-365-platform-service-description/office-365-us-government/gcc-high-and-dod) foi projetado exclusivamente para o Departamento de Defesa dos EUA. 

## <a name="connect-to-power-bi-for-us-government"></a>Conexão ao Power BI for US Government

A URL para se conectar ao Power BI para o Governo dos EUA é diferente da usada para os usuários comerciais. Use as seguintes URLs para entrar no Power BI:

| Versão comercial  | GCC  | GCC High | DoD |
| --- | --- | --- | --- |
| [https://app.powerbi.com/](https://app.powerbi.com) |[https://app.powerbigov.us](https://app.powerbigov.us) | [https://app.high.powerbigov.us](https://app.high.powerbigov.us) | [https://app.mil.powerbigov.us](https://app.mil.powerbigov.us) |

Sua conta pode estar provisionada para mais de uma nuvem. Nesse caso, ao usar o Power BI Desktop, é possível escolher a qual nuvem se conectar quando entrar.

## <a name="purchase-a-power-bi-pro-government-subscription"></a>Compra de uma assinatura governamental do Power BI Pro

Depois de implantar o Office 365, é possível adicionar uma assinatura do Power BI. Siga as instruções passo a passo em [Registrar sua organização do Governo dos EUA](service-govus-signup.md) para comprar o serviço governamental do Power BI Pro. Compre licenças suficientes para todos os usuários que precisam usar o Power BI e as atribua às contas de usuário individuais.

> [!IMPORTANT]
> O Power BI for US Government não está disponível como uma licença gratuita. Cada usuário deve ter uma licença Pro para acessar a Nuvem da Comunidade Governamental. Se uma conta de usuário tiver uma licença gratuita atribuída, ela será autorizada a acessar apenas a nuvem comercial e encontrará problemas de autenticação e de acesso. Se você comprou o Power BI Premium, não precisa atribuir licenças Pro para habilitar o acesso do usuário.  Qualquer usuário na organização pode acessar relatórios compartilhados com eles, desde que o relatório seja publicado em uma capacidade Premium. Examine as diferenças entre os tipos de licença em [Recursos do serviço do Power BI por tipo de licença](service-features-license-type.md).
>
>

## <a name="connectivity-between-government-and-global-azure-cloud-services"></a>Conectividade entre os Serviços de Nuvem do Azure globais e governamentais

O Azure é distribuído em várias nuvens. Por padrão, a habilitação de regras de firewall para abrir uma conexão com uma instância específica da nuvem é possível, mas a rede entre nuvens é diferente.  Para se comunicar entre serviços na nuvem pública e serviços na Nuvem da Comunidade Governamental, é preciso configurar regras de firewall específicas. Por exemplo, se você quiser acessar instâncias da nuvem pública do SQL usando sua implantação da nuvem governamental do Power BI, precisará de uma regra de firewall no SQL. Configure regras de firewall específicas no SQL para permitir conexões à Nuvem do Azure Governamental para os seguintes data centers:

* Gov. EUA – Iowa
* Gov. EUA – Virgínia
* Gov. EUA – Texas
* Gov. EUA – Arizona

Na nuvem pública, os intervalos de IP estão disponíveis. Baixe o arquivo [Marcas de serviço e intervalos de IP do Azure – Nuvem do Governo dos EUA](https://www.microsoft.com/download/details.aspx?id=57063) para obter os intervalos de IP da Nuvem do Governo dos EUA. 

Siga as etapas em [Criar e gerenciar regras de firewall de IP](https://docs.microsoft.com/azure/sql-database/sql-database-firewall-configure#create-and-manage-ip-firewall-rules) para configurar firewalls no SQL.

## <a name="power-bi-feature-availability"></a>Disponibilidade do recurso do Power BI

Para atender aos requisitos dos clientes de nuvem governamental, existem algumas diferenças entre planos comerciais e governamentais. Confira na tabela a seguir quais recursos estão disponíveis em cada ambiente governamental.

|Recurso |   |GCC |GCC-High |DoD|
|------|------|------|------|------|
|Administração|Licenças gratuitas|Não disponível|Não disponível|Não disponível|
|  |Definição de limites de armazenamento de dados|Disponível|Disponível|Disponível|
|  |Uso de grupos do Active Directory para o compartilhamento e o controle de acesso|Disponível|Disponível|Disponível|
|  |Auditoria por meio do Centro de Conformidade e Segurança do Office 365|Disponível|Disponível|Disponível|
|  |Compartilhamento de usuários externos|Disponível|Disponível|Disponível|
|  |Métricas de uso para relatórios e painéis|Não disponível|Não disponível|Não disponível|
|  |B2B do Azure entre GCC e nuvem comercial|Não disponível|Não disponível|Não disponível|
|Criação de relatório|Criar e exibir dashboards e relatórios|Disponível|Disponível|Disponível|
|  |Atualização de dados agendada|Disponível|Disponível|Disponível|
|  |Dashboards de equipe atualizáveis|Disponível|Disponível|Disponível|
|  |Relatórios paginados|Disponível|No roteiro|No roteiro|
|  |Aplicativos de modelo|Não disponível|Não disponível|Não disponível|
|Conectar aos dados|Importação de dados e relatórios do Excel|Disponível|Disponível|Disponível|
|  |Importação de dados de arquivos CSV|Disponível|Disponível|Disponível|
|  |Importação de dados de arquivos do Power BI Desktop|Disponível|Disponível|Disponível|
|  |Conectividade com o CDS|Disponível|Não disponível|Não disponível|
|  |Conector do Azure Data Lake Storage Gen2|Disponível|Não disponível|Não disponível|
|Gerenciamento de dados|Gateway de gerenciamento de dados|Disponível|Disponível|Disponível|
|  |Criptografia de dados no SQL do Azure|Disponível|Disponível|Disponível|
|  |Criptografia de dados no Armazenamento de Blobs para Power BI|Disponível|Disponível|Disponível|
|Integração entre produtos|Inserção no SharePoint Online usando a Web Part do Power BI|Não disponível|Não disponível|Não disponível|
|  |Inserção no SharePoint Online usando a Web Part|Disponível|Disponível|Disponível|
|  |Funções de IA e fluxos de dados|Não disponível|Não disponível|Não disponível|
|  |Conectividade do Power Automate para alertas controlados por dados|Não disponível|Não disponível|Não disponível|
|  |Guia do Power BI no Teams|Disponível|Não disponível|Não disponível|
|  |Automatizado de Machine Learning|Não disponível|Não disponível|Não disponível|
|  |Serviços Cognitivos|Não disponível|Não disponível|Não disponível|
|  |Azure ML|Não disponível|Não disponível|Não disponível|

## <a name="next-steps"></a>Próximas etapas

* [Inscrever-se para o Power BI for US Government](service-govus-signup.md)
* [Microsoft Power Apps US Government](https://docs.microsoft.com/power-platform/admin/powerapps-us-government)
* [Power Automate US Government](https://docs.microsoft.com/power-automate/us-govt)
* <a href="https://channel9.msdn.com/Blogs/Azure/Cognitive-Services-HDInsight-and-Power-BI-on-Azure-Government">Demonstração do governo dos EUA do Power BI</a>
