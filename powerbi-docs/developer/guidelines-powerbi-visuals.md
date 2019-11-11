---
title: Diretrizes para visuais do Power BI
description: Saiba como você pode publicar seu visual personalizado no AppSource para que outros possam descobrir e usá-lo por meio de uma compra.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 07/16/2019
ms.openlocfilehash: 84c873c925c7e733c70b309d5cc2476dff2e553b
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/09/2019
ms.locfileid: "73863946"
---
# <a name="guidelines-for-power-bi-visuals"></a>Diretrizes para visuais do Power BI
Antes de [publicar](https://docs.microsoft.com/power-bi/developer/office-store) seu visual no AppSource para que outras pessoas descubram e usem, verifique se você seguiu as diretrizes para criar uma experiência excelente para seus usuários. 

## <a name="context-menu"></a>Menu de contexto
O menu de contexto é o menu de clique com o botão direito do mouse que é exibido quando o usuário passa o mouse sobre um visual.
Todos os visuais do Power BI devem habilitar o menu de contexto para trazer uma experiência unificada. Confira [este artigo](https://github.com/Microsoft/PowerBI-visuals/blob/gh-pages/tutorials/building-bar-chart/adding-context-menu-to-the-bar.md) para saber como adicionar um menu de contexto.


## <a name="logo-guidelines"></a>Diretrizes de logotipo
> [!NOTE]
> O logotipo do Word neste artigo refere-se a qualquer ícone comercial da empresa, conforme descrito nas imagens abaixo. 

Esta seção descreve as especificações para adicionar logotipos em visuais do Power BI. Os logotipos não são obrigatórios. Se adicionados, eles deverão seguir estas diretrizes. 

> [!IMPORTANT]
> Os logotipos são permitidos *somente no modo de edição*. Logotipos *não podem* ser exibidos no modo de exibição.


![Definições](media/guidelines-powerbi-visuals/definitions.png)

![Coisas a serem consideradas](media/guidelines-powerbi-visuals/things-to-keep-in-mind.png)

![Coisas a serem evitadas](media/guidelines-powerbi-visuals/things-to-avoid.png)

![Tamanho e formato](media/guidelines-powerbi-visuals/size-and-format.png)

![Margens e dimensionamento](media/guidelines-powerbi-visuals/margins-and-sizes.png)

![Modo de edição](media/guidelines-powerbi-visuals/logos-in-edit-mode.png)


Os ícones informativos, caso haja, no modo de leitura, devem estar em conformidade com a cor, o tamanho e a localização dos logotipos acima.

## <a name="guidelines-for-power-bi-visuals-with-additional-purchases"></a>Diretrizes para visuais do Power BI com compras adicionais

Até recentemente, o Marketplace (AppSource) aceitava apenas os visuais gratuitos do Power BI. Essa política foi alterada (em dezembro de 2018) para que você também possa enviar os visuais para o AppSource com uma etiqueta de preço "uma compra adicional pode ser necessária". 

Os visuais "compra adicional pode ser necessária" são semelhantes a suplementos de IAP (compra no aplicativo) na Office Store. Os desenvolvedores também podem enviar esses visuais para a certificação após a equipe do AppSource aprova-los e depois de verificar se eles estão em conformidade com os requisitos de certificação. Para saber mais sobre os requisitos, confira [Visuais do Power BI certificados](../power-bi-custom-visuals-certified.md).

> [!NOTE]
> Para o visual ser certificado, ele não deverá acessar serviços ou recursos externos.

>[!IMPORTANT]  
> Se você atualizar seu visual de gratuito para "Uma compra adicional pode ser necessária", os usuários precisarão receber o mesmo nível de funcionalidade gratuita que tinham antes da atualização. Você pode adicionar recursos avançados opcionais pagos, além dos recursos gratuitos existentes. Recomendamos que você envie os visuais de IAP com os recursos avançados como novos visuais e não atualize os existentes gratuitos.

## <a name="what-changed-in-the-submission-process"></a>O que mudou no processo de envio?

Os desenvolvedores carregam seus visuais de IAP para o AppSource por meio do Painel do Vendedor, como eles faziam para visuais gratuitos. Para indicar que o visual enviado tem recursos de IAP, os desenvolvedores devem escrever nas notas do Painel do vendedor: "Visual com compra no aplicativo." Além disso, os desenvolvedores precisam fornecer um token ou chave de licença para que a equipe de validação poder validar os recursos de IAP. Assim que o visual tiver sido validado e aprovado, a listagem do AppSource para os visuais do IAP diz "Compra adicional pode ser necessária" nas opções de preços.

## <a name="what-is-a-power-bi-visual-with-iap-features"></a>O que é um visual do Power BI com recursos de IAP?

Um visual de IAP é um visual *grátis* que oferece *recursos gratuitos*. Ele também possui alguns recursos avançados para os quais podem ser aplicados custos extras para operá-los. Na descrição do visual, os desenvolvedores devem notificar os usuários sobre os recursos que exigem compras adicionais para operar. Atualmente, a Microsoft não fornece APIs nativas compatíveis com a compra de aplicativos e suplementos.

Os desenvolvedores podem usar qualquer sistema de pagamento de terceiros para essas compras. Para obter mais informações, confira [nossa política de loja](https://docs.microsoft.com/office/dev/store/validation-policies#2-apps-or-add-ins-can-display-certain-ads).

> [!NOTE]
> As marcas d'água não são permitidas nos recursos gratuitos de visuais gratuitos. As marcas d'água podem ser usadas somente em recursos pagos que são usados sem uma licença válida. É recomendável exibir uma janela pop-up com todas as informações relacionadas à licença, se os recursos pagos avançados são usados sem uma licença válida.  


## <a name="best-practices"></a>Práticas recomendadas

### <a name="visual-landing-page"></a>Página de aterrissagem de elementos visuais

Use a página de aterrissagem para esclarecer aos usuários como eles podem usar seu visual e em que local comprar a licença. Não inclua vídeos disparados automaticamente. Adicione apenas material que ajude a melhorar a experiência do usuário, como informações ou links sobre detalhes de compra de licença e como usar os recursos de IAP.

### <a name="license-key-and-token"></a>Token e a chave de licença

Para conveniência do usuário, adicione os campos relacionados ao token ou a chave de licença na parte superior do painel de formato.

## <a name="faq"></a>PERGUNTAS FREQUENTES

Para saber mais sobre visuais, acesse [Perguntas frequentes sobre os visuais com compras adicionais](https://docs.microsoft.com/power-bi/power-bi-custom-visuals-faq#visuals-with-additional-purchases).

## <a name="next-steps"></a>Próximas etapas

Saiba como você pode publicar seu visual personalizado no [AppSource](office-store.md) para que outros possam descobrir e usá-lo.
