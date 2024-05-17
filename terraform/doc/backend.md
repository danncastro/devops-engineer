# Backend

É a estrutura que define onde o terraform irá guardar o estado (TFSTATE) do ambiente.

### Exemplo:

```yaml
backend "s3" {
	bucket = "terraform-state"
	key = "terraform.tfstate"
	region = "us-east-1"
```
