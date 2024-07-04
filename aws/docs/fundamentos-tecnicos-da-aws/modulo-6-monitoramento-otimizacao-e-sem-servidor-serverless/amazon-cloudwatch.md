# Amazon CloudWatch

***

## <mark style="color:red;">**Monitoramento e Visibilidade na AWS**</mark>

Na AWS, os recursos geram uma variedade de dados, incluindo métricas, logs, tráfego de rede e eventos. A dispersão natural desses dados pode dificultar sua coleta e análise sem um ponto centralizado. A solução para isso é o Amazon CloudWatch.

O Amazon CloudWatch é um serviço robusto de monitoramento e observabilidade que coleta dados de diversos componentes AWS. Ele oferece insights cruciais para aplicações, permitindo respostas rápidas a mudanças de performance, otimização de recursos e uma visão integrada da saúde operacional.

#### <mark style="color:blue;">**Por que usar o Amazon CloudWatch**</mark>

| Detectar Comportamentos Anômalos                                                | Definir Alarmes                                                                                  |
| ------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------ |
| Identifique desvios de comportamento que possam indicar problemas operacionais. | Configure alertas para ser notificado imediatamente quando algo não estiver conforme o esperado. |

| Visualizar Logs e Métricas                                                                    | Automação de Ações                                                                           |
| --------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------- |
| Utilize o Console de Gerenciamento da AWS para monitorar e analisar dados de forma eficiente. | Implemente escalabilidade automática e outras ações corretivas com base nos dados coletados. |

| Resolução de Problemas                                                      | Geração de Insights                                                                 |
| --------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- |
| Facilite a identificação e resolução de problemas operacionais rapidamente. | Obtenha informações valiosas para manter a integridade e eficiência das aplicações. |

#### <mark style="color:blue;">**Casos de Uso**</mark>

| E-commerce                                                                                    | Aplicações Web                                                            | Segurança                                                                  |
| --------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------- | -------------------------------------------------------------------------- |
| Monitoramento de picos de tráfego durante vendas sazonais para ajustes dinâmicos de recursos. | Identificação de gargalos de performance e otimização de uso de recursos. | Detecção precoce de atividades suspeitas para mitigação rápida de ameaças. |

O Amazon CloudWatch é essencial para garantir que suas aplicações na AWS operem com eficiência, segurança e alta disponibilidade.

***

### <mark style="color:red;">Métricas: Organização e Utilização</mark>

No Amazon CloudWatch, cada métrica é identificada por um carimbo de data/hora e é agrupada em namespaces, que funcionam como contêineres isolados para categorizar métricas distintas.

#### <mark style="color:blue;">**Namespace e Dimensões**</mark>

| Namespace                                                                                                 | Dimensões                                                                                                                                                                                                                                       |
| --------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| As métricas são organizadas em namespaces, que servem como categorias para agrupar métricas relacionadas. | Cada métrica é associada a dimensões, pares de nome/valor que fornecem identificação adicional. Por exemplo, uma métrica de uma instância EC2 pode ter dimensões como InstanceId para filtrar e obter estatísticas específicas dessa instância. |

#### <mark style="color:blue;">**Por que usar o Amazon CloudWatch**</mark>

| Monitoramento Detalhado                                                 | Organização Eficiente                                                               | Customização                                                                                                                         |
| ----------------------------------------------------------------------- | ----------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------ |
| Permite monitorar e analisar o desempenho de recursos AWS com precisão. | Agrupa métricas em namespaces e usa dimensões para facilitar a navegação e análise. | A capacidade de filtrar métricas por dimensões específicas oferece flexibilidade para análise detalhada e relatórios personalizados. |

#### <mark style="color:blue;">**Casos de Uso**</mark>

| Performance de Aplicações                                                                           |
| --------------------------------------------------------------------------------------------------- |
| Monitorar a utilização de recursos de instâncias EC2 por **InstanceId** para ajustes de capacidade. |

| Ambientes Multi-AZ                                                                                                     | Segurança e Compliance                                                                                |
| ---------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------- |
| Avaliar a latência de replicação de bancos de dados RDS em diferentes zonas de disponibilidade usando dimensões de AZ. | Rastrear atividades de log por dimensões específicas como UserId para detectar acesso não autorizado. |

O Amazon CloudWatch proporciona uma visão detalhada e organizada do desempenho e operações dos seus recursos na AWS, essencial para manter a eficiência e disponibilidade das suas aplicações.

***

### <mark style="color:red;">Métricas Personalizadas: Flexibilidade e Granularidade</mark>

Quando você precisa monitorar aspectos específicos da sua aplicação que não são automaticamente capturados pelas métricas padrão do CloudWatch, as métricas personalizadas são a solução ideal. Essas métricas permitem que você registre dados exclusivos e cruciais para o desempenho da sua aplicação diretamente no CloudWatch.

#### <mark style="color:blue;">**Características das Métricas Personalizadas**</mark>

| Flexibilidade                                                                                                                                                                                        | Granularidade                                                                                                                                                                                                           |
| ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Permitem que você registre qualquer tipo de dado relevante para suas operações, como contagens de visualizações de página, tempos de carregamento de páginas da web ou taxas de erro de solicitação. | Métricas personalizadas de alta resolução oferecem uma captura detalhada ao permitir o envio de pontos de dados até a resolução de 1 segundo. Isso é essencial para monitorar eventos rápidos e precisos em tempo real. |

#### <mark style="color:blue;">**Por que usar Métricas Personalizadas**</mark>

| Monitoramento Específico                                                                                                                     | Resposta Rápida                                                                                                                          |
| -------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------- |
| Capture dados que são específicos para suas necessidades de negócios e que não são monitorados automaticamente pelas métricas padrão da AWS. | A capacidade de monitorar eventos e tendências em tempo real ajuda na detecção precoce de problemas e na resposta imediata a incidentes. |

#### <mark style="color:blue;">**Exemplos de Casos de Uso**</mark>

| Performance de Aplicações Web                                                                                         |
| --------------------------------------------------------------------------------------------------------------------- |
| Monitore tempos de resposta de página e taxas de erros para identificar gargalos e otimizar a experiência do usuário. |

| Monitoramento de Recursos                                                                                             | Análise de Carga de Trabalho                                                                                           |
| --------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------- |
| Acompanhe o número de processos ou threads em execução para ajustar a capacidade e melhorar a eficiência operacional. | Avalie a carga de trabalho da sua aplicação para dimensionar recursos adequadamente e garantir desempenho consistente. |

#### <mark style="color:blue;">**Implementação de Métricas Personalizadas**</mark>

| API PutMetricData                                                                                                                                             |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Use a API PutMetricData para enviar programaticamente suas métricas personalizadas para o CloudWatch, integrando-se facilmente com suas operações existentes. |

As métricas personalizadas no Amazon CloudWatch oferecem a flexibilidade e a precisão necessárias para monitorar de perto o desempenho e a saúde operacional das suas aplicações na AWS, permitindo a tomada de decisões informadas e a otimização contínua.

***

### <mark style="color:red;">Painéis: Visualização Personalizada e Controle</mark>

Após provisionar seus recursos na AWS e começar a coletar métricas no CloudWatch, você pode utilizar os painéis do CloudWatch para visualizar e analisar esses dados de forma personalizada. Os painéis são páginas configuráveis que permitem a visualização de uma ou mais métricas através de diversos tipos de widgets, como gráficos ou texto.

#### <mark style="color:blue;">**Principais Funcionalidades dos Painéis do CloudWatch**</mark>

| Customização Flexível                                                                                                                                                                                                                        | Integração de Dados                                                                                                                                                                                                         |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Crie painéis personalizados para focar em visões específicas do seu ambiente operacional. Cada painel pode ser configurado para exibir métricas de diferentes recursos e regiões, oferecendo uma visão abrangente da sua arquitetura na AWS. | Agregue estatísticas conforme o período de tempo especificado, permitindo análises detalhadas ao longo do tempo. Os dados podem ser visualizados em tempo real para insights imediatos sobre o desempenho atual do sistema. |

#### <mark style="color:blue;">**Benefícios de Utilização**</mark>

| Monitoramento Centralizado                                                                                                 | Tomada de Decisões Informadas                                                                                                |
| -------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------- |
| Visualize métricas críticas de vários serviços da AWS em um único local, simplificando a gestão e a análise de desempenho. | Identifique tendências, padrões e anomalias rapidamente para realizar ajustes proativos e melhorar a eficiência operacional. |

#### <mark style="color:blue;">**Casos de Uso**</mark>

| Gestão de Aplicações Críticas                                                                                                               | Otimização de Custos                                                                                     |
| ------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------- |
| Monitore métricas como tempo de resposta, utilização de CPU e erros de aplicação para garantir alta disponibilidade e performance contínua. | Analise o uso de recursos para identificar oportunidades de otimização e redução de custos operacionais. |

#### <mark style="color:blue;">**Segurança e Controle de Acesso**</mark>

| IAM e Políticas de Acesso                                                                                                                           |
| --------------------------------------------------------------------------------------------------------------------------------------------------- |
| Controle quem pode visualizar e gerenciar os painéis do CloudWatch através de políticas granulares do AWS IAM, garantindo segurança e conformidade. |

Os painéis do Amazon CloudWatch oferecem uma interface poderosa para monitorar e analisar o desempenho dos seus recursos na AWS, ajudando a manter operações eficientes e seguras.

***

### <mark style="color:red;">Logs: Centralize e Analise Seus Logs com Facilidade</mark>

O Amazon CloudWatch Logs oferece um local centralizado para armazenar, monitorar e analisar logs de aplicações em execução em instâncias do Amazon EC2, funções do AWS Lambda e outras fontes na AWS.

#### <mark style="color:blue;">**Principais Funcionalidades do CloudWatch Logs**</mark>

| Armazenamento Centralizado                                                                                        |
| ----------------------------------------------------------------------------------------------------------------- |
| Consolidar logs de várias fontes em um único serviço facilita a gestão e a análise de logs operacionais críticos. |

| Consultas e Filtragem Avançadas                                                                                                                                                                                      | Transformação em Métricas                                                                                                                                                                   |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Utilize consultas para filtrar e analisar dados específicos de logs. Por exemplo, ao investigar erros de lógica em uma aplicação, consulte os logs para identificar rastreamentos de pilha associados a esses erros. | Configure filtros para transformar dados de logs em métricas numéricas no CloudWatch. Essas métricas podem ser visualizadas em painéis para monitoramento contínuo e análise de tendências. |

#### <mark style="color:blue;">**Casos de Uso**</mark>

| Monitoramento de Erros e Problemas                                                                                                | Auditoria e Conformidade                                                                                                |
| --------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------- |
| Identifique rapidamente eventos de erro, anomalias de desempenho ou falhas de aplicação através da análise de logs centralizados. | Mantenha registros detalhados para auditoria de conformidade e investigação forense em caso de incidentes de segurança. |

#### <mark style="color:blue;">**Integração Simplificada**</mark>

| AWS Lambda e Outros Serviços                                                                                                                                                         | Instâncias do EC2                                                                                                                                                                                     |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| AWS Lambda e outros serviços enviam automaticamente logs para o CloudWatch Logs com configuração mínima, simplificando o monitoramento de funções serverless e serviços em execução. | Configure o agente do CloudWatch Logs para enviar logs de instâncias do EC2 com facilidade. Uma vez configurado, o agente garante o envio automático de dados de log para análise no CloudWatch Logs. |

#### <mark style="color:blue;">**Benefícios de Utilização**</mark>

| Visibilidade Operacional                                                                                               | Tomada de Decisões Informadas                                                                                                                         |
| ---------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------- |
| Tenha uma visão unificada e detalhada do desempenho e da integridade da aplicação através da análise contínua de logs. | Utilize dados históricos de logs para melhorar a performance, otimizar recursos e implementar melhorias proativas na infraestrutura e nas aplicações. |

O Amazon CloudWatch Logs simplifica o gerenciamento e a análise de logs, proporcionando insights valiosos para manter a operação eficiente e segura de suas aplicações na AWS.

***

### <mark style="color:red;">**Terminologia dos Logs: Entenda e Organize Seus Logs**</mark>

Ao enviar dados de log para o Amazon CloudWatch Logs, é essencial compreender a terminologia usada para descrever como esses dados são organizados e acessados.

{% tabs %}
{% tab title="Eventos de Log" %}
Cada evento de log é um registro da atividade capturada pela aplicação ou recurso monitorado. Cada evento possui um carimbo de data/hora e uma mensagem descritiva, fornecendo informações cruciais sobre a operação e o status do recurso.
{% endtab %}

{% tab title="Fluxos de Log" %}
Os eventos de log são agrupados em fluxos de log, que representam sequências contínuas de eventos relacionados a um único recurso monitorado. Por exemplo, os logs de uma instância do Amazon EC2 são capturados e agrupados em um fluxo de log específico para essa instância. Isso facilita a análise e o gerenciamento de logs específicos de cada recurso.
{% endtab %}

{% tab title="Grupos de Log" %}
Os fluxos de log são organizados em grupos de log, que são conjuntos de fluxos de log com configurações de retenção e permissões compartilhadas. Por exemplo, você pode agrupar os fluxos de log de várias instâncias do EC2 que hospedam uma aplicação em um único grupo de log. Isso não apenas mantém seus registros organizados, mas também simplifica a aplicação de políticas de retenção de dados e controle de acesso.
{% endtab %}
{% endtabs %}

#### <mark style="color:blue;">**Casos de Uso**</mark>

| Monitoramento de Aplicações em Tempo Real                                                                                                                  | Auditoria e Conformidade                                                                                                                            |
| ---------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------- |
| Utilize fluxos de log para monitorar em tempo real o desempenho e a integridade de aplicações distribuídas em diferentes instâncias EC2 ou funções Lambda. | Organize fluxos de log em grupos específicos para facilitar auditorias de conformidade e investigações forenses em caso de incidentes de segurança. |

#### <mark style="color:blue;">**Por que Usar**</mark>

| Organização e Gestão Simplificadas                                                                                                                                                                      | Visibilidade e Monitoramento Eficientes                                                                                                                                                |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| A estrutura de grupos e fluxos de log do CloudWatch Logs oferece uma maneira intuitiva de organizar e acessar grandes volumes de dados de log, facilitando a análise e a tomada de decisões informadas. | Ao agrupar e organizar fluxos de log, você ganha visibilidade detalhada sobre o desempenho operacional de suas aplicações e recursos, permitindo respostas rápidas a eventos críticos. |

O Amazon CloudWatch Logs fornece uma estrutura robusta para gerenciamento e análise de logs, essencial para manter a integridade e o desempenho de suas operações na AWS.

***

### <mark style="color:red;">Alarmes: Monitoramento Proativo e Ações Automatizadas</mark>

Os alarmes do Amazon CloudWatch permitem que você configure ações automáticas com base em mudanças sustentadas no estado de suas métricas. Esses alarmes são fundamentais para a monitorização proativa de recursos na AWS.

#### <mark style="color:blue;">**Configuração de Alarmes**</mark>

Para criar um alarme, primeiro escolha a métrica que deseja monitorar e defina um threshold que acionará o alarme. Por exemplo, você pode configurar um alarme para uma instância do Amazon EC2 que dispare quando a utilização da CPU ultrapassar 80% por mais de 5 minutos consecutivos. Isso ajuda a evitar acionamentos de alarme por picos temporários de curta duração, concentrando-se em anomalias significativas de desempenho.

#### <mark style="color:blue;">**Estados do Alarme**</mark>

<table data-view="cards"><thead><tr><th></th><th></th><th></th></tr></thead><tbody><tr><td></td><td><mark style="color:green;"><strong>OK:</strong></mark> Indica que a métrica está dentro do threshold definido, sem necessidade de intervenção.</td><td></td></tr><tr><td></td><td><mark style="color:red;"><strong>ALARM (Alarme):</strong></mark> Indica que a métrica ultrapassou o threshold especificado, sinalizando um possível problema operacional que requer atenção imediata.</td><td></td></tr><tr><td></td><td><mark style="color:purple;"><strong>INSUFFICIENT_DATA (Dados insuficientes):</strong></mark> Indica que não há dados suficientes disponíveis para a métrica determinar seu estado atual.</td><td></td></tr></tbody></table>

#### <mark style="color:blue;">**Casos de Uso**</mark>

| Escalabilidade Automática                                                                                                                                                                                                                        | Notificações em Tempo Real                                                                                                                        |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------- |
| Configure alarmes para monitorar métricas como utilização de CPU ou tráfego de rede. Quando o threshold é alcançado, o CloudWatch pode acionar uma ação de escalabilidade automática, aumentando ou diminuindo a capacidade conforme necessário. | Utilize o Amazon SNS para receber notificações instantâneas sempre que um alarme for acionado, permitindo uma resposta rápida a eventos críticos. |

#### <mark style="color:blue;">**Por que Usar**</mark>

| Monitoramento Contínuo                                                                                                                                                          | Resposta Automatizada                                                                                                     |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------- |
| Mantenha uma vigilância constante sobre o desempenho dos seus recursos na AWS, garantindo que problemas sejam identificados e resolvidos antes que impactem os usuários finais. | Automatize respostas a eventos operacionais, reduzindo o tempo de inatividade e melhorando a confiabilidade dos serviços. |

Os alarmes do Amazon CloudWatch são essenciais para operações eficientes na nuvem, proporcionando uma maneira robusta e flexível de monitorar e gerenciar recursos críticos em tempo real.

***

### <mark style="color:red;">Prevenir e solucionar problemas com alarmes do CloudWatch</mark>

O Amazon CloudWatch Logs utiliza filtros de métrica para converter dados de log em métricas que podem ser usadas para criar gráficos ou definir alarmes. Por exemplo, para uma aplicação de diretório de funcionários, você pode configurar um filtro de métrica para monitorar códigos de resposta de erro 500. Em seguida, define um alarme que entra no estado ALARM se o número de erros 500 ultrapassar um limiar específico por um período prolongado, como mais de cinco erros por hora.

#### <mark style="color:blue;">**Configuração e Ação dos Alarmes**</mark>

| Configuração                                                                                                                           | Ação                                                                                                                                                                                                 |
| -------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Configure alarmes para monitorar diferentes aspectos operacionais, como uso de CPU, tráfego de rede ou erros específicos de aplicação. | Defina ações automáticas ou notificações via Amazon SNS quando um alarme é acionado. Por exemplo, envie um e-mail ou alerta de texto para notificar a equipe responsável sobre um problema iminente. |

#### <mark style="color:blue;">**Casos de Uso**</mark>

| Monitoramento Proativo                                                                                                                                                                                                                             | Automação de Respostas                                                                                                                                                            |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Utilize alarmes para identificar problemas antes que eles afetem os usuários finais. Por exemplo, configurar alarmes para iniciar ações automáticas de escalabilidade ou reinicialização de instâncias do Amazon EC2 em resposta a picos de carga. | Configure alarmes para acionar funções do AWS Lambda que executam scripts automatizados para resolver problemas operacionais, como ajustes de configuração ou gestão de recursos. |

#### <mark style="color:blue;">**Por que Usar**</mark>

| Resposta Rápida a Eventos                                                                                                                                                                                | Redução de Impacto                                                                                                                                                          |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Ao integrar produtos da AWS, como CloudWatch, SNS e Lambda, você pode responder rapidamente a eventos críticos, minimizando o tempo de inatividade e garantindo a disponibilidade contínua dos serviços. | A capacidade de automatizar ações de correção de problemas reduz o impacto de problemas operacionais, melhorando a experiência do usuário final e a eficiência operacional. |

Os alarmes do Amazon CloudWatch são essenciais para operações eficientes na nuvem, permitindo que você monitore, aja proativamente e automatize respostas a eventos operacionais críticos em tempo real.

***

### **Recursos**

[Introdução ao Amazon CloudWatch(opens in a new tab)](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/GettingStarted.html)

[O que é o Amazon CloudWatch Logs?(opens in a new tab)](https://docs.aws.amazon.com/AmazonCloudWatch/latest/logs/WhatIsCloudWatchLogs.html)

[Produtos da AWS que publicam métricas do CloudWatch(opens in a new tab)](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/aws-services-cloudwatch-metrics.html)

[Exibir métricas disponíveis(opens in a new tab)](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/viewing\_metrics\_with\_cloudwatch.html)

[Definição de preço do Amazon CloudWatch(opens in a new tab)](https://aws.amazon.com/cloudwatch/pricing/)

[Amazon Simple Notification Service(opens in a new tab)](https://aws.amazon.com/sns/)

[Ações do EC2 Auto Scaling](https://aws.amazon.com/ec2/autoscaling/)

***
