---
title: Práticas recomendadas de desempenho do Power BI
description: Este artigo oferece orientação para criar relatórios rápidos e confiáveis no Power BI
author: MarkMcGeeAtAquent
ms.author: kfile
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 07/30/2018
LocalizationGroup: Reports
ms.openlocfilehash: bddd653b5ac8b49a38a69ae79baf2f96824444ed
ms.sourcegitcommit: 805d52e57a935ac4ce9413d4bc5b31423d33c5b1
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68665329"
---
# <a name="power-bi-performance-best-practices"></a>Práticas recomendadas de desempenho do Power BI

Este artigo oferece orientação para criar relatórios rápidos e confiáveis no Power BI.  

## <a name="use-filters-to-limit-report-visuals-to-display-only-whats-needed"></a>Usar filtros para limitar os visuais de relatório para exibir apenas o que é necessário 

Quanto mais dados um visual precisar exibir, mais lentamente esse visual será carregado. Embora esse princípio pareça óbvio, é fácil esquecer. Por exemplo: suponha que você tenha um grande conjunto de dados. Sobre esse conjunto de dados, você cria um relatório com uma tabela da tabela. Os usuários finais usam segmentações na página para obter as linhas que desejam – normalmente eles só estão interessados em algumas dezenas de linhas.

Um erro comum é deixar o modo de exibição padrão da tabela não filtrado, ou seja, todas as mais de 100 milhões de linhas. Os dados dessas linhas são carregados na memória e descompactados a cada atualização. Esse processamento cria grandes carregamentos de memória. A solução: use o filtro “Os N principais” para reduzir o número máximo de itens que a tabela exibe. É possível definir o item máximo como maior do que o que usuários precisam, por exemplo, 10 mil. O resultado é que a experiência do usuário final não muda, mas o uso da memória cai muito. E o desempenho melhora.

Uma abordagem semelhante a acima é recomendável para todos os visuais em seus relatórios. Pergunte-se: todos os dados neste visual são necessários? Existem maneiras de filtrar a quantidade de dados mostrados no visual com impacto mínimo na experiência do usuário final? Tabelas, em particular, podem ser caras.

## <a name="limit-visuals-on-report-pages"></a>Limitar visuais em páginas do relatório

O princípio acima aplica-se igualmente ao número de elementos visuais em um relatório específico. É altamente recomendável limitar o número de elementos visuais em determinado relatório para apenas o que é necessário. Detalhar as páginas é uma ótima maneira de fornecer detalhes adicionais sem aglomerar mais visuais no relatório.  

## <a name="optimize-your-model"></a>Otimizar o modelo

Algumas práticas recomendadas:

- Remova tabelas ou colunas não usadas, sempre que possível. 
- Evite contagens distintas em campos com alta cardinalidade, ou seja, milhões de valores distintos.  
- Tome medidas para evitar campos com precisão desnecessária e alta cardinalidade. Por exemplo, você pode dividir valores datetime altamente exclusivos em colunas separadas, por exemplo, mês, ano, data e assim por diante. Ou, quando possível, use o arredondamento em campos de alta precisão para diminuir a cardinalidade (por exemplo, 13,29889 -> 13,3).
- Use números inteiros em vez de cadeias de caracteres, sempre que possível.
- Fique atento a funções DAX que precisam testar cada linha em uma tabela, por exemplo, RANKX. No pior dos casos, essas funções podem aumentar exponencialmente o tempo de execução e os requisitos de memória devido ao aumento linear no tamanho da tabela.
- Ao se conectar a fontes de dados por meio do DirectQuery, considere indexar novamente as colunas que normalmente são filtradas ou segmentadas. A indexação melhora muito a capacidade de resposta do relatório.  

Para saber mais sobre como otimizar fontes de dados para o DirectQuery, confira [DirectQuery no SQL Server 2016 Analysis Services](https://blogs.msdn.microsoft.com/analysisservices/2017/04/06/directquery-in-sql-server-2016-analysis-services-whitepaper/).

## <a name="directquery-and-live-connection-understand-underlying-data-source-performance"></a>Conexão dinâmica e do DirectQuery: compreender o desempenho da fonte de dados subjacente

No caso de conexão dinâmica ou do DirectQuery, quando os usuários visitam um relatório do Power BI, o Power BI envia consultas tempo real para a fonte de dados subjacente. Depois que a fonte de dados for retornada com os dados da consulta, o relatório será renderizado. Como resultado, o desempenho do relatório depende muito do desempenho da fonte de dados subjacente.

Nesses casos, é importante entender o desempenho de sua fonte de dados subjacente. Fontes de dados diferentes têm ferramentas diferentes para entender o desempenho da consulta. Por exemplo, SQL Server e SQL Azure fornecem o Repositório de Consultas, que captura um histórico das consultas e suas estatísticas de tempo de execução.

Ao implantar relatórios do Power BI baseados em conexão dinâmica e do DirectQuery, experimente o que os usuários finais farão no Power BI Desktop. Se o relatório apresentar lentidão para ser carregado no Power BI Desktop, ele provavelmente terá lentidão para ser carregado no serviço para os usuários finais. 

## <a name="directquery-best-practices"></a>Práticas recomendadas do DirectQuery

A seção a seguir descreve as práticas recomendadas gerais para se conectar por meio do DirectQuery.
  
### <a name="db-design-guidance"></a>Diretrizes de design de BD

- Envie por push colunas calculadas e medidas para a origem sempre que possível. Quanto mais próximo à origem, maior a probabilidade de desempenho.
- Otimize! Entenda os planos de execução de suas consultas, adicione índices a colunas filtradas comumente e assim por diante.

### <a name="modeling-guidance"></a>Diretrizes de modelagem

- Inicie o Power BI Desktop.
- Evite consultas complexas no Editor de Consultas.
- Não use a filtragem de data relativa no Editor de Consultas.  
- Mantenha medidas simples inicialmente e adicione complexidade de forma incremental.
- Evite relacionamentos em colunas calculadas e colunas de identificador exclusivo.
- Tente configurar "Pressupor integridade referencial" nos relacionamentos – em muitos casos, essa configuração melhora significativamente o desempenho da consulta.  

### <a name="general"></a>Geral

- Aplique filtros primeiro.
- Considere a possibilidade de desativar a interação entre os visuais, que reduz a carga da consulta quando os usuários fazem destaque cruzado.
- Limite o número de elementos visuais e os dados por visuais, conforme descrito acima.
- Habilitar a segurança no nível de linha pode resultar em grandes alterações no desempenho. Teste as diferentes funções de segurança no nível de linha que os usuários assumirão.
- Há tempos limite de nível de consulta impostos pelo serviço para verificar se consultas de longa execução não podem monopolizar os recursos do sistema. Consultas que levam mais de 225 segundos atingem o tempo limite e resultam em um erro de nível do visual.

## <a name="understand-dashboards-and-query-caches"></a>Noções básicas sobre dashboards e caches de consulta

Os visuais fixados nos dashboards são servidos pelo cache de consulta quando o dashboard é carregado. Por outro lado, quando visitar um relatório, as consultas são feitas dinamicamente para a fonte de dados – o serviço do Power BI (no caso de importação) ou a fonte de dados que você especificar (no caso de conexão dinâmica e do DirectQuery).  

> [!NOTE]
> Quando você fixa blocos de relatório dinâmico em um dashboard, eles não são servidos do cache de consulta – em vez disso, eles se comportam como relatórios e fazem consultas a núcleos de back-end em tempo real.

Como o nome sugere, recuperar os dados do cache de consulta fornece um desempenho melhor e mais consistente do que contar com a fonte de dados. Uma maneira de aproveitar essa funcionalidade é ter painéis como a primeira página de aterrissagem para seus usuários. Fixe os visuais usados com frequência e altamente solicitados aos dashboards. Dessa forma, os dashboards tornam-se uma valiosa "primeira linha de defesa" que oferece desempenho consistente com menos carga na capacidade. Os usuários ainda podem clicar no relatório para examinar os detalhes.  
 

Para a conexão dinâmica e do DirectQuery, o cache de consulta é atualizado periodicamente ao consultar a fonte de dados. Por padrão, isso ocorre a cada hora; porém, isso pode ser definido nas configurações do conjunto de dados. Cada atualização de cache de consulta enviará consultas à fonte de dados subjacente para atualizar o cache. O número de consultas geradas depende do número de visuais fixados nos dashboards que dependem dessa fonte de dados. Observe que se a segurança em nível de linha estiver habilitada, as consultas serão geradas para cada contexto de segurança diferente. Por exemplo, se você tiver duas funções diferentes que categorizam seus usuários e eles tiverem duas exibições diferentes dos dados, durante a atualização do cache de consulta, o Power BI gerará dois conjuntos de consultas. 

## <a name="understand-custom-visual-performance"></a>Entender o desempenho do visual personalizado 

Coloque cada visual personalizado em execução para garantir alto desempenho. Visuais personalizados de forma precária podem afetar negativamente o desempenho de todo o relatório. 

## <a name="deep-dive-into-query-performance-with-sql-profiler-and-power-bi-desktop"></a>Aprofundamento no desempenho da consulta com o SQL Profiler e o Power BI Desktop

Para se aprofundar nos visuais que estão usando mais tempo e recursos, conecte o SQL Profiler ao Power BI Desktop para obter toda a exibição completa de desempenho da consulta.

> [!NOTE]
> O Power BI Desktop dá suporte à conexão a uma porta de diagnóstico. A porta de diagnóstico permite que outras ferramentas se conectem e executem rastreamentos para fins de diagnóstico. *Não há suporte para a realização de alterações ao modelo! Alterações ao modelo podem levar a dados corrompidos e a perda de dados.*

Veja as instruções a seguir:
  
1. **Instalar o SQL Server Profiler e executar o Power BI Desktop**

   O SQL Server Profiler está disponível como parte do SQL Server Management Studio.

2. **Determinar a porta que está sendo usada pelo Power BI Desktop**

   Execute o prompt de comando ou o PowerShell com privilégios de administrador. Além disso, use netstat para localizar a porta que o Power BI Desktop está usando para análise:

   `> netstat -b -n`

   O resultado deve ser uma lista de aplicativos e suas portas abertas, por exemplo:  

   `TCP    [::1]:55786            [::1]:55830            ESTABLISHED`

   [msmdsrv.exe]

   Procure a porta usada pelo msmdsrv.exe e grave-a para uso posterior. Nesse caso, você poderia usar a porta 55786.
3. **Conectar o SQL Server Profiler ao Power BI Desktop**

   - Iniciar o SQL Server Profiler no menu **Iniciar**
   - **Arquivo** > **Novo Rastreamento**
   - Tipo de servidor: Analysis Services
   - Nome do servidor: localhost: [número da porta encontrado acima]
   - Na próxima tela, selecione **Executar**
   - Agora, o SQL Profiler está dinâmico e criando ativamente os perfis das consultas que o Power BI Desktop está enviando. 
   - À medida que as consultas são executadas, você pode ver suas respectivas durações e tempos de CPU. Com essas informações, determine quais consultas são os gargalos.  

Por meio do SQL Profiler, você pode identificar as consultas que ocupam o maior tempo de CPU. São essas consultas que provavelmente causam gargalos de desempenho. Os visuais que executam essas consultas devem ser um ponto focal de otimização contínua.

## <a name="gateway-best-practices"></a>Práticas recomendada de gateway

O Gateway de dados local é uma excelente ferramenta para conectar o serviço do Power BI com seus dados locais. Ao mesmo tempo, com planejamento inadequado, ele também pode se tornar um gargalo de desempenho do relatório. Isso é especialmente verdadeiro para conjuntos de dados de conexão do DirectQuery/dinâmica, nos quais todas as consultas e respostas de consultas passam pelo gateway. A seguir estão algumas práticas recomendadas para garantir gateways altamente funcionais: 

- **Use o modo empresarial**, ao contrário do modo pessoal.
- **Especificações de hardware recomendado para o gateway** – CPU de oito núcleos, 16 GB de RAM.
- **Configure o monitoramento** – configure o monitoramento de desempenho no computador do gateway para entender se o gateway está ficando sobrecarregado e se tornando um gargalo. Para obter mais informações, veja [Solução de problemas do Gateway de dados local](service-gateway-onprem-tshoot.md).
- **Escale vertical ou horizontalmente** – se o gateway estiver realmente se tornando um gargalo, considere escalar verticalmente (isto é, mover o gateway para um computador mais potente com mais CPU e RAM) ou escalar horizontalmente (por exemplo, dividir conjuntos de dados em diferentes gateways). 
- **Importação separada vs. DirectQuery** – se escalar horizontalmente, considere separar os gateways responsáveis pela importação versus os gateways responsáveis pelo DirectQuery.

## <a name="network-latency"></a>Latência da rede

A latência de rede pode afetar o desempenho do relatório, aumentando o tempo necessário para que as solicitações acessem o serviço do Power BI e para que as respostas sejam entregues. Locatários no Power BI são atribuídos a uma região específica. Você pode exibir a região de "residência" do locatário, navegando até powerbi.com, selecionando **?** na parte superior direita e, depois, **Sobre o Power BI**. Quando os usuários de um locatário acessam o serviço do Power BI, suas solicitações sempre são roteadas para essa região. Depois que as solicitações acessam o serviço do Power BI, o serviço pode enviar solicitações adicionais, por exemplo, para a fonte de dados subjacente ou o gateway, que também estão sujeitos à latência de rede.

Ferramentas como o [Teste de Velocidade do Azure](http://azurespeedtest.azurewebsites.net/) fornecem uma indicação da latência de rede entre o cliente e a região do Azure. Em geral, para minimizar o impacto da latência de rede, empenhe-se para manter fontes de dados, gateways e o cluster do Power BI o mais próximo possível. Se a latência de rede for um problema, tente localizar os gateways e as fontes de dados mais próximos do seu cluster do Power BI, colocando-os em máquinas virtuais.

Para melhorar ainda mais a latência de rede, considere usar o [Azure ExpressRoute](https://azure.microsoft.com/services/expressroute/), que é capaz de criar conexões de rede mais rápidas e mais confiáveis entre os clientes e os data centers do Azure.

## <a name="next-steps"></a>Próximas etapas

- [Planejando uma implantação do Power BI Enterprise](https://aka.ms/pbienterprisedeploy), com orientação geral sobre implantações em larga escala do Power BI
- [DirectQuery no SQL Server 2016 Analysis Services](https://blogs.msdn.microsoft.com/analysisservices/2017/04/06/directquery-in-sql-server-2016-analysis-services-whitepaper/)
- [[YouTube] Criando relatórios rápidos e confiáveis no Power BI](https://www.youtube.com/watch?v=GhiJABR7XX0)
- [[YouTube] Implantações do Power BI Enterprise](https://www.youtube.com/watch?v=K-zEWICvICM)
