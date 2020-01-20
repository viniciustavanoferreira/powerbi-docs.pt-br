---
title: Conectar-se ao warehouse de computação Snowflake no Power BI Desktop
description: Conecte-se facilmente e use um depósito de computação Snowflake no Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: a62d1cf6d21df822265c3c41d4e74e74181b7051
ms.sourcegitcommit: 801d2baa944469a5b79cf591eb8afd18ca4e00b1
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75885216"
---
# <a name="connect-to-a-snowflake-computing-warehouse-in-power-bi-desktop"></a>Conectar-se a um depósito de computação Snowflake no Power BI Desktop
No Power BI Desktop, você pode se conectar a um depósito de computação **Snowflake** e usar os dados subjacentes, assim como qualquer outra fonte de dados no Power BI Desktop. 

> [!NOTE]
> Você também *deve* instalar o **driver ODBC Snowflake** em computadores que usam o conector **Snowflake** ao usar a arquitetura que corresponde à instalação do **Power BI Desktop**, 32 bits ou 64 bits. Basta seguir o link a seguir e [baixar o driver ODBC Snowflake apropriado](https://go.microsoft.com/fwlink/?LinkID=823762).
> 
> 

## <a name="connect-to-a-snowflake-computing-warehouse"></a>Conectar-se a um depósito de computação Snowflake
Para conectar-se a um depósito de computação **Snowflake**, selecione **Obter Dados** na faixa de opções **Página Inicial** no Power BI Desktop. Selecione **Banco de dados** nas categorias à esquerda e você verá **Snowflake**.

![](media/desktop-connect-snowflake/connect_snowflake_2b.png)

Na janela **Snowflake** que será exibida, digite ou cole o nome do depósito de computação Snowflake na caixa e selecione **OK**. Observe que você pode escolher **Importar** dados diretamente no Power BI ou pode usar o **DirectQuery**. Você pode aprender mais à respeito [usando o DirectQuery](desktop-use-directquery.md).

![](media/desktop-connect-snowflake/connect_snowflake_3.png)

Quando solicitado, insira o nome de usuário e a senha.

![](media/desktop-connect-snowflake/connect-snowflake-4.png)

> [!NOTE]
> Quando você insere seu nome de usuário e senha para um servidor **Snowflake** específico, o Power BI Desktop usa as mesmas credenciais em tentativas de conexão subsequentes. Você pode modificar essas credenciais indo para **Arquivo > Opções e configurações > Configurações de fonte de dados**.
> 
> 

Caso você deseje usar a opção da conta Microsoft, solicite ao administrador do Snowflake que entre em contato com a Snowflake para obter informações sobre como participar da versão prévia privada desse recurso.

![Tipo de autenticação da conta Microsoft no conector do Snowflake.](media/desktop-connect-snowflake/connect-snowflake-6.png)


Depois que você se conectar com êxito, uma janela **Navegador** será mostrada e exibirá os dados disponíveis no servidor, dentre os quais você pode selecionar um ou vários elementos para importar e usar no **Power BI Desktop**.

![Erro 28000 do ODBC causando uma falha na conexão.](media/desktop-connect-snowflake/connect_snowflake_5.png)

Você pode **Carregar** a tabela selecionada, que leva toda a tabela para o **Power BI Desktop** ou você pode **Editar** a consulta, o que abre **Editor de Consultas** para filtrar e refinar o conjunto de dados que você deseja usar e, em seguida, carregar tal conjunto de dados refinado no **Power BI Desktop**.

## <a name="next-steps"></a>Próximas etapas
Há todos os tipos de dados aos quais você pode se conectar usando o Power BI Desktop. Para obter mais informações sobre fontes de dados, confira os seguintes recursos:

* [O que é o Power BI Desktop?](desktop-what-is-desktop.md)
* [Fontes de dados no Power BI Desktop](desktop-data-sources.md)
* [Formatar e combinar dados com o Power BI Desktop](desktop-shape-and-combine-data.md)
* [Conectar-se a pastas de trabalho do Excel no Power BI Desktop](desktop-connect-excel.md)   
* [Inserir dados diretamente no Power BI Desktop](desktop-enter-data-directly-into-desktop.md)   

