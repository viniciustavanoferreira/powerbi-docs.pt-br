---
title: Exemplo de acompanhamento da COVID-19 para governos locais e estaduais dos EUA
description: Baixe e modifique o relatório de exemplo com dados locais e estaduais dos EUA sobre a pandemia de COVID-19.
author: LukaszPawlowski-MS
ms.reviewer: maggies
ms.custom: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/28/2020
ms.author: lukaszp
LocalizationGroup: Samples
ms.openlocfilehash: 8cdc4a9a78c20c7c4e6986b63a3af61a319df1b6
ms.sourcegitcommit: 20f15ee7a11162127e506b86d21e2fff821a4aee
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/29/2020
ms.locfileid: "82584933"
---
# <a name="covid-19-tracking-sample-for-us-state-and-local-governments"></a>Exemplo de acompanhamento da COVID-19 para governos locais e estaduais dos EUA

A equipe do Power BI criou um exemplo de acompanhamento da COVID-19 que permite aos governos locais e estaduais dos EUA publicar ou personalizar um relatório interativo sobre a COVID-19. Com o uso do Power BI Desktop, eles podem analisar e visualizar dados sobre a COVID-19 para manter as comunidades informadas a nível municipal, regional, estadual e nacional. E com a função Publicar na Web do Power BI, eles podem compartilhar o relatório publicamente para informar os cidadãos. O artigo oferece diferentes opções para usar as visualizações interativas do Power BI em uma história, um blog ou um site público próprio.

:::image type="content" source="media/sample-covid-19-us/covid-19-us-tracking-sample.png" alt-text="Exemplo sobre a COVID-19 com dados dos EUA":::

Este artigo aborda como:

- Copiar o código de inserção e colocá-lo em seu próprio site. 
- Fazer personalizações, como a formatação de um estado específico.
- Publicar no serviço do Power BI.
- Publicar na web. 
- Combinar esses dados com os de outra fonte. 

## <a name="prerequisites"></a>Pré-requisitos

Antes de começar a usar o Power BI para contar sua história, estes pré-requisitos deverão ser cumpridos:

- Baixar o aplicativo gratuito do [Power BI Desktop](https://powerbi.microsoft.com/desktop/).
- Inscreva-se no [serviço do Power BI](https://powerbi.microsoft.com/get-started/).

## <a name="option-1-pre-built-embed-code"></a>Opção 1: Código de inserção criado previamente

A Microsoft publicou o relatório de exemplo e criou um código de inserção de publicação na Web. O código de inserção pode ser usado para inserir o exemplo completo, incluindo a exibição nacional, e para fazer uma busca detalhada a nível estadual e municipal em seu próprio site. Antes de publicar esses dados, recomendamos revisar os [avisos de isenção de responsabilidade](#disclaimers) neste artigo.

Para incluir o gráfico interativo em seu site, copie e cole o código de inserção a seguir onde deseja que o gráfico apareça na página da Web.  

```
<iframe width="1600" height="900" src="https://app.powerbi.com/view?r=eyJrIjoiMmI2ZjExMzItZTcwNy00YmUwLWFlMTAtYTUxYzVjODZmYjA5IiwidCI6ImMxMzZlZWMwLWZlOTItNDVlMC1iZWFlLTQ2OTg0OTczZTIzMiIsImMiOjF9" frameborder="0" allowFullScreen="true"></iframe>
```

O código de inserção é um elemento iFrame HTML que pode ser inserido em qualquer página HTML. Ajuste a largura e a altura do iFrame fornecido para caber no seu site. O relatório de exemplo é criado nas proporções de 16:9, portanto escolha um tamanho que preserve essa dimensão. Quando implementado corretamente, o gráfico é exibido sem nenhuma borda cinza extra. É útil [examinar as dicas e macetes de dimensionamento do iFrame](../service-publish-to-web.md#tips-for-iframe-height-and-width) ao fazer essas alterações.

## <a name="option-2-customize-the-sample-power-bi-file"></a>Opção 2: Personalização do arquivo de exemplo do Power BI

O arquivo do Power BI contém os dados e o gráfico interativo em um formato de arquivo .pbix que pode ser editado no Power BI Desktop.  

Uma personalização típica é filtrar o relatório para um estado específico e depois criar seu próprio código de inserção de publicação na Web para o relatório personalizado.

Os dados do USAFacts são fornecidos sob uma licença Creative Commons que exige atribuição. Antes de publicar esses dados, examine os [avisos de isenção de responsabilidade](#disclaimers).

Para começar, [baixe o arquivo .pbix (aqui)](https://go.microsoft.com/fwlink/?linkid=2125058).

### <a name="update-your-report"></a>Atualizar o relatório 

1. Baixe a versão mais recente do aplicativo gratuito, [Power BI Desktop](https://powerbi.microsoft.com/desktop/), caso ainda não tenha feito isso. 

2. Baixe o [arquivo .pbix](https://go.microsoft.com/fwlink/?linkid=2125058), caso ainda não tenha feito isso, e abra-o no Power BI Desktop.

3. Para filtrar o relatório para um estado específico, selecione a seta para expandir o painel Filtros.

    :::image type="content" source="media/sample-covid-19-us/power-bi-covid-19-filters-pane.png" alt-text="Expandir o painel Filtros":::

4. Selecione um estado de seu interesse. 

    :::image type="content" source="media/sample-covid-19-us/power-bi-covid-19-filter-selection.png" alt-text="Selecionar um estado":::

5. Para salvar o arquivo, selecione **Arquivo** > **Salvar**. 

### <a name="refresh-your-report"></a>Atualizar o relatório 

1. Selecione o botão **Atualizar**.

    :::image type="content" source="media/sample-covid-19-us/power-bi-desktop-refresh-button.png" alt-text="Botão Atualizar":::

2. Selecione **Anônimo** > **Conectar**. 

    :::image type="content" source="media/sample-covid-19-us/power-bi-covid-19-azure-blob.png" alt-text="Selecionar Anônimo":::

 
3. Selecione **Ignorar Níveis de Privacidade**, se mostrado > **Salvar**. 

    :::image type="content" source="media/sample-covid-19-us/power-bi-covid-19-privacy-levels.png" alt-text="Selecionar os níveis de privacidade":::

### <a name="publish-your-report-to-the-power-bi-service"></a>Publicar o relatório no serviço do Power BI

Depois de personalizar o relatório conforme sua preferência, [siga as etapas descritas aqui para publicá-lo](../desktop-upload-desktop-files.md) no serviço do Power BI.

### <a name="configure-scheduled-refresh"></a>Configurar a atualização agendada

Para manter os dados no relatório atualizados, você pode [configurar uma atualização agendada](../refresh-scheduled-refresh.md) depois de publicar o relatório.

Ao seguir as etapas, escolha as seguintes opções:

1. Método de autenticação de credenciais da fonte de dados: Anônimo
2. Configuração de nível de privacidade desta fonte de dados: Público

Para testar a configuração de atualização, selecione a opção [Atualizar agora](../refresh-data.md#data-refresh), disponível no item do conjunto de dados.

Os dados atualizados são carregados toda vez que o agendamento é executado. Os dados subjacentes são fornecidos pelo USAFacts e podem não ser atualizados com a mesma frequência do agendamento de atualização. Verifique o [site do USAFacts](https://usafacts.org/visualizations/coronavirus-covid-19-spread-map/) para saber quando os dados subjacentes foram atualizados pela última vez. 

Se pretende publicar o relatório personalizado em seu site, é melhor configurar a atualização do agendamento para execução pelo menos com a mesma frequência das atualizações de dados do USAFacts. Como o USAFacts pode atualizar os dados em horários diferentes do dia, convém configurar várias atualizações por dia. 

### <a name="create-a-publish-to-web-embed-code"></a>Criar um código de inserção de publicação na Web 

Para inserir seu relatório personalizado em seu próprio site, siga as instruções de como [criar seu próprio código de inserção de publicação na Web](../service-publish-to-web.md#create-embed-codes-with-publish-to-web).

Depois de publicar o código de inserção, use o iFrame na caixa de diálogo de confirmação para inserir em seu site.

Se forem feitas alterações no relatório no Power BI Desktop, será possível publicar e substituir o relatório existente no serviço do Power BI. O código de inserção não é alterado. Leva aproximadamente uma hora para que as alterações no relatório ou os dados atualizados sejam exibidas no seu site. 

## <a name="option-3-mash-up-data-from-another-source"></a>Opção 3: Combinação de dados de outra fonte 

Também é possível mesclar os dados neste relatório com os de outra fonte. O exemplo a seguir é baseado nos dados da [Johns Hopkins University](https://github.com/CSSEGISandData/COVID-19). Antes de publicar esses dados, recomendamos revisar os [avisos de isenção de responsabilidade](#disclaimers) neste artigo.

1. Selecione **Obter Dados** > **Web**.

    :::image type="content" source="media/sample-covid-19-us/power-bi-desktop-get-data.png" alt-text="Botão Obter Dados":::

2. Insira a seguinte URL:

    ```
    https://raw.githubusercontent.com/CSSEGISandData/COVID-19/master/csse_covid_19_data/csse_covid_19_time_series/time_series_covid19_confirmed_global.csv
    ```

    :::image type="content" source="media/sample-covid-19-us/power-bi-covid-19-from-web.png" alt-text="Selecionar da Web":::

3. Selecione **OK**. 

    > [!NOTE]
    > O link publicado pela Johns Hopkins University pode mudar. Confira a [página do GitHub da Johns Hopkins](https://github.com/CSSEGISandData/COVID-19) para obter as informações mais recentes.

4. Selecione **Carregar** para carregar o conjunto de dados do total de casos confirmados em todo o mundo.  

    :::image type="content" source="media/sample-covid-19-us/power-bi-covid-19-load-data.png" alt-text="Carregar dados da Web":::

    Este artigo, [Conectar-se a páginas da Web do Power BI Desktop](../desktop-connect-to-web.md), fornece mais informações sobre como carregar dados da Web.
    
O Power BI Desktop pode ser usado em seguida para a visualização dos dados. Por fim, use as etapas da **Opção 2:** [Publicação do relatório no serviço do Power BI](#publish-your-report-to-the-power-bi-service) para publicar o relatório e criar um código de inserção personalizado. 

## <a name="option-4-use-the-covid-19-us-tracking-template-app"></a>Opção 4: usar o aplicativo de modelo Acompanhamento da COVID-19 nos EUA

Para disponibilizar mais uma opção, a equipe do Power BI criou o *aplicativo de modelo* Acompanhamento da COVID-19 nos EUA para que você comece a usá-lo imediatamente. Os aplicativos de modelos são pacotes de relatórios, dashboards e conjuntos de dados para uma fonte de dados específica. Você pode baixá-los no AppSource, usá-los ou modificá-los de acordo com as suas necessidades e distribuí-los para os seus colegas. 

Este aplicativo de modelo Acompanhamento da COVID-19 nos EUA contém um relatório predefinido de métricas da COVID-19 que você pode usar no estado em que se encontra, personalizá-lo diretamente no serviço do Power BI ou baixá-lo para adicionar outras fontes de dados, se desejado. Saiba mais sobre como instalar o [aplicativo de modelo Acompanhamento da COVID-19 nos EUA](../connect-data/service-connect-to-covid-19-tracking.md) e começar a usá-lo imediatamente.

## <a name="about-the-data-source-for-this-report"></a>Sobre a fonte de dados deste relatório
Este relatório interativo agrega dados do Centro de Controle e Prevenção de Doenças (CDC) e de agências de saúde pública de nível local e estadual. Os dados de nível do condado são confirmados pela consulta direta às agências locais e estaduais (link).

Os dados são fornecidos pelo USAFacts. Devido à frequência das atualizações de dados, eles podem não refletir os números exatos divulgados pelas organizações governamentais ou pelos veículos jornalísticos. Para saber mais ou para baixar os dados no [site USAFacts](https://usafacts.org/visualizations/coronavirus-covid-19-spread-map/). 

## <a name="disclaimers"></a>Avisos de Isenção de Responsabilidade

Este relatório e os dados foram fornecidos "no estado em que se encontram", "com todas as falhas" e sem garantia de nenhum tipo. A Microsoft não fornece garantias expressas e isenta-se explicitamente de todas as garantias implícitas, inclusive de comercialização, adequação a um fim específico e de não violação.

Os dados do USAFacts estão disponíveis sob licença do Creative Commons. Para usá-los, cite o USAFacts como provedor de dados e deixe um link de referência para o USAFacts. Confira as etapas exatas de atribuição na seção **#MadewithUSAFacts** da página do USAFacts, [Coronavirus nos Estados Unidos: mapeamento da epidemia de COVID-19 nos estados e condados](https://usafacts.org/visualizations/coronavirus-covid-19-spread-map/).

Os dados da Johns Hopkins University estão protegidos sob direitos autorais 2020 Johns Hopkins University, todos os direitos reservados. Eles são fornecidos ao público exclusivamente para fins educacionais e de pesquisa acadêmica. Aqui estão os [Termos de Uso](https://github.com/CSSEGISandData/COVID-19/blob/master/README.md) completos dos dados mostrados no exemplo de mesclagem. Mais informações estão disponíveis no [site da Johns Hopkins University](https://coronavirus.jhu.edu/map-faq.html).

## <a name="next-steps"></a>Próximas etapas

[Obter exemplos para o Power BI](../sample-datasets.md)