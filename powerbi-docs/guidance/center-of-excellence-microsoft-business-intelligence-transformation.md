---
title: Transformação de BI da Microsoft
description: Saiba como a Microsoft orienta com êxito uma cultura de dados para tomada de decisões de negócios. Ela descreve sua estratégia e visão para o BI.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 07/02/2020
ms.author: v-pemyer
ms.openlocfilehash: 18dc88404b84e786bfee0a15ac169a6e0c1496e4
ms.sourcegitcommit: 561f6de3e4621d9d439dd54fab458ddca78ace2c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/03/2020
ms.locfileid: "85939860"
---
# <a name="microsofts-bi-transformation"></a>Transformação de BI da Microsoft

Este artigo destina-se a profissionais e gerentes de TI. Você aprenderá sobre nossa visão e estratégia de BI, que nos permite aproveitar continuamente nossos dados como um ativo. Você também aprenderá a conduzir com êxito uma cultura de dados de tomada de decisões de negócios com o Power BI.

Primeiro, um pouco de contexto: Hoje, a explosão de dados está afetando os consumidores e as empresas a velocidades assustadoras. O sucesso neste ambiente de uso intensivo de dados requer analistas e executivos que consigam extrair enormes quantidades de dados para insights sucintos. A evolução das ferramentas de BI da Microsoft revolucionou a maneira como a própria Microsoft explora seus dados e obtém as informações corretas necessárias para impulsionar o impacto na empresa.

Como a sua organização também pode revolucionar a maneira como ela trabalha com os dados? Vamos ajudar você a entender isso contando a história do nosso percurso de transformação de BI.

## <a name="microsoft-journey"></a>O percurso da Microsoft

Há vários anos na Microsoft, a cultura organizacional incentivava os indivíduos a buscar a propriedade total de dados e informações. Também havia forte resistência cultural a fazer as coisas de um modo padronizado. Portanto, a cultura organizacional levou a desafios de relatórios e de análise. Especificamente, levou a:

- Definições de dados, hierarquias, métricas e KPIs (indicadores chave de desempenho) inconsistentes. Por exemplo, cada país tinha a própria maneira de relatar novas receitas. Não havia nenhuma consistência, mas muita confusão.
- Os analistas gastavam 75% do tempo coletando e compilando dados.
- Entre os relatórios, 78% eram criados em "ambiente offline".
- Mais de 350 ferramentas e sistemas de finanças centralizados.
- Gasto anual de cerca de US$ 30 milhões em "aplicativos de sombra".

Esses desafios nos levaram a pensar em como poderíamos fazer as coisas de um modo melhor. As equipes de finanças e outras equipes internas receberam suporte executivo para transformar o processo de análise de negócios, que levou à criação de uma plataforma de BI unificada como a única fonte de verdade. (Discutiremos mais sobre nossa plataforma de BI adiante neste artigo.) Por fim, essas inovações levaram à transformação das análises de negócios de exibições de tabela densas em visuais mais simples e detalhados com foco nos principais temas comerciais.

Como atingimos esse resultado bem-sucedido? Fornecer um BI centralizado gerenciado pela TI e estendê-lo com a SSBI (BI por autoatendimento) levou ao sucesso. Descrevemos isso de duas maneiras criativas: _disciplina no centro_ e _flexibilidade na borda_.

### <a name="discipline-at-the-core"></a>Disciplina no centro

A disciplina no centro significa que a TI retém o controle, consultando uma única fonte de dados mestra. Ter uma BI corporativa padronizada e definir taxonomias e hierarquias de KPIs consistentes fazem parte dessa disciplina. O mais importante é que as permissões de dados são impostas centralmente para garantir que nosso pessoal possa ler apenas os dados de que precisam.

Primeiro, compreendemos que nossa transformação de BI não era um problema de tecnologia. Para obter o sucesso, aprendemos primeiro a definir o sucesso e então o converter em métricas-chave. Nunca é demais ressaltar a importância de obtermos consistência de definição em nossos dados.

Nossa transformação não aconteceu de uma só vez. Priorizamos a entrega do scorecard auxiliar consistindo em cerca de 30 KPIs. Então, em vários anos, expandimos gradualmente o número e a profundidade das áreas de assunto e criamos hierarquias de KPI mais complexas. Atualmente, ele nos permite acumular KPIs de nível inferior no nível do cliente até os mais altos no nível da empresa. Agora temos mais de 2 mil KPIs, sendo cada um deles uma medida importante de sucesso alinhada aos objetivos corporativos. Agora, em toda a empresa, os relatórios corporativos e as soluções SSBI apresentam KPIs que são bem definidos, consistentes e seguros.

### <a name="flexibility-at-the-edge"></a>Flexibilidade na borda

Na borda do centro, nossos analistas das equipes de finanças, vendas e marketing se tornaram mais flexíveis e ágeis. Agora eles se beneficiam da capacidade de analisar dados mais rapidamente. Em termos mais formais, esse cenário é descrito como _BI SSBI (Bi por autoatendimento gerenciado)_ . Agora entendemos que o SSBI gerenciado é sobre _benefício mútuo_ para a TI e os analistas. É importante dizer que obtivemos otimizações orientando a padronização, o conhecimento e a reutilização de nossos dados e soluções de BI. E, como empresa, extraímos mais valor de modo sinérgico, pois encontramos o equilíbrio certo entre a BI centralizado e o SSBI gerenciado.

### <a name="our-solution"></a>Nossa solução

**Starlight** é o nome que demos à nossa plataforma de análise e unificação de dados interna, que dá suporte a finanças, vendas, marketing e engenharia. Sua missão é fornecer uma plataforma de dados robusta, compartilhada e escalonável. A plataforma foi criada inteiramente pela área de finanças e continua em operação hoje usando os produtos mais recentes da Microsoft.

O **KPI Lake** não é um Azure Data Lake. Em vez disso, é um modelo de tabela desenvolvido com o Starlight hospedado na IaaS do Azure usando o Microsoft SQL Server Analysis Services. O modelo de tabela entrega dados da fonte de mais de 100 fontes internas e define várias hierarquias e KPIs. Sua missão é habilitar relatórios de desempenho de negócios e equipes de análise em finanças, marketing e vendas. Ele faz isso para obter informações oportunas, precisas e com bom desempenho por meio de modelos unificados de fontes relevantes.

A primeira vez em que foi implantado foi um momento empolgante, pois o modelo de tabela resultou em benefícios imediatos e mensuráveis. A primeira versão centralizou as plataformas de BI de marketing e finanças C+E. Em seguida, nos últimos seis anos, foi expandido para consolidar soluções de insights de negócios adicionais. Hoje, continua evoluindo, capacitando nossas análises de negócios globais e comerciais, bem como relatórios padrão e SSBI. Sua adoção aumentou cinco vezes desde seu lançamento, bem além das nossas expectativas iniciais.

Aqui está um resumo dos principais benefícios:

- Ele alimenta nosso scorecard auxiliar, análises de negócios mundiais e relatórios e análises de finanças, marketing, vendas.
- Ele dá suporte à análise por autoatendimento, permitindo que os analistas descubram informações ocultas nos dados.
- Ele orienta relatórios e análises para compensação de incentivos, análise de marketing e operações, métricas de desempenho de vendas, análises da liderança sênior e processo de planejamento anual.
- Ele fornece relatórios e análises automatizados e dinâmicos de uma _única fonte de verdade_.

O **KPI Lake** é uma ótima história de sucesso. Geralmente, é apresentado aos clientes para demonstrar um exemplo de como usar efetivamente nossas tecnologias mais recentes. Não é surpresa que ressoe fortemente em muitos deles.

#### <a name="how-it-works"></a>Como funciona

A plataforma Starlight gerencia o fluxo de dados da aquisição até o processamento e a publicação:

1. A integração de dados robusta e ágil ocorre de modo agendado, consolidando dados de mais de 100 fontes brutas diferentes. Os sistemas de dados de origem incluem bancos de dados relacionais, Azure Data Lake Storage e bancos do Azure Synapse. As áreas de assunto incluem finanças, marketing, vendas e engenharia.
2. Depois de preparado, os dados são adequados e aprimorados usando os dados mestres e a lógica de negócios. Em seguida, são carregados para tabelas do data warehouse. O modelo de tabela então é atualizado.
3. Os analistas de toda a empresa usam o Excel e o Power BI para fornecer informações e análises do modelo de tabela. E ele permite que os proprietários de negócios liderem definições de métricas para seus próprios negócios. Quando necessário, o dimensionamento é obtido usando a IaaS do Azure com balanceamento de carga.

## <a name="deliver-success"></a>Alcançar o sucesso

É engraçado que todos querem uma única versão da verdade… desde que seja a sua. Porém, para algumas organizações, essa é a realidade. Elas têm diversas versões da verdade como resultado de as pessoas buscarem propriedade total de dados e informações. Para essas organizações, essa abordagem não gerenciada provavelmente não é um caminho para o sucesso dos negócios.

É por isso que acreditamos que você precisa de um _COE (centro de excelência)_ . Um COE é uma equipe central responsável pela definição de métricas e definições de toda a empresa e muito mais. Também é uma função de negócios que organiza as pessoas, os processos e os componentes de tecnologia em um conjunto abrangente de competências e recursos de negócios.

Vemos muita evidência para embasar que ter um COE abrangente e robusto é essencial para fornecer valor e maximizar o sucesso dos negócios. Ele pode incluir iniciativas de mudança, processos padrão, funções, diretrizes, práticas recomendadas, suporte, treinamento e muito mais.

Convidamos você a ler os artigos desta série de COE para saber mais. Vamos ajudar você a descobrir como sua organização pode acolher a mudança para atingir o sucesso.

## <a name="next-steps"></a>Próximas etapas

No [próximo artigo desta série](center-of-excellence-establish.md), saiba como um COE ajudou a Microsoft a criar uma plataforma de dados e análise padronizada para revelar informações de nossos dados.

Para obter mais informações sobre este artigo, confira os seguintes recursos:

- [Estabelecer um centro de excelência](center-of-excellence-establish.md)
- Dúvidas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
- Sugestões? [Contribuir com ideias para aprimorar o Power BI](https://ideas.powerbi.com/)
