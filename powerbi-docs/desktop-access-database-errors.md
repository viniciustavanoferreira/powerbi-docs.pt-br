---
title: Resolver problemas de importação do Access e .XLS no Power BI Desktop
description: Solucionar problemas de importação de bancos de dados do Access e planilhas .XLS no Power BI Desktop e Power Query
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 10/21/2019
ms.author: davidi
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 085a21404fefe214656f31d077c6cba401b8219e
ms.sourcegitcommit: 17f45a81b0dcbf9e3f1fb2a551584170baecd320
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72922539"
---
# <a name="resolve-issues-importing-access-and-xls-files-in-power-bi-desktop"></a>Resolver problemas de importação de arquivos do Access e .XLS no Power BI Desktop

No Power BI Desktop, os bancos de dados do Access e as versões anteriores de pastas de trabalho do Excel (arquivos .XLS do tipo Excel 97-2003) usam o *mecanismo de banco de dados do Access*. Há três situações comuns que podem impedir que o mecanismo de banco de dados do Access funcione corretamente.

## <a name="situation-1-no-access-database-engine-is-installed"></a>Situação 1: Nenhum mecanismo de banco de dados do Access instalado

Se a mensagem de erro do Power BI Desktop indicar que o mecanismo de banco de dados do Access não está instalado, instale a versão de 32 ou 64 bits do mecanismo de banco de dados do Access que corresponde à versão do Power BI Desktop. Instale o Mecanismo de Banco de Dados do Access na [página de downloads](http://www.microsoft.com/download/details.aspx?id=13255).

>[!NOTE]
>Se a versão de bits instalada do mecanismo de banco de dados do Access for diferente da versão de bits de instalação do Microsoft Office, os aplicativos do Office não poderão usar o mecanismo de banco de dados do Access.

## <a name="situation-2-the-access-database-engine-bit-version-32-bit-or-64-bit-is-different-from-your-power-bi-desktop-bit-version"></a>Situação 2: A versão de bits do mecanismo de banco de dados do Access (32 ou 64 bits) é diferente da versão de bits do Power BI Desktop

Essa situação geralmente ocorre quando a versão instalada do Microsoft Office é de 32 bits e a versão do Power BI Desktop instalada é de 64 bits. O oposto pode ocorrer também e a incompatibilidade de versão de bits ocorrerá em ambos os casos. Se você estiver usando uma assinatura do Office 365, confira a [Situação 3](#situation-3-trouble-using-access-or-xls-files-with-an-office-365-subscription) para ver um problema diferente e a resolução. Qualquer uma das seguintes soluções pode corrigir esse erro de incompatibilidade de versão de bits:

### <a name="solution-1"></a>Solução 1

Altere a versão do Power BI Desktop para corresponder à versão de bits de instalação do Microsoft Office. 

1. Para alterar a versão de bits do Power BI Desktop, desinstale o Power BI Desktop e, em seguida, instale a versão do Power BI Desktop que corresponde à sua instalação do Office. 

1. Para selecionar uma versão do Power BI Desktop, selecione **Opções de download avançadas** na página de download do Power BI Desktop.
   
   ![Opções de download avançadas na página de download do Power BI Desktop](media/desktop-access-database-errors/desktop-access-errors-1.png)
   
1. Na página de download que é exibida, escolha o idioma e selecione o botão **Baixar** . 
 
1. Na tela exibida, marque a caixa de seleção ao lado de PBIDesktop.msi para a versão de 32 bits ou PBIDesktop_x64.msi para a versão de 64 bits. 

   Na captura de tela a seguir, a versão de 64 bits é selecionada.
   
   ![Escolher o tipo de download do Power BI Desktop](media/desktop-access-database-errors/desktop-access-errors-2.png)
   
   >[!NOTE]
   >Se você usar a versão de 32 bits do Power BI Desktop ao criar modelos de dados muito grandes, poderá ter problemas de memória insuficiente.

### <a name="solution-2"></a>Solução 2

Altere a versão de bits do Microsoft Office para que corresponda à versão de bits da instalação do Power BI Desktop:

1. Desinstalar o Microsoft Office

2. Instale a versão do Office que corresponde à instalação do Power BI Desktop.

### <a name="solution-3"></a>Solução 3

Se o erro ocorrer quando você tentar abrir um arquivo .XLS (uma pasta de trabalho do Excel 97-2003), evite o uso do mecanismo de banco de dados do Access abrindo o arquivo .XLS no Excel e salvando-o como um arquivo XLSX.

### <a name="solution-4"></a>Solução 4

Se as três soluções anteriores não forem viáveis, será possível instalar as duas versões do mecanismo de banco de dados do Access. No entanto, essa solução alternativa não é recomendada. Embora a instalação das duas versões resolva esse problema para o Power Query para Excel e o Power BI Desktop, ela apresentará erros e problemas em qualquer aplicativo que usa automaticamente (por padrão) a versão de bits do mecanismo de banco de dados do Access que foi instalada primeiro. 

Para instalar as duas versões de bits do mecanismo de banco de dados do Access, siga estas etapas:

1. Instale as duas versões de bits do mecanismo de banco de dados do Access na [página de download](http://www.microsoft.com/download/details.aspx?id=13255). 

1. Execute cada versão do mecanismo de banco de dados do Access usando a opção */passive*. Por exemplo:
   
       c:\users\joe\downloads\AccessDatabaseEngine.exe /passive
   
       c:\users\joe\downloads\AccessDatabaseEngine_x64.exe /passive

## <a name="situation-3-trouble-using-access-or-xls-files-with-an-office-365-subscription"></a>Situação 3: Problemas para utilizar o Access ou arquivos .XLS com uma assinatura do Office 365

Se você estiver usando uma assinatura do Office 365, **Office 2013** ou **Office 2016**, o provedor do mecanismo de banco de dados do Access será registrado em uma localização do Registro virtual que *só* pode ser acessada pelos processos do Microsoft Office. Como resultado, o Mecanismo de Mashup (que é responsável por executar o Excel fora do Office 365 e o Power BI Desktop e não é um processo do Office) não pode usar o provedor do mecanismo de banco de dados do Access.

Para corrigir essa situação, [baixe e instale o componente redistribuível do mecanismo de banco de dados do Access](http://www.microsoft.com/download/details.aspx?id=13255) que corresponde à versão de bits da instalação do Power BI Desktop. Para obter mais informações sobre versões de bits, confira as seções anteriores deste artigo.

## <a name="other-situations-that-can-cause-import-issues"></a>Outras situações que podem causar problemas de importação

Nos esforçamos para abordar o máximo possível de problemas que ocorrem com o Access ou com arquivos XLS. Se você encontrar um problema que não foi abordado neste artigo, envie uma pergunta sobre o problema para o [suporte do Power BI](https://powerbi.microsoft.com/support/). Examinamos regularmente os problemas que podem estar afetando muitos clientes, posteriormente incluindo-os em nossos artigos.

