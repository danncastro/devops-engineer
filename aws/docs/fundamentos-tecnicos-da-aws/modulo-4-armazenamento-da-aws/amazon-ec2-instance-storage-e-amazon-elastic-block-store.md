# Amazon EC2 Instance Storage e Amazon Elastic Block Store

***

## <mark style="color:red;">**Armazenamento de instância do Amazon EC2**</mark>

O armazenamento de instância do Amazon EC2 oferece armazenamento temporário no nível de bloco, localizado em discos fisicamente anexados ao host da instância. Esse armazenamento é estreitamente vinculado ao ciclo de vida da instância do EC2: quando a instância é excluída, o armazenamento também é. Por isso, é considerado um **armazenamento temporário.**

Leia mais sobre isso na [documentação da AWS(opens in a new tab)](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/InstanceStorage.html).

#### <mark style="color:blue;">**Características do Armazenamento de Instância**</mark>

| Localização Física                                                        | Ciclo de Vida                                                     | Velocidade                                                               |
| ------------------------------------------------------------------------- | ----------------------------------------------------------------- | ------------------------------------------------------------------------ |
| Os discos de armazenamento estão fisicamente anexados ao computador host. | O armazenamento é excluído quando a instância do EC2 é encerrada. | Oferece alta performance devido à proximidade física dos discos ao host. |

#### <mark style="color:blue;">**Casos de Uso Ideais**</mark>

| Replicação de Dados                                                                                                                                                                                           | Armazenamento Temporário                                                                                                                                                                                                 |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| <mark style="color:purple;">**Clusters do Hadoop**</mark><mark style="color:purple;">:</mark> Ideal para aplicações que replicam dados para outras instâncias, proporcionando alta performance e resiliência. | <mark style="color:purple;">**Buffers e Caches**</mark><mark style="color:purple;">:</mark> Armazenamento rápido para dados que são alterados frequentemente.                                                            |
| <mark style="color:purple;">**Workloads Baseadas em Cluster**</mark><mark style="color:purple;">:</mark> A velocidade dos volumes conectados localmente é benéfica para a distribuição rápida de dados.       | <mark style="color:purple;">**Dados Transitórios**</mark><mark style="color:purple;">:</mark> Informações temporárias que não precisam ser persistentes.                                                                 |
|                                                                                                                                                                                                               | <mark style="color:purple;">**Conteúdo Temporário**</mark><mark style="color:purple;">:</mark> Ideal para armazenar dados que são constantemente modificados e não precisam ser mantidos após a instância ser encerrada. |

#### <mark style="color:blue;">**Benefícios do Armazenamento de Instância**</mark>

| Alta Performance                                                  | Eficiência                                                           | Resiliência                                                                                                                            |
| ----------------------------------------------------------------- | -------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------- |
| A proximidade dos discos ao host oferece acesso rápido aos dados. | Excelente para tarefas que exigem armazenamento rápido e temporário. | Quando usado em conjunto com outras instâncias para replicação de dados, proporciona uma distribuição de dados eficiente e resiliente. |

O armazenamento de instância do Amazon EC2 é uma solução potente para aplicações que requerem armazenamento temporário de alta velocidade, oferecendo uma combinação de performance e eficiência para dados transitórios e replicáveis.

***

## <mark style="color:red;">**Amazon Elastic Block Storage (Amazon EBS)**</mark>

O Amazon Elastic Block Store (Amazon EBS) é um serviço de armazenamento em nível de bloco que pode ser anexado a instâncias do Amazon EC2. Esses dispositivos de armazenamento são conhecidos como volumes do Amazon EBS, que funcionam de maneira similar a unidades externas conectadas a um laptop. Aqui estão os pontos principais sobre o Amazon EBS:

#### <mark style="color:blue;">**Características dos Volumes do Amazon EBS**</mark>

| Armazenamento em Bloco                                                                                                              | Conexão a Instâncias EC2                                                                                                                                                    | Persistência de Dados                                                                                                          |
| ----------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------ |
| Os volumes do EBS são dispositivos de armazenamento em bloco, permitindo a criação de unidades de tamanho configurado pelo usuário. | A maioria dos volumes pode ser conectada a apenas uma instância do EC2 por vez, mas pode ser desconectada e reconectada a outra instância na mesma zona de disponibilidade. | Os dados em um volume do EBS são preservados independentemente da instância EC2, proporcionando resiliência em caso de falhas. |

#### <mark style="color:blue;">**Multiconexão de Volumes**</mark>

* **Multiconexão**: Recentemente, a AWS introduziu a capacidade de conectar um volume do EBS a várias instâncias EC2 simultaneamente. Esse recurso é limitado a tipos específicos de instância e todas as instâncias devem estar na mesma zona de disponibilidade.

#### <mark style="color:blue;">**Comparação com Unidades Externas**</mark>

| Unidade Externa                                                                                                                                             | Limitações de Tamanho                                                                                                                                                             |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Assim como uma unidade externa, os volumes do EBS são separados da instância EC2. Se a instância EC2 falhar, os dados no volume do EBS permanecem intactos. | Tal como as unidades externas, os volumes do EBS têm limites de tamanho. Por exemplo, um volume pode ter uma capacidade máxima específica, similar a uma unidade externa de 2 TB. |

#### <mark style="color:blue;">**Benefícios do Amazon EBS**</mark>

| Flexibilidade                                                                                                             | Backup e Recuperação                                                     | Desempenho                                                                           |
| ------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------ | ------------------------------------------------------------------------------------ |
| Os volumes do EBS podem ser redimensionados conforme necessário, proporcionando flexibilidade na gestão do armazenamento. | É possível criar snapshots dos volumes para backup e recuperação rápida. | Oferece alto desempenho para aplicações que exigem armazenamento rápido e confiável. |

#### <mark style="color:blue;">**Casos de Uso Comuns**</mark>

| Aplicações Corporativas                                                                                                        | Backup e Recuperação                                                                       | Escalabilidade                                                                           |
| ------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------ | ---------------------------------------------------------------------------------------- |
| Ideal para bancos de dados, sistemas de ERP e outras aplicações que exigem armazenamento de alta performance e baixa latência. | Perfeito para cenários que necessitam de recuperação rápida de dados através de snapshots. | Útil para aplicações que precisam ajustar o tamanho do armazenamento conforme a demanda. |

O Amazon EBS fornece uma solução robusta e flexível para armazenamento em nível de bloco, permitindo que os volumes sejam facilmente gerenciados, redimensionados e conectados a instâncias do EC2. Com a introdução do recurso de multiconexão, o EBS se tornou ainda mais versátil, atendendo a uma ampla gama de necessidades de armazenamento para aplicações modernas.

***

### <mark style="color:red;">Escalar volumes do Amazon EBS</mark>

O Amazon Elastic Block Store (Amazon EBS) oferece duas maneiras principais de dimensionar os volumes de armazenamento para atender às necessidades de sua aplicação:

| Aumentar o Tamanho do Volume                                                                                                                                                                                                                                        | Anexar Múltiplos Volumes                                                                                                                                                                                                                                                                                                                                                                                        |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Você pode aumentar o tamanho de um volume existente do Amazon EBS, desde que não ultrapasse o limite máximo de 16 TB. Por exemplo, se você começar com um volume de 5 TB, pode aumentar gradualmente até 16 TB conforme suas necessidades de armazenamento crescem. | Além de aumentar o tamanho de um volume individual, você pode anexar múltiplos volumes a uma única instância do Amazon EC2. Isso permite que uma instância EC2 tenha uma relação de um para muitos com volumes do EBS. Esses volumes adicionais podem ser anexados durante ou após a criação da instância do EC2, proporcionando flexibilidade para expandir a capacidade de armazenamento conforme necessário. |

#### <mark style="color:blue;">Benefícios de Dimensionamento dos Volumes do EBS</mark>

| Flexibilidade                                                                                                                                                                                                                                                                        | Facilidade de Gerenciamento                                                                                                                                                                                                             |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <mark style="color:purple;">**Ajuste Dinâmico**</mark><mark style="color:purple;">:</mark> A capacidade de aumentar o tamanho do volume ou anexar volumes adicionais permite que você ajuste dinamicamente a capacidade de armazenamento sem interrupção significativa dos serviços. | <mark style="color:purple;">**Snapshots e Backups**</mark><mark style="color:purple;">:</mark> Aumentar volumes e adicionar novos volumes pode ser feito sem perda de dados, e os snapshots podem ser usados para backup e recuperação. |
| <mark style="color:purple;">**Escalabilidade Vertical e Horizontal**</mark><mark style="color:purple;">:</mark> Aumentar o tamanho do volume é uma forma de escalabilidade vertical, enquanto adicionar múltiplos volumes representa escalabilidade horizontal.                      | <mark style="color:purple;">**Desempenho Melhorado**</mark><mark style="color:purple;">:</mark> Distribuir dados em múltiplos volumes pode melhorar o desempenho, especialmente para aplicações de alta demanda de I/O.                 |

#### <mark style="color:blue;">Exemplos de Uso</mark>

| Bancos de Dados                                                                                                     | Armazenamento de Arquivos                                                                                                                                    | Aplicações de Big Data                                                                                           |
| ------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------------------------------------------------------------------------------------------------------------- |
| Bancos de dados que crescem rapidamente podem se beneficiar da capacidade de aumentar o tamanho dos volumes do EBS. | Aplicações que armazenam uma grande quantidade de arquivos podem anexar múltiplos volumes para distribuir a carga de armazenamento e melhorar a performance. | Workloads de Big Data podem utilizar múltiplos volumes para armazenar grandes quantidades de dados distribuídos. |

Escalar volumes do Amazon EBS proporciona flexibilidade e eficiência na gestão de armazenamento em nuvem. A capacidade de aumentar o tamanho do volume e anexar múltiplos volumes a uma única instância do EC2 permite que você adapte facilmente a capacidade de armazenamento às necessidades específicas da sua aplicação, garantindo desempenho e disponibilidade.

***

### <mark style="color:red;">Casos de uso do Amazon EBS</mark>

O Amazon Elastic Block Store (Amazon EBS) é altamente valioso quando há a necessidade de recuperação rápida de dados e persistência de dados a longo prazo.

&#x20;Aqui estão alguns cenários comuns onde o Amazon EBS é amplamente utilizado:

#### <mark style="color:blue;">**1. Sistemas Operacionais**</mark>

| Volumes de Inicialização/Raiz                                                                                                                                                                                                                                            | Boot Volumes                                                                                                                                                   |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| O EBS é frequentemente usado para armazenar sistemas operacionais. O dispositivo raiz de uma instância, executado por meio de uma imagem de máquina da Amazon (AMI), geralmente é um volume do Amazon EBS. Essas instâncias são conhecidas como AMIs com suporte de EBS. | Proporciona um ambiente confiável e persistente para a inicialização de instâncias, garantindo que os dados do sistema operacional estejam sempre disponíveis. |

#### <mark style="color:blue;">**2. Bancos de Dados**</mark>

| Camada de Armazenamento                                                                                                     | Desempenho Consistente                                                                              | Snapshots                                                                                          |
| --------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------- |
| O EBS é ideal para bancos de dados em execução no Amazon EC2 que dependem de leituras e gravações transacionais frequentes. | O EBS oferece desempenho consistente e baixa latência, essenciais para operações de banco de dados. | Permite criar snapshots regulares dos volumes de bancos de dados para backup e recuperação rápida. |

#### <mark style="color:blue;">**3. Aplicações Corporativas**</mark>

| Armazenamento Confiável                                                                                                                       | Backup e Recuperação                                                                                                                                   |
| --------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Fornece uma camada de armazenamento confiável para aplicações críticas de negócios, garantindo alta disponibilidade e durabilidade dos dados. | As capacidades de snapshot do EBS permitem que empresas realizem backups frequentes e restaurem dados rapidamente, minimizando o tempo de inatividade. |

#### <mark style="color:blue;">**4. Aplicações com Alta Taxa de Transferência**</mark>

| Leituras e Gravações Contínuas                                                                                                       | Desempenho de I/O                                                                                                                    | Armazenamento Escalável                                                                                             |
| ------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------- |
| Ideal para aplicações que realizam leituras e gravações longas e contínuas, como sistemas de processamento de dados em larga escala. | O EBS pode ser otimizado para diferentes tipos de desempenho de I/O, adequando-se às necessidades de aplicações intensivas em dados. | Permite escalabilidade horizontal e vertical, atendendo a crescentes volumes de dados sem comprometer o desempenho. |

#### <mark style="color:blue;">Benefícios do Amazon EBS</mark>

| Persistência de Dados                                                                                             | Alta Disponibilidade                                                                                                                              | Gerenciamento de Volumes:                                                                                        |
| ----------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------- |
| Dados armazenados no EBS persistem além do ciclo de vida da instância EC2, oferecendo durabilidade a longo prazo. | Projetado para alta disponibilidade e replicação automática dentro da zona de disponibilidade, garantindo que os dados estejam sempre acessíveis. | Facilita a gestão de volumes, incluindo redimensionamento e snapshots, proporcionando flexibilidade e segurança. |

O Amazon EBS é uma solução de armazenamento em bloco versátil e robusta, ideal para uma variedade de aplicações que exigem recuperação rápida de dados e persistência a longo prazo. Desde volumes de inicialização para sistemas operacionais até armazenamento confiável para bancos de dados e aplicações corporativas, o EBS fornece a base necessária para operações de alta performance e escalabilidade na nuvem.

***

### <mark style="color:red;">Tipos de volume do Amazon EBS</mark>

Os volumes do Amazon Elastic Block Store (EBS) são categorizados em duas principais tecnologias de armazenamento: **unidades de estado sólido (SSDs)** e **unidades de disco rígido (HDDs).** Cada categoria é projetada para diferentes tipos de workloads, com diferentes características de desempenho e custo. A seguir estão os tipos de volumes do EBS oferecidos pela AWS e seus principais casos de uso:

<details>

<summary><mark style="color:purple;">SSD IOPS Provisionadas do EBS (io1/io2)</mark></summary>

**Descrição**: SSDs com a mais alta performance, projetados para workloads transacionais sensíveis à latência.

**Casos de Uso**: Bancos de dados NoSQL e relacionais com intensa entrada/saída (E/S).

**Tamanho do Volume**: 4 GB a 16 TB.

**IOPS Máx**: 64.000.

**Taxa de Transferência Máxima**: 1.000 MB/s.

</details>

<details>

<summary><mark style="color:purple;">SSD de Uso Geral do EBS (gp2/gp3)</mark></summary>

**Descrição**: SSD de uso geral que equilibra preço e performance para diversas workloads transacionais.

**Casos de Uso**: Volumes de boot, aplicações interativas de baixa latência, desenvolvimento e teste.

**Tamanho do Volume**: 1 GB a 16 TB.

**IOPS Máx**: 16.000.

**Taxa de Transferência Máxima**: 250 MB/s.

</details>

<details>

<summary><mark style="color:purple;">HDD com Taxa de Transferência Otimizada do EBS (st1)</mark></summary>

**Descrição**: HDD de baixo custo projetado para workloads com alta taxa de transferência e acesso frequente.

**Casos de Uso**: Big data, data warehouses, processamento de log.

**Tamanho do Volume**: 500 GB a 16 TB.

**IOPS Máx**: 500.

**Taxa de Transferência Máxima**: 500 MB/s.

</details>

<details>

<summary><mark style="color:purple;">HDD Frio do EBS (sc1)</mark></summary>

**Descrição**: HDD de baixo custo projetado para workloads acessadas com menos frequência.

**Casos de Uso**: Dados menos acessados que precisam de menos varreduras por dia.

**Tamanho do Volume**: 500 GB a 16 TB.

**IOPS Máx**: 250.

**Taxa de Transferência Máxima**: 250 MB/s.

</details>

#### <mark style="color:blue;">Gráfico de Comparação</mark>

<figure><img src="../../.gitbook/assets/image (43).png" alt=""><figcaption></figcaption></figure>

#### <mark style="color:blue;">Escolhendo o Volume Certo</mark>

| SSD IOPS Provisionadas (io1/io2)                                                                                                | SSD de Uso Geral (gp2/gp3)                                                                                         | HDD com Taxa de Transferência Otimizada (st1)                                                                | HDD Frio (sc1)                                                                                      |
| ------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------ | --------------------------------------------------------------------------------------------------- |
| Escolha este tipo de volume para aplicações que requerem alta performance e baixa latência, como bancos de dados transacionais. | Ideal para uma ampla gama de workloads, incluindo volumes de inicialização e ambientes de desenvolvimento e teste. | Adequado para workloads que necessitam de alta taxa de transferência, como processamento de big data e logs. | Melhor para dados que são acessados com menos frequência e não requerem alta taxa de transferência. |

Escolher o tipo de volume do EBS certo é crucial para otimizar o desempenho e o custo da sua infraestrutura na AWS.

***

### <mark style="color:red;">Benefícios do Amazon EBS</mark>

O Amazon Elastic Block Store (EBS) oferece uma série de benefícios que o tornam uma escolha robusta para armazenamento de dados na nuvem. Aqui estão os principais benefícios:

{% tabs %}
{% tab title="Alta Disponibilidade" %}
<mark style="color:purple;">**Descrição**</mark><mark style="color:purple;">:</mark> Quando você cria um volume do EBS, ele é replicado automaticamente em sua zona de disponibilidade para evitar a perda de dados de pontos únicos de falha.

<mark style="color:green;">**Benefício**</mark><mark style="color:green;">:</mark> Garante que seus dados sejam resilientes a falhas de hardware e que estejam disponíveis mesmo em cenários de indisponibilidade de uma instância.
{% endtab %}

{% tab title="Persistência de Dados" %}
<mark style="color:purple;">**Descrição**</mark><mark style="color:purple;">:</mark> O armazenamento no EBS persiste mesmo quando a instância associada é desligada ou terminada.

<mark style="color:green;">**Benefício**</mark><mark style="color:green;">:</mark> Permite que você armazene dados de forma durável e acesse-os posteriormente, mesmo após reinicializações ou falhas de instâncias.
{% endtab %}

{% tab title="Criptografia de Dados" %}
<mark style="color:purple;">**Descrição**</mark><mark style="color:purple;">:</mark> Todos os volumes do EBS oferecem suporte a criptografia para proteger seus dados em repouso.

<mark style="color:green;">**Benefício**</mark><mark style="color:green;">:</mark> Garante a segurança dos dados sensíveis, atendendo a requisitos de conformidade e regulamentações de segurança.
{% endtab %}

{% tab title="Flexibilidade" %}
<mark style="color:purple;">**Descrição**</mark><mark style="color:purple;">:</mark> Os volumes do EBS oferecem suporte a alterações instantâneas, como modificar o tipo de volume, o tamanho do volume e a capacidade das operações de IOPS sem interromper a instância.

<mark style="color:green;">**Benefício**</mark><mark style="color:green;">:</mark> Facilita ajustes dinâmicos de capacidade e desempenho, permitindo otimizar recursos conforme as necessidades de carga de trabalho mudam ao longo do tempo.
{% endtab %}

{% tab title=" Backups" %}
<mark style="color:purple;">**Descrição**</mark><mark style="color:purple;">:</mark> O Amazon EBS permite criar backups (snapshots) dos volumes do EBS de forma simples e eficiente.

<mark style="color:green;">**Benefício**</mark><mark style="color:green;">:</mark> Facilita a proteção contra perda de dados acidental ou intencional, além de fornecer um ponto de recuperação confiável para restauração de dados.
{% endtab %}
{% endtabs %}

O Amazon EBS oferece não apenas armazenamento escalável e durável na nuvem, mas também uma série de benefícios que aumentam a resiliência, segurança e flexibilidade das suas aplicações e dados na AWS. Esses recursos são projetados para atender tanto às necessidades operacionais quanto aos requisitos de conformidade, permitindo que você gerencie seu armazenamento de forma eficiente e segura.

***

### <mark style="color:red;">Snapshots do Amazon EBS</mark>

Os snapshots do Amazon EBS são uma ferramenta poderosa para fazer backups e criar novos volumes na AWS. Aqui estão os detalhes sobre como eles funcionam e seus benefícios:

#### <mark style="color:blue;">**Funcionamento dos Snapshots**</mark>

| Backup Incremental:                                                                                                                                                                                                                                                | Redundância e Armazenamento no Amazon S3:                                                                                                                                                                                                                        | Gerenciamento Simples:                                                                                                                                                                                                                       |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <mark style="color:purple;">**Descrição**</mark><mark style="color:purple;">:</mark> Os snapshots do EBS são backups incrementais, o que significa que eles capturam apenas os blocos de dados que foram modificados desde o último snapshot.                      | <mark style="color:purple;">**Descrição**</mark><mark style="color:purple;">:</mark> Os snapshots do EBS são armazenados de forma redundante em várias zonas de disponibilidade usando o Amazon S3.                                                              | <mark style="color:purple;">**Descrição**</mark><mark style="color:purple;">:</mark> Os snapshots do EBS são gerenciados através do console do Amazon EBS, que faz parte do console do Amazon EC2.                                           |
| <mark style="color:green;">**Benefício**</mark><mark style="color:green;">:</mark> Isso economiza espaço de armazenamento, já que apenas os blocos alterados são armazenados no Amazon S3, enquanto blocos não modificados são referenciados do snapshot anterior. | <mark style="color:green;">**Benefício**</mark><mark style="color:green;">:</mark> Garante alta durabilidade e disponibilidade dos backups. A AWS gerencia automaticamente a replicação e a redundância no Amazon S3, sem necessidade de intervenção do usuário. | <mark style="color:green;">**Benefício**</mark><mark style="color:green;">:</mark> Facilita a criação, cópia, restauração e exclusão de snapshots de maneira intuitiva e direta, sem a necessidade de interagir diretamente com o Amazon S3. |

#### <mark style="color:blue;">**Utilizações dos Snapshots**</mark>

| Restauração de Volumes                                                                                                                                                                                                                  | Criação de Novos Volumes                                                                                                                                                                                                        | Clonagem e Testes                                                                                                                                                                                          |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <mark style="color:purple;">**Descrição**</mark><mark style="color:purple;">:</mark> Você pode usar snapshots para restaurar volumes do EBS a partir de backups anteriores, permitindo recuperação de dados em caso de falhas ou erros. | <mark style="color:purple;">**Descrição**</mark><mark style="color:purple;">:</mark> Ao criar um novo volume a partir de um snapshot, você obtém uma cópia exata do volume original no momento em que o snapshot foi tirado.    | <mark style="color:purple;">**Descrição**</mark><mark style="color:purple;">:</mark> Snapshots permitem clonar ambientes e realizar testes em cópias idênticas dos volumes originais.                      |
|                                                                                                                                                                                                                                         | <mark style="color:green;">**Benefício**</mark><mark style="color:green;">:</mark> Útil para replicação de ambientes de produção, desenvolvimento e teste, e para criação de backups adicionais sem impactar o volume original. | <mark style="color:green;">**Benefício**</mark><mark style="color:green;">:</mark> Facilita o desenvolvimento e a validação de mudanças em ambientes seguros, sem risco de comprometer os dados originais. |

Os snapshots do Amazon EBS são uma parte essencial da estratégia de backup na AWS, proporcionando não apenas segurança e durabilidade, mas também flexibilidade para gerenciar e expandir sua infraestrutura de armazenamento de forma eficiente. Utilize-os para garantir a integridade e disponibilidade contínua dos seus dados na nuvem AWS.

***

## <mark style="color:red;">**Recursos**</mark>

[Amazon Elastic Block Store (Amazon EBS)(opens in a new tab)](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/AmazonEBS.html)

[Perguntas frequentes sobre o Amazon EBS](https://aws.amazon.com/ebs/faqs/)

***
