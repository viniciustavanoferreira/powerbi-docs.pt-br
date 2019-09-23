---
title: Usar o Conector SAP BW no Power BI Desktop
description: Usar o Conector SAP BW no Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: af227d2bcbbba2a27804ec74f14003f54aa89dde
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "65514690"
---
# <a name="use-the-sap-bw-connector-in-power-bi-desktop"></a>Usar o Conector SAP BW no Power BI Desktop
Com o Power BI Desktop, você pode acessar os dados do **SAP BW (Business Warehouse)** .

Para saber mais sobre como os clientes da SAP podem se beneficiar conectando o Power BI aos sistemas SAP BW (Business Warehouse) existentes deles, veja o [white paper Power BI e SAP BW](https://aka.ms/powerbiandsapbw). Para obter detalhes de como usar o DirectQuery com o SAP BW, confira o artigo [DirectQuery e SAP BW (Business Warehouse)](desktop-directquery-sap-bw.md).

A partir da versão de junho de 2018 do **Power BI Desktop** (e em disponibilidade geral na versão de outubro de 2018), é possível usar o conector do SAP BW com uma implementação com melhorias significativas para o desempenho e as funcionalidades. Essa versão atualizada do conector do SAP BW foi desenvolvida pela Microsoft e chama-se **Implementação 2.0**. Você pode selecionar a versão 1 (v1) do **Conector do SAP BW** ou o **Conector do SAP da Implementação 2.0**. As seções a seguir descrevem a instalação de cada versão, uma de cada vez. Você pode escolher um dos dois conectores para conectar-se ao SAP BW do Power BI Desktop.

Sugerimos que você use o **Conector do SAP da Implementação 2.0** sempre que possível.

## <a name="installation-of-version-1-of-the-sap-bw-connector"></a>Instalação da versão 1 do Conector do SAP BW
É recomendável usar o Conector do SAP da Implementação 2.0 sempre que possível (veja as instruções na seção a seguir). Esta seção descreve a instalação da versão 1 do **Conector do SAP BW**, que pode ser instalado executando as seguintes etapas de instalação:

1. Instale a biblioteca do **SAP NetWeaver** em seu computador local. É possível obter a biblioteca do **SAP Netweaver** do administrador do SAP ou diretamente do [Centro de Download de Software SAP](https://support.sap.com/swdc). Como o **Centro de Download de Software SAP** altera sua estrutura com frequência, não estão disponíveis diretrizes mais específicas para navegar nesse site. A biblioteca do **SAP NetWeaver** geralmente é incluída também na instalação do SAP Client Tools.
   
   Talvez seja possível pesquisar *SAP Note #1025361* para obter o local de download da versão mais recente. Verifique se a arquitetura da biblioteca **SAP NetWeaver** (32 bits ou 64 bits) corresponde a sua instalação do **Power BI Desktop** e instale todos os arquivos incluídos no **SDK do SAP NetWeaver RFC** de acordo com a Observação SAP.
2. A caixa de diálogo **Obter Dados** inclui uma entrada para o **Servidor de Aplicativos SAP Business Warehouse** e o **Servidor de Mensagens SAP Business Warehouse** na categoria **Banco de dados**.
   
   ![Opções de Obter Dados para o SAP](media/desktop-sap-bw-connector/sap_bw_2a.png)

## <a name="installation-of-implementation-20-sap-connector"></a>Instalação do Conector do SAP da Implementação 2.0

A **Implementação 2.0** do Conector do SAP exige o SAP .NET Connector 3.0. Você pode [baixar o SAP .NET Connector 3.0](https://support.sap.com/en/product/connectors/msnet.html) no site da SAP usando o seguinte link:

* [SAP .NET Connector 3.0](https://support.sap.com/en/product/connectors/msnet.html)

O acesso ao download requer um usuário S válido. É recomendado que os clientes contatem a equipe de base do SAP para obter o SAP .NET Connector 3.0. 

O conector é fornecido nas versões de 32 bits e 64 bits e os usuários *precisam* escolher a versão que corresponde às suas instalações do Power BI Desktop. No momento da escrita deste artigo, o site lista duas versões (para .NET 4.0 Framework):

* SAP Connector for Microsoft .NET 3.0.20.0 para Windows de 32 bits (x86) como um arquivo zip (6,896 KB), 16 de janeiro de 2018
* SAP Connector for Microsoft .NET 3.0.20.0 para Windows de 64 bits (x64) como um arquivo zip (7,180 KB), 16 de janeiro de 2018

Durante a instalação, na janela **Etapas de configuração opcionais**, selecione a opção *Instalar assemblies no cache de assembly global*, conforme é mostrado na imagem a seguir.

![Etapas de configuração opcionais do SAP](media/desktop-sap-bw-connector/sap_bw_2b.png)

> [!NOTE]
> A primeira versão da implementação do SAP BW exige DLLs do Netweaver. Se você estiver usando a Implementação 2.0 do Conector do SAP e não a primeira versão, as DLLs do Netweaver não serão necessárias.


## <a name="version-1-sap-bw-connector-features"></a>Recursos da versão 1 do Conector do SAP BW
A versão 1 do **Conector do SAP BW** no Power BI Desktop permite que você importe dados dos cubos do **Servidor SAP Business Warehouse** ou use o DirectQuery. 

Para saber mais sobre o **conector do SAP BW** e como usá-lo com DirectQuery, veja o artigo [DirectQuery e SAP BW (Business Warehouse)](desktop-directquery-sap-bw.md).

Para estabelecer a conexão, você deve especificar um *Servidor*, um *Número do Sistema* e uma *ID do Cliente*.

![Configurações de conexão do servidor SAP](media/desktop-sap-bw-connector/sap_bw_3a.png)

Também é possível especificar duas **Opções avançadas** adicionais: Código da linguagem e uma instrução MDX personalizada a ser executada no servidor especificado.

![informações de conexão adicionais](media/desktop-sap-bw-connector/sap_bw_4a.png)

Se nenhuma instrução MDX foi especificada, você vê a janela do **Navegador**, que exibe a lista de cubos disponíveis no servidor com a opção de fazer uma busca detalhada de itens dos cubos disponíveis, incluindo dimensões e medidas. O Power BI expõe consultas e cubos expostos pelos [BAPIs OLAP da Interface de Análise Aberta do BW](https://help.sap.com/saphelp_nw70/helpdata/en/d9/ed8c3c59021315e10000000a114084/content.htm).

Ao selecionar um ou mais itens do servidor, uma visualização da tabela de saída é criada, com base em sua seleção.

![Visualização de tabela do SAP](media/desktop-sap-bw-connector/sap_bw_5.png)

A janela do **Navegador** também fornece algumas **Opções de Exibição** que permitem fazer o seguinte:

* **Exibir *Somente os itens selecionados* versus *Todos os itens* (exibição padrão):** essa opção é útil para verificar o conjunto final de itens selecionados. Uma abordagem alternativa para exibir isso é selecionar os *Nomes de Coluna* na área *Visualização*.
* **Habilitar visualizações de dados (comportamento padrão):** também é possível controlar se as visualizações de dados devem ser exibidas nesta caixa de diálogo. A desabilitação das visualizações de dados reduz a quantidade de chamadas do servidor, pois ele não solicita dados para as visualizações.
* **Nomes técnicos:** o SAP BW dá suporte ao conceito de *nomes técnicos* para objetos em um cubo. Os nomes técnicos permitem que um proprietário de cubo exponha nomes *amigáveis* para objetos do cubo, em vez de apenas expor os *nomes físicos* desses objetos no cubo.

![a janela Navegador](media/desktop-sap-bw-connector/sap_bw_6.png)

Depois de selecionar todos os objetos necessários no **Navegador**, é possível decidir o que fazer em seguida selecionando um dos seguintes botões na parte inferior da janela do **Navegador**:

* A seleção de **Carga** dispara o carregamento de todo o conjunto de linhas para a tabela de saída no modelo de dados do Power BI Desktop e, em seguida, o leva para a visualização **Relatório**, em que é possível começar a visualizar dados ou fazer modificações adicionais usando as exibições de **Dados** ou **Relações**.
* A seleção de **Editar** mostra o **Editor de Consultas**, em que é possível executar a transformação de dados adicional e as etapas de filtragem antes que todo o conjunto de linhas seja colocado no modelo de dados do Power BI Desktop.

Além de importar dados de cubos do **SAP BW**, lembre-se de que também é possível importar dados de uma ampla variedade de fontes de dados no Power BI Desktop e combiná-los em um único relatório. Isso apresenta todos os tipos de cenários interessantes para relatórios e análises dos dados do **SAP BW**.

## <a name="using-implementation-20-sap-bw-connector"></a>Usando o Conector do SAP BW da Implementação 2.0

Você precisa criar uma nova conexão para usar a Implementação 2.0 do Conector do SAP BW. Para criar uma nova conexão, execute as etapas a seguir.

1. Na janela **Obter dados**, selecione o **Servidor de Aplicativos do SAP Business Warehouse** ou o **Servidor de Mensagem do SAP Business Warehouse**.

2. Será exibida uma caixa de diálogo da nova conexão permitindo a seleção da implementação. A seleção da **Implementação 2.0**, conforme é mostrado na imagem a seguir, permite as opções Modo de execução, Tamanho do lote e Habilitar estruturas características.

    ![Caixa de diálogo de conexão do SAP](media/desktop-sap-bw-connector/sap_bw_7.png)

3. Selecione **OK** e, em seguida, a experiência com o **Navegador** será a mesma que a descrita na seção anterior para a versão 1 do Conector do SAP BW. 

### <a name="new-options-for-implementation-20"></a>Novas opções da Implementação 2.0 

A Implementação 2.0 é compatível as seguintes opções:

1. **ExecutionMode** – especifica a interface MDX usada para executar consultas no servidor. As opções válidas são as seguintes:

        a. SapBusinessWarehouseExecutionMode.BasXml
        b. SapBusinessWarehouseExecutionMode.BasXmlGzip
        c. SapBusinessWarehouseExecutionMode.DataStream

    O valor padrão dessa opção é SapBusinessWarehouseExecutionMode.BasXmlGzip.

    O uso de *SapBusinessWarehouseExecutionMode.BasXmlGzip* pode melhorar o desempenho em momentos de alta latência para grandes conjuntos de dados.

2. **BatchSize** – especifica o número máximo de linhas que serão recuperadas de cada vez ao executar uma instrução MDX. Um número pequeno de linhas causará mais chamadas para o servidor ao recuperar um conjunto de dados grande. Um número grande de linhas pode melhorar o desempenho, mas pode causar problemas de memória no servidor do SAP BW. O valor padrão é 50000 linhas.

3. **EnableStructures** – um valor lógico que indica se a estruturas características são reconhecidas. O valor padrão dessa opção é false. Afeta a lista de objetos disponíveis para seleção. Não é compatível com o modo de consulta nativa.

A opção **ScaleMeasures** foi preterida nesta implementação. O comportamento agora é igual ao da configuração *ScaleMeasures = false*, que sempre mostra valores fora de escala.

### <a name="additional-improvements-for-implementation-20"></a>Melhorias adicionais para a Implementação 2.0 

A lista com marcadores a seguir descreve algumas das melhorias adicionais fornecidas com a nova implementação:

* Melhoria do desempenho
* Capacidade de recuperar milhões de linhas de dados e fazer um ajuste fino por meio do parâmetro de tamanho do lote.
* Capacidade de alternar os modos de execução.
* Suporte para o modo compactado. Principalmente útil para conexões de alta latência ou grandes conjuntos de dados.
* Melhoria na detecção de variáveis de data
* [Experimental] As dimensões Expor Data (tipo ABAP DATS) e Tempo (tipo ABAP TIMS), como datas e horas, respectivamente, em vez de valores de texto.
* Melhoria no tratamento de exceção. Os erros que ocorrem em chamadas BAPI agora são apresentados.
* Particionamento de coluna nos modos BasXml e BasXmlGzip. Por exemplo, se a consulta MDX gerada recuperar 40 colunas, mas a seleção atual precisar apenas de 10, essa solicitação será passada para o servidor para recuperar um conjunto de dados menor.


### <a name="changing-existing-reports-to-use-implementation-20"></a>Alterar os relatórios existentes para usar a Implementação 2.0 

A alteração dos relatórios existentes para usar a **Implementação 2.0** é possível somente no modo de importação e exige as seguintes etapas manuais.

1. Abra um relatório existente, selecione **Editar Consultas** na faixa de opções e, em seguida, selecione a consulta do SAP Business Warehouse que deseja atualizar.

2. Clique com o botão direito do mouse na consulta e selecione **Editor Avançado**.

3. No **Editor Avançado** altere a chamada SapBusinessWarehouse.Cubes da seguinte maneira: 

    a. Determine se a consulta já contém um registro de opção, como o que é mostrado no exemplo a seguir:

    ![snippet de consulta](media/desktop-sap-bw-connector/sap_bw_9.png)

    b. Se sim, adicione a opção Implementação 2.0 e remova a opção ScaleMeasures, se presente, conforme é mostrado:

    ![snippet de consulta](media/desktop-sap-bw-connector/sap_bw_10.png)

    c. Se a consulta ainda não incluir um registro de opções, adicione-o. Por exemplo, se ela tiver o seguinte:

    ![snippet de consulta](media/desktop-sap-bw-connector/sap_bw_11.png)

    d. Altere-o para:

    ![snippet de consulta](media/desktop-sap-bw-connector/sap_bw_12.png)

4. Foram aplicados todos os esforços necessários para tornar a Implementação 2.0 do Conector do SAP BW compatível com a versão 1 do Conector do SAP BW. No entanto, poderá haver algumas diferenças devido aos diferentes modos de execução de MDX do SAP BW que estejam sendo usados. Para resolver conflitos, tente alternar entre os modos de execução.

## <a name="troubleshooting"></a>Solução de problemas
Esta seção fornece situações de solução de problemas (e soluções) para trabalhar com o conector do **SAP BW**.

1. Dados numéricos do **SAP BW** retorna pontos decimais em vez de vírgulas. Por exemplo, 1,000,000 é retornado como 1.000.000.
   
   O **SAP BW** retorna dados decimais com uma *,* (vírgula) ou um *.* (ponto) como separador decimal. Para especificar quais desses **SAP BW** você deve usar como separador decimal, o driver usado pelo **Power BI Desktop** faz uma chamada para *BAPI_USER_GET_DETAIL*. Essa chamada retorna uma estrutura chamada **PADRÕES**, que tem um campo chamado *DCPFM* que armazena *Notação de Formato Decimal*. Um dos três valores a seguir é usado:
   
       ‘ ‘ (space) = Decimal point is comma: N.NNN,NN
       'X' = Decimal point is period: N,NNN.NN
       'Y' = Decimal point is N NNN NNN,NN
   
   Clientes que relataram esse problema descobriram que a chamada para *BAPI_USER_GET_DETAIL* falha para um usuário específico (o usuário que está mostrando dados incorretos), com uma mensagem de erro semelhante à seguinte:
   
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
   
   Para resolver esse erro, os usuários devem solicitar ao administrador do SAP para conceder ao usuário SAPBW que está sendo usado no Power BI o direito de executar *BAPI_USER_GET_DETAIL*. Também vale a pena verificar se o usuário tem o valor *DCPFM* necessário, conforme descrito anteriormente nesta solução de problemas.
   
2. **Conectividade para consultas SAP BEx**
   
   É possível executar consultas **BEx** no Power BI Desktop habilitando uma propriedade específica, conforme mostrado na seguinte imagem:
   
   ![](media/desktop-sap-bw-connector/sap_bw_8.png)
   
3. A janela **Navegador** não exibe uma visualização dos dados. Em vez disso, ela fornece a mensagem de erro *Referência de objeto não definida para uma instância de um objeto*.
   
   Os usuários SAP precisam acessar módulos de função BAPI específicos para obter metadados e recuperar dados de InfoProviders do SAP BW. Elas incluem:
   * BAPI_MDPROVIDER_GET_CATALOGS
   * BAPI_MDPROVIDER_GET_CUBES
   * BAPI_MDPROVIDER_GET_DIMENSIONS
   * BAPI_MDPROVIDER_GET_HIERARCHYS
   * BAPI_MDPROVIDER_GET_LEVELS
   * BAPI_MDPROVIDER_GET_MEASURES
   * BAPI_MDPROVIDER_GET_MEMBERS
   * BAPI_MDPROVIDER_GET_VARIABLES
   * BAPI_IOBJ_GETDETAIL

   Para resolver esse problema, verifique se o usuário tem acesso aos vários módulos *MDPROVIDER*, bem como *BAPI_IOBJ_GETDETAIL*. Para solucionar este problema ou problemas semelhantes, selecione *Habilitar o rastreamento*, na janela *Diagnóstico*, nas *Opções* do Power BI Desktop. Tente recuperar dados do SAP BW enquanto o rastreio estiver ativo e examine o arquivo de rastreamento para obter mais detalhes.

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
|Power BI Gateway     |DirectQuery | Opção Usar SSO via Kerberos para consultas do DirectQuery | Servidor de Aplicativos | *somente com* gsskrb5/gx64krb5   | Sim  |
|Power BI Gateway     |DirectQuery | Usuário/senha        | Servidor de mensagens | N/D  | Sim  |
|Power BI Gateway     |DirectQuery | Windows por meio de representação (usuário fixo, sem SSO) | Servidor de mensagens | sapcrypto + gsskrb5/gx64krb5  | Sim  |
|Power BI Gateway     |DirectQuery | Opção Usar SSO via Kerberos para consultas do DirectQuery | Servidor de mensagens | sapcrypto + gsskrb5/gx64krb5  | Não  |



## <a name="next-steps"></a>Próximas etapas
Para obter mais informações sobre o SAP e o DirectQuery, confira os seguintes recursos:

* [DirectQuery e SAP HANA](desktop-directquery-sap-hana.md)
* [DirectQuery e SAP BW (Business Warehouse)](desktop-directquery-sap-bw.md)
* [DirectQuery no Power BI](desktop-directquery-about.md)
* [Fontes de dados com suporte do DirectQuery](desktop-directquery-data-sources.md)
* [White paper Power BI e SAP BW](https://aka.ms/powerbiandsapbw)
