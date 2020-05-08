---
title: Interagindo com um mapa do ArcGIS que foi compartilhado com você
description: Usar o visual do ArcGIS Map para Power BI na exibição de leitura como um consumidor de relatório
author: mihart
ms.reviewer: willt, lukasz
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 11/18/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 59685b4c3ceab4b60cba92ec1d3924b902c1426a
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/05/2020
ms.locfileid: "77115298"
---
# <a name="interact-with-arcgis-maps-in-power-bi"></a>Interagir com mapas do ArcGIS no Power BI
Este tópico foi escrito do ponto de vista de uma pessoa que está usando um mapa do ArcGIS no serviço do Power BI, no Desktop ou em um dispositivo móvel. Quando um designer compartilha um visual do ArcGIS Map for Power BI com você, há muitas maneiras de interagir com esse visual.  Para saber mais sobre como criar um mapa do ArcGIS, confira [Tutorial de mapas do ArcGIS pela Esri](../visuals/power-bi-visualization-arcgis.md).

A combinação de mapas do ArcGIS e do Power BI leva o mapeamento para além da apresentação de pontos em um mapa, para um nível totalmente novo. Os designers de relatório começam com um mapa e anexam camadas de dados demográficos a esse mapa. A combinação de camadas de dados baseadas em local (como dados de censo) em um mapa com análise espacial transmite uma compreensão mais profunda dos dados nas visualizações.

> [!TIP]
> GIS significa Geographic Information System (Sistema de Informações Geográficas).
> 

O visual do ArcGIS Map for Power BI mostra as vendas do ano passado por cidade e usa um mapa base de ruas e uma camada de referência para a renda familiar média. O mapa contém dois pinos (vermelho e amarelo) e um raio do tempo de viagem (em roxo).

![Mapa ArcGIS mostrando Estados Unidos com bolhas, alfinetes e tempo de condução](media/power-bi-visualizations-arcgis/power-bi-arcgis-esri.png)

> [!TIP]
> Acesse a [página da ESRI no Power BI](https://www.esri.com/powerbi) para ver muitos exemplos e ler depoimentos. E, em seguida, confira a [Página de Introdução do ArcGIS Maps for Power BI](https://doc.arcgis.com/en/maps-for-powerbi/get-started/about-maps-for-power-bi.htm) da Esri.
> 
> 

## <a name="user-consent"></a>Consentimento do usuário

Na primeira vez que um colega compartilhar um mapa do ArcGIS com você, o Power BI exibirá uma solicitação de consentimento. O ArcGIS Maps for Power BI é fornecido pela Esri https://www.esri.com) e o uso do ArcGIS Maps for Power BI está sujeito aos termos e à política de privacidade da Esri. Os usuários do Power BI que desejam usar os visuais dos Mapas do ArcGIS para o Power BI precisarão aceitar a caixa de diálogo de consentimento.


## <a name="understand-the-layers"></a>Compreender as camadas

Um visual do ArcGIS Maps for Power BI pode ter vários tipos diferentes de camadas de informações de localização demográfica.

### <a name="base-maps"></a>Mapas base

Cada visual do ArcGIS Maps for Power BI começa com um mapa base. Considere os mapas base como a tela dos dados. Um mapa base pode ser uma tela básica escura ou clara,

![mapa base cinza escuro](media/power-bi-visualizations-arcgis/power-bi-basemap-dark.png) 

ou uma tela com um detalhe de rua e de transporte. 

![mapa base cinza escuro](media/power-bi-visualizations-arcgis/power-bi-streets-basemap.png)  

O mapa base é aplicado à tela inteiramente – conforme você faz a panorâmica e aplica zoom, o mapa é atualizado. Amplie para ver informações cada vez mais detalhadas sobre rua e transporte. Faça a panorâmica de um continente para outro e o nível de detalhe permanece constante. Aqui, fizemos a panorâmica de Porto a Beijing.

![mapa base de ruas](media/power-bi-visualizations-arcgis/power-bi-basemap-pan.png)  

### <a name="reference-layers"></a>Camadas de referência

Um *designer* de relatório pode adicionar uma camada de referência. As camadas de referência são hospedadas pela Esri e fornecem uma camada adicional de informações demográficas sobre um local. O exemplo a seguir tem uma camada de referência para a densidade populacional. Cores mais escuras representam maior densidade.

![mapa da área de Orlando mostrando a densidade populacional](media/power-bi-visualizations-arcgis/power-bi-reference.png)  

### <a name="infographics"></a>Infográficos

Um *designer* de relatório pode adicionar muitas camadas de infográficos. Infográficos são indicadores visuais rápidos exibidos ao longo do lado direito da tela do visual. Os infográficos são hospedados pela Esri e fornecem uma camada adicional de informações demográficas sobre um local. O exemplo abaixo tem três infográficos aplicados. Eles não são exibidos no mapa em si, mas em cartões. Os cartões infográficos são atualizados à medida que você aplica zoom, faz panorâmica e seleciona áreas no mapa.

![mapa da área do Orlando ampliado e cartões de infográficos ao longo do lado direito da tela](media/power-bi-visualizations-arcgis/power-bi-infographics.png)  

### <a name="pins"></a>Marcadores

Os marcadores representam locais precisos, como uma cidade ou endereço. Às vezes, os *designers* de relatório usam marcadores com o raio de tempo da viagem. Este exemplo mostra lojas a um raio de 50 milhas de Charlotte, Carolina do Norte.


![Tempo de viagem em Charlotte, NC](media/power-bi-visualizations-arcgis/power-bi-drive-times.png) 


## <a name="interact-with-an-arcgis-maps-for-power-bi-visual"></a>Interagir com um visual do ArcGIS Maps for Power BI
Os recursos disponíveis para você dependem de como o relatório foi compartilhado com você e do seu tipo de conta do Power BI. Com seu administrador do sistema, verifique se você tem dúvidas. Os visuais do ArcGIS Maps for Power BI se comportam de forma muito semelhante a outros visuais em um relatório. Você poderá [mostrar os dados usados para criar a visualização](../consumer/end-user-show-data.md), ver o mapa no [Modo de foco e de tela inteira](../consumer/end-user-focus.md), [adicionar comentários](../consumer/end-user-comment.md), [interagir com os filtros](../consumer/end-user-report-filter.md) definidos pelo *designer* de relatório e muito mais. Os visuais do ArcGIS podem fazer filtragem cruzada com outros visuais na página do relatório e vice-versa.

Passe o mouse sobre locais do mapa base (por exemplo, uma bolha) para revelar dicas de ferramenta. Além disso, use as ferramentas de seleção de visual do ArcGIS para exibir dicas de ferramenta adicionais e para fazer seleções específicas no mapa base ou na camada de referência.  

### <a name="selection-tools"></a>Ferramentas de seleção

O ArcGIS Maps for Power BI permite cinco modos de seleção. No máximo, 250 pontos de dados podem ser selecionados por vez.

![Captura de tela de todas as três ferramentas de seleção](media/power-bi-visualizations-arcgis/power-bi-esri-selection-tools.png)

#### <a name="the-single-select-tool"></a>A ferramenta de seleção única

![captura de tela de uma única ferramenta de seleção](media/power-bi-visualizations-arcgis/power-bi-esri-selection-single2.png) 

Selecione um ponto de dados, uma bolha, um marcador ou um ponto de dados individual da camada de referência. O Power BI exibirá uma dica de ferramenta com detalhes sobre sua seleção. A seleção única faz a filtragem cruzada dos outros visuais na página de relatório com base em sua seleção e atualiza os cartões de infográficos para a área selecionada. 

Aqui selecionamos um ponto de dados de bolha marrom de nosso mapa base. Power BI:
- realça nossa seleção,
- exibe uma dica de ferramenta para esse ponto de dados, 
- atualiza os cartões de infográficos para exibir dados apenas para a nossa seleção e
- faz a filtragem cruzada do gráfico de colunas.

![Captura de tela da dica de ferramenta para a bolha marrom](media/power-bi-visualizations-arcgis/power-bi-single-selects.png)

Se o mapa tiver uma camada de referência, selecionar os locais exibirá os detalhes em uma dica de ferramenta. Aqui selecionamos Seneca County e vemos dados da camada de referência (densidade populacional) que o *designer* de relatório adicionou ao mapa. Neste exemplo, nosso ponto de dados inclui duas contagens diferentes; portanto, nossa dica de ferramenta tem duas páginas. Cada página tem um gráfico. Selecione uma barra no gráfico para exibir detalhes adicionais. 

![Captura de tela da dica de ferramenta para Seneca County](media/power-bi-visualizations-arcgis/power-bi-single-select-ref.png)

> [!TIP]
  > Às vezes, você pode reduzir o número de páginas de dica de ferramenta ampliando para selecionar um local específico.  Caso contrário, se houver localizações sobrepostas, o Power BI poderá apresentar mais de uma dica de ferramenta por vez. Selecionar as setas para mover entre as dicas de ferramentas
  > 
  > ![Dica de ferramenta mostrando três páginas](media/power-bi-visualizations-arcgis/power-bi-3-screens.png)

#### <a name="the-multi-select-tool"></a>A ferramenta de seleção múltipla

![ferramenta de seleção múltipla](media/power-bi-visualizations-arcgis/power-bi-esri-selection-marquee2.png) 

Desenha um retângulo no mapa e seleciona os pontos de dados contidos. Use CTRL para selecionar mais de uma área retangular. A seleção múltipla atualiza os cartões de infográficos para a área selecionada e faz realces cruzados de outros visuais na página de relatório com base em sua seleção.

![ferramenta de seleção múltipla](media/power-bi-visualizations-arcgis/power-bi-multi-select.png) 

#### <a name="the-reference-layer-tool"></a>A ferramenta de camada de referência

![ferramenta de seleção de terceiros para limites](media/power-bi-visualizations-arcgis/power-bi-esri-selection-reference-layer2.png) 

Permite que os limites ou polígonos nas camadas de referência sejam usados para selecionar os pontos de dados contidos. É difícil ver, mas há um contorno amarelo na camada de referência. Ao contrário da ferramenta de seleção única, não obtemos uma dica de ferramenta. Em vez disso, obtemos dados sobre pontos de dados contidos dentro das bordas desse contorno. Neste exemplo, nossa seleção contém um ponto de dados – é para uma loja da Lindseys em Winston Salem.

![ferramenta de seleção de referência](media/power-bi-visualizations-arcgis/power-bi-ref-tool.png) 

#### <a name="the-buffer-tool"></a>A ferramenta de buffer

![quarta ferramenta de seleção para buffers](media/power-bi-visualizations-arcgis/power-bi-esri-selection-4.png) 

Permite a seleção de pontos de dados usando uma camada de buffer. Por exemplo, use essa ferramenta para selecionar um raio de tempo de viagem para interagir com o restante do relatório. O raio do tempo de viagem permanece ativo e os cartões de infográficos continuam refletindo o raio do tempo de viagem, mas selecionar outros pontos de dados no mapa faz a filtragem cruzada dos outros visuais na página do relatório.

![ferramenta de seleção de buffer](media/power-bi-visualizations-arcgis/power-bi-buffer.png) 

#### <a name="the-find-similar-tool"></a>A ferramenta Encontrar Semelhante

![quinta ferramenta de seleção para semelhanças](media/power-bi-visualizations-arcgis/power-bi-esri-selection-reference5.png) 

Permite encontrar locais com atributos semelhantes. Você começa selecionando um ou mais pontos de interesse ou locais de referência, definindo até cinco dimensões que você deseja usar na análise. Encontrar Semelhante calcula os 10 locais no seu mapa mais parecidos com os locais de referência que você definiu. Você pode usar os Cartões de infográficos para saber mais sobre a demografia com relação a cada um dos seus resultados, criar áreas de tempo de viagem para ter uma noção do que está a uma distância de carro de cada um desses locais ou até mesmo usar a ferramenta Encontrar Semelhante para filtrar seu relatório e obter mais insights. O mais importante é que todo o cálculo é feito localmente em seu computador; portanto, tenha certeza de que seus dados confidenciais permanecem protegidos.


## <a name="considerations-and-limitations"></a>Considerações e limitações
Os Mapas do ArcGIS para o Power BI estão disponíveis nos seguintes serviços e aplicativos:

|Serviço/Aplicativo  |Disponibilidade  |
|---------|---------|
|Power BI Desktop     |     Sim    |
|Serviço do Power BI (app.powerbi.com)     |    Sim     |
|Aplicativos móveis do Power BI     |  Sim      |
|Publicar na Web do Power BI     |  Não       |
|Power BI Embedded     |     Não    |
|Incorporação do serviço do Power BI (PowerBI.com)  | Não |


## <a name="how-do-arcgis-maps-for-power-bi-work-together"></a>Como os ArcGIS Maps for Power BI funcionam juntos?
O ArcGIS Maps for Power BI é fornecido pela Esri (https://www.esri.com). O uso do ArcGIS Maps for Power BI está sujeito aos [termos](https://go.microsoft.com/fwlink/?LinkID=8263222) e à [política de privacidade](https://go.microsoft.com/fwlink/?LinkID=826323) da Esri. Os usuários do Power BI que queiram usar os visuais do ArcGIS Maps for Power BI precisam aceitar a caixa de diálogo de consentimento (consulte Consentimento do usuário para obter detalhes).  Usar o ArcGIS Maps for Power BI da Esri está sujeito aos Termos e à Política de Privacidade da Esri que também estão vinculados à caixa de diálogo de consentimento. Cada usuário deve consentir antes de usar o ArcGIS Maps for Power BI pela primeira vez. Depois que o usuário aceitar o consentimento, os dados vinculados ao visual são enviados aos serviços da Esri pelo menos para geocodificação, que significa transformar informações de localização em informações de latitude e longitude que podem ser representadas em um mapa. Você deve considerar que os dados associados à visualização de dados podem ser enviados aos serviços da Esri. A Esri fornece serviços como mapas de base, análise espacial, geocodificação, etc. O visual do ArcGIS Maps for Power BI interage com esses serviços usando uma conexão SSL protegida por um certificado fornecido e mantido pela Esri. Informações adicionais sobre o ArcGIS Maps for Power BI podem ser obtidas da [página do produto ArcGIS Maps for Power BI](https://www.esri.com/powerbi).

### <a name="power-bi-plus"></a>Power BI Plus

![Selecionar o ícone Plus para se inscrever ou entrar](media/power-bi-visualizations-arcgis/power-bi-plus.png)

Quando um usuário se inscreve para uma assinatura Plus oferecida pela Esri por meio do ArcGIS Maps for Power BI, ele está entrando em uma relação direta com a Esri. O Power BI não envia informações pessoais sobre o usuário à Esri. O usuário entra e confia em um aplicativo AAD fornecido pela Esri usando sua própria identidade do AAD. Ao fazer isso, o usuário compartilhará suas informações pessoais diretamente com a Esri. Depois que o usuário adicionar o conteúdo Plus a um visual do ArcGIS Maps for Power BI, os colegas que desejarem exibir ou editar o visual também precisarão de uma assinatura Plus da Esri. 

Para obter perguntas técnicas detalhadas sobre como o ArcGIS Maps for Power BI da Esri funciona, contate a Esri por meio do site de suporte.

## <a name="considerations-and-troubleshooting"></a>Considerações e solução de problemas

**O mapa do ArcGIS não está sendo exibido**    
Em serviços ou aplicativos em que os Mapas do ArcGIS para o Power BI não estiverem disponíveis, a visualização será mostrada como um visual vazio com o logotipo do Power BI.

**Não consigo ver todas as minhas informações no mapa**    
Ao geocodificar a latitude/longitude no mapa, são exibidos até 30.000 pontos de dados. Ao geocodificar os pontos de dados, como CEPs ou endereços de ruas, apenas os primeiros 15 mil pontos de dados são geocodificados. Codificações geográficas de nomes de locais ou países não estarão sujeitas ao limite de 1500 endereços.

**O uso do ArcGIS Maps para Power BI é cobrado?**

O Mapa do ArcGIS para o Power BI está disponível para todos os usuários do Power BI sem custo adicional. Ele é um componente fornecido pela **Esri** e seu uso está sujeito aos termos e à política de privacidade fornecidos pela **Esri**, conforme mencionado anteriormente neste artigo. Se você se inscrever no ArcGIS **Plus**, haverá uma cobrança.

**Estou recebendo uma mensagem de erro que informa que meu cache está cheio**

Esse comportamento é um bug que está sendo resolvido.  Enquanto isso, selecione o link exibido na mensagem de erro para obter instruções sobre como limpar o cache do Power BI.

**Posso exibir meus mapas do ArcGIS offline?**

Não, o Power BI precisa de conectividade de rede para exibir os mapas.

## <a name="next-steps"></a>Próximas etapas
Obter ajuda: A **Esri** oferece uma [documentação abrangente](https://go.microsoft.com/fwlink/?LinkID=828772) sobre o conjunto de recursos do **ArcGIS Maps para Power BI**.

Você pode fazer perguntas, encontrar as informações mais recentes, reportar problemas e encontrar respostas no [thread da comunidade do Power BI relacionado ao **ArcGIS Maps para o Power BI**](https://go.microsoft.com/fwlink/?LinkID=828771).


[Página do produto ArcGIS Maps para Power BI](https://www.esri.com/powerbi)
