# Providers

São responsáveis por comunicar com a API da estrutura desejada e expor os recursos.

Geralmente quando falamos de providers estamos falando de _**IaaS (Infrastructure as a Service)**_, _**PaaS (Platform as a Service)**_ ou _**Saas (Softwares as a Service)**_

### Alguns exemplos de providers:

_**IaaS:**_

* GCP
* AWS
* Azure
* Digital Ocean
* Alibaba Cloud
* Openstack.

_**PaaS:**_

* Heroku.

_**SaaS:**_

* Cloudflare
* DNSSimple
* DNSMadeEasy.

### Exemplo de providers:

```yaml
# The default provider configuration; resources that begin with 'aws_' will use
# It as the default, and It can be referenced as 'aws'.

provider "aws" {
    region = "us-east-1"
}

# Additional provider configuration for west coast region; resources can
# Reference this as 'aws.west'.

provider "aws" {
    alias = "west"
    region = "us-west-2"
}
```
