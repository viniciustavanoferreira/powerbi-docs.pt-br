---
title: Solucionar problemas de atualização
description: Solucionar problemas de atualização
author: mgblythe
manager: kfile
ms.reviewer: kayu
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: troubleshooting
ms.date: 09/13/2019
ms.author: mblythe
LocalizationGroup: Data refresh
ms.openlocfilehash: 564c3d03a7879cd7788e19055d8c11e4de46013f
ms.sourcegitcommit: e5cf19e16112c7dad1591c3b38d232267ffb3ae1
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72543873"
---
# <a name="troubleshooting-refresh-scenarios"></a>Solucionar problemas de atualização

Aqui você pode encontrar informações sobre cenários diferentes que você pode encontrar ao atualizar dados no serviço Power BI.

> [!NOTE]
> Se você encontrar um cenário que não esteja listado abaixo e que esteja causando problemas, solicite ajuda no [site da comunidade](http://community.powerbi.com/) ou crie um [tíquete de suporte](https://powerbi.microsoft.com/support/).
>
>

## <a name="refresh-using-web-connector-doesnt-work-properly"></a>A atualização usando o conector da Web não funciona corretamente

Se você tiver um script de conector da Web usando a função [**Web.Page**](https://msdn.microsoft.com/library/mt260924.aspx) e tiver atualizado o seu conjunto de dados ou relatório após 18 de novembro de 2016, você deverá usar um gateway para que a atualização funcione corretamente.

## <a name="unsupported-data-source-for-refresh"></a>Fonte de dados sem suporte para atualização

Ao configurar um conjunto de dados, é possível receber um erro indicando que o conjunto de dados usa uma fonte de dados sem suporte para atualização. Para obter detalhes, confira [Solucionando problemas de fonte de dados sem suporte para atualização](service-admin-troubleshoot-unsupported-data-source-for-refresh.md).

## <a name="dashboard-doesnt-reflect-changes-after-refresh"></a>O painel de controle não reflete as alterações após a atualização

Aguarde cerca de 10 a 15 minutos para que uma atualização seja mostrada nos blocos do dashboard. Se ainda não aparecer, novamente fixe a visualização para o painel.

## <a name="gatewaynotreachable-when-setting-credentials"></a>GatewayNotReachable ao definir credenciais

Você pode se deparar com `GatewayNotReachable` durante a tentativa de definir credenciais para uma fonte de dados. Isso pode ser o resultado de um gateway desatualizado. Instale o gateway mais recente e tente novamente.

## <a name="processing-error-the-following-system-error-occurred-type-mismatch"></a>Erro de processamento: ocorreu o seguinte erro de sistema: incompatibilidade de tipo

Isso pode ser um problema com o script M em seu arquivo do Power BI Desktop ou com a pasta de trabalho do Excel. Também pode ser devido a uma versão do Power BI Desktop desatualizada.

## <a name="tile-refresh-errors"></a>Erros de atualização de bloco

Para obter uma lista de erros que podem ser encontrados em blocos de dashboard, bem como explicações, veja [Solucionar problemas de erros de bloco](refresh-troubleshooting-tile-errors.md).

## <a name="refresh-fails-when-updating-data-from-sources-that-use-aad-oauth"></a>Falha na atualização ao atualizar dados de fontes que usam o OAuth do AAD

O token OAuth do AAD (**Azure Active Directory**), usado por diversas fontes de dados, expira em cerca de uma hora. Você pode se deparar com situações em que o carregamento de dados demora mais do que a expiração do token (mais de uma hora), já que o serviço do Power BI espera por até duas horas ao carregar dados. Nessa situação, o processo de carregamento de dados pode falhar com um erro de credenciais.

Fontes de dados que usam o OAuth do AAD incluem **Microsoft Dynamics CRM Online**, **SPO** (SharePoint Online) e outras. Se você estiver se conectando a essas fontes de dados e obtiver uma falha de credenciais quando o carregamento de dados demorar mais de uma hora, esse poderá ser o motivo.

A Microsoft está investigando uma solução que permita que o processo de carregamento de dados atualize o token e continue. No entanto, se a instância do Dynamics CRM Online ou do SharePoint Online (ou outra fonte de dados de OAuth do AAD) for tão grande que possa alcançar o limite de carregamento de dados de duas horas, você também poderá enfrentar um problema de tempo de limite de carregamento de dados do serviço do Power BI.

Observe também que, para a atualização funcionar corretamente, ao conectar-se a uma fonte de dados do **SharePoint Online** usando o AAD OAuth, você deverá usar a mesma conta usada para entrar no **serviço do Power BI**.

## <a name="uncompressed-data-limits-for-refresh"></a>Limites de dados descompactados para atualização

O tamanho máximo de conjuntos de dados importados para o **serviço do Power BI** é de 1 GB. Esses conjuntos de dados são altamente compactados para garantir o alto desempenho. Além disso, na capacidade compartilhada, o serviço impõe um limite de 10 GB para a quantidade de dados descompactados que são processados durante a atualização. Esse limite leva em consideração a compactação e, portanto, é muito maior que 1 GB. Conjuntos de dados no Power BI Premium não estão sujeitos a esse limite. Se a atualização no serviço do Power BI falhar por esse motivo, reduza a quantidade de dados que estão sendo importados para o Power BI e tente novamente.

## <a name="scheduled-refresh-timeout"></a>Tempo limite de atualização agendada

A atualização agendada para os conjuntos de dados importados atinge o tempo limite após duas horas. Esse tempo limite é aumentado para cinco horas em conjuntos de dados em workspaces **Premium**. Se você se deparar com esse limite, considere a possibilidade de reduzir o tamanho ou a complexidade do conjunto de dados ou dividir o conjunto de dados em partes menores.

## <a name="scheduled-refresh-failures"></a>Falhas de atualização agendada

Se uma atualização agendada falhar quatro vezes seguidas, o Power BI desabilitará a atualização. Resolva o problema subjacente e, em seguida, reabilite a atualização agendada.

## <a name="access-to-the-resource-is-forbidden"></a>O acesso ao recurso é proibido  

Esse erro pode ocorrer devido a credenciais armazenadas em cache expiradas. Limpe o cache do navegador de Internet entrando no Power BI e acessando https://app.powerbi.com?alwaysPromptForContentProviderCreds=true. Isso força uma atualização de suas credenciais.

## <a name="data-refresh-failure-because-of-password-change-or-expired-credentials"></a>Falha na atualização de dados por causa de alteração de senha ou credenciais expiradas

A atualização de dados também pode falhar devido a credenciais armazenadas em cache expiradas. Limpe o cache do navegador de Internet entrando no Power BI e acessando https://app.powerbi.com?alwaysPromptForContentProviderCreds=true. Isso força uma atualização de suas credenciais.

## <a name="next-steps"></a>Próximas etapas

- [Atualizar dados no Power BI](refresh-data.md)  
- [Solução de problemas do gateway de dados local](service-gateway-onprem-tshoot.md)  
- [Solução de problemas do Gateway do Power BI – Pessoal](service-admin-troubleshooting-power-bi-personal-gateway.md)  

Mais perguntas? [Experimente perguntar à Comunidade do Power BI da Microsoft](http://community.powerbi.com/)

