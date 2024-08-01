# Connecting VPCs

| Título da tarefa | Solicitação de negócios                                                                                                        |
| ---------------- | ------------------------------------------------------------------------------------------------------------------------------ |
| Conectando VPCs  | A equipe de marketing da cidade quer Amazon VPCs separadas para cada departamento que permita a comunicação entre Amazon VPCs. |

<figure><img src="../../../.gitbook/assets/image (120) (1).png" alt=""><figcaption></figcaption></figure>

<details>

<summary><mark style="color:purple;">Contexto</mark></summary>



</details>

***

## <mark style="color:red;">Peering VPC</mark>



***

## <mark style="color:red;">Descrição da tarefa</mark>

Resuma como o peering de VPC funciona com o Amazon VPC.&#x20;

* Explique as etapas para estabelecer uma conexão de peering de VPC.&#x20;
* Crie uma conexão de peering entre dois Amazon VPCs.&#x20;
* Estabeleça uma conexão de peering entre Amazon VPCs usando uma sub-rede específica.

1. **Set up a VPC peering connection**
2. **Ensure that traffic is internally routed within this connection.**

***

### <mark style="color:purple;">**Step 1**</mark>

1. In the navigation bar search box, type: VPC
2. In the search results, under Services, click VPC.
3. Go to the next step.

#### <mark style="color:red;">**Concept**</mark>

Amazon Virtual Private Cloud (Amazon VPC) is a service that helps you launch AWS resources in a logically isolated virtual network that you define. You have complete control over you virtual networking environment.

<figure><img src="../../../.gitbook/assets/image (121).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">**Step 2**</mark>

1. In the left navigation pane, click Your VPCs.
2. In the your VPCs section, review the Marketing, Finance, and Developer VPCs.
3. Go to the next step

#### <mark style="color:red;">**Concept**</mark>

By default, VPCs are isolated from each other. A VPC peering connection is a networking connection between two VPCs that you can use to route traffic between them by using private IP address.

<figure><img src="../../../.gitbook/assets/image (122).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">**Step 3**</mark>

1. In the top navigation bar search box, type: EC2
2. In the search results, under Services, click EC2
3. Go to the next step.

<figure><img src="../../../.gitbook/assets/image (123).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">**Step 4**</mark>

1. In the Resources section, click Instances (running).
2. Go to the next step.

<figure><img src="../../../.gitbook/assets/image (124).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">**Step 5**</mark>

1. In the Instances section, choose the check box to select the FinanceServer instance.
2. On the Details lab, review to see that no Public IPv4 address or DNS is populated for FinanceServer.

* This is because the server was created in a private subnet.

3. Under Private IPv4 addresses, click the copy icon to copy the provided IP address for FinanceServer, and then paste it in the text editor of your choice on your local device.

* You will use this value in later steps.

4. Scroll down to Subnet ID
5. Go to the next step

<figure><img src="../../../.gitbook/assets/image (125).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">**Step 6**</mark>

1. Under Subnet ID, review the provided ID.

* Note that the subnet is private (FinancePrivateSubnet)

2. Go to the next step.

<figure><img src="../../../.gitbook/assets/image (126).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">**Step 7**</mark>

1. To view the details of the MarketingServer instance, clear the check box to deselect the FinanceServer instance, and then choose the check boc to select the MarketingServer instance.
2. On the Details tab, under VPC ID, review the VPC that the MarketingServer instance belongs to
3. In the Instance section, click Connect.
4. Go to the next step

#### <mark style="color:red;">**Concept**</mark>

You can connect to an Amazon Elastic Compute Cloud (Amazon EC2) instance in four ways:&#x20;

* EC2 Insntace Connect
* Session Manager
* SSH client
* EC2 Serial Console

<figure><img src="../../../.gitbook/assets/image (127).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">**Step 8**</mark>

1. Click the Session Manager tab.
2. Click Connect.

* The Session Manager terminal for the MarketingServer instance opens in a new browser tab (or window).

3. Go to the next step.

#### <mark style="color:red;">**Concept**</mark>

Session Manager is a fully managed AWS System Manager capability. With Session Manager, you can manage your Amazon EC2 instances, edge devices, and on-premises servers and virtual machines (VMs). You can use either an interactive one-click browser-based shell or the AWS Command Line Interface (AWS CLI).

<figure><img src="../../../.gitbook/assets/image (128).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">**Step 9**</mark>

1. In the terminal window, replacing the current IP address with the IP address that you copied in an earlier step, run (type the command and press Enter) ping 172.31.x.xx

* This private IPv4 address is for the FinanceServer instance. This command checks the connection to the FinanceServer instance

2. Review to see that your command hangs, and there is no connection.
3. To exit the running process, on your keyboard, press CTRL + C
4. Go to the next step.

#### <mark style="color:red;">**Concept**</mark>

By default, VPCs cannot communicate with resources in other VPCs using private IPv4 addresses or IPv6 addresses. In our example, the FinanceServer instance doesn't have a public IP, so your VPCs don't know how to route data to private IP destinations outside of thir own private range.

<figure><img src="../../../.gitbook/assets/image (129).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">**Step 10**</mark>

1. In the previous browser, in the Amazon EC2 Instances section, under Instance ID, click the MarketingServer instance ID.
2. Go to the nest step

<figure><img src="../../../.gitbook/assets/image (130).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">**Step 11**</mark>

1. Under Subnet ID, click the provided ID.
2. Go to the next step

<mark style="color:red;">**Concept**</mark>

EC2 instances reside within a subnet. A subnet is a range of IP Addresses in your VPC.

<figure><img src="../../../.gitbook/assets/image (131).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">**Step 12**</mark>

1. In the Subnets section, choose the check box to select the subnet name.
2. On the Details tab, under Route table, click the provided route ID.
3. Go to the next step

#### <mark style="color:red;">**Concept**</mark>

An important property of a subnet is its route table. A route table contains a set of rules, called routes. Routes are used to determine where network traffic, from your subnet or gateway, is directed.

<figure><img src="../../../.gitbook/assets/image (132).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">**Step 13**</mark>

1. Under Route tables, choose the Marketing route table.
2. Click the Routes tab.
3. In the Routes section, review the routing rules.

* You should see two routes: one route for the local traffic and one route for the internet traffic through the internet gateway.

4. Go to the next step.

#### <mark style="color:red;">**Concept**</mark>

Routes tables will have rules for local traffic and public IP ranges if a gateway is attached. We recommend that you specify a CIDR block from the private IPv4 address ranges, as specifed in RFC 1918.

<figure><img src="../../../.gitbook/assets/image (133).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">**Step 14**</mark>

1. In the left navigation pane, click Peering connections.
2. In the Peering connections section, click Create peering connection.
3. Go to the next step

#### <mark style="color:red;">**Concept**</mark>:

Instances in either VPC can communicate with each other as if they are in the same network.

<figure><img src="../../../.gitbook/assets/image (134).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">**Step 15**</mark>

1. In the Peering connection settings section, for Name, type: Marketing <> Finance
2. For VPC ID (Requester), on the dropdown menu, choose the Marketing VPC.
3. For VPC CIDRs, review to ensure that the Marketing VPC has 10.10.0.0/16 as its CIDR range.
4. Scrool down to the bottom of the page.
5. Go to the next step

#### <mark style="color:red;">**Concept**</mark>

Your VPC will request that another VPC allow access to its resources. the VPC that makes the request is called the Requester. You can request access to VPCs from other AWS accounts.

<figure><img src="../../../.gitbook/assets/image (135).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">**Step 16**</mark>

1. For VPC ID (Accepter), choose the Finance VPC.
2. For VPC CIDRs, review to ensure that the Finance VPC has 172.31.0.0/16 as it CIDR range.
3. Click Create peering connection.
4. Go to the next step.

<figure><img src="../../../.gitbook/assets/image (136).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">**Step 17**</mark>

1. In the success alert, review the message.
2. Under Status, review to ensure that the status is Pending Acceptance by xxxxxx.
3. Click Actions to expand the dropdown menu.
4. Choose Accept request.
5. Go to the next step

#### <mark style="color:red;">**Concept**</mark>

To request a VPC peering connection with a VPC in your account, ensure that you have the IDs of the VPCs with which you are creating the VPC peering connection. You must both create and accept the VPC peering connection request yourself to activate it. if the peering connection is across accounts, both accounts must accept the connection to activate it.

<figure><img src="../../../.gitbook/assets/image (137).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">**Step 18**</mark>

1. In the pop-up box, click Accept request.
2. Go to the next step

<figure><img src="../../../.gitbook/assets/image (138).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">**Step 19**</mark>

1. In the success alert, review the message.
2. Under Status, review to see that the status is Active.
3. Go to the next step

<figure><img src="../../../.gitbook/assets/image (139).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">**Step 20**</mark>

1. Return to the Instances section on the Amazon EC2 console. and then choose the check box to select the MarketingServer instance.
2. On the Details tab, under Subnet ID, click the provided ID.
3. Go to the next step

#### <mark style="color:red;">**Concept**</mark>

After you establish a peering connection, you must modify the route table associeated with each VPC. You must add a route into each route table to allow traffic to be routed to the peered VPC.

<figure><img src="../../../.gitbook/assets/image (140).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">**Step 21**</mark>

1. In the Subnets section, choose the check box to select the available subnet.
2. Under Route table, click the provided route ID.
3. Go to the next step

<figure><img src="../../../.gitbook/assets/image (141).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">**Step 22**</mark>

1. In the Route tables section, choose the Marketing route table.
2. Click the Routes tab.
3. Click Edit routes.
4. Go to the next step

<figure><img src="../../../.gitbook/assets/image (143).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">**Step 23**</mark>

1. Click Add route.
2. To configure the route, for Destination, in the new search box, type: 172.31.0.0/16
3. For Target, in the dropdown box, choose Peering Connection.
4. Choose the peering connection target that contains Marketing <> Finance.
5. Click Save changes.
6. Go to the next step

<figure><img src="../../../.gitbook/assets/image (144).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">**Step 24**</mark>

1. In the success alert, review the message.
2. Go to the next step

<figure><img src="../../../.gitbook/assets/image (145).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">**Step 25**</mark>

1. Return to the Instance section on the Amazon EC2 console, and then choose the check boc to select the FinanceServer instance.
2. On the Details tab, under Subnet ID, click the provided ID.
3. Go to the next step

<figure><img src="../../../.gitbook/assets/image (146).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">**Step 26**</mark>

1. In the Subnets section, choose the check box to select the available subnet.
2. On the Details tab, under Route table, click the provided route ID.
3. Go to the next step

<figure><img src="../../../.gitbook/assets/image (147).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">**Step 27**</mark>

1. In the Route tables section, choose the Finance route table.
2. Click the Routes tab.
3. Click Edit routes.
4. Go to the next step.

#### <mark style="color:red;">**Concept**</mark>

The route tables for each VPC must be modified to allow traffic across the peering connection.

<figure><img src="../../../.gitbook/assets/image (148).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">**Step 28**</mark>

1. Click Add route.
2. To configure the route, for Destination, in the new search box, type: 10.10.0.0/16
3. For Target, in the dropbox box, choose Peering Connection.
4. Choose the peering connection taget that contains Marketing <> Finance.
5. Click Save changes.
6. Go to the next step

<figure><img src="../../../.gitbook/assets/image (149).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">**Step 29**</mark>

1. In the success alert, review the message.
2. Go to the next step.

<figure><img src="../../../.gitbook/assets/image (150).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">**Step 30**</mark>

1. Return to the Amazon EC2 Instances section, and then choose the check box to select the MarketingServer instance.
2. Click Connect
3. Go to the next step.

<figure><img src="../../../.gitbook/assets/image (151).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">**Step 31**</mark>

1. Click the Session Manager tab.
2. Click Connect
3. Go to the next step

<figure><img src="../../../.gitbook/assets/image (152).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">**Step 32**</mark>

* The Session Manager terminal for the MarketingServer instance opens in a new browser  tab (or window).

1. In the terminal, replacing the current IP address with the IP address that you copied in an earlier step, run: ping 172.31.x.xx

* This private IPv4 address is for the FinanceServer instance.

2. Review to see that the ping command is still not working.
3. To exit the running process, on your keyboard, press CTRL + C.
4. Go to the next step

<mark style="color:red;">**Concept**</mark>:  Peered VPCs do not necessarily accept all data between them. Security features, such as network access control lists and security groups, still apply. Be sure to update them accordingly.

<figure><img src="../../../.gitbook/assets/image (153).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">**Step 33**</mark>

1. In the previous browser, in the Amazon EC2 Instances section, choose the check box to select the FinanceServer instance.
2. Click the Security tab.
3. Under Security groups, click the provided security group name that contains FinanceServerSecurityGroup.
4. Go to the next step

<mark style="color:red;">**Concept**</mark>: Security groups do not automatically accept data from peered VPCs. You must update security groups to allow a peered VPC as an incoming source.

<figure><img src="../../../.gitbook/assets/image (154).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">**Step 34**</mark>

1. Click the Inbound rules tab.
2. Click Edit inbound rules.
3. Go to the next step

#### <mark style="color:red;">**Concept**</mark>

Security groups are stateful. If you send a request from your instance, the responde traffic for that request is allowed to flow in regardless of the inbound rules. This also means that responses to allowed inbound traffic are allowed to flow out, regardless of the outbound rules.

<figure><img src="../../../.gitbook/assets/image (155).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">**Step 35**</mark>

1. Click Add rule.
2. To configure the rule, for Type, in the new search box, choose Custom ICMP - IPv4.
3. For Source, in the new search box, type and choose: 10.10.0.0/16
4. Click Save rules.
5. Return to the Amazon EC2 Instance page, and then connect to the MarketingServer instance by using Session Manager (not shown).
6. Go to the next step.

#### <mark style="color:red;">**Concept**</mark>

Security group rules are always permissive. You can't create rules that deny access. Using security group rules, you can filter traffic based on protocols and port numbers.

<figure><img src="../../../.gitbook/assets/image (156).png" alt=""><figcaption></figcaption></figure>

***

<mark style="color:purple;">**Step 36**</mark>

1. In the terminal, replacing the current  IP address with the IP address that you copied in an earlier step, run: ping 172.31.x.xx

* This private IPv4 address is for the FinanceServer instance.

2. Review the data.

* The MarketingServer instance should now be able to communicate with the FinanceServer instance.

3. To exit the Running process, on your keyboard, press CTRL + C
4. Go to the next step

#### <mark style="color:red;">**Concept**</mark>

Your services can communicate after your VPCs are peered and the security groups allow the corrent traffic. Remember, if you need to add different traffic types, you will have to change the inbound rules of your security groups.

<figure><img src="../../../.gitbook/assets/image (157).png" alt=""><figcaption></figcaption></figure>

***

DIY Activite

* [x] Configure VPC peering between Developer and Finance department VPCs.

<figure><img src="../../../.gitbook/assets/image (158).png" alt=""><figcaption></figcaption></figure>

***
