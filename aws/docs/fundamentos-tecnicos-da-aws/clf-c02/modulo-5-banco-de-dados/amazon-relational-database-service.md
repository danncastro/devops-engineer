# Amazon Relational Database Service

***

## <mark style="color:red;">Amazon RDS</mark>

O Amazon Relational Database Service (Amazon RDS) simplifica a criação e gestão de bancos de dados relacionais na nuvem, liberando os clientes das tarefas operacionais tradicionais. Por exemplo, se você é um vendedor de equipamentos de saúde no Noroeste do Pacífico e deseja se destacar no mercado, ter um banco de dados é essencial, mas administrá-lo diretamente pode ser um fardo.

O Amazon RDS permite concentrar-se nas atividades que realmente diferenciam sua aplicação, ao mesmo tempo que cuida de tarefas como provisionamento, aplicação de patches, escalabilidade e backups. Ele suporta uma variedade de sistemas de gerenciamento de banco de dados, incluindo opções comerciais como Oracle e SQL Server, soluções de código aberto como MySQL, PostgreSQL e MariaDB, além do nativo da nuvem Amazon Aurora.

<figure><img src="../../../.gitbook/assets/image (64).png" alt=""><figcaption></figcaption></figure>

#### <mark style="color:blue;">**Benefícios do Amazon RDS**</mark>

| Simplicidade Operacional                                                                                               | Flexibilidade de Escolha                                                                                                                                                                           | Confiabilidade e Escalabilidade                                                                                            |
| ---------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------- |
| Reduz a complexidade ao automatizar tarefas operacionais, permitindo que equipes foquem em desenvolvimento e inovação. | Oferece uma gama de opções de banco de dados, incluindo o Amazon Aurora, que proporciona maior durabilidade, disponibilidade e desempenho comparado às versões tradicionais do MySQL e PostgreSQL. | Garante alta disponibilidade e escalabilidade automática para lidar com demandas variáveis de tráfego e carga de trabalho. |

#### <mark style="color:blue;">**Por que usar Amazon RDS**</mark>

| Economia de Tempo e Recursos                                                                           | Alta Disponibilidade e Segurança                                                                                               |
| ------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------ |
| Elimina a necessidade de gerenciar infraestrutura física e operacional, reduzindo custos operacionais. | Oferece recursos avançados de segurança e backup, essenciais para proteger dados críticos e garantir continuidade de negócios. |

#### <mark style="color:blue;">**Casos de Uso**</mark>

| Aplicações de E-commerce                                                                               | Sistemas de Gerenciamento de Conteúdo                                     |
| ------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------- |
| Para suportar transações rápidas e confiáveis, mantendo alta disponibilidade durante picos de tráfego. | Para armazenar e recuperar conteúdo digital de maneira eficiente e segura |

Em resumo, o Amazon RDS é uma escolha ideal para empresas que buscam aproveitar os benefícios da computação em nuvem sem comprometer a segurança, a escalabilidade e a eficiência operacional de seus bancos de dados relacionais.

***

### <mark style="color:red;">**Instâncias de banco de dados**</mark>

O Amazon RDS utiliza instâncias de banco de dados para executar os diferentes mecanismos de banco de dados oferecidos. Cada instância de banco de dados é configurada com recursos de computação e armazenamento específicos, dependendo do tipo e do tamanho escolhidos. Essas instâncias são gerenciadas através do console do Amazon RDS, não do Amazon EC2 diretamente.

#### <mark style="color:blue;">**Características das Instâncias de Banco de Dados**</mark>

| Tipos de Instância Disponíveis                                                                                                                                                                        | Armazenamento                                                                                                                                                                             |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <mark style="color:purple;">**Standard (Padrão):**</mark> Para cargas de trabalho gerais.                                                                                                             | Utiliza volumes do Amazon Elastic Block Store (EBS), disponíveis em tipos como SSD de uso geral, SSD com IOPS provisionadas e armazenamento magnético (não recomendado para uso crítico). |
| <mark style="color:purple;">**Memory Optimized (Memória otimizada):**</mark> Otimizadas para aplicações que exigem alta capacidade de memória.                                                        |                                                                                                                                                                                           |
| <mark style="color:purple;">**Burstable Performance (Performance com capacidade de intermitência)**</mark>**:** Oferece um nível de desempenho básico com a capacidade de aumentar para picos de uso. |                                                                                                                                                                                           |

<figure><img src="../../../.gitbook/assets/image (65).png" alt=""><figcaption></figcaption></figure>

#### <mark style="color:blue;">**Por que usar Instâncias de Banco de Dados no Amazon RDS**</mark>

| Flexibilidade de Configuração                                                                              | Gerenciamento Simplificado                                                                                                                        |
| ---------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------- |
| Permite ajustar recursos de computação e armazenamento conforme as necessidades específicas do aplicativo. | Automatiza tarefas operacionais como backup, patching e escalabilidade, liberando equipes para se concentrarem no desenvolvimento de aplicativos. |

#### <mark style="color:blue;">**Casos de Uso**</mark>

| Aplicações Web Escaláveis                                                                  | Ambientes de Desenvolvimento e Teste                                                                      |
| ------------------------------------------------------------------------------------------ | --------------------------------------------------------------------------------------------------------- |
| Utilizam instâncias Memory Optimized para suportar grandes volumes de dados em tempo real. | Aproveitam instâncias Standard para flexibilidade e economia de custos durante ciclos de desenvolvimento. |

<figure><img src="../../../.gitbook/assets/image (66).png" alt=""><figcaption></figcaption></figure>

Em resumo, as instâncias de banco de dados no Amazon RDS oferecem uma maneira flexível e gerenciada de implantar e escalar bancos de dados relacionais na nuvem. São ideais para empresas que buscam simplicidade operacional e alto desempenho, sem comprometer a segurança e a confiabilidade dos dados.

***

### <mark style="color:red;">Amazon RDS em uma Amazon Virtual Private Cloud</mark>

Ao configurar uma instância de banco de dados no Amazon RDS, você escolhe uma Amazon Virtual Private Cloud (VPC) para hospedar seus dados. Dentro dessa VPC, você define um grupo de sub-redes específicas onde as instâncias de banco de dados serão colocadas. Essas sub-redes são associadas a zonas de disponibilidade (AZs), garantindo alta disponibilidade e redundância.

#### <mark style="color:blue;">**Configuração na Amazon RDS em uma Amazon VPC**</mark>

| Grupo de Sub-Redes de Banco de Dados                                                                                                   | Controles de Segurança Avançados                                                                                                     |
| -------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------ |
| Seleciona as AZs que incluem as sub-redes para suas instâncias de banco de dados.                                                      | Utiliza listas de controle de acesso à rede (Network ACLs) e grupos de segurança para controlar o tráfego de rede de forma granular. |
| Escolhe sub-redes privadas sem rota para gateway da Internet, assegurando acesso restrito aos dados apenas pelo back-end da aplicação. | Estabelece firewalls que garantem que somente as instâncias de back-end autorizadas possam acessar o banco de dados.                 |

#### <mark style="color:blue;">**Por que usar Amazon RDS em uma Amazon VPC**</mark>

| Segurança Reforçada                                                                                                                                     | Alta Disponibilidade e Redundância                                                                                                                                 |
| ------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| A segregação em uma VPC com sub-redes privadas e controles de segurança garante que apenas componentes autorizados possam acessar seus dados sensíveis. | Distribui instâncias de banco de dados em múltiplas zonas de disponibilidade para proteção contra falhas de infraestrutura e garantia de continuidade operacional. |

#### <mark style="color:blue;">**Casos de Uso**</mark>

| Aplicações de Saúde e Finanças                                                                                             | Sistemas de Gestão de Conteúdo                                                             |
| -------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------ |
| Onde a conformidade regulatória e a proteção de dados são críticas, exigindo acesso restrito e seguro aos bancos de dados. | Para armazenamento seguro e gerenciamento eficiente de grandes volumes de dados sensíveis. |

Em resumo, configurar o Amazon RDS em uma Amazon VPC proporciona um ambiente altamente controlado e seguro para hospedar bancos de dados na nuvem. É ideal para organizações que valorizam segurança rigorosa, alta disponibilidade e escalabilidade, mantendo a conformidade com regulamentações específicas do setor.

***

### <mark style="color:red;">Proteger Amazon RDS com AWS Identity and Access Management (IAM)</mark>

Proteger seu Amazon RDS com AWS Identity and Access Management (IAM) envolve o uso de políticas IAM para controlar quem pode acessar quais recursos e realizar quais ações. Além das Network ACLs e grupos de segurança que gerenciam o tráfego de rede, as políticas IAM oferecem uma camada adicional de controle sobre permissões específicas.

#### <mark style="color:blue;">**Benefícios do AWS IAM para Amazon RDS**</mark>

| Controle de Acesso Granular                                                                                            | Segurança Reforçada                                                                                                                              | Conformidade e Auditoria                                                                                               |
| ---------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------ | ---------------------------------------------------------------------------------------------------------------------- |
| Permite definir permissões detalhadas para usuários, grupos e funções, restringindo acesso a ações específicas no RDS. | Aumenta a segurança ao limitar quem pode modificar configurações, visualizar dados sensíveis ou realizar operações críticas nos bancos de dados. | Facilita a conformidade com regulamentos ao permitir auditorias detalhadas de acesso e atividades nos bancos de dados. |

#### <mark style="color:blue;">**Por que usar AWS IAM com Amazon RDS**</mark>

| Proteção de Dados Sensíveis                                                                                 | Gestão Eficiente de Acessos                                                                                            |
| ----------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------- |
| Ideal para ambientes que exigem proteção rigorosa de dados, como setores financeiro, saúde e governamental. | Simplifica a gestão de permissões, garantindo que apenas usuários autorizados possam interagir com os recursos do RDS. |

#### <mark style="color:blue;">**Casos de Uso**</mark>

| Aplicações de E-commerce                                                                                                                           | Ambientes de Desenvolvimento e Teste                                                                        |
| -------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------- |
| Para garantir que apenas administradores possam realizar alterações críticas nos bancos de dados, protegendo informações financeiras dos clientes. | Onde é crucial restringir acesso a dados de produção, mantendo a eficiência das equipes de desenvolvimento. |

Em resumo, implementar políticas IAM com Amazon RDS fortalece a segurança e o controle sobre acessos, promovendo a conformidade e a gestão eficiente de recursos na nuvem. É uma prática essencial para organizações que priorizam proteção robusta de dados e gerenciamento seguro de acessos.

***

### <mark style="color:red;">Fazer backup de dados</mark>

Para garantir a segurança e disponibilidade dos seus dados no Amazon RDS, é essencial realizar backups regulares. Existem duas principais opções para isso:

{% tabs %}
{% tab title="Backups Automáticos" %}
1. Ativados por padrão, os backups automáticos abrangem toda a instância de banco de dados e os logs de transações.
2. Você configura uma janela de backup durante períodos de baixa atividade para minimizar impactos no desempenho.
3. Os backups automáticos podem ser retidos por até 35 dias e permitem recuperação point-in-time, restaurando dados até um momento específico.
4. Ideal para garantir alta disponibilidade e recuperação rápida em caso de falhas ou erros de dados.

<figure><img src="../../../.gitbook/assets/image (67).png" alt=""><figcaption></figcaption></figure>
{% endtab %}

{% tab title="Snapshots Manuais:" %}
1. Oferecem flexibilidade para reter backups além dos 35 dias permitidos pelos backups automáticos.
2. Gerenciados através do console do Amazon RDS, esses snapshots são criados e mantidos por tempo indeterminado até você decidir excluí-los.
3. Úteis para atender requisitos de conformidade que exigem retenção prolongada de backups, como um ano ou mais.
4. Ao restaurar dados de um snapshot manual, você cria uma nova instância de banco de dados usando os dados capturados no snapshot.

<figure><img src="../../../.gitbook/assets/image (68).png" alt=""><figcaption></figcaption></figure>
{% endtab %}
{% endtabs %}

#### <mark style="color:blue;">**Por que usar ambas as opções**</mark>

| Redundância e Segurança                                                                                                                     | Conformidade e Longo Prazo                                                                                                                                                   |
| ------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Combinar backups automáticos e snapshots manuais garante redundância de dados, aumentando a segurança contra perda de informações críticas. | Os snapshots manuais são essenciais para atender a exigências de conformidade que requerem retenção prolongada de backups além do período suportado por backups automáticos. |

#### <mark style="color:blue;">**Casos de Uso**</mark>

| Aplicações Críticas                                                                           | Desenvolvimento e Teste                                                                                                       |
| --------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------- |
| Como sistemas financeiros e de saúde, onde a perda de dados pode ter impactos significativos. | Para criar ambientes de teste consistentes e restaurar rapidamente em caso de erros durante o desenvolvimento de aplicativos. |

Em resumo, a implementação combinada de backups automáticos e snapshots manuais no Amazon RDS oferece uma estratégia abrangente para proteger e recuperar seus dados. Essa abordagem assegura alta disponibilidade, conformidade regulatória e suporte eficaz a operações contínuas de TI.

***

### <mark style="color:red;">Redundância com o Amazon RDS Multi-AZ</mark>

O Amazon RDS Multi-AZ oferece redundância automática ao criar uma cópia secundária do seu banco de dados em uma zona de disponibilidade (AZ) adicional. Isso resulta em duas cópias do banco de dados: uma primária em uma sub-rede de uma AZ e uma em standby em outra AZ.

#### <mark style="color:blue;">**Funcionamento do Amazon RDS Multi-AZ**</mark>

| Redundância Automática                                                                                                                     | Melhoria na Disponibilidade                                                                                                                                                  | Failover Automático                                                                                                                                                                                    |
| ------------------------------------------------------------------------------------------------------------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Uma cópia primária é usada para consultas e exibição de dados, enquanto os dados são replicados de forma síncrona para a cópia em standby. | Garante que uma cópia do banco de dados esteja sempre em execução e pronta para assumir a função principal em caso de falhas, como perda de conectividade da cópia primária. | Em caso de falha da cópia primária, ocorre um failover automático para a cópia em standby. Isso é facilitado pelo uso de um nome DNS que redireciona as consultas para o novo banco de dados primário. |

#### <mark style="color:blue;">**Por que usar Amazon RDS Multi-AZ**</mark>

| Alta Disponibilidade                                                                                                    | Continuidade Operacional                                                                               |
| ----------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------ |
| Essencial para aplicações que não podem tolerar interrupções significativas, como sistemas financeiros e de e-commerce. | Assegura que seus serviços permaneçam operacionais mesmo diante de falhas de infraestrutura em uma AZ. |

#### <mark style="color:blue;">**Casos de Uso**</mark>

| Aplicações Críticas                                                              | Ambientes de Produção                                                                                    |
| -------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------- |
| Onde o tempo de inatividade é inaceitável, como plataformas de pagamento online. | Garante disponibilidade constante para suportar cargas de trabalho variáveis e imprevistos operacionais. |

Em resumo, o Amazon RDS Multi-AZ é uma solução recomendada para garantir alta disponibilidade e continuidade operacional dos bancos de dados na nuvem. Ao distribuir cópias do banco de dados em múltiplas zonas de disponibilidade, você reduz significativamente o risco de interrupções e mantém a integridade e acessibilidade dos dados críticos da sua aplicação.

***

## **Recursos**

[Trabalhando com backups(opens in a new tab)](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER\_WorkingWithAutomatedBackups.html)

[Backup e restauração do Amazon RDS(opens in a new tab)](https://aws.amazon.com/rds/details/backup/)

[Criação e uso de uma política do IAM para IAM Database Access(opens in a new tab)](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/UsingWithRDS.IAMDBAuth.IAMPolicy.html)

[Amazon Virtual Private Cloud VPCs e Amazon RDS](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER\_VPC.html)

***
