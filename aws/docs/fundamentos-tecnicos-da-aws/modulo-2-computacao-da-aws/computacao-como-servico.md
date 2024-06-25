# Computação como Serviço

***

## <mark style="color:red;">Servidores</mark>

Para hospedar uma aplicação, o componente fundamental necessário é um servidor, que é responsável por lidar com solicitações HTTP e fornecer respostas aos clientes no modelo cliente-servidor. Esse modelo também se aplica a qualquer comunicação baseada em API.

Um servidor é um computador ou conjunto de computadores conectados à Internet que atendem aos sites para os usuários da Internet, processando suas solicitações. Ele fornece capacidade de CPU, memória e rede necessárias para processar as requisições dos usuários e enviar respostas.

Existem várias opções de servidores HTTP comuns:

* Opções do Windows incluem o IIS (Internet Information Services).
* Opções do Linux incluem o Apache HTTP Web Server, Nginx e Apache Tomcat.

Para executar um servidor HTTP na AWS, você pode utilizar serviços que oferecem poder computacional através do Console de Gerenciamento da AWS. Esses serviços permitem configurar e gerenciar servidores conforme as necessidades da sua aplicação e demandas de tráfego.

Você pode fazer login no console e visualizar a lista completa do AWS Compute Services.

<figure><img src="../../.gitbook/assets/image (7) (1).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:red;">Escolha a opção de computação certa</mark>

Ao configurar servidores na AWS para sua infraestrutura, é crucial entender as opções de computação disponíveis e escolher aquela mais adequada para cada caso de uso. Existem três tipos fundamentais de opções de computação:&#x20;

* Máquinas virtuais (VMs)
* Serviços de contêiner&#x20;
* Computação sem servidor.

As máquinas virtuais são a escolha mais fácil de compreender para aqueles familiarizados com infraestrutura. Uma VM emula um servidor físico, permitindo a instalação de um servidor HTTP para executar aplicações. Na AWS, essas VMs são chamadas de Amazon Elastic Compute Cloud (Amazon EC2). Para usar EC2, você instala um hipervisor em uma máquina host, que provisiona recursos para criar e operar suas VMs. A AWS gerencia os detalhes de operação das máquinas host, incluindo o sistema operacional convidado das VMs.

Alguns serviços de computação da AWS são construídos sobre EC2 ou utilizam conceitos internos de virtualização. Compreender esses fundamentos é crucial antes de explorar opções como serviços de contêinerização e computação sem servidor.

***

## <mark style="color:red;">**Recursos**</mark>

[Whitepaper de serviços de computação](https://docs.aws.amazon.com/whitepapers/latest/aws-overview/compute-services.html)

[Computação na AWS](https://aws.amazon.com/products/compute/)

[Blog de computação da AWS](https://aws.amazon.com/blogs/compute/)

***
