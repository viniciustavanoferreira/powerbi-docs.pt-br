---
title: Atualizar resumos para Power BI
description: Saiba como usar resumos de atualização no Power BI
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/18/2020
ms.author: davidi
LocalizationGroup: Data refresh
ms.openlocfilehash: 854b3500fa985a464130e505a889bb9981cd4151
ms.sourcegitcommit: 250242fd6346b60b0eda7a314944363c0bacaca8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83694379"
---
# <a name="refresh-summaries-for-power-bi"></a>Atualizar resumos para Power BI

A página **resumos de atualização** do Power BI, encontrada no portal de administração do Power BI, fornece controle e informações sobre suas capacidades e agendas de atualização, bem como possíveis sobreposições da agenda de atualização. Você pode usar a página de resumos de atualização para determinar se deve ajustar agendas de atualização, aprender códigos de erro associados a problemas de atualização e gerenciar corretamente seu agendamento de atualização de dados. 

A página resumos de atualização tem duas exibições:

* **Histórico** – exibe o histórico de resumo de atualização de capacidades do Power BI Premium das quais você é um administrador.

* **Agenda** – mostra o modo de exibição da agenda da atualização agendada, que também pode revelar problemas com intervalos de tempo contendo assinaturas demais.

Você também pode exportar informações sobre um evento de atualização para um arquivo .CSV, que pode fornecer informações significativas e insight sobre eventos de atualização ou erros que podem afetar o desempenho ou a conclusão de eventos de atualização agendada.

As seções a seguir examinam cada uma dessas exibições por vez. 

## <a name="refresh-history"></a>Histórico de atualização

Você pode selecionar o modo de exibição de **Histórico** clicando em **Histórico** na página resumos de atualização.

![Modo de exibição de Histórico em resumos de atualização](media/refresh-summaries/refresh-summaries-01a.jpg)

O Histórico fornece uma visão geral dos resultados de atualizações agendadas recentemente nas capacidades para as quais você tem privilégios de administrador. Você pode classificar a exibição por qualquer coluna clicando na coluna. Você pode optar por classificar a exibição pela coluna selecionada por ordem crescente, decrescente ou usando filtros de texto.

![classificar o modo de exibição de Histórico](media/refresh-summaries/refresh-summaries-01b.jpg)

No modo de exibição de Histórico, os dados associados a uma determinada atualização baseiam-se em até 60 registros mais recentes para cada atualização agendada.

Você também pode exportar informações para qualquer atualização agendada para um arquivo .CSV, que inclui informações detalhadas incluindo mensagens de erro para cada evento de atualização. A exportação para um arquivo .CSV permite que você classifique o arquivo com base em qualquer uma das colunas, pesquise palavras, classifique com base em códigos de erro ou proprietários e assim por diante. A imagem a seguir mostra um arquivo .CSV exportado de exemplo. 

![Exportar informações sobre uma atualização](media/refresh-summaries/refresh-summaries-05.jpg)

Com as informações no arquivo exportado, você pode examinar a capacidade, a duração e todas as mensagens de erro registradas para a instância de atualização. 


## <a name="refresh-schedule"></a>Agendamento de atualização

Você pode selecionar o modo de exibição de **Agenda** clicando em **Agenda** nos resumos de atualização. O modo de exibição de Agenda exibe informações de agendamento da semana, divididas em intervalos de 30 minutos. 

![Modo de exibição de Agenda](media/refresh-summaries/refresh-summaries-02a.jpg)

O modo de exibição de Agenda é muito útil para determinar se os intervalos estão corretos entre os eventos de atualização agendados, permitindo que todas as atualizações sejam concluídas sem sobreposição ou se você agendou eventos de atualização que estão demorando muito e resultando em contenção de recursos. Se você enfrentar tal contenção de recursos, ajuste suas agendas de atualização para evitar conflitos ou sobreposição, permitindo que suas atualizações agendadas sejam concluídas com êxito. 

![Modo de exibição de Agenda](media/refresh-summaries/refresh-summaries-02.jpg)

A coluna *Tempo de atualização reservado (minutos)* é um cálculo da média de até 60 registros para cada conjunto de dados associado. O valor numérico para cada intervalo de 30 minutos é a soma de minutos calculada para todas as atualizações agendadas programadas para iniciar no intervalo de tempo **e** as atualizações agendadas definidas para iniciar no intervalo de tempo *anterior*, mas cuja duração média estoura para o intervalo de tempo selecionado.

Você pode selecionar um intervalo de tempo e, em seguida, selecionar o botão **detalhes** associado para ver quais eventos de atualização agendada contribuem para o tempo de atualização reservado, os proprietários deles e quanto tempo eles levam para concluir.

Vejamos um exemplo de como isso funciona. A caixa de diálogo a seguir é exibida quando selecionamos o intervalo de horário de 20:30 para domingo e clicamos em **detalhes**.

![Modo de exibição de Agenda](media/refresh-summaries/refresh-summaries-04.jpg)

Há três eventos de atualização agendados ocorrendo nesse intervalo de tempo. 

As atualizações 1 e 3 estão agendadas para esse intervalo de tempo de 20:30, que podemos determinar examinando o valor na coluna **Intervalo de tempo agendado**. As durações médias são de 4:39 e seis segundos (0:06), respectivamente. Parece que está tudo certo.

No entanto, a atualização agendada n. 2 está agendada para o intervalo de tempo de 20:00, mas já que ela leva uma média de mais de 48 minutos para ser concluída (o que é visto na coluna **Duração média**), esse evento de atualização estoura para o próximo intervalo de tempo de 30 minutos. 

Isso não é bom. O administrador, nesse caso, deve entrar em contato com os proprietários dessa instância de atualização agendada e sugerir que elas encontrem um intervalo de tempo diferente para essa atualização agendada ou reagendem as outras atualizações para que não haja sobreposição ou, ainda, que encontrem alguma outra solução para evitar tal sobreposição. 


## <a name="next-steps"></a>Próximas etapas

- [Atualizar dados no Power BI](refresh-data.md)  
- [Gateway do Power BI – Pessoal](service-gateway-personal-mode.md)  
- [Gateway de dados local (modo pessoal)](service-gateway-onprem.md)  
- [Solução de problemas do gateway de dados local](service-gateway-onprem-tshoot.md)  
- [Solução de problemas do Gateway do Power BI – Pessoal](service-admin-troubleshooting-power-bi-personal-gateway.md)  

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)