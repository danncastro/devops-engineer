# Cloud Economics

| Título da tarefa  | Solicitação de negócios                                                                                                   |
| ----------------- | ------------------------------------------------------------------------------------------------------------------------- |
| Economia da Nuvem | A loja de pranchas de surfe da cidade precisa de uma estimativa de custo de uma arquitetura com uso variável de recursos. |

<figure><img src="../../../.gitbook/assets/image (18).png" alt=""><figcaption></figcaption></figure>

<details>

<summary><mark style="color:purple;">Contexto</mark></summary>

<mark style="background-color:blue;">Client:</mark> Hey there. Thanks for coming! I want to set up my surf shop in the cloud, and i need some help.

<mark style="background-color:orange;">Architect:</mark> No problem. How can i help?

<mark style="background-color:blue;">Client:</mark> My main issue is cost. So far, i get much more web store traffic during the day than i do at night. I think i can cut the number of servers i use at night in half, from four to two.

<mark style="background-color:orange;">Architect:</mark> Yes, that's one of the many advantages of cloud computing. You pay for what you use. Don't need something? Just shut it down and you won't pay for it.

<mark style="background-color:blue;">Client:</mark> Interesting. Before i start to think about migrating, i want to create a cost estimate, but i'm not sure how to begin. Should i mimic my local setup environment? How do i match my current hardware with what is available on AWS?

<mark style="background-color:orange;">Architect:</mark> Yes, you can mimic your current architecture, and the online AWS documentation explains how. Before you start, though, consider that most customers overbuild their on-premises systems, anticipating future growth.

<mark style="background-color:blue;">Client:</mark> So, I can potentially use systems with fewer resources? How does that work? What if my system requires more resources than i thought?

<mark style="background-color:orange;">Architect:</mark> Because cloud resources in the cloud are quickly scaled up or down, you don't need to overbuy for growth. Identity your current needs, and build from that.

<mark style="background-color:blue;">Client:</mark> Okay, that sounds promising. Can you show me how to create an estimate for my architecture so that i can save on costs?

<mark style="background-color:orange;">Architect:</mark> Of course! I'll prepare a price estimate by using the AWS Pricing Calculator, and i'll send you a URL when it's ready.

Keep in mind that different architectures can be used to achieve the same solution, so you have options and a potential to save even more in the future. But architectural improvements can be a conversation for another time.

<mark style="background-color:blue;">Client:</mark> Understood. Let's get this first estimate done so that i can make some decisions.

<mark style="background-color:orange;">Architect:</mark> If you need more resources, you can scale your systems horizontally, which means that you can add more servers when you need them. If your current resources are too weak to run your application, you can scale vertically, which means that you can increase the computing power on one more instances.

<mark style="background-color:blue;">Client:</mark> I'm looking forward to seeing what you find out.

<mark style="background-color:orange;">Architect:</mark> Yes

<mark style="background-color:blue;">Client:</mark> Great! Let's get to it.

</details>

***

## <mark style="color:red;">Recursos</mark>

**AWS Pricing:** This solution uses the AWS Pricing Calculator to create estimates for your AWS use cases. You can model your solutions before building them, explore the AWS service price points, and review the calculations behind your estimates.

Using AWS, you can take control of costs and continuously optimize your spending so that you pay only for the resources you actually need.

Using a static number of resources as your demand fluctuates can overburden your servers when demand is high, which can result in underserved customers.

Cost inefficiencies occur when demand is low by spending money on unused computer capacity.

With AWS your resources are elastic. Meaning you can provision the services that you need on demand, and you pay for only what you use. This way, your infrastructure matches your demand.

Matching infrastructure to demand uses a concept called scaling.

As demand increases, your services can scale out horizontally, which means that you increase capacity by adding more resources (such as EC2 instances) to the system.

As demand decreases, your systems can scale horizontally in the other direction, which menas to number of instances or other resources reserved for use will also decrease.

Using the AWS Pricing Calculator, you can generate an estimate with no commitment and explore AWS services and pricing for your architecture need. You can use the service to help plan how you spend, find cost saving opportunities, and make informed decisions.

***

## <mark style="color:red;">Descrição da tarefa</mark>

Descreva como as estimativas de preços são obtidas.&#x20;

* Use a Calculadora de Preços da AWS para estimar o preço de uma arquitetura da AWS.

1. Create logical pricing groups
2. Create weekly, monthly, and yearly estimates for Amazon EC2 instances.

***

### <mark style="color:purple;">Step 1</mark>

1. Open a new browser tab, and then, in the address bar, type: https://calculator.aws and press Enter.
2. On the AWS Pricing Calculator home page, click Create estimate.
3. Go to the next step.

#### <mark style="color:blue;">Concept</mark>

AWS Pricing Calculator is a quick, effective way to estimate your cloud cost.

<figure><img src="../../../.gitbook/assets/image (19).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 2</mark>

1. On the top breadcrumb menu, click My Estimate.
2. Go to the next step.

#### <mark style="color:blue;">Concept</mark>

Before creating an estimate, consider creating a logical grouping of your services. Grouping your web servers, for example, can be a useful logical grouping.

<figure><img src="../../../.gitbook/assets/image (20).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 3</mark>

1. In the My Estimate section, click Create group.
2. Go to the next step.

#### <mark style="color:blue;">Concept</mark>

Adding multiple groups to an estimate can provide more insight into your data.

<figure><img src="../../../.gitbook/assets/image (21).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 4</mark>

1. In the pop-up box, for Group name, type: Web Servers
2. Click Create group.
3. Go to the next step.

<figure><img src="../../../.gitbook/assets/image (22).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 5</mark>

1. Click Add service.
2. Go to the next step.

<figure><img src="../../../.gitbook/assets/image (23).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 6</mark>

1. In the AWS services section, for Find Service, type: EC2
2. On the Amazon EC2 card, click Configure.
3. Go to the next step.

#### <mark style="color:blue;">Concept</mark>

On each card, you can configure detauls about your service. You can also use the direct links to product pages.

<figure><img src="../../../.gitbook/assets/image (24).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 7</mark>

1. In the pop-up box, for Description, type:

Web Server Estimate

2. For Choose a location type, on the dropdown menu, choose Region.
3. For Choose a Region, choose US East (N. Virginia).
4. Go to the next step.

#### <mark style="color:blue;">Concept</mark>

Different AWS Regions might have different prices. If you have spiky traffic throughout the day, you should use Advanced estimate. Quick estimate assumes consistent utilizantion.

<figure><img src="../../../.gitbook/assets/image (25).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 8</mark>

1. Scroll down to EC2 specifications.
2. For Operating system, choose Linux .
3. For Workloads, choose Daily spike traffic.
4. For Workload days, choose the seven check boxes to select all days (Sunday through Saturday).
5. Scroll down to Baseline.
6. Go to the next step.

#### <mark style="color:blue;">Concept</mark>

The cyclical nature of service usage is common. For example, usage might be heavier during business hours. Make sure that you can model those peak periods.

<figure><img src="../../../.gitbook/assets/image (26).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 9</mark>

1. For Baseline, type: 2
2. For Peak, type: 4
3. For Duration of peak, in the two text boxes, type: 8 (for hours) and 0 (for minutes)
4. Go to the next step.

#### <mark style="color:blue;">Concept</mark>

The baseline usage refers to the minimum amount of servers during nonpeak time. Conversely, peak usage represents the amount of servers required at peak periods.

<figure><img src="../../../.gitbook/assets/image (27).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 10</mark>

1. Scroll down to EC2 Instances.
2. For Any Instance family, for vCPUs, choose 2.
3. For Memory (GiB), choose 4 GiB.
4. For Network performance, choose Any Network Performance.
5. In the instances list, choose the radio button to select t2.medium.
6. Go to the next step.

#### <mark style="color:blue;">Concept</mark>

When creating estimates, users often do one-to-one mappings of their on-premises hardware to the cloud. For example, don't assume that 4 GB is necessary because that is used on premises. One-to-one mapping of hardware specifications often prevents users from effectively making use of all cloud benefits. It's important to rightsize your instances.

<figure><img src="../../../.gitbook/assets/image (28).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 11</mark>

1. Scroll down to Payment options.
2. Choose On-Demand.
3. Scroll down to Show calculations.
4. Go to the next step.

#### <mark style="color:blue;">Concept</mark>

For new cloud customers, we often recommend using On-Demand Instances. After customers have established enough usage data, and are certain of their commitment, they can save future cost by using other plans.

<figure><img src="../../../.gitbook/assets/image (29).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 12</mark>

1. Click to expand Show calculations.
2. Click estimated workload hours.
3. Go to the next step.

<figure><img src="../../../.gitbook/assets/image (30).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 13</mark>

1. In the pop-up box, scroll down to Workload hours per month.
2. Review how your workload hours are broken down per day.
3. Review to see that instances 3 and 4 are being charged for only 8 hours per day while instances 1 and 2 are being charged for 24 hours per day.
4. Under Utilization summary, review the Total On-Demand instance hours per month.
5. Click Close.
6. Go to the next step.

#### <mark style="color:blue;">Concept</mark>

Amazon instance pricing is very granular, offering per-second billing for many instances.

<figure><img src="../../../.gitbook/assets/image (31).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 14</mark>

1. Click to expand the Amazon Elastic Block Store (EBS) section.
2. For Storage for each EC2 Instance, choose General Purpose SSD (gp3).
3. For General Purpose SSD (gp3) - IOPS, type: 30
4. Scroll down to Snapshot Frequency.
5. Go to the next step.

#### <mark style="color:blue;">Concept</mark>

Amazon Elastic Block Storage (Amazon EBS) offers various storage types bases on your workloads. For basic web servers, General Purpose SSDs might suffice. However, for more specialized workloads, involving large data transfer or high input-output operations, other storage types might be appropriate.

<figure><img src="../../../.gitbook/assets/image (32).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 15</mark>

1. For Snapshot Frequency, choose Weekly.
2. For Amount changed per shapshot, type: 1
3. On the right dropdown menu, choose GB.
4. Scroll down to Data transfer.
5. Go to the next step.



***

### <mark style="color:purple;">Step 16</mark>

<figure><img src="../../../.gitbook/assets/image (33).png" alt=""><figcaption></figcaption></figure>

#### <mark style="color:blue;">Concept</mark>

Part of AWS pricing includes includes data transfer rates. All data coming into AWS from the internet is free, but charges for intra-Region and outbound data might apply. If you're unsure about how much data you use, tools exist that can help you measure this on your current systems.

<figure><img src="../../../.gitbook/assets/image (34).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 17</mark>

1. Under Show calculations, review how your Data Transfer rates are calculated.
2. Review the Total Monthly cost.
3. Click Save and add service.
4. Go to the next step.

<figure><img src="../../../.gitbook/assets/image (35).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 18</mark>

1. Click View summary.
2. Go to the next step.

<figure><img src="../../../.gitbook/assets/image (36).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 19</mark>

1. Click Share.
2. Go to the next step.

<figure><img src="../../../.gitbook/assets/image (37).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 20</mark>

1. In the pop-up box, click Agree and continue.
2. Go to the next step.

<figure><img src="../../../.gitbook/assets/image (38).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 21</mark>

1. Click Copy public link.

* You can paste this link in a text editor for future reference.

2. Go to the next step.

#### <mark style="color:blue;">Concept</mark>

Your cost estimate link persists. If you want to share your estimates with other people, send them your link.

<figure><img src="../../../.gitbook/assets/image (39).png" alt=""><figcaption></figcaption></figure>

***

## <mark style="color:red;">DIY Activite</mark>

* [x] Change the EC2 instance type to t2.micro, and then generate a new price estimate URL.

<figure><img src="../../../.gitbook/assets/image (250).png" alt=""><figcaption></figcaption></figure>

***
