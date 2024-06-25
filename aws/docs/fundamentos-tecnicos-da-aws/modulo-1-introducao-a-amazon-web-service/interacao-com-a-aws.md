---
description: Cada ação que você faz na AWS é uma chamada de API autenticada e autorizada.
---

# Interação com a AWS

Na AWS, você pode fazer chamadas de API para serviços e recursos por meio do Console de Gerenciamento da AWS, da AWS Command Line Interface (AWS CLI) ou de Kits de desenvolvimento de software (SDKs) da AWS.

***

## <mark style="color:red;">O Console de Gerenciamento da AWS</mark>

Uma das maneiras mais acessíveis e eficazes de gerenciar recursos na nuvem é através do console baseado na Web fornecido pela AWS. Neste ambiente, você faz login e tem acesso a uma interface intuitiva onde pode escolher e configurar os serviços desejados. Isso se mostra especialmente útil para iniciantes na nuvem, pois facilita a criação e o gerenciamento de recursos sem a necessidade de conhecimentos profundos em infraestrutura de TI. O console web permite que você explore e utilize uma ampla gama de serviços da AWS, simplificando o processo de implantação e administração de aplicações na nuvem de maneira prática e direta.

Quando você faz login pela primeira vez no Console de Gerenciamento da AWS, geralmente é apresentado a uma página de aterrissagem que pode incluir várias seções:

#### <mark style="color:blue;">**Painel de boas-vindas**</mark>

Geralmente, há uma mensagem de boas-vindas ou uma breve introdução sobre como começar.

#### <mark style="color:blue;">**Serviços em destaque**</mark>

Pode haver ícones ou links diretos para os serviços mais utilizados da AWS, como EC2, S3, RDS, etc.

#### <mark style="color:blue;">**Recursos recomendados**</mark>

Dependendo do seu perfil e uso anterior da AWS, pode haver recomendações de recursos ou serviços que podem ser úteis para você.

#### <mark style="color:blue;">**Barra de navegação**</mark>

Uma barra de navegação no topo ou no lado da página permite acessar rapidamente diferentes serviços e recursos da AWS.

#### <mark style="color:blue;">**Notificações ou alertas**</mark>

Pode haver notificações sobre atualizações de serviço, alertas de segurança ou informações importantes.

Abaixo está uma captura de tela que mostra a página de aterrissagem quando você faz login pela primeira vez no Console de Gerenciamento da AWS.

<figure><img src="../../.gitbook/assets/image (33).png" alt=""><figcaption></figcaption></figure>

No Console de Gerenciamento da AWS, os serviços são organizados em categorias como computação, armazenamento, banco de dados e análise, facilitando a navegação e o acesso aos recursos específicos que você precisa.

No canto superior direito do console, há um seletor de região. Ao escolher e alterar a região aqui, você direciona todas as suas solicitações para serviços da AWS na região selecionada. Isso não apenas afeta a localização física dos recursos que você está gerenciando, mas também é refletido no URL do console. Quando você muda a configuração de região, o navegador redireciona automaticamente suas solicitações para o subdomínio correspondente à nova região da AWS, garantindo que você esteja interagindo com os recursos na localização desejada dentro da infraestrutura global da AWS.

***

## <mark style="color:red;">A AWS Command Line Interface (AWS CLI)</mark>

No cenário em que você precisa coletar dados de dezenas de servidores AWS para o front-end da sua aplicação de forma programática e diária, a AWS CLI (Command Line Interface) se torna uma ferramenta essencial.

A AWS CLI é uma ferramenta unificada que permite gerenciar diversos produtos da AWS via linha de comando e automatizar tarefas com scripts. É uma ferramenta de código aberto disponível para Windows, Linux e macOS.

Por exemplo, você pode usar a AWS CLI para executar uma chamada de API como:

```shell
aws ec2 describe-instances
```

Isso retornaria informações detalhadas sobre as instâncias EC2 em execução na sua conta AWS. Com essa capacidade, você pode automatizar a coleta de dados dos seus servidores, eliminando a necessidade de login manual no Console de Gerenciamento da AWS e o trabalho repetitivo de copiar e colar informações.

<figure><img src="../../.gitbook/assets/image (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

Ao agendar e executar scripts da AWS CLI regularmente, você garante que seus relatórios estejam sempre atualizados, mesmo com mudanças constantes nos detalhes dos servidores. Essa abordagem não só aumenta a eficiência operacional, mas também mantém a precisão e a consistência nos processos de gerenciamento de infraestrutura na nuvem.

***

## <mark style="color:red;">SDKs da AWS</mark>

As chamadas de API para a AWS podem ser automatizadas usando SDKs (Software Development Kits) disponíveis para diversas linguagens de programação populares, como **C++, Go, Java, JavaScript, .NET, Node.js, PHP, Python e Ruby.** Estes SDKs são desenvolvidos pela AWS, são de código aberto e oferecem uma maneira conveniente de integrar seu código com os serviços da AWS.

Por exemplo, se você está desenvolvendo uma aplicação em Python que precisa interagir com os serviços da AWS, pode utilizar o SDK da AWS para Python, conhecido como `boto3`. Aqui está um exemplo de como você pode utilizar o SDK para realizar uma chamada de API para descrever instâncias

```python
import boto3

# Criando um cliente para o serviço EC2
ec2 = boto3.client('ec2')

# Fazendo uma chamada de API para descrever instâncias EC2
response = ec2.describe_instances()

# Imprimindo a resposta da chamada de API
print(response)

```

***

## <mark style="color:red;">**Recursos**</mark>&#x20;

[Trabalhando com o Console de Gerenciamento da AWS](https://docs.aws.amazon.com/awsconsolehelpdocs/latest/gsg/getting-started.html)

[AWS Command Line Interface](https://aws.amazon.com/cli/)

[Ferramentas para criação na AWS](https://aws.amazon.com/tools/)

***
