---
description: >-
  A AWS oferece uma gama diversificada de serviços de banco de dados projetados
  para atender a diferentes necessidades e casos de uso. Abaixo está um resumo
  dos principais serviços de banco de dados da
---

# Selecionar o serviço de banco de dados certo

***

A AWS oferece uma gama diversificada de serviços de banco de dados projetados para atender a diferentes necessidades e casos de uso. Abaixo está um resumo dos principais serviços de banco de dados da AWS:

## <mark style="color:red;">**Serviços de banco de dados da AWS**</mark>

<figure><img src="../../.gitbook/assets/image (69).png" alt=""><figcaption></figcaption></figure>

#### <mark style="color:blue;">**Por que usar serviços de banco de dados da AWS**</mark>

| Escalabilidade                                                                                                  | Gerenciamento Simplificado                                                                                     | Alta Disponibilidade                                                                                                        |
| --------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------- |
| Capacidade de dimensionar verticalmente e horizontalmente para lidar com demandas variáveis de tráfego e dados. | Reduz a carga operacional ao automatizar tarefas como provisionamento, backup, e manutenção de infraestrutura. | Oferece opções como replicação multi-AZ e failover automático para garantir disponibilidade contínua de dados e aplicações. |

#### <mark style="color:blue;">**Casos de Uso**</mark>

| Amazon RDS e Aurora                                                                                                      | Amazon DynamoDB                                                                                                                                      | Amazon Neptune                                                                                                     |
| ------------------------------------------------------------------------------------------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------ |
| Ideal para aplicações empresariais que exigem um banco de dados relacional robusto e escalável, como sistemas ERP e CRM. | Recomendado para aplicações que requerem acesso rápido e previsível a grandes volumes de dados, como sistemas de comércio eletrônico e jogos online. | Essencial para aplicações que dependem de estruturas de dados complexas, como redes sociais e detecção de fraudes. |

Cada serviço de banco de dados da AWS é projetado para oferecer desempenho otimizado e recursos específicos para suportar uma ampla variedade de cargas de trabalho, garantindo segurança, escalabilidade e confiabilidade para suas aplicações na nuvem.

***

### <mark style="color:red;">Decomposição de aplicações e bancos de dados</mark>

A medida que o setor evolui, tanto as aplicações quanto os bancos de dados passam por transformações significativas. Hoje, com o aumento do tamanho das aplicações, não é mais comum depender de um único banco de dados para oferecer suporte completo. Em vez disso, as aplicações são decompostas em serviços menores, cada um com seu próprio banco de dados específico. Essa abordagem substitui a ideia de um banco de dados "tamanho único" por uma estratégia de banco de dados complementar, onde cada banco de dados é projetado para fornecer funcionalidade, performance e escala adequadas para cargas de trabalho específicas.

#### <mark style="color:blue;">**Por que usar essa abordagem**</mark>

| Flexibilidade                                                                                                                                           | Escalabilidade                                                                                                                                | Resiliência                                                                                                                                   |
| ------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------- |
| Permite adaptar cada banco de dados para atender precisamente às necessidades da aplicação e da carga de trabalho, otimizando assim o desempenho geral. | Facilita o dimensionamento independente de cada serviço e banco de dados, respondendo dinamicamente às demandas variáveis de tráfego e dados. | Melhora a resiliência geral da aplicação, pois a falha em um serviço ou banco de dados específico não afeta necessariamente toda a aplicação. |

#### <mark style="color:blue;">**Casos de Uso**</mark>

| Microserviços                                                                                                                                                    |
| ---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Em arquiteturas baseadas em microserviços, cada serviço frequentemente possui seu próprio banco de dados, otimizado para a funcionalidade específica do serviço. |

| Aplicações distribuídas                                                                                                                                                                                |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Para aplicações distribuídas que processam grandes volumes de dados, a decomposição em serviços menores com bancos de dados especializados ajuda a gerenciar complexidade e melhorar a escalabilidade. |

| Modernização de aplicações legadas                                                                                                                                                                                       |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Ao migrar aplicações monolíticas para uma arquitetura mais distribuída, a decomposição em serviços menores com bancos de dados dedicados permite aproveitar melhor as vantagens da nuvem e da escalabilidade horizontal. |

Essa abordagem não apenas otimiza o desempenho e a eficiência operacional, mas também facilita a adoção de práticas modernas de desenvolvimento de software, como DevOps e Continuous Integration/Continuous Deployment (CI/CD), impulsionando a inovação e a agilidade organizacional.

***

## **Recursos**

[Bancos de dados na AWS(opens in a new tab)](https://aws.amazon.com/products/databases/)

[Blog de banco de dados da AWS(opens in a new tab)](https://aws.amazon.com/blogs/database/?nc=sn\&loc=4)

[Liberdade de banco de dados](https://aws.amazon.com/products/databases/freedom/?nc=sn\&loc=5)

***
