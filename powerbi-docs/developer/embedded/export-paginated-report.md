---
title: API Exportar relatórios do Power BI
description: Saiba como exportar um relatório paginado incorporado do Power BI
author: KesemSharabi
ms.author: kesharab
ms.topic: conceptual
ms.service: powerbi
ms.subservice: powerbi-developer
ms.date: 04/05/2020
ms.openlocfilehash: acb13a70ea4693f447b70aa59da07cd91639de25
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/05/2020
ms.locfileid: "81268755"
---
# <a name="export-paginated-report-to-file-preview"></a>Exportar o relatório paginado para um arquivo (versão prévia)

A API `exportToFile` permite exportar um relatório paginado do Power BI usando uma chamada REST. Os seguintes formatos de arquivo têm suporte:
* **.pptx** (PowerPoint)
* **.pdf**
* **.xlsx** (Excel)
* **.dox** (Word)
* **.csv**
* **.xml**
* **.mhtml**
* **Imagem**
    * Ao exportar para uma imagem, defina o formato da imagem por meio da configuração de formato de `OutputFormat`
    * Os valores de OutputFormat compatíveis são: .bmp, .emf, .gif, .jpeg, .png ou .tiff (padrão)

## <a name="usage-examples"></a>Exemplos de uso

Você pode usar o recurso de exportação de diversas maneiras. Aqui estão alguns exemplos:

* **Botão Enviar para impressão** – No seu aplicativo, crie um botão que, quando clicado, dispara um trabalho de exportação. O trabalho pode exportar o relatório exibido como um .pdf ou um .pptx e, quando ele for concluído, o usuário poderá receber o arquivo como um download. Usando parâmetros de relatório e configurações de formato, você pode exportar o relatório em um estado específico, incluindo dados filtrados, tamanhos de página personalizados e outras configurações de formato específico. Como a API é assíncrona, pode levar algum tempo até que o arquivo esteja disponível.

* **Anexo de email**: envie um email automatizado em intervalos definidos, com um relatório anexado em .pdf. Esse cenário poderá ser útil se você quiser automatizar o envio de relatórios semanais para executivos.

## <a name="using-the-api"></a>Usando a API

A API é assíncrona. Quando a API [exportToFile](https://docs.microsoft.com/rest/api/power-bi/reports/exporttofile) é chamada, dispara um trabalho de exportação. Depois de disparar o trabalho de exportação, use a [sondagem](https://docs.microsoft.com/rest/api/power-bi/reports/getexporttofilestatus) para rastrear o trabalho até a conclusão.

Quando a exportação for concluída, a chamada à API de sondagem retornará uma [URL do Power BI](https://docs.microsoft.com/rest/api/power-bi/reports/getfileofexporttofile) para a obtenção do arquivo. A URL ficará disponível por 24 horas.

## <a name="supported-features"></a>Recursos compatíveis

### <a name="format-settings"></a>Configurações de formato

Especifique uma variedade de configurações de formato para cada formato de arquivo. Os valores e as propriedades com suporte são equivalentes a [Parâmetros de informações de dispositivo](../../paginated-reports/report-builder-url-parameters.md#report-commands-rdl) para parâmetros de URL de relatórios paginados.

Aqui estão dois exemplos, um para exportar as quatro primeiras páginas de um relatório usando o tamanho da página de relatório para um arquivo .pptx e outro para exportar a terceira página de um relatório para um arquivo .jpeg.

**Como exportar as primeiras quatro páginas para um .pptx**

```json
{
      "format": "PPTX",
      "paginatedReportConfiguration":{
            "formatSettings":{
                  "UseReportPageSize": "true",
                  "StartPage": "1",
                  "EndPage": "4"
            }
      }
}
```

**Como exportar a terceira página para um .jpeg**

```json
{
      "format": "IMAGE",
      "paginatedReportConfiguration":{
            "formatSettings":{
                  "OutputFormat": "JPEG",
                  "StartPage": "3",
                  "EndPage": "3"
            }
      }
}
```

### <a name="report-parameters"></a>Parâmetros de relatório

Você pode usar a API `exportToFile` para exportar programaticamente um relatório com um conjunto de parâmetros de relatório. Isso é feito usando funcionalidades de [parâmetro de relatório](../../paginated-reports/paginated-reports-parameters.md).

Aqui está um exemplo para definir valores de parâmetro de relatório.

```json
{
      "format": "PDF",
      "paginatedReportConfiguration":{
            "parameterValues":[
                  {"name": "State", "value": "WA"},
                  {"name": "City", "value": "Seattle"},
                  {"name": "City", "value": "Bellevue"},
                  {"name": "City", "value": "Redmond"}
            ]
      }
}
```

### <a name="authentication"></a>Autenticação

É possível autenticar usando um usuário (ou usuário mestre) ou uma [entidade de serviço](embed-service-principal.md).

### <a name="row-level-security-rls"></a>RLS (Segurança em Nível de Linha)

Ao usar um conjunto de dados do Power BI que tem RLS (Segurança em Nível de Linha) definida como uma fonte de dados, você pode exportar um relatório mostrando os dados que são visíveis apenas para determinados usuários. Por exemplo, se você estiver exportando um relatório de vendas definido com funções regionais, poderá filtrar o relatório programaticamente para exibir apenas determinada região.

Para exportar usando RLS, você deve ter permissão de leitura para o conjunto de dados do Power BI que o relatório está usando como uma fonte de dados.

Aqui está um exemplo para fornecer um nome de usuário efetivo para RLS.

```json
{
      "format": "PDF",
      "paginatedReportConfiguration":{
            "identities": [
                  {"username": "john@contoso.com"}            
            ]
      }
}
```

## <a name="code-examples"></a>Exemplos de código

O SDK da API do Power BI usado nos exemplos de código pode ser baixado [aqui](https://www.nuget.org/packages/Microsoft.PowerBI.Api).

Ao criar um trabalho de exportação, é necessário seguir três etapas:

1. Enviar uma solicitação de exportação.
2. Executar a sondagem.
3. Obter o arquivo.

Esta seção fornece exemplos para cada etapa.

### <a name="step-1---sending-an-export-request"></a>Etapa 1 – enviar uma solicitação de exportação

A primeira etapa envolve enviar uma solicitação de exportação. Neste exemplo, uma solicitação de exportação é enviada para um intervalo de página, tamanho e valores de parâmetro de relatório específicos.

```csharp
private async Task<string> PostExportRequest(
    Guid reportId,
    Guid groupId)
{
    // For documentation purposes the export configuration is created in this method
    // Ordinarily, it would be created outside and passed in
    var paginatedReportExportConfiguration = new PaginatedReportExportConfiguration()
    {
        FormatSettings = new Dictionary<string, string>()
        {
            {"PageHeight", "14in"},
            {"PageWidth", "8.5in" },
            {"StartPage", "1"},
            {"EndPage", "4"}
        },
        ParameterValues = new List<ParameterValue>()
        {
            { new ParameterValue() {Name = "State", Value = "WA"} },
            { new ParameterValue() {Name = "City", Value = "Redmond"} }
        }
    };

    var exportRequest = new ExportReportRequest
    {
        Format = FileFormat.PDF,
        PaginatedReportExportConfiguration = paginatedReportExportConfiguration,
    };

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
    const int secToMillisec = 1000;
    do
    {
        if (DateTime.UtcNow.Subtract(startTime).TotalMinutes > timeOutInMinutes || token.IsCancellationRequested)
        {
            // Error handling for timeout and cancellations
            return null;
        }

        var httpMessage = 
            await Client.Reports.GetExportToFileStatusInGroupWithHttpMessagesAsync(groupId, reportId, exportId);
            
        exportStatus = httpMessage.Body;
        if (exportStatus.Status == ExportState.Running || exportStatus.Status == ExportState.NotStarted)
        {
            // The recommended waiting time between polling requests can be found in the RetryAfter header
            // Note that this header is only populated when the status is either Running or NotStarted
            var retryAfter = httpMessage.Response.Headers.RetryAfter;
            var retryAfterInSec = retryAfter.Delta.Value.Seconds;

            await Task.Delay(retryAfterInSec * secToMillisec);
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
        var httpMessage = 
            await Client.Reports.GetFileOfExportToFileInGroupWithHttpMessagesAsync(groupId, reportId, export.Id);

        return new ExportedFile
        {
            FileStream = httpMessage.Body,
            ReportName = export.ReportName,
            FileExtension = export.ResourceFileExtension,
        };
    }

    return null;
}

public class ExportedFile
{
    public Stream FileStream;
    public string ReportName;
    public string FileExtension;
}
```

### <a name="end-to-end-example"></a>Exemplo de ponta a ponta

Este é um exemplo de ponta a ponta da exportação de um relatório. O exemplo inclui os seguintes estágios:
1. [Enviar a solicitação de exportação](#step-1---sending-an-export-request).
2. [Executar a sondagem](#step-2---polling).
3. [Obter o arquivo](#step-3---getting-the-file).

```csharp
private async Task<ExportedFile> ExportPaginatedReport(
    Guid reportId,
    Guid groupId,
    int pollingtimeOutInMinutes,
    CancellationToken token)
{
    try
    {
        var exportId = await PostExportRequest(reportId, groupId);

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
>[Exportar relatório para arquivo](export-to.md)

> [!div class="nextstepaction"]
>[Inserir para seus clientes](embed-sample-for-customers.md)

> [!div class="nextstepaction"]
>[Inserir para a organização](embed-sample-for-your-organization.md)