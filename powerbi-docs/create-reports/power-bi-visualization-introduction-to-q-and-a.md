---
title: Criar um visual com P e R do Power BI
description: Aprenda a criar um visual com P e R no serviço do Power BI usando o exemplo de Análise de Varejo
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 05/13/2019
ms.author: maggies
LocalizationGroup: Ask questions of your data
ms.openlocfilehash: 6bd68f5db12367e6c98b6fe61461b89047d8eb56
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85237242"
---
# <a name="create-a-visual-with-power-bi-qa"></a>Criar um visual com P e R do Power BI

Às vezes, a maneira mais rápida de obter uma resposta de seus dados é fazer uma pergunta usando o idioma natural.  Neste artigo, examinamos duas maneiras diferentes de criar a mesma visualização: primeiro, fazendo uma pergunta com P e R e, segundo, criando essa funcionalidade em um relatório. Usamos o serviço do Power BI para criar o visual no relatório, mas o processo é quase idêntico ao uso do Power BI Desktop.

![Gráfico preenchido pelo Power BI](media/power-bi-visualization-introduction-to-q-and-a/power-bi-qna-create-visual.png)

Para acompanhar, você deve usar um relatório que você possa editar, então usaremos um dos exemplos disponíveis com o Power BI.

## <a name="create-a-visual-with-qa"></a>Criar um visual com P e R

Como poderíamos criar esse gráfico de linha usando P e R?

1. Em seu workspace do Power BI, selecione **Obter Dados** \> **Exemplos** \> **Exemplo de Análise de Varejo** > **Conectar**.

1. Abra o dashboard Exemplo de Análise de Varejo e coloque o cursor na caixa de P e R, **Faça uma pergunta sobre seus dados**.

    ![Coloque o cursor na caixa de P e R](media/power-bi-visualization-introduction-to-q-and-a/power-bi-qna-cursor-in-qna-box.png)

2. Na caixa de P e R, digite algo como esta pergunta:
   
    **vendas deste ano e do ano passado por mês como gráfico de área**
   
    Ao digitar uma pergunta, o P e R do Power BI escolhe a melhor visualização para exibir sua resposta, e a visualização muda dinamicamente, na medida em que você modifica a pergunta. Além disso, P e R e ajuda a formatar sua pergunta com sugestões, preenchimento automático e a correção ortográfica. P e R recomenda uma pequena alteração na redação: "vendas deste ano e do ano passado por *mês temporal* como gráfico de área".  

    ![P e R corrigiu a redação](media/power-bi-visualization-introduction-to-q-and-a/power-bi-qna-corrected-create-filled-chart.png)

4. Selecione a frase para aceitar a sugestão. 
   
   Quando terminar de digitar sua pergunta, o resultado será o mesmo gráfico que você vê no dashboard.
   
   ![Gráfico de área preenchido por P e R](media/power-bi-visualization-introduction-to-q-and-a/power-bi-qna-create-filled-chart.png)

4. Para fixar o gráfico no dashboard, selecione o ícone de marcador ![Ícone Fixar](media/power-bi-visualization-introduction-to-q-and-a/pinnooutline.png) no canto superior direito.

## <a name="create-a-visual-in-the-report-editor"></a>Criar um visual no editor de relatório

1. Navegue de volta para o dashboard de exemplo Análise de Varejo.
   
2. O dashboard contém o mesmo bloco de gráfico de área para "Vendas do ano passado e vendas deste ano”.  Selecione este bloco. Não selecione o bloco que você criou com P e R. Selecioná-lo abre P e R. O bloco do gráfico de área original foi criado em um relatório para que ele fosse aberto na página que contém essa visualização.

    ![Dashboard de exemplo de Análise de Varejo](media/power-bi-visualization-introduction-to-q-and-a/power-bi-dashboard.png)

1. Abra o relatório no modo Exibir Edição selecionado **Editar Relatório**.  Se você não for proprietário de um relatório, não terá a opção de abri-lo na exibição de Edição.
   
    ![Botão Editar relatório](media/power-bi-visualization-introduction-to-q-and-a/power-bi-edit-report.png)
4. Selecione o gráfico de área e examinar as configurações do painel **Campos** .  O criador de relatório criou esse gráfico selecionando esses três valores (**Vendas do Ano Passado** e **Vendas Deste Ano > Valor** na tabela **Vendas** e **FiscalMonth** na tabela **Tempo**) e os organizando nas seções **Eixo** e **Valores**.
   
    ![Painel Visualizações](media/power-bi-visualization-introduction-to-q-and-a/gnatutorial_3-new.png)

    Você vê que eles acabaram tendo o mesmo visual. Criá-lo dessa maneira não foi muito complicado. Mas criá-lo com P e R foi muito mais fácil!

## <a name="next-steps"></a>Próximas etapas

- [Use P e R em dashboards e relatórios](power-bi-tutorial-q-and-a.md)  
- [P e R para consumidores](../consumer/end-user-q-and-a.md)
- [Faça seus dados funcionarem bem com P e R no Power BI](service-prepare-data-for-q-and-a.md)

Mais perguntas? [Experimente a Comunidade do Power BI](https://community.powerbi.com/)
