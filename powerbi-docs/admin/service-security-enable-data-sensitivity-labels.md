---
title: Habilitar rótulos de confidencialidade de dados no Power BI
description: Saiba como habilitar rótulos de confidencialidade de dados no Power BI
author: paulinbar
ms.service: powerbi
ms.subservice: powerbi-eim
ms.topic: how-to
ms.date: 06/15/2020
ms.author: painbar
LocalizationGroup: Data from files
ms.openlocfilehash: c6c1c20e88e6da96ed0c7239ee26f63220c28a00
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85227057"
---
# <a name="enable-data-sensitivity-labels-in-power-bi"></a>Habilitar rótulos de confidencialidade de dados no Power BI

Para os [rótulos de confiabilidade de dados da Proteção de Informações da Microsoft](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels) serem usados no Power BI, eles precisam estar habilitados no locatário. Este artigo mostra aos administradores de locatário do Power BI como fazer isso. Para obter mais informações sobre rótulos de confidencialidade de dados no Power BI, consulte [Proteção de dados no Power BI](service-security-data-protection-overview.md). Para obter informações sobre como aplicar rótulos de confidencialidade no Power BI, consulte [Como aplicar rótulos de confidencialidade](../collaborate-share/service-security-apply-data-sensitivity-labels.md) 

Quando os rótulos de confidencialidade estão habilitados:

* Usuários e grupos de segurança específicos em uma organização podem classificar e [aplicar rótulos de confidencialidade](../collaborate-share/service-security-apply-data-sensitivity-labels.md) aos seus relatórios, dashboards, conjuntos de dados e fluxos de dados do Power BI.
* Todos os membros da organização podem ver esses rótulos.

Habilitar rótulos de confidencialidade de dados requer uma licença da Proteção de Informações do Azure. Consulte [Licenciamento](service-security-data-protection-overview.md#licensing) para obter mais detalhes.

## <a name="enable-data-sensitivity-labels"></a>Habilitar rótulos de confidencialidade de dados

Acesse o **Portal de administração** do Power BI, abra o painel **Configurações de locatário** e localize a seção **Proteção de informações**.

![Encontrar a seção Proteção de Informações](media/service-security-enable-data-sensitivity-labels/enable-data-sensitivity-labels-01.png)

Na seção **Proteção de Informações**, execute as seguintes etapas:
1. Abra **Permitir que os usuários apliquem rótulos de confidencialidade ao conteúdo do Power BI**.
1. Habilite a alternância.
1. Defina quem pode aplicar e alterar rótulos de confidencialidade em ativos do Power BI. Por padrão, todos em sua organização poderão aplicar rótulos de confidencialidade. No entanto, você pode optar por habilitar a configuração de rótulos de confidencialidade somente para usuários ou grupos de segurança específicos. Com toda a organização ou grupos de segurança específicos selecionados, você pode excluir subconjuntos de usuários ou grupos de segurança específicos.
   
   * Quando os rótulos de confidencialidade são habilitados para toda a organização, as exceções normalmente são grupos de segurança.
   * Quando os rótulos de confidencialidade são habilitados somente para usuários ou grupos de segurança específicos, as exceções normalmente são usuários específicos.  
    Essa abordagem possibilita impedir que determinados usuários apliquem rótulos de confidencialidade no Power BI, mesmo que eles pertençam a um grupo que tenha permissões para fazer isso.

1. Pressione **Aplicar**.

![Habilitar rótulos de confidencialidade](media/service-security-enable-data-sensitivity-labels/enable-data-sensitivity-labels-02.png)

> [!IMPORTANT]
> Somente usuários do Power BI Pro que têm permissões para *criar* e *editar* no ativo e que fazem parte do grupo de segurança que foi definido nesta seção poderão definir e editar os rótulos de confidencialidade. Os usuários que não fazem parte desse grupo não poderão definir ou editar o rótulo.  

## <a name="troubleshooting"></a>Solução de problemas

O Power BI usa rótulos de confidencialidade da Proteção de Informações da Microsoft. Portanto, se você encontrar uma mensagem de erro ao tentar habilitar rótulos de confidencialidade, pode ser devido aos seguintes motivos:

* Você não tem uma [licença](service-security-data-protection-overview.md#licensing) da Proteção de Informações do Azure.
* Os rótulos de confidencialidade não foram migrados para a versão da Proteção de Informações da Microsoft compatível com o Power BI. Saiba mais sobre [migrar rótulos de confidencialidade](https://docs.microsoft.com/azure/information-protection/configure-policy-migrate-labels).
* Nenhum rótulo de confidencialidade da Proteção de Informações da Microsoft foi definido na organização. Observe que, para ser utilizável, um rótulo precisa fazer parte de uma política publicada. [Saiba mais sobre os rótulos de confidencialidade](https://docs.microsoft.com/Office365/SecurityCompliance/sensitivity-labels) ou visite o [centro de conformidade e segurança da Microsoft](https://sip.protection.office.com/sensitivity?flight=EnableMIPLabels) para ler sobre como definir rótulos e publicar políticas para sua organização.

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

Este artigo descreveu como habilitar rótulos de confidencialidade de dados no Power BI. Os artigos a seguir fornecem mais detalhes sobre a proteção de dados no Power BI. 

* [Visão geral da proteção de dados no Power BI](service-security-data-protection-overview.md)
* [Aplicar rótulos de confidencialidade de dados no Power BI](../collaborate-share/service-security-apply-data-sensitivity-labels.md)
* [Usando controles do Microsoft Cloud App Security no Power BI](service-security-using-microsoft-cloud-app-security-controls.md)
* [Relatório de métricas de proteção de dados](service-security-data-protection-metrics-report.md)