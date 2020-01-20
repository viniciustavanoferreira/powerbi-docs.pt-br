---
title: Criar um relatório em uma Lista do SharePoint
description: Este tutorial mostra como transformar os dados da Lista do SharePoint em um relatório Power BI.
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: tutorial
ms.date: 01/10/2020
ms.author: davidi
LocalizationGroup: Visualizations
ms.openlocfilehash: 4fd350ae5d4a916e6753f7cd66e1fca52137efd5
ms.sourcegitcommit: 052df769e6ace7b9848493cde9f618d6a2ae7df9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/14/2020
ms.locfileid: "75925652"
---
# <a name="create-a-report-on-a-sharepoint-list"></a>Criar um relatório em uma Lista do SharePoint

Muitas equipes e organizações usam Listas no SharePoint Online para armazenar dados porque é fácil configurar e fácil para os usuários atualizarem.  Às vezes, um gráfico é uma maneira muito mais fácil para os usuários entenderem rapidamente os dados em vez de examinar a lista em si. Neste tutorial, mostramos como transformar os dados da Lista do SharePoint em um relatório do Power BI.

Assista a este vídeo de tutorial de cinco minutos ou role para baixo para obter instruções passo a passo.

<iframe width="400" height="450" src="https://www.youtube.com/embed/OZO3x2NF8Ak" frameborder="0" allowfullscreen></iframe>

## <a name="part-1-connect-to-your-sharepoint-list"></a>Parte 1: Conectar-se à Lista do SharePoint

1. Se você ainda não o tiver, baixe e instale o [Power BI Desktop](https://powerbi.microsoft.com/desktop/).
2. Abra o Power BI Desktop e, na guia Página Inicial da faixa de opções, selecione **Obter Dados** > **Mais**.
3. Selecione **Serviços Online** e, em seguida, **Lista do SharePoint Online**.  

    <img src="media/desktop-sharepoint-online-list/desktop-sharepoint-online-list-getdata.png" alt="get data" width="350"/>

4. Selecione **Conectar**.
4. Localize o endereço (também conhecido como uma URL) do site do SharePoint Online que contém sua lista.  Em uma página no SharePoint Online, geralmente você pode obter o endereço do site selecionando **Página Inicial** no painel de navegação ou o ícone do site na parte superior e, em seguida, copiando o endereço da barra de endereços do navegador da Web.

   Assista a um vídeo desta etapa:
   <iframe width="400" height="300" src="https://www.youtube.com/embed/OZO3x2NF8Ak?start=48&end=90" frameborder="0" allowfullscreen></iframe>

5. No Power BI Desktop, cole o endereço no campo **URL do Site** na caixa de diálogo aberta.

6. Você pode ou não ver uma tela de acesso do SharePoint como a imagem a seguir.  Se você não a vir, passe para a etapa 10.  Se você a vir, selecione **Conta Microsoft** no lado esquerdo da página.

    <img src="media/desktop-sharepoint-online-list/desktop-sharepoint-online-list-auth1.png" alt="choose Microsoft account" width="500"/>

7. Selecione **Entrar** e insira o nome de usuário e a senha usados para entrar no Microsoft Office 365.

    <img src="media/desktop-sharepoint-online-list/desktop-sharepoint-online-list-auth2.png" alt="sign in" width="500"/>

8. Quando terminar de entrar, selecione **Conectar**.

9. No lado esquerdo do Navegador, marque a caixa de seleção ao lado da lista do SharePoint à qual você deseja se conectar.

    <img src="media/desktop-sharepoint-online-list/desktop-sharepoint-online-list-select-list.png" alt="get data" width="450"/>

10. Selecione **Carregar**.  O Power BI carrega seus dados de lista para um novo relatório.

## <a name="part-2-create-a-report"></a>Parte 2: Criar um relatório

1. No lado esquerdo, selecione o ícone **Dados** para ver se seus dados da lista do SharePoint foram carregados.

2. Verifique se suas colunas de lista com números mostram o ícone Soma, ou Sigma, no **painel Campos** à direita.  Para as que não mostrarem, selecione o cabeçalho da coluna na exibição de tabela, selecione a guia **Modelagem** e altere o **Tipo de dados** para **Número Decimal** ou **Número Inteiro**, dependendo dos dados.  Se for solicitado que você confirme a alteração, selecione **Sim**.  Se seu número tiver um formato especial, como moeda, você também poderá escolher isso definindo o **Formato**.

   Assista a um vídeo desta etapa:
   <iframe width="400" height="300" src="https://www.youtube.com/embed/OZO3x2NF8Ak?start=147&end=204" frameborder="0" allowfullscreen></iframe>

3. No lado esquerdo, selecione o ícone **Relatório**.
4. Selecione as colunas que você deseja visualizar marcando a caixa de seleção ao lado delas no painel **Campos** à direita.

   Assista a um vídeo desta etapa:
   <iframe width="400" height="300" src="https://www.youtube.com/embed/OZO3x2NF8Ak?start=215&end=252" frameborder="0" allowfullscreen></iframe>

5. Altere o tipo de visual, se necessário.
6. Você pode criar várias visualizações no mesmo relatório desmarcando o visual existente e marcando caixas de seleção para outras colunas no painel **Campos**.
7. Selecione **Salvar** para salvar seu relatório.
