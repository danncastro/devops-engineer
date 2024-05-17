# variables

### Variables

Variáveis são parâmetros para um módulo de Terraform, permitindo que aspectos da implementação sejam customizados sem que seu código seja alterado.

**Exemplo:**

```terraform
variable "image_id"{
    type = string
}

variable "docker_ports"{
    type = list(object({
        internal = number
        externel = number
        protocol = string
    }))
    default = [
        {
            internal = 8300
            external = 8300
            protocol = "tcp"
        }
    ]
}
```

***

**Variables Types:**

* **Input variables :** Are like function arguments
* **Output values :** Are like function return values
* **Local values :** Are like a function's temporary local variables.

***

### Output

Output é uma forma de expor o valor, seja como retorno de um módulo ou imprimindo como retorno do root.

**Exemplo de Output**

```terraform~
output
```

***

### Locals

Um Local é um valor que recebe um nome a partir de uma expressão ou valor

**Exemplo de Locals:**

```terraform
locals {
    # IDs for multiple sets of EC2 Instances, meged together
    instances_ids = concat(aws_instance.blue.-.id, aws_instance.green.-.id)
}

locals {
    # Common tags to  be assigned to all resources
    common_tags = {
        Service = local.service_name
        Owner   = local.owner
    }
}
```
