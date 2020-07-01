---
title: Permitir que os usuários personalizem visuais em um relatório
description: Permita que os leitores de relatório criem sua própria exibição de um relatório, sem editá-lo.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 05/21/2020
ms.author: maggies
LocalizationGroup: Reports
ms.openlocfilehash: 0fdee37f682774e1dac2b1ac6a4fc7a6e8dabe91
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85238082"
---
# <a name="let-users-personalize-visuals-in-a-report"></a>Permitir que os usuários personalizem visuais em um relatório

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-desktop](../includes/yes-desktop.md)] [!INCLUDE [yes-service](../includes/yes-service.md)]

Quando você compartilha um relatório com um público amplo, alguns de seus usuários podem querer ver exibições ligeiramente diferentes de visuais específicos. Talvez eles queiram trocar o que há no eixo, alterar o tipo de visual ou adicionar algo à dica de ferramenta. É difícil criar um visual que atenda aos requisitos de todos. Com essa nova funcionalidade, é possível capacitar seus consumidores para explorar e personalizar elementos visuais, tudo na exibição de leitura de relatório. Eles podem ajustar o visual da maneira que desejarem e salvá-lo como um indicador para verificar mais tarde. Eles não precisam ter permissão de edição para o relatório nem voltar para o autor do relatório para uma alteração.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-personalize-visual.png" alt-text="Personalizar um visual":::
 
## <a name="what-report-consumers-can-change"></a>O que os consumidores de relatório podem alterar

Esse recurso permite que os consumidores recebam insights adicionais por meio da exploração ad hoc de visuais em um relatório Power BI. Para saber como usar esse recurso como um consumidor, confira [Personalizar elementos visuais em seus relatórios](../consumer/end-user-personalize-visuals.md). O recurso é ideal para criadores de relatório que desejam habilitar cenários de exploração básica de seus leitores de relatório. Aqui estão as modificações que os leitores de relatório podem fazer:

- Altere o tipo de visualização
- Alternar uma medida ou dimensão
- Adicionar ou remover uma legenda
- Comparar duas ou mais medidas
- Alterar agregações etc.

Esse recurso não só permite novas funcionalidades de exploração, como inclui maneiras de os consumidores capturarem e compartilharem suas alterações:

- Capturar as alterações
- Compartilhar as alterações
- Redefinir todas as alterações de um relatório
- Redefinir todas as alterações de um visual
- Desmarcar as alterações recentes

## <a name="turn-on-the-preview-feature"></a>Ativar a versão prévia do recurso

Como esse recurso está em versão prévia, primeiro você precisa ativar a opção de recurso. Acesse **Arquivo** > **Opções e Configurações** > **Opções**. Em configurações **Globais** > **Versão prévia dos recursos**, verifique se a opção **Personalizar visuais** está selecionada.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-preview-personalize-visual.png" alt-text="Ativar Personalizar visuais":::

Talvez seja necessário reiniciar o Power BI Desktop para vê-lo nas configurações do arquivo atual.

## <a name="enable-personalization-in-a-report"></a>Habilitar personalização em um relatório

Depois de ativar a opção de visualização, você precisa habilitá-la especificamente para os relatórios para os quais você deseja que os consumidores possam personalizar os visuais.

Você pode habilitar o recurso no Power BI Desktop ou no serviço do Power BI.

### <a name="in-power-bi-desktop"></a>No Power BI Desktop

Para habilitar o recurso no Power BI Desktop, vá para **Arquivo** > **Opções e Configurações** > **Opções** > **Arquivo atual** > **Configurações de relatório**. Verifique se a opção **Personalizar visuais (versão prévia)** está ativada.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-report-settings-personalize-visual.png" alt-text="Habilitar personalização em um relatório":::

### <a name="in-the-power-bi-service"></a>No serviço do Power BI

Para habilitar o recurso no serviço do Power BI, vá para **Configurações** para seu relatório.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-report-service-settings-personalize-visual.png" alt-text="Configurações de relatório no serviço do Power BI":::

Ative **Personalizar visuais (versão prévia)**  > **Salvar**.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-report-service-personalize-visual.png" alt-text="Ativar Personalizar visuais no serviço":::

## <a name="select-visuals-that-can-be-personalized"></a>Selecionar visuais que podem ser personalizados

Quando você habilita essa configuração para um determinado relatório, por padrão, todos os visuais no relatório podem ser personalizados. Se você não quiser que todos os visuais sejam personalizados, poderá ativar ou desativar a configuração por visual.

Selecione o visual > selecione **Formato** no painel **Visualizações** > expanda **Cabeçalho de visual**.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-format-visual-header-personalize.png" alt-text="Selecionar cabeçalho de visual":::
 
Deslize **Personalizar visual** >  **Ligado** ou **Desligado**.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-format-visual-personalize-on-off.png" alt-text="Controle deslizante de Personalizar visual ligado ou desligado":::


## <a name="limitations-and-known-issues"></a>Limitações e problemas conhecidos

Atualmente, o recurso tem algumas limitações a serem consideradas.

- Não há suporte para esse recurso em cenários de inserção, incluindo publicar na Web.
- As explorações de usuário não persistem automaticamente. Você precisa salvar sua exibição como um indicador pessoal para capturar suas alterações.
- Esse recurso tem suporte nos aplicativos móveis do Power BI para tablets Android e iOS e no aplicativo Power BI Windows; não tem suporte nos aplicativos móveis do Power BI para telefones. No entanto, todas as alterações em um visual salvas em um indicador pessoal no serviço do Power BI são respeitadas em todos os aplicativos móveis do Power BI.

Há também alguns problemas conhecidos que estamos abordando:

- Não há suporte para a adição de hierarquia; você precisa adicionar os itens filho individuais.
- Não é possível alterar uma hierarquia de data para uma data ou vice-versa. 
- Com os indicadores pessoais, você pode obter resultados ligeiramente diferentes com base na sequência selecionada. Existe a possibilidade de discrepâncias porque não capturamos o estado completo do relatório, mas apenas as modificações feitas. A solução alternativa é selecionar **Redefinir para o padrão** e, em seguida, selecionar o indicador que você deseja exibir. 

## <a name="next-steps"></a>Próximas etapas

[Personalize os visuais em seus relatórios](../consumer/end-user-personalize-visuals.md).     

Experimente a nova experiência de personalização visual. Forneça seus comentários sobre esse recurso e como podemos continuar melhorando, [no site Power BI Ideas](https://ideas.powerbi.com/forums/265200-power-bi). 

Mais perguntas? [Experimente a Comunidade do Power BI](https://community.powerbi.com/)
