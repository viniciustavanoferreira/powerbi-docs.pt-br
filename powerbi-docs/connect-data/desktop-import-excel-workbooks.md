---
title: Importar pastas de trabalho do Excel para o Power BI Desktop
description: Você pode importar pastas de trabalho do Excel que contêm consultas do Power Query, modelos do Power Pivot e planilhas do Power View para o Power BI Desktop.
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/22/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 68dce4919dcc15cfcdd6a7c6776d569e43f9666b
ms.sourcegitcommit: a72567f26c1653c25f7730fab6210cd011343707
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83561715"
---
# <a name="import-excel-workbooks-into-power-bi-desktop"></a>Importar pastas de trabalho do Excel para o Power BI Desktop
Com o Power BI Desktop, você pode importar facilmente pastas de trabalho do Excel que contêm consultas do Power Query, modelos do Power Pivot e planilhas do Power View para o Power BI Desktop. O Power BI Desktop cria automaticamente relatórios e visualizações com base na pasta de trabalho do Excel. Uma vez importados, você pode continuar melhorando e refinando esses relatórios com o Power BI Desktop, usando os recursos existentes e novos recursos lançados com cada atualização mensal do Power BI Desktop.

## <a name="how-do-i-import-an-excel-workbook"></a>Como importar uma pasta de trabalho do Excel?
1. Para importar uma pasta de trabalho do Excel para o Power BI Desktop, selecione **Arquivo** > **Importar** > **Power Query, Power Pivot, Power View**.

   ![Importar pasta de trabalho do Excel](media/desktop-import-excel-workbooks/importexceltopbi_1.png)


2. Na janela **Abrir**, selecione uma pasta de trabalho do Excel para importar. 

   Embora no momento não haja nenhuma limitação para o tamanho ou número de objetos na pasta de trabalho, o Power BI Desktop leva mais tempo para analisar e importar pastas de trabalho maiores.

   > [!NOTE]
   > Para carregar ou importar arquivos do Excel de pastas do OneDrive for Business compartilhado ou de pastas do Microsoft 365, use o URL do arquivo Excel e insira-os na fonte de dados na Web, no Power BI Desktop. Existem algumas etapas que você precisa seguir para formatar corretamente a URL do OneDrive for Business; para obter informações e a série correta de etapas, confira [Usar os links do OneDrive for Business no Power BI Desktop](desktop-use-onedrive-business-links.md).
   > 
   > 

3. Na caixa de diálogo Importar exibida, selecione **Iniciar**.

   ![Importar conteúdo da pasta de trabalho do Excel](media/desktop-import-excel-workbooks/import-excel-power-bi-5.png)


   O Power BI Desktop analisa a pasta de trabalho e converte-a em um arquivo do Power BI Desktop (.pbix). Essa ação é um evento único; depois de criar o arquivo do Power BI Desktop com essas etapas, ele não terá nenhuma dependência da pasta de trabalho original do Excel e poderá ser modificado, salvo e compartilhado sem afetar a pasta de trabalho original.

   Depois que a importação for concluída, será exibida uma página de resumo que descreve os itens que foram convertidos e também lista os itens que não puderam ser importados.

   ![Importar página de resumo](media/desktop-import-excel-workbooks/importexceltopbi_3.png)

4. Selecione **Fechar**. 

   O Power BI Desktop importa a pasta de trabalho do Excel e carrega um relatório baseado no conteúdo da pasta de trabalho.

   ![Relatório de importação carregado](media/desktop-import-excel-workbooks/importexceltopbi_4.png)

Depois que a pasta de trabalho for importada, você poderá continuar trabalhando no relatório. Você pode criar visualizações, adicionar dados ou criar páginas de relatório usando qualquer um dos recursos e funcionalidades incluídos no Power BI Desktop.

## <a name="which-workbook-elements-are-imported"></a>Quais elementos de pasta de trabalho são importados?
O Power BI Desktop pode importar os elementos a seguir, normalmente conhecidos como *objetos*, no Excel.

| Objeto na pasta de trabalho do Excel | Resultado final no arquivo do Power BI Desktop |
| --- | --- |
| Consultas do Power Query |Todas as consultas do Power Query do Excel são convertidas em consultas no Power BI Desktop. Se houver grupos de consulta definidos na Pasta de Trabalho do Excel, a mesma organização será replicada no Power BI Desktop. Todas as consultas são carregadas, a menos que sejam definidas como **Apenas Criar Conexão** na caixa de diálogo do Excel **Importar Dados**. O comportamento de carregamento é personalizado selecionando **Propriedades** na guia **Página Inicial** do Editor do Power Query no Power BI Desktop. |
| Conexões de dados externos do Power Pivot |Todas as conexões de dados externos do Power Pivot são convertidas em consultas no Power BI Desktop. |
| Tabelas vinculadas ou tabelas de pasta de trabalho atual |Se houver uma tabela de planilha no Excel vinculada ao modelo de dados ou a uma consulta (usando *Da Tabela* ou a função *Excel.CurrentWorkbook()* em M), serão apresentadas as seguintes opções: <ol><li><b>Importe a tabela para o arquivo do Power BI Desktop</b>. Essa tabela é um instantâneo único dos dados, após o qual os dados serão somente leitura na tabela no Power BI Desktop. Há um limite de tamanho de 1 milhão de caracteres (no total, combinando todas as células e cabeçalhos de coluna) para tabelas criadas usando essa opção.</li><li><b>Mantenha uma conexão com a pasta de trabalho original</b>. Como alternativa, você pode manter uma conexão para a Pasta de Trabalho original do Excel e o Power BI Desktop recupera o conteúdo mais recente nessa tabela com cada atualização, assim como qualquer outra consulta criada para uma pasta de trabalho do Excel no Power BI Desktop.</li></ul> |
| Colunas calculadas, medidas, KPIs, categorias de dados e relacionamentos do modelo de dados |Esses objetos de modelo de dados são convertidos em objetos equivalentes no Power BI Desktop. Observe que existem certas categorias de dados que não estão disponíveis no Power BI Desktop, como Imagem. Nesses casos, as informações de categoria de dados serão redefinidas para as colunas em questão. |
| Planilhas do Power View |Uma nova página de relatório é criada para cada planilha do Power View no Excel. O nome e a ordem dessas páginas de relatório correspondem àqueles da pasta de trabalho original do Excel. |

## <a name="are-there-any-limitations-to-importing-a-workbook"></a>Há alguma limitação para importar uma pasta de trabalho?
Existem algumas limitações para importar uma pasta de trabalho no Power BI Desktop:

* **Conexões externas para modelos de tabela do SQL Server Analysis Services:** No Excel 2013, é possível criar uma conexão com os modelos de tabela do SQL Server Analysis Services e criar relatórios do Power View sobre esses modelos, sem a necessidade de importar os dados. Atualmente, não há suporte para esse tipo de conexão como parte da importação de pastas de trabalho do Excel para o Power BI Desktop. Como solução, você deve recriar essas conexões externas no Power BI Desktop.
* **Hierarquias:** atualmente, não há suporte para esse tipo de objeto de modelo de dados no Power BI Desktop. Desse modo, as hierarquias são ignoradas como parte da importação de uma pasta de trabalho do Excel para o Power BI Desktop.
* **Colunas de dados binários:** atualmente, não há suporte para esse tipo de coluna de modelo de dados no Power BI Desktop. Colunas de dados binários são removidas da tabela resultante no Power BI Desktop.
* **Elementos sem suporte do Power View:** há alguns recursos do Power View que não estão disponíveis no Power BI Desktop, como temas ou determinados tipos de visualizações (gráfico de dispersão com eixo de reprodução, comportamentos de drill down e assim por diante). Estas visualizações sem suporte resultam em mensagens de *Visualização Sem Suporte* em seus locais correspondentes no relatório do Power BI Desktop, que você pode excluir ou reconfigurar conforme necessário.
* **Intervalos nomeados usando** ***Da Tabela*** **no Power Query ou usando** ***Excel.CurrentWorkbook*** **em M:** atualmente, não há suporte para a importação desses dados de intervalo nomeado para o Power BI Desktop, mas essa é uma atualização planejada. Atualmente, esses intervalos nomeados são carregados no Power BI Desktop como uma conexão à pasta de trabalho externa do Excel.
* **PowerPivot para SSRS:** atualmente, não há suporte para conexões externas do PowerPivot ao SSRS (SQL Server Reporting Services), porque essa fonte de dados não está disponível atualmente no Power BI Desktop.

