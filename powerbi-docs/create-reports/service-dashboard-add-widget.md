---
title: Adicionar imagens, vídeos e outros elementos a seu dashboard
description: Documentação de como usar o widget Adicionar bloco para adicionar uma imagem, um vídeo, uma caixa de texto, um código da Web e um bloco de dados de streaming em um dashboard.
author: maggiesMSFT
ms.reviewer: ''
featuredvideoid: e2PD8m1Q0vU
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 07/25/2019
ms.author: maggies
LocalizationGroup: Dashboards
ms.openlocfilehash: f98fb7a9d5a01c70eb8cef2a8d5befdbe919d796
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85219463"
---
# <a name="add-images-videos-and-more-to-your-dashboard"></a>Adicionar imagens, vídeos e outros elementos a seu dashboard

Adicione blocos a seu dashboard para incluir imagens, caixas de texto, vídeos, dados de streaming ou códigos da Web. 

Veja Amanda adicionar blocos a um dashboard.

   
<iframe width="560" height="315" src="https://www.youtube.com/embed/e2PD8m1Q0vU" frameborder="0" allowfullscreen></iframe>


## <a name="add-an-image-video-or-other-tile"></a>Adicionar uma imagem, um vídeo ou outro bloco
Você pode adicionar uma imagem, uma caixa de texto, um vídeo, dados de streaming ou código da Web diretamente ao seu dashboard.

1. Selecione **Adicionar bloco** na barra de menus superior do dashboard. Dependendo das limitações de espaço, você poderá ver apenas o sinal de adição ![sinal de adição](media/service-dashboard-add-widget/power-bi-add-tile-icon-small.png).
   
    ![Ícone Adicionar bloco](media/service-dashboard-add-widget/power-bi-add-tile-icon.png)
2. Selecione o tipo de bloco para adicionar: 

    **[Conteúdo da Web](#add-web-content)**

    **[Imagem](#add-an-image)**

    **[Caixa de texto](#add-a-text-box-or-dashboard-heading)**

    **[Vídeo](#add-a-video)**

    **[Dados de streaming personalizados](#add-streaming-data)**
   
    ![Janela Adicionar bloco](media/service-dashboard-add-widget/power-bi-add-tile.png)

## <a name="add-an-image"></a>Adicionar uma imagem
Caso queira adicionar o logotipo da sua empresa ou outra imagem, salve o arquivo de imagem online e vincule-o ao dashboard. Certifique-se de que não sejam necessárias credenciais de segurança para acessar o arquivo de imagem. Por exemplo, como o OneDrive e o SharePoint exigem autenticação, as imagens armazenadas lá não podem ser adicionadas a um dashboard dessa maneira.  

1. Na janela **Adicionar bloco**, selecione **Imagem** > **Avançar**.

2. Na janela **Adicionar bloco de imagens**, adicione as informações da imagem:   
   
   a. Para exibir um título acima da imagem, selecione **Exibir título e subtítulo** e insira um **Título** e um **Subtítulo** opcional.

   b. Insira a **URL** da imagem.

   c. Para tornar o bloco em um hiperlink, selecione **Definir link personalizado** e insira a **URL**. 

      Quando clicarem no título ou na imagem, seus colegas serão levados para essa URL.

   d. Selecione **Aplicar**. 

      ![janela Adicionar bloco de imagem](media/service-dashboard-add-widget/pbi-widget-add-image-new.png)

3. No painel, redimensione e mova a imagem, conforme necessário.
     
     ![Imagem no dashboard](media/service-dashboard-add-widget/power-bi-add-image-dash.png)

## <a name="add-a-text-box-or-dashboard-heading"></a>Adicionar um título de painel ou caixa de texto

Para adicionar um título de dashboard, digite o título na caixa de texto e aumente a fonte.

1. Na janela **Adicionar bloco**, selecione **Caixa de texto** > **Avançar**.

2. Formate a caixa de texto:
   
   a. Para exibir um título acima da caixa de texto, selecione **Exibir título e subtítulo** e insira um **Título** e um **Subtítulo** opcional.

   b. Insira e formate o **Conteúdo** da caixa de texto.  

   c. Opcionalmente, defina um link personalizado para o título. Um link personalizado pode ser um site externo ou um painel ou relatório no workspace. No entanto, neste exemplo, como adicionamos hiperlinks na própria caixa de texto, deixaremos desmarcada a opção **Definir link personalizado**.

   d. Selecione **Aplicar**. 

     ![Janela Adicionar bloco de caixa de texto](media/service-dashboard-add-widget/power-bi-add-textbox.png)
   
3. No painel, redimensione e mova a caixa de texto, conforme necessário.
   
   ![dashboard com imagem e caixa de texto](media/service-dashboard-add-widget/pbi-widget-text-added-new.png)

## <a name="add-a-video"></a>Adicionar um vídeo
Quando você adiciona um bloco de vídeo do YouTube ou Vimeo a seu painel, o vídeo é reproduzido diretamente no painel.

1. Na janela **Adicionar bloco**, selecione **Vídeo** > **Avançar**.
2. Adicione informações sobre o vídeo na janela **Adicionar bloco de vídeo**:   
   
   a. Para exibir um título e um subtítulo na parte superior do bloco de vídeo, selecione **Exibir título e subtítulo** e insira um **Título** e um **Subtítulo** opcional. Neste exemplo, adicionaremos um **Subtítulo** e o converteremos em um hiperlink para a playlist inteira no YouTube.

   b. Insira a **URL do Vídeo**.

   c. Adicione um hiperlink ao **Título** e ao **Subtítulo**, para que seus colegas possam ver a playlist inteira no YouTube depois de assistirem ao vídeo inserido. Para fazer isso, em **Funcionalidade**, selecione **Definir link personalizado** e, em seguida, insira a **URL** para a playlist.

   d. Selecione **Aplicar**.  

   ![Janela Adicionar bloco de vídeo](media/service-dashboard-add-widget/power-bi-add-video-new.png)

3. No painel, redimensione e mova o bloco de vídeo, conforme necessário.
     
   ![Dashboard com bloco de vídeo adicionado](media/service-dashboard-add-widget/pbi-widget-video-added-new.png)
4. Selecione o bloco de vídeo para reproduzir o vídeo.
5. Selecione o subtítulo para visitar a playlist no YouTube.

## <a name="add-streaming-data"></a>Adicionar dados de streaming
Você pode usar o PubNub para adicionar dados de streaming, como feeds do Twitter ou dados de sensor, a um bloco em seu dashboard. O Power BI criou uma integração para obter os dados do PubNub. Aqui, Will explicará como ela funciona.
   

<iframe width="560" height="315" src="https://www.youtube.com/embed/kOuINwgkEkQ" frameborder="0" allowfullscreen></iframe>

1. Na janela **Adicionar bloco**, selecione **Dados de Streaming Personalizados** > **Avançar**.
2. Selecione **Adicionar conjunto de dados de streaming**.
3. Crie um **Novo conjunto de dados de streaming** usando a API do Power BI ou o PubNub.
4. Preencha os campos **Nome do conjunto de dados**, **Chave de assinatura** e **Nome do canal**. Se for uma conexão segura, ela também terá uma chave de autorização. Você pode usar os valores de exemplo para experimentar o PubNub.
5. Selecione **Avançar**.
    Você vê os campos que estão disponíveis no conjunto de dados, com os tipos de dados e o formato JSON.
6. Selecione **Conectar**.
    Você criou um conjunto de dados de streaming.
7. Volte para o dashboard e, mais uma vez, selecione **Adicionar bloco** > **Dados de Streaming Personalizados** > **Avançar**.
8. Selecione o conjunto de dados de sensor que você criou, em seguida, clique em **Avançar**.
9. Selecione o tipo de visual desejado. Geralmente, gráficos de linhas funcionam bem para esses dados.
10. Selecione o **Eixo**, a **Legenda** e os **Valores**.
11. Decida o período para exibição dos dados: segundos, minutos ou horas.
12. Selecione **Avançar**.
13. Forneça um **Título** e um **Subtítulo**, se desejar.
14. Fixe-o ao seu dashboard.


1. Na janela **Adicionar bloco**, selecione **Dados de Streaming Personalizados** > **Avançar**.

2. Selecione **Adicionar conjunto de dados de streaming**.

3. Crie um **Novo conjunto de dados de streaming** usando a API do Power BI ou o PubNub.

4. Preencha os campos **Nome do conjunto de dados**, **Chave de assinatura** e **Nome do canal**. Se for uma conexão segura, ela também terá uma chave de autorização. Você pode usar os valores de exemplo para experimentar o PubNub.

5. Selecione **Avançar**.

   Você vê os campos que estão disponíveis no conjunto de dados, com os tipos de dados e o formato JSON.

6. Selecione **Conectar**.

   Você criou um conjunto de dados de streaming.

7. Volte para o dashboard e, mais uma vez, selecione **Adicionar bloco** > **Dados de Streaming Personalizados** > **Avançar**.

8. Selecione o conjunto de dados de sensor que você criou, em seguida, clique em **Avançar**.

9. Selecione o tipo de visual desejado. Geralmente, gráficos de linhas funcionam bem para esses dados.

10. Selecione o **Eixo**, a **Legenda** e os **Valores**.

11. Decida o período para exibição dos dados: segundos, minutos ou horas.

12. Selecione **Avançar**.

13. Opcionalmente, dê um **Título** e um **Subtítulo**.

14. Fixe-o ao seu dashboard.

## <a name="add-web-content"></a>Adicionar conteúdo da Web
Você pode colar ou digitar qualquer conteúdo HTML, como um bloco, em seu relatório ou dashboard. Insira o código de inserção manualmente ou obtenha a URL de sites como: Twitter, YouTube, embed.ly etc.

1. Na janela **Adicionar bloco**, selecione **Conteúdo da Web** > **Avançar**.

2. Adicione as informações à janela **Adicionar bloco de conteúdo da Web**:
   
   a. Para exibir um título acima do bloco, selecione **Exibir título e subtítulo** e insira um **Título** e um **Subtítulo** opcional.

   b. Insira o código de inserção. Neste exemplo, estamos copiando e colando um feed do Twitter.

   c. Selecione **Aplicar**.

   ![Janela Adicionar bloco de conteúdo da Web](media/service-dashboard-add-widget/power-bi-add-web-content.png)
   

3. No painel, redimensione e mova o bloco de conteúdo da Web, conforme necessário.
     
   ![Dashboard com quatro blocos](media/service-dashboard-add-widget/pbi-widget-code-added-new.png)

### <a name="tips-for-embedding-web-content"></a>Dicas para incorporar o conteúdo da Web
* Para iframes, use uma fonte segura. Se você inserir o código de inserção do iframe e obtiver um bloco em branco, verifique se não está usando *http* como a fonte do iframe. Se estiver, altere-a para *https*.
  
  ```html
  <iframe src="https://xyz.com">
  ```
* Edite as informações de largura e de altura. O código de inserção incorpora um vídeo e define o player de vídeo para 560 x 315 pixels. Esse tamanho não mudará conforme você redimensionar o bloco.
  
  ```html
  <iframe width="560" height="315"
  src="https://www.youtube.com/embed/Cle_rKBpZ28" frameborder="0"
   allowfullscreen></iframe>
  ```
  
  Se você quiser que o player seja redimensionado para se ajustar ao tamanho do bloco, defina a largura e a altura como 100%.
  
  ```html
  <iframe width="100%" height="100%"
  src="https://www.youtube.com/embed/Cle_rKBpZ28" frameborder="0"
   allowfullscreen></iframe>
  ```
* Esse código incorpora um tweet e mantém, como links separados no dashboard, links para o podcast AFK, a página do Twitter do \@GuyInACube, Seguir, #analytics, responder, retweetar e curtir.  Selecionar o bloco propriamente dito leva você até o podcast no Twitter.
  
  ```html
  <blockquote class="twitter-tweet" data-partner="tweetdeck">
  <p lang="en" dir="ltr">Listen to
  <a href="https://twitter.com/GuyInACube">@GuyInACube</a> talk to
  us about making videos about Microsoft Business Intelligence
  platform
  <a href="https://t.co/TmRgalz7tv">https://t.co/TmRgalz7tv </a>
  <a href="https://twitter.com/hashtag/analytics?src=hash">
  #analytics</a></p>&mdash; AFTK Podcast (@aftkpodcast) <a
  href="https://twitter.com/aftkpodcast/status/693465456531771392">
  January 30, 2016</a></blockquote> <script async src="//platform.twitter.com/widgets.js" charset="utf-8"></script>
  ```

## <a name="edit-a-tile"></a>Editar um bloco
Para fazer alterações em um bloco existente:

1. Posicione o cursor sobre o canto superior direito do bloco e selecione **Mais opções** (...).
   
    ![selecionar reticências do bloco](media/service-dashboard-add-widget/pbi_ellipses.png)
2. Selecione **Editar detalhes** para exibir a janela **Detalhes do bloco** e fazer alterações.
   
    ![Editar detalhes](media/service-dashboard-add-widget/pbi-edit.png)

## <a name="considerations-and-troubleshooting"></a>Considerações e solução de problemas
* Para facilitar ainda mais a movimentação do bloco em seu dashboard, adicione um título e um subtítulo opcional.
* Se você quiser inserir conteúdo de um site, mas ele não disponibilizar o código de inserção para cópia, acesse embed.ly para obter ajuda sobre a geração do código de inserção.

## <a name="next-steps"></a>Próximas etapas
[Introdução aos blocos de dashboard para designers do Power BI](service-dashboard-tiles.md)

Mais perguntas? [Experimente a Comunidade do Power BI](https://community.powerbi.com/).

