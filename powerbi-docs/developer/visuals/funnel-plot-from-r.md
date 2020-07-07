---
title: Criar um gráfico de funil do script do R ao visual do R
description: Este artigo descreve como criar um gráfico de funil de script R para o visual do Power BI do R.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: tutorial
ms.date: 04/02/2020
ms.openlocfilehash: cbc8f6366e23aa7fbfb447bbfe56909c09f3e3fd
ms.sourcegitcommit: caf60154a092f88617eb177bc34fb784f2365962
ms.contentlocale: pt-BR
ms.lasthandoff: 06/25/2020
ms.locfileid: "85354468"
---
# <a name="tutorial-build-a-funnel-plot-from-r-script-to-r-visual"></a>Tutorial: Criar um gráfico de funil do script do R ao visual do R
Este artigo descreve como criar um gráfico de funil usando o passo a passo do script R no visual do R.

Neste artigo, você aprenderá a criar:

> [!div class="checklist"]
>
> * um script R para RStudio
> * um visual do R no Power BI
> * um Visual da plataforma R *com base em PNG* no Power BI
> * um Visual da plataforma R *com base em HTML* no Power BI

O gráfico de funil fornece um modo fácil de consumir, interpretar e mostrar a quantidade de variação esperada. O **funil** é formado usando limites de confiança e exceções são mostradas como pontos fora do funil.

Neste exemplo, o gráfico de funil é usado para comparar e analisar vários dados de conjuntos.  

> [!NOTE]
> Os arquivos de origem estão disponíveis para download em cada conjunto de etapas.

## <a name="build-an-r-script-with-dataset"></a>Criar um script R com o conjunto de dados

1. Baixe um [script R mínimo](https://github.com/microsoft/PowerBI-visuals/raw/master/RVisualTutorial/TutorialFunnelPlot/chapter1_R/script_R_v1_00.r) e a tabela de dados dele, [dataset.csv](https://github.com/microsoft/PowerBI-visuals/raw/master/RVisualTutorial/TutorialFunnelPlot/chapter1_R/dataset.csv).

1. Em seguida, edite o script para espelhar [este script](https://github.com/microsoft/PowerBI-visuals/raw/master/RVisualTutorial/TutorialFunnelPlot/chapter1_R/script_R_v1_01.r). Isso adiciona tratamento de erro de entrada e parâmetros de usuário para controlar a aparência do gráfico.

## <a name="build-a-report"></a>Criar um relatório

Em seguida, edite o script para espelhar [este script](https://github.com/microsoft/PowerBI-visuals/raw/master/RVisualTutorial/TutorialFunnelPlot/chapter2_Rvisual/script_RV_v2_00.r). Isso carrega *dataset.csv* em vez de *read.csv* no workspace do Power BI Desktop e cria uma tabela **Mortalidade por Câncer**. Consulte os resultados no [arquivo PBIX](https://github.com/microsoft/PowerBI-visuals/raw/master/RVisualTutorial/TutorialFunnelPlot/chapter2_Rvisual/funnelPlot_Rvisual.pbix) a seguir.

> [!NOTE]
> O `dataset` é um nome embutido em código para o `data.frame` de entrada de qualquer visual do R. 

## <a name="create-an-r-powered-visual-and-package-in-r-code"></a>Criar um visual da plataforma R e um pacote no código R

1. Antes de começar, não se esqueça de [instalar as ferramentas do PBIVIZ](./custom-visual-develop-tutorial.md#installing-packages).

1. Execute o comando a seguir para criar um visual da plataforma R:

   ```bash
   pbiviz new funnel-visual -t rvisual
   cd funnel-visual
   npm install 
   pbiviz package
   ```

   Esse comando cria a pasta *funnel-visual* com o visual de modelo inicial (`-t` para o **modelo**). O PBIVIZ pode ser encontrado na pasta *dist* e o código R dentro do arquivo *script.r*. Tente importá-lo para o Power BI e veja o que acontece.

1. Edite o arquivo *script.r* e substitua o conteúdo pelo script anterior.

1. Edite *capabilities.json* e substitua a cadeia de caracteres `Values` por `dataset`. Isso substitui o nome de "Role" no modelo para que ele fique igual ao código R.

   ![antes e depois](./samples/funnel-plot/chapter-3/funnel-r-visual-v01/capabilities-changes.PNG)

1. *(opcional)* Edite *dependencies.json* e adicione uma seção para cada pacote do R exigido pelo script R. Isso informa o Power BI que ele deve importar automaticamente esses pacotes quando o visual for carregado pela primeira vez.

   ![antes e depois](./samples/funnel-plot/chapter-3/funnel-r-visual-v01/dependencies-changes.PNG)

1. Recrie o pacote do visual usando o comando `pbiviz package` e tente importá-lo para o Power BI.

> [!NOTE]
> Consulte o [PBIX](https://github.com/microsoft/PowerBI-visuals/raw/master/RVisualTutorial/TutorialFunnelPlot/chapter3-RCustomVisual/funnelPlot_RCustomVisual.pbix) e o [código-fonte](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter3_RCustomVisual/funnelRvisual_v01/) para download.

## <a name="make-r-based-visual-improvements"></a>Faça melhorias visuais baseadas em R

O visual ainda não é amigável porque o usuário precisa saber a ordem das colunas na tabela de entrada.

1. Divida o campo de entrada `dataset` em três campos (funções): `Population`, `Number` e `Tooltips`

   ![CV01to02](./media/funnel-plot/diagram-one.PNG)

1. Edite *capabilities.json* e substitua a função `dataset` pelas três novas funções ou baixe [capabilities.json](https://github.com/microsoft/PowerBI-visuals/raw/master/RVisualTutorial/TutorialFunnelPlot/chapter3_RCustomVisual/funnelRvisual_v02/capabilities.json).

   Você precisará atualizar as seções: `dataRoles` e `dataViewMappings`, que definem os nomes, os tipos, as dicas de ferramentas e as colunas máximas para cada campo de entrada.

   ![antes e depois](./samples/funnel-plot/chapter-3/funnel-r-visual-v02/capabilities-before-vs-after.png)
   
   Para obter mais informações, consulte [funcionalidades](./capabilities.md).

1. Edite *script.r* para dar suporte a `Population`, `Number` e `Tooltips` como dataframes de entrada em vez de `dataset` ou baixe [script.r](https://github.com/microsoft/PowerBI-visuals/raw/master/RVisualTutorial/TutorialFunnelPlot/chapter3_RCustomVisual/funnelRvisual_v02/script.r).

   ![Script](./samples/funnel-plot/chapter-3/funnel-r-visual-v02/script-r-before-vs-after.png)

   > [!TIP]
   > Para seguir as alterações no script R, pesquise os blocos de comentário: 
   > 
   > ```r
   > #RVIZ_IN_PBI_GUIDE:BEGIN: Added to enable visual fields
   > ...
   > #RVIZ_IN_PBI_GUIDE:END: Added to enable visual fields
   > 
   > #RVIZ_IN_PBI_GUIDE:BEGIN: Removed to enable visual fields 
   > ...
   > #RVIZ_IN_PBI_GUIDE:BEGIN: Removed to enable visual fields
   > ```

1. Recrie o pacote do visual usando o comando `pbiviz package` e tente importá-lo para o Power BI.

> [!NOTE]
> Consulte o [PBIX](https://github.com/microsoft/PowerBI-visuals/raw/master/RVisualTutorial/TutorialFunnelPlot/chapter3_RCustomVisual/funnelPlot_RCustomVisual.pbix) e o [código-fonte](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter3_RCustomVisual/funnelRvisual_v02) para download.

## <a name="add-user-parameters"></a>Adicione parâmetros do usuário

1. Adicione funcionalidades para que o usuário controle cores e tamanhos de elementos visuais, incluindo parâmetros internos da interface do usuário.

   ![CV02to03](./media/funnel-plot/diagram-two.PNG)

1. Edite *capabilities.json* e atualize a seção `objects`. Aqui, definimos nomes, dicas de ferramenta e tipos de cada parâmetro e também decidimos sobre a partição de parâmetros em grupos (três grupos, nesse caso).

   baixe [capabilities.json](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter3_RCustomVisual/funnelRvisual_v03/capabilities.json). Consulte [propriedades do objeto](./objects-properties.md) para obter mais informações

   ![funcionalidades](./samples/funnel-plot/chapter-3/funnel-r-visual-v03/capabilities-before-after.PNG)

1. Edite *src/settings.ts* para espelhar [este settings.ts](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter3_RCustomVisual/funnelRvisual_v03/src/settings.ts). Esse arquivo é gravado em TypeScript.  

   Aqui, você localizará dois blocos do código além de:
   - Declarar que a nova interface deve reter o valor da propriedade
   - Definir uma propriedade de membro e valores padrão

   ![configurações](./samples/funnel-plot/chapter-3/funnel-r-visual-v03/settings-ts-before-after.PNG)

1. Edite *script.r* para espelhar [este script.r](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter3_RCustomVisual/funnelRvisual_v03/script.r). Isso dá suporte para os parâmetros na interface do usuário adicionando `if.exists` chamadas por parâmetro de usuário.

   > [!TIP]
   > Para seguir as alterações no script R, pesquise os comentários:
   >
   > ```r
   > #RVIZ_IN_PBI_GUIDE:BEGIN:Added to enable user parameters
   >  ...
   > #RVIZ_IN_PBI_GUIDE:END:Added to enable user parameters
   >
   > #RVIZ_IN_PBI_GUIDE:BEGIN:Removed to enable user parameters 
   >  ...
   > #RVIZ_IN_PBI_GUIDE:END:Removed to enable user parameters
   > ```

   ![script antes e depois](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter3_RCustomVisual/funnelRvisual_v03/script_r_before_after_1.png)

   Você pode optar por não expor os parâmetros à interface do usuário, como fizemos.  

1. Recrie o pacote do visual usando o comando `pbiviz package` e tente importá-lo para o Power BI.

> [!NOTE]
> Consulte o [PBIX](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter3_RCustomVisual/funnelPlot_RCustomVisual.pbix) e o [código-fonte](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter3_RCustomVisual/funnelRvisual_v03/) para download.

> [!TIP]
> Aqui adicionamos parâmetros de vários tipos (booliano, numérico, de cadeia de caracteres e de cor) de uma vez. Para um caso simples, consulte [este exemplo](https://github.com/Microsoft/PowerBI-visuals/blob/master/RVisualTutorial/PropertiesPane.md) sobre como adicionar um único parâmetro. 

## <a name="convert-visual-to-rhtml-based-visual"></a>Converter o visual para um visual com base em RHTML

Como o visual resultante é baseado em PNG, ele não é responsivo à focalização do mouse, não pode ser ampliado e assim por diante, portanto, precisamos convertê-lo em um visual baseado em HTML. Criaremos um modelo de Visual vazio baseado em HTML da plataforma R e, em seguida, copiaremos alguns scripts do projeto baseado em PNG.

1. Execute o comando:

   ```bash
   pbiviz new funnel-visual-HTML -t rhtml
   cd funnel-visual-HTML
   npm install 
   pbiviz package
   ```

1. Abra *capabilities.json* e anote a linha `"scriptOutputType":"html"`.

1. Abra *dependencies.json* e anote os nomes dos pacotes do R listados.

1. Abra *script.r* e anote a estrutura. Você pode abri-lo e executá-lo no RStudio, uma vez que ele não usa entrada externa. 

   Isso cria e salva o *out.html*. Esse arquivo é autossuficiente (sem dependências externas) e define os gráficos dentro do widget de HTML. 

   > [!IMPORTANT]
   > Para usuários do `htmlWidgets`, os utilitários do R são fornecidos na [pasta r_files](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter4_RHTMLCustomVisual/funnelRHTMLvisual_v01/r_files) para ajudar a converter objetos `plotly` ou `widget` para HTML autossuficiente. 
   > 
   > Esta versão do visual da plataforma R também dá suporte ao comando `source` (ao contrário dos tipos de visuais anteriores), para tornar o seu código mais legível.   
 
1. Substitua *capabilities.json* pelo *capabilities.json* da etapa anterior ou baixe [capabilities.json](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter4_RHTMLCustomVisual/funnelRHTMLvisual_v01/capabilities.json).

   Certifique-se de manter:

   `"scriptOutputType": "html"`

1. Mescle a versão mais recente do *script.r* com o *script.r* do modelo ou baixe [script.r](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter4_RHTMLCustomVisual/funnelRHTMLvisual_v01/script.r).

   O novo script usa o pacote `plotly` para converter o objeto **ggplot** em um objeto **plotly** e, em seguida, no pacote `htmlWidgets` para salvá-lo em um arquivo HTML. 

   A maioria das funções do utilitário é movida para [_r_files/utils.r_](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter4_RHTMLCustomVisual/funnelRHTMLvisual_v01/r_files/utils.r) e a função `generateNiceTooltips` é adicionada para a aparência do objeto **plotly**.

   ![1](./samples/funnel-plot/chapter-4/RHTML-v01/script-before-after-1.PNG)
   
   ![2](./samples/funnel-plot/chapter-4/RHTML-v01/script-before-after-2.PNG)

   > [!TIP]
   > Para seguir as alterações no script R, pesquise os comentários:
   > 
   > ```r
   > #RVIZ_IN_PBI_GUIDE:BEGIN:Added to create HTML-based 
   >  ...
   > #RVIZ_IN_PBI_GUIDE:BEGIN:Added to create HTML-based
   >
   > #RVIZ_IN_PBI_GUIDE:BEGIN:Removed to create HTML-based  
   > ...
   > #RVIZ_IN_PBI_GUIDE:BEGIN:Removed to create HTML-based
   > ```

1. Mescle a versão mais recente do *dependencies.json* com o *dependencies.json* do modelo, para incluir novas dependências de pacote do R ou baixe [dependencies.json](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter4_RHTMLCustomVisual/funnelRHTMLvisual_v01/dependencies.json).

1. Edite *src/settings.ts* da mesma forma que nas etapas anteriores.

1. Recrie o pacote do visual usando o comando `pbiviz package` e tente importá-lo para o Power BI.

> [!NOTE]
> Consulte o [PBIX e o código-fonte](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter4_RHTMLCustomVisual/funnelRHTMLvisual_v01) para download.

## <a name="build-additional-examples"></a>Criar exemplos adicionais

1. Execute o comando a seguir para criar um projeto vazio: 

   ```bash
   pbiviz new example -t rhtml
   cd example
   npm install 
   pbiviz package
   ```

1. Assuma o código desta [demonstração](http://www.htmlwidgets.org/showcase_networkD3.html) e faça as alterações realçadas:

   ![Alterações realçadas](./media/funnel-plot/diagram-three.PNG)

1. Substitua o *script.r* do seu modelo e execute o `pbiviz package` novamente. Agora o visual está incluído no seu relatório do Power BI.

## <a name="tips-and-tricks"></a>Dicas e truques

* Recomendamos que os desenvolvedores editem *pbiviz.json* para armazenar os metadados corretos, como de **versão**, de **email**, de **nome**, de **tipo de licença** e assim por diante.

   > [!IMPORTANT]
   > O campo **guid** é o identificador exclusivo de um visual. Se você criar um projeto para cada visual, o GUID também será diferente. Ele é o mesmo apenas ao usar um projeto antigo copiado para um novo visual, o que você não deve fazer.

* Edite [*assets/icon.png*](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter4_RHTMLCustomVisual/funnelRHTMLvisual_v01/assets/icon.png) para criar ícones exclusivos para o seu visual. 

* Para depurar o código R no RStudio usando os mesmos dados que no seu relatório do Power BI, adicione o seguinte ao início do script R (edite a variável `fileRda`):

   ```r
   #DEBUG in RStudio
   fileRda = "C:/Users/yourUserName/Temp/tempData.Rda"
   if(file.exists(dirname(fileRda)))
   {
     if(Sys.getenv("RSTUDIO")!="")
       load(file= fileRda)
     else
       save(list = ls(all.names = TRUE), file=fileRda)
   }
   ```

   Isso salva o ambiente de um relatório do Power BI e o carrega em RStudio. 

* Você não precisa desenvolver Visuais da plataforma R do zero com o código disponível no [GitHub](https://github.com/Microsoft?utf8=%E2%9C%93&q=PowerBI&type=&language=R). Você pode selecionar o visual a ser usado como um modelo e copiar o código em um novo projeto.

   Por exemplo, tente usar o [visual personalizado spline](https://github.com/Microsoft/PowerBI-visuals-spline).

* Cada Visual do R aplica o operador de `unique` à sua tabela de entrada. Para evitar que linhas idênticas sejam removidas, considere adicionar um campo de entrada extra com uma ID exclusiva e ignorá-lo no código R.   

* Se você tiver uma conta do Power BI, use o serviço do Power BI para desenvolver um visual [rapidamente](/PowerBI-visuals/docs/step-by-step-lab/creating-a-custom-visual/#testing-the-custom-visual) em vez de recriar o pacote dele com o comando `pbiviz package`.

### <a name="html-widgets-gallery"></a>Galeria de widgets HTML
Explore visuais na [Galeria de widgets HTML](http://gallery.htmlwidgets.org/) para uso no seu próximo visual. Para facilitar as coisas, criamos um [repositório de projeto de visuais](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter4_RHTMLCustomVisual/multipleRHTML) com mais de 20 visuais de HTML interativos dos quais escolher.

> [!TIP]
> Para alternar entre os widgets HTML, use **Formato** > **Configurações** > **Tipo**. Experimente com [este arquivo PBIX](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter4_RHTMLCustomVisual/multipleRHTML/assets/sample.pbix). 

#### <a name="to-use-a-sample-for-your-visual"></a>Para usar uma amostra para o seu visual

1. Baixe a pasta inteira.
1. Edite *script.r* e *dependencies.json* para manter apenas um widget.
1. Edite *capabilities.json* e *settings.ts* para remover o seletor de `Type`.
1. Altere `const updateHTMLHead: boolean = true;` para `false` em *visual.ts*. *(para melhor desempenho)*
1. Altere os metadados no *pbiviz.json* e, mais importante, o campo `guid`.
1. Recrie o pacote e continue a personalizar o visual como desejado. 

![CV02to03](./media/funnel-plot/diagram-four.PNG)

![CV02to03](./media/funnel-plot/diagram-five.PNG)

> [!NOTE]
> Nem todos os widgets neste projeto têm suporte do serviço.

## <a name="next-steps"></a>Próximas etapas

Para saber mais, confira tutoriais adicionais sobre os [visuais do Power BI](./custom-visual-develop-tutorial.md) e os [Visuais do R](/power-bi/visuals/service-r-visuals).

Saiba como [desenvolver e enviar visuais](https://powerbi.microsoft.com/documentation/powerbi-developer-office-store/) para a [Office Store (galeria)](https://store.office.com/appshome.aspx?ui=en-US&rs=en-US&ad=US&clickedfilter=OfficeProductFilter%3aPowerBI&productgroup=PowerBI) ou, para obter mais exemplos, consulte a [Demonstração do script R](https://community.powerbi.com/t5/R-Script-Showcase/bd-p/RVisuals)
