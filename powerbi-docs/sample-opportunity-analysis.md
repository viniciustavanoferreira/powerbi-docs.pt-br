---
title: 'Exemplo de Análise de Oportunidade para o Power BI: Faça um tour'
description: 'Exemplo de Análise de Oportunidade para o Power BI: Faça um tour'
author: maggiesMSFT
ms.reviewer: amac
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 07/02/2019
ms.author: maggies
LocalizationGroup: Samples
ms.openlocfilehash: d871fa15c999e5b6c83b0334d6c978b2ba3c9870
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/09/2019
ms.locfileid: "73858701"
---
# <a name="opportunity-analysis-sample-for-power-bi-take-a-tour"></a>Exemplo de Análise de Oportunidade para o Power BI: Faça um tour

O pacote de conteúdo de exemplo da Análise de Oportunidade contém um painel, um relatório e um conjunto de dados para uma empresa de software que possui dois canais de vendas: *direto* e *parceiro*. O gerente de vendas criou este painel para rastrear oportunidades e receita por região, tamanho da transação e canal.

O exemplo se baseia em duas medidas de receita:

* Receita: A estimativa de um vendedor sobre qual será a receita.
* Receita fatorada: é calculada como a porcentagem (%) entre a receita x probabilidade e é aceita como sendo uma previsão mais precisa da receita de vendas real. A probabilidade é determinada pelo *estágio de venda do negócio* em andamento:
  * Cliente potencial: 10%  
  * Qualificar: 20%  
  * Solução: 40%  
  * Proposta: 60%  
  * Finalizar: 80%

![Painel para o exemplo de Análise de Oportunidade](media/sample-opportunity-analysis/opportunity1.png)

Este exemplo faz parte de uma série que mostra como o Power BI pode ser usado com dados, relatórios e painéis orientados aos negócios. Ele foi criado pela [obviEnce](http://www.obvience.com/) usando dados reais, que foram mantidos anônimos. Os dados estão disponíveis em vários formatos: pacote de conteúdo, arquivo .pbix do Power BI Desktop ou pasta de trabalho do Excel. Confira [Exemplos para o Power BI](sample-datasets.md). 

Este tutorial explora o pacote de conteúdo de exemplo de Análise de Oportunidade no serviço do Power BI. Como as experiências de relatório são muito semelhantes no Power BI Desktop e no serviço, você também pode acompanhar usando o arquivo de exemplo .pbix no Power BI Desktop. 

Você não precisa de uma licença do Power BI para explorar os exemplos no Power BI Desktop. Se você não tiver uma licença do Power BI Pro, poderá salvar a amostra em Meu Espaço de Trabalho no serviço do Power BI. 

## <a name="get-the-sample"></a>Obter o exemplo

Antes de usar o exemplo, primeiro você deve baixá-lo como um [pacote de conteúdo](#get-the-content-pack-for-this-sample), [arquivo .pbix](#get-the-pbix-file-for-this-sample) ou [pasta de trabalho do Excel](#get-the-excel-workbook-for-this-sample).

### <a name="get-the-content-pack-for-this-sample"></a>Obter o pacote de conteúdo para este exemplo

1. Abra o serviço do Power BI (app.powerbi.com), entre e abra o workspace em que você deseja salvar o exemplo. 

    Se você não tiver uma licença do Power BI Pro, poderá salvar a amostra em Meu Espaço de Trabalho.

2. No canto inferior esquerdo, selecione **Obter Dados**.

    ![Selecionar Obter Dados](media/sample-datasets/power-bi-get-data.png)
3. Na página **Obter Dados** que aparece, selecione **Exemplos**.

4. Selecione o **Exemplo de Análise de Oportunidade** e escolha **Conectar**.  

   ![Conectar-se ao exemplo](media/sample-opportunity-analysis/opportunity-connect.png)
5. O Power BI importa o pacote de conteúdo e adiciona um novo painel, um relatório e um conjunto de dados ao seu espaço de trabalho atual.

   ![Entrada de Exemplo de Análise de Oportunidade](media/sample-opportunity-analysis/opportunity-entry.png)

### <a name="get-the-pbix-file-for-this-sample"></a>Obter o arquivo. pbix para este exemplo

Como alternativa, você pode baixar o exemplo de Análise de Oportunidade como um [arquivo .pbix](https://download.microsoft.com/download/9/1/5/915ABCFA-7125-4D85-A7BD-05645BD95BD8/Opportunity%20Analysis%20Sample%20PBIX.pbix), que foi projetado para uso com o Power BI Desktop.

### <a name="get-the-excel-workbook-for-this-sample"></a>Obter a pasta de trabalho do Excel para este exemplo

Se quiser exibir a fonte de dados deste exemplo, ela também está disponível como uma [Pasta de trabalho do Excel](https://go.microsoft.com/fwlink/?LinkId=529782). A pasta de trabalho contém planilhas do Power View que você pode exibir e modificar. Para ver os dados brutos, habilite os suplementos de Análise de Dados e, em seguida, selecione **Power Pivot > Gerenciar**. Para habilitar os suplementos Power View e Power Pivot, confira [Dar uma olhada nos exemplos do Excel dentro do próprio Excel](sample-datasets.md#optional-take-a-look-at-the-excel-samples-from-inside-excel-itself) para obter detalhes.

## <a name="what-is-our-dashboard-telling-us"></a>O que é nosso painel está dizendo?
Nossa gerente de vendas criou um dashboard para acompanhar as métricas mais importantes para ela. Quando ela vir algo interessante, pode selecionar um bloco para examinar os dados:

- A receita da empresa é de US $2 bilhões e a receita fatorada é de US $461 milhões.
- A contagem de oportunidades e a receita seguem um padrão familiar de funil, com os totais diminuindo a cada estágio subsequente.
- A maioria de nossas oportunidades são na região leste.
- Grandes oportunidades geram receita maior do que oportunidades de pequenas ou médias.
- Grandes acordos com parceiros geram mais receita: US$ 8 milhões em média, contra US$ 6 milhões em vendas diretas.

Como o esforço para conseguir um acordo é o mesmo, seja o negócio classificado como grande, médio ou pequeno, nossa empresa deve analisar os dados para saber mais sobre grandes oportunidades.

1. No espaço de trabalho onde você salvou o exemplo, abra a guia **Painéis**, localize o painel **Exemplo de Análise de Oportunidade** e selecione-o.

2. Selecione o bloco **Contagem de Oportunidades por Parceiro, Estágio de Vendas** para abrir a primeira página do relatório Exemplo de Análise de Oportunidade. 

    ![Bloco Contagem de Oportunidades por Parceiro, Estágio de Vendas](media/sample-opportunity-analysis/opportunity2.png)

## <a name="explore-the-pages-in-the-report"></a>Explore outras páginas no relatório

Exiba cada página no relatório selecionando as guias da página na parte inferior.

### <a name="opportunity-count-overview-page"></a>Página Visão Geral da Contagem de Oportunidades
![Página Contagem de Oportunidades](media/sample-opportunity-analysis/opportunity3.png)

Observe o seguintes detalhes:
* Leste é nossa região maior em termos de contagens de oportunidade.  
* No gráfico de pizza **Contagem de Oportunidades por Região**, selecione cada região para filtrar a página por região. Para cada região, observe que os parceiros estão buscando significativamente mais oportunidades grandes.   
* O gráfico de coluna **Contagem de Oportunidades por Parceiro e Tamanho de Oportunidade** mostra que a maioria das grandes oportunidades é controlada por parceiros, enquanto a maioria das oportunidades pequenas e médias não são.
* No gráfico de barras **Contagem de Oportunidades por Estágio de Vendas**, selecione cada **Estágio de Vendas** para ver a diferença na contagem regional. Observe que, embora a região leste tenha a maior contagem de oportunidades, todas as três regiões nos estágios de vendas Solução, Proposta e Finalizar têm contagens comparáveis. Esse resultado significa que fechamos uma porcentagem maior de negócios nas regiões central e oeste.

### <a name="revenue-analysis-page"></a>Página Análise da Receita
Esta página analisa os dados de forma semelhante, mas usa uma perspectiva de receita em vez de contagem.  

![Página Visão Geral da Receita](media/sample-opportunity-analysis/opportunity4.png)

Observe o seguintes detalhes:
* O leste é a nossa maior região, não apenas na contagem de oportunidades, mas também na receita.  
* Se você filtrar o gráfico **Receita por Estágio de Vendas e por Parceiro** selecionando **Sim** para **Por Parceiro**, verá uma receita de US$ 1,5 bilhão e uma receita estimada de US$ 294 milhões. Compare esses montantes a US$ 644 milhões e US$ 166 milhões por receita não controlada por parceiros. 
* A receita média para contas grandes é maior em 8 milhões se a oportunidade for de parceiros, em comparação com 6 milhões para negócios não parceiros.  
* Para parceiros comerciais, a receita média para grandes oportunidades é quase o dobro das oportunidades médias.  
* A receita média para pequenas e médias empresas é comparável aos parceiros e não parceiros comerciais.   

É evidente que nossos parceiros estão fazendo um trabalho melhor do que os não parceiros na venda aos clientes. Pode fazer sentido para direcionar mais negócios por meio de nossos parceiros.

### <a name="opportunity-count-by-region-and-stage"></a>Contagem de Oportunidades por Região e Estágio
Esta página do relatório analisa dados semelhantes aos dados da página anterior, mas os divide por região e cenário. 

![Página Contagens de Estágio de Região](media/sample-opportunity-analysis/opportunity5.png)

Observe o seguintes detalhes:
* Se você selecionar **Leste** no gráfico de pizza **Contagem de Oportunidades por Região** para filtrar pela região Leste, verá que as oportunidades nessa região são divididas quase igualmente entre parceiros e não parceiros.
* As grandes oportunidades são mais comuns na região central, pequena oportunidades são as mais comuns na região leste e oportunidades de médio porte são as mais comuns na região oeste.

### <a name="upcoming-opportunities-by-month-page"></a>Página Oportunidades Futuras por Mês
Para esta página, estamos analisando fatores semelhantes, mas a partir de uma perspectiva de data e hora. 
 
![Página Oportunidades Futuras](media/sample-opportunity-analysis/opportunity6.png)

Nosso CFO usa esta página para gerenciar a carga de trabalho. Ao examinar as oportunidades de receita por mês e o estágio de vendas, ela pode planejar adequadamente.

Observe o seguintes detalhes:
* A receita média para o estágio Finalizar vendas é a mais alta. Essas ofertas de fechamento são prioridade.
* Se você filtrar por mês (selecionando um mês na segmentação **Mês**), verá que janeiro tem uma alta proporção de transações grandes no estágio de vendas Finalizar com uma receita estimada de US$ 75 milhões. Em fevereiro, por outro lado, a maioria dos negócios médios está nos estágios de venda Solução e Proposta.
* Em geral, os números de receita fatorada flutuam com base no estágio de vendas, o número de oportunidades e o tamanho do negócio. Adicione filtros para esses fatores usando o painel **Filtro** à direita para descobrir mais insights.

## <a name="next-steps-connect-to-your-data"></a>Próximas etapas: Conecte-se aos seus dados
Esse ambiente é seguro para teste, pois você pode optar por não salvar as alterações. Mas se você salvá-las, sempre é possível selecionar **Obter Dados** para ter uma nova cópia deste exemplo.

Esperamos que este tour tenha mostrado como os painéis, P e R e relatórios do Power BI podem fornecer informações sobre os dados de exemplo. Agora é sua vez – conecte-se aos seus próprios dados. Com o Power BI, é possível se conectar a uma grande variedade de fontes de dados. Para saber mais, confira [Introdução ao serviço do Power BI](service-get-started.md).

