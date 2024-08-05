# Networking Concepts

| Título da tarefa  | Solicitação de negócios                                                                                      |
| ----------------- | ------------------------------------------------------------------------------------------------------------ |
| Conceitos de rede | Ajude o banco a configurar um ambiente de rede seguro que permita a comunicação entre recursos e a internet. |

<figure><img src="../../../.gitbook/assets/image (17) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

<details>

<summary><mark style="color:purple;">Contexto</mark></summary>



</details>

***

## <mark style="color:red;">Amazon VPC</mark>



***

## <mark style="color:red;">Descrição da tarefa</mark>

Defina os principais recursos de VPCs, sub-redes, gateways de internet e tabelas de rotas.&#x20;

* Descreva os benefícios de usar Amazon VPCs.&#x20;
* Declare os conceitos básicos de notação de bloco CIDR e endereçamento IP.&#x20;
* Explique como o tráfego VPC é roteado e protegido usando gateways, listas de controle de acesso à rede e grupos de segurança.

1. **Explore the components that comprise a virtual private cloud (VPC)**
2. **Configure a route table attached to a subnet within a VPC.**
3. **Configure an internet gateway inside a VPC.**
4. **Configure inbound rules within a security group to control access.**

***

### <mark style="color:purple;">**Step 1**</mark>

1. On the top navigation bar, review the Region selector to ensure that the Region is set to N. Virginio (us-east-1).
2. In the Services search box, type: EC2
3. In the search results, under Services, click EC2.
4. Go to next step

#### <mark style="color:blue;">**Concept**</mark>

AWS launched its very first Amazon Elastic Compute Cloud (Amazon EC2) instance in August, 2006.

<figure><img src="../../../.gitbook/assets/image (22) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">**Step 2**</mark>

1. In the left navigation pane, click instances.
2. Go to the next step

<figure><img src="../../../.gitbook/assets/image (5) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">**Step 3**</mark>

1. In the instances section, choose the check box to select Web Server instance.
2. On the Details tab, under Public IPv4 address, click the copy icon to copy the provided addredd.
3. Go to the next step

<figure><img src="../../../.gitbook/assets/image (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">**Step 4**</mark>

1. In a new browser tab, paste the IP Address that you just copied and press Enter.

* After a few minutes, a site timeout message will appear.

2. To solve this issue return to the previous browser (the Instances page in the Amazon EC2 console).
3. Go to the next step

<figure><img src="../../../.gitbook/assets/image (2) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">**Step 5**</mark>

1. In the instances section, choose the check box to select the Web Server instance.
2. Click the Networking tab.
3. Review the Public and Private IIPv4 address.
4. Go to the next step

#### <mark style="color:blue;">**Concepts**</mark>

Using Amazon Virtual Private Cloud (Amazon VCP), you can launch AWS resources into a virtual network closely resembles a traditional network that you'd operate in you own data center, with the benefits of using the scalable infrastructure of AWS.

<figure><img src="../../../.gitbook/assets/image (3) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">**Step 6**</mark>

1. Under Subnet ID, click the provided ID.
2. Go the next step

#### <mark style="color:blue;">**Concepts**</mark>

A subnet is a range of IP addresses in your VPC. You can launch AWS resources into a specified subnet. Each subnet must reside entirely within one Availability Zone and cannot span zones.

<figure><img src="../../../.gitbook/assets/image (4) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">**Step 7**</mark>

1. In the Subnets section, choose the check box to select the network-concepts subnet.
2. Click the Route table tab.
3. Next to Route table, click the link name that contains web-server-netSubnet1

#### <mark style="color:blue;">**Concepts**</mark>

A route table contains a set of rules, called routes, that are used to determine where network traffic from your subnet or gateway is directed. Use a public subnet for internet-connected resources and a private subnet for resources not connected to the Internet.

<figure><img src="../../../.gitbook/assets/image (5) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">**Step 8**</mark>

1. In the Route tables section, choose the check box to select the network-concepts route table.
2. Click the Routes tab.
3. Review the two route table entries.

* One route sends local traffic to the local network only, and the other route sends all other traffic to the internet through a NAT gateway.

4. Click Edit routes.
5. Go to the next step.

#### <mark style="color:blue;">**Concepts**</mark>

The CIDR naming convention 0.0.0.0/0 represents all IPv4 address (::/0 for IPv6).

<figure><img src="../../../.gitbook/assets/image (6) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">**Step 9**</mark>

1. To delete e NAT gateway from the route table, click Remove.
2. Go to the next step.

#### <mark style="color:blue;">**Concepts**</mark>

A NAT gateway is a network address translation (NAT) service. With a NAT gateway, instances in a private subnet can connect to services outside your VPC. External services cannot initiate a connection with those instances.

<figure><img src="../../../.gitbook/assets/image (7) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">**Step 10**</mark>

1. Click Add route.
2. To configure the new route, for Destination, type: 0.0.0.0/0
3. For Target, choose Internet Gateway.
4. Choose igw-xxxxxxx(network-concepts/VPC).
5. Click Save changes.
6. Go to the next step

#### <mark style="color:blue;">**Concepts**</mark>

An internet gateway serves two purposes:

* Provide a target in your VPC route tables for internet-routable traffic.
* Perform network address translation (NAT) for instances that have been assigned public IPv4 addresses.

<figure><img src="../../../.gitbook/assets/image (8) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">**Step 11**</mark>

1. On the Routes tab, review the new internet gateway association.

* The subnet is now reachable from the internet.

2. Navigate to the Instances page on the Amazon EC2 console.

* Remember, on the top navigation bar, you can use the Services search box (or click Services) to navigate to a different service console

3. Go to the next step

#### <mark style="color:blue;">**Concepts**</mark>

An internet gateway supports IPv4 and IPv6 traffic. It does not cause availability risks or bandwidth constraints on your network traffic. There's no additional charge for having an internet gateway in you account.

<figure><img src="../../../.gitbook/assets/image (9) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">**Step 12**</mark>

1. In the felt navigation pane, click instances.
2. In the Instances section, choose the check box to select the Web Server instance.
3. Click the Security tab.
4. Under Security groups, click WebServerSecurityGroup
5. Go to the next step

<figure><img src="../../../.gitbook/assets/image (10) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">**Step 13**</mark>

1. On the Inbound rules tab, click Edit inbounds rules.
2. Go to the next step

#### <mark style="color:blue;">**Concepts**</mark>

For each security group, you can add rules that control the traffic based on protocols and port numbers. Separate sets of rules exist for inbound traffic and outbound traffic.

<figure><img src="../../../.gitbook/assets/image (11) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">**Step 14**</mark>

1. Click Add rule
2. Go to the next step

#### <mark style="color:blue;">**Concepts**</mark>

When you create a VPC, it comes with a default security group. You can create additional security groups for each VPC.

<figure><img src="../../../.gitbook/assets/image (12) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">**Step 15**</mark>

1. In the Inbound rules section, for Type, click the search box to expand the dropdown menu.
2. Scroll down to see the varius predefined protocols available.

* You can see MYSQL/Aurora protocol on the dropdown menu, which you will use in the upcoming DIY section of this solution.

3. Choose HTTP.
4. Go to the next step.

#### <mark style="color:blue;">Concepts</mark>

You can create a security group and add rules that reflect the role of the instance that is associated with the security group. For example, an instnace that is configured as a web server needs security group rules that allow inbound HTTP and HTTPS access. Likewise, a database instance needs rules that allow access for the type of database, such as access over port 3306 for MySQL.

<figure><img src="../../../.gitbook/assets/image (13) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">**Step 16**</mark>

1. For Source, choose Anywhere-IPV4.
2. Review the recommended setting warning alert.
3. Click Save rules.
4. Go to the next step

#### <mark style="color:blue;">**Concepts**</mark>

Security groups are stateful. For example, if you send request from an instance, the response traffic for that request is allowed to reach the instance regardless of the inbound security group rules. Responses to allowed inbound traffic are allowed to leave the instance, regardless of the outbound rules.

<figure><img src="../../../.gitbook/assets/image (14) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">**Step 17**</mark>

1. In the left navigation pane, click Instances.
2. Go to the next step.

<figure><img src="../../../.gitbook/assets/image (15) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">**Step 18**</mark>

1. In the Instances section, choose the check box to select the Web Server instance.

* This will test connectivity using a Java application.

2. Click the Networking tab.
3. Under Publick IPv4 address, click the copy icon to copy the provided address.
4. Go to the next step

<figure><img src="../../../.gitbook/assets/image (118).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">**Step 19**</mark>

1. In the new browser tab, paste the instance IP address that you just coiped and press Enter.
2. Review the application that loads from the publick IP address.
3. Review the connection from the internet to the Web Server.

* A connection should be established.

4. Review the connection from the Web Server to the DB Server.

* A connection from the Web Server to the DB Server sould display as failed.

5. Go to the next step

#### <mark style="color:blue;">**Concepts**</mark>

To deploy a working internet gateway, the following must be completed:

* The internet gateway must be attached to a VPC
* Route tables associated with your public subnet must have a route to your internet gateway.
* Security groups associated with your VPC must allow traffic to/from the internet.
* Any instances in the VPC must have a public IP or Elastic IP address assigned.

<figure><img src="../../../.gitbook/assets/image (119).png" alt=""><figcaption></figcaption></figure>

***

## DIY Activite

* [ ] &#x20;Escrever

***
