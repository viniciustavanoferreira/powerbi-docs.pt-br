---
title: Perguntas frequentes sobre o Power BI Embedded
description: Navegue por uma lista de perguntas frequentes e respostas sobre o Power BI Embedded.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 02/11/2020
ms.openlocfilehash: 0042c7db70cac103d04d1c48d06c12b71634b541
ms.sourcegitcommit: 444f7fe5068841ede2a366d60c79dcc9420772d4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/30/2020
ms.locfileid: "80403663"
---
# <a name="frequently-asked-questions-about-power-bi-embedded"></a>Perguntas frequentes sobre o Power BI Embedded

* Se você tiver outras dúvidas, [experimente perguntar à comunidade do Power BI](https://community.powerbi.com/).
* Ainda tem um problema? Acesse a [página de suporte do Power BI](https://powerbi.microsoft.com/support/).

## <a name="general"></a>Geral

### <a name="what-is-power-bi-embedded"></a>O que é o Power BI Embedded?

O [PBIE (Microsoft Power BI Embedded)](azure-pbie-what-is-power-bi-embedded.md) permite que os desenvolvedores de aplicativos insiram relatórios incríveis e totalmente interativos em aplicativos, sem precisar criar controles e visualizações de dados desde o início.

### <a name="who-is-the-target-audience-for-power-bi-embedded"></a>Quem é o público-alvo do Power BI Embedded?

Os desenvolvedores e as empresas de software, também como ISVs (fornecedores independentes de software), codificam os aplicativos.

### <a name="how-is-power-bi-embedded-different-from-power-bi-the-service"></a>Qual a diferença entre o Power BI Embedded e o serviço do Power BI?

O Power BI é uma solução de análise de software como serviço que fornece às organizações uma exibição única dos dados corporativos mais críticos.

A Microsoft desenvolveu o Power BI Embedded para ISVs que desejam inserir visuais em seus aplicativos para ajudar seus clientes a tomar decisões analíticas. Isso poupa os ISVs de precisar criar suas próprias soluções analíticas. A [análise integrada](embedding.md) permite que os usuários empresariais acessem os dados corporativos e executem consultas para gerar insights no aplicativo.


### <a name="what-is-the-difference-between-power-bi-premium-and-power-bi-embedded"></a>Qual é a diferença entre o Power BI Premium e o Power BI Embedded?

A capacidade do Power BI Premium é direcionada a empresas que desejam uma solução de BI completa para fornecer uma exibição única da organização, dos parceiros, dos clientes e dos fornecedores. O Power BI Premium ajuda a organização na tomada de decisões. O Power BI Premium é um produto SaaS que permite aos usuários consumir conteúdo por meio do portal do Power BI, de aplicativos móveis e de aplicativos desenvolvidos internamente.

O Power BI Embedded é para ISVs que desejam inserir visuais em seus aplicativos. O Power BI Embedded ajuda os clientes a tomar decisões por ser destinado aos desenvolvedores de aplicativos, de modo que os clientes desses aplicativos, incluindo qualquer pessoa dentro ou fora da organização, podem consumir o conteúdo armazenado na capacidade do Power BI Embedded. Não é possível compartilhar o conteúdo da capacidade do Power BI Embedded por meio de publicação com um clique na Web nem no SharePoint.

### <a name="what-is-the-microsoft-recommendation-for-when-a-customer-should-buy-power-bi-premium-vs-power-bi-embedded"></a>Segundo a recomendação da Microsoft, quando os clientes devem comprar o Power BI Premium e quando devem comprar o Power BI Premium vs. Power BI Embedded?

A Microsoft recomenda que as empresas comprem o Power BI Premium, uma solução de BI de nuvem de autoatendimento e nível empresarial. É recomendável que os ISVs comprem o Power BI Embedded para seus componentes de análise integrada habilitados para nuvem. No entanto, um cliente não tem restrição sobre qual produto comprar.

Pode haver alguns casos em que um ISV (normalmente de grande porte) deseja usar uma SKU P para obter os benefícios adicionais do serviço do Power BI predefinido na organização, bem como inseri-la nos aplicativos. Algumas empresas poderão decidir usar SKUs A no Azure se estiverem interessadas apenas em criar aplicativos de linha de negócios e em inserir análise neles, e não em usar o serviço do Power BI predefinido.

### <a name="how-many-embed-tokens-can-i-create"></a>Quantos tokens inseridos posso criar?

Os tokens inseridos com licença PRO destinam-se para teste de desenvolvimento, portanto, uma conta mestre ou [entidade de serviço](embed-service-principal.md) do Power BI pode gerar apenas um número limitado de tokens. [Compre uma capacidade](#technical) para inserir em um ambiente de produção. Não há limites para a quantidade de tokens inseridos que você pode gerar ao comprar uma capacidade. Acesse [Recursos Disponíveis](https://docs.microsoft.com/rest/api/power-bi/availablefeatures) para verificar o valor de uso que indica o uso inserido atual, em percentual.

## <a name="technical"></a>Técnico

### <a name="where-can-i-learn-more-about-capacity-and-skus-in-power-bi-embedded-analytics"></a>Onde posso aprender mais sobre capacidade e sobre SKUs na análise integrada do Power BI?

Confira o artigo [Capacidade e SKUs na análise integrada do Power BI](embedded-capacity.md).

### <a name="what-are-the-prerequisites-for-creating-a-pbie-capacity-in-azure"></a>Quais são os pré-requisitos para criar uma capacidade de PBIE no Azure?

* Entre no seu diretório organizacional (não compatível com contas Microsoft).
* Você precisa ter um locatário do Power BI, isto é, pelo menos um usuário em seu diretório deve estar inscrito no Power BI. 
* Você precisa ter uma assinatura do Azure em seu diretório organizacional.

### <a name="how-can-i-monitor-power-bi-embedded-capacity-consumption"></a>Como posso monitorar o consumo de capacidade do Power BI Embedded?

* Usando o [portal do administrador do Power BI](../../service-admin-portal.md#power-bi-embedded).

* Fazendo o download do [aplicativo de métricas](https://docs.microsoft.com/power-bi/service-admin-premium-monitor-capacity) no Power BI.

* Usando a [criação de log de diagnóstico do Azure](azure-pbie-diag-logs.md).

### <a name="can-my-capacity-scale-automatically-to-adjust-to-my-app-consumption"></a>Minha capacidade pode ser dimensionada automaticamente para ajustar-se ao consumo do aplicativo?

Embora não haja dimensionamento automático no momento, todas as APIs estão disponíveis para dimensionamento a qualquer momento.

### <a name="why-creatingscalingresuming-a-capacity-results-in-putting-the-capacity-into-a-suspended-state"></a>Por que criar/dimensionar/retomar uma capacidade resulta na capacidade em um estado suspenso?

O provisionamento da capacidade (dimensionar/retomar/criar) pode falhar. É possível usar a API Obter detalhes para verificar o ProvisioningState de uma capacidade: [Capacidades – Obter detalhes](https://docs.microsoft.com/rest/api/power-bi-embedded/capacities/getdetails).

### <a name="can-i-only-create-power-bi-embedded-capacities-in-a-specific-region"></a>Eu só posso criar as capacidades do Power BI Embedded em uma região específica?

Com o recurso [Multi-Geo (Versão Prévia)](embedded-multi-geo.md), você pode comprar uma [capacidade do Power BI Embedded](azure-pbie-create-capacity.md) em uma região diferente do local do seu locatário inicial do Power BI

### <a name="why-cant-i-see-a-workspace-although-i-have-permissions"></a>Por que não consigo ver um workspace mesmo tendo permissões?

Quando um usuário recebe permissões para um workspace, aplicativo ou artefato, ele pode não ser imediatamente disponibilizado por meio de chamadas à API.
O resultado pode ser um artefato ausente em uma resposta de API 'GET' ou um erro ao tentar usar o artefato.
O usuário pode resolver esse problema chamando a [API refreshUserPermissions](https://docs.microsoft.com/rest/api/power-bi/users/refreshuserpermissions), que atualiza as permissões de usuário.


### <a name="how-can-i-find-my-pbi-tenant-region"></a>Como localizar minha região de locatário do PBI?

Você pode usar o portal do PBI para localizar sua região de locatário do PBI.

[https://app.powerbi.com/](`https://app.powerbi.com/`) > ? > Sobre o Power BI

![Sobre o Power BI](media/embedded-faq/about-01.png)
![Região do locatário](media/embedded-faq/tenant-location-01.png)

### <a name="what-does-the-cloud-solution-provider-csp-channel-support"></a>O que é compatível com o canal CSP (Provedor de Soluções na Nuvem)?

* É possível criar o PBIE para seu locatário com o tipo de assinatura CSP
* A conta de parceiro pode ser conectada ao locatário do cliente e comprar o PBIE para o locatário do cliente, especificando o usuário do locatário do cliente como administrador de capacidade do Power BI

### <a name="why-do-i-get-an-unsupported-account-message"></a>Por que recebo uma mensagem de conta sem suporte?

O Power BI exige que você se inscreva com uma conta organizacional. Não é possível tentar se inscrever no Power BI usando uma conta Microsoft.

### <a name="can-i-use-apis-to-create-and-manage-azure-capacities"></a>Posso usar as APIs para criar e gerenciar as capacidades do Azure?

Sim, há cmdlets do PowerShell e APIs REST do Azure Resource Manager que você pode usar para criar e gerenciar recursos de PBIE.

* [APIs REST](https://docs.microsoft.com/rest/api/power-bi-embedded/) 
* [Cmdlets do PowerShell](https://docs.microsoft.com/powershell/module/azurerm.powerbiembedded/)

### <a name="what-is-the-pbi-embedded-dedicated-capacity-role-in-a-pbi-embedded-solution"></a>O que é a função de capacidade dedicada do PBI Incorporado em uma solução de PBI Incorporado?

Para [promover sua solução para produção](embed-sample-for-customers.md#move-to-production), é preciso atribuir o conteúdo do Power BI (workspace) que seu aplicativo usa a uma capacidade do Power BI Embedded (uma SKU).

### <a name="in-what-azure-regions-is-pbi-embedded-available"></a>Em quais regiões do Azure o PBI Embedded está disponível?

[PAM](https://ecosystemmanager.azurewebsites.net/home) (EcoManager) – consulte o gerenciador de disponibilidade do produto

Regiões disponíveis (16 – nas mesmas regiões que o Power BI)

* EUA (6) – Leste dos EUA, Leste dos EUA 2, Centro-Norte dos EUA, Centro-Sul dos EUA, Oeste dos EUA, Oeste dos EUA 2
* Europa (2) – Norte da Europa, Europa Ocidental
* Pacífico Asiático (2) – Sudeste Asiático, Leste da Ásia
* Brasil (1) – Sul do Brasil
* Japão (1) – Leste do Japão
* Austrália (1) – Sudeste da Austrália
* Índia (1) – Oeste da Índia
* Canadá (1) – Canadá Central
* Reino Unido (1) – Sul do Reino Unido

### <a name="what-is-power-bi-embeddeds-authentication-model"></a>Qual é o modelo de autenticação do Power BI Embedded?

O Power BI Embedded continua usando o Azure AD para autenticação do usuário mestre (um usuário licenciado designado do Power BI Pro) ou com [entidade de serviço](embed-service-principal.md) para autenticar o aplicativo dentro do Power BI.  

 Um ISV pode implementar suas próprias autenticação e autorização para seus aplicativos.

Se já tiver um locatário do Azure AD, você poderá usar seu diretório existente. Você também pode criar um novo locatário do Azure AD para segurança de conteúdo do aplicativo inserido.

Para obter um token do AAD, você pode usar uma das [Bibliotecas de Autenticação do Azure Active Directory](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-libraries). Bibliotecas de cliente estão disponíveis para várias plataformas.

### <a name="my-application-already-uses-aad-for-user-authentication-how-can-we-use-this-identity-when-authenticating-to-power-bi-in-a-user-owns-data-scenario"></a>Meu aplicativo já utiliza o AAD para autenticação do usuário. Como podemos usar essa identidade ao fazer a autenticação com o Power BI em um cenário "User Owns Data"?

É o fluxo On-Behalf-Of do OAuth padrão (<https://docs.microsoft.com/azure/active-directory/develop/web-api>). O aplicativo precisa ser configurado para exigir permissões para o serviço do Power BI (com os escopos necessários). Quando tiver um token de usuário no aplicativo, bastará chamar a API ADAL AcquireTokenAsync usando o token de acesso de usuário e especificar a URL do recurso do Power BI como a ID do recurso:

```csharp
var context = new AD.AuthenticationContext(authorityUrl);
var userAssertion = new AD.UserAssertion(userAccessToken);
var clientAssertion = new AD.ClientAssertionCertificate(MyAppId, MyAppCertificate)
var authenticationResult = await context.AcquireTokenAsync(resourceId, clientAssertion, userAssertion);
```

### <a name="what-object-id-is-the-service-principal-object-id"></a>Qual ID de objeto é a ID de objeto da entidade de serviço?

A *ID de objeto* na tela principal de um aplicativo registrado é a ID de objeto para o aplicativo.

A ID de objeto encontrada na seção *Aplicativo gerenciado no diretório local > Propriedades* é a ID de objeto de entidade de serviço que você precisa usar. Essa ID de objeto é para fazer referência a uma entidade de serviço para operações ou fazer alterações na ID de objeto da entidade de serviço. Como aplicar uma entidade de serviço como um administrador a um workspace.

### <a name="how-is-power-bi-embedded-different-from-other-azure-services"></a>Qual a diferença entre o Power BI Embedded e os serviços do Azure?

É necessário ter uma conta do Power BI antes de comprar o Power BI Embedded no Azure. A região implantada do Power BI Embedded determina sua conta do Power BI. Gerencie o recurso do Power BI Embedded no Azure para:

* Aumentar/reduzir
* Adicionar administradores de capacidade
* Pausar/retomar serviço

Use o PowerBI.com para atribuir/cancelar a atribuição de workspaces à capacidade do Power BI Embedded.

### <a name="what-content-pack-data-types-can-you-embed"></a>Quais tipos de dados do pacote de conteúdo podem ser inseridos?

*Não é possível* inserir **Dashboards** e **Blocos** criados com conjuntos de dados do pacote de conteúdo. No entanto, você *pode* inserir **relatórios** criados com um conjunto de dados do pacote de conteúdo.

### <a name="what-is-the-difference-between-using-row-level-security-rls-vs-javascript-filters"></a>Qual é a diferença entre usar filtros RLS (Segurança em Nível de Linha) em vez de JavaScript?

Costuma-se confundir quando usar filtros JavaScript e filtros RLS porque um método trata de como controlar o que um usuário específico pode ver e o outro trata de como otimizar a exibição do usuário.

Para RLS, o desenvolvedor ISV controla a filtragem de dados como parte da criação do modelo e da geração de tokens inseridos. O usuário final vê apenas o que o ISV permitir. Neste caso, o usuário pode optar por ver menos do que o que está sendo filtrado, mas não conseguirá ignorar a configuração de RLS e ver mais do que o permitido.

Para filtragem do lado cliente (JavaScript ), o ISV pode decidir o que o usuário final vê na exibição inicial, mas não pode controlar as alterações que o usuário final pode aplicar à própria exibição. Como o código do cliente Javascript do usuário pode disparar a filtragem de dados no back-end, ele não pode ser considerado seguro.

Confira mais detalhes na referência [Filtros RLS vs JavaScript](embedded-row-level-security.md#using-rls-vs-javascript-filters).

### <a name="how-do-i-manage-permissions-for-service-principals-with-power-bi"></a>Como faço para gerenciar as permissões para as entidades de serviço com o Power BI?

Depois que você habilita a [entidade de serviço](embed-service-principal.md) para ser usada com o Power BI, as permissões do AD do aplicativo não estarão mais em vigor. As permissões do aplicativo então são gerenciadas por meio do portal de administração do Power BI.

As entidades de serviço herdam as permissões para todas as configurações de locatário do Power BI de seu grupo de segurança. Para restringir permissões, crie um grupo de segurança dedicado para entidades de serviço e adicione-o à lista **Exceto grupos de segurança específicos** para as configurações relevantes habilitadas do Power BI.

Essa situação é importante quando você adiciona a entidade de serviço como um **admin** ao novo workspace. Você pode gerenciar essa tarefa por meio de [APIs](https://docs.microsoft.com/rest/api/power-bi/groups/addgroupuser) ou com o serviço do Power BI.

### <a name="when-to-use-an-application-id-vs-a-service-principal-object-id"></a>Quando usar uma ID de aplicativo versus uma ID de objeto de entidade de serviço?

A **[ID do aplicativo](embed-sample-for-customers.md#application-id)** é usada para criar o token de acesso ao passar a ID do aplicativo para autenticação.

Para fazer referência a uma entidade de serviço para operações ou fazer alterações, você usa a **[ID de objeto de entidade de serviço](embed-service-principal.md)** – por exemplo, aplicação de uma entidade de serviço como um administrador a um workspace.

### <a name="can-you-manage-an-on-premises-data-gateway-with-service-principal"></a>Você pode gerenciar um gateway de dados local com a entidade de serviço?

Você não pode gerenciar um gateway de dados local (gateway de dados) usando uma [entidade de serviço](embed-service-principal.md) como você pode fazer com uma conta mestra.

Com uma conta mestra, você pode instalar um gateway de dados, adicionar usuários ao gateway, conectar-se a fontes de dados e realizar outras tarefas administrativas.

Com a entidade de serviço, você pode configurar [RLS (segurança em nível de linha)](embedded-row-level-security.md#on-premises-data-gateway-with-service-principal) usando uma fonte de dados de conexão ativa local do SSAS (SQL Server Analysis Services). Dessa forma, você pode gerenciar usuários e o acesso a dados no SSAS ao integrar com o **Power BI Embedded** usando uma entidade de serviço.

### <a name="can-you-sign-into-the-power-bi-service-with-service-principal"></a>Você pode entrar no serviço do Power BI com a entidade de serviço?

Não, você não pode entrar no Power BI usando a entidade de serviço.

Além disso, você não pode consumir conteúdo como usuário em aplicativos externos (SaaS inserido), apenas ao gerar um token inserido.

### <a name="what-are-the-best-practices-to-improve-performance"></a>Quais são as práticas recomendadas para melhorar o desempenho?

[Desempenho do Power BI Embedded](embedded-performance-best-practices.md)

## <a name="licensing"></a>Licenças

### <a name="how-do-i-purchase-power-bi-embedded"></a>Como fazer para comprar o Power BI Embedded?

O Power BI Embedded está disponível por meio do Azure.

### <a name="what-happens-if-i-already-purchased-power-bi-premium-and-now-i-want-some-power-bi-embedded-in-azure-benefits"></a>O que acontece se já comprei o Power BI Premium e agora quero alguns dos benefícios do Power BI Embedded no Azure?

Os clientes continuam a pagar pelas compras existentes do Power BI Premium até o término do prazo do contrato atual e, então, podem mudar as compras do Power BI Premium conforme necessário naquele momento.

### <a name="do-i-still-have-to-buy-power-bi-premium-to-get-access-to-power-bi-embedded"></a>Ainda preciso comprar o Power BI Premium para obter acesso ao Power BI Embedded?

Não, o Power BI Embedded inclui a capacidade baseada no Azure de que você precisa para implantar e distribuir sua solução aos clientes.

### <a name="whats-the-purchase-commitment-for-power-bi-embedded"></a>O que é a confirmação de compra para o Power BI Embedded?

Os clientes podem alterar o uso a cada hora. Não há nenhum compromisso mensal nem anual pelo serviço do Power BI Embedded.

### <a name="how-does-the-usage-of-power-bi-embedded-show-up-on-my-bill"></a>Como o uso do Power BI Embedded aparece na minha fatura?

O Power BI Embedded é cobrado em uma taxa por hora previsível com base nos tipos de nós implantados. Enquanto o recurso estiver ativo, você será cobrado, mesmo que não haja uso. Você precisa pausar o recurso para interromper a cobrança.

### <a name="who-needs-a-power-bi-pro-license-for-power-bi-embedded-and-why"></a>Quem precisa de uma licença do Power BI Pro para o Power BI Embedded e por quê?

Você precisa de uma licença do Power BI Pro ou uma [entidade de serviço](embed-service-principal.md) para usar APIs REST. Para adicionar relatórios a um workspace do Power BI, um analista precisa de uma licença do Power BI Pro ou de uma entidade de serviço. Para gerenciar o locatário e a capacidade do Power BI, um administrador precisará ter uma licença do Power BI Pro.

Uma vez que o Power BI Embedded permite o uso do portal do Power BI para gerenciar e validar o conteúdo inserido, a licença do Power BI Pro é necessária para autenticar o aplicativo no PowerBI.com para a obtenção do acesso aos relatórios nos repositórios corretos.

No entanto, para a [criação/edição de relatórios inseridos](https://github.com/Microsoft/PowerBI-JavaScript/wiki/Create-Report-in-Embed-View) dentro de seu aplicativo, o usuário final não precisa ter uma licença Pro, pois ele não precisa ser um usuário do Power BI.

### <a name="can-i-get-started-for-free"></a>Posso começar gratuitamente?

Sim. Você pode usar os [créditos Azure](https://azure.microsoft.com/free/) para o Power BI Embedded.

### <a name="can-i-get-a-trial-experience-for-power-bi-embedded-in-azure"></a>Posso experimentar uma avaliação do Power BI Embedded no Azure?

Como o Power BI Embedded faz parte do Azure, é possível usar o serviço com o [crédito de US$ 200 recebido durante a inscrição no Azure](https://azure.microsoft.com/free/).

### <a name="is-power-bi-embedded-available-for-national-clouds-us-government-germany-china"></a>O Power BI Embedded está disponível para nuvens nacionais (Governo dos EUA, Alemanha, China)?

O Power BI Embedded também está disponível para as [nuvens nacionais](embed-sample-for-customers-national-clouds.md).

### <a name="is-power-bi-embedded-available-for-non-profits-and-educational"></a>O Power BI Embedded está disponível para entidades sem fins lucrativos e educacionais?

Não há preço especial do Azure para entidades sem fins lucrativos e educacionais.

## <a name="power-bi-workspace-collection"></a>Coleção de workspaces do Power BI

### <a name="what-is-power-bi-workspace-collection"></a>O que é a Coleção de workspaces do Power BI?

A **Coleção de Workspaces do Power BI** (**Power BI Embedded** versão 1) é uma solução baseada no recurso de **Coleção de Workspaces do Power BI** do Azure. Essa solução permite criar aplicativos do **Power BI Embedded** para seus clientes usando conteúdo do Power BI na solução **Coleção de workspaces do Power BI**, APIs dedicadas e chaves de coleção de workspaces para autenticar o aplicativo no Power BI.

### <a name="can-i-migrate-from-power-bi-workspace-collection-to-power-bi-embedded"></a>Posso migrar da Coleção de workspaces do Power BI para o Power BI Embedded?

1. Você pode usar a ferramenta de migração para clonar o conteúdo da **Coleção de workspaces do Power BI** no Power BI – https://docs.microsoft.com/power-bi/developer/migrate-from-powerbi-embedded#content-migration.

2. Comece com o POC do aplicativo **Power BI Embedded** que usa o conteúdo do Power BI.

3. Quando estiver pronto para a produção, compre uma capacidade dedicada do **Power BI Embedded** e atribua seu conteúdo do Power BI (workspace) a essa capacidade.

    > [!Note]
    > Você pode continuar usando a **Coleção de workspaces do Power BI** enquanto compila em paralelo com uma solução **Power BI Embedded**. Quando estiver pronto, você poderá mover o cliente para a nova solução **Power BI Embedded** e desativar a solução **Coleção de Workspaces do Power BI**.

Para obter mais informações, confira [Como migrar o conteúdo da Coleção de workspaces do Power BI para o Power BI Embedded](https://docs.microsoft.com/power-bi/developer/migrate-from-powerbi-embedded)

### <a name="is-power-bi-workspace-collection-on-a-deprecation-path"></a>A Coleção de Workspaces do Power BI está a caminho de ser preterida?

Sim, mas os clientes que já estão usando a solução **Coleção de Workspaces do Power BI** podem continuar usando-a até que seja preterida. Os clientes também podem criar novas coleções de workspaces e qualquer aplicativo do **Power BI Embedded** que ainda usa a **Coleção de Workspaces do Power BI**.

No entanto, isso também significa que os novos recursos não são adicionados a soluções de **Coleção de Workspaces do Power BI**. Incentivamos os clientes a planejar sua migração para a nova solução **Power BI Embedded**.

### <a name="when-is-power-bi-workspace-collection-support-discontinued"></a>Quando o suporte de coleção de workspaces do Power BI foi descontinuado?

Os clientes que já usam a solução **Coleções de workspace do Power BI** podem continuar usando-a até o final de junho de 2018 ou até o término do contrato de suporte.

### <a name="in-what-regions-can-i-create-a-pbi-workspace-collection"></a>Em quais regiões a Coleção de workspaces do PBI pode ser criada?

As regiões disponíveis são Sudeste da Austrália, Sul do Brasil, Canadá Central, Leste dos EUA 2, Leste do Japão, Centro-Norte dos EUA, Norte da Europa, Centro-Sul dos EUA, Sudeste Asiático, Sul do Reino Unido, Europa Ocidental, Oeste da Índia e Oeste dos EUA.

### <a name="why-should-i-migrate-from-pbi-workspace-collection-to-power-bi-embedded"></a>Por que migrar da Coleção de Workspaces do PBI para o Power BI Embedded?

Há novos recursos e funcionalidades na solução **Power BI Embedded** que não podem ser usados com a **Coleção de Workspaces do Power BI**.

Alguns deles são:
* Todas as fontes de dados do PBI são compatíveis. Apenas duas fontes de dados da **Coleção de Workspaces do Power BI** são compatíveis. 
* Os novos recursos como P e R, atualizar, indicadores, inserção de painéis e blocos, menu personalizado etc. só têm suporte na solução **Power BI Embedded**.
* Modelo de cobrança por capacidade.

## <a name="embedding-setup-tool"></a>Ferramenta de configuração de inserção

### <a name="what-is-the-embedding-setup-tool"></a>O que é a ferramenta de configuração de inserção?

A [Ferramenta de configuração de inserção](https://aka.ms/embedsetup) permite iniciar rapidamente e baixar um aplicativo de exemplo para começar a inserção com o Power BI.

### <a name="which-solution-should-i-choose"></a>Qual solução devo escolher?

* A [inserção para clientes](embedding.md#embedding-for-your-customers) fornece a capacidade de inserir os dashboards e relatórios para usuários que não têm uma conta do Power BI. Execute a solução [Inserir para clientes](https://aka.ms/embedsetup/AppOwnsData).
* A [inserção para a organização](embedding.md#embedding-for-your-organization) permite que você estenda o serviço do Power BI. Execute a solução [Inserir para a organização](https://aka.ms/embedsetup/UserOwnsData).

### <a name="ive-downloaded-the-sample-app-which-solution-do-i-choose"></a>Baixei o aplicativo de exemplo. Qual solução devo escolher?

Se você estiver trabalhando com a experiência **Inserir para clientes**, salve e descompacte o arquivo *PowerBI-Developer-Samples.zip*. Em seguida, abra a pasta *PowerBI-Developer-Samples-master\App Owns Data* e execute o arquivo *PowerBIEmbedded_AppOwnsData.sln*.

Se você estiver trabalhando com a experiência **Inserir para a organização**, salve e descompacte o arquivo *PowerBI-Developer-Samples.zip*. Abra a pasta *PowerBI-Developer-Samples-master\User Owns Data\integrate-report-web-app* e execute o arquivo *pbi-saas-embed-report.sln*.

### <a name="how-can-i-edit-my-registered-application"></a>Como posso editar meu aplicativo registrado?

Confira como editar os aplicativos registrados no Azure AD no [Guia de Início Rápido: Atualizar um aplicativo no Azure Active Directory](https://docs.microsoft.com/azure/active-directory/develop/quickstart-v1-update-azure-ad-app).

### <a name="how-can-i-edit-my-power-bi-user-profile-or-data"></a>Como editar meu perfil do usuário os dados no Power BI?

Você pode aprender a editar os dados do Power BI [aqui](https://docs.microsoft.com/power-bi/service-basic-concepts).

Para saber mais, veja [Solução de problemas de seu aplicativo inserido](embedded-troubleshoot.md).

Mais perguntas? [Experimente a Comunidade do Power BI](https://community.powerbi.com/)
