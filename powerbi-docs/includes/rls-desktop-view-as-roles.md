---
ms.openlocfilehash: 8dc488a47ac2b5b4e7980b7404b2722b1120b6ab
ms.sourcegitcommit: cde65bb8b1bed1ee8cf512651afeb829ddc155de
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77464314"
---
## <a name="validate-the-roles-within-power-bi-desktop"></a>Validar as funções dentro do Power BI Desktop
Depois de criar sua função, você poderá testar os resultados da função no Power BI Desktop.

1. Na guia **Modelagem**, selecione **Exibir como Funções**. 

    ![Selecione Exibir como Funções](./media/rls-desktop-view-as-roles/powerbi-desktop-rls-view-as-roles.png)

    É exibida a janela **Exibir como funções**, na qual você pode ver as funções que criou.

    ![Janela Exibir como funções](./media/rls-desktop-view-as-roles/powerbi-desktop-rls-view-as-roles-dialog.png)

3. Selecione a função criada e selecione **OK** para aplicá-la. 

   Os relatórios renderizam somente os dados relevantes para essa função.

4. Você também pode selecionar **Outro usuário** e fornecer um determinado usuário. 

    ![Selecione Outro usuário](./media/rls-desktop-view-as-roles/powerbi-desktop-rls-other-user.png)

   É melhor fornecer o nome UPN, é ele que será usado pelo serviço do Power BI e pelo Servidor de Relatórios do Power BI.

   No Power BI Desktop, a opção **Outro usuário** exibirá resultados diferentes somente se você estiver usando a segurança dinâmica com base nas expressões DAX. 

5. Selecione **OK**. 

   O relatório será renderizado com base no que esse usuário pode ver.



