---
title: Diretrizes da solução de problemas de relação
description: Diretrizes da solução de problemas de relação de modelo.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 03/02/2020
ms.author: v-pemyer
ms.openlocfilehash: e2854d82d858bb1963b691d32d561c7b3bbfc11a
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/05/2020
ms.locfileid: "78263635"
---
# <a name="relationship-troubleshooting-guidance"></a>Diretrizes da solução de problemas de relação

Este artigo destina-se aos modeladores de dados que trabalham com o Power BI Desktop. Ele fornece orientação sobre como solucionar problemas específicos que você pode encontrar ao desenvolver modelos e relatórios.

[!INCLUDE [relationships-prerequisite-reading](includes/relationships-prerequisite-reading.md)]

## <a name="troubleshooting-checklist"></a>Lista de verificação de solução de problemas

Quando um visual de relatório é configurado para usar campos de duas (ou mais) tabelas e não apresenta o resultado correto (ou nenhum resultado), é possível que o problema esteja nas relações de modelo.

Nesse caso, veja uma lista de verificação geral para solução de problemas a ser seguida. Você pode trabalhar progressivamente na lista de verificação até identificar o(s) problema(s).

1. Alterne o visual para tabela ou matriz ou abra o painel "Ver Dados". É mais fácil solucionar problemas quando você pode ver o resultado da consulta
1. Se houver um resultado de consulta vazio, alterne para o Modo de Exibição de Dados e verifique se as tabelas foram carregadas com linhas de dados
1. Alterne para o Modo de Exibição de Modelo para facilitar a exibição das relações e determinar rapidamente suas propriedades
1. Verifique se existem relações entre as tabelas
1. Verifique se as propriedades da cardinalidade estão configuradas corretamente. Elas poderão estar incorretas se uma coluna no lado "muitos" contiver atualmente valores exclusivos e estar configurada incorretamente como um lado "um"
1. Verifique se as relações estão ativas (linha sólida)
1. Verifique se as direções do filtro dão suporte à propagação (interpretar pontas de seta)
1. Verifique se as colunas corretas estão relacionadas. Selecione a relação ou passe o cursor sobre ela para revelar as colunas relacionadas
1. Verifique se os tipos de dados da coluna relacionados são os mesmos ou pelo menos compatíveis: é possível relacionar uma coluna de texto a uma coluna de número inteiro, mas os filtros não encontrarão correspondências para propagar
1. Alterne para o Modo de Exibição de Dados e verifique se os valores correspondentes podem ser encontrados nas colunas relacionadas

## <a name="troubleshooting-guide"></a>Guia de Solução de Problemas

Confira a seguir uma lista de problemas, juntamente com suas possíveis soluções.

|Problema|Possíveis motivos|
|---------|---------|
|O visual não mostra resultado algum|– O modelo ainda não foi carregado com dados<br />– Não há nenhum dado no contexto de filtro<br />– A Segurança em Nível de Linha está sendo imposta<br />– As relações não estão se propagando entre as tabelas. _Siga a lista de verificação acima_<br />– A Segurança em Nível de Linha está sendo imposta, mas uma relação bidirecional não está ativada para propagação. Confira [RLS (Segurança em Nível de Linha) com o Power BI Desktop](../desktop-rls.md)|
|O visual exibe o mesmo valor para cada agrupamento |– Não existem relações<br />– As relações não estão se propagando entre as tabelas. _Siga a lista de verificação acima_|
|O visual exibe resultados, mas eles não estão corretos|– O visual está configurado incorretamente<br />– A lógica de medida está incorreta<br />– Os dados do modelo precisam ser atualizados<br />– A fonte de dados está incorreta<br />– As colunas de relação estão incorretamente relacionadas (por exemplo, a coluna **ProductID** mapeia para **CustomerID**)<br />– Esta é uma relação entre duas tabelas DirectQuery e o lado "um" da coluna em uma relação contém valores duplicados|
|Os agrupamentos EM BRANCO ou itens de filtro/segmentação são exibidos, e as colunas de origem não contêm espaços EM BRANCO|– Esta é uma relação forte e a coluna no lado "muitos" contém valores não armazenados do lado "um". Confira [Relações de modelo no Power BI Desktop (relações fortes)](../desktop-relationships-understand.md#strong-relationships)<br />– Esta é uma relação de um-para-um e as colunas relacionadas contêm espaços EM BRANCO. Confira [Relações de modelo no Power BI Desktop (relações fortes)](../desktop-relationships-understand.md#strong-relationships)<br />– Uma coluna no lado "muitos" com relação inativa armazena espaços EM BRANCO ou tem valores não armazenados no lado "um"|
|O visual tem dados ausentes|– Filtros incorretos/inesperados foram aplicados<br />– A Segurança em Nível de Linha está sendo imposta<br />– Esta é uma relação fraca, e há espaços em branco nas colunas relacionadas ou problemas na integridade dos dados. Confira [Relações de modelo no Power BI Desktop (relações fracas)](../desktop-relationships-understand.md#weak-relationships)<br />– Esta é uma relação entre duas tabelas DirectQuery. A relação está configurada para [assumir a integridade referencial](../desktop-relationships-understand.md#assume-referential-integrity), mas há problemas na integridade dos dados (valores incompatíveis nas colunas relacionadas)|
|A segurança em nível de linha não está sendo imposta corretamente|– As relações não estão se propagando entre as tabelas. _Siga a lista de verificação acima_<br />– A Segurança em Nível de Linha está sendo imposta, mas uma relação bidirecional não está ativada para propagação. Confira [RLS (Segurança em Nível de Linha) com o Power BI Desktop](../desktop-rls.md)|
|||

## <a name="next-steps"></a>Próximas etapas

Para obter mais informações relacionadas a este artigo, confira os seguintes recursos:

- [Modelar relações no Power BI Desktop](../desktop-relationships-understand.md)
- Perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
- Sugestões? [Contribuir com ideias para aprimorar o Power BI](https://ideas.powerbi.com/)
