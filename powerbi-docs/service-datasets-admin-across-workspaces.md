---
title: Controlar o uso de conjuntos de dados em workspaces (versão prévia) – Power BI
description: Saiba como restringir o fluxo de informações no locatário do Power BI.
author: maggiesMSFT
ms.reviewer: chbraun
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/31/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: d1ad29bebc148d9f30e8d22240dd149787251a0a
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/09/2019
ms.locfileid: "73872575"
---
# <a name="control-the-use-of-datasets-across-workspaces-preview"></a>Controlar o uso de conjuntos de dados em workspaces (versão prévia)

O uso de conjuntos de dados em workspaces é uma maneira eficiente de promover a cultura de dados e a democratização de dados em uma organização. Apesar disso, se você for um administrador do Power BI, às vezes desejará restringir o fluxo de informações em seu locatário do Power BI. Com a configuração de locatário **Usar conjuntos de dados em workspaces**, você poderá restringir a reutilização do conjunto de dados total ou parcialmente por grupos de segurança.

![Configurações de workspace do administrador do Power BI](media/service-datasets-admin-across-workspaces/power-bi-admin-workspace-settings.png)

Se você desligar essa configuração, estes serão os efeitos nos criadores de relatórios:

- O botão para copiar relatórios em workspaces não ficará disponível. 
- Em um relatório baseado em um conjunto de dados compartilhado, o botão **Editar relatório** não ficará disponível.
- No serviço do Power BI, a experiência de descoberta mostra apenas os conjuntos de dados no workspace atual.
- No Power BI Desktop, a experiência de descoberta mostra apenas os conjuntos de dados de workspaces dos quais você é membro.
- No Power BI Desktop, se os usuários abrirem um arquivo .pbix com uma conexão dinâmica com um conjunto de dados fora de workspaces dos quais eles são membros, eles verão uma mensagem de erro solicitando a conexão com outro conjunto de dados.

## <a name="provide-a-link-for-the-certification-process"></a>Fornecer um link para o processo de certificação

Como administrador de locatários, você pode fornecer uma URL para o link **Saiba mais** na página de configuração **Endosso**.  Esse link pode ir para a documentação sobre o processo de certificação. Se você não fornecer um destino para o link **Saiba mais**, por padrão, ele apontará para o artigo sobre [certificação do conjunto de dados](service-datasets-certify.md).

![Saiba mais sobre a certificação do conjunto de dados](media/service-datasets-certify-promote/power-bi-dataset-learn-more-certification.png)

## <a name="next-steps"></a>Próximas etapas

- [Usar conjuntos de dados em workspaces (versão prévia)](service-datasets-across-workspaces.md)
- Dúvidas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
