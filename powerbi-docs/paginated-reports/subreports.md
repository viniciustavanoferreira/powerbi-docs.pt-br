---
title: Sub-relatórios em relatórios paginados no Power BI
description: Neste artigo, você aprenderá sobre as fontes de dados compatíveis para relatórios paginados no serviço do Power BI e como se conectar a fontes de dados do Banco de Dados SQL do Azure.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 04/29/2020
ms.openlocfilehash: 65d1401a66f8e670df1af3097f0e99fb6b647022
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82615693"
---
# <a name="subreports-in-power-bi-paginated-reports"></a>Sub-relatórios em relatórios paginados no Power BI

Um *sub-relatório* é um item de relatório paginado que exibe outro relatório paginado dentro do corpo de um relatório paginado principal. Conceitualmente, um sub-relatório em um relatório é semelhante a um quadro em uma página da Web. Use-o para inserir um relatório dentro de um relatório. É possível usar qualquer relatório como um sub-relatório. Armazene o relatório que é exibido como sub-relatório no mesmo workspace Premium que o do relatório pai. Você pode designar o relatório pai para transmitir parâmetros ao sub-relatório. Um sub-relatório pode ser repetido em regiões de dados, usando um parâmetro para filtrar dados em cada instância do sub-relatório.  
  
 ![Sub-relatório um relatório paginado](media/subreports/paginated-report-subreport.png "Sub-relatório do relatório paginado")  
  
 Nesta ilustração, as informações de contato exibidas no relatório de Ordem de Venda principal vêm de um sub-relatório Contatos.  
  
Crie e modifique arquivos de definição de relatório paginado (.rdl) no Power BI Report Builder. Você pode carregar os sub-relatórios armazenados no SQL Server Reporting Services para um workspace Premium no serviço do Power BI. Os relatórios principais e os sub-relatórios precisam ser publicados no mesmo workspace. Instale o [Power BI Report Builder](https://go.microsoft.com/fwlink/?linkid=2086513).
  
## <a name="work-with-report-builder-and-the-power-bi-service"></a>Trabalhar com o Report Builder e o serviço do Power BI

O Power BI Report Builder pode trabalhar com relatórios paginados em seu computador (conhecidos como relatórios locais) ou com relatórios no serviço do Power BI.  Ao abrir o Report Builder pela primeira vez, você deverá entrar na sua conta do Power BI. Caso contrário, selecione **Entrar** no canto superior direito.

:::image type="content" source="media/subreports/report-builder-sign-in.png" alt-text="Entrar no Power BI":::

Depois de entrar, você verá uma opção **Serviço do Power BI** no Power BI Report Builder para as opções **Abrir** e **Salvar como** no menu **Arquivo**. Ao selecionar a opção **Serviço do Power BI** para salvar um relatório, você cria uma conexão dinâmica entre o Power BI Report Builder e o serviço do Power BI. 

:::image type="content" source="media/subreports/report-builder-subreport-open-service.png" alt-text="Abrir de um serviço do Power BI":::

## <a name="save-a-local-report-to-the-power-bi-service"></a>Salvar um relatório local no serviço do Power BI

Para adicionar um sub-relatório a um relatório principal, primeiro crie os dois relatórios e salve-os no mesmo workspace do Power BI Premium. 

1. Para abrir um relatório local existente, no menu **Arquivo**, selecione **Abrir** > **Este computador** e selecione um arquivo .rdl.  

2. No menu **Arquivo**, selecione **Salvar Como** > **Serviço do Power BI**.  Confira [Publicar um relatório paginado no serviço do Power BI](paginated-reports-save-to-power-bi-service.md) para obter detalhes.

    > [!NOTE]
    > Também é possível carregar um relatório iniciando no serviço do Power BI. O mesmo artigo, [Publicar um relatório paginado no serviço do Power BI](paginated-reports-save-to-power-bi-service.md), tem detalhes.

3. Na caixa de diálogo **Salvar como**, selecione um workspace do Power BI Premium em que você pode armazenar seus relatórios paginados.  Os workspaces Premium têm um ícone de losango ![ícone de losango Premium](media/subreports/report-builder-premium-diamond.png) ao lado do nome.

    :::image type="content" source="media/subreports/report-builder-subreport-save-as-service.png" alt-text="Salvar como no serviço do Power BI":::

4. Selecione **Salvar**.

## <a name="add-a-subreport-to-a-report"></a>Adicionar um sub-relatório a um relatório

Agora que você salvou os dois relatórios no mesmo workspace Premium, pode adicionar um ao outro como um sub-relatório. Há duas maneiras de adicionar um sub-relatório. 

1. Na faixa de opções **Inserir**, selecione o botão **Sub-relatório** ou clique com o botão direito do mouse na tela do relatório e selecione **Inserir** > **Sub-relatório**.

    :::image type="content" source="media/subreports/report-builder-insert-subreport.png" alt-text="Inserir um sub-relatório em um relatório":::

    A caixa de diálogo **Propriedades do Sub-relatório** é aberta.  

2. Selecione o botão **Procurar** > navegue até o relatório que você deseja usar como sub-relatório > especifique o nome do sub-relatório na caixa de texto **Nome**.

3. Configure outras propriedades conforme necessário, incluindo [parâmetros](#use-parameters-in-subreports).

## <a name="use-parameters-in-subreports"></a>Usar parâmetros em sub-relatórios  
 Para passar os parâmetros do relatório pai para o sub-relatório, defina um parâmetro de relatório no relatório que está sendo usado como o sub-relatório. Ao inserir o sub-relatório no relatório pai, você poderá selecionar o parâmetro de relatório e um valor que poderão ser passados do relatório pai para o parâmetro de relatório no sub-relatório.  
  
> [!NOTE]  
> O parâmetro que você seleciona no sub-relatório é um parâmetro de *relatório*, não um parâmetro de *consulta*.  
  
 É possível colocar o sub-relatório no corpo principal do relatório ou em uma região de dados. Se você posicionar o sub-relatório em uma região de dados, ele será repetido em cada instância do grupo ou da linha na região de dados. Você pode passar um valor do grupo ou da linha para o sub-relatório. Na propriedade de valor do sub-relatório, use uma expressão de campo para o campo que contém o valor que você deseja passar para o parâmetro de sub-relatório.  
  
 Para obter mais informações sobre como trabalhar com parâmetros e sub-relatórios, confira [Adicionar um sub-relatório e parâmetros](https://docs.microsoft.com/sql/reporting-services/report-design/add-a-subreport-and-parameters-report-builder-and-ssrs.md) na documentação do SQL Server Reporting Services.  

## <a name="preview-paginated-reports-in-report-builder"></a>Visualizar relatórios paginados no Report Builder

É possível visualizar seus relatórios no Report Builder.

- Na faixa de opções **Página Inicial**, selecione **Executar**. 

Como o Report Builder é uma ferramenta de design, a visualização do relatório pode parecer diferente da renderização do relatório no serviço do Power BI.

### <a name="notes-about-previewing"></a>Observações sobre a visualização

- O Report Builder não armazena credenciais para fontes de dados usadas em relatórios.  O Report Builder solicita cada conjunto de credenciais durante a visualização.  
- Se as fontes de dados do relatório estiverem no local, você precisará configurar um gateway depois de salvar o relatório no workspace do Power BI.
- Se o Report Builder encontrar um erro durante a visualização, ele retornará uma mensagem genérica.  Se o erro for difícil de depurar, considere renderizar o relatório no serviço do Power BI.  

## <a name="considerations"></a>Considerações

### <a name="maintaining-the-connection"></a>Manutenção da conexão

O Report Builder não mantém a conexão com Power BI quando você fecha o arquivo.  É possível trabalhar com um relatório principal local com sub-relatórios armazenados no workspace do Power BI. Certifique-se de salvar o relatório principal no workspace do Power BI antes de fechar o relatório.  Caso contrário, você poderá receber uma mensagem 'não encontrado' durante a visualização, porque não há conexão dinâmica com a serviço do Power BI.  Nesse caso, vá para um sub-relatório e selecione as propriedades.  Abra o sub-relatório novamente do serviço do Power BI.  Isso restabelece a conexão e todos os outros sub-relatórios devem estar bem.

### <a name="renaming-a-subreport"></a>Como renomear um sub-relatório

Se você renomear um sub-relatório no workspace, precisará corrigir a referência de nome no relatório principal. Caso contrário, o sub-relatório não será renderizado. O relatório principal ainda é renderizado com uma mensagem de erro dentro do item de sub-relatório.

## <a name="migrate-large-reports"></a>Migrar relatórios grandes

Se você estiver migrando relatórios grandes para o Power BI, considere o uso da [ferramenta RdlMigration](../guidance/migrate-ssrs-reports-to-power-bi.md).  A ferramenta RdlMigration foi atualizada para manipular nomes de sub-relatório duplicados.  Nomes de sub-relatório duplicados podem ocorrer quando dois ou mais relatórios compartilham o mesmo nome, mas residem em subdiretórios diferentes.  Se os nomes não forem resolvidos exclusivamente, somente o primeiro sub-relatório será reconhecido.

Se você quiser usar o Report Builder para migrar relatórios grandes, é recomendável trabalhar primeiro com os sub-relatórios. Salve cada um no workspace do Power BI para impedir nomes de relatório duplicados.

## <a name="share-reports-with-subreports"></a>Compartilhar relatórios com sub-relatórios

Como dissemos, o relatório principal e os sub-relatórios precisam estar no mesmo workspace. Caso contrário, o sub-relatório não é renderizado. Ao compartilhar o relatório principal, você também precisa compartilhar os sub-relatórios. Se você compartilhar o relatório principal em um aplicativo, inclua também os sub-relatórios nesse aplicativo. Se você compartilhar o relatório principal com usuários ou grupos de usuários diretamente, compartilhe também cada sub-relatório com o mesmo conjunto de usuários ou grupos de usuários.
  
## <a name="next-steps"></a>Próximas etapas

[Solucionar problemas de sub-relatórios em relatórios paginados no Power BI](subreports-troubleshoot.md)

[Exibir um relatório paginado no serviço do Power BI](../consumer/paginated-reports-view-power-bi-service.md)

Mais perguntas? [Experimente a Comunidade do Power BI](https://community.powerbi.com/)
