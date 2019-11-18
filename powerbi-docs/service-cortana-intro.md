---
title: Usar a Cortana para localizar e exibir relatórios e dashboards – Power BI
description: Use o Cortana com o Power BI para obter respostas de seus dados. Atualmente funciona com dashboards e relatórios.
author: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/29/2019
ms.author: maggies
LocalizationGroup: Ask questions of your data
ms.openlocfilehash: b0109798336797eee93f738f15af71c00f818bf8
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/09/2019
ms.locfileid: "73853671"
---
# <a name="find-and-view-your-power-bi-data-with-cortana-for-power-bi"></a>Localizar e exibir seus dados do Power BI com a Cortana para o Power BI
Use a Cortana em seus dispositivos Windows 10 para obter respostas instantâneas para suas perguntas de negócios importantes. Ao se integrar ao Power BI, a Cortana pode recuperar informações importantes diretamente dos relatórios e dashboards do Power BI. Tudo o que você vai precisar é do Windows 10 com a versão de novembro de 2015 ou posterior, da Cortana, do Power BI e de acesso a, pelo menos, um conjunto de dados.

> [!IMPORTANT]
> A integração com a Cortana será preterida no Power BI. A partir de 11 de junho, a Cortana não será mais compatível com dashboards e relatórios.

![Campo de pesquisa da Cortana](media/service-cortana-intro/power-bi-cortana-searchbox.png)

## <a name="preview-the-new-cortana-dashboard-search-experience-for-windows-10"></a>Visualize a nova experiência de pesquisa do *dashboard* da Cortana para o Windows 10
Por um tempo, você conseguiu [usar a Cortana para recuperar determinados tipos de páginas de relatórios](service-cortana-answer-cards.md). Agora, adicionamos uma **nova experiência** – a capacidade de recuperar dashboards também. Experimente e [envie comentários por meio do Power BI Ideas](https://ideas.powerbi.com/forums/265200-power-bi). Eventualmente, a *nova experiência* será estendida para incluir a pesquisa de relatórios da Cortana também.  Um dos principais benefícios da nova experiência é que você não precisa fazer nada especial para configurá-la, não é preciso habilitar a Cortana ou configurar o Windows 10. Ela simplesmente funciona.

> [!NOTE]
> Se ela não “funcionar”, consulte o [Artigo de solução de problemas](service-cortana-troubleshoot.md) para obter ajuda.
> 
> 

A tecnologia subjacente está usando o [Serviço Microsoft Azure Search](https://docs.microsoft.com/azure/search/). Esse serviço de pesquisa fornece recursos adicionais como classificação inteligente, correção de erros e preenchimento automático.

Ambas as experiências da Cortana podem existir de modo paralelo.

## <a name="cortana-for-power-bi-documentation"></a>Documentação da Cortana para o Power BI
Quatro documentos orientam você por meio da configuração e do uso da Cortana para Power BI.

**Artigo 1** (este artigo): Compreender como a Cortana e o Power BI funcionam juntos

**Artigo 2**: [Pesquisar relatórios do Power BI: Habilitar a integração Cortana – Power BI – Windows](service-cortana-enable.md)

**Artigo 3**: [Pesquisar relatórios do Power BI: criar *cartões de respostas especiais da Cortana*](service-cortana-answer-cards.md)

**Artigo 4**: [solucionar problemas](service-cortana-troubleshoot.md)

## <a name="how-cortana-and-power-bi-work-together"></a>Como a Cortana e o Power BI funcionam juntos
Quando você usa a Cortana para fazer uma pergunta, o Power BI pode ser um dos locais em que a Cortana procura por respostas. No Power BI, a Cortana pode encontrar respostas orientadas a dados detalhados nos relatórios do Power BI (que contêm um tipo especial de página de relatório chamada *Cartão de respostas da Cortana*) e de dashboards do Power BI.

Se a Cortana encontrar uma correspondência, ela exibirá o nome da página do dashboard ou do relatório diretamente na tela da Cortana. A página do dashboard ou do relatório pode ser aberta no Power BI. As páginas do relatório também podem ser exploradas à direita na Cortana – elas são interativas.

![exibição da página de relatório interativa na Cortana](media/service-cortana-intro/power-bi-report-cortana-s.png)

### <a name="cortana-and-dashboards-the-new-experience"></a>Cortana e Dashboards (a *nova experiência*)
A Cortana pode encontrar respostas nos dashboards que você tem e nos dashboards que foram compartilhados com você. Faça perguntas à Cortana usando títulos, palavras-chave, nomes de proprietários, nomes de workspaces, nomes de aplicativos e muito mais.

Sua pergunta deve ter pelo menos duas palavras para que a Cortana encontre uma resposta. Portanto, se você pesquisar em um painel que tem um nome de uma palavra (Marketing), adicione a palavra "mostrar" ou "Power BI" ou o nome do proprietário à sua pergunta, como em "mostrar Marketing" e "exemplo de brenda fernandes". 

Se o título do dashboard tiver mais de uma palavra, a Cortana retornará esse dashboard apenas se a pesquisa corresponder a pelo menos duas das palavras ou a uma das palavras mais o nome do proprietário. Para um dashboard chamado “Exemplo de lucratividade do cliente”: 

* a expressão “mostrar cliente” *não* retorna um resultado do dashboard do Power BI.   
* expressões como “mostrar lucratividade do cliente”, ”cliente p”, “cliente s”, ”exemplo de lucratividade”, “exemplo de michele hart”, “mostrar exemplo de lucratividade do cliente” e “mostrar cliente p” *retornam* um resultado do Power BI.
* Adicionar a palavra "powerbi" conta como uma das duas palavras necessárias; portanto, a expressão "amostra do powerbi" *retorna* um resultado do Power BI. 
  
    ![Pesquisa da Cortana com pelo menos duas palavras](media/service-cortana-intro/power-bi-cortana-2-words.png)

### <a name="cortana-and-reports"></a>Cortana e Relatórios
 A Cortana pode encontrar respostas nos relatórios que têm [páginas criadas especificamente para exibição pela Cortana](service-cortana-answer-cards.md). Basta fazer perguntas usando o título ou palavras-chave de uma dessas páginas de relatórios de especialidade.  

A tecnologia subjacente para relatórios usa [P e R do Power BI](power-bi-tutorial-q-and-a.md).

Quando você faz uma pergunta na Cortana, o Power BI responde das páginas do relatório projetadas especificamente para a Cortana. As respostas possíveis são determinadas pela Cortana no mesmo instante, diretamente dos *cartões de resposta* da Cortana já criados no Power BI.  Para explorar mais uma resposta, abra um resultado no Power BI.

> [!NOTE]
> Antes que a Cortana consiga procurar respostas em seus relatórios do Power BI, você precisará [habilitar este recurso usando o serviço do Power BI e configurar o Windows para se comunicar com o Power BI](service-cortana-enable.md).  
> 
> 

## <a name="using-cortana-to-get-answers-from-power-bi"></a>Uso da Cortana para obter respostas do Power BI
1. Início na Cortana. Há várias maneiras diferentes de *abrir* a Cortana: selecione o ícone da Cortana na barra de tarefas (mostrada abaixo), use os comandos de voz ou toque no ícone de pesquisa em seu dispositivo móvel do Windows.
   
     ![](media/service-cortana-intro/power-bi-cortana-searchbox.png)
2. Depois que a Cortana estiver pronta, digite ou fale a sua pergunta na barra de pesquisa da Cortana. A Cortana exibe os resultados disponíveis. Se houver um dashboard do Power BI que corresponda à pergunta, ele aparecerá em **Melhor correspondência** ou em **Power BI**.
   
     ![A pesquisa da Cortana localiza o dashboard do Power BI](media/service-cortana-intro/power-bi-cortana-search-hr.png "A Cortana encontra um dashboard do Power BI")
   
   > [!NOTE]
   > No momento, há suporte apenas em inglês.
   > 
   > 
3. Selecione o painel para abri-lo na Cortana.

    ![Selecione o dashboard do Power BI](media/service-cortana-intro/power-bi-cortana-dashboard.png "Selecione o dashboard do Power BI")

    Você pode alterar o layout [editando a *exibição de telefone* do painel](service-create-dashboard-mobile-phone-view.md). 

1. Na Cortana, você também tem as opções de abrir o painel no serviço do Power BI ou Power BI móvel. Abra o painel no serviço do Power BI selecionando **Aberto na web**. 
   
   ![Abra o dashboard na Cortana](media/service-cortana-intro/power-bi-dashboard-opens.png "Abra o dashboard na Cortana")   
4. Agora vamos usar a Cortana para pesquisar um relatório. Precisaremos conhecer um [relatório que tenha uma página com um cartão de respostas da Cortana ](service-cortana-answer-cards.md). Neste exemplo, um relatório chamado “Cortana-New-Stores” tem uma página do cartão de respostas da Cortana chamada “cortana stores”.  
   
     Digite ou fale a sua pergunta na barra de pesquisa da Cortana. A Cortana exibe os resultados disponíveis. Se houver uma página de relatórios do Power BI que corresponda à pergunta, ela aparecerá em **Melhor correspondência** ou em **Power BI**. E neste exemplo, o arquivo .pbix (e o backup) usado para criar os cartões de respostas também é exibido em **Documentos**.
   
     ![Pesquisar um relatório](media/service-cortana-intro/power-bi-cortana-search3-m.png "pesquisar um relatório") 
5. Selecione a página de relatórios **Armazenamentos da Cortana** para exibi-la na janela da Cortana.
   
    ![A página de relatórios é aberta na Cortana](media/service-cortana-intro/power-bi-report-cortana-opens.png "A página de relatórios é aberta na Cortana")   
   
    Lembre-se, um *cartão de resposta* é um tipo especial de página de relatório do Power BI que foi criado por um proprietário de conjunto de dados.  Para obter mais informações, consulte [Create a Cortana answer card](service-cortana-answer-cards.md) (Criar um cartão de respostas da Cortana).
6. Mas, isso não é tudo. Interaja com as visualizações no cartão de respostas do mesmo modo que você faria no Power BI.
   
   * Por exemplo, selecione um elemento em uma visualização para filtrar e destacar as outras visualizações no cartão de resposta.
     
     ![](media/service-cortana-intro/power-bi-cortana-filtered-new.png)
   * Ou use uma linguagem natural para filtrar os resultados.  Por exemplo, pergunte “Armazenamentos da Cortana para a Lindseys” e veja o cartão filtrado para mostrar apenas os dados da cadeia da Lindseys.
     
     ![Filtro cruzado na Cortana](media/service-cortana-intro/power-bi-cortana-filtered-2.png "Filtro cruzado na Cortana")
7. Continue a explorar. Role até a parte inferior da janela da Cortana e selecione **Abrir no Power BI**.
   
     ![](media/service-cortana-intro/power-bi-cortana-open-new.png)
8. A página de relatórios é aberta no Power BI.    
     ![Abra o relatório na Cortana](media/service-cortana-intro/power-bi-cortana-open2.png "CoO cartão de resposta da Cortana é aberto na pesquisa da Cortana")

## <a name="considerations-and-troubleshooting"></a>Considerações e solução de problemas
* A Cortana não tem acesso a nenhum cartão da Cortana que não tenha sido [habilitado para o Power BI](service-cortana-enable.md).
* Ainda não consegue fazer com que a Cortana funcione com o Power BI?  Experimente a [solução de problemas da Cortana](service-cortana-troubleshoot.md).
* Atualmente, a Cortana para o Power BI está disponível apenas em inglês.
* A Cortana para o Power BI está disponível somente em dispositivos móveis do Windows.

Mais perguntas? [Experimente a Comunidade do Power BI](https://community.powerbi.com/).
Comentários? [Envie comentários ao Power BI Ideas](https://ideas.powerbi.com/forums/265200-power-bi).

## <a name="next-steps"></a>Próximas etapas
[Habilitar a integração Cortana – Power BI – Integração do Windows para relatórios](service-cortana-enable.md)

