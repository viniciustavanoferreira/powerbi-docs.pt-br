---
title: Extensibilidade do conector no Power BI
description: Funcionalidades de extensibilidade do conector, recursos, configurações de segurança e conectores certificados
author: cpopell
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/02/2020
ms.author: gepopell
LocalizationGroup: Connect to data
ms.openlocfilehash: b604ade56335e65b25501eb9fe3d3c2fd185a6f0
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83293503"
---
# <a name="connector-extensibility-in-power-bi"></a>Extensibilidade do conector no Power BI

O Power BI pode se conectar a dados usando conectores existentes e fontes de dados genéricas, como ODBC, OData, OLE DB, Web, CSV, XML e JSON. Ou os desenvolvedores podem habilitar novas fontes de dados com extensões de dados personalizadas chamadas *conectores personalizados*. Alguns conectores personalizados são certificados e distribuídos pela Microsoft como *conectores certificados*.

Para usar conectores personalizados não certificados desenvolvidos por você ou por terceiros, é necessário ajustar as configurações de segurança do Power BI Desktop para permitir que as extensões sejam carregadas sem validação nem aviso. Como esse código pode processar credenciais, incluindo o envio delas via HTTP, e ignorar os níveis de privacidade, você só deverá usar essa configuração de segurança se confiar plenamente nos conectores personalizados.

Outra opção é que o desenvolvedor assine o conector com um certificado e forneça as informações necessárias para usá-lo sem alterar as configurações de segurança. Para obter mais informações, confira [Sobre conectores de terceiros confiáveis](desktop-trusted-third-party-connectors.md).

## <a name="custom-connectors"></a>Conectores personalizados

Os conectores personalizados não certificados podem variar de pequenas APIs comercialmente críticas a serviços amplos específicos do setor para os quais a Microsoft não lançou um conector. Muitos conectores são distribuídos por fornecedores. Caso precise obter um conector de dados específico, entre em contato com o fornecedor. 

Para usar um conector personalizado não certificado, coloque o arquivo *.pq*, *.pqx*, *.m* ou *.mez* do conector na pasta *\[Documentos]\\Power BI Desktop\\Conectores Personalizados*. Caso a pasta ainda não exista, crie-a.

Ajuste as configurações de segurança da extensão de dados da seguinte maneira:

No Power BI Desktop, selecione **Arquivo** > **Opções e configurações** > **Opções** > **Segurança**.

Em **Extensões de Dados**, selecione **(Não Recomendado) Permitir que qualquer extensão seja carregada sem validação nem aviso**. Selecione **OK** e, em seguida, reinicie o Power BI Desktop. 

![Permitir conectores personalizados não certificados nas opções de Segurança da Extensão de Dados](media/desktop-connector-extensibility/data-extension-security-1.png)

A configuração padrão de segurança da extensão de dados do Power BI Desktop é **(Recomendado) Permitir apenas o carregamento de extensões certificadas pela Microsoft e de terceiros confiáveis**. Com essa configuração, se houver conectores personalizados não certificados no sistema, a caixa de diálogo **Conectores Não Certificados** será exibida na inicialização do Power BI Desktop, listando os conectores que não podem ser carregados com segurança.

![Caixa de diálogo Conectores Não Certificados](media/desktop-connector-extensibility/data-extension-security-2.png)

Para resolver o erro, altere a configuração de segurança **Extensões de Dados** ou remova os conectores não certificados da pasta *Conectores Personalizados*.

## <a name="certified-connectors"></a>Conectores certificados

Um subconjunto limitado de extensões de dados é considerado *certificado*. Embora a Microsoft distribua os conectores, ela não é responsável por seu desempenho ou função contínua. O desenvolvedor de terceiros que criou o conector é responsável pela manutenção e pelo suporte dele. 

No Power BI Desktop, os conectores de terceiros certificados são exibidos na lista da caixa de diálogo **Obter Dados**, juntamente com os conectores genéricos e comuns. Você não precisa ajustar as configurações de segurança para usar os conectores certificados.

Caso deseje obter a certificação de um conector personalizado, solicite ao fornecedor que entre em contato pelo email dataconnectors@microsoft.com.
