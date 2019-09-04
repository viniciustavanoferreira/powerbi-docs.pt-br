---
title: Publicar por meio do Power BI Desktop
description: Publicar por meio do Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 08/29/2019
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 69e458d966e656847a4e2122df148e90c1834a58
ms.sourcegitcommit: c0f4d00d483121556a1646b413bab75b9f309ae9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/29/2019
ms.locfileid: "70160315"
---
# <a name="publish-from-power-bi-desktop"></a>Publicar por meio do Power BI Desktop
Quando você publicar um arquivo do **Power BI Desktop** no **serviço do Power BI**, os dados no modelo e os relatórios criados na exibição **Relatório** serão publicados no workspace do Power BI. Você verá um novo conjunto de dados com o mesmo nome e todos os relatórios no seu navegador de workspace.

Publicar por meio do **Power BI Desktop** tem o mesmo efeito que usar **Obter Dados** no Power BI para se conectar e carregar um arquivo do **Power BI Desktop**.

> [!NOTE]
> Quaisquer alterações feitas no relatório do Power BI, como adicionar, excluir ou alterar visualizações em relatórios, não serão salvas no arquivo original do **Power BI Desktop**.
> 
> 

## <a name="to-publish-a-power-bi-desktop-dataset-and-reports"></a>Para publicar relatórios e um conjunto de dados e relatório do Power BI Desktop
1. No Power BI Desktop, selecione **Arquivo** \> **Publicar** \> **Publicar no Power BI** ou clique em **Publicar** na faixa de opções.  

   ![Botão Publicar](media/desktop-upload-desktop-files/pbid_publish_publishbutton.png)

2. Entre no Power BI.
3. Selecionar o destino.

   ![Selecione Publicar destino](media/desktop-upload-desktop-files/pbid_publish_select_destination.png)

Você receberá um link para seu relatório após a conclusão. Clique no link para abrir o relatório no site do Power BI.

![Caixa de diálogo de Publicação bem-sucedida](media/desktop-upload-desktop-files/pbid_publish_success.png)

## <a name="re-publish-or-replace-a-dataset-published-from-power-bi-desktop"></a>Publicar novamente ou substituir um conjunto de dados publicado por meio do Power BI Desktop
Ao publicar um arquivo do **Power BI Desktop**, o conjunto de dados e relatórios criados no **Power BI Desktop** são carregados no seu site do Power BI. Quando você publicar novamente o arquivo do **Power BI Desktop**, o conjunto de dados no seu site do Power BI será substituído pelo conjunto de dados atualizado do arquivo do **Power BI Desktop**.

Isso é tudo muito simples, mas há algumas coisas que você deve saber:

* Se você já tiver dois ou mais conjuntos de dados no Power BI com o mesmo nome que o arquivo do **Power BI Desktop**, a publicação poderá falhar. Verifique se que você tem apenas um conjunto de dados no Power BI com o mesmo nome. Também pode renomear o arquivo e publicar, criando um novo conjunto de dados com o mesmo nome de arquivo.
* Se você renomear ou excluir uma coluna ou medida, qualquer visualizações que você já tenha no Power BI com esse campo poderá ser desfeita. 
* O Power BI ignora as alterações de formato de colunas existentes. Por exemplo, se você alterar o formato de uma coluna de 0,25 para 25%.
* Se você tiver um agendamento de atualização configurado para o conjunto de dados existente no Power BI e adicionar novas fontes de dados ao seu arquivo e, em seguida, publicá-las novamente, será necessário entrar nelas em *Gerenciar Fontes de Dados* antes da próxima atualização agendada.
* Ao republicar um conjunto de dados publicado do **Power BI Desktop** e definir um cronograma de atualização, a atualização de um conjunto de dados é iniciada assim que você republicar. 

