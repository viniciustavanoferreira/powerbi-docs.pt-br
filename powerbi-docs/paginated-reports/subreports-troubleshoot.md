---
title: Solucionar problemas de sub-relatórios em relatórios paginados no Power BI
description: Neste artigo, você aprenderá sobre as fontes de dados compatíveis para relatórios paginados no serviço do Power BI e como se conectar a fontes de dados do Banco de Dados SQL do Azure.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: troubleshooting
ms.date: 04/29/2020
ms.openlocfilehash: 49a4143fe3dbf55b31b4d30473fe6af3c047dda4
ms.sourcegitcommit: a453ba52aafa012896f665660df7df7bc117ade5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/27/2020
ms.locfileid: "85485911"
---
# <a name="troubleshoot-subreports-in-power-bi-paginated-reports"></a>Solucionar problemas de sub-relatórios em relatórios paginados no Power BI

Às vezes, ao usar sub-relatórios em relatórios paginados, você pode obter um resultado inesperado ou em que o recurso não funciona conforme esperado. Este artigo fornece soluções para problemas comuns ao usar sub-relatórios. Um *sub-relatório* é um item de relatório que exibe outro relatório dentro do corpo de um relatório paginado principal. Confira [Solucionar problemas de sub-relatórios em relatórios paginados no Power BI](subreports.md) para obter mais informações.

## <a name="subreport-couldnt-be-found"></a>Não foi possível encontrar o sub-relatório

**Descrição:** o sub-relatório não é renderizado. Em vez disso, uma mensagem de erro é exibida.

### <a name="message"></a>Mensagem

"Não foi possível encontrar o sub-relatório 'Subreport1' no local 'CustomerDetails' especificado. Verifique se o sub-relatório foi publicado e se o nome está correto."

### <a name="possible-reasons"></a>Possíveis motivos

- Um sub-relatório com o nome especificado não existe no mesmo workspace ou aplicativo que o relatório principal.
- O usuário não tem acesso ao sub-relatório.
- O número de sub-relatórios no relatório principal atingiu o limite de 50 sub-relatórios.

### <a name="troubleshooting-steps"></a>Etapas para solucionar problemas

**Em um workspace**

- Verifique se o relatório com o nome na mensagem de erro existe. O nome diferencia maiúsculas de minúsculas.

**Em um aplicativo**

- Verifique se o relatório com o nome na mensagem de erro existe no aplicativo. Entre em contato com o autor do aplicativo para obter assistência adicional.

**Se o relatório for compartilhado**

1. Verifique se o relatório com o nome na mensagem de erro está compartilhado com você.
2. Se o relatório existir, verifique se o nome do proprietário é o mesmo para o relatório principal e o sub-relatório. Em seguida, entre em contato com o proprietário do relatório principal com essas informações.

## <a name="subreport-renders-with-unexpected-content"></a>O sub-relatório é renderizado com conteúdo inesperado

### <a name="possible-reason"></a>Possível motivo

O Power BI permite que os usuários tenham vários relatórios com o mesmo nome no mesmo workspace

### <a name="troubleshooting-steps-for-report-authors"></a>Etapas da solução de problemas (para autores do relatório)

1. Abra o relatório principal no Power BI Report Builder e determine o nome do sub-relatório.
2. Procure relatórios com o mesmo nome no workspace.
3. Localize o relatório esperado e renomeie o restante.

**Para não autores:** entre em contato com o autor.

## <a name="data-retrieval-fails"></a>Falhas na recuperação de dados

**Descrição:** a recuperação de dados falha ao renderizar o sub-relatório. O sub-relatório não é renderizado. Em vez disso, uma mensagem de erro é exibida.

### <a name="message"></a>Mensagem

"Falha na recuperação de dados para o sub-relatório, 'Subreport1', localizado em: 'InvoiceDetails'. Verifique os arquivos de log para obter mais informações."

### <a name="troubleshooting-steps"></a>Etapas para solucionar problemas

O mesmo que as etapas gerais de solução de problemas para relatórios com problemas de acesso a dados.

## <a name="rendering-fails-unspecified-parameters"></a>Falhas de renderização: parâmetros não especificados

**Descrição:** a renderização do sub-relatório falha devido a parâmetros não especificados. O sub-relatório tem parâmetros obrigatórios, mas o relatório principal não define todos eles.

### <a name="message"></a>Mensagem 
"Um ou mais parâmetros não foram especificados para o sub-relatório 'Subreport1', localizado em: 'SubreportAWithDS'."

### <a name="troubleshooting-steps-for-the-report-author"></a>Etapas da solução de problemas (para o autor do relatório)

1. Abra o relatório principal no Power BI Report Builder.
2. Abra o sub-relatório no Power BI Report Builder.
3. Verifique se o conjunto de parâmetros passado dentro do item de relatório de sub-relatório no relatório principal corresponde ao conjunto de parâmetros no sub-relatório.

**Para não autores:** entre em contato com o autor.

## <a name="rendering-fails-recursion-limit"></a>Falhas de renderização: limite de recursão

**Descrição:** a renderização do sub-relatório falha devido ao limite de recursão. Os sub-relatórios não podem ser aninhados mais profundamente do que 20 níveis.

### <a name="message"></a>Mensagem

"O relatório ou o sub-relatório tem um sub-relatório recursivo, 'Subreport1', que excedeu o limite máximo de recursão permitido."

### <a name="troubleshooting-steps-for-report-authors"></a>Etapas da solução de problemas (para autores do relatório)

- Reduza o aninhamento.
- Reprojete a estrutura do relatório.

## <a name="other-errors"></a>Outros erros

**Descrição:** erros que não recaem em nenhuma das categorias anteriores.

### <a name="message"></a>Mensagem

"Erro: não foi possível mostrar o sub-relatório."

### <a name="possible-reasons"></a>Possíveis motivos

- Vários erros durante a renderização do sub-relatório, por exemplo, incompatibilidade de parâmetro com problemas de recuperação de dados.
- Erros inesperados.

### <a name="troubleshooting-steps-for-report-authors"></a>Etapas da solução de problemas (para autores do relatório)

1. Verifique se o sub-relatório pode renderizar diretamente.
2. Se o sub-relatório puder ser renderizado, verifique os parâmetros no sub-relatório e no relatório principal.
3. Verifique se o relatório principal não tem mais de 50 sub-relatórios exclusivos e se o sub-relatório não está aninhado mais profundamente do que 20 níveis.
4. Se você não conseguir resolver o problema, entre em contato com o suporte do Power BI.

**Para não autores:** entre em contato com o autor.

## <a name="next-steps"></a>Próximas etapas

[Sub-relatórios em relatórios paginados no Power BI](subreports.md)

[Exibir um relatório paginado no serviço do Power BI](../consumer/paginated-reports-view-power-bi-service.md)

Mais perguntas? [Experimente a Comunidade do Power BI](https://community.powerbi.com/)
