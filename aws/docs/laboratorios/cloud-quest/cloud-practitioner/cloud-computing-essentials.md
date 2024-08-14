---
description: >-
  Migrar um site existente para hospedagem de site estático no Amazon S3 para
  melhorar a confiabilidade.
---

# Cloud Computing Essentials

| Título da tarefa                         | Solicitação de negócios                                                                                                         |
| ---------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------- |
| Noções básicas sobre computação em nuvem | O portal da cidade precisa migrar a página de previsão do tamanho das ondas da praia para a AWS para melhorar a confiabilidade. |

<figure><img src="../../../.gitbook/assets/image (3) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

<details>

<summary><mark style="color:purple;">Contexto</mark></summary>



</details>

***

## <mark style="color:red;">Amazon S3</mark>

**Overview:** O Amazon Simple Storage Service (Amazon S3) pode ser usado para armazenar qualquer tipo de dado e recuperar qualquer quantidade de dados de qualquer lugar.

No Amazon S3, qualquer tipo de arquivo e qualquer metadado que descreva esse arquivo é chamado de objeto. Objetos são armazenados em contêineres do S3, chamados de buckets.

Esta solução utiliza um bucket S3 para hospedar um site estático. No Amazon S3, o site estático pode suportar qualquer nível de tráfego concebível, a um custo muito modesto, sem a necessidade de configurar, monitorar, escalar ou gerenciar qualquer servidor web.

**Mais Recursos:** Juntamente com um arquivo HTML, arquivos que suportam a funcionalidade da página da web, como scripts do lado do cliente e folhas de estilo, são carregados no bucket S3. Qualquer bucket S3 pode ser configurado para hospedar um site estático.

Quando um bucket S3 é configurado para hospedagem de site, o bucket recebe uma URL. Quando solicitações são feitas a essa URL, o Amazon S3 retorna o arquivo HTML, conhecido como objeto raiz, que foi definido para o bucket.

Para que outros acessem o bucket S3 ou objetos específicos nele, as permissões devem ser configuradas para permitir esse acesso. Uma política de bucket pode ser criada para configurar essas permissões.

**Gerenciamento de Acesso:** Uma política de bucket define quem pode acessar o bucket e que tipo de operações podem ser realizadas. Políticas de bucket são escritas no formato JSON.

JSON é um formato legível por humanos e por computadores usado para armazenar e recuperar dados. JSON é usado por muitas aplicações e em toda a AWS."

***

## <mark style="color:red;">Descrição da tarefa</mark>

Articule as características da plataforma de computação em nuvem da AWS.&#x20;

* Descreva os principais benefícios do uso de produtos e serviços da AWS.&#x20;
* Compare e contraste os serviços de nuvem da AWS com a infraestrutura On-Premises.&#x20;
* Implemente a hospedagem de uma página da Web estática usando o Amazon S3.
* Os residentes da cidade visitam o portal da cidade para obter informações sobre as ondas da praia, o que aciona uma solicitação **GET** do portal para a URL da página estática. O objeto raiz inicial é chamado de **index.html**.

1. Renomeie **index.html** no bucket **S3** para **waver.html** e, em seguida, atualize as configurações do bucket S3 para usar o objeto raiz renomeado.
2. Revise a política de bucket para proteger um bucket no Amazon S3.
3. Ative a hospedagem de site estático no bucket S3.
4. Teste o acesso à página da web hospedada no Amazon S3.

***

### <mark style="color:purple;">**Step 1**</mark>

1. Na caixa de busca da barra de navegação superior, digite: **`S3`**
2. Nos resultados da busca, sob serviços, clique em **`S3`**
3. Vá para o próximo passo.

#### <mark style="color:blue;">Conceito</mark>

O AWS Management Console é uma interface web para acessar e gerenciar a ampla coleção de serviços fornecidos pela Amazon Web Services (AWS).

<figure><img src="../../../.gitbook/assets/image (94).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">**Step 2**</mark>

1. Na aba de buckets de uso geral do laboratório, clique no nome do bucket que começa com **`website-bucket-`**.
2. O bucket que começa com **`website-bucket-`** contém o código necessário para este laboratório.
3. Vá para o próximo passo.

#### <mark style="color:blue;">Conceito</mark>

O Amazon Simple Storage Service (Amazon S3) é um serviço de armazenamento de objetos que oferece escalabilidade líder no setor, disponibilidade de dados, segurança e desempenho. Clientes de todos os tamanhos e indústrias podem usar o Amazon S3 para armazenar e proteger qualquer quantidade de dados para uma variedade de casos de uso, como data lakes, websites, mobile application, backup and restore, arquivamento, aplicativos corporativos, IoT devices, and big data analystics.

<figure><img src="../../../.gitbook/assets/image (96).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 3</mark>

1. Na aba **Objetos**, revise os objetos no bucket

* Cinco arquivos devem ser exibidos.
* Esses arquivos contêm o conteúdo da página estática.
* Arquivos locais podem ser carregados neste bucket S3 usando o botão **Upload**.

2. Marque a caixa de seleção para selecionar `text.html`.
3. Clique em Ações para expandir o **menu suspenso**.
4. Escolha **Renomear** objeto.
5. Vá para o próximo passo.

#### <mark style="color:blue;">Conceito</mark>

Um bucket é um contêiner para objetos armazenados no Amazon S3. Cada objeto está contido em um bucket. O Amazon S3 oferece uma variedade de classes de armazenamento para os objetos que você armazena. Você escolhe uma classe dependendo do seu cenário de uso e dos requisitos de desempenho de acesso. O Amazon S3 fornece classes de armazenamento para objetos de acesso frequente, acesso infrequente e arquivamento.

<figure><img src="../../../.gitbook/assets/image (97).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 4</mark>

1. Para o novo nome do objeto, digite: `error.html`

* Este arquivo contém o código para a página de erro, que abre sempre que algo dá errado.

2. Clique em **salvar alterações.**
3. Vá para o próximo passo.

#### <mark style="color:blue;">Conceito</mark>

Você pode escolher a região geográfica da AWS onde o Amazon S3 armazena os buckets que você cria. Você pode escolher uma região para otimizar a latência, minimizar custos ou atender a requisitos regulatórios. Objetos armazenados em uma região da AWS nunca saem da região, a menos que você os transfira ou replique explicitamente para outra região. Por exemplo, objetos armazenados na região da Europa (Irlanda) nunca a deixam. No entanto, o Amazon S3 armazena redundantemente objetos em vários dispositivos em, **no mínimo, três Zonas de Disponibilidade** em uma região da AWS. Uma Zona de Disponibilidade é um ou mais data centers discretos com energia, rede e conectividade redundantes em uma região da AWS.

<figure><img src="../../../.gitbook/assets/image (98).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 5</mark>

1. Na mensagem de alerta de sucesso, reveja a mensagem
2. Clique na aba **Permissões**
3. Vá para o próximo passo.

#### <mark style="color:blue;">Conceito</mark>

Usando o Amazon S3, você pode carregar objetos de até 5 GB de tamanho com uma única operação PUT. Para objetos maiores, com até 5 TB de tamanho, use a API de upload multipart.

<figure><img src="../../../.gitbook/assets/image (99).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 6</mark>

1. Na seção bloquear acesso público (configurações do bucket), verifique se a opção **bloquear todo o acesso público** está **desativada**.

* Desativar **'bloquear todo o acesso público'** é necessário para a hospedagem de sites estáticos por meio do seu bucket S3.

2. Role para baixo até **Política de Bucket**.
3. Vá para o próximo passo.

#### <mark style="color:blue;">Conceito</mark>

Por padrão, todos os recursos do Amazon S3 (buckets, objetos e sub-recursos relacionados) são privados. Apenas o proprietário do recurso pode acessá-los. O proprietário do recurso pode, opcionalmente, conceder permissões de acesso a outros escrevendo uma política de acesso.

<figure><img src="../../../.gitbook/assets/image (100).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 7</mark>

1. Na janela do editor de política do bucket, revise a política.

* Esta **política** permite o acesso público ao bucket S3.
* O **efeito** indica que esta política permitirá o acesso.
* O **principal** define quem tem acesso. Neste caso, **\*** representa qualquer pessoa.
* A ação define o que os usuários podem fazer com os objetos no bucket. Neste caso, os usuários só podem recuperar dados com GetObject.
* Os recursos especificam que esta política se aplica apenas a este bucket.
* Geralmente, para evitar a exposição acidental de dados, recomendamos permissões restritas para buckets S3 em produção.
* Role até o topo da página.
* Vá para o próximo passo.

#### <mark style="color:blue;">Conceito</mark>

Você pode conceder permissões aos seus recursos do Amazon S3 por meio de **políticas de bucket** e **políticas de usuário**. Ambas as opções utilizam uma linguagem de política de acesso baseada em JSON. Um **Amazon Resource Name (ARN)** identifica exclusivamente os recursos da AWS.

```json
{
    "Version": "2012-10-17",
    "Id": "StaticWebPolicy",
    "Statement": [
        {
            "Sid": "S3GetObjectAllow",
            "Effect": "Allow",
            "Principal": "*",
            "Action": "s3:GetObject",
            "Resource": "arn:aws:s3:::website-bucket-1bf06570/*"
        }
    ]
}
```

<figure><img src="../../../.gitbook/assets/image (251).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 8</mark>

1. Clique na aba **Propriedades**.
2. Vá para o próximo passo.

#### <mark style="color:blue;">Conceito</mark>

Para hospedar um site estático no Amazon S3, configure seu bucket para hospedagem de site estático, defina permissões e adicione um documento de índice. As opções disponíveis incluem redirecionamentos, registros e documentos de erro.

<figure><img src="../../../.gitbook/assets/image (103).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 9</mark>

1. Role para baixo até Hospedagem de site estático.
2. Clique em editar.
3. Vá para o próximo passo.

<figure><img src="../../../.gitbook/assets/image (104).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 10</mark>

1. Para hospedagem de site estático, escolha `Habilitar`.
2. Para tipo de hospedagem, escolha `hospedar um site estático`.
3. Para o documento de índice, digite: `index.html`
4. Para o documento de erro, digite: `error.html`
5. Vá para o próximo passo.

#### <mark style="color:blue;">Conceito</mark>

O Amazon S3 suporta URLs no estilo de hospedagem virtual e no estilo de caminho.

Uma URL no estilo de hospedagem virtual se parece com: [https://bucket-name.s3.Region.amazonaws.com/key](https://bucket-name.s3.region.amazonaws.com/key)

Uma URL no estilo de caminho se parece com[https://s3.Region.amazonaws.com/bucket-name/keyname](https://s3.region.amazonaws.com/bucket-name/keyname)

<figure><img src="../../../.gitbook/assets/image (105).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 11</mark>

1. Role para baixo até o final da página.
2. Clique em **`Salvar alterações.`**
3. Vá para o próximo passo.

<figure><img src="../../../.gitbook/assets/image (252).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 12</mark>

1. Role para baixo até **`hospedagem de site estático`**.
2. Revise para garantir que o tipo de hospedagem esteja definido como **`hospedagem de bucket`**.
3. Sob o endpoint do site do bucket, clique no ícone de **`copiar`** para copiar o endpoint fornecido.
4. Vá para o próximo passo.

<figure><img src="../../../.gitbook/assets/image (106).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:purple;">Step 13</mark>

1. Para carregar a página de Condições das Ondas da Praia, em uma nova aba (ou janela) do navegador, cole o endpoint do site do bucket que você acabou de copiar na barra de endereços e pressione **`Enter.`**
2. Vá para o próximo passo.

<figure><img src="../../../.gitbook/assets/image (107).png" alt=""><figcaption></figcaption></figure>

***

## DIY Activities

* [x] Renomeie **`index.html`** para **`waves.html`**.

<figure><img src="../../../.gitbook/assets/image (17) (2).png" alt=""><figcaption></figcaption></figure>

***
