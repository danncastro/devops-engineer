# data sources

Recupera informações de recursos já criados no ambiente sem precisar gerenciar o mesmo. Ou seja, sem precisar importar o recurso e gerenciá-lo

### Exemplo:

```yaml
data "aws_ami" "exemple" {
	most_recent = true

	owners = ["self"]
	tags = {
		Name = "app-server"
		Tested = "true"
	}
}
```
