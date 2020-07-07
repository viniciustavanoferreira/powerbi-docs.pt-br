---
title: Copiar e colar uma visualização no serviço do Power BI
description: Copiar e colar uma visualização no serviço do Power BI
author: mihart
ms.reviewer: maggie tsang
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: how-to
ms.date: 06/25/2020
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 4ff249002248b438b189b59defffd3c61d981b70
ms.sourcegitcommit: 46a340937d9f01c6daba86a4ab178743858722ec
ms.contentlocale: pt-BR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85398052"
---
# <a name="copy-a-visual-as-an-image-to-your-clipboard"></a>Copiar um visual como uma imagem para a área de transferência

[!INCLUDE[consumer-appliesto-yyyn](../includes/consumer-appliesto-yyyn.md)]

Você já quis compartilhar uma imagem de um relatório ou dashboard do Power BI? Agora você pode copiar o visual e colá-lo em qualquer outro aplicativo compatível com colagem. 

Quando você copia uma imagem estática de um Visual, obtém uma cópia do visual, junto com os metadados. Isso inclui:
* link de volta para o relatório ou dashboard do Power BI
* título do relatório ou dashboard
* observe se a imagem contém informações confidenciais
* carimbo de data/hora da última atualização
* filtros aplicados ao visual

### <a name="copy-from-a-dashboard-tile"></a>Copiar de um bloco do dashboard

1. Navegue até o dashboard do qual você deseja copiar.

2. No canto superior direito do visual, selecione **Mais ações(...)** e escolha **Copiar visual como imagem**. 

    ![Ícone Copiar visual como imagem exibido](media/end-user-copy-paste/power-bi-copy-dashboard.png)

3. Quando a caixa de diálogo **Seu visual está pronto para copiar** é exibida, selecione **Copiar para a área de transferência**.

    ![caixa de diálogo com a opção Copiar para área de transferência](media//end-user-copy-paste/power-bi-copied.png)

4. Depois que o visual for copiado, cole-o em outro aplicativo usando **Ctrl+V** ou clique com o botão direito do mouse > Colar. Na captura de tela abaixo, colamos o visual no Microsoft Word. 

    ![visual colado no Outlook](media//end-user-copy-paste/power-bi-paste-word.png)

### <a name="copy-from-a-report-visual"></a>Copiar de um visual de relatório 

1. Navegue até o relatório do qual você deseja copiar.

2. No canto superior direito do visual, selecione o ícone para **Copiar visual como imagem**. 

    ![Ícone Copiar visual como imagem exibido](media/end-user-copy-paste/power-bi-copy-icon.png)

3. Quando a caixa de diálogo **Seu visual está pronto para copiar** é exibida, selecione **Copiar para a área de transferência**.

    ![caixa de diálogo com a opção Copiar para área de transferência](media//end-user-copy-paste/power-bi-copied.png)


4. Depois que o visual for copiado, cole-o em outro aplicativo usando **Ctrl+V** ou clique com o botão direito do mouse > Colar. Na captura de tela abaixo, colamos o visual em um email.

    ![visual colado no Outlook](media//end-user-copy-paste/power-bi-copy-email.png)

5. Se houver um rótulo de confidencialidade de dados aplicado ao relatório, você receberá um aviso quando selecionar o ícone de cópia.  

    ![aviso de dados confidenciais](media//end-user-copy-paste/power-bi-sensitive.png)

    Além disso, um rótulo de confidencialidade será adicionado aos metadados abaixo do visual colado. 

    ![visual com rótulo de informações confidenciais](media//end-user-copy-paste/power-bi-confidential.png)



## <a name="considerations-and-troubleshooting"></a>Considerações e solução de problemas

   ![cópia não disponível](media//end-user-copy-paste/power-bi-copy-grey.png)


P: Por que o ícone de Cópia está desabilitado em um visual?    
R: Atualmente, damos suporte a visuais nativos do Power BI e visuais personalizados certificados. A compatibilidade é limitada com determinados elementos visuais, incluindo: 
- ESRI e outros visuais de mapa 
- Visuais de Python 
- Visuais do R 
- PowerApps    

R: A capacidade de copiar um visual pode ser desativada pelo seu departamento de TI ou pelo administrador do Power BI.


P: Por que meu visual não está sendo colado corretamente?    
R: Há limitações para visuais personalizados e animados. 



## <a name="next-steps"></a>Próximas etapas
Mais sobre [Visualizações nos relatórios do Power BI](end-user-visual-type.md)

Mais perguntas? [Experimente a Comunidade do Power BI](https://community.powerbi.com/)

