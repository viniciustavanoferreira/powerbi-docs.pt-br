---
title: Usar o SAP HANA no Power BI Desktop
description: Usar o SAP HANA no Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/15/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 9b205a0ae9b58acf054a9afe43196e77ee404c84
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83289110"
---
# <a name="connect-to-sap-hana-databases-in-power-bi-desktop"></a>Conectar-se a bancos de dados SAP HANA no Power BI Desktop

Com o Power BI Desktop, agora você pode acessar bancos de dados do *SAP HANA* . Para usar o SAP HANA, o driver ODBC do SAP HANA deve estar instalado no computador cliente local para que a conexão de dados do SAP HANA do Power BI Desktop funcione corretamente. Você pode baixar as ferramentas de cliente SAP HANA de [Ferramentas de Desenvolvimento SAP](https://tools.hana.ondemand.com/#hanatools), que contém o driver ODBC necessário. Outra opção é obtê-lo do [Centro de Download de Software SAP](https://support.sap.com/en/my-support/software-downloads.html). No portal de software, pesquise os computadores com Windows em *SAP HANA CLIENT*. Como o Centro de Download de Software SAP altera sua estrutura com frequência, não há diretrizes mais específicas disponíveis para navegar nesse site.

Para conectar-s a um banco de dados do SAP HANA, selecione **Obter dados**, escolha **Banco de Dados** > **Banco de Dados SAP HANA** e, em seguida, selecione **Conectar**:

![Banco de Dados SAP HANA, caixa de diálogo Obter Dados, Power BI Desktop](media/desktop-sap-hana/sap-hana-1.png)

Ao conectar-se a um Banco de dados do SAP HANA, especifique o nome do servidor. Em seguida, na lista suspensa da caixa de entrada, especifique a porta.

Nesta versão, o SAP HANA no modo [DirectQuery](desktop-directquery-sap-hana.md) é compatível com o Power BI Desktop e o serviço do Power BI. Você pode publicar e carregar relatórios que usam o SAP HANA no modo DirectQuery para o serviço do Power BI. Você também pode publicar e carregar relatórios no Serviço do Power BI quando não estiver usando o SAP HANA no modo DirectQuery.

## <a name="supported-features-for-sap-hana"></a>Recursos com suporte para o SAP HANA

Esta versão contém vários recursos para o SAP HANA, como mostrado na seguinte lista:

* O conector do Power BI para o SAP HANA usa o driver ODBC do SAP, para fornecer a melhor experiência de usuário.

* O SAP HANA dá suporte às opções de Importação e do DirectQuery.

* O Power BI é compatível com modelos de informação do HANA, como Exibições de Cálculo e Análise, e tem uma navegação otimizada.

* Com o SAP HANA, você também pode usar o recurso direto do SQL para se conectar às Tabelas de Linhas e Colunas.

* O Power BI inclui Navegação Otimizada para modelos do HANA.

* O Power BI é compatível com parâmetros de Variáveis e Entrada do SAP HANA.

* O Power BI é compatível com Exibições de Cálculo com base em contêiner do HDI.

  * O suporte para Exibições de Cálculo baseadas em contêiner do HDI está em versão prévia pública na versão de agosto de 2019 do Power BI Desktop. Para acessar suas Exibições de Cálculo baseadas em contêiner do HDI no Power BI, verifique se os usuários do banco de dados do HANA que você usa com o Power BI têm permissão para acessar o contêiner de runtime do HDI que armazena as exibições que você deseja acessar. Para conceder esse acesso, crie uma função que permita o acesso ao seu contêiner do HDI. Em seguida, atribua a função ao usuário do banco de dados do HANA que você usará com o Power BI. (Esse usuário também deve ter permissão para ler as tabelas do sistema no esquema do \_SYS\_BI, como de costume.) Leia a documentação oficial do SAP para obter instruções detalhadas sobre como criar e atribuir funções de banco de dados. [Esta postagem no blog do SAP](https://blogs.sap.com/2018/01/24/the-easy-way-to-make-your-hdi-container-accessible-to-a-classic-database-user/) pode ser um bom ponto de partida.

  * Atualmente há algumas limitações às variáveis do HANA anexadas a Exibições de Cálculo baseadas em HDI. Essas limitações são devido a erros no lado do HANA.
  
    Primeiro, não é possível aplicar uma variável do HANA a uma coluna compartilhada de uma Exibição de Cálculo baseada em contêiner do HDI. Para corrigir essa limitação, atualize para o HANA 2 versão 37.02 e posteriores ou para o HANA 2 versão 42 e posteriores. Segundo, valores padrão de várias entradas para variáveis e parâmetros atualmente não aparecem na interface do usuário do Power BI. Um erro no SAP HANA causa essa limitação, mas a SAP ainda não anunciou uma correção.

## <a name="limitations-of-sap-hana"></a>Limitações do SAP HANA

Também há algumas limitações no uso do SAP HANA, conforme mostrado abaixo:

* Cadeias de caracteres NVARCHAR são truncadas para um comprimento máximo de 4 mil caracteres Unicode.
* Não há suporte para SMALLDECIMAL.
* Não há suporte para VARBINARY.
* As Datas Válidas estão entre 30/12/1899 e 31/12/9999.

## <a name="next-steps"></a>Próximas etapas

Para obter mais informações sobre o SAP HANA e o DirectQuery, confira os seguintes recursos:

* [DirectQuery e SAP HANA](desktop-directquery-sap-hana.md)
* [Usar DirectQuery no Power BI](desktop-directquery-about.md)
* [Fontes de dados do Power BI](power-bi-data-sources.md)
* [Habilitar a criptografia para SAP HANA](desktop-sap-hana-encryption.md)
