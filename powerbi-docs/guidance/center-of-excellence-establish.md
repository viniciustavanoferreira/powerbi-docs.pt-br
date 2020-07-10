---
title: Estabelecer um centro de excelência
description: Saiba como um centro de excelência ajudou a Microsoft a criar uma análise padronizada e uma plataforma de dados para revelar informações com o modelo operacional certo, envolvimento dos stakeholders e investimentos compartilhados e dedicados.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 07/02/2020
ms.author: v-pemyer
ms.openlocfilehash: 9aab2afd9e3b4b86844c045ceb0346d57baa3e18
ms.sourcegitcommit: 561f6de3e4621d9d439dd54fab458ddca78ace2c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/03/2020
ms.locfileid: "85939864"
---
# <a name="establish-a-center-of-excellence"></a>Estabelecer um centro de excelência

Este artigo destina-se a profissionais e gerentes de TI. Você aprenderá a configurar um COE (centro de excelência) de BI e análise em sua organização e como a Microsoft fez.

Para alguns, há uma compreensão equivocada de que um COE é apenas um suporte técnico, o que está longe da realidade.

Geralmente, um COE de BI e análise é uma equipe de profissionais responsáveis por estabelecer e manter uma plataforma de BI. Essa equipe também é responsável pela criação de uma única fonte de verdade e definir um conjunto de métricas consistentes em toda a empresa para obter e acelerar insights. Ainda assim, um COE é um termo amplo. Ele pode ser implementado e gerenciado de maneiras diferentes, e sua estrutura e seu escopo podem variar de uma organização para outra. Em seu cerne, é sempre uma plataforma robusta que fornece as funcionalidades de insight e dados certas para as pessoas certas no momento certo. Idealmente, também promove a evangelização, o treinamento e o suporte. Na Microsoft, ele é descrito como _[disciplina no cerne](center-of-excellence-microsoft-business-intelligence-transformation.md#discipline-at-the-core)_ e é entregue como nossa plataforma de BI e única fonte de verdade.

Em organizações maiores, você pode encontrar vários COEs com o COE principal _estendido_ por satélite COEs – muitas vezes no nível do departamento. Assim, um COE de satélite é um grupo de especialistas familiarizados com taxonomias e definições que sabem como transformar dados centrais no que faz sentido _para os respectivos departamentos_. Os analistas departamentais recebem permissões para os dados centrais e confiam neles para uso em seus próprios relatórios. Eles criam soluções que dependem de dimensões de núcleo, fatos e lógica de negócios cuidadosamente preparados. Às vezes, eles também podem estendê-lo com conjuntos de negócios menores e específicos de departamento e lógica de negócio. É importante ressaltar que os COEs satélites nunca são desconectados nem atuam de maneira isolada. Na Microsoft, os COEs satélites promovem _[flexibilidade na borda](center-of-excellence-microsoft-business-intelligence-transformation.md#flexibility-at-the-edge)_ .

Para que esse cenário estendido tenha sucesso, os departamentos devem _pagar para reproduzir_. Em outras palavras, os departamentos devem investir financeiramente no COE central. Dessa forma, não há preocupação de "não estar recebendo sua parte" ou que seus requisitos em algum momento não sejam priorizados.

Para dar suporte a esse cenário, o COE central deve ser dimensionado para atender às necessidades departamentais financiadas. Depois que vários conjuntos de dados foram integrados, começam as economias de escala. Na Microsoft, ficou rapidamente evidente que trabalhar de modo central é mais econômico e traz resultados mais rápidos. Quando cada nova área de assunto foi integrada, tivemos uma economia ainda maior de escala que permitiu aproveitar e contribuir em toda a plataforma, reforçando nossa cultura de dados subjacente.

Considere um exemplo: Nossa plataforma de BI fornece lógica de negócios, fatos e dimensões centrais para as áreas de finanças, vendas e marketing. Te também define centenas de KPIs (indicadores chave de desempenho). Agora, um analista no negócio de Power Platform precisa preparar um dashboard de liderança. Alguns dos KPIs, como receita e pipelines, vêm diretamente da plataforma de BI. Outros, no entanto, são baseados em necessidades mais granulares de negócios. Uma dessas necessidades é para um KPI sobre a adoção do usuário do recurso específico do Power BI: fluxos de informações. Portanto, o analista produz um [modelo composto](composite-model-guidance.md) do Power BI para integrar os dados da plataforma de BI central aos dados departamentais. Em seguida, ele adiciona lógica de negócios para definir seus KPIs departamentais. Por fim, ele cria seu dashboard de liderança com base no novo modelo, que aproveita os recursos de COE de toda a empresa amplificados com os dados e o conhecimento locais.

O mais importante é que uma divisão de responsabilidade entre os COEs central e satélites permita aos analistas departamentais se concentrar em explorar novas áreas, em vez de gerenciar uma plataforma de dados. Às vezes, pode até mesmo ser uma relação mutuamente benéfica entre os COEs central e satélites. Por exemplo, um COE satélite pode definir novas métricas que, com benefícios comprovados para os departamentos, acabam como métricas principais benéficas para toda a empresa, disponíveis pelo COE central e com o seu suporte.

## <a name="bi-platform"></a>Plataforma de BI

Em sua organização, o COE pode ser reconhecido por um nome diferente, como equipe ou grupo de BI. O nome importa muito menos do que realmente faz. Se você não tiver uma equipe formalizada, recomendamos cultivar uma equipe que una seus principais especialistas de BI para estabelecer sua plataforma de BI.

Na Microsoft, o COE é conhecido como a plataforma de BI. Ela tem muitos grupos de stakeholders que representam diferentes divisões dentro da empresa, como finanças, vendas e marketing. É organizada para executar [funcionalidades compartilhadas](#shared-capabilities) e [entregas dedicadas](#dedicated-deliveries).

:::image type="content" source="media/center-of-excellence-establish/business-intelligence-platform-operating-model.png" alt-text="O diagrama mostra as funcionalidades compartilhados e as entregas dedicadas, que são descritas nas seções a seguir.":::

### <a name="shared-capabilities"></a>Funcionalidades compartilhadas

Funcionalidades compartilhadas são necessárias para estabelecer e operar a plataforma de BI. Elas dão suporte a todos os grupos de stakeholders que financiam a plataforma. Eles incluem as seguintes equipes:

- **Engenharia da plataforma central:** projetamos a plataforma de BI com uma mentalidade de engenharia. É realmente um conjunto de estruturas que dão suporte à ingestão de dados, ao processamento para aprimorar os dados e à entrega desses dados em modelos de dados para o consumo de analistas. Os engenheiros são responsáveis pelo design técnico e pela implementação dos principais recursos da plataforma de BI. Por exemplo, eles criam e implementam os pipelines de dados.
- **Infraestrutura e hospedagem:** os engenheiros de TI são responsáveis por provisionar e gerenciar todos os serviços do Azure.
- **Suporte e operações:** essa equipe mantém a plataforma em execução. O suporte cuida de necessidades do usuário como permissões de dados. As operações mantêm a plataforma em execução, garantindo que os SLAs (contratos de nível de serviço) sejam cumpridos e comunicando atrasos ou falhas.
- **Gerenciamento de versão:** Os PMs (gerentes de programa) técnicos lançam as alterações. As alterações podem variar de atualizações de estrutura de plataforma a solicitações de alteração feitas em modelos de dados. Elas são a última linha de defesa para garantir que as alterações não causem nenhum problema.

### <a name="dedicated-deliveries"></a>Entregas dedicadas

Há uma equipe de entrega dedicada para cada grupo de stakeholders. Normalmente, consiste em um engenheiro de dados, um engenheiro de análise e um PM técnico – todos financiados pelo respectivo grupo de stakeholders.

## <a name="bi-team-roles"></a>Funções da equipe de BI

Na Microsoft, nossa plataforma de BI é operada por equipes escalonáveis de profissionais. As equipes são alinhadas aos recursos dedicados e compartilhados. Hoje, temos as seguintes funções:

- **Gerentes de programa:** os PMs são um recurso dedicado. Eles atuam como o contato principal entre a equipe de BI e os stakeholders. É trabalho deles converter os requisitos de negócios do stakeholder em uma especificação técnica. E eles gerenciam a priorização dos resultados finais do stakeholder.
- **Leads de banco de dados:** eles são um recurso dedicado responsável pela integração de novos conjuntos de dados no data warehouse centralizado. A integração de um conjunto de dados pode envolver configurar dimensões conformadas, adicionar de atributos personalizados e lógica de negócios, além de nomes e formatação padrão.
- **Leads de análise:** eles são um recurso dedicado responsável pelo design e desenvolvimento de modelos de dados. Eles buscam aplicar uma arquitetura consistente usando a nomenclatura e a formatação padrão. A otimização de desempenho é uma parte importante de sua função.
- **Operações e infraestrutura:** são um recurso compartilhado responsável pelo gerenciamento de trabalhos e pipelines de dados. Também são responsáveis por gerenciar assinaturas do Azure, capacidades do Power BI, máquinas virtuais e gateways de dados.
- **Suporte:** São um recurso compartilhado responsável por escrever documentação, organizar treinamento, comunicar alterações no modelo de dados e responder a perguntas do usuário.

## <a name="governance-and-compliance"></a>Governança e conformidade

Para cada grupo de stakeholders, os PMs líderes fornecem governança e supervisão entre os programas. Sua meta de substituição é garantir que os investimentos em TI gerem valor comercial e reduzam o risco. As reuniões do comitê diretor são feitas regularmente para examinar o progresso e aprovar as principais iniciativas.

## <a name="next-steps"></a>Próximas etapas

Para obter mais informações sobre este artigo, confira os seguintes recursos:

- [Arquitetura da solução de BI no COE](center-of-excellence-business-intelligence-solution-architecture.md)
- Dúvidas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
- Sugestões? [Contribuir com ideias para aprimorar o Power BI](https://ideas.powerbi.com/)
