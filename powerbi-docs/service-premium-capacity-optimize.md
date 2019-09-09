---
title: Otimizar as capacidades do Microsoft Power BI Premium
description: Descreve estratégias de otimização para capacidades do Power BI Premium.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/09/2019
ms.custom: seodec18
LocalizationGroup: Premium
ms.openlocfilehash: 1fb775bd203fc1e0f6342a0d5cd4d9e382b8342a
ms.sourcegitcommit: 9665997274301b228f45aa7250ba557e90164a4d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70750933"
---
# <a name="optimizing-premium-capacities"></a>Otimização de capacidades Premium

Quando surgem problemas de desempenho de capacidade Premium, uma primeira abordagem comum é otimizar ou ajustar suas soluções para restaurar tempos de resposta aceitáveis. A lógica é evitar a compra de capacidade Premium adicional, a menos que seja justificada.

Quando a capacidade Premium adicional é necessária, há duas opções descritas neste artigo:

- Escalar verticalmente uma capacidade Premium existente
- Adicionar uma nova capacidade Premium

Por fim, as abordagens de teste e o dimensionamento da capacidade Premium concluem este artigo.

## <a name="best-practices"></a>Práticas recomendadas

Ao tentar obter a melhor utilização e desempenho, há algumas práticas recomendadas, incluindo:

- Usar workspaces de aplicativo em vez de workspaces pessoais.
- Separar o SSBI (BI de autoatendimento e comercialmente crítico) em diferentes capacidades.

  ![Separar o BI de Autoatendimento e comercialmente crítico em diferentes capacidades](media/service-premium-capacity-optimize/separate-capacities.png)

- Se estiver compartilhando conteúdo apenas com usuários do Power BI Pro, talvez não seja necessário armazenar o conteúdo em uma capacidade dedicada.
- Use capacidades dedicadas ao procurar atingir um tempo de atualização específico ou quando recursos específicos forem necessários. Por exemplo, com grandes conjuntos de altos ou relatórios paginados.

### <a name="addressing-common-questions"></a>Tratando de perguntas comuns

A otimização de implantações do Power BI Premium é um assunto complexo que envolve uma compreensão dos requisitos de carga de trabalho, recursos disponíveis e seu uso efetivo.

Este artigo aborda sete perguntas comuns de suporte, descrevendo possíveis problemas e explicações e informações sobre como identificá-los e resolvê-los.

### <a name="why-is-the-capacity-slow-and-what-can-i-do"></a>Por que a capacidade está lenta e o que posso fazer?

Há muitas razões que podem contribuir para uma capacidade Premium lenta. Essa pergunta requer mais informações para entender o que significa lentidão. Os relatórios estão lentos para carregar? Ou eles estão falhando ao carregar? Os visuais de relatório são lentos para carregar ou atualizar quando os usuários interagem com o relatório? As atualizações estão demorando mais para serem concluídas do que o esperado ou do que antes?

Depois de entender o motivo, você pode começar a investigar. As respostas às seis perguntas a seguir ajudarão você a resolver problemas mais específicos.

### <a name="what-content-is-using-up-my-capacity"></a>Qual conteúdo está esgotando minha capacidade?

Você pode usar o aplicativo **Métricas de Capacidade do Power BI Premium** para filtrar por capacidade e examinar as métricas de desempenho do conteúdo do workspace. É possível examinar as métricas de desempenho e o uso de recursos por hora nos últimos sete dias para todo o conteúdo armazenado em uma capacidade Premium. O monitoramento é geralmente a primeira etapa a ser tomada ao solucionar problemas de uma preocupação geral sobre o desempenho da capacidade Premium.

As principais métricas a serem monitoradas incluem:

- CPU média e contagem de alta utilização.
- Memória Média e contagem de alta utilização, além de uso de memória para conjuntos de dados específicos, fluxos de dados e relatório paginados.
- Conjuntos de valores ativos carregados na memória.
- Durações de consulta média e máxima.
- Tempos médios de espera de consulta.
- Tempo médios de atualização de fluxo de dados e conjunto de dados.

No aplicativo de Métricas de Capacidade Power BI Premium, a memória ativa mostra a quantidade total de memória fornecida a um relatório que não pode ser removida porque está em uso nos últimos três minutos. Um alto pico no tempo de espera de atualização pode ser correlacionado a um conjunto de um grande e/ou ativo.

O gráfico de **Cinco Principais por Duração Média** destaca os cinco principais conjuntos de dados, relatórios paginados e fluxos de dados que consomem recursos de capacidade. O conteúdo nas lista dos cinco principais é candidato à investigação e possível otimização.

### <a name="why-are-reports-slow"></a>Por que os relatórios estão lentos?

As tabelas a seguir mostram possíveis problemas e maneiras de identificá-los e tratá-los.

#### <a name="insufficient-capacity-resources"></a>Recursos de capacidade insuficientes

| Possíveis Explicações | Como Identificar | Como Resolver |
| --- | --- | --- |
| Memória ativa total alta (o modelo não pode ser removido porque está em uso nos últimos três minutos).<br><br> Vários picos altos nos tempos de espera da consulta.<br><br> Vários picos altos nos tempos de espera da atualização. | Monitore as métricas de memória \[[1](#endnote-1)\] e as contagens de remoção \[[2](#endnote-2)\]. | Diminua o tamanho do modelo ou converta no modo DirectQuery. Veja a seção [Otimizando modelos](#optimizing-models) neste artigo.<br><br> Aumente a capacidade.<br><br> Atribua o conteúdo a uma capacidade diferente. |

#### <a name="inefficient-report-designs"></a>Designs de relatório ineficientes

| Possíveis Explicações | Como Identificar | Como Resolver |
| --- | --- | --- |
| As páginas do relatório contêm muitos visuais (a filtragem interativa pode disparar pelo menos uma consulta por visual).<br><br> Os visuais recuperam mais dados do que o necessário. | Examine os designs de relatório.<br><br> Entreviste os usuários de relatório para entender como eles interagem com os relatórios.<br><br> Monitore as métricas de consulta do conjunto de dados \[[3](#endnote-3)\]. | Recrie relatórios com menos visuais por página. |

#### <a name="dataset-is-slow-especially-when-reports-have-previously-performed-well"></a>O conjunto de dados está lento, especialmente quando os relatórios já foram bem executados

| Possíveis Explicações | Como Identificar | Como Resolver |
| --- | --- | --- |
| Volumes cada vez maiores de dados de importação.<br><br> Lógica de cálculo complexa ou ineficiente, incluindo funções de RLS.<br><br> Modelo não totalmente otimizado.<br><br> (DQ/LC) Latência do gateway.<br><br> Tempos de resposta de consulta de origem do DQ lentos. | Examine os designs de modelo.<br><br> Monitore os contadores de desempenho do gateway. | Veja a seção [Otimizando modelos](#optimizing-models) neste artigo. |

#### <a name="high-concurrent-report-usage"></a>Alto uso de relatório simultâneo

| Possíveis Explicações | Como Identificar | Como Resolver |
| --- | --- | --- |
| Tempos de espera de consulta elevados.<br><br> Saturação da CPU.<br><br> Limites de conexão do DQ/LC excedidos. | Monitore a utilização da CPU \[[4](#endnote-4)\], os tempos de espera da consulta e as métricas de utilização do DQ/LC \[[5](#endnote-5)\] + durações da consulta. Se estiverem flutuando, isso poderá indicar problemas de simultaneidade. | Aumente a capacidade ou atribua o conteúdo a uma capacidade diferente.<br><br> Recrie relatórios com menos visuais por página. |

**Observações:**    
<a name="endnote-1"></a>\[1\] Uso Médio de Memória (GB) e Maior Consumo de Memória (GB).   
<a name="endnote-2"></a>\[2\] Remoções de conjunto de dados.   
<a name="endnote-3"></a>\[3\] Consultas de Conjunto de Dados, Duração Média da Consulta de Conjunto de Dados (ms), Contagem de Espera de Conjunto de Dados e Tempo de Espera Médio (ms).   
<a name="endnote-4"></a>\[4\] Contagem de Alta Utilização de CPU e Tempo de Utilização Mais Alta de CPU (últimos sete dias).   
<a name="endnote-5"></a>\[5\] Contagem de Alta Utilização de DQ/LC e Tempo de Utilização Mais Alta de DQ/LC (últimos sete dias).   

### <a name="why-are-reports-not-loading"></a>Por que os relatórios não estão sendo carregados?

Quando os relatórios não são carregados, é claro que a capacidade tem memória insuficiente e está superaquecida. Isso pode ocorrer quando todos os modelos carregados estão sendo consultados ativamente e, portanto, não podem ser removidos e todas as operações de atualização foram pausadas ou atrasadas. O serviço do Power BI tentará carregar o conjunto de dados por 30 segundos e o usuário será notificado normalmente sobre a falha com uma sugestão para tentar novamente em breve.

Atualmente, não há métrica para monitorar falhas de carregamento de relatório. Você pode identificar o potencial desse problema monitorando a memória do sistema, especificamente a maior utilização e a hora de utilização mais alta. Altas remoções de conjunto de dados e longos tempos de espera médios de atualização do conjunto de dados podem sugerir que esse problema está ocorrendo.

Se isso ocorrer apenas algumas vezes, talvez não seja considerado um problema prioritário. Os usuários de relatório são informados de que o serviço está ocupado e que devem tentar novamente após um curto período. Se isso ocorrer com muita frequência, o problema poderá ser resolvido expandindo a capacidade Premium ou atribuindo o conteúdo a uma capacidade diferente.

Os administradores de capacidade (e administradores de serviço do Power BI) podem monitorar a métrica de **Falhas de Consulta** para determinar quando isso acontece. Eles também podem reiniciar a capacidade, redefinindo todas as operações em caso de sobrecarga do sistema.

### <a name="why-are-refreshes-not-starting-on-schedule"></a>Por que as atualizações não são iniciadas no prazo?

As horas de início da atualização agendada não são garantidas. Lembre-se de que o serviço do Power BI sempre priorizará operações interativas em operações em segundo plano. A atualização é uma operação em segundo plano que pode ocorrer quando duas condições são atendidas:

- Há memória suficiente
- O número de atualizações simultâneas com suporte para a capacidade Premium não é excedido

Quando as condições não forem atendidas, a atualização será enfileirada até que as condições sejam favoráveis.

Para uma atualização completa, lembre-se de que pelo menos o tamanho da memória do conjunto de dados atual é necessário. Se não houver memória suficiente disponível, a atualização não poderá ser iniciada até que a remoção do modelo libere memória – isso significa atrasos até que um ou mais conjuntos de valores se tornem inativos e possam ser removidos.

Lembre-se de que o número com suporte de atualizações simultâneas máximas é definido como 1,5 vez os núcleos virtuais de back-end, arredondados.

Uma atualização agendada falhará quando não for possível começar antes da próxima atualização agendada devido ao início. Uma atualização sob demanda disparada manualmente da interface do usuário tentará executar até três vezes antes de falhar.

O administrador de capacidade (e os administradores de serviço do Power BI) pode monitorar a métrica **Tempo Médio de Espera de Atualização (minutos)** para determinar o atraso médio entre a hora agendada e o início da operação.

Embora normalmente não seja uma prioridade administrativa, para influenciar as atualizações de dados no prazo, verifique se há memória suficiente disponível. Isso pode envolver o isolamento de conjuntos de valores para capacidades com recursos suficientes conhecidos. Também é possível que os administradores possam coordenar com os proprietários do conjunto de dados para ajudar a escalonar ou reduzir os tempos de atualização agendados para minimizar as colisões. Observe que não é possível que um administrador exiba a fila de atualização ou recupere agendas de conjunto dados.

### <a name="why-are-refreshes-slow"></a>Por que as atualizações são lentas?

As atualizações podem ser lentas ou percebidas como lentas (como as pergunta comuns anteriores abordam).

Quando a atualização é, na verdade, lenta, isso pode ser devido a vários motivos:

- CPU insuficiente (a atualização pode fazer uso intenso da CPU).
- Memória insuficiente, resultando na pausa da atualização (o que exige que a atualização seja reiniciada quando as condições são favoráveis para reinicializar).
- Motivos de não capacidade, incluindo a capacidade de resposta do sistema de fonte de dados, latência de rede, permissões inválidas ou taxa de transferência do gateway.
- Volume de dados – um bom motivo para configurar a atualização incremental, conforme discutido abaixo.

Os administradores de capacidade (e os administradores de serviço do Power BI) pode monitorar a métrica **Média de Duração de Atualização (minutos)** para determinar um parâmetro de comparação ao longo do tempo e as métricas **Tempo Médio de Espera de Atualização (minutos)** para determinar o atraso médio entre a hora agendada e o início da operação.

A atualização incremental pode reduzir significativamente a duração da atualização de dados, especialmente para grandes tabelas de modelo. Há quatro benefícios associados à atualização incremental:

- **As atualizações são mais rápidas** – apenas um subconjunto de uma tabela precisa ser carregado, reduzindo o uso de CPU e de memória e o paralelismo pode ser maior ao atualizar várias partições.
- **As atualizações ocorrem somente quando necessário** – as políticas de atualização incremental podem ser configuradas para carregar somente quando os dados forem alterados.
- **As atualizações são mais confiáveis** – conexões de execução mais curtas para sistemas de fonte de dados voláteis são menos suscetíveis à desconexão.
- **Os modelos permanecem organizados** – as políticas de atualização incremental podem ser configuradas para remover automaticamente o histórico além de uma janela dinâmica de tempo.

Para saber mais, confira [Atualização incremental no Power BI Premium](service-premium-incremental-refresh.md).

### <a name="why-are-data-refreshes-not-completing"></a>Por que as atualizações de dados não estão sendo concluídas?

Quando a atualização de dados começa, mas não é concluída, pode ser devido a vários motivos:

- Memória insuficiente, mesmo se houver apenas um modelo na capacidade Premium, ou seja, o tamanho do modelo é muito grande.
- Motivos de não capacidade, incluindo a desconexão do sistema da fonte dados, permissões inválidas ou erro de gateway.

Os administradores de capacidade (e administradores de serviço do Power BI) podem monitorar a métrica **Falhas de Atualização devido a memória insuficiente**.

## <a name="optimizing-models"></a>Otimizando modelos

O design de modelo ideal é crucial para a entrega de uma solução eficiente e escalonável. No entanto, está além do escopo deste artigo fazer uma discussão completa. Em vez disso, esta seção mostrará as principais áreas para otimizar modelos.

### <a name="optimizing-power-bi-hosted-models"></a>Otimizando modelos hospedados no Power BI

A otimização de modelos hospedados em uma capacidade Premium pode ser obtida nas camadas de fontes de dados e modelo.

Considere as possibilidades de otimização para um modelo de Importação:

![Possibilidades de otimização para um modelo de Importação](media/service-premium-capacity-optimize/import-model-optimizations.png)

Na camada do datasource:

- As fontes de dados relacionais podem ser otimizadas para garantir a atualização mais rápida possível, aplicando os índices apropriados, definindo as partições de tabela que se alinham aos períodos de atualização incremental e materializando os cálculos (no lugar de tabelas e colunas de modelo calculadas) ou adicionando lógica a exibições.
- As fontes de dados não relacionais podem ser previamente integradas a repositórios relacionais.
- Verifique se os gateways têm recursos suficientes, preferencialmente em computadores dedicados, com largura de banda de rede suficiente e em proximidade com as fontes de dados.

Na camada de modelo:

- Os designs de consulta do Power Query podem minimizar ou remover transformações complexas e especialmente aquelas que mesclam diferentes fontes de dados (data warehouses fazem isso durante o estágio Extract-Transform-Load). Além disso, garantir que os níveis de privacidade de fonte de fontes apropriados sejam definidos pode evitar a necessidade de o Power BI carregar resultados completos para produzir um resultado combinado entre consultas.
- A estrutura do modelo determina os dados a serem carregados e tem um impacto direto no tamanho do modelo. Ela pode ser projetada para evitar o carregamento de dados desnecessários removendo colunas, removendo linhas (especialmente dados históricos) ou carregando dados resumidos (à custa de carregar dados detalhados). A redução drástica de tamanho pode ser obtida removendo colunas de alta cardinalidade (especialmente colunas de texto) que não são armazenadas nem compactadas com muita eficiência.
- O desempenho de consulta de modelo pode ser melhorado configurando relações de direção única, a menos que haja um motivo convincente para permitir a filtragem bidirecional. Considere também usar a função [CROSSFILTER](https://docs.microsoft.com/dax/crossfilter-function), em vez de filtragem bidirecional.
- As tabelas de agregação podem obter respostas de consulta rápidas carregando dados previamente resumidos, no entanto, isso aumentará o tamanho do modelo e resultará em tempos de atualização mais longos. Em geral, as tabelas de agregação devem ser reservadas para modelos muito grandes ou designs de modelo Composto.
- As tabelas e colunas calculadas aumentam o tamanho do modelo e resultam em tempos de atualização mais longos. Em geral, um tamanho de armazenamento menor e o tempo de atualização mais rápido podem ser obtidos quando os dados são materializados ou calculados na fonte de dados. Se isso não for possível, usar colunas personalizadas do Power Query poderá oferecer uma compactação de armazenamento aprimorada.
- Pode haver oportunidade para ajustar expressões DAX para medidas e regras de RLS, talvez reescrevendo a lógica para evitar fórmulas de alto custo
- A atualização incremental pode reduzir drasticamente o tempo de atualização e preservar a memória e a CPU. A atualização incremental também pode ser configurada para remover os tamanhos de modelo de manutenção de dados históricos.
- Um modelo pode ser reprojetado como dois modelos quando há padrões de consulta diferentes e conflitantes. Por exemplo, alguns relatórios apresentam agregações de alto nível sobre todo o histórico e podem tolerar a latência de 24 horas. Outros relatórios se preocupam com os dados de hoje e precisam de acesso granular a transações individuais. Em vez de criar um único modelo para atender a todos os relatórios, crie dois modelos otimizados para cada requisito.

Considere as possibilidades de otimização para um modelo de DirectQuery. Como o modelo emite solicitações de consulta para a fonte de dados subjacente, a otimização da fonte de dados é crítica para fornecer consultas de modelo responsivas.

 ![Possibilidades de otimização para um modelo de DirectQuery](media/service-premium-capacity-optimize/direct-query-model-optimizations.png)

Na camada do datasource:

- A fonte de dados pode ser otimizada para garantir a consulta mais rápida possível por meio de pré-integração de dados (o que não é possível na camada do modelo), aplicação de índices apropriados, definição de partições de tabela, materialização de dados resumidos (com exibições indexadas) e minimização da quantidade de cálculo. A melhor experiência é obtida quando as consultas de passagem precisam apenas filtrar e executar junções internas entre tabelas ou exibições indexadas.
- Verifique se os gateways têm recursos suficientes, preferencialmente em computadores dedicados, com largura de banda de rede suficiente e em proximidade com a fonte de dados.

Na camada de modelo:

- Os designs de consulta do Power Query devem, de preferência, não aplicar nenhuma transformação – caso contrário, tente manter as transformações a um mínimo absoluto.
- O desempenho de consulta de modelo pode ser melhorado configurando relações de direção única, a menos que haja um motivo convincente para permitir a filtragem bidirecional. Além disso, as relações de modelo devem ser configuradas para presumir que a integridade referencial é imposta (quando esse for o caso) e resultará em consultas de fonte de dados usando junções internas mais eficientes (em vez de junções externas).
- Evite criar colunas personalizadas de consulta ou coluna calculada de modelo do Power Query, materializando-as na fonte de fontes, quando possível.
- Pode haver oportunidade para ajustar expressões DAX para medidas e regras de RLS, talvez reescrevendo a lógica para evitar fórmulas de alto custo.

Considere as possibilidades de otimização para um modelo Composto. Lembre-se de que um modelo Composto permite uma combinação de tabelas de importação e DirectQuery.

![Possibilidades de otimização para um modelo composto](media/service-premium-capacity-optimize/composite-model-optimizations.png)

- Em geral, a otimização dos modelos de importação e DirectQuery aplicam-se a tabelas de modelo Composto que usam esses modos de armazenamento.
- Normalmente, busque obter um design equilibrado configurando tabelas do tipo de dimensão (representando entidades de negócios) como modo de armazenamento Duplo e tabelas do tipo de fato (muitas vezes, tabelas grandes, representando fatos operacionais) como modo de armazenamento DirectQuery. O modo de armazenamento duplo significa os modos de armazenamento de Importação e DirectQuery, e isso permite que o serviço do Power BI determine o modo de armazenamento mais eficiente a ser usado ao gerar uma consulta nativa para passagem.
- Verifique se os gateways têm recursos suficientes, preferencialmente em computadores dedicados, com largura de banda de rede suficiente e em proximidade com as fontes de dados
- As tabelas de agregações configuradas como modo de armazenamento de Importação podem fornecer melhorias consideráveis de desempenho de consulta quando usadas para resumir as tabelas do tipo fato do modo de armazenamento DirectQuery. Nesse caso, as tabelas de agregação aumentarão o tamanho do modelo e aumentarão o tempo de atualização e, muitas vezes, essa é uma compensação aceitável para consultas mais rápidas.

### <a name="optimizing-externally-hosted-models"></a>Otimizando modelos hospedados externamente

Muitas possibilidades de otimização discutidas na seção [Otimizando modelos hospedados do Power BI](#optimizing-power-bi-hosted-models) se aplicam também a modelos desenvolvidos com Azure Analysis Services e com o SQL Server Analysis Services. As exceções claras são determinados recursos que não têm suporte no momento, incluindo modelos compostos e tabelas de agregação.

Uma consideração adicional para conjuntos de dados hospedados externamente é a hospedagem de banco de dados em relação ao serviço do Power BI. Para o Azure Analysis Services, isso significa criar o recurso do Azure na mesma região que o locatário do Power BI (região de residência). Para o SQL Server Analysis Services, para IaaS, isso significa hospedar a VM na mesma região e, para o local, significa garantir uma configuração de gateway eficiente.

Além disso, pode ser interessante observar que os bancos de dados do Azure Analysis Services e os bancos de dados de tabela do SQL Server Analysis Services exigem que seus modelos sejam carregados totalmente na memória e que permaneçam lá sempre para dar suporte à consulta. Assim como o serviço do Power BI, precisa haver memória suficiente para atualizar se o modelo precisar permanecer online durante a atualização. Ao contrário do serviço do Power BI, não há nenhum conceito de que os modelos sejam automaticamente inseridos e removidos da memória conforme o uso. O Power BI Premium, portanto, oferece uma abordagem mais eficiente para maximizar a consulta de modelo com menor uso de memória.

## <a name="capacity-planning"></a>Planejamento da capacidade

O tamanho de uma capacidade Premium determina sua memória disponível e os limites e recursos de processador impostos sobre a capacidade. O número de capacidades Premium também deve ser considerado, pois a criação de várias capacidades Premium pode ajudar a isolar as cargas de trabalho umas das outras. Observe que o armazenamento é de 100 TB por nó de capacidade, e isso provavelmente será mais do que suficiente para qualquer carga de trabalho.

Determinar o tamanho e o número de capacidades Premium pode ser desafiador, especialmente para as capacidades iniciais que você criar. A primeira etapa ao dimensionar a capacidade é entender a carga de trabalho média que representa o uso esperado do dia a dia. É importante entender que nem todas as cargas de trabalho são iguais. Por exemplo, em um lado do espectro, é fácil atingir 100 usuários simultâneos acessando uma única página de relatório que contém um único Visual. No entanto, no outro lado do espectro, 100 usuários simultâneos que acessam 100 relatórios diferentes, cada um com 100 visuais na página de relatório, vão impor demandas muito diferentes de recursos de capacidade.

Portanto, os administradores de capacidade precisarão considerar muitos fatores específicos do ambiente, do conteúdo e do uso esperado. O objetivo de substituição é maximizar a utilização da capacidade e, ao mesmo tempo, fornecer tempos de consulta consistentes, tempos de espera aceitáveis e taxas de remoção. Os fatores a serem considerados podem incluir:

- **Características de dados e tamanho do modelo** – os modelos de importação devem ser totalmente carregados na memória para permitir a consulta ou a atualização. Os conjuntos de dados de LC/DQ podem exigir um tempo de processador significativo e possivelmente uma memória significativa para avaliar medidas complexas ou regras de RLS. A memória e o tamanho do processador e a taxa de transferência de consulta LC/DQ são restritos pelo tamanho da capacidade.
- **Modelos ativos simultâneos** – a consulta simultânea de diferentes modelos de importação fornecerá melhor capacidade de resposta e desempenho quando eles permanecerem na memória. Deve haver memória suficiente para hospedar todos os modelos de consulta intensa, com memória adicional para permitir sua atualização.
- **Atualização do modelo de importação** – o tipo de atualização (completo ou incremental), a duração e a complexidade das consultas do Power Query e a lógica de tabela/coluna calculada podem afetar a memória e, principalmente, o uso do processador. As atualizações simultâneas são restritas pelo tamanho da capacidade (1,5 x v-cores de back-end, arredondado).
- **Consultas simultâneas** – muitas consultas simultâneas podem resultar em relatórios sem resposta quando o processador ou as conexões de LC/DQ excedem o limite de capacidade. Isso é especialmente o caso para páginas de relatório que incluem muitos elementos visuais.
- **Fluxos de entrada e relatórios paginados** – a capacidade pode ser configurada para dar suporte a fluxos de dados e a relatórios paginados, cada um exigindo um percentual máximo configurável de memória de capacidade. A memória é dinamicamente alocada para fluxos de dados, mas é alocada estaticamente para relatórios paginados.

Além desses fatores, os administradores de capacidade podem considerar a criação de várias capacidades. Várias capacidades permitem o isolamento de cargas de trabalho e podem ser configuradas para garantir que as cargas de trabalho prioritárias tenham recursos garantidos. Por exemplo, duas capacidades podem ser criadas para separar cargas de trabalho críticas para os negócios de cargas de trabalho SSBI (BI de autoatendimento). A capacidade comercialmente crítica pode ser usada para isolar grandes modelos corporativos, fornecendo a eles recursos garantidos, com o acesso concedido somente ao departamento de TI. A capacidade do SSBI pode ser usada para hospedar um número cada vez maior de modelos menores, com acesso concedido a analistas de negócios. A capacidade SSBI pode às vezes ter esperas de consulta ou atualização toleráveis.

Ao longo do tempo, os Administradores de Capacidade podem balancear os workspaces entre as capacidades movendo o conteúdo entre os workspaces ou workspaces entre as capacidades e dimensionando as capacidades para mais ou para menos. Em geral, para hospedar modelos maiores, você aumenta e, para uma simultaneidade maior, você expande.

Lembre-se de que comprar uma licença fornece ao locatário v-cores. A compra de uma assinatura **P3** pode ser usada para criar uma ou até quatro capacidades Premium, ou seja, 1 x P3 ou 2 x P2 ou 4 x P1. Além disso, antes de aumentar uma capacidade P2 para uma capacidade P3, pode-se considerar dividir os v-cores para criar duas capacidades P1.

## <a name="testing-approaches"></a>Abordagens de teste

Quando o tamanho da capacidade é decidido, o teste pode ser executado criando um ambiente controlado. Uma opção prática e econômica é criar uma capacidade do Azure (SKUs A), observando que uma capacidade P1 tem o mesmo tamanho que uma capacidade A4, tendo as capacidades P2 e P3 o mesmo tamanho que as capacidades A5 e A6, respectivamente. As capacidades do Azure podem ser criadas rapidamente e são cobradas por hora. Assim, quando o teste for concluído, elas poderão ser facilmente excluídas para interromper o acúmulo de custos.

O conteúdo do teste pode ser adicionado aos workspaces criados na capacidade do Azure e então, como um único usuário, pode executar relatórios para gerar uma carga de trabalho realista e representativa das consultas. Se houver modelos de importação, uma atualização para cada modelo também deverá ser executada. As ferramentas de monitoramento podem ser usadas para examinar todas as métricas para entender a utilização de recursos.

É importante que os testes sejam repetíveis. Os testes devem ser executados várias vezes e devem fornecer aproximadamente o mesmo resultado a cada vez. Uma média desses resultados pode ser usada para extrapolar e estimar uma carga de trabalho em condições de produção verdadeiras.

Se você já tiver uma capacidade e os relatórios para os quais deseja fazer o teste de carga, use a [ferramenta de geração de carga do PowerShell](https://aka.ms/PowerBILoadTestingTool) para gerar rapidamente um teste de carga. A ferramenta permite que você calcule quantas instâncias de cada relatório sua capacidade pode executar em uma hora. Você pode usar a ferramenta para avaliar a habilidade da capacidade de renderizar o relatório individual ou renderizar vários relatórios diferentes em paralelo. Para obter mais informações, veja o vídeo [Microsoft Power BI: Capacidade Premium](https://www.youtube.com/watch?time_continue=1860&v=C6vk6wk9dcw).

Para gerar um teste mais complexo, considere desenvolver um aplicativo de teste de carga que simule uma carga de trabalho realista. Para obter mais informações, veja o webinar [Teste de carga de aplicativos Power BI com o Teste de Carga do Visual Studio](https://powerbi.microsoft.com/en-us/blog/week-4-11-webinars-load-testing-power-bi-applications-with-visual-studio-load-test-and-getting-started-with-cds-for-apps-based-model-driven-apps/).

## <a name="acknowledgements"></a>Agradecimentos

Este artigo foi escrito por Peter Myers, MVP de plataforma de dados e especialista independente de BI da [Bitwise Solutions](https://www.bitwisesolutions.com.au/).

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Cenários de capacidade Premium](service-premium-capacity-scenarios.md)   
  
Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)

||||||