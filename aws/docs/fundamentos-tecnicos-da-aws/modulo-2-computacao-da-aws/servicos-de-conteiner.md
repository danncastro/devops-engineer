---
description: >-
  A AWS oferece uma variedade de opções de computação para atender diversas
  necessidades, sendo as principais categorias máquinas virtuais (VMs),
  contêineres e computação sem servidor.
---

# Serviços de contêiner

Cada uma dessas categorias tem suas próprias características e benefícios, permitindo escolher a ferramenta certa para cada tarefa específica.

Os contêineres são uma forma de virtualização leve que permite executar aplicações de forma isolada, porém compartilhando recursos do sistema operacional hospedeiro. Eles são adequados para uma ampla gama de workloads, como aplicações web, migrações de sistemas (**"lift and shift"**), aplicações distribuídas e simplificação de ambientes de desenvolvimento, teste e produção.

Ao optar por contêineres, você ganha flexibilidade na implantação e na gestão de aplicações, já que eles encapsulam todas as dependências da aplicação em um pacote padronizado. Isso facilita a escalabilidade horizontal, permitindo que você implante várias instâncias dos mesmos contêineres para lidar com aumentos de carga de trabalho, por exemplo.

Além disso, contêineres oferecem um ambiente consistente de desenvolvimento para equipes, garantindo que as aplicações funcionem da mesma forma em diferentes estágios do ciclo de vida do software, desde o desenvolvimento até a produção.

Entender as características e os benefícios dos contêineres ajuda na construção de uma arquitetura de nuvem eficiente e adequada para suas necessidades específicas de aplicação e infraestrutura.

***

## <mark style="color:red;">Contêineres</mark>

Embora os contêineres sejam frequentemente vistos como uma tecnologia recente, sua origem remonta aos anos 70, quando certos kernels Linux começaram a demonstrar capacidades de isolamento de processos. Inicialmente, essa funcionalidade exigia configuração manual, o que tornava as operações complexas.

Com o avanço da comunidade de software de código aberto, os contêineres evoluíram significativamente. Hoje, eles são uma solução para desafios tradicionais de computação, como garantir que o software seja executado de maneira confiável ao migrar entre diferentes ambientes computacionais.

Um contêiner é uma unidade padronizada que encapsula seu código juntamente com suas dependências. Esse pacote é projetado para ser executado de maneira consistente e confiável em qualquer plataforma, pois cada contêiner cria um ambiente isolado e independente. Com os contêineres, workloads podem ser facilmente transportadas de um ambiente para outro, seja do desenvolvimento para produção ou da infraestrutura local para a nuvem.

Essa capacidade de portabilidade e isolamento faz dos contêineres uma escolha popular para ambientes de desenvolvimento ágeis, bem como para aplicações que necessitam de escalabilidade e consistência operacional em diferentes cenários de implementação.

***

## <mark style="color:red;">Docker</mark>

Quando se fala em contêineres, é comum associar a tecnologia ao Docker. O Docker é um popular tempo de execução de contêineres que simplifica o gerenciamento de toda a pilha de sistemas operacionais necessária para o isolamento de contêineres, incluindo rede e armazenamento. Ele oferece aos usuários uma plataforma para criar, empacotar, implantar e executar contêineres de maneira eficiente.

O Docker se destaca por sua abordagem simplificada para a criação de ambientes isolados, o que é essencial para a execução confiável de aplicações em diferentes ambientes de computação. Sua popularidade decorre da facilidade de uso e da padronização que oferece aos desenvolvedores e operadores de sistemas, permitindo que eles construam e distribuam aplicações de forma consistente e escalável utilizando contêineres.

***

## <mark style="color:red;">Qual é a diferença entre contêineres e máquinas virtuais (VMs)?</mark>

As máquinas virtuais compartilham o mesmo sistema operacional e kernel do host em que estão executando, enquanto cada máquina virtual contém seu próprio sistema operacional completo. Isso significa que cada máquina virtual precisa manter uma cópia separada do sistema operacional, o que pode resultar em algum desperdício de espaço.

Em contraste, os contêineres são mais leves. Eles inicializam mais rapidamente, quase instantaneamente, em comparação com as máquinas virtuais. Essa diferença no tempo de inicialização é crucial ao projetar aplicações que precisam ser escaladas rapidamente em momentos de picos de carga, como interrupções de entrada e saída (E/S).

Embora os contêineres ofereçam inicialização rápida e eficiência, as máquinas virtuais proporcionam todo o poder de um sistema operacional completo e podem oferecer recursos como a capacidade de instalar diferentes pacotes de software, ter kernels dedicados e outras funcionalidades mais robustas.

***

## <mark style="color:red;">Orquestrar contêineres</mark>

Na AWS, quando você executa contêineres em instâncias do EC2, é essencial entender como gerenciar sua computação em grande escala. Aqui estão os principais pontos a considerar:

#### <mark style="color:blue;">**Colocação de Contêineres em Instâncias**</mark>

Você precisa decidir como distribuir e gerenciar seus contêineres em suas instâncias do EC2. Isso pode incluir estratégias de balanceamento de carga e agrupamento de contêineres em uma mesma instância para otimização de recursos.

#### <mark style="color:blue;">**Tratamento de Falhas de Contêineres**</mark>

É crucial ter um plano para lidar com falhas individuais de contêineres. Isso pode envolver configurações de resiliência, como configurações de reinicialização automática ou uso de serviços de monitoramento para detectar e reagir a falhas.

#### <mark style="color:blue;">**Resposta a Falhas de Instância**</mark>

Caso uma instância do EC2 falhe, você precisa garantir que seus contêineres possam ser movidos ou reprogramados para outras instâncias disponíveis sem impactar a disponibilidade da aplicação.

#### <mark style="color:blue;">**Monitoramento de Implantações de Contêineres**</mark>

É necessário monitorar constantemente o estado e o desempenho dos contêineres em execução. Isso inclui monitorar métricas de saúde, uso de recursos e o comportamento das aplicações hospedadas nos contêineres.

Para simplificar e automatizar essas operações em escala, a AWS oferece serviços de orquestração de contêineres:

#### <mark style="color:blue;">**Amazon Elastic Container Service (ECS)**</mark>

É um serviço gerenciado que permite executar, interromper e gerenciar contêineres Docker em clusters escaláveis de instâncias EC2. O ECS gerencia a escalabilidade, o agendamento de tarefas e a integração com outros serviços da AWS.

#### <mark style="color:blue;">**Amazon Elastic Kubernetes Service (EKS)**</mark>&#x20;

É um serviço gerenciado que facilita a execução do Kubernetes na AWS sem precisar instalar, operar e gerenciar seu próprio cluster Kubernetes. O EKS permite implantar, gerenciar e escalar aplicações contêinerizadas usando Kubernetes.

Esses serviços oferecem funcionalidades avançadas de orquestração, facilitando o gerenciamento de contêineres em grande escala com alta disponibilidade e escalabilidade.

***

### <mark style="color:red;">Gerenciar contêineres com o Amazon Elastic Container Service (Amazon ECS)</mark>

O Amazon ECS é um serviço robusto para gerenciar contêineres, permitindo criar e administrar contêineres em clusters de instâncias EC2. Para utilizar o ECS, é necessário instalar o agente de contêiner em suas instâncias EC2, que facilita a comunicação com o serviço ECS para gerenciar o cluster.

<figure><img src="../../.gitbook/assets/image (17) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

Uma vez que as instâncias de contêiner estão em execução, você pode realizar várias ações, como iniciar, parar e monitorar contêineres, dimensionar horizontalmente e verticalmente, agendar a distribuição de contêineres no cluster, além de configurar permissões e garantir requisitos de disponibilidade.

<figure><img src="../../.gitbook/assets/image (19) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

Para executar sua aplicação no ECS, você define uma "tarefa", que é um arquivo JSON descrevendo os contêineres necessários, incluindo especificações como CPU, memória, portas, imagens, armazenamento e configurações de rede. Essa definição permite que o ECS saiba como configurar e executar seus contêineres de forma eficiente.

Exemplo de uma definição de tarefa simples para um servidor Web Nginx:

```json
{
  "family": "webserver",
  "containerDefinitions": [
    {
      "name": "web",
      "image": "nginx",
      "memory": "100",
      "cpu": "99"
    }
  ],
  "requiresCompatibilities": ["FARGATE"],
  "networkMode": "awsvpc",
  "memory": "512",
  "cpu": "256"
}
```

Neste exemplo, "webserver" é a família da tarefa, "web" é o nome do contêiner usando a imagem do Nginx, e são especificados requisitos de CPU e memória para a tarefa. Essa definição pode ser usada para preparar e executar aplicativos de forma eficiente no Amazon ECS.

***

### <mark style="color:red;">Usar o Kubernetes com o Amazon Elastic Kubernetes Service (Amazon EKS)</mark>

O Kubernetes é uma plataforma de código aberto projetada para gerenciar workloads e serviços em contêineres de maneira portátil e extensível. Integrando o desenvolvimento de software com operações, o Kubernetes criou um ecossistema robusto e amplamente adotado no mercado.

Para usuários do Kubernetes que desejam orquestrar suas workloads na AWS, o Amazon EKS é uma opção viável. Similar ao Amazon ECS em conceito geral, o EKS possui algumas distinções:

#### <mark style="color:blue;">**Instância de Contêiner vs Nó de Trabalho**</mark>

No Amazon ECS, uma instância EC2 com o agente ECS é chamada de instância de contêiner, enquanto no Amazon EKS é chamada de nó de trabalho.

#### <mark style="color:blue;">**Tarefa vs Pod**</mark>

Um contêiner no ECS é chamado de tarefa, enquanto no EKS é chamado de pod, a unidade básica de execução no Kubernetes.

#### <mark style="color:blue;">**Tecnologia Subjacente**</mark>

O Amazon ECS funciona nativamente na tecnologia da AWS, enquanto o Amazon EKS opera sobre o Kubernetes, aproveitando todo o ecossistema e as funcionalidades dessa plataforma.

Se você já utiliza o Kubernetes e busca uma solução de orquestração avançada que ofereça simplicidade, alta disponibilidade e controle refinado sobre sua infraestrutura na nuvem AWS, o Amazon EKS pode ser a ferramenta ideal para suas necessidades.

***

## <mark style="color:red;">**Recursos**</mark>

[containers on AWS](https://aws.amazon.com/containers/services/)

[Docker: o que é um contêiner?](https://www.docker.com/resources/what-container)

[Amazon Elastic Container Service](https://aws.amazon.com/ecs/)

[Github: agente do Amazon ECS](https://github.com/aws/amazon-ecs-agent)

[Amazon ECS ContainerInstances](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/ECS\_instances.html)

[Curso Coursera: criando aplicações em contêineres na AWS](https://www.coursera.org/learn/containerized-apps-on-aws)

***
