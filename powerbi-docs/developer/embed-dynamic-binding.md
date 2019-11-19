---
title: Conectar um relatório a um conjunto de dados usando associação dinâmica
description: Saiba como inserir um relatório usando associação dinâmica.
author: KesemSharabi
ms.author: kesharab
ms.topic: conceptual
ms.service: powerbi
ms.subservice: powerbi-developer
ms.date: 11/07/2019
ms.openlocfilehash: ecc7ec21117c9e2cd974058c63bcf02d72d1f4b1
ms.sourcegitcommit: 50c4bebd3432ef9c09eacb1ac30f028ee4e66d61
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73925752"
---
# <a name="connecting-a-report-to-a-dataset-using-dynamic-binding"></a>Conectar um relatório a um conjunto de dados usando associação dinâmica 

O uso da associação dinâmica só é relevante quando um relatório é conectado a um conjunto de dados. A conexão entre o relatório e o conjunto de dados é conhecida como *associação*. Quando a associação é determinada no ponto de inserção, em vez de ser predeterminada anteriormente, a associação é conhecida como [associação dinâmica](https://nam06.safelinks.protection.outlook.com/?url=https%3A%2F%2Fen.wikipedia.org%2Fwiki%2FLate_binding&data=02%7C01%7CKesem.Sharabi%40microsoft.com%7C5d5b0d2d62cf4818f0c108d7635b151e%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C637087115150775585&sdata=AbEtdJvgy4ivi4v4ziuui%2Bw2ibTQQXBQNYRKbXn5scA%3D&reserved=0).
 
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