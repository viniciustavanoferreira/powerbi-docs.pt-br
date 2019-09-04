---
title: Conectar-se a um banco de dados Oracle
description: Etapas e downloads necessários para conectar o Oracle ao Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 08/29/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 3dce16287c9cdcb7882e332e338137f7598b4010
ms.sourcegitcommit: a00fe5fb545c3df13b7cd13a701fd6a2b2521a17
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70200895"
---
# <a name="connect-to-an-oracle-database"></a>Conectar-se a um banco de dados Oracle
Para se conectar a um banco de dados Oracle com o **Power BI Desktop**, o software cliente Oracle correto deve estar instalado no computador que executa o Power BI Desktop. O software cliente Oracle que você usa depende de qual versão do Power BI Desktop está instalada – a versão de **32 bits** ou a de **64 bits**.

**Versões compatíveis**: Oracle 9 e versões posteriores, software cliente Oracle 8.1.7 e versões posteriores.

## <a name="determining-which-version-of-power-bi-desktop-is-installed"></a>Determinando qual versão do Power BI Desktop está instalada
Para determinar qual versão do Power BI Desktop está instalada, selecione **Arquivo > Ajuda > Sobre** e, em seguida, verifique a linha **Versão:** . Na imagem a seguir, uma versão de 64 bits do Power BI Desktop está é instalada:

![](media/desktop-connect-oracle-database/connect-oracle-database_1.png)

## <a name="installing-the-oracle-client"></a>Instalando o cliente Oracle
Para versões de **32 bits** do Power BI Desktop, use o seguinte link para baixar e instalar o cliente Oracle de **32 bits**:

* [ODAC (Oracle Data Access Components) de 32 bits com Ferramentas de desenvolvimento da Oracle para Visual Studio (12.1.0.2.4)](http://www.oracle.com/technetwork/topics/dotnet/utilsoft-086879.html)

Para versões de **64 bits** do Power BI Desktop, use o seguinte link para baixar e instalar o cliente Oracle de **64 bits**:

* [ODAC de 64 bits 12c, versão 4 (12.1.0.2.4) para Windows x64](http://www.oracle.com/technetwork/database/windows/downloads/index-090165.html)

## <a name="connect-to-an-oracle-database"></a>Conectar-se a um banco de dados Oracle
Depois de instalar o driver de cliente Oracle correspondente, você pode se conectar a um banco de dados Oracle. Para fazer a conexão, execute as seguintes etapas:

1. Na janela Obter Dados, selecione **Banco de Dados > Banco de Dados Oracle**
   
   ![](media/desktop-connect-oracle-database/connect-oracle-database_2.png)
2. Na caixa de diálogo **Banco de Dados Oracle** que aparece, forneça o nome do servidor e selecione **Conectar**. Se for necessário um SID, você pode especificá-lo usando o formato: *ServerName/SID*, em que o SID é o nome exclusivo do banco de dados. Se o formato *ServerName/SID* não funcionar, tente usar *ServerName/ServiceName*, em que ServiceName é o alias usado na conexão.


   ![](media/desktop-connect-oracle-database/connect-oracle-database_3.png)

   > [!TIP]
   > Se você estiver com problemas para conectar-se nesta etapa, tente usar o formato a seguir no campo nome do servidor: (DESCRIPTION=(ADDRESS=(PROTOCOL=TCP)(HOST=host_name)(PORT=port_num))(CONNECT_DATA=(SERVICE_NAME=service_name)))
   
3. Se desejar importar dados usando uma consulta de banco de dados nativo, você pode colocar sua consulta na caixa **Instrução SQL**, disponível ao expandir a seção **Opções avançadas** da caixa de diálogo **Banco de Dados Oracle**.
   
   ![](media/desktop-connect-oracle-database/connect-oracle-database_4.png)
4. Após as informações do seu banco de dados Oracle serem inseridas na caixa de diálogo Banco de Dados Oracle (incluindo informações opcionais, como um SID ou uma consulta de banco de dados nativo), selecione **OK** para se conectar.
5. Se o banco de dados Oracle exigir credenciais de usuário do banco de dados, insira as credenciais na caixa de diálogo quando solicitado.


## <a name="troubleshooting"></a>Solução de problemas

Se você baixou o Power BI Desktop da Microsoft Store, talvez não possa se conectar aos bancos de dados Oracle devido a um problema de driver do Oracle. Se você encontrar esse problema, a mensagem de erro retornada será "Referência de objeto não definida". Para resolver o problema, siga um destes procedimentos:

* Baixe o Power BI Desktop pela https://powerbi.microsoft.com/desktop.

* Se desejar usar a versão da Microsoft Store: no computador local, copie oraons.dll de _12.X.X\client_X_ para _12.X.X\client_X\bin_. O X representa números de versão e diretório.

Se você vir a mensagem de erro *Referência de objeto não definida* no Power BI Gateway ao se conectar a um banco de dados Oracle, talvez seja possível resolver o problema seguindo as instruções encontradas no artigo [Gerenciar sua fonte de dados – Oracle](service-gateway-onprem-manage-oracle.md).
