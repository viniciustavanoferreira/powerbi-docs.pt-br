---
title: Solução de problemas de valores aninhados retornados como texto no serviço do Power BI
description: Saiba mais sobre como corrigir os valores aninhados, que estão sendo convertidos em uma cadeia de caracteres ao usar configurações de privacidade de fonte de dados inadequada
author: cpopell
ms.reviewer: ''
ms.custom: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: troubleshooting
ms.date: 6/4/2019
ms.author: gepopell
LocalizationGroup: Reports
ms.openlocfilehash: ab40ca9c415dacf52f4d82eb2c157d57aef92f93
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/05/2020
ms.locfileid: "73871276"
---
# <a name="troubleshooting-nested-values-returned-as-text-in-power-bi-service"></a>Solução de problemas de valores aninhados retornados como texto no serviço do Power BI

## <a name="cause"></a>Causa

No passado, houve casos em que um relatório do Power BI foi atualizado corretamente no Desktop, mas falhou no serviço do Power BI com um erro como “Não é possível converter o valor “[Table]” para o tipo de Tabela”. Uma das causas desse erro é que, quando o Firewall de Privacidade de Dados armazena em buffer uma fonte de dados, os valores não escalares aninhados (como tabelas, registros, listas e funções) são convertidos automaticamente em valores de texto (como “[Table]” ou “[Record]”).

Agora que o serviço do Power BI dá suporte à configuração dos níveis de privacidade (ou desativa o Firewall inteiramente), esses erros podem ser evitados ao [definir as configurações de privacidade da fonte de dados](https://powerbi.microsoft.com/blog/privacy-levels-for-cloud-data-sources/) no serviço do Power BI para ser não privado.

Começando com o Power BI de junho, quando o Firewall armazena em buffer um aninhado registro/tabela/lista/etc., em vez de converter silenciosamente esses valores em texto, o seguinte erro será produzido: 

`We cannot return a value of type Table in this context`

## <a name="effect-on-loadrefresh"></a>Efeito de carga/atualização

Embora a alteração seja motivada pelo Firewall de buffer, seu impacto também se estende à Carga/Atualização. Para lidar com o comportamento do Firewall de buffer, também precisamos alterar o comportamento de carregamento de aninhados registros/tabelas/etc. para o modelo do Power BI e o modelo de dados do Excel no PQ para Excel. Antes, aninhados registros/tabelas/etc. seriam carregados como valores de texto (como “[Table]” ou “[Record]”). Agora, eles serão tratados como erros, o que resultará em um valor nulo na tabela carregada e em um incremento de contagem de erro nos resultados de carga.

Como esses erros ocorrem somente durante a Carga/Atualização, eles não aparecerão no Editor do Power Query.

### <a name="before"></a>Antes

- Carga/Atualização sem erros
- Tabela carregada contém “[Table]”, “[Record]”, etc.
 

### <a name="after"></a>Depois

- Carga/Atualização com erros
- Tabela carregada contém NULLs (em vez de “[Table]”, “[Record]”, etc.)
 

## <a name="resolution"></a>Resolução

Você está carregando uma coluna que contém os valores não escalares (por exemplo, tabelas, listas, registros, etc.)?
Nesse caso, você poderá eliminar os erros, removendo a coluna.
Se não puder remover a coluna, você deverá poder replicar o comportamento antigo adicionando uma coluna personalizada e usando lógica, como o exemplo a seguir:

`if [MyColumn] is table then "[Table]" else if [MyColumn] is record then "[Record]" else if [MyColumn] is list then "[List]" else if [MyColumn] is function then "[Function]" else [MyColumn]`

O problema será reproduzido no Power BI Desktop se você definir todas as configurações de privacidade da sua fonte de dados como Particular?
Caso seja, você deverá poder resolver o erro ao [definir suas configurações de privacidade de fonte de dados](https://powerbi.microsoft.com/blog/privacy-levels-for-cloud-data-sources/) no serviço do Power BI como não privadas.
