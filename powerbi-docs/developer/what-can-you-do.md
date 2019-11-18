---
title: O que os desenvolvedores podem fazer com o Power BI?
description: O Power BI oferece uma ampla variedade de opções para desenvolvedores. Isso vai desde a inserção até elementos visuais personalizados e conjuntos de dados de streaming.
author: rkarlin
ms.author: rkarlin
ms.topic: overview
ms.service: powerbi
ms.subservice: powerbi-developer
ms.custom: mvc
ms.date: 03/15/2019
ms.openlocfilehash: 9105edd88e83f17f4d6e75a7e45dc123a6789713
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/09/2019
ms.locfileid: "73875683"
---
# <a name="what-can-developers-do-with-power-bi"></a>O que os desenvolvedores podem fazer com o Power BI?

Os desenvolvedores têm diferentes opções ao tentar incluir o conteúdo do Power BI em aplicativos. Como desenvolvedor, você pode usar opções que incluem **inserção com o Power BI**, **elementos visuais personalizados** e **envio de dados por push para o Power BI**.

## <a name="embedding-power-bi-content"></a>Inserção de conteúdo do Power BI

O serviço do Power BI (SaaS) e o serviço do Power BI Embedded no Azure (PaaS) têm APIs para inserir seus painéis e seus relatórios. Esse recurso significa que você pode acessar os recursos mais recentes do Power BI, tais como dashboards, gateways e workspaces ao inserir seu conteúdo.

É possível acessar a [Ferramenta de configuração de inserção](https://aka.ms/embedsetup) para começar rapidamente e baixar um aplicativo de exemplo.

Escolha a solução certa para você:

* A [inserção para clientes](embedding.md#embedding-for-your-customers) fornece a capacidade de inserir os dashboards e relatórios para usuários que não têm uma conta do Power BI. Execute a solução [Inserir para clientes](https://aka.ms/embedsetup/AppOwnsData).

* A [inserção para a organização](embedding.md#embedding-for-your-organization) permite que você estenda o serviço do Power BI. Execute a solução [Inserir para a organização](https://aka.ms/embedsetup/UserOwnsData).

![Exemplo de PBIE](media/what-can-you-do/what-can-you-do-02.png)

Para saber mais sobre inserção com o Power BI, consulte [Inserção com o Power BI](embedding.md).

## <a name="developing-custom-visuals"></a>Desenvolvimento de elementos visuais personalizados

Você pode usar elementos visuais personalizados com o Power BI para criar um tipo exclusivo de visual que seja adequado para você ou sua empresa. Muitas vezes, esses elementos visuais personalizados são criados por desenvolvedores. Eles são criados quando a variedade de elementos visuais inclusos com o Power BI não atende às suas necessidades.

Os elementos visuais personalizados permitem que você crie seus elementos visuais para uso em relatórios do Power BI. Os visuais personalizados são gravados em TypeScript, que é um superconjunto de JavaScript. O TypeScript oferece suporte a alguns recursos avançados e acesso antecipado à funcionalidade do ES6/ES7. A aplicação de estilo do visual é realizada usando CSS (folhas de estilos em cascata). Para facilitar, usamos o pré-compilador Less que é compatível com alguns recursos avançados, como aninhamento, variáveis, condições, loops e outros recursos. Se não quiser usar esses recursos, escreva o CSS simples no arquivo LESS.

![Exemplo de CV](media/what-can-you-do/powerbi-custom-visual-store.png)

Para começar a aprender mais sobre o desenvolvimento de visuais personalizados, confira [Developing a Power BI custom visual](visuals/custom-visual-develop-tutorial.md) (Desenvolvimento de um visual personalizado do Power BI).

## <a name="using-api-automation"></a>Uso da automação de API

O Power BI exibe painéis interativos e que podem ser criados e atualizados por meio de várias fontes de dados diferentes em tempo real. Ao usar qualquer linguagem de programação que dá suporte a chamadas REST, você pode criar aplicativos que se integram a um dashboard do Power BI em tempo real. Você também pode integrar blocos do Power BI e relatórios a aplicativos.

Os desenvolvedores também podem criar suas próprias visualizações de dados, que podem ser usadas em dashboards e relatórios interativos.

![Exemplo de envio de dados por push](media/what-can-you-do/powerbi-push-data.png)

Para ver algumas das coisas que você pode fazer com as APIs do Power BI, consulte [O que um desenvolvedor pode fazer com as APIs do Power BI](overview-of-power-bi-rest-api.md)?

## <a name="next-steps"></a>Próximas etapas

[Inserindo com o Power BI](embedding.md)  

[Desenvolvimento de um visual personalizado do Power BI](https://microsoft.github.io/PowerBI-visuals/docs/step-by-step-lab/developing-a-power-bi-custom-visual/)

[O que os desenvolvedores podem fazer com a API do Power BI?](overview-of-power-bi-rest-api.md)

[Central de Desenvolvedores do Power BI](https://powerbi.microsoft.com/developers/)