---
title: Diretrizes para implantar um gateway de dados para o Power BI
description: Conheça as melhores práticas e considerações para implantar um gateway para Power BI.
author: arthiriyer
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 07/15/2019
ms.author: arthii
LocalizationGroup: Gateways
ms.openlocfilehash: a9d30d1346bf2801cd6cba44cc7cc33d734fccbb
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/05/2020
ms.locfileid: "74699557"
---
# <a name="guidance-for-deploying-a-data-gateway-for-power-bi"></a>Diretrizes para implantar um gateway de dados para o Power BI

[!INCLUDE [gateway-rewrite](includes/gateway-rewrite.md)]

Este artigo fornece diretrizes e considerações para implantar um gateway de dados do Power BI em seu ambiente de rede.

Para saber mais sobre como baixar, instalar, configurar e gerenciar o gateway de dados local, confira [O que é um gateway de dados local?](/data-integration/gateway/service-gateway-onprem). Você também pode saber mais sobre o gateway de dados local e o Power BI visitando o [Microsoft Power blog](https://powerbi.microsoft.com/blog/) e o site da [Comunidade do Power BI da Microsoft](https://community.powerbi.com/).

## <a name="installation-considerations-for-the-on-premises-data-gateway"></a>Considerações de instalação para o gateway de dados local

Antes de instalar o gateway de dados local do seu serviço de nuvem do Power BI, há algumas considerações para se ter em mente. As seções a seguir descrevem essas considerações.

### <a name="number-of-users"></a>Número de usuários

O número de usuário que consome um relatório que usa o gateway é uma métrica importante em sua decisão sobre em que local instalar o gateway. Veja algumas perguntas a serem consideradas:

* Os usuários usam esses relatórios em diferentes momentos do dia?
* Que tipos de conexões eles usam (DirectQuery ou Importação)?
* Todos os usuários usam o mesmo relatório?

Se todos os usuários acessarem um determinado relatório ao mesmo tempo por dia, instale o gateway em um computador capaz de lidar com todas essas solicitações. Confira as seções a seguir para contadores de desempenho e requisitos mínimos que podem ajudar a determinar se um computador é adequado.

Uma restrição no Power BI permite apenas *um* gateway por *relatório*. Mesmo se um relatório basear-se em várias fontes de dados, todas essas fontes de dados deverão passar por um único gateway. Se um dashboard for baseado em *vários* relatórios, você poderá usar um gateway dedicado para cada relatório de contribuição. Dessa forma, você distribui a carga de gateway entre os vários relatórios que contribuem para o único dashboard.

### <a name="connection-type"></a>Tipo de conexão

O Power BI oferece dois tipos de conexões: DirectQuery e Importação. Nem todas as fontes de dados dão suporte aos dois tipos de conexão. Muitos fatores podem contribuir para você escolher um em vez do outro, como requisitos de segurança, desempenho, limites de dados e tamanhos de modelo de dados. Para saber mais sobre tipos de conexão e fontes de dados com suporte, confira a [lista de tipos de fontes de dados disponíveis](service-gateway-data-sources.md#list-of-available-data-source-types).

Dependendo de qual tipo de conexão for usado, o uso do gateway poderá ser diferente. Por exemplo, tente separar as fontes de dados do DirectQuery das fontes de dados de atualização agendadas sempre que possível. A suposição é que elas estejam em diferentes relatórios e possam ser separadas. Separar fontes impede que o gateway tenha milhares de solicitações do DirectQuery em fila ao mesmo tempo em que a atualização agendada da manhã de um modelo de dados de tamanho grande é usada para o dashboard principal da empresa. 

Veja o que considerar para cada opção:

* **Atualização agendada**: dependendo do tamanho da sua consulta e do número de atualizações que ocorrem diariamente, é possível escolher ficar com os requisitos mínimos de hardware recomendados ou atualizar para um computador de melhor desempenho. Se uma determinada consulta não for fechada, transformações ocorrerão no computador do gateway. Como resultado, o computador do gateway se beneficia de ter mais RAM disponível.

* **DirectQuery**: uma consulta é enviada sempre que um usuário abre o relatório ou examina dados. Se você espera que mais de 1.000 usuários acessem os dados simultaneamente, verifique se seu computador tem componentes de hardware robustos e compatíveis. Mais núcleos de CPU resulta em uma melhor taxa de transferência para uma conexão do DirectQuery.

Para obter os requisitos de instalação do computador, confira os [requisitos de instalação](/data-integration/gateway/service-gateway-install#requirements) do gateway de dados local.

### <a name="location"></a>Localização

O local da instalação do gateway pode ter um impacto significativo no desempenho da sua consulta. Tente verificar se o seu gateway, os locais de fonte de dados e o locatário do Power BI estão o mais próximo possível uns dos outros para minimizar a latência de rede. Para determinar o local de locatário do seu Power BI no serviço do Power BI, selecione o ícone **?** ícone no canto superior direito. Selecione **Sobre o Power BI**.

![Determinar a localização do locatário do Power BI](media/service-gateway-deployment-guidance/powerbi-gateway-deployment-guidance_02.png)

Se você pretende usar o gateway de Power BI com o Azure Analysis Services, verifique se as regiões de dados em ambos correspondem. Para saber mais sobre como definir regiões de dados para vários serviços, assista a [este vídeo](https://guyinacube.com/2018/01/power-bi-azure-analysis-services-gateway-data-region/).

## <a name="next-steps"></a>Próximas etapas

* [Definindo as configurações de proxy](/data-integration/gateway/service-gateway-proxy)  
* [Solucionar problemas de gateways – Power BI](service-gateway-onprem-tshoot.md)  
* [Perguntas frequentes do gateway de dados local – Power BI](service-gateway-power-bi-faq.md)  

Mais perguntas? Experimente a [Comunidade do Power BI](https://community.powerbi.com/).

