# complemento

* Terraform é uma ferramenta open source de provisionamento de infraestrutura, criada pela HashiCorp, que permite que definamos nossa infraestrutura como código **(IaC)**, usando uma lingaguem simples e declarativa **(HCL - HashCorp Configuration Language).**
* Desenvolvido em GO e é OpenSource

Item mais importante do terraform, ele informa o recurso que será criado/gerenciado.

**Exemplos:**

```yaml
resources "aws_instance" "web" {
    ami = "ami-a1b2c3d4"
    intance_type = "t2.micro
}
```
