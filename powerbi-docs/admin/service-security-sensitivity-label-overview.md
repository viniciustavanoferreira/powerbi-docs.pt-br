---
title: Rótulos de confidencialidade da Proteção de Informações da Microsoft no Power BI
description: Saiba como os rótulos de confidencialidade da Proteção de Informações da Microsoft funcionam no Power BI
author: paulinbar
manager: rkarlin
ms.service: powerbi
ms.subservice: powerbi-eim
ms.topic: how-to
ms.date: 07/05/2020
ms.author: painbar
LocalizationGroup: Data from files
ms.openlocfilehash: def07ed0ea061c02489d6e92b9648ad1a8d0edad
ms.sourcegitcommit: 181679a50c9d7f7faebcca3a3fc55461f594d9e7
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/07/2020
ms.locfileid: "86034997"
---
# <a name="sensitivity-labels-in-power-bi"></a>Rótulos de confidencialidade no Power BI

Este artigo descreve a funcionalidade de [Rótulos de confidencialidade da Proteção de Informações da Microsoft](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels?view=o365-worldwide) no Power BI. Para obter informações sobre como aplicar rótulos de confidencialidade a relatórios, dashboards, conjuntos de dados e fluxos de dados do Power BI, confira [Como aplicar rótulos de confidencialidade no Power BI](./service-security-apply-data-sensitivity-labels.md). Para obter informações sobre como habilitar rótulos de confidencialidade em seu locatário, confira [Habilitar rótulos de confidencialidade de dados no Power BI](service-security-enable-data-sensitivity-labels.md).

Os rótulos de confidencialidade da Proteção de Informações da Microsoft oferecem um modo simples de os usuários classificarem conteúdo crítico no Power BI sem comprometer a produtividade nem a capacidade de colaborar.

Os rótulos de confidencialidade podem ser aplicados a conjuntos de dados, relatórios, dashboards e fluxos de dados. Quando os dados são exportados do Power BI para arquivos Excel, PowerPoint ou PDF, o Power BI aplica automaticamente um rótulo de confidencialidade ao arquivo exportado e o protege de acordo com as configurações de criptografia de arquivo do rótulo. Dessa forma, seus dados confidenciais permanecem protegidos em qualquer lugar em que estejam.

Os rótulos de sensibilidade aplicados em relatórios do Power BI, dashboards, conjuntos de dados e fluxos de dados ficam visíveis de muitos lugares no serviço do Power BI. Os rótulos de sensibilidade em relatórios e dashboards também são visíveis nos aplicativos móveis do Power BI para iOS e Android e em visuais inseridos.

Um [relatório de métricas de proteção](service-security-data-protection-metrics-report.md) disponível no portal de administração do Power BI dá aos administradores do Power BI visibilidade total sobre os dados confidenciais no locatário do Power BI. Além disso, os logs de auditoria do Power BI incluem informações de rótulo de confidencialidade sobre atividades como aplicação, remoção e alteração de rótulos, bem como sobre atividades como exibição de relatórios, dashboards etc., fornecendo aos administradores do Power BI e segurança visibilidade sobre o consumo de dados confidenciais para fins de monitoramento, investigação e alertas de segurança.

## <a name="important-considerations"></a>Considerações importantes

Aplicar o rótulo de confidencialidade **não** afeta o acesso ao conteúdo no Power BI. O acesso ao conteúdo no Power BI é gerenciado unicamente por permissões do Power BI. Enquanto os rótulos estão visíveis, todas as configurações de criptografia associadas (configuradas no [Centro de segurança do Microsoft 365](https://security.microsoft.com/) ou no [Centro de conformidade do Microsoft 365](https://compliance.microsoft.com/)) não são aplicadas. Elas são aplicadas somente a dados exportados para arquivos do Excel, do PowerPoint e PDF.

Os rótulos de confidencialidade e a criptografia de arquivo **não são** aplicados em nenhum caminho de exportação exceto exportação para Excel, PowerPoint e PDF. O administrador de locatários do Power BI pode desabilitar quaisquer ou todos os caminhos de exportação que não dão suporte à aplicação de rótulos de confidencialidade e as configurações de criptografia de arquivo associadas.

>[!NOTE]
> Usuários com acesso permitido a um relatório têm permissão de acesso a todo o conjunto de dados subjacente, a menos que a [RLS (Segurança em Nível de Linha)](./service-admin-rls.md) limite o acesso. Os autores de relatório podem classificar e rotular relatórios usando rótulos de confidencialidade. Se o rótulo de confidencialidade tiver configurações de proteção, o Power BI aplicará essas configurações de proteção ao exportar dados de relatório para arquivos do Excel, do PowerPoint ou em PDF. Somente usuários autorizados poderão abrir arquivos protegidos.

## <a name="how-sensitivity-labels-work-in-power-bi"></a>Como os rótulos de confidencialidade funcionam no Power BI

Quando você aplica um rótulo de confidencialidade a um dashboard, relatório, conjunto de dados ou fluxo de dados do Power BI, o processo é semelhante a aplicar uma tag a esse recurso, que tem os seguintes benefícios:
* **Personalizável** – você pode criar categorias para diferentes níveis de conteúdo confidencial em sua organização, como Pessoal, Público, Geral, Confidencial e Altamente Confidencial.
* **Texto não criptografado** – como o rótulo está em texto não criptografado, é fácil para os usuários entenderem como tratar o conteúdo de acordo com as diretrizes dos rótulos de confidencialidade.
* **Persistente** – depois que um rótulo de confidencialidade tiver sido aplicado ao conteúdo, ele acompanhará esse conteúdo quando ele for exportado para arquivos do Excel, do PowerPoint e PDF e se tornará a base para a aplicação e a imposição de políticas.

Veja um exemplo rápido de como os rótulos de confidencialidade no Power BI funcionam. A imagem abaixo mostra como um rótulo de confidencialidade é aplicado em um relatório no serviço do Power BI, em seguida, como os dados do relatório são exportados para um arquivo do Excel e, por fim, como o rótulo de confidencialidade e suas proteções são mantidos no arquivo exportado.

![GIF animado mostrando o aplicativo e a persistência de rótulos de confidencialidade](media/service-security-sensitivity-label-overview/ApplyLabelandProtection.gif)

Em aplicativos do Microsoft Office, um rótulo de confidencialidade aparece como uma tag no email ou no documento, semelhante ao que é mostrado na imagem acima.

Você também pode atribuir uma classificação (como um adesivo) ao conteúdo, que persiste e move o conteúdo conforme ele é usado e compartilhado no Power BI. Você pode usar essa classificação para gerar relatórios de uso e ver dados de atividade relacionados ao seu conteúdo confidencial. Com base nessas informações, você sempre pode optar mais tarde por aplicar as configurações de proteção.

## <a name="sensitivity-label-inheritance-upon-creation-of-new-content"></a>Herança de rótulo de confidencialidade na criação de novo conteúdo

Quando novos relatórios e dashboards são criados no serviço do Power BI, eles herdam automaticamente o rótulo de confidencialidade aplicado anteriormente no relatório ou conjunto de dados pai. Por exemplo, um novo relatório criado sobre um conjunto de dados que tenha um rótulo de confidencialidade "Altamente Confidencial" também receberá automaticamente o rótulo "Altamente Confidencial".

A imagem a seguir mostra como o rótulo de confidencialidade de um conjunto de dados é aplicado automaticamente em um novo relatório criado com base no conjunto de dados.

![GIF animado mostrando a herança de rótulos de confidencialidade](media/service-security-sensitivity-label-overview/InheritanceUponCreation.gif)

>[!NOTE]
>Se por algum motivo o rótulo de confidencialidade não puder ser aplicado no novo relatório ou dashboard, o Power BI **não** bloqueará a criação do item.

## <a name="sensitivity-labels-and-protection-on-exported-data"></a>Rótulos de confidencialidade e proteção em dados exportados

Quando os dados são exportados do Power BI para arquivos Excel, PowerPoint ou PDF, o Power BI aplica automaticamente um rótulo de confidencialidade ao arquivo exportado e o protege de acordo com as configurações de criptografia de arquivo do rótulo. Dessa forma, seus dados confidenciais permanecem protegidos em qualquer lugar em que estejam.

Um usuário que exporta um arquivo do Power BI tem permissões para acessar e editar esse arquivo de acordo com as configurações de rótulo de confidencialidade. Ele não obtém permissões de proprietário para o arquivo.

Os rótulos de confidencialidade e a proteção não serão aplicados quando os dados forem exportados para arquivos .csv ou .pbix, Analisar no Excel ou qualquer outro caminho de exportação.

A aplicação de um rótulo de confidencialidade e a proteção para um arquivo exportado não adiciona a marcação de conteúdo ao arquivo. No entanto, se o rótulo estiver configurado para aplicar marcações de conteúdo, as marcações serão automaticamente aplicadas pelo cliente de rotulagem unificado da Proteção de Informações do Azure quando o arquivo for aberto em aplicativos da área de trabalho do Office. As marcações de conteúdo não são aplicadas automaticamente quando você usa rotulagem interna para aplicativos Web, de área de trabalho ou de dispositivos móveis. Consulte [Quando os aplicativos do Office aplicam criptografia e marcação de conteúdo](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels-office-apps?view=o365-worldwide#when-office-apps-apply-content-marking-and-encryption) para obter mais detalhes.

A exportação falhará se um rótulo não puder ser aplicado quando os dados forem exportados para um arquivo. Para verificar se a exportação falhou porque o rótulo não pôde ser aplicado, clique no nome do dashboard ou do relatório no centro da barra de título e veja se ele diz "O rótulo de confidencialidade não pode ser carregado" no menu suspenso de informações que é aberto. Isso poderá acontecer como resultado de um problema do sistema temporário ou se o rótulo aplicado não tiver sido publicado ou tiver sido excluído pelo administrador de segurança.

## <a name="sensitivity-label-persistence-in-embedded-reports-and-dashboards"></a>Persistência de rótulo de confidencialidade em relatórios e dashboards inseridos

Você pode inserir relatórios, dashboards e visuais do Power BI em aplicativos de negócios, como o Microsoft Teams e o SharePoint, ou no site de uma organização. Quando você insere um visual, relatório ou dashboard que tem um rótulo de confidencialidade aplicado, o rótulo de confidencialidade fica visível na exibição inserida e o rótulo e a proteção serão mantidos quando os dados forem exportados para o Excel.

![Captura de tela do relatório inserido no SharePoint Online](media/service-security-sensitivity-label-overview/embedded-report-sensitivity-label.png)

Há suporte para os seguintes cenários de inserção:
* [Inserir para a organização](../developer/embedded/embed-sample-for-your-organization.md)
* Aplicativos Microsoft 365 (por exemplo, [Teams](../collaborate-share/service-embed-report-microsoft-teams.md) e [SharePoint](../collaborate-share/service-embed-report-spo.md))
* [Inserção de URL segura](../collaborate-share/service-embed-secure.md) (inserção do serviço do Power BI) 

## <a name="sensitivity-labels-in-the-power-bi-mobile-apps"></a>Rótulos de confidencialidade em aplicativos móveis do Power BI

Os rótulos de confidencialidade podem ser exibidos em relatórios e dashboards em aplicativos móveis do Power BI. Um ícone ao lado do nome do relatório ou dashboard indica que ele tem um rótulo de confidencialidade, e o tipo de rótulo e sua descrição podem ser encontrados na caixa informações do relatório ou do dashboard.

![Captura de tela de rótulo de confidencialidade no aplicativo móvel](media/service-security-sensitivity-label-overview/mobile-app-sensitivity-label2.png)

## <a name="supported-clouds"></a>Nuvens com suporte
Os rótulos de confidencialidade têm suporte apenas em locatários de nuvens (públicas) globais, eles não têm suporte em locatários de nuvens como as nacionais.

## <a name="requirements-for-using-sensitivity-labels-in-power-bi"></a>Requisitos para usar rótulos de confidencialidade no Power BI

Antes que os rótulos de confidencialidade possam ser habilitados e usados no Power BI, você precisará concluir os seguintes pré-requisitos:
* garantir que os rótulos de confidencialidade tenham sido definidos na [central de segurança do Microsoft 365](https://security.microsoft.com/) ou na [central de conformidade do Microsoft 365](https://compliance.microsoft.com/).
* [Habilitar rótulos de confidencialidade](service-security-enable-data-sensitivity-labels.md) no Power BI.
* Garantir que os usuários tenham as [licenças apropriadas](#licensing).

## <a name="licensing"></a>Licenças

* Aplicar e exibir os rótulos de confidencialidade da Proteção de Informações da Microsoft no Power BI exige uma licença Premium P1 ou Premium P2 da Proteção de Informações do Azure. A Proteção de Informações do Microsoft Azure pode ser adquirida de forma independente ou por meio de um dos pacotes de licenciamento da Microsoft. Confira [preço da Proteção de Informações do Azure](https://azure.microsoft.com/pricing/details/information-protection/) para obter detalhes.
* A exibição e a aplicação de rótulos em aplicativos do Office têm [requisitos de licenciamento](https://docs.microsoft.com/microsoft-365/compliance/get-started-with-sensitivity-labels#subscription-and-licensing-requirements-for-sensitivity-labels).
* Para aplicar rótulos a conteúdo do Power BI, o usuário precisa ter uma licença do Power BI Pro, além de uma das licenças da Proteção de Informações do Azure mencionadas acima.

## <a name="sensitivity-label-creation-and-management"></a>Criação e gerenciamento de rótulo de confidencialidade

Os rótulos de confidencialidade são criados e gerenciados na [central de segurança do Microsoft 365](https://security.microsoft.com/) ou na [central de conformidade do Microsoft 365](https://compliance.microsoft.com/).

Para acessar os rótulos de confidencialidade em qualquer um desses centros, navegue para **Classificação > Rótulos de confidencialidade**. Esses rótulos de confidencialidade podem ser usados por vários serviços da Microsoft, como a Proteção de Informações do Azure, os aplicativos do Office e os serviços do Office 365.

>[!Important]
> Se a sua organização usa rótulos de confidencialidade da Proteção de Informações do Azure, você precisa [migrá-los](https://docs.microsoft.com/azure/information-protection/configure-policy-migrate-labels) para um dos serviços listados anteriormente para que eles sejam usados no Power BI.

## <a name="limitations"></a>Limitações

A lista a seguir fornece algumas limitações dos rótulos de confidencialidade no Power BI:

* Os rótulos de confidencialidade podem ser aplicados apenas a dashboards, relatórios, conjuntos de dados e fluxos de dados. Atualmente, eles não estão disponíveis para [relatórios paginados](../paginated-reports/report-builder-power-bi.md) e pastas de trabalho.
* Os rótulos de confidencialidade em ativos do Power BI ficam visíveis apenas na lista do workspace, nas exibições de linhagem, favoritos, recentes e de aplicativos. Atualmente, os rótulos não estão visíveis na exibição “compartilhado comigo”. Observe, no entanto, que um rótulo aplicado a um ativo do Power BI, mesmo que não esteja visível, sempre persistirá em dados exportados para arquivos do Excel, do PowerPoint e PDF.
* Os rótulos de confidencialidade de dados não são compatíveis com os aplicativos de modelo. Os rótulos de confidencialidade definidos pelo criador do aplicativo de modelo são removidos quando o aplicativo é extraído e instalado, e os rótulos de confidencialidade adicionados aos artefatos em um aplicativo de modelo instalado pelo consumidor do aplicativo são perdidos (redefinidos para nothing) quando o aplicativo é atualizado.
* O Power BI não é compatível com os rótulos de confidencialidade dos tipos de proteção [Não Encaminhar](https://docs.microsoft.com/microsoft-365/compliance/encryption-sensitivity-labels?view=o365-worldwide#let-users-assign-permissions) e [definido pelo usuário](https://docs.microsoft.com/microsoft-365/compliance/encryption-sensitivity-labels?view=o365-worldwide#let-users-assign-permissions) e [HYOK](https://docs.microsoft.com/azure/information-protection/configure-adrms-restrictions). Os tipos de proteção Não Encaminhar e definidos pelo usuário referem-se aos rótulos definidos no [Centro de segurança do Microsoft 365](https://security.microsoft.com/) ou no [Centro de conformidade do Microsoft 365](https://compliance.microsoft.com/).
* Não é recomendável permitir que os usuários apliquem rótulos pai no Power BI. Se um rótulo pai for aplicado ao conteúdo, a exportação de dados desse conteúdo para um arquivo (Excel, PowerPoint e PDF) falhará. Consulte [Sub-rótulos (rótulos de agrupamento)](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels?view=o365-worldwide#sublabels-grouping-labels).

## <a name="next-steps"></a>Próximas etapas

Este artigo forneceu uma visão geral da proteção de dados no Power BI. Os artigos a seguir fornecem mais detalhes sobre a proteção de dados no Power BI. 

* [Habilitar rótulos de confidencialidade no Power BI](service-security-enable-data-sensitivity-labels.md)
* [Como aplicar rótulos de confidencialidade no Power BI](service-security-apply-data-sensitivity-labels.md)
* [Usando controles do Microsoft Cloud App Security no Power BI](service-security-using-microsoft-cloud-app-security-controls.md)
* [Relatório de métricas de proteção](service-security-data-protection-metrics-report.md)