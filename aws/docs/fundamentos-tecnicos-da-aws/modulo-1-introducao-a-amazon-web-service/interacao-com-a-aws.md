---
description: Cada ação que você faz na AWS é uma chamada de API autenticada e autorizada.
---

# Interação com a AWS

Na AWS, você pode fazer chamadas de API para serviços e recursos por meio do Console de Gerenciamento da AWS, da AWS Command Line Interface (AWS CLI) ou de Kits de desenvolvimento de software (SDKs) da AWS.

***

## <mark style="color:red;">O Console de Gerenciamento da AWS</mark>

Uma das maneiras mais acessíveis e eficazes de gerenciar recursos na nuvem é através do console baseado na Web fornecido pela AWS.

* É uma **interface baseada na Web** para gerenciar recursos na nuvem.
* Permite que você **faça login** e acesse uma **interface intuitiva** para **escolher** e **configurar** serviços.
* É especialmente útil para **iniciantes** na nuvem, facilitando a **criação** e **gerenciamento** de recursos sem conhecimentos profundos em infraestrutura de TI.
* Oferece uma **ampla gama de serviços** da AWS, simplificando a **implantação** e **administração** de aplicações na nuvem de maneira **prática** e **direta**.

#### <mark style="color:blue;">**Painel de boas-vindas**</mark>

Geralmente inclui uma **mensagem de boas-vindas** ou uma **breve introdução** sobre como **começar**.

#### <mark style="color:blue;">**Serviços em destaque**</mark>

Exibe **ícones** ou **links diretos** para os serviços mais utilizados, como **EC2**, **S3**, **RDS**, etc.

#### <mark style="color:blue;">**Recursos recomendados**</mark>

Sugestões de **recursos** ou **serviços** baseadas no seu **perfil** e uso anterior da AWS.

#### <mark style="color:blue;">**Barra de navegação**</mark>

Permite acessar rapidamente **diferentes serviços** e recursos da AWS, localizada no topo ou no lado da página.

#### <mark style="color:blue;">**Notificações ou alertas**</mark>

Informa sobre **atualizações de serviço**, **alertas de segurança** ou outras **informações importantes**.

Abaixo está uma captura de tela que mostra a página de aterrissagem quando você faz login pela primeira vez no Console de Gerenciamento da AWS.

<figure><img src="../../.gitbook/assets/image (33) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

No **Console de Gerenciamento da AWS**, os serviços são organizados em **categorias** como:

* **Computação**
* **Armazenamento**
* **Banco de Dados**
* **Análise**

Essa organização facilita a **navegação** e o **acesso** aos recursos específicos que você precisa.

#### <mark style="color:blue;">**Seletor de Região no Console da AWS**</mark>

No **canto superior direito** do console, há um **seletor de região**.

* **Escolher e alterar a região** direciona todas as suas solicitações para serviços da AWS na **região selecionada**.
* Isso afeta:
  * A **localização física** dos recursos que você está gerenciando.
  * O **URL** do console, que é refletido no subdomínio correspondente à nova região.
* **Mudanças na configuração de região** fazem com que o navegador redirecione automaticamente suas solicitações para o subdomínio da nova região da AWS, garantindo interação com os recursos na localização desejada dentro da **infraestrutura global** da AWS.

***

## <mark style="color:red;">A AWS Command Line Interface (AWS CLI)</mark>

**AWS CLI** é uma ferramenta essencial quando você precisa:

* **Coletar dados** de dezenas de **servidores AWS**.
* Realizar essas operações de forma **programática** e **diária**.

**AWS CLI** é uma **ferramenta unificada** que permite:

* **Gerenciar diversos produtos da AWS** via **linha de comando**.
* **Automatizar tarefas** com **scripts**.

É uma **ferramenta de código aberto** disponível para **Windows**, **Linux** e **macOS**.

#### <mark style="color:blue;">Exemplo de Uso da AWS CLI</mark>

Por exemplo, você pode usar a AWS CLI para executar uma chamada de API como:

```shell
aws ec2 describe-instances
```

#### <mark style="color:blue;">Coleta de Dados com AWS CLI</mark>

Executar o comando `aws ec2 describe-instances` retornaria **informações detalhadas** sobre as **instâncias EC2** em execução na sua conta AWS.

Com essa capacidade, você pode:

* **Automatizar a coleta de dados** dos seus **servidores**.
* Eliminar a **necessidade de login manual** no Console de Gerenciamento da AWS.
* Evitar o **trabalho repetitivo** de **copiar e colar informações**.

<figure><img src="../../.gitbook/assets/image (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

**Agendar e executar scripts** da AWS CLI regularmente:

* Garante que seus **relatórios** estejam sempre **atualizados**, mesmo com **mudanças constantes** nos detalhes dos servidores.
* Aumenta a **eficiência operacional**.
* Mantém a **precisão** e a **consistência** nos processos de **gerenciamento de infraestrutura** na nuvem.

***

## <mark style="color:red;">SDKs da AWS</mark>

As chamadas de **API** para a AWS podem ser automatizadas usando **SDKs (Software Development Kits)**.

**SDKs** estão disponíveis para diversas **linguagens de programação** populares, como:

* **C++**
* **Go**
* **Java**
* **JavaScript**
* **.NET**
* **Node.js**
* **PHP**
* **Python**
* **Ruby**
* Os **SDKs** são desenvolvidos pela **AWS**, são de **código aberto** e oferecem uma maneira **conveniente** de integrar seu código com os **serviços da AWS**.

#### <mark style="color:blue;">**Exemplo de Uso do SDK da AWS (boto3) em Python**</mark>

* Se você está desenvolvendo uma aplicação em **Python** que precisa interagir com os **serviços da AWS**, pode utilizar o **SDK da AWS para Python**, conhecido como **boto3**.
* Exemplo: Você pode usar o **boto3** para realizar uma **chamada de API** para **descrever instâncias**.

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
