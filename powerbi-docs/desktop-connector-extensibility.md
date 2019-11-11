---
title: Extensibilidade do conector no Power BI
description: Funcionalidades de extensibilidade do conector, recursos, configurações de segurança e conectores certificados
author: cpopell
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/22/2019
ms.author: gepopell
LocalizationGroup: Connect to data
ms.openlocfilehash: e493e4a41e7b357a23677c1c50f654dbee51e0ca
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/09/2019
ms.locfileid: "73878412"
---
# <a name="connector-extensibility-in-power-bi"></a>Extensibilidade do conector no Power BI

No Power BI, clientes e desenvolvedores podem estender as fontes de dados às quais se conectam de muitas maneiras. Eles usam conectores existentes e fontes de dados genéricas (como ODBC, OData, Oledb, Web, CSV, XML, JSON). Ou os desenvolvedores criam extensões de dados, denominadas **Conectores Personalizados**, e as tornam **Conectores Certificados**.

No momento, habilite **Conectores Personalizados** usando um menu que permite que você controle com segurança o nível do código personalizado cuja execução você deseja permitir em seu sistema. É possível escolher todos os conectores ou apenas conectores certificados e distribuídos pela Microsoft na caixa de diálogo **Obter Dados**.

## <a name="custom-connectors"></a>Conectores personalizados

Os **Conectores Personalizados** podem incluir uma ampla gama de possibilidades, que variam de pequenas APIs essenciais para os negócios até grandes serviços específicos do setor para os quais a Microsoft ainda não lançou um conector. Muitos conectores são distribuídos pelo fornecedor. Se você precisar de um conector de dados específico, contate um fornecedor.

Para usar um **Conector Personalizado**, coloque-o na pasta *\[Documentos\\Power BI Desktop\\Conectores Personalizados* e ajuste as configurações de segurança, conforme descrito na seção a seguir.

Você não precisa ajustar as configurações de segurança para usar **Conectores Certificados**.

## <a name="data-extension-security"></a>Segurança da extensão de dados

Para alterar as configurações de segurança da extensão de dados, em **Power BI Desktop** selecione **Arquivo > Opções e configurações > Opções > Segurança**.

![Controlar se você deseja carregar os conectores personalizados com opções de Segurança da Extensão de Dados](media/desktop-connector-extensibility/data-extension-security-1.png)

Em **Extensões de Dados**, você pode selecionar dois níveis de segurança:

* (Recomendado) Permitir o carregamento somente de extensões certificadas
* (Não recomendado) Permitir o carregamento de qualquer extensão sem aviso

Se planeja usar **Conectores Personalizados** ou conectores que você ou terceiros desenvolveram, selecione **“(Não recomendado) Permitir o carregamento de qualquer extensão sem aviso”** . Não recomendamos essa configuração de segurança, a menos que você confie completamente em seus Conectores Personalizados. Porque o código lá pode lidar com credenciais, incluindo seu envio por HTTP, e ignorar níveis de privacidade.

Na configuração de segurança **"(Recomendado)"** , se houver conectores personalizados em seu sistema, você receberá o erro “O seguinte conector não foi certificado e não foi possível verificar se é seguro usar” seguido por uma lista de conectores que não podem ser carregados com segurança.

![Uma caixa de diálogo descreve os Conectores Personalizados que não podem ser carregados por causa das configurações de segurança, nesse caso, o TripPin](media/desktop-connector-extensibility/data-extension-security-2.png)

Para resolver o erro sem alterar a segurança, remova os conectores não assinados da pasta 'Conectores Personalizados'.

Para resolver o erro e usar esses conectores, altere suas configurações de segurança para **“(Não recomendado) Permitir o carregamento de qualquer extensão sem aviso”** , conforme descrito anteriormente. Em seguida, reinicie o **Power BI Desktop**.

## <a name="certified-connectors"></a>Conectores certificados

Um subconjunto limitado de extensões de dados é considerado **Certificado**. Acesse os conectores certificados na caixa de diálogo **Obter Dados**. Mas, o desenvolvedor de terceiros que criou o conector é responsável por sua manutenção e suporte. Embora a Microsoft distribua os conectores, ela não é responsável por seu desempenho ou função contínua.

Se você deseja que um conector personalizado seja certificado, solicite que seu fornecedor contate dataconnectors@microsoft.com.
