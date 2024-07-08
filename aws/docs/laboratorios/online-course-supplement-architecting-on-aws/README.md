# Online Course Supplement: Architecting on AWS

***

## <mark style="color:red;">**Objetivos do laboratório**</mark>

Após a conclusão deste laboratório, você saberá como:

* Implantar uma rede virtual em várias Zonas de Disponibilidade em uma Região usando um modelo do CloudFormation fornecido.
* Implantar um banco de dados relacional altamente disponível e totalmente gerenciado nessas zonas de disponibilidade usando o Amazon RDS.
* Criar uma camada de cache de banco de dados usando o ElastiCache para consultas executadas com frequência para aprimorar o desempenho do tempo de resposta HTTP e reduzir a pressão sobre o banco de dados no qual foi criada uma instância na etapa anterior.
* Usar o Amazon EFS para provisionar uma camada de armazenamento compartilhada em várias Zonas de Disponibilidade para a camada de aplicativo, com tecnologia NFS.
* Criar um grupo de servidores da web que serão dimensionados automaticamente em resposta às variações de carga para concluir sua camada de aplicativo.

***

### <mark style="color:red;">**Resultado**</mark>

Você afirmará sua capacidade de projetar e criar um site altamente disponível na AWS. Para concluir esta tarefa, você vai:

* Resolver problemas de arquitetura reais usando o conhecimento do curso.
* Criar um site funcional na AWS com instruções mínimas.

***

### <mark style="color:red;">**Contexto**</mark>

A _Empresa de Exemplo_ cria campanhas de marketing para empresas de pequeno a médio porte. Até o momento, a Empresa de Exemplo hospeda os clientes usando um data center on-premises. Recentemente, eles decidiram migrar as operações para a nuvem para economizar e transformar os negócios com uma abordagem que prioriza a nuvem. Alguns membros da equipe têm experiência em nuvem e recomendaram os serviços de nuvem AWS para criar a solução. A Empresa de Exemplo contratou você para trabalhar com as equipes de engenharia para criar uma prova de conceito para os negócios.

A Empresa de Exemplo decidiu recriar o portal da web deles. Os clientes usam o portal para acessar as contas, criar planos de marketing e executar análises de dados em campanhas de marketing. Eles gostariam de ter um protótipo funcional em duas semanas.&#x20;

Você precisa criar uma arquitetura para dar suporte a este aplicativo. Sua solução precisa ser rápida, durável, dimensionável e mais econômica do que a infraestrutura on-premises existente. A empresa tem um gerente de projeto experiente que já criou um plano de projeto. Use o plano do projeto para:&#x20;

* (1) Obter adesão das equipes para seu projeto
* (2) Manter a empresa no caminho certo para entregar um protótipo funcional no tempo previsto.

***

### <mark style="color:red;">**Diagrama da arquitetura**</mark>

<figure><img src="../../.gitbook/assets/image (29).png" alt=""><figcaption></figcaption></figure>

{% tabs %}
{% tab title="1 - Amazon VPC" %}
Com a Amazon VPC, você pode executar os recursos da AWS em uma rede virtual definida por você. Essa rede virtual se assemelha a uma rede tradicional que você operaria no seu datacenter, com os benefícios de usar a infreaestrutura dimensionável e econômica da AWS
{% endtab %}

{% tab title="2 - ALB" %}
O Application Load Balancer distribui o tráfego de entrada do aplicativo por vários destinos em várias Zonas de Disponibilidade. Nesse caso, ele está distribuindo tráfego entre várias sub-redes de aplicativos. Isso aumenta a disponibilidade do seu aplicativo. Adicione um ou mais ouvintes ao seu balanceador de carga.
{% endtab %}

{% tab title="3 - Gateway NAT" %}
Um gateway NAT é um serviço NAT. Você pode usar um gateway NAT para que as instâncias em uma sub-red privada possam se conectar a serviços fora do sua VPC, mas os serviços externos não podem iniciar uma conexão com essas instãncias.
{% endtab %}

{% tab title="4 - Grupo do Auto Scaling" %}
Um grupo do Auto Scaling é um conjunto de instâncias do EC2 que são tratadas como um grupo lógico para fins de auto scaling e gerenciamento.
{% endtab %}
{% endtabs %}

{% tabs %}
{% tab title="5 - Pontos de montagem" %}
Os pontos de acesso do Amazon EFS (ou pontos de montagem) são pontos de entrada específicos do aplicativo em um sistema de arquivos EFS. Os pontos de montagem do EFS facilitam o gerenciamento do acesso de aplicativos a conjuntos de dados compartilhados. Os pontos de acesso podem impor informações de usuários e grupos. Você também pode configurar um diretório-raiz diferente para o sistema de arquivos para que os clientes possam acessar dados no diretório especificado ou nos subdiretórios.
{% endtab %}

{% tab title="6 - ElastiCache" %}
Com o Amazon ElastiCache, você pode configurar, executar e dimencionar armazenamentos de dados em memória populares de código aberto na nuvem. Crie aplicativos com uso intenso de dados ou aumente o desempenho de aplicativos existentes recuperando dados de armazenamentos de dados em memória com alta taxa de transferência e baixa latência**. "Memcached"** é um mecanismo de cache específico no serviço ElastiCache neste laboratório.
{% endtab %}

{% tab title="7 - Aurora" %}
O Aurora é um mecanismo de banco de dados relacional totalmente gerenciado que é compatível com o MySQL e o PostgreSQL. Esse serviço é executado na plataforma Amazon RDS.
{% endtab %}

{% tab title="8 - Amazon EFS" %}
O Amazon EFS oferece armazenamento de arquivos para suas instâncias do Amazon EC2. Com o Amazon EFS, você pode criar um sistema de arquivos, montar ele em instâncias do EC2 e depois ler e gravar dados de instância do EC2 de/para um sistema de arquivos.
{% endtab %}
{% endtabs %}

***

### <mark style="color:red;">**Tarefas do laboratório**</mark>

<figure><img src="../../.gitbook/assets/image (30).png" alt=""><figcaption></figcaption></figure>

***
