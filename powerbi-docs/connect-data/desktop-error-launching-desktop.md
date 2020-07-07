---
title: Solucionar problemas ao iniciar o Power BI Desktop
description: Solucionar problemas ao iniciar o Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: troubleshooting
ms.date: 01/14/2020
ms.author: davidi
LocalizationGroup: Troubleshooting
ms.openlocfilehash: ba59a08ee1b50e44af71312a25d77fb67c8fca2d
ms.sourcegitcommit: a453ba52aafa012896f665660df7df7bc117ade5
ms.contentlocale: pt-BR
ms.lasthandoff: 06/27/2020
ms.locfileid: "85485428"
---
# <a name="troubleshoot-opening-power-bi-desktop"></a>Solucionar problemas ao abrir o Power BI Desktop

No Power BI Desktop, os usuários que instalaram e estão executando versões anteriores do *gateway de dados local do Power BI* podem ser impedidos de abrir o Power BI Desktop, devido às restrições de políticas administrativas que o gateway local do Power BI estabeleceu nos pipes nomeados no computador local.

## <a name="resolve-issues-with-the-on-premises-data-gateway-and-power-bi-desktop"></a>Resolver problemas com o Gateway de dados local e o Power BI Desktop

Você tem três opções para resolver o problema associado ao Gateway de dados local e permitir a abertura do Power BI Desktop:

### <a name="resolution-1-install-the-latest-version-of-power-bi-on-premises-data-gateway"></a>Resolução 1: instalar a versão mais recente do Gateway de dados local do Power BI

A versão mais recente do Gateway de dados local do Power BI não coloca restrições de pipe nomeado no computador local e permite que o Power BI Desktop seja aberto corretamente. Se você precisa continuar usando o Gateway de dados local do Power BI, a resolução recomendada será atualizá-lo. Baixe a [versão mais recente do Gateway de dados local do Power BI](https://go.microsoft.com/fwlink/?LinkId=698863). O link é leva você direto ao executável da instalação.

### <a name="resolution-2-uninstall-or-stop-the-power-bi-on-premises-data-gateway-microsoft-service"></a>Resolução 2: desinstalar ou interromper o serviço Microsoft de gateway de dados local do Power BI

Você pode desinstalar o gateway de dados local do Power BI se não precisar mais dele. Ou pode interromper o serviço Microsoft de gateway de dados local do Power BI, que remove a restrição de política e permite a abertura do Power BI Desktop.

### <a name="resolution-3-run-power-bi-desktop-with-administrator-privilege"></a>Resolução 3: executar o Power BI Desktop com privilégios de administrador

Em vez disso, você pode iniciar com êxito Power BI Desktop como administrador, que também permite que o Power BI Desktop seja aberto. Ainda é recomendável que você instale a versão mais recente do gateway de dados local do Power BI, conforme descrito anteriormente.

O Power BI Desktop foi projetado como uma arquitetura multiprocesso, e vários desses processos se comunicam usando pipes nomeados do Windows. Pode haver outros processos que interferem com esses pipes nomeados. O motivo mais comum para essa interferência é a segurança, incluindo situações nas quais o software antivírus ou firewalls podem bloquear os pipes ou redirecionar o tráfego para uma porta específica. Abrir o Power BI Desktop com privilégios de administrador pode resolver esse problema. Se você não puder abrir com privilégios de administrador, peça ao administrador para determinar quais regras de segurança estão impedindo que os pipes nomeados se comuniquem corretamente. Em seguida, inclua o Power BI Desktop e seus respectivos subprocessos nas listas de permissões.

## <a name="resolve-issues-when-connecting-to-sql-server"></a>Solucionar problemas ao conectar-se ao SQL Server

Ao tentar se conectar a um banco de dados do SQL Server, você pode receber uma mensagem de erro semelhante à seguinte:

`"An error happened while reading data from the provider:`\
`'Could not load file or assembly 'System.EnterpriseServices, Version=4.0.0.0, Culture=neutral, PublicKeyToken=xxxxxxxxxxxxx' or one of its dependencies.`\
`Either a required impersonation level was not provided, or the provided impersonation level is invalid. (Exception from HRESULT: 0x80070542)'"`

Geralmente, você pode resolver o problema se abrir o Power BI Desktop como administrador antes de fazer a conexão com o SQL Server.

Depois de abrir o Power BI Desktop como um administrador e estabelecer a conexão, as DLLs necessárias serão registradas corretamente. Depois disso, não será mais necessário abrir o Power BI Desktop como administrador.

## <a name="get-help-with-other-launch-issues"></a>Obter ajuda com outros problemas de inicialização

Fazemos o possível para cobrir o máximo de problemas que ocorrem com o Power BI Desktop. Examinamos regularmente os problemas que podem estar afetando muitos clientes, posteriormente incluindo-os em nossos artigos.

Se o problema ao abrir o Power BI Desktop não estiver associado ao gateway de dados local ou se as resoluções anteriores não funcionarem, envie um incidente de suporte para o *suporte do Power BI*, (<https://support.powerbi.com>) para ajudar você a identificar e resolver o problema.

Se posteriormente você se deparar com outros problemas com Power BI Desktop, ative o rastreamento e coleta de arquivos de log. Os arquivos de log podem ajudar a isolar e identificar o problema. Para ativar o rastreamento, escolha **Arquivo** > **Opções e configurações** > **Opções**, selecione **Diagnóstico** e, em seguida, selecione **Habilitar rastreamento**. O Power BI Desktop deve estar em execução para definir essa opção, mas isso será útil em problemas futuros associados à abertura do Power BI Desktop.
