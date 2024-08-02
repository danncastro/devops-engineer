# Cloud First Steps

| Título da tarefa          | Solicitação de negócios                                                                                                                |
| ------------------------- | -------------------------------------------------------------------------------------------------------------------------------------- |
| Primeiros passos na nuvem | O sistema de estabilização da ilha está falhando e precisa de maior confiabilidade e disponibilidade para seus módulos computacionais. |

<figure><img src="../../../.gitbook/assets/image (2) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

<details>

<summary><mark style="color:purple;">Contexto</mark></summary>



</details>

***

## <mark style="color:red;">Amazon EC2</mark>

**Overview**: This solution improves the reliability and availability of the island's stabilization system by moving its computational system by moving its computational module to the AWS global infrastructure

The computational modulo can move to the cloud by using the compute capacity of Amazon Elastic Compute Cloud (Amazon EC2) instances.

An AWS Region is a physical location around the world where data centers are clustered. Each Region consists of two or more Availability Zones (AZs) with a 99.99% service-level agreement (SLA) commitment.

Amazon Elastic Block Store (Amazon EBS) is an efficient, high-performance, block-storage service dedigned for use with Amazon EC2.

**Global Infrastructure Benefits:** To imrpove availability, the computational module runs on EC2 instances deployed in separate AZs within the Region. An AZ is one or more discrete data centers with redundant power, networking, and connectivity in a AWS Region.

***

## <mark style="color:red;">Descrição da tarefa</mark>

Resuma os benefícios da infraestrutura da AWS. Descreva as regiões e zonas de disponibilidade da AWS.&#x20;

* Implante instâncias do Amazon EC2 em várias zonas de disponibilidade.

1. **Launch two EC2 instances into separate AZs in same Region**
2. **Configure a user data scropt to display the instance in a browser**

***

### <mark style="color:purple;">**Step 1**</mark>

1. On the top navigation bar, review the Region selector to ensure that the Region is set to N. Virginia (us-east-1)
2. In the Services search box, type: EC2
3. In the search results, under service, click EC2
4. Go to the next step

<figure><img src="../../../.gitbook/assets/image (4) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">**Step 2**</mark>

1. In the left navigation pane, click EC2 Dashboard.
2. In the Launch instance section, click Launch Instance.
3. Go to the next step

#### <mark style="color:blue;">**Concept**</mark>

An Amazon Elastic Compute Cloud (Amazon EC2) instance is a virtual server in the cloud.

<figure><img src="../../../.gitbook/assets/image (5) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">**Step 3**</mark>

1. In the Name and tags section, for name, type a name that you like, such as: webserver01
2. In the Application and OS images section, under Quick Start, choose Amazon Linux.
3. Scroll down to Amazon Machine Image (AMI).
4. Go to the next step

#### <mark style="color:blue;">**Concept**</mark>

An Amazon Machine Image (AMI) provides the information required to launch an instance. You must specify an AMI when you launch an instance. You can launch multiple instances from a single AMI when you need multiple instances with the same configuration. You can use different AMIs to launch instances when you need different configurations.

<figure><img src="../../../.gitbook/assets/image (6) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">**Step 4**</mark>

1. Click the Amazon Machine Image (AMI) dropdown menu.
2. Choose Amazon Linux 2 AMI (HVM).

* Be sure to choose Amazon Linux 2, not Amazon Linux 2023 AMI, or your launch will fail.

3. For instance type, if not already selected, choose t2.micro.
4. Scroll down to Key pair (login)
5. Go to the next step.

#### <mark style="color:blue;">**Concept**</mark>

When you launch an instance, the instance type that you specify determines the hardware of the host computer used for your instance. Each instance type offers different compute, memory, and storage capabilities and are grouped in instance families based on these capabilities.

<figure><img src="../../../.gitbook/assets/image (7) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">**Step 5**</mark>

1. For Key pair name, choose proceed without a key pair.
2. In the Network settings section, click Edit.
3. Go to the next setp

#### <mark style="color:blue;">**Concept**</mark>

Amazon EC2 uses public key cryptography to encrypt and decrypt login information. Public key cryptography uses a public key to encrypt a piece of data, and then the recipient uses their private key to decrypt the data. The public and private keys are known as a key pair.

<figure><img src="../../../.gitbook/assets/image (8) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">**Step 6**</mark>

1. For VPC, choose LabVpc.

* Your solution will fail if you do not choose this VPC.

2. For Subnet, choose the subnet in the us-east-1a Availability Zone

* Node the AZ choices on the dopdown list.

3. Go to the next step

#### <mark style="color:blue;">**Concept**</mark>

Amazon EC2 is hosted in multiple locations worldwide. These locations are composed of Regions, Availability Zones (AZs), and Local Zones. Each Region, is a separate geographic area that has multiple, isolated localtions known as Availability Zones.

A virtual Private Cloud (VPC) is a virtual network dedicated to your AWS account. While a VPC resides in an AWS Region, a subnet must reside within a single AZ.

<figure><img src="../../../.gitbook/assets/image (9) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">**Step 7**</mark>

1. For Security Group Name, type: Security-Group-Lab
2. For Description, type: HTTP Security Group
3. For Type, choose HTTP.
4. Scroll down to configure storage,
5. Go to the next step;

#### <mark style="color:blue;">**Concept**</mark>

A security group acts as a virtual firewall that controls the traffic for one or more instances. When you launch an instance, you can specify one or more security groups is used. You can add rules to each security group that allows traffic to or from its associated instances.

<figure><img src="../../../.gitbook/assets/image (10) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">**Step 8**</mark>

1. In the configure storage section, for Root volume, choose gp2 from the dropdown menu.

* If gp3 is selected, confirme that you chose the correct AMI in a provious step.

2. Click to expand the Advanced details section.
3. Go to the next step

#### <mark style="color:blue;">**Concepts**</mark>

When you launch an instance, the root device volume contains the image used to boot instance

<figure><img src="../../../.gitbook/assets/image (11) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">**Step 9**</mark>

1. Open the user-data file that you downloaded earlier ([user-data](https://github.com/danncastro/aws-hands-on-labs/blob/main/cloud-quest/cloud-pratitioner/user-data)), and then review the content.

* This user data script launches a web server, using port 80, to display internal information about the instance.
* The code block in your file is longer than what is displayed in the screenshot exemple.

2. Go to the next step

<figure><img src="../../../.gitbook/assets/image (12) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">**Step 10**</mark>

1. On the console, scroll down to User data.
2. Click choose file.
3. Select the user-data file that you review in previous step (not shown)
4. Go to the next step.

<mark style="color:blue;">**Concept**</mark>

When you launch an instance in Amazon EC2, you have the options of passing user data to the instance that can be used to perform common automated configuration task and even run scripts after the instance starts.

<figure><img src="../../../.gitbook/assets/image (13) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">**Step 11**</mark>

1. Review the User data content
2. Go to next step

<figure><img src="../../../.gitbook/assets/image (14) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">**Step 12**</mark>

1. Review the Summary section.

* The Summary section, when your browser is fully expanded, will float on the right side.
* For Software Image (AMI) confirm you have selected Amazon Linux 2.

2. Click Launch instance.
3. Go to the next step

#### <mark style="color:blue;">**Concept**</mark>

It's always a good idea to review the instance launch details that you have configured before you deploy the instance.

<figure><img src="../../../.gitbook/assets/image (15) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">**Step 13**</mark>

1. In the sucess alert, review the message.
2. Scroll down to the bottom of the page.
3. Go to the next step

<figure><img src="../../../.gitbook/assets/image (16) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">**Step 14**</mark>

1. Click view all instances.

* If you receive an error related to insufficient capacity, try using the t3 instance family instead of t2.

2. Go to the next step.

<figure><img src="../../../.gitbook/assets/image (17) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">**Step 15**</mark>

1. In the instances section, choose the check box to select your EC2 instance.
2. Under Instance state, review to ensure that the instance is Running before proceeding.
3. After the instance state display Running, under Public IPv4 DNS, click the copy icon to copy the provided address.

* Do not use the "open address" link.

4. Go to the next step.

#### <mark style="color:blue;">**Concept**</mark>

An instance enters the pending state when it launches for the firt time. It changes to a running state when it is ready for use.

<figure><img src="../../../.gitbook/assets/image (19) (1) (1).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">**Step 16**</mark>

1. In a new browser tab address bar, paste the DNS that you just copied and press Enter.
2. Review the details about your instance.

* The user data script generates a webpage to display the instance details.
* You might need to refresh your browser to see that the instance is running.
* If you see a connection timeout message when opening the webpage, check that the address begins with http and not https.
* The public DNS and the security group are used to access the instance details that appear on the webpag.

<figure><img src="../../../.gitbook/assets/image (20) (1) (1).png" alt=""><figcaption></figcaption></figure>

***

## DIY Activities

* [x] Launch a second Amazon EC2 instance in a different Availability Zone of the same AWS Region.

<figure><img src="../../../.gitbook/assets/image (19) (2).png" alt=""><figcaption></figcaption></figure>

![](<../../../.gitbook/assets/image (20) (2).png>)<img src="../../../.gitbook/assets/image (21) (2).png" alt="" data-size="original">

***
