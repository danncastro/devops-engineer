# Questions

***

1. Which resource acts as a virtual firewall that controls the traffic for one or more instances?

* [ ] Amazon Virtual Private Cloud (Amazon VPC)
* [x] Security Groups
* [ ] Network Access Control Lists (ACLs)

> Os Security Groups atuam como firewalls virtuais que controlam o tráfego de entrada e saída para uma ou mais instâncias dentro de uma Amazon Virtual Private Cloud (VPC). Eles são recursos fundamentais para definir permissões de acesso e regras de tráfego, permitindo ou negando comunicações com base em protocolos, portas e endereços IP.

2. How many Availability Zones, at least, make up an AWS Region?

* [ ] One
* [x] Two
* [ ] Three
* [ ] Ten

> A quantidade mínima de Zonas de Disponibilidade (Availability Zones - AZs) que compõem uma Região da AWS é **duas**. Cada Região da AWS começa com pelo menos duas AZs, e algumas Regiões podem eventualmente expandir para três ou mais AZs conforme a demanda e o crescimento dos serviços naquela região.

3. Which location option can be selected when launching an Amazon EC2 instance in an AWS Region?

* [ ] Bucket
* [x] Availability Zone
* [ ] Transit Gateway
* [ ] Container

> Ao lançar uma instância EC2, você pode escolher em qual Zona de Disponibilidade (Availability Zone) dentro da Região deseja implantar a instância. As Availability Zones são locais físicos distintos dentro de uma Região da AWS, projetados para serem isolados uns dos outros em termos de falhas de infraestrutura.

4. What is the best description of an AWS Region?

* [ ] The physical location of a single AWS data center
* [x] Multiple, isolated, and physically separate Availability Zones within a geographic area.
* [ ] A combination of exactly two AWS Availabily Zones

> Uma Região da AWS é composta por mwwwwwwwwwwwwwwúltiplas Zonas de Disponibilidade (Availability Zones - AZs), que são áreas geográficas distintas e fisicamente separadas umas das outras dentro de uma mesma região geográfica. As AZs são projetadas para serem isoladas umas das outras em termos de falhas de infraestrutura, proporcionando alta disponibilidade e resiliência para os serviços hospedados na AWS.

5. The default view for the AWS Management Console displays all resources in all Regions.

* [ ] True
* [x] False

> O console de gerenciamento da AWS não exibe todos os recursos em todas as regiões por padrão. Quando você acessa o console pela primeira vez ou quando faz login, geralmente é apresentada uma visão inicial que pode variar, mas não inclui automaticamente todos os recursos de todas as regiões.
>
> Para visualizar recursos em uma região específica, você precisa selecionar a região desejada no console. Cada região da AWS é tratada separadamente em termos de recursos e configurações visíveis no console de gerenciamento.

6. What does Amazon EC2 provide in the cloud that is secure and resizable?

* [ ] Storage capacity
* [ ] Databases tables
* [x] Compute capacity
* [ ] Backup volumes

> Amazon EC2 (Elastic Compute Cloud) fornece capacidade de computação na nuvem que é segura e redimensionável. Isso significa que você pode provisionar e ajustar facilmente servidores virtuais (instâncias) de acordo com as necessidades da sua aplicação, modificando recursos como CPU, memória e armazenamento conforme necessário.

7. EC2 Instance Connect can help users connect to an instance. What are the two components of the connection?

* [ ] Linux/RDP
* [x] Linux/SSH
* [ ] Windows/RDP
* [ ] Windows/SSH

> EC2 Instance Connect ajuda os usuários a se conectarem a uma instância EC2.

8. Which type of scaling is used when the number of EC2 instances is increased behind a load balancer?

* [ ] Vertical
* [x] Horizontal

> Escalabilidade horizontal refere-se ao aumento do número de instâncias ou recursos distribuídos, como instâncias EC2, para lidar com um maior volume de tráfego ou carga de trabalho. Nesse contexto, adicionar mais instâncias EC2 (por exemplo, aumentar o tamanho do grupo de instâncias atrás de um balanceador de carga) é um exemplo de escalabilidade horizontal, o que permite distribuir melhor a carga e melhorar a disponibilidade do serviço.

9. What is an example of an Amazon EC2 instance type?

* [x] m5.large
* [ ] ARM64
* [ ] web\_server
* [ ] Bucket

> Os tipos de instância EC2, como "m5.large", representam diferentes combinações de CPU, memória, armazenamento e capacidades de rede para atender a diferentes requisitos de carga de trabalho. Cada tipo de instância é otimizado para um conjunto específico de casos de uso e requerimentos de desempenho.

10. An Amazon EBS backed EC2 instance must be in a specific state to change its instance type. Which one?

* [x] Stopped
* [ ] Runing
* [ ] Terminated
* [ ] Imaged

> Para realizar a alteração do tipo de instância, é necessário parar a instância primeiro. Somente quando a instância está parada é que você pode modificar seu tipo (instance type).

11. What can connect a user to an Amazon EC2 Linux instance through an SSH client?

* [ ] Instance ID
* [x] Public IP address
* [ ] Metadata

> O ID da instância (Option 1) é usado para identificar a instância na AWS, mas não é usado diretamente para conectar-se via SSH. O metadados (Option 3) são informações sobre a instância que podem ser acessadas internamente pela instância, mas não são usadas diretamente para estabelecer uma conexão SSH do usuário.
>
> \
> O endereço IP público da instância EC2 é necessário para estabelecer a conexão SSH a partir de um cliente SSH como o OpenSSH.

12. What can be changed to scale an Amazon EC2 instance to the demands of workload?

* [ ] Region
* [ ] Availability Zone
* [ ] DNS
* [x] Type

> O "tipo" (instance type) de uma instância EC2 pode ser modificado para aumentar ou diminuir a capacidade de CPU, memória e armazenamento conforme necessário para lidar com variações na carga de trabalho.

13. What is 10.0.0.0/16 an exemple of?

* [ ] &#x20;IP Address
* [x] CIDR block
* [ ] Security group rule
* [ ] Instance ID

> O CIDR (Classless Inter-Domain Routing) é um método para designar um intervalo de endereços IP que consiste em um endereço IP de rede seguido por uma barra (/) e um número que especifica quantos bits do endereço IP são destinados à rede.

14. What is true about default virtual private clouds (VPCs)? (Select THREE)

* [x] All instances deployed to a default VPC are private
* [ ] All instances deployed to default VPC are public
* [x] A default VPC is created in each AWS Region in an account
* [x] Default VPC can be modified.

15. What can be used to restrict access to specific Amazon EC2 instances? (Select TWO)

* [ ] VPC route tables
* [ ] VPC peering
* [x] Security groups
* [x] Private subnets

> **Security groups**: São firewalls virtuais que controlam o tráfego de rede para uma ou mais instâncias. Você pode definir regras de entrada e saída para permitir ou negar tráfego com base no protocolo, na porta e no endereço IP.
>
> **Private subnets**: Sub-redes privadas dentro de um VPC que não têm uma rota direta para a internet. Ao colocar instâncias em sub-redes privadas e configurar corretamente as rotas e gateways, você pode restringir o acesso direto às instâncias apenas a partir de redes ou serviços específicos.

16. EC2 Instance Connect requires a user-create and downloaded SSH key.

* [ ] True
* [x] False

> EC2 Instance Connect não requer que o usuário crie ou baixe uma chave SSH. Em vez disso, ele usa chaves SSH gerenciadas pela AWS para autenticar e permitir que os usuários se conectem às instâncias EC2 de maneira segura, sem que os usuários precisem gerenciar suas próprias chaves SSH.

17. NAT gateways allow instances in a private subnet to connect to the internet.

* [x] True
* [ ] False

> NAT Gateways permitem que instâncias em sub-redes privadas se conectem à internet de forma segura, ao agirem como intermediários entre as instâncias na sub-rede privada e a internet pública. Isso é feito redirecionando o tráfego de saída da instância através do NAT Gateway, que possui um endereço IP público associado para comunicação externa.

18. What can be configured when creating a new Amazon EC2 instance? (Select TWO).

* [x] Instance type
* [ ] S3 bucket
* [ ] Database engine
* [x] Security group

> **Tipo de instância**: Define a capacidade computacional da instância, como quantidade de CPU, memória RAM e armazenamento temporário.
>
> **Grupo de segurança**: Define as regras de firewall virtual que controlam o tráfego de rede para a instância, especificando quais protocolos, portas e endereços IP são permitidos ou bloqueados.

19. A company wants to allow users from the internet (0.0.0.0/0) to visit their website. Which traffic types should they add to their inbound security group rules? (Select TWO).

* [ ] RDP
* [x] HTTP
* [ ] SSH
* [x] HTTPS
* [ ] IMAP

> **HTTP (80)**: Usado para tráfego web não criptografado.
>
> **HTTPS (443)**: Usado para tráfego web criptografado usando SSL/TLS.

20. &#x20;Which key-value pair can be used to describe an Amazon EC2 instance through custom content and metadata?

* [ ] EBS
* [ ] Definitions
* [ ] Policies
* [x] Tags

> As tags são pares de chave-valor que você pode atribuir a recursos na AWS, como instâncias EC2, volumes EBS, snapshots, etc. Elas são usadas para categorizar e identificar recursos, além de permitir a aplicação de políticas e automatização de processos com base nessas tags.

21. By default, Amazon RDS will retain a backup of a DB instance for a period of 7 days.

* [x] True
* [ ] False

> Por padrão, o Amazon RDS (Relational Database Service) retém backups automáticos de uma instância de banco de dados por um período de 7 dias. Durante esse período, você pode restaurar o banco de dados para qualquer momento durante o período de retenção de backup de 7 dias.

22. Which functions does Amazon RDS perform on the bhalf of users? (Select THREE)

* [x] Provision the infrastructure capacity
* [x] Install the database software
* [x] Automate data backups
* [ ] Create database users

> Provisionar a capacidade de infraestrutura: Amazon RDS gerencia a configuração e a escalabilidade da infraestrutura subjacente necessária para executar o banco de dados.
>
> Instalar o software do banco de dados: Amazon RDS gerencia a instalação e a configuração inicial do software do banco de dados escolhido.
>
> Automatizar backups de dados: Amazon RDS fornece backups automáticos e recuperação de falhas para garantir a durabilidade dos dados.

23. What should users do if their Amazon RDS queries seem to be running slowly? (Select THREE)

* [x] Enable enhanced monitoring on the database instance
* [x] Review the slow query logs for MariaDB or MySQL
* [ ] Review the client-side SQL Server traces.
* [x] Modify the DB instance to run as a Multi-AZ deployment

> Habilitar o monitoramento aprimorado na instância do banco de dados: Isso permite monitorar métricas detalhadas de desempenho que podem ajudar a identificar gargalos.
>
> Revisar os logs de consultas lentas para MariaDB ou MySQL: Esses logs registram consultas que estão levando mais tempo para serem executadas, ajudando a identificar problemas de desempenho específicos.
>
> Modificar a instância do banco de dados para executar como um deployment Multi-AZ (disponibilidade em várias zonas): Embora isso não seja diretamente relacionado à melhoria de desempenho, pode melhorar a resiliência e disponibilidade do banco de dados, o que pode ser um fator importante em cenários de alto tráfego.

24. What happens if a weekly maintenance window is not specified when creating an RDS DB instance?

* [x] A 30-minute window will be assigned by default
* [ ] The DB instance will not start
* [ ] A maintenance window will not be created
* [ ] A read replica instance will automatically be created.

25. Which database engines does Amazon RDS support? (Select THREE)

* [ ] DB2
* [x] Oracle
* [x] PostgreSQL
* [x] MySQL

26. &#x20;What is an Amazon S3 bucket?

* [ ] An optional organization folder (objects can also be stored at the root of an Amazon S3 infrastructure)
* [ ] A container for objects stored in Amazon S3 (every object is contained in a bucket)
* [ ] An alias for a folder within Amazon S3

> Um bucket do Amazon S3 é um recipiente de nível superior para armazenar objetos, onde cada objeto é armazenado dentro de um bucket específico. Não é um alias para uma pasta dentro do Amazon S3; ao contrário, os objetos podem ser armazenados diretamente no nível raiz de um bucket.

27. Which format are Amazon S3 bucket policies and IAM policies written in?

* [x] JSON
* [ ] HTML
* [ ] CSV
* [ ] XML

> JSON é o formato padrão usado para definir políticas tanto para buckets do Amazon S3 quanto para políticas IAM na AWS. É um formato de texto simples que é fácil de ler e escrever, além de ser amplamente suportado por ferramentas e APIs da AWS.

28. How can an Amazon S3 bucket owner grant public access to a bucket when configuring it fot website hosting?

* [ ] S3 buckets are publicly accessible by default
* [ ] Enabling website hosting on an S3 bucket enables public access by default
* [x] The S3 bucket owner can create a bucket policy.

> Ao criar uma política de bucket, o proprietário pode especificar as condições sob as quais o conteúdo do bucket é acessível publicamente. Isso inclui permitir acesso de leitura a todos (por exemplo, definindo uma política que permite o princípio `*` ou um endereço IP específico).

29. Which AWS service provides object storage and is built to store and retrieve any amount of data from anywhere on the internet?

* [ ] Amazon Elastic Block Store (Amazon EBS)
* [ ] Amazon Simple Notification Service (Amazon SNS)
* [x] Amazon Simple Storage Service (Amazon S3)
* [ ] Amazon Elastic Compute Cloud (Amazon EC2)

> O Amazon S3 é um serviço de armazenamento de objetos altamente escalável, durável e seguro, projetado para armazenar e recuperar grandes quantidades de dados de forma eficiente pela internet

30. What can be included when creating an Amazon Machine Image (AMI)? (Select THREE)

* [x] Installed software
* [x] Operating System
* [ ] Public IP address
* [x] EBS snapshots

> **Software instalado**: A AMI pode capturar o estado atual do software instalado na instância EC2.
>
> **Sistema operacional**: A AMI inclui a imagem do sistema operacional da instância EC2.
>
> **Snapshots de EBS**: Você pode incluir snapshots de volumes EBS associados à instância EC2 na AMI, capturando assim os dados persistentes armazenados nesses volumes.

31. Virtual private cloud (VPC) peering connections can route traffic by using private IPv4 or IPv6 addresses.

* [x] True
* [ ] False

> As conexões de VPC peering podem rotear tráfego usando endereços IPv4 ou IPv6 privados. Isso permite que instâncias em VPCs diferentes se comuniquem usando endereços IP privados, desde que exista uma conexão de peering configurada entre os VPCs correspondentes.

32. What is true about virtual private cloud (VPC) peering connections? (Select TWO)

* [x] There is no single point of failure for communication
* [x] There is no bandwidth bottleneck
* [ ] VPC peering connections require a public subnet.

> **Não há um único ponto de falha para a comunicação:** As conexões de peering de VPC são estabelecidas entre VPCs em uma única região da AWS e não possuem um único ponto de falha, desde que a infraestrutura de rede subjacente esteja funcionando corretamente.
>
> **Não há gargalo de largura de banda:** As conexões de peering de VPC aproveitam a rede da AWS para rotear o tráfego entre as VPCs, garantindo que a largura de banda seja escalável conforme necessário, sem restrições de gargalo de tráfego.\
> **As conexões de peering de VPC exigem uma sub-red pública:** É incorreta, pois as conexões de peering de VPC não requerem uma sub-rede pública; elas podem ser estabelecidas entre VPCs que estão em sub-redes privadas.

33. Virtual private clouds (VPCs) can be peered across AWS Region.

* [x] True
* [ ] False

> Com o AWS VPC Peering, é possível estabelecer conexões entre VPCs diferentes, independentemente da região em que estão localizadas.

34. When peering relationships are stablished betewen virtual private clouds (VPCs) across different AWS Regions, traffic always stays on the global AWS backbone and never traverses the public internet.

* [x] True
* [ ] False

35. A virtual private cloud (VPC) peering connection can be established only between two VPCs.

* [x] True
* [ ] False

> A conexão de peering de Virtual Private Cloud (VPC) pode ser estabelecida apenas entre duas VPCs. Isso significa que uma conexão de peering conecta diretamente dois VPCs e não pode ser expandida para conectar mais de dois VPCs ao mesmo tempo.

36. &#x20;Which type of deployment model is used in cloud computing? (Select THREE)

* [x] Cloud
* [ ] Partner
* [x] Hybrid
* [x] On premises

> **Nuvem (Cloud)**: Refere-se à implantação de serviços ou recursos em um provedor de serviços de nuvem pública, como AWS, Azure, Google Cloud, etc.
>
> **Híbrido (Hybrid)**: Este modelo combina serviços de nuvem pública com recursos de infraestrutura local (on premises), permitindo integração e portabilidade de dados e aplicações entre ambos.
>
> **No local (On premises)**: Refere-se à infraestrutura tradicional de TI, onde os recursos são mantidos e gerenciados internamente pela organização, sem usar serviços de nuvem pública.

37. &#x20;Which AWS service provides resizable compute capacity in the cloud, designed to help developers with web-scale computing?

* [x] Amazon Elastic Compute Cloud (Amazon EC2)
* [ ] Amazon Simple Storage Service (Amazon S3)
* [ ] Amazon SageMaker

> O Amazon EC2 permite que os usuários obtenham e configurem capacidade de computação virtual conforme necessário, proporcionando flexibilidade para escalar recursos de computação de acordo com os requisitos específicos de aplicativos e cargas de trabalho.

38. A developer would like to set up a simple, low-cost, static website that delivers HTML, JavaScript, images, video, and other files to visitors. Which action should the developer take?

* [x] Create an Amazon S3 bucket, and then enable static website hosting
* [ ] Set up an Amazon EC2 instance, and then install WordPress on the instance
* [ ] Use Amazon Lightsail to launch and manage a web server
* [ ] Launch AWS Elastic Beanstalk to configure a web application

> **Amazon S3 (Simple Storage Service)** é um serviço de armazenamento de objetos na AWS, projetado para armazenar e recuperar qualquer quantidade de dados de forma segura e escalável.
>
> Ao criar um bucket no Amazon S3, é possível configurá-lo para hospedagem de site estático. Isso significa que o S3 pode servir diretamente os arquivos HTML, JavaScript, imagens, vídeos, etc., para os visitantes do site.
>
> Esta abordagem é altamente escalável e de baixo custo, pois o Amazon S3 oferece preços competitivos e é dimensionado automaticamente para atender a demandas variáveis de tráfego.

39. The AWS Management Console is recommended for uploading files larger than 160 GB to Amazon S3

* [ ] True
* [x] False

> O AWS Management Console não é recomendado para fazer upload de arquivos tão grandes quanto 160 GB para o Amazon S3 devido a limitações práticas de tamanho de arquivo e à possibilidade de interrupções na conexão durante um upload tão extenso.
>
> Para uploads de arquivos grandes, especialmente acima de alguns gigabytes, é recomendado usar ferramentas como o AWS CLI (Command Line Interface), SDKs (Software Development Kits), ou até mesmo serviços de transferência como o AWS Transfer Family.
>
> Essas ferramentas são mais robustas e oferecem recursos como a capacidade de retomar uploads após interrupções e uma melhor gestão de erros.

40. &#x20;What is the maximum number of objects that an Amazon S3 bucket can store?

* [ ] 1 million
* [ ] 100 billion
* [ ] 1 trillion
* [x] There is no limit

> Amazon S3 é altamente escalável e projetado para armazenar uma quantidade praticamente ilimitada de objetos.
>
> Não há um limite específico no número total de objetos que um bucket do Amazon S3 pode conter.
>
> No entanto, existem limites relacionados ao tamanho individual de cada objeto e ao tamanho total do bucket, mas não há um limite absoluto no número de objetos
