# Computing Solutions

| Título da tarefa       | Solicitação de negócios                                                                                                                            |
| ---------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------- |
| Soluções de Computação | O servidor da escola que executa a solução de agendamento precisa de mais memória. Auxilie no dimensionamento vertical da instância do Amazon EC2. |

<figure><img src="../../../.gitbook/assets/image (21) (1).png" alt=""><figcaption></figcaption></figure>

<details>

<summary><mark style="color:purple;">Contexto</mark></summary>



</details>

***

### <mark style="color:red;">Familly Amazon EC2</mark>



***

### <mark style="color:red;">Descrição da tarefa</mark>

Descreva famílias de instâncias e tipos de instâncias do Amazon EC2.&#x20;

* Descreva o dimensionamento horizontal e vertical.
* Reconhecer opções para conectar-se a instâncias do Amazon EC2.

1. **Explore Amazon EC2 instance types.**
2. **Filter EC2 instances based on their attributes.**
3. **Connect to an EC2 instance using Amazon EC2 Session Manager**
4. **View EC2 instance metadata using the instance public IP address.**
5. **Start and stop an EC2 instance by using the Amazon EC2 console.**

***

### <mark style="color:purple;">**Step 1**</mark>

1. On the top navigation bar, review the Region selector to ensure that the Region is set to N. Virginio (us-east-1).
2. In the Services search box, type: EC2
3. In the search results, under Services, click EC2.
4. Go to next step

<figure><img src="../../../.gitbook/assets/image (22) (1).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">**Step 2**</mark>

1. In the left navigation pane, click instances.
2. Go to the next step

#### <mark style="color:blue;">**Concepts**</mark>

Amazon Elastic Compute Cloud (Amazon EC2) instances provide virtual compute capacity in the cloud. With a choice of processor, storage, networking, operating system, and purchase model the service offers a broad and deep solution.

<figure><img src="../../../.gitbook/assets/image (23) (1).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">**Step 3**</mark>

1. In the instances section, choose the check box to select the AWS Computing Solutions instance.
2. Click the Details tab.
3. Review the details.
4. Go to the next step

#### <mark style="color:blue;">**Concepts**</mark>

Information about the instance (such as its public IP, private IP, and public DNS) is displyaed in the instance summary section by selecting the EC2 instance.

<figure><img src="../../../.gitbook/assets/image (24) (1).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">**Step 4**</mark>

1. in the left navigation pane, click Instance Types.
2. Go to the next step

#### <mark style="color:blue;">**Concept**</mark>

Amazon EC2 provides a wide selection of instance types that belong to instance families that are optimized to fit different use cases.

<figure><img src="../../../.gitbook/assets/image (25) (1).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">**Step 5**</mark>

1. In the Instances types section, in the filter box, type the fllowing and press Enter after each:

* t3.large
* c5.large
* r5.large

2. Choose the three check boxes to select each added instance types.
3. Go to the next step

#### <mark style="color:blue;">Concept</mark>

Each instance type includes one or more instance sizes, so you can scale your resources to the requirements of your target workload.

<figure><img src="../../../.gitbook/assets/image (26) (1).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">**Step 6**</mark>

1. For each instance types, review the instance details.
2. To compare compute, networking, storage, accelerators, and pricing information, scroll down.
3. In the left navigation pane, click instances.
4. Go to the next step

#### <mark style="color:blue;">**Concept**</mark>

Using the Amazon EC2 console, you can filter instance attributes such as instance types, instance family, and instance size. You can search using keyworkds, atribute names, or expressions.

<figure><img src="../../../.gitbook/assets/image (27) (1).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">**Step 7**</mark>

1. Choose the check box to select the AWS Computing Solutions instances.
2. On the details tab, under Public IPv4 address, click the copy icon to copy the provided address.

* Do not use the "open address" link

3. Go to the next step

#### <mark style="color:blue;">**Concept**</mark>

Instance metadata is data about your instance that you can use to configure or manage the running instance. Instance metadata is divided into categories; for exemple, host name, events, and securiy groups.

<figure><img src="../../../.gitbook/assets/image (28) (1).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">**Step 8**</mark>

1. Open a new browser tab, and then paste the IP Address that you just copied and press Enter (not shown).
2. Review the instance details, and then return to the previous browser.

* You should land on the instance page in the Amazon EC2 Console.

3. Go to the next step.

#### <mark style="color:blue;">**Concept**</mark>

When creeating a new insntace, you can enable the instance metadata service (IMDS) through the Advanced details sections. This way, you can display attibute details by using the instance's public IP.

![](<../../../.gitbook/assets/image (29) (1).png>)

***

### <mark style="color:purple;">**Step 9**</mark>

1. In the instances section, click Connect.
2. Go to the next step

#### <mark style="color:blue;">**Concept**</mark>

You have the flexibility to connect to an EC2 instance by using Amazon EC2 Instance Connect, Session Manager (a capability of AWS Systems Manager), or an SSH client.

<figure><img src="../../../.gitbook/assets/image (30) (1) (1).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">**Step 10**</mark>

1. Click EC2 Instance Connect tab.
2. Review the connection settings.
3. Click the Session Manager tab.
4. Go to the next step

#### <mark style="color:blue;">**Concept**</mark>

EC2 Instance Connect provides an efficient and secure way to connect to your Linux instances. EC2 Instance Connect uses AWS Identity and Access Management (IAM) policies and principals to control SSH access to you instances, removing the need to share and manage SSH keys.

<figure><img src="../../../.gitbook/assets/image (31) (1).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">**Step 11**</mark>

1. Review the Session Manager usage details.
2. Click the SSH client tab.
3. Go to the next step

#### <mark style="color:blue;">**Concept**</mark>

Using Session Manager, you can manage your EC2 instances through an interactive one-click, browser-based shell or through the AWS Command Line Interface (AWS CLI). After the session begins, you can run bash commands as you would through any other connection type.

<figure><img src="../../../.gitbook/assets/image (32) (1).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">**Step 12**</mark>

1. Review the requirements for connecting through SSH.
2. Click to go back to the Session Manager tab.
3. Go to the next step.

#### <mark style="color:blue;">**Concept**</mark>

You can connect to your instance by using an SSH client on your local device through your instance key pair. Your device might have an SSH client by default or you might need to install an SSH client.

<figure><img src="../../../.gitbook/assets/image (33) (1).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">**Step 13**</mark>

1. Click connect, and then wait for the terminal window to open.
2. Go to the next step.

#### <mark style="color:blue;">**Concept**</mark>

Session Manager provides secure and auditable node management without the need to open inbound ports, maintain bastion hosts, or manage SSH keys. Session Manager also allows you to comply with corporate policies that require controlled access to managed nodes, strict security practicesm and fully auditable logs with node access details, while providing end users with simple onde-click cross-platform access to your managed nodes.

<figure><img src="../../../.gitbook/assets/image (34) (1).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">**Step 14**</mark>

1. To provide root privileges to the current session, in the terminal window, at the command prompt, run the following command (type the command and press Enter):  `sudo -i`
2. To change to the application directory, run: `cd ../home/ec2-user/sample-app`

* Be sure to add a space between `cd` and the `../` command.
* A sample application resides on this instance.

3. To view the files in the sample\_app directory, run: `ls`
4. To check the instance log, run: `tail -lf aws_compute_solutions.log`

#### <mark style="color:blue;">**Concept**</mark>

After you are connected to the instance, you can control the instance by using AWS CLI command. The command prompt behaves as if you are connected locally.

<figure><img src="../../../.gitbook/assets/image (35) (1).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">**Step 15**</mark>

1. Review the log details.

* To quit, press CTRL + C on your keyboard.

2. Close the terminal tab to return to the instances page in the Amazon EC2 console.
3. Go to the next step.

<figure><img src="../../../.gitbook/assets/image (36) (1).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">**Step 16**</mark>

1. Click Actions to expand the dropdown menu.
2. Choose Instance settings.
3. Choose Edit user data.
4. Go to the next step

#### <mark style="color:blue;">**Concept**</mark>

You can use the Actions dropdown menu to control the instance state and modify instance attributes.

<figure><img src="../../../.gitbook/assets/image (37) (1).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">**Step 17**</mark>

1. Under Current user data, review the commands.
2. Click Cancel.
3. Go to the next step

#### <mark style="color:blue;">Concept</mark>

You can also use instance metadata to access user data that you specified when launching your instance.

<figure><img src="../../../.gitbook/assets/image (38) (1).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">**Step 18**</mark>

1. In the left navigation pane, click instances.
2. In the Instances section, click Instance state to expand the dropdown menu.
3. Choose Stop instance.
4. Go to the next step.

#### <mark style="color:blue;">**Concept**</mark>

Using the instance state dropdown menu, you can place an instance into different states of activity. You can start and stop an instance if it has an Amazon Elastic Block Store (Amazon EBS) volume as its root device.

<figure><img src="../../../.gitbook/assets/image (39).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">**Step 19**</mark>

1. In the pop-up box, click Stop.
2. Go to the next step

#### <mark style="color:blue;">**Concept**</mark>

Afteran instance stops, CPU usage and data transfer charges cease, but storage charges for any attached Amazon EBS volumes continue.

<figure><img src="../../../.gitbook/assets/image (40).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">**Step 20**</mark>

1. Review the successfully stopped banner.
2. On the Details tab, after the instance state changes to Stopped, review the Public IPv4 address and DNS.

* They should both be empty. You may need to click the refresh button under the banner to see the empty settings.

3. Go to the next step.

#### <mark style="color:blue;">**Concept**</mark>

Each time you start a stopped instance, AWS charges a minimum of one minutes for the use of per-second billing instances. After one minute, AWS charges only for the seconds that you use.

<figure><img src="../../../.gitbook/assets/image (41).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">**Step 21**</mark>

1. In Actions to expand the dropdown menu.
2. Choose instance settings.
3. Review the available options.

* You have different options to change your instance, such as type, termination protectionm and shutdown behavior.

4. Go to the next step.

#### <mark style="color:blue;">**Concept**</mark>

You must stop your Amazon EBS-backend instance before you can change its instance type. Plan for downtime while your instance is stopped. Stopping the instance and changing its instance type might take a few minutes, and restarting your instance might take a variable amount of time depending on your application's startup scripts.

<figure><img src="../../../.gitbook/assets/image (42).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">**Step 22**</mark>

1. Click Instance state to expand the dropdown menu.
2. Choose Start Instance.
3. Go to the next step

<figure><img src="../../../.gitbook/assets/image (43).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">**Step 23**</mark>

1. After the instance reaches the Running state, review the instance details.

* Node that the public IPv3 address and DNS are now populated.

2. Go to the next step.

<figure><img src="../../../.gitbook/assets/image (44).png" alt=""><figcaption></figcaption></figure>

***

## DIY Activite

* [ ] Escrever

***
