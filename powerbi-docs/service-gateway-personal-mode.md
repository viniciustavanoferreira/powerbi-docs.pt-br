---
title: Usar gateways pessoais no Power BI
description: Fornece informações sobre o gateway de dados local (modo pessoal) para o Power BI que os indivíduos podem usar para se conectar a dados locais.
author: arthiriyer
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 07/15/2019
ms.author: arthii
LocalizationGroup: Gateways
ms.openlocfilehash: ee93635abdff63c98eeaaca24640ac229a4dc97c
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/05/2020
ms.locfileid: "74699258"
---
# <a name="use-personal-gateways-in-power-bi"></a>Usar gateways pessoais no Power BI

[!INCLUDE [gateway-rewrite](includes/gateway-rewrite.md)]

O gateway de dados local (modo pessoal) é uma versão do gateway de dados local que funciona apenas com o Power BI. É possível usar um gateway pessoal para instalar um gateway em seu próprio computador e obter acesso aos dados locais.

> [!NOTE]
> Você pode ter apena sum gateway de modo pessoal em execução para cada usuário do Power BI. Se você instalar outro gateway de modo pessoal para o mesmo usuário, mesmo que em um computador diferente, a instalação mais recente substituirá a instalação anterior existente.

## <a name="on-premises-data-gateway-vs-on-premises-data-gateway-personal-mode"></a>Gateway de dados local versus gateway de dados local (modo pessoal)

A tabela a seguir descreve as diferenças entre um gateway de dados local e um gateway de dados local (modo pessoal).

|   |Gateway de dados local | Gateway de dados local (modo pessoal) |
| ---- | ---- | ---- |
|Serviços de nuvem compatíveis |Power BI, PowerApps, Aplicativos Lógicos do Azure, Power Automate, Azure Analysis Services, fluxos de dados |Power BI |
|Execuções |Conforme configurado pelos usuários que têm acesso ao gateway |Como você para a autenticação do Windows e conforme configurado por você para outros tipos de autenticação |
|É possível instalar somente como administrador do computador |Sim |Não |
|Gateway centralizado e gerenciamento de fonte de dados |Sim |Não |
|Importar dados e agendar atualização |Sim |Sim |
|Suporte a DirectQuery |Sim |Não |
|Suporte do LiveConnect para o Analysis Services |Sim |Não |

## <a name="install-the-on-premises-data-gateway-personal-mode"></a>Instalar o gateway de dados local (modo pessoal)

Para instalar o gateway de dados local (modo pessoal):

1. [Baixe o gateway de dados local](https://go.microsoft.com/fwlink/?LinkId=820925&clcid=0x409).

2. No instalador, selecione o gateway de dados local (modo pessoal) e, em seguida, selecione **Avançar**.

   ![Selecione o gateway de dados local (modo pessoal)](media/service-gateway-personal-mode/personal-gateway-select.png)

Os arquivos do gateway são instalados em _"%localappdata%\Microsoft\On-premises data gateway (personal mode)_ . Após a instalação ser concluída com êxito e você entrar, você verá a seguinte tela.

![O gateway de dados local (modo pessoal) foi bem-sucedido](media/service-gateway-personal-mode/personal-gateway-complete.png)

## <a name="use-fast-combine-with-the-personal-gateway"></a>Usar a Combinação Rápida com o gateway pessoal

A Combinação Rápida em um gateway pessoal ajuda a ignorar níveis de privacidade especificados durante a execução de consultas. Para habilitar a Combinação Rápida para trabalhar com o gateway de dados local (modo pessoal):

1. Usando o Explorador de Arquivos, abra o arquivo a seguir:

   `%localappdata%\Microsoft\On-premises data gateway (personal mode)\Microsoft.PowerBI.DataMovement.Pipeline.GatewayCore.dll.config`

2. Na parte inferior do arquivo, adicione o seguinte texto:

    ```xml
    <setting name="EnableFastCombine" serializeAs="String">
       <value>true</value>
    </setting>
    ```

3. Após a conclusão, a configuração entrará em vigor em aproximadamente um minuto. Para verificar se ela está funcionando corretamente, tente fazer uma atualização sob demanda no serviço do Power BI para confirmar se a Combinação Rápida está funcionando.

## <a name="frequently-asked-questions-faq"></a>Perguntas frequentes

**Pergunta:** É possível executar o gateway de dados local (modo pessoal) lado a lado com o gateway de dados local (antes conhecido como a versão Enterprise do gateway)?
  
**Resposta:** Sim, os dois gateways podem ser executados simultaneamente.

**Pergunta:** É possível executar o gateway de dados local (modo pessoal) como serviço?
  
**Resposta:** Não. O gateway de dados local (modo pessoal) só pode ser executado como aplicativo. Se precisar executar o gateway como serviço ou no modo admin, você precisará considerar o [gateway de dados local](/data-integration/gateway/service-gateway-onprem) (anteriormente conhecido como gateway Corporativo).

**Pergunta:** Com que frequência o gateway de dados local (modo pessoal) é atualizado?
  
**Resposta:** Planejamos atualizar o gateway pessoal mensalmente.

**Pergunta:** Por que estou solicitado a atualizar minhas credenciais?
  
**Resposta:** Muitas situações podem acionar uma solicitação de credenciais. A mais comum é você ter reinstalado o gateway de dados local (modo pessoal) em um computador diferente de seu gateway do Power BI – pessoal. Também pode haver um problema na fonte de dados e o Power BI não conseguiu realizar uma conexão de teste ou ocorreu um erro de tempo limite ou do sistema. Para atualizar suas credenciais no serviço do Power BI, selecione o ícone de engrenagem e **Configurações** > **Conjuntos de dados**. Localize o conjunto de dados em questão e selecione **Credenciais da fonte de dados**.

**Pergunta:** Por quanto tempo meu gateway pessoal anterior ficará offline durante a atualização?
  
**Resposta:** Atualizar o gateway pessoal para a nova versão leva apenas alguns minutos.

**Pergunta:** Estou usando scripts de R e Python. Eles são compatíveis?
  
**Resposta:** Os scripts de R e Python são compatíveis com o modo pessoal.

## <a name="next-steps"></a>Próximas etapas

* [Definindo as configurações de proxy do gateway de dados locais](/data-integration/gateway/service-gateway-proxy)  

Mais perguntas? Experimente a [Comunidade do Power BI](https://community.powerbi.com/).
