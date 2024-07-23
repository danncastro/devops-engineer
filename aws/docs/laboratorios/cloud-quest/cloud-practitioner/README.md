---
description: >-
  Os praticantes de nuvem criarão soluções básicas de nuvem usando serviços da
  AWS.
---

# Cloud Practitioner

Você aprenderá sobre conceitos da AWS Cloud, conceitos de segurança, casos de uso comuns, modelos de cobrança e precificação e impactos comerciais.

Você pode ganhar um distintivo digital por concluir todas as tarefas do Cloud Practitioner. Os distintivos digitais do AWS Cloud Quest permitem que você demonstre seu conhecimento em criação de soluções.

{% embed url="https://www.aboutamazon.com.br/noticias/aws/aws-oferece-5-treinamentos-baseados-em-jogos-para-aprimorar-suas-habilidades-em-nuvem" %}

***

## <mark style="color:red;">**Objetivos de aprendizagem**</mark>

Para cada tarefa, você receberá uma conta automatizada para criar uma nova solução no console da AWS.

***

### <mark style="color:red;">Databases in Practice</mark>

| Título da tarefa          | Solicitação de negócios                                                                            |
| ------------------------- | -------------------------------------------------------------------------------------------------- |
| Bases de dados na prática | Melhore as operações, o desempenho e a disponibilidade do banco de dados relacional da seguradora. |

<figure><img src="../../../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>

<details>

<summary><mark style="color:purple;">Gerenciamento de banco de dados com Amazon RDS</mark></summary>

Revise os recursos, benefícios e tipos de banco de dados disponíveis com o Amazon RDS. Descreva o dimensionamento vertical e horizontal no Amazon RDS. Use réplicas de leitura do Amazon RDS para aumentar o desempenho do banco de dados.&#x20;

1. Implemente implantações multi-AZ do Amazon RDS para aumentar a disponibilidade.

* [x] Launch an Amazon RDS instance.
* [x] Configure a Multi-AZ deploymnet
* [x] Configure Amazon RDS backups.

***

<mark style="color:purple;">**Step 1**</mark>

1. In the top navigation bar search box, type: RDS
2. In the search results, under Services, click RDS.
3. Go to the next step

![](<../../../.gitbook/assets/image (1).png>)

<mark style="color:purple;">**Step 2**</mark>

1. In the left navigation pane, click Databases.
2. In the Databases section, click Create database.
3. Go to the next step

<mark style="color:red;">**Concept:**</mark> Amazon Relational Database Service (Amazon RDS) is a managed service. This  means that your database administrator can focus on innovating instead of patching and updating their database and infrastructure.

Amazon RDS is optmized for memory, performance, and input/output. With Amazon RDS, you only pay for the resources that you actually consume.

![](<../../../.gitbook/assets/image (2).png>)

<mark style="color:purple;">**Step 3**</mark>

1. To fine-tune your configuration, for Choose a database creation method, choose Standard create.
2. For Engine type, choose MariaDB.
3. Go to the next step.

<mark style="color:red;">**Concept:**</mark> AWS offers several familiar database (DB) engines. Amazon Aurora, a lightning fast database solution at AWS, is up to five times faster than MySQL and three times faster than PostgreSQL. Aurora databases are highly secure, available, and durable.

&#x20;![](<../../../.gitbook/assets/image (3).png>)

<mark style="color:purple;">**Step 4**</mark>

1. For Engine Version, keep the default MariaDB version provided.

* The default version might be different from what is displayed in the screenshot example.

2. For Templates, choose Dev/Test.
3. Go to the next step

<mark style="color:red;">**Concept:**</mark> Amazon RDS provides three templates for you deployment: Production, Dev/Test, and Free Tier. Use Free Tier if you wish to learn or deploy a quick proof of concept. Use Production only when deploying a production-level system

![](<../../../.gitbook/assets/image (4).png>)

<mark style="color:purple;">**Step 5**</mark>

1. For DB instance identifier, type: my-database

* This is the name of your DB instance.

2. For Master username, keep the default username of admin.
3. For Credentials management, choose Self managed
4. For Master password, type: ILoveLearning!123
5. For Confirm password, type the password again.
6. Go to the next step

<mark style="color:red;">**Concept:**</mark> You DB instance identifier is the name that you see when you search for your instance in the console. You can connect this database with the credentials that you provide here.

![](<../../../.gitbook/assets/image (5).png>)

<mark style="color:purple;">**Step 6**</mark>

1. Scroll down to instance configuration
2. For DB Instance class, choose Burstable classes.
3. On the dropdown menu below that, choose db.t3.xlarge

* Only t3 db classes are supoported in this lab.

4. For Storage type, on the dropdown menu, choose General Purpose SSD (gp2).
5. For Allocated storage, type: 20
6. Go to the next step

<mark style="color:red;">**Concept:**</mark> Amazaon RDS supports the most demanding database applications. You can choose between two SSD-backed storage options. One is optimized for high performance OLTP applications, and the other is optimize for cost-effective, general-purpose use.

![](<../../../.gitbook/assets/image (6).png>)

<mark style="color:purple;">**Step 7**</mark>

1. For Storage autoscaling, chick the expand arrow.
2. Review the default option of Enable storage autoscaling.
3. For Maximum storage threshold, review the default threshold of 1000GB.
4. Under Availability & durability, for multi-AZ deployment, choose Create a standby instance.
5. Go to the next step

<mark style="color:red;">**Concept:**</mark> Using the MySQL, MariaDB, Oracle, and PostgreSQL engines, you can scale up to 64 TB of storage. SQL Server supports up too 16 TB. Storage scaling is on the fly, with zero downtime.

![](<../../../.gitbook/assets/image (7).png>)

<mark style="color:purple;">**Step 8**</mark>

1. In the Connectivity section, for Virtual private cloud (VPC), keep the default value of Default VPC.
2. For DB subnet group, keep the default setting.
3. For Public access, keep the default setting.
4. For VPC security group (firewall), keep the default setting.
5. Go to the next step

<mark style="color:red;">**Concept:**</mark> Amazon RDS helps you control network access to you database. You can also run your RDS DB instances in a virtual private cloud (VPC). This way, you can isolate your DB instances and connect to you existing IT infraestructure through an industry standard encrypted IPsec VPN.

![](<../../../.gitbook/assets/image (8).png>)

<mark style="color:purple;">**Step 9**</mark>

1. In the Monitoring section, for Performance insights, clear the check box to deselect Turn on Performance Insights.
2. For Additional configuration, click the expand arrow.
3. For Enhanced Monitoring, clear the check box to deselect Enable Enhanced monitoring.

* If either Performance Insights or Enhanced monitoring are enabled, you'll get a permissions error when trying to create the database.

4. Scroll down to the Additional configuration section.
5. Go to the next step.

![](<../../../.gitbook/assets/image (9).png>)

<mark style="color:purple;">**Step 10**</mark>

1. In the Additional configuration section, for Additional configuration, click de expand arrow.
2. For Initial database name, type: my\_database
3. For DB parameter group and Option group, review the default options.
4. Under Backup, review the default options.
5. Go to the next step

<mark style="color:red;">**Concept:**</mark> In order for AWS to sucessfully provision an RDS DB instance for you, you must first specify an initial database name. if you failt to spacify an initial database, your instance can still be provisioned, but it might not work properly.

![](<../../../.gitbook/assets/image (10).png>)

<mark style="color:purple;">**Step 11**</mark>

1. In the Additional configuration section, for Encryption, review the default option of Enable encryption.
2. Go to the next step

![](<../../../.gitbook/assets/image (12).png>)

<mark style="color:purple;">**Step 12**</mark>

1. For Maintenance, clear the check box to deselect Enable auto minor version upgrade.
2. For Maintenance window, review the default selection of No preference
3. Scroll down and click Create database (not shown).
4. Go to the next step.

![](<../../../.gitbook/assets/image (13).png>)

<mark style="color:purple;">**Step 13**</mark>

* Expect about 15-20 minutes to create your RDS instance. It's a great time to get a cup of coffe or a snack!
* You may see a pop-up window. Please close it.

1. When you return, in the Databases section, click the refresh icon.
2. Under Status, review to ensure that the DB status is Available.
3. Click my-database.
4. Go to the next step

![](<../../../.gitbook/assets/image (14).png>)

<mark style="color:purple;">**Step 14**</mark>

1. Click Actions to expand the dropdown menu.
2. Review the different options.

* The options, such as Create read replica, can be used to manage your existing DB instance.

3. Go to the next step.

![](<../../../.gitbook/assets/image (15).png>)

***

DIY Activities

* [x] Create a read replica of your primary database using a db.t3.xlarge instance

![](<../../../.gitbook/assets/image (16).png>)

***

</details>

***

### <mark style="color:red;">Connecting VPCs</mark>

| Título da tarefa | Solicitação de negócios                                                                                                        |
| ---------------- | ------------------------------------------------------------------------------------------------------------------------------ |
| Conectando VPCs  | A equipe de marketing da cidade quer Amazon VPCs separadas para cada departamento que permita a comunicação entre Amazon VPCs. |

<figure><img src="../../../.gitbook/assets/image (120).png" alt=""><figcaption></figcaption></figure>

<details>

<summary><mark style="color:purple;">Estabelecendo conexão de peering de VPC</mark></summary>

Resuma como o peering de VPC funciona com o Amazon VPC. Explique as etapas para estabelecer uma conexão de peering de VPC. Crie uma conexão de peering entre dois Amazon VPCs.&#x20;

1. Estabeleça uma conexão de peering entre Amazon VPCs usando uma sub-rede específica.

* [ ] Set up a VPC peering connection
* [ ] Ensure that traffic is internally routed within this connection.

***

<mark style="color:purple;">**Step 1**</mark>

1. In the navigation bar search box, type: VPC
2. In the search results, under Services, click VPC.
3. Go to the next step.

<mark style="color:red;">**Concept**</mark>: Amazon Virtual Private Cloud (Amazon VPC) is a service that helps you launch AWS resources in a logically isolated virtual network that you define. You have complete control over you virtual networking environment.

![](<../../../.gitbook/assets/image (121).png>)

<mark style="color:purple;">**Step 2**</mark>

1. In the left navigation pane, click Your VPCs.
2. In the your VPCs section, review the Marketing, Finance, and Developer VPCs.
3. Go to the next step

<mark style="color:red;">**Concept**</mark>: By default, VPCs are isolated from each other. A VPC peering connection is a networking connection between two VPCs that you can use to route traffic between them by using private IP address.

![](<../../../.gitbook/assets/image (122).png>)

<mark style="color:purple;">**Step 3**</mark>

1. In the top navigation bar search box, type: EC2
2. In the search results, under Services, click EC2
3. Go to the next step.

![](<../../../.gitbook/assets/image (123).png>)

<mark style="color:purple;">**Step 4**</mark>

1. In the Resources section, click Instances (running).
2. Go to the next step.

![](<../../../.gitbook/assets/image (124).png>)

<mark style="color:purple;">**Step 5**</mark>

1. In the Instances section, choose the check box to select the FinanceServer instance.
2. On the Details lab, review to see that no Public IPv4 address or DNS is populated for FinanceServer.

* This is because the server was created in a private subnet.

3. Under Private IPv4 addresses, click the copy icon to copy the provided IP address for FinanceServer, and then paste it in the text editor of your choice on your local device.

* You will use this value in later steps.

4. Scroll down to Subnet ID
5. Go to the next step

![](<../../../.gitbook/assets/image (125).png>)

<mark style="color:purple;">**Step 6**</mark>

1. Under Subnet ID, review the provided ID.

* Note that the subnet is private (FinancePrivateSubnet)

2. Go to the next step.

![](<../../../.gitbook/assets/image (126).png>)

<mark style="color:purple;">**Step 7**</mark>

1. To view the details of the MarketingServer instance, clear the check box to deselect the FinanceServer instance, and then choose the check boc to select the MarketingServer instance.
2. On the Details tab, under VPC ID, review the VPC that the MarketingServer instance belongs to
3. In the Instance section, click Connect.
4. Go to the next step

<mark style="color:red;">**Concept**</mark>: You can connect to an Amazon Elastic Compute Cloud (Amazon EC2) instance in four ways:&#x20;

* EC2 Insntace Connect
* Session Manager
* SSH client
* EC2 Serial Console

![](<../../../.gitbook/assets/image (127).png>)

<mark style="color:purple;">**Step 8**</mark>

1. Click the Session Manager tab.
2. Click Connect.

* The Session Manager terminal for the MarketingServer instance opens in a new browser tab (or window).

3. Go to the next step.

<mark style="color:red;">**Concept**</mark>: Session Manager is a fully managed AWS System Manager capability. With Session Manager, you can manage your Amazon EC2 instances, edge devices, and on-premises servers and virtual machines (VMs). You can use either an interactive one-click browser-based shell or the AWS Command Line Interface (AWS CLI).

![](<../../../.gitbook/assets/image (128).png>)

<mark style="color:purple;">**Step 9**</mark>

1. In the terminal window, replacing the current IP address with the IP address that you copied in an earlier step, run (type the command and press Enter) ping 172.31.x.xx

* This private IPv4 address is for the FinanceServer instance. This command checks the connection to the FinanceServer instance

2. Review to see that your command hangs, and there is no connection.
3. To exit the running process, on your keyboard, press CTRL + C
4. Go to the next step.

<mark style="color:red;">**Concept**</mark>: By default, VPCs cannot communicate with resources in other VPCs using private IPv4 addresses or IPv6 addresses. In our example, the FinanceServer instance doesn't have a public IP, so your VPCs don't know how to route data to private IP destinations outside of thir own private range.

![](<../../../.gitbook/assets/image (129).png>)

<mark style="color:purple;">**Step 10**</mark>

1. In the previous browser, in the Amazon EC2 Instances section, under Instance ID, click the MarketingServer instance ID.
2. Go to the nest step

![](<../../../.gitbook/assets/image (130).png>)

<mark style="color:purple;">**Step 11**</mark>

1. Under Subnet ID, click the provided ID.
2. Go to the next step

<mark style="color:red;">**Concept**</mark>: EC2 instances reside within a subnet. A subnet is a range of IP Addresses in your VPC.

![](<../../../.gitbook/assets/image (131).png>)

<mark style="color:purple;">**Step 12**</mark>

1. In the Subnets section, choose the check box to select the subnet name.
2. On the Details tab, under Route table, click the provided route ID.
3. Go to the next step

<mark style="color:red;">**Concept**</mark>: An important property of a subnet is its route table. A route table contains a set of rules, called routes. Routes are used to determine where network traffic, from your subnet or gateway, is directed.

![](<../../../.gitbook/assets/image (132).png>)

<mark style="color:purple;">**Step 13**</mark>

1. Under Route tables, choose the Marketing route table.
2. Click the Routes tab.
3. In the Routes section, review the routing rules.

* You should see two routes: one route for the local traffic and one route for the internet traffic through the internet gateway.

4. Go to the next step.

<mark style="color:red;">**Concept**</mark>: Routes tables will have rules for local traffic and public IP ranges if a gateway is attached. We recommend that you specify a CIDR block from the private IPv4 address ranges, as specifed in RFC 1918.

![](<../../../.gitbook/assets/image (133).png>)

<mark style="color:purple;">**Step 14**</mark>

1. In the left navigation pane, click Peering connections.
2. In the Peering connections section, click Create peering connection.
3. Go to the next step

<mark style="color:red;">**Concept**</mark>:  Instances in either VPC can communicate with each other as if they are in the same network.

![](<../../../.gitbook/assets/image (134).png>)

<mark style="color:purple;">**Step 15**</mark>

1. In the Peering connection settings section, for Name, type: Marketing <> Finance
2. For VPC ID (Requester), on the dropdown menu, choose the Marketing VPC.
3. For VPC CIDRs, review to ensure that the Marketing VPC has 10.10.0.0/16 as its CIDR range.
4. Scrool down to the bottom of the page.
5. Go to the next step

<mark style="color:red;">**Concept**</mark>: Your VPC will request that another VPC allow access to its resources. the VPC that makes the request is called the Requester. You can request access to VPCs from other AWS accounts.

![](<../../../.gitbook/assets/image (135).png>)

<mark style="color:purple;">**Step 16**</mark>

1. For VPC ID (Accepter), choose the Finance VPC.
2. For VPC CIDRs, review to ensure that the Finance VPC has 172.31.0.0/16 as it CIDR range.
3. Click Create peering connection.
4. Go to the next step.

![](<../../../.gitbook/assets/image (136).png>)

<mark style="color:purple;">**Step 17**</mark>

1. In the success alert, review the message.
2. Under Status, review to ensure that the status is Pending Acceptance by xxxxxx.
3. Click Actions to expand the dropdown menu.
4. Choose Accept request.
5. Go to the next step

<mark style="color:red;">**Concept**</mark>: To request a VPC peering connection with a VPC in your account, ensure that you have the IDs of the VPCs with which you are creating the VPC peering connection. You must both create and accept the VPC peering connection request yourself to activate it. if the peering connection is across accounts, both accounts must accept the connection to activate it.

![](<../../../.gitbook/assets/image (137).png>)

<mark style="color:purple;">**Step 18**</mark>

1. In the pop-up box, click Accept request.
2. Go to the next step

![](<../../../.gitbook/assets/image (138).png>)

<mark style="color:purple;">**Step 19**</mark>

1. In the success alert, review the message.
2. Under Status, review to see that the status is Active.
3. Go to the next step

![](<../../../.gitbook/assets/image (139).png>)

<mark style="color:purple;">**Step 20**</mark>

1. Return to the Instances section on the Amazon EC2 console. and then choose the check box to select the MarketingServer instance.
2. On the Details tab, under Subnet ID, click the provided ID.
3. Go to the next step

<mark style="color:red;">**Concept**</mark>: After you establish a peering connection, you must modify the route table associeated with each VPC. You must add a route into each route table to allow traffic to be routed to the peered VPC.

![](<../../../.gitbook/assets/image (140).png>)

<mark style="color:purple;">**Step 21**</mark>

1. In the Subnets section, choose the check box to select the available subnet.
2. Under Route table, click the provided route ID.
3. Go to the next step

![](<../../../.gitbook/assets/image (141).png>)

<mark style="color:purple;">**Step 22**</mark>

1. In the Route tables section, choose the Marketing route table.
2. Click the Routes tab.
3. Click Edit routes.
4. Go to the next step

![](<../../../.gitbook/assets/image (143).png>)

<mark style="color:purple;">**Step 23**</mark>

1. Click Add route.
2. To configure the route, for Destination, in the new search box, type: 172.31.0.0/16
3. For Target, in the dropdown box, choose Peering Connection.
4. Choose the peering connection target that contains Marketing <> Finance.
5. Click Save changes.
6. Go to the next step

![](<../../../.gitbook/assets/image (144).png>)

<mark style="color:purple;">**Step 24**</mark>

1. In the success alert, review the message.
2. Go to the next step

![](<../../../.gitbook/assets/image (145).png>)

<mark style="color:purple;">**Step 25**</mark>

1. Return to the Instance section on the Amazon EC2 console, and then choose the check boc to select the FinanceServer instance.
2. On the Details tab, under Subnet ID, click the provided ID.
3. Go to the next step

![](<../../../.gitbook/assets/image (146).png>)

<mark style="color:purple;">**Step 26**</mark>

1. In the Subnets section, choose the check box to select the available subnet.
2. On the Details tab, under Route table, click the provided route ID.
3. Go to the next step

![](<../../../.gitbook/assets/image (147).png>)

<mark style="color:purple;">**Step 27**</mark>

1. In the Route tables section, choose the Finance route table.
2. Click the Routes tab.
3. Click Edit routes.
4. Go to the next step.

<mark style="color:red;">**Concept**</mark>: The route tables for each VPC must be modified to allow traffic across the peering connection.

![](<../../../.gitbook/assets/image (148).png>)

<mark style="color:purple;">**Step 28**</mark>

1. Click Add route.
2. To configure the route, for Destination, in the new search box, type: 10.10.0.0/16
3. For Target, in the dropbox box, choose Peering Connection.
4. Choose the peering connection taget that contains Marketing <> Finance.
5. Click Save changes.
6. Go to the next step

![](<../../../.gitbook/assets/image (149).png>)

<mark style="color:purple;">**Step 29**</mark>

1. In the success alert, review the message.
2. Go to the next step.

![](<../../../.gitbook/assets/image (150).png>)

<mark style="color:purple;">**Step 30**</mark>

1. Return to the Amazon EC2 Instances section, and then choose the check box to select the MarketingServer instance.
2. Click Connect
3. Go to the next step.

![](<../../../.gitbook/assets/image (151).png>)

<mark style="color:purple;">**Step 31**</mark>

1. Click the Session Manager tab.
2. Click Connect
3. Go to the next step

![](<../../../.gitbook/assets/image (152).png>)

<mark style="color:purple;">**Step 32**</mark>

* The Session Manager terminal for the MarketingServer instance opens in a new browser  tab (or window).

1. In the terminal, replacing the current IP address with the IP address that you copied in an earlier step, run: ping 172.31.x.xx

* This private IPv4 address is for the FinanceServer instance.

2. Review to see that the ping command is still not working.
3. To exit the running process, on your keyboard, press CTRL + C.
4. Go to the next step

<mark style="color:red;">**Concept**</mark>:  Peered VPCs do not necessarily accept all data between them. Security features, such as network access control lists and security groups, still apply. Be sure to update them accordingly.

![](<../../../.gitbook/assets/image (153).png>)

<mark style="color:purple;">**Step 33**</mark>

1. In the previous browser, in the Amazon EC2 Instances section, choose the check box to select the FinanceServer instance.
2. Click the Security tab.
3. Under Security groups, click the provided security group name that contains FinanceServerSecurityGroup.
4. Go to the next step

<mark style="color:red;">**Concept**</mark>: Security groups do not automatically accept data from peered VPCs. You must update security groups to allow a peered VPC as an incoming source.

![](<../../../.gitbook/assets/image (154).png>)

<mark style="color:purple;">**Step 34**</mark>

1. Click the Inbound rules tab.
2. Click Edit inbound rules.
3. Go to the next step

<mark style="color:red;">**Concept**</mark>: Security groups are stateful. If you send a request from your instance, the responde traffic for that request is allowed to flow in regardless of the inbound rules. This also means that responses to allowed inbound traffic are allowed to flow out, regardless of the outbound rules.

![](<../../../.gitbook/assets/image (155).png>)

<mark style="color:purple;">**Step 35**</mark>

1. Click Add rule.
2. To configure the rule, for Type, in the new search box, choose Custom ICMP - IPv4.
3. For Source, in the new search box, type and choose: 10.10.0.0/16
4. Click Save rules.
5. Return to the Amazon EC2 Instance page, and then connect to the MarketingServer instance by using Session Manager (not shown).
6. Go to the next step.

<mark style="color:red;">**Concept**</mark>: Security group rules are always permissive. You can't create rules that deny access. Using security group rules, you can filter traffic based on protocols and port numbers.

![](<../../../.gitbook/assets/image (156).png>)

<mark style="color:purple;">**Step 36**</mark>

1. In the terminal, replacing the current  IP address with the IP address that you copied in an earlier step, run: ping 172.31.x.xx

* This private IPv4 address is for the FinanceServer instance.

2. Review the data.

* The MarketingServer instance should now be able to communicate with the FinanceServer instance.

3. To exit the Running process, on your keyboard, press CTRL + C
4. Go to the next step

<mark style="color:red;">**Concept**</mark>: Your services can communicate after your VPCs are peered and the security groups allow the corrent traffic. Remember, if you need to add different traffic types, you will have to change the inbound rules of your security groups.

![](<../../../.gitbook/assets/image (157).png>)

***

DIY Activite

* [x] Configure VPC peering between Developer and Finance department VPCs.

![](<../../../.gitbook/assets/image (158).png>)

</details>





| Título da tarefa                                                     | Solicitação de negócios                                                                                                                                      |
| -------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| <ol start="8"><li>Sistemas de arquivos na nuvem</li></ol>            | Ajude a agência de modelos de animais de estimação da cidade a compartilhar dados de arquivos sem provisionar ou gerenciar armazenamento.                    |
| <ol start="9"><li>Aplicações de autocura e dimensionamento</li></ol> | Ajude o café de jogos da cidade a implementar servidores de recuperação automática, restringindo os clientes a uma capacidade de provisionamento específica. |
| <ol start="10"><li>Aplicações Web de Alta Disponibilidade</li></ol>  | Ajude a agência de viagens a criar uma arquitetura de aplicativo web de alta disponibilidade.                                                                |
| <ol start="11"><li>Conceitos Básicos de Segurança</li></ol>          | Ajude a melhorar a segurança na bolsa de valores da cidade garantindo que os engenheiros de suporte possam executar somente ações autorizadas.               |
| <ol start="12"><li>Economia da Nuvem</li></ol>                       | A loja de pranchas de surfe da cidade precisa de uma estimativa de custo de uma arquitetura com uso variável de recursos.                                    |

| Objetivos de aprendizado                                                                                                                                                                                                                                                                  |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <ol start="8"><li>Resuma as diferentes opções de armazenamento disponíveis na AWS. Resuma os principais recursos e benefícios do Amazon EFS. Identifique casos de uso comercial para o Amazon EFS. Configure endpoints do Amazon EFS para acessar o armazenamento centralizado.</li></ol> |
| <ol start="9"><li>Descreva os recursos de autocura e dimensionamento oferecidos pelos grupos de Auto Scaling. Crie um grupo de Auto Scaling com limites de recursos rígidos. Configure um grupo de Auto Scaling para responder a um evento baseado em tempo.</li></ol>                    |
| <ol start="10"><li>Descreva os princípios para arquitetar aplicativos de alta disponibilidade. Resuma os benefícios de usar um AWS Application Load Balancer (ALB). Use grupos de Auto Scaling com balanceamento de carga e monitoramento de integridade.</li></ol>                       |
| <ol start="11"><li>Descreva o processo de criação e as diferenças entre usuários, funções e grupos do AWS IAM. Revise a estrutura e os componentes das Políticas do AWS IAM. Resuma o Modelo de Responsabilidade Compartilhada da AWS e os programas de conformidade.</li></ol>           |
| <ol start="12"><li>Descreva como as estimativas de preços são obtidas. Use a Calculadora de Preços da AWS para estimar o preço de uma arquitetura da AWS.</li></ol>                                                                                                                       |

<details>

<summary><mark style="color:purple;">Challenges</mark></summary>

<img src="../../../.gitbook/assets/image (109).png" alt="" data-size="original">![](<../../../.gitbook/assets/image (117).png>)![](<../../../.gitbook/assets/image (4) (1).png>)![](<../../../.gitbook/assets/image (175).png>)

</details>

<details>

<summary><mark style="color:purple;">Services Cards Resources</mark></summary>

![](<../../../.gitbook/assets/image (114).png>)![](<../../../.gitbook/assets/image (115).png>)![](<../../../.gitbook/assets/image (116).png>)![](<../../../.gitbook/assets/image (30).png>)![](<../../../.gitbook/assets/image (1) (1).png>)![](<../../../.gitbook/assets/image (2) (1).png>)![](<../../../.gitbook/assets/image (3) (1).png>)![](<../../../.gitbook/assets/image (22).png>)![](<../../../.gitbook/assets/image (23).png>)![](<../../../.gitbook/assets/image (24).png>)![](<../../../.gitbook/assets/image (25).png>)![](<../../../.gitbook/assets/image (26).png>)![](<../../../.gitbook/assets/image (27).png>)![](<../../../.gitbook/assets/image (28).png>)![](<../../../.gitbook/assets/image (29).png>)![](<../../../.gitbook/assets/image (159).png>)![](<../../../.gitbook/assets/image (166).png>)![](<../../../.gitbook/assets/image (167).png>)![](<../../../.gitbook/assets/image (168).png>)![](<../../../.gitbook/assets/image (169).png>)![](<../../../.gitbook/assets/image (170).png>)![](<../../../.gitbook/assets/image (171).png>)

![](<../../../.gitbook/assets/image (172).png>)![](<../../../.gitbook/assets/image (173).png>)![](<../../../.gitbook/assets/image (174).png>)![](<../../../.gitbook/assets/image (204).png>)![](<../../../.gitbook/assets/image (205).png>)![](<../../../.gitbook/assets/image (206).png>)![](<../../../.gitbook/assets/image (207).png>)![](<../../../.gitbook/assets/image (208).png>)![](<../../../.gitbook/assets/image (209).png>)![](<../../../.gitbook/assets/image (210).png>)

</details>
