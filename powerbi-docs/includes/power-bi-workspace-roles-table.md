---
title: Funções de workspace do Power BI
description: Tabela de funções de workspace do Power BI
services: powerbi
author: maggiesMSFT
ms.service: powerbi
ms.topic: include
ms.date: 06/23/2020
ms.author: maggies
ms.custom: include file
ms.openlocfilehash: 9ddf9df0feaed2a2a0177d11e9b36f34135801c6
ms.sourcegitcommit: caf60154a092f88617eb177bc34fb784f2365962
ms.contentlocale: pt-BR
ms.lasthandoff: 06/25/2020
ms.locfileid: "85365246"
---
|Funcionalidade   | Administrador  | Membro  | Colaborador  | Visualizador |
|---|---|---|---|---|
| Atualizar e excluir o workspace.  |  |   |   |   | 
| Adicionar/remover pessoas, incluindo outros administradores.  |  ![Marca de seleção Sim](media/power-bi-workspace-roles-table/green-checkmark.png) |   |   |   |
| Permitir que os colaboradores atualizem o aplicativo deste workspace  |  ![Marca de seleção Sim](media/power-bi-workspace-roles-table/green-checkmark.png) |   |   |   |
| Adicionar membros ou outras pessoas com permissões inferiores.  |  ![Marca de seleção Sim](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Marca de seleção Sim](media/power-bi-workspace-roles-table/green-checkmark.png)  |   |   |
| Publicar e alterar permissões para um aplicativo |  ![Marca de seleção Sim](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Marca de seleção Sim](media/power-bi-workspace-roles-table/green-checkmark.png)  |   |   |
| Atualizar um aplicativo. |  ![Marca de seleção Sim](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Marca de seleção Sim](media/power-bi-workspace-roles-table/green-checkmark.png)  |  Se permitido <sup>1</sup>  |   |
| Compartilhar um item ou aplicativo.<sup>2</sup> |  ![Marca de seleção Sim](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Marca de seleção Sim](media/power-bi-workspace-roles-table/green-checkmark.png)  |   |   |
| Permitir que outras pessoas compartilhem itens novamente.<sup>2</sup> |  ![Marca de seleção Sim](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Marca de seleção Sim](media/power-bi-workspace-roles-table/green-checkmark.png)  |   |   |
| Destacar aplicativos na página inicial de colegas |  ![Marca de seleção Sim](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Marca de seleção Sim](media/power-bi-workspace-roles-table/green-checkmark.png)  |   |   |
| Destacar dashboards e relatórios na página inicial de colegas |  ![Marca de seleção Sim](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Marca de seleção Sim](media/power-bi-workspace-roles-table/green-checkmark.png)  | ![Marca de seleção Sim](media/power-bi-workspace-roles-table/green-checkmark.png) |   |
| Criar, editar e excluir conteúdo no workspace.  |  ![Marca de seleção Sim](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Marca de seleção Sim](media/power-bi-workspace-roles-table/green-checkmark.png)  | ![Marca de seleção Sim](media/power-bi-workspace-roles-table/green-checkmark.png)  |   |
| Publicar relatórios no workspace, excluir conteúdo.  |  ![Marca de seleção Sim](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Marca de seleção Sim](media/power-bi-workspace-roles-table/green-checkmark.png)  | ![Marca de seleção Sim](media/power-bi-workspace-roles-table/green-checkmark.png)  |   |
| Criar um relatório em outro workspace com base em um conjunto de dados nesse workspace.<sup>2</sup> |  ![Marca de seleção Sim](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Marca de seleção Sim](media/power-bi-workspace-roles-table/green-checkmark.png)  | ![Marca de seleção Sim](media/power-bi-workspace-roles-table/green-checkmark.png)  |   |
| Copiar um relatório.<sup>3</sup> | ![Marca de seleção Sim](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Marca de seleção Sim](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Marca de seleção Sim](media/power-bi-workspace-roles-table/green-checkmark.png) |  |
| Agendar atualizações de dados por meio do gateway local.<sup>4</sup> | ![Marca de seleção Sim](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Marca de seleção Sim](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Marca de seleção Sim](media/power-bi-workspace-roles-table/green-checkmark.png) |  |
| Modificar configurações de conexão do gateway.<sup>4</sup> | ![Marca de seleção Sim](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Marca de seleção Sim](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Marca de seleção Sim](media/power-bi-workspace-roles-table/green-checkmark.png) |  |
| Exibir um item e interagir com ele.<sup>5</sup> |  ![Marca de seleção Sim](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Marca de seleção Sim](media/power-bi-workspace-roles-table/green-checkmark.png)  | ![Marca de seleção Sim](media/power-bi-workspace-roles-table/green-checkmark.png)  | ![Marca de seleção Sim](media/power-bi-workspace-roles-table/green-checkmark.png)  |
| Ler dados armazenados em fluxo de trabalho do workspace | ![Marca de seleção Sim](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Marca de seleção Sim](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Marca de seleção Sim](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Marca de seleção Sim](media/power-bi-workspace-roles-table/green-checkmark.png) |

<sup>1</sup> Os Colaboradores poderão atualizar os metadados do aplicativo, mas não publicar um novo aplicativo nem alterar quem tem permissão para o aplicativo, se o [administrador do workspace delegar essa permissão aos Colaboradores](../collaborate-share/service-create-the-new-workspaces.md#security-settings).

<sup>2</sup> Colaboradores e Espectadores também poderão compartilhar itens em um workspace quando tiverem permissões para Compartilhar Novamente.

<sup>3</sup> Para copiar um relatório e criar um relatório em outro workspace com base em um conjunto de dados desse workspace, você precisará da [permissão Criar no conjunto de dados](../connect-data/service-datasets-build-permissions.md). Para os conjuntos de dados desse workspace, as pessoas com as funções Administrador, Membro e Colaborador terão automaticamente a permissão Criar por meio das respectivas funções de workspace.

<sup>4</sup> Tenha em mente que você também precisa de permissões no gateway. Essas permissões são gerenciadas em outro lugar, independentemente das permissões e das funções do workspace. Confira [Gerenciar um gateway local](https://docs.microsoft.com/data-integration/gateway/service-gateway-manage) para obter detalhes.

<sup>5</sup> Mesmo se não tiver uma licença Power BI Pro, você poderá exibir itens e interagir com eles no serviço do Power BI se os itens estiverem em um workspace em uma capacidade Premium.
