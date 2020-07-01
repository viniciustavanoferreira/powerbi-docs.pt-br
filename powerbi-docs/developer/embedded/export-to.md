---
title: API Exportar relatórios do Power BI
description: Saiba como exportar um relatório incorporado do Power BI
author: KesemSharabi
ms.author: kesharab
ms.topic: how-to
ms.service: powerbi
ms.subservice: powerbi-developer
ms.date: 03/24/2020
ms.openlocfilehash: 546f712c87e67240fd15ee2563252d8f322212c7
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85220990"
---
# <a name="export-power-bi-report-to-file-preview"></a>Exportar relatório do Power BI para um arquivo (versão prévia)

A API `exportToFile` permite exportar um relatório do Power BI usando uma chamada REST. Os seguintes formatos de arquivo têm suporte:
* **.pptx** (PowerPoint)
* **.pdf**
* **.png**
    * Ao exportar para um .png, um relatório com várias páginas é compactado em um arquivo .zip
    * Cada arquivo no .zip representa uma página do relatório
    * Os nomes das páginas são os mesmos que os valores de retorno das APIs [Obter Páginas](https://docs.microsoft.com/rest/api/power-bi/reports/getpages) ou [Obter Páginas em Grupo](https://docs.microsoft.com/rest/api/power-bi/reports/getpagesingroup)

## <a name="usage-examples"></a>Exemplos de uso

Você pode usar o recurso de exportação de diversas maneiras. Aqui estão alguns exemplos:

* **Botão Enviar para impressão** – No seu aplicativo, crie um botão que, quando clicado, dispara um trabalho de exportação. O trabalho pode exportar o relatório exibido como um .pdf ou um .pptx e, quando ele for concluído, o usuário poderá receber o arquivo como um download. Usando indicadores, é possível exportar o relatório em um estado específico, incluindo filtros configurados, segmentações e configurações adicionais. Como a API é assíncrona, pode levar algum tempo até que o arquivo esteja disponível.

* **Anexo de email**: envie um email automatizado em intervalos definidos, com um relatório anexado em .pdf. Esse cenário poderá ser útil se você quiser automatizar o envio de relatórios semanais para executivos.

## <a name="using-the-api"></a>Usando a API

Antes de usar a API, verifique se as seguintes [configurações de locatário administrador](../../admin/service-admin-portal.md#tenant-settings) estão definidas:
* **Exportar relatórios como apresentações do PowerPoint ou documentos PDF** – Habilitado por padrão.
* **Exportar relatórios como arquivos de imagem**: necessário somente para *.png* e desabilitado por padrão.

A API é assíncrona. Quando a API [exportToFile](https://docs.microsoft.com/rest/api/power-bi/reports/exporttofile) é chamada, dispara um trabalho de exportação. Depois de disparar o trabalho de exportação, use a [sondagem](https://docs.microsoft.com/rest/api/power-bi/reports/getexporttofilestatus) para rastrear o trabalho até a conclusão.

Durante a sondagem, a API retorna um número que representa a quantidade de trabalho concluída. Cada trabalho de exportação é calculado com base no número de páginas que o relatório possui. Todas as páginas têm o mesmo tamanho. Por exemplo, caso você esteja exportando um relatório com 10 páginas e a sondagem retornar 70, isso significa que a API processou sete de 10 páginas no trabalho de exportação.

Quando a exportação for concluída, a chamada à API de sondagem retornará uma [URL do Power BI](https://docs.microsoft.com/rest/api/power-bi/reports/getfileofexporttofile) para a obtenção do arquivo. A URL ficará disponível por 24 horas.

## <a name="supported-features"></a>Recursos compatíveis

### <a name="selecting-which-pages-to-print"></a>Selecionar as páginas para impressão

Especifique as páginas para impressão de acordo com o valor de retorno de [Obter Páginas](https://docs.microsoft.com/rest/api/power-bi/reports/getpages) ou [Obter Páginas em Grupo](https://docs.microsoft.com/rest/api/power-bi/reports/getpagesingroup). Também é possível especificar a ordem das páginas que você está exportando.

### <a name="bookmarks"></a>Indicadores

 Você pode usar a API `exportToFile` para exportar por programação um relatório em um estado específico depois de aplicar filtros a ele. Faça isso usando os recursos de [Indicadores](../../consumer/end-user-bookmarks.md). Para exportar um relatório por meio de indicadores use a [API JavaScript de indicadores](https://github.com/Microsoft/PowerBI-JavaScript/wiki/Bookmarks).

 Por exemplo, você pode usar o método `capturedBookmark.state` do indicador para capturar as alterações que um usuário específico executou no relatório, depois pode exportá-lo no seu estado atual.

Não há suporte para [indicadores pessoais](../../consumer/end-user-bookmarks.md#personal-bookmarks) e [filtros persistentes](https://powerbi.microsoft.com/blog/announcing-persistent-filters-in-the-service/).

### <a name="authentication"></a>Autenticação

É possível autenticar usando um usuário (ou usuário mestre) ou uma [entidade de serviço](embed-service-principal.md).

### <a name="row-level-security-rls"></a>RLS (Segurança em Nível de Linha)

Com a [RLS (Segurança em Nível de Linha)](embedded-row-level-security.md), é possível exportar um relatório mostrando dados que só ficam visíveis para determinados usuários. Por exemplo, se você estiver exportando um relatório de vendas definido com funções regionais, poderá filtrar o relatório programaticamente para exibir apenas determinada região.

Para exportar usando RLS, você deve ter as seguintes permissões:
* Permissões de gravação e recompartilhamento do conjunto de dados ao qual o relatório está conectado
* Se o relatório residir em um workspace v1, você precisará ser o administrador do workspace
* Caso o relatório resida em um workspace v2, você precisará ser membro ou administrador do workspace

### <a name="data-protection"></a>Proteção de dados

Os formatos .pdf e .pptx dão suporte a [rótulos de confidencialidade](../../admin/service-security-data-protection-overview.md#sensitivity-labels-in-power-bi). Se você exportar um relatório com um rótulo de confidencialidade para um .pdf ou um .pptx, o arquivo exportado exibirá o relatório com o respectivo rótulo de confidencialidade.

Um relatório com um rótulo de confidencialidade não pode ser exportado para um .pdf ou um .pptx com uma [entidade de serviço](embed-service-principal.md).

### <a name="localization"></a>Localização

Ao usar a API `exportToFile`, você pode passar o local desejado. As configurações de localização afetam a maneira como o relatório é exibido, por exemplo, ao alterar a formatação de acordo com o local selecionado.

## <a name="concurrent-requests"></a>Solicitações simultâneas

`exportToFile` dá suporte a solicitações de trabalho de exportação simultâneas. A tabela abaixo mostra o número de trabalhos que você pode executar simultaneamente, dependendo do SKU em que seu relatório reside. Solicitações simultâneas se referem a páginas de relatórios. Por exemplo, 20 páginas em uma solicitação de exportação em um SKU A6 serão processadas de forma simultânea. Isso leva aproximadamente o mesmo tempo que enviar 20 solicitações de exportação com uma página cada.

Um trabalho que excede o número de solicitações simultâneas não será concluído. Por exemplo, se você exportar três páginas em um SKU A1, o primeiro trabalho será executado, e os dois posteriores aguardarão até os próximos dois ciclos de execução.

|SKU do Azure  |SKU do Office  |Máximo de páginas de relatório simultâneas  |
|-----------|------------|-----------|
|A1         |EM1         |1          |
|A2         |EM2         |2          |
|A3         |EM3         |3          |
|A4         |P1          |6          |
|A5         |P2          |12         |
|A6         |P3          |24         |

## <a name="limitations"></a>Limitações

* O relatório que você está exportando deve residir em uma capacidade Premium ou Embedded.
* O conjunto de dados que você está exportando deve residir em uma capacidade Premium ou Embedded.
* Para versão prévia pública, o número de páginas de relatório do Power BI exportadas por hora é limitado a 50 por capacidade.
* Os relatórios exportados não podem exceder um tamanho de arquivo de 250 MB.
* Ao exportar para um .png, não há suporte aos rótulos de confidencialidade.
* Um relatório com um rótulo de confidencialidade não pode ser exportado para um .pdf ou um .pptx com uma [entidade de serviço](embed-service-principal.md).
* O número de páginas que podem ser incluídas em um relatório exportado é 30. Se o relatório incluir mais páginas, a API retornará um erro, e o trabalho de exportação será cancelado.
* Não há suporte para [indicadores pessoais](../../consumer/end-user-bookmarks.md#personal-bookmarks) e [filtros persistentes](https://powerbi.microsoft.com/blog/announcing-persistent-filters-in-the-service/).
* Não há suporte para os visuais do Power BI listados abaixo. Quando um relatório que contém estes visuais é exportado, as partes do relatório que os contêm não são renderizadas, e é exibido um símbolo de erro.
    * Visuais do Power BI não certificados
    * Visuais do R
    * PowerApps
    * Visuais de Python
    * Visio

## <a name="code-examples"></a>Exemplos de código

Ao criar um trabalho de exportação, é necessário seguir três etapas:

1. Enviar uma solicitação de exportação.
2. Executar a sondagem.
3. Obter o arquivo.

Esta seção fornece exemplos para cada etapa.

### <a name="step-1---sending-an-export-request"></a>Etapa 1 – enviar uma solicitação de exportação

A primeira etapa envolve enviar uma solicitação de exportação. Neste exemplo, solicitação de exportação é enviada para uma página específica.

```csharp
/////// Export sample ///////
private async Task<string> PostExportRequest(
    Guid reportId,
    Guid groupId,
    FileFormat format,
    IList<string> pageNames = null /* Get the page names from the GetPages API */)
{
    var powerBIReportExportConfiguration = new PowerBIReportExportConfiguration
    {
        Settings = new ExportReportSettings
        {
            Locale = "en-us",
        },
        // Note that page names differ from the page display names.
        // To get the page names use the GetPages API.
        Pages = pageNames?.Select(pn => new ExportReportPage(pageName = pn)).ToList(),
    };
    var exportRequest = new ExportReportRequest
    {
        Format = format,
        PowerBIReportConfiguration = powerBIReportExportConfiguration,
    };

    // The 'Client' object is an instance of the Power BI .NET SDK
    var export = await Client.Reports.ExportToFileInGroupAsync(groupId, reportId, exportRequest);

    // Save the export ID, you'll need it for polling and getting the exported file
    return export.Id;
}
```

### <a name="step-2---polling"></a>Etapa 2 – executar a sondagem

Depois de enviar a solicitação de exportação, use a sondagem para identificar quando o arquivo de exportação que você está esperando ficou pronto.

```csharp
private async Task<Export> PollExportRequest(
    Guid reportId,
    Guid groupId,
    string exportId /* Get from the ExportToAsync response */,
    int timeOutInMinutes,
    CancellationToken token)
{
    Export exportStatus = null;
    DateTime startTime = DateTime.UtcNow;
    const int c_secToMillisec = 1000;
    do
    {
        if (DateTime.UtcNow.Subtract(startTime).TotalMinutes > timeOutInMinutes || token.IsCancellationRequested)
        {
            // Error handling for timeout and cancellations 
            return null;
        }

        // The 'Client' object is an instance of the Power BI .NET SDK
        var httpMessage = await Client.Reports.GetExportToFileStatusInGroupWithHttpMessagesAsync(groupId, reportId, exportId);
        exportStatus = httpMessage.Body;

        // You can track the export progress using the PercentComplete that's part of the response
        SomeTextBox.Text = string.Format("{0} (Percent Complete : {1}%)", exportStatus.Status.ToString(), exportStatus.PercentComplete);
        if (exportStatus.Status == ExportState.Running || exportStatus.Status == ExportState.NotStarted)
        {
            // The recommended waiting time between polling requests can be found in the RetryAfter header
            // Note that this header is only populated when the status is either Running or NotStarted
            var retryAfter = httpMessage.Response.Headers.RetryAfter;
            var retryAfterInSec = retryAfter.Delta.Value.Seconds;
            await Task.Delay(retryAfterInSec * c_secToMillisec);
        }
    }
    // While not in a terminal state, keep polling
    while (exportStatus.Status != ExportState.Succeeded && exportStatus.Status != ExportState.Failed);
    return exportStatus;
}
```

### <a name="step-3---getting-the-file"></a>Etapa 3 – obter o arquivo

Quando a sondagem retornar uma URL, use este exemplo para receber o arquivo.

```csharp
private async Task<ExportedFile> GetExportedFile(
    Guid reportId,
    Guid groupId,
    Export export /* Get from the GetExportStatusAsync response */)
{
    if (export.Status == ExportState.Succeeded)
    {
        // The 'Client' object is an instance of the Power BI .NET SDK
        var fileStream = await Client.Reports.GetFileOfExportToFileAsync(groupId, reportId, export.Id);
        return new ExportedFile
        {
            FileStream = fileStream,
            FileSuffix = export.ResourceFileExtension,
        };
    }
    return null;
}
public class ExportedFile
{
    public Stream FileStream;
    public string FileSuffix;
}
```

### <a name="end-to-end-example"></a>Exemplo de ponta a ponta

Este é um exemplo de ponta a ponta da exportação de um relatório. O exemplo inclui os seguintes estágios:
1. [Enviar a solicitação de exportação](#step-1---sending-an-export-request).
2. [Executar a sondagem](#step-2---polling).
3. [Obter o arquivo](#step-3---getting-the-file).

```csharp
private async Task<ExportedFile> ExportPowerBIReport(
    Guid reportId,
    Guid groupId,
    FileFormat format,
    int pollingtimeOutInMinutes,
    CancellationToken token,
    IList<string> pageNames = null /* Get the page names from the GetPages API */)
{
    try
    {
        var exportId = await PostExportRequest(reportId, groupId, format, pageNames);
        var export = await PollExportRequest(reportId, groupId, exportId, pollingtimeOutInMinutes, token);
        if (export == null || export.Status != ExportState.Succeeded)
        {
            // Error, failure in exporting the report
            return null;
        }
        return await GetExportedFile(reportId, groupId, export);
    }
    catch
    {
        // Error handling
        throw;
    }
}
```

## <a name="next-steps"></a>Próximas etapas

Confira novamente como incorporar conteúdo para seus clientes e para sua empresa:

> [!div class="nextstepaction"]
>[Exportar o relatório paginado para um arquivo](export-paginated-report.md)

> [!div class="nextstepaction"]
>[Inserir para seus clientes](embed-sample-for-customers.md)

> [!div class="nextstepaction"]
>[Inserir para a organização](embed-sample-for-your-organization.md)
