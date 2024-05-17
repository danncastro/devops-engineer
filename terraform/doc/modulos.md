# Módulos

É como uma abstração de um conjunto de recurso para reaproveitamento do mesmo;

### Exemplo:

```yaml
module "servers" {
	source = "./app-cluster"

	servers = 5
}
```

```yaml
module "name" {
	source = "/caminho/para/o/modulo"
}
```
