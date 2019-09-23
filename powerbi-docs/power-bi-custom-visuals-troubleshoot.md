---
title: Solucionar problemas sobre como desenvolver visuais personalizados do Power BI
description: Este artigo aborda alguns problemas comuns que podem ser encontrados ao desenvolver ou criar um visual personalizado do Power BI.
author: sranins
ms.author: rasala
manager: kfile
ms.reviewer: maghan
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 11/06/2018
ms.openlocfilehash: cbda8cca80c32056f06788e53540d7f2d6ed972d
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "61421760"
---
# <a name="troubleshoot-power-bi-custom-visuals"></a>Solucionar problemas dos visuais personalizados do Power BI

## <a name="debug"></a>Depurar

**Comando Pbiviz não encontrado (ou erros semelhantes)**

Se você executar `pbiviz` na linha de comando do seu terminal, a tela de ajuda será exibida. Caso contrário, ele não está instalado corretamente. Verifique se no mínimo a versão 4.0 do NodeJS está instalada.

**Não é possível localizar o visual de depuração na guia Visualizações**

O visual de depuração é semelhante a um ícone de aviso dentro da guia **Visualizações**.

![Seleção de visuais](media/power-bi-custom-visuals-troubleshoot/powerbi-developer-visual-selection.png)

Se ele não estiver visível, verifique se você o habilitou nas configurações do Power BI.

> [!NOTE]
> No momento, o visual de depuração somente está disponível no serviço do Power BI, mas não no Power BI Desktop nem no aplicativo móvel. O visual empacotado ainda funcionará em todos os lugares.

**Não é possível contatar o servidor de elemento visual**

Execute o servidor de visual com o comando `pbiviz start` na linha de comando do terminal na raiz do projeto de visual. Se o servidor não estiver em execução, provavelmente os certificados SSL não foram instalados corretamente.

Fique à vontade para contatar a equipe de suporte de visuais personalizados: *pbicvsupport@microsoft.com*  caso tenha perguntas, comentários ou problemas.

## <a name="next-steps"></a>Próximas etapas

Para saber mais, acesse [Frequently asked questions about Power BI custom visuals](power-bi-custom-visuals-faq.md#organizational-custom-visuals) (Perguntas frequentes sobre os visuais personalizados do Power BI).
