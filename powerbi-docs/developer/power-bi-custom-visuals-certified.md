---
title: Visuais do Power BI certificados
description: Requisitos e processos de envio de um visual personalizado para certificação e uma lista de visuais do Power BI certificados.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.topic: conceptual
ms.subservice: powerbi-custom-visuals
ms.date: 02/17/2020
ms.openlocfilehash: 52a99380f8e1afc39ddfc59a401418e61fe6ad58
ms.sourcegitcommit: ec4d2d0f52d737e8e0583f6a7b16e6fd87382510
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2020
ms.locfileid: "77782425"
---
# <a name="get-a-power-bi-visual-certified"></a>Certificar um visual do Power BI

Os visuais certificados do Power BI são visuais do Power BI na [AppSource](https://appsource.microsoft.com/en-us/marketplace/apps?page=1&product=power-bi-visuals) que atendem aos [requisitos de código](#certification-requirements) da equipe do Microsoft Power BI. Esses visuais são testados para confirmar que não acessam serviços ou recursos externos, e que seguem diretrizes e padrões de codificação seguros.

Depois que um visual do Power BI é certificado, ele oferece mais recursos. Por exemplo, você pode [exportar para o PowerPoint](../consumer/end-user-powerpoint.md) ou exibir o visual em emails recebidos quando um usuário [assina páginas do relatório](../consumer/end-user-subscribe.md).

O processo de certificação é opcional. Os visuais do Power BI que não são certificados não são necessariamente inseguros. Alguns visuais do Power BI não são certificados por não atenderem a um ou mais dos [requisitos de certificação](https://docs.microsoft.com/power-bi/power-bi-custom-visuals-certified?#certification-requirements). Por exemplo, um visual do mapa do Power BI que se conecta a um serviço externo ou um visual do Power BI que usa bibliotecas comerciais.

> [!NOTE]
> A Microsoft não é a autora de visuais do Power BI de terceiros. Entre em contato diretamente com o autor para verificar a funcionalidade dos visuais de terceiros.

## <a name="certification-requirements"></a>Requisitos de certificação

Para [certificar](#get-a-power-bi-visual-certified) seu visual do Power BI, ele deverá estar em conformidade com os requisitos listados nesta seção. 

### <a name="general-requirements"></a>Requisitos gerais

Seu visual do Power BI precisa ser aprovado pelo Painel do Vendedor ou Partner Center. Recomendamos que o seu visual do Power BI já esteja na [AppSource](https://appsource.microsoft.com/marketplace/apps?page=1&product=power-bi-visuals). Veja como publicar um visual do Power BI na AppSource em [Publicar visuais do Power BI no Partner Center](office-store.md).

Antes de enviar o seu visual do Power BI para certificação, verifique se ele está em conformidade com as [diretrizes para visuais do Power BI](./guidelines-powerbi-visuals.md).

Ao enviar o visual do Power BI, certifique-se de que o pacote compilado corresponda exatamente ao pacote enviado.

### <a name="code-repository-requirements"></a>Requisitos do repositório de códigos

Embora não seja necessário compartilhar publicamente seu código no GitHub, o repositório de código precisa estar disponível para análise da equipe do Power BI. A melhor maneira de fazer isso é fornecendo o código-fonte (JavaScript ou TypeScript) no GitHub.

O repositório deve conter o seguinte:
* Código para apenas um visual do Power BI. Ele não pode conter o código de vários visuais do Power BI nem de códigos não relacionados.
* Um branch chamado **certification** (é necessário que esteja em letras minúsculas). O código-fonte nessa ramificação deve corresponder ao pacote enviado. Esse código só poderá ser atualizado durante o próximo processo de envio, se você estiver reenviando seu visual do Power BI.

Se seu visual do Power BI usar pacotes npm privados ou submódulos git, você deverá fornecer acesso aos repositórios adicionais que contêm esse código.

Para entender como é a aparência de um repositório do visual do Power BI, examine o [gráfico de barras de exemplo de visuais do Power BI](https://github.com/microsoft/PowerBI-visuals-sampleBarChartgi) no repositório GitHub.

### <a name="file-requirements"></a>Requisitos de arquivo

Use a versão mais recente da API para gravar o visual do Power BI.

O repositório deve incluir os seguintes arquivos:
* **.gitignore** – adicione `node_modules` a este arquivo. O código não pode incluir a pasta *node_modules*.
* **capabilities.json** – se estiver enviando uma versão mais recente do seu visual do Power BI com alterações nas propriedades desse arquivo, verifique se elas não interrompem relatórios para os usuários existentes.
* **pbiviz.json**
* **package.json**
* **package-lock.json**
* **tsconfig.json**

### <a name="command-requirements"></a>Requisitos de comando

Os comandos a seguir não devem retornar erros.

* `npm install`
* `pbiviz package`
* `npm audit` – não deve retornar qualquer aviso de nível alto ou moderado.
* [TSlint da Microsoft](https://www.npmjs.com/package/tslint-microsoft-contrib) sem configurações substituídas. Esse comando não deve retornar erros de lint.

### <a name="compiling-requirements"></a>Requisitos de compilação

Use a versão mais recente do [powerbi-visuals-tools](https://www.npmjs.com/package/powerbi-visuals-tools) para gravar o visual do Power BI.

O visual do Power BI deve ser compilado com `pbiviz package`. Se estiver usando seus próprios scripts de compilação, forneça um comando personalizado de compilação `npm run package`.



### <a name="source-code-requirements"></a>Requisitos do código-fonte

Verifique se está seguindo a lista de políticas de [certificação adicional de visuais do Power BI](https://docs.microsoft.com/legal/marketplace/certification-policies#1200-power-bi-visuals-additional-certification). Se o envio não seguir essas diretrizes, o email de rejeição do Partner Center incluirá os números da política listados nesse link.

Siga os requisitos de código listados abaixo para garantir que seu código esteja alinhado com as políticas de certificação do Power BI.  

**Necessário**
* Use apenas componentes públicos OSS analisáveis, como bibliotecas JavaScript ou TypeScript públicas.
* O código deve ser compatível com a [API de Renderização de Eventos](./visuals/event-service.md).
* Verifique se o DOM é manipulado com segurança. Use a limpeza para os dados do usuário ou a entrada do usuário, antes de adicioná-lo ao DOM.
* Use o [relatório de exemplo](https://github.com/Microsoft/PowerBI-visuals/raw/gh-pages/assets/reports/large_data.pbix) como um conjunto de dados de teste.

**Não permitido**
* Acesso a serviços ou recursos externos. Por exemplo, nenhuma solicitação HTTP/S ou WebSocket pode sair do Power BI para outros serviços.
* Uso de `innerHTML` ou `D3.html(user data or user input)`.
* Erros ou exceções de JavaScript no console do navegador para os dados de entrada.
* Código arbitrário ou dinâmico, como `eval()`, uso inseguro de `settimeout()`, `requestAnimationFrame()`, `setinterval(user input function)` e entrada do usuário ou dados do usuário.
* Arquivos ou projetos reduzidos do JavaScript.

## <a name="submitting-a-power-bi-visual-for-certification"></a>Enviar um visual do Power BI para certificação

Você pode solicitar que seu visual do Power BI seja certificado pela equipe do Power BI por meio do Partner Center.

>[!TIP]
>O processo de certificação do Power BI pode demorar um pouco. Se você estiver criando um novo visual do Power BI, recomendamos que o publique por meio do Partner Center antes de solicitar a certificação do Power BI. Isso garante que a publicação do visual não seja adiada.

Para solicitar a certificação do Power BI:

1. Conecte-se ao Partner Center.
2. Na **página Visão Geral**, escolha seu visual do Power BI e vá para a página de configuração do **Produto**.
3. Marque a caixa de seleção **Solicitar a certificação do Power BI**.
4. Na página **Revisar e publicar**, na caixa de texto **Notas para certificação**, forneça um link para o código-fonte e as credenciais necessárias para acessá-lo.

>[!NOTE]
> Se você estiver no meio de um processo de envio de visual do Power BI e precisar usar o [Painel do Vendedor](https://docs.microsoft.com/office/dev/store/use-the-seller-dashboard-to-submit-to-the-office-store) (a antiga ferramenta de gerenciamento), confira as instruções em [Processo de envio da certificação do Painel do Vendedor](seller-dashboard.md#seller-dashboard-certification-submission-process).

### <a name="private-repository-submission-process"></a>Processo de envio de repositório particular

Se você estiver usando um repositório particular, como o GitHub, para enviar seu visual do Power BI para certificação, siga as instruções nesta seção.
1. Crie uma nova conta para a equipe de validação.
2. Configure a [autenticação de dois fatores](https://help.github.com/github/authenticating-to-github/securing-your-account-with-two-factor-authentication-2fa) para a sua conta.
3. [Gere um novo conjunto de códigos de recuperação](https://help.github.com/github/authenticating-to-github/configuring-two-factor-authentication-recovery-methods#generating-a-new-set-of-recovery-codes).
4. Ao enviar o visual do Power BI, forneça o seguinte:
    * Um link para o repositório
    * Credenciais de logon (incluindo uma senha)
    * Códigos de recuperação
    * Permissões somente de leitura para nossa conta ([pbicvsupport](https://github.com/pbicvsupport))

## <a name="certified-power-bi-visuals"></a>Visuais do Power BI certificados

Os visuais do Power BI certificados estão listados abaixo. Clique no link para abrir o visual do Power BI no AppSource. Se um vídeo estiver disponível, você poderá clicar no link para assistir.

* [Sistemas 3AG – Gráfico de barras com variação absoluta](https://appsource.microsoft.com/product/power-bi-visuals/WA104381802)
*  [3AG Systems – Bar Chart With Relative Variance](https://appsource.microsoft.com/product/power-bi-visuals/WA104381912) (Sistemas 3AG – Gráfico de barras com variação relativa)
*  [3AG Systems – Column Chart With Relative Variance](https://appsource.microsoft.com/product/power-bi-visuals/WA104381803) (Sistemas 3AG – gráfico de colunas com variação relativa)
*  [Sistemas 3AG – gráfico de colunas com variação](https://appsource.microsoft.com/product/power-bi-visuals/WA104381724)
* [Visual de Rosca Avançado (edição completa)](https://appsource.microsoft.com/product/power-bi-visuals/WA104381941)
*  [Visual de Rosca Avançado (edição light)](https://appsource.microsoft.com/product/power-bi-visuals/WA104380858)
*  [Visual de Gráfico Avançado](https://appsource.microsoft.com/product/power-bi-visuals/WA104382086)
*  [Visualização de Rede Avançada](https://appsource.microsoft.com/product/power-bi-visuals/WA104381942)
*  [Visual de Série Temporal Avançado (edição completa)](https://appsource.microsoft.com/product/power-bi-visuals/WA104381943)
*  [Aster Plot](https://appsource.microsoft.com/product/power-bi-visuals/WA104380759)
*  [Beyondsoft Calendar](https://appsource.microsoft.com/product/power-bi-visuals/WA104381096)
*  [Bowtie Chart by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380838)
*  [Box and Whisker chart](https://appsource.microsoft.com/product/power-bi-visuals/WA104380831)
* [Box and Whisker chart by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104381351)
*  [Brick Chart by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380836)
*  [Bubble Chart by Akvelon](https://appsource.microsoft.com/product/power-bi-visuals/WA104381340)
*  [Gráfico com marcadores](https://appsource.microsoft.com/product/power-bi-visuals/WA104380755), **[link](https://youtu.be/AOlsFYkfkcw)** do vídeo
* [Bullet Chart](https://appsource.microsoft.com/product/power-bi-visuals/WA104380755)
*  [Bullet Chart by OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104380953), **[link do vídeo](https://youtu.be/mtvUNl9bMjA)**
* [Calendar by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104381844)
*  [Calendar by Tallan](https://appsource.microsoft.com/product/power-bi-visuals/WA104381146)
*  [Candlestick by OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104380952) **[link do vídeo](https://youtu.be/nT_18gyRxPo)**
*  [Card with States by OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104380967)
*  [Chiclet Slicer](https://appsource.microsoft.com/product/power-bi-visuals/WA104380756)
*  [Chord](https://appsource.microsoft.com/product/power-bi-visuals/WA104380761), **[link do vídeo](https://youtu.be/AQvd2FhRyCI)**
*  [Circular Gauge by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380837)
*  [Cluster Map](https://appsource.microsoft.com/product/power-bi-visuals/WA104380806)
* [Custom Calendar by Akvelon](https://appsource.microsoft.com/product/power-bi-visuals/WA104381179)
* [Cylindrical Gauge by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380874)
*  [Indicador de Discagem](https://appsource.microsoft.com/product/power-bi-visuals/WA104381184)
[Gráfico de Pontos](https://appsource.microsoft.com/product/power-bi-visuals/WA104380760)
*  [Dot Plot by OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104380949), **[link do vídeo](https://youtu.be/By16pX9KT40)**
*  [Drilldown Cartogram](https://appsource.microsoft.com/product/power-bi-visuals/WA104381045)
*  [Drilldown Choropleth](https://appsource.microsoft.com/product/power-bi-visuals/WA104381044)
*  [Gráfico de colunas de busca detalhada](https://appsource.microsoft.com/product/power-bi-visuals/WA104380857), **[link do vídeo](https://youtu.be/lBy2gQQ5YsQ)**
*  [Gráfico de colunas de busca detalhada para dados baseados em tempo](https://appsource.microsoft.com/product/power-bi-visuals/WA104380881), **[link do vídeo](https://youtu.be/T_mRou18vx0)**
*  [Gráfico de rosca com busca detalhada](https://appsource.microsoft.com/product/power-bi-visuals/WA104380858), **[link do vídeo](https://youtu.be/AUVFrSHmPeo)**
*  [Dual KPI](https://appsource.microsoft.com/product/power-bi-visuals/WA104380774)
*  [Dica de ferramenta dinâmica pelo Software MAQ](https://appsource.microsoft.com/product/power-bi-visuals/WA104380983)
*  [Dispersão Avançada](https://appsource.microsoft.com/product/power-bi-visuals/WA104380762), **[link do vídeo](https://youtu.be/xCfM0cjM4do)**
*  [Enlighten Aquarium](https://appsource.microsoft.com/product/power-bi-visuals/WA104381112)
*  [Enlighten Slicer](https://appsource.microsoft.com/product/power-bi-visuals/WA104380960)
*  [Enlighten Stack Shuffle](https://appsource.microsoft.com/product/power-bi-visuals/WA104380849)
*  [Enlighten Waffle Chart](https://appsource.microsoft.com/product/power-bi-visuals/WA104380850)
*  [Filter by List by Devscope](https://appsource.microsoft.com/product/power-bi-visuals/WA104381413), **[link do vídeo](https://youtu.be/RetEWGwBu0I)**
*  [Gráfico Direcionado por Força](https://appsource.microsoft.com/product/power-bi-visuals/WA104380764), **[link do vídeo](https://youtu.be/YsTa7uyJ4sg)**
*  [Funnel with Source by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104381334)
*  [Gantt](https://appsource.microsoft.com/product/power-bi-visuals/WA104380765), **[link do vídeo](https://youtu.be/qJ7s_KrGiUU)**
* [Gantt Chart by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104381364)
*  [Globe Data Bars](https://appsource.microsoft.com/product/power-bi-visuals/WA104381344)
*  [Grid da MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380825)
*  [Hierarchy Chart by Akvelon](https://appsource.microsoft.com/product/power-bi-visuals/WA104381333), **[link do vídeo](https://youtu.be/0ZGzJaq_KT4)**
*  [Histogram Chart](https://appsource.microsoft.com/product/power-bi-visuals/WA104380776)
*  [Histogram with points by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104381032)
* [Gráfico de barras horizontais](https://appsource.microsoft.com/product/power-bi-visuals/WA104381230)
*  [Horizontal Funnel by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380846)
*  [Image by CloudScope](https://appsource.microsoft.com/product/power-bi-visuals/WA104381297)
*  [Image Grid](https://appsource.microsoft.com/product/power-bi-visuals/WA104381355)
*  [Infographic Designer](https://appsource.microsoft.com/product/power-bi-visuals/WA104380898)
*  [KPI Chart by Akvelon](https://appsource.microsoft.com/product/power-bi-visuals/WA104381432)
*  [KPI Column da MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380996)
*  [Grade de KPI da MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380947)
*  [KPI Indicator](https://appsource.microsoft.com/product/power-bi-visuals/WA104380832)
*  [KPI Ticker da MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380946)
* [Linear Gauge by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380821)
*  [LineDot Chart](https://appsource.microsoft.com/product/power-bi-visuals/WA104380766)
*  [Gráfico Mekko](https://appsource.microsoft.com/product/power-bi-visuals/WA104380785), **[link do vídeo](https://youtu.be/90FLCKpgicA)**
*  [Vários KPIs](https://appsource.microsoft.com/product/power-bi-visuals/WA104381763)
*  [Visão geral da CloudScope](https://appsource.microsoft.com/product/power-bi-visuals/WA104381477)
*  [Play Axis (Dynamic Slicer)](https://appsource.microsoft.com/product/power-bi-visuals/WA104380981)
*  [Power KPI](https://appsource.microsoft.com/product/power-bi-visuals/WA104381083), [link do vídeo](https://youtu.be/IvfIP3E6-1Q)
*  [Power KPI Matrix](https://appsource.microsoft.com/product/power-bi-visuals/WA104381299), **[link do vídeo](https://youtu.be/1enze8pcGzY)**
*  [Gráfico de Pulso](https://appsource.microsoft.com/product/power-bi-visuals/WA104381006), **[link do vídeo](https://youtu.be/DQWdcQtjDVw)**
*  [Gráfico de quadrante por MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104381011)
*  [Radar Chart](https://appsource.microsoft.com/product/power-bi-visuals/WA104380771)
*  [Ring Chart by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380824)
*  [Rotating Chart by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104381007)
*  [Gráfico Sankey](https://appsource.microsoft.com/product/power-bi-visuals/WA104380777), **[link do vídeo](https://youtu.be/WWP9wVUHGaA)**
*  [Scatter Chart by Akvelon](https://appsource.microsoft.com/product/power-bi-visuals/WA104381703)
*  [Scroller](https://appsource.microsoft.com/product/power-bi-visuals/WA104381018)
*  [Smart Filter by OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104380859), **[link do vídeo](https://youtu.be/gcJsDDRQq28)**
*  [Sparkline by OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104380910), **[link do vídeo](https://youtu.be/0m3Vnvso9tY)**
*  [Stream Graph](https://appsource.microsoft.com/product/power-bi-visuals/WA104380772)
*  [Sunburst](https://appsource.microsoft.com/product/power-bi-visuals/WA104380767)
*  [Synoptic Panel da OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104380873)
*  [Table Heatmap](https://appsource.microsoft.com/product/power-bi-visuals/WA104380818)
*  [Tacômetro](https://appsource.microsoft.com/product/power-bi-visuals/WA104380937), **[link do vídeo](https://youtu.be/C3OXdETbS9o)**
*  [Filtro de texto](https://appsource.microsoft.com/product/power-bi-visuals/WA104381309)
*  [Text Wrapper by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380826)
*  [Termômetro da MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380847)
*  [Segmentação de pincel de tempo](https://appsource.microsoft.com/product/power-bi-visuals/WA104380798)
*  [Segmentação de Linha do Tempo](https://appsource.microsoft.com/product/power-bi-visuals/WA104380786), **[link do vídeo](https://youtu.be/ozMtZ4_NZ10)**
*  [Timeline by CloudScope](https://appsource.microsoft.com/product/power-bi-visuals/WA104381427), [link do vídeo](https://youtu.be/szNi9YgXFJc)
*  [Gráfico de Tornado](https://appsource.microsoft.com/product/power-bi-visuals/WA104380768), **[link do vídeo](https://www.youtube.com/watch?v=AQvd2FhRyCI)**
*  [Trading Chart by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380823)
* [Cartão de KPI Final](https://appsource.microsoft.com/product/power-bi-visuals/WA104381977)
*  [Variação final](https://appsource.microsoft.com/product/power-bi-visuals/WA104381140), **[link do vídeo](https://youtu.be/pDYF8iZxERs)**
*  [Cascata Final](https://appsource.microsoft.com/product/power-bi-visuals/WA104380956), **[link do vídeo](https://youtu.be/0BZsVCQdEkc)**
*  [User List by CloudScope](https://appsource.microsoft.com/product/power-bi-visuals/WA104381426)
*  [Diagrama Venn da MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104381231)
*  [Gráfico de Violino](https://appsource.microsoft.com/product/power-bi-visuals/WA104381947)
*  [Visual do Visio](https://appsource.microsoft.com/product/power-bi-visuals/WA104381132)
*  [Gráfico de Waffle](https://appsource.microsoft.com/product/power-bi-visuals/WA104381049), **[link do vídeo](https://youtu.be/1vRqYUsm3Vk)**
*  [Nuvem de Palavras](https://appsource.microsoft.com/product/power-bi-visuals/WA104380752), **[link do vídeo](https://youtu.be/AblTenl9fqo)**

## <a name="faq"></a>Perguntas frequentes

Para obter mais informações sobre visuais, acesse [Perguntas frequentes sobre visuais certificados](power-bi-custom-visuals-faq.md#certified-power-bi-visuals).

## <a name="next-steps"></a>Próximas etapas

* [Desenvolvimento de um visual personalizado do Power BI](../developer/custom-visual-develop-tutorial.md)
* [Playlist de visuais personalizados da Microsoft no YouTube](https://www.youtube.com/playlist?list=PL1N57mwBHtN1vIjfvuBIzZllrmKo-Vz6x)  
* [Visualizações no Power BI](../visuals/power-bi-report-visualizations.md)  
* [Visualizações personalizadas no Power BI](power-bi-custom-visuals.md)  
* [Publicar visuais do Power BI no Microsoft AppSource](../developer/office-store.md) 
* Se você for desenvolvedor da Web e tiver interesse em criar seus próprios visuais do Power BI e adicioná-los ao  [Microsoft AppSource](https://appsource.microsoft.com), comece pelo tutorial  [Desenvolver um visual do Power BI](visuals/custom-visual-develop-tutorial.md). 

Mais perguntas? [Experimente a Comunidade do Power BI](https://community.powerbi.com/)
