---
title: Conectar-se ao Xero com o Power BI
description: Xero para o Power BI
author: paulinbar
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 03/06/2020
ms.author: painbar
LocalizationGroup: Connect to services
ms.openlocfilehash: adb2f66b043b09ecb584870cf96f4c491960d59b
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83348426"
---
# <a name="connect-to-xero-with-power-bi"></a>Conectar-se ao Xero com o Power BI
O Xero é um software de contabilidade online fácil de usar, criado especificamente para pequenas empresas. Crie visualizações interessantes com base em seus dados financeiros do Xero com este aplicativo de modelo do Power BI. O dashboard padrão inclui várias métricas de pequenas empresas, como posição de caixa, receita versus despesas, tendência de perda de lucros, períodos médios de cobrança e retorno sobre o investimento.

Conecte-se ao [aplicativo de modelo do Xero](https://app.powerbi.com/getdata/services/xero) para o Power BI ou saiba mais sobre a integração do [Xero e o Power BI](https://help.xero.com/Power-BI).

## <a name="how-to-connect"></a>Como se conectar

[!INCLUDE [powerbi-service-apps-get-more-apps](../includes/powerbi-service-apps-get-more-apps.md)]

3. Selecione **Xero** \> **Obter agora**.
4. Em **Instalar este aplicativo do Power BI?** , selecione **Instalar**.

    ![Instalar o Xero](media/service-connect-to-xero/power-bi-install-xero.png)

4. No painel **Aplicativos**, selecione o bloco **Xero**.

   ![Selecionar o bloco Xero](media/service-connect-to-xero/power-bi-start-xero.png)

6. Em **Introdução a seu novo aplicativo**, selecione **Conectar**.

    ![Introdução ao novo aplicativo](media/service-connect-to-zendesk/power-bi-new-app-connect-get-started.png)

4. Insira um apelido para a organização associado à sua conta do Xero. Você poderá usar qualquer um. Ele servirá principalmente para ajudar os usuários com várias organizações do Xero a mantê-las organizadas. Confira detalhes sobre como [localizar parâmetros](#FindingParams) mais adiante neste artigo.

    ![Apelido da organização](media/service-connect-to-xero/params.png)

5. No **Método de Autenticação**, selecione **OAuth**. Quando solicitado, faça logon em sua conta do Xero e selecione a organização à qual você deseja se conectar. Após terminar o logon, selecione **Entrar** para iniciar o processo de carregamento.
   
    ![Método de autenticação](media/service-connect-to-xero/creds.png)
   
    ![Bem-vindo ao Xero](media/service-connect-to-xero/creds2.png)
6. Após a aprovação, o processo de importação será iniciado automaticamente. Quando concluído, um novo dashboard, relatório e modelo serão exibidos no painel de navegação. Selecione o painel para exibir os dados importados por você.
   
     ![Dashboard do Xero](media/service-connect-to-xero/power-bi-xero-dashboard.png)

**E agora?**

* Tente [fazer uma pergunta na caixa de P e R](../consumer/end-user-q-and-a.md) na parte superior do dashboard
* [Altere os blocos](../create-reports/service-dashboard-edit-tile.md) no dashboard.
* [Selecione um bloco](../consumer/end-user-tiles.md) para abrir o relatório subjacente.
* Enquanto seu conjunto de dados será agendado para ser atualizado diariamente, você pode alterar o agendamento de atualização ou tentar atualizá-lo sob demanda usando **Atualizar Agora**

## <a name="whats-included"></a>O que está incluído
O dashboard do aplicativo de modelo inclui blocos e métricas que abrangem uma variedade de áreas, com relatórios correspondentes para saber mais:  

| Área | Blocos do Dashboard | Relatório |
| --- | --- | --- |
| Caixa |Fluxo de caixa diário <br>Entrada de caixa <br>Saída de caixa <br>Saldo de fechamento por conta <br>Saldo de fechamento hoje |Contas Bancárias |
| Cliente |Vendas faturadas <br>Vendas faturadas por cliente <br>Tendência de crescimento das vendas faturadas <br>Faturas devidas <br>Contas a receber pendentes <br>Contas a receber vencidas |Cliente <br>Inventário |
| Fornecedor |Compras cobradas <br>Compras cobradas por fornecedor <br>Tendência de crescimento das compras cobradas <br> Cobranças devidas <br>Contas a pagar pendentes <br>Contas a pagar vencidas |Fornecedores <br>Inventário |
| Inventário |Quantidade de vendas mensais por produto |Inventário |
| Lucros e perdas |Lucros e perdas mensais <br>Lucro líquido neste ano fiscal <br>Lucro líquido neste mês <br>Principais contas de despesas |Lucros e perdas |
| Balanço |Total de ativos <br>Total de passivos <br>Capital próprio |Balanço |
| Saúde |Índice atual <br>Percentual de lucro bruto <br> Retorno sobre o total de ativos <br>Índice total de passivos/capital próprio |Saúde <br>Glossário e Observações técnicas |

O conjunto de dados também inclui as seguintes tabelas para personalizar seus relatórios e dashboards:  

* Endereços  
* Alertas  
* Saldo Diário do Extrato Bancário  
* Extratos Bancários  
* Contatos  
* Declarações de despesas  
* Itens de linha da fatura  
* Faturas  
* Itens  
* Final do Mês  
* Organização  
* Balancete  
* Contas do Xero

## <a name="system-requirements"></a>Requisitos do sistema
As funções a seguir são necessárias para acessar o aplicativo de modelo do Xero: "Padrão + Relatórios" ou "Supervisor".

<a name="FindingParams"></a>

## <a name="finding-parameters"></a>Localizando parâmetros
Forneça um nome à sua organização para acompanhá-la no Power BI. Um nome específico permite que você se conecte a várias organizações diferentes. Não é possível se conectar à mesma empresa várias vezes, pois isso afeta a atualização agendada.   

## <a name="troubleshooting"></a>Solução de problemas
* Os usuários do Xero precisam ter as seguintes funções a fim de acessar o aplicativo de modelo do Xero para o Power BI: "Padrão + Relatórios" ou "Supervisor". O aplicativo de modelo depende das permissões baseadas no usuário para acessar os dados de relatórios por meio do Power BI.
* Durante o carregamento, os blocos no dashboard estão em um estado de carregamento genérico. Eles permanecem dessa maneira até que a carga completa seja concluída. Se você receber uma notificação de que o carregamento foi concluído, mas os blocos ainda estão carregando, tente atualizar os blocos do dashboard usando ... na parte superior direita do dashboard.
* Caso seu aplicativo de modelo não seja atualizado, verifique se você se conectou à mesma organização mais de uma vez no Power BI. O Xero permite apenas uma única conexão ativa a uma organização, e você pode ver um erro indicando que suas credenciais serão inválidas se você se conectar à mesma organização mais de uma vez.  
* Em caso de problemas ao se conectar ao aplicativo de modelo do Xero para o Power BI, como mensagens de erro ou tempos de carregamento lentos, primeiro limpe o cache e os cookies e reinicie o navegador. Em seguida, reconecte-se ao Power BI.  

Caso tenha outras dúvidas, envie um tíquete em https://support.powerbi.com se o problema persistir.

## <a name="next-steps"></a>Próximas etapas
[Introdução ao Power BI](../fundamentals/service-get-started.md)

[Obter dados no Power BI](service-get-data.md)
