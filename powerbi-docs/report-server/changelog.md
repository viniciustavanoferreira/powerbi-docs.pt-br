---
title: Log de alterações para o Servidor de Relatórios do Power BI
description: Esse log de alterações é para o Servidor de Relatório do Power BI e lista novos itens juntamente com correções de bug para cada build lançado.
ms.author: jaimeta
author: jtarquino
ms.reviewer: maggies
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 03/02/2020
ms.openlocfilehash: 0a8cf16ddf7fe9e091599f1790a37a83b9923240
ms.sourcegitcommit: d65da4738f011beec8f4423085cbd483511cdfb0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/03/2020
ms.locfileid: "78237950"
---
# <a name="change-log-for-power-bi-report-server"></a>Log de alterações para o Servidor de Relatórios do Power BI

Esse log de alterações é para o Servidor de Relatório do Power BI e lista novos itens juntamente com correções de bug para cada build lançado.

Para obter informações detalhadas sobre os novos recursos, consulte [Novidades no Servidor de Relatório do Power BI](whats-new.md). 


## <a name="january-2020"></a>Janeiro de 2020
- **Servidor de Relatório do Power BI**
    - *Versão: 1.6.7364.4075 (Build 15.0.1102.777), Lançamento: 2 de março de 2020*
         - Correções de bug
           -  Correção de relatórios do Power BI com falha ao carregar certas fontes de dados
           -  Correção do local de download de links da área de trabalho do Servidor de Relatórios do Power BI no portal
           -  Correção de DynamicImageDPI para renderização de Excel
           -  Correção de conexões do Oracle que usavam a cultura de thread incorreta em determinados cenários com vários usuários
           -  Correção do valor padrão de CustomHeaders que causava falhas na inserção de relatórios
           -  Correção dos nomes de parâmetro SQL que eram gerados incorretamente em alguns casos
    - *Versão: 1.6.7327.3007 (Build 15.0.1102.759), Lançamento: 23 de janeiro de 2020*
         - Recursos
            -  Exportar relatórios do Power BI para o Excel.
           -  Suporte a conjuntos de dados do Power BI Premium para relatórios paginados.
           -  Suporte a Text Alt (texto alternativo) para elementos de relatório paginados.
           -  Suporte a cabeçalhos personalizados.
           -  Suporte para as Instâncias Gerenciadas do SQL do Azure como um catálogo.
           -  Transparent Database Encryption para o catálogo.
        - Atualizações de segurança
        - Correções de bug
            - Correções de acessibilidade para leitores de tela, renderização de relatório e navegação por teclado.
            - Correção para salvar títulos de relatório de vários bytes.
            - Correção para log detalhado que afeta a confiabilidade do servidor de relatório.
          - Correção para garantir dados dinâmicos nos relatórios do Power BI em dispositivos móveis.
          - Correção para aplicar realce entre visuais na exportação filtrada de relatórios do Power BI.
          - Correção para redigir rodapé ao exportar para o Word com expressão para visibilidade de relatórios paginados. 
     
- **Power BI Desktop (otimizado para o Servidor de Relatórios do Power BI)**
    - *Versão: 2.76.5678.1521 (janeiro de 2020), Lançamento: 23 de janeiro de 2020* (novo build e nova versão)
        - Contém as alterações necessárias para conexão com o Servidor de Relatórios do Power BI (janeiro de 2020)        


## <a name="september-2019"></a>Setembro de 2019
- **Servidor de Relatório do Power BI**
    - *Versão: 1.6.7236.4246 (Build 15.0.1102.646), Lançamento: 25 de outubro de 2019*
        - Atualizações de segurança
        - Correções de bug
            - Correção do .NET Framework 4.7 não instalada.
            - Correção de relatórios paginados para o Teradata com parâmetros de vários valores com o erro 110083.
            - A correção do valor de URLRoot não funcionará se houver várias associações de URL de serviço Web e uma delas for https://+80/reportserver.
          - Correção dos valores de parâmetro de vários valores dos relatórios paginados exibidos fora da área do relatório.
          
    - *Versão: 1.6.7221.30698 (Compilação 15.0.1102.620), Lançada: 9 de outubro de 2019*
        - Correções de bug
            - Correção para o visual personalizado do Filtro de Texto.
            - Correção para o desempenho do menu suspenso de segmentação de dados.
            - Correção para Strip PII da telemetria.
          - Correção para URLs que não diferenciam maiúsculas de minúsculas.
          
    - *Versão 1.6.7206.38019 (Build 15.0.1102.597), lançamento: 26 de setembro de 2019*
        - Atualizações de segurança
        - Correções de bug
           - Relatórios paginados
             - Correção para os problemas de acessibilidade encontrados ao usar o Internet Explorer e o Microsoft Edge.
             - Correção de problemas com o SAP HANA durante o teste de conexão.
             - Correção de problemas encontrados ao fornecer a lista de endereços de email.
             - Correção para relatórios do Power BI que usam uma fonte de dados do DirectQuery e autenticação integrada.
             - Correção para relatórios paginados a serem renderizados com parâmetros de filtro quando o instantâneo está habilitado.
             - Correção para execução dupla de procedimentos armazenados durante a execução do relatório.
             - Correção na conta de serviço padrão, que recebia permissões de logon do SQL Server quando a conta de serviço personalizada estava configurada para executar o Servidor de Relatórios do Power BI.
             - Correção para acessar modelos ao atualizar em um fuso horário japonês.
             - Correção de modelos obsoletos quando uma nova versão do relatório é carregada durante a atualização.
             - Correção de valores de parâmetro que contêm o caractere '&'.
         - Programação
             - Atualização da API Web: /PowerBIReports({Id})/DataSources (PATCH) para permitir atualizações de cadeia de conexão.
         
- **Power BI Desktop (otimizado para o Servidor de Relatórios do Power BI)**
    - *Versão: 2.73.5586.1501 (setembro de 2019), Lançamento: 25 de outubro de 2019*
        - Correções de bug
            - Correção da telemetria.
            
    - *Versão: 2.73.5586.1241 (setembro de 2019), Lançada: 9 de outubro de 2019*
        - Correções de bug
            - Correção para o visual personalizado do Filtro de Texto.
            - Correção para o desempenho do menu suspenso de segmentação de dados.
            - Correção para Strip PII da telemetria.
            
    - *Versão: 2.73.5586.821 (Setembro de 2019), lançamento: 26 de setembro de 2019* (novo build e nova versão)
        - Contém as alterações necessárias para conexão com o Servidor de Relatórios do Power BI (Setembro de 2019)

    
## <a name="may-2019"></a>Maio de 2019

- **Servidor de Relatório do Power BI**          
    - *Versão 1.5.7074.36177 (Build 15.0.1102.371), lançamento: 21 de maio de 2019*
        - Correções de bug
            - Relatórios paginados
                - Correção para sempre habilitar a inserção de fonte do pdf.
                - Correção para definir cookies enviados via https como Seguro
                - Correção de problemas com pop-ups devido a erros de script
                - Correção de problemas de exibição com o Aplicativo Móvel em telefones Android
                - Correção para o Navegador de Tempo de Relatório Móvel mostrar os números de semana corretos, independentemente do início do ano fiscal
                - A propriedade configurável 'RestrictedResourceMimeTypeForUpload' foi adicionada para que os administradores especifiquem tipos de mime banidos
         - Recursos
            - Adicionando suporte para Visuais Confiáveis ao PBIRS

- **Power BI Desktop (otimizado para o Servidor de Relatórios do Power BI)**
    - *Versão: 2.69.5467.1801 (maio de 2019), lançamento: 21 de maio de 2019*
        - Correções de bug
            - Correção para evitar a reinserção de credenciais durante ao fazer upload de PBIX para PBIRS
            - Correções para abrir documentos com # no nome do arquivo
            - Adicionado link mais fácil para navegação de volta para a janela de seleção PBIRS
            - Correção para o modo de Alto Contraste no PBIRS para exibir o botão Voltar, exibir mensagens visuais de aviso.
            - Correções de interface do usuário ao painel de seleção, tela de dimensionamento.

    - *Versão: 2.69.5467.5201 (maio de 2019), lançada em: 30 de julho de 2019*
        - Correções de bug
            - Correção de registro em log de telemetria incorreto

## <a name="january-2019"></a>Janeiro de 2019

- **Servidor de Relatório do Power BI**          
    - *Versão 1.4.7024.16477 (Build 15.0.1102.299), lançamento: 28 de março de 2019*
        - Correções de bug
            - Relatórios do Power BI
                - Correção de problema com credenciais básicas ao usar a consulta direta para SAP Hana e SAP BW
                - Correção de atualização de dados de feed OData falha com "Não foi possível carregar o arquivo ou o assembly ' Microsoft.OData.Core.NetFX35.V7'"

- **Servidor de Relatório do Power BI**            
    - *Versão 1.4.6969.7395 (build 15.0.1102.235), Lançamento: 30 de janeiro de 2019*
        - Correções de bug
            - Relatórios do Power BI
                - Correção de problema com credenciais básicas ao usar a Consulta Direta
                - Correção de relações bidirecionais com filtros aplicados à Segurança em Nível de Linha
                - Correção de dados obsoletos após a atualização de um modelo em um ambiente expandido
                - Correção da barra de rolagem dupla para tabela/matriz no Firefox 63+
                - Correção para aumentar ou reduzir (+/-) tamanho de ícone no Internet Explorer
            - Relatórios paginados
                - Correção de problema com a atualização de uso de uma fonte de dados compartilhada para um relatório

    - *Versão 1.4.6960.38798 (Build 15.0.1102.222), Lançamento: 22 de janeiro de 2019*
        - Recursos
            - Relatórios do Power BI 
                - Suporte para Segurança em Nível de Linha
                - Expandir e recolher nos cabeçalhos de linha de matriz
                - Copiar e colar entre arquivos .pbix
                - Guias de alinhamento inteligente
                - Suporte para Conector SAP BW 2.0
            - Administradores
                - Capacidade de definir extensões de recursos que podem ser carregados para o servidor de relatório
                - Capacidade de restringir os esquemas de hiperlink compatíveis
            - Programação
                - Nova API Web: /PowerBIReports({Id})/DataModelRoles (GET)
                - Nova API Web: /PowerBIReports({Id})/DataModelRoleAssignments (GET e PUT)
                - Para ver mais detalhes, confira [API REST do Servidor de Relatórios do Power BI](https://app.swaggerhub.com/apis/microsoft-rs/PBIRS/2.0)
        - Correções de bug
            - Vulnerabilidade de injeção de HTML
            - A exportação para PDF não está mostrando o símbolo de Euro
            - A ação de salvar uma senha com várias fontes de dados em relatórios do Power BI invalida as senhas não alteradas
            - Visuais exibem problemas no Aplicativo Power BI Mobile depois de ficarem ociosos

- **Power BI Desktop (otimizado para o Servidor de Relatórios do Power BI)**
    - *Versão: 2.65.5313.1562 (janeiro de 2019). Lançamento: 30 de janeiro de 2019*
        - O atalho e os ícones fixados permanecem após a desinstalação do Servidor de Relatórios do Power BI
        - Correção para a fixação do Servidor de Relatórios do Power BI no menu Iniciar, que apresenta texto ou ícone em preto

    - *Versão: 2.65.5313.1421 (janeiro de 2019), lançamento: 22 de janeiro de 2019* (novo build e nova versão)
        - Contém as alterações necessárias para conexão com o Servidor de Relatórios do Power BI (janeiro de 2019) 
    - *Versão: 2.65.5313.5141 (janeiro de 2019), lançada em: 31 de janeiro de 2019* (novo build e nova versão)
        - Correções de bug
            - Correção de registro em log de telemetria incorreto

## <a name="august-2018"></a>Agosto de 2018

- **Servidor de Relatório do Power BI**
    - *Versão 1.3.6816.37243 (Build 15.0.2.557), lançamento: 30 de agosto de 2018*
        - Correções de bug
            - Foi corrigido um problema que ocorria quando o servidor era atualizado de versões anteriores do Servidor de Relatórios de PBI em que um redirecionamento de associação não era atualizado e o cliente via isto:      
            *`
            Failed to load expression host assembly. Details: Could not load file or assembly 'Microsoft.ReportingServices.ProcessingObjectModel, Version=2018.7.0.0, Culture=neutral, PublicKeyToken=89845dcd8080cc91' or one of its dependencies. The located assembly's manifest definition does not match the assembly reference. (Exception from HRESULT: 0x80131040) (rsErrorLoadingExprHostAssembly)
             `*
             
            - O bug de transparência de rótulo de dados agora foi corrigido.
            
    - *Versão 1.3.6801.38816 (Build 15.0.2.540), lançamento: 15 de agosto de 2018*
        - Recursos
            - O suporte para DirectQuery de SSO do SAP HANA com o Kerberos já está disponível para relatórios do Power BI
            - API de visual personalizado fornecida com a versão 1.13.0
            - Os visuais personalizados podem voltar a uma versão anterior compatível com a versão atual da API do servidor (se disponível)

- **Power BI Desktop (otimizado para o Servidor de Relatórios do Power BI)**
    - *Versão: 2.61.5192.641 (agosto de 2018), lançamento: 15 de agosto de 2018*
        - Contém as alterações necessárias para conexão com o Servidor de Relatórios do Power BI (agosto de 2018)         
    - *Versão: 2.61.5192.7701 (agosto de 2018), lançamento: 8 de agosto de 2019* (novo build e nova versão)
        - Correções de bug
            - Correção de registro em log de telemetria incorreto
            
## <a name="march-2018"></a>Março de 2018

- **Servidor de Relatório do Power BI**
    - *Versão 1.2.6690.34729 (Build 15.0.2.402), lançamento: 27 de abril de 2018*
        - Correções de bug
            - Habilitar a migração de catálogos do SQL Server Reporting Services 2017
            - Para relatórios do Power BI (PBIX)
                - Os relatórios podem ser atualizados quando um servidor está configurado para usar a autenticação personalizada
                - Modificar as propriedades de um relatório não redefine as credenciais da fonte de dados
            - Para relatórios paginados (RDL)
                - O uso de `Lookup()` ou funções derivadas, como `LookupSet()` e `MultiLookup()`, em expressões RDL não resulta mais em `#Error`
                - Os relatórios vinculados respeitam o tamanho da página do relatório de destino ao imprimir
                - É possível criar assinaturas para relatórios vinculados que usam parâmetros em cascata
                - É possível alterar padrões de parâmetro com vários valores ao usar o IE11
                - É possível editar as opções de entrega de assinatura controladas por dados
                - É possível exibir e editar assinaturas enquanto a assinatura está em execução
                - Configurar credenciais de fonte de dados não remove as cadeias de caracteres de conexão baseadas em expressão
            - Para KPIs
                - As linhas de tendência são atualizadas com os dados
            - Melhorias na estabilidade geral

    - *Versão 1.2.6660.39920 (Build 15.0.2.389), lançamento: 28 de março de 2018*
        - Correções de bug
            - Para Relatórios do Power BI (PBIX), correção para Exportar Dados que não está funcionando em Visuais do Power BI
            - Para Relatórios do Power BI (PBIX), correção para filtros de URL não estão funcionando
            - Para Relatórios Paginados (RDL), correção para imagens que não são exibidas corretamente no IE11 após a atualização para a versão de março do Servidor de Relatórios do Power BI

    - *Versão 1.2.6648.38132 (Build 15.0.2.378), lançamento: 19 de março de 2018*
        - Atualizações de Segurança
        - Aprimoramentos de acessibilidade
        - Correções de bug
            - Para Relatórios Paginados (RDL), correção de visibilidade de parâmetros em um relatório vinculado que é revertido após a edição de suas propriedades
            - Correção para o portal da Web com autenticação de formulários personalizados que está ignorando o cookie sliding expiration
            - Correção para exportação para o Word, que cria uma altura de linha desigual se o conteúdo da linha está vazio
            - Para Relatórios Paginados (RDL), correção para cadeia de conexão baseada em expressão que é excluída quando alteramos a credencial da fonte de dados
            - Correção para a capacidade de usar um KPI com valores de texto
            - Para Relatórios Paginados (RDL), correção para a capacidade de atribuir um novo conjunto de dados para um Relatório Paginado (RDL) existente
            - Outras correções de estabilidade e de facilidade de uso

- **Power BI Desktop (otimizado para o Servidor de Relatórios do Power BI)**
    - Versão: 2.56.5023.1043 (março de 2018), lançamento: 19 de março de 2018
        - Contém as alterações necessárias para a conexão ao Servidor de Relatórios do Power BI (março de 2018)

## <a name="october-2017"></a>Outubro de 2017

- **Servidor de Relatório do Power BI**
    - *Versão 1.1.6582.41691 (Build 14.0.600.442), lançamento: 10 de janeiro de 2018*
        - Atualizações de Segurança
        - Correções de bug
            - Correção para Model.GetParameters retornando 400
            - Correção para configurar o conjunto de dados compartilhado para Relatórios Paginados existentes (RDL)
            - Correção para ExecutionNotFoundException ao exportar o relatório com valores de parâmetros diferentes para PDF

    - *Versão 1.1.6551.5155 (Build 14.0.600.438), lançamento: 11 de dezembro de 2017*
        - Correções de bug
            - Falha ao salvar dados após a atualização para determinados relatórios do Power BI Desktop.

    - *Versão 1.1.6530.30789 (Build 14.0.600.437), lançamento: 17 de novembro de 2017*
        - Correções de bug
            - Correção para Cenários de Autenticação Básica 
            - A correção para dias da semana não pode ser selecionada na página de agendamentos para Assinaturas, Planos de Atualização de Cache e Instantâneos de Histórico no Portal
            - Para Relatórios Paginados (RDL), correção para expressões na caixa de texto com a propriedade CanGrow configurada como false resulta em valores que não mostram cores e fontes inadequadas
            - Para Relatórios do Power BI (PBIX), a correção para adicionar Legendas de gráfico de linhas renderiza um visual vazio

    - *Versão 1.1.6514.9163 (Build 14.0.600.434), lançamento: 1º de novembro de 2017*
        - Correções de bug
            - Corrigir problemas de confiabilidade de upload para relatórios PBIX acima de 500 MB
            - Corrigir problemas de carregamento de problema para relatórios PBIX acima de 1GB

    - *Versão 1.1.6513.3500 (Build 14.0.600.433), lançamento: 31 de outubro de 2017*
        - Recursos
            - Suporte para modelo de dados inserido
            - Exibição de pasta de trabalho do Excel (com a integração do Servidor do Office Online habilitada)
            - Atualização de dados agendada (PBIX)
            - Suporte para consulta direta
            - Suporte para arquivos grandes (até 2 GB)
            - API REST pública
            - Suporte para conjunto de dados compartilhado no Power BI Desktop (via OData)
            - Suporte para parâmetro de URL para arquivos PBIX
            - Aprimoramentos de acessibilidade

- **Power BI Desktop (otimizado para o Servidor de Relatórios do Power BI)**
    - *Versão: 2.51.4885.3981 (outubro de 2017), lançamento: 10 de abril de 2018*
        - Atualizações de Segurança

    - *Versão: 2.51.4885.2501 (outubro de 2017), lançamento: 10 de janeiro de 2018*
        - Atualizações de Segurança

    - *Versão: 2.51.4885.1423 (outubro de 2017), lançamento: 17 de novembro de 2017*
        - Correções de bug
            - Correção para Power BI Desktop de 32 bits falha na execução em SO x86
            - Para os Relatórios do Power BI (PBIX), correção para mostrar linhas de grade do eixo x
            - Outras correções de bugs secundários

    - *Versão: 2.51.4885.1041 (outubro de 2017), lançamento: 31 de outubro de 2017*
        - Recursos
            - Contém as alterações necessárias para a conexão ao Servidor de Relatórios do Power BI (outubro de 2017)

## <a name="june-2017"></a>Junho de 2017

- **Servidor de Relatório do Power BI**
    - *Build 14.0.600.309, lançamento: 10 de janeiro de 2018*
        - Atualizações de Segurança

    - *Build 14.0.600.305, lançamento: 19 de setembro de 2017*  
        - Correções de bug
            - Atualizar para a versão mais recente do [Controle da Web do Bing Maps](https://msdn.microsoft.com/library/mt712542.aspx)

    - *Build 14.0.600.301, lançamento: 11 de julho de 2017*
        - Correções de bug
            - A marca `{{UserId}}` resolve para as credenciais armazenadas, em vez do usuário que executa o relatório nos Relatórios do Power BI
            - Algumas imagens apresentam falha ao ser renderizadas em relatórios do Servidor de Relatório do Power BI
            - Não é possível alterar o nome de um Relatório do Power BI no Servidor de Relatório do Power BI
            - Não é possível carregar visuais personalizados no aplicativo móvel Power BI (isso requer a reinstalação do aplicativo móvel para limpar o cache local)

    - *Build 14.0.600.271, lançamento: 12 de junho de 2017*
        - Versão inicial do Servidor de Relatório do Power BI

- **Power BI Desktop (otimizado para o Servidor de Relatórios do Power BI)**
    - *Versão: 2.47.4766.4901 (junho de 2017), lançamento: 10 de janeiro de 2018*
        - Atualizações de Segurança

## <a name="next-steps"></a>Próximas etapas

[O que é o Servidor de Relatórios do Power BI?](get-started.md)
[Visão geral do administrador](admin-handbook-overview.md)  
[Instalar o Servidor de Relatório do Power BI](install-report-server.md)  
[Baixar o Construtor de Relatórios](https://www.microsoft.com/download/details.aspx?id=53613)  
[Baixar o SSDT (SQL Server Data Tools)](https://go.microsoft.com/fwlink/?LinkID=616714)

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
