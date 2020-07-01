---
title: Conectar-se ao warehouse de computação Snowflake no Power BI Desktop
description: Conecte-se facilmente e use um depósito de computação Snowflake no Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: how-to
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: b343136acb22d213c0e2ad2dfcf83fbda805e88a
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85224129"
---
# <a name="connect-to-a-snowflake-computing-warehouse-in-power-bi-desktop"></a>Conectar-se a um depósito de computação Snowflake no Power BI Desktop
No Power BI Desktop, você pode se conectar a um depósito de computação **Snowflake** e usar os dados subjacentes, assim como qualquer outra fonte de dados no Power BI Desktop. 

## <a name="connect-to-a-snowflake-computing-warehouse"></a>Conectar-se a um depósito de computação Snowflake
Para conectar-se a um depósito de computação **Snowflake**, selecione **Obter Dados** na faixa de opções **Página Inicial** no Power BI Desktop. Selecione **Banco de dados** nas categorias à esquerda e você verá **Snowflake**.

![](media/desktop-connect-snowflake/connect-snowflake-2b.png)

Na janela **Snowflake** que será exibida, digite ou cole o nome do depósito de computação Snowflake na caixa e selecione **OK**. Observe que você pode escolher **Importar** dados diretamente no Power BI ou pode usar o **DirectQuery**. Você pode aprender mais à respeito [usando o DirectQuery](desktop-use-directquery.md). Observe que o SSO do AAD dá suporte apenas ao DirectQuery.

![](media/desktop-connect-snowflake/connect-snowflake-3.png)

Quando solicitado, insira o nome de usuário e a senha.

![](media/desktop-connect-snowflake/connect-snowflake-4.png)

> [!NOTE]
> Quando você insere seu nome de usuário e senha para um servidor **Snowflake** específico, o Power BI Desktop usa as mesmas credenciais em tentativas de conexão subsequentes. Você pode modificar essas credenciais indo para **Arquivo > Opções e configurações > Configurações de fonte de dados**.
> 
> 

Se você quiser usar a opção da conta Microsoft, a integração do AAD do Snowflake deverá ser configurada no Snowflake. Para fazer isso, leia a seção Introdução da [Documentação do Snowflake sobre o tópico](https://docs.snowflake.net/manuals/user-guide/oauth-powerbi.html#power-bi-sso-to-snowflake).

![Tipo de autenticação da conta Microsoft no conector do Snowflake.](media/desktop-connect-snowflake/connect-snowflake-6.png)


Depois que você se conectar com êxito, uma janela **Navegador** será mostrada e exibirá os dados disponíveis no servidor, dentre os quais você pode selecionar um ou vários elementos para importar e usar no **Power BI Desktop**.

![Erro 28000 do ODBC causando uma falha na conexão.](media/desktop-connect-snowflake/connect-snowflake-5.png)

Você pode **Carregar** a tabela selecionada, que leva toda a tabela para o **Power BI Desktop** ou você pode **Editar** a consulta, o que abre **Editor de Consultas** para filtrar e refinar o conjunto de dados que você deseja usar e, em seguida, carregar tal conjunto de dados refinado no **Power BI Desktop**.

## <a name="next-steps"></a>Próximas etapas
Há todos os tipos de dados aos quais você pode se conectar usando o Power BI Desktop. Para obter mais informações sobre fontes de dados, confira os seguintes recursos:

* [O que é o Power BI Desktop?](../fundamentals/desktop-what-is-desktop.md)
* [Fontes de dados no Power BI Desktop](desktop-data-sources.md)
* [Formatar e combinar dados com o Power BI Desktop](desktop-shape-and-combine-data.md)
* [Conectar-se a pastas de trabalho do Excel no Power BI Desktop](desktop-connect-excel.md)   
* [Inserir dados diretamente no Power BI Desktop](desktop-enter-data-directly-into-desktop.md)   
