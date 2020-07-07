---
title: Saiba quais pacotes do Python têm suporte
description: Pacotes do Python com suporte e sem suporte no Power BI
author: otarb
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/26/2020
ms.author: otarb
LocalizationGroup: Connect to data
ms.openlocfilehash: b1dc77d2ebf0803430ceeace7e14bfa62a6d2a60
ms.sourcegitcommit: e8b12d97076c1387088841c3404eb7478be9155c
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85785174"
---
# <a name="create-visuals-by-using-python-packages-in-the-power-bi-service"></a>Criar visuais usando pacotes do Python no serviço do Power BI
Você pode usar a [linguagem de programação Python](https://www.python.org/) avançada para criar visuais no serviço do Power BI. Muitos pacotes do Python têm suporte no serviço do Power BI, e mais pacotes têm suporte o tempo todo.

As seções a seguir fornecem uma tabela alfabética de quais pacotes do Python têm suporte no Power BI. 

## <a name="request-support-for-a-new-python-package"></a>Solicitar suporte para um novo pacote do Python
Os pacotes do Python com suporte no **serviço do Power BI** são encontrados na seção a seguir, intitulada **Pacotes com suporte**. Se você quiser solicitar o suporte de um pacote do Python não encontrado na lista, envie sua solicitação para [Ideias do Power BI](https://ideas.powerbi.com).

## <a name="requirements-and-limitations-of-python-packages"></a>Requisitos e limitações para pacotes do Python
Há alguns requisitos e limitações para pacotes do Python:

* Runtime atual do Python: Python 3.7.7.
* O serviço do Power BI, em sua grande parte, dá suporte a pacotes do Python com licenças de software gratuitas e de software livre, como GPL-2, GPL-3, MIT+ e assim por diante.
* O serviço do Power BI dá suporte a pacotes publicados no PyPI. O serviço não dá suporte a pacotes do Python personalizados ou privados. Recomendamos que os usuários disponibilizem seus pacotes privados no PyPI antes de solicitar que o pacote fique disponível no serviço do Power BI.
* Em visuais do Python no **Power BI Desktop**, você pode instalar qualquer pacote, incluindo pacotes do Python personalizados.
* Por motivos de privacidade e segurança, os pacotes do Python que fornecem consultas de cliente-servidor por meio da World Wide Web no serviço não são compatíveis. A rede está bloqueada para essas tentativas.
* O processo de aprovação para a inclusão de um novo pacote do Python tem uma árvore de dependências; algumas delas que precisam ser instaladas no serviço não têm suporte.

## <a name="python-packages-that-are-supported-in-power-bi"></a>Pacotes do Python com suporte no Power BI
A tabela a seguir mostra quais pacotes **têm suporte** no serviço do Power BI.


|        Pacote        |   Versão   |                                   Link                                   |
|-----------------------|-------------|--------------------------------------------------------------------------|
|matplotlib|3.2.1|https://pypi.org/project/matplotlib|
|numpy|1.18.4|https://pypi.org/project/numpy|
|pandas|1.0.1|https://pypi.org/project/pandas|
|scikit-learn|0.23.0|https://pypi.org/project/scikit-learn|
|scipy|1.4.1|https://pypi.org/project/scipy|
|s  eaborn|0.10.1|https://pypi.org/project/seaborn|
|statsmodels|0.11.1|https://pypi.org/project/statsmodels|
|xgboost|1.1.0|https://pypi.org/project/xgboost|

## <a name="next-steps"></a>Próximas etapas
Para saber mais sobre o Python no Power BI, confira os seguintes artigos:

* [Criar visuais do Power BI usando Python](desktop-python-visuals.md)
* [Executar scripts do Python no Power BI Desktop](desktop-python-scripts.md)
* [Usar o Python no Editor de Consultas](desktop-python-in-query-editor.md)
