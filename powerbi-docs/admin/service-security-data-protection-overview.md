---
title: Proteção de dados no Power BI
description: Saiba como a proteção de dados funciona no Power BI
author: paulinbar
manager: rkarlin
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/21/2020
ms.author: painbar
LocalizationGroup: Data from files
ms.openlocfilehash: fa969f8f738cf09e9e01e284de8f60e2fd8ce9ab
ms.sourcegitcommit: cd64ddd3a6888253dca3b2e3fe24ed8bb9b66bc6
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/03/2020
ms.locfileid: "84315662"
---
# <a name="data-protection-in-power-bi"></a>Proteção de dados no Power BI

Empresas modernas têm requisitos e regulamentos empresariais restritivos sobre como manusear e proteger dados confidenciais. Para fornecer controle e visibilidade sobre tais dados, o Power BI é integrado à Proteção de Informações da Microsoft e ao Microsoft Cloud App Security. Isso permite a você:
* Use os [rótulos de confidencialidade](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels?view=o365-worldwide) da Proteção de Informações da Microsoft para classificar e rotular o conteúdo (dashboards, relatórios, conjuntos de dados e fluxos de dados) no serviço do Power BI, usando a mesma taxonomia usada para classificar e proteger arquivos no Office 365.
* Aplique os rótulos de confidencialidade da Proteção de Informações da Microsoft e a proteção aos dados quando eles forem exportados para arquivos do Excel, do PowerPoint ou PDF.
* usar o Microsoft Cloud App Security para monitorar atividades no Power BI, investigar problemas de segurança e proteger conteúdo no Power BI com o Controle de Aplicativo de Acesso Condicional do Microsoft Cloud App Security.

**Observações importantes**
* Aplicar o rótulo de confidencialidade **não** afeta o acesso ao conteúdo no Power BI. O acesso ao conteúdo no Power BI é gerenciado unicamente por permissões do Power BI. Enquanto os rótulos estão visíveis, todas as configurações de criptografia associadas (configuradas no [Centro de segurança do Microsoft 365](https://security.microsoft.com/) ou no [Centro de conformidade do Microsoft 365](https://compliance.microsoft.com/)) não são aplicadas. Elas são aplicadas somente a dados exportados para arquivos do Excel, do PowerPoint e PDF.
* Os rótulos de confidencialidade e a criptografia de arquivo **não são** aplicados em nenhum caminho de exportação exceto exportação para Excel, PowerPoint e PDF. O administrador de locatários do Power BI pode desabilitar quaisquer ou todos os caminhos de exportação que não dão suporte à aplicação de rótulos de confidencialidade e as configurações de criptografia de arquivo associadas.

## <a name="sensitivity-labels-in-power-bi"></a>Rótulos de confidencialidade no Power BI

Os rótulos de confidencialidade são criados e gerenciados na [central de segurança do Microsoft 365](https://security.microsoft.com/) ou na [central de conformidade do Microsoft 365](https://compliance.microsoft.com/).

Para acessar os rótulos de confidencialidade em qualquer um desses centros, navegue para **Classificação > Rótulos de confidencialidade**. Esses rótulos de confidencialidade podem ser usados por vários serviços da Microsoft, como a Proteção de Informações do Azure, os aplicativos do Office e os serviços do Office 365.

> [!Important]
> Se a sua organização usa rótulos de confidencialidade da Proteção de Informações do Azure, você precisa [migrá-los](https://docs.microsoft.com/azure/information-protection/configure-policy-migrate-labels) para um dos serviços listados anteriormente para que eles sejam usados no Power BI.

> [!NOTE]
> Os rótulos de confidencialidade têm suporte apenas para locatários em nuvens públicas, eles não têm suporte para locatários em nuvens, como em nuvens soberanas.

## <a name="how-sensitivity-labels-work-in-power-bi"></a>Como os rótulos de confidencialidade funcionam no Power BI

Quando você aplica um rótulo de confidencialidade a um dashboard, relatório, conjunto de dados ou fluxo de dados do Power BI, o processo é semelhante a aplicar uma tag a esse recurso, que tem os seguintes benefícios:
* **Personalizável** – você pode criar categorias para diferentes níveis de conteúdo confidencial em sua organização, como Pessoal, Público, Geral, Confidencial e Altamente Confidencial.
* **Texto não criptografado** – como o rótulo está em texto não criptografado, é fácil para os usuários entenderem como tratar o conteúdo de acordo com as diretrizes dos rótulos de confidencialidade.
* **Persistente** – depois que um rótulo de confidencialidade tiver sido aplicado ao conteúdo, ele acompanhará esse conteúdo quando ele for exportado para arquivos do Excel, do PowerPoint e PDF e se tornará a base para a aplicação e a imposição de políticas.

Isso significa que o rótulo de confidencialidade segue o conteúdo quando ele for exportado para arquivos do Excel, do PowerPoint e PDF e se torna a base para aplicar e impor políticas.

Os administradores de locatários do Power BI podem controlar [exportar para Excel](service-admin-portal.md#export-to-excel) e [exportar para PowerPoint e PDF](service-admin-portal.md#export-reports-as-powerpoint-presentations-or-pdf-documents) no [Portal de administração do Power BI](service-admin-portal.md).

## <a name="sensitivity-label-example"></a>Exemplo de rótulo de confidencialidade

Veja um exemplo rápido de como um rótulo de confidencialidade no Power BI pode funcionar.
1. No serviço do Power BI, o rótulo de confidencialidade **Altamente Confidencial** é aplicado a um relatório.

   ![Rótulos de confidencialidade na exibição de lista](media/service-security-data-protection-overview/sensitivity-labels-overview-01.png)
   
1. Quando dados desse relatório são exportados para um arquivo do Excel, o rótulo de confidencialidade e a proteção são aplicados ao arquivo do Excel exportado.

   ![O rótulo de confidencialidade segue o conteúdo](media/service-security-data-protection-overview/sensitivity-labels-overview-02.png)

Em aplicativos do Microsoft Office, um rótulo de confidencialidade aparece como uma tag no email ou no documento, semelhante ao que é mostrado na imagem acima. Você também pode atribuir uma classificação (como um adesivo) ao conteúdo, que persiste e move o conteúdo conforme ele é usado e compartilhado no Power BI. Você pode usar essa classificação para gerar relatórios de uso e ver dados de atividade relacionados ao seu conteúdo confidencial. Com base nessas informações, você sempre pode optar mais tarde por aplicar as configurações de proteção.

## <a name="requirements-for-using-sensitivity-labels-in-power-bi"></a>Requisitos para usar rótulos de confidencialidade no Power BI

Antes que os rótulos de confidencialidade possam ser habilitados e usados no Power BI, você precisará concluir os seguintes pré-requisitos:
* garantir que os rótulos de confidencialidade tenham sido definidos na [central de segurança do Microsoft 365](https://security.microsoft.com/) ou na [central de conformidade do Microsoft 365](https://compliance.microsoft.com/).
* [Habilitar rótulos de confidencialidade](service-security-enable-data-sensitivity-labels.md) no Power BI.
* Garantir que os usuários tenham as [licenças apropriadas](#licensing).
* Se estiver usando Microsoft Cloud App Security com o Power BI, você deverá ter o [licenciamento apropriado](service-security-using-microsoft-cloud-app-security-controls.md#cloud-app-security-licensing).

## <a name="protect-content-using-microsoft-cloud-app-security"></a>Proteger o conteúdo usando o Microsoft Cloud App Security

Você pode proteger o conteúdo no Power BI contra vazamentos ou violações indesejadas usando o Microsoft Cloud App Security. Após o Microsoft Cloud App Security ser definido e configurado, os administradores de segurança poderão monitorar o acesso e a atividade do usuário, executar a análise de risco em tempo real e definir controles específicos do rótulo.

Por exemplo, as organizações podem usar o Microsoft Cloud App Security para configurar uma política que impede que os usuários baixem dados confidenciais do Power BI para dispositivos não gerenciados. Essa configuração permite que os usuários permaneçam produtivos e se conectem ao Power BI de qualquer lugar, enquanto usam o Microsoft Cloud App Security para evitar ações do usuário comprometedoras, tudo isso em tempo real.

**Requisitos**

Antes que seus rótulos de confidencialidade possam usar o Microsoft Cloud App Security, os seguintes pré-requisitos precisarão ser atendidos:
* O Cloud App Security e a Proteção de Informações do Azure [precisam estar habilitados para o locatário](https://docs.microsoft.com/cloud-app-security/azip-integration).
* O aplicativo [precisa estar conectado ao Microsoft Cloud App Security](https://docs.microsoft.com/cloud-app-security/enable-instant-visibility-protection-and-governance-actions-for-your-apps).

## <a name="licensing"></a>Licenças

* Aplicar e exibir os rótulos de confidencialidade da Proteção de Informações da Microsoft no Power BI exige uma licença Premium P1 ou Premium P2 da Proteção de Informações do Azure. A Proteção de Informações do Microsoft Azure pode ser adquirida de forma independente ou por meio de um dos pacotes de licenciamento da Microsoft. Confira [preço da Proteção de Informações do Azure](https://azure.microsoft.com/pricing/details/information-protection/) para obter detalhes.
* A exibição e a aplicação de rótulos em aplicativos do Office têm [requisitos de licenciamento](https://docs.microsoft.com/microsoft-365/compliance/get-started-with-sensitivity-labels#subscription-and-licensing-requirements-for-sensitivity-labels).
* Para aplicar rótulos a conteúdo do Power BI, o usuário precisa ter uma licença do Power BI Pro, além de uma das licenças da Proteção de Informações do Azure mencionadas acima.
* Você precisará ter as [licenças necessárias para o Microsoft Cloud App Security](https://docs.microsoft.com/power-bi/admin/service-security-using-microsoft-cloud-app-security-controls#microsoft-cloud-app-security-licensing) se pretender usá-las para proteger o conteúdo do Power BI contra vazamentos e violações indesejados.

## <a name="considerations-and-limitations"></a>Considerações e limitações

A lista a seguir fornece algumas limitações dos rótulos de confidencialidade no Power BI:

**Geral**
* Os rótulos de confidencialidade podem ser aplicados apenas a dashboards, relatórios, conjuntos de dados e fluxos de dados. Atualmente, eles não estão disponíveis para [relatórios paginados](../paginated-reports/report-builder-power-bi.md) e pastas de trabalho.
* Os rótulos de confidencialidade em ativos do Power BI ficam visíveis apenas na lista do workspace, nas exibições de linhagem, favoritos, recentes e de aplicativos. Atualmente, os rótulos não estão visíveis na exibição “compartilhado comigo”. Observe, no entanto, que um rótulo aplicado a um ativo do Power BI, mesmo que não esteja visível, sempre persistirá em dados exportados para arquivos do Excel, do PowerPoint e PDF.
* Os rótulos de confidencialidade têm suporte apenas para locatários na nuvem global (pública). Os rótulos de confidencialidade não têm suporte para locatários em outras nuvens.
* Os rótulos de confidencialidade de dados não são compatíveis com os aplicativos de modelo. Os rótulos de confidencialidade definidos pelo criador do aplicativo de modelo são removidos quando o aplicativo é extraído e instalado, e os rótulos de confidencialidade adicionados aos artefatos em um aplicativo de modelo instalado pelo consumidor do aplicativo são perdidos (redefinidos para nothing) quando o aplicativo é atualizado.
* O Power BI não é compatível com os rótulos de confidencialidade dos tipos de proteção [Não Encaminhar](https://docs.microsoft.com/microsoft-365/compliance/encryption-sensitivity-labels?view=o365-worldwide#let-users-assign-permissions) e [definido pelo usuário](https://docs.microsoft.com/microsoft-365/compliance/encryption-sensitivity-labels?view=o365-worldwide#let-users-assign-permissions) e [HYOK](https://docs.microsoft.com/azure/information-protection/configure-adrms-restrictions). Os tipos de proteção Não Encaminhar e definidos pelo usuário referem-se aos rótulos definidos no [Centro de segurança do Microsoft 365](https://security.microsoft.com/) ou no [Centro de conformidade do Microsoft 365](https://compliance.microsoft.com/).
* Não é recomendável permitir que os usuários apliquem rótulos pai no Power BI. Se um rótulo pai for aplicado ao conteúdo, a exportação de dados desse conteúdo para um arquivo (Excel, PowerPoint e PDF) falhará. Consulte [Sub-rótulos (rótulos de agrupamento)](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels?view=o365-worldwide#sublabels-grouping-labels).

**Exportar**
* Os controles de rótulo e de proteção serão aplicados somente quando os dados forem exportados para arquivos do Excel, do PowerPoint e PDF. O rótulo e a proteção não serão aplicados quando os dados forem exportados para arquivos .csv ou .pbix, Analisar no Excel ou qualquer outro caminho de exportação.
* A aplicação de um rótulo de confidencialidade e a proteção para um arquivo exportado não adiciona a marcação de conteúdo ao arquivo. No entanto, se o rótulo estiver configurado para aplicar marcações de conteúdo, elas serão automaticamente aplicadas pelo cliente de rotulagem unificado da Proteção de Informações do Azure quando o arquivo for aberto em aplicativos da área de trabalho do Office. As marcações de conteúdo não são aplicadas automaticamente quando você usa rotulagem interna para aplicativos Web, de área de trabalho ou de dispositivos móveis. Consulte [Quando os aplicativos do Office aplicam criptografia e marcação de conteúdo](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels-office-apps?view=o365-worldwide#when-office-apps-apply-content-marking-and-encryption) para obter mais detalhes.
* Um usuário que exporta um arquivo do Power BI tem permissões para acessar e editar esse arquivo de acordo com as configurações do rótulo de confidencialidade. O usuário que exporta os dados não obtém permissões de proprietário para o arquivo.
* A exportação falhará se um rótulo não puder ser aplicado quando os dados forem exportados para um arquivo. Para verificar se a exportação falhou porque o rótulo não pôde ser aplicado, clique no nome do dashboard ou do relatório no centro da barra de título e veja se ele diz "O rótulo de confidencialidade não pode ser carregado" no menu suspenso de informações que é aberto. Isso poderá acontecer se o rótulo aplicado não tiver sido publicado ou tiver sido excluído pelo administrador de segurança ou como resultado de um problema do sistema temporário.


## <a name="next-steps"></a>Próximas etapas

Este artigo forneceu uma visão geral da proteção de dados no Power BI. Os artigos a seguir fornecem mais detalhes sobre a proteção de dados no Power BI. 

* [Habilitar rótulos de confidencialidade de dados no Power BI](service-security-enable-data-sensitivity-labels.md)
* [Aplicar rótulos de confidencialidade de dados no Power BI](../collaborate-share/service-security-apply-data-sensitivity-labels.md)
* [Usando controles do Microsoft Cloud App Security no Power BI](service-security-using-microsoft-cloud-app-security-controls.md)
* [Relatório de métricas de proteção de dados](service-security-data-protection-metrics-report.md)