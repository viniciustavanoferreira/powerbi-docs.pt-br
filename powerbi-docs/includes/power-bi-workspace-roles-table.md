---
title: Funções de workspace do Power BI
description: Tabela de funções de workspace do Power BI
services: powerbi
author: maggiesMSFT
ms.service: powerbi
ms.topic: include
ms.date: 05/26/2020
ms.author: maggies
ms.custom: include file
ms.openlocfilehash: 708599eb3f39d4c627a11753cb964d6425f75640
ms.sourcegitcommit: a7b142685738a2f26ae0a5fa08f894f9ff03557b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/28/2020
ms.locfileid: "84120373"
---
|Funcionalidade   | Administrador  | Membro  | Colaborador  | Visualizador |
|---|---|---|---|---|
| Atualizar e excluir o workspace.  |  |   |   |   | 
| Adicionar/remover pessoas, incluindo outros administradores.  |  ![Marca de seleção Sim](media/power-bi-workspace-roles-table/green-checkmark.png) |   |   |   |
| Adicionar membros ou outras pessoas com permissões inferiores.  |  ![Marca de seleção Sim](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Marca de seleção Sim](media/power-bi-workspace-roles-table/green-checkmark.png)  |   |   |
| Publicar e atualizar um aplicativo. |  ![Marca de seleção Sim](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Marca de seleção Sim](media/power-bi-workspace-roles-table/green-checkmark.png)  |   |   |
| Compartilhar um item ou um aplicativo.<sup>1</sup> |  ![Marca de seleção Sim](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Marca de seleção Sim](media/power-bi-workspace-roles-table/green-checkmark.png)  |   |   |
| Permitir que outras pessoas compartilhem itens novamente.<sup>1</sup> |  ![Marca de seleção Sim](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Marca de seleção Sim](media/power-bi-workspace-roles-table/green-checkmark.png)  |   |   |
| Destacar aplicativos na página inicial de colegas |  ![Marca de seleção Sim](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Marca de seleção Sim](media/power-bi-workspace-roles-table/green-checkmark.png)  |   |   |
| Destacar dashboards e relatórios na página inicial de colegas |  ![Marca de seleção Sim](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Marca de seleção Sim](media/power-bi-workspace-roles-table/green-checkmark.png)  | ![Marca de seleção Sim](media/power-bi-workspace-roles-table/green-checkmark.png) |   |
| Criar, editar e excluir conteúdo no workspace.  |  ![Marca de seleção Sim](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Marca de seleção Sim](media/power-bi-workspace-roles-table/green-checkmark.png)  | ![Marca de seleção Sim](media/power-bi-workspace-roles-table/green-checkmark.png)  |   |
| Publicar relatórios no workspace, excluir conteúdo.  |  ![Marca de seleção Sim](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Marca de seleção Sim](media/power-bi-workspace-roles-table/green-checkmark.png)  | ![Marca de seleção Sim](media/power-bi-workspace-roles-table/green-checkmark.png)  |   |
| Criar um relatório em outro workspace com base em um conjunto de dados nesse workspace.<sup>2</sup> |  ![Marca de seleção Sim](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Marca de seleção Sim](media/power-bi-workspace-roles-table/green-checkmark.png)  | ![Marca de seleção Sim](media/power-bi-workspace-roles-table/green-checkmark.png)  |   |
| Copiar um relatório.<sup>2</sup> | ![Marca de seleção Sim](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Marca de seleção Sim](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Marca de seleção Sim](media/power-bi-workspace-roles-table/green-checkmark.png) |  |
| Agendar atualizações de dados por meio do gateway local.<sup>3</sup> | ![Marca de seleção Sim](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Marca de seleção Sim](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Marca de seleção Sim](media/power-bi-workspace-roles-table/green-checkmark.png) |  |
| Modificar configurações de conexão do gateway.<sup>3</sup> | ![Marca de seleção Sim](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Marca de seleção Sim](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Marca de seleção Sim](media/power-bi-workspace-roles-table/green-checkmark.png) |  |
| Exibir e interagir com um item.<sup>4</sup> |  ![Marca de seleção Sim](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Marca de seleção Sim](media/power-bi-workspace-roles-table/green-checkmark.png)  | ![Marca de seleção Sim](media/power-bi-workspace-roles-table/green-checkmark.png)  | ![Marca de seleção Sim](media/power-bi-workspace-roles-table/green-checkmark.png)  |
| Ler dados armazenados em fluxo de trabalho do workspace | ![Marca de seleção Sim](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Marca de seleção Sim](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Marca de seleção Sim](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Marca de seleção Sim](media/power-bi-workspace-roles-table/green-checkmark.png) |

<sup>1</sup> Colaboradores e Visualizadores também poderão compartilhar itens em um workspace quando tiverem permissões para Compartilhar novamente.

<sup>2</sup> Para copiar um relatório e criar um relatório em outro workspace com base em um conjunto de dados desse workspace, você precisará ter a [permissão Criar no conjunto de dados](../connect-data/service-datasets-build-permissions.md). Para os conjuntos de dados desse workspace, as pessoas com as funções Administrador, Membro e Colaborador terão automaticamente a permissão Criar por meio das respectivas funções de workspace.

<sup>3</sup> Tenha em mente que você também precisa de permissões no gateway. Essas permissões são gerenciadas em outro lugar, independentemente das permissões e das funções do workspace. Confira [Gerenciar um gateway local](https://docs.microsoft.com/data-integration/gateway/service-gateway-manage) para obter detalhes.

<sup>4</sup> Mesmo se não tiver uma licença Power BI Pro, você poderá exibir itens e interagir com eles no serviço do Power BI se os itens estiverem em um workspace em uma capacidade Premium.

