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

{% tab title="Familiaridade e Suporte" %}
Os bancos de dados relacionais são amplamente adotados desde os anos 70, o que resulta em uma grande base de conhecimento e suporte técnico disponível. Profissionais frequentemente possuem experiência prévia, facilitando o desenvolvimento e a manutenção de sistemas.
{% endtab %}

{% tab title="Integridade e Confiabilidade" %}
Garantem que os dados sejam mantidos com alta integridade, seguindo os princípios ACID (Atomicidade, Consistência, Isolamento, Durabilidade). Isso assegura que as transações sejam processadas de forma segura e confiável, sem comprometer a precisão dos dados.
{% endtab %}
{% endtabs %}

**Por que usar um Banco de Dados Relacional?**

| Aplicações Transacionais                                                                                               | Sistemas de Gestão de Conteúdo                                                                                                     | Análise de Negócios                                                                                                                          | Segurança e Conformidade                                                                                                       |
| ---------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------ |
| Ideais para sistemas que exigem transações seguras e consistentes, como processamento de pedidos e sistemas bancários. | Eficientes para armazenar e recuperar grandes volumes de dados estruturados, como informações de clientes e históricos de compras. | Facilitam análises complexas ao permitir consultas detalhadas que abrangem múltiplas tabelas, essenciais para tomadas de decisão informadas. | Oferecem recursos robustos para controle de acesso e auditoria, garantindo conformidade com regulamentos de proteção de dados. |

Em resumo, os bancos de dados relacionais são essenciais para organizações que valorizam a integridade, confiabilidade e eficiência na gestão de seus dados. Eles não apenas simplificam o desenvolvimento e manutenção de sistemas, mas também proporcionam uma base sólida para operações críticas e análises estratégicas.

***
