# Databases in Practice

| Título da tarefa          | Solicitação de negócios                                                                            |
| ------------------------- | -------------------------------------------------------------------------------------------------- |
| Bases de dados na prática | Melhore as operações, o desempenho e a disponibilidade do banco de dados relacional da seguradora. |

<figure><img src="../../../.gitbook/assets/image (120).png" alt=""><figcaption></figcaption></figure>

<details>

<summary><mark style="color:purple;">Contexto</mark></summary>



</details>

***

## <mark style="color:red;">Amazon RDS</mark>



***

## <mark style="color:red;">Descrição da tarefa</mark>

Revise os recursos, benefícios e tipos de banco de dados disponíveis com o Amazon RDS.&#x20;

* Descreva o dimensionamento vertical e horizontal no Amazon RDS.&#x20;
* Use réplicas de leitura do Amazon RDS para aumentar o desempenho do banco de dados.&#x20;
* Implemente implantações multi-AZ do Amazon RDS para aumentar a disponibilidade.

1. **Launch an Amazon RDS instance.**
2. **Configure a Multi-AZ deploymnet**
3. **Configure Amazon RDS backups.**

***

### <mark style="color:purple;">**Step 1**</mark>

1. In the top navigation bar search box, type: RDS
2. In the search results, under Services, click RDS.
3. Go to the next step

<figure><img src="../../../.gitbook/assets/image (1) (2).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">**Step 2**</mark>

1. In the left navigation pane, click Databases.
2. In the Databases section, click Create database.
3. Go to the next step

#### <mark style="color:blue;">**Concept**</mark>

Amazon Relational Database Service (Amazon RDS) is a managed service. This  means that your database administrator can focus on innovating instead of patching and updating their database and infrastructure.

Amazon RDS is optmized for memory, performance, and input/output. With Amazon RDS, you only pay for the resources that you actually consume.

<figure><img src="../../../.gitbook/assets/image (2) (2).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">**Step 3**</mark>

1. To fine-tune your configuration, for Choose a database creation method, choose Standard create.
2. For Engine type, choose MariaDB.
3. Go to the next step.

#### <mark style="color:blue;">**Concept**</mark>

AWS offers several familiar database (DB) engines. Amazon Aurora, a lightning fast database solution at AWS, is up to five times faster than MySQL and three times faster than PostgreSQL. Aurora databases are highly secure, available, and durable.

&#x20;

<figure><img src="../../../.gitbook/assets/image (3) (2).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">**Step 4**</mark>

1. For Engine Version, keep the default MariaDB version provided.

* The default version might be different from what is displayed in the screenshot example.

2. For Templates, choose Dev/Test.
3. Go to the next step

<mark style="color:blue;">**Concept**</mark>

Amazon RDS provides three templates for you deployment: Production, Dev/Test, and Free Tier. Use Free Tier if you wish to learn or deploy a quick proof of concept. Use Production only when deploying a production-level system

<figure><img src="../../../.gitbook/assets/image (4) (2).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">**Step 5**</mark>

1. For DB instance identifier, type: my-database

* This is the name of your DB instance.

2. For Master username, keep the default username of admin.
3. For Credentials management, choose Self managed
4. For Master password, type: ILoveLearning!123
5. For Confirm password, type the password again.
6. Go to the next step

#### <mark style="color:blue;">**Concept**</mark>

You DB instance identifier is the name that you see when you search for your instance in the console. You can connect this database with the credentials that you provide here.

<figure><img src="../../../.gitbook/assets/image (5) (2).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">**Step 6**</mark>

1. Scroll down to instance configuration
2. For DB Instance class, choose Burstable classes.
3. On the dropdown menu below that, choose db.t3.xlarge

* Only t3 db classes are supoported in this lab.

4. For Storage type, on the dropdown menu, choose General Purpose SSD (gp2).
5. For Allocated storage, type: 20
6. Go to the next step

<mark style="color:blue;">**Concept**</mark>

Amazaon RDS supports the most demanding database applications. You can choose between two SSD-backed storage options. One is optimized for high performance OLTP applications, and the other is optimize for cost-effective, general-purpose use.

<figure><img src="../../../.gitbook/assets/image (6) (2).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">**Step 7**</mark>

1. For Storage autoscaling, chick the expand arrow.
2. Review the default option of Enable storage autoscaling.
3. For Maximum storage threshold, review the default threshold of 1000GB.
4. Under Availability & durability, for multi-AZ deployment, choose Create a standby instance.
5. Go to the next step

#### <mark style="color:blue;">**Concept**</mark>

Using the MySQL, MariaDB, Oracle, and PostgreSQL engines, you can scale up to 64 TB of storage. SQL Server supports up too 16 TB. Storage scaling is on the fly, with zero downtime.

<figure><img src="../../../.gitbook/assets/image (7) (2).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">**Step 8**</mark>

1. In the Connectivity section, for Virtual private cloud (VPC), keep the default value of Default VPC.
2. For DB subnet group, keep the default setting.
3. For Public access, keep the default setting.
4. For VPC security group (firewall), keep the default setting.
5. Go to the next step

#### <mark style="color:blue;">**Concept**</mark>

Amazon RDS helps you control network access to you database. You can also run your RDS DB instances in a virtual private cloud (VPC). This way, you can isolate your DB instances and connect to you existing IT infraestructure through an industry standard encrypted IPsec VPN.

<figure><img src="../../../.gitbook/assets/image (8) (2).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">**Step 9**</mark>

1. In the Monitoring section, for Performance insights, clear the check box to deselect Turn on Performance Insights.
2. For Additional configuration, click the expand arrow.
3. For Enhanced Monitoring, clear the check box to deselect Enable Enhanced monitoring.

* If either Performance Insights or Enhanced monitoring are enabled, you'll get a permissions error when trying to create the database.

4. Scroll down to the Additional configuration section.
5. Go to the next step.

<figure><img src="../../../.gitbook/assets/image (9) (2).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">**Step 10**</mark>

1. In the Additional configuration section, for Additional configuration, click de expand arrow.
2. For Initial database name, type: my\_database
3. For DB parameter group and Option group, review the default options.
4. Under Backup, review the default options.
5. Go to the next step

#### <mark style="color:blue;">**Concept**</mark>

In order for AWS to sucessfully provision an RDS DB instance for you, you must first specify an initial database name. if you failt to spacify an initial database, your instance can still be provisioned, but it might not work properly.

<figure><img src="../../../.gitbook/assets/image (10) (2).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">**Step 11**</mark>

1. In the Additional configuration section, for Encryption, review the default option of Enable encryption.
2. Go to the next step

<figure><img src="../../../.gitbook/assets/image (12) (2).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">**Step 12**</mark>

1. For Maintenance, clear the check box to deselect Enable auto minor version upgrade.
2. For Maintenance window, review the default selection of No preference
3. Scroll down and click Create database (not shown).
4. Go to the next step.

<figure><img src="../../../.gitbook/assets/image (13) (2).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">**Step 13**</mark>

* Expect about 15-20 minutes to create your RDS instance. It's a great time to get a cup of coffe or a snack!
* You may see a pop-up window. Please close it.

1. When you return, in the Databases section, click the refresh icon.
2. Under Status, review to ensure that the DB status is Available.
3. Click my-database.
4. Go to the next step

<figure><img src="../../../.gitbook/assets/image (14) (2).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">**Step 14**</mark>

1. Click Actions to expand the dropdown menu.
2. Review the different options.

* The options, such as Create read replica, can be used to manage your existing DB instance.

3. Go to the next step.

<figure><img src="../../../.gitbook/assets/image (15) (2).png" alt=""><figcaption></figcaption></figure>

***

## <mark style="color:red;">DIY Activities</mark>

* [x] Create a read replica of your primary database using a db.t3.xlarge instance

<figure><img src="../../../.gitbook/assets/image (16) (2).png" alt=""><figcaption></figcaption></figure>

***
