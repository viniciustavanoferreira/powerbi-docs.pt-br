---
ms.openlocfilehash: 6e48713315b23cf322b635f1650374251b639e4f
ms.sourcegitcommit: bbd9b38f30a4ca5cb8072496c9cacb635b03aa88
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71409346"
---
## <a name="define-roles-and-rules-in-power-bi-desktop"></a>Definir funções e regras no Power BI Desktop
É possível definir funções e regras no Power BI Desktop. Quando você publica no Power BI, ele também publica as definições de função.

Para definir funções de segurança, siga estas etapas.

1. Importe os dados para o relatório do Power BI Desktop ou configure uma conexão do DirectQuery.
   
   > [!NOTE]
   > Você não pode definir funções no Power BI Desktop BI para as conexões dinâmicas do Analysis Services. Você precisa fazer isso no modelo do Analysis Services.
   > 
   > 
1. Selecione a guia **Modelagem**.
2. Selecione **Gerenciar Funções**.
   
   ![](./media/rls-desktop-define-roles/powerbi-desktop-security.png)
4. Selecione **Criar**.
   
   ![](./media/rls-desktop-define-roles/powerbi-desktop-security-create-role.png)
5. Forneça um nome para a função. 
6. Selecione a tabela à qual você deseja aplicar uma regra DAX.
7. Insira as expressões DAX. Essa expressão deve retornar true ou false. Por exemplo: [ID da Entidade] = “Valor”.
   
   > [!NOTE]
   > Você pode usar o *username()* nesta expressão. Lembre-se de que *username()* terá o formato *DOMÍNIO\nomedeusuário* no Power BI Desktop. Dentro do serviço do Power BI e do Servidor de Relatórios do Power BI, ele está no formato do nome UPN do usuário. Como alternativa, você pode usar *userprincipalname()* , que sempre retorna o usuário no formato de seu nome UPN, *nome de usuário\@contoso.com*.
   > 
   > 
   
   ![](./media/rls-desktop-define-roles/powerbi-desktop-security-create-rule.png)
8. Depois de criar a expressão DAX, você pode selecionar a seleção acima da caixa de expressão para validar a expressão.
      
   ![](./media/rls-desktop-define-roles/powerbi-desktop-security-validate-dax.png)
   
   > [!NOTE]
   > Nessa caixa de expressão, use vírgulas para separar argumentos da função DAX, mesmo que esteja usando uma localidade que normalmente usa separadores de ponto e vírgula (por exemplo, francês ou alemão). 
   >
   >
   
9. Selecione **Salvar**.

Não é possível atribuir usuários a uma função no Power BI Desktop. Você pode atribuí-los no serviço do Power BI. É possível habilitar a segurança dinâmica no Power BI Desktop fazendo uso das funções DAX *username()* ou *userprincipalname()* e configurando as relações corretas. 

