---
title: Always Encrypted em Servidor de Relatórios do Power BI
description: Este artigo detalha o suporte para Always Encrypted no Servidor de Relatórios do Power BI ao usar os tipos de fonte de dados Microsoft SQL Server e Banco de Dados SQL do Microsoft Azure.
author: maggiesMSFT
ms.reviewer: cfinlan
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 01/22/2020
ms.author: maggies
ms.openlocfilehash: f8d711bba8dc7570f2d470554fd1d971639bbb7b
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/05/2020
ms.locfileid: "76710196"
---
# <a name="always-encrypted-in-power-bi-report-server"></a>Always Encrypted em Servidor de Relatórios do Power BI

Este artigo detalha o suporte para Always Encrypted no Servidor de Relatórios do Power BI ao usar os tipos de fonte de dados Microsoft SQL Server e Banco de Dados SQL do Microsoft Azure. Para obter mais informações sobre os recursos Always Encrypted no SQL Server, leia o artigo [Always Encrypted](https://docs.microsoft.com/sql/relational-databases/security/encryption/always-encrypted-database-engine).

## <a name="always-encrypted-user-isolation"></a>Isolamento de usuário Always Encrypted

Neste momento, o Servidor de Relatórios do Power BI não restringirá o acesso a colunas Always Encrypted em relatórios se um usuário tiver acesso ao relatório.  Portanto, se o servidor tiver recebido acesso às chaves de criptografia de coluna por meio da chave mestra de coluna, os usuários terão acesso a todas as colunas para os relatórios que eles podem acessar.

## <a name="always-encrypted-column-usage"></a>Uso de coluna Always Encrypted

### <a name="key-storage-strategies"></a>Estratégias de armazenamento de chaves

|Armazenamento  |Com suporte  |
|---------|---------|
|Repositório de Certificados do Windows | Sim |
|Azure Key Vault | Não |
| CNG (Cryptography Next Generation) | Não |

### <a name="certificate-storage-and-access"></a>Armazenamento e acesso de certificado

A conta que requer acesso ao certificado é a conta de serviço. O certificado deve ser armazenado no repositório de certificados do computador local. Para obter mais informações, veja:

- [Configurar a conta de serviço do servidor de relatório](https://docs.microsoft.com/sql/reporting-services/install-windows/configure-the-report-server-service-account-ssrs-configuration-manager) (Configuration Manager)
- Seção [Como disponibilizar certificados para aplicativos e usuários](https://docs.microsoft.com/sql/relational-databases/security/encryption/create-and-store-column-master-keys-always-encrypted#making-certificates-available-to-applications-and-users) no artigo do SQL Server "Criar e armazenar chaves mestras de coluna para Always Encrypted".

### <a name="column-encryption-strategy"></a>Estratégia de criptografia de coluna

No Servidor de Relatórios do Power BI, a estratégia de criptografia de coluna pode ser *determinística* ou *aleatória*. A tabela a seguir explica as diferenças, dependendo de qual estratégia ela usa.

|Use  |Determinística  |Aleatória  |
|---------|---------|---------|
|Pode ser lido no estado em que se encontra nos resultados de uma consulta, por exemplo, instruções SELECT. | Sim  | Sim  |
|Pode ser usado como uma entidade Agrupar por dentro da consulta. | Sim | Não |
|Pode ser usado como um campo de agregação, com exceção de COUNT e DISTINCT. | Não, exceto por COUNT e DISTINCT | Não |
|Pode ser usado como um parâmetro de relatório | Sim | Não |

Leia mais sobre [criptografia determinística vs. aleatória](https://docs.microsoft.com/sql/relational-databases/security/encryption/always-encrypted-database-engine#selecting--deterministic-or-randomized-encryption).

### <a name="parameter-usage"></a>Uso de parâmetro

O uso do parâmetro aplica-se somente à criptografia determinística.

**Parâmetro de valor único**.  Você pode usar um parâmetro de valor único em uma coluna Always Encrypted.

**Parâmetro de diversos valores**. Você não pode usar um parâmetro de diversos valores com mais de um valor em uma coluna Always Encrypted.

**Parâmetros em cascata**. Você poderá usar parâmetros em cascata com Always Encrypted se *todos* os itens seguintes forem verdadeiros:

- Todas as colunas de Always Encrypted devem ser Always Encrypted com estratégia determinística.
- Todos os parâmetros usados em relação às colunas Always Encrypted são parâmetros de valor único.
- Todas as comparações SQL usam o operador Equals (=).

## <a name="datatype-support"></a>Suporte a tipo de dados

| Tipo de dados SQL | Compatível com campo de leitura | Compatível com o uso como um elemento Agrupar por | Agregações compatíveis (COUNT, DISTINCT, MAX, MIN, SUM etc.) | Compatível com filtragem por meio de igualdade usando parâmetros | Anotações |
| --- | --- | --- | --- | --- | --- |
| int | Sim | Sim | COUNT, DISTINCT | Sim, como Inteiro |   |
| FLOAT | Sim | Sim | COUNT, DISTINCT | Sim, como Float |   |
| NVARCHAR | Sim | Sim | COUNT, DISTINCT | Sim, como Texto | A criptografia determinística deve usar uma ordenação de colunas com uma ordem de classificação binary2 para as colunas de caracteres. Leia o artigo [Always Encrypted](https://docs.microsoft.com/sql/relational-databases/security/encryption/always-encrypted-database-engine#selecting--deterministic-or-randomized-encryption) do SQL Server para obter detalhes.  |
| varchar | Sim | Sim | COUNT, DISTINCT | Não |   |
| decimal | Sim | Sim | COUNT, DISTINCT | Não |   |
| numeric | Sim | Sim | COUNT, DISTINCT | Não |   |
| datetime | Sim | Sim | COUNT, DISTINCT | Não |   |
| datetime2 | Sim | Sim | COUNT, DISTINCT | Sim, como Data/Hora | Compatível se a coluna não tiver nenhuma precisão de milissegundo (em outras palavras, nenhum datetime2(0)) |

## <a name="aggregation-alternatives"></a>Alternativas de agregação

No momento, as únicas agregações compatíveis em colunas determinísticas Always Encrypted são as agregações que usam diretamente o operador Equals (=). Essa limitação do SQL Server se deve à natureza de colunas Always Encrypted. Os usuários devem agregar no relatório, em vez de no banco de dados.

## <a name="always-encrypted-in-connection-strings"></a>Always Encrypted em cadeias de conexão

Você precisa habilitar Always Encrypted na cadeia de conexão para uma fonte de dados do SQL Server. Leia mais sobre como habilitar [Always Encrypted em consultas de aplicativo](https://docs.microsoft.com/sql/relational-databases/security/encryption/develop-using-always-encrypted-with-net-framework-data-provider#enabling-always-encrypted-for-application-queries).

## <a name="next-steps"></a>Próximas etapas

[Always Encrypted](https://docs.microsoft.com/sql/relational-databases/security/encryption/always-encrypted-database-engine) no SQL Server e no Banco de Dados SQL do Azure

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)

