---
description: >-
  Create and configure an Amazon EC2 Auto Scaling group that follows scheduled
  scaling activities to add and remove EC2 instances.
---

# Auto-Healing and Scaling Applications

| Título da tarefa                         | Solicitação de negócios                                                                                                                                      |
| ---------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Aplicações de autocura e dimensionamento | Ajude o café de jogos da cidade a implementar servidores de recuperação automática, restringindo os clientes a uma capacidade de provisionamento específica. |

<figure><img src="../../../.gitbook/assets/image (219).png" alt=""><figcaption></figcaption></figure>

<details>

<summary><mark style="color:purple;">Contexto</mark></summary>

<mark style="background-color:blue;">Client</mark><mark style="background-color:yellow;">:</mark> Hi! I own the city's best gaming cafe. Thanks for answering my call for help

<mark style="background-color:orange;">Architect</mark>:I am a gamer too. How can i help?

<mark style="background-color:blue;">Client</mark>: Gaming parties are so hot right now, and we're allowing our users to host their own servers for various games in our cafe.

We have a maximum number of Amazon EC2 instances that we allow users to provision each day, but we do not have controls to enforce this rule.

So, we have a couple of issues. First, if an EC2 instance crashes, we have no automatic way to replace it.

Second, we want users to stay within their server provisioning limit.

<mark style="background-color:orange;">Architect</mark>: This sounds like a perfect opportunity to use Auto Scaling groups.

You can set up launch templates for your users' game web servers. In those templates, you can configure the number of EC2 instances to automatically scale up or down based on demand.

You can also set hard limits on the number of instances that users can provision.

<mark style="background-color:blue;">Client</mark>: Oh, that sounds execellent! But we have another issue.

A large party is booked from 8:00 PM to 1:00 AM every Tuesday. The moment the party starts, we want servers up and ready. The moment the party ends, we want the servers to shut down.

How can we ensure that user game servers start up and shut down at specific times?

<mark style="background-color:orange;">Architect</mark>: Using Auto Scaling groups, you can configure scheduled scaling that launches and terminates instances according to a predefined schedule.

<mark style="background-color:blue;">Client</mark>: I think Auto Scaling groups can work fro us!

Can you configure an Auto Scaling group for our gaming servers?

</details>

***

## <mark style="color:red;">Amazon EC2 Auto Scaling</mark>

Amazon EC2 Auto Scaling helps ensure that you have the correct number of EC2 instances available to handle the load on your application.

You can specify the minimum and maximum number of instances in each Auto Scaling group, which helps ensure that you group doesn't go below or above these limits.

If you specify a desired capacity, either when you create the group or at any time after, Amazon EC2 Auto Scaling helps ensure that your group has the desired amount of instances.

Scheduled scaling helps you set up your own timings for scaling in and out according to predictable load changes

You can configure the Auto Scaling group to, for example, increase capacity on Tuesday at 8:00 PM and decrease capacity on Wednesday at 1:00 AM

You can use dynamic scaling to define how to scale capacity in response to changing demand.

In this solution, an Amazon CloudWatch alarm is configured to monitor CPU utilization greater than 70 percent.

You can create a dynamic scaling policy to track a specific CloudWatch metric (ALARM: cpu avg > 70%) that adds servers if the alarm is invoked.

In this solution, a scheduled scaling event terminates all instances in the Auto Scaling group.

***

## <mark style="color:red;">Descrição da tarefa</mark>

Descreva os recursos de autocura e dimensionamento oferecidos pelos grupos de Auto Scaling.&#x20;

* Crie um grupo de Auto Scaling com limites de recursos rígidos.&#x20;
* Configure um grupo de Auto Scaling para responder a um evento baseado em tempo.

1. Create an an Amazon EC2 Auto Scaling group
2. Assign EC2 instances to the Auto Scaling group.

***

### <mark style="color:purple;">Step 1</mark>

1. In the top navigation bar search box, type: EC2
2. In the search results, under Services, click EC2.
3. Go to the next step.

#### <mark style="color:blue;">Concept</mark>

AWS Auto Scaling monitors your applications and automatically adjusts capacity to maintain steady, predictable performance at the lowest possible cost.

<figure><img src="../../../.gitbook/assets/image (220).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 2</mark>

1. In the left navigation pane, click Instances.
2. In the Instances section, under Instance ID, click the Game Server instance ID.
3. Go to the next step.

#### <mark style="color:blue;">Concept</mark>

AWS Auto Scaling can help you optimize your utilization and cost efficiencies when consuming AWS services, so you only pay for the resources you actually need. When demand drops, AWS Auto Scaling will automatically remove any excess resource capacity so that you avoid overspending.

<figure><img src="../../../.gitbook/assets/image (221).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 3</mark>

1. For the Game Server instance, under Public IPv4 address, click the icon to copy the provided address.
2. Go to the next step.

#### <mark style="color:blue;">Concept</mark>

AWS Auto Scaling continually monitors your applications to make sure that they are operating at your desired performance levels. Using AWS Auto Scaling, you maintain optimal application performance and availability, even when workloads are periodic, unpredictable, or continuously changing.

<figure><img src="../../../.gitbook/assets/image (222).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 4</mark>

1. In a new browser tab (or window) address bar, type: http://
2. After http://, paste the web server public IP address that you just copied and press Enter.
3. Go to the next step.

<figure><img src="../../../.gitbook/assets/image (223).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 5</mark>

1. Return to the Amazon EC2 console (in the previous browser), and then, in the left navigation pane, click Instances.
2. In the Instance section, choose the check box to select Game Server.
3. Click Actions to expand the dropdown menu.
4. Choose Image and templates.
5. Choose Create image.
6. Go to the next step.

#### <mark style="color:blue;">Concept</mark>

You can capture the contents of an instance and its volume into an Amazon Machine Image (AMI). An AMI is a template used for launching new intrances with identical configurations.

<figure><img src="../../../.gitbook/assets/image (224).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 6</mark>

1. For Image name, type: GameServer
2. For Image description, type: Regular customer game server
3. Go to the next step.

#### <mark style="color:blue;">Concept</mark>

By default, Amazon Elasticc Compute Cloud (Amazon EC2) shuts down the instance, takes snapshots of any attached volumes, crates and registers the AMI, and then reboots the instance. You can enable the "No reboot" option if you don't want your instance to be restarted.

<figure><img src="../../../.gitbook/assets/image (225).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 7</mark>

1. Scroll down to Tags.
2. For Tags, choose Tag image and snapshots together.
3. Click Create image.
4. Go to the next step.

#### <mark style="color:blue;">Concept</mark>

By default, an AMI that you create is available only within the AWS Region of creation. To use the same AMI in another Region, you must copy the AMI to that other Region.

<figure><img src="../../../.gitbook/assets/image (226).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 8</mark>

1. In the left navigation pane, under Images, click AMIs.
2. Review to see that the GameServer AMI was created.

* It might take up to 5 minutes for the AMI to be created.

3. At the top of the page, if needed, click the refresh icon periodically.
4. Under Status, review to ensure that the AMI is available.
5. In the left navigation pane, click Launch Templates.
6. Go to the next step.

<figure><img src="../../../.gitbook/assets/image (227).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 9</mark>

1. On the Launch Templates home page, click Create launch template.
2. Go to the next step.

#### <mark style="color:blue;">Concept</mark>

You can use launch templates to store launch parameters so that you do not have to specify them every time you launch an instance. For example, a launch template can contain the AMI ID, instance type, and network settings that you typically use to launch instances.

<figure><img src="../../../.gitbook/assets/image (228).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 10</mark>

1. In the Launch template name and description section, for Launch template name, type: GameServerTemplate
2. For Template version description, type: Regular customer game server template
3. For Auto Scaling guidance, choose the check box to select Provide guidance to help me....
4. Go to the next step

#### <mark style="color:blue;">Concept</mark>

You can create up to 5,000 launch templates per Region and 10,000 version per launch template.

<figure><img src="../../../.gitbook/assets/image (27) (1).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 11</mark>

1. Scroll down to Application and OS Images.
2. Click the My AMIs tab.
3. Choose Owned by me.
4. For Amazon Machine Image (AMI), on the dropdown menu, choose GameServer.
5. Go to the next step.

<figure><img src="../../../.gitbook/assets/image (28) (1).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 12</mark>

1. Scroll down to Instance type.
2. For Instance type, choose t2.nano.
3. Click Create new key pair.
4. Go to the next step.

#### <mark style="color:blue;">Concept</mark>

For each launch template, you can create one or more numbered launch template versions. The first version specifies the instance type, AMI ID, subnet, and key pair to use to launch the instance.

<figure><img src="../../../.gitbook/assets/image (29) (1).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 13</mark>

1. In the pop-up box, for Key pair name, type: GameServerKeyPair
2. For Key pair type, choose RSA.
3. For Private key file format, choose .pem.
4. Click Create key pair.
5. After you are prompted to download (not shown), save the GameServeKeyPair file.
6. Go to the next step.

#### <mark style="color:blue;">Concept</mark>

For the private key file format, if you plan to access your EC2 instance through Windows or the Putty program, you will choose the .ppk file format. If you use a unix-based (Linux, MacOS) shell with OpenSSH. You will choose the .pem file format.

<figure><img src="../../../.gitbook/assets/image (30) (1).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 14</mark>

1. Click Network settings to expand the section.
2. For Firewall (security groups), choose Select existing security group.
3. For Security groups, choose WebServerSecurityGroup.
4. Go to the next step.

<figure><img src="../../../.gitbook/assets/image (31) (1).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 15</mark>

1. Scroll down to the bottom of page.
2. In the Summary section, review the details.
3. Click Create launch template.
4. Go to the next step.

#### <mark style="color:blue;">Concept</mark>

For resource tags, specify tags by providing key and value combinations. You can tag the instance, the volumes, Sport Instance requests, or all three. For network interfaces, you can specify ip to two network interfaces for the instance.

<figure><img src="../../../.gitbook/assets/image (32) (1).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 16</mark>

1. Scroll down to the bottom of the page.
2. Click View launch templates.
3. Go to the next step.

#### <mark style="color:blue;">Concept</mark>

This launch template can be used to configure the auto scaling and healing properties of your system. When a server goes down, this information is used to create a new instance.

<figure><img src="../../../.gitbook/assets/image (33) (1).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 17</mark>

1. In the left navigation pane, click Auto Scaling Groups.
2. On the Auto Scaling Groups home page, click Create Auto Scaling group.
3. Go to the next step.

#### <mark style="color:blue;">Concept</mark>

Using AWS Auto Scaling, you can build scaling plans that automate how groups of different resources respond to changes in demand. You can optimize for balance between availability and costs. AWS Auto Scaling automatically creates all of the scaling policies, and it sets targets for you based on your preference.

<figure><img src="../../../.gitbook/assets/image (34) (1).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 18</mark>

1. In the Choose launch template or configuration step, for Auto Scaling group name, type: RegularCustomerGameServer
2. For Launch template, choose GameServerTemplate.
3. Go to the next step.

#### <mark style="color:blue;">Concept</mark>

Note the properties that were proviously specified in the launch template default for the Auto Scaling group. Information, such as instance type, has already been selected for you.

<figure><img src="../../../.gitbook/assets/image (35) (1).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 19</mark>

1. Scroll down to the bottom of the page.
2. Click Next.
3. Go to the next step.

#### <mark style="color:blue;">Concept</mark>

If you host an application on multiple EC2 instances, you can launch instances across multiple instance types and purchase options (Sport and On-Demand Instances) by choosing Combine purchase options and instance types. This is an advanced feature in which your team can optimize costs using different deployment strategies.

<figure><img src="../../../.gitbook/assets/image (36) (1).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 20</mark>

1. In the Choose instance launch options step, for VPC, choose the VPC name that ends with auto-healing-and-scaling/GameServerVPC.
2. For Availability Zones and subnets, choose both subnet names that contain game-server-netSubnet.
3. Go to the next step.

<figure><img src="../../../.gitbook/assets/image (37) (1).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 21</mark>

1. Scroll down to the bottom of the page.
2. Click Next.
3. Go to the next step.

<figure><img src="../../../.gitbook/assets/image (38) (1).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 22</mark>

1. In the Configure advanced options step, for Load balancing, choose No load balancer.

* Keep all other default values for VPC Lattice integration options.

2. Scroll down to Health checks.
3. Go to the next step.

#### <mark style="color:blue;">Concept</mark>

Amazon EC2 Auto Scaling can determine the health status of an instance by using one or more of the following.

* Status checks provided by Amazon EC2 to identify hardware and software issues that might impair an instance
* Health checks provided by a load balancer, which can include custom health checks

<figure><img src="../../../.gitbook/assets/image (39) (1).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 23</mark>

1. For health check grace period, type: 240
2. Click Next.
3. Go to the next step.

<figure><img src="../../../.gitbook/assets/image (40) (1).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 24</mark>

1. In the Configure group size and scaling policies step, for Desired capacity, type: 2
2. For Min desired capacity, type: 2
3. For Max desired capacity, type: 4
4. For Automatic scaling, choose Target tracking scaling policy.
5. Go to the next step.

#### <mark style="color:blue;">Concept</mark>

With target tracking scalling policies, you select a scaling metric (for example, CPU utilization) and set a target value. Amazon EC2 Auto Scaling creates and manages the Amazon CloudWatch alarms that invoke the scaling policy. It calculates the scaling adjustment based on the metric and the target value.

<figure><img src="../../../.gitbook/assets/image (41).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 25</mark>

1. Scroll down to Automatic scaling.
2. For Scaling policy name, type: CPU Utilization
3. For Metric type, choose Average CPU utilization.
4. For Target value, type: 70
5. Scroll down to the bottom of the page, and then click Next (not shown).
6. Go to the next step.

<figure><img src="../../../.gitbook/assets/image (42).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 26</mark>

1. In the Add notifications step, click Skip to review.
2. Go to the next step.

#### <mark style="color:blue;">Concept</mark>

You can be notified when Amazon EC2 Auto Scaling is launching or terminating the EC2 instances in your Auto Scaling group. You can manage notifications by using Amazon Simple Notification Service (Amazon SNS).

<figure><img src="../../../.gitbook/assets/image (43).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 27</mark>

1. In the Review step, scroll down to review your configuration settings.
2. Click Create Auto Scaling group.
3. Go to the next step.

<figure><img src="../../../.gitbook/assets/image (44).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 28</mark>

1. In the Auto Scaling groups section, click RegularCustomerGameServer.
2. Go to the next step.

#### <mark style="color:blue;">Concept</mark>

After you create a scaling policy, Amazon EC2 Auto Scaling starts evaluating the policy against the metrics that you selected.

<figure><img src="../../../.gitbook/assets/image (45).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 29</mark>

1. Click the Activity tab.
2. In the Activity history section, review to see that two instances are created to meet the "desired and actual capacity."
3. Go to the next step.

#### <mark style="color:blue;">Concept</mark>

You can see the history of your scaling group. If additional conditions are added to you scaling group, you can view which condition has caused the system to scale.

<figure><img src="../../../.gitbook/assets/image (46).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 30</mark>

1. Click the Automatic scaling tab.
2. Scroll down to Scheduled actions.
3. Go to the next step.

#### <mark style="color:blue;">Concept</mark>

Scheduled scaling helps you to set up your own scaling schedule according to predictable load changes. For example, let's say that the traffic to your web app starts to increase every week based on a predictable factor. You can configure your system to preempt this event.

<figure><img src="../../../.gitbook/assets/image (47).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 31</mark>

1. Click Create scheduled action.
2. Go to the next step.

<figure><img src="../../../.gitbook/assets/image (48).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 32</mark>

1. In the pop-up box, for Name, type: SecondWaveOfRegulars
2. For Desired capacity, type: 3
3. For Min, type: 3
4. For Max, type: 4
5. For Recurrence, choose Every week.
6. For Specific start time, choose a future date, and then type 20:00 in the next text box.
7. Click Create.
8. Go to the next step.

#### <mark style="color:blue;">Concept</mark>

By default, the times that you set are in Coordinated Universal Time (UTC). When specifying a recurring schedule with a cron expression, using the AWS CLI or an SDK, you can change the time zone to correspond to your local time zone or a time zone from another part of your network.

<figure><img src="../../../.gitbook/assets/image (49).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 33</mark>

1. In the Scheduled actions section, review the new scheduled action.
2. Go to the next step.

<figure><img src="../../../.gitbook/assets/image (50).png" alt=""><figcaption></figcaption></figure>

***

## <mark style="color:red;">DIY Activite</mark>

* [x] Configure an auto scaling policy to scale down to 0 resources at 01:00 AM every day.

<figure><img src="../../../.gitbook/assets/image (52).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (51).png" alt=""><figcaption></figcaption></figure>

***
