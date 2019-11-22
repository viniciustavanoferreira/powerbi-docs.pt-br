---
title: Visuais no Power BI
description: Visualizações personalizadas no Power BI
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/15/2019
LocalizationGroup: Visualizations
ms.openlocfilehash: a45566d6fe9f4833ebed91e7c10656a8ca1c6961
ms.sourcegitcommit: 08b73af260ded51daaa6749338cb85db2eab587f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/15/2019
ms.locfileid: "74102055"
---
# <a name="visuals-in-power-bi"></a>Visuais no Power BI

Ao criar ou editar um relatório do Power BI, é possível usar muitos tipos diferentes de visuais. Os ícones desses visuais são exibidos no painel **Visualizações**. Esses visuais vêm pré-empacotados quando você baixa o [Power BI Desktop](https://powerbi.microsoft.com/desktop/) ou abre o [serviço do Power BI](https://app.powerbi.com).

![visualizações](media/power-bi-custom-visuals/power-bi-visualizations.png)

No entanto, você não está limitado a esse conjunto de visuais. Se você selecionar **Mais opções** (...) na parte inferior, outra fonte de visuais de relatório ficará disponível – *visuais do Power BI*.

Os desenvolvedores criam visuais do Power BI usando o SDK de visuais do Power BI. Esses visuais permitem que os usuários de negócios vejam seus dados da maneira que melhor se adapta aos seus negócios. Os autores do relatório podem importar os arquivos de visuais personalizados para seus relatórios e usá-los como eles fariam com outros visuais do Power BI. Os visuais têm uma importância especial no Power BI e podem ser filtrados, realçados, editados, compartilhados e assim por diante.

Visuais do Power BI são implantados de três maneiras:

* Arquivos de elementos visuais personalizados
* Elementos visuais organizacionais
* Elementos visuais do Marketplace

## <a name="custom-visual-files"></a>Arquivos de elementos visuais personalizados

Os visuais do Power BI são pacotes que incluem o código para renderizar os dados fornecidos a eles. Qualquer pessoa pode criar um visual personalizado e empacotá-lo como um único arquivo `.pbiviz`, que pode ser importado em um relatório do Power BI.

> [!WARNING]
> Um visual personalizado poderia conter código com riscos de segurança ou de privacidade. Verifique se você confia no autor e na fonte do visual personalizado antes de importá-lo em seu relatório.

## <a name="organizational-visuals"></a>Elementos visuais organizacionais

Os administradores do Power BI aprovam e implantam visuais do Power BI em sua organização, que os autores de relatório podem descobrir, atualizar e usar com facilidade. Os administradores podem gerenciar facilmente (por exemplo, atualizar versão, desabilitar/habilitar) esses visuais.

 [Leia mais sobre visuais da organização](power-bi-custom-visuals-organization.md).

## <a name="marketplace-visuals"></a>Elementos visuais do Marketplace

Os membros da comunidade e a Microsoft contribuíram com seus visuais do Power BI para benefício público e os publicaram no marketplace [AppSource](https://appsource.microsoft.com/marketplace/apps?product=power-bi-visuals). É possível baixar esses visuais e adicioná-los aos seus relatórios do Power BI. A Microsoft testou e aprovou esses visuais do Power BI com relação à funcionalidade e à qualidade.

O que é o [AppSource](office-store.md)? É o lugar em que você pode encontrar aplicativos, suplementos e extensões para seu software da Microsoft. A AppSource conecta milhões de usuários de produtos como o Office 365, o Azure, o Dynamics 365, o Cortana e o Power BI com soluções que os ajudam a realizar seu trabalho com mais eficiência, perspicácia ou harmonia do que antes.

### <a name="certified-visuals"></a>Elementos visuais certificados

Os visuais certificados para o Power BI são visuais de marketplace que passaram por rigorosos testes de qualidade adicionais e são compatíveis em outros cenários, como [assinaturas de email](../service-report-subscribe.md) e para serem [exportados para o PowerPoint](../consumer/end-user-powerpoint.md).
Para ver a lista de visuais do Power BI certificados ou para enviar seus próprios, confira [Visuais do Power BI certificados](power-bi-custom-visuals-certified.md).

Você é um desenvolvedor da Web e está interessado em criar suas próprias visualizações e adicioná-las ao AppSource? Confira [Developing a Power BI custom visual](visuals/custom-visual-develop-tutorial.md) (Desenvolvimento de um visual personalizado do Power BI) e saiba como [publicar visuais personalizados no AppSource](office-store.md).

### <a name="import-a-custom-visual-from-a-file"></a>Importar um visual personalizado de um arquivo

1. Selecione as reticências na parte inferior do painel **Visualizações**.

    ![visualizations2](media/power-bi-custom-visuals/power-bi-visualizations2.png)

2. No menu suspenso, selecione **Importar do arquivo**.

    ![importar do arquivo](media/power-bi-custom-visuals/power-bi-custom-visual-import-from-file.png)

3. No menu de arquivo **Abrir**, selecione o arquivo `.pbiviz` que você deseja importar e, em seguida, selecione **Abrir**. O ícone do visual personalizado é adicionado à parte inferior do seu painel **Visualizações** e agora está disponível para uso em seu relatório.

    ![currículo importado](media/power-bi-custom-visuals/power-bi-custom-visual-imported.png)

### <a name="import-organizational-visuals"></a>Importar elementos visuais organizacionais

1. Selecione as reticências na parte inferior do painel **Visualizações**.

    ![visual org 1](media/power-bi-custom-visuals/power-bi-visual-org-01.png)

2. No menu suspenso, selecione **Importar do marketplace**.

    ![visual org 2](media/power-bi-custom-visuals/power-bi-visual-org-02.png)

3. Selecione **MINHA ORGANIZAÇÃO** no menu da guia superior.

    ![visual org 3](media/power-bi-custom-visuals/power-bi-visual-org-03.png)

4. Role a lista para localizar o visual para importar.

    ![visual org 4](media/power-bi-custom-visuals/power-bi-visual-org-04.png)

5. Selecione **Adicionar** para importar o visual personalizado. O ícone é adicionado à parte inferior do seu painel **Visualizações** e agora está disponível para uso em seu relatório.

    ![visual org 5](media/power-bi-custom-visuals/power-bi-visual-org-05.png)

## <a name="download-or-import-power-bi-visuals-from-microsoft-appsource"></a>Baixar ou importar visuais do Power BI do Microsoft AppSource

Você tem duas opções para baixar e importar os visuais do Power BI: de dentro do Power BI e do [site do AppSource](https://appsource.microsoft.com/).

### <a name="import-power-bi-visuals-from-within-power-bi"></a>Importar visuais do Power BI de dentro do Power BI

1. Selecione as reticências na parte inferior do painel **Visualizações**.

    ![visualizações 2](media/power-bi-custom-visuals/power-bi-visualizations2.png)

2. No menu suspenso, selecione **Importar do marketplace**.

    ![visual org 2](media/power-bi-custom-visuals/power-bi-visual-org-02.png)

3. Role a lista para localizar o visual para importar.

    ![importar visual](media/power-bi-custom-visuals/power-bi-import-visual.png)

4. Para saber mais sobre um dos visuais, realce e selecione-o.

    ![Selecionar](media/power-bi-custom-visuals/power-bi-select.png)

5. Na página de detalhes, você pode exibir capturas de tela, vídeos, descrições detalhadas e muito mais.

    ![Sinóptico](media/power-bi-custom-visuals/power-bi-synoptic.png)

6. Role para baixo para ver as análises.

    ![Revisões](media/power-bi-custom-visuals/power-bi-reviews.png)

7. Selecione **Adicionar** para importar o visual personalizado. O ícone é adicionado à parte inferior do seu painel **Visualizações** e agora está disponível para uso em seu relatório.

    ![visual importado](media/power-bi-custom-visuals/power-bi-custom-visual-imported.png)

### <a name="download-and-import-power-bi-visuals-from-microsoft-appsource"></a>Baixar e importar visuais do Power BI do Microsoft AppSource

1. Inicie em [Microsoft AppSource](https://appsource.microsoft.com) e selecione a guia para **Aplicativos**.

    ![AppSource](media/power-bi-custom-visuals/power-bi-appsource-apps.png)

2. Acesse a [página de resultados de Aplicativos](https://appsource.microsoft.com/marketplace/apps), em que é possível exibir os principais aplicativos em cada categoria, incluindo *Aplicativos do Power BI*. Estamos procurando visuais do Power BI, então vamos selecionar **Visuais do Power BI** na lista do painel de navegação para restringir os resultados.

    ![Visuais do AppSource](media/power-bi-custom-visuals/power-bi-appsource-visuals.png)

3. O AppSource exibe um bloco para cada visual personalizado.  Cada bloco tem um instantâneo de visual personalizado com uma breve descrição e um link de download. Para ver mais detalhes, selecione o bloco.

    ![Visual personalizado selecionado](media/power-bi-custom-visuals/powerbi-custom-select-visual.png)

4. Na página de detalhes, você pode exibir capturas de tela, vídeos, descrições detalhadas e muito mais. Selecione **Obter agora** para baixar o visual personalizado e, em seguida, concorde com os Termos de uso.

    ![AppSource Get](media/power-bi-custom-visuals/power-bi-appsource-get.png)

5. Selecione o link para baixar o visual personalizado.

    ![Baixar](media/power-bi-custom-visuals/powerbi-custom-download.png)

    A página de download também inclui instruções sobre como importar o visual personalizado para o Power BI Desktop e para o serviço do Power BI.

    Você também pode baixar um relatório de exemplo que inclua o visual personalizado e apresente suas funcionalidades.

    ![Experimentar exemplo](media/power-bi-custom-visuals/powerbi-custom-try-sample.png)

6. Salve o arquivo `.pbiviz` e, em seguida, abra o Power BI.

7. Importe o arquivo `.pbiviz` para seu relatório. (Confira a seção acima [Importar um visual personalizado de um arquivo](#import-a-custom-visual-from-a-file)).

## <a name="considerations-and-limitations"></a>Considerações e limitações

* Um visual personalizado é adicionado a um relatório específico quando importado. Se você desejar usar o visual em outro relatório, você precisará importá-lo nesse relatório também. Quando um relatório com um visual personalizado é salvo com a opção **Salvar como** , uma cópia do visual personalizado será salva com o novo relatório.

* Se você não vir um painel **Visualizações**, isso significará que você não tem as permissões de edição do relatório.  Só é possível adicionar visuais do Power BI a relatórios que você pode editar, não a relatórios que só foram compartilhados com você.

## <a name="troubleshoot"></a>Solucionar problemas

Para solucionar problemas, confira [Solução de problemas com visuais do Power BI](power-bi-custom-visuals-troubleshoot.md).

## <a name="faq"></a>PERGUNTAS FREQUENTES

Para saber mais e solucionar suas dúvidas, acesse [Perguntas frequentes sobre os visuais do Power BI](power-bi-custom-visuals-faq.md#organizational-visuals).

## <a name="next-steps"></a>Próximas etapas

* [Visualizações em relatórios do Power BI](../visuals/power-bi-report-visualizations.md)

Mais perguntas? [Experimente a Comunidade do Power BI](https://community.powerbi.com/).
