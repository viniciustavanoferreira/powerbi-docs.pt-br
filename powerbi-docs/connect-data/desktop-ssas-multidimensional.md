---
title: Dados multidimensionais do Analysis Services no Power BI Desktop
description: Dados multidimensionais do SSAS (SQL Server Analysis Services) no Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/15/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: eac1134ff12025d05cd59e86b7538cde58e3a2ee
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83287684"
---
# <a name="connect-to-ssas-multidimensional-models-in-power-bi-desktop"></a>Conectar-se a modelos multidimensionais do SSAS no Power BI Desktop

Com o Power BI Desktop, você pode acessar *modelos multidimensionais do SSAS*, normalmente chamados de *SSAS MD*.

Para se conectar a um banco de dados do SSAS MD, selecione **Obter Dados**, escolha **Banco de Dados** > **Banco de dados do SQL Server Analysis Services** e selecione **Conectar**:

![Banco de dados do SSAS (SQL Server Analysis Services), caixa de diálogo Obter Dados, Power BI Desktop](media/desktop-ssas-multidimensional/ssas-multidimensional-2.png)

O serviço do Power BI e o Power BI Desktop são compatíveis com modelos multidimensionais do SSAS no modo de conexão dinâmico. Você pode publicar e carregar relatórios que usam **Modelos Multidimensionais SSAS** no modo dinâmico para o serviço do Power BI.

## <a name="capabilities-and-features-of-ssas-md"></a>Recursos e capacidades do SSAS MD

As seções a seguir descrevem os recursos e capacidades das conexões do Power BI e SSAS MD.

### <a name="tabular-metadata-of-multidimensional-models"></a>Metadados tabulares de modelos multidimensionais

A tabela a seguir mostra a correspondência entre objetos multidimensionais e os metadados tabulares que são retornados ao Power BI Desktop. O Power BI consulta metadados tabulares no modelo. Com base nos metadados retornados, o Power BI Desktop executa consultas DAX apropriadas no SSAS quando você cria uma visualização (como uma tabela, matriz, gráfico ou segmentação).

| Objeto multidimensional de BISM | Metadados tabulares |
| --- | --- |
| Cubo |Modelo |
| Dimensão do cubo |Tabela |
| Atributos de dimensão (chaves), nome |Colunas |
| Grupo de medidas |Tabela |
| Medida |Medida |
| Medidas sem grupo de medidas associado |Na tabela chamada *Medidas* |
| Grupo de medidas -> relação da dimensão do cubo |Relação |
| Perspectiva |Perspectiva |
| KPI |KPI |
| Hierarquias do usuário/pai-filho |Hierarquias |

### <a name="measures-measure-groups-and-kpis"></a>Medidas, grupos de medidas e KPIs

Os grupos de medidas em um cubo multidimensional são expostos como tabelas com o sinal ∑ (sigma) ao lado deles no painel **Campos**. As medidas calculadas sem um grupo de medidas associado são agrupadas em uma tabela especial chamada *Medidas* nos metadados tabulares.

Para ajudar a simplificar modelos complexos em um modelo multidimensional, você pode definir um conjunto de medidas ou KPIs em um cubo a ser localizado em uma *Pasta de exibição*. O Power BI reconhece as pastas de exibição nos metadados tabulares e mostra as medidas e KPIs dentro delas. Os KPIs em bancos de dados multidimensionais dão suporte a *Valor*, *Meta*, *Gráfico de Status* e *Gráfico de Tendência*.

### <a name="dimension-attribute-type"></a>Tipo de atributo de dimensão

Os modelos multidimensionais também dão suporte à associação de atributos de dimensão com tipos de atributo de dimensão específicos. Por exemplo, uma dimensão **Geografia** em que os atributos de dimensão *Cidade*, *Estado/Província*, *País* e *CEP* têm tipos de geografia apropriados associados a eles é exposta nos metadados tabulares. O Power BI reconhece os metadados, permitindo a criação de visualizações de mapa. Você reconhecerá essas associações pelo ícone de *mapa* ao lado do elemento no painel **Campo** no Power BI.

O Power BI também pode renderizar imagens quando você fornece um campo contendo as URLs (Uniform Resource Locators) das imagens. Você pode especificar esses campos como tipos *ImageURL* no SQL Server Data Tools (ou, em seguida, no Power BI). As informações de tipo são fornecidas ao Power BI nos metadados tabulares. O Power BI pode recuperar essas imagens da URL e exibi-las em visuais.

### <a name="parent-child-hierarchies"></a>Hierarquias pai-filho

Os modelos multidimensionais são compatíveis com hierarquias pai-filho, apresentadas como uma *hierarquia* nos metadados tabulares. Cada nível da hierarquia pai-filho é exposto como uma coluna oculta nos metadados tabulares. O atributo-chave da dimensão pai-filho não é exposto nos metadados tabulares.

### <a name="dimension-calculated-members"></a>Membros calculados da dimensão

Os modelos multidimensionais dão suporte à criação de vários tipos de *membros calculados*. Os dois tipos mais comuns de membros calculados são:

* Membros calculados em hierarquias de atributos que não são irmãos de *Todos*
* Membros calculados em hierarquias de usuário

Os modelos multidimensionais expõem *membros calculados em hierarquias de atributo* como valores de uma coluna. Você terá algumas opções e restrições adicionais se expuser este tipo de membro calculado:

* Um atributo de dimensão pode ter um *UnknownMember* opcional.

* Um atributo com membros calculados não pode ser o atributo-chave da dimensão, a menos que seja o único atributo da dimensão.

* Um atributo com membros calculados não pode ser um atributo pai-filho.

Os membros calculados de hierarquias de usuário não são expostos no Power BI. Em vez disso, você pode se conectar a um cubo que contém membros calculados em hierarquias de usuário. No entanto, você não poderá ver os membros calculados se eles não atenderem às restrições mencionadas na lista com marcadores anterior.

### <a name="security"></a>Segurança

Os modelos multidimensionais são compatíveis com a segurança no nível da dimensão e da célula por meio de *funções*. Quando você se conecta a um cubo com o Power BI, é autenticado e avaliado quanto às permissões apropriadas. Se um usuário tiver a *segurança de dimensão* aplicada, os respectivos membros da dimensão não serão vistos pelo usuário no Power BI. No entanto, quando um usuário tiver definido uma permissão de *segurança da célula*, em que determinadas células são restritas, esse usuário não poderá se conectar ao cubo usando o Power BI.

## <a name="considerations-and-limitations"></a>Considerações e limitações

Há algumas limitações no uso do SSAS MD:

* Somente as edições Enterprise e BI do SQL Server 2014 são compatíveis com conexões dinâmicas. Para a edição Standard do SQL Server, o SQL Server 2016 ou posterior é necessário para conexões dinâmicas.

* *Ações* e *conjuntos nomeados* não são expostos no Power BI. Para criar visuais e relatórios, você ainda pode se conectar a cubos que também contêm ações ou conjuntos nomeados.

* Quando Power BI exibe metadados para um modelo do SSAS, ocasionalmente você não pode recuperar dados do modelo. Esse cenário poderá ocorrer se você tiver instalado a versão de 32 bits do provedor MSOLAP, mas não a versão de 64 bits. Instalar a versão de 64 bits pode resolver o problema.

* Você não pode criar medidas no *nível do relatório* ao criar um relatório que esteja conectado em tempo real a um modelo multidimensional SSAS. As únicas medidas disponíveis são as definidas no modelo multidimensional.

## <a name="supported-features-of-ssas-md-in-power-bi-desktop"></a>Recursos compatíveis do SSAS MD no Power BI Desktop

O consumo dos elementos a seguir são compatíveis com esta versão do SSAS MD. Para saber mais sobre esses recursos, confira [Noções básicas sobre o Power View para modelos multidimensionais](/sql/analysis-services/multidimensional-models/understanding-power-view-for-multidimensional-models?view=sql-server-2014).

* Membros padrão
* Atributos de dimensão
* Tipos de atributo de dimensão
* Membros calculados da dimensão, que:
  * deverão ser um membro real quando a dimensão tiver mais de um atributo;
  * não podem ser o atributo-chave da dimensão, a menos que sejam o único atributo; e
  * não podem ser um atributo pai-filho.
* Segurança da dimensão
* Exibir pastas
* Hierarquias
* ImageUrls
* KPIs
* tendências de KPI
* Medidas (com ou sem grupos de medidas)
* Medidas como variantes

## <a name="troubleshooting"></a>Solução de problemas

A lista a seguir descreve todos os problemas conhecidos de conexão com o SSAS (SQL Server Analysis Services).

* **Erro: Não foi possível carregar o esquema de modelo** – esse erro normalmente ocorre quando o usuário que se conecta ao Analysis Services não tem acesso ao banco de dados/cubo.
