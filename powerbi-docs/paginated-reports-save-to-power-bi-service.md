---
title: Publicar um relatório paginado no serviço do Power BI
description: Neste tutorial, você aprende a publicar um relatório paginado no serviço do Power BI fazendo o upload do computador local.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 01/03/2020
ms.openlocfilehash: 5f77e17eccf4c99e7a391ea310a34848c604e01d
ms.sourcegitcommit: b68a47b1854588a319a5a2d5d6a79bba2da3a4e6
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2020
ms.locfileid: "75732074"
---
# <a name="publish-a-paginated-report-to-the-power-bi-service"></a>Publicar um relatório paginado no serviço do Power BI

Neste artigo, você aprende a publicar um relatório paginado no serviço do Power BI fazendo o upload do computador local. Você pode carregar relatórios paginados para o Meu Workspace ou qualquer outro workspace, desde que o workspace esteja em uma capacidade Premium. Localize o ícone de losango ![Ícone de losango da capacidade do Power BI Premium](media/paginated-reports-save-to-power-bi-service/premium-diamond.png) ao lado do nome do workspace. 

Se a fonte de dados do relatório estiver no local, você precisará criar um gateway depois de carregar o relatório. Confira a seção [Criar um gateway](#create-a-gateway) mais adiante neste artigo.

## <a name="add-a-workspace-to-a-premium-capacity"></a>Adicionar um workspace a uma capacidade Premium

Se o workspace não tem o ícone de losango ![Ícone de losango da capacidade do Power BI Premium](media/paginated-reports-save-to-power-bi-service/premium-diamond.png) ao lado do nome, você precisará adicionar o workspace a uma capacidade Premium. 

1. Selecione **Workspaces**, selecione as reticências ( **...** ) ao lado do nome do workspace e, em seguida, selecione **Editar Workspace**.

    ![Selecionar Editar Workspace](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-edit-workspace.png)

1. Na caixa de diálogo **Editar Workspace**, expanda **Avançado** e, em seguida, deslize **Capacidade dedicada** para **Ativado**.

    ![Selecionar Capacidade Dedicada](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-edit-workspace-dialog.png)

   Talvez não seja possível alterá-la. Caso contrário, entre em contato com o administrador da capacidade do Power BI Premium para conceder a você direitos de atribuição para adicionar seu workspace a uma capacidade Premium.

## <a name="from-report-builder-publish-a-paginated-report"></a>No Report Builder, publique um relatório paginado

1. Crie seu relatório paginado no Construtor de Relatórios e salve-o em seu computador local.

1. No menu **Arquivo** do Report Builder, selecione **Salvar como**.

    ![Menu Arquivo > Salvar > Salvar como](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-save-as.png)

    Se você ainda não tiver entrado no Power BI, precisará entrar nele ou criar uma conta agora. No canto superior direito do Report Builder, selecione **Entrar** e conclua as etapas.

2. Na lista de workspaces à esquerda, selecione um workspace com o ícone de losango ![ícone de losango de capacidade do Power BI Premium](media/paginated-reports-save-to-power-bi-service/premium-diamond.png) ao lado do respectivo nome. Digite um **Nome de arquivo** na caixa > **Salvar**. 

    ![Selecionar um workspace Premium](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-select-workspace.png)

4. Abra o serviço do Power BI em um navegador e procure o workspace Premium em que o relatório paginado foi publicado. Na guia **Relatórios**, você verá o relatório.

    ![Relatório paginado na lista Relatórios](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-wwi-report.png)

5. Selecione o relatório paginado para abri-lo no serviço do Power BI. Se tiver parâmetros, você precisará selecioná-los antes de poder exibir o relatório.

    ![Selecionar parâmetros](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-select-parameters.png)

6. Se a fonte de dados do relatório estiver no local, leia mais sobre como [criar um gateway](#create-a-gateway) neste artigo para acessar a fonte de dados.

## <a name="from-the-power-bi-service-upload-a-paginated-report"></a>No serviço do Power BI, carregue um relatório paginado

Inicie também no serviço do Power BI e carregue um relatório paginado.

1. Crie seu relatório paginado no Construtor de Relatórios e salve-o em seu computador local.

1. Abra o serviço do Power BI em um navegador e navegue até o workspace Premium onde deseja publicar o relatório. Observe o ícone de losango ![Ícone de losango da capacidade do Power BI Premium](media/paginated-reports-save-to-power-bi-service/premium-diamond.png) ao lado do nome. 

1. Selecione **Obter Dados**.

    ![Obter Dados do Power BI](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-get-data.png)

1. Na caixa **Arquivos** , selecione **Obter**.

    ![Obter Arquivos do Power BI](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-files-get.png)

1. Selecione **Arquivo Local** > navegue até o relatório paginado > **Abrir**.

    ![Selecionar Arquivo Local](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-local-file.png)

1. Selecione **Continuar** > **Editar Credenciais**.

    ![Selecionar Editar Credenciais](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-select-edit-credentials.png)

1. Configure suas credenciais > **Entrar**.

    ![Editar credenciais](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-credentials.png)

   Na guia **Relatórios**, você verá o relatório.

    ![Relatório paginado na lista Relatórios](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-wwi-report.png)

1. Selecione-o para abri-lo no serviço do Power BI. Se tiver parâmetros, você precisará selecioná-los antes de poder exibir o relatório.
 
    ![Selecionar parâmetros](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-select-parameters.png)

6. Se a fonte de dados do relatório estiver no local, leia mais sobre como [criar um gateway](#create-a-gateway) neste artigo para acessar a fonte de dados.

## <a name="create-a-gateway"></a>Criar um gateway

Assim como qualquer outro relatório do Power BI, se a fonte de dados do relatório estiver no local, você precisará criar ou conectar-se a um gateway para acessar os dados.

1. Ao lado do nome do relatório, selecione **Gerenciar**.

   ![Gerenciar um relatório paginado](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-manage.png)

1. Veja o artigo de serviço do Power BI [O que é um gateway de dados local](service-gateway-onprem.md) para obter detalhes e as próximas etapas.

### <a name="gateway-limitations"></a>Limitações de gateway

Atualmente, os gateways não dão suporte a parâmetros de vários valores.


## <a name="next-steps"></a>Próximas etapas

- [Exibir um relatório paginado no serviço do Power BI](consumer/paginated-reports-view-power-bi-service.md)
- [O que são os relatórios paginados no Power BI Premium?](paginated-reports-report-builder-power-bi.md)
- [Tutorial: Inserir relatórios paginados do Power BI em um aplicativo para seus clientes](developer/embed-paginated-reports-customers.md)

