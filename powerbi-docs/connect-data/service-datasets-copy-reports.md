---
title: Copiar relatórios de outros aplicativos e workspaces – Power BI
description: Saiba como você pode criar e salvar uma cópia do relatório em seu próprio workspace.
author: maggiesMSFT
ms.reviewer: kayu
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/30/2020
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: d70f029568dca578bb76350a42b5146ecc335759
ms.sourcegitcommit: 5e5a7e15cdd55f71b0806016ff91256a398704c1
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83793099"
---
# <a name="copy-reports-from-other-workspaces"></a>Copiar relatórios de outros workspaces

Quando encontrar um relatório de sua preferência em um workspace ou aplicativo, você poderá fazer uma cópia dele e salvá-lo em um workspace diferente. Em seguida, você pode modificar esse relatório, adicionando ou excluindo visuais e outros elementos. Você não precisa se preocupar com a criação do modelo de dados. Ele já foi criado para você. Além disso, é muito mais fácil modificar um relatório existente do que começar do zero. No entanto, ao criar um aplicativo no seu workspace, algumas vezes você não pode publicar sua cópia do relatório no aplicativo. Para ver detalhes, confira [Considerações e limitações no artigo "Usar conjuntos de dados em workspaces"](service-datasets-across-workspaces.md#considerations-and-limitations).

> [!NOTE]
> Para fazer uma cópia, você precisa de uma licença Pro, mesmo que o relatório original esteja em um workspace em uma capacidade Premium.

## <a name="save-a-copy-of-a-report-in-a-workspace"></a>Salvar uma cópia de um relatório no workspace

1. Em um workspace, acesse a exibição de lista Relatórios.

    ![Exibição de lista de relatórios](media/service-datasets-copy-reports/power-bi-report-list-view.png)

1. Em **Ações**, selecione **Salvar uma cópia**.

    ![Salvar uma cópia de um relatório](media/service-datasets-copy-reports/power-bi-dataset-save-report-copy.png)

    Você só verá o ícone **Salvar uma cópia** se o relatório estiver em um workspace da nova experiência e você tiver a [permissão Criar](service-datasets-build-permissions.md). Mesmo que tiver acesso ao workspace, você precisará ter a permissão Criar no conjunto de dados.

3. Em **Salvar uma cópia deste relatório**, dê um nome ao relatório e selecione o workspace de destino.

    ![Caixa de diálogo Salvar uma cópia](media/service-datasets-copy-reports/power-bi-dataset-save-report.png)

    Salve o relatório no workspace atual ou em outro workspace no serviço do Power BI. Você só verá os workspaces que são os workspaces da nova experiência no qual você é membro. 
  
4. Selecione **Salvar**.

    O Power BI cria automaticamente uma cópia do relatório e uma entrada na lista de conjuntos de dados se o relatório é baseado em um conjunto de dados fora do workspace. O ícone para esse conjunto de dados é diferente do ícone para conjuntos de dados no workspace: ![Ícone do conjunto de dados compartilhado](media/service-datasets-discover-across-workspaces/power-bi-shared-dataset-icon.png)
    
    Dessa forma, os membros do workspace podem saber quais relatórios e dashboards usam conjuntos de dados que estão fora do workspace. A entrada mostra informações sobre o conjunto de dados e algumas ações selecionadas.

    ![Ações do conjunto de dados](media/service-datasets-across-workspaces/power-bi-dataset-actions.png)

    Confira a [Sua cópia do relatório](#your-copy-of-the-report) neste artigo para obter mais informações sobre o relatório e o conjunto de dados relacionado.

## <a name="copy-a-report-in-an-app"></a>Copiar um relatório em um aplicativo

1. Em um aplicativo, abra o relatório que você deseja copiar.
2. Na barra de menus, selecione **Mais opções** ( **...** ) > **Salvar uma cópia**.

    ![Salvar uma cópia do relatório](media/service-datasets-copy-reports/power-bi-save-copy.png)

    Você só verá a opção **Salvar uma cópia** se o relatório estiver em um workspace da nova experiência e você tiver a [permissão Criar](service-datasets-build-permissions.md).

3. Dê um nome ao seu relatório > **Salvar**.

    ![Nomear sua cópia do relatório](media/service-datasets-copy-reports/power-bi-save-report-from-app.png)

    Sua cópia é salva automaticamente no My Workspace.

4. Selecione **Ir para o relatório** para abrir a cópia.

## <a name="your-copy-of-the-report"></a>Sua cópia do relatório

Ao salvar uma cópia do relatório, você criará uma conexão dinâmica com o conjunto de dados e poderá abrir a experiência de criação de relatório com o conjunto de dados completo disponível. 

![Editar sua cópia do relatório](media/service-datasets-copy-reports/power-bi-edit-report-copy.png)

Você não fez uma cópia do conjunto de dados. O conjunto de dados ainda reside em sua localização original. Você pode usar todas as tabelas e as medidas no conjunto de dados para criar seu próprio relatório. As restrições de RLS (Segurança em Nível de Linha) no conjunto de dados estão em vigor, de modo que você veja apenas os dados que têm permissões de ver de acordo com sua função RLS.

## <a name="view-related-datasets"></a>Exibir conjuntos de dados relacionados

Quando você tem um relatório em um workspace baseado em um conjunto de dados em outro workspace, talvez seja necessário saber mais sobre o conjunto de dados no qual ele se baseia.

1. Na exibição de lista Relatórios, selecione **Exibir relacionados**.

    ![Ícone Exibir relacionados](media/service-datasets-copy-reports/power-bi-dataset-view-related.png)

1. A caixa de diálogo **Conteúdo relacionado** mostra todos os itens relacionados. Nessa lista, o conjunto de dados se parece com qualquer outro. Você não pode saber se ele reside em outro workspace. Esse problema é conhecido.
 
    ![Caixa de diálogo Conteúdo relacionado](media/service-datasets-copy-reports/power-bi-dataset-related.png)

## <a name="delete-a-report-and-its-shared-dataset"></a>Excluir um relatório e seu conjunto de dados compartilhado

Você pode decidir que não deseja mais o relatório e seu conjunto de dados compartilhado associado no workspace.

1. Exclua o relatório. Na lista de relatórios no espaço de trabalho, selecione o ícone **Excluir**.

    ![Excluir ícone de relatório](media/service-datasets-across-workspaces/power-bi-datasets-delete-report.png)

2. Na lista de conjuntos de dados, você vê que os conjuntos de dados compartilhados não têm ícones **Excluir**. Atualize a página ou vá para uma página diferente e retorne. O conjunto de dados será eliminado. Caso contrário, verifique **Exibição relacionada**. Pode estar relacionado a outra tabela em seu workspace.

    ![Ícone Exibir relacionados](media/service-datasets-across-workspaces/power-bi-dataset-view-related-icon.png)

    > [!NOTE]
    > A exclusão do conjunto de dados compartilhado neste workspace não exclui o conjunto de dados. Ela exclui apenas a referência a ele.


## <a name="next-steps"></a>Próximas etapas

- [Usar conjuntos de dados em workspaces](service-datasets-across-workspaces.md)
- Dúvidas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
