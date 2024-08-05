---
description: >-
  A infraestrutura física, como datacenters e redes de conexão, continua sendo
  fundamental para todas as aplicações em nuvem.
---

# Infraestrutura Global da AWS

Na AWS, essa infraestrutura física constitui a base global da AWS, organizada em regiões e zonas de disponibilidade.

***

## <mark style="color:red;">**Regiões**</mark>

<figure><img src="../../.gitbook/assets/image (5) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

A AWS hospeda seus datacenters em diversas regiões geográficas ao redor do mundo. Cada região recebe o nome do local onde está situada, como por exemplo, Região do Norte da Virgínia nos Estados Unidos e Região do Oregon, também nos Estados Unidos. A AWS possui regiões em várias partes do mundo, incluindo Ásia-Pacífico, Canadá, Europa, Oriente Médio e América do Sul, e está em constante expansão para melhor atender às necessidades de seus clientes.

Cada região da AWS está associada a um nome geográfico e a um código de região.

<figure><img src="../../.gitbook/assets/image (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

Aqui estão exemplos de códigos de região:

| us-east-1                                                                                             | ap-northeast-1                                                                                         |
| ----------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------ |
| A primeira região criada na área leste dos EUA. O nome geográfico desta região é o Norte da Virgínia. | A primeira região criada na região nordeste da Ásia-Pacífico. O nome geográfico desta região é Tóquio. |

As regiões da AWS não dependem umas das outras. Os dados não são replicados de uma Região para outra, sem consentimento e autorização explícitos do cliente.

***

### <mark style="color:red;">**Escolha a região certa da AWS**</mark>

Quando você decidir qual região da AWS hospedar suas aplicações e workloads, considere quatro aspectos principais: _**latência, preço, disponibilidade do serviço e conformidade.**_

{% tabs %}
{% tab title="Latência" %}
Para otimizar o desempenho de aplicações sensíveis à latência, como jogos, telefonia, WebSockets e IoT, é crucial escolher uma Região de servidor próxima aos usuários. Isso reduz o tempo de resposta entre solicitações de dados e suas respostas, minimizando os tempos de espera para os clientes. Mesmo aplicações assíncronas, como plataformas de comércio eletrônico, podem ser impactadas pela latência da conectividade do usuário, portanto, também se beneficiam de uma infraestrutura de servidor localizada estrategicamente.
{% endtab %}

{% tab title="Preços" %}
Os preços dos serviços da AWS variam de região para região devido a diferenças na economia local e nos custos associados à operação de datacenters, como conectividade com a Internet, custos de equipamentos importados, questões alfandegárias, imóveis e outros fatores. Em vez de aplicar uma taxa fixa globalmente, a AWS ajusta seus preços para refletir esses elementos financeiros específicos de cada localidade. Isso garante que os clientes paguem um valor justo e competitivo com base nas condições econômicas e operacionais locais.
{% endtab %}

{% tab title="Disponibilidade do Serviço" %}
Alguns serviços podem não estar disponíveis em algumas regiões. A documentação da AWS fornece uma tabela que mostra os serviços disponíveis em cada região.
{% endtab %}

{% tab title="Conformidade de dados" %}
Para empresas corporativas, é comum haver regulamentações que exigem que os dados dos clientes sejam armazenados em uma localização geográfica específica. Nesses casos, é importante escolher uma Região da AWS que esteja em conformidade com esses requisitos regulatórios. Isso garante que a empresa cumpra suas obrigações legais relacionadas à privacidade e segurança dos dados dos clientes, evitando potenciais penalidades e garantindo a confiança dos usuários em relação à proteção de suas informações pessoais.
{% endtab %}
{% endtabs %}

***

## <mark style="color:red;">Zonas de disponibilidade</mark>

<figure><img src="../../.gitbook/assets/image (2) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

Dentro de cada Região da AWS, existem clusters de Zonas de Disponibilidade (AZs). Cada AZ é composta por um ou mais datacenters equipados com redundância de energia, rede e conectividade. Esses datacenters são situados em locais discretos e não divulgados, mas são interligados por links de alta velocidade e baixa latência, garantindo alta disponibilidade e confiabilidade dos serviços hospedados.

Cada AZ é identificada por um nome de código que inclui uma letra no final do código da Região. Por exemplo, **"us-east-1a"** refere-se à AZ **'a'** na Região **"us-east-1" (Norte da Virgínia)**, enquanto **"sa-east-1b"** indica a AZ **'b'** na Região **"sa-east-1" (São Paulo)**. Isso significa que se você encontrar um recurso em **"us-east-1c"**, pode deduzir que esse recurso está localizado na AZ **'c'** da Região **"us-east-1"**.

***

### <mark style="color:red;">**Escopo dos produtos da AWS**</mark>

Dependendo do serviço da AWS que você está utilizando, os recursos podem ser implantados em diferentes níveis: **Zona de Disponibilidade (AZ), Região ou Global**. Cada serviço possui características específicas de escopo, o que pode impactar a arquitetura da sua aplicação.

Quando um serviço opera com escopo de região, você simplesmente seleciona a Região onde deseja implantar o serviço. Não há necessidade de especificar uma AZ individual durante a implantação. Isso indica que o serviço é gerenciado automaticamente pela AWS para aumentar a durabilidade e a disponibilidade dos dados.

Por outro lado, alguns serviços exigem que você especifique uma Zona de Disponibilidade (AZ) durante a configuração. Nestes casos, você tem a responsabilidade de garantir a durabilidade e a alta disponibilidade dos recursos dentro da AZ escolhida.

É essencial entender essas diferenças ao projetar sua arquitetura na AWS, pois o escopo do serviço afeta diretamente como você configura, gerencia e garante a resiliência da sua aplicação na nuvem.

***

### <mark style="color:red;">**Manter a resiliência**</mark>

Para garantir a disponibilidade contínua da sua aplicação na nuvem, é crucial adotar práticas que promovam alta disponibilidade e resiliência. Uma estratégia recomendada é utilizar serviços gerenciados com escopo de região, que já incluem níveis elevados de disponibilidade e resiliência integrados.

Quando não for possível usar serviços gerenciados com escopo de região, é essencial configurar sua carga de trabalho para ser replicada em múltiplas Zonas de Disponibilidade (AZs). Recomenda-se, no mínimo, configurar sua aplicação em duas AZs. Isso significa que, se uma AZ enfrentar uma falha, sua aplicação continuará operando na segunda AZ, capaz de assumir o tráfego.

Essa abordagem distribuída em várias AZs não apenas reduz o impacto de possíveis falhas locais, mas também melhora a resiliência global da sua infraestrutura na nuvem, assegurando que sua aplicação permaneça disponível para seus usuários mesmo diante de eventos inesperados.

<figure><img src="../../.gitbook/assets/image (3) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

***

## <mark style="color:red;">**Recursos**</mark>&#x20;

[Infraestrutura global](https://aws.amazon.com/about-aws/global-infrastructure/)

[Documentação de infraestrutura global da AWS](https://docs.aws.amazon.com/whitepapers/latest/aws-overview/global-infrastructure.html)

[Zonas de disponibilidade e regiões da AWS](https://aws.amazon.com/about-aws/global-infrastructure/regions\_az/)

[Endpoints de produto da AWS](https://docs.aws.amazon.com/general/latest/gr/rande.html)

[Produtos regionais da AWS](https://aws.amazon.com/about-aws/global-infrastructure/regional-product-services/)

***
