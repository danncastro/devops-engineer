# Roteamento de tráfego com o Amazon Elastic Load Balancing

***

## <mark style="color:red;">Balanceadores de carga</mark>

O balanceamento de carga é o processo de distribuição de solicitações entre um grupo de recursos. Em uma aplicação como um diretório de funcionários hospedado em instâncias do EC2, os recursos são os servidores que hospedam a aplicação e as solicitações são os pedidos enviados por usuários.

#### <mark style="color:blue;">**Como Funciona**</mark>

Para implementar o balanceamento de carga, primeiro você habilita um balanceador para receber todo o tráfego e distribuí-lo para os servidores de backend usando um algoritmo, como o round-robin, que encaminha as solicitações sequencialmente para cada servidor.

#### <mark style="color:blue;">**Benefícios e Casos de Uso**</mark>

| Distribuição Equitativa                                                                                            | Alta Disponibilidade                                                                                       | Elasticidade                                                                                                               |
| ------------------------------------------------------------------------------------------------------------------ | ---------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------- |
| Garante que nenhum servidor fique sobrecarregado, melhorando o desempenho e a capacidade de resposta da aplicação. | Reduz o impacto de falhas de servidor, redirecionando automaticamente o tráfego para instâncias saudáveis. | Facilita a escalabilidade horizontal adicionando ou removendo instâncias conforme necessário, sem interrupções no serviço. |

#### <mark style="color:blue;">**Por que Usar Elastic Load Balancing (ELB)**</mark>

Embora seja possível configurar soluções de balanceamento de carga em software nas instâncias do EC2, a AWS oferece o Elastic Load Balancing como um serviço gerenciado que simplifica a configuração e operação.

#### <mark style="color:blue;">**Benefícios Adicionais do ELB**</mark>

| Integração com AWS                                                                                                        | Monitoramento Avançado                                                                                     | Segurança Aprimorada                                                                    |
| ------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------- |
| Total integração com outros serviços AWS, como Auto Scaling, que ajusta automaticamente a capacidade com base na demanda. | Funcionalidades integradas de monitoramento e diagnóstico para garantir alta disponibilidade e desempenho. | Gerencia o tráfego de entrada para proteger contra ataques e explorar vulnerabilidades. |

#### <mark style="color:blue;">**Casos de Uso**</mark>

| Aplicações Web                                                                               | Microsserviços                                                                                                        |
| -------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------- |
| Distribuição de tráfego para múltiplas instâncias EC2 que hospedam um site ou aplicação web. | Encaminhamento de solicitações para diferentes serviços em um ambiente de microsserviços para otimização de recursos. |

| Aplicações com Grande Escala                                                                          |
| ----------------------------------------------------------------------------------------------------- |
| Suporte para lidar com picos de tráfego sazonal ou inesperado, mantendo a estabilidade e performance. |

Adotar o Elastic Load Balancing não apenas melhora a confiabilidade e escalabilidade das suas aplicações, mas também simplifica a gestão de tráfego e garante uma experiência contínua para os usuários, independentemente da carga de trabalho ou condições operacionais.

***

## <mark style="color:red;">Recursos do Elastic Load Balancing (ELB)</mark>

O serviço ELB oferece uma solução gerenciada para balanceamento de carga, eliminando a necessidade de gerenciar e operar seu próprio sistema. Ele distribui o tráfego de entrada da aplicação entre instâncias do EC2, contêineres, endereços IP e funções do AWS Lambda. Principais recursos incluem:

| Balanceamento Híbrido                                                                                                                         | Alta Disponibilidade                                                                                                                           |
| --------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------- |
| O ELB pode balancear carga para endereços IP, permitindo um funcionamento híbrido que inclui servidores on-premises, além de recursos na AWS. | Implantado em várias zonas de disponibilidade, o ELB garante alta disponibilidade, redirecionando automaticamente o tráfego em caso de falhas. |

| Escalabilidade Automática                                                                                                                         |
| ------------------------------------------------------------------------------------------------------------------------------------------------- |
| Dimensiona automaticamente para lidar com picos de tráfego, garantindo que a aplicação de back-end seja capaz de processar todas as solicitações. |

#### <mark style="color:blue;">**Benefícios Adicionais do ELB**</mark>

| Integração Versátil                                                                                                                                                                             | Gestão Simplificada                                                                                                                      | Segurança e Confiabilidade                                                                                                              |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------- |
| Pode ser configurado para distribuir tráfego para diversos tipos de recursos, como EC2, contêineres Docker, endereços IP e funções Lambda, adequando-se a diferentes arquiteturas de aplicação. | Elimina a necessidade de configurar e manter um sistema de balanceamento de carga próprio, reduzindo custos operacionais e complexidade. | Gerencia o tráfego de entrada de forma segura, protegendo contra ataques e garantindo uma experiência contínua para os usuários finais. |

#### <mark style="color:blue;">**Casos de Uso do ELB**</mark>

| Aplicações Web Escalonáveis                                                                                  |
| ------------------------------------------------------------------------------------------------------------ |
| Distribuição de tráfego para instâncias EC2 em um ambiente web para lidar com altos volumes de solicitações. |

| Arquiteturas de Microsserviços                                                                                                       | Ambientes Híbridos                                                                                                                                    |
| ------------------------------------------------------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------- |
| Encaminhamento de tráfego para diferentes serviços dentro de uma arquitetura de microsserviços, otimizando a utilização de recursos. | Integração de servidores on-premises com recursos na nuvem AWS, utilizando o ELB para balancear carga entre ambos os ambientes de forma transparente. |

Adotar o Elastic Load Balancing não apenas melhora a escalabilidade e disponibilidade das aplicações, mas também simplifica a gestão de tráfego em ambientes complexos, garantindo uma resposta eficiente às demandas variáveis de tráfego.

***

### <mark style="color:red;">Verificações de integridade</mark>

Garantir a integridade operacional de uma aplicação é crucial para manter sua disponibilidade e desempenho. Simplesmente verificar se uma porta está aberta não garante que a aplicação esteja funcionando corretamente. Uma abordagem mais eficaz é implementar verificações de integridade que validem todos os componentes críticos da aplicação.

#### <mark style="color:blue;">**Implementação Adequada de Verificações de Integridade**</mark>

Por exemplo, na aplicação "Diretório de Funcionários", que depende de um banco de dados e do Amazon S3, uma verificação de integridade ideal deveria testar todos esses elementos essenciais. Uma prática comum é criar uma página de monitoramento como "/monitor", que realiza chamadas ao banco de dados para verificar a conexão e obter dados, além de interagir com o Amazon S3 para validar o acesso aos arquivos necessários. Essa página de monitoramento é então configurada no balanceador de carga para ser verificada regularmente.

<figure><img src="../../.gitbook/assets/image (2) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

<mark style="color:blue;">**Benefícios das Verificações de Integridade**</mark>

| Garantia de Disponibilidade                                                                                                                                                                                                                                |
| ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Ao configurar verificações de integridade detalhadas, o balanceador de carga (ELB) pode detectar rapidamente instâncias do EC2 que não estão respondendo corretamente e interromper o tráfego para elas, direcionando-o apenas para instâncias funcionais. |

| Automação da Escalabilidade                                                                                                                                                              | Controle de Tráfego e Conexões                                                                                                                                                                             |
| ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Em conjunção com o EC2 Auto Scaling, o ELB permite a substituição automática de instâncias defeituosas por novas, mantendo assim a capacidade de resposta da aplicação diante de falhas. | O ELB coordena com o EC2 Auto Scaling para gerenciar o encerramento controlado de instâncias EC2 sem interrupções bruscas nas conexões dos clientes, através da característica de "diminuição de conexão". |

#### <mark style="color:blue;">**Casos de Uso das Verificações de Integridade**</mark>

| Aplicações Críticas para o Negócio                                                                                                                                                                                       | Ambientes de Microsserviços                                                                                                                                                                                                                                      |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Em ambientes onde a disponibilidade contínua é crucial, como em aplicações financeiras ou de e-commerce, as verificações de integridade garantem que apenas instâncias saudáveis respondam às solicitações dos clientes. | Em arquiteturas baseadas em microsserviços, onde várias partes da aplicação devem estar em funcionamento para garantir a operação geral, as verificações de integridade asseguram que todos os serviços estejam operacionais e prontos para atender às demandas. |

Implementar verificações de integridade robustas não apenas fortalece a disponibilidade da aplicação, mas também melhora a eficiência operacional ao automatizar a detecção e recuperação de falhas, mantendo uma experiência consistente para os usuários finais.

***

### <mark style="color:red;">Componentes ELB</mark>

O serviço Elastic Load Balancing (ELB) da AWS é composto por três componentes principais que desempenham papéis cruciais na distribuição e gerenciamento do tráfego de aplicativos:

<figure><img src="../../.gitbook/assets/image (3) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

<details>

<summary><mark style="color:purple;"><strong>Listeners</strong></mark></summary>

Listeners são configurações que verificam a porta de entrada para o tráfego. Eles monitoram as solicitações recebidas e decidem para onde direcionar com base nas regras configuradas. Por exemplo, você pode configurar um listener HTTP na porta 80 que encaminha o tráfego para um grupo de destino configurado para lidar com solicitações HTTP.

</details>

<details>

<summary><mark style="color:purple;"><strong>Rules (Regras)</strong></mark></summary>

As regras definem como o tráfego deve ser roteado com base nas condições especificadas. Elas estão associadas aos listeners e ajudam a determinar o destino das solicitações com base em critérios como o caminho da URL, cabeçalhos HTTP, métodos de requisição, entre outros. Por exemplo, uma regra pode direcionar todas as solicitações com o caminho "/api" para um grupo de destino específico configurado para lidar com a lógica da API.

</details>

<details>

<summary><mark style="color:purple;"><strong>Target Groups (Grupos de Destino)</strong></mark></summary>

Os grupos de destino são conjuntos de instâncias do EC2, contêineres do ECS, endereços IP ou funções do AWS Lambda que recebem tráfego do ELB. Eles determinam onde o tráfego será encaminhado depois que as regras e listeners do ELB decidirem qual destino corresponde à solicitação. Os grupos de destino garantem que o tráfego seja distribuído de forma eficiente e que a carga seja equilibrada entre os recursos disponíveis.

</details>

#### <mark style="color:blue;">**Por que usar?**</mark>

| Escalabilidade automática                                                                                                                                                                                                            | Alta disponibilidade                                                                                                                                                                                                                  |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| O ELB facilita a escalabilidade automática adicionando ou removendo instâncias de forma dinâmica com base na carga de tráfego. Isso garante que a aplicação possa lidar com aumentos repentinos de demanda sem quedas no desempenho. | Ao distribuir o tráfego entre múltiplos destinos (instâncias EC2, contêineres, etc.) e em várias zonas de disponibilidade, o ELB ajuda a garantir que a aplicação esteja sempre acessível, mesmo em caso de falha em um dos recursos. |

| Gerenciamento simplificado                                                                                                                                                                 | Flexibilidade                                                                                                                                                                                                        |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Elimina a necessidade de gerenciar manualmente o tráfego de entrada e saída, pois o ELB cuida das verificações de integridade, roteamento e distribuição do tráfego de forma automatizada. | Permite configurar diferentes listeners, regras e grupos de destino para atender a diferentes tipos de tráfego e requisitos de aplicativos, proporcionando flexibilidade na arquitetura de aplicativos distribuídos. |

Os componentes do ELB trabalham juntos para melhorar a disponibilidade, escalabilidade e confiabilidade das aplicações hospedadas na AWS, proporcionando uma experiência de usuário mais estável e consistente.

***

## <mark style="color:red;">Application Load Balancer</mark>

O Application Load Balancer (ALB) da AWS oferece uma série de recursos poderosos para melhorar a gestão e a segurança do tráfego de aplicações baseadas em HTTP e HTTPS:

| Roteamento Granular                                                                                                                                                                                                                           | Respostas Diretas e Redirecionamento                                                                                                                              |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| O ALB roteia o tráfego com base em dados detalhados da solicitação, como caminho do URL, host, cabeçalhos e método HTTP, além do endereço IP do cliente. Isso permite direcionar solicitações para diferentes grupos de destino com precisão. | O ALB pode responder diretamente ao cliente com páginas HTML fixas ou redirecionar solicitações para outros locais, reduzindo a carga nos servidores de back-end. |

| Descarregamento TLS                                                                                                                                 | Autenticação de Usuários                                                                                                                                                        | Proteção do Tráfego                                                                                                                                           |
| --------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Suporta tráfego HTTPS, gerenciando certificados SSL/TLS para criptografar o tráfego entre clientes e ALB, protegendo assim a integridade dos dados. | Integra-se a protocolos como OpenID Connect, SAML, LDAP e Microsoft Active Directory para autenticar usuários antes de permitir o acesso às aplicações, reforçando a segurança. | Utiliza grupos de segurança para restringir o tráfego apenas a intervalos de endereços IP autorizados, aumentando a segurança contra acessos não autorizados. |

| Algoritmos de Roteamento                                                                                                                                                                              | Sticky Sessions                                                                                                                                                                         |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Oferece opções como round-robin para distribuir igualmente as solicitações entre servidores e least outstanding requests (menos solicitações pendentes) para equilibrar cargas de trabalho variáveis. | Permite manter sessões persistentes direcionando solicitações do mesmo cliente para o mesmo servidor de back-end, ideal para aplicações com estado que requerem continuidade de sessão. |

O ALB é ideal para aplicações que necessitam de flexibilidade no roteamento, segurança avançada, e suporte eficaz para tráfego HTTP e HTTPS. Ele simplifica a gestão de tráfego web e contribui para uma experiência de usuário mais estável e segura, especialmente em ambientes com alta demanda e requisitos de segurança rigorosos.

***

## <mark style="color:red;">Network Load Balancer</mark>

O Network Load Balancer (NLB) da AWS é otimizado para aplicações que requerem alto desempenho, escalabilidade e flexibilidade em roteamento de tráfego na camada de conexão:

| Suporte a Protocolos TCP, UDP e TLS                                                                                                                                                                                                                                                       | Algoritmo de Roteamento Hash de Fluxo                                                                                                                                                                                      |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| O NLB opera na camada de conexão e oferece suporte aos protocolos TCP, UDP e TLS. Enquanto não entende o conteúdo específico de solicitações HTTP ou HTTPS, é eficaz para rotear tráfego baseado em endereços IP de origem e destino, portas e outros parâmetros da camada de transporte. | Utiliza um algoritmo que distribui pacotes com base em múltiplos parâmetros, como protocolo, endereços IP e portas de origem e destino, garantindo que pacotes semelhantes sejam sempre direcionados para o mesmo destino. |

| Sticky Sessions Baseadas em IP                                                                                                                                                                         | Descarregamento TLS                                                                                                                             |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| Ao contrário do ALB, o NLB utiliza sticky sessions baseadas no endereço IP de origem do cliente, permitindo que as solicitações sejam persistentemente direcionadas para o mesmo servidor de back-end. | Capacidade de gerenciar o tráfego TLS, o que inclui a capacidade de descarregar TLS dos servidores de back-end para reduzir a carga nos mesmos. |

| Alta Capacidade e Desempenho                                                                                                                                        | Suporte a Endereços IP Estáticos e Elásticos                                                                                                                                                  |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Projetado para lidar com milhões de solicitações por segundo de forma eficiente, sem necessidade de escalar para atingir altos volumes de tráfego instantaneamente. | Oferece opções para endereços IP estáticos ou elásticos, adequados para cenários onde é necessário enviar tráfego diretamente para um endereço IP específico, sem depender de resoluções DNS. |

| Preservação do Endereço IP de Origem                                                                                                                                             |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| O NLB mantém o endereço IP real do cliente ao enviar tráfego para os servidores de back-end, ideal para aplicações que requerem visibilidade do endereço IP original do cliente. |

O NLB é ideal para aplicações que operam em camadas mais baixas do modelo OSI, como aplicações que utilizam protocolos TCP, UDP e TLS diretamente. É especialmente útil em cenários onde é crucial manter a integridade e a consistência das conexões com base nos parâmetros de rede específicos, além de suportar altas cargas de tráfego de maneira eficiente e escalável.

***

### <mark style="color:red;">Selecione entre tipos de ELB</mark>

Para escolher entre os tipos de serviço do Elastic Load Balancer (ELB), é crucial entender as necessidades específicas da sua aplicação e como cada tipo de balancer atende a essas exigências:

<figure><img src="../../.gitbook/assets/image (4) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

#### <mark style="color:blue;">**Escolha do ELB**</mark>

| Cenários de uso                                                                                                                                                   | Desempenho de rede                                                                                                                                                                |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Use o ALB para aplicações web que necessitam de roteamento avançado baseado em HTTP/HTTPS, gerenciamento de tráfego flexível e suporte a autenticação de usuário. | Opte pelo NLB para aplicações que requerem alto desempenho, escalabilidade instantânea e preservação do endereço IP original do cliente, operando com protocolos TCP, UDP ou TLS. |

Ao escolher entre ALB e NLB, considere sempre os requisitos específicos da aplicação em termos de protocolos suportados, necessidades de roteamento, segurança e desempenho de rede para garantir a melhor solução de balanceamento de carga.

***

## **Recursos**

[Comparação de produtos do Elastic Load Balancer(opens in a new tab)](https://aws.amazon.com/elasticloadbalancing/features/#Product\_comparisons)

[AWS Certificate Manager(opens in a new tab)](https://aws.amazon.com/certificate-manager/)

[Autenticar usuários usando um Application Load Balancer(opens in a new tab)](https://docs.aws.amazon.com/elasticloadbalancing/latest/application/listener-authenticate-users.html)

[Como o AWS WAF funciona(opens in a new tab)](https://docs.aws.amazon.com/waf/latest/developerguide/how-aws-waf-works.html)

[Introdução ao AWS Gateway Load Balancer](https://aws.amazon.com/blogs/aws/introducing-aws-gateway-load-balancer-easy-deployment-scalability-and-high-availability-for-partner-appliances/)

***
