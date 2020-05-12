---
title: Permitir que os usuários personalizem visuais em um relatório
description: Permita que os leitores de relatório criem sua própria exibição de um relatório, sem editá-lo.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/09/2020
ms.author: maggies
LocalizationGroup: Reports
ms.openlocfilehash: abc936c6ea4b61e4837e05fbde110e5159296815
ms.sourcegitcommit: a199dda2ab50184ce25f7c9a01e7ada382a88d2c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82867106"
---
# <a name="let-users-personalize-visuals-in-a-report"></a>Permitir que os usuários personalizem visuais em um relatório

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-desktop](../includes/yes-desktop.md)] [!INCLUDE [yes-service](../includes/yes-service.md)]

Quando você compartilha um relatório com um público amplo, alguns de seus usuários podem querer ver exibições ligeiramente diferentes de visuais específicos. Talvez eles queiram trocar o que há no eixo, alterar o tipo de visual ou adicionar algo à dica de ferramenta. É difícil criar um visual que atenda aos requisitos de todos. Com essa nova funcionalidade, é possível capacitar seus consumidores para explorar e personalizar elementos visuais, tudo na exibição de leitura de relatório. Eles podem ajustar o visual da maneira que desejarem e salvá-lo como um indicador para verificar mais tarde. Eles não precisam ter permissão de edição para o relatório nem voltar para o autor do relatório para uma alteração.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-personalize-visual.png" alt-text="Personalizar um visual":::
 
## <a name="what-report-consumers-can-change"></a>O que os consumidores de relatório podem alterar

Esse recurso permite que os consumidores recebam insights adicionais por meio da exploração ad hoc de visuais em um relatório Power BI. O recurso é ideal para criadores de relatório que desejam habilitar cenários de exploração básica de seus leitores de relatório. Aqui estão as modificações que os leitores de relatório podem fazer:

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

## <a name="personalize-visuals-in-the-power-bi-service"></a>Personalizar visuais no serviço do Power BI

Ao personalizar um visual, seus consumidores podem explorar os dados de várias maneiras, sem deixar a exibição de leitura do relatório. Os exemplos a seguir mostram diferentes maneiras como os usuários podem modificar uma visualização para atender às necessidades deles. 

1. Abra um relatório no modo de exibição de leitura no serviço do Power BI.

2. No canto superior direito do visual, selecione o ícone **Personalizar este visual** ![Personalizar este visual](media/power-bi-personalize-visuals/power-bi-personalize-visual-icon.png). 

### <a name="change-the-visualization-type"></a>Altere o tipo de visualização

É possível exibir a visualização para uma representação diferente alterando o **Tipo de visualização**.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-personalize-change-visual-type.png" alt-text="Alterar o tipo de visualização":::
 
### <a name="swap-out-a-measure-or-dimension"></a>Alternar uma medida ou dimensão
É possível substituir uma medida ou dimensão no eixo X selecionando o campo que você deseja substituir e, em seguida, selecionando outra medida ou dimensão.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-personalize-change-axis.png" alt-text="Alterar o eixo":::
 
### <a name="add-or-remove-a-legend"></a>Adicionar ou remover uma legenda
Ao adicionar uma legenda, você pode codificar por cores um visual com base em uma categoria. É possível eliminar a codificação por cores categórica desmarcando a caixa **Legenda** no painel **Personalizar**. 

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-personalize-change-legend.png" alt-text="Adicionar ou remover a legenda":::

### <a name="compare-two-or-more-different-measures"></a>Comparar duas ou mais medidas diferentes
É possível comparar e contrastar os valores para medidas diferentes usando o ícone + para adicionar várias medidas a um visual.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-personalize-compare-measures.png" alt-text="Comparar medidas":::

### <a name="change-aggregations"></a>Alterar agregações
É possível alterar a forma como uma medida é calculada alterando a agregação no painel **Personalizar**.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-personalize-change-aggregation.png" alt-text="Alterar agregações":::

### <a name="capture-changes"></a>Capturar alterações 
Usando indicadores pessoais, capture as alterações para que você possa retornar à exibição personalizada. 

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-personalize-bookmark.png" alt-text="Criar um indicador":::
 
Também é possível tornar o indicador seu modo de exibição padrão.

### <a name="share-changes"></a>Compartilhar alterações 
Se você tiver permissões de leitura e recompartilhamento, ao compartilhar o relatório, poderá optar por incluir as alterações.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-personalize-share-changes.png" alt-text="Compartilhar alterações":::
 
### <a name="reset-all-your-changes-to-a-report"></a>Redefinir todas as suas alterações para um relatório

Selecione **Redefinir para o padrão** para remover todas as suas alterações no relatório e defini-las de volta para a exibição do relatório salva pela última vez do autor.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-personalize-reset-all.png" alt-text="Redefinir todas as alterações":::
 
### <a name="reset-all-your-changes-to-a-visual"></a>Redefinir todas as suas alterações para um visual

Selecione **Redefinir este visual** para remover todas as suas alterações em um visual específico e defini-las de volta para a exibição do visual salva pela última vez do autor.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-personalize-reset-visual.png" alt-text="Redefinir todas as alterações visuais":::
 
### <a name="clear-recent-changes"></a>Limpar alterações recentes

Selecione o ícone de borracha para limpar todas as alterações recentes feitas desde que você abriu o painel **Personalizar**.  

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-personalize-revert-changes.png" alt-text="Reverter alterações recentes":::

## <a name="limitations-and-known-issues"></a>Limitações e problemas conhecidos

Atualmente, o recurso tem algumas limitações a serem consideradas.

- Não há suporte para esse recurso em cenários de inserção, incluindo publicar na Web.
- As explorações de usuário não persistem automaticamente. Você precisa salvar sua exibição como um indicador pessoal para capturar suas alterações.
- Você não pode alterar visuais enquanto estiver nos aplicativos móveis do Power BI. No entanto, todas as alterações visuais salvas em um indicador pessoal no serviço do Power BI são respeitadas nos aplicativos móveis.

Há também alguns problemas conhecidos que estamos abordando:

- Não há suporte para a adição de hierarquia; você precisa adicionar os itens filho individuais.
- Não é possível alterar uma hierarquia de data para uma data ou vice-versa. 
- Com os indicadores pessoais, você pode obter resultados ligeiramente diferentes com base na sequência selecionada. Existe a possibilidade de discrepâncias porque não capturamos o estado completo do relatório, mas apenas as modificações feitas. A solução alternativa é selecionar **Redefinir para o padrão** e, em seguida, selecionar o indicador que você deseja exibir. 

## <a name="next-steps"></a>Próximas etapas

Experimente a nova experiência de personalização visual. Forneça seus comentários sobre esse recurso e como podemos continuar melhorando, [no site Power BI Ideas](https://ideas.powerbi.com/forums/265200-power-bi). 

Mais perguntas? [Experimente a Comunidade do Power BI](https://community.powerbi.com/)

