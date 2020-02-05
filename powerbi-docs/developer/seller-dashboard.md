---
title: Enviar um visual do Power BI para o AppSource usando o Painel do Vendedor
description: Enviar um visual do Power BI para o AppSource usando o Painel do Vendedor
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.topic: conceptual
ms.subservice: powerbi-custom-visuals
ms.date: 12/03/2019
ms.openlocfilehash: 73a6a3d16ae2515af41a3232a37579e18876f38b
ms.sourcegitcommit: 8e3d53cf971853c32eff4531d2d3cdb725a199af
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/04/2020
ms.locfileid: "75223658"
---
# <a name="submit-a-power-bi-visual-to-appsource-using-seller-dashboard"></a>Enviar um visual do Power BI para o AppSource usando o Painel do Vendedor

Você deve enviar um email com os arquivos **pbiviz** e **pbix** à equipe do Power BI antes de enviar para o AppSource. Isso permite à equipe do Power BI carregar os arquivos para o servidor de compartilhamento público. Caso contrário, a loja não poderá recuperar os arquivos. Envie os arquivos com os novos envios de visuais do Power BI, as atualizações em visuais de Power BI existentes e correções de envios rejeitados.

>[!NOTE]
>O [Painel do Vendedor](https://docs.microsoft.com/office/dev/store/use-the-seller-dashboard-to-submit-to-the-office-store) está sendo descontinuado. Ele será substituído pelo [Partner Center](https://docs.microsoft.com/partner-center/). Use o Painel do Vendedor apenas se você estiver no meio de um envio de visual do Power BI. Se estiver enviando um novo visual do Power BI para o AppSource, use o [método do Partner Center](office-store.md#submitting-to-appsource).

### <a name="seller-dashboard-submission-process"></a>Processo de envio do Painel do Vendedor

Você deve ter uma conta de desenvolvedor válida do Office para se conectar ao [Centro de Desenvolvimento do Office](https://dev.office.com/). Uma conta de desenvolvedor do Office deve ser uma Conta Microsoft Live ID, por exemplo, hotmail.com ou outlook.com.

1. Navegue até a [central de desenvolvedores](https://sellerdashboard.microsoft.com/Application/Summary).

2. Selecione **Adicionar um novo aplicativo**.

    ![Adicionar um aplicativo](media/office-store/powerbi-custom-visual-add-an-app.png)

3. Selecione **Visual personalizado do Power BI** e **Avançar**.

4. Selecione **+** em **Pacote do aplicativo** e selecione o arquivo XML do pacote do aplicativo recebido da equipe do Power BI na caixa de diálogo Abrir Arquivo.

    ![Pacote do aplicativo](media/office-store/powerbi-custom-visual-apppackage.png)

5. Você deve receber uma aprovação de que este é um pacote do aplicativo Power BI válido.

    ![Manifesto aprovado](media/office-store/powerbi-custom-visual-manifest-approved.png)

6. Preencha os detalhes das **Informações gerais**.

   * *Título do envio:* Como seu envio será nomeado na central de desenvolvedores.
   * *Versão:* Seu número de versão é preenchido automaticamente no pacote do aplicativo do suplemento.
   * *Data de lançamento (UTC):* Selecione uma data de lançamento na loja para seu aplicativo. Se uma data futura for escolhida, seu aplicativo não estará disponível na loja até essa data.
   * *Categoria:* A primeira categoria será automaticamente preenchida como "Visualização de dados + BI". Esta é a forma como todos os visuais do Power BI são marcados. Você pode fornecer até duas categorias adicionais para ajudar os usuários a pesquisar facilmente seu visual.
   * *Notas de teste:* opcionais, se você quiser fornecer algumas instruções para os testadores da Microsoft
   * *Meu aplicativo chama, dá suporte para, contém ou usa criptografias:* deixe desmarcado
   * *Tornar este suplemento disponível no catálogo de suplemento do Office no iPad:* deixe desmarcado
7. Faça upload do seu logotipo do visual, selecionando **+** em **Logotipo do aplicativo**. Em seguida, selecione o arquivo de ícone na caixa de diálogo Abrir arquivo. O arquivo deve ser .png, .jpg, .jpeg ou .gif. Ele deve ter exatamente 300 px (largura) x 300 px (altura) e não pode exceder 512 KB de tamanho.

    ![Logotipo do aplicativo](media/office-store/powerbi-custom-visual-app-logo.png)

8. Preencha os detalhes dos **Documentos de suporte**.

   * Link do documento de suporte
   * Link do documento de privacidade
   * Link do vídeo
   * Contrato de Licença de Usuário Final (EULA)

       Você deve fazer upload de um arquivo EULA. Você pode usar seu próprio EULA ou o EULA padrão na Office Store para os visuais do Power BI. Para usar o EULA padrão, cole a seguinte URL na caixa de diálogo de upload de arquivo do "Contrato de licença de usuário final" do painel do vendedor: [https://visuals.azureedge.net/app-store/Power BI – Default Custom Visual EULA.pdf](https://visuals.azureedge.net/app-store/Power%20BI%20-%20Default%20Custom%20Visual%20EULA.pdf).

9. Selecione **Avançar** para prosseguir para a página **Detalhes**.

10. Selecione **Idioma** e escolha um idioma na lista.

    ![Idioma](media/office-store/powerbi-custom-visual-language.png)

11. Preencha os detalhes da "Descrição".

    * *Nome do aplicativo (para esse idioma):* Insira o título do seu aplicativo, como deve aparecer na vitrine.
    * *Descrição resumida:* Insira uma descrição resumida do seu aplicativo, com até 100 caracteres, como deve aparecer na vitrine. Essa descrição será exibida nas páginas de nível superior, juntamente com o logotipo. Você pode usar a descrição do pacote pbiviz.
    * *Descrição longa:* Forneça uma descrição mais detalhada de seu aplicativo que os clientes verão na sua página de detalhes do aplicativo. Se desejar transformar seu elemento visual em software livre para a comunidade aprimorá-lo, forneça aqui o link para o repositório público, como o GitHub.

12. Faça upload de, pelo menos, uma captura de tela. O formato pode ser .png, .jpg, .jpeg ou .gif. Ele deve ter exatamente 1.366 px (largura) x 768 px (altura). Não pode ser maior do que 1.024 KB para o tamanho do arquivo. *Para melhor utilização, adicione bolhas de texto para articular a proposição de valores dos principais recursos mostrados em cada captura de tela.*

12. Se quiser adicionar mais idiomas, selecione **Adicionar um idioma** e repita as etapas 10 e 11. A adição de mais idiomas ajudará os usuários a exibirem os detalhes visuais personalizados em seu próprio idioma. Os idiomas que não serão listados usarão o primeiro idioma selecionado como padrão.

13. Quando terminar de adicionar os idiomas, selecione **Avançar** para prosseguir para a página **Bloquear o acesso**.

14. Se quiser impedir que clientes em regiões ou países específicos usem ou comprem seu aplicativo, marque a caixa de seleção e escolha na lista.

15. Selecione **Avançar** para prosseguir para a página **Preço**.

16. Atualmente, há suporte apenas para visuais *gratuitos* e aquisições adicionais dentro do visual (compra no aplicativo) não são permitidas. Selecione **Este aplicativo é gratuito**.

    > [!NOTE]
    > Se você selecionar qualquer outra opção que não seja a gratuita ou tiver um conteúdo de compra no aplicativo no visual enviado, o envio será rejeitado.

17. Agora é possível selecionar **Salvar como rascunho** e enviar mais tarde ou selecionar **Enviar para aprovação** para enviar o visual personalizado à Office Store.

## <a name="seller-dashboard-certification-submission-process"></a>Processo de envio da certificação do Painel do Vendedor

Siga as instruções nesta seção para enviar um visual do Power BI para certificação no Painel do Vendedor. Use esse método se você tiver enviado um visual do Power BI anteriormente para o AppSource por meio do Painel do Vendedor.

1. Envie um email à equipe de suporte de visuais do Power BI (pbicvsupport@microsoft.com). No email, inclua as seguintes informações:
    * Título: Solicitação de certificação visual
    * Link para o repositório do GitHub em que o código-fonte legível por humanos está hospedado
    * [Cumprir os requisitos](power-bi-custom-visuals-certified.md#certification-requirements)
    * Passar a revisão de código

2. A equipe de visuais do Microsoft Power BI notifica você quando seu visual do Power BI é certificado e adicionado à lista de [visuais certificados do Power BI](power-bi-custom-visuals-certified.md#certified-power-bi-visuals) ou é rejeitado com um relatório dos problemas que precisam ser corrigidos. É responsabilidade do desenvolvedor manter uma linha aberta de comunicação com a Microsoft e atualizar os visuais certificados como necessário.

## <a name="tracking-submission-status-and-usage"></a>Acompanhamento do uso e do status do envio

Você pode examinar as [políticas de validação](https://dev.office.com/officestore/docs/validation-policies#13-power-bi-custom-visuals).

Após o envio, você poderá exibir o status do envio no [dashboard de aplicativos](https://sellerdashboard.microsoft.com/Application/Summary/).

## <a name="certify-your-visual"></a>Certificar seu visual

Depois de criar seu visual, você tem a opção de [certificá-lo](../developer/power-bi-custom-visuals-certified.md).

## <a name="next-steps"></a>Próximas etapas

[Desenvolvimento de um visual personalizado do Power BI](visuals/custom-visual-develop-tutorial.md)  
[Visualizações no Power BI](../visuals/power-bi-report-visualizations.md)  
[Visualizações personalizadas no Power BI](../developer/power-bi-custom-visuals.md)  
[Obter um visual do Power BI certificado](../developer/power-bi-custom-visuals-certified.md)

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
