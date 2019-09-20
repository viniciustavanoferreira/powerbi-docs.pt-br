---
title: Obter o Power BI Desktop
description: Baixar e instalar o Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 09/10/2019
ms.author: davidi
LocalizationGroup: Get started
ms.openlocfilehash: e7a96186fe68ed0d70de7a502e81da4f24f4d802
ms.sourcegitcommit: db4fc5da8e65e0a3dc35582d7142a64ad3405de7
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70903608"
---
# <a name="get-power-bi-desktop"></a>Obter o Power BI Desktop
O **Power BI Desktop** permite a criação de consultas, modelos e relatórios avançados que visualizam dados. Com o **Power BI Desktop**, você pode criar modelos de dados, criar relatórios e compartilhar seu trabalho publicando-o no serviço do Power BI.  **Power BI Desktop** é um download gratuito.

É possível obter o **Power BI Desktop** de duas maneiras e cada uma delas é descrita nas seções a seguir:

* **Fazer download** diretamente (um pacote baixado e instalado no computador)
* Instalação como aplicativo da **Microsoft Store**

Qualquer uma dessas abordagens instalarão a versão mais recente do **Power BI Desktop** no seu computador, mas há algumas diferenças dignas de nota, que serão descritas nas seções a seguir.

## <a name="download-power-bi-desktop"></a>Baixe o Power BI Desktop
Para baixar a versão mais recente do **Power BI Desktop**, você pode selecionar o ícone de download no canto superior direito do serviço do Power BI e selecionar **Power BI Desktop**.

![Baixar a versão mais recente do Power BI Desktop](media/desktop-get-the-desktop/getpbid_downloads.png)

Você também pode baixar a versão mais recente do Power BI Desktop da seguinte página de download:

* [**Download do Power BI Desktop** (ambas as versões de 32 e 64 bits)](https://powerbi.microsoft.com/desktop).
  
  [![Baixar a versão mais recente do Power BI Desktop](media/service-admin-power-bi-security/PBI_Security_01.png)](https://powerbi.microsoft.com/desktop)

Independentemente de qual modo você optar por baixar, quando o **Power BI Desktop** for baixado, você será solicitado a executar o arquivo de instalação:

![Executar o arquivo de instalação do Power BI Desktop](media/desktop-get-the-desktop/download-desktop-exe.png)

Começando na versão de julho de 2019, o **Power BI Desktop** é fornecido como um pacote de instalação .exe único que contém todos os idiomas compatíveis. Há arquivos separados para as versões de 32 e 64 bits. Desde setembro de 2019, os pacotes .msi foram descontinuados, exigindo o executável .exe para instalação. Essa abordagem torna a distribuição, as atualizações e a instalação (especialmente para administradores) muito mais fáceis e práticas. Você também pode usar parâmetros de linha de comando para personalizar o processo de instalação, conforme descrito na seção [como usar opções de linha de comando durante a instalação](#using-command-line-options-during-installation) posteriormente neste artigo.

Após você iniciar o pacote de instalação, o **Power BI Desktop** é instalado como um aplicativo e executado na área de trabalho.

![O aplicativo do Power BI Desktop é executado na área de trabalho](media/desktop-get-the-desktop/designer_gsg_install.png)

> [!NOTE]
> A instalação da versão baixada (MSI) e a versão do **Microsoft Store** do **Power BI Desktop** no mesmo computador (às vezes conhecida como instalação *lado a lado*) não é compatível.
> 
> 

## <a name="install-as-an-app-from-the-microsoft-store"></a>Instalação como aplicativo da Microsoft Store
Também é possível obter o **Power BI Desktop** na Microsoft Store, por meio do link a seguir:

* [Instale o**Power BI Desktop** da **Microsoft Store**](http://aka.ms/pbidesktopstore)

  ![Obter o Power BI Desktop da Microsoft Store](media/desktop-get-the-desktop/getpbid_04.png)

Há algumas vantagens em obter o **Power BI Desktop** na Microsoft Store:

* **Atualizações automáticas** – assim que disponível, o Windows baixa a versão mais recente automaticamente em segundo plano, de modo que a sua versão permaneça sempre atualizada.
* **Downloads menores**: a **Microsoft Store** garante que apenas os componentes alterados em cada atualização sejam baixados em seu computador, o que resulta em downloads menores para cada atualização.
* **O privilégio de administrador não é necessário** – quando você baixa o pacote diretamente e o instala, é necessário ser administrador para que a instalação seja concluída com êxito. Quando você obtém o **Power BI Desktop** na Microsoft Store, o privilégio de administrador *não* é necessário.
* **Disponibilização de TI habilitada**: a versão da **Microsoft Store** pode ser implantada, ou *disponibilizada*, mais facilmente para todos os membros da sua organização e pode disponibilizar o **Power BI Desktop** por meio da **Microsoft Store para Empresas**.
* **Detecção de idioma** – a versão da **Microsoft Store** inclui todos os idiomas com suporte e verifica qual deles está sendo usado no computador toda vez que ele é iniciado. Isso também afeta a localização de modelos criados no **Power BI Desktop**. Por exemplo, hierarquias de datas internas corresponderão ao idioma que o **Power BI Desktop** estava usando quando o arquivo .pbix foi criado.

Há algumas considerações e limitações para instalar o **Power BI Desktop** da Microsoft Store, como:

* Se o conector SAP for utilizado, poderá ser necessário mover os arquivos do driver do SAP para a pasta *Windows\System32*.
* Instalar o **Power BI Desktop** da Microsoft Store não copia as configurações do usuário da versão do .exe. Talvez seja necessário se reconectar às suas fontes de dados recentes e inserir novamente as credenciais de sua fonte de dados. 

> [!NOTE]
> A instalação da versão baixada (MSI) e a versão do **Microsoft Store** do **Power BI Desktop** no mesmo computador (às vezes conhecida como instalação *lado a lado*) não é compatível. Você deve desinstalar manualmente o **Power BI Desktop** antes de fazer download da **Microsoft Store**
> 
> [!NOTE]
> A versão do Servidor de Relatórios do Power BI do **Power BI Desktop** é uma instalação separada e diferente das versões discutidas neste artigo. Para saber mais sobre a versão do Servidor de Relatórios do **Power BI Desktop**, consulte [Criar um relatório do Power BI para o Servidor de Relatórios do Power BI](report-server/quickstart-create-powerbi-report.md).
> 
> 

## <a name="using-power-bi-desktop"></a>Usando o Power BI Desktop
Ao inicializar o **Power BI Desktop**, uma tela de *Boas-vindas* será exibida.

![Tela de Boas-vindas do Power BI Desktop](media/desktop-get-the-desktop/getpbid_05.png)

Se essa for sua primeira vez usando o **Power BI Desktop** (se a instalação não for uma atualização), será solicitado que você preencha um formulário e responda a algumas perguntas ou então que entre no **serviço do Power BI** antes que seja possível continuar.

Daí, você pode começar a criar relatórios ou modelos de dados e compartilhá-los com outros usuários no serviço do Power BI. Confira os links **Obter mais informações** no final deste artigo para links em guias que podem ajudá-lo a começar a usar **Power BI Desktop**.

## <a name="minimum-requirements"></a>Requisitos mínimos
A lista a seguir fornece os requisitos mínimos para executar o **Power BI Desktop**:

* Windows 7 / Windows Server 2008 R2 ou posterior
* .NET 4.5
* Internet Explorer 10 ou posterior
* **Memória (RAM):** ao menos 1 GB disponível; recomendável 1,5 GB ou mais.
* **Vídeo:** recomendável pelo menos 1440 x 900 ou 1600 x 900 (16:9). Resoluções mais baixas, como 1024 x 768 ou 1280 x 800 não são recomendadas, pois determinados controles (como fechar a tela de inicialização) são exibidos além destas resoluções.
* **Configurações de vídeo do Windows:** se as configurações de vídeo forem definidas para alterar o tamanho do texto, dos aplicativos e de outros itens para mais de 100%, talvez você não consiga ver algumas caixas de diálogo que devem ser fechadas ou respondidas para que seja possível continuar usando o **Power BI Desktop**. Caso tenha esse problema, verifique as **Configurações de vídeo** acessando **Configurações > Sistema > Vídeo** no Windows e use o controle deslizante para retornar as configurações de vídeo para 100%.
* **CPU:** recomendável processador x86 ou x64 bits de 1 GHz (gigahertz) ou mais rápido.

## <a name="considerations-and-limitations"></a>Considerações e limitações

Queremos que a sua experiência com o Power BI Desktop seja sempre incrível. Às vezes, você pode ter problemas com o Power BI Desktop, por isso, esta seção apresenta soluções ou sugestões para solucionar esses problemas. 

### <a name="installing-power-bi-desktop-on-remote-machines"></a>Instalando o Power BI Desktop em computadores remotos

Se for implantar o Power BI Desktop para seus usuários com uma ferramenta que exige um arquivo de instalação do Windows (arquivo .msi), você poderá extrair o arquivo .msi do arquivo .exe do instalador do Power BI Desktop. É possível usar ferramentas de terceiros, como a WiX Toolset, para fazer isso.

> [!NOTE]
> Como um produto de terceiros, as opções da WiX Toolset podem ser alteradas sem prévio aviso. Verifique a documentação da ferramenta para ver as informações mais atualizadas e a lista de contatos do usuário para obter ajuda.

* No computador em que você baixou o instalador do Power BI Desktop, baixe e instale a última versão da WiX Toolset no site da WiX em https://wixtoolset.org/.
* Abra uma janela de linha de comando como um administrador e navegue até a pasta em que instalou a WiX Toolset.
* Execute o seguinte comando: 
    
    ```Dark.exe <path to Power BI Desktop installer> -x <output folder>```

    Por exemplo, execute:

    ``` Dark.exe C:\PBIDesktop_x64.exe -x C:\output```

* A pasta de saída conterá uma pasta chamada *AttachedContainer* que inclui os arquivos .msi.




### <a name="using-command-line-options-during-installation"></a>Como usar opções de linha de comando durante a instalação 

Ao instalar o Power BI Desktop, você pode definir propriedades e opções com opções de linha de comando. Isso é especialmente útil para administradores que gerenciam ou facilitam a instalação de Power BI Desktop entre organizações. Essas opções se aplicam a instalações .msi e .exe. 


|Opção de linha de comando  |Comportamento  |
|---------|---------|
|-q, -quiet, -s, -silent     |instalação silenciosa         |
|-passive     |mostrar apenas a barra de progresso durante a instalação         |
|-norestart     |suprimir o requisito de reinicialização do computador         |
|-forcerestart     |reiniciar o computador sem um prompt após a instalação         |
|-promptrestart     |avisar o usuário se a reinicialização do computador for necessária (padrão)         |
|-l<>, -log<>     |registrar a instalação em um arquivo específico, com o arquivo especificado em <>         |
|-uninstall     |desinstalar o Power BI Desktop         |
|-repair     |reparar a instalação (ou instalar, se ela não estiver instalada no momento)         |
|-package, -update     |instalar o Power BI Desktop (padrão, desde que -uninstall ou -repair não estejam especificados)         |

Você também pode usar os seguintes **parâmetros de sintaxe**, que são especificados com uma sintaxe "PROPERTY=VALUE":


|Parâmetro  |Significado  |
|---------|---------|
|ACCEPT_EULA     |Exige o valor 1 para aceitar automaticamente o EULA         |
|ENABLECXP     |O valor 1 é para inscrição no programa de experiência do cliente, que captura telemetria sobre uso do produto         |
|INSTALLDESKTOPSHORTCUT     |O valor 1 adiciona um atalho à Área de Trabalho         |
|INSTALLLOCATION     |Caminho do arquivo onde você o quer instalado         |
|LANGUAGE     |Código de localidade, por exemplo, en-US, de-DE, pr-BR, para forçar o idioma padrão do aplicativo. Se nenhum idioma for especificado, o Power BI Desktop exibirá o idioma do SO Windows. Isso pode ser alterado pelo usuário na caixa de diálogo Opções.         |
|REG_SHOWLEADGENDIALOG     |O valor 0 desabilita mostrando a caixa de diálogo que aparece antes de você entrar no Power BI Desktop         |




Por exemplo, você pode executá-lo com a seguinte sintaxe para instalar sem qualquer interface de usuário, usando o idioma alemão: 

```“-quiet LANG=de-DE ACCEPT_EULA=1”```


### <a name="issues-when-using-previous-releases-of-power-bi-desktop"></a>Problemas ao usar versões anteriores do Power BI Desktop

Alguns usuários encontram um erro semelhante ao seguinte ao usar uma versão desatualizada do **Power BI Desktop**: 

    "We weren't able to restore the saved database to the model" 

A atualização para a versão atual do Power BI Desktop geralmente resolve esse problema.

### <a name="disabling-notifications"></a>Desabilitar as notificações
Recomendamos a atualização para a versão mais recente do Power BI Desktop, a fim de aproveitar os avanços em recursos, desempenho, estabilidade e outras melhorias. Talvez algumas organizações não queiram que os usuários atualizem a cada nova versão. Você pode desabilitar as notificações modificando o Registro com as seguintes etapas:

1. No Editor do Registro, navegue até *HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft Power BI Desktop*
2. Crie uma nova entrada com as seguintes configurações: *REG_DWORD: DisableUpdateNotification*
3. Defina o valor da nova entrada como **1**.

Será necessário reiniciar o computador para que a alteração entre em vigor.

### <a name="power-bi-desktop-loads-with-a-partial-screen"></a>O Power BI Desktop é carregado com uma tela parcial

Em certas circunstâncias, incluindo algumas configurações de resolução de tela, alguns usuários poderão ver o Power BI Desktop renderizar o conteúdo com grandes áreas negras. Geralmente, isso é resultado de atualizações recentes do sistema operacional que afetaram o modo de renderização dos itens, e não o resultado direto de como o Power BI Desktop apresenta o conteúdo. Independentemente disso, grandes áreas negras não são tão interessantes quanto belos visuais, então, para resolver esse problema, execute estas etapas:

1. Pressione a tecla Iniciar e digite a palavra *desfocado* na barra de pesquisa exibida.
2. Na caixa de diálogo exibida, selecione a opção: *Permitir que o Windows corrija aplicativos que estão desfocados.*
3. Reinicie o Power BI Desktop.

Esse problema poderá ser resolvido após o lançamento de atualizações subsequentes do Windows. 
 

## <a name="next-steps"></a>Próximas etapas
Depois que você instalar o **Power BI Desktop**, o conteúdo a seguir poderá ajudá-lo a colocar ele em funcionamento rapidamente:

* [O que é o Power BI Desktop?](desktop-what-is-desktop.md)
* [Visão geral de Consulta com o Power BI Desktop](desktop-query-overview.md)
* [Fontes de dados no Power BI Desktop](desktop-data-sources.md)
* [Conectar-se a dados no Power BI Desktop](desktop-connect-to-data.md)
* [Formatar e combinar dados com o Power BI Desktop](desktop-shape-and-combine-data.md)
* [Tarefas comuns de consulta no Power BI Desktop](desktop-common-query-tasks.md)   

