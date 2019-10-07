---
title: Elementos visuais de organização no Power BI
description: Usar, gerenciar e criar visuais organizacionais no Power BI
author: KesemSharabi
ms.author: kesharab
manager: rkarlin
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 12/11/2018
LocalizationGroup: Visualizations
ms.openlocfilehash: b10a856a98c892b32e873bd01105c52777d2b413
ms.sourcegitcommit: b7a9862b6da940ddebe61bc945a353f91cd0e4bd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/04/2019
ms.locfileid: "71946181"
---
# <a name="organizational-visuals-in-power-bi"></a>Elementos visuais de organização no Power BI

Você pode usar visuais no Power BI para criar um tipo exclusivo de visual que seja adequado para você. Os visuais do Power BI são criados por desenvolvedores e frequentemente são criados quando a variedade de visuais que estão incluídos no Power BI não atende a sua necessidade.

Em algumas organizações, os visuais do Power BI são ainda mais importantes. Eles podem ser necessários para transmitir dados específicos ou insights exclusivos para a organização, podem ter requisitos de dados especiais ou dar destaque a métodos particulares de negócios. Essas organizações precisam desenvolver visuais do Power BI, compartilhá-los em toda a organização e garantir que eles sejam mantidos corretamente. Os visuais do Power BI permitem que as organizações façam exatamente isso.

A imagem a seguir mostra o processo pelo qual os visuais do Power BI da organização fluem do administrador, passando pelo desenvolvimento e manutenção, para ao fim chegar ao analista de dados.

![Imagem do visual personalizado](media/power-bi-custom-visuals-organizational/custom-visual-org-01.jpg)

Os elementos visuais organizacionais são implantados e gerenciados pelo administrador do Power BI no portal de administração. Uma vez implantados no repositório organizacional, os usuários da organização podem facilmente descobrir e importar os visuais do Power BI da organização em seus relatórios diretamente do Power BI Desktop.

Para saber mais sobre como usar visuais do Power BI da organização nos relatórios que você criou, confira o seguinte artigo: [Saber mais sobre como importar elementos visuais organizacionais em seus relatórios](power-bi-custom-visuals.md).

## <a name="administer-organizational-power-bi-visuals"></a>Administração de visuais do Power BI da organização

Para saber mais sobre como administrar, implantar e gerenciar visuais do Power BI na sua organização, confira o seguinte artigo: [Saiba mais sobre a implantação e o gerenciamento de visuais do Power BI na organização](https://go.microsoft.com/fwlink/?linkid=866790).

> [!WARNING]
> Um elemento visual personalizado pode conter código com riscos de segurança ou privacidade. É importante confiar no autor e na origem de qualquer elemento visual personalizado antes de implantá-lo no repositório da organização.

## <a name="considerations-and-limitations"></a>Considerações e limitações

Há várias considerações e limitações das quais você precisa estar ciente.

Administrador:

* Não há suporte para visuais do Power BI herdados (como visuais do Power BI que não são criados com base nas novas APIs com controle de versão)

* Se um elemento visual personalizado é excluído do repositório, os relatórios existentes que usam o elemento visual excluído param de renderizar. A operação de exclusão do repositório não é reversível. Para desabilitar temporariamente um visual personalizado, use o recurso "Desabilitar".

Usuário final:

* Os visuais do Power BI da organização são visuais privados importados do repositório da organização. Como todo visual privado, eles não podem ser [exportados para o PowerPoint](https://docs.microsoft.com/power-bi/consumer/end-user-powerpoint) nem exibidos em emails recebidos quando um usuário [assina as páginas do relatório](https://docs.microsoft.com/power-bi/consumer/end-user-subscribe). Apenas [visuais do Power BI certificados](https://docs.microsoft.com/power-bi/power-bi-custom-visuals-certified) importados diretamente do marketplace oferecem suporte a esses recursos.

* Os elementos visuais do Visio, do PowerApps, do Map box e do GlobeMap do marketplace do AppSource não serão renderizados se forem implantados por meio do repositório da organização.

## <a name="troubleshoot"></a>Solucionar problemas

Para saber mais sobre a solução de problemas, acesse [Solução de problemas com visuais do Power BI](power-bi-custom-visuals-troubleshoot.md).

## <a name="faq"></a>PERGUNTAS FREQUENTES

Para saber mais e solucionar suas dúvidas, acesse [Perguntas frequentes sobre os visuais do Power BI](power-bi-custom-visuals-faq.md#organizational-visuals).

Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/).
