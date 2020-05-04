---
title: Dicas de desempenho
description: Como criar um visual de alto desempenho do Power BI
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 04/20/2020
ms.openlocfilehash: 7ebc02b2c459517957425e78438e12e89dc2e1bb
ms.sourcegitcommit: 1059c6222458f189fb5301dcb689dad2b2c00bc1
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2020
ms.locfileid: "82196550"
---
# <a name="how-to-build-a-high-performance-power-bi-visual"></a>Como criar um visual de alto desempenho do Power BI
Este artigo abordará técnicas sobre como um desenvolvedor pode alcançar um alto desempenho ao renderizar visuais. 

Ninguém quer que um visual leve muito tempo para ser renderizado e usar o máximo de desempenho que pode ser obtido com a codificação se torna crítico durante a renderização. 

> [!NOTE]
> À medida que continuamos aprimorando a plataforma, novas versões da API são lançadas constantemente. Para aproveitar a plataforma e o conjunto de recursos dos visuais do Power BI ao máximo, recomendamos que você se mantenha atualizado com a versão mais recente.
>
> Desde a última **versão 2.1**, em média, houve um aprimoramento de 20% dos tempos de carregamento de visuais do Power BI.

## <a name="power-bi-visual-performance-tips"></a>Dicas de desempenho de visuais do Power BI
Veja a seguir algumas recomendações sobre como obter um desempenho ideal de visuais. 

### <a name="use-user-timing-api"></a>Usar a API de Tempo de Usuário
O uso da **API de Tempo de Usuário** para medir o desempenho do JavaScript do aplicativo pode ajudar você a decidir quais partes do script precisam receber uma otimização.

Para obter mais informações, confira a [API de Tempo de Usuário](https://msdn.microsoft.com/library/hh772738(v=vs.85).aspx).

### <a name="review-animation-loops"></a>Examinar loops de animação
O loop de animação redesenha os elementos inalterados? 

 - Problema: desenhar elementos que não mudam de quadro para quadro é um desperdício de tempo.

 - Solução: atualize os quadros seletivamente. 
 
Quando chega o momento de animar visualizações estáticas, é tentador aglomerar um código de desenho em uma função de atualização e chamá-lo repetidamente com os novos dados para cada iteração do loop de animação.

Em vez disso, considere o padrão de atualização a seguir e use um método de construtor visual para desenhar tudo que é estático; em seguida, a função de atualização só precisará desenhar os elementos de visualização que foram alterados. 

   > [!TIP]
   > Loops de animação ineficientes geralmente são encontrados em eixos e legendas.

### <a name="cache-dom-nodes"></a>Nós DOM do cache 
Quando um nó ou uma lista de nós é recuperado do DOM, você precisa pensar se é possível reutilizá-los em cálculos posteriores (às vezes, até mesmo na próxima iteração do loop). Desde que você não precise adicionar nem excluir nós adicionais na área relevante, o cache deles pode aprimorar a eficiência geral do aplicativo.

Para garantir que o código seja rápido e não deixe o navegador mais lento, minimize o acesso ao DOM. 

- Antes: 

   ```javascript
   public update(options: VisualUpdateOptions) { 
       let axis = $(".axis"); 
   }
   ```

- Após: 

   ```javascript
   public constructor(options: VisualConstructorOptions) { 
       this.$root = $(options.element); 
       this.xAxis = this.$root.find(".xAxis"); 
   } 
 
   public update(options: VisualUpdateOptions) { 
       let axis = this.axis; 
   }
   ```

### <a name="avoid-dom-manipulation"></a>Evitar a manipulação do DOM 
Limite a manipulação do DOM o máximo possível.  Operações de inserção, como `prepend()`, `append()` e `after()`, são demoradas e não devem ser usadas, a menos que sejam necessárias.

Por exemplo:

  ```javascript
  for (let i=0; i<1000; i++) { 
      $('#list').append('<li>'+i+'</li>');
  }
  ```

O exemplo acima pode ser acelerado com `html()` e pela criação da lista antecipadamente: 

  ```javascript
  let list = ''; 
  for (let i=0; i<1000; i++) { 
      list += '<li>'+i+'</li>'; 
  } 

  $('#list').html(list); 
  ```

### <a name="reconsider-jquery"></a>Reconsiderar o JQuery

A limitação das estruturas JS e o uso do JS nativo sempre que possível podem aumentar a largura de banda disponível e reduzir a sobrecarga de processamento. Isso também pode limitar os problemas de compatibilidade com navegadores mais antigos. 

Para obter mais informações, confira [youmightnotneedjquery.com](http://youmightnotneedjquery.com/) para obter exemplos alternativos de funções como `show`, `hide`, `addClass` do JQuery, entre outros.  

### <a name="use-canvas-or-webgl"></a>Usar o Canvas ou o WebGL 
Para o uso repetido de animações, considere o uso do **Canvas** ou do **WebGL** em vez do SVG. Ao contrário do SVG, com essas opções, o desempenho é determinado pelo tamanho, em vez do conteúdo. 

Leia mais sobre as diferenças em [SVG versus Canvas: como escolher](https://msdn.microsoft.com/library/gg193983(v=vs.85).aspx). 

### <a name="use-requestanimationframe-instead-of-settimeout"></a>Usar requestAnimationFrame em vez de setTimeout 
Se você usar [requestAnimationFrame](https://www.w3.org/TR/animation-timing/) para atualizar as animações na tela, as funções de animação serão chamadas **antes** de o navegador chamar outro redesenho.

Para obter mais informações, confira esta [amostra](https://testdrive-archive.azurewebsites.net/Graphics/RequestAnimationFrame/Default.html) sobre animação suave com `requestAnimationFrame`.

## <a name="next-steps"></a>Próximas etapas

Saiba mais sobre técnicas de otimização no [Guia de otimização do Power BI](/power-bi/guidance/power-bi-optimization).
