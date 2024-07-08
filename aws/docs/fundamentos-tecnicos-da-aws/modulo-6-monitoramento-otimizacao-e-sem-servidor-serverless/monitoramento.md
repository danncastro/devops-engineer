# Monitoramento

***

## <mark style="color:red;">**Objetivo do monitoramento**</mark>

<figure><img src="../../.gitbook/assets/image (35).png" alt=""><figcaption></figcaption></figure>

O monitoramento é essencial para operar eficientemente um site ou aplicação na AWS, como um diretório de funcionários. Ele permite responder a perguntas críticas como:

* Quantas visitas meu site recebe diariamente?
* Como o número de visitantes varia ao longo do tempo?
* Há problemas de desempenho ou disponibilidade no site?
* Estou preparado se minha instância do Amazon EC2 ficar sem capacidade?
* Receberei alertas se meu site ficar inativo?

Monitoramento envolve a coleta e análise contínuas de dados sobre a saúde operacional e uso de recursos. Esses dados são essenciais para tomar decisões informadas e identificar problemas como uso excessivo de recursos, falhas de aplicação, configurações incorretas ou questões de segurança.

#### <mark style="color:blue;">**Por que usar monitoramento**</mark>

| Previsão de Problemas                                          | Otimização de Recursos                                  |
| -------------------------------------------------------------- | ------------------------------------------------------- |
| Identificar e resolver problemas antes que afetem os usuários. | Ajustar recursos com base em padrões de uso observados. |

| Resposta Rápida                                                                     | Planejamento de Capacidade                                                     |
| ----------------------------------------------------------------------------------- | ------------------------------------------------------------------------------ |
| Agir proativamente com alertas instantâneos sobre falhas ou degradações de serviço. | Planejar expansões ou ajustes de capacidade com base em tendências de tráfego. |

#### <mark style="color:blue;">**Casos de Uso**</mark>

| Sites de comércio eletrônico                                                          |
| ------------------------------------------------------------------------------------- |
| Monitorar tráfego e transações para garantir disponibilidade durante picos de vendas. |

| Aplicações web de alto tráfego                                                         | Aplicações críticas                                                                          |
| -------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------- |
| Rastrear comportamento de usuários e otimizar recursos para manter desempenho estável. | Garantir alta disponibilidade e resposta rápida a falhas para aplicações sensíveis ao tempo. |

Os dados coletados através do monitoramento, como métricas e logs, são vitais para uma operação suave e eficaz, oferecendo visibilidade essencial para manter a confiabilidade e a performance das aplicações na nuvem.

***

### <mark style="color:red;">**Uso de Métricas para Resolução de Problemas**</mark>

Os recursos da AWS que sustentam suas soluções geram uma variedade de dados que podem ser úteis para coletar. Cada ponto de dados gerado por um recurso é uma métrica. Ao longo do tempo, essas métricas coletadas e analisadas se transformam em estatísticas, como a média de utilização da CPU, exibindo picos.

Por exemplo, para avaliar a saúde de uma instância do Amazon EC2, a utilização da CPU é um indicador crucial. Alta utilização pode indicar alto tráfego ou um processo com erro consumindo recursos. Ao identificar uma utilização anormal da CPU acima de um threshold específico por um período prolongado, isso pode sinalizar a necessidade de escalonamento automático ou a investigação manual para resolver problemas.

#### <mark style="color:blue;">**Por que usar Métricas**</mark>

| Identificação Proativa de Problemas                                     |
| ----------------------------------------------------------------------- |
| Detectar anomalias antes que afetem a performance ou a disponibilidade. |

| Otimização de Recursos                                           | Resolução Rápida de Incidentes                                             |
| ---------------------------------------------------------------- | -------------------------------------------------------------------------- |
| Ajustar capacidade com base em padrões de utilização observados. | Agir rapidamente em eventos anormais para minimizar impactos operacionais. |

#### <mark style="color:blue;">**Casos de Uso**</mark>

| Aplicações Web de Alto Tráfego                                   |
| ---------------------------------------------------------------- |
| Monitorar e ajustar recursos para suportar variações na demanda. |

| Ambientes Críticos                                                                | Desenvolvimento e Testes                                                       |
| --------------------------------------------------------------------------------- | ------------------------------------------------------------------------------ |
| Garantir performance estável e disponibilidade contínua para serviços essenciais. | Identificar gargalos e otimizar eficiência durante o ciclo de desenvolvimento. |

Métricas como utilização de rede, performance de disco, uso de memória e logs de aplicativos no Amazon EC2 são cruciais para entender e otimizar a infraestrutura na nuvem.

***

### <mark style="color:red;">Tipos de métricas</mark>

Os recursos variados da AWS geram tipos específicos de métricas. Por exemplo, um bucket no Amazon S3 não possui métricas de utilização de CPU como uma instância do EC2. Em vez disso, o Amazon S3 monitora métricas relacionadas aos objetos armazenados, como tamanho total do bucket e número de objetos. Além disso, o S3 registra métricas sobre solicitações feitas ao bucket, como leitura ou gravação de objetos.

Por outro lado, o Amazon Relational Database Service (Amazon RDS) oferece métricas como conexões de banco de dados, utilização de CPU das instâncias e uso de espaço em disco. Cada serviço na AWS gera métricas específicas para refletir o uso e o desempenho de seus recursos.

#### <mark style="color:blue;">**Por que usar Métricas**</mark>

| Visibilidade e Controle                                | Otimização de Custos                                | Planejamento Estratégico                                             |
| ------------------------------------------------------ | --------------------------------------------------- | -------------------------------------------------------------------- |
| Monitorar saúde operacional e performance de recursos. | Identificar subutilização ou excesso de capacidade. | Basear decisões em dados concretos sobre utilização e comportamento. |

#### <mark style="color:blue;">**Casos de Uso**</mark>

| Armazenamento em Nuvem                                       |
| ------------------------------------------------------------ |
| Gerenciar capacidade e custos de armazenamento no Amazon S3. |

| Bancos de Dados Relacionais                          | Aplicações de Alta Disponibilidade                            |
| ---------------------------------------------------- | ------------------------------------------------------------- |
| Monitorar desempenho e escalabilidade no Amazon RDS. | Ajustar recursos para atender picos de demanda em tempo real. |

Ao escolher as métricas a serem monitoradas, considere os requisitos específicos de cada serviço e como as métricas podem contribuir para a eficiência operacional e a otimização de recursos na AWS.

***

### <mark style="color:red;">**Benefícios do Monitoramento na AWS**</mark>

O monitoramento oferece visibilidade essencial sobre seus recursos, proporcionando uma série de benefícios fundamentais:

<details>

<summary><mark style="color:purple;">Resolução Proativa de Problemas</mark></summary>

Monitorar métricas como taxa de erros e latência de solicitações permite identificar problemas antes que afetem os usuários finais. Isso possibilita ações preventivas para evitar interrupções e corrigir problemas rapidamente.

</details>

<details>

<summary><mark style="color:purple;">Melhoria de Performance e Confiabilidade</mark></summary>

Ao monitorar todos os componentes da sua aplicação, você pode identificar gargalos e melhorar a eficiência do sistema como um todo. Isso resulta em maior performance e confiabilidade para seus usuários.

</details>

<details>

<summary><mark style="color:purple;">Detecção de Ameaças e Anomalias</mark></summary>

O monitoramento contínuo cria uma linha de base do comportamento normal dos seus recursos. Isso ajuda a identificar anomalias, como picos de tráfego ou acessos não autorizados, permitindo ação imediata para mitigar ameaças à segurança.

</details>

<details>

<summary><mark style="color:purple;">Decisões Orientadas por Dados</mark></summary>

Utilizando métricas, você pode tomar decisões informadas para o seu negócio. Por exemplo, monitorar a adoção de um novo recurso em sua aplicação permite ajustar estratégias com base no uso real, otimizando investimentos e recursos.

</details>

<details>

<summary><mark style="color:purple;">Otimização de Custos</mark></summary>

Ao identificar recursos subutilizados ou excessivamente dimensionados, o monitoramento ajuda a ajustar corretamente a capacidade dos seus recursos. Isso resulta em uma infraestrutura mais econômica e eficiente, evitando gastos desnecessários.

</details>

#### <mark style="color:blue;">**Casos de Uso**</mark>

| E-commerce                                                                         | Aplicações Web                                                                      | Segurança                                                               |
| ---------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- | ----------------------------------------------------------------------- |
| Monitoramento de transações para evitar falhas durante períodos de pico de vendas. | Identificação de problemas de desempenho antes que afetem a experiência do usuário. | Detecção precoce de atividades suspeitas para proteger dados sensíveis. |

#### <mark style="color:blue;">**Por que usar o Monitoramento**</mark>

| Prevenção de Interrupções                      | Otimização Operacional             |
| ---------------------------------------------- | ---------------------------------- |
| Garante disponibilidade contínua dos serviços. | Aumenta eficiência e reduz custos. |

| Segurança Avançada                   | Decisões Estratégicas                                    |
| ------------------------------------ | -------------------------------------------------------- |
| Protege contra ameaças cibernéticas. | Baseia-se em dados para melhorar estratégias de negócio. |

***

### <mark style="color:red;">Visibilidade</mark>

#### <mark style="color:blue;">**Amazon CloudWatch: Monitoramento e Visibilidade na AWS**</mark>

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

### **Recurso**

[AWS: Amazon CloudWatch](https://aws.amazon.com/cloudwatch/)

***
