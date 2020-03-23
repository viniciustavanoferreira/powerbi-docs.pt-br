---
title: Dicas e truques para fazer perguntas com P e R
description: Dicas e truques para fazer perguntas com a P e R no Power BI
author: mihart
ms.reviewer: Mohammad
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 03/11/2020
ms.author: mihart
LocalizationGroup: Ask questions of your data
ms.openlocfilehash: d97ff72c385edd4c59c6eb72ce1eb873656923c9
ms.sourcegitcommit: 6bbc3d0073ca605c50911c162dc9f58926db7b66
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79376812"
---
# <a name="tips-for-asking-questions-in-power-bi-qa"></a>Dicas para fazer perguntas na P e R do Power BI

[!INCLUDE[consumer-appliesto-yyny](../includes/consumer-appliesto-yyny.md)]

## <a name="words-and-terminology-that-qa-recognizes"></a>Palavras e terminologia reconhecida pela P e R
A lista de palavras-chave nesta página não é abrangente.  A melhor maneira de ver se o Power BI reconhece uma palavra-chave é testá-la digitando-a na caixa de perguntas.  Se a palavra ou o termo estiver esmaecido, o Power BI não o reconhece.

A lista abaixo usa o presente do indicativo, mas, na maioria dos casos, todos os tempos verbais são reconhecidos. Por exemplo, "é" inclui: **são**, **foi**, **foram**, **será**, **tem**, **têm**, **tinha**, **terão**, **teve**, **fazem**, **faz**, **fez**.  Além disso, "classifica" inclui **classificou** e **classificando**.  O Power BI também reconhece e inclui as versões singular e plural de uma palavra. 

> [!NOTE]
> P e R também está disponível no [aplicativo do Microsoft Power BI para iOS nos dispositivos iPod Touch, iPhones e iPads](mobile/mobile-apps-ios-qna.md).
>  


|Categoria  |Palavras-chave  |Column3  |
|---------|---------|---------|
|**Agregações**     | total, soma, valor, número, quantidade, contagem, média, no máximo, no mínimo, menos, mais, maior, menor, mais alto, mais baixo, grande, pequeno, máximo, máx, melhor, pior, mínimo, mín          |
|     |         |         
**Artigos**     |  um, uma, o, a              |
|     |         |         
|**Em branco e Booliano**     |   em branco, vazio, nulo, prefixado com "não" ou "não-", cadeia de caracteres vazia, texto vazio, verdadeiro, v, falso, f          |
|     |         |         |
|**Comparações**     |   vs, versus, comparado a, em comparação com            |
|     |         |         |
|**Conjunções**     |  e, ou, cada um de, com, versus, mas, nem, juntamente com, além de       |         
|          |         |
|**Contrações**     |  P e R reconhece quase todas as contrações, é só experimentar.  Aqui estão alguns exemplos: não fiz, não tenho, ele fez, ele é, ele não é, isso é, ela vai, eles fizeram, não eram, quem é, não vai, não iria          |
|        |         |
|**Datas**     |       O Power BI reconhece a maioria dos termos de data (dia, semana, mês, ano, trimestre, década, etc.) e datas escritas em vários formatos diferentes (veja abaixo). O Power BI também reconhece as seguintes palavras-chave: MonthName, Dias 1 a 31, década. Exemplos: 3 de janeiro de 1995, 3 janeiro 1995, 3 jan 1995, 03 jan 95, 3 de janeiro, janeiro de 1995, jan 1995, 1995/01, 01/95, nomes de meses         |
|        |         |
|**Datas relativas**     |   hoje, agora, hora atual, ontem, amanhã, atual, próximo, a seguir, último, anterior, atrás, um momento atrás, antes de, depois, depois de, a partir de, às, a partir de agora, um momento mais tarde, no futuro, passado, anterior, em, ao longo de, N dias atrás, N dias a partir de hoje, no próximo, uma vez, duas vezes.|
|    |  Exemplo: contagem de pedidos nos últimos 6 dias.  |            |
|        |         |
|**Igualdade (Intervalo)**     |   em, igual a, =, depois, é maior que, em, entre, antes, anterior, posterior  |
|  |Exemplos: O ano do pedido é anterior a 2012? O preço está entre 10 e 20? A idade de Marcelo é maior que 40? Total de vendas em 200-300?              |
|        |         |
|**Igualdade (Valor)**     |   é, igual, igual a, em, de, para, dentro de, está em, está no(a) |
|   | Exemplos: Quais produtos são verdes? A data do pedido é igual a 2012. A idade de Marcelo é 40? Total de vendas que não é igual a 200? A data do pedido de 1/1/2016. 10 no preço? De cor verde? 10 no preço?              |
|        |         |
|**Nomes**     |       Se uma coluna no conjunto de dados contiver a frase "nome" (por exemplo, NomeDoFuncionário), a P e R entenderá que os valores nessa coluna são nomes. Você pode fazer perguntas como "quais funcionários se chamam pedro."          |
|        |         |
**Pronomes**  | ele/ela, dele/dela, ele mesmo/ela mesma, seu/sua, isso, isso mesmo, isto, este, esse, deste, disto, desta, aquela
|**Comandos de consulta**     |    classificado, classificar por, direção, grupo, agrupar por, por, mostrar, listar, exibir, me dê, nomear, apenas, somente, organizar, comparar, com, em relação a, em ordem alfabética, em ordem crescente, em ordem decrescente, ordenar             |
|        |         |
|**Intervalo**     |      maior que, mais que, acima de, superior a, >, menos que, menor que, abaixo de, sob, <, pelo menos, não menor que, >=, no máximo, não mais que, <=, em, entre, no intervalo de, a partir de, posterior a, anterior a, após, em, às, depois, antes de, desde, com início em, com término em           |
|        |         |
**Vezes**  |am, pm, horas, em ponto, meio-dia, meia-noite, hora, minuto, segundo, hh:mm:ss  |
|  |  Exemplos: 22h, 22h35, 22h35min15s, 10 da noite, meio-dia, meia-noite, hora, minuto, segundo.  |
|  |  |
|**N superior**     |     (ordem, classificação): superior, inferior, o maior, o menor, o primeiro, o último, o próximo, o mais recente, o mais antigo, o mais novo            |
|        |         |
|**Tipos de visual**     |  todos os tipos de visual nativos do Power BI.  Se esta for uma opção no painel Visualizações, você poderá incluí-la em sua pergunta.  A exceção a esta regra são [visuais do Power BI](../developer/visuals/power-bi-custom-visuals.md) que você adicionou manualmente ao painel Visualização.  |
|  |  Exemplo: mostrar distritos por mês e vendas total como um gráfico de barras               |
|        |         |
|**Palavras interrogativas (relação, qualificada)**  | quando, onde, qual, quem, quanto, quantos, quantas vezes, com que frequência, qual valor, quantidade, número, valor, quanto tempo, o que                |

## <a name="qa-helps-you-phrase-the-question"></a>A P e R ajuda a formular a pergunta
A P e R faz todo o possível para entender e responder à pergunta que está sendo feita. Tenta entender de várias maneiras. Para todas essas frases, é possível aceitar a ação completa, a ação parcial ou não aceitá-la. Ao digitar sua pergunta, a P e R:

* preenche automaticamente palavras e perguntas. Ela usa várias estratégias, incluindo o preenchimento automático de palavras reconhecidas, perguntas armazenadas e perguntas usadas anteriormente que retornaram respostas válidas. Se houver mais de uma opção de preenchimento automático disponível, elas serão apresentadas em uma lista suspensa.
* corrige a ortografia.
* fornece uma visualização da resposta na forma de um visual. O visual é atualizado conforme você digita e edita a pergunta (ele não aguarda até que você pressione Enter).
* sugere termos de substituição do(s) conjunto(s) de dados subjacente(s) quando você move o cursor de volta para a caixa de pergunta.
* reformula a pergunta com base nos dados do(s) conjunto(s) de dados subjacente(s). A P e R substitui as palavras usadas por sinônimos do(s) conjunto(s) de dados subjacente(s). Ao ler a reformulação, você sabe se a P e R entendeu sua pergunta ou não. 
* adiciona um sublinhado duplo às palavras que ele não entende.
* adiciona um sublinhado simples às palavras que ele entende.
* permite que você entre em contato com o proprietário do relatório ou do dashboard quando seu termo não for encontrado ou sua pergunta não obtiver resultados.

## <a name="dont-stop-now"></a>Não parar agora
Depois que a P e R exibir os resultados, é só conversar! Use os recursos interativos do visual e da P e R para descobrir mais informações.

## <a name="next-steps"></a>Próximas etapas
Voltar a [P e R no Power BI](end-user-q-and-a.md)  

[Power BI – conceitos básicos](end-user-basic-concepts.md)  

Mais perguntas? [Experimente a Comunidade do Power BI](https://community.powerbi.com/)

