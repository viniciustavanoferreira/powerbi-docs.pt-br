---
title: Solução de problemas do gateway do Power BI (modo pessoal)
description: Solução de problemas do gateway do Power BI (modo pessoal)
author: arthiriyer
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: troubleshooting
ms.date: 5/06/2019
ms.author: arthii
LocalizationGroup: Troubleshooting
ms.openlocfilehash: da21acf2c37136b70bdb7ab70060422655ac879c
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83323863"
---
# <a name="troubleshooting-power-bi-gateway-personal-mode"></a>Solução de problemas do gateway do Power BI (modo pessoal)

[!INCLUDE [gateway-rewrite](../includes/gateway-rewrite.md)]

As seções a seguir mostram alguns problemas comuns que você poderá ter ao usar o gateway de dados local (modo pessoal) do Power BI.

## <a name="update-to-the-latest-version"></a>Atualizar para a versão mais recente

A versão atual do gateway para uso pessoal é o gateway de dados local (modo pessoal). Atualize sua instalação para usar essa versão.

Muitos problemas podem surgir quando a versão do gateway está desatualizada. É uma boa prática geral ter certeza que você está com a versão mais recente. Se você não tiver atualizado o gateway por um mês ou mais, considere instalar a versão mais recente do gateway. Em seguida, veja se você pode reproduzir o problema.

## <a name="installation"></a>Instalação
**O gateway (modo pessoal) opera em versões de 64 bits:** Se o seu computador for uma versão de 32 bits, você não poderá instalar o gateway (modo pessoal). Seu sistema operacional precisa ser da versão de 64 bits. Instale uma versão de 64 bits do Windows ou instale o gateway (modo pessoal) em um computador de 64 bits.

**O Gateway (modo pessoal) falha ao ser instalado como um serviço, mesmo que você seja um administrador local do computador:** A instalação poderá falhar se o usuário estiver no grupo Administrador local do computador, mas a Política de Grupo não permite que o nome de usuário entre como um serviço. Assegure-se de que a Política de Grupo permita que um usuário entre como um serviço. Estamos trabalhando para encontrar uma correção para esse problema. Para obter mais informações, consulte [Adicionar o direito de fazer logon como um serviço a uma conta](https://technet.microsoft.com/library/cc739424.aspx).

**Tempo limite da operação atingido:** Essa mensagem será comum se o computador (computador físico ou VM), no qual o gateway (modo pessoal) está sendo instalado, tiver um processador de núcleo único. Feche todos os aplicativos, desligue todos os processos não essenciais e tente instalar novamente.

**O Gateway de gerenciamento de dados ou o conector de Analysis Services não pode ser instalado no mesmo computador que o gateway (modo pessoal):** Se você já tiver um conector de Analysis Services ou um gateway de gerenciamento de dados instalado, deverá primeiro desinstalar o conector ou o gateway. Em seguida, tente instalar o gateway (modo pessoal).

> [!NOTE]
> Se você tiver algum problema durante a instalação, os logs de instalação poderão fornecer informações para ajudá-lo a resolver o problema. Para obter mais informações, consulte [Logs de instalação](#SetupLogs).
> 
> 

 **Configuração de proxy:** Você poderá encontrar problemas com a configuração do gateway (modo pessoal) se o ambiente precisar usar um proxy. Para saber mais sobre como configurar informações de proxy, consulte [Definir as configurações de proxy para o gateway de dados local](/data-integration/gateway/service-gateway-proxy).

## <a name="schedule-refresh"></a>Agendar atualização
**Erro: As credenciais armazenadas na nuvem estão ausentes.**

Você poderá obter esse erro nas configurações de \<conjunto de dados\> se tiver uma atualização agendada e tiver desinstalado e reinstalado o gateway (modo pessoal). Ao desinstalar um gateway (modo pessoal), as credenciais da fonte de dados de um conjunto de dados que foram configuradas para atualização são removidas do serviço do Power BI.

**Solução:** No Power BI, vá para as configurações de atualização de um conjunto de dados. Em **Gerenciar Fontes de Dados**, para qualquer fonte de dados com um erro, selecione **Editar credenciais**. Em seguida, entre novamente na fonte de dados.

**Erro: As credenciais fornecidas para o conjunto de dados são inválidas. Atualize as credenciais por meio de uma atualização ou no diálogo Configurações de Fonte de Dados para continuar.**

**Solução:** Se você receber uma mensagem de credenciais, isso pode significar:

* Os nomes de usuário e as senhas usados para entrar nas fontes de dados não estão atualizados. No Power BI, vá para as configurações de atualização do conjunto de dados. Em **Gerenciar Fontes de Dados**, selecione **Editar credenciais** para atualizar as credenciais da fonte de dados.
* Os mashups entre uma fonte de nuvem e uma fonte local, em uma única consulta, falharão em ser atualizados no gateway (modo pessoal) se uma das fontes estiver usando o OAuth para autenticação. Um exemplo desse problema é um mashup entre o CRM Online e uma instância do SQL Server local. O mashup falha porque o CRM Online exige o OAuth.
  
  Esse erro é um problema conhecido e está sendo analisado. Para resolver o problema, tenha uma consulta separada para a fonte de nuvem e a fonte local. Em seguida, use uma consulta de mesclagem ou de acréscimo para combiná-las.

**Erro: Fonte de dados sem suporte.**

**Solução:** Se você recebe uma mensagem informando que não há suporte para a fonte de dados em **Agendar Atualização** nas configurações, isso pode significar que: 

* Atualmente, a atualização da fonte de dados no Power BI não é um procedimento compatível. 
* A pasta de trabalho do Excel não contém um modelo de dados, somente os dados de planilha. O Power BI atualmente dá suporte apenas à atualização se a pasta de trabalho do Excel carregada contiver um modelo de dados. Quando você importa dados usando o Power Query no Excel, escolha a opção **Carregar** para carregá-los para um modelo de dados. Essa opção garante que os dados sejam importados em um modelo de dados. 

**Erro: [não é possível combinar dados] &lt;A parte da consulta&gt;/&lt;…&gt;/&lt;…&gt; está acessando fontes de dados com níveis de privacidade que não podem ser usados em conjunto. Recompile esta combinação de dados.**

**Solução:** Esse erro ocorre devido a restrições no nível de privacidade e aos tipos de fonte de dados que estão sendo usados.

**Erro: Erro na fonte de dados: não é possível converter o valor "\[Table\]" no tipo Tabela.**

**Solução:** Esse erro ocorre devido a restrições no nível de privacidade e aos tipos de fonte de dados que estão sendo usados.

**Erro: Não há espaço suficiente para esta linha.**

**Solução:** Esse erro ocorrerá se você tiver uma única linha com um tamanho maior que 4 MB. Encontre a linha da fonte de dados e tente filtrá-la ou reduzir seu tamanho.

## <a name="data-sources"></a>Fontes de dados
**Provedor de dados ausente:** O gateway (modo pessoal) opera somente em versões de 64 bits. Ele exige a instalação de uma versão de 64 bits dos provedores de dados no mesmo computador em que o gateway (modo pessoal) está instalado. Por exemplo, se a fonte de dados no conjunto de dados for o Microsoft Access, será necessário instalar o provedor ACE de 64 bits no mesmo computador em que o gateway (modo pessoal) está instalado. 

>[!NOTE]
>Se você tiver o Excel com a versão de 32 bits, não será possível instalar um provedor ACE com a versão de 64 bits no mesmo computador.

**Não há suporte à autenticação do Windows para o banco de dados do Access:** Atualmente, o Power BI dá suporte apenas à autenticação anônima para o banco de dados do Access.

**Erro: Erro de início de sessão quando você insere as credenciais para uma fonte de dados:** Se você receber um erro como este quando inserir as credenciais do Windows para uma fonte de dados: 

  ![Mensagem de erro de credencial do Windows](media/service-admin-troubleshooting-power-bi-personal-gateway/pbi_pg_credentialserror.jpg.png)

Talvez você ainda esteja em uma versão mais antiga do gateway (modo pessoal). 

**Solução:** Para obter mais informações, consulte [Instalar a versão mais recente do gateway do Power BI (modo pessoal)](https://powerbi.microsoft.com/gateway/).

**Erro: Erro de conexão quando você seleciona a autenticação do Windows para uma fonte de dados usando o ACE OLEDB:** Se você receber o seguinte erro ao inserir as credenciais de fonte de dados para uma fonte de dados usando um provedor de ACE OLEDB:

![Mensagem de erro de credencial da fonte de dados](media/service-admin-troubleshooting-power-bi-personal-gateway/aceoledberror.png)

Atualmente, o Power BI não dá suporte à autenticação do Windows para uma fonte de dados usando o provedor ACE OLEDB.

**Solução:** Para solucionar esse erro, você pode selecionar **Autenticação anônima**. Para o provedor ACE OLEDB herdado, as credenciais Anônimas são equivalentes às credenciais do Windows.

## <a name="tile-refresh"></a>Atualização de bloco
Se você receber um erro quando os blocos do painel forem atualizados, consulte [Como solucionar problemas de erros de bloco](refresh-troubleshooting-tile-errors.md).

## <a name="tools-for-troubleshooting"></a>Ferramentas para solução de problemas
### <a name="refresh-history"></a>Histórico de atualização
O **Histórico de Atualização** pode ajudá-lo a ver quais erros ocorreram, além de fornecer dados úteis se você precisa criar uma solicitação de suporte. É possível exibir atualizações agendadas e sob demanda. Aqui você pode acessar o **Histórico de atualização**.

1. No painel de navegação do Power BI, em **Conjuntos de dados**, selecione um conjunto de dados. Abra o menu e selecione **Agendar atualização**.

   ![Selecione Agendar Atualização](media/service-admin-troubleshooting-power-bi-personal-gateway/scheduled-refresh.png)
1. Em **Configurações para...** , selecione **Histórico de Atualização**. 

   ![Selecionar Histórico de Atualização](media/service-admin-troubleshooting-power-bi-personal-gateway/scheduled-refresh-2.png)
   
   ![Informações do histórico de atualização](media/service-admin-troubleshooting-power-bi-personal-gateway/refresh-history.png)

### <a name="event-logs"></a>Logs de eventos
Vários logs de eventos podem fornecer informações. Os dois primeiros, **gateway de gerenciamento de dados** e **PowerBIGateway**, estarão presentes se você for um administrador no computador. Se não for um administrador e estiver usando o gateway de dados (modo pessoal), você verá as entradas de log dentro do log de **Aplicativo**.

O **Gateway do Gerenciamento de Dados** e os logs do **PowerBIGateway** estiverem presentes nos **logs de aplicativos e serviços**.

![Gateway do Gerenciamento de Dados e logs do PowerBIGateway](media/service-admin-troubleshooting-power-bi-personal-gateway/event-logs.png)

### <a name="fiddler-trace"></a>Rastreamento do Fiddler
O [Fiddler](https://www.telerik.com/fiddler) é uma ferramenta gratuita da Telerik que monitora o tráfego HTTP. Você pode ver a comunicação com o serviço do Power BI do computador cliente. Essa comunicação pode mostrar erros e outras informações relacionadas.

![Rastreamento do Fiddler](media/service-admin-troubleshooting-power-bi-personal-gateway/fiddler.png)

<a name="SetupLogs"></a>

### <a name="setup-logs"></a>Logs de instalação
Em caso de falha na instalação do gateway (modo pessoal), você verá um link para exibir o log de instalação. O log de instalação pode mostrar detalhes sobre a falha. Esses logs são os logs de instalação do Windows, também conhecidos como logs do MSI. Eles podem ser bastante complexos e de difícil leitura. Normalmente, o erro resultante é mostrado na parte inferior, mas não é comum determinar a causa do erro. Pode ser resultado de erros em um log diferente. Também pode ser resultado de um erro acima no log.

![Link para o log de instalação](media/service-admin-troubleshooting-power-bi-personal-gateway/setup-log.png)

Como alternativa, você pode ir para a pasta temporária (%temp%) e procurar por arquivos que comecem com *Power\_BI\_* .

> [!NOTE]
> Ir para %temp% poderá levá-lo a uma subpasta de Temp. Os arquivos do *Power\_BI\_* estarão na raiz do diretório Temp. Talvez seja necessário subir um nível ou dois.
> 
> 

![Pasta Temp](media/service-admin-troubleshooting-power-bi-personal-gateway/setup-logs2.png)

## <a name="next-steps"></a>Próximas etapas
- [Definir as configurações de proxy do gateway de dados local](/data-integration/gateway/service-gateway-proxy)- [para a atualização de dados](refresh-data.md)  
- [Gateway do Power BI – Pessoal](service-gateway-personal-mode.md)  
- [Solução de problemas de erros de bloco](refresh-troubleshooting-tile-errors.md)  
- [Solução de problemas do gateway de dados local](service-gateway-onprem-tshoot.md) 
 
Mais perguntas? Experimente perguntar à [Comunidade do Power BI](https://community.powerbi.com/).
