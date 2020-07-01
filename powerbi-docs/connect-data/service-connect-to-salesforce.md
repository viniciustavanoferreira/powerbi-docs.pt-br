---
title: Conectar-se ao Salesforce com o Power BI
description: Salesforce para o Power BI
author: SarinaJoan
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: how-to
ms.date: 05/30/2019
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: 41d5350bf2986f9b8f0f01acf97e96eafc3b4db8
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85229503"
---
# <a name="connect-to-salesforce-with-power-bi"></a>Conectar-se ao Salesforce com o Power BI
Com o Power BI, você pode se conectar facilmente à sua conta do Salesforce.com. Com essa conexão, você pode recuperar os dados do Salesforce e ter um dashboard e relatórios automaticamente fornecidos.

Leia mais sobre a [Integração do Salesforce](https://powerbi.microsoft.com/integrations/salesforce) com o Power BI.

## <a name="how-to-connect"></a>Como se conectar
1. No Power BI, selecione **Obter Dados** na parte inferior do painel de navegação.
   
   ![](media/service-connect-to-salesforce/pbi_getdata.png) 
2. Na caixa **Serviços** , selecione **Obter**.
   
   ![](media/service-connect-to-salesforce/pbi_getservices.png) 
3. Selecione **Análise para Salesforce** e selecione **Obter**.  
   
   ![](media/service-connect-to-salesforce/salesforce.png)
4. Selecione **Entrar** para iniciar o fluxo de conexão.
   
    ![](media/service-connect-to-salesforce/dialog.png)
5. Quando solicitado, insira suas credenciais do Salesforce. Selecione **Permitir** e permita que o Power BI acesse suas informações e dados básicos do Salesforce.
   
   ![](media/service-connect-to-salesforce/sf_authorize.png)
6. Configure o que você desejaria importar para o Power BI usando a opção de lista suspensa:
   
   * **Dashboard**
     
     Selecione um painel predefinido com base em uma persona (como **Gerente de Vendas**). Esses dashboards recuperam um conjunto específico de dados padrão do Salesforce, que não incluem campos personalizados.
     
     ![](media/service-connect-to-salesforce/pbi_salesforcechooserole.png)
   * **Relatórios**
     
     Selecione um ou mais relatórios personalizados da conta do Salesforce. Esses relatórios correspondem às visualizações no Salesforce, podendo incluir dados de objetos ou campos personalizados.
     
     ![](media/service-connect-to-salesforce/pbi_salesforcereports.png)
     
     Se você não vir quaisquer relatórios, adicione ou crie-os em sua conta do Salesforce e tente conectar-se novamente.

7. Selecione **Conectar** para iniciar o processo de importação. Durante a importação, você verá uma notificação mostrando que a importação está em andamento. Quando a importação for concluída, você verá um dashboard, relatório e conjunto de dados para seus dados do Salesforce listados no painel de navegação.
   
   ![](media/service-connect-to-salesforce/pbi_getdatasalesforcedash.png)

Você pode alterar o dashboard para exibir os dados como você quiser. Você pode fazer perguntas com P e R ou [selecionar um bloco](../consumer/end-user-tiles.md) para abrir o relatório subjacente e [editar ou remover blocos de dashboard](../create-reports/service-dashboard-edit-tile.md).

**E agora?**

* Tente [fazer uma pergunta na caixa de P e R](../consumer/end-user-q-and-a.md) na parte superior do dashboard
* [Editar ou remover um bloco](../create-reports/service-dashboard-edit-tile.md) no dashboard
* [Selecionar um bloco](../create-reports/service-dashboard-tiles.md) para abrir o relatório subjacente
* Enquanto seu conjunto de dados está agendado para ser atualizado diariamente, você pode alterar o agendamento de atualização ou tentar atualizá-lo sob demanda usando **Atualizar Agora**

## <a name="system-requirements-and-considerations"></a>Considerações e requisitos do sistema

- Estar conectado a uma conta do Salesforce que tenha acesso habilitado à API

- Permissão concedida ao aplicativo do Power BI durante a conexão

- A conta ter chamadas à API suficientes disponíveis para efetuar pull dos dados e atualizá-los

- Um token de autenticação válido é necessário para a atualização. O SalesForce tem um limite de cinco tokens de autenticação por aplicativo, portanto, verifique se você tem cinco ou menos conjuntos de dados do Salesforce importados.

- A API dos Relatórios do Salesforce tem uma restrição que dá suporte a até 2.000 linhas de dados.


## <a name="troubleshooting"></a>Solução de problemas

Se você se deparar com erros, examine os requisitos acima. 

Atualmente não há suporte para conexão em um domínio personalizado ou de área restrita.

### <a name="unable-to-connect-to-the-remote-server-message"></a>Mensagem "Não é possível conectar ao servidor remoto"

Se você receber uma mensagem "Não é possível conectar ao servidor remoto" ao tentar se conectar à sua conta do Salesforce, confira esta solução no fórum: [Mensagem de erro na conexão do Salesforce Connector: Unable to connect to the remote server](https://www.outsystems.com/forums/Forum_TopicView.aspx?TopicId=17674&TopicName=log-in-error-message-unable-to-connect-to-the-remote-server&) (Mensagem de erro de entrada no conector do Salesforce: Não é possível se conectar ao servidor remoto)


## <a name="next-steps"></a>Próximas etapas
[O que é o Power BI?](../fundamentals/power-bi-overview.md)

[Fontes de dados para o serviço do Power BI](service-get-data.md)
