---
title: Desabilitar atualização em segundo plano do Power Query
description: Diretrizes sobre quando desabilitar a atualização em segundo plano do Power Query.
author: peter-myers
manager: asaxton
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 09/26/2019
ms.author: v-pemyer
ms.openlocfilehash: 59cb62a9186da03a265fc3a8711d7275c3772af3
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/05/2020
ms.locfileid: "75623051"
---
# <a name="disable-power-query-background-refresh"></a>Desabilitar atualização em segundo plano do Power Query

Este artigo destina-se a modeladores de dados de importação que trabalham com Power BI Desktop.

Por padrão, quando Power Query importa dados, ele também armazena em cache até 1.000 linhas de dados de visualização para cada consulta. Os dados de visualização ajudam a apresentar uma visualização rápida dos dados de origem e dos resultados da transformação para cada etapa de suas consultas. Eles são armazenados separadamente no disco e não dentro do arquivo do Power BI Desktop.

No entanto, quando o arquivo do Power BI Desktop contém muitas consultas, a recuperação e o armazenamento de dados de visualização podem estender o tempo necessário para concluir uma atualização.

## <a name="recommendation"></a>Recomendação

Você obterá uma atualização mais rápida definindo o arquivo do Power BI Desktop para atualizar o cache de visualização _em segundo plano_. No Power BI Desktop, você habilita essa opção selecionando _Arquivo > Opções e Configurações > Opções_ e, em seguida, selecionando a página _Carregamento de Dados_. Em seguida, você pode ativar a opção **Permitir que a visualização de dados seja baixada em segundo plano**. Observe que essa opção só pode ser definida para o arquivo atual.

![Opções de dados em segundo plano do Power BI Desktop](media/power-query-background-refresh/power-query-options-background-data.png)

Habilitar a atualização em segundo plano pode fazer com que os dados de visualização fiquem desatualizados. Se isso ocorrer, o Editor do Power Query o notificará com o seguinte aviso:

![Aviso do Editor do Power Query sobre dados de visualização antigos](media/power-query-background-refresh/power-query-preview-data-old.png)

Sempre é possível atualizar o cache de visualização. Você pode atualizá-lo para uma única consulta ou para todas as consultas, usando o comando **Atualizar Visualização**. Você o encontrará na faixa de opções **Página Inicial** da janela do Editor do Power Query.

![Comandos do Editor do Power Query para atualizar dados de visualização](media/power-query-background-refresh/power-query-refresh-preview-data.png)

## <a name="next-steps"></a>Próximas etapas

Para obter mais informações relacionadas a este artigo, confira os seguintes recursos:

- [Documentação do Power Query](/power-query/)
- Perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
