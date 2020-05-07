---
title: Adicionar opções de formatação a um visual personalizado do Power BI
description: Um tutorial sobre como desenvolver opções de formato visual personalizado do Power BI
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.topic: tutorial
ms.subservice: powerbi-custom-visuals
ms.date: 11/21/2018
ms.openlocfilehash: 3d0dc39fbf6d1daf978292d0e5e43129e66376c7
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/05/2020
ms.locfileid: "79380998"
---
# <a name="tutorial-adding-formatting-options-to-a-power-bi-visual"></a>Tutorial: Adicionar opções de formatação a um visual do Power BI

Nesse tutorial, vamos mostrar como adicionar propriedades comuns ao visual.

Neste tutorial, você aprenderá a:
> [!div class="checklist"]
> * Adicionar propriedades visuais.
> * Empacotar o visual.
> * Importar o visual personalizado para um relatório do Power BI Desktop.

## <a name="adding-formatting-options"></a>Como adicionar opções de formatação

1. Na **Power BI**, selecione o **Formato de Página**.

    Será exibida uma mensagem informando: *Opções de formatação não estão disponíveis para este visual.*

    ![Pincel de formatação](media/custom-visual-develop-tutorial-format-options/format-paintbrush.png)

2. No **Visual Studio Code**, abra o arquivo *capabilities.json*.

3. Antes da matriz **dataViewMappings**, adicione **objetos** (depois da linha 8).

    ```json
    "objects": {},
    ```

    ![Adicionar objetos](media/custom-visual-develop-tutorial-format-options/add-objects.png)

4. Salve o arquivo **capabilities.json**.

5. No **Power BI**, revise as opções de formatação novamente.

    > [!Note]
    > Se as opções de formatação não forem alteradas, selecione **Recarregar visual personalizado**.

    ![Exibir opções de formatação](media/custom-visual-develop-tutorial-format-options/view-formatting-options.png)

6. Defina a opção **Título** como *Desligado*. Observe que o visual não exibe mais o nome da medida no canto superior esquerdo.

    ![A opção de bloco está desativada](media/custom-visual-develop-tutorial-format-options/tile-option-off.png)

    ![Sem bloco de nome](media/custom-visual-develop-tutorial-format-options/no-name-tile.png)

### <a name="adding-custom-formatting-options"></a>Adicionar opções de formatação personalizadas

Você pode adicionar propriedades personalizadas para ativar a configuração da cor do círculo, além da largura da borda.

1. No PowerShell, interrompa o visual personalizado.

2. No Visual Studio Code, no arquivo **capabilities.json**, insira o seguinte fragmento JSON no objeto rotulado **objects**.

    ```json
        {
            "circle": {
                "displayName": "Circle",
                "properties": {
                    "circleColor": {
                        "displayName": "Color",
                        "description": "The fill color of the circle.",
                        "type": {
                            "fill": {
                                "solid": {
                                    "color": true
                                }
                            }
                        }
                    },
                    "circleThickness": {
                        "displayName": "Thickness",
                        "description": "The circle thickness.",
                        "type": {
                            "numeric": true
                        }
                    }
                }
            }
        }
    ```

    O fragmento JSON descreve um grupo denominado circle, que consiste em duas opções denominadas circleColor e circleThickness.

   ![Código de espessura do círculo](media/custom-visual-develop-tutorial-format-options/circle-thickness-code.png)

3. Salve o arquivo **capabilities.json**.

4. No **painel do Explorer**, de dentro da pasta **src**, selecione **settings.ts**. *Esse arquivo representa as configurações para o visual inicial*.

5. No arquivo **settings.ts**, substitua as duas classes pelo código a seguir.

    ```typescript
    export class CircleSettings {
        public circleColor: string = "white";
        public circleThickness: number = 2;
    }
    export class VisualSettings extends DataViewObjectsParser {
        public circle: CircleSettings = new CircleSettings();
    }
    ```

    ![Classes de módulo](media/custom-visual-develop-tutorial-format-options/module-classes.png)

    Esse módulo define as duas classes. A classe **CircleSettings** define duas propriedades com nomes que correspondem aos objetos definidos no arquivo **capabilities.json** (**circleColor** e **circleThickness**) e também define valores padrão. A classe **VisualSettings** herda a classe **DataViewObjectParser** e adiciona uma propriedade chamada **circle**, que corresponde ao objeto definido no arquivo *capabilities.json*, e retorna uma instância de **CircleSettings**.

6. Salve o arquivo **settings.ts**.

7. Abra o arquivo **visual.ts**.

8. No arquivo **visual.ts**,

    importar `VisualSettings`, `VisualObjectInstanceEnumeration` e `EnumerateVisualObjectInstancesOptions`:

    ```typescript
    import { VisualSettings } from "./settings";
    import VisualObjectInstanceEnumeration = powerbi.VisualObjectInstanceEnumeration;
    import EnumerateVisualObjectInstancesOptions = powerbi.EnumerateVisualObjectInstancesOptions;
    ```

    e na classe **Visual**, adicione a seguinte propriedade:

    ```typescript
    private visualSettings: VisualSettings;
    ```

    Esta propriedade armazena uma referência ao objeto **VisualSettings**, descrevendo as configurações do visual.

    ![Adicionar classe visual](media/custom-visual-develop-tutorial-format-options/visual-class-add-on.png)

9. Na classe **Visual**, adicione o seguinte método antes do método **update**. Este método é usado para preencher as opções de formatação.

    ```typescript
    public enumerateObjectInstances(options: EnumerateVisualObjectInstancesOptions): VisualObjectInstanceEnumeration {
        const settings: VisualSettings = this.visualSettings || <VisualSettings>VisualSettings.getDefault();
        return VisualSettings.enumerateObjectInstances(settings, options);
    }
    ```

    Este método é usado para preencher as opções de formatação.

    ![Objeto Visual settings](media/custom-visual-develop-tutorial-format-options/visual-settings-object.png)

10. No método **update**, após a declaração da variável **radius**, adicione o seguinte código.

    ```typescript
    this.visualSettings = VisualSettings.parse<VisualSettings>(dataView);

    this.visualSettings.circle.circleThickness = Math.max(0, this.visualSettings.circle.circleThickness);
    this.visualSettings.circle.circleThickness = Math.min(10, this.visualSettings.circle.circleThickness);
    ```

    Este código recupera as opções de formato. Ele ajusta qualquer valor passado para a propriedade **circleThickness**, convertendo-o para 0 se for negativo ou 10 se for um valor maior que 10.

    ![Variável radius](media/custom-visual-develop-tutorial-format-options/radius.png)

11. No **elemento circle**, modifique o valor em **fill style** para a seguinte expressão.

    ```typescript
    this.visualSettings.circle.circleColor
    ```

    ![Preenche o elemento circle](media/custom-visual-develop-tutorial-format-options/circle-element-fill.png)

12. No **elemento circle**, modifique o valor em **stroke-width style** para a seguinte expressão.

    ```typescript
    this.visualSettings.circle.circleThickness
    ```

    ![Espessura do traço do círculo](media/custom-visual-develop-tutorial-format-options/circle-stroke-width.png)

13. Salve o arquivo visual.ts.

14. No PowerShell, inicie o visual.

    ```powershell
    pbiviz start
    ```

15. No **Power BI**, na barra de ferramentas flutuando acima do visual, selecione **Ativar/Desativar Recarga Automática**.

16. Nas opções de **formato visual**, expanda **Círculo**.

    ![Formato do círculo](media/custom-visual-develop-tutorial-format-options/circle-format.png)

    Modifique as opções de **cor** e **espessura**.

    Modifique a opção de **espessura** para um valor menor do que zero e um valor maior do que 10. Em seguida, observe que o visual atualiza o valor para um mínimo ou máximo tolerável.

## <a name="packaging-the-custom-visual"></a>Preparar o visual personalizado

Insira valores de propriedade para o projeto visual personalizado, atualize o arquivo de ícone e, em seguida, prepare o visual personalizado.

1. No **PowerShell**, interrompa o visual personalizado.

2. Abra o arquivo **biviz.json** no **Visual Studio Code**.

3. No objeto **visual**, modifique a propriedade **displayName** para *Circle Card*.

    No painel **Visualizações**, passar o mouse sobre o ícone revela o nome de exibição.

    ![Visual Nome de Exibição](media/custom-visual-develop-tutorial-format-options/display-name-viz.png)

4. Para a propriedade **description**, insira o texto a seguir.

    *Exibe um valor de medida formatado dentro de um círculo*

5. Preencha **supportUrl** e **gitHubUrl** para o visual.

    Exemplo:

    ```json
    {
        "supportUrl": "https://community.powerbi.com",
        "gitHubUrl": "https://github.com/microsoft/PowerBI-visuals-circlecard"
    }
    ```

6. Insira seus detalhes no objeto **author**.

7. Salve o arquivo **pbiviz.json**.

8. No objeto **assets**, observe que o documento define um caminho para um ícone. O ícone é a imagem que aparece no painel **_Visualizações_** . Ele deve ser um arquivo **PNG**, *20 pixels por 20 pixels*.

9. No Windows Explorer, copie o arquivo icon.png, e cole-o para substituir o arquivo padrão localizado na pasta assets.

10. No Visual Studio Code, no painel do Explorer, expanda a pasta assets e, em seguida, selecione o arquivo icon.png.

11. Verifique o ícone.

    ![Imagem do painel de visualização](media/custom-visual-develop-tutorial-format-options/viz-pane-image.png)

12. No Visual Studio Code, verifique se todos os arquivos foram salvos.

13. Para preparar o visual personalizado, no PowerShell, digite o seguinte comando.

    ```powershell
    pbiviz package
    ```

    ![Pasta dist](media/custom-visual-develop-tutorial-format-options/dist-folder.png)

Agora o pacote é enviado para a pasta **dist** do projeto. O pacote contém tudo o que é necessário para importar o visual personalizado para o serviço do Power BI ou para um relatório do Power BI Desktop. Você preparou o visual personalizado e agora ele está pronto para uso.

## <a name="importing-the-custom-visual"></a>Importar o visual personalizado

Agora você pode abrir o relatório do Power BI Desktop e importar o visual personalizado Circle Card.

1. Abra o **Power BI Desktop**, crie um novo relatório com qualquer *conjunto de dados de amostra*

2. No painel **_Visualizações_** , selecione as **reticências** e, em seguida, selecione **Importar do arquivo**.

    ![Adicionar visualização personalizada à área de trabalho](media/custom-visual-develop-tutorial-format-options/add-custom-viz-to-desktop.png)

3. Na **janela de importação**, selecione **Importar**.

4. Na janela aberta, acesse a pasta **dist** no diretório do projeto.

5. Selecione o arquivo **circleCard.pbiviz** e, em seguida, selecione **Abrir**.

6. Após a importação bem-sucedida, selecione **OK**.

7. Verifique se o visual foi adicionado ao painel **_Visualizações_** .

    ![Exibir no painel de visualização do Power BI Desktop](media/custom-visual-develop-tutorial-format-options/view-in-desktop-viz-pane.png)

8. Passe o mouse sobre o ícone **Circle Card** e observe a dica de ferramenta que aparece.

## <a name="debugging"></a>Depuração

Para obter dicas de como depurar seu visual personalizado, veja o [guia depuração](https://microsoft.github.io/PowerBI-visuals/docs/how-to-guide/how-to-debug/).

## <a name="next-steps"></a>Próximas etapas

É possível listar seu visual desenvolvido recentemente para outras pessoas usarem enviando-o para o **AppSource**. Para saber mais sobre esse processo, veja [Publicar visuais do Power BI no AppSource](office-store.md).
