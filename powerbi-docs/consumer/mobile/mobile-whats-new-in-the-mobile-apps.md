---
title: Novidades em aplicativos móveis para o Power BI
description: Novidades em aplicativos móveis para o Power BI
author: paulinbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 11/12/2019
ms.author: painbar
ms.openlocfilehash: c188f2b00447ff9f97059e81e7945f67e3170c6d
ms.sourcegitcommit: 0d7ad791a2d2bef45d5d60e38e0af4c9fc22187b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/13/2019
ms.locfileid: "74010031"
---
# <a name="whats-new-in-the-mobile-apps-for-power-bi"></a>Novidades em aplicativos móveis para o Power BI
Para informações sobre “Novidades” relacionadas, consulte:

* [Blog da equipe do Power BI para os aplicativos móveis](https://powerbi.microsoft.com/blog/tag/mobile/)
* [Novidades no Power BI Desktop](../../desktop-latest-update.md)  
* [Novidades no serviço do Power BI](../../service-whats-new.md)  

## <a name="october-2019"></a>Outubro de 2019

### <a name="android-support-for-remote-configuration-of-report-server-access-settings"></a>Suporte do Android para configuração remota das definições de acesso do Servidor de Relatório

Adicionamos suporte do Android para configuração remota das definições de acesso do Servidor de Relatório do aplicativo móvel do Power BI. Agora os administradores de TI podem usar a ferramenta de MDM da organização para configurar remotamente essas configurações em dispositivos iOS e Android. Confira [Configurar o acesso do aplicativo móvel do Power BI ao Servidor de Relatório remotamente](https://docs.microsoft.com/power-bi/report-server/configure-powerbi-mobile-apps-remote) para obter detalhes.

### <a name="cross-report-drillthrough"></a>Detalhamento entre relatórios

Neste mês, adicionamos suporte ao detalhamento entre relatórios. Agora você pode tocar em um ponto de dados do qual fazer uma busca detalhada para acessar outros relatórios e páginas de relatório. Quando você faz uma busca detalhada para uma página de destino, o conteúdo nessas páginas é filtrado com base nas configurações do detalhamento.

> [!NOTE]
> O detalhamento entre relatórios só estará disponível se tiver sido habilitado durante a criação do relatório. [Saiba mais sobre o detalhamento entre relatórios](https://docs.microsoft.com/power-bi/desktop-cross-report-drill-through).


### <a name="data-sensitivity-labels"></a>Rótulos de confidencialidade dos dados

Agora você pode ver os rótulos de confidencialidade que os proprietários de conteúdo definiram em relatórios, dashboards, conjuntos de dados e fluxos de dados para classificar a confidencialidade de seus próprios dados. Os rótulos de confidencialidade determinam como o conteúdo pode ser compartilhado com outros usuários. [Saiba mais sobre os rótulos de confidencialidade de dados no Power BI](https://docs.microsoft.com/power-bi/admin/service-security-data-protection-overview).

### <a name="support-for-custom-app-navigation-windows"></a>Suporte para navegação de aplicativo personalizada (Windows)

O suporte para navegação de aplicativo personalizada foi adicionado para dispositivos Windows além do iOS e Android (confira [O que é a nova entrada de setembro](#september-2019)).

## <a name="september-2019"></a>Setembro de 2019

### <a name="support-for-custom-app-navigation-ios-and-android"></a>Suporte para navegação de aplicativo personalizada (iOS e Android)

Adicionamos suporte para navegação de aplicativo personalizada. Agora, quando você abre um aplicativo no Power BI Mobile, a experiência de navegação personalizada criada pelo criador de aplicativos estará disponível. A navegação do aplicativo pode ser organizada por conteúdo e pode incluir novos itens, como links e seções recolhíveis.
Leia mais sobre a [navegação personalizada](https://powerbi.microsoft.com/blog/designing-custom-navigation-for-power-bi-apps-is-now-available/).

## <a name="august-2019"></a>Agosto de 2019

### <a name="introducting-power-bi-mobile-new-look-preview-ios-and-android"></a>Introdução ao novo visual (versão prévia) do Power BI Mobile (iOS e Android)

Atualizamos nosso aplicativo e introduzimos novas experiências, adicionando uma página inicial que fornece acesso rápido ao conteúdo que você usa com mais frequência, bem como novas barras de navegação que proporcionam maneiras fáceis de navegar pelo aplicativo. Com as experiências novas e atualizadas, agora está mais rápido e fácil encontrar o que você precisa e quando precisa.
Uma vez que o novo visual está em versão prévia, você precisará ativá-lo para usufruir dele.
Leia mais sobre o [Novo visual do Power BI Mobile](https://powerbi.microsoft.com/blog/introducing-power-bi-mobile-apps-new-look-preview/).

![Novo visual do Power BI Mobile](./media/mobile-whats-new-in-the-mobile-apps/power-bi-mobile-new-look2.gif)

### <a name="secured-access-with-azure-active-directory-ad-application-proxy-ios-and-android"></a>Acesso seguro com o Proxy do Aplicativo do Azure AD (Active Directory) (iOS e Android)

Firmamos uma parceria com a equipe do Azure Active Directory para integrar os aplicativos para dispositivos móveis do Power BI com o Proxy do Aplicativo do AAD (Azure Active Directory). Com essa configuração, é possível conectar-se ao Servidor de Relatório hospedado nos limites corporativos no aplicativo do Power BI Mobile, sem precisar definir configurações locais complexas. Leia mais em [Integração entre o Power BI Mobile e o Proxy de Aplicativo do Azure AD](https://powerbi.microsoft.com/blog/access-on-prem-report-server-from-your-power-bi-mobile-app-with-azure-active-directory-application-proxy/). Saiba [como configurar o Proxy de Aplicativo do Azure AD e o Power BI](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy-integrate-with-power-bi).

## <a name="july-2019"></a>Julho de 2019

### <a name="report-page-tooltips"></a>Dicas de ferramentas de página de relatório

Dicas de ferramentas de relatório agora são compatíveis ao exibir relatórios em aplicativos móveis. Basta pressionar um visual que tenha uma dica de ferramenta de relatório vinculada a ele e mantê-lo pressionado que a dica será mostrada.  

![Dica de ferramenta de tela de relatório](./media/mobile-whats-new-in-the-mobile-apps/report-canvas-tooltip.png)
 
> [!NOTE]
> As dicas de ferramentas de relatório são compatíveis com dispositivos com mais de 640 pixels de tamanho e visor de 320. Dispositivos menores usam dicas de ferramenta padrão.


## <a name="june-2019"></a>Junho de 2019

### <a name="barcode-scanning-is-now-available-in-android"></a>A verificação de código de barras já está disponível no Android
Agora, você pode usar o aplicativo Power B no Android (celular e tablet) para digitalizar códigos de barras impressos em produtos ou prateleiras da loja para exibir relatórios do Power BI relacionados, filtrados pelo valor digitalizado. Mais sobre como [filtrar seus dados com códigos de barras](mobile-apps-scan-barcode-iphone.md).

### <a name="supporting-pbix-reports-hosted-in-pbi-rs-over-adfs-configuration-ios-android"></a>Suporte a relatórios de PBIX hospedados no PBI-RS em detrimento da configuração do ADFS (iOS, Android)

Agora os relatórios do Power BI (PBIX) hospedados no PBI-RS com configuração de ADFS também podem ser acessados dos aplicativos móveis do Power BI.

## <a name="may-2019"></a>Maio de 2019

### <a name="siri-shortcuts-support-ios"></a>Suporte para Atalhos da Siri (iOS)
Os usuários podem criar Atalhos da Siri para seus relatórios e dashboards do Power BI e, em seguida, abri-los diretamente da interface de voz da Siri. [Leia como usar Atalhos da Siri no aplicativo do Power BI para iOS](https://powerbi.microsoft.com/blog/introducing-siri-integration-with-power-bi-mobile-ios-app-preview/).

### <a name="device-search-ios"></a>Pesquisa de dispositivo (iOS)
Integração do Power BI com a pesquisa de dispositivo do iOS (destaque). A pesquisa de conteúdo no iPhone ou iPad agora também incluirá itens do Power BI. Quando os usuários usarem a pesquisa de dispositivo nativa, pessoas, workspaces, aplicativos, dashboards e relatórios do Power BI correspondentes aos critérios de pesquisa também serão listados nos resultados. [Visite a postagem no blog para saber mais](https://powerbi.microsoft.com/blog/introducing-siri-integration-with-power-bi-mobile-ios-app-preview/).


### <a name="single-tap-report-interaction---ga"></a>Interação com relatórios com toque simples – disponibilidade geral

O toque simples agora está em disponibilidade geral e se tornará a interação por toque padrão para novos usuários. Os usuários ainda poderão desativá-lo e optar pelo toque duplo nas configurações do aplicativo.

### <a name="enhanced-conditional-access-protection-ios-android"></a>Proteção avançada de acesso condicional (iOS, Android)

Integramos com a [nova funcionalidade de acesso condicional baseado na proteção do aplicativo](https://docs.microsoft.com/azure/active-directory/conditional-access/app-protection-based-conditional-access) do AAD para aumentar a segurança limitando o acesso ao Power BI antes que a política do aplicativo seja aplicada.

### <a name="device-protection-ios"></a>Proteção de dispositivo (iOS)

Os usuários podem usar a proteção interna do dispositivo para proteger o Power BI, solicitando Face ID, Touch ID ou senha para acessar o Power BI. Isso pode ser controlado pelo usuário usando as configurações do aplicativo, mas também pelos administradores usando o Intune e qualquer outra ferramenta de MDM. [Saiba mais](https://docs.microsoft.com/power-bi/consumer/mobile/mobile-ios-native-secure-access).

### <a name="one-page-report-slideshow-windows"></a>Apresentação de slides de relatório de uma página (Windows)

Suporte para atualização automática para relatórios de uma página na apresentação de slides. Portanto, se a fonte de dados subjacente do relatório for atualizada, nós detectaremos e atualizaremos os dados na página.


## <a name="april-2019"></a>Abril de 2019

### <a name="key-influencers-visual"></a>Visual de Principais influenciadores 

Os visual de Principais influenciadores está disponível em seu aplicativo móvel. Este visual permite que você execute a análise de fatores importantes sobre seus dados com apenas alguns toques.

### <a name="add-comments-to-report-content-android-and-ios"></a>Adicionar comentários ao conteúdo do relatório (Android e iOS)

Agora, você pode usar comentários para colaborar e compartilhar opiniões sobre as páginas e visuais do relatório. Leia mais sobre o acréscimo de comentários no Serviço do Power BI e no Power BI Mobile [neste blog](https://powerbi.microsoft.com/blog/announcing-report-commenting-for-power-bi-service-and-mobile/). 

### <a name="maximize-the-view-with-full-screen-mode-android-and-ios"></a>Maximizar a exibição com o modo de tela inteira (Android e iOS)

Adicionamos um novo botão que permite controlar quando você deseja se concentrar em seus dados removendo cabeçalhos e rodapés e proporcionando o espaço máximo para exibir seus relatórios.

## <a name="march-2019"></a>Março de 2019

### <a name="supporting-external-guest-users-in-power-bi-apps-ios-android"></a>Suporte a usuários convidados externos em aplicativos do Power BI (iOS, Android)

Você pode acessar o conteúdo do Power BI compartilhado com você de outra organização diretamente do aplicativo (também conhecido como B2B). Leia mais sobre B2B em aplicativos móveis do Power BI [aqui](https://powerbi.microsoft.com/blog/power-bi-mobile-apps-now-support-azure-ad-b2b-guest-users/).

### <a name="enhancing-windows-presentation-mode-with-slideshow-windows"></a>Aprimorando o modo de apresentação do Windows com a apresentação de slides (Windows)

Com a [apresentação de slides](https://powerbi.microsoft.com/blog/enhancing-presentation-mode-with-slideshow-in-windows-power-bi-app/), você pode usar telas públicas em seu escritório para executar relatórios do Power BI em tela inteira, que alternarão automaticamente entre as páginas do relatório.  

### <a name="supporting-pbi-rs-reports-over-adfs-and-wap-configuration-ios-only"></a>Suporte para relatórios de PBI-RS com configuração de ADFS e WAP (somente iOS)

Relatórios do Power BI (PBIX) hospedados no PBI-RS com configuração de ADFS agora podem ser acessados do aplicativo do Power BI para iOS.

### <a name="enabling-single-tap-interaction-with-report-visuals"></a>Habilitação de interação com toque simples com visuais de relatório

Alteramos a interação com relatórios de modo que ela exigirá apenas um toque em um visual, botão ou segmentação para interagir com seus dados imediatamente. Os usuários não precisarão mais tocar em um visual para selecioná-lo e tocar novamente para interagir com ele, um toque simples fará ambos.

![Interação com toque simples](./media/mobile-whats-new-in-the-mobile-apps/single-tap-2.gif)

> [!NOTE]
> Os usuários existentes precisarão ativar este comportamento na configuração do aplicativo. Para obter mais informações, confira o artigo [Como configurar a interação de relatório com toque simples](https://docs.microsoft.com/power-bi/consumer/mobile/mobile-app-single-tap).

## <a name="january---february-2019"></a>Janeiro – Fevereiro de 2019
 
### <a name="visio-visuals"></a>Elementos visuais do Visio

Ao habilitar o logon único (SSO) em visuais do Visio, não é necessária nenhuma etapa de login adicional ao visualizar o relatório com o visuais do Visio no aplicativo. 

### <a name="dashboard-commenting-is-coming-to-power-bi-mobile-windows-app"></a>O Painel de comentários está chegando ao aplicativo do Windows do Power BI Mobile

Você pode adicionar comentários diretamente aos dashboards e blocos específicos para discutir seus dados; qualquer pessoa que exibir o dashboard verá seus comentários. 

## <a name="december-2018"></a>Dezembro de 2018

### <a name="filter-is-now-available-for-landscape-reports"></a>O filtro já está disponível para relatórios no modo paisagem 

O painel de filtro do relatório já está disponível para relatórios no modo paisagem, além de relatórios de telefone.

## <a name="november-2018"></a>Novembro de 2018

### <a name="modern-visual-header"></a>Cabeçalho de visual moderno 

Os relatórios que usam o novo “cabeçalho de visual moderno” deixarão de alocar espaço para cabeçalhos, resultando em menos espaço vazio e mais espaço para as visualizações.

### <a name="enhance-presentation-mode-windows"></a>Modo de apresentação aprimorada (Windows)

Modo de apresentação aprimorada para dispositivos Surface Hub e Windows 10.  Desfrute de uma experiência aprimorada da sala de reuniões do Surface Hub, com ferramentas de colaboração e apresentação aperfeiçoadas e uma exibição sem bordas otimizada para tela grande, para que você possa se concentrar em seus dados. O modo de apresentação também fornece ferramentas como escrita à tinta para ajudar você a apresentar e a debater sobre seus dados com eficiência. Leia mais sobre o modo de apresentação [aqui](https://powerbi.microsoft.com/blog/presentation-mode-in-power-bi-windows-app/).

### <a name="portrait-report-layout-in-tablets-ios-and-android"></a>Layout de relatórios em retrato em tablets (iOS e Android)

Agora, quando existe um layout de relatório de telefone, ele é usado para exibir relatórios no tablet na orientação de modo retrato. Leia mais sobre [como criar o layout de telefone no serviço do Power BI ou Desktop](https://docs.microsoft.com/power-bi/desktop-create-phone-report/).

### <a name="supporting-report-query-string"></a>Suporte a cadeia de caracteres de consulta de relatório 

O link de abertura do relatório que inclui a cadeia de consulta agora será aberto no aplicativo móvel e será filtrado previamente com base nas condições definidas na cadeia de consulta. Saiba mais sobre [como criar a URL de relatório com a cadeia de caracteres de consulta](https://docs.microsoft.com/power-bi/service-url-filters/).  

### <a name="shared-credentials-now-in-android"></a>Credenciais compartilhadas (agora no Android)

Entrar no Power BI pelo aplicativo móvel nunca foi tão fácil. Graças às credenciais compartilhadas, simplificamos o processo de entrada por meio do uso de outras credenciais de aplicativo do Office 365 no dispositivo para autenticar você no serviço do Power BI.

### <a name="in-app-urls-now-in-android"></a>URLs no aplicativo (agora no Android) 

Os links nos relatórios que apontarem para outros artefatos do Power BI agora abrirão diretamente no aplicativo. Isso permitirá que você crie fluxos personalizados de navegação, por exemplo, vinculando um relatório a um painel.

### <a name="show-data-and-copy-values"></a>Mostrar valores de dados e cópia

O menu de ação visual de relatório (...) agora tem a opção de mostrar os dados subjacentes em formato de tabela. Na tabela é possível tocar e segurar para selecionar e copiar os valores dela (supondo que não haja uma política do Intune que restrinja a cópia).

## <a name="october-2018"></a>Outubro de 2018

### <a name="paginated-report-preview-all-devices"></a>Versão prévia de relatórios paginados (todos os dispositivos)

Os relatórios paginados já estão disponíveis no serviço do Power BI. Os usuários com acesso aos relatórios paginados no serviço do Power BI também podem acessá-los no próprio aplicativo móvel. 

Leia a [postagem do blog do Power BI sobre os relatórios paginados no ambiente móvel](https://powerbi.microsoft.com/blog/power-bi-paginated-reports-also-available-in-power-bi-mobile-apps-preview/).

### <a name="shared-credentials-ios"></a>Credenciais compartilhadas (iOS)

Entrar no Power BI pelo aplicativo móvel nunca foi tão fácil. Graças às credenciais compartilhadas, simplificamos o processo de entrada por meio do uso de outras credenciais de aplicativo do Office 365 no dispositivo para autenticar você no serviço do Power BI.

### <a name="in-app-urls-ios"></a>URLs no aplicativo (iOS) 

Os links nos relatórios que apontarem para outros artefatos do Power BI agora abrirão diretamente no aplicativo. Isso permitirá que você crie fluxos personalizados de navegação, por exemplo, vinculando um relatório a um painel.

### <a name="ios12-and-watchos-5-support"></a>Suporte para iOS12 e watchOS 5 

Atualizamos o aplicativo Power BI para iOS para um funcionamento perfeito com o novo sistema operacional no relógio e em dispositivos móveis.

## <a name="september-2018"></a>Setembro de 2018

### <a name="phone-report-editing-in-the-browser-all-devices"></a>Edição de relatório de telefone no navegador (todos os dispositivos)

Agora, é possível criar um layout de relatório de telefone para um relatório que já está publicado no serviço do Power BI e não apenas no Power BI Desktop. Ele é criado no modo de edição em seu navegador.

### <a name="dashboard-commenting-ios-and-android"></a>Comentários no dashboard (iOS e Android) 

Você pode adicionar comentários diretamente aos dashboards e blocos específicos para discutir seus dados; qualquer pessoa que exibir o dashboard verá seus comentários. Também é possível trazer outras pessoas de sua organização para a conversa por meio de @mentioning. Aquelas que você @mentioned recebem uma notificação por push com sua mensagem no celular.

Atualmente disponível para dispositivos iOS e Android. O suporte para Windows virá em breve.

Leia a [postagem no blog do Power BI sobre comentários no dashboard](https://powerbi.microsoft.com/blog/announcing-dashboard-comments-in-power-bi/).

### <a name="single-sign-on-windows"></a>Logon único (Windows)

O SSO (logon único) é um dos recursos mais solicitados para o Power BI Mobile for Windows. Agora, você pode usar suas contas organizacionais primárias não apenas para entrar em seus dispositivos móveis com Windows ingressados no domínio, mas também para entrar sem interrupções no serviço do Power BI. Leia mais sobre [SSO e os aplicativos móveis com Windows](mobile-windows-10-app-single-sign-on-sso.md).

## <a name="previous-months"></a>Meses anteriores

### <a name="july-2018"></a>Julho de 2018

#### <a name="ios-and-android-only"></a>Apenas iOS e Android

**Filtros compartilhados**

Agora você pode receber relatórios com segmentações e filtros compartilhados.

**Suporte de imagem em segundo plano**

Quando você exibe um relatório no modo paisagem em seu dispositivo móvel, vê as mesmas imagens em segundo plano que vê no Power BI na Web.


### <a name="june-2018"></a>Junho de 2018

#### <a name="full-canvas-reports"></a>Relatórios de tela inteira

Barras de ação superiores e inferiores agora desaparecerão logo após o relatório carregar, para que você veja mais do seu relatório de uma vez.

#### <a name="increased-phone-report-canvas-size"></a>Tamanho maior da tela do relatório do telefone

Aumentamos o tamanho da tela do relatório do telefone para ter espaço para mais elementos visuais.

### <a name="may-2018"></a>Mai 2018

#### <a name="mobile-drill-through-all-mobile-apps"></a>Detalhamento móvel: todos os aplicativos móveis

Você poderá detalhar de um ponto de dados selecionado para outra página de relatório nos aplicativos móveis, se o autor do relatório tiver definido essa ação. 

#### <a name="back-button-all-mobile-apps"></a>Botão Voltar: todos os aplicativos móveis

Agora quando você navega em um relatório passando o dedo, escolhendo uma página de relatório na barra de ação ou usando o detalhamento, o botão Voltar retorna à página anterior que você estava olhando. 

#### <a name="dashboard-themes-all-mobile-apps"></a>Temas do dashboard: todos os aplicativos móveis

Quando os autores de relatório personalizam os temas do dashboard no serviço do Power BI, a aparência do dashboard também é alterada no aplicativo móvel. No entanto, você não verá as imagens da tela de fundo.

#### <a name="ios-configure-power-bi-ios-mobile-app-access-to-a-report-server-remotely"></a>iOS: Configurar o acesso do aplicativo móvel do Power BI iOS a um servidor de relatório remotamente

Seu administrador de TI agora pode usar uma ferramenta MDM para configurar o acesso do aplicativo móvel do Power BI iOS a um servidor de relatório. Confira [Configurar o acesso do aplicativo móvel do Power BI iOS a um servidor de relatório remotamente](../../report-server/configure-powerbi-mobile-apps-remote.md) para obter detalhes.

#### <a name="power-bi-for-mixed-reality-app-preview"></a>Aplicativo Power BI para Realidade Misturada (versão prévia)

O aplicativo Power BI para Realidade Misturada agora está na Microsoft Store. Veja seus dashboards e relatórios imerso no mundo virtual, ou posicione-os e veja-os em locais específicos no seu ambiente. Assista ao novo vídeo [Apresentando o Power BI no Hololens](https://www.youtube.com/watch?v=J_X_nOFUBss) para entender o contexto ou leia o artigo sobre o novo [aplicativo Power BI para Realidade Misturada](mobile-mixed-reality-app.md).


### <a name="april-2018"></a>Abril de 2018

#### <a name="mobile-drill-down-and-drill-up"></a>Fazer drill down e fazer drill up móvel

Agora você pode fazer drill down e drill up para se aprofundar em elementos visuais de relatório em seu dispositivo móvel. Para acessar esse novo recurso, toque e segure para abrir o menu de dica de ferramenta em um visual do relatório e toque nos botões de análise para explorar seus dados em profundidade. Saiba mais sobre [fazer drill up e drill drown nos aplicativos móveis](https://powerbi.microsoft.com/blog/drill-down-up-in-power-bi-mobile-apps/).

#### <a name="persistent-filters"></a>Filtros persistentes

Recentemente atualizamos filtros de relatórios e segmentações de dados, para que eles fossem salvos automaticamente no Power BI na Web para o aplicativo móvel do Power BI. Agora filtros e segmentações de dados que você definir no aplicativo móvel são salvos automaticamente no Power BI na Web.


### <a name="march-2018"></a>Março de 2018

#### <a name="power-bi-for-mixed-reality-app-preview"></a>Aplicativo Power BI para Realidade Misturada (versão prévia)

Na mudança mais recente para levar os dados até você, criamos o aplicativo Power BI para Realidade Misturada. Veja seus dashboards e relatórios imerso no mundo virtual, ou posicione-os e veja-os em locais específicos no seu ambiente. Leia mais sobre o novo [aplicativo Power BI para Realidade Misturada](mobile-mixed-reality-app.md).

#### <a name="share-reports-and-dashboards-externally"></a>Compartilhar relatórios e dashboards externamente

Compartilhe dashboards e relatórios com usuários fora da sua organização, diretamente do aplicativo. O compartilhamento externo é ativado para contas organizacionais e sociais. 

#### <a name="persistent-filters"></a>Filtros persistentes

Quando você define filtros e segmentações no Power BI na Web, suas opções de filtro também são salvas em seu aplicativo para dispositivos móveis, para que você possa continuar de onde parou.

#### <a name="refresh-reports-on-the-ipad"></a>Atualizar relatórios no iPad

Os relatórios do Power BI agora têm um botão de atualização no aplicativo do iPad.

### <a name="february-2018"></a>Fevereiro de 2018

#### <a name="share-reports"></a>Compartilhar relatórios

Agora é possível compartilhar um relatório diretamente dos aplicativos móveis. Leia mais sobre [como compartilhar dashboards e relatórios dos aplicativos móveis](mobile-share-dashboard-from-the-mobile-apps.md)

#### <a name="improved-tooltips"></a>Dicas de ferramentas aprimoradas

Quando você toca e segura em um visual de relatório para acessar as dicas de ferramentas, agora você pode arrastar o dedo pelo visual para explorar os detalhes de cada ponto de dados pelo caminho.

### <a name="january-2018"></a>Janeiro de 2018

#### <a name="report-favorites"></a>Relatórios favoritos

Marque relatórios como favoritos para que eles apareçam na página **Favoritos**. Leia mais sobre [favoritos nos aplicativos móveis do Power BI](mobile-apps-favorites.md).

#### <a name="view-shared-reports"></a>Exibir relatórios compartilhados

Agora quando alguém compartilhar um relatório com você, ele é listado na página **Compartilhado comigo** junto com os painéis.

#### <a name="improved-hyperlink-support"></a>Suporte de hiperlink aprimorado

Agora você pode tocar em links em elementos visuais personalizados para abri-los em seu navegador móvel.

#### <a name="intune-integration-android"></a>Integração do Intune (Android)

Suporte para acesso condicional usando o gerenciamento de dispositivos móveis do Intune.

### <a name="december-2017"></a>Dezembro de 2017

#### <a name="improved-security-management"></a>Gerenciamento de segurança melhorado 

Adicionamos suporte para CA (acesso condicional) e MDM (gerenciamento de dispositivo móvel) do Microsoft Intune em dispositivos Android para melhorar a segurança dos dados da organização. Já está disponível no iOS.

#### <a name="improved-permission-management"></a>Gerenciamento de permissões aprimorado

Foram feitas algumas alterações que permitem um gerenciamento mais preciso das permissões do usuário para relatórios, dashboards e conjuntos de dados.

#### <a name="auto-installed-apps"></a>Aplicativos instalados automaticamente

Não é necessário instalar alguns dos aplicativos no Power BI. Os criadores de aplicativos do Power BI em sua organização podem criar *aplicativos* que contêm uma coleção de dashboards e relatórios. Em seguida, eles podem publicar o aplicativo e defini-lo para ser instalado automaticamente no serviço do Power BI e nos aplicativos móveis do Power BI. Quando um aplicativo é definido para ser instalado para você, ele é exibido automaticamente no menu **Aplicativos**:

![Aplicativos nos aplicativos móveis do Power BI](./media/mobile-whats-new-in-the-mobile-apps/power-bi-apps-mobile-apps.png)

### <a name="november-2017"></a>Novembro de 2017
#### <a name="iphone-x-optimization"></a>Otimização do iPhone X

Otimizamos o layout do aplicativo para o iPhone X, para que você possa explorar os dados em estilo em cada dispositivo.

### <a name="october-2017"></a>Outubro de 2017
#### <a name="filters-for-phone-reports-in-android"></a>Filtros para relatórios para telefone no Android

Se você criar um relatório com páginas otimizadas para telefone no Power BI Desktop e o relatório tiver filtros, agora você poderá aplicar esses filtros ao relatório para telefone em seu Android. Leia mais sobre filtros para relatórios do Power BI no Android.

#### <a name="show-data-in-reports"></a>Mostrar dados em relatórios

Agora você pode alternar visuais em seus relatórios para uma exibição de tabela para ver os números por trás dos dados. Para acessar esse recurso, toque em “Mostrar dados” no menu … do visual no relatório ou no novo ícone no menu de ação do visual expandido.

### <a name="september-2017"></a>Setembro de 2017
#### <a name="filters-for-phone-reports-in-iphones"></a>Filtros para relatórios para telefone em iPhones
Se você criar um relatório com páginas otimizadas para telefone no Power BI Desktop e o relatório tiver filtros, agora você poderá aplicar esses filtros no relatório para telefone em seu iPhone. Leia mais sobre [filtros para relatórios do Power BI em iPhones](https://powerbi.microsoft.com/blog/filters-coming-for-phone-reports-on-ios/).

### <a name="august-2017"></a>Agosto de 2017
#### <a name="ios-proxy-settings-support"></a>Suporte a configurações de proxy do iOS
Agora você pode definir as configurações de proxy no aplicativo móvel iOS do Power BI. Isso significa que Power BI agora funcionará com conexões VPN em seu dispositivo móvel, permitindo que mais usuários e organizações aproveitem o poder do Power BI com segurança, em qualquer lugar.

### <a name="july-2017"></a>Julho de 2017
Leia o [resumo de julho de 2017 sobre os recursos dos aplicativos móveis](https://powerbi.microsoft.com/blog/power-bi-service-and-mobile-july-feature-summary/#ios-preview)

#### <a name="ios-devices"></a>Dispositivos iOS
**Nova experiência de P e R no iOS (Versão prévia)** Em vez de apenas receber uma mensagem para sua pergunta, agora você pode usar linguagem natural para obter insights com escopo definido. Mesmo se você não tiver certeza do que está procurando, a P e R proativamente traz à tona os insights relevantes para seus dados. A nova experiência de P e R em dispositivos móveis, desenvolvida em colaboração com a equipe da Microsoft Research, apresenta tecnologias poderosas em nosso produto. Experimente o tutorial [Faça perguntas sobre seus dados nos aplicativos móveis do iOS](mobile-apps-ios-qna.md).

### <a name="responsive-visuals"></a>Visuais responsivos
**Visual responsivo para dashboards e relatórios do telefone** Você pode definir os visuais em seu dashboard ou relatório para serem *responsivos*, para mudarem dinamicamente para exibir o máximo de dados e insight, independentemente do tamanho da tela. Leia o [blog sobre visuais responsivos](https://powerbi.microsoft.com/blog/power-bi-desktop-july-feature-summary-2/#responsiveVisuals).

### <a name="june-2107"></a>Junho de 2107
#### <a name="all-devices"></a>Todos os dispositivos
**Criar favoritos aplicativos** Já é possível tornar um dashboard em um favorito. Recentemente, o [Power BI adicionou aplicativos](../../service-create-distribute-apps.md) e agora você pode tornar aplicativos em favoritos também. 

### <a name="may-2017"></a>Maio de 2017
#### <a name="all-devices"></a>Todos os dispositivos
**Novo menu: Compartilhado comigo** Acesse Compartilhado comigo no menu do aplicativo móvel para ver todo o conteúdo que foi compartilhado com você.

**Novo menu: Aplicativos** Um aplicativo é uma coleção de painéis e relatórios desenvolvidos pela sua organização para fornecer métricas-chave para tomar decisões mais rápidas e fáceis, orientadas por dados.

Leia mais sobre [how your Power BI content is organized](mobile-apps-quickstart-view-dashboard-report.md) (como o conteúdo do Power BI é organizado).

#### <a name="ios-and-android-devices"></a>Dispositivos Android e iOS
**Visualização do Servidor de Relatório do Power BI** Crie e publique relatórios locais do Power BI. Em seguida, [exiba e interaja com eles no seu dispositivo móvel iOS ou Android](mobile-app-ssrs-kpis-mobile-on-premises-reports.md). 

### <a name="april-2017"></a>Abril de 2017
Leia o [mobile apps feature summary for April 2017](https://powerbi.microsoft.com/blog/power-bi-mobile-apps-feature-summary-march-april-2017/) (resumo de abril de 2017 sobre os recursos dos aplicativos móveis)

#### <a name="all-devices"></a>Todos os dispositivos
**Cor de plano de fundo de relatórios de telefone** Quando você definir uma cor da tela de fundo para um relatório no Power BI Desktop, o relatório de telefone terá a mesma cor da tela de fundo. Mais sobre [otimizar páginas de relatório para telefones](../../desktop-create-phone-report.md).

**Desenvolva visuais personalizados para dispositivos móveis** Leia este [Guia do desenvolvedor](https://github.com/Microsoft/PowerBI-visuals/blob/master/Tutorial/MobileGuideline.md) para obter dicas de como criar visuais personalizados que tenham boa aparência e funcionem bem em dispositivos móveis.

#### <a name="ios-devices"></a>Dispositivos iOS
**Fale com seus dados: faça perguntas falando** Agora você pode [fazer perguntas sobre seus dados com P e R](mobile-apps-ios-qna.md) falando em vez de digitando. 

### <a name="march-2017"></a>Março de 2017
Leia o [resumo de março de 2017 sobre os recursos dos aplicativos móveis](https://powerbi.microsoft.com/blog/power-bi-mobile-apps-feature-summary-march-2017/).

#### <a name="all-devices"></a>Todos os dispositivos
**Interações de segmentação de dados**

Melhoramos a interação por toque nas segmentações do tempo.

#### <a name="ios-devices"></a>Dispositivos iOS
**Faça perguntas sobre seus dados com P e R e forneça-nos comentários** Tente fazer perguntas sobre seus dados com P e R e, em seguida, envie-nos um smiley ou um rosto triste dando sua opinião.

**Use o toque 3D para ações comuns** Pressione o ícone do aplicativo Power BI na tela inicial do seu iPhone 6s ou superior para acessar notificações, pesquisas e dashboards usados recentemente.

**Suporte para idiomas da direita para esquerda** Os aplicativos móveis do Power BI agora dão suporte a idiomas da direita para esquerda. Nesse contexto, os "idiomas da direita para esquerda" referem-se a sistemas de escrita árabe e hebraico, que são escritos da direita para esquerda e exigem formatação contextual. Consulte a lista de [Idiomas com suporte nos aplicativos móveis do Power BI](mobile-apps-supported-languages.md).

#### <a name="android-devices"></a>Dispositivos Android
**Conectar-se a mais de um servidor do SSRS** 

Agora você pode se conectar com até cinco servidores do SSRS (SQL Server Reporting Services) ao mesmo tempo.

**Solicitar acesso aos dashboards** 

Se você digitalizar um código QR para um dashboard ao qual você não tenha acesso, agora será possível enviar uma solicitação de acesso diretamente do aplicativo móvel.

### <a name="february-2017"></a>Fevereiro de 2017
#### <a name="all-devices"></a>Todos os dispositivos
**Rolagem facilitada** 

Agora é possível rolar em gráficos de barras e colunas em um relatório ao tocar no próprio gráfico, em vez de tocar na barra de rolagem na lateral.

#### <a name="ios-devices"></a>Dispositivos iOS
**Faça perguntas sobre seus dados com uma visualização de P e R** 

Com P e R, faça perguntas sobre seus dados usando suas próprias palavras e o Power BI dará as respostas. P e R já está no serviço do Power BI em https://powerbi.com. Agora, ele também está [disponível no aplicativo móvel em seu iPhone ou iPad](mobile-apps-ios-qna.md).

**Conectar-se a mais de um servidor do SSRS** 

Agora você pode se conectar com até cinco servidores do SSRS (SQL Server Reporting Services) ao mesmo tempo.

#### <a name="android-tablets"></a>Tablets Android
O **aplicativo móvel do Power BI** para tablets com Android agora está disponível globalmente. Introdução ao [Power BI em seu tablet Android](mobile-android-app-get-started.md).

#### <a name="ios-and-android-devices"></a>Dispositivos Android e iOS
**Novo menu para os blocos de dashboard** Navegue até o relatório subjacente, expanda o bloco ou gerencie um alerta, tudo isso diretamente de um menu no bloco de um dashboard. 

Esse menu é novo para iOS, telefones com Android no modo paisagem e tablets com Android. Ele já estava disponível em telefones com Windows e Android no modo retrato.

### <a name="january-2017"></a>Janeiro de 2017
Leia o [resumo dos recursos do blog de aplicativos móveis de janeiro de 2017](https://powerbi.microsoft.com/blog/power-bi-mobile-apps-feature-summary-january-2017).

#### <a name="all-devices"></a>Todos os dispositivos
**Carregar mais de 100 linhas em tabelas e matrizes** Agora, se você tiver uma grande tabela ou matriz no painel ou relatório, vamos mostrar a maior quantidade possível de dados no bloco. No modo de foco, você pode rolar para baixo para carregar linhas adicionais.

**Disponibilidade geral – relatório de celular** os relatórios do Power BI no celular estão disponíveis. Na área de trabalho do Power BI, você pode personalizar uma exibição de retrato de um relatório existente para usuários móveis. Saiba mais sobre a [criação de relatórios de celular no Power BI Desktop](../../desktop-create-phone-report.md) e [experiência de relatório em celulares](mobile-apps-view-phone-report.md).

#### <a name="ios"></a>iOS
**Autenticação do SSRS usando a visualização dos Serviços de Federação do Active Directory (ADFS)** Agora você pode entrar nos servidores locais do SQL Server Reporting Services do seu dispositivo móvel com a sua conta corporativa. Leia mais sobre [usar o OAuth para se conectar aos servidores do SSRS](mobile-oauth-ssrs.md).

#### <a name="android"></a>Android
**Autenticação do SSRS usando a visualização dos Serviços de Federação do Active Directory (ADFS)** Agora você pode entrar nos servidores locais do SQL Server Reporting Services do seu dispositivo móvel com a sua conta corporativa. Leia mais sobre [usar o OAuth para se conectar aos servidores do SSRS](mobile-oauth-ssrs.md).

**Novos e aprimorados: Anote e compartilhe ideias rapidamente** O compartilhamento e as anotações já estão funcionando nos dispositivos Android. O menu aprimorado torna mais fácil e rápido fazer anotações e compartilhar informações, e você também pode compartilhar um relatório anotado ou diretamente do aplicativo do Power BI.

### <a name="december-2016"></a>Dezembro de 2016
Leia o [resumo dos recursos do blog de aplicativos móveis de dezembro de 2016](https://powerbi.microsoft.com/blog/power-bi-mobile-apps-feature-summary-december-2016).

#### <a name="all-devices"></a>Todos os dispositivos
**Atualização em segundo plano offline**

Para verificar se é possível acessar os dados mais recentes enquanto você está offline, podemos executar uma atualização em segundo plano do aplicativo, para que as suas informações comerciais sejam atualizadas, mesmo que você não as tenha acessado há algum tempo. Para verificar se determinados dashboards estão sempre atualizados, basta marcá-los como favoritos. Saiba mais sobre as [funcionalidades offline nos aplicativos móveis do Power BI](mobile-apps-offline-data.md).

#### <a name="ios-devices"></a>Dispositivos iOS
**Anotar e compartilhar**

Agora você pode anotar e compartilhar blocos, relatórios ou visualizações no aplicativo móvel do Power BI para iOS. 

* [No iPhone](mobile-annotate-and-share-a-tile-from-the-mobile-apps.md)
* [No iPad](mobile-annotate-and-share-a-tile-from-the-mobile-apps.md)

**Solicitar acesso aos dashboards**

Se você digitalizar um código QR para um dashboard ao qual você não tenha acesso, agora será possível enviar uma solicitação de acesso diretamente do aplicativo móvel.

**URL personalizada em bloco de imagem**

Se um bloco de imagem tiver uma URL personalizada definida pelo proprietário do dashboard, ao tocar no bloco, você acessará diretamente a URL sem precisar abrir o bloco no modo de foco. 

#### <a name="iphone"></a>iPhone
**Melhorias para Apple Watch**

Agora você pode atualizar dados do Apple Watch diretamente do aplicativo Watch. Na página de índice do dashboard, pressione e segure para atualizar os dados. (Para essa ação funcionar, o aplicativo móvel do Power BI deve estar em execução em segundo plano no seu iPhone).

#### <a name="android"></a>Android
**URL personalizada em bloco de imagem**

Se um bloco de imagem tiver uma URL personalizada definida pelo proprietário do dashboard, ao tocar no bloco, você acessará diretamente a URL sem precisar abrir o bloco no modo de foco. Além disso, os blocos do painel com as URLs personalizadas predefinidas agora podem redirecionar os leitores para os relatórios no aplicativo.

### <a name="november-2016"></a>Novembro de 2016
Leia o [resumo de recursos dos aplicativos móveis do Power BI publicado em novembro de 2016](https://powerbi.microsoft.com/blog/power-bi-mobile-apps-feature-summary-november-2016/).

#### <a name="android-tablets"></a>Tablets Android
**Aplicativo móvel do Power BI para tablets Android** Sim, aqui está a versão prévia.

* Experimente o [Power BI no tablet Android](mobile-android-app-get-started.md)
* Conheça [os relatórios móveis e KPIs do Reporting Services no tablet Android](mobile-app-ssrs-kpis-mobile-on-premises-reports.md)

#### <a name="android-devices"></a>Dispositivos Android
**Versão prévia: Gerenciamento de Aplicativo Móvel do Intune** O suporte do Power BI para o MAM (Gerenciamento de Aplicativo Móvel) do Microsoft Intune agora está em versão prévia para os usuários do Power BI Pro em dispositivos Android. 

**Favoritos** Marque seus dashboards favoritos no dispositivo Android e veja todos os seus [dashboards favoritos do Power BI e relatórios móveis e KPIs favoritos do Reporting Services](mobile-android-app-get-started.md#view-your-favorite-dashboards-kpis-and-reports) reunidos em um único local conveniente. 

#### <a name="ios-devices"></a>Dispositivos iOS
**Links** As URLs em blocos e visualizações agora são clicáveis e abertas em um navegador.

#### <a name="windows-devices"></a>Dispositivos Windows
**Centralize um mapa** para se concentrar nos dados que estão próximos à sua localização

### <a name="septemberoctober-2016"></a>Setembro/outubro de 2016
Leia o [resumo de recursos dos aplicativos móveis do Power BI publicado em outubro de 2016](https://powerbi.microsoft.com/blog/power-bi-mobile-apps-feature-summary-october-2016/).

#### <a name="all-devices"></a>Todos os dispositivos
**Favoritos como página de aterrissagem** se você marcou a qualquer um dos seus painéis como favoritos, sua página inicial será a entrada de Favoritos. 

**Navegação aprimorada** A navegação principal tem uma nova aparência e a navegação de grupos foi movida para o catálogo de grupos. 

**Melhorias de desempenho de relatório e de painel** Melhorou a experiência de carregamento de relatórios e painéis nos aplicativos móveis do Power BI

**Notificações de alerta avançadas** As notificações para os alertas controlados por dados agora contêm mais informações sobre o que disparou o alerta e porquê.

#### <a name="ios-on-iphones"></a>iOS em iPhones
**Aprimoramentos de atualização do Apple Watch** O aplicativo móvel Apple Watch foi aprimorado para o Watch OS3

#### <a name="android-phones"></a>Telefones Android
**Adição de atualização manual de bloco** Agora você pode atualizar manualmente seus blocos de painel. Para blocos com base no DirectQuery, isso recuperará os dados mais recentes do conjunto de dados.

#### <a name="windows-10-phones"></a>Telefones Windows 10
**Filtragem geográfica** No seu telefone Windows 10 você pode filtrar o relatório com base em sua localização atual e ver apenas os dados que deseja.

**Visualização do SandDance** Esta visualização personalizada agora está disponível no Surface Hub

### <a name="august-2016"></a>Agosto de 2016
#### <a name="all-phones"></a>Todos os telefones
**Favoritos** Veja seus dashboards favoritos de todos os aplicativos móveis do Power BI e gerencie a lista de favoritos dos aplicativos móveis do Power BI para dispositivos iOS e Windows 10. Leia mais sobre [favoritos nos aplicativos móveis do Power BI](mobile-apps-favorites.md).

**Classificação de dados do dashboard** Veja as classificações de dados que os proprietários do dashboard atribuíram aos seus dashboards. Leia mais sobre [classificar dashboards](../../service-data-classification.md).

**Alertas orientados a dados** Seja notificado por um alerta quando seus dados forem alterados de formas predefinidas para KPI, medidor e blocos de cartão. Saiba mais sobre:

* [Alertas no aplicativo Power BI para telefones Android](mobile-set-data-alerts-in-the-mobile-apps.md). 
* [Alertas nos aplicativos Power BI para iOS](mobile-set-data-alerts-in-the-mobile-apps.md). 
* [Alertas no aplicativo Power BI para dispositivos com Windows 10](mobile-set-data-alerts-in-the-mobile-apps.md).

#### <a name="ios-on-iphones-and-ipads"></a>iOS em iPhones e iPads
**Blocos de tela inteira no modo de foco no iPad** Ao tocar em um bloco no seu iPad, ele agora abrirá a tela inteira no modo de foco, aproveitando todo o tamanho da tela do iPad.

**Atualizar manualmente os blocos** Atualize manualmente seus blocos abrindo o dashboard no aplicativo móvel do Power BI para iOS e movendo para baixo na parte superior da tela. 

**Suporte para o Intune MAM** Suporte adicionado para recursos de gerenciamento de aplicativos móveis (MAM) do Microsoft Intune.

Leia mais sobre [Microsoft Intune em aplicativos móveis do Power BI](../../service-admin-mobile-intune.md).

#### <a name="windows-10-devices"></a>Dispositivos Windows 10
**Modos de tela inteira e apresentação** Exiba relatórios no modo de apresentação no Surface Hub, além de dashboards, relatórios e blocos no modo de tela inteira em dispositivos com Windows 10.

### <a name="july-2016"></a>Julho de 2016
#### <a name="all-phones"></a>Todos os telefones
O serviço do Power BI, agora você pode [criar uma exibição de um dashboard, especificamente para telefones](../../service-create-dashboard-mobile-phone-view.md) no modo retrato. 

#### <a name="android-phones"></a>Telefones Android
**Guia Favoritos** Acesse todos os seus dashboards favoritos em um único local.

**Gerenciamento de segurança aprimorado** Selecione uma classificação de risco para os dados de negócios apresentados em um painel específico.

**Aviso e faixas melhorados** Melhoramos os avisos e faixas para o aplicativo móvel.

**Códigos QR para páginas de relatório** Um código QR gerado no serviço será vinculado a uma página específica, ao invés de todo o relatório.

**Alertas aprimorados** Alertas orientados a dados agora são formatados com base na localidade do seu dispositivo.

#### <a name="ios-on-iphones-and-ipads"></a>iOS em iPhones e iPads
**Gerenciamento de segurança aprimorado** Selecione uma classificação de risco para os dados de negócios apresentados em um painel específico.

**Percepções móveis** Exiba dados de resumo (máx., mín. e todos) nos blocos do gráfico de colunas agrupados.

**Atualização manual melhorada** Agora você pode atualizar manualmente seus blocos de painel. Para blocos com base em consulta direta, ela recupera os dados mais recentes do modelo de dados.

**Aviso e faixas melhorados** Melhoramos os avisos e faixas para o aplicativo móvel.

**Códigos QR para páginas de relatório** Um código QR gerado no serviço será vinculado a uma página específica, ao invés de todo o relatório.

**Melhorias gerais** Melhoramos mensagens de erro de blocos no aplicativo móvel.

#### <a name="windows-10-devices"></a>Dispositivos Windows 10
**Gerenciamento de segurança aprimorado** Selecione uma classificação de risco para os dados de negócios apresentados em um painel específico.

**Aviso e faixas melhorados** Melhoramos os avisos e faixas para o aplicativo móvel.

### <a name="june-2016"></a>Junho de 2016
Confira a [postagem no blog dos aplicativos móveis do Power BI de junho](https://powerbi.microsoft.com/blog/power-bi-mobile-apps-update-june-2016/) para obter mais detalhes.

#### <a name="qr-codes-now-display-in-augmented-reality-ios"></a>Os códigos de barras QR agora são exibidos em realidade aumentada (iOS)
Agora, quando você digitaliza um código QR gerado pelo serviço do Power BI, o bloco é renderizado em realidade aumentada. 

Mais sobre como [se conectar a dados no mundo real](mobile-apps-data-in-real-world-context.md).

#### <a name="filter-data-with-barcodes-iphone"></a>Filtrar dados com códigos de barras (iPhone)
Agora, você pode digitalizar códigos de barras impressos em produtos ou prateleiras da loja para exibir relatórios do Power BI relacionados, filtrados pelo valor digitalizado. 

Mais sobre como [filtrar seus dados com códigos de barras](mobile-apps-scan-barcode-iphone.md).

#### <a name="sql-server-2016-reporting-services-mobile-reports"></a>Relatórios móveis do SQL Server 2016 Reporting Services
Agora, você pode executar uma consulta drill-through por meio de um KPI ou relatório móvel do Reporting Services para outro relatório móvel ou para qualquer URL personalizada.

#### <a name="notification-center"></a>Central de notificações
A central de notificações no aplicativo móvel do Power BI mostra novos dados ou dashboards compartilhados com você ou alterações nos grupos aos quais você pertence.

### <a name="may-2016"></a>Maio de 2016
#### <a name="ios-devices-and-android-phones"></a>dispositivos iOS e telefones Android
* Os **códigos de barras QR** agora estão disponíveis **para relatórios** também. Digitalize o código com seu aplicativo do Power BI para ir diretamente para um relatório relacionado, sem a necessidade navegação nem de pesquisa.
* **Gerenciamento de dados aprimorado** para o SQL Server 2016 Reporting Services: Tempos de carga e consumo de dados reduzidos no seu dispositivo.
* **Relatórios móveis com temas do SQL Server 2016**: Confira os temas para relatórios móveis em seu dispositivo.
* **Filtragem geográfica**: Filtre relatórios por sua localização atual.

### <a name="april-2016"></a>Abril de 2016
Consulte o [blog de Aplicativos Móveis do Power BI de abril](https://powerbi.microsoft.com/blog/power-bi-mobile-apps-update-april-2016/) para obter mais detalhes.

#### <a name="all-apps"></a>Todos os aplicativos
* Selecione mais de uma opção em uma segmentação do relatório.

#### <a name="android-mobile-app"></a>Aplicativo móvel do Android
* Relatórios móveis do **SQL Server 2016 Reporting[ Services](mobile-app-ssrs-kpis-mobile-on-premises-reports.md)** agora em telefones Android.
* **Galeria de relatórios** Abra seus relatórios diretamente na galeria de relatórios.
* **A autenticação NTLM** dá suporte aos relatórios móveis no SQL Server 2016 Reporting Services.

#### <a name="power-bi-app-for-windows-10-devices"></a>Aplicativo Power BI para dispositivos Windows 10
* **Modo de apresentação** Exibir painéis e relatórios do Power BI painéis no modo de apresentação do aplicativo Power BI.
* Relatórios móveis do **SQL Server 2016 Reporting[ Services](mobile-app-windows-10-ssrs-kpis-mobile-reports.md)** agora em dispositivos com Windows 10.
* Veja **dicas de ferramentas de dados** ao focalizar o mouse em um bloco do dashboard.

### <a name="march-2016"></a>Março de 2016
Leia o [blog dos Aplicativos Móveis do Power BI publicado em março de 2016](https://powerbi.microsoft.com/blog/power-bi-mobile-apps-update-march-2016/).

#### <a name="iphone-mobile-app"></a>Aplicativo móvel do iPhone
**Apple Watch** Veja os blocos e KPIs do Power BI no [Apple Watch](mobile-apple-watch.md).

**iOS 9.0 e posterior** Para acomodar a melhor experiência e os novos recursos para o Power BI, agora damos suporte apenas a dispositivos que executam o iOS 9.0 e posterior.

**Pesquisa global** Adição de uma nova lista de “exibidos recentemente” e a pesquisa global, para que você possa encontrar os dados de que precisa rapidamente.

**Galeria de relatórios** Abra seus relatórios diretamente na galeria de relatórios.

**Dados atualizados offline** A nova atualização em segundo plano atualiza automaticamente os dados armazenados em cache quando estiver online, para que você tenha os dados mais recentes [mesmo quando estiver offline](mobile-apps-offline-data.md). 

**Blocos do Bing e do R** Abra blocos do Bing e do R no modo foco.

#### <a name="android-mobile-app"></a>Aplicativo móvel do Android
**Relatórios móveis do SQL Server 2016 e KPIs** [Exiba relatórios móveis do SQL Server 2016 e KPIs](mobile-app-ssrs-kpis-mobile-on-premises-reports.md) e navegue entre as pastas do SSRS.

**Exibir relatórios** Abra relatórios de blocos em seus dashboards.

**Dados atualizados offline** A nova atualização em segundo plano atualiza automaticamente os dados armazenados em cache quando estiver online, para que você tenha os dados mais recentes [mesmo quando estiver offline](mobile-apps-offline-data.md). 

#### <a name="power-bi-app-for-windows-10-devices"></a>Aplicativo Power BI para dispositivos Windows 10
**Acesso rápido** Acesse seus dashboards, relatórios e grupos rapidamente com uma nova lista de “exibidos recentemente” e uma pesquisa global para encontrar os dados necessários.

**Blocos do Bing e do R** Abra blocos do Bing e do R no modo foco.

**Mais blocos dinâmicos na tela inicial** [Fixe KPIs e placas de linha em sua tela inicial](mobile-pin-dashboard-start-screen-windows-10-phone-app.md) como blocos dinâmicos, para que você possa ver todas as métricas críticas imediatamente.

**Pince para aplicar zoom** Use Pince para aplicar zoom no tablet para examinar os dashboards mais detalhadamente.

**Notificações** Receba notificações quando seus conjuntos de dados, relatórios e dashboards forem atualizados com novos dados.

**Galeria de relatórios** Abra seus relatórios diretamente na galeria de relatórios.

### <a name="february-2016"></a>Fevereiro de 2016
#### <a name="android"></a>Android
Veja dashboards no [modo paisagem em telefones Android](mobile-apps-view-dashboard.md#view-dashboards-on-your-android-phone). 

#### <a name="power-bi-app-for-windows-10-devices"></a>Aplicativo Power BI para dispositivos Windows 10
Veja [relatórios em seu telefone Windows 10](mobile-reports-in-the-mobile-apps.md).

Tempo mais rápido para [insights em seus painéis do Windows 10 para dispositivos móveis](mobile-tiles-in-the-mobile-apps.md): Compartilhar um instantâneo de bloco ou abrir um relatório diretamente no painel.

### <a name="january-2016"></a>Janeiro de 2016
Todas as melhorias feitas em janeiro já estão incluídas no novo [aplicativo Power BI para telefones Windows 10](mobile-windows-10-phone-app-get-started.md), lançado em dezembro de 2015. Agora, eles serão distribuídos a outros aplicativos do Power BI para dispositivos móveis. Leia a postagem no blog sobre esses aprimoramentos.

**Suporte a dados em tempo real** Atualização de painéis em tempo real para que você não precise atualizá-los manualmente.

**Indicadores offline** Quando não houver sinal, você encontrará um indicador offline na parte superior do painel.

**Acesso a dados em cache** Dados em cache não expirar mais, portanto você tema cesso a seus dados em cache indefinidamente enquanto estiver offline.

**Blocos de R e widgets da Web** Exiba esses novos tipos de bloco no seu dispositivo móvel.

**Dashboards do Bing** No serviço do Power BI, agora é possível criar [dashboards com os resultados da pesquisa do Bing](../../service-connect-to-services.md) e vê-los em seu dispositivo móvel.

**Páginas de relatório fixadas como blocos em dashboards** Agora, você pode fixar uma página de relatório inteira em um dashboard no serviço do Power BI e exibir páginas de relatórios no aplicativo do Power BI no seu iPhone ou telefone Android.

### <a name="december-2015"></a>Dezembro de 2015
A equipe do Power BI terminou 2015 forte, com várias atualizações e adições importantes.

#### <a name="sql-server-2016-reporting-services-mobile-reports-in-ios"></a>Relatórios móveis do SQL Server 2016 Reporting Services no iOS
Agora você pode exibir os relatórios móveis do SQL Server no aplicativo Power BI em seu dispositivo iOS, seja ele um iPad ou um iPhone. Leia mais:

* Postagem no blog [SQL 16 SSRS no aplicativo Power BI para iOS](https://blogs.msdn.com/b/powerbi/archive/2015/12/30/sql-16-ssrs-on-power-bi-app-for-ios.aspx)
* Ver documentação [KPIs e relatórios móveis do SQL Server nos aplicativos para iPhone e iPad](mobile-app-ssrs-kpis-mobile-on-premises-reports.md)

#### <a name="power-bi-app-for-windows-10-phones"></a>Aplicativo Power BI para telefones Windows 10
O novo aplicativo Power BI para telefones Windows 10 é otimizado para produtividade móvel e por toque. Explore relatórios e painéis, convide seus colegas para exibir dados e compartilhe informações por email para envolver sua equipe. Além disso, é possível [fixar dashboards do Power BI na tela inicial do Windows Phone](mobile-pin-dashboard-start-screen-windows-10-phone-app.md).

* Leia a [postagem no blog do aplicativo Power BI para telefones Windows 10](https://blogs.msdn.com/b/powerbi/archive/2015/12/30/announcing-the-power-bi-app-for-windows-10-mobile.aspx).
* [Introdução ao aplicativo Power BI para telefones Windows 10](mobile-windows-10-phone-app-get-started.md).

#### <a name="other-additions"></a>Outras adições
Leia a [postagem no blog publicada em dezembro sobre os aplicativos móveis do Power BI](https://blogs.msdn.com/b/powerbi/archive/2015/12/30/power-bi-mobile-apps-update-_2d00_-december-2015.aspx) para obter mais detalhes.

* Receba notificações quando um colega compartilhar um painel com você. (iOS)
* Veja todas as páginas de relatório fixadas em seus dashboards. (iOS e Android)
* [Digitalize um código QR](https://blogs.msdn.com/b/powerbi/archive/2015/12/08/bridge-the-gap-between-your-physical-world-and-your-bi-using-qr-codes.aspx) e vá diretamente para um bloco relevante em seu telefone Android.

### <a name="november-2015"></a>Novembro de 2015
Leia a [postagem no blog móvel do Power BI publicada em novembro de 2015](https://blogs.msdn.com/b/powerbi/archive/2015/11/24/power-bi-mobile-apps-update-_2d00_-november-2015.aspx).

#### <a name="all-power-bi-mobile-apps"></a>Todos os aplicativos móveis do Power BI
* Uma nova experiência de boas-vindas.
* Capacidade aprimorada de dados do gráfico.

#### <a name="ios-and-android-mobile-apps"></a>Aplicativos móveis para iOS e Android
* As empresas agora podem [configurar aplicativos móveis do Power BI para iOS e Android com o Microsoft Intune](../../service-admin-mobile-intune.md) a fim de gerenciar dispositivos e aplicativos.

#### <a name="iphone-mobile-app"></a>Aplicativo móvel do iPhone
* [Adicione um bloco de imagem a um dashboard](mobile-iphone-app-get-started.md) diretamente do iPhone.
* [Crie códigos QR no serviço do Power BI](../../service-create-qr-code-for-tile.md) e digitalize-os no iPhone para abrir o aplicativo Power BI em um bloco específico.

#### <a name="the-power-bi-app-for-windows-devices"></a>O aplicativo do Power BI para dispositivos Windows
* [Vincule diretamente de um bloco a uma URL específica](../../service-dashboard-edit-tile.md#hyperlink).

### <a name="october-2015"></a>Outubro de 2015
Leia a [postagem no blog móvel do Power BI publicada em meados de outubro](https://blogs.msdn.com/b/powerbi/archive/2015/10/21/power-bi-mobile-mid-october-updates-are-here.aspx).

#### <a name="all-power-bi-mobile-apps"></a>Todos os aplicativos móveis do Power BI
* Os gráficos de linha com um eixo y baseado em percentual agora calculam o intervalo do visual de acordo com os dados reais. O gráfico agora é iniciado do ponto de dados mais baixo no gráfico, em vez de um valor padrão.
* Os gráficos de linha, coluna e barras agora podem ter rótulos de dados. 
  
    ![](media/mobile-whats-new-in-the-mobile-apps/pbi_mobilelinechart.png)

#### <a name="iphone"></a>iPhone
* Mantenha-se atualizado com os mais recentes painéis de seus grupos - receba notificações em seu iPhone sempre que um membro da equipe adicionar um painel a um de seus grupos.
  
    ![](media/mobile-whats-new-in-the-mobile-apps/pbi_iph_grpdashalertcrop.png)
* Agora você pode exibir painéis horizontalmente, apenas girando seu telefone. Leia mais sobre o [modo paisagem no aplicativo iPhone](https://blogs.msdn.com/b/powerbi/archive/2015/11/02/enjoy-the-landscape-with-the-power-bi-iphone-app.aspx).
  
    ![](media/mobile-whats-new-in-the-mobile-apps/pbi_iph_landscape.png)

### <a name="september-2015"></a>Setembro de 2015
Aprimoramentos nos aplicativos móveis do Power BI, Android, iOS (iPhone e iPad) e Windows. Leia a [postagem no blog móvel do Power BI publicada em meados de setembro](https://blogs.msdn.com/b/powerbi/archive/2015/09/23/power-bi-mobile-mid-september-updates-are-here.aspx).

#### <a name="android"></a>Android
* Suporte para workspaces de grupo: colabore com colegas em workspaces do grupo. 
* Suporte para usuários não autenticados:  para alguns cenários em que os usuários não puderem entrar no aplicativo, adicionamos uma maneira rápida e conveniente de entrar em contato com o suporte e enviar comentários.
* Melhor experiência de usuário ao acessar painéis usando a segurança baseada em função.          
* Formatação de dados aprimorados de gráficos e alinhamento de todos os blocos do painel. 

#### <a name="ios-iphone-and-ipad"></a>iOS (iPhone e iPad)
* Navegação nova e aprimorada: a nova navegação de gaveta aumenta a propriedade da tela e melhora a navegação através do aplicativo. 
* Workspaces do grupo: colabore com colegas em workspaces do grupo. 
* O processo de autenticação atualiza a qualidade, desempenho e melhorias de funcionalidade aprimoram o processo de autenticação, incluindo o suporte para SSO (Logon único). 
* Representação de dados melhorada dos blocos do gráfico de linha para comprimir melhor o eixo x.
* Experiência aprimorada do usuário ao usar com segurança baseada em função.
* Melhorias otimizadas de toque para os blocos do gráfico matriz: agora você pode percorrer facilmente através dos dados de matriz e visualizar todos os dados facilmente e de forma intuitiva.
* Formatação de dados aprimorados de gráficos e alinhamentos de todos os blocos do painel. 
* Remoção do suporte do iOS 7: manter os mais altos padrões de segurança para o Power BI, não daremos mais suporte aos dispositivos iOS 7 instalados. É necessário iOS 8 e superior. 
* Envie comentários e classificação adicionados ao aplicativo: capacidade adicionada do aplicativo de enviar comentários e fornecer classificações para que seja possível aumentar a influência da comunidade em nosso roteiro e promover os problemas facilmente e diretamente no aplicativo.

#### <a name="windows"></a>Windows
* Bloco de mapa aprimorada de renderização no modo em foco para aumentar o espaço na tela.
* Melhor experiência de usuário ao acessar painéis usando a segurança baseada em função. 
* Uma nova funcionalidade permite que você navegue para frente e para trás por meio de blocos de painel explorando-os diretamente no modo em foco sem a necessidade de retornar ao painel para selecionar o próximo bloco.
* Estabilidade adicional e melhorias de desempenho. 

