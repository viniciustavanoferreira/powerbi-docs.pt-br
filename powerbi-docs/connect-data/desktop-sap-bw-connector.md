---
title: Usar o Conector SAP BW (Business Warehouse) no Power BI Desktop
description: Usar o Conector SAP BW no Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/13/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: a28ed76238e9caff0b41f6c88e28f606cc420e1e
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83289754"
---
# <a name="use-the-sap-business-warehouse-connector-in-power-bi-desktop"></a>Usar o conector SAP Business Warehouse no Power BI Desktop

Com o Power BI Desktop, você pode acessar os dados do *SAP BW (Business Warehouse)* .

Para saber mais sobre como os clientes da SAP podem se beneficiar da conexão do Power BI aos sistemas SAP BW existentes deles, confira o [white paper Power BI e SAP BW](https://aka.ms/powerbiandsapbw). Para obter detalhes de como usar o DirectQuery com o SAP BW, confira [DirectQuery e SAP BW (Business Warehouse)](desktop-directquery-sap-bw.md).

A partir da versão de junho de 2018 do Power BI Desktop (e em disponibilidade geral desde outubro de 2018), é possível usar o *conector SAP BW* com uma implementação que apresenta melhora significativa no desempenho e nas funcionalidades. A Microsoft desenvolveu a *Implementação 2.0* do conector SAP BW. Você pode selecionar a versão 1 do Conector SAP BW ou o Conector SAP da Implementação 2.0. As seções a seguir descrevem a instalação de cada versão, uma de cada vez. Você pode escolher um dos dois conectores para conectar-se ao SAP BW do Power BI Desktop.

Sugerimos que você use o Conector SAP da Implementação 2.0 sempre que possível.

## <a name="installation-of-version-1-of-the-sap-bw-connector"></a>Instalação da versão 1 do Conector do SAP BW

Recomendamos usar o conector SAP da Implementação 2.0 sempre que possível. Esta seção descreve a instalação da versão 1 do conector SAP BW.

1. Instale a biblioteca do *SAP NetWeaver* em seu computador local. É possível obter a biblioteca do SAP NetWeaver do administrador do SAP ou diretamente do [Centro de Download de Software SAP](https://support.sap.com/swdc). Como o Centro de Download de Software SAP altera sua estrutura com frequência, não há diretrizes mais específicas disponíveis para navegar nesse site. A biblioteca do SAP NetWeaver geralmente está incluída na instalação do SAP Client Tools.

   Você pode pesquisar o *SAP Observação #1025361* para obter o local de download da versão mais recente. Verifique se a arquitetura da biblioteca SAP NetWeaver (32 bits ou 64 bits) corresponde à instalação do Power BI Desktop. Instale todos os arquivos incluídos no *SDK RFC do SAP NetWeaver* de acordo com a Nota SAP.
2. No Power BI Desktop, selecione **Obter Dados**. As opções de **Banco de Dados** incluem o *Servidor de Aplicativos SAP Business Warehouse* e o *Servidor de Mensagens SAP Business Warehouse*.

   ![Opções de Obter Dados para o SAP](media/desktop-sap-bw-connector/sap_bw_2a.png)

## <a name="installation-of-implementation-20-sap-connector"></a>Instalação do Conector do SAP da Implementação 2.0

A Implementação 2.0 do Conector SAP exige o SAP .NET Connector 3.0. O acesso ao download requer um usuário S válido. Entre em contato com sua equipe do SAP Basis para obter o Conector do SAP .NET 3.0.

Você pode baixar o [SAP .NET Connector 3.0](https://support.sap.com/en/product/connectors/msnet.html) na SAP.

O conector é fornecido em versões de 32 bits e 64 bits. Escolha a versão que corresponde à sua instalação do Power BI Desktop. Atualmente, o site lista duas versões para o .NET 4.0 Framework:

* SAP Connector for Microsoft .NET 3.0.22.0 para Windows de 32 bits (x86) como um arquivo zip (6.896 KB), 1º de junho de 2019
* SAP Connector for Microsoft .NET 3.0.22.0 para Windows de 64 bits (x64) como um arquivo zip (7.180 KB), 1º de junho de 2019

Durante a instalação, em **Etapas de configuração opcionais**, não deixe de selecionar *Instalar assemblies no GAC*.

![Etapas de configuração opcionais do SAP](media/desktop-sap-bw-connector/sap_bw_2b.png)

> [!NOTE]
> A primeira versão da implementação do SAP BW exigia DLLs do NetWeaver. Se você está usando a implementação 2.0 do Conector SAP e não está usando a primeira versão, as DLLs do NetWeaver não são necessárias.

## <a name="version-1-sap-bw-connector-features"></a>Recursos da versão 1 do Conector do SAP BW

A versão 1 do Conector SAP BW no Power BI Desktop permite que você importe dados dos cubos do *Servidor SAP Business Warehouse* ou use o DirectQuery.

Para saber mais sobre o Conector SAP BW e como usá-lo com DirectQuery, confira [DirectQuery e SAP BW (Business Warehouse)](desktop-directquery-sap-bw.md).

Durante a conexão, especifique um **Servidor**, um **Número do Sistema** e uma **ID do Cliente** para estabelecê-la.

![Configurações de conexão do servidor SAP](media/desktop-sap-bw-connector/sap_bw_3a.png)

Também é possível especificar duas **Opções avançadas** adicionais: **Código da linguagem** e uma **instrução MDX** personalizada a ser executada no servidor especificado.

![informações de conexão adicionais](media/desktop-sap-bw-connector/sap_bw_4a.png)

Se você não especificar uma instrução MDX, a configuração de conexão exibirá a lista de cubos disponíveis no servidor. Você pode fazer uma busca detalhada e selecionar itens nos cubos disponíveis, incluindo dimensões e medidas. O Power BI expõe consultas e cubos expostos pelas [Interfaces de Análise Aberta](https://help.sap.com/saphelp_nw70/helpdata/en/d9/ed8c3c59021315e10000000a114084/content.htm).

Quando você seleciona um ou mais itens do servidor, o diálogo Navegador cria uma visualização da tabela de saída.

![Visualização de tabela do SAP](media/desktop-sap-bw-connector/sap_bw_5.png)

O diálogo **Navegador** também fornece opções de exibição:

* **Exibir somente os itens selecionados**. Por padrão, o **Navegador** exibe todos os itens.  essa opção é útil para verificar o conjunto final de itens selecionados. Uma abordagem alternativa para exibir os itens selecionados é selecionar os nomes de coluna na área de visualização.
* **Habilitar visualizações de dados**. Esse valor é o padrão. Exibir visualizações de dados. A desabilitação das visualizações de dados reduz a quantidade de chamadas do servidor, pois ele não solicita dados para as visualizações.
* **Nomes técnicos**. o SAP BW dá suporte ao conceito de *nomes técnicos* para objetos em um cubo. Os nomes técnicos permitem que o proprietário de um cubo exponha *nomes amigáveis* para objetos do cubo, em vez de apenas expor os *nomes físicos* desses objetos no cubo.

![a janela Navegador](media/desktop-sap-bw-connector/sap_bw_6.png)

Depois de selecionar todos os objetos necessários, você pode decidir o que fazer em seguida selecionando uma das seguintes opções:

* Selecione **Carregar** para carregar o conjunto inteiro de linhas que formará a tabela de saída no modelo de dados do Power BI Desktop. O modo de exibição **Relatório** é aberto. Você pode começar a visualizar os dados ou a fazer mais modificações por meio dos modos de exibição **Dados** ou **Relacionamentos**.
* Selecione **editar** para abrir o **Editor de Consultas**. Especifique as etapas adicionais de transformação e filtragem de dados antes que todo o conjunto de linhas seja trazido para o modelo de dados do Power BI Desktop.

Além de importar dados de cubos do SAP BW, também é possível importar dados de uma ampla variedade de fontes de dados no Power BI Desktop e combiná-los em um único relatório. Essa possibilidade viabiliza vários tipos de cenários interessantes para relatórios e análises dos dados do SAP BW.

## <a name="using-implementation-20-sap-bw-connector"></a>Usando o Conector do SAP BW da Implementação 2.0

Crie uma conexão para usar a Implementação 2.0 do Conector SAP BW. Para criar uma nova conexão, execute as etapas a seguir.

1. Selecione **Obter Dados**. Selecione o **Servidor de Aplicativos SAP Business Warehouse** ou o **Servidor de Mensagem SAP Business Warehouse** e conecte-se.

2. No diálogo da nova conexão, selecione a implementação. A seleção da **Implementação** **2.0**, conforme é mostrado na imagem a seguir, habilita as opções **Modo de execução**, **Tamanho do lote** e **Habilitar estruturas de característica**.

    ![Caixa de diálogo de conexão do SAP](media/desktop-sap-bw-connector/sap_bw_7.png)

3. Selecione **OK**. Daqui em diante, a experiência será a mesma descrita em [Recursos da Versão 1 do Conector SAP BW](#version-1-sap-bw-connector-features) para o Conector SAP BW da versão 1.

### <a name="new-options-for-implementation-20"></a>Novas opções da Implementação 2.0

A Implementação 2.0 é compatível as seguintes opções:

* *ExecutionMode* especifica a interface MDX usada para executar consultas no servidor. As seguintes opções são válidas:

  * `SapBusinessWarehouseExecutionMode.BasXml`
  * `SapBusinessWarehouseExecutionMode.BasXmlGzip`
  * `SapBusinessWarehouseExecutionMode.DataStream`

    O valor padrão é `SapBusinessWarehouseExecutionMode.BasXmlGzip`.

    O uso de `SapBusinessWarehouseExecutionMode.BasXmlGzip` pode melhorar o desempenho em períodos de alta latência envolvendo grandes conjuntos de dados.

* *BatchSize* especifica o número máximo de linhas que serão recuperadas de cada vez durante a execução de uma instrução MDX. Um número pequeno gerará mais chamadas para o servidor, mas recuperará um conjunto de dados grande. Um número grande de linhas pode melhorar o desempenho, mas pode causar problemas de memória no servidor do SAP BW. O valor padrão é 50000 linhas.

* *EnableStructures* indica se as estruturas de característica são reconhecidas. O valor padrão dessa opção é false. Afeta a lista de objetos disponíveis para seleção. Não é compatível com o modo de consulta nativa.

A opção *ScaleMeasures* foi preterida nesta implementação. O comportamento agora é igual ao de se configurar *ScaleMeasures* como false, sempre mostrando valores fora de escala.

### <a name="additional-improvements-for-implementation-20"></a>Melhorias adicionais para a Implementação 2.0

Esta lista descreve algumas das melhorias adicionais que a nova implementação apresenta:

* Desempenho aprimorado.
* Capacidade de recuperar milhões de linhas de dados e fazer um ajuste fino por meio do parâmetro de tamanho do lote.
* Capacidade de alternar os modos de execução.
* Suporte para o modo compactado. Principalmente útil para conexões de alta latência ou grandes conjuntos de dados.
* Melhoria na detecção de variáveis `Date`.
* [Experimental] Exposição das dimensões `Date` (tipo ABAP DATS) e `Time` (tipo ABAP TIMS), como datas e horas, respectivamente, em vez de valores de texto.
* Melhoria no tratamento de exceção. Os erros que ocorrem em chamadas BAPI agora são apresentados.
* Particionamento de coluna nos modos BasXml e BasXmlGzip. Por exemplo, se a consulta MDX gerada recuperar 40 colunas, mas a seleção atual precisar apenas de 10, essa solicitação será passada para o servidor para recuperar um conjunto de dados menor.

### <a name="changing-existing-reports-to-use-implementation-20"></a>Alterar os relatórios existentes para usar a Implementação 2.0

A alteração nos relatórios existentes para usar a Implementação 2.0 só é possível no modo de importação. Siga estas etapas:

1. Abra um relatório existente, selecione **Editar Consultas** na faixa de opções e selecione a consulta do SAP Business Warehouse a ser atualizada.

1. Clique com o botão direito do mouse na consulta e selecione **Editor Avançado**.

1. No **Editor Avançado**, altere a chamada `SapBusinessWarehouse.Cubes` da seguinte maneira:

    Determine se a consulta já contém um registro de opção, como o seguinte exemplo:

    ![snippet de consulta](media/desktop-sap-bw-connector/sap_bw_9.png)

    Se for o caso, adicione a opção `Implementation` 2.0 e remova a opção `ScaleMeasures`, se presente, conforme mostrado abaixo:

    ![snippet de consulta](media/desktop-sap-bw-connector/sap_bw_10.png)

    Se a consulta ainda não incluir um registro de opções, adicione-o. Para a seguinte opção:

    ![snippet de consulta](media/desktop-sap-bw-connector/sap_bw_11.png)

    Altere-o para:

    ![snippet de consulta](media/desktop-sap-bw-connector/sap_bw_12.png)

Todos os esforços necessários foram feitos para tornar a Implementação 2.0 do Conector SAP BW compatível com a versão 1. No entanto, poderá haver algumas diferenças por conta dos diferentes modos de execução de MDX do SAP BW que estejam sendo usados. Para resolver conflitos, tente alternar entre os modos de execução.

## <a name="troubleshooting"></a>Solução de problemas

Esta seção fornece hipóteses e soluções de problemas que podem ocorrer no trabalho com o conector SAP BW.

1. Dados numéricos do SAP BW retorna pontos decimais em vez de vírgulas. Por exemplo, 1,000,000 é retornado como 1.000.000.

   O SAP BW retorna dados decimais com uma `,` (vírgula) ou um `.` (ponto) como separador decimal. Para especificar quais desses o SAP BW deve usar como separador decimal, o driver usado pelo Power BI Desktop faz uma chamada para `BAPI_USER_GET_DETAIL`. Essa chamada retorna uma estrutura denominada `DEFAULTS`, que tem um campo chamado `DCPFM` que armazena *Notação de Formato Decimal*. O campo assume um dos seguintes valores:

   * ‘ ‘ (espaço) = ponto decimal é vírgula: N.NNN,NN
   * ‘X’ = ponto decimal é ponto: N,NNN.NN
   * ‘Y’ = ponto decimal é N NNN NNN,NN

   Os clientes que relataram esse problema descobriram que a chamada para `BAPI_USER_GET_DETAIL` falha para um usuário específico, que está mostrando dados incorretos, com uma mensagem de erro semelhante à seguinte:

   ```xml
    You are not authorized to display users in group TI:
        <item>
            <TYPE>E</TYPE>
            <ID>01</ID>
            <NUMBER>512</NUMBER>
            <MESSAGE>You are not authorized to display users in group TI</MESSAGE>
            <LOG_NO/>
            <LOG_MSG_NO>000000</LOG_MSG_NO>
            <MESSAGE_V1>TI</MESSAGE_V1>
            <MESSAGE_V2/>
            <MESSAGE_V3/>
            <MESSAGE_V4/>
            <PARAMETER/>
            <ROW>0</ROW>
            <FIELD>BNAME</FIELD>
            <SYSTEM>CLNTPW1400</SYSTEM>
        </item>
   ```

   Para resolver esse erro, os usuários deverão solicitar ao administrador do SAP para conceder ao usuário SAPBW que está sendo usado no Power BI o direito de executar `BAPI_USER_GET_DETAIL`. Também vale a pena verificar se o usuário tem o valor `DCPFM` necessário, conforme descrito anteriormente nesta solução de problemas.

2. Conectividade para consultas SAP BEx
   
   É possível executar consultas BEx no Power BI Desktop habilitando uma propriedade específica, conforme mostrado na seguinte imagem:
   
   ![Habilitar versão para acesso externo](media/desktop-sap-bw-connector/sap_bw_8.png)
   
3. A janela **Navegador** não exibe uma visualização dos dados. Em vez disso, ela fornece a mensagem de erro *Referência de objeto não definida para uma instância de um objeto*.
   
   Os usuários SAP precisam acessar módulos de função BAPI específicos para obter metadados e recuperar dados de InfoProviders do SAP BW. Esses módulos incluem:

   * BAPI_MDPROVIDER_GET_CATALOGS
   * BAPI_MDPROVIDER_GET_CUBES
   * BAPI_MDPROVIDER_GET_DIMENSIONS
   * BAPI_MDPROVIDER_GET_HIERARCHYS
   * BAPI_MDPROVIDER_GET_LEVELS
   * BAPI_MDPROVIDER_GET_MEASURES
   * BAPI_MDPROVIDER_GET_MEMBERS
   * BAPI_MDPROVIDER_GET_VARIABLES
   * BAPI_IOBJ_GETDETAIL

   Para resolver o problema, verifique se o usuário tem acesso aos vários módulos MDPROVIDER e a `BAPI_IOBJ_GETDETAIL`. Para solucionar o problema em questão ou problemas semelhantes, habilite o rastreamento. **Selecionar Arquivo** > **Opções e configurações** > **Opções**. Em **Opções**, selecione **Diagnóstico** e selecione **Habilitar rastreamento**. Tente recuperar dados do SAP BW enquanto o rastreio estiver ativo e examine o arquivo de rastreamento para obter mais detalhes.

## <a name="sap-bw-connection-support"></a>Suporte de Conexão do SAP BW

A tabela a seguir fornece detalhes sobre o suporte atual para o SAP BW.

|Produto  |Modo  |Autenticação  |Conector  |Biblioteca SNC  |Compatível  |
|---------|---------|---------|---------|---------|---------|
|Power BI Desktop     |Qualquer         | Usuário/senha  | Servidor de Aplicativos | N/D  | Sim  |
|Power BI Desktop     |Qualquer         | Windows          | Servidor de Aplicativos | sapcrypto + gsskrb5/gx64krb5  | Sim  |
|Power BI Desktop     |Qualquer         | Windows por meio de representação | Servidor de Aplicativos | sapcrypto + gsskrb5/gx64krb5  | Sim  |
|Power BI Desktop     |Qualquer         | Usuário/senha        | Servidor de mensagens | N/D  | Sim  |
|Power BI Desktop     |Qualquer         | Windows        | Servidor de mensagens | sapcrypto + gsskrb5/gx64krb5  | Sim  |
|Power BI Desktop     |Qualquer         | Windows por meio de representação | Servidor de mensagens | sapcrypto + gsskrb5/gx64krb5  | Sim  |
|Power BI Gateway     |Importar      | Semelhante ao Power BI Desktop |         |   |   |
|Power BI Gateway     |DirectQuery | Usuário/senha        | Servidor de Aplicativos | N/D  | Sim  |
|Power BI Gateway     |DirectQuery | Windows por meio de representação (usuário fixo, sem SSO) | Servidor de Aplicativos | sapcrypto + gsskrb5/gx64krb5  | Sim  |
|Power BI Gateway     |DirectQuery | Opção Usar SSO via Kerberos para consultas do DirectQuery | Servidor de Aplicativos | sapcrypto + gsskrb5/gx64krb5   | Sim  |
|Power BI Gateway     |DirectQuery | Usuário/senha        | Servidor de mensagens | N/D  | Sim  |
|Power BI Gateway     |DirectQuery | Windows por meio de representação (usuário fixo, sem SSO) | Servidor de mensagens | sapcrypto + gsskrb5/gx64krb5  | Sim  |
|Power BI Gateway     |DirectQuery | Opção Usar SSO via Kerberos para consultas do DirectQuery | Servidor de mensagens | gsskrb5/gx64krb5  | Não  |
|Power BI Gateway     |DirectQuery | Opção Usar SSO via Kerberos para consultas do DirectQuery | Servidor de mensagens | sapcrypto  | Sim  |

## <a name="next-steps"></a>Próximas etapas

Para obter mais informações sobre o SAP e o DirectQuery, confira os seguintes recursos:

* [DirectQuery e SAP HANA](desktop-directquery-sap-hana.md)
* [DirectQuery e SAP BW (Business Warehouse)](desktop-directquery-sap-bw.md)
* [Usar o DirectQuery no Power BI](desktop-directquery-about.md)
* [Fontes de dados do Power BI](power-bi-data-sources.md)
* [White paper Power BI e SAP BW](https://aka.ms/powerbiandsapbw)
