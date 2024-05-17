# introducao terraform

**Provisioners**

* São responsáveis por provisionar o ambiente, podemos dizer que provisioners são o ultimo recurso e devem ser utilizados apenas se a API do provider não fornecer todos os recursos que precisamos. Alguns exemplos de provisioners:
  * _**file**_
  * _**local-exec**_
  * _**remote-exec**_
  * _**chef**_
  * _**puppet**_
  * _**salt**_

O Terraform utiliza a linguagem _**HCL (Hashicorp Configuration Language)**_ que é uma linguagem declarativa de fácil entendimento e compatível com JSON.

**Tags**

* Tags são utilizadas para adicionar informações relevantes ao usuario.

**Comandos**

* _**terraform fmt**_ - Formata o codigo.

***

### Laboratorio pratico:

***

**Criando usuário na aws:**

* 1 - Acesse o console da AWS e faça o login com sua conta e pesquise pelo produto _**IAM (Identity and Access Management)**_
* 2 - Iremos criar um usuário para interagir com a AWS, clique em _**USERS**_ e em seguida em _**ADD USER**_
* 3 - Digite um nome para o usuário, selecione _**programatic access**_ para que seja criado um ID e Senha para a chave de acesso e clique em _**Next.**_
* 4 - Adicione a politica _**AmazonEC2FullAccess**_ ao usuário, o que dará permissão total ao usuário apenas a recursos da EC2, e clique em _**Next.**_
* 5 - Vamos adicionar uma tag que contenham informações uteis para descrever o ambiente, e clique em _**Next.**_
* 6 - Verifique os dados e clique em _**Create user**_
* 7 - Clique em _**show**_ e copie o _**Access key ID**_ e _**Secret access key.**_

***

**Instalando o AWS CLI:**

*   1 - Iremos instalar o _**AWS CLI (Command Line Interface)**_ para autenticarmos via terminal e possibilitar nosso acesso via terraform.

    ```bash
    $ cd /tmp
    $ curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
    $ unzip awscliv2.zip
    $ sudo ./aws/install
    ```
* 2 - Verifique a instalação através do comando _**aws --version**_
* 3 - Agora iremos configurar nosso cli com o ID e chave de acesso criadas anteriormente
* 4 - execute o comando _**aws configure**_ e em seguida digite o ID e Chave (para região e output format apenas tecle ).
* 5 - Isso vai configurar o arquivo _**\~/.aws/credential**_s com suas credenciais

***

**Instalando o Terraform:**

```
~~~bash
$ cd /tmp 
$ curl https://releases.hashicorp.com/terraform/0.12.24/terraform_0.12.24_linux_amd64.zip -o terraform.zip
$ unzip terraform.zip
$ sudo mv terraform /usr/local/bin
$ terraform --version
~~~
```

* 1 - Caso o comando _**terraform --version**_ retorne a versão correta, significa que a instalação ocorreu com sucesso.

***

**Criando o código HCL**

* Os arquivos utilizados pelo terraform tem a terminação _**.tf**_
*   1 - Criaremos o diretório para armazenar nosso código bem como um arquivo para configurar nosso _**backend**_

    ```bash
    $ mkdir ~/terraform-101
    $ cd ~/terraform-101
    $ code . backend.tf
    ```
*   2 - No arquivo _**backend.tf**_ iremos adicionar o conteúdo para informar qual será o _**provider**_ utilizado, no nosso caso _**aws**_, bem como a região que será aplicada.

    \~/terraform-101/backend.tf

    ```terraform
    provider "aws" {
        region = var.region
    }
    ```
* 3 - Declaramos um conteudo proveniente de uma variavel chamada _**region**_ através do parâmetro _**var.nome\_variavel**_
* 4 - O uso de variáveis não é necessário, podemos simplesmente declarar os valores diretamente no arquivo, porém ao utilizar as variáveis a manutenção e o reaproveitamento do código é feito de maneira mais simples
*   5 - Vamos criar um arquivo _**ec2.tf**_ que será responsável pela definição da nossa instância ec2

    ```bash
    $ vim ec2.tf
    ```

    ```terraform
    resource "aws_instance" "server" {
        ami           = var.ami
        instance_type = var.instance_type

        tags = {
            Name        = var.name
            Environment = var.env
            Provisioner = "Terraform"
        }
    }
    ```
* 6 - Novamente estamos declarando diversas variáveis e precisamos definilas em um arquivo para que seja utilizada.
*   7 - Criaremos o arquivo _**variables.tf**_ onde definiremos estas variáveis.

    ```bash
    $ vim variables.tf
    ```

    ```terraform
    variable "region" {
        description = "Define what region the instance will be deployed"
        default = "us-east-1"
    }

    variable "name" {
        description = "Name of the Application"
        default = "server01"
    }

    variable "env" {
        description = "Environment of the Application"
        default = "prod"
    }

    variable "ami" {
        description = "AWS AMI to be used "
        default = "ami-07ebfd5b3428b6f4d"
    }

    variable "instance_type" {
        description = "AWS Instance type defines the hardware configuration of the machine"
        default = "t2.micro"
    }
    ```
* 8 - O campo _**description**_ informa a descrição de cada variável, é uma boa prática dizer o que cada variável significa e/ou para que é utilizada.
* 9 - O campo _**default**_ informa o valor padrão da variável.
* 10 - Agora que ja criamos nosso arquivo precisamos executar o comando _**terraform init**_ para que seja feito download dos providers do terraform em nosso diretório.
* 11 - Agora que iniciamos o provider teremos uma pasta oculta _**.terraform**_ em nosso diretório com os plugins necessários.
* 12 - Podemos agora efetuar o planejamento da nossa infraestrutura através do comando _**terraform plan**_ , que será responsável por nos mostrar qual seria o resultado após a aplicação do nosso código.
* 13 - No final da saída do comando é exibido quantos planos serão _aplicados_, _modificados_ ou _destruídos_.
* 14 - Para aplicar o plano utilizaremos o comando _**terraform apply**_ que nos mostrará o resultado do plan e perguntando se queremos aplicar o recurso, _**digite yes**_.
* 15 - Ao executar um terraform, é criado um arquivo _**terraform.tfstate**_ no diretório com o conteúdo do que foi criado/modificado para que o terraform possa efetuar ações de modificação na infraestrutura sabendo seu estado anterior.
*   16 - Vamos alterar o nome da variável _**name**_ para _**server02**_ e executar novamente o _**terraform apply.**_

    ```bash
    vim variables.tf
    ```

    ```terraform
    variable "name" {
        description = "Name of the Application"
        default = "server02"
    }
    ```

17 - Execute o _**terraform plan**_ e verifique que o nome da instância será modificado, porém ela não será destruida e recriada.

18 - Podemos executar o _**terraform apply**_ para aplicar a configuração.

19 - Para destruir a instância podemos executar o comando _**terraform destroy**_

20 - _**Digite yes**_ para destruir a instância, note que o processo todo levará um tempo para ser executado, aguarde o retorno pelo terminal.

### Improve it (Atribuindo security group a uma instância já existente)

**Exemplo**

```conf
resource "aws_security_group" "ssh" {
    name = "allow_ssh"
    description = "Allow SSH connections"

    ingress {
        from_port = 22
        to_port = 22
        protocol = "tcp"
        cidr_blocks = ["0.0.0.0/0"]
    }
}

resource "aws_instance" "exemple" {
    ami                    = "ami-6edd3078"
    instance_type          = "t2.micro"
    vpc_security_group_ids = ["${aws_security_group.ssh.id}"]
    tags{
        Name = "Test Machine"
    }
}
```

### Drawbacks

**GeoEnginner** **TerraGrunt**

**Declarativa vs Procedural**

Acessar um valor de um resource

**Exemplo:**

```yaml
tipo.nome.algum_output
```
