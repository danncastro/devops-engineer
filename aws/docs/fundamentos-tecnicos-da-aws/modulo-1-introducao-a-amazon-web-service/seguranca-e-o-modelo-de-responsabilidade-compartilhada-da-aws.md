---
description: >-
  Quando você trabalha com a Nuvem AWS, gerenciar a segurança e a conformidade é
  uma responsabilidade compartilhada entre a AWS e você.
---

# Segurança e o modelo de responsabilidade compartilhada da AWS

Para descrever essa responsabilidade compartilhada, a AWS criou o modelo de responsabilidade compartilhada. A distinção de responsabilidade é comumente chamada de segurança DA nuvem versus segurança NA nuvem.

<figure><img src="../../.gitbook/assets/image (2) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

***

## <mark style="color:red;">Responsabilidade da AWS</mark>

A **AWS** assume a **responsabilidade** pela **segurança da infraestrutura** da nuvem.

Isso inclui a **proteção** e garantia de:

* **Regiões** e **Zonas de Disponibilidade**.
* **Datacenters** onde os serviços são executados.

A responsabilidade da AWS abrange:

* **Segurança física** dos edifícios.
* **Gestão** dos componentes de **hardware**, **software** e **rede** necessários para operar os serviços.
* **Servidores físicos**, **sistemas operacionais de host**, **camadas de virtualização** e **componentes de rede**.

#### <mark style="color:blue;">**Níveis de Responsabilidade da AWS**</mark>

* O **nível de responsabilidade** da **AWS** varia conforme o **serviço oferecido**.
* A AWS classifica seus serviços em **três categorias principais**, cada uma com diferentes níveis de **responsabilidade compartilhada** entre a AWS e o **cliente**.

A tabela a seguir fornece informações sobre cada um, incluindo a responsabilidade da AWS.

<figure><img src="../../.gitbook/assets/image (3) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
**Observação:** os serviços de contêiner referem-se a contêineres de aplicação de abstração da AWS nos bastidores, e não aos serviços de contêiner do Docker. Isso permite que a AWS retire a responsabilidade de gerenciar a plataforma dos clientes.
{% endhint %}

***

## <mark style="color:red;">Responsabilidade do cliente</mark>

Os **clientes** têm **responsabilidades significativas** em relação à **segurança na nuvem** ao utilizar os serviços da **AWS**.

* É **essencial** configurar corretamente os **serviços** e **aplicações**.
* Garantir a **segurança dos dados** em conformidade com as **melhores práticas de segurança** é uma responsabilidade do cliente.

#### <mark style="color:blue;">**Variabilidade da Responsabilidade do Cliente**</mark>

* O **nível de responsabilidade** do **cliente** varia conforme o **serviço da AWS** utilizado.
* Em alguns casos, o cliente precisa:
  * **Realizar todas as configurações** e **gerenciamento de segurança** necessários.
* Em **serviços mais abstratos**, a responsabilidade do cliente pode se concentrar em:
  * **Gestão dos dados**.
  * **Controle de acesso** aos recursos.

Para ajudar a entender essas responsabilidades, a AWS classifica seus serviços em três categorias principais. Essas categorias permitem que você determine claramente o seu papel na segurança ao usar cada produto da AWS:

<figure><img src="../../.gitbook/assets/image (4) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

#### <mark style="color:blue;">**Garantindo a Segurança com Produtos da AWS**</mark>

Para garantir a **segurança adequada** ao usar produtos da **AWS**, os clientes precisam:

* Considerar cuidadosamente os **níveis de responsabilidade** exigidos para proteger cada serviço.
* Avaliar como o **modelo de segurança compartilhado** da AWS se alinha com:
  * **Padrões de segurança internos**.
  * **Leis e regulamentos** aplicáveis ao ambiente de TI da organização.

Responsabilidades do Cliente na Gestão da Segurança incluem alguns pontos essenciais :

#### <mark style="color:blue;">**Controle sobre os dados**</mark><mark style="color:blue;">:</mark>&#x20;

Clientes têm **controle total** sobre seus próprios dados e são responsáveis por gerenciar a **segurança** relacionada ao conteúdo armazenado na **AWS**.

#### <mark style="color:blue;">**Escolha da região**</mark>

Selecionar uma **região AWS** alinhada com os **regulamentos de soberania de dados** aplicáveis à organização.

#### <mark style="color:blue;">**Proteção de dados**</mark>

Implementar **mecanismos** como **criptografia** e **backups programados** para proteger os dados contra **acessos não autorizados** e **perda de informações**.

#### <mark style="color:blue;">**Controle de acesso**</mark>

Utilizar **controles de acesso** para restringir quem pode acessar seus dados e recursos, garantindo que apenas **pessoas autorizadas** possam realizar operações críticas.

#### <mark style="color:blue;">**Mitigação de Riscos**</mark><mark style="color:blue;">:</mark>

* Adotar essas **práticas de segurança** para **mitigar riscos** e fortalecer a **proteção dos dados** na nuvem.
* Garantir **conformidade com normas regulatórias** e manter a **integridade** e **confidencialidade** das informações críticas.

***

## <mark style="color:red;">Recursos</mark>

[Modelo de responsabilidade compartilhada](https://aws.amazon.com/compliance/shared-responsibility-model/)

***
