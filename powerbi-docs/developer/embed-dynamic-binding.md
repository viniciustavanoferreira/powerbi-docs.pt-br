---
title: Conectar um relatório a um conjunto de dados usando associação dinâmica
description: Saiba como inserir um relatório usando associação dinâmica.
author: KesemSharabi
ms.author: kesharab
ms.topic: conceptual
ms.service: powerbi
ms.subservice: powerbi-developer
ms.date: 11/07/2019
ms.openlocfilehash: 1f54ce3a6bfd69caa3f386b7684e3df7f725523d
ms.sourcegitcommit: a1409030a1616027b138128695b80f6843258168
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76709533"
---
# <a name="connect-a-report-to-a-dataset-using-dynamic-binding"></a>Conectar um relatório a um conjunto de dados usando associação dinâmica 

Quando um usuário se conecta a um conjunto de dados, você pode usar a associação dinâmica. A conexão entre o relatório e o conjunto de dados é conhecida como *associação*. Quando a associação é determinada no ponto de inserção, em vez de ser predeterminada anteriormente, a associação é conhecida como associação dinâmica.

Ao inserir um relatório de Power BI usando *associação dinâmica*, você pode conectar o mesmo relatório a diferentes conjuntos de valores, dependendo das credenciais do usuário.

Isso significa que você pode usar um relatório para exibir informações diferentes, dependendo do conjunto de dados ao qual ele está conectado. Por exemplo, um relatório que mostra valores de venda de varejo pode ser conectado a diferentes conjuntos de dados de revendedores e produzir resultados diferentes, dependendo do conjunto de dados do varejista ao qual ele está conectado.

O relatório e o conjunto de dados não precisam residir no mesmo workspace. Ambos os workspaces (aquele que contém o relatório e aquele que contém o conjunto de dados) devem ser atribuídos a uma [capacidade](azure-pbie-create-capacity.md).

Como parte do processo de inserção, certifique-se de *gerar um token com permissões suficientes* e *ajustar o objeto de configuração*.

## <a name="generating-a-token-with-sufficient-permissions"></a>Gerar um token com permissões suficientes

A associação dinâmica tem suporte para os cenários de *Inserção para a sua organização* e *Inserção para seus clientes*. A tabela abaixo descreve as considerações para cada cenário.

|Cenário  |Propriedade dos dados  |Token  |Requisitos  |
|---------|---------|---------|---------|
|*Como inserir para sua organização*    |O usuário possui dados         |Token de acesso para usuários do Power BI         |O usuário cujo token do Azure AD é usado deve ter as permissões apropriadas para todos os artefatos.         |
|*Inserção para seus clientes*     |O aplicativo possui dados         |Token de acesso para usuários não do Power BI         |Deve incluir permissões para o relatório e o conjunto de dados associado dinamicamente. Use a [API para geração de um token de inserção para vários itens](embed-sample-for-customers.md#multiEmbedToken) a fim de gerar um token de inserção que ofereça suporte a vários artefatos.         |

## <a name="adjusting-the-config-object"></a>Como ajustar o objeto de configuração
Adicione `datasetBinding` ao objeto de configuração. Use o exemplo abaixo como referência.

```javascript
var config = {
    type: 'report',
    tokenType: models.TokenType.Embed,
    accessToken: accessToken,
    embedUrl: embedUrl,
    id: "reportId", // The wanted report id
    permissions: permissions,

    // -----  Adjustment required for dynamic binding ---- //
    datasetBinding: {
        datasetId: "notOriginalDatasetId",  // </The wanted dataset id
    }
    // ---- End of dynamic binding adjustment ---- //
};

// Get a reference to the embedded report HTML element
var embedContainer = $('#embedContainer')[0];

// Embed the report and display it within the div container
var report = powerbi.embed(embedContainer, config);
```

## <a name="next-steps"></a>Próximas etapas

Se você não estiver familiarizado com a inserção no Power BI, leia estes tutoriais para saber como inserir seu conteúdo do Power BI:
* [Tutorial: Inserir conteúdo do Power BI em um aplicativo para seus clientes](embed-sample-for-customers.md)
* [Tutorial: Inserir o conteúdo do Power BI em um aplicativo para a sua organização](embed-sample-for-your-organization.md)