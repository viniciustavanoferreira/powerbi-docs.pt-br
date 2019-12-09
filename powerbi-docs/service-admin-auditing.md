---
title: Usar a auditoria na organização
description: Saiba como você pode usar a auditoria com o Power BI para monitorar e investigar as ações executadas. Você pode usar a Central de Segurança e Conformidade ou usar o PowerShell.
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 09/09/2019
ms.author: kfollis
ms.custom: seodec18
LocalizationGroup: Administration
ms.openlocfilehash: 868d3dc2463f5ed94b8d8ccd85e5edff33ca1c6e
ms.sourcegitcommit: f77b24a8a588605f005c9bb1fdad864955885718
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2019
ms.locfileid: "74698913"
---
# <a name="use-auditing-within-your-organization"></a>Usar a auditoria na organização

Saber quem está executando uma ação em determinado item, em seu locatário do Power BI pode ser essencial para ajudar a organização a atender a seus requisitos, como gerenciamento de registros e conformidade regulamentar. Use a auditoria do Power BI para auditar as ações executadas pelos usuários, como "Exibir Relatório" e "Exibir Painel". Não é possível usar a auditoria para auditar permissões.

Trabalhe com a auditoria no Centro de Conformidade e Segurança do Office 365 ou use o PowerShell. A auditoria conta com a funcionalidade no Exchange Online, que é provisionado automaticamente para dar suporte ao Power BI.

Você pode filtrar os dados de auditoria por intervalo de datas, usuário, painel, tipo de relatório, conjunto de dados e tipo de atividade. Você pode também baixar as atividades em um arquivo CSV (valores separados por vírgula) para analisá-las offline.

## <a name="requirements"></a>Requisitos

Você deve atender a esses requisitos para acessar logs de auditoria:

* Para acessar o log de auditoria, é necessário ser um administrador global ou ser atribuído à função de Logs de Auditoria ou Logs de Auditoria Somente Exibição no Exchange Online. Por padrão, essas funções são atribuídas a grupos de funções de Gerenciamento de Conformidade e Gerenciamento de Organização, na página **Permissões**, no centro de administração do Exchange.

    Para fornecer contas não administrativas com acesso ao log de auditoria, você deve adicionar o usuário como membro de um desses grupos de função. Como alternativa, crie um grupo de função personalizado no Centro de administração do Exchange, atribua a função de Logs de Auditoria ou Logs de Auditoria Somente Exibição a esse grupo e adicione a conta não administrativa ao novo grupo de função. Para obter mais informações, veja [Gerenciar grupos de função no Exchange Online](/Exchange/permissions-exo/role-groups).

    Se você não conseguir acessar o Centro de administração do Exchange no Centro de administração do Microsoft 365, vá para https://outlook.office365.com/ecp e entre usando suas credenciais.

* Caso tenha acesso ao log de auditoria, mas não seja um administrador global ou administrador de serviço do Power BI, você não terá acesso ao portal de administração do Power BI. Nesse caso, você deve usar um link direto para o [Centro de Conformidade e Segurança do Office 365](https://sip.protection.office.com/#/unifiedauditlog).

## <a name="access-your-audit-logs"></a>Acessar os logs de auditoria

Para acessar os logs, primeiro habilite o log no Power BI. Para saber mais, confira [Logs de auditoria](service-admin-portal.md#audit-logs) na documentação do portal do administrador. Pode haver um atraso de até 48 horas entre o tempo de habilitação da auditoria e a possibilidade de exibir dados de auditoria. Se os dados não forem exibidos imediatamente, verifique os logs de auditoria mais tarde. Pode haver um atraso semelhante entre a obtenção da permissão para exibir os logs de auditoria e a possibilidade de acessá-los.

Os logs de auditoria do Power BI estão disponíveis diretamente no [Centro de Conformidade e Segurança do Office 365](https://sip.protection.office.com/#/unifiedauditlog). Há também um link no portal de administração do Power BI:

1. No Power BI, selecione o **ícone de engrenagem**, no canto superior direito, e selecione **Portal de administração**.

   ![Captura de tela do menu suspenso de engrenagem com a opção do Portal de administração exibida.](media/service-admin-auditing/powerbi-admin.png)

1. Selecione **Logs de Auditoria**.

1. Selecione **Ir para o Centro de Administração do O365**.

   ![Captura de tela do portal de administração com as opções Logs de auditoria e Ir para o Centro de administração do Microsoft Office 365 exibidas.](media/service-admin-auditing/audit-log-o365-admin-center.png)

## <a name="search-only-power-bi-activities"></a>Pesquisar somente as atividades do Power BI

Restrinja os resultados apenas para as atividades do Power BI fazendo o seguinte. Confira uma lista de atividades em [lista de atividades auditadas pelo Power BI](#activities-audited-by-power-bi) mais adiante neste artigo.

1. Na página **Pesquisa de log de auditoria**, em **Pesquisar**, selecione o menu suspenso para **Atividades**.

2. Selecione **Atividades do Power BI**.

   ![Captura de tela do recurso Pesquisa de log de auditoria, com as atividades do Power BI exibidas.](media/service-admin-auditing/audit-log-search-filter-by-powerbi.png)

3. Selecione qualquer lugar fora da caixa de seleção para fechá-la.

As pesquisas retornarão apenas atividades do Power BI.

## <a name="search-the-audit-logs-by-date"></a>Pesquisar os logs de auditoria por data

Você pode pesquisar os logs por intervalo de datas usando os campos **Data de início** e **Data de término**. A seleção padrão nos últimos sete dias. A tela apresenta a data e a hora no formato UTC (Tempo Universal Coordenado). O intervalo de datas máximo que você pode especificar é 90 dias. 

Você receberá um erro, se o intervalo de datas selecionado for maior que 90 dias. Se você estiver usando o intervalo de datas máximo de 90 dias, selecione a hora atual para a **Data de início**. Caso contrário, você receberá uma mensagem de erro informando que a data de início é anterior à data de término. Se você ativou a auditoria nos últimos 90 dias, o intervalo de datas não poderá começar antes da data na qual a auditoria foi ativada.

![Captura de tela do recurso Pesquisa de log de auditoria, com as opções de Data de Início e Data de Término exibidas.](media/service-admin-auditing/search-audit-log-by-date.png)

## <a name="search-the-audit-logs-by-users"></a>Pesquisar os logs de auditoria por usuários

Você pode procurar por entradas de log de auditoria das atividades realizadas por usuários específicos. Para fazer isso, insira um ou mais nomes de usuário no campo **Usuários**. O nome de usuário tem a aparência de um endereço de email. Trata-se da conta que o usuário utiliza para entrar no Power BI. Deixe esta caixa em branco para retornar as entradas para todos os usuários (e contas de serviço) em sua organização.

![Pesquisar por usuários](media/service-admin-auditing/search-audit-log-by-user.png)

## <a name="view-search-results"></a>Exibir resultados da pesquisa

Após selecionar **Pesquisar**, o programa carregará os resultados da pesquisa. Depois de alguns instantes, eles serão exibidos em **Resultados**. Quando a pesquisa é concluída, a tela mostra o número de resultados encontrados. A **Pesquisa de log de auditoria** exibe no máximo mil eventos. Se os critérios da pesquisa gerarem mais de mil eventos, o aplicativo exibirá os mil eventos mais recentes.

### <a name="view-the-main-results"></a>Exibir os resultados principais

A área **Resultados** inclui as seguintes informações sobre cada evento retornado pela pesquisa. Selecione um cabeçalho de coluna em **Resultados** para classificar os resultados.

| **Coluna** | **Definição** |
| --- | --- |
| Date |A data e a hora (no formato UTC) quando o evento ocorreu. |
| Endereço IP |O endereço IP do dispositivo usado para a atividade registrada. O aplicativo exibe o endereço IP no formato de endereço IPv4 ou IPv6. |
| Usuário |O usuário (ou a conta de serviço) que executou a ação que acionou o evento. |
| Atividade |A atividade executada pelo usuário. Esse valor corresponde às atividades que você selecionou na lista suspensa **Atividades**. Para um evento do log de auditoria de administrador do Exchange, o valor desta coluna é um cmdlet do Exchange. |
| Item |O objeto criado ou modificado devido à atividade correspondente. Por exemplo, o arquivo exibido ou modificado, ou a conta de usuário atualizada. Nem todas as atividades têm um valor nesta coluna. |
| Detalhe |Detalhes adicionais sobre uma atividade. Novamente, nem todas as atividades têm um valor. |

### <a name="view-the-details-for-an-event"></a>Exibir os detalhes de um evento

Para exibir mais detalhes sobre um evento, selecione o registro do evento na lista de resultados da pesquisa. A página **Detalhes** é exibida contendo as propriedades detalhadas do registro do evento. As propriedades exibidas da página **Detalhes** dependem do serviço do Office 365 em que o evento ocorre.

Para exibir esses detalhes, selecione **Mais informações**. Todas as entradas do Power BI têm um valor de 20 para a propriedade RecordType. Para saber mais sobre outras propriedades, confira [Propriedades detalhadas no log de auditoria](/office365/securitycompliance/detailed-properties-in-the-office-365-audit-log/).

   ![Captura de tela da caixa de diálogo de detalhes da auditoria com a opção Mais informações exibida.](media/service-admin-auditing/audit-details.png)

## <a name="export-search-results"></a>Exportar resultados da pesquisa

Para exportar o log de auditoria do Power BI para um arquivo CSV, siga estas etapas.

1. Selecione **Exportar resultados**.

1. Selecione **Salvar resultados carregados** ou **Baixar todos os resultados**.

    ![Captura de tela da opção Exportar resultados.](media/service-admin-auditing/export-auditing-results.png)

## <a name="use-powershell-to-search-audit-logs"></a>Usar o PowerShell para pesquisar logs de auditoria

Você também pode usar o PowerShell para acessar os logs de auditoria com base em seu logon. O exemplo a seguir mostra como conectar-se ao Exchange Online PowerShell e então usar o comando [Search-UnifiedAuditLog](/powershell/module/exchange/policy-and-compliance-audit/search-unifiedauditlog?view=exchange-ps/) para efetuar o pull de entradas de log de auditoria do Power BI. Para executar o script, o administrador deve atribuir a você as permissões apropriadas, conforme descrito na seção [Requisitos](#requirements).

```powershell
Set-ExecutionPolicy RemoteSigned

$UserCredential = Get-Credential

$Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell-liveid/ -Credential $UserCredential -Authentication Basic -AllowRedirection

Import-PSSession $Session
Search-UnifiedAuditLog -StartDate 9/11/2018 -EndDate 9/15/2018 -RecordType PowerBI -ResultSize 1000 | Format-Table | More
```

## <a name="use-powershell-to-export-audit-logs"></a>Usar o PowerShell para exportar logs de auditoria

Você também pode usar o PowerShell para exportar os resultados da pesquisa de logs de auditoria. O exemplo a seguir mostra como enviar usando o comando [Search-UnifiedAuditLog](/powershell/module/exchange/policy-and-compliance-audit/search-unifiedauditlog?view=exchange-ps/) e exportar os resultados usando o cmdlet [Export-Csv](/powershell/module/microsoft.powershell.utility/export-csv). Para executar o script, o administrador deve atribuir a você as permissões apropriadas, conforme descrito na seção [Requisitos](#requirements).

```powershell
$UserCredential = Get-Credential

$Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell-liveid/ -Credential $UserCredential -Authentication Basic -AllowRedirection

Import-PSSession $Session
Search-UnifiedAuditLog -StartDate 9/11/2019 -EndDate 9/15/2019 -RecordType PowerBI -ResultSize 5000 |
Export-Csv -Path "c:\temp\PowerBIAuditLog.csv" -NoTypeInformation

Remove-PSSession $Session
```

Para obter mais informações sobre como se conectar ao Exchange Online, consulte [Conectar ao Exchange Online PowerShell](/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell/). Para ver outro exemplo de como usar o PowerShell com os logs de auditoria, confira [Usar o log de auditoria do Power BI e o PowerShell para atribuir licenças do Power BI Pro](https://powerbi.microsoft.com/blog/using-power-bi-audit-log-and-powershell-to-assign-power-bi-pro-licenses/).

## <a name="activities-audited-by-power-bi"></a>Atividades auditadas pelo Power BI

As atividades a seguir são auditadas pelo Power BI:

| Nome amigável                                     | Nome da operação                              | Observações                                  |
|---------------------------------------------------|---------------------------------------------|------------------------------------------|
| Fonte de dados adicionada ao gateway do Power BI             | AddDatasourceToGateway                      |                                          |
| Acesso à pasta do Power BI adicionado                      | AddFolderAccess                             | Atualmente não usado                       |
| Adicionados membros de grupo do Power BI                      | AddGroupMembers                             |                                          |
| Administrador anexou conta de armazenamento de fluxo de dados ao locatário | AdminAttachedDataflowStorageAccountToTenant | Atualmente não usado                       |
| Conjunto de dados do Power BI analisado                         | AnalyzedByExternalApplication               |                                          |
| Relatório do Power BI analisado                          | AnalyzeInExcel                              |                                          |
| Conta de armazenamento de fluxo de dados anexada                 | AttachedDataflowStorageAccount              |                                          |
| Conjunto de dados do Power BI associado ao gateway                | BindToGateway                               |                                          |
| Atualização de fluxo de dados cancelada                        | CancelDataflowRefresh                       |                                          |
| Estado da capacidade alterado                            | ChangeCapacityState                         |                                          |
| Atribuição de usuário da capacidade alterado                  | UpdateCapacityUsersAssignment               |                                          |
| Conexões de conjunto de dados do Power BI alteradas              | SetAllConnections                           |                                          |
| Administradores de gateway do Power BI alterados                   | ChangeGatewayAdministrators                 |                                          |
| Usuários da fonte de dados de gateway do Power BI alterados        | ChangeGatewayDatasourceUsers                |                                          |
| Pacote de conteúdo organizacional do Power BI criado      | CreateOrgApp                                |                                          |
| Aplicativo do Power BI criado                              | CreateApp                                   |                                          |
| Dashboard do Power BI criado                        | CreateDashboard                             |                                          |
| Fluxo de dados do Power BI criado                         | CreateDataflow                              |                                          |
| Conjunto de dados do Power BI criado                          | CreateDataset                               |                                          |
| Assinatura de email do Power BI criada               | CreateEmailSubscription                     |                                          |
| Pasta do Power BI criada                           | CreateFolder                                |                                          |
| Gateway do Power BI criado                          | CreateGateway                               |                                          |
| Grupo do Power BI criado                            | CreateGroup                                 |                                          |
| Relatório do Power BI criado                           | CreateReport                                |                                          |
| Fluxo de dados migrado para conta de armazenamento externa     | DataflowMigratedToExternalStorageAccount    | Atualmente não usado                       |
| Permissões de fluxo de dados adicionadas                        | DataflowPermissionsAdded                    | Atualmente não usado                       |
| Permissões de fluxo de dados removidas                      | DataflowPermissionsRemoved                  | Atualmente não usado                       |
| Pacote de conteúdo organizacional do Power BI excluído      | DeleteOrgApp                                |                                          |
| Comentário do Power BI excluído                          | DeleteComment                               |                                          |
| Dashboard do Power BI excluído                        | DeleteDashboard                             | Atualmente não usado                       |
| Fluxo de dados do Power BI excluído                         | DeleteDataflow                              | Atualmente não usado                       |
| Conjunto de dados do Power BI excluído                          | DeleteDataset                               |                                          |
| Assinatura de email do Power BI excluída               | DeleteEmailSubscription                     |                                          |
| Pasta do Power BI excluída                           | DeleteFolder                                |                                          |
| Acesso à pasta do Power BI excluído                    | DeleteFolderAccess                          | Atualmente não usado                       |
| Gateway do Power BI excluído                          | DeleteGateway                               |                                          |
| Grupo do Power BI excluído                            | DeleteGroup                                 |                                          |
| Relatório do Power BI excluído                           | DeleteReport                                |                                          |
| Fontes de dados de conjunto de dados do Power BI descobertas          | GetDatasources                              |                                          |
| Relatório do Power BI baixado                        | DownloadReport                              |                                          |
| Propriedades de fluxo de dados editadas                        | EditDataflowProperties                      |                                          |
| Permissão de certificação do Power BI editada          | EditCertificationPermission                 | Atualmente não usado                       |
| Dashboard do Power BI editado                         | EditDashboard                               | Atualmente não usado                       |
| Conjunto de dados do Power BI editado                           | EditDataset                                 |                                          |
| Propriedades do conjunto de dados do Power BI editadas                | EditDatasetProperties                       | Atualmente não usado                       |
| Relatório do Power BI editado                            | EditReport                                  |                                          |
| Fluxo de dados do Power BI exportado                        | ExportDataflow                              |                                          |
| Dados visuais de relatório do Power BI exportados              | ExportReport                                |                                          |
| Dados de bloco do Power BI exportados                       | ExportTile                                  |                                          |
| Falha ao adicionar permissões de fluxo de dados                | FailedToAddDataflowPermissions              | Atualmente não usado                       |
| Falha ao remover permissões de fluxo de dados             | FailedToRemoveDataflowPermissions           | Atualmente não usado                       |
| Token SAS de fluxo de dados do Power BI gerado             | GenerateDataflowSasToken                    |                                          |
| Token de inserção do Power BI gerado                    | GenerateEmbedToken                          |                                          |
| Arquivo importado para o Power BI                         | Importar                                      |                                          |
| Aplicativo do Power BI instalado                            | InstallApp                                  |                                          |
| Workspace migrado para uma capacidade                  | MigrateWorkspaceIntoCapacity                |                                          |
| Comentário do Power BI postado                           | PostComment                                 |                                          |
| Dashboard do Power BI impresso                        | PrintDashboard                              |                                          |
| Página de relatório do Power BI impressa                      | PrintReport                                 |                                          |
| Relatório do Power BI publicado na Web                  | PublishToWebReport                          |                                          |
| Segredo de fluxo de dados do Power BI recebido do Key Vault  | ReceiveDataflowSecretFromKeyVault           |                                          |
| Fonte de dados removida do gateway do Power BI         | RemoveDatasourceFromGateway                 |                                          |
| Membros de grupo do Power BI removidos                    | DeleteGroupMembers                          |                                          |
| Workspace removido de uma capacidade                 | RemoveWorkspacesFromCapacity                |                                          |
| Dashboard do Power BI renomeado                        | RenameDashboard                             |                                          |
| Atualização de fluxo de dados do Power BI solicitada               | RequestDataflowRefresh                      | Atualmente não usado                       |
| Atualização de conjunto de dados do Power BI solicitada                | RefreshDataset                              |                                          |
| Workspaces do Power BI recuperados                     | GetWorkspaces                               |                                          |
| Definir o local de armazenamento do fluxo de dados como um workspace     | SetDataflowStorageLocationForWorkspace      |                                          |
| Definir atualização agendada no fluxo de dados do Power BI        | SetScheduledRefreshOnDataflow               |                                          |
| Definir atualização agendada no conjunto de dados do Power BI         | SetScheduledRefresh                         |                                          |
| Dashboard do Power BI compartilhado                         | ShareDashboard                              |                                          |
| Relatório do Power BI compartilhado                            | ShareReport                                 |                                          |
| Avaliação estendida do Power BI iniciada                   | OptInForExtendedProTrial                    | Atualmente não usado                       |
| Avaliação do Power BI iniciada                            | OptInForProTrial                            |                                          |
| Assumiu uma fonte de dados do Power BI                   | TakeOverDatasource                          |                                          |
| Assumiu um conjunto de dados do Power BI                        | TakeOverDataset                             |                                          |
| Assumiu um fluxo de dados do Power BI                     | TookOverDataflow                             |                                          |
| Aplicativo do Power BI não publicado                          | UnpublishApp                                |                                          |
| Atualizar configurações de governança de recursos de capacidade      | UpdateCapacityResourceGovernanceSettings    | Atualmente não está no Centro de administração do Microsoft 365 |
| Administrador de capacidade atualizado                            | UpdateCapacityAdmins                        |                                          |
| Nome de exibição de capacidade atualizado                     | UpdateCapacityDisplayName                   |                                          |
| Permissões de atribuição de armazenamento de fluxo de dados atualizadas   | UpdatedDataflowStorageAssignmentPermissions |                                          |
| Configurações do Power BI da organização atualizadas          | UpdatedAdminFeatureSwitch                   |                                          |
| Aplicativo do Power BI atualizado                              | UpdateApp                                   |                                          |
| Fluxo de dados do Power BI atualizado                         | UpdateDataflow                              |                                          |
| Fontes de dados de conjunto de dados do Power BI atualizadas             | UpdateDatasources                           |                                          |
| Parâmetros de conjunto de dados do Power BI atualizados               | UpdateDatasetParameters                     |                                          |
| Assinatura de email do Power BI atualizada               | UpdateEmailSubscription                     |                                          |
| Pasta do Power BI atualizada                           | UpdateFolder                                |                                          |
| Acesso à pasta do Power BI atualizado                    | UpdateFolderAccess                          |                                          |
| Credenciais da fonte de dados de gateway do Power BI atualizadas  | UpdateDatasourceCredentials                 |                                          |
| Dashboard do Power BI exibido                         | ViewDashboard                               |                                          |
| Fluxo de dados do Power BI exibido                          | ViewDataflow                                |                                          |
| Relatório do Power BI exibido                            | ViewReport                                  |                                          |
| Bloco do Power BI exibido                              | ViewTile                                    |                                          |
| Métricas de uso do Power BI exibidas                     | ViewUsageMetrics                            |                                          |
|                                                   |                                             |                                          |

## <a name="next-steps"></a>Próximas etapas

[O que é administração do Power BI?](service-admin-administering-power-bi-in-your-organization.md)  

[Portal de administração do Power BI](service-admin-portal.md)  

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
