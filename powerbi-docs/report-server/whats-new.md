---
title: Novidades no Servidor de Relatório do Power BI
description: Saiba quais são as novidades no Servidor de Relatório do Power BI. Este artigo aborda as principais áreas de recursos e é atualizado conforme novos itens são lançados.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 02/27/2020
ms.openlocfilehash: 3ce1ae5207af6f4aaf844679bcd3ae52d2c13819
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83348150"
---
# <a name="whats-new-in-power-bi-report-server"></a>Novidades no Servidor de Relatório do Power BI

Saiba mais sobre as novidades do Servidor de Relatórios do Power BI e do Power BI Desktop otimizado para o Servidor de Relatórios do Power BI. Este artigo aborda as principais áreas de recursos e é atualizado a cada novo lançamento.

Baixe o [Servidor de Relatórios do Power BI e o Power BI Desktop otimizado para o Servidor de Relatórios do Power BI](https://powerbi.microsoft.com/report-server/).

Para saber mais sobre as “Novidades” do Power BI, consulte:

* [Novidades no serviço do Power BI](../fundamentals/service-whats-new.md)
* [Novidades no Power BI Desktop](../fundamentals/desktop-latest-update.md)
* [Novidades em aplicativos móveis para o Power BI](../consumer/mobile/mobile-whats-new-in-the-mobile-apps.md)

## <a name="january-2020"></a>Janeiro de 2020

Confira a postagem no blog de janeiro de 2020 sobre o Servidor de Relatórios do Power BI para obter mais detalhes.

### <a name="power-bi-desktop-optimized-for-power-bi-report-server"></a>Power BI Desktop otimizado para o Servidor de Relatórios do Power BI

Esta versão traz muitos recursos novos, como formatação condicional para botões, aprimoramentos de criação de perfil de dados e mais configurações de formatação para KPIs e visuais de tabela. Veja a seguir uma lista resumida de atualizações:

**Relatórios**

- Definição de um valor de matriz ou de coluna da tabela como uma URL personalizada
- Configurações de formatação de visual do KPI
- Atualizações na experiência do painel de filtro

**Análise**

- Formatação condicional de botões
- Maior carregamento de insights do recurso Analisar
- Nova função DAX: Trimestre

**Preparação de dados**

- Melhorias na criação de perfil de dados

**Outros**

- Novo formato de arquivo: .pbids
- Melhorias de desempenho das operações de modelagem

**Relatórios**

*Definir um valor de matriz ou de coluna da tabela como uma URL personalizada*

Você pode definir um valor de matriz ou de coluna da tabela como uma URL personalizada. Você encontra essa nova opção no cartão de formatação condicional, no painel de formatação.

*Configurações de formatação de visual do KPI*

A versão deste mês tem KPIs com novas opções de formatação:

- Formatação de texto do indicador (família de fontes, cor e alinhamento)
- Transparência do eixo de tendência
- Formatação de texto de meta e distância (texto do rótulo, família de fontes, cor e tamanho)
- Formatação de distância de texto (texto do rótulo, direção positiva, família de fontes, cor e tamanho)
- Adição de rótulo de data com formatação (família de fontes, cor e tamanho)

Você pode formatar condicionalmente algumas destas novas opções:

- Cor da fonte do indicador
- Cor da fonte da meta e cor da fonte de distância da meta
- As cores de status bom/ruim/neutro
- Cor da fonte de data

*Atualizações na experiência do painel de filtro*

Como parte da disponibilidade geral da nova experiência de filtro da [última versão](https://powerbi.microsoft.com/blog/power-bi-report-server-september-2019-feature-summary/#filterPane), simplificamos o processo de transição dos relatórios atuais para o novo painel. Ao abrir o Servidor de Relatórios do Power BI pela primeira vez, você verá uma caixa de diálogo de atualização automática do painel de filtro. Essas atualizações também incluem os banners no Servidor de Relatórios quando os relatórios precisam ser migrados para a nova experiência.

**Análise**

*Formatação condicional para botões*

Essas atualizações de formatação condicional estão relacionadas aos botões. Agora você pode definir dinamicamente a formatação para as seguintes propriedades:

- Cor da fonte do texto do botão
- Texto do botão
- Cor da linha do ícone
- Cor do contorno
- Cor de Preenchimento
- Dica de ferramenta de botão (no cartão de ação)

*Maior carregamento de insights do recurso Analisar*

Quando você executa o recurso Analisar para encontrar insights em seus dados, por exemplo, para Explicar um aumento, acionamos os modelos de machine learning somente por um período definido para mostrar insights em tempo hábil. Agora, quando você tiver muitos dados para analisar, será possível continuar executando a análise após o tempo limite inicial.

*Nova função DAX: Quarter*

Este mês, temos uma nova função DAX, a Quarter. A função Quarter retorna o trimestre correspondente a uma data especificada.

**Preparação de dados**

*Melhorias na criação de perfil de dados*

Este mês, estamos introduzindo algumas melhorias significativas em nossos recursos de criação de perfil de dados no Editor do Power Query, incluindo:

- Várias opções de agrupamento para o visual de distribuição de valor do painel de Perfil da Coluna, específicas por tipo de coluna, além dos critérios "Por Valor" existentes.
- Texto: Por comprimento do texto (número de caracteres).
- Número: Por sinal (positivo/negativo) e Paridade (par/ímpar).
- Data/Datetime: Por ano, mês, dia, semana do ano, dia da semana, período do dia (AM/PM) e hora do dia.
- E mais outros tipos de dados, como de Lógica Verdadeiro/Falso.

*Opções de filtro*

Você já pode aproveitar vários critérios de agrupamento específicos de tipo no painel de distribuição dos Perfis de Colunas. Agora, você também pode aplicar filtros dentro de textos explicativos para cada um dos valores no gráfico de distribuição quando critérios de agrupamento são aplicados. Por exemplo, no painel Perfis de Dados de uma coluna Data/Datetime, você pode excluir todos os valores que se enquadram em determinado mês.

**Outros**

*Novo formato de arquivo: .pbids*

Este mês, estamos lançando um novo formato de arquivo: .pbids, para otimizar a experiência da opção "Obter Dados" para criadores de relatórios em sua organização. Recomendamos que os administradores criem esses arquivos para as conexões mais usadas.

Quando um criador de relatório abre um arquivo .pbids, o Power BI Desktop solicita autenticação para conectar-se à fonte de dados especificada no arquivo. Em seguida, o usuário seleciona as tabelas a serem carregadas no modelo. Também pode ser necessário selecionar o banco de dados, caso isso ainda não tenha sido especificado no arquivo. A partir daí, o criador do relatório pode começar a criar visualizações.

Encontre detalhes e exemplos na seção [Usar arquivos .pbids para obter dados](../connect-data/desktop-data-sources.md#using-pbids-files-to-get-data) do artigo "Fontes de dados no Power BI Desktop".

*Melhorias de desempenho das operações de modelagem*

Fizemos uma melhoria de desempenho no mecanismo do Analysis Services para acelerar as operações de modelagem, como a adição de medidas ou colunas calculadas e a criação de relacionamentos. A quantidade de aprimoramento que você vê depende do modelo, mas percebemos que alguns clientes tiveram um desempenho 20x mais rápido em ações como abertura de arquivos e adição de medidas.

Essas são as novidades da versão de janeiro de 2020 do Servidor de Relatórios do Power BI. Continue enviando comentários e não se esqueça de [votar nos recursos que você gostaria de ver no Power BI](https://ideas.powerbi.com/forums/265200-power-bi).

### <a name="power-bi-report-server"></a>Servidor de Relatórios do Power BI

#### <a name="export-to-excel-from-power-bi-reports"></a>Exportar relatórios do Power BI para o Excel

A exportação de um relatório do Power BI com o Servidor de Relatórios do Power BI para o Excel agora funciona da mesma maneira que exportar um relatório do Power BI para o Excel no serviço do Power BI. Você pode exportar diretamente para o formato .xlsx do Excel, e o limite de exportação é de 150 mil linhas.

#### <a name="azure-sql-managed-instance-support"></a>Suporte às instâncias gerenciadas do Azure SQL

Agora você pode hospedar um catálogo de banco de dados usado no Servidor de Relatórios do Power BI em uma MI (Instância Gerenciada) do Banco de Dados SQL do Azure hospedada em uma máquina virtual ou em seu data center. O suporte é limitado ao uso de credenciais de banco de dados para a conexão com a MI do SQL.

#### <a name="power-bi-premium-dataset-support"></a>Suporte ao conjunto de dados do Power BI Premium

Você pode se conectar aos conjuntos de dados do Power BI usando o Construtor de Relatórios da Microsoft ou o SSDT (SQL Server Data Tools). Em seguida, pode publicar esses relatórios no Servidor de Relatórios do Power BI usando a conectividade do SQL Server Analysis Services. Para ativar o cenário, os usuários precisam usar um nome de usuário e senha armazenados do Windows.

#### <a name="alttext-alternative-text-support-for-report-elements"></a>Suporte a Text Alt (texto alternativo) para elementos de relatório

Ao criar relatórios, você pode usar dicas de ferramentas para especificar o texto de cada elemento no relatório. As tecnologias de leitura de tela usarão essas dicas de ferramentas.

#### <a name="azure-active-directory-application-proxy-support"></a>Suporte de Proxy de Aplicativo do Azure Active Directory

Com o Proxy de Aplicativo do Azure Active Directory, você não precisa mais gerenciar seu próprio proxy de aplicativo Web para permitir acesso seguro via aplicativos móveis ou da Web. Confira [Acesso remoto a aplicativos locais por meio do Proxy de Aplicativo do Azure Active Directory](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy) para obter mais informações.

#### <a name="custom-headers"></a>Cabeçalhos personalizados

Define os valores do cabeçalho para todas as URLs que correspondem ao padrão de regex especificado. Os usuários podem atualizar o valor do cabeçalho personalizado com XML válido para definir os valores do cabeçalho para as URLs de solicitação selecionadas. Os administradores podem adicionar qualquer número de cabeçalhos no XML. Confira [CustomHeaders](/sql/reporting-services/tools/server-properties-advanced-page-reporting-services#customheaders) no artigo **Página avançada de propriedades do servidor** do Reporting Services para obter detalhes.

#### <a name="transparent-database-encryption"></a>Transparent Data Encryption

O Servidor de Relatórios do Power BI agora dá suporte ao recurso de Transparent Data Encryption para o banco de dados de catálogo das edições Enterprise e Standard do Servidor de Relatórios do Power BI.

#### <a name="power-bi-visuals-api"></a>API de visuais do Power BI

A versão da API fornecida com esta versão é a 2.6.

#### <a name="microsoft-report-builder-update"></a>Atualização do Construtor de Relatórios da Microsoft

A versão recém-lançada do Construtor de Relatórios é totalmente compatível com as versões 2016, 2017 e 2019 do Reporting Services. Também é compatível com todas as versões lançadas e compatíveis do Servidor de Relatórios do Power BI.

## <a name="september-2019"></a>Setembro de 2019

Consulte a postagem no blog [Servidor de Relatórios do Power BI Setembro de 2019](https://powerbi.microsoft.com/blog/power-bi-report-server-september-2019-feature-summary/) para obter detalhes sobre todos os novos recursos.

A atualização de Setembro de 2019 do Servidor de Relatórios do Power BI está repleta de novos recursos de relatório do Power BI. Estes são alguns dos destaques:

- **Filtros no nível do visual para segmentações** Você pode adicionar um filtro no nível do visual às segmentações. Ele funciona como todos os outros filtros no nível do visual, filtrando apenas a segmentação em si e nenhum outro visual. Esse filtro é útil para filtrar espaços em branco ou quando você quer usar filtros de medidas.
- **Conjuntos de ícones para tabelas e matrizes** Com os ícones de KPI, você pode configurar regras para mostrar diferentes conjuntos de ícones em sua tabela e matriz, de forma semelhante aos conjuntos de ícones do Excel.
- **Agrupamento de visuais** Agora, você pode agrupar visuais, formas, caixas de texto, imagens e botões em uma página de relatório, assim como ocorre no PowerPoint. Ao agrupar os objetos, você pode movê-los e redimensioná-los juntos. O agrupamento facilita o trabalho em um relatório com muitos objetos dispostos em camadas em cada página.
- **Novos temas padrão** Para acompanhar as novas opções JSON de temas, estamos atualizando os temas disponíveis para os relatórios e alterando o tema padrão para novos relatórios. O novo tema padrão se alinha melhor com a linguagem de design da Microsoft e segue as melhores práticas de design para visuais. 
- **Design do painel atualizado** Atualizamos grande parte de nossa interface. Atualizamos todos os painéis, o rodapé e o seletor de exibição com uma cor mais clara, um espaçamento atualizado e introduzimos novos ícones. O novo design é a primeira etapa para atualizar a interface inteira.

Aqui está a lista completa de recursos. 

### <a name="reporting"></a>Relatórios

- Design do painel atualizado
- Filtros no nível do visual para segmentações
- Classificação para o painel do analisador de desempenho
- Dicas de ferramenta no cabeçalho do visual
- Personalização de rótulo do total de tabela e da matriz
- Suporte para sincronização da segmentação de hierarquia
- Tamanhos de fonte uniformes entre visuais
- Conjuntos de ícones para tabela e matriz
- Suporte percentual para formatação condicional por regras
- O novo painel de filtro agora está em disponibilidade geral
- Suporte a cores de dados ao usar o eixo de reprodução em gráficos de dispersão
- Melhorias de desempenho ao usar a data relativa e segmentações suspensas
- Agrupamento de visuais
- Classes de cor e texto em temas
- Novos temas padrão

### <a name="analytics"></a>Análise

- Cadeias de formato personalizadas
- Atualizações de formatação condicional para opções de formatação

    - Cores de segundo plano e do título dos visuais
    - Cores do cartão
    - Cores e preenchimento do medidor
    - Texto alternativo
    - Cor da borda

- Avisos de formatação condicional
- Melhoria de detectabilidade de detalhamento
- Novas expressões DAX: REMOVEFILTERS e CONVERT
- Novo operador de comparação DAX: ==

### <a name="data-preparation"></a>Preparação de dados

- Melhorias no IntelliSense M
- Nova transformação: Dividir coluna por posições
- Copiar para a área de transferência da criação de perfil de dados


## <a name="may-2019"></a>Maio de 2019

### <a name="power-bi-desktop-for-power-bi-report-server"></a>Power BI Desktop para o Servidor de Relatórios do Power BI

Confira a postagem no blog [Servidor de Relatórios do Power BI Maio de 2019](https://powerbi.microsoft.com/blog/power-bi-report-server-update-may-2019/) para obter detalhes sobre todos os novos recursos.

Estes são alguns dos destaques da versão:

#### <a name="performance-analyzer"></a>Performance analyzer 

Se o relatório for executado mais lentamente do que o esperado, experimente o Performance Analyzer no Power BI Desktop. Quando é iniciado, ele cria um arquivo de log com informações sobre cada ação executada no relatório. Saiba mais sobre o [Performance Analyzer](../create-reports/desktop-performance-analyzer.md).

#### <a name="new-modeling-view"></a>Nova exibição de modelagem

Na nova exibição de Modelagem no Power BI Desktop, você pode exibir e trabalhar com conjuntos de dados complexos que contêm muitas tabelas. Os destaques incluem vários layouts de diagrama e edição em massa de colunas, medidas e tabelas. Leia mais sobre a [exibição de Modelagem](../transform-model/desktop-modeling-view.md).

#### <a name="accessible-visual-interaction"></a>Interação visual acessível

Agora, você pode acessar pontos de dados em muitos dos visuais internos usando a navegação por teclado. Saiba mais sobre [acessibilidade nos relatórios do Power BI](../desktop-accessibility.md).

#### <a name="conditional-formatting-titles-and-web-url-actions"></a>Títulos de formatação condicional e ações de URL da Web

Os relatórios do Power BI são interativos. Faz sentido que os títulos de um relatório sejam dinâmicos, de forma a refletir o estado atual do relatório. Você pode usar a mesma formatação associada à expressão para tornar as URLs de seus botões, formas e imagens dinâmicas. Leia mais sobre [títulos baseados em expressões](../create-reports/desktop-conditional-format-visual-titles.md).

#### <a name="cross-highlight-by-axis-labels"></a>Realce cruzado por rótulos de eixo

Selecione os rótulos de categoria do eixo em um visual para realçar de maneira cruzada os outros elementos em uma página, assim como você selecionaria os pontos de dados de um visual. Saiba mais sobre o [realce cruzado](../create-reports/power-bi-reports-filters-and-highlighting.md#ad-hoc-highlighting).

#### <a name="all-the-new-features"></a>Todos os novos recursos

Aqui está a lista de todos os novos recursos:

#### <a name="reporting"></a>Relatórios

- Realce cruzado em um único ponto em gráficos de linhas 
- Quebra automática de linha em títulos 
- Atualização da interação padrão de visual com a filtragem cruzada
- Cantos arredondados para bordas de visuais 
- Segmentação com seleção única  
- Suporte para mapa de calor para os mapas do Bing  
- Realce cruzado por rótulos de eixo  
- Formatação de dica de ferramenta padrão  
- Suporte de URL da Web estático para botões, formas e imagens  
- Opções de alinhamento da página   
- Aprimoramentos do painel de seleção  
- Interação visual acessível  
- Formatação condicional para títulos de visuais  
- Formatação condicional para ações de URL da Web para botões, imagens e formas
- Painel do Performance Analyzer
- Navegação por teclado em matrizes e tabelas
- Controle de posição do rótulo de dados de linha
- Controle de tamanho de texto de indicador visual de KPI

#### <a name="analytics"></a>Análise

- A exibição de datas como hierarquia já está em disponibilidade geral  

#### <a name="modeling"></a>Modelagem

- O novo modo de exibição de modelagem já está em disponibilidade geral
- Novas funções do DAX
- Atualização a função ALLSELECTED DAX
- Desabilitar tabelas de atualização automática para novos relatórios

### <a name="power-bi-report-server"></a>Servidor de Relatórios do Power BI

#### <a name="support-for-trusted-visuals"></a>Suporte para visuais confiáveis

Adicionamos suporte para Visuais Confiáveis para o Servidor de Relatórios do Power BI. Atualmente, damos suporte a visuais do Mapbox e do PowerOn. Não há suporte para ESRI, Visio e PowerApps nesta versão.

#### <a name="improved-security-features"></a>Recursos de segurança aprimorados

**RestrictedResourceMimeTypeForUpload**, que os administradores podem usar para especificar uma lista separada por vírgulas de tipos MIME banidos, por exemplo, text/html.

## <a name="january-2019"></a>Janeiro de 2019

Suporte para esses recursos em relatórios do Power BI:

[**Segurança em nível de linha**](row-level-security-report-server.md) Configurar a RLS (Segurança em Nível de Linha) com o Servidor de Relatórios do Microsoft Power BI pode restringir acesso a dados para determinados usuários. Os filtros restringem o acesso a dados no nível da linha e você pode definir filtros nas funções.

[**Expandir e recolher os cabeçalhos de linha de matriz**](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2018-feature-summary/#expandCollapse) Adicionamos a capacidade de expandir e recolher cabeçalhos de linha individuais, um dos recursos visuais mais solicitados.

[**Copiar e colar entre arquivos .pbix**](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2018-feature-summary/#copyPaste) Você pode copiar os elementos visuais entre arquivos .pbix, no menu de contexto do visual ou com o atalho de teclado Ctrl + C padrão e colá-los em outro relatório com Ctrl + V.

[**Guias de alinhamento inteligentes**](https://powerbi.microsoft.com/blog/power-bi-desktop-december-2018-feature-summary/#smartGuides) Você vê guias de alinhamento inteligentes ao mover objetos na sua página de relatório, assim como você vê no PowerPoint, para ajudá-lo a alinhar tudo na sua página. Você vê as guias inteligentes sempre que arrasta ou redimensiona algo na página. Quando você move um objeto para perto de outro, ele se ajusta em uma posição alinhada com o outro objeto.

**Recursos de acessibilidade** Há muitos recursos de acessibilidade para listar: por exemplo, [suporte de acessibilidade do painel de lista de campos](https://powerbi.microsoft.com/blog/power-bi-desktop-december-2018-feature-summary/#fieldList). O painel de lista de campos é totalmente acessível. Você pode navegar pelo painel usando apenas o teclado e um leitor de tela e usar o menu de contexto para adicionar campos à sua página de relatório.

#### <a name="power-bi-visuals"></a>Visuais do Power BI

- A versão da API fornecida com esta versão é a 2.3.

### <a name="administrator-settings"></a>Configurações do administrador

Os administradores podem definir as seguintes propriedades nas Propriedades Avançadas do SSMS para o farm de servidores:

**AllowedResourceExtensionsForUpload** Definir extensões de recursos que podem ser carregados para o servidor de relatório. Extensões para tipos de arquivo internos, como &ast;.rdl e &ast;.pbix não devem ser incluídos. O padrão é "&ast;, &ast;.xml, &ast;.xsd, &ast;.xsl, &ast;.png, &ast;.gif, &ast;.jpg, &ast;.tif, &ast;.jpeg, &ast;.tiff, &ast;.bmp, &ast;.pdf, &ast;.svg, &ast;.rtf, &ast;.txt, &ast;.doc, &ast;.docx, &ast;.pps, &ast;.ppt, &ast;.pptx". 

**SupportedHyperlinkSchemes** Define uma lista separada por vírgulas dos esquemas de URI que têm permissão para serem definidos em ações de hiperlink que têm permissão para serem processados ou então "&ast;" para habilitar todos os esquemas de hiperlink. Por exemplo, definir "http,https" permitiria hiperlinks para "https://www. contoso.com", mas removeria hiperlinks para "mailto:bill@contoso.com" ou "javascript:window.open(‘ www.contoso.com’, ‘_blank’)". O padrão é "&ast;".

## <a name="august-2018"></a>Agosto de 2018

Em agosto de 2018, vários novos recursos foram adicionados à versão do Power BI Desktop otimizada para o Servidor de Relatórios do Power BI. Aqui estão elas, divididas por área:

- [Relatórios](#reporting)
- [Análise](#analytics)
- [Modelagem](#modeling)

### <a name="highlights-of-the-august-2018-release"></a>Destaques da versão de agosto de 2018

De toda a longa lista de novos recursos, estes se destacam por serem mais interessantes. Para obter mais informações, confira nossa [postagem no blog](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/).

#### <a name="report-theming"></a>Tema do relatório

O tema do relatório foi adicionado à versão de agosto de 2018 do Servidor de Relatórios do Power BI, que permite colorir rapidamente o relatório inteiro para corresponder a um tema ou à identidade visual da empresa. Quando você importa um tema, todos os gráficos são atualizados automaticamente para usar as cores do tema e você pode ter acesso às cores do tema na paleta de cores. Você pode carregar um arquivo de tema usando a opção **Importar Tema** no botão **Mudar Tema**.

Um arquivo de tema é um arquivo JSON que inclui todas as cores que você deseja usar em seu relatório, juntamente com qualquer formatação padrão que deseja aplicar aos visuais.
Aqui está um exemplo simples de tema JSON que apenas atualiza as cores padrão do relatório:

```json
{
"name": "waveform",
"dataColors": [ "#31B6FD", "#4584D3", "#5BD078", "#A5D028", "#F5C040", "#05E0DB", "#3153FD", "#4C45D3", "#5BD0B0", "#54D028", "#D0F540", "#057BE0" ],
"background":"#FFFFFF",
"foreground": "#F2F2F2",
"tableAccent":"#5BD078"
}
```

#### <a name="conditional-formatting-by-a-different-field"></a>Formatação condicional usando um campo diferente

A capacidade de formatar uma coluna usando um campo diferente em seu modelo é uma das melhorias significativas da formatação condicional.

#### <a name="conditional-formatting-by-values"></a>Formatação condicional usando valores

Outro tipo novo de formatação condicional é o valor **Formatar por campo**. O valor Formatar por campo permite usar uma medida ou coluna que especifica uma cor, por meio de um código hexadecimal ou um nome, e aplica essa cor à cor da tela de fundo ou da fonte.

#### <a name="report-page-tooltips"></a>Dicas de ferramentas de página de relatório

O recurso de dicas de ferramenta da página de relatório foi incluído na atualização de agosto de 2018 do Servidor de Relatórios do Power BI. Esse recurso permite criar uma página de relatório a ser usada como uma dica de ferramenta personalizada para outros visuais no relatório.

#### <a name="log-axis-improvements"></a>Melhorias do eixo logarítmico

Melhoramos consideravelmente o eixo logarítmico em seus gráficos cartesianos. Agora, você pode selecionar a escala logarítmica do eixo numérico de qualquer gráfico cartesiano, incluindo o gráfico de combinação, quando houver dados completamente positivos ou completamente negativos.

#### <a name="sap-hana-sso-direct-query"></a>DirectQuery de SSO do SAP HANA

O suporte para DirectQuery de SSO do SAP HANA com o Kerberos já está disponível para relatórios do Power BI.

>[!Note]
>Há suporte para esse cenário apenas quando o SAP HANA é tratado como uma fonte de dados relacional com os relatórios que você criou no Power BI Desktop.  Para habilitar isso no Power BI Desktop, no menu do DirectQuery, em Opções, marque "Tratar SAP HANA como uma fonte relacional" e clique em OK.

#### <a name="power-bi-visuals"></a>Visuais do Power BI

- A versão da API fornecida com esta versão é a 1.13.0.

- Agora, os visuais do Power BI podem voltar a uma versão anterior compatível com a versão atual da API do servidor (se disponível).

### <a name="reporting"></a>Relatórios 

- [Tema do relatório](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#theming)
- [Botões para disparar ações](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#buttons)
- [Estilos de linha do gráfico de combinação](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#comboLines)
- [Melhor classificação padrão para visuais](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#sort)
- [Segmentação numérica](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#numericSlicer)
- [Sincronizando de segmentação avançada](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#slicerSync)
- [Melhorias do eixo logarítmico](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#logAxis)
- [Opções de rótulo de dados para gráfico de funil](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#funnelChart)
- [Definir a largura do traço da linha para zero](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#lineStroke)
- [Suporte para alto contraste em relatórios](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#highContrast)
- [Controle de raio de rosca](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#donutRadius)
- [Controle de posição de rótulos de detalhe de pizza e rosca](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#detailLabels)
- [Formatar rótulos de dados separadamente para cada medida em um gráfico de combinação](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#comboLabels)
- [Novo cabeçalho visual com mais flexibilidade e formatação](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#visualHeader)
- [Formatação de papel de parede](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#wallpaper)
- [Dicas de ferramentas de tabela e de matriz](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#tableTooltips)
- [Desativar dicas de ferramentas para visuais](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#tooltips)
- [Acessibilidade de segmentação](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#slicerAccessibility)
- [Melhorias do painel de formatação](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#formattingPane)
- [Suporte para linha de nível em gráficos de linhas e de combinação](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#steppedLine)
- [Melhoria da experiência de classificação](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#sorting)
- [Imprimir relatórios por meio da Exportação para PDF (no Power BI Desktop)](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#print)
- [Criar grupos de indicadores](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#bookmarks)
- [Redefinição de segmentação](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#slicer)
- [Dicas de ferramenta da página de relatório](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#reportPageTooltips)

### <a name="analytics"></a>Análise

- [Nova função DAX: COMBINEVALUES()](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#combineValues)
- [Detalhamento de medida](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#measureDrillthrough)
- [Formatação condicional usando um campo diferente](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#conditionalFormattingField)
- [Formatação condicional usando valores](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#conditionalFormattingValue)

### <a name="modeling"></a>Modelagem

- [Filtragem e classificação na exibição de dados](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#filterAndSort)
- [Melhoria na formatação de localidade](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#locale)
- [Categorias de dados para medidas](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#dataCategory)
- [Funções estatísticas do DAX](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#dax)

## <a name="may-2018"></a>Mai 2018

### <a name="configure-power-bi-ios-mobile-apps-for-report-servers-remotely"></a>Configurar aplicativos móveis do Power BI iOS para servidores de relatório remotamente

Como um administrador de TI, agora é possível usar ferramenta MDM da sua organização para configurar remotamente o acesso de aplicativo móvel do Power BI iOS a um servidor de relatório. Confira [Configurar o acesso do aplicativo móvel do Power BI iOS a um servidor de relatório remotamente](configure-powerbi-mobile-apps-remote.md) para obter detalhes.

## <a name="march-2018"></a>Março de 2018

Em março de 2018, houve a adição de muitos recursos novos à versão do Power BI Desktop otimizado para o Servidor de Relatórios do Power BI. Aqui estão elas, divididas por área:

- [Visuais](#visuals-updates)
- [Relatórios](#reporting)
- [Análise](#analytics)
- [Desempenho](#performance)
- [Servidor de relatórios](#report-server)
- [Outros](#other-improvements)

### <a name="highlights-of-the-march-2018-release"></a>Destaques da versão de março de 2018

De toda a longa lista de novos recursos, estes se destacam por serem mais interessantes.

#### <a name="rule-based-conditional-formatting-for-table-and-matrix"></a>[Formatação condicional baseada em regras para visuais de tabela e de matriz](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#conditionalFormatting)

Crie regras para colorir condicionalmente a tela de fundo ou a fonte de uma coluna com base na lógica de negócios específica na tabela ou na matriz.

#### <a name="show-and-hide-pages"></a>[Mostrar e ocultar páginas](https://powerbi.microsoft.com/blog/power-bi-desktop-january-2018-feature-summary/#hidePages)

Você deseja que os leitores acessem seu relatório, mas algumas páginas não estão concluídas. Agora você pode ocultá-las até que elas fiquem prontas. Ou você pode ocultar páginas da navegação normal, permitindo que os leitores cheguem à página por indicadores ou por detalhamento.

#### <a name="bookmarking"></a>[Uso de indicadores](https://powerbi.microsoft.com/blog/power-bi-desktop-march-2018-feature-summary/#bookmarking)

Falando de uso de indicadores, crie-os para contar uma história com os dados em seu relatório.

- [Realce cruzado para indicadores](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#bookmarkCrossHighlighting): indicadores mantêm e exibem o estado com realce cruzado da página do relatório no momento em que são criados.
- [Mais flexibilidade para indicadores](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#bookmarkFlexibility): indicadores refletem as propriedades que você define no relatório e afeta somente os visuais que você escolhe.

#### <a name="multi-select-data-points-across-multiple-charts"></a>[Pontos de dados de seleção múltipla em vários gráficos](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#crosshighlight)

Selecione vários pontos de dados em vários gráficos e aplique a filtragem cruzada a toda a página.

#### <a name="sync-slicers-across-multiple-pages-of-your-report"></a>[Sincronizar segmentações de dados em várias páginas do relatório](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#syncSlicers)

Uma segmentação de dados pode se aplicar a uma, duas ou mais páginas em um relatório.

#### <a name="quick-measures"></a>[Medidas rápidas](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#quickMeasures) 

Crie medidas com base em medidas existentes e nas colunas numéricas em uma tabela.

#### <a name="drilling-down-filters-other-visuals"></a>[Filtros de detalhamento de outros elementos visuais](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#drillFiltersOtherVisuals)

Quando você faz drill down em uma determinada categoria em um visual, você pode filtrar todos os elementos visuais na página por essa mesma categoria.

### <a name="visuals-updates"></a>Atualizações de visuais

- [Alinhamento de células para visuais de tabela e de matriz](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#alignment)
- [Ver unidades e controle de precisão para colunas de tabela e de matriz](https://powerbi.microsoft.com/blog/power-bi-desktop-march-2018-feature-summary/#displayUnits)
- [Rótulos de dados de estouro para elementos visuais de gráfico de barras e colunas](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#overflow)
- [Controlar a cor da tela de fundo do rótulo de dados para Cartesiano e visuais de mapas](https://powerbi.microsoft.com/blog/power-bi-desktop-january-2018-feature-summary/#dataLabelBackground)
- [Controle de preenchimento de barra/coluna](https://powerbi.microsoft.com/blog/power-bi-desktop-january-2018-feature-summary/#padding)
- [Aumentar a área usada para rótulos de eixo em gráficos](https://powerbi.microsoft.com/blog/power-bi-desktop-january-2018-feature-summary/#axisSize)
- [Dispersão visual de agrupamentos do eixo x e y](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#scatterChart)
- [Amostragem de alta densidade para mapas com base em latitude e longitude](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#highDensityMaps)
- [Segmentações responsivas](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#responsive)
- [Adicionar uma data de âncora para segmentação de data relativa](https://powerbi.microsoft.com/blog/power-bi-desktop-january-2018-feature-summary/#anchorDate)

### <a name="reporting"></a>Relatórios

- [Desativar o cabeçalho do visual no modo de leitura em um relatório](https://powerbi.microsoft.com/blog/power-bi-desktop-march-2018-feature-summary/#visualHeader)
- [Opções de relatório para fontes de dados lentas](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#slowDataSource)
- [Posicionamento de visual padrão aprimorado](https://powerbi.microsoft.com/blog/power-bi-desktop-march-2018-feature-summary/#visualPlacement)
- [Controle a ordem visual por meio do painel de seleção](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#selectionPane)
- [Bloqueie objetos no relatório](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#lock)
- [Pesquisar o painel de formatação e análise](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#search)
- [Painel de propriedades de campo e descrições de campo](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#fieldPropertiesPane)

### <a name="analytics"></a>Análise

- [UTCNOW() e UTCTODAY()](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#utcDAX)
- [Marcar tabela de datas personalizada](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#customDateTable)
- [Detalhar filtros de outros visuais](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#drillFiltersOtherVisuals)
- [Formatação de nível de célula para modelos multidimensionais do AS para cartão de múltiplas linhas](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#cellLevelFormatting)

### <a name="performance"></a>Desempenho

- [Melhorias de desempenho de filtragem](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#filtering)
- [Melhorias de desempenho DirectQuery](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#dqPerf)
- [Melhorias de desempenho de abrir e salvar](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#savePerf)
- [Melhorias de “Mostrar itens sem dados”](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#showItemsWithNoData)

### <a name="report-server"></a>Servidor de relatórios

#### <a name="export-to-accessible-pdf"></a>Exportar para PDF acessível

Quando você exporta um relatório paginado (RDL) para PDF, você pode obter um arquivo PDF acessível/marcado. Ele é maior em tamanho, mas sua leitura e navegação pelos leitores de tela e outras tecnologias assistenciais é mais fácil. Você habilita o PDF acessível definindo a configuração de informações de dispositivo **AccessiblePDF** para **True**. Consulte [Configuração de Informações de Dispositivo PDF](https://docs.microsoft.com/sql/reporting-services/pdf-device-information-settings) e [Alterar as Configurações de Informações do Dispositivo](https://docs.microsoft.com/sql/reporting-services/customize-rendering-extension-parameters-in-rsreportserver-config#changing-device-information-settings).

### <a name="other-improvements"></a>Outros aprimoramentos

- [Aprimoramentos em Adicionar Coluna de Exemplos](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#addColumnFromExamples)
- [Link rápido para Serviços de Consultoria](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#consultingServices)
- [Relatório de erros aprimorado](https://powerbi.microsoft.com/blog/power-bi-desktop-march-2018-feature-summary/#errors)
- [Ver erros anteriores que você encontrou](https://powerbi.microsoft.com/blog/power-bi-desktop-march-2018-feature-summary/#viewErrors)

## <a name="october-2017"></a>Outubro de 2017

### <a name="power-bi-report-data-sources"></a>Fontes de dados de relatório do Power BI

Os relatórios do Power BI no Servidor de Relatórios do Power BI podem conectar-se a uma variedade de fontes de dados. É possível importar e agendar a atualização de dados ou consultá-los diretamente usando o DirectQuery ou uma conexão dinâmica ao SQL Server Analysis Services. Veja a lista das fontes de dados compatíveis com a atualização agendada e as compatíveis com o DirectQuery em "Fontes de dados de relatórios do Power BI no Servidor de Relatórios do Power BI".

### <a name="scheduled-data-refresh-for-imported-data"></a>Atualização agendada de dados importados

No Servidor de Relatórios do Power BI, é possível configurar a atualização de dados agendada para manter os dados atualizados nos relatórios do Power BI usando um modelo inserido, em vez de uma conexão dinâmica ou o DirectQuery. Com um modelo inserido, os dados importados são desconectados da fonte de dados original. Eles precisam ser atualizados para permanecerem em sua versão mais recente e a atualização agendada é a maneira de fazer isso. Leia mais sobre a "atualização agendada dos relatórios do Power BI no Servidor de Relatórios do Power BI".

### <a name="editing-power-bi-reports-from-the-server"></a>Editando relatórios do Power BI no servidor

É possível abrir e editar os arquivos de relatório do Power BI (.pbix) no servidor, mas você retorna o arquivo original carregado. **Se os dados tiverem sido atualizados pelo servidor, eles não estarão atualizados quando você abrir o arquivo pela primeira vez**. Para ver a alteração, você precisará atualizá-los manual e localmente.

### <a name="large-file-uploaddownload"></a>Upload/download de arquivo grande

Você pode carregar arquivos de até 2 GB, embora, por padrão, esse limite é definido como 1 GB nas configurações do Servidor de Relatórios no SSMS (SQL Server Management Studio).  Esses arquivos são armazenados no banco de dados como no SharePoint e nenhuma configuração especial para o catálogo do SQL Server é necessária.  

### <a name="accessing-shared-datasets-as-odata-feeds"></a>Acessando conjuntos de dados compartilhados como feeds OData

Você pode acessar os conjuntos de dados compartilhados do Power BI Desktop com um feed OData. Para obter mais informações, consulte [Acessando conjuntos de dados compartilhados como feeds OData no Servidor de Relatórios do Power BI](access-dataset-odata.md).

### <a name="scale-out"></a>Escalabilidade horizontal

Esta versão é compatível com escalabilidade horizontal. Use um balanceador de carga e defina a afinidade do servidor para uma melhor experiência. O cenário ainda não está otimizado para expansão, portanto, você verá os modelos potencialmente replicados em vários nós. O cenário funcionará sem o balanceador de carga de rede e as sessões temporárias. No entanto, você não só verá um uso excessivo de memória nos nós conforme o modelo for carregado N vezes, como o desempenho também ficará mais lento entre as conexões conforme o modelo for transmitido a um novo nó entre as solicitações.  

### <a name="administrator-settings"></a>Configurações do administrador

Os administradores podem definir as seguintes propriedades nas Propriedades Avançadas do SSMS para o farm de servidores:

* EnableCustomVisuals: Verdadeiro/Falso
* EnablePowerBIReportEmbeddedModels: Verdadeiro/Falso
* EnablePowerBIReportExportData: Verdadeiro/Falso
* MaxFileSizeMb: agora, o padrão é 1000
* ModelCleanupCycleMinutes: a frequência de verificação para remover modelos da memória
* ModelExpirationMinutes: quanto tempo levará até o modelo expirar e ser removido, com base no último uso
* ScheduleRefreshTimeoutMinutes: quanto tempo pode demorar a atualização de dados para um modelo. O padrão é duas horas.  Não há nenhum limite máximo.

**Arquivo de configuração rsreportserver.config**

```xml
<Configuration>
  <Service>
    <PollingInterval>10</PollingInterval>
    <IsDataModelRefreshService>false</IsDataModelRefreshService>
    <MaxQueueThreads>0</MaxQueueThreads>
  </Service>
</Configuration>
```

### <a name="developer-api"></a>API para desenvolvedores

A API para desenvolvedores (API REST) apresentada para o SSRS 2017 foi estendida para o Servidor de Relatórios do Power BI trabalhar com arquivos do Excel e .pbix. Um possível caso de uso é, por meio de programação, baixar arquivos do servidor, atualizá-los e publicá-los novamente. Essa é a única maneira de atualizar as pastas de trabalho do Excel com modelos do PowerPivot, por exemplo.

Há uma nova API separada para arquivos grandes, que será atualizada na versão do Servidor de Relatórios do Power BI do Swagger. 

### <a name="sql-server-analysis-services-ssas-and-the-power-bi-report-server-memory-footprint"></a>O SSAS (SQL Server Analysis Services) e o volume de memória do Servidor de Relatórios do Power BI

O Servidor de Relatórios do Power BI agora hospeda o SSAS (SQL Server Analysis Services) internamente. Isso não é específico para a atualização agendada. Hospedar o SSAS pode expandir consideravelmente o volume de memória do servidor de relatório. O arquivo de configuração AS.ini está disponível nos nós do servidor, portanto, se estiver familiarizado com o SSAS, será possível atualizar as configurações, incluindo o limite máximo de memória, o cache de disco, etc. Consulte [Propriedades de servidor do Analysis Services](https://docs.microsoft.com/sql/analysis-services/server-properties/server-properties-in-analysis-services) para obter detalhes.

### <a name="viewing-and-interacting-with-excel-workbooks"></a>Exibição e interação com as pastas de trabalho do Excel

O Excel e o Power BI contêm um portfólio de ferramentas que é exclusivo no setor. Juntas, elas permitem que os analistas de negócios reúnam, moldem, analisem e explorem visualmente seus dados com mais facilidade. Além de exibirem os relatórios do Power BI no portal da Web, os usuários empresariais agora podem fazer o mesmo com as pastas de trabalho do Excel no Servidor de Relatórios do Power BI, o que proporciona a eles uma única localização para publicar e exibir seu conteúdo de autoatendimento do Microsoft BI.

Publicamos um [passo a passo de como adicionar um OOS (Servidor do Office Online) em seu ambiente de versão prévia do Servidor de Relatórios do Power BI](excel-oos.md). Os clientes que têm uma conta de Licenciamento por Volume podem baixar o OOS do Centro de Manutenção da Licença de Volume sem nenhum custo e terão a funcionalidade somente exibição. Uma vez configuradas, os usuários poderão exibir e interagir com as pastas de trabalho do Excel que:

* Não tiverem nenhuma dependência de fonte de dados externa
* Tiverem uma conexão dinâmica com uma fonte de dados externa do SQL Server Analysis Services
* Tiver um modelo de dados PowerPivot

### <a name="support-for-new-table-and-matrix-visuals"></a>Suporte para os novos elementos visuais de matriz e de tabela

O Servidor de Relatórios do Power BI agora é compatível com os novos elementos visuais de matriz e de tabela do Power BI. Para criar relatórios com esses elementos visuais, você precisará de uma versão atualizada do Power BI Desktop para a versão de outubro de 2017. Ela não pode ser instalada lado a lado com a versão do Power BI Desktop (junho de 2017). Para obter a versão mais recente do Power BI Desktop, na [página de download do Servidor de Relatórios do Power BI](https://powerbi.microsoft.com/report-server/), selecione **Opções de download avançadas**.

## <a name="june-2017"></a>Junho de 2017

* Servidor de Relatório do Power BI disponibilizado para o público geral (GA).

## <a name="may-2017"></a>Maio de 2017

* Visualização do Servidor de Relatório do Power BI disponibilizada
* Capacidade de publicar relatórios do Power BI local
  * Suporte para visuais do Power BI
  * Suporte para **conexões dinâmicas do Analysis Services** somente com as novas fontes de dados que serão fornecidas.
  * Aplicativo Power BI para Celulares atualizado para exibir relatórios do Power BI hospedados no Servidor de Relatório do Power BI
* Colaboração aprimorada em relatórios com comentários

## <a name="next-steps"></a>Próximas etapas

Verifique essas fontes para ficar atualizado sobre os novos recursos no Servidor de Relatórios do Power BI.

* [Blog do Microsoft Power BI](https://powerbi.microsoft.com/blog/)
* O [canal do YouTube Guy in a Cube](https://aka.ms/guyinacube)

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
