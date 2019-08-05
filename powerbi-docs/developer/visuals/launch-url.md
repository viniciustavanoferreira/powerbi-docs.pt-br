---
title: URL de inicialização
description: Visuais do Power BI podem abrir a URL na nova guia
author: Guy-Moses
ms.author: guymos
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 1a7002c3b45f341c0cbc0db683bc4f8a113e21f9
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68424851"
---
# <a name="launch-url"></a>URL de inicialização

A URL de inicialização permite abrir uma nova guia (ou janela) do navegador, delegando o trabalho real ao Power BI.

## <a name="sample"></a>Exemplo

```typescript
   this.host.launchUrl('https://powerbi.microsoft.com');
```

## <a name="usage"></a>Uso

Use a chamada à API `host.launchUrl()` passando a URL de destino como um argumento de cadeia de caracteres:

```typescript
this.host.launchUrl('http://some.link.net');
```

## <a name="restrictions"></a>Restrições

* Use apenas caminhos absolutos, não relativos. `http://some.link.net/subfolder/page.html` está ok, `/page.html` não será aberto.
* Atualmente, somente os protocolos `http` e `https` têm suporte. Evite `ftp`, `mailto` e assim por diante.

## <a name="best-practices"></a>Práticas recomendadas

1. Na maioria dos casos, é melhor abrir apenas um link como uma resposta à ação explícita de um usuário. Facilite para o usuário entender que clicar no link ou no botão resultará na abertura de uma nova guia. Disparar uma chamada `launchUrl()` sem uma ação do usuário ou como um efeito colateral de uma ação diferente pode ser confuso ou frustrante para o usuário.
2. Se o link não for crucial para o funcionamento correto do visual, ele será redirecionado para fornecer ao autor do relatório uma maneira de desabilitar e ocultar o link. Isso é especialmente relevante para casos especiais de uso de Power BI, como inserir um relatório em um aplicativo de terceiros ou publicá-lo na Web.
3. Evite disparar uma chamada `launchUrl()` de dentro de um loop, a função `update` do visual ou qualquer outro código recorrente com frequência.

## <a name="step-by-step-example"></a>Exemplo passo a passo

### <a name="adding-a-link-launching-element"></a>Adicionando um elemento de inicialização de link

As linhas a seguir foram adicionadas à função `constructor` do visual:

```typescript
    this.helpLinkElement = this.createHelpLinkElement();
    options.element.appendChild(this.helpLinkElement);
```

E uma função particular que cria e anexa o elemento de âncora foi adicionada:

```typescript
private createHelpLinkElement(): Element {
    let linkElement = document.createElement("a");
    linkElement.textContent = "?";
    linkElement.setAttribute("title", "Open documentation");
    linkElement.setAttribute("class", "helpLink");
    linkElement.addEventListener("click", () => {
        this.host.launchUrl("https://docs.microsoft.com/power-bi/developer/custom-visual-develop-tutorial");
    });
    return linkElement;
};
```

Por fim, uma entrada no arquivo visual.less define o estilo para o elemento link:

```less
.helpLink {
    position: absolute;
    top: 0px;
    right: 12px;
    display: block;
    width: 20px;
    height: 20px;
    border: 2px solid #80B0E0;
    border-radius: 20px;
    color: #80B0E0;
    text-align: center;
    font-size: 16px;
    line-height: 20px;
    background-color: #FFFFFF;
    transition: all 900ms ease;

    &:hover {
        background-color: #DDEEFF;
        color: #5080B0;
        border-color: #5080B0;
        transition: all 250ms ease;
    }

    &.hidden {
        display: none;
    }
}
```

### <a name="adding-a-toggling-mechanism"></a>Adicionar um mecanismo de alternância

Isso requer a adição de um objeto estático (consulte o [tutorial de objeto estático](https://microsoft.github.io/PowerBI-visuals/docs/concepts/objects-and-properties)) para que o autor do relatório possa alternar a visibilidade do elemento link (o padrão é definido como oculto).
Um objeto `showHelpLink` estático booliano foi adicionado à entrada de objetos `capabilities.json`:

```typescript
"objects": {
    "generalView": {
            "displayName": "General View",
            "properties":
                "showHelpLink": {
                    "displayName": "Show Help Button",
                    "type": {
                        "bool": true
                    }
                }
            }
        }
    }
```

![Ativar/desativar URL](./media/launchurl-toggle.png)

E, na função `update` do visual, as seguintes linhas foram adicionadas:

```typescript
if (settings.generalView.showHelpLink) {
    this.helpLinkElement.classList.remove("hidden");
} else {
    this.helpLinkElement.classList.add("hidden");
}
```

A classe `hidden` é definida em visual.Less para controlar a exibição do elemento.
