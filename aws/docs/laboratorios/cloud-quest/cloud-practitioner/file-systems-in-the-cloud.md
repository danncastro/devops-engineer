---
description: >-
  Deploy and maintain a file system infrastructure that is accessible from three
  different servers.
---

# File Systems in the Cloud

| Título da tarefa              | Solicitação de negócios                                                                                                                   |
| ----------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------- |
| Sistemas de arquivos na nuvem | Ajude a agência de modelos de animais de estimação da cidade a compartilhar dados de arquivos sem provisionar ou gerenciar armazenamento. |

<figure><img src="../../../.gitbook/assets/image (211).png" alt=""><figcaption></figcaption></figure>

<details>

<summary><mark style="color:purple;">Contexto</mark></summary>

<mark style="background-color:blue;">Client</mark><mark style="background-color:yellow;">:</mark> Hi there. Thanks for coming by to help us out. This is an important time for the city's only pet modeling agency.

<mark style="background-color:orange;">Architect:</mark> No problem. I am happy to help, and i love pets, too!

<mark style="background-color:blue;">Client</mark>: Great! Let me. In the past year we have established three new company branches in the city, and each branch has its own pet image server that connects to a local client management application.

<mark style="background-color:blue;">Client</mark>: Each server stores images of all of of our pet clients along with informational metadata. We use a custom application to sync the client data across all three branches, but it takes too much time to access the images, and it's not always consistent.

<mark style="background-color:orange;">Architect</mark>: I see. Is the storage capacity on each branch server the same?

<mark style="background-color:blue;">Client</mark>: No. And that is another problem. Our synching solution fails sometimes because one branch server might run out of storage space. We need a solution that centralizes our image storage and scales automatically.

<mark style="background-color:orange;">Architect</mark>: Okay. one more question. Does your team update the same files and also restrict certain files with permissions?

<mark style="background-color:blue;">Client</mark>: Yes, all branches access and update the same pet client files, and we have certain folders for our VIP clients that only our concierge team has access to.

<mark style="background-color:orange;">Architect</mark>: Thanks! Based on your answers, I would recommend Amazon Elastic File System. Amazon EFS is a serverless, set-and-forget solution that you can use to share file data without provisioning or managing storage.

<mark style="background-color:orange;">Architect</mark>: Using Amazon EFS, you can create shared network drives so that your branches, can access pet client photos from a central location, and you can restrict access with file-level permissions.

<mark style="background-color:blue;">Client</mark>: That sounds good, but what about the storage capacity?

<mark style="background-color:orange;">Architect</mark>: Amazon EFS provides petabyte-scale storage that grows and shrinks automatically as you add and remove files.

<mark style="background-color:blue;">Client</mark>: Nice! We want centralized storage, but what happens if Amazon EFS fails? Will we lose all of our client data?

<mark style="background-color:orange;">Architect</mark>: That is quite unlikely. Amazon EFS is highly available and is designed for 99.999999999 percent durability.

<mark style="background-color:orange;">Architect</mark>: Also, by default, for file systems using standard storage classes, every Amazon EFS object is redundantly stored across multiple Availability Zones. Amazon EFS is even designed to sustain concurrent device failures by quickly detecting and repairing any lost redundancy.

<mark style="background-color:blue;">Client</mark>: Wow, that's amazing! I think moving to Amazon EFS might work. Can you help us create an EFS file system in which all of our branches can access pet client photos from a single location?

<mark style="background-color:blue;">Client</mark>: Will you help us create an EFS file system?

<mark style="background-color:orange;">Architect</mark>: Accept

<mark style="background-color:blue;">Client</mark>: Great! I will let you get to work

</details>

***

## <mark style="color:red;">Amazon EFS</mark>

**Overview**: This solution uses three web servers distributed across separate Availability Zones. The web servers need to share the same unstructured data. The data consists of PHP files, config files, plugins, and images

**Benefits**: Amazon Elastic File System (Amazon EFS) is used here as a shared file system. Amazon EFS can be used to share file data without provisioning or managing servers.

**Features**: Amazon EFS automatically grows and shrinks as files are added and removed, so capacity doesn't need to be managed.

Servers access shared data in Amazon EFS by using mount targets in each Availability Zone.

Applications on each server view each mounted file system as a local path, similar to "`/mnt/efs`"

***

## <mark style="color:red;">Descrição da tarefa</mark>

Resuma as diferentes opções de armazenamento disponíveis na AWS.&#x20;

* Resuma os principais recursos e benefícios do Amazon EFS.&#x20;
* Identifique casos de uso comercial para o Amazon EFS.&#x20;
* Configure endpoints do Amazon EFS para acessar o armazenamento centralizado.

1. **Launch and configure an Amazon EFS file system**
2. **Mount the file system to an Amazon EC2 instance.**
3. **Connect a second EC2 instance to the same file system**
4. **Share files between the two EC2 instances.**

***

### <mark style="color:purple;">Step 1</mark>

1. In the top navigation bar search box, type: EC2
2. In the search results, under Services, click EC2
3. Go to the next step.

#### <mark style="color:blue;">Concept</mark>

Amazon Elastic File System (Amazon EFS) provides a serverless, set-and-forget elastic file system that you can use to share file data without provisioning or managing storage.

<figure><img src="../../../.gitbook/assets/image (212).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 2</mark>

1. In the left navigation pane, click Instances.
2. Go to the next step

#### <mark style="color:blue;">Concept</mark>

Using Amazon EFS, you can grow and shrink your file systems automatically as you add and remove files, removing the need to provision and manage capacity to accommodate growth.

<figure><img src="../../../.gitbook/assets/image (213).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 3</mark>

1. In the Instances section, review the names of the three existing instances

* You can safely ignore the instances type if it differs from the example screenshot and any others in the tab.

2. To review all of the details, scroll to the right
3. Go to the next step

#### <mark style="color:blue;">Concept</mark>

Amazon EFS creates a shared storage file system that is available concurrently to multiple instances in Amazon Elastic Compute Cloud (Amazon EC2).

<figure><img src="../../../.gitbook/assets/image (214).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 4</mark>

1. Under Availability Zone, review the Availability Zone for each instance.
2. In the left navigation pane, scroll down to Network & Security.
3. Click Security Groups.
4. Go to the next step.

#### <mark style="color:blue;">Concept</mark>

After creating the EFS file system, you create mount targets on each subnet. The mount target enables communication from Amazon EC2 instances on the subnet. Amazon EFS uses the Network File System (NFSv4) protocol. EC2 instances that connect to the file system are NFS clients.

<figure><img src="../../../.gitbook/assets/image (215).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 5</mark>

1. In the Security Groups section, review the Web\_Server\_SG security group.

* The webserver security group is already linked to the web servers.

2. Click Create security group.
3. Go to the next step.

#### <mark style="color:blue;">Concept</mark>

When you create an Amazon EFS mount target, you must attach a security group. The security group determines which EC2 instances can access the file system as NFS clients.

<figure><img src="../../../.gitbook/assets/image (216).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 6</mark>

1. For Security group name, type: PetModels-EFS-1-SG
2. For Description, type: Restrict access to web servers only.
3. For VPC, on the dropdown menu, choose PetModels.

* You might need to remove the existing VPC by clicking X.

4. In the inbound rules section, click Add rule.
5. Go to the next step

#### <mark style="color:blue;">Concept</mark>

Security groups are linked to a single VPC. You can assign a security group to one or more EC2 instances, but each instance must be in the same VPC as the security group.

<figure><img src="../../../.gitbook/assets/image (217).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 7</mark>

1. To configure the new rule, for Type, choose NFS.
2. Unser Source, click the search field.
3. In the dropdown menu, choose the webserver security group.
4. Go to the next step.

#### <mark style="color:blue;">Concept</mark>

EFS file systems require an inbound NFS rule. By selecting a security group as the incoming source, any EC2 instances linked to the security group you select will have NFS client access to the file system.

<figure><img src="../../../.gitbook/assets/image (218).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 8</mark>

1. Scroll down to the bottom of the page.
2. Click Create security group.
3. Go to the next step.

<figure><img src="../../../.gitbook/assets/image (54).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 9</mark>

1. Under Security group name, review the name.
2. Go to the next step.

#### <mark style="color:blue;">Concept</mark>

After the Amazon EFS security group is created, you are prepared to create the file system.

<figure><img src="../../../.gitbook/assets/image (2) (1).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 10</mark>

1. In the top navigation bar search box, type: EFS
2. In the search results, under Services, click EFS.
3. Go to the next step

#### <mark style="color:blue;">Concept</mark>

Amazon EFS is built to scale on demand, up to petabytes of storage capacity, without disrupting applications.

<figure><img src="../../../.gitbook/assets/image (3) (1).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 11</mark>

1. On the Amazon EFS console home page, click Create file system.
2. Go to the next step.

#### <mark style="color:blue;">Concept</mark>

To create Amazon EFS resources, such as a file system and access points, a user must have AWS identity and Access Management (IAM) permissions for the corresponding API action and resource.

<figure><img src="../../../.gitbook/assets/image (4) (1).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 12</mark>

1. In the pop-up box, for name, type: PetModels-EFS-1
2. For VPC, choose the PetModels VPC.
3. Click Customize
4. Go to the next step

#### <mark style="color:blue;">Concept</mark>

You can choose to use Standard or One Zone storage classes in Amazon EFS. Standard stores data within and across multiple Availability Zones (AZs). One Zone stores data redundantly within a single AZ, at a lower price than Standard, for workloads that don't require multi-AZ resilience.

<figure><img src="../../../.gitbook/assets/image (5) (1).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 13</mark>

1. Under Automatic backups, clear the check box to deselect Enable automatic backups.
2. Under Lifecycle management, for Transition into Infrequent Access (IA), choose None
3. For Transition into Archive, choose None.
4. Sroll down to the Performance settings section.
5. Go to the next step

#### <mark style="color:blue;">Concept</mark>

You can disable automatic backups and lifecycle management to reduce costs until you are in production.

<figure><img src="../../../.gitbook/assets/image (6) (1).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 14</mark>

1. In the Performance settings section, for Throughput mode, choose the radio button to select Bursting.
2. Click Next.
3. Go to the next step

<figure><img src="../../../.gitbook/assets/image (7) (1).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 15</mark>

1. To remove the subnet, under Mount targets, for AZ us-east-1c, click Remove.
2. For AZ us-east-1b, click Remove
3. To remove the security group, for AZ us-east-1a, under Security groups, click the X in the existing security group.
4. Go to the next step

#### <mark style="color:blue;">Concept</mark>

For simplucity during testing, you can start with a single mount target in a sinble Availability Zone.

<figure><img src="../../../.gitbook/assets/image (8) (1).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 16</mark>

1. For AZ us-east-1a, under Security group, choose the PetModels-EFS-1-SG security group.
2. Click Next.
3. Go to the next step.

#### <mark style="color:blue;">Concept</mark>

By attaching your custom security group to the mount target, you control where the source of incoming traffic to the file system can originate.

<figure><img src="../../../.gitbook/assets/image (9) (1).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 17</mark>

1. In the File system policy step, click next.
2. Go to the next step

<figure><img src="../../../.gitbook/assets/image (10) (1).png" alt=""><figcaption></figcaption></figure>



***

### <mark style="color:purple;">Step 18</mark>

1. In the Review and create step, scroll down to the bottom of the page.
2. Click Create
3. Go to the next step

<figure><img src="../../../.gitbook/assets/image (11) (1).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 19</mark>

1. In the success alert, review the message.
2. In the File system section, under Name, click PetModels-EFS-1.
3. Go to the next step

#### <mark style="color:blue;">Concept</mark>

After the new file system is available, you can use automatically created commands to mount the file system.

<figure><img src="../../../.gitbook/assets/image (12) (1).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 20</mark>

1. Click Attach
2. Go to the next step

<figure><img src="../../../.gitbook/assets/image (13) (1).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 21</mark>

1. In the pop-up box, under Using the EFS mount helper, click the copy icon to copy the mount command, and then paste it in your text editor.

* You will use this command in later steps.

2. Click Close.
3. Go to the next step

#### <mark style="color:blue;">Concept</mark>

The Amazon EFS client (amazon-efs-utils) is an open-source collection of Amazon EFS tools. This package is available in the Amazon Linux package repositories, and you can build and install the package on other Linux distributions.

The Amazon EFS client includes a mount helper and tooling that helps you perform encryption of data in transit for Amazon EFS file systems.

<figure><img src="../../../.gitbook/assets/image (14) (1).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 22</mark>

1. In the top navigation bar search box, type: EC2
2. In the search results, under Services, click EC2
3. Go to the next step

#### <mark style="color:blue;">Concept</mark>

After you have copied the mount command, you can connect to your Amazon EC2 instance and mount the file system.

<figure><img src="../../../.gitbook/assets/image (15) (1).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 23</mark>

1. In the left navigation pane, click Instances.
2. Go to the next step

<figure><img src="../../../.gitbook/assets/image (16) (1).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 24</mark>

1. In the Instances section, choose the check box to select WebServer1.
2. Click Connect.
3. Go to the next step

#### <mark style="color:blue;">Concept</mark>

To connect to an instance, Amazon EC2 supports SSH, Session Manager (a capability of AWS Systems Manager), or Amazon EC2 Instance Connect.

Session Manager is a fully managed AWS System Manager capability. With Session Manager, you can manage your Amazon Elastic Compute Cloud (Amazon EC2) instances, edge services, and on-premises servers and virtual machines (VMs).

<figure><img src="../../../.gitbook/assets/image (17) (1).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 25</mark>

1. In the Connect to instance page, click Session Manager.
2. Click Connect.

* The Session Manager terminal opens in a new browser tab (or window). Keep the previous browser tab open.

3. Go to the next step

#### <mark style="color:blue;">Concept</mark>

Session Manager provides secure and auditable node management without the need to open inbound ports, maintain bastion hosts, or manage SSH keys. Session Manager also allows you to comply with corporate policies that require controlled access to managed nodes, strict security practices, and fully auditable logs with node access details, while providing end users with simple one-click cross-platform access to your managed nodes.

<figure><img src="../../../.gitbook/assets/image (18) (1).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 26</mark>

1. In the terminal, at the command prompt, run (type the command and press Enter): sudo -i
2. In the terminal, run: sudo yum install -y amazon-efs-utils
3. Go to the next step

#### <mark style="color:blue;">Concept</mark>

The Amazon EFS client is available in the Amazon Linux package repositories. You can build and install the package on other Linux repositories. Installing the utilities makes the mount commands quicker to process and troubleshoot.

<figure><img src="../../../.gitbook/assets/image (19) (1).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 27</mark>

1. Review the packages installed from the yum command in the previous step.
2. Go to the next step

<figure><img src="../../../.gitbook/assets/image (20) (1).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 28</mark>

* In this step, you use Linux commands to create a data directory, and then mount the newly created Amazon EFS file system to that directory. You create a log file and append information to it. The log file and its contents will be visible from other instances that have the same file system mounted.

1. In the terminal, run: mkdir data

* If you receive a Permission Denied message, run: cd \~/

2. In the terminal, run: ls
3. In the terminal, paste the sudo mount command that you copied from the Amazon EFS console in an earkuer step. At the end of the command, replace the "efs" folder name with "data" (without quotes) and press Enter.

* The command should look similar to what is displayed in the screenshot example.

4. In the terminal, run: cd data
5. To create a log file, run: sudo bash -c "cat>> efs-1-setup.log"

* No output will appear. Instead, the cursor will move to a new line and wait for your next input.

6. In the terminal, run: efs-1 mounted in site A
7. To end the cat session, on your keyboard, press CTRL + C.
8. To view the log file contents, run: cat efs-1-setup.log
9. Go to the next step.

<figure><img src="../../../.gitbook/assets/image (21) (1).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 29</mark>

1. Return to the previous browser tab, and then, in the top navigation bar search box, type: EFS
2. In the search results, under Services click EFS.
3. Go to the next step

#### <mark style="color:blue;">Concept</mark>

After successfully mounting the new file system, you are ready to add more mount points for other subnets in other Availability Zones within the same VPC.

<figure><img src="../../../.gitbook/assets/image (22) (1).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 30</mark>

1. In the File systems section, under Name, click PetModels-EFS-1.
2. Go to the next step.

#### <mark style="color:blue;">Concept</mark>

You can mount a file system on compute instances in your virtual private cloud (VPC), including Amazon EC2, Amazon Elastic Container Service (Amazon ECS), and AWS Lambda.

<figure><img src="../../../.gitbook/assets/image (23) (1).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 31</mark>

1. Click the Network tab.
2. Click Manage.
3. Go to the next step.

#### <mark style="color:blue;">Concept</mark>

Using the Network tab in the console, you can display and manage your mount targets.

<figure><img src="../../../.gitbook/assets/image (24) (1).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 32</mark>

1. Under Mount targets, click Add mount target.
2. Go to the next step.

#### <mark style="color:blue;">Concept</mark>

For Amazon EFS file systems that use Standard storage classes, you can create a mount target in each Availability Zone in an AWS Region.

<figure><img src="../../../.gitbook/assets/image (25) (1).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 33</mark>

1. Under Availability zone, review to ensure us-east-1b is selected.
2. Under Subnet ID, on the dropdown menu, choose PetModels-Subnet2.
3. Go to the next step.

#### <mark style="color:blue;">Concept</mark>

You can create mount targets for a file system by using the AWS Management Console, AWS CLI, or by programmatically using AWS SDKs. When using the console, you can create mount targets when you first create file system or after the file system is created.

<figure><img src="../../../.gitbook/assets/image (26) (1).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 34</mark>

1. For Security groups, on the dropdown menu, choose PetModels-EFS-1-SG.
2. Click Save.

* If the error message "User is not authorized to perform that action on the specified resource" appears, you can safely ignore it and continue the lab.

3. Go to the next step.

#### <mark style="color:blue;">Concept</mark>

In most cases, you will assign the same security group to each mount target.

<figure><img src="../../../.gitbook/assets/image (27) (1).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 35</mark>

1. After a few minutes, on the Network tab, click the refresh icon.
2. For the new mount target, under Mount target state, review to ensure that the state is Available.

* If needed, wait for the state to change before proceeding.

3. Go to the next step.

#### <mark style="color:blue;">Concept</mark>

Each mount target installs an elastic network interface (ENI) into the chosen subnet. An ENI is a logical networking component in a VPC that represents a virtual network card. The ENI automatically receives an IP address from the VPC.

<figure><img src="../../../.gitbook/assets/image (28) (1).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 36</mark>

1. In the top navigation bar search box, type: EC2
2. In the search results, under Services, click EC2.
3. Go to the next step.

#### <mark style="color:blue;">Concept</mark>

After creating an additional mount target, you can mount the file system on instances in the specified subnet.

<figure><img src="../../../.gitbook/assets/image (29) (1).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 37</mark>

1. In the left navigation pane, click Instances.
2. Go to the next step.

<figure><img src="../../../.gitbook/assets/image (30) (1).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 38</mark>

1. In the Instances section, choose the check box to select WebServer2.
2. Click Connect.
3. Go to the next step.

<figure><img src="../../../.gitbook/assets/image (31) (1).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 39</mark>

1. In the Connect to instance page, click Session Manager.
2. Click Connect.
3. Go to the next step.

<figure><img src="../../../.gitbook/assets/image (32) (1).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 40</mark>

1. In the terminal, run: sudo -i
2. In the terminal, run: sudo yum install -y amazon-efs-utils
3. Go to the next step.

<figure><img src="../../../.gitbook/assets/image (33) (1).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 41</mark>

* In this step, you create a data directory, mount your Amazon EFS file system to the data directory, add entries to the existing log file, and view them.

1. In the terminal, run: mkdir data

* If you receive a Permission Denied message, run: cd \~/

2. In the terminal, run: ls
3. In the terminal, paste the sudo mount command that you copied from the Amazon EFS console in an earlier step. At the end of the command, replace the "efs" folder name with "data" (without quotes) and press Enter.

* The command should look similar to what is displayed in the screenshot example.

4. In the terminal, run: cd data
5. In the terminal, run: cat efs-1-setup.log
6. In the terminal, run: sudo bash -c "cat >> efs-1-setup.log"

* No output will appear. Instead, the cursor will move to a new line and wait for your next input.

7. In the terminal, run: efs-1 mounted in site B
8. To end the cat session, on your keyboard, press Ctrl+C.
9. To view the log file contents, run: cat efs-1-setup.log

* You have successfully mounted an Amazon EFS file system to two Amazon EC2 instances in separate Availability Zones.

10. Go to the next step.

#### <mark style="color:blue;">Concept</mark>

You can use Amazon EC2 user data to bootstrap files systems to new instances when they launch.

<figure><img src="../../../.gitbook/assets/image (34) (1).png" alt=""><figcaption></figcaption></figure>

***

## <mark style="color:red;">DIY Activite</mark>

* [x] Mount an Amazon EFS endpoint to a third EC2 instance.
* [x] Test that the files are accessible from the EC2 instance.

<figure><img src="../../../.gitbook/assets/image (35) (1).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (38) (1).png" alt=""><figcaption></figcaption></figure>

***
