---
ms.openlocfilehash: 27d6db6cf8ad8ebd7b2c957954ceec34b83681d0
ms.sourcegitcommit: cde65bb8b1bed1ee8cf512651afeb829ddc155de
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77464317"
---
## <a name="define-roles-and-rules-in-power-bi-desktop"></a>Definir funções e regras no Power BI Desktop
É possível definir funções e regras no Power BI Desktop. Quando você publica no Power BI, ele também publica as definições de função.

Para definir funções de segurança, siga estas etapas.

1. Importe os dados para o relatório do Power BI Desktop ou configure uma conexão do DirectQuery.
   
   > [!NOTE]
   > Você não pode definir funções no Power BI Desktop BI para as conexões dinâmicas do Analysis Services. Você precisa fazer isso no modelo do Analysis Services.
   > 
   > 
2. Na guia **Modelagem**, selecione **Gerenciar Funções**.
   
   ![Selecione Gerenciar Funções](./media/rls-desktop-define-roles/powerbi-desktop-security.png)
3. Na janela **Gerenciar funções**, selecione **Criar**.
   
   ![Selecione Criar](./media/rls-desktop-define-roles/powerbi-desktop-security-create-role.png)
4. Em **Funções**, forneça um nome para a função. 
5. Em **Tabelas**, selecione a tabela à qual deseja aplicar uma regra DAX.
6. Na caixa **Expressão DAX da tabela de filtro**, insira as expressões DAX. Essa expressão retorna um valor de verdadeiro ou falso. Por exemplo: ```[Entity ID] = “Value”```.
      
   ![Janela Gerenciar funções](./media/rls-desktop-define-roles/powerbi-desktop-security-create-rule.png)

   > [!NOTE]
   > Você pode usar o *username()* nesta expressão. Lembre-se de que *username()* terá o formato *DOMÍNIO\nomedeusuário* no Power BI Desktop. Dentro do serviço do Power BI e do Servidor de Relatórios do Power BI, ele está no formato do nome UPN do usuário. Como alternativa, você pode usar *userprincipalname()* , que sempre retorna o usuário no formato de seu nome UPN, *nome de usuário\@contoso.com*.
   > 
   > 

7. Depois de criar a expressão DAX, selecione a marca de seleção acima da caixa de expressão para validar a expressão.
      
   ![Validar expressão DAX](./media/rls-desktop-define-roles/powerbi-desktop-security-validate-dax.png)
   
   > [!NOTE]
   > Nessa caixa de expressão, use vírgulas para separar argumentos da função DAX, mesmo que esteja usando uma localidade que normalmente usa separadores de ponto e vírgula (por exemplo, francês ou alemão). 
   >
   >
   
8. Selecione **Salvar**.

Não é possível atribuir usuários a uma função no Power BI Desktop. Você pode atribuí-los no serviço do Power BI. É possível habilitar a segurança dinâmica no Power BI Desktop fazendo uso das funções DAX *username()* ou *userprincipalname()* e configurando as relações corretas. 

