---
description: O lambda executa sua função em um ambiente seguro e isolado.
---

# AWS Lambda

***

## <mark style="color:red;">Remover trabalho pesado sem diferenciação</mark>

Ao escolher onde executar seu código na AWS, as responsabilidades variam conforme o serviço utilizado:

| Execução no Amazon EC2                                                                                                        |
| ----------------------------------------------------------------------------------------------------------------------------- |
| A AWS é responsável pelo hardware físico.                                                                                     |
| Você é responsável pelo sistema operacional convidado, segurança e patches, configuração de rede, segurança e escalabilidade. |

| Execução em contêineres no Amazon ECS e Amazon EKS                                                                                            |
| --------------------------------------------------------------------------------------------------------------------------------------------- |
| A AWS gerencia mais do ambiente de contêineres, como implantação dos contêineres em instâncias EC2 e gerenciamento do cluster de contêineres. |
| Você ainda é responsável por manter as instâncias EC2 subjacentes, incluindo sistema operacional, segurança, patches e configuração de rede.  |

| Computação sem servidor na AWS                                                                                                                                                                  |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Se você optar pela computação sem servidor (como AWS Lambda ou AWS Fargate), a AWS gerencia quase todos os aspectos do ambiente de execução.                                                    |
| Você não precisa gerenciar instâncias EC2 ou clusters de contêineres. A AWS assume responsabilidade pela infraestrutura física, escalabilidade automática e manutenção do ambiente de execução. |

Portanto, escolher entre EC2, ECS/EKS e computação sem servidor depende do nível de controle e responsabilidade operacional que você deseja manter versus delegar à AWS. A computação sem servidor oferece maior abstração e simplificação operacional, enquanto EC2 e serviços de contêineres como ECS e EKS permitem maior controle sobre o ambiente de execução.

***

### <mark style="color:red;">Adote a computação sem servidor</mark>

A computação sem servidor oferece várias vantagens fundamentais, resumidas nos seguintes aspectos:

#### <mark style="color:blue;">**Nenhum servidor para provisionar ou gerenciar**</mark>

Elimina a necessidade de configurar e gerenciar servidores físicos ou virtuais, permitindo que os desenvolvedores se concentrem diretamente no código da aplicação.

#### <mark style="color:blue;">Escalabilidade automática com uso</mark>

Os serviços sem servidor dimensionam automaticamente recursos computacionais de acordo com a demanda, garantindo que a aplicação esteja sempre disponível e capaz de lidar com picos de tráfego.

#### <mark style="color:blue;">**Não há cobrança por recursos ociosos**</mark>

Você paga apenas pelo tempo de execução do código ou pelos recursos consumidos durante a execução da função, sem custos adicionais associados a recursos inativos.

#### <mark style="color:blue;">**Disponibilidade e tolerância a falhas incorporadas**</mark>

Os serviços sem servidor são projetados para serem altamente disponíveis e resilientes, gerenciando automaticamente falhas de infraestrutura sem interrupção perceptível para os usuários finais.

Ao escolher serviços como AWS Fargate ou AWS Lambda, você pode aproveitar esses benefícios para concentrar-se mais na diferenciação da sua aplicação, em vez de se preocupar com tarefas operacionais como garantir disponibilidade, escalabilidade e gerenciamento de servidores. Isso permite que os desenvolvedores se concentrem em desenvolver e entregar valor aos usuários finais de maneira eficiente e escalável.

***

### <mark style="color:red;">Explorar contêineres sem servidor com o AWS Fargate</mark>

O Amazon ECS e o Amazon EKS permitem que você execute seus contêineres nos dois modos a seguir:

* Amazon EC2
* AWS Fargate

<figure><img src="../../.gitbook/assets/image (20) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

O AWS Fargate é uma solução de computação sem servidor projetada especificamente para contêineres. Ele simplifica significativamente o gerenciamento de infraestrutura ao dimensionar automaticamente os recursos necessários para executar aplicações, permitindo que os desenvolvedores se concentrem no desenvolvimento de software.

Principais características e benefícios do AWS Fargate:

#### <mark style="color:blue;">**Abstração de instâncias do EC2**</mark>

Fargate elimina a necessidade de gerenciar instâncias EC2 diretamente. Em vez disso, ele gerencia automaticamente a infraestrutura necessária para executar contêineres, desde o provisionamento até o escalonamento.

#### <mark style="color:blue;">**Compatibilidade com Amazon ECS e Amazon EKS**</mark>

Integra-se perfeitamente com as arquiteturas de contêineres do Amazon ECS e Amazon EKS. Isso significa que você pode usar as mesmas primitivas, APIs e integrações familiares da AWS para gerenciar e implantar contêineres no Fargate.

#### <mark style="color:blue;">**Isolamento de workload e segurança aprimorada**</mark>

Oferece isolamento robusto entre workloads de contêineres, garantindo segurança por design. Cada aplicação ou microserviço é executado em um ambiente virtual isolado, proporcionando maior segurança e confiabilidade.

#### <mark style="color:blue;">**Integração nativa com AWS IAM e Amazon VPC**</mark>

Utiliza integração nativa com o AWS Identity and Access Management (IAM) para gerenciar permissões e acesso, além de se integrar perfeitamente à Amazon Virtual Private Cloud (VPC). Isso permite iniciar contêineres Fargate dentro da sua rede VPC e controlar a conectividade com suas aplicações de forma segura e flexível.

Em resumo, o AWS Fargate simplifica drasticamente a execução de contêineres na nuvem, oferecendo automação de infraestrutura, segurança avançada e integração transparente com serviços da AWS, permitindo aos desenvolvedores concentrarem-se exclusivamente na criação e na evolução das suas aplicações.

***

### <mark style="color:red;">Executar código no AWS Lambda</mark>

O AWS Lambda é uma solução de computação sem servidor que simplifica significativamente a execução de código sem a necessidade de gerenciar servidores ou contêineres EC2.

Principais características e benefícios do AWS Lambda:

#### <mark style="color:blue;">**Sem gerenciamento de servidores ou contêineres**</mark>

Com o Lambda, você não precisa provisionar, gerenciar ou escalar servidores ou contêineres. Basta fazer o upload do seu código-fonte e o Lambda cuida de todo o ambiente necessário para executar o código de maneira eficiente.

#### <mark style="color:blue;">**Flexibilidade para diversos casos de uso**</mark>

Suporta uma ampla gama de aplicativos e serviços de backend, como processamento de dados, processamento de streams em tempo real, machine learning, WebSockets, backends IoT, backends móveis e aplicações web.

#### <mark style="color:blue;">**Automação de escala e alta disponibilidade**</mark>

O Lambda gerencia automaticamente a escala do código conforme necessário, garantindo alta disponibilidade sem que você precise se preocupar com ajustes manuais. Ele oferece escalabilidade contínua com medição de subsegundo, o que significa que você paga apenas pelo tempo de execução do seu código.

#### <mark style="color:blue;">**Performance consistente**</mark>

Proporciona performance consistente independentemente do número de execuções simultâneas ou da carga de trabalho, garantindo uma experiência previsível para seus usuários finais.

Em resumo, o AWS Lambda permite implantar e escalar suas cargas de trabalho e aplicações de forma eficiente e simplificada, liberando os desenvolvedores para se concentrarem exclusivamente na lógica de negócios e na inovação de suas aplicações, sem se preocupar com a complexidade operacional de gerenciar infraestrutura.

***

### <mark style="color:red;">Como o AWS Lambda funciona</mark>

Uma função do Lambda tem três componentes principais: acionador, código e configuração.

O AWS Lambda é uma plataforma de computação sem servidor que oferece flexibilidade no desenvolvimento e configuração de funções executadas em resposta a eventos. Aqui estão os principais pontos sobre como configurar e usar funções do Lambda:

| Criação do código-fonte                                                                                                                                                                                    | Configuração da função do Lambda                                                                                                                                                   |
| ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Pode ser desenvolvido do zero.                                                                                                                                                                             | Especifica o tempo de execução, como Python, Node.js, Ruby, Go, Java ou .NET Core, ou pode definir um tempo de execução personalizado.                                             |
| Utiliza modelos fornecidos pela AWS.                                                                                                                                                                       | Configuração inclui definições de rede, variáveis de ambiente, alocação de memória, tipo de invocação, permissões de acesso e outras configurações detalhadas conforme necessário. |
| Aproveita o código disponível no AWS Serverless Application Repository, que inclui exemplos como "hello world", habilidades do Amazon Alexa, processamento de imagens, codificação de vídeo, entre outros. |                                                                                                                                                                                    |

| Facilidade de gerenciamento                                                                                                                                                                     | Acionadores (Triggers)                                                                                                                                           |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Werner Vogels, CTO da Amazon, destaca que "nenhum servidor é mais fácil de gerenciar do que nenhum servidor", resumindo a conveniência das soluções sem servidor como AWS Fargate e AWS Lambda. | Determinam quando a função do Lambda será executada em resposta a eventos específicos na AWS.                                                                    |
| Essas soluções eliminam a necessidade de gerenciar infraestrutura física ou virtual diretamente, permitindo foco total no desenvolvimento de aplicações e na resposta a eventos.                | Integra com outros serviços AWS para automatizar a execução de funções em resposta a chamadas de API, eventos de armazenamento, mensagens de fila, entre outros. |

Em resumo, o AWS Lambda proporciona uma maneira eficiente e escalável de executar código sem se preocupar com a complexidade de gerenciar servidores, adequando-se a uma ampla gama de casos de uso desde processamento de dados até aplicações web e IoT.

***

### <mark style="color:red;">**Handler de função do AWS Lambda**</mark>

O handler de função do AWS Lambda é o método no código da função que processa eventos. Quando sua função é invocada, o Lambda executa o método do manipulador. Quando o manipulador é encerrado ou retorna uma resposta, ele se torna disponível para lidar com outro evento.&#x20;

Você pode usar a seguinte sintaxe geral ao criar um manipulador de funções no Python.

```python
def handler_name(event, context):
...
return some_value
```

***

### <mark style="color:red;">**Nomeação**</mark>

O nome do manipulador de função do Lambda é determinado pelas seguintes regras:

#### <mark style="color:blue;">**Nome do arquivo onde está localizado o código do manipulador de função do Lambda**</mark>

* Se o código do manipulador estiver em um arquivo chamado `lambda_function.py`, por exemplo, o nome padrão do manipulador será `lambda_function.lambda_handler`. Aqui, `lambda_function` é o nome do arquivo e `lambda_handler` é o nome da função Python definida dentro desse arquivo.

#### <mark style="color:blue;">**Nome da função do manipulador Python**</mark>

* O nome do manipulador de função pode ser qualquer nome válido. No entanto, ao usar o console do Lambda, o padrão é `lambda_function.lambda_handler`, seguindo o exemplo acima.

#### <mark style="color:blue;">**Personalização no Console do Lambda**</mark>

* Se você optar por usar um nome diferente para o manipulador de função no console do Lambda, é necessário atualizar esse nome nas configurações de tempo de execução da função.

Em resumo, o nome do manipulador de função do Lambda reflete tanto o nome do arquivo onde o código está localizado quanto o nome da função Python específica dentro desse arquivo. Isso facilita a configuração e a identificação do ponto de entrada para a execução da função do Lambda.

***

### <mark style="color:red;">**Granularidade de faturamento**</mark>

O AWS Lambda oferece um modelo de cobrança que é altamente eficiente e flexível para diferentes tipos de cargas de trabalho:

#### <mark style="color:blue;">**Modelo de Cobrança**</mark>&#x20;

Você paga apenas pelo uso real do Lambda. Isso significa que você é cobrado pelo número de vezes que sua função é acionada (solicitações) e pelo tempo exato que o código leva para ser executado, arredondado para o milissegundo mais próximo. Não há tempo mínimo de execução.

#### <mark style="color:blue;">**Precisão na Cobrança**</mark>&#x20;

A AWS calcula o tempo de execução com uma precisão de milissegundos, garantindo que você pague apenas pelo tempo exato utilizado pela sua função. Isso torna o Lambda econômico para funções que são executadas rapidamente, como APIs de baixa latência ou processos com durações abaixo de 100 milissegundos.

#### <mark style="color:blue;">**Flexibilidade de Uso**</mark>&#x20;

Como não há necessidade de provisionar ou gerenciar servidores, o Lambda permite escalar automaticamente em resposta ao número de solicitações recebidas. Isso não apenas simplifica a infraestrutura, mas também otimiza os custos, garantindo que você não pague por recursos ociosos.

Em resumo, o modelo de cobrança do AWS Lambda é ideal para aplicações com demandas variáveis ou imprevisíveis, proporcionando economia significativa ao executar funções de curta duração ou operações que requerem baixa latência. Leia mais aqui:\
&#x20;[https://aws.amazon.com/blogs/aws/new-for-aws-lambda-1ms-billing-granularity-adds-cost-savings/](https://aws.amazon.com/blogs/aws/new-for-aws-lambda-1ms-billing-granularity-adds-cost-savings/)

***

### <mark style="color:red;">**Código-fonte**</mark>

Você pode encontrar um tutorial sobre a criação da função do AWS Lambda, assim como o código usado na demonstração do AWS Lambda, aqui:&#x20;

{% embed url="https://aws.amazon.com/blogs/compute/resize-images-on-the-fly-with-amazon-s3-aws-lambda-and-amazon-api-gateway/" %}

***

## <mark style="color:red;">**Recursos**</mark>

[AWS: sem servidor](https://aws.amazon.com/serverless/)

[Construção de aplicações Python modernas na AWS](https://www.coursera.org/learn/building-modern-python-applications-on-aws)

[Recursos sem servidor da AWS](https://aws.amazon.com/serverless/resources/?serverless.sort-by=item.additionalFields.createdDate\&serverless.sort-order=desc)

[Construção de aplicações com arquiteturas sem servidor](https://aws.amazon.com/lambda/serverless-architectures-learn-more/)

[Práticas recomendadas para a organização de aplicações sem servidor maiores](https://aws.amazon.com/blogs/compute/best-practices-for-organizing-larger-serverless-applications/)

[Gerenciamento de funções do AWS Lambda](https://docs.aws.amazon.com/lambda/latest/dg/lambda-functions.html)

[10 coisas que os arquitetos sem servidor precisam saber](https://aws.amazon.com/blogs/architecture/ten-things-serverless-architects-should-know/)

[AWS Alien Attack! Uma aventura sem servidor](https://alienattack.workshop.aws/)

***
