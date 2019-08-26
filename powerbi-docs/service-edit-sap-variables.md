---
title: Editar variáveis do SAP no serviço do Power BI (versão prévia)
description: Azure e Power BI
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 08/12/2019
LocalizationGroup: Data from databases
ms.openlocfilehash: aff72d8efed716af2e7f4c881b22af12e248c207
ms.sourcegitcommit: 0e50ebfa8762e19286566432870ef16d242ac78f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68962885"
---
# <a name="edit-sap-variables-in-the-power-bi-service-preview"></a>Editar variáveis do SAP no serviço do Power BI (versão prévia)

Ao usar o SAP Business Warehouse ou o SAP HANA com o DirectQuery, os autores de relatório agora podem permitir que os usuários finais editem variáveis do SAP no **serviço do Power BI** para workspaces Premium.

![Caixa de diálogo Editar variáveis](media/service-edit-sap-variables/sap-edit-variables-dialog.png)

Este documento descreve os requisitos para editar variáveis no Power BI, como habilitar essa versão prévia do recurso e onde editar variáveis no serviço do Power BI.

## <a name="requirements-for-sap-edit-variables"></a>Requisitos para editar variáveis do SAP

Há alguns requisitos para o uso do recurso editar variáveis do SAP. A lista a seguir descreve esses requisitos.

**Nova experiência de filtro necessária** – você deve ter a [nova experiência de filtro](power-bi-report-filter.md) habilitada para seu relatório. Veja como você pode habilitá-lo para seu relatório no Power BI Desktop:
- No Power BI Desktop, selecione **Arquivo** > **Opções e Configurações** > **Opções**
- Na barra de navegação à esquerda, em **Arquivo atual**, selecione **Configurações de relatório**.
- Em **Experiência de filtragem**, selecione **Habilitar o painel de filtros atualizado**.

**Conexões do DirectQuery necessárias** – você deve se conectar à fonte de dados do SAP usando o DirectQuery. Não há suporte para importar conexões.

**Assinatura do Power BI Premium necessária** – o recurso editar variáveis do SAP só funciona, no momento, em assinaturas do Power BI Premium.

**Configuração de SSO necessária** – para que este recurso funcione, o SSO (logon único) deve estar configurado. Confira [visão geral do SSO (logon único)](service-gateway-sso-overview.md) para saber mais.

**Novos bits de gateway necessários** – Baixe o gateway mais recente e atualize seu gateway existente. Confira [gateway de serviço](service-gateway-onprem.md) para saber mais.

**Somente multidimensional para SAP HANA** – para o SAP HANA, o recurso editar variáveis do SAP só funciona com modelos multidimensionais e não funciona em fontes relacionais.

**Sem suporte em nuvens soberanas** – no momento, o Power Query Online não está disponível em nuvens soberanas; portanto, também não há suporte para esse recurso em nuvens soberanas.

## <a name="how-to-enable-the-feature"></a>Como habilitar o recurso

Para habilitar o recurso **editar variáveis do SAP**, no Power BI Desktop, conecte-se a uma fonte de dados do SAP HANA ou do SAP BW. Em seguida, acesse **Arquivo > Opções e configurações > Opções** e, em seguida, na seção Arquivo Atual no painel esquerdo, selecione **DirectQuery**. Quando você seleciona isso, no painel direito, você vê as opções de DirectQuery e uma caixa de seleção em que você pode **Permitir que usuários finais alterem as variáveis do SAP no relatório (versão prévia)**, conforme mostrado na imagem a seguir.

![Opções do DirectQuery](media/service-edit-sap-variables/sap-preview-setting-in-desktop.png)

## <a name="use-sap-edit-variables-in-power-bi-desktop"></a>Usar editar variáveis do SAP no Power BI Desktop

Ao usar o recurso editar variáveis do SAP no Power BI Desktop, você pode editar as variáveis selecionando o link Editar variáveis no menu **Editar Consultas** na faixa de seleção. Lá, a seguinte caixa de diálogo é exibida. Esse recurso ficou disponível no Power BI Desktop por um tempo. Os criadores de relatório podem selecionar variáveis do relatório usando a caixa de diálogo a seguir.

![Adicionar itens](media/service-edit-sap-variables/sap-variables-add-items.png)

## <a name="use-sap-edit-variables-in-the-service"></a>Usar o recurso editar variáveis do SAP no serviço

Depois que o relatório for publicado no serviço do Power BI, os usuários poderão ver o link **Editar variáveis** no novo painel Filtrar. Se você estiver publicando o relatório pela primeira vez, poderá levar até 5 minutos antes que o link Editar variável seja exibido. Se o link não tiver sido exibido, você precisará atualizar manualmente o conjunto de dados.
Você pode fazer isso:

1. No serviço do Power BI, selecione a guia **Conjuntos de Dados** na lista de conteúdo de um workspace.

2. Localize o conjunto de dados que você precisa atualizar e selecione o ícone **Atualizar**.

    ![Editar variáveis](media/service-edit-sap-variables/sap-edit-variables-link.png)

3. A seleção do link Editar variáveis abre a caixa de diálogo **Editar variáveis**, em que os usuários podem substituir variáveis. Selecionar o botão **Redefinir** redefine as variáveis para os valores originais que foram exibidos quando essa caixa de diálogo foi aberta.

    ![Caixa de diálogo Editar variáveis](media/service-edit-sap-variables/sap-edit-variables-dialog.png)

4. Alterações na caixa de diálogo **Editar variáveis** persistem apenas para este usuário (semelhante a outros comportamentos de persistência no Power BI). Selecionar **Redefinir para padrão**, mostrado na imagem a seguir, redefine o relatório para o estado original do seu criador, incluindo as variáveis.

    ![Redefinir para padrão](media/service-edit-sap-variables/reset-to-default.png)

Ao trabalhar em um relatório publicado no serviço do Power BI que usa o SAP HANA ou o SAP BW com o recurso **Editar variáveis** habilitado, o proprietário do relatório pode alterar esses padrões. O proprietário do relatório pode alterar as variáveis no modo de edição e salvá-lo para habilitar que essas configurações se tornem as *novas configurações padrão* desse relatório. Outros usuários que acessarem o relatório depois que essas alterações forem feitas pelo proprietário do relatório verão as novas configurações como os padrões.

## <a name="issues-and-considerations"></a>Problemas e considerações

Nesse momento, não há suporte para o recurso editar variáveis do SAP nos aplicativos.

## <a name="next-steps"></a>Próximas etapas

Para saber mais sobre o SAP HANA, o SAP BW ou o DirectQuery, leia os seguintes artigos:

- [Usar o SAP HANA no Power BI Desktop](desktop-sap-hana.md)
- [DirectQuery e SAP BW (Business Warehouse)](desktop-directquery-sap-bw.md)
- [DirectQuery e SAP HANA](desktop-directquery-sap-hana.md)
- [Usar o DirectQuery no Power BI](desktop-directquery-about.md)