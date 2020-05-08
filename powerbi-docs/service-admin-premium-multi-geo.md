---
title: Suporte Multi-Geo para o Power BI Premium
description: Saiba como implantar conteúdos em data centers nas regiões que não sejam a região de residência do locatário do Power BI.
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 02/05/2019
LocalizationGroup: Premium
ms.openlocfilehash: 4b30e2fbf4ec3607b3ee155749a1ddeeb9f76cad
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/05/2020
ms.locfileid: "80147344"
---
# <a name="configure-multi-geo-support-for-power-bi-premium"></a>Configurar o suporte Multi-Geo para o Power BI Premium

O Multi-Geo é um recurso do Power BI Premium que ajuda os clientes multinacionais a atender os requisitos de residência de dados organizacionais, regionais ou específicos do setor. Como cliente Power BI Premium, você pode implantar conteúdos em data centers nas regiões que não sejam a região de residência do locatário do Power BI. Uma área geográfica (geografia) pode conter mais de uma região. Por exemplo, os Estados Unidos é uma área geográfica e o Centro-Oeste dos EUA e o Centro-Sul dos EUA são regiões nos Estados Unidos. É possível optar por implantar o conteúdo em qualquer uma das áreas geográficas a seguir:

- Estados Unidos
- Canadá
- Reino Unido
- Brasil
- Europa
- Japão
- Índia
- Pacífico Asiático
- Austrália
- África

O Multi-Geo não está disponível no Power BI Alemanha, no Power BI China operado pela 21Vianet nem no Power BI para o governo dos EUA.

O Multi-Geo agora também está disponível no Power BI Embedded. Leia mais em [Suporte a Multi-Geo no Power BI Embedded](developer/embedded/embedded-multi-geo.md).

## <a name="enable-and-configure"></a>Habilitar e configurar

Para novas capacidades, habilite o Multi-Geo selecionando uma região diferente da padrão na lista suspensa.  Cada capacidade disponível mostra a região em que está localizada, como **Centro-Oeste dos EUA**.

![Tamanho da capacidade: selecione uma região. Power BI com Multi-Geo](media/service-admin-premium-multi-geo/power-bi-multi-geo-capacity-size.png)

Após criar a capacidade, ela permanece nessa região e todo workspace criado terá o conteúdo armazenado nessa região. É possível migrar os workspaces de uma região para outra por meio do menu suspenso na tela de configurações do workspace.

![Editar workspace: escolha uma capacidade disponível. Power BI com Multi-Geo](media/service-admin-premium-multi-geo/power-bi-multi-geo-edit-workspace.png)

Esta mensagem aparece para confirmar a alteração.

![Confirmação de alteração do workspace atribuído](media/service-admin-premium-multi-geo/power-bi-multi-geo-change-assigned-workspace-capacity.png)

Neste momento, não é preciso redefinir as credenciais de gateway durante a migração.  Após serem armazenadas na região de capacidade Premium, será preciso redefini-las no término da migração.

Durante a migração, pode haver falhas em certas operações, como a publicação de novos conjuntos de dados ou a atualização agendada de dados.  

Os itens a seguir são armazenados na região Premium quando o Multi-Geo está habilitado:

- Modelos (arquivos .ABF) para importação e conjuntos de dados de consulta direta
- Cache de consulta
- Imagens R

Os próximos itens permanecem na região de residência do locatário:

- Conjuntos de dados por push
- Pastas de trabalho do Excel
- Metadados do painel/relatório: por exemplo, nomes de blocos, consultas de blocos
- Barramentos de serviço para consultas de gateway ou trabalhos de atualização agendada
- Permissões
- Credenciais de conjunto de dados

## <a name="view-capacity-regions"></a>Exibir regiões de capacidade

No Portal de administração, você pode exibir todas as capacidades do locatário do Power BI e as regiões em que estão atualmente localizadas.

![Exibir capacidades premium](media/service-admin-premium-multi-geo/power-bi-multi-geo-premium-capacities.png) 

## <a name="change-the-region-for-existing-content"></a>Alterar a região de conteúdo existente

Se for preciso alterar a região de um conteúdo existente, existem duas opções.

- Criar uma segunda capacidade e transferir os workspaces. Os usuários gratuitos não enfrentarão qualquer tempo de inatividade, contanto que o locatário tenha núcleos virtuais sobressalentes.
- Se a criação de uma segunda capacidade não for viável, é possível transferir temporariamente o conteúdo de volta para uma capacidade compartilhada do Premium. Não são necessários núcleos extras, mas os usuários gratuitos terão algum tempo de inatividade.

## <a name="move-content-out-of-multi-geo"></a>Transferir o conteúdo para fora do Multi-Geo  

É possível levar os workspaces para fora da capacidade do Multi-Geo de duas maneiras:

- Excluir a capacidade atual em que o workspace está localizado.  Isso vai transferir o workspace de volta para a capacidade compartilhada na região de residência.
- Migre os workspaces individuais de volta para a capacidade Premium localizada no locatário de residência.

## <a name="limitations-and-considerations"></a>Limitações e considerações

- Confirme que toda movimentação iniciada entre as regiões seguem todos os requisitos de conformidade corporativos e governamentais antes de iniciar a transferência de dados.
- Uma consulta em cache armazenada em uma região remota permanece nessa região em repouso. No entanto, outros dados em trânsito podem ir e voltar entre várias regiões geográficas.
- Ao mover dados de uma região para outra em um ambiente Multi-Geo, os dados de origem podem permanecer na região da qual foram movidos por até 30 dias. Durante esse período, os usuários finais não terão acesso a eles. Eles foram removidos desta região e destruídos durante o período de 30 dias.

- No momento, o recurso de [fluxos de dados](service-dataflows-overview.md) não é compatível com o Multi-Geo.

## <a name="next-steps"></a>Próximas etapas

- [O que é o Power BI Premium?](service-premium-what-is.md)
- [Multi-Geo para capacidades do Power BI Embedded](developer/embedded/embedded-multi-geo.md)

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
