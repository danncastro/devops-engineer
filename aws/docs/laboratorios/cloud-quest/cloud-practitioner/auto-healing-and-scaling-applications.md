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



#### <mark style="color:blue;">Concept</mark>

***

### <mark style="color:purple;">Step 11</mark>



#### <mark style="color:blue;">Concept</mark>

***

### <mark style="color:purple;">Step 12</mark>



#### <mark style="color:blue;">Concept</mark>

***

### <mark style="color:purple;">Step 13</mark>



#### <mark style="color:blue;">Concept</mark>

***

### <mark style="color:purple;">Step 14</mark>



#### <mark style="color:blue;">Concept</mark>

***

### <mark style="color:purple;">Step 15</mark>



#### <mark style="color:blue;">Concept</mark>

***

### <mark style="color:purple;">Step 16</mark>



#### <mark style="color:blue;">Concept</mark>

***

### <mark style="color:purple;">Step 17</mark>



#### <mark style="color:blue;">Concept</mark>

***

### <mark style="color:purple;">Step 18</mark>



#### <mark style="color:blue;">Concept</mark>

***

### <mark style="color:purple;">Step 19</mark>



#### <mark style="color:blue;">Concept</mark>

***

### <mark style="color:purple;">Step 20</mark>



#### <mark style="color:blue;">Concept</mark>

***

### <mark style="color:purple;">Step 21</mark>



#### <mark style="color:blue;">Concept</mark>

***

### <mark style="color:purple;">Step 22</mark>



#### <mark style="color:blue;">Concept</mark>

***

### <mark style="color:purple;">Step 23</mark>



#### <mark style="color:blue;">Concept</mark>

***

### <mark style="color:purple;">Step 24</mark>



#### <mark style="color:blue;">Concept</mark>

***

### <mark style="color:purple;">Step 25</mark>



#### <mark style="color:blue;">Concept</mark>

***

### <mark style="color:purple;">Step 26</mark>



#### <mark style="color:blue;">Concept</mark>

***

### <mark style="color:purple;">Step 27</mark>



#### <mark style="color:blue;">Concept</mark>

***

### <mark style="color:purple;">Step 28</mark>



#### <mark style="color:blue;">Concept</mark>

***

### <mark style="color:purple;">Step 29</mark>



#### <mark style="color:blue;">Concept</mark>

***

### <mark style="color:purple;">Step 30</mark>



#### <mark style="color:blue;">Concept</mark>

***

### <mark style="color:purple;">Step 31</mark>



#### <mark style="color:blue;">Concept</mark>



### <mark style="color:purple;">Step 32</mark>



#### <mark style="color:blue;">Concept</mark>



### <mark style="color:purple;">Step 33</mark>



#### <mark style="color:blue;">Concept</mark>



***

## <mark style="color:red;">DIY Activite</mark>

* [ ] Configure an auto scaling policy to scale down to 0 resources at 01:00 AM every day.

***
