---
title: O que são os aplicativos de modelo do Power BI?
description: Este artigo é uma visão geral do programa de aplicativos de modelo do Power BI. Saiba como criar aplicativos do Power BI com pouca ou nenhuma codificação e implantá-los para qualquer cliente do Power BI.
author: paulinbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 12/17/2019
ms.author: painbar
ms.openlocfilehash: 528c86a75e2f255ad502dbdf973a61cd9de693d4
ms.sourcegitcommit: 8e3d53cf971853c32eff4531d2d3cdb725a199af
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/04/2020
ms.locfileid: "75224142"
---
# <a name="what-are-power-bi-template-apps"></a>O que são os aplicativos de modelo do Power BI?

Os novos *aplicativos de modelo* do Power BI permitem que os parceiros do Power BI criem aplicativos do Power BI com pouca ou nenhuma codificação e implante-os para qualquer cliente do Power BI.  Este artigo é uma visão geral do programa de aplicativos de modelo do Power BI.

Os aplicativos de modelo são uma substituição dos atuais pacotes de conteúdo do serviço. Como parceiro do Power BI, você cria um conjunto de conteúdo pronto para uso por seus clientes e o publica por conta própria.  

Você cria aplicativos de modelo que permitem que seus clientes se conectem e criem instâncias dentro das próprias contas. Como especialistas em domínio, eles podem desbloquear os dados de modo a facilitar o consumo para usuários empresariais.  

Você envia seus aplicativos de modelo ao Portal do Cloud Partner. Os aplicativos são disponibilizados publicamente no [ marketplace de aplicativos do Power BI](https://app.powerbi.com/getdata/services) e no [Microsoft AppSource](https://appsource.microsoft.com/?product=power-bi). Aqui está uma visão de alto nível da experiência de criação do aplicativo de modelo público.

## <a name="power-bi-apps-marketplace"></a>Marketplace de aplicativos do Power BI

Os aplicativos de modelo do Power BI permitem que os usuários do Power BI Pro ou Power BI Premium obtenham informações imediatas por meio de painéis e relatórios predefinidos que podem ser conectados a fontes de dados ativas. Muitos aplicativos do Power BI já estão disponíveis no [Marketplace de aplicativos do Power BI](https://app.powerbi.com/getdata/services).

|  |
|     :---:      |
| [![Microsoft Project Web App](./media/service-template-apps-overview/project-web.png)](https://app.powerbi.com/groups/me/getapps/services/pbi_msprojectonline.pbi-microsoftprojectwebapp) [![Aplicativo Web do Backup do Azure](./media/service-template-apps-overview/azure-backup.png)](https://app.powerbi.com/groups/me/getapps/services/pbi-azurebackup.pbi-azurebackup-template) [![Aplicativo Web do Dynamic 365 Business Central – Sales](./media/service-template-apps-overview/dynamics-sales.png)](https://app.powerbi.com/groups/me/getapps/services/microsoftdynsmb.businesscentral_sales) [![Aplicativo Web do Microsoft Forms Pro Customer Satisfaction](./media/service-template-apps-overview/forms-pro.png)](https://app.powerbi.com/groups/me/getapps/services/msfp.formsprocustomersatisfaction) |
|  |

## <a name="process"></a>Processo
O processo geral para desenvolver e enviar um aplicativo de modelo envolve vários estágios. Alguns estágios podem incluir mais de uma atividade ao mesmo tempo.


| Estágio | Power BI Desktop |  |Serviço do Power BI  |  |Portal do Cloud Partner  |
|---|--------|--|---------|---------|---------|
| **Um** | Criar um modelo de dados e um relatório em um arquivo .pbix |  | Criar um workspace. Importar um arquivo .pbix. Criar um dashboard complementar  |  | Registrar-se como parceiro |
| **Dois** |  |  | Criar um pacote de teste e executar a validação interna        |  | |
| **Três** | |  | Promover o pacote de teste à pré-produção para validação fora do locatário do Power BI e enviá-lo ao AppSource  |  | Com o pacote de pré-produção, criar uma oferta do aplicativo de modelo do Power BI e iniciar o processo de validação |
| **Quatro** | |  | Promover o pacote de pré-produção à produção |  | Ativá-lo |

## <a name="before-you-begin"></a>Antes de começar

Para criar o aplicativo de modelo, você precisará ter permissões para criar um. Confira o portal de administração do Power BI, configurações de Aplicativo de modelo para obter mais detalhes. 

Para publicar um aplicativo de modelo no serviço do Power BI e no AppSource, é necessário atender aos requisitos para [se tornar um Editor do Marketplace de Nuvem](https://docs.microsoft.com/azure/marketplace/become-publisher).
 
## <a name="high-level-steps"></a>Etapas de alto nível

Veja a seguir as etapas de alto nível. 

1. [Examinar os requisitos](#requirements) e verificar se você atende a todos eles. 

2. Criar um relatório no Power BI Desktop. Usar parâmetros para salvá-lo como um arquivo que possa ser usado por outras pessoas. 

3. Criar um workspace para o aplicativo de modelo em seu locatário no serviço do Power BI (app.powerbi.com). 

4. Importar o arquivo .pbix e adicionar conteúdo, como um dashboard ao aplicativo. 

5. Criar um pacote de teste para testar o aplicativo de modelo em sua organização. 

6. Promover o aplicativo de teste à pré-produção para enviá-lo para validação no AppSource e testá-lo fora de seu próprio locatário. 

7. Enviar o conteúdo à Plataforma do Cloud Partner para publicação. 

8. Ative sua oferta no AppSource e mova o aplicativo para produção no Power BI.

9. Agora você poderá iniciar o desenvolvimento da próxima versão no mesmo workspace, em pré-produção. 

## <a name="requirements"></a>Requisitos

Para criar o aplicativo de modelo, você precisará ter permissões para criar um. Confira o [portal de administração do Power BI, configurações de Aplicativo de modelo](service-admin-portal.md#template-apps-settings) para obter mais detalhes. 

Para publicar um aplicativo de modelo no serviço do Power BI e no AppSource, é necessário atender aos requisitos para [se tornar um Editor do Marketplace de Nuvem](https://docs.microsoft.com/azure/marketplace/become-publisher).
 > [!NOTE] 
 > Envios de aplicativos de modelo são gerenciados no [Portal do Cloud Partner](https://cloudpartner.azure.com). Use a mesma conta de registro da Central de Desenvolvedores para entrar. Você deve ter apenas uma conta da Microsoft para suas ofertas do AppSource. As contas não devem ser específicas para serviços individuais ou ofertas.

## <a name="tips"></a>Dicas 

- Garanta que o aplicativo inclua dados de exemplo para ajudar as pessoas a começar a usá-lo com um clique. 
- Examine cuidadosamente o aplicativo instalando-o em seu locatário e em um locatário secundário. Verifique se os clientes veem apenas o que você deseja que eles vejam. 
- Use o AppSource como sua loja online para hospedar o aplicativo. Dessa forma, todas as pessoas que usam o Power BI poderão encontrar seu aplicativo. 
- Considere a possibilidade de oferecer mais de um aplicativo de modelo para cenários exclusivos separados. 
- Habilite a personalização de dados, por exemplo, suporte à conexão personalizada e à configuração de parâmetros pelo instalador.

Confira [Dicas para a criação de aplicativos de modelo no Power BI](service-template-apps-tips.md) para obter mais sugestões.

## <a name="known-limitations"></a>Limitações conhecidas

| Recurso | Limitações conhecidas |
|---------|---------|
|Conteúdo:  Conjuntos de dados   | É necessário que exatamente um conjunto de dados esteja presente. Apenas conjuntos de dados criados no Power BI Desktop (arquivos .pbix) são permitidos. <br>Sem suporte: Conjuntos de dados de outros aplicativos de modelo, conjuntos de dados entre workspaces, relatórios paginados (arquivos .rdl) e pastas de trabalho do Excel |
|Conteúdo: Dashboards | Blocos em tempo real não são permitidos (em outras palavras, não há suporte para conjunto de dados de streaming ou push) |
|Conteúdo: Fluxos de dados | Sem suporte: Fluxos de dados |
|Conteúdo de arquivos | Apenas arquivos PBIX são permitidos. <br>Sem suporte: arquivos .rdl (relatórios paginados) e pastas de trabalho do Excel   |
| Fontes de dados | Fontes de dados compatíveis com a atualização de Dados Agendada na nuvem são permitidas. <br>Sem suporte: <li> DirectQuery</li><li>Conexões dinâmicas (sem o Azure AS)</li> <li>Fontes de dados locais (não há suporte para gateways pessoais e empresariais)</li> <li>Em tempo real (não há suporte para conjunto de dados de push)</li> <li>Modelos compostos</li></ul> |
| Conjunto de dados: entre workspaces | Conjuntos de dados entre workspaces não são permitidos  |
| Parâmetros de consulta | Sem suporte: Parâmetros do tipo "Qualquer" ou "Binário" bloqueiam a operação de atualização do conjunto de dados |
| Visuais personalizados | Somente há suporte para visuais personalizados disponíveis publicamente. Não há suporte para [visuais personalizados organizacionais](developer/power-bi-custom-visuals-organization.md) |

## <a name="support"></a>Suporte
Para obter suporte durante o desenvolvimento, use [https://powerbi.microsoft.com/support](https://powerbi.microsoft.com/support). Monitoramos e gerenciamos esse site ativamente. Os incidentes com clientes chegam rapidamente à equipe apropriada.

## <a name="next-steps"></a>Próximas etapas

[Criar um aplicativo de modelo](service-template-apps-create.md)
