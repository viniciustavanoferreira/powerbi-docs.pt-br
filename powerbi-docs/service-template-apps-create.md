---
title: Criar aplicativos de modelo no Power BI
description: Como criar aplicativos de modelo no Power BI que podem ser distribuídos para qualquer cliente do Power BI.
author: teddybercovitz
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 09/15/2019
ms.author: tebercov
ms.openlocfilehash: 836dfcc0569c906b145df3e3f3d14f03c08d4938
ms.sourcegitcommit: 8cc2b7510aae76c0334df6f495752e143a5851c4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73432146"
---
# <a name="create-a-template-app-in-power-bi"></a>Criar um aplicativo de modelo no Power BI

Os novos *aplicativos de modelo* do Power BI permitem que os parceiros do Power BI criem aplicativos do Power BI com pouca ou nenhuma codificação e implante-os para qualquer cliente do Power BI.  Este artigo contém instruções passo a passo para a criação de um aplicativo de modelo do Power BI.

Caso possa criar relatórios e dashboards do Power BI, você poderá se tornar um *construtor de aplicativos de modelo* e criar e empacotar o conteúdo analítico em um *aplicativo*. Você pode implantar o aplicativo em outros locatários do Power BI por meio de qualquer plataforma disponível, como o AppSource, ou usando-o em seu próprio serviço Web. Como construtor, você tem a possibilidade de criar um pacote de análise protegido para distribuição.

Os administradores de locatários do Power BI controlam e administram quem, em suas organizações, pode criar aplicativos de modelo e quem pode instalá-los. Aqueles usuários que estão autorizados podem instalar o aplicativo de modelo e, em seguida, modificá-lo e distribuí-lo para os consumidores do Power BI em suas organizações.

## <a name="prerequisites"></a>Pré-requisitos

Estes são os requisitos para a criação de um aplicativo de modelo:  

- Uma [licença do Power BI Pro](service-self-service-signup-for-power-bi.md)
- Uma [instalação do Power BI Desktop](desktop-get-the-desktop.md) (opcional)
- Familiaridade com os [conceitos básicos do Power BI](service-basic-concepts.md)
- Permissões para compartilhar um aplicativo de modelo publicamente. Confira o [portal de administração do Power BI, configurações de Aplicativo de modelo](service-admin-portal.md#template-apps-settings) para obter mais detalhes.

## <a name="create-the-template-workspace"></a>Criar o workspace de modelo

Para criar um aplicativo de modelo que pode ser distribuído para outros locatários do Power BI, você precisa criá-lo em um dos novos workspaces.

1. No serviço do Power BI, selecione **Workspaces** > **Criar workspace**.

    ![Criar o workspace](media/service-template-apps-create/power-bi-new-workspace.png)

2. Em **Criar workspace**, selecione **Atualizar para novo**.

    ![Experimentar os novos workspaces](media/service-template-apps-create/power-bi-upgrade-new.png)

3. Insira um nome, uma descrição (opcional) e a imagem de logotipo (opcional) para o workspace.

4. Expanda a seção **Avançado** e selecione **Desenvolver um aplicativo de modelo**.

    ![Desenvolver um aplicativo de modelo](media/service-template-apps-create/power-bi-template-app-develop.png)

5. Selecione **Salvar**.
>[!NOTE]
>Você precisa de permissões de administrador do Power BI para promover aplicativos de modelo.

## <a name="create-the-content-in-your-template-app"></a>Criar o conteúdo no aplicativo de modelo

Assim como ocorre com um workspace comum do Power BI, a próxima etapa é criar o conteúdo no workspace.  

- [Crie o conteúdo do Power BI](power-bi-creator-landing.md) no workspace.

Caso esteja usando parâmetros no Power Query, verifique se eles têm um tipo bem definido (por exemplo, Texto). Não há suporte para os tipos Qualquer e Binário.

O artigo [Dicas para a criação de aplicativos de modelo no Power BI](service-template-apps-tips.md) traz sugestões a serem consideradas ao criar relatórios e painéis para o aplicativo de modelo.

## <a name="create-the-test-template-app"></a>Criar o aplicativo de modelo de teste

Agora que há algum conteúdo no workspace, você está pronto para empacotá-lo em um aplicativo de modelo. A primeira etapa é criar um aplicativo de modelo de teste, acessível somente na organização do locatário.

1. No workspace de modelo, selecione **Criar aplicativo**.

    ![Criar aplicativo](media/service-template-apps-create/power-bi-create-app.png)

    Aqui, você preenche as opções de compilação adicionais para o aplicativo de modelo, em cinco categorias:

    **Identidade Visual**

    ![Identidade visual](media/service-template-apps-create/power-bi-create-branding.png)
    - Nome do aplicativo
    - Descrição
    - Site de suporte (o link é apresentado nas informações do aplicativo após a redistribuição do aplicativo de modelo como aplicativo da organização)
    - Logotipo do aplicativo (limite de tamanho do arquivo 45K, taxa de proporção de 1:1, formatos .png, .jpg e .jpeg)
    - Cores do tema de aplicativo

    **Navegação**

    Ative o **Novo construtor de navegação**, no qual você pode definir o painel de navegação esquerdo do aplicativo (confira [Projetar a experiência de navegação](service-create-distribute-apps.md#design-the-navigation-experience) neste artigo para obter detalhes).

   ![Definir a página de aterrissagem do aplicativo](media/service-template-apps-install-distribute/power-bi-install-app-content.png)
    
    **Página de aterrissagem do aplicativo:** Se decidir recusar o construtor de navegação, você terá a opção de selecionar a página de aterrissagem do aplicativo. Defina um relatório ou um dashboard para ser a página de aterrissagem do aplicativo. Use uma página de aterrissagem que dê a impressão certa.

    **Controle**

    Defina limitações e restrições que os usuários do aplicativo terão com o conteúdo do aplicativo. Você pode usar esse controle para proteger propriedade intelectual no seu aplicativo.

    ![Controle](media/service-template-apps-create/power-bi-create-control.png)

    >[!NOTE]
    >A exportação para o formato. pbix está sempre bloqueada para usuários que instalam o aplicativo.

    **Parâmetros**

    Use esta categoria para gerenciar o comportamento de parâmetro ao se conectar a fontes de dados. Saiba mais sobre a [criação de parâmetros de consulta](https://powerbi.microsoft.com/blog/deep-dive-into-query-parameters-and-power-bi-templates/).

    ![Parâmetros](media/service-template-apps-create/power-bi-create-parameters.png)
    - **Valor**: valor de parâmetro padrão.
    - **Obrigatório**: use essa opção para exigir o que o instalador insira um parâmetro específico do usuário.
    - **Bloqueio**: o bloqueio impede que o instalador atualize um parâmetro.

    **Acesso** Na fase de teste, decida quais outras pessoas em sua organização podem instalar e testar o aplicativo. Não se preocupe, você sempre poderá voltar e alterar essas configurações posteriormente (a configuração não afeta o acesso do aplicativo de modelo distribuído).

2. Selecione **Criar aplicativo**.

    Você verá uma mensagem indicando que o aplicativo de teste está pronto, com um link para copiar e compartilhar com os testadores do aplicativo.

    ![O aplicativo de teste está pronto](media/service-template-apps-create/power-bi-template-app-test-ready.png)

    Você também realizou a primeira etapa do processo de gerenciamento de versão, que é descrita a seguir.

## <a name="manage-the-template-app-release"></a>Gerenciar a versão do aplicativo de modelo

Antes de liberar esse aplicativo de modelo publicamente, é recomendável verificar se ele está pronto para liberação. O Power BI criou o painel de gerenciamento de versão, no qual você pode seguir e inspecionar o caminho completo da versão do aplicativo. Você também pode disparar a transição de um estágio a outro. Os estágios comuns são:

- Gerar um aplicativo de teste: para teste apenas em sua organização.
- Promover o pacote de teste ao estágio de pré-produção: teste fora de sua organização.
- Promover o pacote de pré-produção à produção: versão de produção.
- Exclua qualquer pacote ou comece novamente no estágio anterior.

O URL não muda quando você se move entre os estágios de lançamento. A promoção não afeta a URL em si.

Vamos percorrer os estágios:

1. No workspace de modelo, selecione **Gerenciamento de Versão**.

    ![Ícone do gerenciamento de versão](media/service-template-apps-create/power-bi-release-management-icon.png)

2. Selecione **Criar aplicativo**.

    Se você criar o aplicativo de teste em **Criar o aplicativo de modelo de teste** acima, o ponto amarelo ao lado de **Teste** já estará preenchido e você não precisará selecionar **Criar aplicativo** aqui. Se você selecioná-lo, voltará ao processo de criação do aplicativo de modelo.

3. Selecione **Obter link**.

    ![Criar aplicativo, obter link](media/service-template-apps-create/power-bi-dev-template-create-app-get-link.png)

4. Para testar a experiência de instalação do aplicativo, copie o link na janela de notificação e cole-o em uma nova janela do navegador.

    Nela, você seguirá o mesmo procedimento que os clientes seguirão. Confira [Instalar e distribuir aplicativos de modelo em sua organização](service-template-apps-install-distribute.md) para a versão deles.

5. Na caixa de diálogo, selecione **Instalar**.

    Quando a instalação for bem-sucedida, você verá uma notificação indicando que o novo aplicativo está pronto.

6. Selecione **Ir para o aplicativo**.
7. Em **Introdução ao novo aplicativo**, você verá o aplicativo como ele será exibido para os clientes.

    ![Introdução ao aplicativo](media/service-template-apps-create/power-bi-template-app-get-started.png)
8. Selecione **Explorar Aplicativo** para verificar o aplicativo de teste com os dados de exemplo.
9. Para fazer alterações, volte ao aplicativo no workspace original. Atualize o aplicativo de teste até ficar satisfeito.
10. Quando estiver pronto para promover o aplicativo à pré-produção para testes adicionais fora do locatário, volte ao painel **Release Management** e selecione **Promover aplicativo**. 

    ![Promover aplicativo à pré-produção](media/service-template-apps-create/power-bi-template-app-promote.png)
    >[!NOTE]
    > Quando o aplicativo é promovido, ele se torna disponível publicamente fora da sua organização.

    Se essa opção não for exibida, contate o administrador do Power BI para que ele conceda [permissões de desenvolvimento de aplicativos de modelo](service-admin-portal.md#template-apps-settings) no portal de administração.
11. Selecione **Promover** para confirmar sua escolha.
12. Copie essa nova URL para compartilhamento fora do locatário para teste. Esse link também é aquele que você enviará para iniciar o processo de distribuição do aplicativo no AppSource ao criar uma [nova oferta do Portal do Cloud Partner](https://docs.microsoft.com/azure/marketplace/cloud-partner-portal/power-bi/cpp-publish-offer). Envie somente links de pré-produção para Portal do Cloud Partner. Somente depois que o aplicativo for aprovado e receber notificação de que está publicado no AppSource, você poderá promover esse pacote para produção no Power BI.
13. Quando o aplicativo estiver pronto para produção ou compartilhamento por meio do AppSource, volte ao painel **Gerenciamento de Versão** e selecione **Promover aplicativo** ao lado de **Pré-produção**.
14. Selecione **Promover** para confirmar sua escolha.

    Agora o aplicativo está em produção e pronto para distribuição.

    ![Aplicativo em produção](media/service-template-apps-create/power-bi-template-app-production.png)

Para disponibilizar o aplicativo amplamente para milhares de usuários do Power BI no mundo, recomendamos que você o envie ao AppSource. Confira a [oferta do Aplicativo do Power BI](https://docs.microsoft.com/azure/marketplace/cloud-partner-portal/power-bi/cpp-power-bi-offer) para obter mais detalhes.

## <a name="next-steps"></a>Próximas etapas

Veja como os clientes interagem com o aplicativo de modelo em [Instalar, personalizar e distribuir aplicativos de modelo em sua organização](service-template-apps-install-distribute.md).

Confira a [oferta do Aplicativo do Power BI](https://docs.microsoft.com/azure/marketplace/cloud-partner-portal/power-bi/cpp-power-bi-offer) para obter mais detalhes sobre como distribuir o aplicativo.
