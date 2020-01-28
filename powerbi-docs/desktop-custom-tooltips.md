---
title: Personalizando dicas de ferramenta no Power BI Desktop
description: Crie dicas de ferramenta personalizadas para visuais usando arrastar e soltar
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/15/2020
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 93177ac56bc2d8ecfe4b85f4ab66daef6bf0f0f3
ms.sourcegitcommit: 3d6b27e3936e451339d8c11e9af1a72c725a5668
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2020
ms.locfileid: "76160985"
---
# <a name="customize-tooltips-in-power-bi-desktop"></a>Personalizar as dicas de ferramentas no Power BI Desktop

Dicas de ferramenta são uma maneira elegante de fornecer mais informações contextuais e detalhes sobre pontos de dados em um visual. A imagem a seguir mostra uma dica de ferramenta aplicada a um gráfico no Power BI Desktop.

![Dica de ferramenta padrão](media/desktop-custom-tooltips/custom-tooltips-1.png)

Quando uma visualização é criada, a dica de ferramenta padrão exibe a categoria e o valor do ponto de dados. Há muitas instâncias em que a personalização das informações da dica de ferramenta é útil. A personalização das dicas de ferramenta fornece informações e contexto adicionais aos usuários que olham o visual. Dicas de ferramentas personalizadas permitem que você especifique os pontos de dados adicionais que são exibidos como parte da dica de ferramenta.

## <a name="how-to-customize-tooltips"></a>Como personalizar dicas de ferramentas

Para criar uma dica de ferramenta personalizada, nos **Campos** do painel **Visualizações**, arraste um campo para o bucket **Dicas de Ferramenta**, que é mostrado na imagem a seguir. Na imagem a seguir, três campos foram colocados no bucket **Dicas de Ferramenta**.

![Campos Adicionar dica de ferramenta](media/desktop-custom-tooltips/custom-tooltips-2.png)

Depois que as dicas de ferramenta são adicionadas a **Dicas de Ferramenta**, o mouse passado sobre um ponto de dados na visualização mostra os valores desses campos.

![Dica de ferramenta personalizada](media/desktop-custom-tooltips/custom-tooltips-3.png)

## <a name="customizing-tooltips-with-aggregation-or-quick-measures"></a>Personalizar dicas de ferramenta com agregação ou medidas rápidas

Você poderá personalizar ainda mais uma dica de ferramenta se selecionar uma função de agregação ou uma *medida rápida*. Selecione a seta ao lado do campo no bucket **Dicas de Ferramenta**. Selecione uma das opções disponíveis.

![Dica de ferramenta com medida rápida](media/desktop-custom-tooltips/custom-tooltips-4.png)

Há várias maneiras de personalizar dicas de ferramenta usando qualquer campo disponível no conjunto de dados, para transmitir informações e ideias rápidas para os usuários que exibem seus painéis e relatórios.
