---
title: Evitar páginas em branco ao imprimir relatórios paginados
description: Orientação para a criação de relatórios paginados para evitar páginas em branco na impressão.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 01/14/2020
ms.author: v-pemyer
ms.openlocfilehash: 76d1631b95c30d5ae56ced5d64e5174f6f9db759
ms.sourcegitcommit: 0ae9328e7b35799d5d9613a6d79d2f86f53d9ab0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/16/2020
ms.locfileid: "76041855"
---
# <a name="avoid-blank-pages-when-printing-paginated-reports"></a>Evitar páginas em branco ao imprimir relatórios paginados

Este artigo se destina aos autores de relatórios que elaboram [relatórios paginados](../paginated-reports-report-builder-power-bi.md) do Power BI. Ele fornece recomendações para ajudar a evitar páginas em branco quando o relatório é exportado para um formato de página física, como PDF ou Microsoft Word, ou quando é impresso.

## <a name="page-setup"></a>Configuração de página

As propriedades de tamanho de página de relatório determinam a orientação, as dimensões e as margens da página. Acesse essas propriedades de relatório:

- Usando a **Página de Propriedades** do relatório: clique com o botão direito do mouse na área cinza-escura fora da tela relatório e selecione _Propriedades do Relatório_.
- Usando o Painel [**Propriedades**](../paginated-reports-report-design-view.md#4-properties-pane): clique na área cinza-escura fora da tela do relatório para selecionar o objeto de relatório. Verifique se o painel **Propriedades** está aberto.

A página **Configurar Página** da **Página de Propriedades** do relatório fornece uma interface amigável para exibir e atualizar as propriedades de configuração de página.

![A imagem mostra a janela Propriedades do Relatório, realçando a página Configurar Página.](media/report-paginated-blank-page/report-page-setup-properties.png)

Verifique se todas as propriedades de tamanho de página estão configuradas corretamente:

|Property|Recomendação|
|---------|---------|
|Unidades de página|Selecione as unidades relevantes: polegadas ou centímetros.|
|Orientação|Selecione a opção correta: retrato ou paisagem.|
|Tamanho do papel|Selecione um tamanho de papel ou atribua valores de largura e altura personalizados.|
|Margens|Defina os valores apropriados para as margens esquerda, direita, superior e inferior.|
|||

## <a name="report-body-width"></a>Largura do corpo do relatório

As propriedades de tamanho de página determinam o espaço disponível para objetos de relatório. Os objetos do relatório podem ser regiões de dados, visualizações de dados ou outros itens de relatório.

Um motivo comum para a saída de páginas em branco é porque a largura do corpo do relatório _ultrapassa o espaço de página disponível_.

Você só pode exibir e definir a largura do corpo do relatório usando o painel **Propriedades**. Primeiro clique em qualquer lugar em uma área vazia do corpo do relatório.

![A imagem mostra o painel Propriedades, destacando a propriedade largura do corpo do relatório.](media/report-paginated-blank-page/report-body-properties-width.png)

Certifique-se de que o valor da largura não exceda a largura da página disponível. Use a fórmula a seguir:

```Report body width <= Report page width - (Left margin + Right margin)```

> [!NOTE]
> Não é possível reduzir a largura do corpo do relatório se já houver objetos no espaço que você quer remover. Primeiro você precisa reposicioná-los ou redimensioná-los antes de reduzir a largura.
>
> Também é possível aumentar automaticamente a largura do corpo do relatório ao adicionar novos objetos ou ao redimensionar ou reposicionar os objetos existentes. O designer de relatórios sempre amplia o corpo para acomodar a posição e o tamanho dos objetos contidos.

## <a name="report-body-height"></a>Altura do corpo do relatório

Outro motivo que causa a saída de páginas em branco é quando há excesso de espaços no corpo do relatório após o último objeto.

É recomendável sempre reduzir a altura do corpo para remover qualquer espaço à direita.

![A imagem mostra um design de relatório. O espaço abaixo da região de dados Tablix é realçado e marcado como desnecessário.](media/report-paginated-blank-page/report-body-remove-trailing-space.png)

## <a name="page-break-options"></a>Opções de quebra de página

Cada região e visualização de dados têm opções de quebra de página. É possível acessar essas opções na página de propriedades ou no painel **Propriedades**.

Verifique se a propriedade **Adicionar uma quebra de página após** não está ativada sem necessidade.

![A imagem mostra a janela Propriedades de Tablix. A propriedade "Adicionar uma quebra de página após" está ativada.](media/report-paginated-blank-page/data-region-page-break-option-after.png)

## <a name="consume-container-whitespace"></a>Consumir Espaço em Branco do Contêiner

Se o problema da página em branco persistir, você também pode tentar desabilitar a propriedade **ConsumeContainerWhitespace** do relatório. Ela só pode ser configurada no painel **Propriedades**.

![A imagem mostra o painel Propriedades, destacando a propriedade ConsumeContainerWhitespace.](media/report-paginated-blank-page/report-properties-consumecontainerwhitespace.png)

Ela fica habilitada por padrão. Ela determina se o espaço em branco mínimo em contêineres, como o corpo do relatório ou um retângulo, deve ser consumido. Somente o espaço em branco à direita e abaixo do conteúdo é afetado.

## <a name="printer-paper-size"></a>Tamanho do papel da impressora

Por fim, se você estiver imprimindo o relatório em papel, verifique se o papel correto está carregado na impressora. O tamanho do papel físico deve corresponder ao [tamanho do papel do relatório](#page-setup).

## <a name="next-steps"></a>Próximas etapas

Para obter mais informações relacionadas a este artigo, confira os seguintes recursos:

- [O que são os relatórios paginados no Power BI Premium?](../paginated-reports-report-builder-power-bi.md)
- [Paginação em relatórios paginados no Power BI](../paginated-reports-pagination.md)
- Dúvidas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
- Sugestões? [Contribuir com ideias para aprimorar o Power BI](https://ideas.powerbi.com)
