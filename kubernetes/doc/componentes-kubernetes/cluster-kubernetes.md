---
description: Ao implantar o Kubernetes, você obtém um cluster.
---

# Cluster Kubernetes

{% embed url="https://kubernetes.io/pt-br/docs/concepts/overview/components/" %}

***

## <mark style="color:red;">Overview</mark>

Um **cluster Kubernetes** é composto por um conjunto de servidores, chamados **nodes**, que executam aplicações em containers dentro de **Pods,** que são as unidades básicas de execução no Kubernetes, encapsulando um ou mais containers de uma aplicação.

> _Quando se executa o Kubernetes, está se executando um cluster._&#x20;

* **Cluster:** Representa a infraestrutura em execução, sempre composta por:
  * **Control Plane:** Gerencia o cluster e coordena os nós de processamento.
  * **Worker Nodes:** Servidores que hospedam os Pods, onde as aplicações realmente rodam.

> No mínimo, um cluster K8s contém um plano de controle `Control-plane` e pelo menos um servidor de processamento `Worker node` ("Máquina ou nó `(node)"`).

<figure><img src="../.gitbook/assets/image (170).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (178).png" alt=""><figcaption></figcaption></figure>

**Ambiente de Gerenciamento:**

* Em produção, é distribuído por múltiplas máquinas para garantir alta disponibilidade e tolerância a falhas.

***

## <mark style="color:red;">API-Resources</mark>

{% embed url="https://kubernetes.io/docs/reference/kubectl/" %}

Executando no terminal podemos visualizar uma descrição dos recursos disponíveis no Kubernetes assim como também possíveis abreviações aceitas pelo `kubectl`

```bash
kubectl api-resource
```

***
