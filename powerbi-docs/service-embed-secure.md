---
title: Inserir um relatório em um site ou portal seguro
description: O recurso de inserção do Power BI permite aos usuários inserir relatórios em portais da Web internos com facilidade e segurança.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/27/2020
LocalizationGroup: Share your work
ms.openlocfilehash: 4be8a1ce88d50461ca51bb65278b823046459e30
ms.sourcegitcommit: 20f15ee7a11162127e506b86d21e2fff821a4aee
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/29/2020
ms.locfileid: "82585047"
---
# <a name="embed-a-report-in-a-secure-portal-or-website"></a>Inserir um relatório em um site ou portal seguro

Com a nova opção **Inserir** para relatórios do Power BI, você pode inserir relatórios em portais Web internos com facilidade e segurança. Esses portais podem ser **baseados em nuvem** ou **hospedados localmente**, como o SharePoint 2019. Relatórios inseridos respeitam todas as permissões de itens e segurança de dados por meio da [RLS (Segurança em Nível de Linha)](service-admin-rls.md). Eles fornecem a inserção sem código em qualquer portal que aceite uma URL ou iFrame. 

A opção **Inserir** dá suporte aos [filtros de URL](service-url-filters.md) e às configurações de URL. Ela permite a integração com portais usando uma abordagem de codificação mínima que requer apenas conhecimentos básicos de HTML e JavaScript.

## <a name="how-to-embed-power-bi-reports-into-portals"></a>Como inserir relatórios do Power BI em portais

1. Abra um relatório no serviço do Power BI.

2. No menu **Mais opções (...)** , selecione **Inserir** >  **Site ou portal**.

    ![Opção de site ou portal](media/service-embed-secure/power-bi-more-options-website.png)

2. Escolha a opção **Inserir** para abrir uma caixa de diálogo que fornece um link e um iFrame que podem ser usados para inserir o relatório com segurança.

    ![Caixa de diálogo da opção Inserir](media/service-embed-secure/secure-embed-code-dialog.png)

3. Quer um usuário abra uma URL de relatório diretamente ou incorporada em um portal da Web, o acesso ao relatório exigirá autenticação. A tela a seguir será exibida se o usuário não tiver entrado no Power BI na sessão atual do navegador. Ao selecionar **Entrar**, uma nova janela ou guia do navegador poderá ser aberta. Se não for solicitado que o usuário entre, será necessário verificar se há bloqueadores de pop-up ativados.

    ![Entrar para exibir este relatório](media/service-embed-secure/secure-embed-sign-in.png)

4. Depois que o usuário entrar, o relatório será aberto e mostrará os dados, permitindo a navegação pelas páginas e a configuração de filtros. Somente os usuários com permissão de exibição poderão ver o relatório no Power BI. Todas as regras de [RLS (Segurança em Nível de Linha)](service-admin-rls.md) também são aplicadas. Por último, o usuário precisa estar licenciado corretamente, ou precisa de uma licença do Power BI Pro ou o relatório deve estar em um workspace que esteja em uma capacidade do Power BI Premium. O usuário precisará entrar novamente toda vez que abrir uma nova janela do navegador. No entanto, uma vez conectado, outros relatórios serão carregados automaticamente.

    ![Inserir relatório](media/service-embed-secure/secure-embed-report.png)

5. Ao usar um iFrame, talvez seja necessário editar a **altura** e a **largura** para que caibam na página da Web do Portal.

    ![Definir altura e largura](media/service-embed-secure/secure-embed-size.png)

## <a name="granting-report-access"></a>Concedendo acesso ao relatório

A opção **Inserir** não permite automaticamente que os usuários exibam o relatório. As permissões de exibição são definidas no serviço do Power BI.

No serviço do Power BI, você pode compartilhar relatórios inseridos com usuários que necessitam de acesso. Se estiver usando um grupo do Office 365, você poderá listar o usuário como um membro do workspace. Para obter mais informações, consulte como [gerenciar seu workspace no Power BI e no Office 365](service-manage-app-workspace-in-power-bi-and-office-365.md).

## <a name="licensing"></a>Licenças

Para exibir os relatórios inseridos, os usuários precisam de uma licença do Power BI Pro ou o conteúdo precisa estar em um workspace que esteja em uma [capacidade do Power BI Premium (SKU EM ou P)](service-admin-premium-purchase.md).

## <a name="customize-your-embed-experience-using-url-settings"></a>Personalizar sua experiência de inserção usando configurações de URL

Você pode personalizar a experiência do usuário usando as configurações de entrada da URL de inserção. No iFrame fornecido, você pode atualizar as configurações de **src** da URL.

| Property  | Descrição  |  |  |  |
|--------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---|---|---|
| pageName  | Você pode usar o parâmetro de cadeia de caracteres de consulta **pageName** para definir qual página do relatório abrir. Você pode encontrar esse valor no final da URL do relatório ao exibi-lo no serviço do Power BI, conforme mostrado abaixo. |  |  |  |
| Filtros de URL  | Você pode usar [Filtros de URL](service-url-filters.md) na URL de inserção recebida da interface do usuário do Power BI para filtrar o conteúdo da inserção. Dessa forma, você pode criar integrações de código baixo tendo apenas experiências básicas em HTML e JavaScript.  |  |  |  |

## <a name="set-which-page-opens-for-an-embedded-report"></a>Definir qual página é aberta para um relatório inserido 

Você pode encontrar o valor do **pageName** no final da URL do relatório ao exibi-lo no serviço do Power BI.

1. Abra o relatório no serviço do Power BI em seu navegador da Web e copie a URL da barra de endereço.

    ![Seção de relatório](media/service-embed-secure/secure-embed-report-section.png)

2. Anexe a configuração **pageName** à URL.

    ![Anexar pageName](media/service-embed-secure/secure-embed-append-page-name.png)

## <a name="filter-report-content-using-url-filters"></a>Filtrar o conteúdo do relatório usando filtros de URL 

Você pode usar [filtros de URL](service-url-filters.md) para fornecer diferentes exibições de um relatório. Por exemplo, a URL a seguir filtra o relatório para mostrar dados ao setor de energia.

Usar a combinação de **pageName** e [Filtros de URL](service-url-filters.md) pode ser poderosa. Você pode criar experiências usando HTML e JavaScript básicos.

Por exemplo, eis um botão que você pode adicionar a uma página HTML:

```html
<button class="textLarge" onclick='show("ReportSection", "Energy");' style="display: inline-block;">Show Energy</button>
```

Ao ser pressionado, o botão chama uma função para atualizar o iFrame com uma URL atualizada, que inclui o filtro para o setor de energia.

```javascript
function show(pageName, filterValue)

{

var newUrl = baseUrl + "&pageName=" + pageName;

if(null != filterValue && "" != filterValue)

{

newUrl += "&$filter=Industries/Industry eq '" + filterValue + "'";

}

//Assumes there's an iFrame on the page with id="iFrame"

var report = document.getElementById("iFrame")

report.src = newUrl;

}
```

![Filtrar](media/service-embed-secure/secure-embed-filter.png)

Você pode adicionar quantos botões desejar para criar uma experiência personalizada de código baixo. 

## <a name="considerations-and-limitations"></a>Considerações e limitações

* Os relatórios paginados são compatíveis com cenários de inserção seguros, e os relatórios paginados com parâmetros de URL também são compatíveis. Leia mais sobre [como passar parâmetros de relatório em uma URL para um relatório paginado](paginated-reports/report-builder-url-pass-parameters.md).

* Não há suporte a usuários convidados externos com integração entre empresas (B2B) do Azure.

* A inserção segura funciona para relatórios publicados no serviço do Power BI.

* O usuário precisa entrar para ver o relatório sempre que abrir uma nova janela do navegador.

* Alguns navegadores exigem que você atualize a página após entrar, especialmente ao usar os modos InPrivate ou Incognito.

* Você poderá ter problemas se usar versões de navegador sem suporte. O Power BI é compatível com [a seguinte lista de navegadores](power-bi-browsers.md).

* Não há suporte para o servidor do SharePoint clássico, pois ele requer versões anteriores ao Internet Explorer 11 ou a habilitação do modo de exibição de compatibilidade.

* Para obter uma experiência de logon único, use a [opção Inserir no SharePoint Online](service-embed-report-spo.md) ou crie uma integração personalizada usando o método de inserção o [usuário possui dados](developer/embedded/embed-sample-for-your-organization.md). 

* O recurso de autenticação automática fornecido com a opção **Inserir** não funciona com a API JavaScript do Power BI. Para a API JavaScript do Power BI, use o método de inserção [o usuário possui dados](developer/embedded/embed-sample-for-your-organization.md). 

* O tempo de vida do token de autenticação é controlado com base nas configurações do AAD. Quando o token de autenticação expirar, o usuário precisará atualizar o navegador para obter um token de autenticação atualizado. O tempo de vida padrão é de uma hora, mas ele pode ser mais curto ou mais longo na sua organização.

## <a name="next-steps"></a>Próximas etapas

* [Maneiras de compartilhar seu trabalho no Power BI](service-how-to-collaborate-distribute-dashboards-reports.md)

* [Filtrar relatórios usando parâmetros da cadeia de caracteres de consulta na URL](service-url-filters.md)

* [Inserir com Web Part de Relatório no SharePoint Online](service-embed-report-spo.md)

* [Publicar na Web por meio do Power BI](service-publish-to-web.md)
