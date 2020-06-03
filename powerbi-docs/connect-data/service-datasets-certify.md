---
title: Certificar conjuntos de dados – Power BI
description: Saiba como orientar os usuários corporativos a conjuntos de dados confiáveis e de alta qualidade.
author: maggiesMSFT
ms.reviewer: kayu
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/30/2020
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: a6d03521cd3962dcf9549d99076d8606b1142976
ms.sourcegitcommit: 5e5a7e15cdd55f71b0806016ff91256a398704c1
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83792931"
---
# <a name="certify-datasets---power-bi"></a>Certificar conjuntos de dados – Power BI

Sua organização pode certificar conjuntos de dados que são a fonte autorizada de informações críticas. Esses conjuntos de dados são exibidos em destaque quando os designers de relatórios começam a criar um relatório e buscam dados confiáveis. A certificação pode ser um processo altamente seletivo, com a certificação de apenas os conjuntos de dados mais importantes. Os administradores de locatários do Power BI têm uma nova configuração para poder controlar rigidamente quem pode certificar conjuntos de dados. Portanto, os administradores podem garantir que a certificação desse conjunto de dados resulte em conjuntos de dados realmente confiáveis e autorizados, projetados para uso em toda a organização.

Agora os usuários do Power BI podem ter acesso a muitos conjuntos de dados diferentes e, portanto, as empresas precisam orientá-los aos conjuntos de dados confiáveis e de alta qualidade. O Power BI fornece duas maneiras de *endossar* conjuntos de dados:

- **Promoção**: Os proprietários de conjuntos de dados e outros em um workspace podem promover seus conjuntos de dados quando estiverem prontos para uso generalizado. Confira [Promover seu conjunto de dados](service-datasets-promote.md) para obter detalhes. 
- **Certificação**: Os proprietários de conjuntos de dados podem solicitar a certificação de um conjunto de dados promovido. Um grupo seleto de usuários definidos na configuração do administrador de locatários **Certificação do Conjunto de Dados** decide quais conjuntos de dados serão certificados. O nome da pessoa que certificou um conjunto de dados é exibido em uma dica de ferramenta durante a experiência de descoberta do conjunto de dados; passe o mouse sobre o rótulo **Certificado** e você o verá.

## <a name="certify-a-dataset"></a>Certificar um conjunto de dados

O administrador de locatários pode fornecer uma URL para o link **Saiba mais** na página de configuração **Endosso**.  Eles podem vinculá-lo à documentação sobre o processo de certificação. Se eles não fornecerem um destino para o link **Saiba mais**, por padrão, ele apontará para este artigo.

![Saiba mais sobre a certificação do conjunto de dados](media/service-datasets-certify-promote/power-bi-dataset-learn-more-certification.png)

Ser nomeado como alguém que pode certificar conjuntos de dados certamente é uma grande responsabilidade. Quando um criador de conjuntos de dados contata você sobre como certificar um conjunto de dados, esse é o início de seu processo de habilitação. Quando você estiver satisfeito com um conjunto de dados que mereça a certificação, estas serão as últimas etapas.

1. O proprietário do conjunto de dados precisa conceder a você as permissões de membro no workspace no qual reside o conjunto de dados.
1. Se o administrador de locatários nomear você como alguém que pode certificar conjuntos de dados, a opção **Certificado** na seção **Endosso** de **Configurações** do conjunto de dados estará disponível. Selecione **Certificado**.
1. Selecione **Aplicar**.

Leia mais sobre como os administradores de locatários [controlam o uso de conjuntos de dados em workspaces](service-datasets-admin-across-workspaces.md).

## <a name="next-steps"></a>Próximas etapas

* Leia mais sobre [como usar conjuntos de dados em workspaces](service-datasets-across-workspaces.md)
* Dúvidas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
