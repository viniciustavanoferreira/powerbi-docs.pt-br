---
title: Exportar relatórios completos para o PowerPoint
description: Saiba como exportar um relatório do Power BI para o PowerPoint.
author: mihart
ms.reviewer: ''
ms.custom: contperfq4
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 05/12/2020
ms.author: mihart
LocalizationGroup: Share your work
ms.openlocfilehash: 1dbb35ab45a1172044cedb7fbe484ed4da6c43db
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83348357"
---
# <a name="export-reports-to-powerpoint"></a>Exportar relatórios para o PowerPoint

[!INCLUDE[consumer-appliesto-yyny](../includes/consumer-appliesto-yyny.md)]


Com o serviço do Power BI (app.powerbi.com), é possível publicar seu relatório no Microsoft PowerPoint e criar facilmente um conjunto de slides com base em seu relatório do Power BI. Quando você exporta para o PowerPoint, ocorre o seguinte:

* Cada página no relatório do Power BI se torna um slide individual no PowerPoint.
* Cada página no relatório do Power BI é exportada como uma única imagem de alta resolução no PowerPoint.
* Você pode preservar as configurações de filtros e segmentações que adicionou ao relatório.
* É criado um link no PowerPoint que é vinculado ao relatório do Power BI.

Obter o **relatório do Power BI** exportado no **PowerPoint** é rápido. Siga as etapas descritas na próxima seção.

Você também pode copiar um visual por vez do serviço do Power BI e colá-lo no PowerPoint (ou em qualquer outro programa que ofereça suporte à colagem). Selecione o ícone **Copiar como imagem** para copiar o visual para a área de transferência. Em seguida, abra o PowerPoint e cole o visual. Para obter mais informações, confira [Copiar visuais como imagens estáticas](../power-bi-visualization-copy-paste.md).

![Selecione o ícone Copiar como imagem](media/end-user-powerpoint/power-bi-copy.png)

## <a name="export-your-power-bi-report-to-powerpoint"></a>Exportar um relatório do Power BI para o PowerPoint
No **serviço do Power BI**, selecione um relatório para exibi-lo na tela. Você pode também selecionar um relatório na **Página Inicial**, em **Aplicativos** ou em qualquer outro contêiner, no painel de navegação.

[!INCLUDE [power-bi-service-new-look-include](../includes/power-bi-service-new-look-include.md)]

Quando o relatório que você deseja exportar para o PowerPoint for exibido na tela, selecione **Exportar** > **PowerPoint** na barra de menus.

![Selecione Exportar na barra de menus](media/end-user-powerpoint/power-bi-export.png)

Na janela pop-up exibida, você tem a opção de selecionar **Valores Atuais** ou **Valores Padrão**. A opção **Valores Atuais** exporta o relatório no estado atual, que inclui as alterações ativas feitas nos valores de segmentação e de filtro.  A maioria dos usuários seleciona essa opção. Se você tiver rolado a tela, **Valores atuais** não incluirá o estado de rolagem do visual, mas, em vez disso, exportará a parte superior dos dados. Como alternativa, a seleção de **Valores Padrão** exporta o relatório no estado original, como o *designer* o compartilhou, e não reflete as alterações feitas no estado original.

![Selecione o que exportar](media/end-user-powerpoint/power-bi-current-values.png)
 
Além disso, há uma caixa de seleção para marcar se você deseja ou não exportar as guias ocultas de um relatório. Marque essa caixa se quiser exportar somente as guias de relatório visíveis para você no navegador. Se preferir obter todas as guias ocultas como parte da exportação, deixe a caixa de seleção desmarcada. Se a caixa de seleção estiver esmaecida, não haverá guias ocultas no relatório. Um exemplo de guia oculta seria uma guia de dica de ferramenta. [Dicas de ferramenta personalizadas](../create-reports/desktop-tooltips.md) são criadas pelos *designers* de relatórios e não são exibidas como guias do relatório para o serviço do Power BI para *consumidores*. 

Depois de fazer as seleções, selecione **Exportar** para continuar. Você verá uma faixa de notificação no canto superior direito da janela do navegador de serviço do Power BI de que o relatório está sendo exportado para o PowerPoint. 



![Notificação de exportação para o PowerPoint em andamento](media/end-user-powerpoint/power-bi-export-progress.png)

A exportação pode levar alguns minutos. Os fatores que podem afetar o tempo necessário incluem a estrutura do relatório e a carga atual no serviço do Power BI. Você pode continuar trabalhando no Power BI enquanto o relatório está sendo exportado.

Após o serviço do Power BI concluir o processo de exportação, o banner de notificação mudará para informá-lo. O arquivo estará disponível quando o navegador exibir os arquivos baixados. Na imagem a seguir, ele é mostrado como uma faixa de download na parte inferior da janela do navegador.

![notificação do navegador na parte inferior da tela](media/end-user-powerpoint/power-bi-browsers.png)

E isso é tudo para ele. Você pode baixá-lo, abri-lo com o PowerPoint e, em seguida, modificá-lo ou aprimorá-lo, como faria com qualquer outro material do PowerPoint.

## <a name="open-the-powerpoint-file"></a>Abrir o arquivo do PowerPoint
Quando você abre o arquivo do PowerPoint que o Power BI exportou, encontra alguns elementos interessantes e úteis. Dê uma olhada na imagem a seguir e veja os elementos numerados que descrevem alguns desses recursos interessantes. As páginas no PowerPoint sempre são criadas com o tamanho padrão 9:16, independentemente do tamanho ou das dimensões da página original no relatório do Power BI.

![O PowerPoint abre](media/end-user-powerpoint/power-bi-powerpoint-numbered.png)

1. A primeira página do conjunto de slides inclui o nome do relatório e um link para que você possa **Exibir no Power BI** o relatório no qual o conjunto de slides se baseia.
2. Você também obtém algumas informações úteis sobre o relatório. **Última atualização de dados** mostra a data e a hora em que o relatório exportado se baseia. **Baixado em** mostra a data e a hora em que o relatório de Power BI foi exportado para um arquivo do PowerPoint. A hora de **Baixado às** é definida para o fuso horário do seu computador no momento da exportação.


3. Cada página do relatório é um slide separado, conforme mostrado no painel de navegação. 
4. O relatório publicado é renderizado no idioma de acordo com as configurações do Power BI ou pela configuração de localidade do seu navegador. Para obter ou definir sua preferência de idioma, selecione o ícone de engrenagem ![Ícone de engrenagem](media/end-user-powerpoint/power-bi-settings-icon.png) > **Configurações** > **Geral** > **Idioma**. Para obter informações sobre localidade, confira [Idiomas com suporte e países ou regiões do Power BI](../fundamentals/supported-languages-countries-regions.md).


Quando você exibir um slide individual, verá que cada página de relatório é uma imagem independente. A rolagem não está disponível no PowerPoint, pois cada slide é uma imagem estática.

![Tela mostrando cada visual como uma imagem separada](media/end-user-powerpoint/power-bi-images.png)

O que fazer com seu material do PowerPoint daí em diante, ou com qualquer uma das imagens em alta resolução, cabe a você.

## <a name="considerations-and-troubleshooting"></a>Considerações e solução de problemas
Há algumas considerações e limitações para ter em mente ao trabalhar com o recurso **Exportar para o PowerPoint**.
 

* No momento, os [filtros de URL](../service-url-filters.md) não são respeitados quando você escolhe **Valores atuais** para a exportação.

* Ao exportar para o PowerPoint, se o relatório usar uma fonte personalizada, essa fonte será substituída por uma fonte padrão.

* Os seguintes tipos de visuais não têm suporte e não serão exportados para o PowerPoint:
   - Não há suporte para [visuais personalizados que não foram certificados](../developer/power-bi-custom-visuals-certified.md). 
   - O [visual ESRI ArcGIS](../visuals/power-bi-visualizations-arcgis.md) não é compatível
   - Não há suporte para visuais R e Python.
   - As imagens de segundo plano são cortadas com a área delimitadora do gráfico. Recomendamos que você remova as imagens de segundo plano antes de exportar para o PowerPoint.

* Alguns relatórios não podem ser exportados. Elas incluem:
    - Relatórios que são propriedade de um usuário fora de seu domínio de locatário do Power BI, como um relatório de alguém de fora de sua organização e compartilhado com você.
    - Se você compartilhar um dashboard com alguém fora de sua organização, ou seja, um usuário que não está em seu locatário do Power BI, esse usuário não poderá exportar os relatórios associados ao dashboard compartilhado para o PowerPoint. Por exemplo, se você for aaron@contoso.com, poderá compartilhar com david@cohowinery.com. No entanto, david@cohowinery.com não poderá exportar os relatórios associados para o PowerPoint.
    - Relatórios com mais de 30 páginas. Apenas as primeiras 30 páginas serão exportadas.
    - Relatórios sendo exportados para versões mais antigas do PowerPoint.

* Se o item de menu **Exportar para o PowerPoint** não estiver disponível no serviço do Power BI, provavelmente será porque seu administrador de locatários desabilitou o recurso. Entre em contato com seu administrador de locatários para obter detalhes.
* O serviço Power BI usa a configuração de idioma do Power BI como o idioma para a exportação do PowerPoint. Para obter ou definir sua preferência de idioma, selecione o ícone de engrenagem ![Ícone de engrenagem](media/end-user-powerpoint/power-bi-settings-icon.png) > **Configurações** > **Geral** > **Idioma**.



## <a name="next-steps"></a>Próximas etapas
[Copiar visuais como imagens estáticas](../power-bi-visualization-copy-paste.md)    
[Imprimir um relatório](end-user-print.md)
