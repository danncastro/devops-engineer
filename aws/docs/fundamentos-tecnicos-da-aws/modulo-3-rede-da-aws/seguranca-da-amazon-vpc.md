# Segurança da Amazon VPC

***

## <mark style="color:red;">Sub-redes seguras com listas de controle de acesso à rede</mark>

Uma Lista de Controle de Acesso à Rede **(Network ACL)** é semelhante a um firewall aplicado ao nível da sub-rede, permitindo controlar quais tipos de tráfego podem entrar ou sair da sub-rede. Você configura isso definindo regras que especificam o que deseja permitir ou negar.&#x20;

Veja um exemplo:

<figure><img src="../../.gitbook/assets/image (2) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

A Network ACL padrão, exemplificada na tabela acima, permite todo o tráfego entrar e sair da sub-rede. Isso é um bom ponto de partida para permitir que os dados fluam livremente pela sub-rede.

No entanto, você pode querer restringir o tráfego em um nível mais granular. Por exemplo, para uma aplicação web, você pode configurar regras específicas para permitir apenas tráfego **HTTPS** e **RDP (Remote Desktop Protocol)** para servidores web:

<figure><img src="../../.gitbook/assets/image (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
**Observação:** No exemplo acima da Network ACL, é permitida a porta **443** para entrada e o intervalo de saída de **1025-65535**. Isso ocorre porque o **HTTP usa a porta 443** para iniciar uma conexão e responde usando uma porta efêmera. As Network ACLs são **stateless (não mantêm o estado)**, portanto você precisa incluir as portas de saída que serão usadas pelo protocolo para resposta. Se essas portas não forem incluídas, o servidor pode responder, mas o tráfego não sairá da sub-rede.
{% endhint %}

As Network ACLs são configuradas inicialmente para permitir tráfego de entrada e saída. Você pode ajustar essas configurações para aumentar a segurança conforme necessário.

***

## <mark style="color:red;">Instâncias do EC2 seguras com grupos de segurança</mark>

A próxima camada de segurança é para suas instâncias do EC2, onde você pode criar um firewall chamado grupo de segurança. A configuração padrão de um grupo de segurança bloqueia todo o tráfego de entrada e permite todo o tráfego de saída.

<figure><img src="../../.gitbook/assets/image (2) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

#### <mark style="color:blue;">**Comportamento de Estado**</mark>

Os grupos de segurança são stateful, o que significa que eles lembram se uma conexão foi originalmente iniciada pela instância do EC2 ou de fora. Isso permite que o tráfego de resposta seja permitido temporariamente sem a necessidade de modificar as regras de entrada.

#### <mark style="color:blue;">**Regras de Entrada**</mark>

Se você quiser que sua instância do EC2 aceite tráfego da Internet, deve abrir portas de entrada específicas. Por exemplo, para um servidor web, você pode precisar aceitar solicitações HTTP e HTTPS. Abaixo está um exemplo de regras de entrada:

<figure><img src="../../.gitbook/assets/image (3) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

#### <mark style="color:blue;">**Segregação de Tráfego com Grupos de Segurança**</mark>

Você aprendeu anteriormente que sub-redes podem ser usadas para segregar tráfego entre computadores na rede. Grupos de segurança podem ser usados da mesma maneira. Um padrão comum é organizar recursos em diferentes grupos e criar grupos de segurança para controlar a comunicação de rede entre eles.

<figure><img src="../../.gitbook/assets/image (4) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

#### <mark style="color:blue;">**Exemplo de Arquitetura**</mark>

Neste exemplo, três camadas são definidas e isoladas com regras de grupos de segurança:

| Camada Web                             | Camada de Aplicação                     | Camada de Banco de Dados                          |
| -------------------------------------- | --------------------------------------- | ------------------------------------------------- |
| Permite tráfego da Internet via HTTPS. | Permite tráfego da camada Web via HTTP. | Permite tráfego da camada de aplicação via MySQL. |

#### <mark style="color:blue;">**Vantagens dos Grupos de Segurança**</mark>

Diferente dos ambientes on-premises tradicionais, onde o isolamento é feito por configuração VLAN, na AWS, os grupos de segurança permitem obter o mesmo isolamento sem amarrá-lo à infraestrutura de rede física.

Ao configurar os grupos de segurança de maneira adequada, você garante que suas instâncias do EC2 fiquem protegidas contra tráfego indesejado, permitindo apenas as conexões necessárias para o funcionamento correto dos seus serviços e aplicações.

***

## <mark style="color:red;">**Recursos**</mark>

[Tabelas de rotas](https://docs.aws.amazon.com/vpc/latest/userguide/VPC\_Route\_Tables.html)

[Exemplo de opções de roteamento](https://docs.aws.amazon.com/vpc/latest/userguide/route-table-options.html)

[Trabalho com tabelas de roteamento](https://docs.aws.amazon.com/vpc/latest/userguide/WorkWithRouteTables.html)

[Network ACLs](https://docs.aws.amazon.com/vpc/latest/userguide/vpc-network-acls.html)

[Grupos de segurança para sua VPC](https://docs.aws.amazon.com/vpc/latest/userguide/VPC\_SecurityGroups.html)

[Eu hospedo um site em uma instância do EC2. Como permito que meus usuários se conectem ao HTTP (80) ou HTTPS (443)?](https://aws.amazon.com/premiumsupport/knowledge-center/connect-http-https-ec2/)

***
