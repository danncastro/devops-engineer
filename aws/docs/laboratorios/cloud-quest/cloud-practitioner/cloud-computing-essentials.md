# Cloud Computing Essentials

| Título da tarefa                         | Solicitação de negócios                                                                                                         |
| ---------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------- |
| Noções básicas sobre computação em nuvem | O portal da cidade precisa migrar a página de previsão do tamanho das ondas da praia para a AWS para melhorar a confiabilidade. |

<figure><img src="../../../.gitbook/assets/image (3) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

<details>

<summary><mark style="color:purple;">Contexto</mark></summary>



</details>

***

## <mark style="color:red;">Amazon S3</mark>



***

## <mark style="color:red;">Descrição da tarefa</mark>

Articule as características da plataforma de computação em nuvem da AWS. Descreva os principais benefícios do uso de produtos e serviços da AWS.&#x20;

* Compare e contraste os serviços de nuvem da AWS com a infraestrutura On-Premises.&#x20;
* Implemente a hospedagem de uma página da Web estática usando o Amazon S3.

1. **Create a bucket in Amazon S3.**
2. **Enable static website hosting on the S3 Bucket**
3. **Test access to the webpage hosted on Amazon S3**

***

### <mark style="color:purple;">**Step 1**</mark>

1. In the top navigation bar search box, type: S3
2. In the search results, under services, click S3.
3. Go to the next step

#### <mark style="color:blue;">**Concept**</mark>

The AWS Management Console is a web interface to access and manage the broad collection of service provided by Amazon Web Service (AWS).

<figure><img src="../../../.gitbook/assets/image (94).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">**Step 2**</mark>

1. On the General purpose buckets lab tab, click the bucket name that starts with website-bucket-.
2. The bucket name that starts with website-bucket- contains code required for this lab.
3. Go to the next step

#### <mark style="color:blue;">**Concept**</mark>&#x20;

Amazon Simple Storage Service(Amazon S3) is an object storage service that offers industry-leading scalability, data availability, security, and performance. Customers of all sizes and industries can use Amazon S3 to store and protect any amount of data for a range of use cases, such as data lakes, websites, mobile application, backup and restore, archive, enterprise applications, IoT devices, and big data analystics.

<figure><img src="../../../.gitbook/assets/image (96).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 3</mark>

1. On the Objects tab, review the objects in the bucket

* Five files should be displayed
* These files contain the contents of the static webpage
* Local files can be loaded into this S3 bucket by using the Upload button.

2. choose the check box to select text.html.
3. Click Actions to expand the dropdown menu
4. Choose Rename object
5. Go to the next step

#### <mark style="color:blue;">**Concept**</mark>

A bucket is a container for objects stored in Amazon S3. Every object is contained in a bucket. Amazon S3 offers a range of storage classes for the objects that you store. You choose a class depending on your use case scenario and performance access requirements. Amazon S3 provides storage classes for frequently accessed, infrequently accessedm and archive access objects.

<figure><img src="../../../.gitbook/assets/image (97).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 4</mark>

1. Fpr new object name, type: error.html

* This file contains the code for the error page, which opens whenever something goes wrong.

2. Click save changes.
3. Go to the next step

#### <mark style="color:blue;">**Concepts**</mark>

You can choose the geographical. AWS Region where Amazon S3 stores the buckets that you create. You might choose a Region to optimize latency, minimize costs, or address regulatory requirements. Objects stored in an AWS Region never leave the Region unless you explicitly transfer or replicate them to another Region. For example, objects stored in the Europe (ireland) Region never leave it. Howewer, Amazon S3 redundantly stores objects on multiple devices across a minimum of three Availability Zones in an AWS Region. An Availability Zones is one or more dicrete data centers with redundant power, networking, and connectivity in an AWS Region.

<figure><img src="../../../.gitbook/assets/image (98).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 5</mark>

1. In the success alert, review the message.
2. Click the Permissions tab.
3. Go to the next step

#### <mark style="color:blue;">**Concept**</mark>

Using Amazon S3, you can upload objects up to 5GB in size with a single PUT operation. For larget objects, up to 5TB in size, use the mutipart upload API.

<figure><img src="../../../.gitbook/assets/image (99).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 6</mark>

1. In the block public access(bucket settings) section, review to ensure that blick all public access is set to Off.

* Turning off "blick all public access" is necessary for static web hosting through your S3 bucket.

2. Scroll down to Bucket policy
3. Go to the step

#### <mark style="color:blue;">**Concept**</mark>

By default, all Amazon S3 resources(buckets, objects, and related subresources) are private. Only the resource owner can access them. The resource owner can optionally grant access permissions to others by writing an access policy.

<figure><img src="../../../.gitbook/assets/image (100).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 7</mark>

1. In the bucket policy editor window, review the policy

* This policy allows public access to the S3 bucket
* Effect says this policy will Allow acess.
* Principal defines who has access, In this case, \* represents anyone.
* Action defines what users can do to objects in the bucket. In this case, users can only retrieve data with GetObject.
* Resources specifiles that this policy applies to only this bucket.
* Generally, to safeguard against unintentional data exposure, we recommend strict S3 bucket permissions in production.
* Scroll up to the top of the page.
* Go to the next step

#### <mark style="color:blue;">**Concept**</mark>

You can grant permissions to your Amazon S3 resources through bucket policies and user policies. Both options use JSON-based access policy language. An Amazon Resource Name(ARN) uniquely identifies AWS resources.

```json
{
    "Version": "2012-10-17",
    "Id": "StaticWebPolicy",
    "Statement": [
        {
            "Sid": "S3GetObjectAllow",
            "Effect": "Allow",
            "Principal": "*",
            "Action": "s3:GetObject",
            "Resource": "arn:aws:s3:::website-bucket-1bf06570/*"
        }
    ]
}
```

***

### <mark style="color:purple;">Step 8</mark>

1. Click the Properties tab.
2. Go to the next step

#### <mark style="color:blue;">**Concept**</mark>

To hosta static website on Amazon S3, configure you bucket for static website hosting, set permissions, and add in index document, Available options include redirects, logging, and error documents.

<figure><img src="../../../.gitbook/assets/image (103).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 9</mark>

1. Scroll down to Static website hosting.
2. Click edit
3. Go to the next step

<figure><img src="../../../.gitbook/assets/image (104).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 10</mark>

1. For static website hosting, choose Enable.
2. For hosting type, choose host a static website
3. For index document, type: index.html
4. For error document, type: error.html
5. Go to the next step

#### <mark style="color:blue;">**Concept**</mark>

Amazon S3 supports virtual-hosted-style URL's and path-style URL's.

A virtual-hosted-style URL looks like: https://bucket-name.s3.Region.amazonaws.com/key

A path-style URL look like: https://s3.Region.amazonaws.com/bucket-name/keyname

<figure><img src="../../../.gitbook/assets/image (105).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 11</mark>

1. Scroll down to the bottom of the page.
2. Click Save changes
3. Go to the next step

***

### <mark style="color:purple;">Step 12</mark>

1. Croll down to static website hosting.
2. Review to ensure that hosting type is set to bucket hosting.
3. Under bucket website endpoint, click the copy icon to copy the provided endpoint.
4. Go to the next step

<figure><img src="../../../.gitbook/assets/image (106).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 13</mark>

1. To load the Beach Wave Conditions webpage, in a new browser tab(or window) address bar, paste the bucket website endpoint that you just copied, and then press Enter.
2. Go to next step

<figure><img src="../../../.gitbook/assets/image (107).png" alt=""><figcaption></figcaption></figure>

***

## DIY Activities

* [x] Rename index.html to waves.html

<figure><img src="../../../.gitbook/assets/image (17).png" alt=""><figcaption></figcaption></figure>

***

***
