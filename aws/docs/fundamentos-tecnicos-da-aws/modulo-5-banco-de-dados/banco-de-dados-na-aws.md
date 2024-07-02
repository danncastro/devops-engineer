# Banco de dados na AWS

***

## <mark style="color:red;">Histórico por trás de bancos de dados corporativos</mark>

Antigamente, escolher um banco de dados era uma decisão simples. Os clientes tinham apenas algumas opções disponíveis e, após considerar alguns fornecedores, acabavam escolhendo um para todas as suas aplicações. Geralmente, as empresas optavam por uma tecnologia de banco de dados sem uma compreensão completa de seu caso de uso específico. Desde os anos 70, o tipo de banco de dados mais popular entre as empresas tem sido o banco de dados relacional.

#### <mark style="color:blue;">**Evolução dos Bancos de Dados Corporativos**</mark>

Nos últimos anos, a paisagem dos bancos de dados corporativos mudou significativamente. Com o avanço da tecnologia e o aumento da diversidade nas necessidades de dados, as empresas agora têm uma variedade muito maior de opções de bancos de dados para escolher. Essas opções incluem bancos de dados relacionais tradicionais, bancos de dados NoSQL que oferecem flexibilidade para dados não estruturados e semi-estruturados, além de soluções específicas para dados em tempo real e análise de big data.

#### <mark style="color:blue;">**Decisões Baseadas no Caso de Uso**</mark>

Atualmente, as empresas estão cada vez mais optando por tecnologias de banco de dados que são mais adequadas para o seu caso de uso específico. Em vez de adotar uma abordagem de tamanho único, elas avaliam cuidadosamente os requisitos de suas aplicações, considerando fatores como escalabilidade, desempenho, necessidades de consulta e integração com outras ferramentas e sistemas. Isso tem levado a um ambiente mais diversificado e adaptável no campo dos bancos de dados corporativos.

<mark style="color:blue;">**Importância da Escolha Certa**</mark>

Escolher o banco de dados correto é crucial para o sucesso das operações de uma empresa. Uma decisão adequada pode melhorar significativamente a eficiência, reduzir custos e permitir inovação em áreas como análise de dados, experiência do usuário e suporte a novas iniciativas tecnológicas. Portanto, entender profundamente o caso de uso e considerar todas as opções disponíveis é essencial para tomar uma decisão informada e estratégica em relação aos bancos de dados corporativos.

***

## <mark style="color:red;">Bancos de dados relacionais</mark>

Bancos de dados relacionais são estruturados para organizar dados em tabelas, onde cada tabela contém informações relacionadas entre si, utilizando o conceito de "relacional".

#### <mark style="color:blue;">**Estrutura de um Banco de Dados Relacional**</mark>

Um banco de dados relacional organiza dados em tabelas, onde cada tabela é composta por linhas (registros) e colunas (atributos). Cada linha representa uma entrada específica e cada coluna descreve um atributo dessa entrada. Por exemplo, em um banco de dados relacional para livros, pode-se ter uma tabela para livros, outra para vendas e uma terceira para autores.

#### <mark style="color:blue;">**Exemplo de Estrutura**</mark>

Na tabela de livros, cada linha pode conter o ISBN, título, autor e formato do livro, cada um em sua própria coluna. A tabela de livros compartilha um atributo com as outras tabelas, como o autor, criando um relacionamento entre elas.

<figure><img src="../../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>

#### <mark style="color:blue;">**Esquema Lógico**</mark>

O conjunto de tabelas, suas colunas e os relacionamentos entre elas formam o esquema lógico do banco de dados relacional. Este esquema é fixo no momento em que o banco de dados é criado e operacionalizado. Mudanças significativas no esquema, como adicionar novas tabelas ou modificar relacionamentos existentes, geralmente requerem planejamento prévio e podem ser complexas de implementar após o banco de dados estar em uso.

#### <mark style="color:blue;">**Importância do Planejamento do Esquema**</mark>

Com bancos de dados relacionais, o design do esquema é crucial, pois define como os dados serão armazenados, acessados e relacionados ao longo do tempo. A modelagem de dados deve ser cuidadosamente planejada antes da implementação do banco de dados, para garantir que atenda aos requisitos atuais e futuros da aplicação.

Bancos de dados relacionais são fundamentais para muitas aplicações devido à sua estrutura organizada e capacidade de gerenciar relacionamentos complexos entre dados. A rigidez do esquema lógico requer uma abordagem cuidadosa durante o design inicial para evitar complicações e garantir a eficiência operacional do banco de dados ao longo do tempo.

***

### <mark style="color:red;">Sistema de gerenciamento de banco de dados relacional</mark>

Um Sistema de Gerenciamento de Banco de Dados Relacional (RDBMS) facilita a criação, atualização e administração de bancos de dados estruturados. Exemplos populares incluem MySQL, PostgreSQL, Oracle, SQL Server e Amazon Aurora.&#x20;

Esses sistemas permitem aos usuários interagir utilizando SQL (Structured Query Language), como exemplificado na consulta a seguir:

#### <mark style="color:blue;">**Funcionamento do RDBMS**</mark>

Os RDBMS são acessados e manipulados usando consultas na Linguagem de Consulta Estruturada (SQL). Um exemplo básico de consulta SQL é:

```sql
SELECT * FROM table_name;
```

Essa consulta seleciona todos os dados de uma tabela específica. No entanto, a verdadeira potência das consultas SQL reside na capacidade de criar consultas complexas que permitem extrair informações de várias tabelas simultaneamente para analisar padrões e responder a desafios de negócios específicos.

#### <mark style="color:blue;">**Por que usar um RDBMS?**</mark>

{% tabs %}
{% tab title="Estruturação de Dados" %}
RDBMS permite estruturar os dados de forma coesa, organizando informações em tabelas com relações claras entre elas (chaves primárias e estrangeiras).
{% endtab %}

{% tab title="Integridade dos Dados" %}
Garante consistência e integridade dos dados através de restrições como chaves estrangeiras e regras de validação.
{% endtab %}

{% tab title="Escalabilidade" %}
Capacidade de lidar com grandes volumes de dados e suportar múltiplos usuários simultaneamente, mantendo o desempenho.
{% endtab %}
{% endtabs %}

{% tabs %}
{% tab title="Segurança" %}
Controle de acesso aos dados com permissões granulares, garantindo que apenas usuários autorizados possam visualizar ou modificar informações sensíveis.
{% endtab %}

{% tab title="Recursos Avançados de Consulta" %}
Possibilita a execução de consultas complexas, incluindo junções (joins), agregações e subconsultas, essenciais para análises de negócios sofisticadas.
{% endtab %}

{% tab title="Compatibilidade com Padrões" %}
SQL é um padrão amplamente aceito, garantindo portabilidade entre diferentes sistemas RDBMS e facilitando a migração de dados.
{% endtab %}
{% endtabs %}

#### <mark style="color:blue;">**Casos de Uso**</mark>

| Aplicações Web                                                                  | Análise de Dados                                                                                                                 | Sistemas de Gerenciamento de Conteúdo                                                          | Sistemas de Suporte a Decisão                                                            |
| ------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------- |
| Para armazenamento de dados de usuários, conteúdo dinâmico e transações online. | Suporta operações complexas para análise de grandes conjuntos de dados, como em empresas de e-commerce para previsões de vendas. | Armazenamento e recuperação eficientes de conteúdo digital, como imagens, vídeos e documentos. | Utilização de consultas SQL para extrair insights que orientem estratégias empresariais. |

Em resumo, um RDBMS é essencial para organizações que dependem de dados estruturados e precisam de uma plataforma robusta para armazenamento, consulta e análise eficiente de informações críticas.

***

### <mark style="color:red;">Benefícios de banco de dados relacional</mark>

Os bancos de dados relacionais oferecem uma série de vantagens significativas:

{% tabs %}
{% tab title="Junções Eficientes" %}
Permitem combinar dados de várias tabelas, facilitando a compreensão dos relacionamentos entre os dados. Por exemplo, ao analisar vendas junto com informações de clientes para insights mais profundos.
{% endtab %}

{% tab title="Redução de Redundância" %}
Minimiza a duplicação de dados ao permitir que informações sejam armazenadas uma vez e referenciadas em várias tabelas. Isso melhora a consistência dos dados e economiza espaço de armazenamento.
{% endtab %}
{% endtabs %}

{% tabs %}
{% tab title="Familiaridade e Suporte" %}
Os bancos de dados relacionais são amplamente adotados desde os anos 70, o que resulta em uma grande base de conhecimento e suporte técnico disponível. Profissionais frequentemente possuem experiência prévia, facilitando o desenvolvimento e a manutenção de sistemas.
{% endtab %}

{% tab title="Integridade e Confiabilidade" %}
Garantem que os dados sejam mantidos com alta integridade, seguindo os princípios ACID (Atomicidade, Consistência, Isolamento, Durabilidade). Isso assegura que as transações sejam processadas de forma segura e confiável, sem comprometer a precisão dos dados.
{% endtab %}
{% endtabs %}

#### <mark style="color:blue;">**Por que usar um Banco de Dados Relacional?**</mark>

| Aplicações Transacionais                                                                                               | Sistemas de Gestão de Conteúdo                                                                                                     |
| ---------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------- |
| Ideais para sistemas que exigem transações seguras e consistentes, como processamento de pedidos e sistemas bancários. | Eficientes para armazenar e recuperar grandes volumes de dados estruturados, como informações de clientes e históricos de compras. |

| Análise de Negócios                                                                                                                          | Segurança e Conformidade                                                                                                       |
| -------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------ |
| Facilitam análises complexas ao permitir consultas detalhadas que abrangem múltiplas tabelas, essenciais para tomadas de decisão informadas. | Oferecem recursos robustos para controle de acesso e auditoria, garantindo conformidade com regulamentos de proteção de dados. |

Em resumo, os bancos de dados relacionais são essenciais para organizações que valorizam a integridade, confiabilidade e eficiência na gestão de seus dados. Eles não apenas simplificam o desenvolvimento e manutenção de sistemas, mas também proporcionam uma base sólida para operações críticas e análises estratégicas.

***

### <mark style="color:red;">Casos de uso de banco de dados relacional</mark>

Os bancos de dados relacionais são fundamentais em muitas aplicações críticas e têm uma ampla gama de usos significativos no mundo moderno. Aqui estão alguns cenários comuns em que eles são essenciais:

{% tabs %}
{% tab title="Estabilidade e Consistência" %}
São ideais para aplicações com estruturas de dados estáveis e que exigem armazenamento persistente seguro. Isso inclui migrações de sistemas on-premises para a nuvem, onde a estrutura de dados permanece praticamente inalterada.
{% endtab %}

{% tab title="Aplicações Críticas que Demandam ACID" %}
São essenciais em cenários que requerem conformidade com os princípios ACID, como:

**Planejamento de Recursos Empresariais (ERP)**: Para gerenciar recursos corporativos, como finanças, inventário e recursos humanos, garantindo integridade e consistência dos dados.

**Sistemas de Gerenciamento de Relacionamento com o Cliente (CRM)**: Para manter registros precisos e acessíveis de interações com clientes, suportando transações complexas e relatórios detalhados.

**Aplicações Financeiras e Comerciais**: Para processamento de transações seguras e confiáveis, onde a precisão dos dados é crucial para decisões empresariais e conformidade regulatória.
{% endtab %}
{% endtabs %}

#### <mark style="color:blue;">**Por que usar Bancos de Dados Relacionais?**</mark>

| Segurança e Conformidade                                                                                                          | Desempenho e Escalabilidade                                                                                                          |
| --------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------ |
| Garantem a integridade dos dados e oferecem robustos controles de segurança, essenciais para aplicações financeiras e comerciais. | São capazes de lidar com grandes volumes de dados e suportar múltiplos usuários simultaneamente, mantendo um desempenho consistente. |

| Suporte a Transações Complexas                                                                                             | Compatibilidade e Suporte                                                                                                          |
| -------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------- |
| Permitem operações complexas e consultas detalhadas, necessárias para análises de dados avançadas e relatórios gerenciais. | Amplamente adotados e suportados, facilitando a integração com outras tecnologias e a migração de dados entre diferentes sistemas. |

Em resumo, os bancos de dados relacionais são a escolha preferida para aplicações empresariais que exigem consistência, segurança e confiabilidade. Eles fornecem uma base sólida para o armazenamento e manipulação de dados críticos, essenciais para o funcionamento eficiente e seguro de sistemas empresariais essenciais.

***

## <mark style="color:red;">Escolha entre bancos de dados não gerenciados e gerenciados</mark>

Ao decidir entre bancos de dados gerenciados e não gerenciados na AWS para executar um banco de dados relacional, é crucial entender as diferenças e considerações envolvidas.

#### <mark style="color:blue;">**Bancos de Dados Gerenciados vs. Não Gerenciados na AWS**</mark>

Ao optar por um banco de dados relacional na AWS, você enfrentará a escolha entre um serviço gerenciado e um não gerenciado. Essa decisão reflete um equilíbrio entre conveniência e controle, semelhante ao modelo de responsabilidade compartilhada da AWS, onde as responsabilidades de segurança são divididas entre o provedor de serviços (AWS) e o cliente.

#### <mark style="color:blue;">**Benefícios e Considerações**</mark>

| Serviços Gerenciados                                                                                                                                                                                                | Serviços Não Gerenciados                                                                                                                                                                                                                       |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <mark style="color:purple;">**Conveniência**</mark>**:** Ideal para equipes que valorizam a automação de tarefas operacionais, como backup, patching e escalabilidade automática.                                   | <mark style="color:purple;">**Controle Total:**</mark> Oferece maior controle sobre configurações e personalizações específicas do banco de dados, adequado para cenários que exigem ajustes finos ou integração com infraestrutura existente. |
| <mark style="color:purple;">**Menor Overhead:**</mark> Reduz a carga de trabalho operacional, permitindo que equipes se concentrem mais no desenvolvimento de aplicativos e menos na manutenção do banco de dados.  | <mark style="color:purple;">**Flexibilidade:**</mark> Permite adaptar o ambiente de banco de dados às necessidades específicas da aplicação ou da empresa.                                                                                     |
| <mark style="color:purple;">**Exemplos de Uso:**</mark> Recomendado para aplicações críticas, como sistemas de comércio eletrônico, onde alta disponibilidade e gerenciamento eficiente de recursos são essenciais. | <mark style="color:purple;">**Exemplos de Uso:**</mark> Útil para aplicações que requerem configurações personalizadas ou integrações complexas, como sistemas legados ou ambientes de pesquisa.                                               |

#### <mark style="color:blue;">**Por que escolher um Banco de Dados Gerenciado**</mark>

| Economia de Tempo e Recursos                                                                                      | Escalabilidade e Disponibilidade                                                                                        | Segurança e Conformidade                                                                                                 |
| ----------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------ |
| Automatiza tarefas operacionais rotineiras, liberando equipes para se concentrarem em inovação e desenvolvimento. | Garante alta disponibilidade e dimensionamento automático, fundamental para aplicações com demandas variáveis de carga. | Oferece configurações de segurança padronizadas e gerenciamento de patches, mantendo a conformidade com regulamentações. |

#### <mark style="color:blue;">**Casos de Uso**</mark>

| Aplicações Web e Mobile                                                                                                | Sistemas de Análise de Dados                                                                    |
| ---------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- |
| Beneficiam-se da escalabilidade automática e gerenciamento simplificado, suportando picos de tráfego sem interrupções. | Aproveitam a capacidade de processar grandes volumes de dados de maneira eficiente e escalável. |

Em resumo, a escolha entre bancos de dados gerenciados e não gerenciados na AWS depende das necessidades específicas da aplicação, da importância de automação e da complexidade operacional desejada. Cada abordagem oferece benefícios distintos, permitindo que você otimize o desempenho e a gestão dos seus dados conforme suas prioridades empresariais e técnicas.

***

### <mark style="color:red;">**Banco de dados on-premises**</mark>

Se você opera um banco de dados relacional on-premises (em seu próprio datacenter), assume total responsabilidade por todos os aspectos da operação. Isso inclui desde a segurança física e elétrica do datacenter até o gerenciamento da infraestrutura da máquina hospedeira, administração do banco de dados, otimização de consultas e gestão dos dados dos clientes. Esse nível de responsabilidade proporciona um controle absoluto sobre todos os aspectos operacionais.

#### <mark style="color:blue;">**Benefícios e Considerações**</mark>

| Controle Total                                                                                                                                                                                                     | Segurança Personalizada                                                                                                                            | Custos e Investimentos                                                                                                                                                                                      |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Gerenciar um banco de dados on-premises oferece controle direto sobre todos os aspectos da infraestrutura e operação do banco de dados. Isso é crucial para empresas que exigem máxima personalização e segurança. | Permite implementar medidas de segurança específicas adaptadas às necessidades da empresa, garantindo conformidade e proteção dos dados sensíveis. | Implica em investimentos significativos em infraestrutura, manutenção e atualizações contínuas. Os custos operacionais podem ser altos, especialmente para garantir alta disponibilidade e backup adequado. |

#### <mark style="color:blue;">**Por que escolher um Banco de Dados On-Premises**</mark>

| Segurança e Conformidade                                                                                                                              | Personalização Extrema                                                                                                        |
| ----------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------- |
| Ideal para setores regulamentados que exigem controle total sobre a localização física dos dados e implementação de políticas de segurança rigorosas. | Útil para aplicações que necessitam de configurações altamente personalizadas ou integração profunda com sistemas existentes. |

#### <mark style="color:blue;">**Casos de Uso**</mark>

| Governo e Setores Regulamentados                                                                                      | Aplicações Críticas para o Negócio                                                                                                                                 |
| --------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Onde a privacidade e a conformidade regulatória são essenciais, exigindo controle total sobre a infraestrutura de TI. | Como sistemas financeiros ou de saúde, que demandam altos níveis de segurança e disponibilidade, com requisitos específicos de desempenho e integridade dos dados. |

Em resumo, a escolha de um banco de dados on-premises oferece controle total e personalização, mas vem com o ônus de altos custos operacionais e responsabilidade integral pela gestão da infraestrutura. É adequado para organizações que valorizam o controle direto sobre seus dados e estão preparadas para investir recursos significativos em sua manutenção e segurança.

***

### <mark style="color:red;">**Banco de dados não gerenciado**</mark>

<figure><img src="../../.gitbook/assets/image (62).png" alt=""><figcaption></figcaption></figure>

Se você optar por hospedar seu banco de dados relacional no Amazon EC2, estará escolhendo uma opção não gerenciada. Nesse cenário, a AWS assume a responsabilidade pela implementação e manutenção da infraestrutura física, incluindo hardware e sistema operacional das instâncias do EC2. No entanto, você continua responsável por gerenciar a instância do EC2, administrar o banco de dados hospedado nessa instância, otimizar consultas e gerenciar os dados dos clientes.

#### <mark style="color:blue;">**Benefícios e Considerações**</mark>

| Flexibilidade de Configuração                                                                                                  | Controle Operacional                                                                                                       | Responsabilidade Compartilhada                                                                                         |
| ------------------------------------------------------------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------- |
| Permite ajustar a configuração da instância do EC2 e do banco de dados de acordo com as necessidades específicas da aplicação. | Você mantém controle total sobre o gerenciamento do banco de dados, incluindo otimizações de desempenho e personalizações. | A AWS cuida da camada física e de infraestrutura, enquanto você se concentra na administração do software e dos dados. |

#### <mark style="color:blue;">**Por que escolher um Banco de Dados não Gerenciado**</mark>

| Personalização Avançada                                                                                                        | Controle de Custos                                                                                                        |
| ------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------- |
| Útil para aplicações que requerem ajustes precisos de configuração e desempenho, adaptados às demandas específicas do negócio. | Pode ser mais econômico para cargas de trabalho previsíveis e estáveis, permitindo otimizar recursos conforme necessário. |

#### <mark style="color:blue;">**Casos de Uso**</mark>

| Aplicações com Requisitos Específicos de Performance                                           | Ambientes de Desenvolvimento e Teste                                  |
| ---------------------------------------------------------------------------------------------- | --------------------------------------------------------------------- |
| Como plataformas de jogos online que precisam de latência mínima e escalabilidade instantânea. | Onde a flexibilidade de configuração e custo efetivo são prioridades. |

Em resumo, optar por um banco de dados não gerenciado no Amazon EC2 oferece flexibilidade e controle operacional, permitindo personalização avançada e ajustes específicos de desempenho. É ideal para organizações que têm a capacidade e a necessidade de gerenciar diretamente sua infraestrutura de banco de dados, aproveitando ao máximo as vantagens da computação em nuvem com responsabilidade compartilhada.

***

### <mark style="color:red;">**Banco de dados gerenciado**</mark>

<figure><img src="../../.gitbook/assets/image (63).png" alt=""><figcaption></figcaption></figure>

Optar por um serviço de banco de dados gerenciado na AWS oferece uma solução conveniente para hospedar seu banco de dados relacional. Esses serviços configuram e gerenciam tanto a instância do EC2 quanto o banco de dados, fornecendo recursos como alta disponibilidade, escalabilidade automática, aplicação de patches e backups.

#### <mark style="color:blue;">**Benefícios e Considerações**</mark>

| Conveniência Operacional                                                                                                           | Automatização de Tarefas                                                                                                           | Segurança e Conformidade                                                                                                                            |
| ---------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------- |
| Elimina a necessidade de gerenciar a infraestrutura física e operacional, permitindo foco maior no desenvolvimento de aplicativos. | Inclui configurações automáticas para alta disponibilidade e escalabilidade, bem como rotinas automáticas de backup e atualização. | Garante práticas de segurança padrão e conformidade regulatória, enquanto você mantém o controle sobre ajustes de desempenho e segurança dos dados. |

#### <mark style="color:blue;">**Por que escolher um Banco de Dados Gerenciado**</mark>

| Redução de Overhead Operacional                                                                                  | Escalabilidade Simplificada                                                                             |
| ---------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- |
| Ideal para equipes que buscam reduzir a carga operacional, aproveitando automações robustas fornecidas pela AWS. | Suporta crescimento rápido e flutuações na demanda sem necessidade de intervenção manual significativa. |

#### <mark style="color:blue;">**Casos de Uso**</mark>

| Aplicações Web de Alto Tráfego                                                                                | Aplicações SaaS (Software as a Service)                                                                 |
| ------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- |
| Como plataformas de e-commerce que exigem escalabilidade automática para lidar com picos sazonais de tráfego. | Onde a segurança e a confiabilidade do banco de dados são críticas para manter a satisfação do cliente. |

Em resumo, um banco de dados gerenciado na AWS proporciona conveniência ao automatizar tarefas operacionais complexas, enquanto ainda oferece controle sobre configurações de desempenho e segurança. É uma escolha eficiente para empresas que valorizam a simplicidade operacional e a escalabilidade, permitindo foco nos objetivos de negócio em vez da infraestrutura de TI.

***

## **Recursos**&#x20;

[O que é um banco de dados relacional?(opens in a new tab)](https://aws.amazon.com/relational-database/)

[Bancos de dados na AWS](https://aws.amazon.com/products/databases/)

***
