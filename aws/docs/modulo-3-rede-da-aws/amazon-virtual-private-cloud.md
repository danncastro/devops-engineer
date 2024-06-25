---
description: >-
  Uma virtual private cloud (VPC) é uma rede isolada que você cria na Nuvem AWS,
  semelhante a uma rede tradicional em um datacenter.
---

# Amazon Virtual Private Cloud

***

## <mark style="color:red;">**Amazon VPC**</mark>

Ao criar uma VPC, você precisa escolher três fatores principais:

#### <mark style="color:blue;">**Nome da VPC**</mark>

Identifica sua VPC de forma única.

#### <mark style="color:blue;">**Região**</mark>

A região onde a VPC ficará ativa. Cada VPC pode abranger várias zonas de disponibilidade dentro da região selecionada.

#### <mark style="color:blue;">**Intervalo de IP em notação CIDR**</mark>

Define o tamanho da rede. Cada VPC pode ter até quatro intervalos de IP `/16`.

Com essas informações, a AWS provisiona a rede e os endereços IP correspondentes.

<figure><img src="https://explore.skillbuilder.aws/files/a/w/aws_prod1_docebosaas_com/1719277200/s1PqlMxm0AztwotOhL-USw/tincan/954352_1676568571_p1gpdis23dphj1i0b12fk1vub1t4o4_zip/assets/ms62YrBx0r9beOuN_gBIQRKAAJm-Ejrep.png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:red;">Criar uma sub-rede</mark>

Após criar sua VPC, você precisa criar sub-redes dentro dela. Sub-redes são redes menores dentro da sua rede principal, similares às redes de área local virtuais (VLANs) em uma rede on-premises. Em redes on-premises, sub-redes são usadas para isolar ou otimizar o tráfego de rede. Na AWS, sub-redes fornecem opções de alta disponibilidade e conectividade para seus recursos.

Ao criar uma sub-rede, você deve especificar:

#### <mark style="color:blue;">**A VPC onde a sub-rede será ativa**</mark>

Por exemplo, VPC (10.0.0.0/16).

#### <mark style="color:blue;">**Zona de disponibilidade**</mark>

A zona específica onde a sub-rede estará ativa. Por exemplo, AZ1.

#### <mark style="color:blue;">**Bloco CIDR para a sub-rede**</mark>

Deve ser um subconjunto do bloco CIDR da VPC. Por exemplo, 10.0.0.0/24.

Quando você lança uma instância do EC2, ela é executada dentro de uma sub-rede, que está localizada na zona de disponibilidade escolhida.

<figure><img src="https://explore.skillbuilder.aws/files/a/w/aws_prod1_docebosaas_com/1719277200/s1PqlMxm0AztwotOhL-USw/tincan/954352_1676568571_p1gpdis23dphj1i0b12fk1vub1t4o4_zip/assets/wQv1xQ5HjvooxuDQ_KxREwnUZMmYjuiXr.png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:red;">**Alta disponibilidade com uma VPC**</mark>

Ao criar suas sub-redes, é importante considerar a alta disponibilidade. Para garantir redundância e tolerância a falhas, crie pelo menos duas sub-redes em duas zonas de disponibilidade diferentes.

Como discutido anteriormente, é importante lembrar que "tudo falha o tempo todo". Na rede de exemplo, se uma das zonas de disponibilidade falhar, seus recursos ainda estarão disponíveis na outra zona como backup. Isso assegura que sua aplicação permaneça acessível mesmo diante de falhas em uma das zonas de disponibilidade.

<figure><img src="https://explore.skillbuilder.aws/files/a/w/aws_prod1_docebosaas_com/1719277200/s1PqlMxm0AztwotOhL-USw/tincan/954352_1676568571_p1gpdis23dphj1i0b12fk1vub1t4o4_zip/assets/a1qzleKqA_-x98VS_dkTjO3U_sYK8UrG5.png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:red;">**IPs reservados**</mark>

Para que a AWS configure sua VPC adequadamente, a AWS reserva cinco endereços IP em cada sub-rede. Esses endereços são usados para roteamento, **Domain Name System (DNS)** e gerenciamento de rede.

Por exemplo, considere uma VPC com o intervalo de IP `10.0.0.0/22`. Essa VPC tem um total de **1.024 endereços IP**. Esse total é dividido em quatro sub-redes de tamanho igual, cada uma com um intervalo de IP `/24`, contendo **256 endereços IP**. De cada um desses intervalos, apenas **251 endereços IP** estão disponíveis para uso, pois a AWS reserva cinco.

<figure><img src="https://explore.skillbuilder.aws/files/a/w/aws_prod1_docebosaas_com/1719277200/s1PqlMxm0AztwotOhL-USw/tincan/954352_1676568571_p1gpdis23dphj1i0b12fk1vub1t4o4_zip/assets/8X00JPWTAtA-yJ6E_wu1sr-tFxpPkIRHM.jpg" alt=""><figcaption></figcaption></figure>

Os cinco endereços IP reservados são:

Endereço de rede (primeiro endereço do bloco).

1. Gateway padrão (segundo endereço do bloco).
2. DNS da AWS (terceiro endereço do bloco).
3. Endereço reservado para uso futuro (quarto endereço do bloco).
4. Endereço de broadcast (último endereço do bloco).

Esses endereços reservados podem afetar o design da sua rede. Um ponto de partida comum para iniciantes é criar uma VPC com um intervalo de IP `/16` e sub-redes com intervalo de IP `/24`. Isso fornece uma grande quantidade de endereços IP para trabalhar nos níveis de VPC e sub-rede.

***

### <mark style="color:red;">Gateways</mark>

#### <mark style="color:blue;">**Gateway da Internet**</mark>

Para permitir a conectividade com a Internet para sua VPC, você deve criar um **Internet Gateway**. Pense nele como um modem: assim como um modem conecta seu computador à Internet, o gateway da Internet conecta sua VPC à Internet. Diferente do modem residencial, que pode ficar inativo ou offline, um gateway da Internet é altamente disponível e escalável. Após a criação, você anexa o gateway da Internet à sua VPC.

#### <mark style="color:blue;">**Gateway Privado Virtual**</mark>

Um **Virtual Private Gateway,** conecta sua VPC na AWS a outra rede privada. Depois de criar e anexar um gateway privado virtual a uma VPC, ele atua como a âncora do lado da AWS da conexão. Do outro lado, você precisará de um gateway do cliente conectado à outra rede privada. Esse gateway do cliente pode ser um dispositivo físico ou uma aplicação de software. Com ambos os gateways em funcionamento, você pode estabelecer uma conexão VPN criptografada entre as duas redes.

***

## <mark style="color:red;">**Recursos**</mark>

[VPC com sub-redes públicas e privadas (NAT)](https://docs.aws.amazon.com/vpc/latest/userguide/VPC\_Scenario2.html)

[Tabelas de rotas personalizadas](https://docs.aws.amazon.com/vpc/latest/userguide/VPC\_Route\_Tables.html#CustomRouteTables)

[Gateway do cliente](https://docs.aws.amazon.com/vpn/latest/s2svpn/how\_it\_works.html#CustomerGateway)

[O que é a Amazon VPC?](https://docs.aws.amazon.com/vpc/latest/userguide/what-is-amazon-vpc.html)

[VPCs e sub-redes](https://docs.aws.amazon.com/vpc/latest/userguide/VPC\_Subnets.html)

***
