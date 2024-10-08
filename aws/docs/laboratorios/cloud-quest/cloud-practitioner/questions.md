# Questions

***

1. Which resource acts as a virtual firewall that controls the traffic for one or more instances?

* [ ] Amazon Virtual Private Cloud (Amazon VPC)
* [x] Security Groups
* [ ] Network Access Control Lists (ACLs)

> Os Security Groups atuam como firewalls virtuais que controlam o tráfego de entrada e saída para uma ou mais instâncias dentro de uma Amazon Virtual Private Cloud (VPC). Eles são recursos fundamentais para definir permissões de acesso e regras de tráfego, permitindo ou negando comunicações com base em protocolos, portas e endereços IP.

2. How many Availability Zones, at least, make up an AWS Region?

* [ ] One
* [ ] Two
* [x] Three
* [ ] Ten

>

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
* [ ] Running
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

22. Which functions does Amazon RDS perform on the behalf of users? (Select THREE)

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
* [x] Review the client-side SQL Server traces.
* [ ] Modify the DB instance to run as a Multi-AZ deployment

> **Enable enhanced monitoring on the database instance**: Ativar o monitoramento aprimorado (Enhanced Monitoring) pode fornecer métricas detalhadas e em tempo real sobre o desempenho da instância de banco de dados, o que pode ajudar a identificar problemas de recursos e desempenho que estão afetando a execução das consultas.
>
> **Review the slow query logs for MariaDB or MySQL**: Revisar os logs de consultas lentas para MariaDB ou MySQL pode ajudar a identificar quais consultas estão demorando mais do que o esperado e fornecer insights sobre possíveis melhorias ou otimizações.
>
> **Review the client-side SQL Server traces**: Para instâncias SQL Server, revisar os rastreamentos (traces) do lado do cliente pode fornecer informações detalhadas sobre o desempenho das consultas e ajudar a diagnosticar problemas.
>
>
>
> A opção **Modify the DB instance to run as a Multi-AZ deployment** não é diretamente relevante para a otimização do desempenho das consultas. O deployment Multi-AZ é mais voltado para alta disponibilidade e recuperação de desastres, e não para melhorar o desempenho das consultas.

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

41. Which statements about the scan operation in Amazon DynamoDB are correct? (Select TWO)

* [x] A scan consumes the same amount of read capacity when a filter expression is present.
* [ ] A scan consumes more read capacity when a filter expression is presentwdas
* [x] A filter expression is applied after a scan finishes but before the results are returned

42. &#x20;A company's data archietects designed thir database schema to make the most common and import database queries as fast and as inexpensive as possible. Which AWS service is best suited to achieve their goal?

* [ ] Amazon RDS
* [x] Amazon DynamoDB
* [ ] Amazon Redshift
* [ ] Amazon Neptune

> Amazon DynamoDB é um banco de dados NoSQL totalmente gerenciado que é otimizado para consultas rápidas e escalabilidade automática. Ele é especialmente projetado para lidar com cargas de trabalho de leitura intensiva e fornece latências consistentemente baixas, independentemente do volume de dados. Além disso, permite ajustar a capacidade de leitura e gravação com base nas necessidades específicas da aplicação, o que ajuda a controlar os custos operacionais.

43. &#x20;Which statements about pagination are correct? (Select TWO)

* [x] Which pagination, the query results are divided into "pages" of data that are 1 MB in size (or less)
* [ ] The NextEvaluatedKey from a query responde should be used as the ExclusiveStartKey for the next query request.
* [x] The LastEvaluatedKey from a query response should be used as the ExclusiveStartKey for the next query request

44. After a write operation In Amazon DynamoDB, a read request might not reflect the latest data unless another read request is invoked after a short time. Which consistency type is this?

* [ ] Strongly consistent reads
* [x] Eventually consistent reads
* [ ] Nearly real-time consistency

45. Which AWS service is a key-value and document database that delivers single-digit millisecond performance at any scale?

* [ ] Amazon RDS
* [ ] Amazon Route 53
* [x] Amazon DynamoDB
* [ ] Amazon Aurora

46. What are the basic components of Amazon DynamoDB?

* [ ] Collection, document, filed, and view
* [ ] Tables, primary keys, and sequences
* [x] Tables, items, and attributes

47. Which statements about the query operation in Amazon DynamoDB are correct? (Select TWO)

* [x] &#x20;In a query operation, users must provide the name and a value of the partition key. The sort key is optional.
* [ ] In a query operation, users must provide the name and a value of the partition key as well as the sort key
* [ ] A filter expression cannot contain partition key or sort key attributes.
* [x] A filter expression can contain partition key or sort key attributes

48. Which statements about secondary indexes are correct? (Select THREE)

* [x] A local secondary index is an index that has the same partition key as the base table, but a different sort key.
* [ ] A local secondary index is an index that has the same partition and sort key as the base table
* [x] A global secondary index is an index with a partition key and a sort key that can be different from those on the base table
* [x] A global secondary index has its own provisioned throughput settings for read and write capacity

49. A security group was configured with a rule to allow HTTPS traffic to an instance. What will happen if an HTTP connection is attempted?

* [ ] The security group will allow the incoming connection but will deny the outgoing connection
* [x] Unless there is a rule explicitly allowing HTTP, the security group will deny the connection
* [ ] The security group  will allow the connection because HTTPS implies HTTP as well.

> A razão para isso é que o HTTPS (Hypertext Transfer Protocol Secure) e o HTTP (Hypertext Transfer Protocol) são protocolos diferentes, mesmo que o HTTPS implique uma camada de segurança adicional sobre o HTTP, eles são tratados separadamente pelas regras do grupo de segurança.

50. &#x20;Which AWS service allows two Linux applications, running in different AZs, to share a common file system?

* [x] Amazon Elastic File System (Amazon EFS)
* [ ] Amazon Elastc Block Storage (Amazon EBS)
* [ ] Amazon Simple Storage Service (Amazon S3)

> O Amazon EFS é um sistema de arquivos baseado em NFS que pode ser montado em várias instâncias EC2 em diferentes AZs, permitindo o acesso simultâneo aos arquivos de várias instâncias.
>
> Os outros serviços mencionados são:
>
> **Amazon Elastic Block Store (Amazon EBS)**: Fornece volumes de armazenamento em bloco que são conectados a instâncias EC2 e não podem ser compartilhados entre instâncias em diferentes AZs.
>
> **Amazon Simple Storage Service (Amazon S3)**: Oferece armazenamento de objetos e é ideal para armazenar dados, mas não fornece um sistema de arquivos montável como o EFS.

51. Which protocol does Amazon File System (Amazon EFS) support?

* [ ] Service Message Blocks (SMB)
* [ ] File Transfer Protocol (FTP)
* [x] Network File System (NFS)

> O NFS é um protocolo de sistema de arquivos em rede que permite que instâncias EC2 acessem o sistema de arquivos de forma semelhante a um sistema de arquivos local, facilitando a troca de arquivos entre instâncias e suportando acesso simultâneo a partir de múltiplas instâncias.
>
> Os outros protocolos mencionados são:
>
> **Service Message Blocks (SMB)**: Utilizado por sistemas Windows para compartilhamento de arquivos em rede. O EFS não suporta SMB nativamente.
>
> **File Transfer Protocol (FTP)**: Um protocolo para transferência de arquivos entre sistemas em uma rede. O EFS não usa FTP para acessar arquivos.

52. Which AWS services can access a file system in Amazon Elastic File System (Amazon EFS)? (Select THREE).

* [ ] Amazon Relational Database Service (Amazon RDS)
* [x] Amazon Compute Cloud (Amazon EC2)
* [x] AWS Lambda
* [x] Amazon Sagemaker

> **Amazon EC2**: Instâncias EC2 podem montar e acessar o sistema de arquivos do EFS como se fosse um sistema de arquivos local.
>
> **AWS Lambda**: Funções Lambda podem montar um sistema de arquivos do EFS para acessar dados durante a execução da função, permitindo que você use o armazenamento persistente do EFS.
>
> **Amazon SageMaker**: O Amazon SageMaker pode acessar o sistema de arquivos do EFS para carregar e salvar dados de treinamento e modelos, facilitando a integração com dados armazenados no EFS.
>
> O **Amazon RDS** não pode acessar diretamente um sistema de arquivos do EFS. RDS é um serviço de banco de dados gerenciado e não possui suporte nativo para montar e usar sistemas de arquivos como o EFS.

53. Which resource provides an IP address for an NFSv4 endpoint on which a file system in Amazon Elastic File System (Amazon EFS) can be mounted?

* [ ] An access point
* [ ] A file share
* [x] A mount target
* [ ] A resource policy

> **Mount Target**: Fornece um ponto de acesso na VPC (Virtual Private Cloud) com um IP específico que pode ser utilizado pelas instâncias EC2 para montar o sistema de arquivos EFS. Cada mount target está associado a uma sub-rede dentro da VPC e tem um endereço IP que as instâncias EC2 usam para acessar o EFS.
>
> **Access Point**: Um ponto de acesso (access point) no EFS fornece uma maneira de configurar acesso específico a diretórios dentro do sistema de arquivos, mas não fornece diretamente o IP para montar o sistema de arquivos.
>
> **File Share**: Este termo geralmente se refere a um conceito mais amplo de compartilhamento de arquivos e não se aplica diretamente ao conceito de montar um sistema de arquivos EFS.
>
> **Resource Policy**: Políticas de recursos são usadas para definir permissões e controle de acesso, mas não fornecem endereços IP para montar o sistema de arquivos.

54. A company's data engineers have multiple subnets in an Availability Zone in their virtual private cloud (VPC). Where would they create a mount target when deploying a new Amazon Elastic File System (Amazon EFS) file system?

* [ ] In one of the subnets
* [x] In all of the subnets
* [ ] In all public subnets
* [ ] In all private subnets

> **Em um dos subnets**: Criar um mount target em apenas uma subnet limita o acesso ao sistema de arquivos apenas para as instâncias nessa subnet específica. Isso pode não ser suficiente se as instâncias em outras subnets também precisarem acessar o EFS.
>
> **Em todos os subnets**: Criar mount targets em todos os subnets relevantes dentro da Zona de Disponibilidade garante que todas as instâncias nessas subnets possam acessar o sistema de arquivos EFS.
>
> **Em todas as subnets públicas**: Isso não é necessário a menos que você precise especificamente que o sistema de arquivos esteja acessível a partir de subnets públicas. Normalmente, você criaria mount targets em subnets privadas para acesso interno.
>
> **Em todas as subnets privadas**: Isso é semelhante a criar mount targets em todos os subnets, mas focado apenas em subnets privadas, se sua arquitetura usar apenas subnets privadas para as instâncias.

55. Which statements about the query operation in Amazon DynamoDB are correct?(Select TWO.)

* [x] In a query operation, users must provide the name and a value of the partition key. The sort key is optional
* [ ] In a query operation, users must provide the name and a value of the partition key as well as the sort key
* [ ] A filter expression cannot contain partition key or sort key attributes
* [x] A filter expression can contain partition key or sort key attributes.

>
>
> **Em uma operação de consulta, os usuários devem fornecer o nome e um valor da chave de partição. A chave de ordenação é opcional.**
>
> * Quando você realiza uma operação de consulta no DynamoDB, é necessário fornecer o nome e o valor da chave de partição. A chave de ordenação é opcional; se você quiser consultar todos os itens que têm a mesma chave de partição, você pode omitir a chave de ordenação, mas se quiser restringir ainda mais os resultados, pode especificar a chave de ordenação.
>
> **Uma expressão de filtro pode conter atributos de chave de partição ou chave de ordenação.**
>
> * Embora a expressão de filtro não possa ser usada para restringir a consulta baseada apenas na chave de partição ou chave de ordenação (essas são usadas para buscar os dados), você pode usar uma expressão de filtro para refinar ainda mais os resultados retornados pela consulta, incluindo atributos da chave de partição ou chave de ordenação. No entanto, vale notar que a expressão de filtro é aplicada após a consulta inicial, então, os itens que não correspondem à expressão de filtro ainda são lidos e retornados pela consulta, mas não estarão nos resultados finais.

56. Amazon S3 bucket policy sizes have a 20 KB limit.

* [x] True
* [ ] False

> A política de um bucket do Amazon S3 tem um limite de tamanho de 20 KB. Isso significa que o tamanho total de uma política de bucket, incluindo todos os blocos e declarações, não pode exceder 20 KB. Se a política exceder esse limite, você precisará simplificar ou dividir a política em várias partes.

57. What are the three primary management functions of Amazon EC2 Auto Scaling? (Select THREE)

* [x] Monitor the health of running instances.
* [ ] Block traffic to unsecured instances.
* [x] Replace impaired instances automatically
* [x] Balance capacity across Availability Zones.

> **Monitorar a saúde das instâncias em execução**: O Auto Scaling monitora a saúde das instâncias EC2 em seu grupo. Se uma instância for considerada não saudável, o Auto Scaling pode substituir a instância automaticamente.
>
> **Substituir instâncias comprometidas automaticamente**: Se uma instância se tornar não saudável ou apresentar problemas, o Auto Scaling pode automaticamente substituir a instância comprometida por uma nova, garantindo que o número desejado de instâncias esteja em execução.
>
> **Equilibrar a capacidade entre Zonas de Disponibilidade**: O Auto Scaling pode distribuir automaticamente as instâncias entre várias Zonas de Disponibilidade para melhorar a disponibilidade e a tolerância a falhas.
>
> A opção **"Bloquear o tráfego para instâncias não seguras"** não é uma função direta do EC2 Auto Scaling. Isso geralmente é tratado por outras medidas de segurança, como grupos de segurança e listas de controle de acesso.

58. Which types of AWS Auto Scaling are valid?(Select THREE)

* [x] Scheduled
* [x] Dynamic
* [x] Predictive
* [ ] Spot
* [ ] On-Demand

> **Scheduled**: O Auto Scaling programado permite que você configure escalonamentos automáticos em horários específicos, com base em um cronograma. Por exemplo, você pode configurar o Auto Scaling para aumentar a capacidade durante as horas de pico e reduzir durante os períodos de baixa demanda.
>
> **Dynamic**: O Auto Scaling dinâmico ajusta automaticamente a capacidade com base em condições de demanda em tempo real, como a carga de CPU ou a utilização da memória. Ele responde a métricas e políticas definidas para escalar para cima ou para baixo conforme necessário.
>
> **Predictive**: O Auto Scaling preditivo usa modelos de aprendizado de máquina para prever a demanda futura e ajustar a capacidade com base nessas previsões. Ele tenta antecipar picos e quedas de demanda para otimizar a escalabilidade antes que a demanda real ocorra.
>
>
>
> As opções **Spot** e **On-Demand** não são tipos de Auto Scaling, mas sim tipos de instâncias EC2. As instâncias Spot são baseadas em lances e podem ser interrompidas com pouco aviso, enquanto as instâncias On-Demand são pagas por hora ou por segundo e não têm compromissos de longo prazo.

59. Which statement regarding Amazon EC2 instances is true?

* [x] An AMI is a template used for launching new instances with identical configurations.
* [ ] A new EC2 instance, created from an AMI, must be of the exact same instance type as the instance that the AMI was created from.
* [ ] The size of an EC2 instance cannot be increased after it is created
* [ ] An Auto Scaling group is automatically created when an AMI is built.

> **Uma AMI é um template usado para iniciar novas instâncias com configurações idênticas.**
>
> * **Verdadeiro.** Uma Amazon Machine Image (AMI) é um template que contém a configuração do sistema operacional, aplicativos e configurações necessárias para iniciar novas instâncias EC2 com a mesma configuração.
>
>
>
> **Uma nova instância EC2, criada a partir de uma AMI, deve ser do mesmo tipo de instância exato que a instância da qual a AMI foi criada.**
>
> * **Falso.** Quando você cria uma instância a partir de uma AMI, você pode escolher qualquer tipo de instância disponível. Não é necessário que a nova instância seja do mesmo tipo que a instância original.
>
>
>
> **O tamanho de uma instância EC2 não pode ser aumentado após ser criada.**
>
> * **Falso.** Você pode alterar o tipo de instância (tamanho) de uma instância EC2 existente, desde que pare a instância antes de alterar o tipo e a instância esteja em um estado que permita o redimensionamento.
>
>
>
> **Um grupo de Auto Scaling é criado automaticamente quando uma AMI é construída.**
>
> * **Falso.** A criação de um grupo de Auto Scaling é uma ação separada e não ocorre automaticamente quando uma AMI é criada. Você precisa criar e configurar um grupo de Auto Scaling separadamente, se necessário.

60. &#x20;By default, a user-created Amazon Machine Image (AMI) is available in all AWS Regions.

* [ ] True
* [x] False

> Por padrão, uma Amazon Machine Image (AMI) criada pelo usuário está disponível apenas na região onde foi criada. Se você deseja tornar a AMI disponível em outras regiões, você precisa copiar a AMI para essas regiões específicas. Isso pode ser feito manualmente através do Console de Gerenciamento da AWS, da AWS CLI ou usando a AWS SDK.
>
> A disponibilidade de uma AMI em todas as regiões não é automática e requer uma ação explícita para copiar a imagem para outras regiões.

61. Which metrics can be tracked in a scaling policy? (Select THREE)

* [x] Average CPU utilization
* [x] Average network in
* [x] Average network out
* [ ] Maximum memory usage

> Em uma política de escalonamento no Amazon EC2 Auto Scaling, você pode acompanhar várias métricas para determinar quando escalar para cima ou para baixo. As métricas que podem ser rastreadas em uma política de escalonamento incluem:
>
> 1. **Average CPU utilization**: Utilização média da CPU é uma métrica comum usada para decidir quando adicionar ou remover instâncias. Se a utilização da CPU média ultrapassar um limite definido, o Auto Scaling pode adicionar mais instâncias.
> 2. **Average network in**: A média de dados recebidos pela instância pode ser usada para escalar com base no tráfego de entrada. Se a média de dados recebidos exceder um limite, pode ser um sinal de que mais capacidade é necessária.
> 3. **Average network out**: A média de dados enviados pela instância pode ser monitorada para determinar a necessidade de escalabilidade com base no tráfego de saída. Se a média de dados enviados for alta, o Auto Scaling pode adicionar mais instâncias para lidar com a carga.
>
>
>
> A **Maximum memory usage** (uso máximo de memória) não é uma métrica disponível diretamente para políticas de escalonamento no Auto Scaling do EC2, pois o Amazon EC2 Auto Scaling não fornece métricas de uso de memória nativamente. Para monitorar o uso de memória, você precisaria usar uma solução personalizada, como a coleta de métricas de memória com o CloudWatch Agent e a configuração de alarmes com base nessas métricas.

62. Which statement regarding auto scaling and load balancing is true?

* [ ] An Auto Scaling group can use only are Availability Zone at a time
* [ ] Auto Scaling groups must be used independently of load balancer.
* [x] A load balancer will route traffic to all targets, no matter which Availability Zone the targets are in
* [ ] Load balancers must use the same security group as the instances behind it.

> **Um Auto Scaling group pode usar várias Zonas de Disponibilidade ao mesmo tempo** para melhorar a disponibilidade e a resiliência. A escolha de uma única Zona de Disponibilidade não é uma limitação para o Auto Scaling group.
>
> **Auto Scaling groups não precisam ser usados independentemente de um balanceador de carga.** Normalmente, um balanceador de carga é usado em conjunto com um Auto Scaling group para distribuir o tráfego de entrada entre as instâncias em execução e garantir alta disponibilidade.
>
> **Os balanceadores de carga não precisam usar o mesmo grupo de segurança que as instâncias que estão por trás deles.** No entanto, é importante que as regras de segurança estejam configuradas corretamente para permitir que o tráfego passe entre o balanceador de carga e as instâncias.

63. &#x20;A user causes a Auto Scaling group to drop below the defined minimum by manually terminating an instance. What is the outcome?

* [ ] Nothing.
* [ ] The entire Auto Scaling group is shut down
* [ ] A new minimum number is set.
* [x] A new instance is launched to meet the minimum requirement.

> Quando um usuário termina manualmente uma instância em um Auto Scaling group e isso faz com que o número de instâncias caia abaixo do número mínimo definido, o Auto Scaling group detecta que a quantidade de instâncias está abaixo do mínimo e automaticamente lança uma nova instância para atender ao limite mínimo configurado. O Auto Scaling está projetado para garantir que o número de instâncias esteja sempre dentro dos limites configurados (mínimo e máximo).

64. &#x20;When a load balancer detects an unhealthy target, it stops routing traffic to that target even when the target becomes healthy again.

* [ ] True
* [x] False

> Quando um balanceador de carga detecta um alvo (target) como não saudável, ele para de direcionar o tráfego para esse alvo. No entanto, se o alvo se tornar saudável novamente, o balanceador de carga começará a rotear tráfego para ele novamente, conforme a configuração de verificação de integridade (health checks). O balanceador de carga monitora continuamente o estado dos alvos e recomeça a distribuição de tráfego para alvos que recuperaram a saúde.

65. What do Application Load Balancers use to verify that traffic should be sent to a target?

* [ ] Security group
* [x] Health check
* [ ] Scaling policy
* [ ] Subnet

> Os Application Load Balancers (ALBs) usam verificações de integridade (health checks) para determinar se o tráfego deve ser direcionado para um alvo específico. As verificações de integridade são realizadas periodicamente para garantir que os alvos estejam funcionando corretamente e possam lidar com o tráfego. Se um alvo não passar nas verificações de integridade, o balanceador de carga para de enviar tráfego para ele até que ele se recupere e passe novamente nas verificações.

66. &#x20;Which targets for an Application Load Balancer are valid? (Select THREE)

* [x] Instance
* [x] Lambda function
* [ ] Database
* [x] IP address

> **Instance**: Você pode registrar instâncias EC2 como alvos para um ALB.
>
> **Lambda function**: O ALB pode invocar funções Lambda diretamente como alvos, permitindo que você utilize funções Lambda para processar solicitações.
>
> **IP address**: O ALB pode direcionar o tráfego para endereços IP específicos, o que é útil para direcionar o tráfego para recursos fora da AWS ou para instâncias em uma VPC privada.
>
>
>
> **Database** não é um alvo válido para um ALB. O ALB é projetado para distribuir tráfego para aplicações e serviços, mas não para bancos de dados diretamente.

67. Which statements about the root user in an AWS account are true? (Select THREE)

* [x] The root user should not be used for everyday tasks.
* [x] The root user should be used to create an IAM admin account
* [ ] The root user has no permissions by default
* [x] The root user has all permissions by default.

> **O usuário root não deve ser usado para tarefas diárias.**: Por motivos de segurança, é recomendável que o usuário root seja usado apenas para tarefas administrativas essenciais e não para atividades do dia a dia. Para operações diárias, você deve criar e usar contas IAM com permissões específicas e mínimas necessárias.
>
> **O usuário root deve ser usado para criar uma conta IAM admin.**: Para configurar a conta inicial de administração e definir permissões detalhadas, o usuário root deve ser usado. Após isso, você pode criar usuários IAM com permissões administrativas que podem ser usadas para gerenciar a conta AWS.
>
> **O usuário root tem todas as permissões por padrão.**: O usuário root é o único usuário com acesso total a todos os recursos e operações na conta AWS. Ele não está limitado por permissões específicas como os usuários IAM.
>
>
>
> **O usuário root não tem permissões por padrão** é incorreta porque o usuário root tem todas as permissões por padrão e não precisa de permissões adicionais para acessar qualquer recurso na conta AWS.

68. The Principal element is used in a resource-bases JSON policy to specify the principal that is allowed or denied access to a resource. What is an example of a principal that can be specifed? (Select THREE)

* [x] IAM user
* [x] IAM role
* [ ] S3 Bucket
* [x] AWS Services

> **IAM user**: Um usuário IAM pode ser especificado como um principal em uma política baseada em recursos. Isso permite que você defina permissões específicas para um usuário em relação a um recurso.
>
> **IAM role**: Um papel IAM também pode ser especificado como um principal. Isso é útil quando você deseja permitir que um papel assuma um recurso específico ou tenha acesso a um recurso.
>
> **AWS Services**: Serviços da AWS podem ser especificados como principais em políticas baseadas em recursos. Por exemplo, você pode permitir que um serviço como o Amazon EC2 acesse um recurso do Amazon S3.
>
>
>
> **S3 Bucket** não é um exemplo de principal, pois um bucket S3 é um recurso, não um principal que pode ser especificado em uma política. Em uma política baseada em recursos, você define quais principais têm acesso a um recurso específico, mas o bucket em si não é considerado um principal.

69. Which statements best describe the shared responsibility model for AWS security? (Select TWO)

* [x] AWS is responsible for the security of the underlying cloud infrastructure
* [ ] AWS is responsible for securing workloads that customers deploy on AWS
* [ ] Customers are responsible for the security of the underlying cloud infrastructure.
* [x] Customers are responsible for securing workloads that they deploy on AWS

> **AWS é responsável pela segurança da infraestrutura subjacente da nuvem**: A AWS gerencia a segurança da infraestrutura que suporta seus serviços de nuvem, incluindo hardware, software, redes e instalações físicas.
>
> **Os clientes são responsáveis por garantir a segurança das cargas de trabalho que eles implantam na AWS**: Os clientes devem gerenciar e proteger suas próprias aplicações, dados e configurações nos serviços da AWS. Isso inclui a configuração de segurança, o gerenciamento de identidades e permissões, e a proteção de dados.
>
>
>
> **AWS é responsável por garantir a segurança das cargas de trabalho que os clientes implantam na AWS** não está correta porque a segurança das cargas de trabalho é uma responsabilidade do cliente.
>
> **Os clientes são responsáveis pela segurança da infraestrutura subjacente da nuvem** também está incorreto porque a responsabilidade pela segurança da infraestrutura subjacente é da AWS, não dos clientes.

70. AWS identity and Access Management (IAM) users can belong to multiple groups, but IAM user groups cannot be nested.

* [x] True
* [ ] False

> Os usuários do AWS Identity and Access Management (IAM) podem pertencer a vários grupos, mas os grupos IAM não podem ser aninhados. Isso significa que você não pode criar um grupo de IAM e adicionar outro grupo como membro desse grupo. Cada grupo é independente e pode conter apenas usuários do IAM, sem suporte para hierarquia ou aninhamento de grupos.

71. Which option designates the API calls to allow or deny in an IAM policy?

* [ ] Principal
* [ ] Effect
* [ ] Resource
* [x] Action

> **Action**: Este elemento em uma política IAM especifica quais ações são permitidas ou negadas. As ações podem ser operações específicas em um serviço AWS, como `s3:GetObject` para permitir que um usuário leia objetos de um bucket S3 ou `ec2:StartInstances` para permitir que um usuário inicie instâncias EC2.
>
>
>
> **Principal**: Define quem está autorizado ou negado, como um usuário, grupo, papel ou serviço.
>
> **Effect**: Especifica se a política permite (`Allow`) ou nega (`Deny`) o acesso às ações definidas.
>
> **Resource**: Define quais recursos a política se aplica, como buckets S3, instâncias EC2 ou tabelas DynamoDB.

72. Which Amazon EC2 pricing model adjusts based on supply and demand of EC2 instances?

* [ ] On-Demand instances
* [ ] Reserved Instances
* [x] Spot Instances
* [ ] Convertible Reserved Instances

> O modelo de preços **Spot Instances** do Amazon EC2 ajusta o custo com base na oferta e na demanda de instâncias EC2. Com as Spot Instances, você pode aproveitar a capacidade não utilizada da AWS a preços reduzidos, que são definidos por um leilão em tempo real. O preço das Spot Instances varia conforme a demanda e a oferta de capacidade em uma região específica. Você pode definir um preço máximo que está disposto a pagar, e se o preço Spot atual estiver abaixo desse valor e a capacidade estiver disponível, sua instância será executada.
>
>
>
> As outras opções têm os seguintes modelos de preços:
>
> **On-Demand instances**: Você paga por hora ou por segundo de uso, sem compromisso de longo prazo, e o custo não varia com base na oferta e demanda.
>
> **Reserved Instances**: Você paga uma taxa fixa para uma instância por um período de um ou três anos, com a opção de um pagamento único ou em parcelas. O custo é previsível e não depende de oferta e demanda.
>
> **Convertible Reserved Instances**: Semelhante às Reserved Instances, mas com a flexibilidade de trocar o tipo de instância, a família e a região. O custo é fixo, baseado em um compromisso de longo prazo.

73. What is true about Amazon S3 pricing? (Select TWO)

* [ ] Charges occur per bucket.
* [ ] Charges occur per object
* [x] Charges occur per gibibyte (GiB)
* [x] Charges occur per GET, PUT, COPY, POST, and LIST request
* [ ] Charges occur per connection

> **Charges occur per gibibyte (GiB)**: A cobrança do Amazon S3 é baseada na quantidade de dados armazenados em gigabytes (GiB). O custo é calculado com base no volume total de dados armazenados.
>
> **Charges occur per GET, PUT, COPY, POST, and LIST request**: Além do armazenamento, o Amazon S3 cobra pelas operações realizadas, como GET, PUT, COPY, POST e LIST. Cada tipo de solicitação tem um custo associado.
>
>
>
> As outras opções estão incorretas por estas razões:
>
> **Charges occur per bucket**: O Amazon S3 não cobra especificamente por bucket, mas sim pelo armazenamento e pelas solicitações realizadas.
>
> **Charges occur per object**: Embora o armazenamento e as operações possam ser calculados com base no número de objetos, a cobrança principal é baseada no volume total de armazenamento e nas solicitações feitas, não por objeto individualmente.
>
> **Charges occur per connection**: O Amazon S3 não cobra por conex

74. Which AWS pricing model offers lower prices on compute and machine learning across any AWS Region?

* [ ] Pay-as-you-go
* [ ] On-demand
* [ ] Dedicated hosts
* [ ] Saving Plans

> **Savings Plans** é o modelo de preços da AWS que oferece preços reduzidos para computação e aprendizado de máquina em qualquer região da AWS. Os Savings Plans permitem que você se comprometa com uma certa quantidade de uso de computação ou recursos de aprendizado de máquina por um período de um ou três anos em troca de um desconto significativo em relação às tarifas padrão.
>
>
>
> Aqui estão os detalhes dos outros modelos de preços mencionados:
>
> **Pay-as-you-go**: Este modelo oferece preços padrão e flexíveis baseados no uso real dos recursos, sem compromisso de longo prazo. É o modelo mais básico e não oferece descontos adicionais.
>
> **On-demand**: Esse modelo permite pagar pelo uso dos recursos sem compromisso de longo prazo. Os preços são baseados na utilização real e não oferecem descontos em comparação com os preços padrão.
>
> **Dedicated hosts**: Este modelo permite que você use servidores dedicados para instâncias EC2, o que pode ser útil para atender a requisitos de conformidade e licenciamento. No entanto, não oferece necessariamente preços reduzidos em comparação com os modelos de preço padrão.
>
>
>
> Os **Savings Plans** são a melhor opção para obter preços mais baixos em uma ampla gama de serviços e regiões, oferecendo flexibilidade em comparação com o modelo de instância reservada.

75. Windows and Linux Amazon EC2 instances have Free Tier eligible instance types.

* [x] True
* [ ] False

76. Which AWS Pricing Calculator path can be used to generate an estimate for the Amazon EC2 instances with an hourly snapshot requirement?

* [ ] Quick
* [ ] Express
* [ ] Detailed
* [ ] Advanced

>

77. Which resource automates the creation, retention, and deletion of Amazon Elastic Block Store (Amazon EBS) snapshots and AMIs backed by Amazon EBS?

* [x] Amazon Data Lifecycle Manager
* [ ] Amazon S3 Intelligent Tiering
* [ ] AWS Config
* [ ] AWS Systems Manager

> **Amazon Data Lifecycle Manager** é o recurso da AWS que automatiza a criação, retenção e exclusão de snapshots do Amazon Elastic Block Store (Amazon EBS) e de AMIs (Amazon Machine Images) que são baseadas em volumes do EBS. Ele permite que você defina políticas para gerenciar esses recursos, garantindo que os snapshots e AMIs sejam criados e excluídos de acordo com suas necessidades de backup e retenção.
>
>
>
> Os outros recursos mencionados têm os seguintes papéis:
>
> **Amazon S3 Intelligent Tiering**: Otimiza o custo de armazenamento de dados no Amazon S3 ao mover automaticamente os dados entre diferentes classes de armazenamento com base no padrão de acesso.
>
> **AWS Config**: Monitora e registra as configurações dos recursos da AWS, e avalia as configurações para conformidade com as políticas definidas, mas não gerencia diretamente a criação e retenção de snapshots ou AMIs.
>
> **AWS Systems Manager**: Fornece ferramentas para gerenciar e automatizar a administração de instâncias e recursos, como automação de tarefas, mas não é específico para a criação e gerenciamento de snapshots e AMIs.

78. A customer has two m5.xlarge Amazon EC2 instances, each with 40 GB of storage attached. One instance is running while the other is stopped. Which statement is true?

* [ ] The customer will be charged for the one running instance and for 40 GB of storage.
* [ ] The customer will be charged for the one running instance and for 80 GB of storage.
* [ ] The customer will be charged for the two instances and for 80 GB of storage

>

79. &#x20;Which source does AWS Pricing Calculator use to create estimates?

* [x] AWS Price List API
* [ ] Public Amazon S3 bucket
* [ ] AWS Cost Explorer console
* [ ] Customer pricing contract

> O **AWS Price List API** é a fonte que o AWS Pricing Calculator utiliza para criar estimativas. Este API fornece informações detalhadas sobre os preços dos serviços da AWS, permitindo que o AWS Pricing Calculator acesse dados atualizados sobre os custos dos serviços para criar estimativas precisas para os clientes.
>
>
>
> Aqui está o papel das outras opções:
>
> **Public Amazon S3 bucket**: Não é utilizado diretamente para gerar estimativas no AWS Pricing Calculator. O S3 bucket público pode conter documentos e informações sobre preços, mas não é a fonte principal de dados para o cálculo de estimativas.
>
> **AWS Cost Explorer console**: Ferramenta que permite visualizar e analisar os custos e uso dos serviços AWS. Não é utilizado para gerar estimativas, mas para analisar os custos atuais e históricos.
>
> **Customer pricing contract**: Refere-se a contratos personalizados e descontos acordados entre a AWS e um cliente específico. O AWS Pricing Calculator utiliza a lista de preços padrão da AWS e não se baseia em contratos individuais para estimativas padrão.

80. What is true about Amazon EC2 pricing?

* [ ] All storage attached to an instance is included in the hourly instance price
* [x] When an instance is stopped, charges for the instance stop but any attached Amazon EBS storage continues to be billed
* [ ] All instances are charged their hourly rate whether they are running or stopped
* [ ] A stopped instance is still charged, but at a lower rate.

> **Quando uma instância está parada, as cobranças pela instância param, mas qualquer armazenamento Amazon EBS anexado continua a ser cobrado**: As cobranças pela instância EC2 cessam quando a instância está parada, mas o armazenamento associado (volumes EBS) continua a ser cobrado. O armazenamento EBS é cobrado separadamente e continua a gerar custos enquanto o volume estiver provisionado, independentemente do estado da instância EC2.
>
>
>
> As outras opções são incorretas por estas razões:
>
> **All storage attached to an instance is included in the hourly instance price**: O armazenamento EBS não está incluído no preço da instância EC2. O armazenamento EBS é cobrado separadamente com base no volume e na quantidade de dados armazenados.
>
> **All instances are charged their hourly rate whether they are running or stopped**: As instâncias EC2 são cobradas por hora apenas quando estão em execução. Quando estão paradas, não há cobrança pelo tempo de execução da instância, mas o armazenamento EBS continua a gerar custos.
>
> **A stopped instance is still charged, but at a lower rate**: Isso não é correto. Instâncias EC2 paradas não são cobradas pelo tempo de execução, mas o armazenamento EBS continua a ser cobrado. Não há um "preço reduzido" para instâncias paradas; a cobrança ocorre apenas pelo armazenamento EBS e outras características que continuam a ser provisionadas.

81. There is no charge for inbound data from the internet into AWS.

* [x] True
* [ ] False

> Não há cobrança para dados que entram na AWS a partir da Internet. O tráfego de entrada para a AWS, também conhecido como inbound data, é gratuito. No entanto, a AWS cobra pelo tráfego de saída, que é o dado que sai da AWS para a Internet ou para outras regiões da AWS. Portanto, enquanto você não paga por dados que entram na AWS, você é cobrado pelos dados que saem.

82.
