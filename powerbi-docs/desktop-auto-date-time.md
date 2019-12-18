---
title: Data/hora automática no Power BI Desktop
description: Compreenda a funcionalidade de data/hora automática no Power BI Desktop.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 10/23/2019
ms.author: v-pemyer
ms.openlocfilehash: 1f350e8ff888ffc2fd95e6c47bf84ccc96ebf88b
ms.sourcegitcommit: 5bb62c630e592af561173e449fc113efd7f84808
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/11/2019
ms.locfileid: "75000148"
---
# <a name="auto-datetime-in-power-bi-desktop"></a>Data/hora automática no Power BI Desktop

Este artigo se destina a modeladores de dados que estão desenvolvendo modelos de Importação ou Compostos no Power BI Desktop. Ele apresenta e descreve a opção de _Data/hora automática_.

A Data/hora automática é uma opção de carregamento de dados no Power BI Desktop. A finalidade dessa opção é oferecer suporte a relatórios de inteligência de dados temporais convenientes com base em colunas de data carregadas em um modelo. Especificamente, ela permite que os autores de relatórios usem seu modelo de dados para filtrar, agrupar e fazer drill-down usando períodos do calendário (anos, trimestres, meses e dias). O que é importante é que você não precisa desenvolver explicitamente essas funcionalidades de inteligência de dados temporais.

Quando a opção está habilitada, o Power BI Desktop cria uma tabela de data/hora oculta automática para cada coluna de data, desde que todas as condições a seguir sejam verdadeiras:

- O modo de armazenamento de tabela é Import
- O tipo de dados da coluna é data ou data/hora
- A coluna não é o lado de "muitos" de um relacionamento de modelo

## <a name="how-it-works"></a>Como funciona

Cada tabela de data/hora automática é, na verdade, uma [tabela calculada](desktop-calculated-tables.md) que gera linhas de dados usando a função DAX [CALENDAR](/dax/calendar-function-dax). Cada tabela também inclui seis colunas calculadas: **Day**, **MonthNo**, **Month**, **QuarterNo**, **Quarter** e **Year**.

> [!NOTE]
> O Power BI traduz e formata os nomes e valores da coluna de acordo com a [linguagem do modelo](supported-languages-countries-regions.md#choose-the-language-for-the-model-in-power-bi-desktop).

O Power BI Desktop também cria uma relação entre a coluna **Data** da tabela de data/hora automática e a coluna de data do modelo.

A tabela de data/hora automática contém os anos de calendário completos que abrangem todos os valores de data armazenados na coluna de data do modelo. Por exemplo, se o valor mais antigo em uma coluna de data for 20 de março de 2016 e o valor mais recente for 23 de outubro de 2019, a tabela conterá 1.461 linhas. Representa uma linha para cada data nos quatro anos civis de 2016 a 2019. Quando o Power BI atualiza o modelo, cada tabela de data/hora automática também é atualizada. Dessa forma, o modelo sempre conterá datas que abrangem os valores da coluna de data.

Se fosse possível ver as linhas de uma tabela de data/hora automática, elas poderiam ter esta aparência:

![Exemplo de quais linhas de uma tabela de data/hora automática podem ser semelhantes. Exibe sete colunas: Date, Day, MonthNo, Month, QuarterNo, Quarter e Year. Exibe 10 linhas de dados que descrevem as datas de 1º de janeiro de 2019 a 10 de janeiro de 2019.](media/desktop-auto-date-time/auto-date-time-hidden-table-example-rows.png)

> [!NOTE]
> As tabelas de data/hora automáticas ficam permanentemente ocultas, mesmo para modeladores. Elas não podem ser vistas no painel **Campos** nem no diagrama de exibição de modelo e suas linhas não podem ser vistas na exibição de dados. Além disso, a tabela e sua coluna não podem ser referenciadas diretamente por expressões DAX.

A tabela também define uma hierarquia, fornecendo visuais com um caminho de busca detalhada nos níveis de ano, trimestre, mês e dia.

Se fosse possível ver uma tabela de data/hora automática no diagrama de exibição de modelo, ela poderia ser parecida com isto (colunas relacionadas são realçadas):

![Exemplo de como uma tabela de data/hora automática oculta poderia ser. Exibe duas tabelas: Sales e LocalDateTime. As tabelas são relacionadas com base na coluna OrderDate da tabela Sales e na coluna Date da tabela LocalDateTime. LocalDateTime define sete colunas: Date, Day, Month, MonthNo, Quarter, QuarterNo, Year e uma única hierarquia. A hierarquia é denominada Hierarquia de Data e consiste em quatro níveis: Year, Quarter, Month e Day.](media/desktop-auto-date-time/auto-date-time-hidden-table-example-diagram.png)

## <a name="work-with-auto-datetime"></a>Trabalhar com data/hora automática

Quando existe uma tabela de data/hora automática para uma coluna de data (e essa coluna está visível), os autores de relatório não localizam essa coluna como um campo no painel **Campos**. Em vez disso, eles encontrarão um objeto expansível que tem o nome da coluna de data. Você pode identificá-lo facilmente porque ele é adornado com um ícone de calendário. Quando os autores do relatório expandirem o objeto Calendário, eles encontrarão uma hierarquia chamada **Hierarquia de Data**. Depois de expandir a hierarquia, eles encontrarão quatro níveis: **Year**, **Quarter**, **Month** e **Day**.

![Exemplo do painel Campos com a tabela Sales expandida aberta. Ele contém um campo OrderDate, adornado com o ícone de calendário. Ele é expandido aberto e contém uma hierarquia chamada Hierarquia de Data. Ele também é expandido e contém quatro níveis: Year, Quarter, Month e Day.](media/desktop-auto-date-time/auto-date-time-fields-pane-example.png)

A hierarquia de data/hora automática gerada pode ser usada para configurar um visual exatamente da mesma maneira que as hierarquias normais podem ser usadas. Os visuais podem ser configurados usando toda a **Hierarquia de Data** ou níveis específicos da hierarquia.

Há, no entanto, uma funcionalidade adicional sem suporte em hierarquias normais. Quando a hierarquia de data/hora automática (ou um nível da hierarquia) é adicionada a um visual, o autor do relatório pode alternar entre usar a hierarquia ou a coluna de data. Essa abordagem faz sentido para alguns visuais, quando tudo de que você precisa é a coluna de data, não a hierarquia e seus níveis. Comece configurando o campo de visual (clique com o botão direito do mouse no campo de visual ou clique na seta para baixo) e, em seguida, use o menu de contexto para alternar entre a coluna data ou a hierarquia de data.

![Exemplo de uma configuração de campo visual para a hierarquia OrderDate. O menu de contexto aberto exibe duas opções, permitindo que a alternância use a coluna OrderDate ou a Hierarquia de Data.](media/desktop-auto-date-time/auto-date-time-configure-visuals-fields.png)

Por fim, os cálculos de modelo, gravados em DAX, podem referenciar uma coluna de data _diretamente_ ou as colunas da tabela de data/hora automática ocultas _indiretamente_.

A fórmula escrita no Power BI Desktop pode fazer referência a uma coluna de data da maneira normal. As colunas da tabela de data/hora automáticas, no entanto, devem ser referenciadas usando uma sintaxe estendida especial. Você começa fazendo referência à coluna de data e, em seguida, seguindo-a por um ponto (.). A barra de fórmulas preenchimento automático permitirá que você selecione uma coluna da tabela de data/hora automática.

![Exemplo de inserção de uma expressão de medida DAX na barra de fórmulas. A fórmula, até o momento, indica Date Count = COUNT(Sales[OrderDate]. e uma lista de preenchimento automático apresenta todas as sete colunas da tabela de data/hora automática oculta. Essas colunas são: Date, Day, Month, MonthNo, Quarter, QuarterNo e Year.](media/desktop-auto-date-time/auto-date-time-dax-auto-complete.png)

No Power BI Desktop, uma expressão de medida válida pode indicar:

```dax
Date Count = COUNT(Sales[OrderDate].[Date])
```

> [!NOTE]
> Embora essa expressão de medida seja válida no Power BI Desktop, ela não é uma sintaxe DAX correta. Internamente, o Power BI Desktop transpõe sua expressão para fazer referência à coluna da tabela de data/hora automática verdadeira (oculta).

## <a name="configure-auto-datetime-option"></a>Configurar opção de data/hora automática

A data/hora automática pode ser configurada _globalmente_ ou para o _arquivo atual_. A opção global se aplica a novos arquivos do Power BI Desktop e pode ser ativada ou desativada a qualquer momento. Para uma nova instalação do Power BI Desktop, as duas opções padrão são ativadas.

A opção de arquivo atual também pode ser ativada ou desativada a qualquer momento. Quando ativada, tabelas de data/hora automática são criadas. Quando desativada, todas as tabelas de data/hora automática são removidas do modelo.

> [!CAUTION]
> Tome cuidado ao desativar a opção de arquivo atual, pois isso removerá as tabelas de data/hora automática. Corrija todos os filtros de relatório ou visuais desfeitos que foram configurados para usá-los.

No Power BI Desktop selecione _Arquivo > Opções e configurações > Opções_ e, em seguida, selecione a página **Global** ou **Arquivo Atual**. Em qualquer página, a opção existe na seção **Inteligência de Tempo**.

![Como configurar opções do Power BI Desktop. A página Carregamento de Dados do grupo GLOBAL é selecionada. Na seção Inteligência de Dados Temporais, a opção data/hora automática para novos arquivos está marcada.](media/desktop-auto-date-time/auto-date-time-configure-global-options.png)

## <a name="next-steps"></a>Próximas etapas

Para obter mais informações relacionadas a este artigo, confira os seguintes recursos:

- [Diretrizes de data/hora automática no Power BI Desktop](guidance/auto-date-time.md)
- [Definir e usar tabelas de datas no Power BI Desktop](desktop-date-tables.md)
- Dúvidas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
