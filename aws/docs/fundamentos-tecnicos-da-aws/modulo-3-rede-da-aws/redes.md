---
description: >-
  A rede é como você conecta computadores em todo o mundo e permite que eles se
  comuniquem uns com os outros.
---

# Redes

***

## <mark style="color:red;">Noções básicas de redes</mark>

Uma maneira fácil de entender como as redes funcionam é compará-las ao envio de uma carta. Quando você envia uma carta, precisa considerar três elementos principais:

1. A carga útil, que é a própria carta dentro do envelope.
2. O endereço do remetente na seção **"De"**.
3. O endereço do destinatário na seção **"Para"**.

Cada endereço precisa conter informações detalhadas, como:

* Nome do destinatário e do remetente
* Rua
* Cidade
* Estado ou província
* CEP ou código postal
* País

Esses detalhes são essenciais para garantir que a carta chegue corretamente ao destino. Sem um endereço completo e preciso, os funcionários dos correios não podem entregar a carta de forma adequada.

No mundo digital, a entrega de mensagens funciona de maneira semelhante, através de um processo chamado roteamento. Os computadores usam informações de endereçamento para garantir que os dados sejam enviados para o destinatário correto, assim como os correios fazem com as cartas.

***

### <mark style="color:red;">Endereços IP</mark>

Para que suas mensagens sejam roteadas corretamente, é necessário um endereço. Assim como cada casa tem um endereço postal, cada computador tem um endereço IP. No lugar da combinação de rua, cidade, estado, CEP e país, um endereço IP usa uma sequência de bits, composta de 0s e 1s.

Por exemplo, um endereço IP de 32 bits no formato binário pode ser representado da seguinte forma:

<figure><img src="https://explore.skillbuilder.aws/files/a/w/aws_prod1_docebosaas_com/1719252000/eHRhLbLLbvc_I-Jch4WVhA/tincan/954352_1676568571_p1gpdis23dphj1i0b12fk1vub1t4o4_zip/assets/mROZu0qA5Drsqfsi_MqSUJDRMLwF_EJf5.png" alt=""><figcaption></figcaption></figure>

É chamado de endereço de 32 bits porque consiste em 32 dígitos binários. Sinta-se à vontade para contar.

***

### <mark style="color:red;">Notação IPv4</mark>

Geralmente, os endereços IP não são apresentados em formato binário. Em vez disso, eles são convertidos para formato decimal e anotados como endereços IPv4.

Os 32 bits de um endereço IP são divididos em quatro grupos de 8 bits, chamados octetos. Cada octeto é então convertido para o formato decimal e os grupos são separados por pontos.

Por exemplo, um endereço IP em binário convertido para octetos decimais ficariam assim:

<figure><img src="https://explore.skillbuilder.aws/files/a/w/aws_prod1_docebosaas_com/1719252000/eHRhLbLLbvc_I-Jch4WVhA/tincan/954352_1676568571_p1gpdis23dphj1i0b12fk1vub1t4o4_zip/assets/F3YRtEoFVQL-G8ma_3O1LCsMztT9hP6Gv.png" alt=""><figcaption></figcaption></figure>

Essa forma de apresentação é chamada de endereço IPv4. É crucial para identificar um único computador na rede. Porém, quando se trabalha com redes, é importante entender a notação CIDR, que ajuda na especificação de faixas de endereços IP.

***

### <mark style="color:red;">Notação CIDR</mark>

O endereço `192.168.1.30` representa um único endereço IP. Se você quiser especificar um intervalo de endereços IP, como de `192.168.1.0` a `192.168.1.255`, pode usar a notação CIDR (Classless Inter-Domain Routing).

A notação CIDR é uma maneira compacta de especificar um intervalo de endereços IP, determinando quantos endereços estão disponíveis.

Ela começa com um endereço IP inicial, seguido por uma barra (**"/")** e um número que indica quantos bits do endereço IP são fixos. Por exemplo, na notação `192.168.1.0/24`, os primeiros 24 bits do endereço IP são fixos, e os restantes são variáveis.

Aqui está como funciona:

<figure><img src="../../.gitbook/assets/image (46) (1).png" alt=""><figcaption></figcaption></figure>

* `192.168.1.0/24`
* Os primeiros 24 bits são fixos: `192.168.1.`
* Os 8 bits restantes podem variar: `.0 a .255.`

Isso resulta em 256 endereços IP, já que cada um dos 8 bits variáveis pode ser **0** ou **1** (**2^8 = 256**).

{% hint style="info" %}
Quanto MAIOR o número após a **"/"**, Menor o intervalo de endereços IP.  Por exemplo, `192.168.1.0/24` tem menos endereços do que `192.168.0.0/16`.
{% endhint %}

Na AWS, você pode escolher o tamanho da rede usando a notação CIDR. O menor intervalo é `/28`, com **16 endereços IP**, e o maior é `/16`, com **65.536 endereços IP.**

***

## <mark style="color:red;">**Recursos**</mark>

[Stanford: Introdução à rede de computadores](https://web.stanford.edu/class/cs101/network-1-introduction.html)

[Ionos: CIDR: o que é roteamento entre domínios sem classe?](https://www.ionos.com/digitalguide/server/know-how/cidr-classless-inter-domain-routing/)

[CIDR.xyz](https://cidr.xyz/)

***
