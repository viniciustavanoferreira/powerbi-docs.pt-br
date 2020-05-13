---
title: Perguntas frequentes do gateway de dados local – Power BI
description: Este artigo são as perguntas frequentes sobre o gateway de dados local do Power BI. Esse artigo reúne as perguntas frequentes sobre o gateway usado no Power BI.
author: arthiriyer
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 07/15/2019
ms.author: arthii
LocalizationGroup: Gateways
ms.openlocfilehash: f64fcd86d54c20e1318d38c2a73e9bca2174558a
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83302657"
---
# <a name="on-premises-data-gateway-faq---power-bi"></a>Perguntas frequentes do gateway de dados local – Power BI

[!INCLUDE [gateway-rewrite](../includes/gateway-rewrite.md)]

## <a name="power-bi"></a>Power BI

**Pergunta:** Preciso atualizar o gateway de dados local (modo pessoal)?

**Resposta:** Não, você pode continuar usando o gateway (modo pessoal) do Power BI.

**Pergunta:** Há alguma permissão especial necessária para instalar o gateway e gerenciá-lo no serviço do Power BI?

**Resposta:** Nenhuma permissão especial é necessária.

**Pergunta:** Posso carregar pastas de trabalho do Excel com modelos de dados do PowerPivot que se conectam a fontes de dados locais? Preciso ter um gateway para este cenário? 

**Resposta:** Sim, você pode carregar a pasta de trabalho. Não, não é necessário ter um gateway. Mas, como os dados residem no modelo de dados do Excel, os relatórios do Power BI baseados na pasta de trabalho do Excel não serão dinâmicos. Para atualizar os relatórios no Power BI, você precisa carregar novamente uma pasta de trabalho atualizada. Se preferir, use o gateway com a atualização agendada.

**Pergunta:** Se os usuários compartilharem dashboards que têm uma conexão do DirectQuery, os outros usuários poderão ver os dados mesmo que não tenham as mesmas permissões? 

**Resposta:** Para um dashboard conectado ao Azure Analysis Services, os usuários verão apenas os dados aos quais tiverem acesso. Se os usuários não tiverem as mesmas permissões, não poderão ver os dados. Para outras fontes de dados, todos os usuários compartilharão as credenciais inseridas pelo administrador para aquela fonte de dados.

**Pergunta:** Por que não consigo me conectar ao servidor do Oracle? 

**Resposta:** Talvez seja necessário instalar o cliente Oracle e configurar o arquivo tnsnames.ora com as informações de servidor apropriadas para se conectar ao servidor do Oracle. Essa é uma instalação separada fora do gateway. Para obter mais informações, consulte [Instalando o cliente Oracle](service-gateway-onprem-manage-oracle.md#install-the-oracle-client).

**Pergunta:** Estou usando scripts R. Ele tem suporte?

**Resposta**: Os scripts R têm suporte apenas para o modo pessoal.

## <a name="analysis-services-in-power-bi"></a>Analysis Services no Power BI

**Pergunta:** Posso usar msdmpump.dll para criar mapeamentos de nome de usuário efetivo personalizados para o Analysis Services? 

**Resposta:** Não. Esse uso não é compatível no momento.

**Pergunta:** Posso usar o gateway para me conectar a uma instância multidimensional (OLAP)? 

**Resposta:** Sim. O gateway de dados local é compatível com conexões dinâmicas tanto para modelos de Tabela quanto para modelos Multidimensionais do Analysis Services.

**Pergunta:** E se eu instalar o gateway em um computador em um domínio diferente do meu servidor local que usa a autenticação do Windows? 

**Resposta:** Não há nenhuma garantia nesse caso. Tudo depende a relação de confiança entre os dois domínios. Se os dois domínios diferentes estiverem em um modelo de domínio confiável, o gateway poderá se conectar ao servidor do Analysis Services e o nome de usuário efetivo poderá ser resolvido. Caso contrário, poderá ocorrer uma falha de logon.

**Pergunta:** Como posso descobrir qual nome de usuário efetivo está sendo transmitido para meu servidor local do Analysis Services? 

**Resposta:** Respondemos a essa pergunta no [artigo de solução de problemas](service-gateway-onprem-tshoot.md).

## <a name="next-steps"></a>Próximas etapas

* [Solução de problemas do gateway de dados local](/data-integration/gateway/service-gateway-tshoot)

Mais perguntas? Experimente a [Comunidade do Power BI](https://community.powerbi.com/).
