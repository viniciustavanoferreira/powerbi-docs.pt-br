---
title: Acessar tabelas em destaque do Power BI no Excel (versão preliminar)
description: No Excel, você pode encontrar dados de tabelas em destaque em conjuntos de dados do Power BI na Galeria de Tipos de Dados.
author: maggiesMSFT
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 05/20/2020
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: a872c0ada80a7168ebc6bb545de1ad474c4561b7
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85226353"
---
# <a name="access-power-bi-featured-tables-in-excel-preview"></a>Acessar tabelas em destaque do Power BI no Excel (versão preliminar)

No Excel, você pode encontrar dados de tabelas em destaque em conjuntos de dados do Power BI na Galeria de Tipos de Dados. As tabelas em destaque facilitam a adição de dados empresariais a suas planilhas do Excel. Usando os recursos de conjuntos de dados certificados e promovidos do Power BI, as organizações permitem que mais usuários encontrem e usem dados relevantes e atualizáveis para tomar decisões melhores. Leia a documentação do Excel para saber mais como usar [tipos de dados do Excel vinculados ao Power BI](https://support.office.com/article/use-excel-data-types-from-power-bi-preview-cd8938ce-f963-444d-b82a-7140848241e9).

A galeria Tipos de Dados mostra somente as tabelas em destaque definidas por um modelador nos conjunto de dados do Power BI. Os conjuntos de dados acessíveis no Power BI também podem ser encontrados no Excel. No Excel, selecione a opção **Conjunto de Dados do Power BI** em **Obter Dados** na faixa de opções **Dados**.

## <a name="access-power-bi-data-through-the-excel-data-types-gallery"></a>Acessar dados do Power BI por meio da galeria Tipos de Dados do Excel
As tabelas em destaque nos conjuntos de dados do Power BI são exibidas na galeria Tipos de Dados do Excel na faixa de opções Dados.

:::image type="content" source="media/service-excel-featured-tables/excel-data-ribbon.png" alt-text="Faixa de opções Dados Excel":::

Quando expandida, a galeria mostra os principais tipos de dados disponíveis.

:::image type="content" source="media/service-excel-featured-tables/excel-data-types-gallery.png" alt-text="Galeria Tipos de Dados do Excel":::
 
Para pesquisar dados em uma tabela em destaque do Power BI, selecione uma célula ou um intervalo na planilha do Excel.

:::image type="content" source="media/service-excel-featured-tables/excel-select-cell.png" alt-text="Selecionar uma célula":::
 
Selecione a opção **Dados Organizacionais** da galeria para pesquisar dados em tabelas em destaque nos conjuntos de dados certificados aos quais você tem acesso.

:::image type="content" source="media/service-excel-featured-tables/excel-organizational-data.png" alt-text="Dados organizacionais do Excel":::
 
Selecione um tipo de dados específico se você souber que tipo de dados está pesquisando, ou se não encontrar linhas correspondentes usando a opção Dados Organizacionais.

:::image type="content" source="media/service-excel-featured-tables/excel-select-data-type.png" alt-text="Selecionar um tipo de dados":::
 
Ao fazer uma pesquisa, se uma linha correspondente for encontrada com alta confiança, a célula será imediatamente vinculada a essa linha. O ícone do item vinculado indica que a célula está vinculada à linha no Power BI.

:::image type="content" source="media/service-excel-featured-tables/excel-linked-item-icon.png" alt-text="Ícone de item vinculado":::

Se uma célula tiver várias linhas correspondentes potenciais, um painel seletor de dados será mostrado. A célula mostra o ícone de ponto de interrogação, que abre o painel seletor de dados para essa linha. No exemplo a seguir, o usuário já selecionou um intervalo de A2:A7 e pesquisou uma tabela de recursos do Power BI.

:::image type="content" source="media/service-excel-featured-tables/excel-multiple-matches.png" alt-text="Várias linhas correspondentes possíveis":::

O painel **Seletor de Dados** mostra as linhas potencialmente correspondentes.

:::image type="content" source="media/service-excel-featured-tables/excel-data-selector-pane.png" alt-text="Painel Seletor de Dados do Excel":::
 
A opção Dados Organizacionais pode retornar linhas de vários tipos de dados. O Excel agrupa as linhas potencialmente correspondentes pelo tipo de dados do qual elas vieram. O Excel classifica os tipos de dados com base na linha correspondente mais forte possível. Use as setas de divisa para recolher e expandir os tipos de dados para linhas correspondentes.

:::image type="content" source="media/service-excel-featured-tables/excel-data-selector-multiple.png" alt-text="Painel Seletor de Dados do Excel":::
 
Para escolher a linha correta, selecione o nome da linha para ver mais detalhes. Após encontrar uma linha, pressione **Selecionar** para vincular a linha à célula no Excel. 

:::image type="content" source="media/service-excel-featured-tables/excel-data-selector-select.png" alt-text="Detalhes do Seletor de Dados":::
 
Quando uma linha é selecionada, a célula é vinculada à linha e seu valor corresponde ao valor do campo **Rótulo de Linha** na tabela em destaque do Power BI. 

:::image type="content" source="media/service-excel-featured-tables/excel-linked-item-icon.png" alt-text="Item vinculado do Excel":::
 
A seleção do ícone de **célula vinculada** mostra um cartão com dados de quaisquer campos e campos calculados na tabela em destaque. O título do cartão mostra o valor do campo do rótulo de linha na tabela em destaque.
 
:::image type="content" source="media/service-excel-featured-tables/excel-linked-item-details.png" alt-text="Detalhes do item vinculado":::

Selecione o ícone **Inserir Dados** para adicionar valores de campo à grade.

:::image type="content" source="media/service-excel-featured-tables/excel-insert-data.png" alt-text="Inserir dados"::: 

Selecione um nome de campo na lista de campos para adicionar seu valor à grade.  

:::image type="content" source="media/service-excel-featured-tables/excel-select-field.png" alt-text="Selecionar um nome de campo":::

O valor do campo é colocado na célula adjacente. A fórmula da célula refere-se à célula vinculada e ao nome do campo, para que você possa usar os dados em funções do Excel.

:::image type="content" source="media/service-excel-featured-tables/excel-cell-formula.png" alt-text="Fórmula de célula do Excel":::
 
Quando você formata seus dados como uma tabela do Excel, a adição de campos expande a tabela e define o cabeçalho da coluna para corresponder ao nome do campo. As linhas vinculadas aos mesmos tipos de dados também são preenchidas com seus respectivos valores.

:::image type="content" source="media/service-excel-featured-tables/excel-field-column-name.png" alt-text="O campo é o nome da coluna"::: 

## <a name="cell-formulas"></a>Fórmulas de células

Ao usar uma tabela do Excel, você pode fazer referência à coluna da tabela vinculada e, em seguida, adicionar campos de dados usando a referência de `.` (ponto).

:::image type="content" source="media/service-excel-featured-tables/excel-dot-reference.png" alt-text="Referência de ponto do Excel":::

Da mesma forma, ao usar uma célula, você pode fazer referência à célula e usar a referência de `.` (ponto) para recuperar campos.

:::image type="content" source="media/service-excel-featured-tables/excel-cell-dot-reference.png" alt-text="Referência de ponto da célula":::
 
## <a name="data-caching-and-refresh"></a>Atualização e cache de dados

Quando o Excel vincula uma célula a uma linha em uma tabela em destaque do Power BI, ele recupera e salva todos os valores do campo no arquivo do Excel. Qualquer pessoa com a qual você compartilha o arquivo pode fazer referência a qualquer um dos campos, sem solicitar dados do Power BI.  

Use o botão **Atualizar Tudo** na faixa de opções **Dados** para atualizar dados em células vinculadas. 

:::image type="content" source="media/service-excel-featured-tables/excel-refresh-all.png" alt-text="Atualizar Tudo":::
 
Você também pode atualizar células individuais. Clique com o botão direito do mouse na célula e selecione **Tipos de Dados** > **Atualizar**.

## <a name="show-a-card-change-or-convert-to-text"></a>Mostrar um cartão, alterar ou converter em texto

As células vinculadas têm opções de menu com o botão direito do mouse adicionadas. Clique com o botão direito do mouse em uma célula > selecione **Tipos de Dados** >  

- **Mostrar Cartão**
- **Atualizar**
- **Alteração** 
- **Converter em Texto**.

:::image type="content" source="media/service-excel-featured-tables/excel-right-click-data-type.png" alt-text="Clique com o botão direito do mouse em Converter em Texto":::
 
**Converter em Texto** remove o link para a linha na tabela em destaque do Power BI. Além disso, o texto na célula será o valor do rótulo de linha da célula vinculada. Se você vinculou uma célula a uma linha que não pretendia, selecione **Desfazer** no Excel para restaurar os valores iniciais da célula.

## <a name="licensing"></a>Licenças
A galeria Tipos de Dados do Excel e experiências conectadas para tabelas em destaque do Power BI estão disponíveis somente para clientes do Excel E5 e G5. 

## <a name="security"></a>Segurança

Você vê somente tabelas em destaque de conjuntos de dados dos quais tem permissão no Power BI. Durante a atualização de dados, você deve ter permissão para acessar o conjunto de dados no Power BI para recuperar as linhas. Isso requer a permissão Criar ou Gravar no conjunto de dados. O Excel armazena em cache os dados retornados para a linha inteira. Qualquer pessoa com a qual você compartilha o arquivo do Excel pode ver os dados de todos os campos em todas as células vinculadas.

Se um conjunto de dados Power BI tiver segurança em nível de linha ou um rótulo de confidencialidade da Proteção de Informações da Microsoft aplicado a ele, as tabelas em destaque desse conjunto não serão incluídas na galeria Tipos de Dados do Excel. Essa é uma limitação da versão preliminar inicial.

## <a name="curate-a-featured-table-in-power-bi-desktop"></a>Coletar uma tabela em destaque no Power BI Desktop
A galeria Tipos de Dados do Excel mostra as tabelas em destaque em conjuntos de dados carregados para o serviço do Power BI. Use o Power BI Desktop para coletar as tabelas em destaque no modelo de dados e carregá-las no serviço do Power BI.

### <a name="turn-on-the-featured-table-preview"></a>Ativar a versão preliminar da tabela em destaque

1. No Power BI Desktop, selecione **Arquivo** > **Opções e Configurações** > **Opções** > **Versão Prévia dos Recursos**.
2. Marque a caixa de seleção **Tabelas em destaque**.

    :::image type="content" source="media/service-excel-featured-tables/power-bi-preview-featured-tables.png" alt-text="Opção Versão prévia das tabelas em destaque":::

### <a name="select-a-table"></a>Selecionar uma tabela

1. No Power BI Desktop, vá para Exibição de modelo.

    :::image type="content" source="media/service-excel-featured-tables/power-bi-model-view.png" alt-text="Exibição de modelo":::
 
2. Selecione uma tabela e defina **É tabela em destaque** para **Sim**.

    :::image type="content" source="media/service-excel-featured-tables/power-bi-featured-table-yes.png" alt-text="Definir É tabela em destaque como Sim":::

4. Em **Configurar esta tabela em destaque**, forneça os campos obrigatórios:

    - Uma **Descrição**.
    - O valor do campo **Rótulo de linha** é usado no Excel para que os usuários possam identificar facilmente a linha. Ele aparece como o valor da célula de uma célula vinculada, no painel **Seletor de Dados** e no cartão **Informações**. 
    - O valor do campo **Coluna de chave** fornece a ID exclusiva para a linha. Esse valor permite que o Excel vincule uma célula a uma linha específica na tabela.

    :::image type="content" source="media/service-excel-featured-tables/power-bi-set-up-featured-table.png" alt-text="Configurar tabela em destaque":::

Após publicar ou importar o conjunto de dados para a serviço do Power BI, a tabela em destaque é exibida na galeria Tipos de Dados do Excel.

- O Excel armazena em cache a lista de tipos de dados, portanto, é necessário reiniciar o Excel para ver as tabelas em destaque publicadas recentemente.
- Alguns conjuntos de dados não têm suporte na versão preliminar, as tabelas em destaque definidas neles não aparecerão no Excel. Confira considerações e limitações para obter mais detalhes.

## <a name="administrative-control"></a>Controle administrativo

Os administradores do Power BI podem controlar quem na organização pode usar tabelas em destaque na galeria Tipos de Dados do Excel. Confira [Configurações de tabelas em destaque](../admin/service-admin-portal.md#featured-tables-settings) no artigo do Portal de administração para obter detalhes. 
 
### <a name="auditing"></a>Auditoria

Os logs de auditoria de administração mostram estes eventos para tabelas em destaque:

- **AnalyzedByExternalApplication**: dá aos administradores visibilidade dos usuários que estão acessando cada tabela em destaque.
- **UpdateFeaturedTables**: dá aos administradores visibilidade dos usuários que estão publicando e atualizando tabelas em destaque.

Para obter uma lista completa dos eventos de log de auditoria, confira [Acompanhar atividades do usuário no Power BI](../admin/service-admin-auditing.md).

## <a name="considerations-and-limitations"></a>Considerações e limitações

Aqui estão as limitações para a versão preliminar inicial:

- A integração está disponível em compilações internas do Excel.
- A galeria Tipos de Dados do Excel inclui tabelas em destaque para usuários com a licença apropriada no Power BI Desktop e no serviço do Power BI. O suporte para o serviço do Power BI pode não estar disponível no lançamento da versão preliminar, mas será adicionado.
- As tabelas em destaque em conjuntos de dados do Power BI que usam os seguintes recursos não são mostradas no Excel: 

    - Conjuntos de dados de segurança em nível de linha.
    - Conjuntos de dados habilitados da Proteção de Informações da Microsoft.
    - Conjuntos de dados do DirectQuery.
    - Conjuntos de dados com uma conexão dinâmica.

- O Excel mostra somente os dados em colunas e colunas calculadas na tabela em destaque. Os itens a seguir não são fornecidos na versão preliminar inicial:

    - Medidas definidas na tabela de recursos.
    - Medidas definidas em tabelas relacionadas e medidas implícitas calculadas de relações.

- O Excel exibe somente tabelas em destaque armazenadas nos novos workspaces do Power BI. Tabelas em destaque armazenadas nos workspaces clássicos, ou em Meu Workspace, não são mostradas como tipos de dados no Excel. Você pode [atualizar workspaces clássicos para os novos workspaces](service-upgrade-workspaces.md) no Power BI.

A experiência de Tipos de Dados no Excel é semelhante a uma função de pesquisa. Usa um valor de célula fornecido pela planilha do Excel e pesquisa linhas correspondentes nas tabelas em destaque do Power BI. A experiência de pesquisa tem os seguintes comportamentos:

- Ao usar o botão **Dados Organizacionais** para pesquisar, o Excel pesquisa somente tabelas em destaque em conjuntos de dados certificados.
- A correspondência de linha é baseada em colunas de texto na tabela em destaque. Usa a mesma indexação que o recurso P e R do Power BI, que é otimizado para pesquisa em inglês. Pesquisar em outros idiomas pode não resultar em correspondências precisas. As colunas numéricas não são consideradas para correspondência.
- A correspondência é baseada em correspondências exatas e de prefixo para termos de pesquisa individuais. O valor de uma célula é dividido com base em espaços ou em outros caracteres de espaço em branco como guias. Em seguida, cada palavra é considerada um termo de pesquisa. Os valores do campo de texto de uma linha são comparados a cada termo de pesquisa para correspondências exatas e de prefixo. Uma correspondência de prefixo será retornada se o campo de texto da linha começar com o termo de pesquisa. Por exemplo, se uma célula contiver "São Paulo", então "São" e "Paulo" serão termos de pesquisa distintos. 

    - As linhas com colunas de texto cujo valor corresponda exatamente a "São" ou "Paulo" serão retornadas. 
    - As linhas com colunas de texto cujo valor comece com "São" ou "Paulo" serão retornadas. 
    - Além disso, as linhas que contenham "São" ou "Paulo", mas não comecem com esses valores, não serão retornadas.

- O Power BI retorna no máximo 100 sugestões de linha para cada célula.
- Não há suporte para a configuração ou atualização da tabela em destaque no ponto de extremidade XMLA
- Arquivos do Excel com um modelo de dados podem ser usados para publicar tabelas em destaque. Carregue os dados no Power BI Desktop e, em seguida, publique a tabela em destaque.
- Alterar o nome da tabela, o rótulo da linha ou a coluna de chave da tabela em destaque pode afetar os usuários do Excel com células vinculadas a linhas na tabela. 
- O Excel mostra quando os dados foram recuperados do conjunto de dados do Power BI. Isso não é necessariamente o momento em que os dados foram atualizados no Power BI, ou a hora do ponto de dados mais recente em um conjunto de dados. Por exemplo, digamos que um conjunto de dados no Power BI tenha sido atualizado há uma semana, mas os dados de origem subjacentes tinham uma semana quando a atualização ocorreu. Os dados reais seriam de duas semanas, mas o Excel mostraria os dados recuperados como a data/hora em que os dados foram obtidos no Excel.

## <a name="next-steps"></a>Próximas etapas

- Dúvidas? [Experimente a Comunidade do Power BI](https://community.powerbi.com/)

