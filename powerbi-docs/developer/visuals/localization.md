---
title: Entender o mapeamento de exibição de dados em visuais do Power BI
description: Este artigo descreve como o Power BI transforma os dados antes de passá-los para elementos visuais.
author: KesemSharabi
ms.author: kesharab
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: ad63a1b97c744e8614e584874c4d896a85598e48
ms.sourcegitcommit: 0cc594ebb78a6d0e88784673ed09f8aefd10c7a7
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76819113"
---
# <a name="add-the-locale-in-power-bi-for-custom-visuals"></a>Adicionar a localidade no Power BI para visuais personalizados

Os visuais podem recuperar a localidade do Power BI para localizar o conteúdo para o idioma relevante.

Leia mais sobre os [Idiomas e países/regiões com suporte do Power BI](./../../supported-languages-countries-regions.md)

Por exemplo, obter a localidade no visual de Gráfico de Barras de Exemplo.

![Localização no visual de Gráfico de Barras de Exemplo](media/locale-in-samplebarchart.png)

Cada um desses gráficos de barras foi criado com uma localidade diferente (inglês, basco e híndi) e isso é exibido na dica de ferramenta.

> [!NOTE]
> O gerenciador de localização no código do visual tem suporte da API 1.10.0 e superior.

## <a name="get-the-locale"></a>Obter a localidade

O `locale` é passado como uma cadeia de caracteres durante a inicialização do visual. Se uma localidade for alterada no Power BI, o visual será gerado novamente com a nova localidade. Você pode encontrar o código completo do exemplo em SampleBarChart with Locale

Agora, o construtor BarChart tem um membro de localidade, que é instanciado no construtor com a instância de localidade do host.

```typescript
private locale: string;
...
this.locale = options.host.locale;
```

Localidades com suporte:

Cadeia de caracteres de localidade | Idioma
--------------|----------------------
ar-SA | العربية (árabe)
bg-BG | български (búlgaro)
ca-ES | català (catalão)
cs-CZ | čeština (tcheco)
da-DK | dansk (dinamarquês)
de-DE | Deutsche (alemão)
el-GR | ελληνικά (grego)
en-US | English (inglês)
es-ES | español service (espanhol)
et-EE | eesti (estoniano)
eU-ES | Euskal (basco)
fi-FI | suomi (finlandês)
fr-FR | français (francês)
gl-ES | galego
he-IL | עברית (hebraico)
hi-IN | हिन्दी (híndi)
hr-HR | hrvatski (croata)
hu-HU | magyar (húngaro)
id-ID | Bahasa Indonesia (indonésio)
it-IT | italiano
ja-JP | 日本の (japonês)
kk-KZ | Қазақ (cazaque)
ko-KR | 한국의 (coreano)
lt-LT | Lietuvos (lituano)
lv-LV | Latvijas (letão)
ms-MY | Bahasa Melayu (malaio)
nb-NO | norsk (norueguês)
nl-NL | Nederlands (holandês)
pl-PL | Polski (polonês)
pt-BR | português
pt-PT | português
ro-RO | românesc (romeno)
ru-RU | русский (russo)
sk-SK | slovenský (eslovaco)
sl-SI | slovenski (esloveno)
sr-Cyrl-RS | Српски (sérvio)
sr-Latn-RS | srpski (sérvio)
sv-SE | Svenska (sueco)
th-TH | ไทย (tailandês)
tr-TR | Türk (turco)
uk-UA | український (ucraniano)
vi-VN | tiếng Việt (vietnamita)
zh-CN | 中国 (chinês simplificado)
zh-TW | 中國 (chinês tradicional)

> [!NOTE]
> Na área de trabalho do PowerBI, a propriedade de localidade conterá o idioma do PowerBI Desktop instalado.

## <a name="localizing-the-property-pane-for-custom-visuals"></a>Localizando o painel de propriedades para visuais personalizados

Os campos no painel de propriedades podem ser localizados a fim de fornecer uma experiência mais integrada e coerente. Isso faz com que seu visual personalizado se comporte como qualquer outro visual principal do Power BI.

Por exemplo, um visual personalizado não localizado criado usando o comando `pbiviz new` mostrará os seguintes campos no painel de propriedades:

![Localização no painel de propriedades](media/property-pane.png)

Os Dados da categoria e os Dados de medida são definidos no arquivo capabilities.json como `displayName`.

## <a name="how-to-localize-capabilities"></a>Como localizar funcionalidades

Primeiro, adicione uma chave de nome de exibição a cada nome de exibição que você deseja localizar em suas funcionalidades. Neste exemplo:

```json
{
    "dataRoles": [
        {
            "displayName": "Category Data",
            "displayNameKey": "VisualCategoryDataNameKey1",
            "name": "category",
            "kind": "Grouping"
        },
        {
            "displayName": "Measure Data",
            "displayNameKey": "VisualMeasureDataNameKey2",
            "name": "measure",
            "kind": "Measure"
        }
    ]
}
```

Em seguida, adicione um diretório chamado stringResources. O diretório conterá todos os arquivos de recursos de cadeia de caracteres diferentes com base nas localidades às quais você quiser que o visual dê suporte. Nesse diretório, você precisará adicionar um arquivo JSON para cada localidade à qual deseja dar suporte. Esses arquivos contêm as informações de localidade e os valores de cadeias de caracteres localizados para cada displayNameKey que você deseja substituir.

Em nosso exemplo, digamos que queremos dar suporte a árabe e hebraico. Será necessário adicionar dois arquivos JSON da seguinte maneira:

![Cadeias de caracteres de localização na pasta de recursos de cadeia de caracteres](media/stringresources-files.png)

Cada arquivo JSON define uma única localidade (esse arquivo deve ser uma das localidades da lista de suporte acima), com os valores de cadeia de caracteres referente às chaves de nome de exibição desejadas. Em nosso exemplo, o arquivo de recurso de cadeia de caracteres para o hebraico terá a seguinte aparência:

```json
{
    "locale": "he-IL",
    "values": {
        "VisualCategoryDataNameKey1": "קטגוריה",
        "VisualMeasureDataNameKey2": "יחידות מידה"
    }
}
```

Todas as etapas necessárias para usar o gerenciador de localização são descritas abaixo.

> [!NOTE]
> Atualmente, a localização não tem suporte para depurar o visual de desenvolvimento

## <a name="setup-environment"></a>Ambiente de configuração

### <a name="desktop"></a>Área de trabalho

Para uso da área de trabalho, baixe a versão localizada do Power BI Desktop em https://powerbi.microsoft.com.

### <a name="web-service"></a>Serviço Web

Se você usar o cliente Web (navegador) no serviço, altere o idioma nas configurações:

![Localização no serviço Web](media/webservice-settings.png)

## <a name="resource-file"></a>Arquivo de recurso

Adicione um arquivo resources.resjson a uma pasta com o nome da localidade que você usará dentro da pasta stringResources. Em nosso exemplo, eles são en-US e ru-RU.

![O novo arquivo resjson](media/new-resjson.png)

Depois disso, adicione todas as cadeias de caracteres de localização que você usará no arquivo resources.resjson que adicionou na etapa anterior.

```json
{
    ...
    "Role_Legend": "Обозначения",
    "Role_task": "Задача",
    "Role_StartDate": "Дата начала",
    "Role_Duration": "Длительность"
    ...
}
```

Este exemplo é a versão en-US do arquivo resources.resjson:

```json
{
    ...
    "Role_Legend": "Legend",
    "Role_task": "Task",
    "Role_StartDate": "Start date",
    "Role_Duration": "Duration"
    ...
}
```

Nova instância do localizationManager Crie uma instância do localizationManager no código do visual da seguinte maneira

```typescript
private localizationManager: ILocalizationManager;

constructor(options: VisualConstructorOptions) {
    this.localizationManager = options.host.createLocalizationManager();
}
```

## <a name="localizationmanager-usage-sample"></a>Exemplo de uso de localizationManager

Agora, você pode chamar a função getDisplayName do gerenciador de localização com o argumento de chave de cadeia de caracteres definido em resources.resjson para obter a cadeia de caracteres necessária em qualquer lugar de seu código:

```typescript
let legend: string = this.localization.getDisplayName("Role_Legend");
```

Ela retorna "Legend" para en-US e "Обозначения" para ru-RU

## <a name="next-steps"></a>Próximas etapas

* [Leia sobre como usar os utilitários de formatação para fornecer formatos localizados](utils-formatting.md)
