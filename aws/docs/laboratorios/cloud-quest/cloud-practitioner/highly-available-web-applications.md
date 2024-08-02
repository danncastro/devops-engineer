# Highly Available Web Applications

| Título da tarefa                       | Solicitação de negócios                                                                       |
| -------------------------------------- | --------------------------------------------------------------------------------------------- |
| Aplicações Web de Alta Disponibilidade | Ajude a agência de viagens a criar uma arquitetura de aplicativo web de alta disponibilidade. |

<figure><img src="../../../.gitbook/assets/image (26).png" alt=""><figcaption></figcaption></figure>

<details>

<summary><mark style="color:purple;">Contexto</mark></summary>

<mark style="background-color:blue;">Client</mark><mark style="background-color:yellow;">:</mark> Hi! Thank you for answering our request for help. Our travel agency just had a disastrous promotional event.

<mark style="background-color:orange;">Architect:</mark> Oh, I'm sorry to hear that. What happened?

<mark style="background-color:blue;">Client</mark><mark style="background-color:yellow;">:</mark> The promotional event we held last week increased our web traffic and overloaded our website. All requests were being timed out.

Worse than that, our EC2 instances were also hosted in an Availability Zone that was affected by severe storms. We were offiline for hours.

<mark style="background-color:orange;">Architect:</mark> I'm so sorry this happened. Let's talk about how you can prevent it in the future.

First, you can use AWS to create an Auto Scaling group across multiple Availability Zones, ensuring that your resources aren't isolated.

Second, you can create a load balancer so that network traffic is distributed equelly across your servers.

<mark style="background-color:blue;">Client</mark><mark style="background-color:yellow;">:</mark> Okay, so if i spread instances out over multiple Availability Zones, will that make us 100 percent safe from failures?

<mark style="background-color:orange;">Architect:</mark> No system is 100 percent failure proof, but Availability Zones reside in geographically distinct locations, and a singular event is unlikely to affect multiple Availability Zones simultaneously.

<mark style="background-color:blue;">Client:</mark> Got it. But how would we verify that our site is down in a different Availability Zone?

<mark style="background-color:orange;">Architect:</mark> After you spread your EC2 instances over multiple Availability Zones, you can attach an load balancer to your Auto Scaling group to ensure high availability and elasticity.

You can also monitor EC2 instances health by setting up a health check on your load balancer.

<mark style="background-color:blue;">Client:</mark> This sounds promising! Can you build this system for us? Our site needs to handle the increased demand.

Will you help us make our travel booking site highly available?

</details>

***

## <mark style="color:red;">Recursos</mark>

**AWS Infraestructure:** This classic web application solution uses an AWS Cloud compute infrastructure to ensure that an application is highly available.

**Amazon Route 53:** Amazon Route 53 provides DNS sevices to streamline domain management.

**Amazon CloudFront:** Amazon CloudFront is used to deliver static and dynamic content. CloudFront can cache frequentlt accessed content to decrease latency.

**Amazon S3:** Amazon Simple Storage Sevice (Amazon S3) is used to store static assets, such as images and video.

**Amazon ELB:** Elastic Load Balancing is used to distribute traffic across multiple Availability Zones. Amazon EC2 Auto Scaling groups are deployed for redundancy&#x20;

**AWS Auto Scaling:** AWS Auto Scaling creates groups of servers that grow or shrink in capacity, depending on demand.

**Amazon CloudWatch:** AWS Auto Scaling also works directly with Amazon CloudWatch, for metrics data, and with Elastic Load Balancing to add and remove hosts for load distribution.

For example, if a web server reports greater than 80 percent CPU utilization over a period of time, an additional web server could be quickly deployed and automatically added to the load balancer.

***

## <mark style="color:red;">Descrição da tarefa</mark>

Descreva os princípios para arquitetar aplicativos de alta disponibilidade.&#x20;

* Resuma os benefícios de usar um AWS Application Load Balancer (ALB).&#x20;
* Use grupos de Auto Scaling com balanceamento de carga e monitoramento de integridade.

1. Configure an Auto Scaling group to use an Application Load Balances.
2. Configure load balancer health checks for the Auto Scaling group
3. Add a second Availability Zone to the Auto Scaling group

***

### <mark style="color:purple;">Step 1</mark>

1. In the top navigation bar search box, type: EC2
2. In the search results, under Services, click EC2.
3. Go to the next step.

#### <mark style="color:blue;">Concept</mark>

By placing your web server in an Amazon EC2 Auto Scaling group behind a load balancer, you can archieve high availability for your application.

<figure><img src="../../../.gitbook/assets/image (229).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 2</mark>

1. In the left navigation pane, click Auto Scaling Groups.
2. In the Auto Scaling groups section, choose the check box to select TravelAgencyWebServers.
3. On the Details tab, review the current capacity details.
4. Go to the next step.

#### <mark style="color:blue;">Concept</mark>

Minimum and maximum capacity define the boundaries for the number of instances allowed in the Auto Scaling group. The desired capacity is the initial capacity of the Auto Scaling group and the capacity it attempts to maintain. The Auto Scaling group in this practice lab example can currently contain only one instance.

<figure><img src="../../../.gitbook/assets/image (230).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 3</mark>

1. Click the Instance management tab.
2. Review to see that there is currently one instance in the Auto Scaling group.
3. Go to the next step.

#### <mark style="color:blue;">Concept</mark>

An Auto Scaling group starts by launching enough instances to meet its desired capacity. It maintains this number of instances by performing periodic health checks on the instances in the group.

<figure><img src="../../../.gitbook/assets/image (231).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 4</mark>

1. Click the Details tab.
2. Scroll down to Network.
3. Go to the next step.

#### <mark style="color:blue;">Concept</mark>

You must specify at least one Availability Zone when you create your Auto Scaling group. An Auto Scaling group can be configured across multiple Availability Zones for increased availability.

<figure><img src="../../../.gitbook/assets/image (232).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 5</mark>

1. In the Network section, review to see that the Auto Scaling group is configured with a single subnet from one Availability Zone.
2. Scroll down to Load balancing.
3. Go to the next step.

#### <mark style="color:blue;">Concept</mark>

You define which subnets, from one or more Availability Zones, are linked to the Auto Scaling group. This defines where your Amazon EC2 resources, linked to the Auto Scaling group, can reside.

<figure><img src="../../../.gitbook/assets/image (233).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 6</mark>

1. Click Edit.
2. Go to the next step.

<figure><img src="../../../.gitbook/assets/image (234).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 7</mark>

1. Click Add a new load balancer.
2. Go to the next step.

#### <mark style="color:blue;">Concept</mark>

When you attach a load balancer to your Auto Scaling group, the load balancer register with the group and acts as a single point of contact for all incoming web traffic to the group.

<figure><img src="../../../.gitbook/assets/image (235).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 8</mark>

1. For Load balancer type, choose Application Load Balancer.
2. For Load balancer scheme, choose Internet-facing.
3. Go to the next step.

#### <mark style="color:blue;">Concept</mark>

Choose the Application Load Balancer to manage web-based applications that require HTTPS connectivity. The load balancer must be internet-facing if your web applications are for public access.

<figure><img src="../../../.gitbook/assets/image (236).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 9</mark>

1. For Availability Zones and subnets, choose the three check boxes to select all three Availability Zones.
2. On each of the three dropdown menus, choose the available public subnet.
3. For Default routing (forward to), choose Create a target group.

* Keep the defaults.

4. To create the Application Load Balancer, click Update.
5. Go to the next step.

#### <mark style="color:blue;">Concept</mark>

A load balancer takes requests from clients and distributes them across targets in a target group. After you enable an Availability Zone, the load balancer starts routing requests to the registered targets in that Availability Zone.

<figure><img src="../../../.gitbook/assets/image (237).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 10</mark>

1. In the left navigation pane, click Security Groups.
2. In the Security Groups section, click Create security group.
3. Go to the next step.

#### <mark style="color:blue;">Concept</mark>

To customize the traffic flow between the load balancer and the web servers, you can create new security groups that define what traffic is allowed to the load balancer and what traffic is allowed to the web servers behind the load balancer.

<figure><img src="../../../.gitbook/assets/image (238).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 11</mark>

1 . In the Basic details section, for Security group name, type: TravelAgencyLoadBalancer

2. For Description, type a description that you like, such as Allow access to the travel agency load balancer from the internet.
3. For VPC, choose the VPC name that ends with lab/TravelAgencyVpc.

* To remove the existing VPC entry, you might need to click the X.

4. In the Inbound rules section, click Add rule.
5. Go to the next step.

#### <mark style="color:blue;">Concept</mark>

Security groups are assigned to a virtual private cloud (VPC). This means thaat the security group can be assigned only to resources within the VPC.

<figure><img src="../../../.gitbook/assets/image (239).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 12</mark>

1. In the Inbound rules section, for Type, choose HTTP.
2. To allow all inbound traffic, for Source, in the Custom search box, choose 0.0.0.0/0.
3. Go to the next step.

#### <mark style="color:blue;">Concept</mark>

For a public-facing load balancer, you specify 0.0.0.0/0 as a source to accept traffic from any address. By specifying a security group as an outbound destination, you can restrict traffic to be sent only to instances associated with the specified security group.

<figure><img src="../../../.gitbook/assets/image (240).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 13</mark>

1. In the Outbound rules section, for Type, choose HTTP.
2. For Destination, choose the TravelAgencyWebServer security group.
3. Remove the 0.0.0.0/0 destination (not shown).
4. Go to the next step.

<figure><img src="../../../.gitbook/assets/image (241).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 14</mark>

1. Scroll down to the bottom of the page.
2. Click Create security group.
3. Go to the next step.

#### <mark style="color:blue;">Concept</mark>

Security groups are not active unless they are assigned to a resource.

<figure><img src="../../../.gitbook/assets/image (242).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 15</mark>

1. In the left navigation pane, click Security Groups.
2. In the Security Groups section, choose the check box to select the TravelAgencyWebServer security group.
3. On the Actions dropdown menu, choose Edit inbound rules.
4. Go to the next step.

#### <mark style="color:blue;">Concept</mark>

To increase security, you can edit the security group(used by EC2 instances hehind the Application Load Balancer) to allow only inbound traffic from the load balancer.

<figure><img src="../../../.gitbook/assets/image (243).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 16</mark>

1. In the Inbound rules section, to remove the existing rule, click Delete.

* You must delete the existing rule to modify the rule type.

2. To add a new rule, click Add rule.
3. Go to the next step.

#### <mark style="color:blue;">Concept</mark>

By removing the 0.0.0.0/0 source and replacing it with a security group, you can control which resources are allowed to send traffic to instnaces without having to input address ranges. Only traffic from the instances associated with the security group is allowed.

<figure><img src="../../../.gitbook/assets/image (244).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 17</mark>

1. For Type, choose HTTP.
2. For Source, choose the TravelAgencyLoadBalancer security group.
3. Go to the next step.

<figure><img src="../../../.gitbook/assets/image (245).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 18</mark>

1. Click Save rules.
2. Go to the next step.

<figure><img src="../../../.gitbook/assets/image (246).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 19</mark>

1. In the left navigation pane, click Load Balancers.
2. In the Load balancers section, click TravelAgencyWebServers-1.
3. Go to the next step.

#### <mark style="color:blue;">Concept</mark>

Custom security groups are active only after you assign them to an instance. You can assign multiple security groups to an instance.

<figure><img src="../../../.gitbook/assets/image (247).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 20</mark>

1. Scroll down to the Security tab.
2. Go to the next step.

<figure><img src="../../../.gitbook/assets/image (248).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 21</mark>

1. On the Security tab, click Edit.
2. Go to the next step.

#### <mark style="color:blue;">Concept</mark>

The security groups that you associate with your load balancer determine your rules for controlling where traffic can come from and where it can be sent.

<figure><img src="../../../.gitbook/assets/image (249).png" alt=""><figcaption></figcaption></figure>

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

***

### <mark style="color:purple;">Step 32</mark>

#### <mark style="color:blue;">Concept</mark>

***

### <mark style="color:purple;">Step 33</mark>

#### <mark style="color:blue;">Concept</mark>

***

### <mark style="color:purple;">Step 34</mark>

#### <mark style="color:blue;">Concept</mark>

***

### <mark style="color:purple;">Step 35</mark>

#### <mark style="color:blue;">Concept</mark>

***

### <mark style="color:purple;">Step 36</mark>

#### <mark style="color:blue;">Concept</mark>

***

### <mark style="color:purple;">Step 37</mark>

#### <mark style="color:blue;">Concept</mark>

***

### <mark style="color:purple;">Step 38</mark>

#### <mark style="color:blue;">Concept</mark>

***

### <mark style="color:purple;">Step 39</mark>

#### <mark style="color:blue;">Concept</mark>

***

***

### <mark style="color:purple;">Step 40</mark>

#### <mark style="color:blue;">Concept</mark>

***

### <mark style="color:purple;">Step 41</mark>

#### <mark style="color:blue;">Concept</mark>

***

### <mark style="color:purple;">Step 42</mark>

#### <mark style="color:blue;">Concept</mark>

***

### <mark style="color:purple;">Step 43</mark>

#### <mark style="color:blue;">Concept</mark>

***

### <mark style="color:purple;">Step 44</mark>

#### <mark style="color:blue;">Concept</mark>

***

### <mark style="color:purple;">Step 45</mark>

#### <mark style="color:blue;">Concept</mark>

***

## <mark style="color:red;">DIY Activite</mark>

* [ ] Configure an Auto Scaling group to include a new EC2 instance in a third Availability Zone.

***
