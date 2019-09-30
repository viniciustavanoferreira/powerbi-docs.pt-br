---
title: Enviar dados por push a um conjunto de dados
description: Enviar dados por push a um conjunto de dados do Power BI
author: rkarlin
ms.author: rkarlin
manager: kfile
ms.reviewer: madia
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 05/22/2019
ms.openlocfilehash: 9eb81610044f795b6f9dc5c58aeefad13de06542
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66222154"
---
# <a name="push-data-into-a-power-bi-dataset"></a>Enviar dados por push a um conjunto de dados do Power BI

A API do Power BI permite enviar dados por push para um conjunto de dados do Power BI. Neste artigo, mostramos como enviar por push um conjunto de dados de Marketing de Vendas contendo uma tabela Produtos para um conjunto de dados existente.

Antes de começar, é necessário ter uma conta do Azure AD (Azure Active Directory) e uma [conta do Power BI](create-an-azure-active-directory-tenant.md).

## <a name="steps-to-push-data-into-a-dataset"></a>Etapas para enviar dados por push a um conjunto de dados

* Etapa 1: [Registrar um aplicativo com o Azure AD](walkthrough-push-data-register-app-with-azure-ad.md)
* Etapa 2: [Obter um token de acesso de autenticação](walkthrough-push-data-get-token.md)
* Etapa 3: [Criar um conjunto de dados no Power BI](walkthrough-push-data-create-dataset.md)
* Etapa 4: [Obter um conjunto de dados para adicionar linhas em uma tabela do Power BI](walkthrough-push-data-get-datasets.md)
* Etapa 5: [Adicionar linhas a uma tabela do Power BI](walkthrough-push-data-add-rows.md)

A próxima seção é uma discussão geral sobre as operações da API do Power BI que enviam dados por push.

## <a name="power-bi-api-operations-to-push-data"></a>Operações da API do Power BI para enviar dados por push

Com a API REST do Power BI, você pode enviar por push fontes de dados para o Power BI. Quando um aplicativo adiciona linhas a um conjunto de dados, os blocos de painel são atualizados automaticamente com os novos dados. Para enviar dados por push, use as operações [PostDataset](https://docs.microsoft.com/rest/api/power-bi/pushdatasets/datasets_postdataset) e [PostRows](https://docs.microsoft.com/rest/api/power-bi/pushdatasets/datasets_postrows). Para encontrar um conjunto de dados, use a operação [Obter Conjuntos de Dados](https://docs.microsoft.com/rest/api/power-bi/datasets/getdatasets). Você pode passar uma ID de grupo para trabalhar com um grupo para qualquer uma dessas operações. Para obter uma lista de IDs de grupo, use a operação [Obter Grupos](https://docs.microsoft.com/rest/api/power-bi/groups/getgroups).

Estas são as operações para enviar dados por push a um conjunto de dados:

* [PostDataset](https://docs.microsoft.com/rest/api/power-bi/pushdatasets/datasets_postdataset)
* [Obter conjuntos de dados](https://docs.microsoft.com/rest/api/power-bi/datasets/getdatasets)
* [Postar Linhas](https://docs.microsoft.com/rest/api/power-bi/pushdatasets/datasets_postrows)
* [Obter grupos](https://docs.microsoft.com/rest/api/power-bi/groups/getgroups)

Você pode criar um conjunto de dados no Power BI passando uma cadeia de caracteres JSON (JavaScript Object Notation) para o serviço do Power BI. Para saber mais sobre o JSON, veja [Apresentando o JSON](http://json.org/).

A cadeia de caracteres JSON para um conjunto de dados tem o seguinte formato:

**Objeto JSON do conjunto de dados do Power BI**

    {"name": "dataset_name", "tables":
        [{"name": "", "columns":
            [{ "name": "column_name1", "dataType": "data_type"},
             { "name": "column_name2", "dataType": "data_type"},
             { ... }
            ]
          }
        ]
    }

Em nosso exemplo de conjunto de dados de Marketing de Vendas, você passaria uma cadeia de caracteres JSON conforme mostrado a seguir. Neste exemplo, **SalesMarketing** é o nome do conjunto de dados e **Product** é o nome da tabela. Depois de definir a tabela, você pode definir o esquema da tabela. Para o conjunto de dados **SalesMarketing**, o esquema da tabela tem estas colunas: ProductID, Manufacturer, Category, Segment, Product e IsCompete.

**JSON de objeto de conjunto de dados de exemplo**

    {
        "name": "SalesMarketing",
        "tables": [
            {
                "name": "Product",
                "columns": [
                {
                    "name": "ProductID",
                    "dataType": "int"
                },
                {
                    "name": "Manufacturer",
                    "dataType": "string"
                },
                {
                    "name": "Category",
                    "dataType": "string"
                },
                {
                    "name": "Segment",
                    "dataType": "string"
                },
                {
                    "name": "Product",
                    "dataType": "string"
                },
                {
                    "name": "IsCompete",
                    "dataType": "bool"
                }
                ]
            }
        ]
    }

Para um esquema de tabela do Power BI, você pode usar os seguintes tipos de dados.

## <a name="power-bi-table-data-types"></a>Tipos de dados de tabela do Power BI

| **Tipo de dados** | **Restrições** |
| --- | --- |
| Int64 |Int64.MaxValue e Int64.MinValue não permitidos. |
| Double |Valores de Double.MaxValue e Double.MinValue não permitidos. Não há suporte para NaN. Não há suporte para +Infinity e -Infinity em algumas funções (por exemplo, Min e Max). |
| Booliano |Nenhum |
| Datetime |Durante o carregamento de dados, podemos quantizar valores com frações de dias para múltiplos inteiros de 1/300 de segundo (3,33 ms). |
| Cadeia de caracteres |Atualmente, permite até 128 mil caracteres. |

## <a name="learn-more-about-pushing-data-into-power-bi"></a>Saiba mais sobre como enviar dados por push ao Power BI

Para começar a enviar dados por push a um conjunto de dados, consulte [Etapa 1: Registrar um aplicativo com o Azure Active Directory](walkthrough-push-data-register-app-with-azure-ad.md) no painel de navegação à esquerda.

[Próxima etapa >](walkthrough-push-data-register-app-with-azure-ad.md)

## <a name="next-steps"></a>Próximas etapas

[Inscrever-se no Power BI](create-an-azure-active-directory-tenant.md)  
[Introdução ao JSON](http://json.org/)  
[Visão geral da API REST do Power BI](overview-of-power-bi-rest-api.md)  
Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)