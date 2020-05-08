---
title: Perguntas frequentes de recuperação de desastre, failover e alta disponibilidade do Power BI
description: Entenda como o serviço do Power BI oferece alta disponibilidade e fornece continuidade dos negócios e recuperação de desastres para seus usuários.
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 02/20/2020
ms.author: kfollis
LocalizationGroup: Administration
ms.openlocfilehash: 3dd50d4f57b3146135cde5e91062ed3b2a0eecc1
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/05/2020
ms.locfileid: "77527328"
---
# <a name="power-bi-high-availability-failover-and-disaster-recovery-faq"></a>Perguntas frequentes de recuperação de desastre, failover e alta disponibilidade do Power BI

Este artigo explica como o serviço do Power BI oferece alta disponibilidade e fornece continuidade dos negócios e recuperação de desastres para seus usuários. Depois de ler este artigo, você deverá ter um melhor entendimento de como alta disponibilidade é obtida, em que circunstâncias o Power BI executa um failover e o que esperar do serviço quando o failover ocorrer.

## <a name="what-does-high-availability-mean-for-power-bi"></a>O que "alta disponibilidade" significa para o Power BI?

Power BI é um SaaS (Software como Serviço) totalmente gerenciado.  A Microsoft projeta-o e opera-o para ser resiliente a falhas de infraestrutura para que os usuários sempre possam acessar seus relatórios.  O serviço tem o suporte de um [SLA de 99,9%](https://www.microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&DocumentTypeId=37).

## <a name="what-is-a-power-bi-failover"></a>O que é um failover do Power BI?

O Power BI mantém várias instâncias de cada componente em datacenters do Azure (também conhecidos como regiões) para garantir a continuidade dos negócios. Se houver uma interrupção ou um problema que faça com que o Power BI fique inacessível ou inoperante em uma região, o Power BI falhará todos os seus componentes nessa região para uma instância de backup. O failover restaura a disponibilidade e capacidade de operação da instância do serviço do Power BI em uma nova região (geralmente dentro do mesmo local geográfico, como observado no [Microsoft Trust Center](https://www.microsoft.com/TrustCenter/CloudServices/business-application-platform/data-location)).

Uma instância do serviço do Power BI que sofreu failover dá suporte apenas a _operações de leitura_, o que significa que as operações a seguir não têm suporte durante o failover: atualizações, operações de publicação de relatório, modificações de dashboard ou de relatório e outras operações que exigem alterações nos metadados do Power BI (por exemplo, inserção de um comentário em um relatório).  Operações de leitura, como exibição de dashboards e de relatórios (que não são baseados em DirectQuery ou no Live Connect para fontes de dados locais) continuarão a funcionar normalmente.

## <a name="how-are-backup-instances-kept-in-sync-with-my-data"></a>Como as instâncias de backup são mantidas em sincronia com meus dados?

Todos os componentes do serviço do Power BI sincronizam regularmente suas instâncias de backup. Podemos ter como destino uma sincronização de ponto no tempo de 15 minutos para o conteúdo carregado ou alterado no Power BI. No caso de um failover, o Power BI usa [replicação do Armazenamento do Azure com redundância geográfica](/azure/storage/common/storage-redundancy-grs) e [replicação do SQL do Azure com redundância geográfica](/azure/sql-database/sql-database-active-geo-replication) para garantir que instâncias de backup existam em outras regiões e que possam ser usadas no caso de um failover.

## <a name="where-are-the-failover-clusters-located"></a>Onde os clusters de failover estão localizados?

Instâncias de backup residem no mesmo local geográfico (área geográfica) que você selecionou quando sua organização se inscreveu no Power BI, exceto quando observado no [Microsoft Trust Center](https://www.microsoft.com/TrustCenter/CloudServices/business-application-platform/data-location). Uma área geográfica pode conter várias regiões, e a Microsoft pode replicar dados para qualquer uma das regiões dentro de um determinado local para resiliência de dados. A Microsoft não replicará nem moverá dados do cliente para fora da área geográfica. Para um mapeamento das áreas geográficas oferecidas pelo Power BI e das regiões dentro delas, veja o [Microsoft Trust Center](https://www.microsoft.com/TrustCenter/CloudServices/business-application-platform/data-location).

## <a name="how-does-microsoft-decide-to-failover"></a>Como a Microsoft decide fazer failover?

Há dois sistemas diferentes que indicam quando um failover pode ser necessário:

- Nossas investigações de monitoramento internas e externas indicam uma falta de disponibilidade ou incapacidade de funcionar corretamente. Essas indicações podem ser baseadas em interrupções detectadas nos componentes do Power BI ou de um ou mais dos serviços dos quais o Power BI depende em uma região.
- A equipe de operações central do Microsoft Azure nos informa de uma interrupção crítica em uma região.

Em ambos os casos, os membros da equipe executiva do Power BI tomar a decisão de fazer failover; a decisão em si não é automatizada. Depois que a decisão é tomada, o processo de failover ocorre automaticamente.

## <a name="how-do-i-know-power-bi-is-now-in-failover-mode"></a>Como saber o que Power BI agora está no modo de failover?

Uma notificação é postada na página de suporte do Power BI ([https://powerbi.microsoft.com/support/](https://powerbi.microsoft.com/support/)). A notificação inclui as principais operações que não estão disponíveis durante o failover, incluindo publicação, atualização, criação de dashboard, duplicação de dashboard e alterações de permissão.

## <a name="how-long-does-it-take-power-bi-to-fail-over"></a>Quanto tempo o Power BI leva para fazer failover?

O Power BI leva aproximadamente 15 minutos para se tornar operacional novamente quando se identifica que um failover é necessário. O tempo para identificar que um failover é necessário varia com base no cenário corrompido. 

Depois que um failover é executado, o Power BI usa a replicação geográfica do Armazenamento do Azure para executar o failover. Essas replicações geralmente têm um ponto de retorno de 15 minutos. No entanto, o [Armazenamento do Azure não garante esse período](https://docs.microsoft.com/azure/storage/common/storage-redundancy) com um SLA e, portanto, o Power BI também não é capaz de garantir um período. 


## <a name="when-does-my-power-bi-instance-return-to-the-original-region"></a>Quando a minha instância do Power BI retorna para a região original?

Instâncias de serviço do Power BI retornam para as respectivas regiões originais quando o problema que causou o failover é resolvido. Confira a página de suporte do Power BI: Quando o problema é resolvido, a equipe do Power BI remove a notificação que descreve o failover. Nesse ponto, as operações devem ser voltar ao normal.

## <a name="am-i-responsible-for-the-availability-of-my-power-bi-solution"></a>Eu sou responsável pela disponibilidade da minha solução do Power BI?

Se a solução do Power BI usada em sua organização envolve um dos elementos a seguir, você precisa executar algumas medidas para garantir que a solução permaneça altamente disponível:

- Se sua organização usa o Power BI Premium, você precisa garantir que a capacidade Premium seja dimensionada para atender às demandas de carga da sua implantação.  O [white paper de planejamento e implantação do Power BI Premium](https://aka.ms/Premium-Capacity-Planning-Deployment) e o [aplicativo de métricas de capacidade do Power BI Premium](service-admin-premium-monitor-capacity.md) podem ajudar você a planejar e atender a esse requisito. Regularmente, adicionamos novos recursos para o aplicativo de métricas e o portal de administração no Power BI para ajudar.
- Se sua organização acessar fontes de dados locais usando o gateway de dados local, você precisará configurar o gateway [conforme descrito neste artigo](/data-integration/gateway/service-gateway-high-availability-clusters) para dar suporte a alta disponibilidade. Siga estas diretrizes se você estiver atualizando relatórios no modo de importação ou estiver acessando dados ou modelos de dados usando o DirectQuery ou Live Connect.

## <a name="will-gateways-function-when-in-failover-mode"></a>Os gateways funcionarão no modo de failover?

Não. Os dados necessários de fontes de dados locais (qualquer relatório e dashboard com base em consulta direta e Live Connect) não funcionarão durante um failover. No entanto, a configuração do gateway não é alterada: Quando a instância do Power BI retorna ao estado original, os gateways voltam às suas funções normais.
