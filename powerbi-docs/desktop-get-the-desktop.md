---
title: Obter o Power BI Desktop
description: Baixar e instalar o Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/29/2020
ms.author: davidi
LocalizationGroup: Get started
ms.openlocfilehash: 6c2c41221e4a199d6a5d3a800f3820746ef7389a
ms.sourcegitcommit: 8b300151b5c59bc66bfef1ca2ad08593d4d05d6a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2020
ms.locfileid: "76888352"
---
# <a name="get-power-bi-desktop"></a>Obter o Power BI Desktop
O Power BI Desktop permite a criação de consultas, modelos e relatórios avançados que visualizam dados. Com o Power BI Desktop, você pode criar modelos de dados, criar relatórios e compartilhar seu trabalho publicando-o no serviço do Power BI. O Power BI Desktop é um download gratuito.

É possível obter o Power BI Desktop de duas maneiras, e cada uma delas é descrita nas seções a seguir:

* [Instalação como aplicativo da Microsoft Store](#install-as-an-app-from-the-microsoft-store).
* [Download direto, como um executável baixado e instalado em seu computador](#download-power-bi-desktop-directly).

Qualquer uma dessas abordagens instala a versão mais recente do Power BI Desktop no seu computador, mas há algumas diferenças dignas de nota, que serão descritas nas seções a seguir.

## <a name="install-as-an-app-from-the-microsoft-store"></a>Instalação como aplicativo da Microsoft Store
Há algumas maneiras de acessar a versão mais recente do Power BI Desktop na Microsoft Store. 

1. Use uma das opções a seguir para abrir a página do **Power BI Desktop** na Microsoft Store:

   - Abra um navegador e vá diretamente para a página do [Power BI Desktop](https://aka.ms/pbidesktopstore) na Microsoft Store.

    - No [serviço do Power BI](https://docs.microsoft.com/power-bi/service-get-started), selecione o ícone **Download** no canto superior direito e, em seguida, selecione **Power BI Desktop**.

      ![Baixar o Power BI Desktop do Serviço do Power BI](media/desktop-get-the-desktop/getpbid_downloads.png)

   - Acesse a [página de produto do Power BI Desktop](https://powerbi.microsoft.com/desktop/) e, em seguida, selecione **Baixar gratuitamente**.
  
2. Após chegar à página do **Power BI Desktop** na Microsoft Store, selecione **Instalar**.

     ![Obter o Power BI Desktop da Microsoft Store](media/desktop-get-the-desktop/getpbid_04.png)

Há algumas vantagens em obter o Power BI Desktop na Microsoft Store:

* **Atualizações automáticas**: assim que disponível, o Windows baixa a versão mais recente automaticamente em segundo plano, de modo que a sua versão permaneça sempre atualizada.
* **Downloads menores**: a Microsoft Store garante que apenas os componentes alterados em cada atualização sejam baixados em seu computador, o que resulta em downloads menores para cada atualização.
* **O privilégio de administrador não é necessário**: quando você baixa o pacote diretamente e o instala, é necessário ser administrador para que a instalação seja concluída com êxito. Se você obtiver o Power BI Desktop na Microsoft Store, o privilégio de administrador *não* será necessário.
* **Distribuição de TI habilitada**: por meio da Microsoft Store para Empresas, você pode implantar mais facilmente, ou *distribuir* o Power BI Desktop para todos em sua organização

* **Detecção de idioma**: a versão da Microsoft Store inclui todos os idiomas com suporte e verifica qual deles está sendo usado no computador toda vez que ele é iniciado. Esse suporte para idiomas também afeta a localização dos modelos criados no Power BI Desktop. Por exemplo, hierarquias de data internas correspondem ao idioma que o Power BI Desktop está usando quando o arquivo .pbix é criado.

As seguintes considerações e limitações se aplicam quando você instala o Power BI Desktop da Microsoft Store:

* Se o conector SAP for utilizado, poderá ser necessário mover os arquivos do driver do SAP para a pasta *Windows\System32*.
* Instalar o Power BI Desktop da Microsoft Store não copia as configurações do usuário da versão do .exe. Talvez seja necessário se reconectar às suas fontes de dados recentes e inserir novamente as credenciais de sua fonte de dados. 

> [!NOTE]
> A versão do Servidor de Relatórios do Power BI do Power BI Desktop é uma instalação separada e diferente das versões discutidas neste artigo. Para saber mais sobre a versão do Servidor de Relatórios do Power BI Desktop, consulte [Criar um relatório do Power BI para o Servidor de Relatórios do Power BI](report-server/quickstart-create-powerbi-report.md).
> 
> 

## <a name="download-power-bi-desktop-directly"></a>Baixar o Power BI Desktop diretamente
  
  Para baixar o executável do Power BI Desktop no Centro de Download, selecione **Baixar** na [página do Centro de Download](https://www.microsoft.com/download/details.aspx?id=58494). Em seguida, especifique um arquivo de instalação de 32 bits ou 64 bits para baixar.

  ![Especificar o arquivo de instalação do Power BI Desktop](media/desktop-get-the-desktop/download-desktop-exe.png)

### <a name="install-power-bi-desktop-after-downloading-it"></a>Instalar o Power BI Desktop após baixá-lo
Será solicitado que você execute o arquivo de instalação após terminar de baixá-lo.

Na versão de julho de 2019 e versões posteriores, o Power BI Desktop é fornecido como um pacote de instalação .exe único que contém todos os idiomas com suporte, com um arquivo .exe separado para as versões de 32 e de 64 bits. Desde setembro de 2019, os pacotes .msi foram descontinuados, exigindo o executável .exe para instalação. Essa abordagem torna a distribuição, as atualizações e a instalação (especialmente para administradores) muito mais fáceis e práticas. Você também pode usar parâmetros de linha de comando para personalizar o processo de instalação, conforme descrito em [Como usar opções de linha de comando durante a instalação](#using-command-line-options-during-installation).

Após você iniciar o pacote de instalação, o Power BI Desktop é instalado como um aplicativo e é executado na área de trabalho.

![Executar a instalação do Power BI Desktop](media/desktop-get-the-desktop/designer_gsg_install.png)

> [!NOTE]
> A instalação da versão baixada (MSI), que foi preterida, e da versão do Microsoft Store do Power BI Desktop no mesmo computador (às vezes conhecida como instalação *lado a lado*) não tem suporte. Desinstale manualmente o Power BI Desktop antes de baixá-lo por meio da Microsoft Store.
> 

## <a name="using-power-bi-desktop"></a>Usando o Power BI Desktop
Ao iniciar o Power BI Desktop, uma tela de Boas-vindas será exibida.

![Tela de Boas-vindas do Power BI Desktop](media/desktop-get-the-desktop/getpbid_05.png)

Se você estiver usando o Power BI Desktop pela primeira vez (ou seja, a instalação não é uma atualização), será solicitado que preencha um formulário ou entre no serviço do Power BI antes de continuar.

Daí, você pode começar a criar relatórios ou modelos de dados e compartilhá-los com outros usuários no serviço do Power BI. Confira a seção [Próximas etapas](#next-steps) para obter links para guias para ajudá-lo a começar a usar o Power BI Desktop.

## <a name="minimum-requirements"></a>Requisitos mínimos
A lista a seguir fornece os requisitos mínimos para executar o Power BI Desktop:

* Windows 7 / Windows Server 2008 R2 ou posterior
* .NET 4.5
* Internet Explorer 10 ou posterior
* Memória (RAM): ao menos 1 GB disponível; recomendável 1,5 GB ou mais.
* Exibição: recomendável pelo menos 1440 x 900 ou 1600 x 900 (16:9). Resoluções mais baixas, como 1024 x 768 ou 1280 x 800 não são recomendadas, pois determinados controles (como fechar a tela de inicialização) são exibidos além destas resoluções.
* Configurações de exibição do Windows: se as configurações de exibição forem definidas para alterar o tamanho do texto, dos aplicativos e de outros itens para mais de 100%, talvez você não consiga ver algumas caixas de diálogo com que precisa interagir para continuar usando o Power BI Desktop. Caso tenha esse problema, verifique as configurações de exibição no Windows acessando **Configurações** > **Sistema** > **Exibição** e use o controle deslizante para retornar as configurações de exibição para 100%.
* CPU: recomendável processador x86 de 32 ou 64 bits de 1 GHz (giga-hertz) ou mais rápido.

## <a name="considerations-and-limitations"></a>Considerações e limitações

Queremos que a sua experiência com o Power BI Desktop seja incrível. Como você pode vir a ter problemas com o Power BI Desktop, esta seção apresenta soluções ou sugestões para solucionar esses problemas. 

### <a name="using-command-line-options-during-installation"></a>Como usar opções de linha de comando durante a instalação 

Ao instalar o Power BI Desktop, você pode definir propriedades e opções com opções de linha de comando. Essas configurações são especialmente úteis para administradores que gerenciam ou facilitam a instalação de Power BI Desktop entre organizações. Essas opções se aplicam a instalações .msi e .exe. 


|Opção de linha de comando  |Comportamento  |
|---------|---------|
|-q, -quiet, -s, -silent     |Instalação silenciosa         |
|-passive     |Mostrar apenas a barra de progresso durante a instalação         |
|-norestart     |Suprimir o requisito de reinicialização do computador         |
|-forcerestart     |Reiniciar o computador sem um prompt após a instalação         |
|-promptrestart     |Avisar o usuário se a reinicialização do computador for necessária (padrão)         |
|-l<>, -log<>     |Registrar a instalação em um arquivo específico, com o arquivo especificado em <>         |
|-uninstall     |Desinstalar o Power BI Desktop         |
|-repair     |Reparar a instalação (ou instalar, se ela não estiver instalada no momento)         |
|-package, -update     |Instalar o Power BI Desktop (padrão, desde que -uninstall ou -repair não estejam especificados)         |

Você também pode usar os seguintes parâmetros de sintaxe, que são especificados com uma sintaxe *property = value*:

|Parâmetro  |Significado  |
|---------|---------|
|ACCEPT_EULA     |Exige o valor 1 para aceitar automaticamente o EULA         |
|ENABLECXP     |O valor 1 é para inscrição no programa de experiência do cliente, que captura telemetria sobre uso do produto         |
|INSTALLDESKTOPSHORTCUT     |Um valor 1 adiciona um atalho à Área de Trabalho         |
|INSTALLLOCATION     |Caminho do arquivo onde você o quer instalado         |
|LANGUAGE     |O código de localidade, por exemplo, en-US, de-DE, pt-BR, para forçar o idioma padrão do aplicativo. Se você não especificar o idioma, o Power BI Desktop exibirá o idioma do SO Windows. Você pode alterar essa configuração na caixa de diálogo **Opções**.         |
|REG_SHOWLEADGENDIALOG     |Um valor 0 desabilita mostrando a caixa de diálogo que aparece antes de você entrar no Power BI Desktop.         |
|DISABLE_UPDATE_NOTIFICATION     |O valor de 1 desabilita as notificações de atualização.         |


Por exemplo, você pode executar o Power BI Desktop com as seguintes opções e parâmetros para instalar sem qualquer interface do usuário, usando o idioma alemão: 

```-quiet LANG=de-DE ACCEPT_EULA=1```

### <a name="installing-power-bi-desktop-on-remote-machines"></a>Instalando o Power BI Desktop em computadores remotos

Se for implantar o Power BI Desktop para seus usuários com uma ferramenta que exige um arquivo de instalação do Windows (arquivo .msi), você poderá extrair o arquivo .msi do arquivo .exe do instalador do Power BI Desktop. Use uma ferramenta de terceiros, como o WiX Toolset.

> [!NOTE]
> Como um produto de terceiros, as opções da WiX Toolset podem ser alteradas sem prévio aviso. Verifique a documentação da ferramenta para ver as informações mais atualizadas e entre em contato com a lista de endereçamento a usuários para obter ajuda.

1. No computador em que você baixou o instalador do Power BI Desktop, instale a última versão do [WiX Toolset](https://wixtoolset.org/).
2. Abra uma janela de linha de comando como um administrador e navegue até a pasta em que instalou a WiX Toolset.
3. Execute o seguinte comando: 
    
    ```Dark.exe <path to Power BI Desktop installer> -x <output folder>```

    Por exemplo:

    ``` Dark.exe C:\PBIDesktop_x64.exe -x C:\output```

    A pasta de saída contém uma pasta chamada *AttachedContainer*, que inclui os arquivos .msi.


### <a name="issues-when-using-previous-releases-of-power-bi-desktop"></a>Problemas ao usar versões anteriores do Power BI Desktop

Alguns usuários podem encontrar uma mensagem de erro semelhante à seguinte ao usar uma versão desatualizada do Power BI Desktop: 

*Não conseguimos restaurar o banco de dados salvo no modelo* 

A atualização para a versão atual do Power BI Desktop geralmente resolve esse problema.

### <a name="disabling-notifications"></a>Desabilitar as notificações
Recomendamos a atualização para a versão mais recente do Power BI Desktop, a fim de aproveitar os avanços em recursos, desempenho, estabilidade e outras melhorias. Talvez algumas organizações não queiram que os usuários atualizem a cada nova versão. Você pode desabilitar as notificações modificando o Registro com as seguintes etapas:

1. No Editor do Registro, navegue para a chave **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft Power BI Desktop**.
2. Crie uma entrada **REG_DWORD** na chave com o seguinte nome: **DisableUpdateNotification**.
3. Defina o valor da nova entrada como **1**.
4. Reinicie o computador para que a alteração entre em vigor.

### <a name="power-bi-desktop-loads-with-a-partial-screen"></a>O Power BI Desktop é carregado com uma tela parcial

Em certas circunstâncias, incluindo algumas configurações de resolução de tela, alguns usuários poderão ver o Power BI Desktop renderizar o conteúdo com grandes áreas negras. Geralmente, esse problema é resultado de atualizações recentes do sistema operacional que afetaram o modo de renderização dos itens, e não o resultado direto de como o Power BI Desktop apresenta o conteúdo. Siga estas etapas para resolver o problema:

1. Pressione a tecla **Iniciar** e digite a palavra *desfocado* na barra de pesquisa exibida.
2. Na caixa de diálogo exibida, selecione a opção: **Permitir que o Windows corrija aplicativos que estão desfocados.**
3. Reinicie o Power BI Desktop.

Esse problema poderá ser resolvido após o lançamento de atualizações posteriores do Windows. 
 

## <a name="next-steps"></a>Próximas etapas
Depois que você instalar o Power BI Desktop, confira o conteúdo a seguir para ajudá-lo a colocá-lo em funcionamento rapidamente:

* [O que é o Power BI Desktop?](desktop-what-is-desktop.md)
* [Visão geral da Consulta no Power BI Desktop](desktop-query-overview.md)
* [Fontes de dados no Power BI Desktop](desktop-data-sources.md)
* [Conectar-se a dados no Power BI Desktop](desktop-connect-to-data.md)
* [Formatar e combinar dados no Power BI Desktop](desktop-shape-and-combine-data.md)
* [Tarefas comuns de consulta no Power BI Desktop](desktop-common-query-tasks.md)   

