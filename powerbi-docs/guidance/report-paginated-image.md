---
title: Diretrizes de uso de imagem para relatórios paginados
description: Diretrizes para o uso de imagens em relatórios paginados do Power BI.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 02/16/2020
ms.author: v-pemyer
ms.openlocfilehash: d2f3f36911c72df1b95ceb5bd90043870559cc62
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/05/2020
ms.locfileid: "78920723"
---
# <a name="image-use-guidance-for-paginated-reports"></a>Diretrizes de uso de imagem para relatórios paginados

Este artigo se destina aos autores de relatórios que elaboram [relatórios paginados](../paginated-reports/paginated-reports-report-builder-power-bi.md) do Power BI. Ele fornece sugestões ao trabalhar com imagens. Normalmente, as imagens em layouts de relatório podem exibir um gráfico como um logotipo de empresa ou imagens.

As imagens podem ser armazenadas em três locais diferentes:

- Dentro do relatório (inseridas)
- Em um servidor Web
- Em um banco de dados, que podem ser recuperadas por um conjunto de dados

Elas podem ser usadas em uma variedade de cenários em seus layouts de relatório:

- Logotipo independente ou imagem
- Imagens associadas a linhas de dados
- Tela de fundo para determinados itens de relatório:
  - Corpo do relatório
  - Caixa de texto
  - Retângulo
  - Região de dados Tablix (tabela, matriz ou lista)

## <a name="suggestions"></a>Sugestões

Considere as seguintes sugestões para fornecer layouts de relatório profissionais, facilidade de manutenção e desempenho de relatório otimizado:

- **Use o menor tamanho possível**: recomendamos que você prepare imagens que sejam pequenas em tamanho, ainda que pareçam nítidas. Trata-se de promover um equilíbrio entre qualidade e tamanho. Considere usar um editor de gráficos (como o MS Paint) para reduzir o tamanho do arquivo de imagem.
- **Evite imagens incorporadas**: primeiro, imagens incorporadas podem sobrecarregar o tamanho do arquivo de relatório, o que pode contribuir para desacelerar a renderização do relatório. Segundo, imagens incorporadas poderão rapidamente se tornar um pesadelo de manutenção se você precisar atualizar muitas imagens de relatório (como poderá ser o caso, se o logotipo da sua empresa for alterado).
- **Use o armazenamento do servidor Web**: o armazenamento de imagens em um servidor Web é uma boa opção, principalmente para o logotipo da empresa, que pode ter origem no site da empresa. No entanto, tome cuidado se os usuários acessarem relatórios fora da rede. Nesse caso, verifique se as imagens estão disponíveis pela Internet.

    Quando as imagens se relacionam com seus dados (como imagens de seus vendedores), nomeie arquivos de imagem para que uma expressão de relatório possa produzir dinamicamente o caminho da URL da imagem. Por exemplo, você pode nomear as imagens de vendedores usando o número de funcionário de cada vendedor. Fornecer o conjunto de dados de relatório recupera o número do funcionário; você pode escrever uma expressão para produzir o caminho completo da URL da imagem.
- **Use o armazenamento do banco de dados**: quando um banco de dados relacional armazena um dado de imagem, faz sentido originar os dados da imagem diretamente das tabelas de banco de dados – principalmente quando as imagens não são muito grandes.
- **Imagens em segundo plano apropriadas**: se você decidir usar imagens em segundo plano, tome cuidado para não desviar o usuário de relatório dos dados do relatório. 

    Além disso, use _imagens com marca-d'água_. Em geral, as imagens com marca-d'água têm uma tela de fundo transparente (ou têm a mesma cor da tela de fundo usada pelo relatório). Elas também usam cores esmaecidas. Exemplos comuns de imagens com marca-d'água incluem o logotipo da empresa ou rótulos de confidencialidade, como "Rascunho" ou "Confidencial".

## <a name="next-steps"></a>Próximas etapas

Para obter mais informações relacionadas a este artigo, confira os seguintes recursos:

- [O que são os relatórios paginados no Power BI Premium?](../paginated-reports/paginated-reports-report-builder-power-bi.md)
- Dúvidas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
- Sugestões? [Contribuir com ideias para aprimorar o Power BI](https://ideas.powerbi.com/)
