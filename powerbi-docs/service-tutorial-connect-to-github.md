---
title: 'Tutorial: Conectar-se a um repositório GitHub com o Power BI'
description: Neste tutorial, você se conecta a dados reais no serviço do GitHub com o Power BI, e Power BI cria dashboards e relatórios automaticamente.
author: maggiesMSFT
ms.reviewer: SarinaJoan
ms.service: powerbi
ms.subservice: powerbi-service
ms.custom: connect-to-services
ms.topic: tutorial
ms.date: 08/07/2019
ms.author: maggies
LocalizationGroup: Connect to services
ms.openlocfilehash: a3c87a700df1c35596b6520cc64d9b580ccb74eb
ms.sourcegitcommit: 444f7fe5068841ede2a366d60c79dcc9420772d4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/30/2020
ms.locfileid: "80403401"
---
# <a name="tutorial-connect-to-a-github-repo-with-power-bi"></a>Tutorial: Conectar-se a um repositório GitHub com o Power BI
Neste tutorial, você se conecta a dados reais no serviço do GitHub com o Power BI, e Power BI cria dashboards e relatórios automaticamente. Conecte-se ao repositório público de conteúdo do Power BI (também conhecido como *repo*) e veja as respostas para perguntas como: Quantas pessoas contribuem com o conteúdo público do Power BI? Quem contribui mais? Qual dia da semana tem mais contribuições? Dentre outras perguntas. 

![O relatório do GitHub no Power BI](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-punch-card.png)

Neste tutorial, você concluirá as etapas a seguir:

> [!div class="checklist"]
> * Inscrever-se para uma conta do GitHub, caso ainda não tenha uma 
> * Entrar em sua conta do Power BI ou inscrever-se, caso ainda não tenha uma
> * Abrir o serviço do Power BI
> * Encontrar o aplicativo GitHub
> * Inserir as informações do repositório GitHub público do Power BI
> * Exibir o dashboard e o relatório com os dados do GitHub
> * Limpar os recursos, excluindo o aplicativo

Se você não estiver inscrito no Power BI, [inscreva-se para uma avaliação gratuita](https://app.powerbi.com/signupredirect?pbi_source=web) antes de começar.

## <a name="prerequisites"></a>Pré-requisitos

Para concluir este tutorial, você precisará de uma conta do GitHub, caso ainda não tenha uma. 

- Inscrever-se para uma [conta do GitHub](https://docs.microsoft.com/contribute/get-started-setup-github).


## <a name="how-to-connect"></a>Como se conectar
1. Entre no serviço do Power BI (`https://app.powerbi.com`). 
2. No painel de navegação, selecione **Aplicativos** e **Obter aplicativos**.
   
   ![Obter aplicativos do Power BI](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial.png) 

3. Selecione **Aplicativos**, digite **GitHub** na caixa de pesquisa > **Obtenha agora**.
   
   ![Get GitHub do Power BI](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-app-source.png) 

4. Em **Instalar este aplicativo do Power BI?** selecione **Instalar**.
5. Em **Seu novo aplicativo está pronto**, selecione **Ir para o aplicativo**.
6. Em **Introdução a seu novo aplicativo**, selecione **Conectar**.

    ![Introdução ao novo aplicativo](media/service-tutorial-connect-to-github/power-bi-new-app-connect-get-started.png)

7. Digite o nome do repositório e também o seu proprietário. A URL desse repositório é https://github.com/MicrosoftDocs/powerbi-docs, portanto o **Proprietário do Repositório** é **MicrosoftDocs** e o **Repositório** é **powerbi-docs**. 
   
    ![Nome do repositório do GitHub do Power BI](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-connect.png)

5. Insira as credenciais do GitHub que você criou. O Power BI poderá ignorar esta etapa se você já tiver entrado no GitHub em seu navegador. 

6. Como **Método de Autenticação**, mantenha **oAuth2** selecionado para **Entrar** no \>.

7. Siga as telas de autenticação do GitHub. Conceda permissão para o Power BI aos dados do GitHub.
   
   Agora o Power BI pode se conectar ao GitHub e aos dados.  Os dados são atualizados uma vez por dia.

8. Depois que o Power BI importa os dados, você vê os conteúdos de seu novo workspace do GitHub. 
9. Selecione a seta ao lado do nome do workspace no painel de navegação. Você vê que o workspace contém um dashboard e um relatório. 

    ![Aplicativo no painel de navegação](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-left-nav-expanded.png)

10. Selecione **Mais opções** (...) ao lado do nome do dashboard > **Renomear** > digite **dashboard do GitHub**.
 
    ![Bloco do GitHub do Power BI](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-left-nav.png) 

8. Selecione o ícone de navegação global para minimizar o painel de navegação, aumentando o espaço disponível.

    ![Ícone de navegação global](media/service-tutorial-connect-to-github/power-bi-global-navigation-icon.png)

10. Selecione o seu dashboard do GitHub.
    
    O dashboard do GitHub contém dados dinâmicos, portanto, os valores exibidos podem ser diferentes.

    ![Dashboard do GitHub no Power BI](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-new-dashboard.png)

    

## <a name="ask-a-question"></a>Fazer uma pergunta

1. Coloque o cursor em **Faça uma pergunta sobre os dados**. O Power BI oferece **Perguntas para você começar**. 

1. Selecione **Quantos usuários existem?** .
 
    ![Quantos usuários existem?](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-qna-how-many-users.png)

13. Entre **Quantos** e **usuários existem**, digite **solicitações de pull por**. 

     O Power BI cria um gráfico de barras mostrando o número de solicitações de pull por pessoa.

    ![Quantas solicitações de pull por usuário existem?](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-qna-how-many-prs.png)


13. Selecione fixar para fixá-la ao seu dashboard e, em seguida, **Saia das P e R**.

## <a name="view-the-github-report"></a>Exibir o relatório do GitHub 

1. No dashboard do GitHub, selecione o gráfico de colunas com as **Solicitações de Pull por Mês** para abrir o relatório relacionado.

    ![Gráfico de colunas com as solicitações de pull por mês](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-column-chart.png)

2. Selecione um nome de usuário no gráfico **Total de solicitações de pull por usuário**. Neste exemplo, vemos que a maior parte de suas horas foram em fevereiro.

    ![Realce do relatório do GitHub do Power BI](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-cross-filter-total-prs.png)

3. Selecione a guia **Cartão de Pontos** para exibir a próxima página do relatório. 
 
    ![Cartão de Pontos do relatório do GitHub do Power BI](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-tues-3pm.png)

    Aparentemente, terça-feira às 15h é o dia da semana e a hora mais comuns para *confirmações (commits)* , quando as pessoas fazem check-in de seus trabalhos.

## <a name="clean-up-resources"></a>Limpar recursos

Agora que você já concluiu o tutorial, é possível excluir o aplicativo GitHub. 

1. No painel de navegação, selecione **Aplicativos**.
2. Focalize o bloco do GitHub e selecione a lixeira **Excluir**.

    ![Excluir o aplicativo GitHub](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-delete.png)

## <a name="next-steps"></a>Próximas etapas

Neste tutorial, você se conectou a um repositório público do GitHub e obteve dados que o Power BI formatou em um dashboard e em um relatório. Você respondeu algumas perguntas sobre os dados explorando o dashboard e o relatório. Agora você pode aprender mais sobre como se conectar a outros serviços, como o Salesforce, o Microsoft Dynamics e o Google Analytics. 
 
> [!div class="nextstepaction"]
> [Conectar aos serviços online que você usa](service-connect-to-services.md)


