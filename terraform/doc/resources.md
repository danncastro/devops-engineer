# Resources

Item mais importante do terraform, ele informa o recurso que será criado/gerenciado.

### Exemplos:

```yaml
resources "aws_instance" "web" {
    ami = "ami-a1b2c3d4"
    intance_type = "t2.micro
}
```
