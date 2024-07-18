---
description: >-
  Quando você trabalha com a Nuvem AWS, gerenciar a segurança e a conformidade é
  uma responsabilidade compartilhada entre a AWS e você.
---

# Segurança e o modelo de responsabilidade compartilhada da AWS

Para descrever essa responsabilidade compartilhada, a AWS criou o modelo de responsabilidade compartilhada. A distinção de responsabilidade é comumente chamada de segurança DA nuvem versus segurança NA nuvem.

<figure><img src="../../.gitbook/assets/image (2) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

***

## <mark style="color:red;">Responsabilidade da AWS</mark>

A AWS assume a responsabilidade pela segurança da infraestrutura da nuvem, o que inclui proteger e garantir desde as regiões e zonas de disponibilidade até os datacenters onde os serviços são executados. Isso abrange a segurança física dos edifícios, bem como a gestão dos componentes de hardware, software e rede necessários para operar os serviços da AWS, como servidores físicos, sistemas operacionais de host, camadas de virtualização e componentes de rede.

O nível de responsabilidade da AWS varia conforme o serviço oferecido. A AWS classifica seus serviços em três categorias principais, cada uma com diferentes níveis de responsabilidade compartilhada entre a AWS e o cliente.

A tabela a seguir fornece informações sobre cada um, incluindo a responsabilidade da AWS.

<figure><img src="../../.gitbook/assets/image (3) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
**Observação:** os serviços de contêiner referem-se a contêineres de aplicação de abstração da AWS nos bastidores, e não aos serviços de contêiner do Docker. Isso permite que a AWS retire a responsabilidade de gerenciar a plataforma dos clientes.
{% endhint %}

***

## <mark style="color:red;">Responsabilidade do cliente</mark>

Os clientes têm responsabilidades significativas em relação à segurança na nuvem ao utilizar os serviços da AWS. É essencial configurar corretamente os serviços e aplicações, garantindo a segurança dos dados em conformidade com as melhores práticas de segurança.

O nível de responsabilidade do cliente varia conforme o serviço da AWS utilizado. Em alguns casos, você precisa realizar todas as configurações e gerenciamento de segurança necessários. Em serviços mais abstratos, sua responsabilidade pode se concentrar principalmente na gestão dos dados e no controle de acesso aos recursos.

Para ajudar a entender essas responsabilidades, a AWS classifica seus serviços em três categorias principais. Essas categorias permitem que você determine claramente o seu papel na segurança ao usar cada produto da AWS:

<figure><img src="../../.gitbook/assets/image (4) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

Para garantir a segurança adequada ao usar produtos da AWS, os clientes precisam considerar cuidadosamente os níveis de responsabilidade exigidos para proteger cada serviço. Isso envolve avaliar como o modelo de segurança compartilhado da AWS se alinha com os padrões de segurança internos e com as leis e regulamentos aplicáveis ao ambiente de TI da organização.

É crucial entender que os clientes têm controle total sobre seus próprios dados e são responsáveis por gerenciar a segurança relacionada ao conteúdo armazenado na AWS. Alguns pontos essenciais incluem:

#### <mark style="color:blue;">**Escolha da região**</mark>

Selecionar uma região AWS que esteja alinhada com os regulamentos de soberania de dados aplicáveis à organização.

#### <mark style="color:blue;">**Proteção de dados**</mark>

Implementar mecanismos como criptografia e backups programados para proteger os dados armazenados na AWS contra acessos não autorizados e perda de informações.

#### <mark style="color:blue;">**Controle de acesso**</mark>

Utilizar controles de acesso para restringir quem pode acessar seus dados e recursos na AWS, garantindo que apenas as pessoas autorizadas tenham permissão para realizar operações críticas.

Ao adotar essas práticas de segurança, os clientes podem mitigar riscos e fortalecer a proteção de seus dados e recursos na nuvem, garantindo conformidade com normas regulatórias e mantendo a integridade e a confidencialidade das informações críticas.

***

## <mark style="color:red;">Recursos</mark>

[Modelo de responsabilidade compartilhada](https://aws.amazon.com/compliance/shared-responsibility-model/)

***
