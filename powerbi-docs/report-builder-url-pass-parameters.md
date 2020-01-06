---
title: Passar um parâmetro de relatório em uma URL para um relatório paginado – Construtor de Relatórios do Power BI
description: Este tópico descreve como passar parâmetros de relatório para um relatório, incluindo-os na URL de um relatório paginado.
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
author: maggiesMSFT
ms.author: maggies
ms.reviewer: cfinlan
ms.custom: ''
ms.date: 08/29/2019
ms.openlocfilehash: 44e56613a69069351f21aa7d515fc2bb296e6728
ms.sourcegitcommit: 6272c4a0f267708ca7d38a45774f3bedd680f2d6
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/06/2020
ms.locfileid: "74128262"
---
# <a name="pass-a-report-parameter-in-a-url-for-a-paginated-report-in-power-bi"></a>Passar um parâmetro de relatório em uma URL para um relatório paginado no Power BI 

Você pode passar parâmetros de relatório para um relatório, incluindo-os na URL de um relatório paginado. Todos os parâmetros de consulta podem ter parâmetros de relatório correspondentes. Portanto, você passa um parâmetro de consulta para um relatório por meio do parâmetro de relatório correspondente. Será necessário acrescentar o prefixo ao nome do parâmetro `rp:` para que o Power BI o reconheça na URL. 

Os parâmetros de relatório diferenciam maiúsculas de minúsculas e usam os seguintes caracteres especiais: 

- Um espaço na parte do parâmetro da URL será substituído por um sinal de adição (+).  Por exemplo: 

    ```rp:Holiday=Christmas+Day```

- Um ponto e vírgula em qualquer parte da cadeia de caracteres será substituído pelos caracteres `%3A`.

Os navegadores devem executar automaticamente a codificação de URL apropriada. Você não precisa codificar nenhum dos caracteres manualmente. 

Para definir um parâmetro de relatório dentro de uma URL, use a seguinte sintaxe: 

```
rp:parameter=value
```

Por exemplo, para especificar dois parâmetros, "Vendedor" e "Estado", definidos em um relatório na sua área Meu Workspace, você usaria a seguinte URL: 

```
https://app.powerbi.com/groups/me/rdlreports/xxxxxxx-abc7-40f0-b456-febzf9cdda4d?rp:Salesperson=Tie+Bear&rp:State=Utah 
```

Para especificar os mesmos dois parâmetros definidos em um relatório em um aplicativo, você usaria a seguinte URL: 

```
https://app.powerbi.com/groups/me/apps/xxxxxxx-c4c4-4217-afd9-3920a0d1e2b0/rdlreports/b1d5e659-639e-41d0-b733-05d2bca9853c?rp:Salesperson=Tiggee&State=Utah 
```

Para passar um valor nulo para um parâmetro, use a seguinte sintaxe: 

```
parameter:isnull=true
```

Por exemplo:

```
rp:SalesOrderNumber:isnull=true
```

Para passar um valor Booliano, use 0 para false e 1 para true. Para passar um valor Float, inclua o separador decimal da localidade do servidor.

> [!NOTE]
> Se o relatório contiver um parâmetro de relatório com um valor padrão e o valor da propriedade **Prompt** for **false** (ou seja, se a propriedade **Usuário do Prompt** não estiver selecionada no Report Manager), então você não poderá passar um valor para esse parâmetro de relatório dentro de uma URL. Isso fornece aos administradores a opção de impedir que os usuários finais adicionem ou modifiquem os valores de determinados parâmetros de relatório.

## <a name="additional-examples"></a>Exemplos adicionais 

O exemplo de URL a seguir inclui um parâmetro com vários valores, "Vendedor". O formato usado para um parâmetro com vários valores é repetir o nome do parâmetro para cada valor. 

```
https://app.powerbi.com/groups/me/rdlreports/xxxxxxx-abc7-40f0-b456-febzf9cdda4d?rp:Salesperson=Tie+Bear&rp:Salesperson=Mickey 
```

O exemplo de URL a seguir passa um único parâmetro, SellStartDate, com o valor de "1/7/2005" para um servidor de relatório em modo nativo.

```
https://app.powerbi.com/groups/me/rdlreports/xxxxxxx-abc7-40f0-b456-febzf9cdda4d?rp:SellStartDate=7/1/2005
```

## <a name="next-steps"></a>Próximas etapas

- [Parâmetros de URL em relatórios paginados no Power BI](report-builder-url-parameters.md)
- [O que são os relatórios paginados no Power BI Premium?](paginated-reports-report-builder-power-bi.md)
