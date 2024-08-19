---
description: >-
  A infraestrutura física, como datacenters e redes de conexão, continua sendo
  fundamental para todas as aplicações em nuvem.
---

# Infraestrutura Global da AWS

Na AWS, essa infraestrutura física constitui a base global da AWS, organizada em regiões e zonas de disponibilidade.

***

## <mark style="color:red;">**Regiões**</mark>

<figure><img src="../../../.gitbook/assets/image (5) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

A **AWS** hospeda seus datacenters em várias **regiões geográficas** ao redor do mundo. Cada região é nomeada conforme sua localização, como por exemplo:

* **Região do Norte da Virgínia** (Estados Unidos)
* **Região do Oregon** (Estados Unidos)

A AWS possui regiões em diversas partes do globo, incluindo:

* **Ásia-Pacífico**
* **Canadá**
* **Europa**
* **Oriente Médio**
* **América do Sul**

E continua em **constante expansão** para atender melhor às necessidades dos seus clientes.

#### <mark style="color:blue;">Cada região da AWS está associada a um nome geográfico e a um código de região.</mark>

<figure><img src="../../../.gitbook/assets/image (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

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
Para otimizar o desempenho de aplicações sensíveis à **latência** (como jogos, telefonia, WebSockets e IoT), escolha uma **região** próxima aos usuários. Isso reduz o **tempo de resposta** entre solicitações e respostas, minimizando os tempos de espera. Aplicações assíncronas, como plataformas de **comércio eletrônico**, também se beneficiam de uma **infraestrutura de servidor** estrategicamente localizada.
{% endtab %}

{% tab title="Preços" %}
Os **preços** dos serviços da AWS variam entre regiões devido a diferenças na economia local e custos operacionais, como **conectividade com a Internet**, **equipamentos importados**, questões **alfandegárias** e **imóveis**. A AWS ajusta seus preços para refletir as condições econômicas e operacionais locais, garantindo que os clientes paguem um valor justo e competitivo.
{% endtab %}

{% tab title="Disponibilidade do Serviço" %}
Alguns **serviços** podem não estar disponíveis em todas as regiões. Consulte a **documentação da AWS** para verificar quais serviços estão disponíveis em cada região.
{% endtab %}

{% tab title="Conformidade de dados" %}
Empresas podem ter **regulamentações** que exigem que os dados dos clientes sejam armazenados em locais específicos. Escolha uma região da AWS que esteja em conformidade com esses **requisitos regulatórios** para garantir a **privacidade** e **segurança** dos dados, evitando penalidades e mantendo a confiança dos usuários.
{% endtab %}
{% endtabs %}

***

## <mark style="color:red;">Zonas de disponibilidade</mark>

<figure><img src="../../../.gitbook/assets/image (2) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

Dentro de cada **Região** da AWS, existem **clusters** de **Zonas de Disponibilidade (AZs)**. Cada AZ é composta por **um ou mais datacenters**, que têm **redundância de energia**, **rede** e **conectividade**. Esses datacenters estão localizados em **locais discretos** e não divulgados, mas são interligados por **links de alta velocidade** e **baixa latência**, garantindo **alta disponibilidade** e **confiabilidade** dos serviços.

Cada AZ é identificada por um **nome de código** que inclui uma letra no final do código da Região. Por exemplo:

* **"us-east-1a"** refere-se à AZ 'a' na Região **"us-east-1"** (Norte da Virgínia).
* **"sa-east-1b"** indica a AZ 'b' na Região **"sa-east-1"** (São Paulo).

Se você encontrar um recurso em **"us-east-1c"**, isso indica que o recurso está localizado na AZ 'c' da Região **"us-east-1"**.

***

### <mark style="color:red;">**Escopo dos produtos da AWS**</mark>

Os **recursos da AWS** podem ser implantados em diferentes níveis:

* **Zona de Disponibilidade (AZ)**
* **Região**
* **Global**

Cada **serviço** tem características específicas de **escopo**, o que pode impactar a **arquitetura** da sua aplicação.

Quando um serviço opera com **escopo de Região**:

* Você **seleciona a Região** onde deseja implantar o serviço.
* Não é necessário **especificar uma AZ** individual durante a implantação.
* O serviço é **gerenciado automaticamente pela AWS** para aumentar a **durabilidade** e a **disponibilidade** dos dados.

Por outro lado, alguns serviços exigem que você especifique uma Zona de Disponibilidade (AZ) .

Para alguns serviços com **escopo de AZ**:

* É necessário **especificar uma Zona de Disponibilidade (AZ)** durante a configuração.
* A responsabilidade de garantir a **durabilidade** e a **alta disponibilidade** dos recursos dentro da AZ escolhida é **sua**.

É **essencial** entender as diferenças de escopo ao projetar sua **arquitetura** na AWS, pois:

* O **escopo do serviço** afeta diretamente como você **configura**, **gerencia** e garante a **resiliência** da sua aplicação na nuvem.

***

### <mark style="color:red;">**Manter a resiliência**</mark>

Para garantir a **disponibilidade contínua** da sua aplicação na nuvem:

* **Adote práticas** que promovam **alta disponibilidade** e **resiliência**.
* Uma estratégia recomendada é usar **serviços gerenciados com escopo de região**, que já incluem **níveis elevados de disponibilidade** e **resiliência** integrados.

Quando não for possível usar **serviços gerenciados com escopo de região**:

* **Configure sua carga de trabalho** para ser **replicada em múltiplas Zonas de Disponibilidade (AZs)**.
* **Recomenda-se** configurar sua aplicação em **duas AZs** no mínimo.
* Se uma AZ enfrentar uma **falha**, a aplicação continuará operando na **segunda AZ**, que pode assumir o **tráfego**.

A **abordagem distribuída** em várias Zonas de Disponibilidade (AZs):

* **Reduz o impacto** de possíveis **falhas locais**.
* Melhora a **resiliência global** da sua **infraestrutura na nuvem**.
* Assegura que sua aplicação permaneça **disponível** para os usuários, mesmo diante de **eventos inesperados**.

<figure><img src="../../../.gitbook/assets/image (3) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

***

## <mark style="color:red;">**Recursos**</mark>&#x20;

[Infraestrutura global](https://aws.amazon.com/about-aws/global-infrastructure/)

[Documentação de infraestrutura global da AWS](https://docs.aws.amazon.com/whitepapers/latest/aws-overview/global-infrastructure.html)

[Zonas de disponibilidade e regiões da AWS](https://aws.amazon.com/about-aws/global-infrastructure/regions\_az/)

[Endpoints de produto da AWS](https://docs.aws.amazon.com/general/latest/gr/rande.html)

[Produtos regionais da AWS](https://aws.amazon.com/about-aws/global-infrastructure/regional-product-services/)

***
