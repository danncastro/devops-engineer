# Amazon DynamoDB

***

## <mark style="color:red;">**Introdução ao Amazon DynamoDB**</mark>

O Amazon DynamoDB é um serviço de banco de dados NoSQL totalmente gerenciado pela AWS, projetado para oferecer alta performance e escalabilidade automática. Com o DynamoDB, você elimina a complexidade de gerenciar um banco de dados distribuído, pois não precisa se preocupar com provisionamento, configuração de hardware, replicação ou escalabilidade de cluster.

#### <mark style="color:blue;">**Características principais do Amazon DynamoDB**</mark>

| Performance Previsível                                                                                                        | Elasticidade Vertical                                                                                                                                   |
| ----------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Garante resposta rápida mesmo sob cargas intensas de solicitações, escalando automaticamente para atender demandas variáveis. | Permite ajustar a capacidade de taxa de transferência das tabelas de forma dinâmica, sem impacto na performance ou necessidade de tempo de inatividade. |

| Monitoramento Simplificado                                                                                             | Distribuição Automática                                                                                                                              |
| ---------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------- |
| Utiliza o Console de Gerenciamento da AWS para acompanhar recursos utilizados e métricas de performance em tempo real. | Distribui dados e tráfego entre servidores para atender aos requisitos de taxa de transferência e armazenamento, mantendo consistência e velocidade. |

#### <mark style="color:blue;">**Por que usar Amazon DynamoDB**</mark>

| Aplicações de Alta Escala                                                                                                         | Ambientes de IoT                                                                                                                                  |
| --------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------- |
| Ideal para aplicativos que requerem resposta rápida e escalabilidade eficiente, como jogos online e aplicativos móveis populares. | Suporta ingestão e processamento de grandes volumes de dados gerados por dispositivos IoT, mantendo alta disponibilidade e integridade dos dados. |

#### <mark style="color:blue;">**Casos de Uso**</mark>

| Gaming                                                                                    | IoT                                                                                                                                |
| ----------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------- |
| Armazenamento de perfis de jogadores e registros de jogo com acesso rápido e consistente. | Gerenciamento de dados de sensores e dispositivos IoT, garantindo alta performance e escalabilidade para grandes volumes de dados. |

Em resumo, o Amazon DynamoDB é uma escolha robusta para aplicações que exigem escalabilidade, performance previsível e gerenciamento simplificado de banco de dados NoSQL. Sua capacidade de ajustar dinamicamente a capacidade de resposta às demandas do aplicativo faz dele uma solução eficaz para diversos cenários de uso na nuvem.

***

### <mark style="color:red;">**Componentes principais do Amazon DynamoDB**</mark>

O Amazon DynamoDB utiliza tabelas, itens e atributos como seus principais componentes para armazenamento e organização de dados:

| Tabelas                                                                                                                                                                                                                                                   |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Funcionam como contêineres de dados, semelhantes a tabelas em outros bancos de dados. Por exemplo, uma tabela "Pessoas" pode armazenar informações de contato de indivíduos, enquanto uma tabela "Carros" pode conter detalhes sobre diferentes veículos. |

| Itens                                                                                                                                                                                        |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| São as entidades individuais dentro das tabelas. Cada item representa uma única entidade de dados, como uma pessoa específica na tabela "Pessoas" ou um carro específico na tabela "Carros". |

| Atributos                                                                                                                                                                                                                                                    |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| São os componentes individuais de dados que compõem um item. Por exemplo, em um item da tabela "Pessoas", os atributos podem incluir PersonID (ID da pessoa), LastName (Sobrenome), FirstName (Nome), etc. Cada atributo é uma unidade de dados indivisível. |

#### <mark style="color:blue;">**Por que usar Amazon DynamoDB**</mark>

| Alta Performance                                                                                  | Flexibilidade                                                                                                                              | Gerenciamento Simplificado                                                                                                                                                  |
| ------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Oferece acesso rápido e escalabilidade automática para atender a grandes volumes de solicitações. | Suporta estruturas de dados dinâmicas com esquemas flexíveis, permitindo adicionar ou modificar atributos sem alterar o esquema da tabela. | Totalmente gerenciado pela AWS, elimina a necessidade de provisionamento de infraestrutura, replicação de dados e gerenciamento de clusters, reduzindo a carga operacional. |

#### <mark style="color:blue;">**Casos de Uso**</mark>

| Aplicações Web Escaláveis                                                                                                            | Gerenciamento de Sessões                                                                                       |
| ------------------------------------------------------------------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------- |
| Ideal para armazenar perfis de usuário, sessões e dados de configuração em aplicações que requerem rápida escalabilidade horizontal. |  Armazenamento de sessões de usuário para aplicações web para garantir consistência e rápido acesso aos dados. |

O Amazon DynamoDB é uma escolha poderosa para aplicações que exigem alta disponibilidade, escalabilidade automática e gerenciamento simplificado de dados NoSQL na nuvem.

***

### <mark style="color:red;">**Segurança do Amazon DynamoDB**</mark>

O Amazon DynamoDB prioriza a segurança dos dados através da criptografia em repouso, reduzindo a complexidade e os desafios operacionais associados à proteção de informações sensíveis. Essa medida garante que os dados armazenados permaneçam seguros contra acesso não autorizado, proporcionando tranquilidade aos usuários quanto à integridade e confidencialidade de seus dados.

#### <mark style="color:blue;">**Por que usar criptografia em repouso no Amazon DynamoDB**</mark>

| Proteção Avançada de Dados                                                                                                                           | Simplicidade Operacional                                                                                                                                                                           |
| ---------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| A criptografia em repouso protege os dados armazenados contra ameaças internas e externas, garantindo conformidade com regulamentações de segurança. | Elimina a necessidade de implementar e gerenciar soluções de criptografia complexas, permitindo que os desenvolvedores foquem na criação de aplicações sem se preocupar com a segurança dos dados. |

#### <mark style="color:blue;">**Casos de Uso**</mark>

| Aplicações de Saúde e Finanças                                                                                                                | Armazenamento de Dados Sensíveis                                                                                                            |
| --------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------- |
| Ideal para proteger informações críticas de pacientes e dados financeiros, assegurando conformidade com regulamentações como HIPAA e PCI DSS. | Utilizado em ambientes que exigem proteção robusta de dados confidenciais, como informações de identidade pessoal e detalhes de transações. |

A criptografia em repouso no Amazon DynamoDB não só fortalece a segurança dos dados como também simplifica a conformidade regulatória e operacional, sendo uma escolha essencial para aplicações que priorizam a proteção e a privacidade dos dados.

[Criptografia do DynamoDB em repouso(opens in a new tab)](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/EncryptionAtRest.html).

***

## **Recursos**

[Introdução ao Amazon DynamoDB](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/Introduction.html)

***
