---
title: Controle de versão do modelo de dados do Power BI
description: Modelo de Dados exposto por um serviço OData
author: rkarlin
ms.author: rkarlin
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 06/08/2018
ms.openlocfilehash: 6456974e7c05b65eb084d00bb1970d4291a0cf0c
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "61385609"
---
# <a name="data-model-versioning"></a>Controle de versão do Modelo de Dados

O modelo de dados exposto por um Serviço OData, como o modelo de dados do Power BI, define um contrato entre o serviço OData e seus clientes. Os serviços podem estender o modelo somente de maneira a não dividir os clientes existentes. Alterações significativas, como remover propriedades ou alterar o tipo de propriedades existentes, exigem que uma nova versão de serviço esteja disponível em uma URL raiz de serviço diferente para o novo modelo.  
  
As adições de modelos de dados a seguir são consideradas seguras e não requerem que os serviços realizem controle de versão de seu ponto de entrada.  
  
* Adicionar uma propriedade que permite valor nulo ou tem um valor padrão: se ela tem o mesmo nome que uma propriedade dinâmica existente, deverá ter o mesmo tipo (ou o tipo base) que essa propriedade dinâmica existente  
* Adicionar uma propriedade de navegação que permite valor nulo ou tem um valor de coleção: se ela tem o mesmo nome que uma propriedade de navegação dinâmica existente, deverá ter o mesmo tipo (ou o tipo base) que essa propriedade de navegação dinâmica existente  
* Adicionar um novo tipo de entidade ao modelo  
* Adicionar um novo tipo complexo ao modelo  
* Adicionar um novo conjunto de entidades  
* Adicionar um novo singleton  
* Adicionar uma ação, uma função, uma importação de ação ou importação de função
* Adicionar um parâmetro de ação que permite valor nulo  
* Adicionar uma enumeração ou definição de tipo  
* Adicionar qualquer anotação a um elemento de modelo que não precisa ser compreendido pelo cliente para interagir corretamente com o serviço  
  
Os clientes ***DEVEM*** estar preparados para que os serviços efetuem essas alterações incrementais em seu modelo. Em particular, os clientes devem estar preparados para receber propriedades e tipos derivados não definidos previamente pelo serviço.  
  
Os serviços ***NÃO DEVEM*** alterar seu modelo de dados de acordo com o usuário autenticado. Se o modelo de dados é dependente de usuário ou de grupo de usuários, todas as alterações DEVEM ser alterações seguras, conforme definido nesta seção na comparação do modelo completo com o modelo visível para os usuários com autorizações limitadas.  
  
Para saber mais sobre os padrões do Modelo de Dados OData, consulte [OData versão 4.0 parte 1: protocolo mais errata 02](http://docs.oasis-open.org/odata/odata/v4.0/odata-v4.0-part1-protocol.html).  
  
## <a name="see-also"></a>Consulte também
[Visão geral da API REST do Power BI](https://docs.microsoft.com/rest/api/power-bi/)  