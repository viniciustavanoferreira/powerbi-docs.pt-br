---
title: Associação dinâmica
description: Saiba como inserir um relatório usando associação dinâmica.
author: KesemSharabi
ms.author: kesharab
manager: rkarlin
ms.topic: conceptual
ms.service: powerbi
ms.subservice: powerbi-developer
ms.date: 09/25/2019
ms.openlocfilehash: 8b42b397f726e492eda80a99eb730c215eb17ccb
ms.sourcegitcommit: 23ad768020a9daf129f69a462a2d46d59d2349d2
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72776227"
---
# <a name="dynamic-binding"></a>Associação dinâmica

A associação dinâmica permite selecionar um conjunto de dados ao inserir um relatório. O relatório e o conjunto de dados não precisam residir no mesmo workspace. Os usuários finais veem resultados diferentes dependendo do conjunto de dados selecionado.

Ambos os workspaces (aquele que contém o relatório e aquele que contém o conjunto de um) devem ser atribuídos a uma capacidade.

A inserção de um relatório usando associação dinâmica tem dois estágios:
1. Como gerar um token
2. Como ajustar o objeto de configuração

## <a name="generating-a-token"></a>Como gerar um token
Para gerar um token, use a [API para gerar um token de inserção para vários itens](embed-sample-for-customers.md#multiEmbedToken).

A associação dinâmica tem suporte para os dois cenários de incorporação, *Inserção para a sua organização* e *Inserção para seus clientes*.

| Solução                   | Token                               | Requisitos                                                                                                                                                  |
|---------------------------------|-------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------|
| *Como inserir para sua organização* | Token de acesso para usuários do Power BI     | O usuário cujo token do Azure AD é usado deve ter as permissões apropriadas para todos os artefatos.                                                                    |
| *Inserção para seus clientes*    | Token de acesso para usuários não do Power BI | Deve incluir permissões para o relatório e o conjunto de dados associado dinamicamente. Use a nova API para gerar um token de inserção que dê suporte a vários artefatos. |

## <a name="adjusting-the-config-object"></a>Como ajustar o objeto de configuração
Adicione `datasetBinding` ao objeto de configuração. Use o exemplo na parte inferior da página como referência.

Se você não estiver familiarizado com a inserção no Power BI, leia estes tutoriais para saber como inserir seu conteúdo do Power BI:
* [Inserir conteúdo do Power BI em um aplicativo para seus clientes](embed-sample-for-customers.md)
* [Tutorial: Inserir o conteúdo do Power BI em um aplicativo para a sua organização](embed-sample-for-your-organization.md)

 ### <a name="example"></a>Exemplo
```javascript
var config = {
    type: 'report',
    tokenType: models.TokenType.Embed,
    accessToken: accessToken,
    embedUrl: embedUrl,
    id: "reportId", // The wanted report id
    permissions: permissions,

    /////////////////////////////////////////////
    // Adjustment required for dynamic binding //
    datasetBinding: {
        datasetId: "notOriginalDatasetId",  // </The wanted dataset id
    }
    // End of dynamic binding adjustment            //
    /////////////////////////////////////////////
};

// Get a reference to the embedded report HTML element
var embedContainer = $('#embedContainer')[0];

// Embed the report and display it within the div container
var report = powerbi.embed(embedContainer, config);
```