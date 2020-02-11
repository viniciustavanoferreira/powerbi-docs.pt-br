---
title: Publicar na Web por meio do Power BI
description: Com o recurso Publicar na Web do Power BI, você pode inserir facilmente visualizações interativas online do Power BI, como postagens no blog e sites, por meio de emails ou mídia social, em qualquer dispositivo.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 01/30/2020
LocalizationGroup: Share your work
ms.openlocfilehash: 53cc311f2fb0bfa4ab876c80b81ee2a092c4fd8c
ms.sourcegitcommit: 53c2b5ea4ee1fe2659804d5ccc8e4bb445a8bcad
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2020
ms.locfileid: "76913619"
---
# <a name="publish-to-web-from-power-bi"></a>Publicar na Web por meio do Power BI

Com a opção **Publicar na Web** do Power BI, é possível inserir facilmente visualizações interativas online do Power BI, como postagens no blog e sites, por email ou mídia social, em qualquer dispositivo. Também é possível editar, atualizar ou descompartilhar com facilidade os visuais publicados.

> [!WARNING]
> Quando você usa **Publicar na Web**, qualquer pessoa na Internet pode exibir seu relatório ou visual publicado. Isso não requer nenhuma autenticação e inclui a exibição de dados de nível de detalhes que seus relatórios agregam. Antes de publicar um relatório, verifique se não há problema em compartilhar os dados e as visualizações publicamente. Não publique informações confidenciais nem proprietárias. Em caso de dúvida, verifique as políticas de sua organização antes da publicação.

>[!Note]
>Para inserir seu conteúdo com segurança em um portal ou site interno, use as opções [Inserir](service-embed-secure.md) ou [Inserir no SharePoint Online](service-embed-report-spo.md). Isso garante que todas as permissões e segurança de dados sejam aplicadas quando seus usuários estiverem exibindo seus dados internos.

## <a name="how-to-use-publish-to-web"></a>Como usar o recurso Publicar na Web

**Publicar na Web** está disponível para relatórios que podem ser editados em seus workspaces pessoais e de grupo.  Ele não está disponível para relatórios compartilhados com você ou para aqueles que dependem de segurança em nível de linha para proteger os dados. Confira a seção [**Limitações**](#limitations) abaixo para ver uma lista completa de casos em que o recurso **Publicar na Web** não é compatível. Leia o **Aviso** indicado anteriormente neste artigo antes de usar o recurso **Publicar na Web**.

O breve vídeo a seguir mostra como esse recurso funciona. Em seguida, experimente você mesmo nas etapas abaixo.

<iframe width="560" height="315" src="https://www.youtube.com/embed/UF9QtqE7s4Y" frameborder="0" allowfullscreen></iframe>

As etapas a seguir descrevem como usar o recurso **Publicar na Web**.

1. Abra um relatório em seu workspace que você pode editar e selecione **Arquivo > Publicar na Web**.

   ![PtW1](media/service-publish-to-web/publish_to_web1.png)
   
2. Se você não tem permissão para criar códigos de inserção, entre em contato com o administrador do Power BI

   ![PtW1](media/service-publish-to-web/publish_to_web_admin_prompt.png)

3. Examine o conteúdo da caixa de diálogo e selecione **Criar um código de inserção**.

   ![PtW2](media/service-publish-to-web/publish_to_web2_ga.png)

4. Leia o aviso, conforme mostrado aqui, e confirme se os dados estão corretos para ser inseridos em um site público. Em caso afirmativo, selecione **Publicar**.

   ![PtW3](media/service-publish-to-web/publish_to_web3_ga.png)

5. Uma caixa de diálogo é exibida com um link. É possível enviar este link em um email, inseri-lo em código como um iFrame ou colá-lo diretamente em uma página da Web ou em um blog.

   ![PtW4](media/service-publish-to-web/publish_to_web4.png)

6. Se anteriormente você tiver criado um código de inserção para um relatório e selecionar o recurso **Publicar na Web**, você não verá as caixas de diálogo nas etapas 2 a 4. Em vez disso, a caixa de diálogo **Código de inserção** será exibida:

   ![PtW5](media/service-publish-to-web/publish_to_web5.png)

   Você pode criar apenas um código de inserção para cada relatório.


## <a name="tips-and-tricks-for-view-modes"></a>Dicas e truques para modos de exibição

Quando você insere conteúdo em uma postagem no blog, normalmente é necessário ajustá-lo em um tamanho específico da tela.  É possível ajustar a altura e a largura na marca iFrame conforme necessário. No entanto, é necessário verificar se seu relatório se encaixa na área fornecida do iFrame; portanto, também é necessário definir um Modo de Exibição ao editar o relatório.

A tabela a seguir fornece diretrizes sobre o Modo de Exibição e como ele aparecerá quando for inserido.

| Modo de Exibição | Sua aparência quando inserido |
| --- | --- |
| ![PtW6b](media/service-publish-to-web/publish_to_web6b.png) |**Ajustar à página** respeita a altura e a largura da página de seu relatório. Se você definir sua página para proporções *dinâmicas* como 16:9 ou 4:3, seu conteúdo será ajustado para caber no iFrame. Quando inserido em um iFrame, o uso de **Ajustar à página** pode resultar na *aplicação do formato letterbox*, no qual uma tela de fundo cinza é mostrada nas áreas do iFrame depois que o conteúdo é ajustado para caber no iFrame. Para minimizar a aplicação do formato letterbox, defina a altura e a largura do iFrame de modo condizente. |
| ![PtW6d](media/service-publish-to-web/publish_to_web6d.png) |**Tamanho real** verifica se o relatório preserva seu tamanho, conforme definido na página do relatório. Isso pode resultar na exibição de barras de rolagem no iFrame. Defina a altura e a largura do iFrame para evitar barras de rolagem. |
| ![PtW6c](media/service-publish-to-web/publish_to_web6c.png) |**Ajustar à largura** verifica se o conteúdo se ajusta à área horizontal do iFrame. Uma borda ainda será mostrada, mas o conteúdo será dimensionado para usar todo o espaço horizontal disponível. |

## <a name="tips-and-tricks-for-iframe-height-and-width"></a>Dicas e truques para a altura e largura do iFrame

Um código de inserção da configuração **Publicar na Web** será parecido com o exemplo a seguir:

![PtW7](media/service-publish-to-web/publish_to_web7.png)
 
É possível editar a largura e a altura manualmente para verificar se o código se ajusta exatamente da forma como você deseja na página em que é inserido.

Para obter um ajuste mais perfeito, tente adicionar 56 pixels à altura do iFrame para acomodar o tamanho atual da barra inferior. Se sua página de relatório usar o tamanho dinâmico, a tabela abaixo fornecerá alguns tamanhos que podem ser usados para obter um ajuste sem a aplicação do formato letterbox.

| Taxa | Tamanho | Dimensões (Largura x Altura) |
| --- | --- | --- |
| 16:9 |Pequeno |640 x 416 px |
| 16:9 |Médio |800 x 506 px |
| 16:9 |Grande |960 x 596 px |
| 4:3 |Pequeno |640 x 536 px |
| 4:3 |Médio |800 x 656 px |
| 4:3 |Grande |960 x 776 px |

## <a name="manage-embed-codes"></a>Gerenciar códigos de inserção

Após criar um código de inserção no recurso **Publicar na Web**, será possível gerenciar seus códigos no menu **Configurações** no Power BI. O gerenciamento de códigos de inserção inclui a capacidade de remover o visual ou o relatório de destino de um código (tornando o código de inserção inutilizável) ou de obter o código de inserção.

1. Para gerenciar seus códigos de inserção de **Publicar na Web** , abra a engrenagem **Configurações** e selecione **Gerenciar códigos de inserção**.

   ![PtW8](media/service-publish-to-web/publish_to_web8.png)

2. Seus códigos de inserção são exibidos.

   ![PtW9](media/service-publish-to-web/publish_to_web9.png)

3. É possível recuperar ou excluir um código de inserção. Excluí-lo desabilita qualquer link para esse relatório ou visual.

   ![PtW10](media/service-publish-to-web/publish_to_web10.png)

4. Se você selecionar **Excluir**, deverá confirmar.

   ![PtW11](media/service-publish-to-web/publish_to_web11.png)

## <a name="updates-to-reports-and-data-refresh"></a>Atualizações em relatórios e atualização de dados

Depois de criar seu código de inserção no recurso **Publicar na Web** e compartilhá-lo, o relatório será atualizado com todas as alterações feitas, e o link do código de inserção ficará ativo imediatamente. Qualquer pessoa que abrir o link poderá vê-lo. Após essa ação inicial, contudo, as atualizações em relatórios ou visuais poderão levar aproximadamente uma hora até se tornarem visíveis para seus usuários. Para saber mais, confira a seção [**Como isso funciona**](#howitworks) posteriormente neste artigo. 

## <a name="data-refresh"></a>Atualização de dados

As atualizações de dados são refletidas automaticamente no relatório ou visual inserido. Pode levar aproximadamente uma hora para que os dados atualizados estejam visíveis nos códigos de inserção. Para desabilitar a atualização automática, selecione **não atualizar** no agendamento do conjunto de dados que o relatório usa.  

## <a name="custom-visuals"></a>Visuais personalizados

Há suporte para visuais personalizados no recurso **Publicar na Web**. Quando você usa o recurso **Publicar na Web**, os usuários com os quais você compartilha seu visual publicado não precisam habilitar visuais personalizados para exibir o relatório.

## <a name="limitations"></a>Limitações

O recurso **Publicar na Web** é compatível com a maioria das fontes de dados e relatórios no serviço do Power BI; no entanto, veja abaixo o que não é compatível ou o que não está disponível atualmente com **Publicar na Web**:

- Relatórios que usam a segurança em nível de linha.
- Relatórios que usam qualquer fonte de dados de Conexão Dinâmica, incluindo Tabulares do Analysis Services hospedados localmente no Analysis Service Multidimensional e o Azure Analysis Services.
- Relatórios compartilhados com você diretamente ou por meio de um pacote de conteúdo organizacional.
- Relatórios em um grupo no qual você não é um membro de edição.
- No momento, os visuais do “R” em relatórios do recurso **Publicar na Web** não são compatíveis.
- Exportar dados de visuais em um relatório, que foi publicado na Web.
- Visuais do ArcGIS Maps for Power BI.
- Relatórios que contêm medidas DAX no nível do relatório.
- Modelos de consulta de dados de logon único.
- Informações confidenciais ou proprietárias.
- [Conjuntos de dados compartilhados e certificados](service-datasets-share.md).
- O recurso de autenticação automática fornecido com a opção **Inserir** não funciona com a API JavaScript do Power BI. Para a API JavaScript do Power BI, use a abordagem [o usuário possui dados](developer/embed-sample-for-your-organization.md) para inserção.

## <a name="tenant-setting"></a>Configuração de locatário

A configuração **Publicar na Web** fornece opções com as quais os usuários podem criar códigos de inserção.

![Configuração Publicar na Web](media/service-admin-portal/powerbi-admin-publish-to-web-setting.png)

Você precisará entrar em contato com um administrador do Power BI para criar códigos de inserção se a opção **Escolher como os códigos de inserção funcionam** estiver definida como **Permitir somente códigos de inserção existentes** e a configuração **Publicar na Web** estiver **Habilitada**.

![Solicitação Publicar na Web](media/service-publish-to-web/publish_to_web_admin_prompt.png)

Os administradores do Power BI podem habilitar ou desabilitar o recurso **Publicar na Web**. Eles também podem restringir o acesso a grupos específicos, que podem afetar sua capacidade de criar um código de inserção. Dependendo do local onde se encontra a configuração **Publicar na Web**, você verá diferentes opções na interface do usuário.

|Recurso |Habilitado para toda a organização |Desabilitado para toda a organização |Grupos de segurança específicos   |
|---------|---------|---------|---------|
|**Publicar na Web** no menu **Arquivo** do relatório|Habilitado para todos|Não visível para todos|Visível somente para usuários ou grupos autorizados.|
|**Gerenciar códigos de inserção** em **Configurações**|Habilitado para todos|Habilitado para todos|Habilitado para todos.<br><br>Opção * **Excluir** somente para usuários ou grupos autorizados.<br>* **Obter códigos** habilitados para todos.|
|**Códigos de inserção** no portal de administração|O status refletirá um dos seguintes estados:<br>* Ativo<br>* Sem suporte<br>* Bloqueado|O status exibirá **Desabilitado**|O status refletirá um dos seguintes estados:<br>* Ativo<br>* Sem suporte<br>* Bloqueado<br><br>Se um usuário não estiver autorizado conforme a configuração do locatário, o status exibirá **violado**.|
|Relatórios publicados existentes|Tudo habilitado|Tudo desabilitado|Os relatórios continuam a ser renderizados para todos.|

## <a name="understanding-the-embed-code-status-column"></a>Noções básicas sobre a coluna de status do código de inserção

>[!Note]
>Você deve revisar regularmente os códigos de inserção publicados e remover os que não precisam mais estar disponíveis publicamente. 

A página **Gerenciar códigos de inserção** inclui uma coluna de status. Por padrão, os códigos de inserção estão **Ativos**, mas também podem ter um dos status listados abaixo.

| Status | Descrição |
| --- | --- |
| **Ativo** |O relatório está disponível para que os usuários da Internet o vejam e interajam com ele. |
| **Bloqueado** |O conteúdo do relatório viola os [Termos de Serviço do Power BI](https://powerbi.microsoft.com/terms-of-service). A Microsoft o bloqueou. Entre em contato com o suporte se acreditar que o conteúdo foi bloqueado por engano. |
| **Sem suporte** |O conjunto de dados do relatório está usando a segurança em nível de linha ou outra configuração sem suporte. Confira a seção [**Limitações**](#limitations) para ver uma lista completa. |
| **Violado** |O código de inserção está fora da política de locatário definida. Normalmente, isso ocorre quando um código de inserção era criado e a configuração de locatário do recurso **Publicar na Web** era alterada para excluir o usuário que tem o código de inserção. Se a configuração do locatário estiver desabilitada ou o usuário não tiver mais permissão para criar códigos de inserção, os códigos de inserção existentes mostrarão um status **Violado**. |

## <a name="how-to-report-a-concern-with-publish-to-web-content"></a>Como relatar um problema com o conteúdo de Publicar na Web

Para relatar um problema relacionado ao conteúdo do recurso **Publicar na Web** inserido em um site ou blog, use o ícone **Sinalizador** na barra inferior, conforme mostrado na imagem a seguir. Você deverá enviar um email à Microsoft explicando sua preocupação. A Microsoft avaliará o conteúdo com base nos Termos de Serviço do Power BI e tomará as devidas providências.

Para relatar um problema, selecione o ícone **sinalizador** na barra inferior do relatório de **Publicar na Web** exibido.

![PtW12](media/service-publish-to-web/publish_to_web12_ga.png)

## <a name="licensing-and-pricing"></a>Licenciamento e preços

Você precisa ser um usuário do Microsoft Power BI para usar o recurso **Publicar na Web**. Os visualizadores do seu relatório não precisam ser usuários do Power BI.

<a name="howitworks"></a>
## <a name="how-it-works-technical-details"></a>Como isso funciona (detalhes técnicos)

Quando você cria um código de inserção usando **Publicar na Web**, o relatório fica visível para os usuários da Internet. Está disponível publicamente e, portanto, você pode esperar que as pessoas que verão seu relatório o compartilhem com facilidade por meio da mídia social no futuro. Conforme os usuários exibem o relatório, abrindo a URL pública direta ou exibindo-o inserido em uma página da Web ou em um blog, o Power BI armazena em cache a definição do relatório e os resultados das consultas necessárias para exibi-lo. Com isso, milhares de usuários simultâneos podem exibir o relatório sem afetar o desempenho.

O cache é duradouro; portanto, se você atualizar a definição do relatório (por exemplo, alterar seu Modo de exibição) ou atualizar os dados do relatório, poderá levar aproximadamente uma hora até que as alterações sejam refletidas na versão do relatório que seus usuários veem. Portanto, é recomendável que você teste seu trabalho antecipadamente e crie o código de inserção de **Publicar na Web** somente quando estiver satisfeito com as configurações.

## <a name="next-steps"></a>Próximas etapas

- [Web part do relatório do SharePoint Online](service-embed-report-spo.md) 

- [Inserir o relatório em um site ou portal seguro](service-embed-secure.md)

Mais perguntas? [Experimente a Comunidade do Power BI](https://community.powerbi.com/)
