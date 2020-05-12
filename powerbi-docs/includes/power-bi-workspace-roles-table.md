---
title: Funções de workspace do Power BI
description: Tabela de funções de workspace do Power BI
services: powerbi
author: maggiesMSFT
ms.service: powerbi
ms.topic: include
ms.date: 04/23/2020
ms.author: maggies
ms.custom: include file
ms.openlocfilehash: 5ed3a65f1ef65640c76ada765931a85714aad3af
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82781330"
---
Estas são as capacidades das quatro funções: administradores, membros, colaboradores e visualizadores. Todos esses recursos, exceto exibição e interação, exigem uma licença Power BI Pro.

|Funcionalidade   | Administrador  | Membro  | Colaborador  | Visualizador |
|---|---|---|---|---|
| Atualizar e excluir o workspace.  | X  |   |   |   | 
| Adicionar/remover pessoas, incluindo outros administradores.  | X  |   |   |   |
| Adicionar membros ou outras pessoas com permissões inferiores.  |  X | X  |   |   |
| Publicar e atualizar um aplicativo. |  X | X  |   |   |
| Compartilhar um item ou um aplicativo.<sup>1</sup> |  X | X  |   |   |
| Permitir que outras pessoas compartilhem itens novamente.<sup>1</sup> |  X | X  |   |   |
| Destacar aplicativos na página inicial de colegas |  X | X  |   |   |
| Destacar dashboards e relatórios na página inicial de colegas |  X | X  | X |   |
| Criar, editar e excluir conteúdo no workspace.  |  X | X  | X  |   |
| Publicar relatórios no workspace, excluir conteúdo.  |  X | X  | X  |   |
| Criar um relatório em outro workspace com base em um conjunto de dados neste workspace.<sup>1</sup> |  X | X  | X  |   |
| Copiar um relatório.<sup>2</sup> | X | X | X |  |
| Agendar atualizações de dados por meio do gateway local.<sup>3</sup> | X | X | X |  |
| Modificar configurações de conexão do gateway.<sup>3</sup> | X | X | X |  |
| Exibir e interagir com um item.<sup>4</sup> |  X | X  | X  | X  |
| Ler dados armazenados em fluxo de trabalho do workspace | X | X | X | X |

1. Colaboradores e Espectadores podem compartilhar itens em um workspace quando têm permissões para Recompartilhar.
2. Para copiar um relatório e criar um relatório em outro workspace com base em um conjunto de dados desse workspace, você precisará ter a permissão Criar no conjunto de dados. Para os conjuntos de dados desse workspace, as pessoas com as funções Administrador, Membro e Colaborador têm a permissão Criar por meio das respectivas funções de workspace.
3. Tenha em mente que você também precisa de permissões no gateway. Essas permissões são gerenciadas em outro lugar, independentemente das permissões e das funções do workspace. Confira [Gerenciar um gateway local](https://docs.microsoft.com/data-integration/gateway/service-gateway-manage) para obter detalhes.
4. Mesmo se não tiver uma licença Power BI Pro, você poderá exibir itens e interagir com eles no serviço do Power BI se os itens estiverem em um workspace em uma capacidade Premium.

