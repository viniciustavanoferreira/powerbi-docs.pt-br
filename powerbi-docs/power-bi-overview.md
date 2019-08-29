---
title: O que é Power BI?
description: Visão geral do Power BI e como as diferentes partes se combinam – Power BI Desktop, serviço do Power BI, Power BI Mobile, Servidor de Relatórios e Power BI Embedded.
author: maggiesMSFT
manager: kfile
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: overview
ms.date: 08/19/2019
ms.author: maggies
LocalizationGroup: Get started
ms.openlocfilehash: 0e12d110708c955e0c63e11f7578523222375448
ms.sourcegitcommit: 4a3afe761d2f4a5bd897fafb36b53961739e8466
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/20/2019
ms.locfileid: "69654989"
---
# <a name="what-is-power-bi"></a>O que é Power BI?
O **Power BI** é uma coleção de serviços de software, aplicativos e conectores que trabalham juntos para transformar suas fontes de dados não relacionadas em informações coerentes, visualmente envolventes e interativas. Os dados podem estar em uma planilha do Excel ou em uma coleção de data warehouses híbridos locais ou baseados na nuvem. Com o Power BI, você pode conectar-se facilmente a fontes de dados, visualizar e descobrir conteúdo importante e compartilhá-lo com todas as pessoas que quiser.

![diagrama mostrando fontes de entrada para o Power BI](media/power-bi-overview/power-bi-input-new.png)

O Power BI pode ser simples e rápido, capaz de criar insights rápidos com base em uma planilha do Excel ou em um banco de dados local. Mas o Power BI também é robusto e de nível empresarial, pronto para ampla modelagem e análise em tempo real, bem como para desenvolvimento personalizado. Ele pode ser sua ferramenta pessoal de relatório e visualização e servir como o mecanismo de decisões e análise para projetos de grupo, divisões ou empresas inteiras.

## <a name="the-parts-of-power-bi"></a>As partes do Power BI
O Power BI consiste em: 
- Um aplicativo de desktop do Windows chamado **Power BI Desktop**.
- Um serviço SaaS (*software como serviço*) online chamado de **serviço do Power BI**. 
- **Aplicativos móveis** do Power BI para dispositivos Windows, iOS e Android.

![Power BI Desktop, serviço, Mobile](media/power-bi-overview/power-bi-overview-blocks.png)

Esses três elementos&mdash;Power BI Desktop, o serviço e os aplicativos móveis&mdash;são projetados para que as pessoas possam criar, compartilhar e consumir com eficiência insights empresariais da maneira mais adequada para elas ou para as respectivas funções.

O quarto elemento, o **Servidor de Relatórios do Power BI**, permite publicar relatórios do Power BI em um servidor de relatórios local, depois de criá-los no Power BI Desktop. Leia mais sobre o [Servidor de Relatório do Power BI](#on-premises-reporting-with-power-bi-report-server).

## <a name="how-power-bi-matches-your-role"></a>Como o Power BI corresponde à sua função
A forma de uso do Power BI pode depender de sua função em um projeto ou uma equipe. Outras pessoas, em outras funções, podem usar o Power BI de modo diferente.

Por exemplo, você pode usar principalmente o **serviço do Power BI**, mas seu colega que trabalha com cálculos de grandes dados numéricos e com a criação de relatórios de negócios pode usar extensivamente o **Power BI Desktop** para criar relatórios e publicá-los no serviço do Power BI, onde é possível exibi-los. Outro colega da área de vendas talvez use o **aplicativo para telefone do Power BI** principalmente para monitorar o progresso das cotas de vendas e analisar detalhes de novas vendas potenciais.

Caso seja um desenvolvedor, você pode usar APIs do Power BI para efetuar push dos dados para conjuntos de dados ou para inserir relatórios e dashboards em seus próprios aplicativos personalizados. Ter uma ideia de um novo visual? Crie-o você mesmo e compartilhe-o com outras pessoas.  

Você também pode usar cada elemento do Power BI em momentos diferentes, dependendo do objetivo ou da função em determinado projeto.

A maneira de usar o Power BI depende do respectivo recurso ou serviço que seja mais adequado como ferramenta para o caso. Por exemplo, é possível usar o Power BI Desktop para criar relatórios para sua própria equipe sobre as estatísticas de participação do cliente e exibir o inventário e o progresso da fabricação em um dashboard em tempo real no serviço do Power BI. Todos os elementos do Power BI estão disponíveis para você. Por isso, ele é um programa tão versátil e interessante.

Explore os documentos pertinentes à sua função:
- Power BI para [***designers***](desktop-what-is-desktop.md)
- Power BI para [***consumidores***](consumer/end-user-consumer.md)
- Power BI para [***desenvolvedores***](developer/what-can-you-do.md)
- Power BI para [***administradores***](service-admin-administering-power-bi-in-your-organization.md)

## <a name="the-flow-of-work-in-power-bi"></a>O fluxo de trabalho no Power BI
Um fluxo de trabalho comum no Power BI começa pela conexão com fontes de dados e pela criação de um relatório no Power BI Desktop. Você então publica esse relatório do Power BI Desktop no serviço do Power BI e o compartilha para que os usuários finais no serviço do Power BI e nos dispositivos móveis possam exibir e interagir com o relatório.
Esse fluxo de trabalho é comum e mostra como os três principais elementos do Power BI se complementam.

Veja uma [comparação detalhada entre o Power BI Desktop e o serviço do Power BI](service-service-vs-desktop.md).

Mas e se você não estiver pronto para ir para a nuvem e quiser manter seus relatórios atrás de um firewall corporativo?  Continue lendo.

## <a name="on-premises-reporting-with-power-bi-report-server"></a>Relatórios locais com o Servidor de Relatório do Power BI
Crie, implante e gerencie os relatórios móveis e paginados do Power BI localmente com a variedade de ferramentas e serviços prontos para uso que o Servidor de Relatórios do Power BI oferece.

![diagrama para local](media/power-bi-overview/power-bi-report-server2.png)

O Servidor de Relatórios do Power BI é uma solução que você implanta atrás do firewall e, em seguida, fornece relatórios para os usuários corretos de diferentes maneiras, seja exibindo-os em um navegador da Web, em um dispositivo móvel ou como um email. E, como o Servidor de Relatórios do Power BI é compatível com o Power BI na nuvem, você pode ir para a nuvem quando estiver pronto. 

Leia mais sobre o [Servidor de Relatório do Power BI](report-server/get-started.md).

## <a name="next-steps"></a>Próximas etapas
- [Início Rápido: Saiba como usar o serviço do Power BI](service-the-new-power-bi-experience.md)   
- [Tutorial: Introdução ao serviço do Power BI](service-get-started.md)
- [Início Rápido: conectar-se a dados no Power BI Desktop](desktop-quickstart-connect-to-data.md)
