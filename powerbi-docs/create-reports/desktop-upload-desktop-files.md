---
title: Publicar por meio do Power BI Desktop
description: Publicar por meio do Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/20/2020
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 4a363ce72002003981f1bcbe46e0f5367f89860f
ms.sourcegitcommit: c1f05254eaf5adb563f8d4f33c299119134c7d1f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83733452"
---
# <a name="publish-datasets-and-reports-from-power-bi-desktop"></a>Publicar conjuntos de dados e relatórios por meio do Power BI Desktop
Ao publicar um arquivo do Power BI Desktop no serviço do Power BI, você publica os dados no modelo em seu workspace do Power BI. O mesmo vale para todos os relatórios criados na exibição **Relatório**. Você verá um novo conjunto de dados com o mesmo nome e todos os relatórios no seu navegador de workspace.

Publicar por meio do Power BI Desktop tem o mesmo efeito que usar **Obter Dados** no Power BI para conectar e carregar um arquivo do Power BI Desktop.

> [!NOTE]
> As alterações feitas ao relatório no Power BI não serão salvas de volta no arquivo original do Power BI Desktop. Isso inclui quando você adiciona, exclui ou altera visualizações em relatórios.
> 
> 

## <a name="to-publish-a-power-bi-desktop-dataset-and-reports"></a>Para publicar relatórios e um conjunto de dados e relatório do Power BI Desktop
1. No Power BI Desktop, escolha **Arquivo** \> **Publicar** \> **Publicar no Power BI** ou selecione **Publicar** na faixa de opções.  

   ![Botão Publicar](media/desktop-upload-desktop-files/pbid_publish_publishbutton.png)

2. Entre no Power BI.
3. Selecionar o destino.

   ![Selecione Publicar destino](media/desktop-upload-desktop-files/pbid_publish_select_destination.png)

Quando a publicação for concluída, você receberá um link para seu relatório. Selecione o link para abrir o relatório no site do Power BI.

![Caixa de diálogo de Publicação bem-sucedida](media/desktop-upload-desktop-files/pbid_publish_success.png)

## <a name="republish-or-replace-a-dataset-published-from-power-bi-desktop"></a>Republicar ou substituir um conjunto de dados publicado por meio do Power BI Desktop
O conjunto de dados e todos os relatórios criados no Power BI Desktop são carregados para seu site do Power BI quando você publica um arquivo do Power BI Desktop. Quando você republica o arquivo do Power BI Desktop, o conjunto de dados no seu site do Power BI é substituído pelo conjunto de dados atualizado do arquivo do Power BI Desktop.

Esse processo é simples, mas há algumas coisas que você deve saber:

* Dois ou mais conjuntos de dados no Power BI com o mesmo nome que o arquivo do Power BI Desktop podem causar a falha da publicação. Verifique se que você tem apenas um conjunto de dados no Power BI com o mesmo nome. Também pode renomear o arquivo e publicar, criando um novo conjunto de dados com o mesmo nome de arquivo.
* Se você renomear ou excluir uma coluna ou medida, qualquer visualizações que você já tenha no Power BI com esse campo poderá ser desfeita. 
* O Power BI ignora as alterações de formato de colunas existentes. Por exemplo, se você alterar o formato de uma coluna de 0,25% para 25%.
* Digamos que você tenha uma agenda de atualização configurada para seu conjunto de dados no Power BI. Ao adicionar novas fontes de dados ao arquivo e republicar, você precisará entrar nelas antes da próxima atualização agendada.
* Ao republicar um conjunto de dados publicado do Power BI Desktop e definir uma agenda de atualização, a atualização de um conjunto de dados é iniciada assim que você republicar.
* Quando você faz uma alteração em um conjunto e o publica novamente, uma mensagem mostra quantos workspaces, relatórios e dashboards são potencialmente afetados pela alteração e solicita que confirme que deseja substituir o conjunto de dados atualmente publicado pelo que você modificou. A mensagem também fornece um link para a análise de impacto completa do conjunto de dados no serviço do Power BI, em que você pode ver mais informações e tomar medidas para atenuar os riscos de sua alteração.

   ![Aviso sobre o impacto da republicação de um conjunto de dados](media/desktop-upload-desktop-files/pbid-dataset-impact-analysis-desktop-warning.png)

   [Saiba mais sobre a análise do impacto do conjunto de dados](../collaborate-share/service-dataset-impact-analysis.md).