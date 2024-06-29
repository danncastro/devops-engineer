# Escolha o serviço de armazenamento certo

***

## <mark style="color:red;">Quis de escolha de serviços</mark>

{% tabs %}
{% tab title="Pergunta 1" %}
<figure><img src="../../.gitbook/assets/image (48).png" alt=""><figcaption></figcaption></figure>

**Resposta:**

<figure><img src="../../.gitbook/assets/image (50).png" alt=""><figcaption></figcaption></figure>
{% endtab %}

{% tab title="Pergunta 2" %}
<figure><img src="../../.gitbook/assets/image (51).png" alt=""><figcaption></figcaption></figure>

**Resposta:**

<figure><img src="../../.gitbook/assets/image (53).png" alt=""><figcaption></figcaption></figure>
{% endtab %}

{% tab title="Pergunta 3" %}
<figure><img src="../../.gitbook/assets/image (54).png" alt=""><figcaption></figcaption></figure>

**Resposta:**

<figure><img src="../../.gitbook/assets/image (55).png" alt=""><figcaption></figcaption></figure>
{% endtab %}

{% tab title="Pergunta 4" %}
<figure><img src="../../.gitbook/assets/image (56).png" alt=""><figcaption></figcaption></figure>

**Resposta:**

<figure><img src="../../.gitbook/assets/image (57).png" alt=""><figcaption></figcaption></figure>
{% endtab %}
{% endtabs %}

***

### <mark style="color:red;">Armazenamento de instância do Amazon EC2</mark>

O armazenamento de instâncias no Amazon EC2 é um tipo de armazenamento de bloco temporário integrado ao servidor físico que hospeda a instância. Ele é ideal para armazenar dados que não precisam ser persistentes, como buffers, caches e dados temporários. Por estar diretamente ligado à instância EC2, é rápido e eficiente para operações que exigem baixa latência.

#### <mark style="color:blue;">**Casos de uso**</mark>

| Buffers e Caches                                                                                                                                      | Dados Scratch                                                                                                                                                      |
| ----------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| É utilizado para armazenar dados temporários que precisam ser acessados rapidamente pela aplicação, como buffers de rede ou caches de banco de dados. | Muitas aplicações geram dados temporários durante o processamento, como arquivos temporários ou logs temporários, que são armazenados neste tipo de armazenamento. |

#### <mark style="color:blue;">**Por que usar o armazenamento de instâncias**</mark>

Para necessidades de armazenamento de dados persistentes ou que requerem flexibilidade de gerenciamento, como redimensionamento de volume ou criação de snapshots, é recomendado usar o Amazon EBS (Elastic Block Store), que oferece esses recursos adicionais e pode ser separado do servidor EC2.

| Baixa Latência                                                                                                                                                                                                              | Eficiência de Custo                                                                                                                                                                                                                   | Desempenho                                                                                                                                                                                       |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Por estar diretamente conectado ao servidor físico da instância EC2, o armazenamento de instâncias oferece baixa latência para operações de leitura e gravação, o que é crucial para aplicações que exigem alto desempenho. | Como é integrado ao servidor EC2, não há custo adicional para armazenamento de instâncias além do custo da instância EC2 em si, o que pode ser uma vantagem para cargas de trabalho temporárias que não exigem persistência de dados. | É otimizado para casos de uso onde alta performance e baixa latência são fundamentais, garantindo que aplicações sensíveis ao desempenho possam executar operações de armazenamento rapidamente. |

***

### <mark style="color:red;">Amazon EBS</mark>

O Amazon EBS é projetado para armazenar dados que precisam persistir através de diferentes eventos, como paradas de instância, encerramentos ou falhas de hardware. Ele oferece dois tipos principais de volumes: **SSD** e **HDD**, cada um adequado para diferentes tipos de cargas de trabalho.

#### <mark style="color:blue;">**Tipos de volumes**</mark>

| SSD                                                                                                                     | HDD                                                                                                                                                           |
| ----------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Dependência de desempenho em IOPS (operações de entrada/saída por segundo).                                             | Dependência de desempenho em MB/s (taxa de transferência).                                                                                                    |
| Ideal para workloads transacionais, como bancos de dados e volumes de inicialização que requerem acesso rápido a dados. | Ideal para workloads com intensa necessidade de transferência de dados, como big data, data warehouses, processamento de logs e operações de E/S sequenciais. |

#### <mark style="color:blue;">**Recursos importantes do Amazon EBS**</mark>

{% tabs %}
{% tab title="Armazenamento em Bloco" %}
O Amazon EBS fornece armazenamento em bloco que pode ser provisionado e anexado a instâncias do EC2 conforme necessário.
{% endtab %}

{% tab title="Provisionamento Antecipado" %}
Você paga pelo armazenamento que provisiona, o que permite ajustar a capacidade conforme suas necessidades sem custos excessivos.
{% endtab %}

{% tab title="Replicação e Disponibilidade" %}
Os volumes do EBS são replicados automaticamente em múltiplos servidores dentro de uma única zona de disponibilidade, garantindo alta disponibilidade e durabilidade dos dados.
{% endtab %}

{% tab title="Limitação de Anexo" %}
Cada volume do EBS normalmente só pode ser anexado a uma instância do EC2 por vez, o que é importante considerar ao planejar arquiteturas de aplicativos distribuídos ou de alta disponibilidade.
{% endtab %}
{% endtabs %}

#### <mark style="color:blue;">**Casos de Uso**</mark>

| SSD                                                                                                                                               | HDD                                                                                                                                                           |
| ------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Recomendado para aplicações que exigem baixa latência e alto desempenho de IOPS, como bancos de dados transacionais ou servidores de aplicativos. | Ideal para cargas de trabalho que precisam processar grandes volumes de dados de forma eficiente, como análise de big data ou processamento de logs em lotes. |

Comparado a outros serviços de armazenamento na nuvem, o Amazon EBS destaca-se pela sua flexibilidade em termos de desempenho e tipos de volume, além da integração direta com instâncias do EC2 para uma arquitetura simplificada e escalável.

***

### <mark style="color:red;">Amazon S3</mark>

O Amazon S3 é uma solução de armazenamento altamente escalável e econômica, especialmente adequada para dados que não sofrem alterações frequentes. É ideal para uma variedade de casos de uso, como armazenamento de conteúdo estático da web, mídia, backups, arquivamento e dados para análise. Além disso, pode hospedar sites estáticos completos usando nomes de domínio personalizados.

#### <mark style="color:blue;">**Recursos principais do Amazon S3**</mark>

{% tabs %}
{% tab title="Armazenamento de Objetos" %}
O Amazon S3 armazena dados como objetos, cada um composto por dados, metadados e um identificador único (chave). Isso o torna adequado para armazenar grandes quantidades de dados não estruturados, como arquivos de mídia, documentos e backups.
{% endtab %}

{% tab title="Modelo de Pagamento Sob Demanda" %}
Você paga apenas pelo armazenamento e transferência de dados que utiliza, sem necessidade de provisionar antecipadamente capacidade de armazenamento. Isso proporciona flexibilidade para escalar de acordo com as necessidades de armazenamento.
{% endtab %}

{% tab title="Alta Disponibilidade e Durabilidade" %}
Os objetos armazenados no Amazon S3 são replicados automaticamente em várias zonas de disponibilidade dentro de uma região, garantindo alta disponibilidade e durabilidade dos dados.
{% endtab %}

{% tab title="Desacoplamento de Armazenamento e Computação" %}
Ao contrário do Amazon EBS, o Amazon S3 não está diretamente conectado às instâncias de computação (EC2). Isso permite separar o armazenamento dos dados da computação, facilitando arquiteturas distribuídas e escaláveis.
{% endtab %}
{% endtabs %}

#### <mark style="color:blue;">**Casos de Uso**</mark>

| Armazenamento de Mídia e Conteúdo Estático                                                                       | Backups e Arquivamento                                                                                                              | Análise de Dados                                                                                                                    |
| ---------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------- |
| Ideal para armazenar arquivos de áudio, vídeo, imagens e outros tipos de mídia que são acessados com frequência. | Perfeito para manter cópias de segurança de dados críticos ou arquivar dados que precisam ser retidos por longos períodos de tempo. | Usado para armazenar dados brutos ou agregados que são analisados por ferramentas de análise, como data lakes e pipelines de dados. |

Comparado a soluções de armazenamento em bloco como o Amazon EBS, o Amazon S3 se destaca pela sua economia, escalabilidade e flexibilidade para armazenar grandes volumes de dados não estruturados, com acesso seguro e eficiente através de APIs.

***

### <mark style="color:red;">Amazon Elastic File System (Amazon EFS) e Amazon FSx</mark>

Quando se trata de armazenamento de arquivos na AWS, especialmente se você precisa que o armazenamento possa ser acessado por várias instâncias do EC2, há duas opções principais: **Amazon Elastic File System (Amazon EFS)** e Amazon **FSx**.

#### <mark style="color:blue;">**Amazon Elastic File System (Amazon EFS)**</mark>

| Descrição                                                                                                                                                                        | Modelo de Pagamento                                                                                                                                     | Casos de Uso                                                                                                                                                                                                                                                             |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| É um sistema de arquivos NFS (Network File System) totalmente gerenciado que oferece escalabilidade automática e pode ser acessado por várias instâncias do EC2 simultaneamente. | Assim como o Amazon S3, você paga pelo armazenamento e transferência de dados que utiliza, sem a necessidade de provisionar capacidade antecipadamente. | <p>Ideal para aplicações que precisam compartilhar dados entre várias instâncias do EC2, como ambientes de desenvolvimento e produção, containers, e ambientes de análise de dados.<br><br><a href="https://aws.amazon.com/efs/faq/">Perguntas frequentes do EFS</a></p> |

#### <mark style="color:blue;">**Amazon FSx**</mark>

| Amazon FSx for Windows File Server                                                                                                                                                                                                                      | Amazon FSx for Lustre                                                                                                                                                                                                                                                      |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| É um servidor de arquivo gerenciado totalmente integrado ao Windows Server que suporta o protocolo SMB (Server Message Block), adequado para aplicações que exigem compatibilidade com sistemas Windows e necessitam de recursos como Active Directory. | É um sistema de arquivo Lustre totalmente gerenciado que se integra diretamente ao Amazon S3, otimizado para cargas de trabalho que exigem alto desempenho de I/O e acesso rápido a grandes volumes de dados, como computação de alto desempenho e processamento de dados. |
| [Perguntas frequentes do FSx for Windows File Server](https://aws.amazon.com/fsx/windows/faqs/?nc=sn\&loc=8)                                                                                                                                            | [Perguntas frequentes do FSx for Lustre](https://aws.amazon.com/fsx/lustre/faqs/?nc=sn\&loc=5)                                                                                                                                                                             |

#### <mark style="color:blue;">**Recursos Importantes do Amazon EFS e do Amazon FSx**</mark>

* Ambos são serviços de armazenamento de arquivos que permitem montagem em várias instâncias do EC2, facilitando o compartilhamento de dados entre ambientes distribuídos.
* O modelo de pagamento sob demanda permite escalabilidade e reduz o custo inicial, pois você paga apenas pelo que utiliza.
* Amazon EFS e Amazon FSx são projetados para diferentes tipos de cargas de trabalho e ambientes, oferecendo opções flexíveis dependendo dos requisitos específicos da aplicação.

#### <mark style="color:blue;">**Escolha do Serviço**</mark>

| Amazon EFS                                                                                                                                                                            | Amazon FSx                                                                                                                                                                                                                                             |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Ideal para cenários onde é necessário um sistema de arquivos compatível com NFS e que possa ser acessado por várias instâncias do EC2 simultaneamente, com escalabilidade automática. | Escolha o Amazon FSx for Windows File Server se você precisa de compatibilidade com o ambiente Windows e suporte ao protocolo SMB. Opte pelo Amazon FSx for Lustre se sua aplicação requer alto desempenho de I/O e integração direta com o Amazon S3. |

Comparado ao Amazon EBS, que é um armazenamento em bloco para uso exclusivo com instâncias do EC2, tanto o Amazon EFS quanto o Amazon FSx oferecem flexibilidade adicional para cenários onde o compartilhamento de arquivos entre várias instâncias é essencial.

***

## **Recursos**

[Armazenamento](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/Storage.html)

[Armazenamento em nuvem na AWS](https://aws.amazon.com/products/storage/)

[Amazon EFS: como funciona](https://docs.aws.amazon.com/efs/latest/ug/how-it-works.html)

[Amazon FSx for Windows File Server](https://aws.amazon.com/fsx/windows/)

[Amazon FSx for Lustre](https://aws.amazon.com/fsx/lustre/)

***
