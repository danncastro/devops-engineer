# Introdução a Amazon Web Services

***

## Conceitos de Nuvem

1. **Benefícios da Nuvem:**
   * **Escalabilidade:** A capacidade de aumentar ou diminuir os recursos conforme necessário.
   * **Pague pelo que usar:** Modelo de pagamento baseado no uso, sem necessidade de grandes investimentos iniciais.
   * **Alta Disponibilidade:** Redundância e distribuição de dados para minimizar o tempo de inatividade.
2. **Modelos de Implantação:**
   * **Nuvem Pública:** Infraestrutura compartilhada disponível ao público, como a AWS.
   * **Nuvem Privada:** Infraestrutura dedicada a uma única organização, oferecendo mais controle e segurança.
   * **Nuvem Híbrida:** Combinação de nuvem pública e privada, permitindo flexibilidade e otimização de recursos.

***

## Serviços Principais da AWS

1. **Computação:**
   * **EC2:** Serviços de servidores virtuais na nuvem, altamente configuráveis.
   * **Lambda:** Execução de código sem necessidade de gerenciamento de servidores, com base em eventos.
   * **Elastic Beanstalk:** Plataforma para implantação e gerenciamento de aplicativos, automatizando processos como escalabilidade.
2. **Armazenamento:**
   * **S3:** Armazenamento de objetos altamente escalável, usado para backup, arquivamento e análise de dados.
   * **EBS:** Armazenamento em bloco, ideal para uso com EC2, oferecendo alta disponibilidade e resiliência.
   * **Glacier:** Armazenamento de longo prazo para arquivamento, com custos reduzidos.
3. **Rede e CDN:**
   * **VPC:** Rede virtual isolada onde você pode definir suas próprias regras de rede e segurança.
   * **CloudFront:** Serviço de CDN que entrega conteúdo de baixa latência globalmente.
   * **Route 53:** Serviço de DNS altamente disponível e escalável.

***

#### Segurança e Conformidade

1. **IAM (Identity and Access Management):**
   * Gerenciamento de usuários e permissões, permitindo controle detalhado sobre quem pode acessar quais recursos.
2. **Segurança de Rede:**
   * **Security Groups:** Regras de firewall para controlar o tráfego de entrada e saída em instâncias EC2.
   * **NACLs (Network Access Control Lists):** Controles de segurança para sub-redes inteiras, oferecendo uma camada adicional de segurança.
3. **Conformidade e Certificações:**
   * AWS oferece várias certificações e é compatível com regulamentos como GDPR, HIPAA, etc., garantindo conformidade e segurança.

#### Gerenciamento de Custo e Desempenho

1. **Cost Explorer:**
   * Ferramenta que permite analisar e visualizar custos e uso de recursos, ajudando a otimizar despesas.
2. **AWS Trusted Advisor:**
   * Serviço que oferece recomendações para otimizar segurança, desempenho, e custo.
3. **Auto Scaling:**
   * Ajuste automático da capacidade de computação com base na demanda, garantindo economia e desempenho ideal.

#### Arquitetura de Alta Disponibilidade

1. **Design para Falhas:**
   * Projetar sistemas que possam continuar operando mesmo em caso de falhas, usando redundância e recuperação automatizada.
2. **Escalabilidade:**
   * Capacidade de aumentar a capacidade do sistema para lidar com a demanda crescente, tanto vertical quanto horizontalmente.
3. **Elastic Load Balancing (ELB):**
   * Distribui automaticamente o tráfego de entrada em várias instâncias, garantindo disponibilidade e resiliência.
