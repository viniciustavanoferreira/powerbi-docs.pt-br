---
title: Conformidade da extensão de renderização de PDFs com a ISO 14289-1 – Servidor de Relatórios do Power BI e SSRS
description: Este documento descreve a conformidade da Extensão de Renderização de PDFs do Servidor de Relatórios do Power BI e do SQL Server Reporting Services com especificações ISO 14289-1 (PDF/UA).
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 11/04/2019
ms.author: maggies
ms.openlocfilehash: bfefcef18b8cd92a5c3b15c2dcbd4653a6c7c9cd
ms.sourcegitcommit: 0cc594ebb78a6d0e88784673ed09f8aefd10c7a7
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76819504"
---
# <a name="pdf-rendering-extension-conformance-to-iso-14289-1---power-bi-report-server--ssrs"></a>Conformidade da extensão de renderização de PDFs com a ISO 14289-1 – Servidor de Relatórios do Power BI e SSRS

Aplica-se a: Servidor de Relatórios do Power BI e SSRS (SQL Server Reporting Services)

Este documento descreve a conformidade da Extensão de Renderização de PDFs do Servidor de Relatórios do Power BI e do SQL Server Reporting Services com especificações [ISO 14289-1 (PDF/UA)](https://www.pdfa.org/publication/pdfua-in-a-nutshell/).

> [!NOTE]
> Você pode salvar ou imprimir este whitepaper selecionando **Imprimir** no seu navegador e, em seguida, selecionando **Salvar como PDF**.

## <a name="1--scope"></a>1.  Escopo

Não aplicável

## <a name="2--normative-references"></a>2.  Referências normativas

Não aplicável

## <a name="3--terms-and-definitions"></a>3.  Termos e definições

Não aplicável

## <a name="4--notation"></a>4.  Anotações

Não aplicável

## <a name="5-version-identification"></a>5. Identificação da Versão

A Extensão de renderização de PDFs oferece suporte para PDF/UA, conforme descrito neste documento. Em alguns casos, apresentados abaixo, é responsabilidade do usuário seguir as etapas para verificar se um PDF está em conformidade completa com PDF/UA.  Esperamos que o usuário adicione a versão do PDF/UA e os identificadores de conformidade adequados como a última etapa deste processo, indicando que o trabalho necessário foi feito que o PDF esteja totalmente em conformidade com o PDF/UA.

Todos os itens listados neste documento são baseados na renderização de um documento PDF com a configuração de informações do dispositivo AccessiblePdf definida como `true`. Em alguns casos, as limitações de conformidade ocorrem devido a limitações na linguagem RDL.

## <a name="6--conformance-requirements"></a>6.  Requisitos de conformidade

|     Critérios     |     Recurso de suporte     |     Comentários      |
|----|--------|--------|
|    6.1 Geral    |                 Compatível    |    A Extensão de Renderização de PDFs cria o PDF versão 1.7.    |
|    6.2 Arquivos de conformidade    |                 Há suporte com exceções    |    Confira os comentários na seção 7 – Requisitos de formato de arquivo.    |
|    6.3 Leitor de conformidade    |     Não Aplicável     |         |
|    6.4 Tecnologia adaptativa de conformidade    |     Não Aplicável     |         |

## <a name="7--file-format-requirements"></a>7.  Requisitos do formato de arquivo

|     Critérios     |     Recurso de suporte     |     Comentários      |
|-----|-------|------------------------|
|    7.1 Geral    |                 Há suporte com exceções    |    Todo o conteúdo real deve ser marcado conforme definido no ISO 32000-1:2008, 14,8. Os artefatos (ISO 32000-1:2008, 14.8.2.2.2) não devem ser marcados na árvore de estrutura. <li> A Extensão de Renderização de PDFs não oferece a flexibilidade de marcar explicitamente itens individuais como artefatos; portanto, em vez disso, ele definirá como artefato tudo que é mapeado para os critérios no ISO 32000-1:2008, 14.8.2.2.2.<br>O conteúdo deverá ser marcado na árvore de estrutura com as marcas semanticamente apropriadas em uma ordem lógica de leitura. <br> **Observação** 4   A WCAG 2.0, Diretriz 1.4 explica problemas com relação ao contraste, à cor e a outras opções de formatação para melhorar a acessibilidade. <br><li> O usuário precisaria verificar se seu documento não está sujeito a esses problemas. <br>As marcas padrão definidas no ISO 32000-1:2008, 14.8.4, não devem ser remapeadas. <li> A Extensão de Renderização de PDFs não mapeia novamente as marcas padrão. Os documentos começam com o Elemento raiz do documento. <br>Os arquivos que reivindicam conformidade com esse Padrão Internacional devem ter um valor de falso Suspeitos (ISO   32000-1:2008, Tabela 321). <li> A Extensão de Renderização de PDFs não tem a entrada Suspeitos. Esta propriedade é opcional.    |
|    7.2 Texto    |                 Há suporte com exceções    |    O conteúdo deverá ser marcado na ordem lógica de leitura. A marca mais semanticamente adequada deverá ser usada para cada elemento lógico no conteúdo do documento. <br><li> A Extensão de Renderização de PDFs marca o conteúdo em ordem lógica de leitura tanto quanto possível.<br>Os códigos de caractere deverão mapear para Unicode, conforme descrito no ISO 32000-1:2008, 14.8.2.4.2. Os caracteres não incluídos na especificação Unicode podem usar a área de uso particular Unicode ou declarar outra codificação de caractere. <br>A linguagem natural deve ser declarada conforme discutido no ISO 32000-1:2008, 14.9.2 e/ou conforme descrito no ISO   32000-1:2008, 7.9.2. As alterações no idioma natural devem ser declaradas. As alterações em um idioma natural dentro das cadeias de caracteres de texto (por ex., dentro de descrições alternativas) devem ser declaradas usando um identificador de idioma conforme descrito no ISO 32000-1:2008, 14.9.2.2. <br><li> A extensão de Renderização de PDFs só declara o idioma natural no nível do documento    |
|    7.3 Elementos gráficos    |                 Há suporte com exceções    |    Os objetos gráficos, diferente de objetos de texto, devem ser marcados com uma marca Figura conforme descrito no ISO 32000-1:2008, 14.8.4.5, Tabela 340. Se qualquer uma das seguintes exceções forem verdadeiras, o elemento gráfico deverá ser marcado como um artefato: <br><li> o elemento gráfico não representa um conteúdo significativo ou <li>  o elemento gráfico é exibido como uma tela de fundo para uma anotação de link; nesse caso, o texto alternativo no link deverá descrever o elemento gráfico e o link. <li> A Extensão de Renderização de PDFs marca objetos gráficos com a marca Figura. <br>Uma legenda que acompanha uma figura deve ser marcada com Legenda. <li> No momento, a Extensão de Renderização de PDFs não marca legendas em figuras com Legenda. <br>As marcas de figura devem incluir uma representação alternativa ou texto de substituição que representa o conteúdo marcado com a marca Figura, conforme observado em ISO 32000-1:2008, 14.7.2, Tabela 323. <br>**Observação** 1 Confira também WCAG 2.0, Diretriz 1.1. <br>Se o texto representado em um elemento gráfico não for o texto em um idioma natural que deva ser lido por um leitor humano, o texto alternativo que descreve a natureza ou a finalidade do elemento gráfico deverá ser fornecido. <br>**Observação** 2 Texto que é um exemplo de tipo ou um exemplo do sistema de escrita usado por um idioma são exemplos de texto que não está em um idioma natural.   A Extensão de Renderização de PDFs dá suporte a texto alt em figuras, embora caiba ao usuário adicionar o texto alt. <br>Observação adicional com relação ao atributo BBox: <br><li> No momento, a Extensão de Renderização de PDFs não grava o atributo BBox. <li> Uma alternativa é marcar de novo manualmente as ilustrações como novas Figuras ou como Artefatos.    |
|    7.4 Títulos    |                 Não Aplicável    |    A RDL não dá suporte à marcação de títulos de forma alguma. Cabe ao usuário marcá-los, conforme apropriado.    |
|    7.5 Tabelas    |                 Há suporte com exceções    |    As tabelas devem incluir cabeçalhos. Os cabeçalhos da tabela devem ser marcados de acordo com o ISO 32000-1:2008, Tabela 337 e Tabela 349. <br>**Observação** 1 As tabelas podem conter cabeçalhos de coluna, de linha ou ambos. <br>**Observação** 2 O máximo de informações possível sobre a estrutura de tabelas precisa ser disponibilizado quando se confia na tecnologia adaptativa. Os cabeçalhos desempenham uma função importante no fornecimento de informações estruturais. <br><li> Cabe ao usuário incluir cabeçalhos em suas tabelas. A RDL e a Extensão de Renderização de PDFs fornecem suporte para cabeçalhos de linha. <br>  Elementos de estrutura do tipo TH devem ter um atributo Scope.   <li> A Extensão de Renderização de PDFs inclui um atributo Scope em elementos TH para Membros de Coluna e Linha, mas não para células de Canto.<br>As estruturas de marcação de tabela só devem ser usadas para marcar o conteúdo apresentado dentro de relações lógicas de linha e/ou coluna.   <li> Isso depende de como o usuário optou por usar tabelas em sua RDL.    |
|    7.6 Listas    |                 Não Aplicável    |    A RDL não dá suporte à marcação de listas. Na RDL, elas são estruturalmente uma tabela com uma única célula de tabela. <br>Cabe ao usuário marcá-las novamente, conforme apropriado.    |
|    7.7 Expressões matemáticas    |                 Há suporte com exceções    |    Todas as expressões matemáticas devem ser colocadas dentro de uma marca de fórmula, conforme detalhado no ISO 32000-1:2008, 14.8.4.5 e devem ter um atributo Alt. <br><li> No momento, a Extensão de Renderização de PDFs não coloca expressões matemáticas dentro de uma marca de fórmula. <br>Os requisitos relacionados ao mapeamento de caracteres para Unicode devem se aplicar a expressões matemáticas, conforme estabelecido no ISO 32000-1:2008, 9.10.2 e 14.8.2.4. <br><li> Isso é compatível com a Extensão de Renderização de PDFs.    |
|    7.8 Cabeçalhos e rodapés de página    |                 Compatível    |    Cabeçalhos e rodapé em execução devem ser identificados como Artefatos de paginação e ser classificados como subtipos Cabeçalho ou Rodapé de acordo com o ISO 32000-1:2008, 14.8.2.2.2, Tabela 330. <br><li> Cabeçalhos ou Rodapés são tratados e marcados como artefatos.    |
|    7.9 Notas e referências    |                 Não Aplicável    |    A Extensão de Renderização de PDFs não dá suporte à marcação de notas e referências. <br>Cabe ao usuário marcá-las, conforme apropriado.    |
|    7.10 Conteúdo opcional    |                 Não Aplicável    |         |
|    7.11 Arquivos inseridos    |                 Não Aplicável    |         |
|    7.12 Threads de artigo    |                 Não Aplicável    |         |
|    7.13 Assinaturas digitais    |                 Não Aplicável    |         |
|    7.14 Formulários não interativos    |                 Não Aplicável    |         |
|    7.15 XFA    |                 Não Aplicável    |         |
|    7.16 Segurança    |                 Não Aplicável    |         |
|    7.17 Navegação    |                 Compatível    |    Um documento deve incluir uma estrutura de tópicos do documento que corresponda à ordem de leitura e ao nível de destinos de navegação (ISO 32000-1:2008, 12.3.3). <br><li> A RDL dá suporte a indicadores para um item de relatório, mas o usuário deve selecionar essa opção. Esses indicadores são renderizados como uma estrutura de tópicos do documento pela Extensão de Renderização de PDFs. <br>Se presentes, as entradas na árvore de números PageLabels (ISO 32000-1:2008, 7.7.2, Tabela 28) deverão ser semanticamente apropriadas. <br><li> A Extensão de Renderização de PDFs não inclui uma árvore de números PageLabels.    |
|    7.18 Anotações    |                 Não Aplicável    |    A RDL não dá suporte a anotações    |
|    7.21 Fontes    |                 Compatível    |         |
|    7.21.1 Geral    |                 Compatível    |         |
|    7.21.2 Tipos de fonte    |                 Compatível    |         |
|    7.21.3 Fontes compostas    |                 Compatível    |         |
|    7.21.3.1 Geral    |                 Compatível    |         |
|    7.21 3.2 CIDFonts    |                 Compatível    |         |
|    7.21.3.3 CMaps    |                 Compatível    |         |
|    7.21.4 Inserção    |                 Compatível    |         |
|    7.21.4.1 Geral    |                 Compatível    |         |
|    7.21.4.2 Inserção de subconjunto    |                 Compatível    |         |
|    7.21.5 Métricas da fonte    |                 Compatível    |         |
|    7.21.6 Codificações de caracteres    |                 Compatível    |         |
|    7.21.7 Mapas de caracteres Unicode    |                 Compatível    |         |
|    7.21.8 Uso do glifo .notdef    |                 Compatível    |         |

## <a name="8--conforming-reader-requirements"></a>8.  Requisitos do leitor de conformidade

Não aplicável

## <a name="9--at-requirements"></a>9.  Requisitos de AT

Não aplicável

## <a name="disclaimer"></a>Disclaimer

© 2017 Microsoft Corporation. All rights reserved. The names of actual companies and products mentioned herein may be the trademarks of their respective owners. The information contained in this document represents the current view of Microsoft Corporation on the issues discussed as of the date of publication. Microsoft cannot guarantee the accuracy of any information presented after the date of publication. Microsoft regularly updates its websites with new information about the accessibility of products as that information becomes available.

Customization of the product voids this conformance statement from Microsoft. Please consult with Assistive Technology (AT) vendors for compatibility specifications of specific AT products.

This document is for informational purposes only. MICROSOFT MAKES NO WARRANTIES, EXPRESS OR IMPLIED, IN THIS DOCUMENT.


## <a name="next-steps"></a>Próximas etapas
[Visão geral do administrador](admin-handbook-overview.md)  

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)

