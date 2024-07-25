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

<summary><mark style="color:purple;">Contexto com cliente</mark></summary>

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

1. Launch and configure an Amazon EFS file system
2. Mount the file system to an Amazon EC2 instance.
3. Connect a second EC2 instance to the same file system
4. Share files between the two EC2 instances.

***

### <mark style="color:purple;">Step 1</mark>

***

## <mark style="color:red;">DIY Activite</mark>

* [ ] Mount an Amazon EFS endpoint to a third EC2 instance.
* [ ] Test that the files are accessible from the EC2 instance.

***
