---
title: Relatórios paginados no serviço do Power BI
description: Documentação que descreve os relatórios paginados e como exibi-los no serviço do Power BI
author: mihart
ms.reviewer: chris finlan
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 03/11/2020
ms.author: mihart
LocalizationGroup: Common tasks
ms.openlocfilehash: c4c21dc0f02e547cd7319d789a3eb66cce1f4b88
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/05/2020
ms.locfileid: "79377341"
---
# <a name="paginated-reports-in-the-power-bi-service"></a>Relatórios paginados no serviço do Power BI

[!INCLUDE[consumer-appliesto-yyny](../includes/consumer-appliesto-yyny.md)]

Você aprendeu sobre os [Relatórios do Power BI](end-user-reports.md), que são os relatórios que você terá maior probabilidade de encontrar. No entanto, há outro tipo de relatório chamado *relatório paginado*. Os *designers* de relatórios podem compartilhar relatórios paginados com você em um workspace na capacidade Premium ou em um aplicativo desse workspace. 

## <a name="what-is-a-paginated-report"></a>O que é um relatório paginado?

Esses relatórios são chamados de *paginados* porque são formatados de modo a se adaptarem bem a uma página impressa. Uma vantagem é que eles exibem todos os dados em uma tabela, mesmo que a tabela abranja várias páginas. Às vezes, os relatórios paginados são chamados de "pixel perfeito" porque os *designers* do relatório podem controlar seu layout de página de maneira exata.

Quando os *designers* de relatórios criam um relatório paginado, na verdade eles estão criando uma *definição de relatório*. Ele não contém os dados. Especifica onde obter os dados, quais dados devem ser obtidos e como exibir os dados. Quando você executa o relatório, o processador de relatório usa a definição de relatório, recupera os dados e combina-os com o layout do relatório para gerar o relatório. Às vezes, o relatório exibe dados padrão. Outras vezes, você precisa inserir parâmetros antes que o relatório possa exibir dados. 

   ![Parâmetros do relatório](./media/end-user-paginated-report/power-bi-report-parameters.png)

E essa normalmente é a extensão da interação – definir os parâmetros. Se você for um analista de cobrança, poderá usar relatórios paginados para criar ou imprimir faturas. Se for um gerente de vendas, poderá usar relatórios paginados para exibir pedidos por loja ou vendedor. 

Este relatório paginado simples gera dados de lucro por ano após você selecionar o parâmetro **Ano**. 

![Relatório simples com um parâmetro](./media/end-user-paginated-report/power-bi-report-simple.png)

Em comparação com os relatórios paginados, os relatórios do Power BI são muito mais interativos. Os relatórios do Power BI permitem relatórios ad hoc e dão suporte a muitos outros tipos de visuais, incluindo visuais do Power BI.

## <a name="identify-a-paginated-report"></a>Identificar um relatório paginado

Em listas de conteúdo e em sua página de aterrissagem Inicial, os relatórios paginados podem ser identificados pelo ![ícone de relatório paginado](media/end-user-paginated-report/power-bi-report-icon.png).  Um relatório paginado pode ser compartilhado com você diretamente ou como parte de um [aplicativo do Power BI](end-user-apps.md). Se o *designer* de relatórios lhe concedeu permissões, você poderá compartilhar novamente o relatório paginado e inscrever a si mesmo e a outras pessoas.

![lista de relatórios mostrando ícones diferentes](./media/end-user-paginated-report/power-bi-report-list.png)

## <a name="interact-with-a-paginated-report"></a>Interagir com um relatório paginado

A maneira como você interage com um relatório paginado é diferente de outros relatórios. Você pode fazer coisas como imprimir, marcar, exportar e comentar, mas há menos interatividade. Geralmente, os relatórios paginados exigem que você faça entradas para preencher a tela do relatório.  Em outras ocasiões, o relatório exibe dados padrão e você pode inserir parâmetros para ver dados diferentes.

### <a name="print-a-paginated-report"></a>Imprimir um relatório paginado

Os relatórios *paginados* são formatados de forma a se ajustarem bem a uma página e a serem impressos adequadamente. O que você vê no navegador é o que vê ao imprimir. Além disso, se o relatório tiver uma tabela longa, a tabela inteira será impressa, mesmo que ocupe várias páginas. 

Os relatórios paginados podem ter muitas páginas. Por exemplo, esse relatório tem 563 páginas. Cada página é disposta exatamente, com uma página por fatura e cabeçalhos e rodapés repetidos. Ao imprimir este relatório, você terá quebras de página entre as faturas.

   ![Página um de um relatório paginado da Tailspin Toys](./media/end-user-paginated-report/power-bi-paginated-500.png)


### <a name="navigate-the-paginated-report"></a>Navegar no relatório paginado

Neste relatório de pedido de vendas, há três parâmetros: Tipo de negócio, Revendedor e Número da ordem. 

![relatório com três parâmetros](./media/end-user-paginated-report/power-bi-parameter.png)

Para alterar as informações que estão sendo exibidas, insira novos valores para os três parâmetros e selecione **Exibir relatório**. Aqui, selecionamos **Loja de bicicletas especiais**, **Alpine Ski House** e o número da ordem **SO46085**. Selecionar **Exibir relatório** atualiza nossa tela de relatório com essa nova ordem de venda.

![alterar os parâmetros](./media/end-user-paginated-report/power-bi-order.png)

A nova ordem de venda é exibida, usando os parâmetros que selecionamos. 

![uma nova ordem de venda](./media/end-user-paginated-report/power-bi-new-order.png)

Alguns relatórios paginados têm muitas páginas.  Use os controles de página para navegar pelo relatório. 

![controles de página](./media/end-user-paginated-report/power-bi-page.png)

### <a name="export-the-paginated-report"></a>Exportar o relatório paginado
Você tem diversas opções para exportar relatórios paginados, incluindo PDF, Word, XML, PowerPoint, Excel e muito mais. Ao exportar, a maior parte possível da formatação é preservada. Os relatórios paginados exportados para Excel, Word, PowerPoint, MHTML e PDF, por exemplo, mantêm a formatação "pixel perfeito". 

![uma nova ordem de venda](./media/end-user-paginated-report/power-bi-exporting.png)

![quatro tipos diferentes de exportação](./media/end-user-paginated-report/power-bi-four.png)

### <a name="subscribe-to-the-paginated-report"></a>Assinar o relatório paginado
Quando você assina um relatório paginado, o Power BI envia um email com o relatório como anexo. Ao configurar sua assinatura, escolha a frequência com que deseja receber os emails: diariamente, semanalmente, mensalmente ou por hora. A assinatura contém um anexo com a saída do relatório completa, que pode ter até 25 MB. Exporte o relatório inteiro ou escolha os parâmetros antecipadamente. Escolha entre vários tipos de anexos, incluindo Excel, PDF, PowerPoint e muito mais.  

![Formatos para assinatura](./media/end-user-paginated-report/power-bi-export-list.png)

## <a name="considerations-and-troubleshooting"></a>Considerações e solução de problemas

- Um relatório paginado pode parecer estar em branco até você selecionar os parâmetros e escolher **Exibir relatório**.

- Se você não tiver nenhum relatório paginado, pode ser que ninguém tenha compartilhado esse tipo de relatório com você. Também é possível que o administrador do sistema não tenha habilitado relatórios paginados para você. 

 

## <a name="next-steps"></a>Próximas etapas
- [Relatórios do Power BI](end-user-reports.md)
- Mais perguntas? Experimente a [Comunidade do Power BI](https://community.powerbi.com/).

