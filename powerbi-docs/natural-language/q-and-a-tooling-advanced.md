---
title: Editar o esquema linguístico de P e R e adicionar frases no Power BI Desktop
description: Como usar o Power BI Desktop para editar o esquema linguístico usado por P e R do Power BI.
author: mohaali
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 10/18/2019
ms.author: mohaali
ms.openlocfilehash: d1ae995c3e98befe776ac091a0312e281e97022e
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/09/2019
ms.locfileid: "73875343"
---
# <a name="edit-qa-linguistic-schema-and-add-phrasings-in-power-bi-desktop"></a>Editar o esquema linguístico de P e R e adicionar frases no Power BI Desktop 
Usar linguagem natural e expressões comuns para fazer perguntas sobre seus dados é eficiente. Ainda mais avançado é quando os seus dados respondem. Quando você faz uma pergunta para P e R do Power BI, ele se esforça para responder corretamente. Porém, para interações de P e R ainda melhores, você pode aprimorar as respostas. Uma maneira de fazer isso é editar o esquema linguístico. 

Tudo começa com os dados empresariais.  Quanto melhor for o modelo de dados, mais fácil será para que os usuários recebam respostas de qualidade. Uma maneira de melhorar o modelo é adicionar um esquema linguístico que defina e categorize a terminologia e as relações entre os nomes de tabela e de coluna no conjunto de dados. O Power BI Desktop é onde você gerencia seus esquemas linguísticos. 

Existem dois lados de P e R.  O primeiro lado é a preparação ou *modelagem*.  O segundo lado é fazer perguntas e explorar os dados ou *consumi-los*. Em algumas empresas, os funcionários conhecidos como *modeladores de dados* ou administradores de TI podem ser aqueles que montam os conjuntos de dados, criam os modelos de dados e publicam os conjuntos de dados no Power BI.  Um conjunto diferente de funcionários são aqueles que "consomem" os dados online.  Em outras empresas, essas funções podem ser combinadas. 

Este artigo destina-se aos modeladores de dados, as pessoas que otimizam os conjuntos de dados para fornecer os melhores resultados de P e R possíveis. 

## <a name="what-is-a-linguistic-schema"></a>O que é um esquema linguístico?
Um esquema linguístico descreve os termos e as frases que as P e R devem compreender para os objetos dentro de um conjunto de dados, incluindo classes gramaticais, sinônimos e frases em relação a esse conjunto de dados. Quando você importa um conjunto de dados ou se conectar a ele, o Power BI cria um esquema linguístico com base na estrutura do conjunto de dados. Quando você faz uma pergunta às P e R, elas buscam correspondências e relações nos dados para descobrir a intenção da pergunta. Por exemplo, elas procuram substantivos, verbos, adjetivos, frases e outros elementos. E elas também procuram relações, como quais colunas são objetos de um verbo. 

Provavelmente, você já conhece as classes gramaticais (caso contrário, confira abaixo), mas *fraseamentos* podem ser um termo novo.  Um fraseamento é a maneira como você fala (ou *fraseia*) sobre as relações entre as coisas. Por exemplo, para descrever a relação entre produtos e clientes, você pode dizer "os clientes compram produtos". Ou para descrever a relação entre os clientes e as idades, você pode dizer "as idades indicam quantos anos os clientes têm". Ou, para descrever a relação entre os clientes e os números de telefone, você pode simplesmente dizer "os clientes têm números de telefone".

Essas frases podem ter uma variedade de formas e tamanhos. Algumas correspondem diretamente às relações no modelo de dados. Algumas relacionam colunas com as tabelas que as contêm. Outras relacionam várias tabelas e colunas em relações complexas. Em todos os casos, elas descrevem como os elementos são relacionados, usando termos comuns.

Os esquemas linguísticos são salvos no formato .yaml. Esse formato está relacionado ao renomado formato JSON, mas oferece uma sintaxe mais flexível e mais fácil de ler. Os esquemas linguísticos podem ser editados, exportados e importados para o Power BI Desktop.

## <a name="prerequisites"></a>Pré-requisitos

- Se você ainda não leu o artigo em [melhorando seu modelo de dados para P e R](q-and-a-best-practices.md), talvez convenha lê-lo primeiro. Ele inclui diversas dicas para projetar e melhorar seu modelo de dados e uma seção importante sobre como adicionar sinônimos.  
- Baixe [arquivos .yaml e .pbix](https://go.microsoft.com/fwlink/?linkid=871858) de exemplo.   
- Instale um editor de arquivo .yaml. Recomendamos o [Visual Studio Code](https://code.visualstudio.com/).

### <a name="set-up-an-editor-for-yaml-files"></a>Configurar um editor para arquivos .yaml
Recomendamos usar o Visual Studio Code para editar arquivos .yaml de esquema linguístico. O Visual Studio Code inclui suporte pronto para uso para arquivos .yaml e pode ser estendido para validar especificamente o formato do esquema linguístico do Power BI.
1. Instale o [Visual Studio Code](https://code.visualstudio.com/).    

2. Selecione o esquema linguístico de exemplo salvo anteriormente: [arquivo .yaml](https://go.microsoft.com/fwlink/?linkid=871858) (SummerOlympics.lsdl.yaml).    
4. Selecione **Visual Studio Code** e **Sempre usar este aplicativo para abrir arquivos .yaml**.

    ![Como você deseja abrir este arquivo](media/q-and-a-tooling-advanced/power-bi-visual-code.png)

4. No Visual Studio Code, instale o suporte para YAML pela extensão do Red Hat.    
    a. Selecione a guia **Extensões** (a última à esquerda) ou pressione CTRL + SHIFT + X.    
    ![ícone de extensões](media/q-and-a-tooling-advanced/power-bi-extensions.png)    
    b. Procure "yaml" e selecione **Suporte para YAML pelo Red Hat** na lista.    
    c. Selecione **Instalar > Recarregar**.


## <a name="working-with-linguistic-schemas"></a>Trabalhando com esquemas linguísticos

Há duas maneiras de trabalhar com esquemas linguísticos. Uma maneira é editar, importar e exportar o .yaml na faixa de opções do Power BI Desktop. Essa maneira é abordada no artigo [Experiência com as ferramentas de P e R](q-and-a-tooling-intro.md) do Power BI. Você não precisa abrir o arquivo .yaml para melhorar a P e R. 

A outra maneira de editar um esquema linguístico é exportar e editar o arquivo .yaml diretamente.  Ao editar um arquivo .yaml de esquema linguístico, você marca colunas na tabela como diferentes elementos gramaticais e define as palavras que um colega pode usar para enunciar uma pergunta. Por exemplo, você poderia declarar as colunas que são o sujeito e o objeto do verbo. Adicione palavras alternativas que seus colegas podem usar para se referir a tabelas, colunas e medidas no seu modelo. 

![Arquivo .yaml de esquema linguístico de exemplo](media/q-and-a-tooling-advanced/power-bi-linguistic-schema.png)

Para editar um esquema linguístico, você precisará abri-lo (exportá-lo) do Power BI Desktop. Salvar o arquivo .yaml novamente na mesma localização é considerado uma importação.  Mas, em vez disso, você também pode importar outros arquivos .yaml.  Se, por exemplo, você tem um conjunto de dados semelhante e já trabalhou muito adicionando classes gramaticais, identificando relações, criando fraseamentos e sinônimos, use esse arquivo .yaml em outro arquivo do Power BI Desktop. 

As P e R usam todas essas informações em conjunto com todos os aprimoramentos feitos por você para melhorar as respostas, o preenchimento automático e o resumo das perguntas.

## <a name="edit-a-linguistic-schema"></a>Editar um esquema linguístico
Quando você exporta o esquema linguístico do Power BI Desktop pela primeira vez, a maior parte do conteúdo do arquivo, ou todo ele, é gerada automaticamente pelo mecanismo de P e R. Estas entidades, palavras (sinônimos), relações e frases geradas são designadas com uma marca **Estado: Gerado**. Elas são incluídas no arquivo principalmente para fins informativos, mas podem ser um ponto de partida útil para suas próprias alterações. 

> [!NOTE]
> O arquivo .yaml de exemplo incluído neste tutorial não contém as marcas **Estado:Gerado** ou **Estado:Excluído**, pois ele foi preparado especialmente para este tutorial. Para ver essas marcas, abra um arquivo .pbix não editado na exibição Relações e exporte o esquema linguístico.

![YAML mostrando Estado: Gerado](media/q-and-a-tooling-advanced/power-bi-generated-state.png)

Ao importar o arquivo de esquema linguístico novamente no Power BI Desktop, tudo o que estiver marcado como **Estado: Gerado** é ignorado e, depois, regenerado. Portanto, se você deseja alterar um conteúdo gerado, remova também a marca correspondente **Estado: Gerado**. Da mesma forma, se você deseja remover um conteúdo gerado, altere a marca **Estado: Gerado** para o **Estado: Excluído** para que ele não seja regenerado ao importar o arquivo de esquema linguístico.

### <a name="export-then-import-a-yaml-file"></a>Exportar e, em seguida, importar um arquivo .yaml

1. Abra o conjunto de dados na exibição Modelo no Power BI Desktop. 
2. Na guia **Modelagem**, selecione **Esquema Linguístico** > **Exportar esquema linguístico**.
3. Salve-o. O nome do arquivo termina com .lsdl.yaml.
4. Abra-o no Visual Code ou em outro editor.
4. Na exibição Modelo no Power BI Desktop, na guia **Modelagem**, selecione **Esquema Linguístico** > **Importar esquema linguístico**. 
6. Navegue até a localização em que você salvou o arquivo .yaml editado e selecione-o. Uma mensagem de êxito informa que o arquivo .yaml de esquema linguístico foi importado com êxito.

    ![Mensagem de êxito](media/q-and-a-tooling-advanced/power-bi-success.png)

## <a name="phrasings-in-the-linguistic-schema"></a>Fraseamentos no esquema linguístico
Novamente, um fraseamento é a maneira como você fala (ou “fraseia”) sobre as relações entre as coisas. Por exemplo, para descrever a relação entre produtos e clientes, você pode dizer "os clientes compram produtos".

## <a name="where-do-phrasings-come-from"></a>De onde vêm as frases?
O Power BI adiciona muitas frases simples ao esquema linguístico automaticamente, com base na estrutura do modelo e em algumas suposições com base nos nomes das colunas. Por exemplo:
- A maioria das colunas está relacionada à tabela que as contém com um fraseamento simples, como “os produtos têm descrições”.
- As relações de modelo resultam em fraseamentos padrão para ambas as direções da relação, como “os pedidos têm produtos” e “os produtos têm pedidos”.
- Algumas relações de modelo podem ter uma frase padrão mais complexa, com base em seus nomes de coluna, como "os pedidos são enviados para cidades".

No entanto, os usuários podem falar sobre as coisas de diversas maneiras, as quais a P e R não consegue adivinhar. Por isso, o ideal é adicionar seus próprios fraseamentos manualmente.

## <a name="why-add-phrasings"></a>Por que adicionar fraseamentos?
O primeiro motivo para adicionar uma frase é definir um novo termo. Por exemplo, para poder solicitar uma "lista dos clientes mais velhos", primeiro você precisará ensinar às P e R qual o significado de "antigos". Isso poderá ser feito adicionando uma frase como "as idades indicam quantos anos os clientes têm".

O segundo motivo para adicionar uma frase é resolver a ambiguidade. A pesquisa básica de palavra-chave só chega a esse ponto quando as palavras têm mais de um significado. Por exemplo, “voos para Chicago” não é igual a “voos de Chicago”. Mas as P e R apenas saberão qual delas você quer dizer se você adicionar as frases “os voos são das cidades de saída” e “os voos são para as cidades de chegada”. Da mesma forma, as P e R só entenderão a diferença entre “carros que Pedro vendeu para Teresa” e “carros que Pedro comprou de Teresa” se você adicionar as frases “clientes compram carros de funcionários” e “funcionários vendem carros para os clientes”.

O motivo final para adicionar uma frase é melhorar as reformulações. Em vez das P e R retornarem “Mostrar os clientes e seus produtos”, seria mais claro se elas retornassem “Mostrar os clientes e os produtos que eles compraram” ou “Mostrar os clientes e os produtos que eles examinaram”, dependendo de como elas compreenderem a pergunta. Adicionar frases personalizadas permite que as reformulações sejam mais explícitas e não sejam ambíguas.


## <a name="kinds-of-phrasings"></a>Tipos de fraseamentos
Para entender os diferentes tipos de frases, primeiro você precisará se lembrar de alguns termos de gramática básica:
- Um *substantivo* é uma pessoa, um lugar ou uma coisa. 
    Exemplos: carro, adolescente, Rita, capacitor de fluxo
- Um *verbo* é uma ação ou um estado de ser. 
    Exemplos: eclodir, estourar, devorar, ejetar
- Um *adjetivo* é uma palavra descritiva que modifica um substantivo. 
    Exemplos: poderoso, mágico, dourado, roubado
- Uma *preposição* é uma palavra usada antes de um substantivo para relacioná-lo a um substantivo, um verbo ou um adjetivo anterior Exemplos: de, para, com, até
-  Um *atributo* é um recurso ou uma qualidade de algo.
-  Um *nome* é uma palavra ou um conjunto de palavras pelo qual uma pessoa, um animal, uma coisa ou um lugar é referenciado.   


### <a name="attribute-phrasings"></a>Frases de atributo
As frases de atributo são o ponto forte de P e R, usadas quando algo está agindo como um atributo de algo. Elas são simples e diretas, e executam a maior parte do trabalho pesado quando uma frase mais específica e detalhada não foi definida. As frases de atributo são descritas usando o verbo básico “tem” (“produtos têm categorias” e “países-sede têm cidades-sede”). Elas também aceitam automaticamente perguntas com as preposições “de” e “para” (“categorias de produtos”, “pedidos de produtos”) e possessivos (“pedidos de João”). As frases de atributo são usadas em perguntas como esta:

- Quais clientes têm pedidos?
- Listar cidades host por país em ordem crescente
- Mostrar pedidos que tenham chai
- Listar clientes com pedidos
- Qual é a categoria de cada produto?
- Contar os pedidos de Vinicius Monte    

O Power BI gera a grande maioria das frases de atributo necessárias no seu modelo, com base na independência de tabela/coluna e relações de modelos. Normalmente, você não precisa criá-los.
Este é um exemplo da aparência de um fraseamento de atributo no esquema linguístico:

```json
product_has_category:
  Binding: {Table: Products}
  Phrasings:
  - Attribute: {Subject: product, Object: product.category}
```
 
### <a name="name-phrasings"></a>Frases de nome
Os fraseamentos de nome serão úteis se o modelo de dados tiver uma tabela que contém objetos nomeados, como nomes de atletas e nomes de clientes. Por exemplo, uma frase "nomes para produto são nomes de produtos" é essencial para que você possa usar nomes para produtos em perguntas. Frases de nome também habilitam “chamado” como um verbo (por exemplo, “Listar clientes chamados Pedro Silva”). Contudo, elas são mais importantes quando usadas junto com outras frases, para permitir que um valor de nome seja usado para se referir a uma linha de tabela específica. Por exemplo, em “Clientes que compraram chai”, as P e R podem deduzir que o valor “chai” se refere a toda a linha da tabela de produtos e não apenas a um valor na coluna de nome de produto. As frases de nome são usadas em perguntas como esta:    
- Quais funcionários chamam Vinicius Monte
- Quem chama Tiago Ribeiro
- Esportes de Samuel Costa
- Contagem de atletas chamadas Teresa
- O que Vinicius Monte comprou?

Supondo que você usou uma convenção de nomenclatura sensata para colunas de nome no seu modelo (por exemplo, “Nome” ou “ProductName” em vez de “PrdNm”), o Power BI gera a maioria das frases de nome necessárias no seu modelo automaticamente, por isso normalmente você não precisa criá-los por conta própria.

Este é um exemplo de como as frases de nome aparecem dentro do esquema linguístico:

```json
employee_has_name:
  Binding: {Table: Employees}
  Phrasings:
  - Name:
      Subject: employee
      Name: employee.name
```

 
### <a name="adjective-phrasings"></a>Fraseamentos de adjetivo
As frases adjetivas definem novos adjetivos usados para descrever coisas no modelo. Por exemplo, a frase "clientes satisfeitos são aqueles com classificação maior que seis" é necessária para fazer perguntas como "listar os clientes satisfeitos em Des Moines". Há vários formatos de frases adjetivas para serem usados em situações diferentes.

As *frases adjetivas simples* definem um adjetivo novo com base em uma condição, como "os produtos preteridos são aqueles com status igual a D". As frases adjetivas simples são usadas em perguntas como esta:
- Quais produtos foram preteridos?
- Listar os produtos preteridos
- Listar os medalhistas de ouro
- Produtos que estão pendentes

Este é um exemplo da aparência de um fraseamento de adjetivo simples no esquema linguístico:

o_produto_foi_preterido:

```json
Binding: {Table: Products}
  Conditions:
  - Target: product.discontinued
    Operator: Equals
    Value: true
  Phrasings:
  - Adjective:
      Subject: product
      Adjectives: [discontinued]
```

Os *fraseamentos de adjetivo de medida* definem um novo adjetivo com base em um valor numérico que indica até que ponto o adjetivo se aplica, como “tamanhos indicam a extensão dos rios” e "países pequenos/regiões pequenas têm extensões de terra pequenas". As frases adjetivas de medida são usadas em perguntas destes tipos:
- Listar os rios longos
- Quais rios são os mais longos?
- Listar os menores países/as menores regiões que ganharam medalhas de ouro no basquete
- Qual o comprimento do Rio Grande?

Este é um exemplo da aparência de um fraseamento de adjetivo de medida no esquema linguístico:

o_rio_tem_comprimento:

 ```json
Binding: {Table: Rivers}
  Phrasings:
  - Adjective:
      Subject: river
      Adjectives: [long]
      Antonyms: [short]
      Measurement: river.length
```

As *frases adjetivas dinâmicas* definem um conjunto de adjetivos novos com base nos valores de uma coluna no modelo, por exemplo, "as cores descrevem os produtos" e “os eventos têm gêneros de eventos”. As frases adjetivas dinâmicas são usadas em perguntas como esta:
- Listar os produtos vermelhos
- Quais produtos são verdes?
- Mostrar eventos de patinação para mulheres
- Contar problemas que estão ativos

Este é um exemplo da aparência de um fraseamento de adjetivo dinâmico no esquema linguístico:

o_produto_tem_cor:
```json
Binding: {Table: Products}
  Phrasings:
  - DynamicAdjective:
      Subject: product
      Adjective: product.color
```

 
### <a name="noun-phrasings"></a>Frases nominais
As frases nominais definem nomes novos que descrevem subconjuntos de coisas no modelo. Elas geralmente incluem algum tipo de medida ou de condição específica do modelo. Por exemplo, para nosso modelo Olimpíadas, o ideal é adicionar fraseamentos que distinguem campeões de medalhistas, esportes com bola de esportes aquáticos, equipes de indivíduos, categorias de idade dos atletas (adolescentes, adultos, seniores) etc. Para nosso banco de dados de filmes, é possível adicionar frases nominais para “fracassos são filmes com lucro líquido < 0” para fazer perguntas como “contar os fracassos por ano”. Há dois formatos de frases nominais para serem usados em situações diferentes.

As *frases nominais simples* definem um substantivo novo com base em uma condição, como "prestadores de serviço são funcionários em que tempo total é igual a false" e "campeão é um atleta para o qual a contagem de medalhas é maior que cinco". As frases nominais simples são usadas em perguntas como esta:

- Quais funcionários são prestadores de serviço?
- Contar os prestadores de serviço em Portland
- Quantos campeões houve em 2016

Este é um exemplo da aparência de um fraseamento de substantivo simples no esquema linguístico:

o_funcionário_é_prestador_de_serviço:

```json
Binding: {Table: Employees}
  Conditions:
  - Target: employee.full_time
    Operator: Equals
    Value: false
  Phrasings:
  - Noun:
      Subject: employee
      Nouns: [contractor]
```

As *frases nominais dinâmicas* definem um conjunto de substantivos novos com base nos valores em uma coluna do modelo, como "trabalhos definem subconjuntos de funcionários". As frases nominais dinâmicas são usadas em perguntas como esta:

- Listar os caixas em Chicago
- Quais funcionários são baristas?
- Listar os árbitros em 1992

Este é um exemplo de como uma frase nominal dinâmica aparece dentro do esquema linguístico: o_funcionário_tem_trabalho:

 ```json
Binding: {Table: Employees}
  Phrasings:
  - DynamicNoun:
      Subject: employee
      Noun: employee.job
```

### <a name="preposition-phrasings"></a>Frases prepositivas
As frases prepositivas são usadas para descrever como as coisas no modelo são relacionadas por meio de preposições. Por exemplo, uma frase "as cidades estão em países" melhora a compreensão de perguntas como "contar as cidades em Washington". Algumas frases prepositivas são criadas automaticamente quando uma coluna é reconhecida como uma entidade geográfica. As frases prepositivas são usadas em perguntas como esta:

- Contar os clientes em Nova York
- Listar os livros sobre linguística
- Em qual cidade está Marco Santos?
- Há quantos livros de Stephen Pinker?
 
Este é um exemplo de como uma frase prepositiva aparece dentro do esquema linguístico: os_clientes_estão_em_cidades:

 ```json
Binding: {Table: Customers}
  Phrasings:
  - Preposition:
      Subject: customer
      Prepositions: [in]
      Object: customer.city
```

 
### <a name="verb-phrasings"></a>Fraseamentos de verbo
As frases verbais são usadas para descrever como as coisas no modelo são relacionadas por meio de verbos. Por exemplo, uma frase "os clientes compram produtos" melhora a compreensão de perguntas como "quem comprou queijo?" e "o que Pedro comprou?" As frases verbais são as mais flexíveis de todos os tipos de frases, geralmente relacionando mais de duas coisas entre si, como em "os funcionários vendem produtos para clientes". As frases verbais são usadas em perguntas como esta:

- Quem vendeu o que a quem?
- Qual funcionário vendeu chai para Pedro?
- Quantos clientes compraram chai de Teresa?
- Listar os produtos que Teresa vendeu a Pedro.
- Quais produtos preteridos foram vendidos para clientes de Chicago por funcionários de Boston?

As frases verbais também podem conter frases prepositivas, que aumentam a flexibilidade, como em "os atletas ganham medalhas em competições" ou "os clientes recebem reembolsos de produtos". As frases verbais com frases prepositivas são usadas nesses tipos de perguntas:

- Quantos atletas ganharam uma medalha de ouro no campeonato Visa?
- Quais cientes receberam reembolso para queijo?
- Em qual competição Danell Leyva ganhou uma medalha de bronze?

Algumas frases verbais são criadas automaticamente quando uma coluna é reconhecida por conter um verbo e uma preposição.

Este é um exemplo de como uma frase verbal aparece dentro do esquema linguístico: os_clientes_compram_produtos_de_vendedores:

```json
Binding: {Table: Orders}
  Phrasings:
  - Verb:
      Subject: customer
      Verbs: [buy, purchase]
      Object: product
      PrepositionalPhrases:
      - Prepositions: [from]
        Object: salesperson
```

### <a name="relationships-with-multiple-phrasings"></a>Relações com várias frases
Frequentemente, uma única relação pode ser descrita de mais de uma maneira. Nesse caso, uma única relação pode ter mais de uma frase. É comum que uma relação entre uma entidade de tabela e uma entidade de coluna tenha uma frase de atributo e outra frase. Por exemplo, na relação entre o cliente e o nome do cliente, é recomendável ter tanto uma frase de atributo (por exemplo, “clientes têm nomes”) quanto uma frase de nome (por exemplo, “nomes de clientes são os nomes dos clientes”) para que seja possível fazer os dois tipos de perguntas.

Este é um exemplo de como uma relação com duas frases aparece dentro do esquema linguístico: o_cliente_tem_nome:

  ```json
Binding: {Table: Customers}
  Phrasings:
    - Attribute: {Subject: customer, Object: customer.name}
    - Name:
        Subject: customer
        Object: customer.name
```

Outro exemplo seria adicionar a frase alternativa "os funcionários vendem produtos para clientes" à relação "os clientes compram produtos de funcionários". Observe que não é necessário adicionar variações, como “funcionários vendem produtos *para clientes*” ou “produtos são vendidos para clientes *pelos funcionários*”, pois as variações “pelos” e “para” do sujeito e do objeto indireto são inferidas automaticamente pela P e R.

## <a name="considerations-and-troubleshooting"></a>Considerações e solução de problemas
Se você fizer uma alteração em um arquivo .lsdl.yaml que não esteja em conformidade com o formato do esquema linguístico, agora você verá rabiscos de validação para indicar problemas: 

![arquivo yaml mostrando os erros](media/q-and-a-tooling-advanced/power-bi-yaml-errors.png)

Mais perguntas? [Experimente a Comunidade do Power BI](https://community.powerbi.com/)
