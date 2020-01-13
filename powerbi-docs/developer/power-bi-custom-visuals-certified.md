---
title: Visuais do Power BI certificados
description: Requisitos e processos para enviar um visual personalizado para certificação. E uma lista de visuais do Power BI certificados.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.topic: conceptual
ms.subservice: powerbi-custom-visuals
ms.date: 12/02/2019
ms.openlocfilehash: c39b96122016746905ea09c0983adf50356f0c77
ms.sourcegitcommit: 6272c4a0f267708ca7d38a45774f3bedd680f2d6
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/06/2020
ms.locfileid: "75221955"
---
# <a name="get-a-power-bi-visual-certified"></a>Certificar um visual do Power BI

Visuais do Power BI certificados são visuais nos *Marketplace* que cumprem determinados requisitos de *código especificado* que a *equipe do Microsoft Power BI* testou e aprovou. Os testes foram criados para verificar se o visual não acessa serviços ou recursos externos.

Os visuais do Power BI certificados e os [visuais do Power BI padrão](power-bi-custom-visuals.md) são usados da mesma forma. Eles podem ser adicionados ao [Power BI Desktop](../desktop-what-is-desktop.md) e ao [serviço do Power BI](../power-bi-service-overview.md) e visualizados com o [Power BI Mobile](../consumer/mobile/mobile-apps-for-mobile-devices.md) e o [Power BI Embedded](embedding.md).

O processo de certificação é opcional. Fica a critério dos desenvolvedores decidir se desejam que seus visuais do Power BI no Marketplace sejam certificados. Depois que um visual do Power BI é certificado, ele oferece mais recursos. Por exemplo, você pode [exportar para o PowerPoint](../consumer/end-user-powerpoint.md) ou exibir o visual em emails recebidos quando um usuário [assina páginas do relatório](../consumer/end-user-subscribe.md).

Visuais do Power BI não certificados não são necessariamente visuais não seguros. Alguns visuais não são certificados, pois não são compatíveis com um ou mais dos [requisitos de certificação](https://docs.microsoft.com/power-bi/power-bi-custom-visuals-certified?#certification-requirements). Por exemplo, conectar-se a um serviço externo, como o mapa de visuais, ou usar bibliotecas comerciais ou visuais.

Se você for desenvolvedor da Web e tiver interesse em criar seus próprios visuais do Power BI e adicioná-los ao  [Microsoft AppSource](https://appsource.microsoft.com), comece pelo tutorial  [Desenvolver um visual do Power BI](visuals/custom-visual-develop-tutorial.md).

> [!NOTE]
> A **Microsoft***não* é a autora de visuais do Power BI de terceiros. Recomendamos aos clientes contatar o autor diretamente para verificar a funcionalidade dos visuais de terceiros.

> [!IMPORTANT]
> A Microsoft pode remover um visual do Power BI da lista de [Visuais do Power BI certificados](#certified-power-bi-visuals) a seu próprio critério.

## <a name="certification-requirements"></a>Requisitos de certificação

Para [certificar](#get-a-power-bi-visual-certified) seu visual do Power BI, verifique se ele está em conformidade com os requisitos listados nesta seção. 

> [!TIP]
> Recomendamos que você use o EsLint com o conjunto de regras de segurança padrão para validar previamente seu código antes do envio.

* Painel do Vendedor ou Partner Center da Microsoft aprovado. Seu visual do Power BI deve estar em nosso [marketplace](https://appsource.microsoft.com/marketplace/apps?page=1&product=power-bi-visuals).
* O visual do Power BI é gravado com a *versão 2.5 ou superior da API*.
* O repositório de código está disponível para revisão por meio da equipe do Power BI. Por exemplo, um formato legível do código-fonte (JavaScript ou TypeScript) está disponível para nós por meio do GitHub.

    >[!NOTE]
    > Você não precisa compartilhar publicamente seu código no Github.

* Requisitos do repositório de códigos:
  * Deve incluir estes arquivos:
    * .gitignore
    * capabilities.json
    * pbiviz.json
    * package.json
    * package-lock.json
    * tsconfig.json
  * Não deve incluir a pasta *node_modules* (adicione *node_modules* ao arquivo .gitingore*).
  * O comando de *npm install* não deve retornar erros.
  * O comando *npm audit* não deve retornar avisos com nível alto ou moderado.
  * O comando *pbiviz package* não deve retornar erros.
  * Deve incluir o [TSlint da Microsoft](https://www.npmjs.com/package/tslint-microsoft-contrib) sem nenhuma configuração substituída. Esse comando não deve retornar erros de lint.
   * O pacote compilado do visual do Power BI deve corresponder ao pacote enviado.
* Requisitos do código-fonte:
   * O visual do Power BI deve ter suporte para a [Renderização da API de Eventos](./visuals/event-service.md).
   * Garantir que nenhum código arbitrário/dinâmico seja executado (bad: eval(), não seguro para uso de setTimeout(), requestAnimationFrame(), setInterval (alguma função com entrada do usuário), executando entradas/dados do usuário).
   * Garantir que o DOM seja manipulado de forma segura (bad: innerHTML, D3.html(<algumas entradas/dados do usuário>), e usar a limpeza para entradas/dados do usuário, antes de adicioná-lo ao DOM.
   * Garantir que não haja erros ou exceções de javascript no console do navegador para os dados de entrada. Os usuários podem usar seu visual do Power BI com um intervalo diferente de dados inesperados, portanto, o visual não deve falhar. Use [este relatório de exemplo](https://github.com/Microsoft/PowerBI-visuals/raw/gh-pages/assets/reports/large_data.pbix) como um conjunto de dados de teste.

* Se as propriedades no arquivo *capabilities.json* forem alteradas, verifique se elas não interrompem os relatórios existentes do usuário.

* Garanta que o visual do Power BI esteja em conformidade com as [diretrizes para visuais do Power BI](./guidelines-powerbi-visuals.md).
    
* Seu código só pode usar componentes públicos OSS analisáveis, como bibliotecas Javascript ou TypeScript públicas. É preciso que o código-fonte fique disponível para revisão e não tenha vulnerabilidades conhecidas. Não podemos verificar um visual personalizado usando um componente comercial.

* O visual do Power BI não deve acessar serviços ou recursos externos. Por exemplo, nenhuma solicitação HTTP/S ou WebSocket pode sair do Power BI para outros serviços. 

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

Mais perguntas? [Experimente a Comunidade do Power BI](https://community.powerbi.com/)
