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

### <mark style="color:red;">Cloud Computing Essentials</mark>

| Título da tarefa                         | Solicitação de negócios                                                                                                         |
| ---------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------- |
| Noções básicas sobre computação em nuvem | O portal da cidade precisa migrar a página de previsão do tamanho das ondas da praia para a AWS para melhorar a confiabilidade. |

<details>

<summary><mark style="color:purple;">Migrar Website para nuvem, garantindo a confiabilidade com Amazon S3</mark></summary>

Articule as características da plataforma de computação em nuvem da AWS. Descreva os principais benefícios do uso de produtos e serviços da AWS. Compare e contraste os serviços de nuvem da AWS com a infraestrutura On-Premises.&#x20;

1. Implemente a hospedagem de uma página da Web estática usando o Amazon S3.

* [x] Create a bucket in Amazon S3.
* [x] Enable static website hosting on the S3 Bucket
* [x] Test access to the webpage hosted on Amazon S3

***

<mark style="color:purple;">Step 1</mark>

1. In the top navigation bar search box, type: S3
2. In the search results, under services, click S3.
3. Go to the next step

<mark style="color:red;">**Concept:**</mark> The AWS Management Console is a web interface to access and manage the broad collection of service provided by Amazon Web Service (AWS).

![](<../../.gitbook/assets/image (94).png>)

<mark style="color:purple;">Step 2</mark>

1. On the General purpose buckets lab tab, click the bucket name that starts with website-bucket-.
2. The bucket name that starts with website-bucket- contains code required for this lab.
3. Go to the next step

<mark style="color:red;">**Concept:**</mark> Amazon Simple Storage Service(Amazon S3) is an object storage service that offers industry-leading scalability, data availability, security, and performance. Customers of all sizes and industries can use Amazon S3 to store and protect any amount of data for a range of use cases, such as data lakes, websites, mobile application, backup and restore, archive, enterprise applications, IoT devices, and big data analystics.

![](<../../.gitbook/assets/image (96).png>)

<mark style="color:purple;">Step 3</mark>

1. On the Objects tab, review the objects in the bucket

* Five files should be displayed
* These files contain the contents of the static webpage
* Local files can be loaded into this S3 bucket by using the Upload button.

2. choose the check box to select text.html.
3. Click Actions to expand the dropdown menu
4. Choose Rename object
5. Go to the next step

<mark style="color:red;">**Concept**</mark><mark style="color:red;">:</mark> A bucket is a container for objects stored in Amazon S3. Every object is contained in a bucket. Amazon S3 offers a range of storage classes for the objects that you store. You choose a class depending on your use case scenario and performance access requirements. Amazon S3 provides storage classes for frequently accessed, infrequently accessedm and archive access objects.

![](<../../.gitbook/assets/image (97).png>)

<mark style="color:purple;">Step 4</mark>

1. Fpr new object name, type: error.html

* This file contains the code for the error page, which opens whenever something goes wrong.

2. Click save changes.
3. Go to the next step

<mark style="color:red;">**Concepts**</mark>: You can choose the geographical. AWS Region where Amazon S3 stores the buckets that you create. You might choose a Region to optimize latency, minimize costs, or address regulatory requirements. Objects stored in an AWS Region never leave the Region unless you explicitly transfer or replicate them to another Region. For example, objects stored in the Europe (ireland) Region never leave it. Howewer, Amazon S3 redundantly stores objects on multiple devices across a minimum of three Availability Zones in an AWS Region. An Availability Zones is one or more dicrete data centers with redundant power, networking, and connectivity in an AWS Region.

![](<../../.gitbook/assets/image (98).png>)

<mark style="color:purple;">Step 5</mark>

1. In the success alert, review the message.
2. Click the Permissions tab.
3. Go to the next step

<mark style="color:red;">**Concept:**</mark> Using Amazon S3, you can upload objects up to 5GB in size with a single PUT operation. For larget objects, up to 5TB in size, use the mutipart upload API.

![](<../../.gitbook/assets/image (99).png>)

<mark style="color:purple;">Step 6</mark>

1. In the block public access(bucket settings) section, review to ensure that blick all public access is set to Off.

* Turning off "blick all public access" is necessary for static web hosting through your S3 bucket.

2. Scroll down to Bucket policy
3. Go to the step

<mark style="color:red;">**Concept:**</mark> By default, all Amazon S3 resources(buckets, objects, and related subresources) are private. Only the resource owner can access them. The resource owner can optionally grant access permissions to others by writing an access policy.

![](<../../.gitbook/assets/image (100).png>)

<mark style="color:purple;">Step 7</mark>

1. In the bucket policy editor window, review the policy

* This policy allows public access to the S3 bucket
* Effect says this policy will Allow acess.
* Principal defines who has access, In this case, \* represents anyone.
* Action defines what users can do to objects in the bucket. In this case, users can only retrieve data with GetObject.
* Resources specifiles that this policy applies to only this bucket.
* Generally, to safeguard against unintentional data exposure, we recommend strict S3 bucket permissions in production.
* Scroll up to the top of the page.
* Go to the next step

<mark style="color:red;">**Concept:**</mark> You can grant permissions to your Amazon S3 resources through bucket policies and user policies. Both options use JSON-based access policy language. An Amazon Resource Name(ARN) uniquely identifies AWS resources.

```json
{
    "Version": "2012-10-17",
    "Id": "StaticWebPolicy",
    "Statement": [
        {
            "Sid": "S3GetObjectAllow",
            "Effect": "Allow",
            "Principal": "*",
            "Action": "s3:GetObject",
            "Resource": "arn:aws:s3:::website-bucket-1bf06570/*"
        }
    ]
}
```

<mark style="color:purple;">Step 8</mark>

1. Click the Properties tab.
2. Go to the next step

<mark style="color:red;">**Concept**</mark>: To hosta static website on Amazon S3, configure you bucket for static website hosting, set permissions, and add in index document, Available options include redirects, logging, and error documents.

![](<../../.gitbook/assets/image (103).png>)

<mark style="color:purple;">Step 9</mark>

1. Scroll down to Static website hosting.
2. Click edit
3. Go to the next step

![](<../../.gitbook/assets/image (104).png>)

<mark style="color:purple;">Step 10</mark>

1. For static website hosting, choose Enable.
2. For hosting type, choose host a static website
3. For index document, type: index.html
4. For error document, type: error.html
5. Go to the next step

<mark style="color:red;">**Concept:**</mark> Amazon S3 supports virtual-hosted-style URL's and path-style URL's.

A virtual-hosted-style URL looks like: https://bucket-name.s3.Region.amazonaws.com/key

A path-style URL look like: https://s3.Region.amazonaws.com/bucket-name/keyname

![](<../../.gitbook/assets/image (105).png>)

<mark style="color:purple;">Step 11</mark>

1. Scroll down to the bottom of the page.
2. Click Save changes
3. Go to the next step

<mark style="color:purple;">Step 12</mark>

1. Croll down to static website hosting.
2. Review to ensure that hosting type is set to bucket hosting.
3. Under bucket website endpoint, click the copy icon to copy the provided endpoint.
4. Go to the next step

![](<../../.gitbook/assets/image (106).png>)

<mark style="color:purple;">Step 13</mark>

1. To load the Beach Wave Conditions webpage, in a new browser tab(or window) address bar, paste the bucket website endpoint that you just copied, and then press Enter.
2. Go to next step

![](<../../.gitbook/assets/image (107).png>)

Finishe.

</details>

#### <mark style="color:blue;">DAP - Arquitetura da solicitação</mark>

<figure><img src="../../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:red;">Cloud First Steps</mark>

| Título da tarefa          | Solicitação de negócios                                                                                                                |
| ------------------------- | -------------------------------------------------------------------------------------------------------------------------------------- |
| Primeiros passos na nuvem | O sistema de estabilização da ilha está falhando e precisa de maior confiabilidade e disponibilidade para seus módulos computacionais. |

<details>

<summary><mark style="color:purple;">Implementar servidores de alta disponibilidade com Amazon EC2</mark></summary>

Resuma os benefícios da infraestrutura da AWS. Descreva as regiões e zonas de disponibilidade da AWS.&#x20;

1. Implante instâncias do Amazon EC2 em várias zonas de disponibilidade.

* [x] Launch two EC2 instances into separate AZs in same Region
* [x] Configure a user data scropt to display the instance in a browser

***

<mark style="color:purple;">**Step 1**</mark>

1. On the top navigation bar, review the Region selector to ensure that the Region is set to N. Virginia (us-east-1)
2. In the Services search box, type: EC2
3. In the search results, under service, click EC2
4. Go to the next step

<img src="../../.gitbook/assets/image (4).png" alt="" data-size="original">

<mark style="color:purple;">**Step 2**</mark>

1. In the left navigation pane, click EC2 Dashboard.
2. In the Launch instance section, click Launch Instance.
3. Go to the next step

<mark style="color:red;">**Concept:**</mark> An Amazon Elastic Compute Cloud (Amazon EC2) instance is a virtual server in the cloud.

![](<../../.gitbook/assets/image (5).png>)

<mark style="color:purple;">**Step 3**</mark>

1. In the Name and tags section, for name, type a name that you like, such as: webserver01
2. In the Application and OS images section, under Quick Start, choose Amazon Linux.
3. Scroll down to Amazon Machine Image (AMI).
4. Go to the next step

<mark style="color:red;">**Concept:**</mark> An Amazon Machine Image (AMI) provides the information required to launch an instance. You must specify an AMI when you launch an instance. You can launch multiple instances from a single AMI when you need multiple instances with the same configuration. You can use different AMIs to launch instances when you need different configurations.

![](<../../.gitbook/assets/image (6).png>)

<mark style="color:purple;">**Step 4**</mark>

1. Click the Amazon Machine Image (AMI) dropdown menu.
2. Choose Amazon Linux 2 AMI (HVM).

* Be sure to choose Amazon Linux 2, not Amazon Linux 2023 AMI, or your launch will fail.

3. For instance type, if not already selected, choose t2.micro.
4. Scroll down to Key pair (login)
5. Go to the next step.

<mark style="color:red;">**Concept:**</mark> When you launch an instance, the instance type that you specify determines the hardware of the host computer used for your instance. Each instance type offers different compute, memory, and storage capabilities and are grouped in instance families based on these capabilities.

![](<../../.gitbook/assets/image (7).png>)

<mark style="color:purple;">**Step 5**</mark>

1. For Key pair name, choose proceed without a key pair.
2. In the Network settings section, click Edit.
3. Go to the next setp

<mark style="color:red;">**Concept:**</mark> Amazon EC2 uses public key cryptography to encrypt and decrypt login information. Public key cryptography uses a public key to encrypt a piece of data, and then the recipient uses their private key to decrypt the data. The public and private keys are known as a key pair.

![](<../../.gitbook/assets/image (8).png>)

<mark style="color:purple;">**Step 6**</mark>

1. For VPC, choose LabVpc.

* Your solution will fail if you do not choose this VPC.

2. For Subnet, choose the subnet in the us-east-1a Availability Zone

* Node the AZ choices on the dopdown list.

3. Go to the next step

<mark style="color:red;">**Concept:**</mark> Amazon EC2 is hosted in multiple locations worldwide. These locations are composed of Regions, Availability Zones (AZs), and Local Zones. Each Region, is a separate geographic area that has multiple, isolated localtions known as Availability Zones.

A virtual Private Cloud (VPC) is a virtual network dedicated to your AWS account. While a VPC resides in an AWS Region, a subnet must reside within a single AZ.

![](<../../.gitbook/assets/image (9).png>)

<mark style="color:purple;">**Step 7**</mark>

1. For Security Group Name, type: Security-Group-Lab
2. For Description, type: HTTP Security Group
3. For Type, choose HTTP.
4. Scroll down to configure storage,
5. Go to the next step;

<mark style="color:red;">**Concept:**</mark> A security group acts as a virtual firewall that controls the traffic for one or more instances. When you launch an instance, you can specify one or more security groups is used. You can add rules to each security group that allows traffic to or from its associated instances.

![](<../../.gitbook/assets/image (10).png>)

<mark style="color:purple;">**Step 7**</mark>

1. In the configure storage section, for Root volume, choose gp2 from the dropdown menu.

* If gp3 is selected, confirme that you chose the correct AMI in a provious step.

2. Click to expand the Advanced details section.
3. Go to the next step

<mark style="color:red;">**Concepts:**</mark> When you launch an instance, the root device volume contains the image used to boot instance

![](<../../.gitbook/assets/image (11).png>)

<mark style="color:purple;">**Step 8**</mark>

1. Open the user-data file that you downloaded earlier ([user-data](https://github.com/danncastro/aws-hands-on-labs/blob/main/cloud-quest/cloud-pratitioner/user-data)), and then review the content.

* This user data script launches a web server, using port 80, to display internal information about the instance.
* The code block in your file is longer than what is displayed in the screenshot exemple.

2. Go to the next step

![](<../../.gitbook/assets/image (12).png>)

<mark style="color:purple;">**Step 9**</mark>

1. On the console, scroll down to User data.
2. Click choose file.
3. Select the user-data file that you review in previous step (not shown)
4. Go to the next step.

<mark style="color:red;">**Concept**</mark>: When you launch an instance in Amazon EC2, you have the options of passing user data to the instance that can be used to perform common automated configuration task and even run scripts after the instance starts.

![](<../../.gitbook/assets/image (13).png>)

<mark style="color:purple;">**Step 10**</mark>

1. Review the User data content
2. Go to next step

![](<../../.gitbook/assets/image (14).png>)

<mark style="color:purple;">**Step 11**</mark>

1. Review the Summary section.

* The Summary section, when your browser is fully expanded, will float on the right side.
* For Software Image (AMI) confirm you have selected Amazon Linux 2.

2. Click Launch instance.
3. Go to the next step

<mark style="color:red;">**Concept:**</mark> It's always a good idea to review the instance launch details that you have configured before you deploy the instance.

![](<../../.gitbook/assets/image (15).png>)

<mark style="color:purple;">**Step 12**</mark>

1. In the sucess alert, review the message.
2. Scroll down to the bottom of the page.
3. Go to the next step

![](<../../.gitbook/assets/image (16).png>)

<mark style="color:purple;">**Step 13**</mark>

1. Click view all instances.

* If you receive an error related to insufficient capacity, try using the t3 instance family instead of t2.

2. Go to the next step.

![](<../../.gitbook/assets/image (17).png>)

<mark style="color:purple;">**Step 14**</mark>

1. In the instances section, choose the check box to select your EC2 instance.
2. Under Instance state, review to ensure that the instance is Running before proceeding.
3. After the instance state display Running, under Public IPv4 DNS, click the copy icon to copy the provided address.

* Do not use the "open address" link.

4. Go to the next step.

<mark style="color:red;">**Concept:**</mark> An instance enters the pending state when it launches for the firt time. It changes to a running state when it is ready for use.

![](<../../.gitbook/assets/image (19).png>)

<mark style="color:purple;">**Step 15**</mark>

1. In a new browser tab address bar, paste the DNS that you just copied and press Enter.
2. Review the details about your instance.

* The user data script generates a webpage to display the instance details.
* You might need to refresh your browser to see that the instance is running.
* If you see a connection timeout message when opening the webpage, check that the address begins with http and not https.
* The public DNS and the security group are used to access the instance details that appear on the webpag.

<img src="../../.gitbook/assets/image (20).png" alt="" data-size="original">

Finished.

</details>

#### <mark style="color:blue;">DAP - Arquitetura da solicitação</mark>

<figure><img src="../../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>

***

***

### <mark style="color:red;">Computing Solutions</mark>

| Título da tarefa       | Solicitação de negócios                                                                                                                            |
| ---------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------- |
| Soluções de Computação | O servidor da escola que executa a solução de agendamento precisa de mais memória. Auxilie no dimensionamento vertical da instância do Amazon EC2. |

<details>

<summary><mark style="color:purple;">Alterando o tipo de familia de instancia para melhor performance.</mark></summary>

Descreva famílias de instâncias e tipos de instâncias do Amazon EC2. Descreva o dimensionamento horizontal e vertical.

1. Reconhecer opções para conectar-se a instâncias do Amazon EC2.

* [x] &#x20;Explore Amazon EC2 instance types.
* [x] Filter EC2 instances based on their attributes.
* [x] Connect to an EC2 instance using Amazon EC2 Session Manager
* [x] View EC2 instance metadata using the instance public IP address.
* [x] Start and stop an EC2 instance by using the Amazon EC2 console.

***

<mark style="color:purple;">**Step 1**</mark>

1. On the top navigation bar, review the Region selector to ensure that the Region is set to N. Virginio (us-east-1).
2. In the Services search box, type: EC2
3. In the search results, under Services, click EC2.
4. Go to next step

![](<../../.gitbook/assets/image (22).png>)

<mark style="color:purple;">**Step 2**</mark>

1. In the left navigation pane, click instances.
2. Go to the next step

<mark style="color:red;">**Concepts:**</mark> Amazon Elastic Compute Cloud (Amazon EC2) instances provide virtual compute capacity in the cloud. With a choice of processor, storage, networking, operating system, and purchase model the service offers a broad and deep solution.

![](<../../.gitbook/assets/image (23).png>)

<mark style="color:purple;">**Step 3**</mark>

1. In the instances section, choose the check box to select the AWS Computing Solutions instance.
2. Click the Details tab.
3. Review the details.
4. Go to the next step

<mark style="color:red;">**Concepts**</mark>: Information about the instance (such as its public IP, private IP, and public DNS) is displyaed in the instance summary section by selecting the EC2 instance.

![](<../../.gitbook/assets/image (24).png>)

<mark style="color:purple;">**Step 4**</mark>

1. in the left navigation pane, click Instance Types.
2. Go to the next step

<mark style="color:red;">**Concept:**</mark> Amazon EC2 provides a wide selection of instance types that belong to instance families that are optimized to fit different use cases.

![](<../../.gitbook/assets/image (25).png>)

<mark style="color:purple;">**Step 5**</mark>

1. In the Instances types section, in the filter box, type the fllowing and press Enter after each:

* t3.large
* c5.large
* r5.large

2. Choose the three check boxes to select each added instance types.
3. Go to the next step

<mark style="color:red;">Concept:</mark> Each instance type includes one or more instance sizes, so you can scale your resources to the requirements of your target workload.

![](<../../.gitbook/assets/image (26).png>)

<mark style="color:purple;">**Step 6**</mark>

1. For each instance types, review the instance details.
2. To compare compute, networking, storage, accelerators, and pricing information, scroll down.
3. In the left navigation pane, click instances.
4. Go to the next step

<mark style="color:red;">**Concept:**</mark> Using the Amazon EC2 console, you can filter instance attributes such as instance types, instance family, and instance size. You can search using keyworkds, atribute names, or expressions.

![](<../../.gitbook/assets/image (27).png>)

<mark style="color:purple;">**Step 7**</mark>

1. Choose the check box to select the AWS Computing Solutions instances.
2. On the details tab, under Public IPv4 address, click the copy icon to copy the provided address.

* Do not use the "open address" link

3. Go to the next step

<mark style="color:red;">**Concept:**</mark> Instance metadata is data about your instance that you can use to configure or manage the running instance. Instance metadata is divided into categories; for exemple, host name, events, and securiy groups.

![](<../../.gitbook/assets/image (28).png>)

<mark style="color:purple;">**Step 8**</mark>

1. Open a new browser tab, and then paste the IP Address that you just copied and press Enter (not shown).
2. Review the instance details, and then return to the previous browser.

* You should land on the instance page in the Amazon EC2 Console.

3. Go to the next step.

<mark style="color:red;">**Concept:**</mark> When creeating a new insntace, you can enable the instance metadata service (IMDS) through the Advanced details sections. This way, you can display attibute details by using the instance's public IP.

![](<../../.gitbook/assets/image (29).png>)

<mark style="color:purple;">**Step 9**</mark>

1. In the instances section, click Connect.
2. Go to the next step

<mark style="color:red;">**Concept:**</mark> You have the flexibility to connect to an EC2 instance by using Amazon EC2 Instance Connect, Session Manager (a capability of AWS Systems Manager), or an SSH client.

![](<../../.gitbook/assets/image (30).png>)

<mark style="color:purple;">**Step 10**</mark>

1. Click EC2 Instance Connect tab.
2. Review the connection settings.
3. Click the Session Manager tab.
4. Go to the next step

<mark style="color:red;">**Concept:**</mark> EC2 Instance Connect provides an efficient and secure way to connect to your Linux instances. EC2 Instance Connect uses AWS Identity and Access Management (IAM) policies and principals to control SSH access to you instances, removing the need to share and manage SSH keys.

![](<../../.gitbook/assets/image (31).png>)

<mark style="color:purple;">**Step 11**</mark>

1. Review the Session Manager usage details.
2. Click the SSH client tab.
3. Go to the next step

<mark style="color:red;">**Concept:**</mark> Using Session Manager, you can manage your EC2 instances through an interactive one-click, browser-based shell or through the AWS Command Line Interface (AWS CLI). After the session begins, you can run bash commands as you would through any other connection type.

![](<../../.gitbook/assets/image (32).png>)

<mark style="color:purple;">**Step 12**</mark>

1. Review the requirements for connecting through SSH.
2. Click to go back to the Session Manager tab.
3. Go to the next step.

<mark style="color:red;">**Concept:**</mark> You can connect to your instance by using an SSH client on your local device through your instance key pair. Your device might have an SSH client by default or you might need to install an SSH client.

![](<../../.gitbook/assets/image (33).png>)

<mark style="color:purple;">**Step 13**</mark>

1. Click connect, and then wait for the terminal window to open.
2. Go to the next step.

<mark style="color:red;">**Concept:**</mark> Session Manager provides secure and auditable node management without the need to open inbound ports, maintain bastion hosts, or manage SSH keys. Session Manager also allows you to comply with corporate policies that require controlled access to managed nodes, strict security practicesm and fully auditable logs with node access details, while providing end users with simple onde-click cross-platform access to your managed nodes.

![](<../../.gitbook/assets/image (34).png>)

<mark style="color:purple;">**Step 14**</mark>

1. To provide root privileges to the current session, in the terminal window, at the command prompt, run the following command (type the command and press Enter):  `sudo -i`
2. To change to the application directory, run: `cd ../home/ec2-user/sample-app`

* Be sure to add a space between `cd` and the `../` command.
* A sample application resides on this instance.

3. To view the files in the sample\_app directory, run: `ls`
4. To check the instance log, run: `tail -lf aws_compute_solutions.log`

<mark style="color:red;">**Concept:**</mark> After you are connected to the instance, you can control the instance by using AWS CLI command. The command prompt behaves as if you are connected locally.

![](<../../.gitbook/assets/image (35).png>)

<mark style="color:purple;">**Step 15**</mark>

1. Review the log details.

* To quit, press CTRL + C on your keyboard.

2. Close the terminal tab to return to the instances page in the Amazon EC2 console.
3. Go to the next step.

![](<../../.gitbook/assets/image (36).png>)

<mark style="color:purple;">**Step 16**</mark>

1. Click Actions to expand the dropdown menu.
2. Choose Instance settings.
3. Choose Edit user data.
4. Go to the next step

<mark style="color:red;">**Concept:**</mark> You can use the Actions dropdown menu to control the instance state and modify instance attributes.

![](<../../.gitbook/assets/image (37).png>)

<mark style="color:purple;">**Step 17**</mark>

1. Under Current user data, review the commands.
2. Click Cancel.
3. Go to the next step

<mark style="color:red;">**Concept**</mark>**:** You can also use instance metadata to access user data that you specified when launching your instance.

![](<../../.gitbook/assets/image (38).png>)

<mark style="color:purple;">**Step 18**</mark>

1. In the left navigation pane, click instances.
2. In the Instances section, click Instance state to expand the dropdown menu.
3. Choose Stop instance.
4. Go to the next step.

<mark style="color:red;">**Concept:**</mark> Using the instance state dropdown menu, you can place an instance into different states of activity. You can start and stop an instance if it has an Amazon Elastic Block Store (Amazon EBS) volume as its root device.

![](<../../.gitbook/assets/image (39).png>)

<mark style="color:purple;">**Step 19**</mark>

1. In the pop-up box, click Stop.
2. Go to the next step

<mark style="color:red;">**Concept:**</mark> Afteran instance stops, CPU usage and data transfer charges cease, but storage charges for any attached Amazon EBS volumes continue.

![](<../../.gitbook/assets/image (40).png>)

<mark style="color:purple;">**Step 20**</mark>

1. Review the successfully stopped banner.
2. On the Details tab, after the instance state changes to Stopped, review the Public IPv4 address and DNS.

* They should both be empty. You may need to click the refresh button under the banner to see the empty settings.

3. Go to the next step.

<mark style="color:red;">**Concept:**</mark> Each time you start a stopped instance, AWS charges a minimum of one minutes for the use of per-second billing instances. After one minute, AWS charges only for the seconds that you use.

![](<../../.gitbook/assets/image (41).png>)

<mark style="color:purple;">**Step 21**</mark>

1. In Actions to expand the dropdown menu.
2. Choose instance settings.
3. Review the available options.

* You have different options to change your instance, such as type, termination protectionm and shutdown behavior.

4. Go to the next step.

<mark style="color:red;">**Concept:**</mark> You must stop your Amazon EBS-backend instance before you can change its instance type. Plan for downtime while your instance is stopped. Stopping the instance and changing its instance type might take a few minutes, and restarting your instance might take a variable amount of time depending on your application's startup scripts.

![](<../../.gitbook/assets/image (42).png>)

<mark style="color:purple;">**Step 22**</mark>

1. Click Instance state to expand the dropdown menu.
2. Choose Start Instance.
3. Go to the next step

![](<../../.gitbook/assets/image (43).png>)

<mark style="color:purple;">**Step 23**</mark>

1. After the instance reaches the Running state, review the instance details.

* Node that the public IPv3 address and DNS are now populated.

2. Go to the next step.

![](<../../.gitbook/assets/image (44).png>)

Finished.

</details>

#### <mark style="color:blue;">DAP - Arquitetura da solução</mark>

<figure><img src="../../.gitbook/assets/image (21).png" alt=""><figcaption></figcaption></figure>

***

***

### <mark style="color:red;">Networking Concepts</mark>

| Título da tarefa  | Solicitação de negócios                                                                                      |
| ----------------- | ------------------------------------------------------------------------------------------------------------ |
| Conceitos de rede | Ajude o banco a configurar um ambiente de rede seguro que permita a comunicação entre recursos e a internet. |

<figure><img src="../../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>

<details>

<summary><mark style="color:purple;">Configuração de rede segura com Amazon VPCs</mark></summary>

Defina os principais recursos de VPCs, sub-redes, gateways de internet e tabelas de rotas. Descreva os benefícios de usar Amazon VPCs. Declare os conceitos básicos de notação de bloco CIDR e endereçamento IP.&#x20;

1. Explique como o tráfego VPC é roteado e protegido usando gateways, listas de controle de acesso à rede e grupos de segurança.

* [ ] Explore the components that comprise a virtual private cloud (VPC)
* [ ] Configure a route table attached to a subnet within a VPC.
* [ ] Configure an internet gateway inside a VPC.
* [ ] Configure inbound rules within a security group to control access.

***

</details>





|                                                                      |                                                                                                                                                              |
| -------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| <ol start="4"><li></li></ol>                                         |                                                                                                                                                              |
| <ol start="5"><li>Bases de dados na prática</li></ol>                | Melhore as operações, o desempenho e a disponibilidade do banco de dados relacional da seguradora.                                                           |
| <ol start="6"><li>Conectando VPCs</li></ol>                          | A equipe de marketing da cidade quer Amazon VPCs separadas para cada departamento que permita a comunicação entre Amazon VPCs.                               |
| <ol start="7"><li>Primeiro banco de dados NoSQL</li></ol>            | Ajude o serviço de streaming de entretenimento da ilha a implementar um banco de dados NoSQL para desenvolver novos recursos.                                |
| <ol start="8"><li>Sistemas de arquivos na nuvem</li></ol>            | Ajude a agência de modelos de animais de estimação da cidade a compartilhar dados de arquivos sem provisionar ou gerenciar armazenamento.                    |
| <ol start="9"><li>Aplicações de autocura e dimensionamento</li></ol> | Ajude o café de jogos da cidade a implementar servidores de recuperação automática, restringindo os clientes a uma capacidade de provisionamento específica. |
| <ol start="10"><li>Aplicações Web de Alta Disponibilidade</li></ol>  | Ajude a agência de viagens a criar uma arquitetura de aplicativo web de alta disponibilidade.                                                                |
| <ol start="11"><li>Conceitos Básicos de Segurança</li></ol>          | Ajude a melhorar a segurança na bolsa de valores da cidade garantindo que os engenheiros de suporte possam executar somente ações autorizadas.               |
| <ol start="12"><li>Economia da Nuvem</li></ol>                       | A loja de pranchas de surfe da cidade precisa de uma estimativa de custo de uma arquitetura com uso variável de recursos.                                    |

| Objetivos de aprendizado                                                                                                                                                                                                                                                                                                                               |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| <ol start="3"><li></li></ol>                                                                                                                                                                                                                                                                                                                           |
| <ol start="4"><li></li></ol>                                                                                                                                                                                                                                                                                                                           |
| <ol start="5"><li>Revise os recursos, benefícios e tipos de banco de dados disponíveis com o Amazon RDS. Descreva o dimensionamento vertical e horizontal no Amazon RDS. Use réplicas de leitura do Amazon RDS para aumentar o desempenho do banco de dados. Implemente implantações multi-AZ do Amazon RDS para aumentar a disponibilidade.</li></ol> |
| <ol start="6"><li>Resuma como o peering de VPC funciona com o Amazon VPC. Explique as etapas para estabelecer uma conexão de peering de VPC. Crie uma conexão de peering entre dois Amazon VPCs. Estabeleça uma conexão de peering entre Amazon VPCs usando uma sub-rede específica.</li></ol>                                                         |
| <ol start="7"><li>Resuma os diferentes usos de bancos de dados comuns criados para propósitos específicos. Descreva os recursos e benefícios do Amazon DynamoDB. Interaja com os elementos e atributos de um banco de dados Amazon DynamoDB. Configure um banco de dados NoSQL com o Amazon DynamoDB.</li></ol>                                        |
| <ol start="8"><li>Resuma as diferentes opções de armazenamento disponíveis na AWS. Resuma os principais recursos e benefícios do Amazon EFS. Identifique casos de uso comercial para o Amazon EFS. Configure endpoints do Amazon EFS para acessar o armazenamento centralizado.</li></ol>                                                              |
| <ol start="9"><li>Descreva os recursos de autocura e dimensionamento oferecidos pelos grupos de Auto Scaling. Crie um grupo de Auto Scaling com limites de recursos rígidos. Configure um grupo de Auto Scaling para responder a um evento baseado em tempo.</li></ol>                                                                                 |
| <ol start="10"><li>Descreva os princípios para arquitetar aplicativos de alta disponibilidade. Resuma os benefícios de usar um AWS Application Load Balancer (ALB). Use grupos de Auto Scaling com balanceamento de carga e monitoramento de integridade.</li></ol>                                                                                    |
| <ol start="11"><li>Descreva o processo de criação e as diferenças entre usuários, funções e grupos do AWS IAM. Revise a estrutura e os componentes das Políticas do AWS IAM. Resuma o Modelo de Responsabilidade Compartilhada da AWS e os programas de conformidade.</li></ol>                                                                        |
| <ol start="12"><li>Descreva como as estimativas de preços são obtidas. Use a Calculadora de Preços da AWS para estimar o preço de uma arquitetura da AWS.</li></ol>                                                                                                                                                                                    |

<details>

<summary><mark style="color:purple;">Challenges</mark></summary>

<img src="../../.gitbook/assets/image (109).png" alt="" data-size="original">![](<../../.gitbook/assets/image (117).png>)

</details>

<details>

<summary><mark style="color:purple;">Services Cards</mark></summary>

![](<../../.gitbook/assets/image (114).png>)![](<../../.gitbook/assets/image (115).png>)![](<../../.gitbook/assets/image (116).png>)

</details>

***
