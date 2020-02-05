---
title: Perguntas frequentes sobre visuais do Power BI
description: Navegue por uma lista de perguntas frequentes e respostas sobre os visuais do Power BI
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.topic: conceptual
ms.subservice: powerbi-custom-visuals
ms.custom: ''
ms.date: 12/17/2018
ms.openlocfilehash: 01fe7056c844a9eed96356e478cc23d5593809bd
ms.sourcegitcommit: 8e3d53cf971853c32eff4531d2d3cdb725a199af
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/04/2020
ms.locfileid: "75759050"
---
# <a name="power-bi-visuals-faq"></a>Perguntas frequentes sobre os visuais do Power BI

## <a name="organizational-power-bi-visuals"></a>Visuais do Power BI da organização

O portal de administração permite o gerenciamento de visuais do Power BI para sua organização.

### <a name="how-can-the-admin-manage-organizational-power-bi-visuals"></a>De que maneira o administrador pode gerenciar os visuais do Power BI da organização?

Na guia *Visuais da organização* do Portal de Administração, o administrador consegue visualizar e [gerenciar todos os visuais do Power BI da organização na empresa](../service-admin-portal.md#organizational-visuals). Isso inclui adicionar, desabilitar, habilitar e excluir os visuais do Power BI.

Os usuários na organização podem encontrar com facilidade os visuais do Power BI e importá-los para seus relatórios diretamente do Power BI Desktop ou do Serviço do Power BI.

Quando o administrador carrega uma nova versão de um visual do Power BI da organização, todos recebem a mesma versão atualizada. Todos os relatórios que usam visuais atualizados do Power BI são atualizados automaticamente.

Os usuários podem encontrar os visuais do Power BI da organização no Power BI Desktop interno e no serviço do Power BI no repositório da organização, na guia *MINHA ORGANIZAÇÃO*. 

### <a name="if-an-admin-uploads-a-power-bi-visual-from-the-public-marketplace-to-the-organization-store-is-it-automatically-updated-once-a-vendor-updates-the-visual-in-the-public-marketplace"></a>Se um administrador carregar um visual do Power BI do marketplace público para o repositório da organização, ele será automaticamente atualizado quando um fornecedor atualizar o visual no marketplace público?

Não, não há uma atualização automática do marketplace público. É responsabilidade do administrador atualizar a versão dos visuais do Power BI da organização.

### <a name="is-there-a-way-to-disable-the-organization-store"></a>Existe alguma forma de desabilitar o repositório da organização?

Não, os usuários sempre visualizam a guia *MINHA ORGANIZAÇÃO* no Power BI Desktop e no serviço do Power BI. Se um administrador desabilitar ou excluir todos os visuais do Power BI da organização do portal de administração, o repositório organizacional ficará vazio.
  
### <a name="if-the-admin-disables-power-bi-visuals-from-the-admin-portal-tenant-settings-do-users-still-have-access-to-the-organizational-power-bi-visuals"></a>Se o administrador desabilitar os visuais do Power BI do Portal de Administração (configurações de locatário), os usuários ainda terão acesso aos visuais do Power BI da organização?

Sim, se o administrador desabilitar os visuais do Power BI no Portal de Administração, isso não afetará o repositório organizacional.

Algumas organizações desabilitam os visuais do Power BI e habilitam apenas os visuais selecionados que foram importados e carregados pelo administrador do Power BI no repositório organizacional.

A desabilitação dos visuais do Power BI no Portal de Administração não é uma imposição no Power BI Desktop. Os usuários do desktop ainda poderão adicionar e usar os visuais do Power BI do marketplace público nos próprios relatórios. No entanto, esses visuais públicos do Power BI deixam de ser renderizados após serem publicados no serviço do Power BI e geram um erro apropriado. 

Quando a configuração de visuais do Power BI no portal de administração é imposta, os usuários no serviço do Power BI não podem importar visuais do Power BI do marketplace público. Somente visuais do repositório organizacional podem ser importados.

### <a name="what-are-the-advantages-of-power-bi-visuals-in-the-organizational-store"></a>Quais são as vantagens dos visuais do Power BI no repositório organizacional?

* Todos recebem a mesma versão do visual, que é controlada pelo administrador do Power BI. Depois que o administrador atualiza a versão do visual no Portal de Administração, todos os usuários na organização recebem a versão atualizada automaticamente.

* Não é necessário compartilhar arquivos dos visuais por email ou pastas compartilhadas. As ofertas do repositório organizacional são visíveis para todos os membros conectados.

* Segurança e compatibilidade: as novas versões dos visuais do Power BI da organização são atualizadas automaticamente em todos os relatórios.

* Os administradores podem controlar quais visuais do Power BI são disponibilizados em toda a organização.

* Os administradores podem habilitar/desabilitar visuais para testes no Portal de Administração.

## <a name="certified-power-bi-visuals"></a>Visuais do Power BI certificados

### <a name="what-are-certified-power-bi-visuals"></a>O que são visuais do Power BI certificados?

Os visuais do Power BI certificados são visuais que atendem a determinados [requisitos](power-bi-custom-visuals-certified.md) e são certificados pela Microsoft.

No [marketplace](https://appsource.microsoft.com/marketplace/apps?page=1&product=power-bi-visuals), os visuais do Power BI certificados têm uma notificação amarela indicando isso.

A Microsoft não é a autora de visuais do Power BI de terceiros. Recomendamos aos clientes contatar o autor diretamente para verificar a funcionalidade dos visuais de terceiros.

### <a name="what-tests-are-done-during-the-certification-process"></a>Quais testes são feitos durante o processo de certificação?

Os testes do processo de certificação incluem, entre outros: 
* Revisões de código
* Análise de código estático
* Vazamento de dados
* Difusão de dados
* Teste de penetração
* Testes de XSS de acesso
* Injeção de dados mal-intencionados
* Validação de entrada
* Testes funcionais
 
### <a name="are-certified-power-bi-visual-checked-again-with-every-new-submission-upgrade"></a>O visual do Power BI certificado é verificado novamente a cada novo envio (atualização)?

Sim. Sempre que uma nova versão do visual de certificado é enviada para o Marketplace, a atualização da versão do visual fica sob as mesmas verificações de certificação.

A certificação de atualização de versão é automática. Se houver uma violação que faça com que a atualização seja rejeitada, um email será enviado ao desenvolvedor para explicar o que precisa ser corrigido.

### <a name="can-a-certified-power-bi-visual-stop-lose-its-certification-after-a-new-update"></a>Uma interrupção do visual do Power BI certificado perde sua certificação após uma nova atualização?

Não, isso não é possível. Um visual certificado não pode perder sua certificação com uma nova atualização. A atualização é rejeitada.
 
### <a name="do-i-need-to-share-my-code-in-a-public-repository-if-im-certifying-my-power-bi-visual"></a>Precisarei compartilhar meu código em um repositório público se estiver certificando meu visual do Power BI?

Não, você não precisa compartilhar seu código publicamente.

Forneça permissões de leitura para verificar o código do visual do Power BI. Por exemplo, usando um repositório privado no GitHub.
 
### <a name="does-a-certified-power-bi-visual-have-to-be-in-the-marketplace"></a>Um visual do Power BI certificado deve estar no marketplace?

Sim. Os visuais privados não são certificados.
 
### <a name="how-long-does-it-take-to-certify-my-visual"></a>Quanto tempo leva para certificar meu visual?

A certificação de um novo visual do Power BI (primeira certificação) pode levar até quatro semanas. 

A certificação de uma versão atualizada de um visual do Power BI pode levar até três semanas. 

### <a name="does-the-certification-process-ensure-that-there-is-no-data-leakage"></a>O processo de certificação garante que não haja vazamento de dados?

Os testes executados são projetados para verificar se o visual não acessa serviços ou recursos externos. 

A Microsoft não é a autora de visuais do Power BI de terceiros. Recomendamos aos clientes contatar o autor diretamente para verificar a funcionalidade dos visuais do Power BI de terceiros.
 
### <a name="are-uncertified-power-bi-visuals-safe-to-use"></a>É seguro usar visuais do Power BI não certificados?

Visuais do Power BI não certificados não são necessariamente visuais não seguros.

Alguns visuais não são certificados, pois não são compatíveis com um ou mais dos [requisitos de certificação](https://docs.microsoft.com/power-bi/power-bi-custom-visuals-certified?#certification-requirements). Por exemplo, conectar-se a um serviço externo, como o mapa de visuais, ou usar bibliotecas comerciais ou visuais.
 
## <a name="visuals-with-additional-purchases"></a>Visuais com compras adicionais

### <a name="what-is-a-visual-with-additional-purchases"></a>O que é um visual com compras adicionais?

Um visual com compras adicionais é semelhante aos suplementos de IAP (compra no aplicativo). Esses suplementos incluem uma marca de preço **Uma compra adicional pode ser necessária**.

Os visuais de IAP do Power BI são gratuitos e podem ser baixados. Os usuários não pagam nada para baixar esses visuais do Power BI do marketplace.

Os visuais de IAP oferecem compras opcionais no aplicativo para recursos avançados.  

### <a name="what-is-changing-in-the-submission-process"></a>O que está mudando no processo de envio?

O processo de envio de visuais de IAP do Power BI para o marketplace é o mesmo processo para visuais do Power BI gratuitos. Você pode enviar um visual do Power BI para ser certificado usando o [Partner Center](https://docs.microsoft.com/partner-center/).


Ao registrar seu visual do Power BI, navegue até a guia *Configuração do produto* e marque a caixa de seleção *Meu produto requer a compra de um serviço*.

### <a name="what-should-i-do-beforesubmittingmy-iap-power-bi-visual"></a>O que devo fazer antes de enviar meu visual de IAP do Power BI?

Se você estiver trabalhando em um visual de IAP do Power BI, verifique se ele está em conformidade com as [diretrizes](guidelines-powerbi-visuals.md).  

> [!NOTE]
> Os visuais do Power BI gratuitos com um recurso de IAP adicionado devem manter os mesmos recursos gratuitos oferecidos anteriormente. Você pode adicionar recursos pagos avançados opcionais aos recursos gratuitos antigos. É recomendável enviar o visual de IAP do Power BI com os recursos avançados como um novo visual do Power BI, e não como uma atualização ao antigo gratuito.

### <a name="do-iap-power-bi-visuals-need-to-be-certified"></a>Os visuais de IAP do Power BI precisam ser certificados?

O processo de [certificação](power-bi-custom-visuals-certified.md) é opcional. Cabe ao desenvolvedor decidir certificar seu visual de IAP do Power BI ou não.

### <a name="can-i-get-my-iap-power-bi-visual-certified"></a>Posso obter meu visual de IAP do Power BI certificado?

Sim, assim que o visual de IAP do Power BI for aprovado pela equipe do AppSource, você poderá enviá-lo para ser [certificado](power-bi-custom-visuals-certified.md).

A certificação é um processo opcional; cabe a você decidir se deseja que seu visual de IAP seja certificado.

## <a name="additional-questions"></a>Outras perguntas

### <a name="how-to-get-support"></a>Como obtenho suporte?

Fique à vontade para contatar a equipe de suporte de visuais do Power BI em pbicvsupport@microsoft.com, caso tenha perguntas, comentários ou problemas.  

## <a name="next-steps"></a>Próximas etapas

Saiba mais em [Solução de problemas com visuais do Power BI](power-bi-custom-visuals-troubleshoot.md).
