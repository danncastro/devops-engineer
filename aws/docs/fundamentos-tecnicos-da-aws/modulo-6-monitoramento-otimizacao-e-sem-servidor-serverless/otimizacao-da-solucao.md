# Otimização da solução

***

## <mark style="color:red;">Disponibilidade</mark>

A disponibilidade de um sistema é frequentemente expressa como uma porcentagem de tempo de atividade ao longo de um ano ou em termos de "noves", indicando o quanto o sistema está operacional. Veja na tabela exemplos de disponibilidade e seu equivalente em tempo de inatividade anual:

<figure><img src="../../.gitbook/assets/image (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

#### <mark style="color:blue;">**Como Aumentar a Disponibilidade**</mark>

Para aumentar a disponibilidade, é necessário implementar redundância. Isso geralmente envolve mais infraestrutura, datacenters adicionais, servidores extras, replicação de dados e backups. No entanto, isso também significa custos adicionais significativos. É crucial equilibrar a necessidade de alta disponibilidade com os custos associados.

#### <mark style="color:blue;">**Benefícios e Casos de Uso**</mark>

| Continuidade Operacional                                                                                                                                                     | Resiliência                                                                                                                                                                                       | Satisfação do Cliente                                                                                                                                  |
| ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Alta disponibilidade é crucial para aplicações críticas que exigem operação contínua, como sistemas de pagamento, serviços financeiros e plataformas de comércio eletrônico. | Redundância aumenta a resiliência do sistema contra falhas de hardware, falhas de datacenters ou desastres naturais, garantindo que os serviços permaneçam acessíveis mesmo durante interrupções. | Clientes esperam que os serviços estejam disponíveis o tempo todo. Alta disponibilidade aumenta a satisfação do cliente e constrói confiança na marca. |

#### <mark style="color:blue;">**Por que Usar**</mark>

| Minimização de Impactos                                                                                                     | Conformidade com SLAs                                                                                                      |
| --------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------- |
| Reduzir o tempo de inatividade ajuda a minimizar impactos financeiros e reputacionais associados a interrupções de serviço. | Cumprir com acordos de nível de serviço (SLAs) que garantem uma disponibilidade mínima é fundamental para muitos negócios. |

A busca por maior disponibilidade requer um equilíbrio cuidadoso entre investimentos em infraestrutura redundante e os benefícios obtidos em termos de operações contínuas e satisfação do cliente.

***

### <mark style="color:red;">Melhorar a disponibilidade das aplicações</mark>

Na configuração atual da aplicação, uma instância do EC2 hospeda a aplicação, o Amazon Simple Storage Service (Amazon S3) gerencia as imagens e o Amazon DynamoDB armazena os dados estruturados. No entanto, essa única instância do EC2 representa um ponto único de falha para a aplicação.

Embora o Amazon S3 e o DynamoDB sejam altamente disponíveis, os clientes não poderão acessar a aplicação se essa única instância do EC2 ficar indisponível. Uma solução para esse problema é adicionar mais servidores para distribuir a carga e aumentar a disponibilidade da aplicação.

#### <mark style="color:blue;">**Benefícios e Casos de Uso**</mark>

| Redundância e Alta Disponibilidade                                                                                                                                                                             |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Ao adicionar mais instâncias do EC2, você reduz a dependência de um único servidor, aumentando a disponibilidade da aplicação. Isso permite que os clientes acessem a aplicação mesmo se uma instância falhar. |

| Escalabilidade                                                                                                                                               | Balanceamento de Carga                                                                                                                                                                                                   |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Adicionar servidores não só melhora a disponibilidade, mas também permite que a aplicação atenda a um maior número de usuários sem comprometer o desempenho. | Com várias instâncias do EC2, você pode configurar um balanceador de carga (load balancer) para distribuir o tráfego entre os servidores de forma eficiente, melhorando ainda mais a disponibilidade e a escalabilidade. |

#### <mark style="color:blue;">**Por que Usar**</mark>

| Continuidade de Serviço                                                                                                                   | Resiliência contra Falhas                                                                                                                                              | Conformidade e SLAs                                                                                                                                                            |
| ----------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Reduzir os pontos únicos de falha garante que a aplicação permaneça acessível, mesmo durante falhas de hardware ou manutenção programada. | Distribuir a carga entre várias instâncias do EC2 protege contra falhas individuais, garantindo uma melhor experiência do usuário e reduzindo interrupções no serviço. | Cumprir com requisitos de disponibilidade definidos em acordos de nível de serviço (SLAs) é fundamental para manter a confiança dos clientes e evitar penalidades contratuais. |

Ao adicionar redundância através de múltiplas instâncias do EC2, você fortalece a infraestrutura da sua aplicação na AWS, assegurando que ela possa lidar com demandas variáveis e permanecer operacional em condições adversas.

***

### <mark style="color:red;">Segunda zona de disponibilidade</mark>

A localização física de um servidor desempenha um papel crucial na garantia da disponibilidade de uma aplicação. Além dos problemas potenciais de software no nível do sistema operacional ou da aplicação, falhas de hardware também devem ser consideradas, desde o servidor físico até o datacenter ou a própria zona de disponibilidade que hospeda a máquina virtual.

Para mitigar esses riscos, é recomendável implantar uma segunda instância do EC2 em uma zona de disponibilidade diferente. Isso não apenas oferece redundância contra falhas localizadas, mas também pode resolver problemas relacionados ao sistema operacional e à aplicação.

#### <mark style="color:blue;">**Benefícios e Casos de Uso**</mark>

| Redundância Geográfica                                                                                                                                                     | Resiliência contra Desastres                                                                                                                                              |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Distribuir instâncias do EC2 entre diferentes zonas de disponibilidade garante que a aplicação permaneça acessível mesmo se uma zona inteira experimentar uma interrupção. | Em caso de falha crítica, como uma interrupção de energia ou desastre natural em uma zona específica, a segunda zona de disponibilidade mantém a continuidade do serviço. |

| Balanceamento de Carga e Alta Disponibilidade                                                                                                                                 |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Configurando um balanceador de carga entre múltiplas zonas de disponibilidade, você pode distribuir o tráfego de maneira eficiente e assegurar alta disponibilidade contínua. |

#### <mark style="color:blue;">**Por que Usar**</mark>

<table><thead><tr><th>Minimização de Riscos</th><th width="250">Conformidade e SLAs</th><th>Escalabilidade e Desempenho</th></tr></thead><tbody><tr><td>Reduzir a dependência de uma única zona de disponibilidade minimiza os riscos de interrupções prolongadas e melhora a robustez da infraestrutura da aplicação.</td><td>Cumprir com requisitos de disponibilidade definidos em acordos de nível de serviço (SLAs) é essencial para atender às expectativas dos clientes e garantir a conformidade regulatória.</td><td>Distribuir instâncias do EC2 em várias zonas de disponibilidade suporta a escalabilidade da aplicação, permitindo que ela cresça conforme a demanda sem comprometer o desempenho.</td></tr></tbody></table>

Ao implantar uma segunda zona de disponibilidade, você fortalece a infraestrutura da sua aplicação na AWS, proporcionando uma camada adicional de proteção contra falhas e melhorando sua capacidade de resistir a eventos adversos.

***

### <mark style="color:red;">Replicação, Redirecionamento e Alta Disponibilidade</mark>

#### <mark style="color:blue;">**Processo de Replicação**</mark>

Um desafio ao utilizar várias instâncias do EC2 é garantir que os arquivos de configuração, patches de software e aplicações sejam replicados entre as instâncias de forma eficiente. Automatizar esse processo é essencial para manter a consistência e a integridade da aplicação em todas as instâncias.

#### <mark style="color:blue;">**Benefícios e Casos de Uso**</mark>

| Consistência Operacional                                                                                                                                                                          | Escala e Flexibilidade                                                                                                                        |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------- |
| Automatizar a replicação garante que todas as instâncias estejam sempre sincronizadas com as últimas atualizações e configurações, reduzindo erros humanos e melhorando a eficiência operacional. | Permite escalar horizontalmente adicionando novas instâncias sem interrupções significativas, suportando picos de carga e demandas variáveis. |

#### <mark style="color:blue;">**Redirecionamento do Cliente**</mark>

Outro desafio é garantir que os clientes sejam direcionados corretamente para as diferentes instâncias de servidor disponíveis. Isso pode ser realizado de várias maneiras, incluindo o uso de DNS para apontar clientes para os IPs dos servidores. No entanto, o tempo de propagação do DNS pode ser um problema, especialmente em atualizações rápidas de infraestrutura.

#### <mark style="color:blue;">**Benefícios e Casos de Uso**</mark>

| Redução de Latência                                                                                                                                                | Maior Disponibilidade                                                                                                                                      |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Utilizar balanceadores de carga permite distribuir o tráfego de forma inteligente entre as instâncias, reduzindo a latência e melhorando a experiência do usuário. | Evita interrupções de serviço ao garantir que o tráfego seja redirecionado apenas para instâncias operacionais, mesmo durante atualizações ou manutenções. |

#### <mark style="color:blue;">**Tipos de Alta Disponibilidade**</mark>

Ao implementar múltiplas instâncias, é crucial decidir o tipo de arquitetura de alta disponibilidade adequada para suas necessidades.

| Ativo-Passivo                                                                                                                                                                    | Ativo-Ativo                                                                                                                                                                                                                                                   |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Ideal para aplicações com estado, onde apenas uma instância está ativa enquanto a outra fica em standby. Isso garante que os dados da sessão do cliente permaneçam consistentes. | Mais adequado para aplicações stateless, onde ambas as instâncias estão ativas e podem compartilhar a carga de trabalho. Isso melhora a escalabilidade e a capacidade de resposta do sistema, mas requer uma gestão cuidadosa dos dados de sessão do cliente. |

#### <mark style="color:blue;">**Benefícios e Casos de Uso**</mark>

| Resiliência e Escalabilidade                                                                                                                                                                                     | Flexibilidade de Implementação                                                                                                                                               |
| ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Arquiteturas ativo-passivo garantem continuidade operacional em caso de falhas, enquanto ativo-ativo permite distribuir melhor a carga de trabalho para otimizar recursos e suportar um maior volume de tráfego. | Escolher entre ativo-passivo e ativo-ativo depende das necessidades específicas da aplicação em termos de resiliência, escalabilidade e exigências de consistência de dados. |

Implementar estratégias eficazes de replicação, redirecionamento e alta disponibilidade não apenas melhora a robustez da infraestrutura, mas também garante uma experiência de usuário estável e confiável, independentemente das condições operacionais e do volume de tráfego.

***

## **Recursos**

[Alta disponibilidade e escalabilidade na AWS(opens in a new tab)](https://docs.aws.amazon.com/whitepapers/latest/real-time-communication-on-aws/high-availability-and-scalability-on-aws.html)

[Pilar de confiabilidade da AWS: AWS Well-Architected Framework](https://d1.awsstatic.com/whitepapers/architecture/AWS-Reliability-Pillar.pdf)

***
