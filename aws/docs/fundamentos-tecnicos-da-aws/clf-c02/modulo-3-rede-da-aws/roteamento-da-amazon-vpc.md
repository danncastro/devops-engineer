# Roteamento da Amazon VPC

***

## <mark style="color:red;">**Tabela de rotas principal**</mark>

Quando você cria uma VPC, a AWS gera automaticamente uma tabela de rotas chamada tabela de rotas principal. Uma tabela de rotas contém um conjunto de regras, chamadas rotas, que determinam para onde o tráfego de rede deve ser direcionado. A configuração padrão da tabela de rotas principal permite o tráfego entre todas as sub-redes dentro da VPC, garantindo a comunicação interna.

Aqui está um exemplo de uma tabela de rotas principal:

| Destino     | Alvo  |
| ----------- | ----- |
| 10.0.0.0/16 | Local |

#### <mark style="color:blue;">**Componentes Principais:**</mark>

* **Destino**: Este é o intervalo de endereços IP para onde você deseja que o tráfego seja direcionado. Semelhante ao endereço em uma carta, você precisa de um destino para encaminhar o tráfego corretamente. No contexto de uma VPC, o destino seria o intervalo de IP da própria rede VPC.
* **Alvo**: Este é o ponto de conexão para onde o tráfego deve ser enviado. No caso da tabela de rotas principal, o alvo é a própria rede VPC local, permitindo a comunicação interna entre as sub-redes.

#### <mark style="color:blue;">Exemplo:</mark>

<figure><img src="https://explore.skillbuilder.aws/files/a/w/aws_prod1_docebosaas_com/1719288000/qv1ubG4XmDzlGeSEaz41BQ/tincan/954352_1676568571_p1gpdis23dphj1i0b12fk1vub1t4o4_zip/assets/224LjBjaE-9SXuVC_-X2_R4cjJxpD1O-V.jpg" alt=""><figcaption></figcaption></figure>

Essa configuração padrão é crucial para garantir que todas as sub-redes dentro da VPC possam se comunicar entre si sem necessidade de configurações adicionais.

***

## <mark style="color:red;">**Tabelas de rotas personalizadas**</mark>

Embora a tabela de rotas principal seja utilizada implicitamente por sub-redes sem uma associação explícita, pode ser necessário configurar rotas específicas por sub-rede para permitir o acesso a recursos fora da VPC. Por exemplo, em uma aplicação com front-end e banco de dados separados, você pode criar sub-redes distintas para cada recurso e configurar rotas personalizadas para cada uma delas.

Quando você associa uma tabela de rotas personalizada a uma sub-rede, essa sub-rede utiliza essa tabela em vez da tabela de rotas principal. Cada tabela de rotas personalizada já inclui a rota local, que permite a comunicação entre todos os recursos e sub-redes na VPC. A rota local é essencial e não pode ser removida.

Isso permite um controle mais granular sobre como o tráfego é roteado dentro da sua VPC, adequando-se às necessidades específicas de diferentes componentes da sua aplicação ou serviço.

<figure><img src="https://explore.skillbuilder.aws/files/a/w/aws_prod1_docebosaas_com/1719288000/qv1ubG4XmDzlGeSEaz41BQ/tincan/954352_1676568571_p1gpdis23dphj1i0b12fk1vub1t4o4_zip/assets/CShrXPlESdZvNZBP_JqDCkbcIDd0Z0j86.jpg" alt=""><figcaption></figcaption></figure>

***
