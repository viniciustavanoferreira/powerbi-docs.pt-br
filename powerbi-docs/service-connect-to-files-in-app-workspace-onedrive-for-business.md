---
title: Conectar-se a arquivos no OneDrive para um workspace do Power BI
description: Leia sobre como armazenar e se conectar aos seus arquivos de Excel, CSV e do Power BI Desktop no OneDrive para o seu workspace do Power BI.
author: maggiesMSFT
ms.reviewer: lukasz
ms.service: powerbi
ms.topic: conceptual
ms.date: 04/15/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 180fd8d451be794070d8b0f4d37c40965671d23d
ms.sourcegitcommit: 6272c4a0f267708ca7d38a45774f3bedd680f2d6
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/06/2020
ms.locfileid: "73854873"
---
# <a name="connect-to-files-stored-in-onedrive-for-your-power-bi-workspace"></a>Conecte-se a arquivos armazenados no OneDrive para seu workspace do Power BI
Após você [criar um workspace no Power BI](service-create-distribute-apps.md), é possível armazenar os arquivos do Excel, de CSV e do Power BI Desktop no OneDrive for Business para o seu workspace do Power BI. Você pode continuar atualizando os arquivos armazenados no OneDrive, e essas atualizações serão refletidas automaticamente nos relatórios e painéis do Power BI com base nos arquivos. 

> [!NOTE]
> A nova experiência de workspace mudará a relação entre os workspaces do Power BI e os grupos do Office 365. Você não criará automaticamente um grupo do Office 365 sempre que criar um dos novos workspaces. Leia sobre [como criar os novos espaços de trabalho](service-create-the-new-workspaces.md)

A adição de arquivos ao seu workspace consiste em um processo de duas etapas: 

1. Primeiro você [carrega arquivos para o OneDrive para Negócios](service-connect-to-files-in-app-workspace-onedrive-for-business.md#1-upload-files-to-the-onedrive-for-business-for-your-workspace) do seu workspace.
2. Em seguida, você [conecta-se a esses arquivos do Power BI](service-connect-to-files-in-app-workspace-onedrive-for-business.md#2-import-excel-files-as-datasets-or-as-excel-online-workbooks).

> [!NOTE]
> Os workspaces estão disponíveis apenas no [Power BI Pro](service-features-license-type.md).
> 

## <a name="1-upload-files-to-the-onedrive-for-business-for-your-workspace"></a>1 Carregar arquivos no OneDrive for Business para o seu workspace
1. No serviço do Power BI, selecione a seta ao lado de Workspaces &gt; selecione as reticências ( **...** ) ao lado do nome do workspace. 
   
   ![](media/service-connect-to-files-in-app-workspace-onedrive-for-business/power-bi-app-ellipsis.png)
2. Selecione **Arquivos** para abrir o OneDrive para Negócios do workspace no Office 365.
   
   > [!NOTE]
   > Se você não vir **Arquivos** no menu do workspace, selecione **Membros** para abrir o OneDrive for Business para o seu workspace. Nele, selecione **Arquivos**. O Office 365 configura um local de armazenamento do OneDrive para seus arquivos do workspace de grupo do aplicativo. Esse processo pode levar algum tempo. 
   > 
   > 
3. Aqui você pode carregar seus arquivos no OneDrive for Business para o seu workspace. Selecione **Carregar**e navegue até os arquivos.
   
   ![](media/service-connect-to-files-in-app-workspace-onedrive-for-business/pbi_grpfilesonedrive.png)

## <a name="2-import-excel-files-as-datasets-or-as-excel-online-workbooks"></a>2 Importar arquivos do Excel como conjuntos de dados ou como pastas de trabalho do Excel Online
Agora que os arquivos estão no OneDrive for Business para o seu workspace, você tem uma opção. Você pode: 

* [Importar os dados da pasta de trabalho do Excel como um conjunto de dados](service-get-data-from-files.md). e usar os dados para criar relatórios e painéis que podem ser exibidos em um navegador da Web e em dispositivos móveis.
* Ou [conectar-se a uma pasta de trabalho completa do Excel no Power BI](service-excel-workbook-files.md) e exibi-la exatamente como aparece no Excel Online.

### <a name="import-or-connect-to-the-files-in-your-workspace"></a>Importar ou conectar-se aos arquivos em seu workspace
1. No Power BI, mude para o workspace, para que o nome do workspace esteja no canto superior esquerdo. 
2. Selecione **Obter Dados** na parte inferior do painel de navegação. 
   
   ![](media/service-connect-to-files-in-app-workspace-onedrive-for-business/power-bi-app-get-data-button.png)
3. Na caixa **Arquivos** , selecione **Obter**.
   
   ![](media/service-connect-to-files-in-app-workspace-onedrive-for-business/pbi_getfiles.png)
4. Selecione **OneDrive** - *Nome do Seu Workspace*.
   
    ![](media/service-connect-to-files-in-app-workspace-onedrive-for-business/pbi_grp_one_drive_shrpt.png)
5. Selecione o arquivo desejado > **Conectar**.
   
    Nessa ocasião, você decide se deseja [importar os dados da pasta de trabalho do Excel](service-get-data-from-files.md) ou [conectar-se a pastas de trabalho inteiras do Excel](service-excel-workbook-files.md).
6. Selecione **Importar** ou **Conectar**.
   
    ![](media/service-connect-to-files-in-app-workspace-onedrive-for-business/pbi_importexceldataorwholecrop.png)
7. Se você selecionar **Importar** a pasta de trabalho aparecerá na guia **Conjuntos de dados**. 
   
    ![](media/service-connect-to-files-in-app-workspace-onedrive-for-business/power-bi-app-excel-file-import.png)
   
    Se você selecionar **Conectar**, a pasta de trabalho estará na guia **Pastas de trabalho**.
   
    ![](media/service-connect-to-files-in-app-workspace-onedrive-for-business/power-bi-app-excel-file-connect.png)

## <a name="next-steps"></a>Próximas etapas
* [Criar aplicativos e workspaces no Power BI](service-create-distribute-apps.md)
* [Importar dados das pastas de trabalho do Excel](service-get-data-from-files.md)
* [Conectar-se a todas as pastas de trabalho do Excel](service-excel-workbook-files.md)
* Mais perguntas? [Experimente a Comunidade do Power BI](https://community.powerbi.com/)
* Comentários? Visite [Power BI Ideias](https://ideas.powerbi.com/forums/265200-power-bi) (Ideias do Power BI)

