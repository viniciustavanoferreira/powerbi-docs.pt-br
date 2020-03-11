---
title: Diretrizes para visuais do Power BI
description: Saiba como você pode publicar seu visual personalizado no Microsoft AppSource para que outras pessoas possam descobri-lo e usá-lo por meio de uma compra.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.topic: conceptual
ms.subservice: powerbi-custom-visuals
ms.date: 07/16/2019
ms.openlocfilehash: 0203c191965bd2a496c1a5062b85af64d22b3b76
ms.sourcegitcommit: 743167a911991d19019fef16a6c582212f6a9229
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78400431"
---
# <a name="guidelines-for-power-bi-visuals"></a>Diretrizes para visuais do Power BI
Antes de [publicar](https://docs.microsoft.com/power-bi/developer/office-store) seu visual do Power BI no Microsoft AppSource para outras pessoas descobrirem e usarem, siga as diretrizes para criar uma experiência excelente para seus usuários.

## <a name="power-bi-visuals-with-additional-purchases"></a>Visuais do Power BI com compras adicionais

Você pode enviar visuais do Power BI gratuitos para o Marketplace (Microsoft AppSource). Você também pode enviar os visuais do Power BI do Microsoft AppSource que têm uma marca de preço com "uma compra adicional pode ser necessária". Os visuais do Power BI "Uma compra adicional pode ser necessária" são semelhantes a suplementos de IAP (Compra no Aplicativo) na Office Store. 

Assim como ocorre com um visual gratuito do Power BI, o visual do Power BI com IAP também pode ser certificado. Antes de enviar seu visual do Power BI com IAP para certificação, verifique se ele cumpre os [requisitos de certificação](../power-bi-custom-visuals-certified.md). 

### <a name="what-is-a-power-bi-visual-with-iap-features"></a>O que é um visual do Power BI com recursos de IAP?

Um visual do Power BI com IAP é um visual *gratuito* que oferece *recursos gratuitos*. Ele também tem alguns recursos avançados aos quais podem ser aplicados custos extras. Na descrição do visual do Power BI, os desenvolvedores devem notificar os usuários sobre os recursos que exigem compras adicionais para serem operados. Atualmente, a Microsoft não fornece APIs nativas compatíveis com a compra de aplicativos e suplementos.

Os desenvolvedores podem usar qualquer sistema de pagamento de terceiros para essas compras. Para obter mais informações, confira [nossa política de loja](https://docs.microsoft.com/legal/marketplace/certification-policies#11002-displaying-ads).


>[!IMPORTANT]  
> Se você atualizar seu visual do Power BI de gratuito para "Uma compra adicional pode ser necessária", os usuários precisarão receber o mesmo nível de funcionalidade gratuita que tinham antes da atualização. Você pode adicionar recursos avançados opcionais pagos, além dos recursos gratuitos existentes.

### <a name="watermarks"></a>Marcas d' água

Você pode usar marcas d'água para que os clientes continuem usando os recursos avançados com IAP sem pagar. 

As marcas d'água podem ser usadas para demonstrar a funcionalidade completa do visual do Power BI antes de uma compra ser feita. 

* As marcas d'água podem ser usadas somente em recursos pagos que são usados sem uma licença válida.
* As marcas d'água não são permitidas em visuais do Power BI com uma marca de preço *gratuita*.
* As marcas d'água não são permitidas em visuais com IAP quando o usuário usa recursos gratuitos. 

### <a name="pop-up-window"></a>Janela pop-up

Você pode usar uma janela pop-up para explicar como comprar uma licença quando uma licença inválida (ou expirada) é usada com seu visual com IAP do Power BI.

### <a name="submission-process"></a>Processo de envio

Siga o [processo de envio](office-store.md#submitting-to-appsource), navegue até a guia *Configuração do produto* e marque a caixa de seleção *Meu produto requer a compra de um serviço*.

Depois que o visual do Power BI for validado e aprovado, a listagem do Microsoft AppSource para o visual do Power BI com IAP informará "Uma compra adicional pode ser necessária" nas opções de preço.

>[!NOTE]
>Se o seu visual do Power BI já foi enviado usando o [Painel do Vendedor](https://docs.microsoft.com/office/dev/store/use-the-seller-dashboard-to-submit-to-the-office-store), e você deseja adicionar um recurso de IAP, é necessário escrever nas notas do Painel do Vendedor: "Visual com compra no aplicativo". Você também precisa fornecer um token ou chave de licença para que a equipe de validação possa validar os recursos de IAP.

## <a name="context-menu"></a>Menu de contexto
O menu de contexto é o menu de clique com o botão direito do mouse que é exibido quando o usuário passa o mouse sobre um visual.
Todos os visuais do Power BI devem habilitar o menu de contexto para trazer uma experiência unificada. Confira [este artigo](https://github.com/Microsoft/PowerBI-visuals/blob/gh-pages/tutorials/building-bar-chart/adding-context-menu-to-the-bar.md) para saber como adicionar um menu de contexto.

## <a name="commercial-logo"></a>Logotipo comercial
Esta seção descreve as especificações para adicionar logotipos comerciais em visuais do Power BI. Os logotipos comerciais não são obrigatórios. Se adicionados, eles deverão seguir estas diretrizes.

> [!NOTE]
> * Neste artigo, "logotipo comercial" refere-se a qualquer ícone corporativo comercial, conforme descrito nas imagens abaixo.
> * O logotipo comercial da Microsoft é usado neste artigo apenas como um exemplo. Use seu próprio logotipo comercial com seu visual do Power BI.

> [!IMPORTANT]
> Os logotipos comerciais são permitidos *somente no modo de edição*. Os logotipos comerciais *não podem* ser exibidos no modo de exibição.

### <a name="commercial-logo-type"></a>Tipo de logotipo comercial

Há três tipos de logotipos comerciais:
* **Logotipos:** um logotipo é composto por dois elementos bloqueados juntos, um ícone e um nome.

    ![Logotipo da Microsoft](media/guidelines-powerbi-visuals/microsoft-logo.png)

* **Símbolo:** um gráfico sem nenhum texto.

    ![Símbolo da Microsoft](media/guidelines-powerbi-visuals/microsoft-symbol.png)

* **Logotipo:** um logotipo sem um ícone, composto apenas por texto.

    ![Símbolo da Microsoft](media/guidelines-powerbi-visuals/microsoft-logotype.png)

### <a name="commercial-logo-color"></a>Cor do logotipo comercial

Ao usar um logotipo comercial, a cor dele deverá ser cinza (cor hexadecimal #C8C8C8). Não adicione efeitos como gradientes ao logotipo comercial.

* **Logotipo**

    ![Símbolo da Microsoft](media/guidelines-powerbi-visuals/grey-microsoft-logo.png)

* **Símbolo:** um gráfico sem nenhum texto.

    ![Símbolo da Microsoft](media/guidelines-powerbi-visuals/grey-microsoft-symbol.png)

* **Logotipo:** um logotipo sem um ícone, composto apenas por texto.

    ![Símbolo da Microsoft](media/guidelines-powerbi-visuals/grey-microsoft-logotype.png)

> [!TIP]
> * Se seu visual do Power BI contém um gráfico, considere adicionar uma tela de fundo branca com margens de 10 px ao seu logotipo.
> * Considere adicionar uma sombra projetada ao seu logotipo (30% de opacidade preta).

### <a name="commercial-logo-size"></a>Tamanho do logotipo comercial

Um visual do Power BI exige dois logotipos comerciais, um para blocos grandes e outro para blocos pequenos. Coloque o logotipo dentro de uma caixa delimitadora no canto superior ou inferior direito, com margens de 4 px.

A tabela a seguir descreve as considerações de tamanho dos visuais do Power BI.

|  |Visual do Power BI pequeno  |Visual do Power BI grande  |
|---------|---------|---------|
|*Largura do logotipo*    |Até 240 px         |Maior que 240 px         |
|*Altura do logotipo*     |Até 160 px         |Maior que 160 px         |
|*Tamanho da caixa delimitadora*     |40 x 15 px         |101 x 30 px         |
|*Exemplo do logotipo comercial*     |![Símbolo da Microsoft](media/guidelines-powerbi-visuals/grey-microsoft-symbol.png)         |![Logotipo da Microsoft](media/guidelines-powerbi-visuals/grey-microsoft-logo.png)         |
|*Exemplo de caixa delimitadora*    |![exemplo de logotipo pequeno](media/guidelines-powerbi-visuals/small-logo-box.png)         |![exemplo de logotipo grande](media/guidelines-powerbi-visuals/big-logo-box.png)         |
|    |         |         |

### <a name="commercial-logo-behavior"></a>Comportamento do logotipo comercial

Os logotipos comerciais são permitidos apenas no modo de edição. Quando clicado, um logotipo comercial só pode incluir a seguinte funcionalidade:

* Clicar no logotipo comercial redireciona você para o site.

* Clicar no logotipo comercial abre uma janela pop-up com informações adicionais. A janela pop-up deve ser dividida em duas seções:
    * Uma área de marketing que pode incluir o logotipo comercial, um visual e as classificações de mercado.
    * Uma área de informações que pode incluir informações e links.    


### <a name="things-to-avoid"></a>Coisas a serem evitadas

* Os logotipos comerciais não podem ser exibidos no modo de exibição.

* Um logotipo comercial animado pode exibir animação por até cinco segundos.

* Se o visual do Power BI incluir ícones informativos (i) no modo de leitura, eles deverão estar em conformidade com a cor, o tamanho e o local do logotipo comercial, conforme descrito acima.

* Evite um logotipo comercial colorido ou um preto. O logotipo comercial deve ser cinza (cor hexadecimal #C8C8C8).

    ![Logotipo colorido não autorizado](media/guidelines-powerbi-visuals/no-color-logo.png) ![Logotipo preto não autorizado](media/guidelines-powerbi-visuals/black-logo.png)

* Um logotipo comercial com efeitos como gradientes ou sombras fortes.

    ![Estilo de logotipo não autorizado](media/guidelines-powerbi-visuals/no-style-logo.png)

## <a name="best-practices"></a>Práticas recomendadas

Ao publicar um visual do Power BI, considere as seguintes recomendações a fim de proporcionar uma ótima experiência aos usuários.

### <a name="visual-landing-page"></a>Página de aterrissagem de elementos visuais

Use a página de aterrissagem para esclarecer aos usuários como eles podem usar seu visual do Power BI e em que local comprar a licença. Não inclua vídeos disparados automaticamente. Adicione apenas material que ajude a melhorar a experiência do usuário, como informações ou links sobre detalhes de compra de licença e como usar os recursos de IAP.

### <a name="license-key-and-token"></a>Token e a chave de licença

Para conveniência do usuário, adicione os campos relacionados ao token ou a chave de licença na parte superior do painel de formato.

## <a name="faq"></a>Perguntas frequentes

Para saber mais sobre visuais do Power BI, confira [Perguntas frequentes sobre os visuais do Power BI com compras adicionais](https://docs.microsoft.com/power-bi/power-bi-custom-visuals-faq#visuals-with-additional-purchases).

## <a name="next-steps"></a>Próximas etapas

Saiba como você pode publicar seu visual do Power BI no [Microsoft AppSource](office-store.md) para outras pessoas descobrirem e usarem.