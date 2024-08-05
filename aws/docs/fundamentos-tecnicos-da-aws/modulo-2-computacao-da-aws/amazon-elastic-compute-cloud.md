# Amazon Elastic Compute Cloud

***

## <mark style="color:red;">Amazon EC2</mark>

<figure><img src="../../.gitbook/assets/image (8) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

O Amazon EC2 é um serviço na nuvem que oferece capacidade computacional escalável e segura. Ele permite criar e gerenciar servidores virtuais conhecidos como instâncias do EC2. Apesar de ser frequentemente associado a servidores web, EC2 é versátil e pode suportar uma ampla variedade de cargas de trabalho.

Para configurar uma instância do EC2, você utiliza o Console de Gerenciamento da AWS, a Interface de Linhas de Comando (CLI) da AWS, SDKs da AWS, ferramentas de automação ou serviços de orquestração de infraestrutura. Durante a criação de uma instância, você precisa especificar:

| Especificações de hardware                                                               | Configurações lógicas                                                                                                                                                                                                                                                                                                     |
| ---------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Como CPU, memória, rede e armazenamento necessários para suas necessidades de aplicação. | Tais como a rede onde a instância será lançada, regras de firewall (grupos de segurança), métodos de autenticação e o sistema operacional desejado.                                                                                                                                                                       |
|                                                                                          | Para iniciar uma instância do EC2, você escolhe uma imagem de máquina da Amazon (AMI), que é uma imagem pré-configurada contendo o sistema operacional e outros softwares necessários para sua aplicação. Este processo define o ambiente inicial da instância, que pode ser posteriormente ajustado conforme necessário. |

***

### <mark style="color:red;">Imagem de máquina da Amazon</mark>

No contexto da infraestrutura tradicional, o processo de provisionamento de um servidor envolve a instalação do sistema operacional através de discos de instalação, unidades de instalação ou assistentes de instalação pela rede. Na AWS, por outro lado, o processo é simplificado, pois a instalação do sistema operacional não é uma preocupação direta do usuário. Em vez disso, o sistema operacional já está integrado na **AMI (Amazon Machine Image)** que você seleciona.

Ao escolher uma AMI na AWS, você pode configurar diversos aspectos, como:

| Sistema Operacional                                                               | Mapeamentos de Armazenamento                                                             |
| --------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------- |
| A AMI já inclui uma imagem pré-configurada do sistema operacional de sua escolha. | Você pode especificar como os volumes de armazenamento serão conectados à instância EC2. |

| Arquitetura                                                                                                    | Software Adicional                                                                                         |
| -------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------- |
| Você pode selecionar a arquitetura da instância, como ARM de **32 bits, 64 bits** ou outros tipos compatíveis. | Algumas AMIs podem incluir software adicional pré-instalado, facilitando o setup inicial de sua aplicação. |

Essa abordagem permite uma rápida e consistente implementação de servidores na nuvem AWS, eliminando a necessidade de configurar manualmente cada componente do sistema operacional, o que é típico em ambientes tradicionais de infraestrutura física.

***

### <mark style="color:red;">Relação entre AMIs e instâncias do EC2</mark>

As instâncias do EC2 são essencialmente versões em execução do que está definido em uma AMI, de forma similar a como um bolo assado é uma versão em execução de uma receita de bolo. Se você tem familiaridade com desenvolvimento de software, pode fazer uma analogia desse relacionamento com o de uma classe e um objeto.

Uma classe no desenvolvimento de software é algo que é modelado e definido, enquanto um objeto é uma instância específica com a qual se interage. Da mesma maneira, uma AMI na AWS é a definição do que sua instância EC2 será, enquanto a instância EC2 em si é a entidade ativa que você usa para executar e interagir, como hospedar um servidor web para distribuir conteúdo aos usuários.

Quando você inicia uma nova instância EC2, a AWS aloca uma máquina virtual que roda em um hipervisor. A AMI selecionada é então copiada para o volume raiz, que contém a imagem utilizada para inicializar o sistema da instância. Posteriormente, você obtém um servidor no qual pode conectar-se e instalar pacotes e software adicional. Por exemplo, você pode configurar um servidor web junto com o código-fonte da aplicação de diretório de funcionários.

<figure><img src="../../.gitbook/assets/image (9) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

Uma grande vantagem das AMIs é a reutilização. Você pode escolher uma AMI baseada em Linux, configurar o servidor HTTP, pacotes de aplicação e qualquer software adicional necessário para executar sua aplicação. Se precisar criar uma segunda instância EC2 com as mesmas configurações, pode repetir o processo de criação e configuração, ou criar uma nova instância a partir da AMI original. Isso garantirá que sua nova instância tenha as mesmas configurações que a primeira, pois as definições da AMI são replicadas.

<figure><img src="../../.gitbook/assets/image (10) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:red;">Encontre AMIs</mark>

Você pode selecionar uma AMI nas seguintes categorias:

* AMIs de início rápido, que são criadas pela AWS para ajudar você a começar rapidamente
* AMIs do AWS Marketplace, que fornecem software comercial e de código aberto conceituados de fornecedores terceiros
* Minhas AMIs, que são criadas por meio de suas instâncias do EC2
* AMIs da comunidade fornecidas pela comunidade de usuários da AWS
* Crie sua própria imagem personalizada com o EC2 Image Builder

<figure><img src="../../.gitbook/assets/image (11) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

Cada AMI no Console de Gerenciamento da AWS tem um **ID de AMI**, que é prefixado por “**ami-**”, seguido por um hash aleatório de números e letras. Os IDs são exclusivos para cada região da AWS.

***

## <mark style="color:red;">**Recursos**</mark>

[Amazon EC2](https://aws.amazon.com/ec2/)

[Imagens de máquina da Amazon (AMI)](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/AMIs.html)

[Criação de uma AMI Linux com suporte para o Amazon EBS](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/creating-an-ami-ebs.html)

[O o que é o EC2 Image Builder?](https://docs.aws.amazon.com/imagebuilder/latest/userguide/what-is-image-builder.html)

***
