---
description: >-
  Agora que você entende como selecionar o sistema operacional para sua
  instância do EC2, você está pronto para configurar outras opções importantes,
  como o tipo de instância, rede e armazenamento.
---

# Ciclo de vida da instância do Amazon EC2

Para uma aplicação como o diretório de funcionários, é essencial escolher instâncias com capacidade suficiente para executar servidores web e processar solicitações dos clientes de forma eficiente. O dimensionamento da instância deve ser baseado nas necessidades específicas da aplicação e na estimativa do tamanho da base de usuários.

Ao planejar a capacidade de servidores para uma aplicação local (on-premises), normalmente envolve decisões complexas e investimentos significativos em capital inicial. No entanto, na AWS, você pode ajustar facilmente a alocação de recursos da sua infraestrutura com uma simples chamada de API. Isso se deve ao modelo de pagamento conforme o uso da AWS, onde você paga apenas pelo que utiliza. Essa flexibilidade permite ajustar dinamicamente a capacidade de infraestrutura de acordo com a demanda da aplicação, ao invés de prever e investir antecipadamente em recursos que podem não ser totalmente utilizados.

***

## <mark style="color:red;">Tipos de instância do Amazon EC2</mark>

As instâncias do Amazon EC2 são compostas por uma combinação de recursos essenciais como processadores virtuais (vCPUs), memória, capacidade de rede e, em certos casos, armazenamento de instâncias e unidades de processamento gráfico (GPUs). Ao configurar uma instância do EC2, é crucial determinar as quantidades necessárias de cada um desses componentes de acordo com os requisitos da sua aplicação e carga de trabalho esperada.

<figure><img src="../../.gitbook/assets/image (12) (1) (1).png" alt=""><figcaption></figcaption></figure>

A AWS oferece uma variedade de tipos de instância que diferem em termos de desempenho e capacidade. Algumas instâncias fornecem mais recursos do que outras. Para entender melhor as capacidades de uma instância específica, é necessário examinar seu tipo. Os tipos de instância são categorizados por um prefixo que identifica a família da instância e a geração, seguido pelo tamanho. Por exemplo, no caso do tipo de instância c5.large:

| c5                                                                                                                                                              | large                                                                                                                                                                      |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Identifica a família de instâncias e sua geração. No exemplo, c5 indica que é da quinta geração de instâncias da família C, otimizada para computação genérica. | Indica o tamanho da instância dentro dessa família, especificando a quantidade de recursos disponíveis, como vCPUs, memória e outros recursos específicos da configuração. |

Essa estrutura de nomenclatura ajuda a escolher a instância mais apropriada com base nos requisitos de desempenho e capacidade da sua aplicação na AWS.

***

### <mark style="color:red;">Famílias de instâncias</mark>

No exemplo c5.large, a letra "c" indica que a instância pertence à família otimizada para computação. A AWS oferece diversas famílias de instâncias, cada uma projetada para atender a diferentes tipos de cargas de trabalho. Abaixo está uma tabela que descreve algumas famílias de instâncias e os casos de uso típicos para cada uma:

<figure><img src="../../.gitbook/assets/image (14) (1).png" alt=""><figcaption></figcaption></figure>

Cada família de instância possui características específicas que a tornam mais adequada para diferentes tipos de aplicações. Escolher a família correta é essencial para otimizar o desempenho e os custos da sua infraestrutura na AWS, alinhando-se às necessidades específicas da sua carga de trabalho.

***

### <mark style="color:red;">Locais de instâncias do EC2</mark>

Por padrão, as instâncias do EC2 são lançadas dentro de uma rede denominada Amazon Virtual Private Cloud (Amazon VPC) padrão. Essa VPC é criada automaticamente pela AWS para facilitar o uso inicial do Amazon EC2, eliminando a necessidade de configurar uma VPC do zero.

É importante destacar que qualquer recurso colocado na VPC padrão é público e acessível pela Internet. Portanto, não é recomendável armazenar dados de clientes ou informações privadas nessa rede padrão.

Conforme você se torna mais familiarizado com a estrutura de rede da AWS, é aconselhável modificar essa configuração padrão e criar suas próprias VPCs personalizadas. Isso permite restringir o acesso usando mecanismos adicionais de roteamento e conectividade, adequando a configuração de rede às necessidades específicas de segurança e isolamento da sua aplicação.

***

### <mark style="color:red;">Arquitetar para alta disponibilidade</mark>

Ao projetar sua arquitetura na AWS, é crucial considerar a alta disponibilidade como um princípio fundamental. Cada instância do EC2 é implantada em uma zona de disponibilidade que você escolhe. Produtos AWS que operam ao nível da zona de disponibilidade devem ser arquitetados para alta disponibilidade.

Embora as instâncias do EC2 sejam geralmente confiáveis, é uma prática recomendada distribuir sua carga de trabalho em várias instâncias ao invés de depender de uma única instância. Isso oferece uma resiliência maior contra falhas. Ao dimensionar sua aplicação, especificar o tamanho da instância apropriado é vantajoso, permitindo que você utilize várias instâncias menores em vez de poucas instâncias maiores.

Por exemplo, se sua aplicação depende de um único front-end e essa instância falha, a aplicação inteira pode ficar fora do ar. Em contraste, distribuindo a carga em 10 instâncias e uma falhando, apenas 10% da capacidade é perdida, minimizando o impacto na disponibilidade da aplicação.

Para garantir alta disponibilidade, arquitete sua aplicação de forma que utilize pelo menos duas instâncias do EC2 em duas zonas de disponibilidade diferentes. Isso ajuda a mitigar falhas em uma zona específica, mantendo sua aplicação operacional mesmo se uma zona de disponibilidade falhar.

<figure><img src="../../.gitbook/assets/image (15) (1).png" alt=""><figcaption></figcaption></figure>

***

## <mark style="color:red;">Ciclo de vida da instância do EC2</mark>

Uma instância do EC2 faz a transição entre estados diferentes desde o momento em que você a cria até o término.

<figure><img src="../../.gitbook/assets/image (16) (1).png" alt=""><figcaption></figcaption></figure>

1. Quando você executa uma instância, ela entra no estado **pendente**. Quando uma instância está pendente, o faturamento não foi iniciado. Nesse estágio, a instância está se preparando para entrar no estado em execução. Dependendo do local em que a AWS executa todas as ações necessárias para configurar uma instância, como copiar o conteúdo da AMI para o dispositivo raiz e alocar os componentes de rede necessários.
2. Quando sua instância estiver **em execução**, ela estará pronta para uso. Este também é o estágio em que o faturamento começa. Assim que uma instância estiver em execução, você poderá executar outras ações na instância, como reinicializar, encerrar, parar e hibernar (stop-hibernate).
3. Reinicializar uma instância, é diferente de executar uma ação de parada e, em seguida, uma ação de início. **A reinicialização** de uma instância equivale a reinicialização de um sistema operacional. A instância permanece no mesmo computador host e mantém seu endereço de IP público e privado, além de quaisquer dados em seu armazenamento de instância.
4. Normalmente, leva alguns minutos para a reinicialização ser concluída. Quando você interrompe e inicia uma instância, sua instância pode ser colocada em um novo servidor físico subjacente. Portanto, você perde todos os dados no armazenamento de instâncias que estavam no computador host anterior. Quando você interrompe uma instância, a instância obtém um novo endereço IP público, mas mantém o mesmo endereço IP privado.
5. Quando você **encerrar** uma instância, os armazenamentos de instâncias são apagados e você perde o endereço IP público e o endereço IP privado da máquina. O encerramento de uma instância significa que você não pode mais acessar a máquina.

***

### <mark style="color:red;">Diferença entre parar e hibernar (stop-hibernate)</mark>

No cenário em que você está construindo uma aplicação de três camadas que se torna muito popular, com servidores Web, servidores de aplicação e servidores de banco de dados, é crucial considerar estratégias para otimizar o desempenho e a disponibilidade do banco de dados.

Quando a demanda aumenta e para aliviar o estresse no banco de dados, uma abordagem eficaz seria implementar uma camada de back-end personalizada que cacheia as informações do banco de dados na memória (RAM). Para isso, executar essa solução de cache no Amazon EC2 é uma escolha comum.

No entanto, é importante garantir que os dados na memória sejam persistentes para evitar perdas em caso de interrupção da instância. Nesse contexto, o recurso de hibernação (stop-hibernate) do Amazon EC2 é fundamental. Quando você hiberna uma instância, a AWS sinaliza o sistema operacional para salvar o conteúdo da memória (RAM) no volume raiz do Amazon EBS, garantindo que os dados sejam preservados entre as sessões de execução da instância.

Utilizar a hibernação elimina a necessidade de criar scripts manuais para salvar dados da RAM antes de desligar o servidor, oferecendo uma solução conveniente e confiável para manter a integridade dos dados na camada de cache de back-end personalizada. Isso é especialmente vantajoso em cenários de aplicativos em que a velocidade e a disponibilidade dos dados são críticas para o desempenho da aplicação.

***

## <mark style="color:red;">Preços</mark>

Uma das maneiras de reduzir custos com o Amazon EC2 é escolher a opção de definição de preço certa para a forma como suas aplicações são executadas. A AWS oferece três principais opções de compra para instâncias do EC2: instâncias sob demanda, reservadas e spot.

<figure><img src="../../.gitbook/assets/image (45).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:red;">Pague conforme o uso com instâncias sob demanda</mark>

Com instâncias sob demanda na AWS, você paga pela capacidade computacional conforme a utilização, sem compromissos de longo prazo. A cobrança começa quando a instância está em execução e para quando ela é interrompida ou encerrada. O preço por segundo para instâncias sob demanda em execução é fixo.

Para aplicações que requerem servidores operacionais continuamente, o modelo sob demanda pode não ser a opção mais econômica, pois não há necessidade de desligar os servidores. Por exemplo, um servidor web que hospeda o front-end de um aplicativo corporativo pode precisar estar disponível 24 horas por dia, 7 dias por semana, mesmo quando não há usuários ativos acessando o site.

Nesses casos, onde a interrupção dos servidores não é uma opção viável, considerar o uso de instâncias reservadas pode ser vantajoso para economizar custos. As instâncias reservadas permitem compromissos de longo prazo com descontos significativos em comparação com instâncias sob demanda. Você pode reservar capacidade computacional por 1 ou 3 anos, garantindo um preço mais baixo por hora durante todo o período reservado.

Dessa forma, mesmo se sua aplicação requer servidores operacionais sem interrupção, você pode economizar consideravelmente utilizando instâncias reservadas, mantendo a disponibilidade constante necessária para atender às necessidades dos usuários.

***

As Instâncias Reservadas (RIs) na AWS oferecem descontos significativos em comparação com instâncias sob demanda. Elas proporcionam uma taxa por hora com desconto e a opção de reservar capacidade para instâncias do EC2. Existem três opções de pagamento: adiantamento integral, adiantamento parcial e sem adiantamento, disponíveis para períodos de 1 ou 3 anos.

Aqui estão os principais pontos sobre as opções de pagamento e os descontos associados às RIs:

#### <mark style="color:blue;">**Adiantamento integral**</mark>

Oferece o maior desconto comparado às outras opções. Requer o pagamento completo antecipado para o período escolhido (1 ou 3 anos).

#### <mark style="color:blue;">**Adiantamento parcial**</mark>

Oferece um desconto menor do que o adiantamento integral, mas ainda significativo em relação às instâncias sob demanda. Requer um pagamento parcial antecipado.

#### <mark style="color:blue;">**Sem adiantamento**</mark>

Oferece um desconto maior do que instâncias sob demanda, mas menor do que as RIs com adiantamento. Não requer pagamento antecipado, sendo cobrado o valor da RI ao longo do período de uso.

É importante notar que instâncias sob demanda e instâncias sem adiantamento têm descontos semelhantes, mas com diferenças fundamentais na forma de pagamento e compromisso. Ao escolher uma instância sob demanda, você paga apenas quando a instância está em execução e não há compromisso de longo prazo. Por outro lado, ao interromper uma RI, você ainda é cobrado pelo período contratado (1 ou 3 anos), pois já se comprometeu com essa capacidade.

As RIs são associadas a um tipo de instância e a uma zona de disponibilidade específica, oferecendo desconto com base no tipo de instância reservada, não em instâncias individuais. Isso proporciona flexibilidade ao usar instâncias reservadas em diferentes contextos e cenários, mantendo os custos reduzidos em comparação com instâncias sob demanda.

***

### <mark style="color:red;">Economize em custos com instâncias spot</mark>

As instâncias spot do Amazon EC2 oferecem uma maneira econômica de aproveitar a capacidade não utilizada na AWS, com descontos de até 90% em comparação com os preços sob demanda. Aqui estão algumas considerações importantes para usar instâncias spot de forma eficaz:

#### <mark style="color:blue;">**Definição de preço**</mark>

Você define um limite de preço máximo que está disposto a pagar por hora pela instância. Esse preço é comparado com o preço spot atual determinado pela AWS. Se o preço spot estiver abaixo do seu limite, você recebe a instância.

#### <mark style="color:blue;">**Possibilidade de interrupção**</mark>

Uma consideração crucial é que as instâncias spot podem ser interrompidas pela AWS com um aviso prévio de 2 minutos. Isso ocorre quando a capacidade não está mais disponível para uma instância spot específica ou se o preço spot excede seu limite definido.

#### <mark style="color:blue;">**Workloads tolerantes a falhas**</mark>

Devido à possibilidade de interrupção, as workloads que podem lidar com falhas de forma inerente são ideais para instâncias spot. Isso inclui aplicações como big data, workloads em contêineres, CI/CD, servidores web, computação de alta performance (HPC), renderização de imagens e mídia, além de testes e desenvolvimento.

#### <mark style="color:blue;">**Benefícios econômicos**</mark>

Apesar da possibilidade de interrupção, as instâncias spot oferecem uma oportunidade significativa de economia de custos para workloads que podem ser flexíveis quanto ao tempo de execução e não exigem disponibilidade contínua.

Em resumo, ao escolher instâncias spot, é fundamental entender suas características únicas, como a possibilidade de interrupção, e selecionar workloads que se beneficiem dessas condições, aproveitando os descontos substanciais oferecidos pela AWS.

***

## <mark style="color:red;">**Recursos**</mark>

[Amazon EC2](https://aws.amazon.com/ec2/)

[VPC padrão e sub-redes padrão](https://docs.aws.amazon.com/vpc/latest/userguide/default-vpc.html)

[Pilar de confiabilidade da AWS (PDF)](https://d1.awsstatic.com/whitepapers/architecture/AWS-Reliability-Pillar.pdf)

[Ciclo de vida da instância](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-instance-lifecycle.html)

[Definição de preço do Amazon EC2](https://aws.amazon.com/ec2/pricing/)

[Definição de preço sob demanda do Amazon EC2](https://aws.amazon.com/ec2/pricing/on-demand/)

[Definição de preço de instâncias spot do Amazon EC2](https://aws.amazon.com/ec2/spot/pricing/)

[Definição de preço de instâncias reservadas do Amazon EC2](https://aws.amazon.com/ec2/pricing/reserved-instances/pricing/)

***
