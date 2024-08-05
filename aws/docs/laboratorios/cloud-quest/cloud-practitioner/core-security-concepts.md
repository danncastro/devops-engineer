---
description: >-
  Use IAM to provide work permissions to engineers by using group settings and
  the least privilege principle.
---

# Core Security Concepts

| Título da tarefa               | Solicitação de negócios                                                                                                                        |
| ------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------- |
| Conceitos Básicos de Segurança | Ajude a melhorar a segurança na bolsa de valores da cidade garantindo que os engenheiros de suporte possam executar somente ações autorizadas. |

<figure><img src="../../../.gitbook/assets/image (5).png" alt=""><figcaption></figcaption></figure>

<details>

<summary><mark style="color:purple;">Contexto</mark></summary>

<mark style="background-color:blue;">Client</mark>: Hello, and welcome to the city stock exchange. Thanks for answering our call.

<mark style="background-color:orange;">Architect</mark>:  No problem. How can i help you?

<mark style="background-color:blue;">Client</mark>: We recently decided to create a Support Engineering team. As this team grows, we want to be able to manage users efficiently, providing all support engineers the same set of permissions. Can AWS help with this?

<mark style="background-color:orange;">Architect</mark>: Yes! AWS has a service called AWS Identity and Access Management, or IAM. You can use IAM to create policies that manage AWS users and groups, and you can use permissions to allow and deny access too AWS resources. Using IAM, you can manage your security requirements at scale.

<mark style="background-color:blue;">Client</mark>: So, with policies, do i need to learn every type of permission for all AWS services? I just want my support engineers to have read-only access to Amazon EC2 and Amazon RDS.

<mark style="background-color:orange;">Architect</mark>: No, you don't. IAM delivers prebuilt AWS managed policies to help you get started quickly. Two prebuilt policies provide read-only access to Amazon EC2 and Amazon RDS.

<mark style="background-color:blue;">Client</mark>: Great, And if i don't want to use those predefined policies? Can i create my own?

<mark style="background-color:orange;">Architect</mark>: Yes! You can create your own custom policy and apply it to your resources. AWS also has tools that can help you create policy files.

<mark style="background-color:blue;">Client</mark>: Wow. Sounds like there are lot of options. How about the actual creation of a user? I wolud like my support engineers to have access to the AWS Management Console and to developer tools. I also want to assign users to the Support Engineering team righ away.

<mark style="background-color:orange;">Architect</mark>: When you create users, you can assign them permissions to access resources through the AWS Management Console, AWS CLI, or developer tools. You can also place users in groups and assign permissions.

<mark style="background-color:blue;">Client</mark>: Thanks! This sounds promising.

Can you show us how to get started by creating users and a user group for our Support Engineering team?

<mark style="background-color:orange;">Architect</mark>: Yes

<mark style="background-color:blue;">Client</mark>: Thanks so much. Our security team will sleep well knowing that permissions are locked down.

</details>

***

## <mark style="color:red;">Recursos</mark>

**AWS IAM:** This solution uses AWS Identity and Access Management (IAM) to create a SupportEngineers group with limited permissions.

First, an IAM user group is created.

A read-only access policy for the Amazon EC2 Service is attached to the SupportEngineers group.

IAM users are created and added to the SupportEngineers user group.

**IAM Features:** All users that belong to the SupportEngineers group will inherit the permissions set in the policies that are attached to the group.

Multiple policies can be attached to the same user group to further refine permissions.

***

## <mark style="color:red;">Descrição da tarefa</mark>

Descreva o processo de criação e as diferenças entre usuários, funções e grupos do AWS IAM.&#x20;

* Revise a estrutura e os componentes das Políticas do AWS IAM.&#x20;
* Resuma o Modelo de Responsabilidade Compartilhada da AWS e os programas de conformidade.

1. Create an IAM group and users.
2. Attach an AWS managed policy to a group of users.

***

### <mark style="color:purple;">Step 1</mark>

1. In the top navigation bar search box, type: IAM
2. In the search results, under Services, click IAM.
3. Go to the next step.

#### <mark style="color:blue;">Concept</mark>

You can use AWS Identity and Access Management (IAM) to manage secure acess to AWS services and resources. IAM is a feature of your AWS account, offered at no additional charge. You are charged only for the use of other AWS services by your users.

<figure><img src="../../../.gitbook/assets/image (1) (1).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 2</mark>

1. In the left navigation pane, click User groups.
2. In the User groups section, click Create group.
3. Go to the next step.

#### <mark style="color:blue;">Concept</mark>

A collection of users will often need a similar set of permissions. An IAM group can be used to define permissions for multiple users. When IAM users are added to a group, they inherit all the permissions attachd to the group.

<figure><img src="../../../.gitbook/assets/image (2) (1).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 3</mark>

1. For User group name, type: SupportEngineers
2. Scroll down to Attach permissions policies.
3. Go to the next step.

#### <mark style="color:blue;">Concept</mark>

A user group can contain many users, and a user can belong to multiple user groups. User groups can't be nested; they can contain only users, not other user groups. There is no default user group that automatically includes all users in the AWS account. If you want a user group like that, you must create it and assign each new user to it.

<figure><img src="../../../.gitbook/assets/image (3) (1).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 4</mark>

1. In the Attach permissions policies search box, type: AmazonEC2ReadOnlyAccess and press Enter.
2. Under Policy name, choose the check box to select AmazonEC2ReadOnlyAccess.
3. Click Create group.
4. Go to the next step.

#### <mark style="color:blue;">Concept</mark>

A policy is an object in AWS that, when associated with an identiy or resource, defines their permissions. AWS evaluates policies every time an IAM principal (user or role) makes a request.

<figure><img src="../../../.gitbook/assets/image (4) (1).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 5</mark>

1. In the left navigation pane, click Users.
2. In the Users section, click Create user.
3. Go to the next step.

#### <mark style="color:blue;">Concept</mark>

An IAM user is an entity that you create in AWS to represent the person or application that uses it to interact with AWS. A user in AWS consists of a name and credentials. An IAM user with administrator permissions is not the same thing as the AWS account root user.

<figure><img src="../../../.gitbook/assets/image (5) (1).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 6</mark>

1. In the Specify user details step, for User name, type: support-engineer-1
2. Choose the check box to select Provide user access to the AWS Management Console.
3. For Console password, Choose Custom password.
4. In the Custom password text box, type: supportPassword!123

* All passwords must contain at least eight characters with a mix of characters that are uppercase, lowercase, numbers, and symbols. Your IAM user will not be able to sign in if these requirements are not met.

5. Clear the check box to deselect Users must create a new password at next sign-in.
6. Scroll down and click Next (not shown).
7. Go to the next step.

#### <mark style="color:blue;">Concept</mark>

Disabling the AWS Management Console access password for a user prevents them from signing ain to the console by using their user name and password. It does not change their permissions or prevent them from accessing the console by using an assumed role.

<figure><img src="../../../.gitbook/assets/image (6).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 7</mark>

1. In the Set permissions step, for Permissions options, choose Add user to group.
2. In the User groups section, choose the check box to select SupportEngineers.
3. Click Next.
4. Go to the next step.

#### <mark style="color:blue;">Concept</mark>

A user can belong to more than one group. In the event that groups have conficting polices, AWS has a policy evaluation logic.

<figure><img src="../../../.gitbook/assets/image (7).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 8</mark>

1. In the Review and create step, in the Tags section, click Add new tag.
2. For Key, type: job-title
3. For Value, type: Support Engineer
4. Click Create user.
5. Go to the next step.

#### <mark style="color:blue;">Concept</mark>

Users can have tags associated with them,  which can help you manage a large amount of users in the furure

<figure><img src="../../../.gitbook/assets/image (8).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 9</mark>

1. In the Retrieve password step, under Console sign-in URL, click the copy icon to copy the provided URL, and then paste it to the text editor of your choice on your device.

* You can also download the .csv file that contains the console sign-in link and credentials by clicking Download .csv file.

2. Click Return to users list.
3. Click Continue on the pop-up (not shown).
4. Go to the next step.

#### <mark style="color:blue;">Concept</mark>

For extra security, you can enable multi-factor authentication (MFA) for all users in your account. Using MFA, user have a device that generates a response to an authentication challenge. If a user's password or access keys are compromised, you account resources are still secure because of the additional authentication requirement.

<figure><img src="../../../.gitbook/assets/image (9).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 10</mark>

1. In a new incognito or private browsing window address bar, paste the console sign-in link that you just copied and press Enter.

* Using an incognito or private browsing window for this step, you can remain logged in with your original credentials in the previous browser window.

2. For IAM user name, type: support-engineer-1
3. For Password, type: supportPassword!123
4. Click Sign in.
5. Go to the next step.

#### <mark style="color:blue;">Concept</mark>

As ab administrator, you can sign in as your newly created user to review their access level. Regularky change your own passwords and access keys, and make sure that all IAM users in your account also regularly change theirs. If you allow users to change their own passwords, create a custom password policy that requires them to create strong passwords.

<figure><img src="../../../.gitbook/assets/image (10).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 11</mark>

1. In the top navigation bar search box, type: EC2
2. In the search results, under Services, click EC2.
3. Go to the next step.

#### <mark style="color:blue;">Concept</mark>

Amazon Elastic Compute Cloud (Amazon EC2) is a web service that provides resizable compute capacity in the cloud. It is designed to help streamline web-scale computing for developers.

<figure><img src="../../../.gitbook/assets/image (11).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 12</mark>

1. On the top navigation bar, click the Region selector dropdown menu.
2. If it is not chosen already, choose US East (N. Virginia) us-east-1.
3. Go to the next step.

<figure><img src="../../../.gitbook/assets/image (12).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 13</mark>

1. On the EC2 Dashboard, in the Resources section, click Instances (running).
2. Go to the next step.

#### <mark style="color:blue;">Concept</mark>

The Amazon EC2 Dashboard displays metrics on the number of resources by type.

<figure><img src="../../../.gitbook/assets/image (13).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 14</mark>

1. In the Instances section, choose the check box to select the Web Server instance.
2. At the top of the page, click Instance state to expand the dropdown menu.
3. Choose Terminate instance.
4. Go to the next step.

#### <mark style="color:blue;">Concept</mark>

All updates to user and group permissions are immediate.

<figure><img src="../../../.gitbook/assets/image (14).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 15</mark>

1. In the pop-up box, click Terminate.
2. Go to the next step.

<figure><img src="../../../.gitbook/assets/image (15).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 16</mark>

1. In the error alert, review the Failed to terminate message, stating that you cannot delete an instance due to user permissions.
2. Go to the next step.

#### <mark style="color:blue;">Concept</mark>

Users can perform actions only that are allowed by the assigned IAM policies.

<figure><img src="../../../.gitbook/assets/image (16).png" alt=""><figcaption></figcaption></figure>

***

## <mark style="color:red;">DIY Activite</mark>

* [x] &#x20;Grant the SupportEngineers group read-only access to Amazon RDS

<figure><img src="../../../.gitbook/assets/image (17).png" alt=""><figcaption></figcaption></figure>

***
