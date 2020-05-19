---
title: Teste de envio de um visual de Power BI
description: Este artigo descreve casos de teste pelos quais seu visual deve passar antes de publicar no AppSource. Há também casos de teste opcionais.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 04/15/2020
ms.openlocfilehash: 65e00fa5311ea12c9fe0011c6aa7c3e779f33dc5
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83131132"
---
# <a name="submission-testing-of-a-power-bi-visual"></a>Teste de envio de um visual de Power BI

Antes de publicar seu visual no [AppSource](https://appsource.microsoft.com/marketplace/apps?product=power-bi-visuals), ele deverá passar por esses casos de teste. Teste seu visual antes de enviá-lo. Se o seu visual não for aprovado nos casos de teste necessários, ele será rejeitado.

Para saber mais sobre o processo de publicação, confira [Publicar visuais do Power BI no Partner Center](./office-store.md).

## <a name="general-test-cases"></a>Casos de teste gerais

| Caso de teste | Resultados esperados
| --------- | ----------------
| Crie um **Gráfico de colunas empilhadas** com **Categoria** e **Valor**. Converta-o em seu visual e, em seguida, retorne-o para gráfico de colunas. | Nenhum erro é exibido após essas conversões. |
| Crie um **Indicador** com três medidas. Converta-o em seu visual e, em seguida, retorne-o para o **Indicador**. | Nenhum erro é exibido após essas conversões. |
| Faça seleções em seu visual. | Outros visuais refletem as seleções. |
| Selecione elementos em outros visuais. | Seu visual mostra dados filtrados de acordo com a seleção em outros visuais. |
| Verifique as condições mín/máx de **dataViewMapping**. | Os buckets de campo podem aceitar vários campos, um único campo ou são determinados por outros buckets. As condições mín/máx de **dataViewMapping** devem ser configuradas corretamente nos recursos do seu visual. |
| Remova todos os campos em ordens diferentes. | O visual limpa corretamente à medida que os campos são removidos em ordem arbitrária. Não há erros no console ou no navegador. |
| Abra o painel **Formato** com cada configuração de bucket possível. | Este teste não dispara exceções de referência nulas. |
| Filtre dados usando o painel **​​Filtro** no nível de visual, página e relatório. | As dicas de ferramentas estão corretas após a aplicação de filtros. As dicas de ferramentas mostram o valor filtrado. |
| Filtrar dados usando uma **Segmentação de Dados**. | As dicas de ferramentas estão corretas após a aplicação de filtros. As dicas de ferramentas mostram o valor filtrado. |
| Filtre dados usando um visual publicado. Por exemplo, selecione uma fatia de pizza ou uma coluna. | As dicas de ferramentas estão corretas após a aplicação de filtros. As dicas de ferramentas mostram o valor filtrado. |
| Se houver suporte para filtragem cruzada, verifique se os filtros funcionam corretamente. | A seleção aplicada filtra outros visuais nesta página do relatório. |
| Selecione com as teclas Ctrl, Alt e Shift. | Nenhum comportamento inesperado é exibido. |
| Altere o **Modo de Exibição** para **Tamanho Real**, **Ajustar à Página** e **Ajustar à Largura**. | As coordenadas do mouse são precisas. |
| Redimensione seu visual. | O visual reage corretamente ao redimensionamento. |
| Defina o tamanho do relatório para o mínimo. | Não há erros de exibição. |
| Verifique se as barras de rolagem funcionam corretamente. | As barras de rolagem devem existir, se necessário. Verifique os tamanhos das barras de rolagem. As barras de rolagem não devem ser muito largas ou compridas. A posição e o tamanho das barras de rolagem devem estar de acordo com outros elementos do seu visual. Verifique se são necessárias barras de rolagem para diferentes tamanhos do visual. |
| Fixe seu visual em um **Painel**. | O visual deve ser exibido corretamente. |
| Adicione várias versões do visual a uma única página de relatório. | Todas as versões do visual são exibidas e operam corretamente. |
| Adicione várias versões do visual a várias páginas de relatório. | Todas as versões do visual são exibidas e operam corretamente. |
| Alterne entre páginas do relatório. | O visual é exibido corretamente. |
| Teste a exibição de leitura e a exibição de edição para o visual. | Todas as funções funcionam corretamente. |
| Se o seu visual usa animações, adicione, altere e exclua elementos do visual. | A animação dos visuais funciona corretamente. |
| Abra o painel **Propriedades**. Ative e desative as propriedades, insira texto personalizado, destaque as opções disponíveis e insira dados inválidos. | O visual responde corretamente. |
| Salve o relatório e reabra-o. | Todas as configurações de propriedades persistem. |
| Alterne as páginas no relatório e, em seguida, retorne. | Todas as configurações de propriedades persistem. |
| Teste todas as funcionalidades do visual, incluindo diferentes opções fornecidas pelo visual. | Todas as exibições e recursos funcionam corretamente. |
| Teste todos os tipos de dados numéricos, de data e de caractere, como nos testes a seguir. | Todos os dados estão formatados corretamente. |
| Verifique a formatação dos valores das dicas de ferramenta, rótulos de eixo, rótulos de dados e outros elementos visuais com formatação. | Todos os elementos estão formatados corretamente. |
| Verifique se os rótulos de dados usam a cadeia de caracteres de formato. | Todos os rótulos de dados estão formatados corretamente. |
| Ative e desative a formatação automática para valores numéricos nas dicas de ferramentas. | As dicas de ferramentas exibem os valores corretamente. |
| Teste as entradas de dados com diferentes tipos de dados, incluindo sequências numéricas, de texto, de data e hora e de formato diferentes do modelo. Teste diferentes volumes de dados, como milhares de linhas, uma linha e duas linhas. | Todas as exibições e recursos funcionam corretamente. |
| Forneça dados inválidos ao seu visual, como nulo, infinito, valores negativos e tipos de valores incorretos. | Todas as exibições e recursos funcionam corretamente. |

## <a name="optional-browser-testing"></a>Teste de navegador opcional

A equipe do AppSource valida o visual nas versões mais recentes do Windows dos navegadores Google Chrome, Microsoft Edge e Mozilla Firefox.
Opcionalmente, teste o visual nos navegadores a seguir.

| Caso de teste | Resultados esperados
| --------- | ----------------
| **Windows** |
| Google Chrome (versão anterior) | Todas as exibições e recursos funcionam corretamente. |
| Mozilla Firefox (versão anterior) | Todas as exibições e recursos funcionam corretamente. |
| Microsoft Edge (versão anterior) | Todas as exibições e recursos funcionam corretamente. |
| Microsoft Internet Explorer 11 (opcional) | Todas as exibições e recursos funcionam corretamente. |
| **macOS** |
| Chrome (versão anterior) | Todas as exibições e recursos funcionam corretamente. |
| Firefox (versão anterior) | Todas as exibições e recursos funcionam corretamente. |
| Safari (versão anterior) | Todas as exibições e recursos funcionam corretamente. |
| **Linux** |
| Firefox (versões mais recentes e anteriores) | Todas as exibições e recursos funcionam corretamente. |
| **Mobile iOS** |
| Apple Safari iPad (versão anterior do Safari) | Todas as exibições e recursos funcionam corretamente. |
| Chrome iPad (versão mais recente do Safari) | Todas as exibições e recursos funcionam corretamente. |
| **Mobile Android** |
| Chrome (versões mais recentes e anteriores) | Todas as exibições e recursos funcionam corretamente. |

## <a name="desktop-testing"></a>Teste de desktop

Teste o visual na versão atual do [Power BI Desktop](https://powerbi.microsoft.com/en-us/desktop/).

| Caso de teste | Resultados esperados
| --------- | ----------------
| Teste todos os recursos do visual. | Todas as exibições e recursos funcionam corretamente. |
| Importe, salve, abra um arquivo e publique no serviço Web do Power BI usando o botão **Publicar** no Power BI Desktop. | Todas as exibições e recursos funcionam corretamente. |
| Altere a cadeia de caracteres de formato numérico para ter zero casas decimais ou três casas decimais, aumentando ou diminuindo a precisão. | O visual é exibido corretamente. |

## <a name="performance-testing"></a>Testes de desempenho

O visual deve ter um nível aceitável. Use ferramentas de desenvolvedor para validar o desempenho. Não confie em indicações visuais e nos logs de tempo do console.

| Caso de teste | Resultados esperados
| --------- | ----------------
| Crie um visual com muitos elementos visuais. | O visual deve ter um bom desempenho e não congelar o aplicativo. Não deve haver problemas de desempenho com elementos como velocidade da animação, redimensionamento, filtragem e seleção.

## <a name="next-steps"></a>Próximas etapas

Para saber mais sobre o processo de publicação, confira [Publicar visuais do Power BI no Partner Center](./office-store.md).

Mais perguntas? [Perguntar à Comunidade do Power BI](https://community.powerbi.com/).
