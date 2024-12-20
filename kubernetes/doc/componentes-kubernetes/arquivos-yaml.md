---
description: >-
  O YAML (YAML Ain't Markup Language) é um formato de dados legível por humanos,
  usado principalmente para configuração de aplicações e definição de recursos,
  como no Kubernetes.
---

# Arquivos YAML

***

YAML significa -> "**Y**AML **A**int't **M**arkup **L**anguage" (YAML Não é uma Linguagem de Marcação)

<figure><img src="../.gitbook/assets/image (183).png" alt=""><figcaption></figcaption></figure>

* **Estrutura de dados:** Chave-valor.
* **Case sensitive:** YAML diferencia maiúsculas de minúsculas.
* **Codificação de Caracteres:** Suporta **UTF-8** ou **UTF-16**.
* **Não se deve utilizar o tab:** _É necessário utilizar espaços em branco porque os caracteres de tabulação não são permitidos_
* **Formato Simples:** Não utiliza chaves, colchetes, tags de fechamento ou aspas como no XML ou JSON._._
* Os arquivos YAML têm a extensão **.yml** ou **.yaml**

<figure><img src="../.gitbook/assets/image (184).png" alt=""><figcaption></figcaption></figure>

* HumanResource - O formato YAML é projetado para ser facilmente compreendido por seres humanos, oferecendo uma legibilidade superior em comparação ao **XML** ou **JSON**.

## <mark style="color:red;">YAML Kubernetes Exemple</mark>

<figure><img src="../.gitbook/assets/image (138).png" alt=""><figcaption></figcaption></figure>

***

### <mark style="color:red;">apiVersion</mark>&#x20;

{% embed url="https://kubernetes.io/docs/reference/using-api/#api-versioning" %}

Qual a versão de API do Kubernetes que será usado para criar esse recurso. API era uma única aplicação centralizada que foi dividida em diversas partes, por exemplo:&#x20;

> _a **versão alfa, a versão beta e a versão estável.**_&#x20;

* Onde a alfa tem coisas que podem ainda estar contendo bug;&#x20;

***

* Embaixo nós temos a beta que já pode ser considerada segura, mas ainda não é bom utilizar definitivamente;&#x20;

***

* E a versão estável que é um **“v”** seguido de um número inteiro, onde é a versão estável efetivamente para uso.&#x20;

> _E ela possui também diversos grupos para utilizar._

Isso pode ser consultado executando o comando kubectl api-resource

<table><thead><tr><th width="146" align="center">POD</th><th width="218" align="center">Deployment </th><th width="180" align="center">Service</th><th align="center">ReplicaSet</th></tr></thead><tbody><tr><td align="center">v1</td><td align="center">apps/v1</td><td align="center">v1</td><td align="center">apps/v1</td></tr></tbody></table>

***

### <mark style="color:red;">Kind</mark>&#x20;

O **`kind`** define o tipo de recurso a ser criado no Kubernetes. Alguns exemplos incluem:

> _Ex: (Pod, Deployment, Service... etc.)_

***

### <mark style="color:red;">Metadata</mark>&#x20;

Dados que ajudam a identificar de forma única o objeto.

* **Nome (name):** O nome do recurso.
* **UID:** Identificador único do objeto.
* **Namespace:** O namespace onde o objeto está localizado.

#### <mark style="color:blue;">Labels</mark>

Pares chave/valor usados para organizar e selecionar objetos e subconjuntos de objetos dentro do Kubernetes.

* As _Labels_ podem ser anexadas aos objetos no momento da criação e posteriormente adicionadas e modificadas a qualquer momento.
* Cada objeto pode ter um conjunto de _Labels_ de chave/valor definidos.
* Cada chave deve ser exclusiva para um determinado objeto.

***

### <mark style="color:red;">Spec</mark>&#x20;

Contém as especificações e definições do objeto Kubernetes. Cada tipo de objeto tem seu formato de spec específico. Por exemplo, um `Pod` pode ter uma lista de containers, enquanto um `Deployment` define o número de réplicas.

> A documentação de [referência da API do Kubernetes](https://kubernetes.io/docs/reference/kubernetes-api/) pode ajudar a encontrar o formato de especificação para todos os objetos que você pode criar usando Kubernetes.

***

### <mark style="color:red;">Selectors</mark>

Os **Selectors** permitem [selecione recursos do Kubernetes](https://kubernetes.io/docs/concepts/overview/working-with-objects/kubernetes-objects) baseado no valor de um ou mais campos de um recurso. Eles são úteis para selecionar subconjuntos de recursos que atendem a critérios definidos, como o nome ou o status.

Seguem alguns exemplos de buscas utilizando seletores de campos:

`metadata.name=my-service`

`metadata.namespace!=default`

`status.phase=Pending`

***
